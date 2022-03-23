eks 클러스터에 argocd를 설치해요 (helm 차트 이용)

export ADMIN_PASSWORD="비밀번호"
export ARGOCD_PASSWORD="$(htpasswd -nbBC 10 "" ${ADMIN_PASSWORD} | tr -d ':\n' | sed 's/$2y/$2a/')"
export ARGOCD_SERVER_SECRET="채워넣기" # random string
export ARGOCD_WEBHOOK="채워넣기" # random string
export ARGOCD_NOTI_TOKEN="토큰발급받아서채우기"
export ARGOCD_HOSTNAME="url"


sha1 방식의 ssh key는 지원하지 않음. ed25519 방cd ..식으로 키를 만들어 넣어주기 

export ARGOCD_GITHUB_ID="tldms0327"
export ARGOCD_GITHUB_SECRET="$(cat ~/.ssh/id_ed25519 | tr -d ':\n' | sed 's/$2y/$2a/')" # github OAuth Apps
export GRAFANA_GITHUB_ID="tldms0327" 
export GRAFANA_GITHUB_SECRET="$(cat ~/.ssh/id_ed25519 | tr -d ':\n' | sed 's/$2y/$2a/')" # github OAuth Apps


# replace values.yaml
cp values.yaml values.output.yaml
find . -name values.output.yaml -exec sed -i "" -e "s/ARGOCD_HOSTNAME/${ARGOCD_HOSTNAME}/g" {} \;
find . -name values.output.yaml -exec sed -i "" -e "s@ARGOCD_PASSWORD@${ARGOCD_PASSWORD}@g" {} \;
find . -name values.output.yaml -exec sed -i "" -e "s/ARGOCD_MTIME/${ARGOCD_MTIME}/g" {} \;
find . -name values.output.yaml -exec sed -i "" -e "s/ARGOCD_SERVER_SECRET/${ARGOCD_SERVER_SECRET}/g" {} \;
find . -name values.output.yaml -exec sed -i "" -e "s/ARGOCD_GITHUB_ID/${ARGOCD_GITHUB_ID}/g" {} \;
find . -name values.output.yaml -exec sed -i "" -e "s@ARGOCD_GITHUB_SECRET@${ARGOCD_GITHUB_SECRET}@g" {} \;
find . -name values.output.yaml -exec sed -i "" -e "s/ARGOCD_WEBHOOK/${ARGOCD_WEBHOOK}/g" {} \;
find . -name values.output.yaml -exec sed -i "" -e "s/GITHUB_ORG/${GITHUB_ORG}/g" {} \;
find . -name values.output.yaml -exec sed -i "" -e "s/GITHUB_TEAM/${GITHUB_TEAM}/g" {} \;
find . -name values.output.yaml -exec sed -i "" -e "s/ARGOCD_NOTI_TOKEN/${ARGOCD_NOTI_TOKEN}/g" {} \;
