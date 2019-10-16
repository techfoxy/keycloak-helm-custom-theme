# keycloak-helm-custom-theme
Demo how to apply a custom theme when installing keycloak using helm chart.

Apply when deploy the Keycloak helm chart [codecentric/keycloak](https://github.com/codecentric/helm-charts/tree/master/charts/keycloak)

# How to customize the keycloak theme
Keycloak supports for deeply customize for almost every pages which including:
- Login/Register/Forgot Password/2FA Login...
- Account management pages
- Admin pages
- Welcome page
- Email templates

Keycloak has already provide the theme structure in the "Base theme", and when creating a new theme, it's recommended to inherit from this theme by specify it as parent theme. Then, all you have to do is override what you want to customize only.

One another note is that you can customize everything, but because of keycloak had defined a complicated structure in the theme in the "*.ftl" with their own logic, so it would better to keep the origin structure and just update the "look and feel" style only. This make sure you will not broke any built-in features which may currently hidden by some settings.

# How to apply the theme to the Keycloak Helm chart
## Build and Push the Keycloak Theme as a Docker Image
After update the theme, you must build the new theme as a Docker image and push to any docker registery like Docker Hub or any other private docker registery services as such Azure Container Registery (ACR) or AWS Container Registry (ECR). In this guide, I will push the theme docker container to the Docker Hub as a Public repository.

To build a docker image and push to the docker hub, please refer to the Docker guide for how to accomplish this task.

After build and push to the Docker Hub, now I have a Docker Image as Public Repository at: [techfoxy/techfoxy_kecyloak_theme](https://cloud.docker.com/repository/registry-1.docker.io/techfoxy/techfoxy_keycloak_theme)

Note: When debuging the theme, I had build some docker images with different tag (0.1,0.2). You can overwrite the tag when re-build the docker image, but when running the Helm chart, it may got an issue about the docker image caching, so solving this issue easy, you just push a new docker image with a new tag.

## Update the values.yaml for using the new customized theme.
Please follow to the values.yaml and update to match your requirement.