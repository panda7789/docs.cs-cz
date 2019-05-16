---
title: Kdy neprovádět nasazení do kontejnerů Windows
description: Modernizace stávajících aplikací .NET pomocí cloudu Azure a Windows kontejnery | Kdy neprovádět nasazení do kontejnerů Windows
ms.date: 04/28/2018
ms.openlocfilehash: 65e793b846b495e9a1be6db9ddfa38bbf0d49445
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65638902"
---
# <a name="when-not-to-deploy-to-windows-containers"></a>Kdy neprovádět nasazení do kontejnerů Windows

Některé technologie Windows nejsou podporovány kontejnery Windows. V takových případech musíte stále migrovat na virtuální počítače standardy, obvykle pomocí právě Windows a služby IIS.

Případy nejsou podporovány v kontejnerech Windows, od května 2018:

- Microsoft Message Queuing (MSMQ) aktuálně dostupná jenom v kontejnerech Windows podle verze v1803 Windows serveru, ale ne ve všech předchozích verzích.

  - [Fórum UserVoice žádosti](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

  - [Diskuzní fórum](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

- Microsoft distribuované transakce koordinátor (MSDTC) se aktuálně nepodporuje v kontejnerech Windows.

  - [Problém Githubu](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

- Aplikace Microsoft Office v současné době nepodporuje kontejnery.

  - [Fórum UserVoice žádosti](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

- Uživatelské rozhraní aplikace (visual uživatelského rozhraní klientských aplikací) nejsou podporované scénáře.

- Infrastrukturu role Windows (DNS, DHCP, řadičů domény, NTP, tisk, souborový server, IAM atd.) nejsou podporované scénáře.

Pro další nepodporované scénáře a požadavky komunity, podívejte se na fóru UserVoice pro kontejnery Windows: <https://windowsserver.uservoice.com/forums/304624-containers>.

### <a name="additional-resources"></a>Další zdroje

- **Virtuální počítače a kontejnery v Azure**

    <https://azure.microsoft.com/overview/containers/>

> [!div class="step-by-step"]
> [Předchozí](deploy-existing-net-apps-as-windows-containers.md)
> [další](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)
