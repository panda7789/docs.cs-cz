---
title: Kdy neprovádět nasazení do kontejnerů Windows
description: Modernizovat stávající aplikace .NET pomocí cloudu Azure a kontejnerů Windows | Kdy nasadit do kontejnerů Windows
ms.date: 04/28/2018
ms.openlocfilehash: 65e793b846b495e9a1be6db9ddfa38bbf0d49445
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/08/2019
ms.locfileid: "68676913"
---
# <a name="when-not-to-deploy-to-windows-containers"></a>Kdy neprovádět nasazení do kontejnerů Windows

Kontejnery Windows nepodporují některé technologie Windows. V těchto případech je stále potřeba migrovat na virtuální počítače Standard, obvykle jenom na Windows a IIS.

Případy nepodporované v kontejnerech Windows, od května 2018:

- Služba Řízení front zpráv (MSMQ) je aktuálně dostupná jenom v kontejnerech Windows, které jsou založené na verzi Windows serveru v1803, ale ne v jiných předchozích verzích.

  - [Fórum žádosti UserVoice](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

  - [Diskuzní fórum](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

- Microsoft DTC (Distributed Transaction Coordinator) (MSDTC) aktuálně není v kontejnerech Windows podporován.

  - [Problém GitHubu](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

- Systém Microsoft Office v současné době nepodporuje kontejnery.

  - [Fórum žádosti UserVoice](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

- Aplikace uživatelského rozhraní (klientské aplikace s vizuálním uživatelským rozhraním) nepodporují scénáře.

- Role infrastruktury systému Windows (DNS, DHCP, DC, NTP, tisk, souborový server, IAM atd.) nejsou podporované scénáře.

Další nepodporované scénáře a požadavky od komunity najdete v tématu Fórum UserVoice pro kontejnery Windows: <https://windowsserver.uservoice.com/forums/304624-containers>.

### <a name="additional-resources"></a>Další materiály a zdroje informací

- **Virtuální počítače a kontejnery v Azure**

    <https://azure.microsoft.com/overview/containers/>

> [!div class="step-by-step"]
> [Předchozí](deploy-existing-net-apps-as-windows-containers.md)
> [Další](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
