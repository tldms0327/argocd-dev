eks 클러스터에 argocd를 설치해요 (helm 차트 이용)

export ADMIN_PASSWORD="admin"
export ARGOCD_PASSWORD="$(htpasswd -nbBC 10 "" ${ADMIN_PASSWORD} | tr -d ':\n' | sed 's/$2y/$2a/')"
export ARGOCD_SERVER_SECRET="dkanrjsk" # random string
export ARGOCD_WEBHOOK="dkanrjsk" # random string
export ARGOCD_NOTI_TOKEN="TOKEN" # xoxp-xxxx <https://api.slack.com/apps>


sha1 방식의 ssh key는 지원하지 않음. ed25519 방식으로 키를 만들어 넣어주기 

export ARGOCD_GITHUB_ID="tldms0327"
export ARGOCD_GITHUB_SECRET="$(cat ~/.ssh/id_ed25519 | tr -d ':\n' | sed 's/$2y/$2a/')" # github OAuth Apps
export GRAFANA_GITHUB_ID="tldms0327" 
export GRAFANA_GITHUB_SECRET="$(cat ~/.ssh/id_ed25519 | tr -d ':\n' | sed 's/$2y/$2a/')" # github OAuth Apps