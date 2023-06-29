# The Flying Birds - Infrastructure

This repository contains the configuration files and information about the infrastructure used by The Flying Birds project. We leverage Kubernetes as our backend platform for efficient management and scalability.

## Contents

- [Backend](#backend)
- [Services](#services)
- [Minecraft Servers](#minecraft-servers)

## Backend

The backend of our infrastructure consists of the following components:

### Nexus Repository
[Nexus Repository](https://www.sonatype.com/nexus-repository-oss) is used to host our plugins, server files, and Docker images.

### Rancher
[Rancher](https://rancher.com/) is an administration and maintenance tool that simplifies the management of our servers. It provides an intuitive interface for easy control over the infrastructure.

### Longhorn
[Longhorn](https://longhorn.io/) is utilized as a distributed storage solution across the cluster. It ensures high availability and reliability of our data.

### Grafana Prometheus
[Grafana Prometheus](https://grafana.com/oss/prometheus/) is employed for monitoring the health and performance of our servers and cluster. It helps us proactively identify and address any potential issues.

### Coder Development environment
We are using a Coder development environment for easily creating sandboxed, environments of our servers.

## Services

We offer the following services within our infrastructure:

- **Website:** Our website serves as a central hub for project information, updates, and community engagement.
- **Discord Bot:** We have developed a Discord bot that assists with various tasks and enhances the user experience on our Discord server.

## Minecraft Servers

The Flying Birds project hosts the following Minecraft servers, providing diverse gameplay experiences to our community:

- **Flamecord:** A proxy for our servers, that we can have intercommunication.
- **Vanilla Server:** Our vanilla server provides a pure Minecraft experience without any modifications.
- **Creative:** The creative server allows players to unleash their creativity and build impressive structures.
- **Parkour:** This server focuses on parkour challenges, testing players' agility and skills.
- **Factions:** In our factions server, players can form alliances, wage wars, and conquer territories.
- **Lobby:** The lobby server acts as a central hub, providing access to other servers and serving as a gathering place for players.

### MySQL Database
We utilize a MySQL database to support Minecraft plugins such as Luckyperms, enabling advanced functionality within the game.


## More Information
Feel free to explore our infrastructure and join our Minecraft servers for an exciting gaming experience.

If you have any questions or need further assistance, please reach out to our team.
