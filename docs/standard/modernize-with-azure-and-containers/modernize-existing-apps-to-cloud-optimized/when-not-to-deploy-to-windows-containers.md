---
title: Pokud není k nasazení do systému Windows kontejnery
description: Modernizovat existující aplikace .NET s kontejnery cloudu Azure a Windows | Pokud není k nasazení do systému Windows kontejnery
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: 819f32955ff019414bef8820d17d272eddc11bf8
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/10/2018
---
# <a name="when-not-to-deploy-to-windows-containers"></a>Pokud není k nasazení do systému Windows kontejnery

Některé technologie systému Windows nepodporuje kontejnery systému Windows. V takových případech musíte stále migraci virtuálních počítačů standardy, obvykle s pouze systém Windows a služby IIS.

Nepodporované ve Windows kontejnery, od může 2018 případech: 

-   Microsoft služby Řízení front zpráv (MSMQ) aktuálně je k dispozici pouze v kontejnerech Windows založené na Windows Server v1803 verze, ale není v jiných předchozích verzích. 

    -   [Fórum požadavek UserVoice](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

    -   [Diskusní fórum](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

-   Microsoft Distributed Transaction Coordinator služba MSDTC () aktuálně není podporována v systému Windows kontejnerech.

    -   [Problém Githubu](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

-   Aplikace Microsoft Office aktuálně nepodporuje kontejnery.

    -   [Fórum požadavek UserVoice](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

-   Uživatelské rozhraní aplikace (aplikace klienta s visual uživatelským rozhraním) nejsou podporované scénáře.

-   Role infrastruktury systému Windows (DNS, DHCP, řadič domény, NTP, tisk, souborový server, IAM atd.) nejsou podporované scénáře.


Další-nepodporované scénáře a požadavky od komunity, najdete v části UserVoice fórum pro Windows kontejnery: <https://windowsserver.uservoice.com/forums/304624-containers>.

### <a name="additional-resources"></a>Další zdroje

-   **Virtuální počítače a kontejnerů v Azure**

    [https://docs.microsoft.com/azure/virtual-machines/windows/containers](https://docs.microsoft.com/azure/virtual-machines/windows/containers)

>[!div class="step-by-step"]
[Předchozí](deploy-existing-net-apps-as-windows-containers.md)
[další](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
