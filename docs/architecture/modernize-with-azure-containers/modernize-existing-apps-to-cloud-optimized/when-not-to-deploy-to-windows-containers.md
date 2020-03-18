---
title: Kdy neprovádět nasazení do kontejnerů Windows
description: Modernizace stávajících aplikací .NET pomocí Azure Cloudu a kontejnerů Windows | Kdy není nasadit do kontejnerů Windows
ms.date: 04/28/2018
ms.openlocfilehash: 65e793b846b495e9a1be6db9ddfa38bbf0d49445
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "68676913"
---
# <a name="when-not-to-deploy-to-windows-containers"></a>Kdy neprovádět nasazení do kontejnerů Windows

Některé technologie systému Windows nejsou kontejnery systému Windows podporovány. V těchto případech stále potřebujete migrovat na virtuální servery standardy, obvykle pouze se systémem Windows a službou IIS.

Případy, které nejsou podporovány v kontejnerech windows, od května 2018:

- Služba Microsoft Message Queuing (MSMQ) je v současné době k dispozici pouze v kontejnerech systému Windows na základě verze windows server v1803, ale ne v jiných předchozích verzích.

  - [Fórum pro žádosti uživatele UserVoice](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

  - [Diskuzní fórum](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

- Koordinátor distribuovaných transakcí společnosti Microsoft (MSDTC) není v kontejnerech systému Windows aktuálně podporován.

  - [Problém githubu](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

- Sada Microsoft Office aktuálně nepodporuje kontejnery.

  - [Fórum pro žádosti uživatele UserVoice](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

- Aplikace uživatelského rozhraní (klientské aplikace s vizuálním uživatelským rozhraním) nejsou podporované scénáře.

- Role infrastruktury systému Windows (DNS, DHCP, DC, NTP, PRINT, souborový server, IAM atd.) nejsou podporovány scénáře.

Další nepodporované scénáře a požadavky komunity najdete ve fóru UserVoice <https://windowsserver.uservoice.com/forums/304624-containers>pro kontejnery windows: .

### <a name="additional-resources"></a>Další zdroje

- **Virtuální počítače a kontejnery v Azure**

    <https://azure.microsoft.com/overview/containers/>

> [!div class="step-by-step"]
> [Předchozí](deploy-existing-net-apps-as-windows-containers.md)
> [další](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
