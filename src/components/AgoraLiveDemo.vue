<template>
    <div class="container">
        <span>{{tips}}</span>
    </div>
</template>

<script>
    import AgoraRTC from 'agora-rtc-sdk'

    const rtc = {
        client: null,
        joined: false,
        published: false,
        localStream: null,
        remoteStreams: [],
        params: {}
    }

    const option = {
        appID: "d7bef4a65cf24ff382e16409ae72fbe3",
        channel: "agora-live-demo",
        uid: null,
        token: "006d7bef4a65cf24ff382e16409ae72fbe3IADkgJ5KEU4xqsz4pbU0C8IJ8Az6qrHcoE8cT487/MAAgUwwKGMAAAAAEAAtzXrLsSLoXgEAAQCwIuhe"
    }

    export default {
        name: "AgoraLiveDemo",
        data: () => {
            return {
                tips: ''
            }
        },
        mounted() {

            rtc.client = AgoraRTC.createClient({mode: 'live', codec: 'h264'});
            let self = this;

            rtc.client.init(option.appID, () => {
                console.log('init success');
                self.tips = "Agora RTC初始化成功";

                //设置客户端角色
                rtc.client.setClientRole('host');

                // Join a channel
                rtc.client.join(option.token ? option.token : null, option.channel, option.uid ? +option.uid : null, function (uid) {
                    console.log("join channel: " + option.channel + " success, uid: " + uid);
                    rtc.params.uid = uid;

                    self.tips = "频道：" + option.channel + " uid: " + uid;
                }, function (err) {
                    console.error("client join failed", err)
                    self.tips = "加入频道失败：" + err;
                });
            }, (err) => {
                console.error('init fail ' + err);
                self.tips = "Agora RTC初始化失败";
            })
        }
    }
</script>

<style scoped>

</style>