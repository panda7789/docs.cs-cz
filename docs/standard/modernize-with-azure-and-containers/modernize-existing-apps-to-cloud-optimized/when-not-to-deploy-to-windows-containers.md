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
# <a name="when-not-to-deploy-to-windows-containers"></a><span data-ttu-id="726ec-103">Pokud není k nasazení do systému Windows kontejnery</span><span class="sxs-lookup"><span data-stu-id="726ec-103">When not to deploy to Windows Containers</span></span>

<span data-ttu-id="726ec-104">Některé technologie systému Windows nepodporuje kontejnery systému Windows.</span><span class="sxs-lookup"><span data-stu-id="726ec-104">Some Windows technologies are not supported by Windows Containers.</span></span> <span data-ttu-id="726ec-105">V takových případech musíte stále migraci virtuálních počítačů standardy, obvykle s pouze systém Windows a služby IIS.</span><span class="sxs-lookup"><span data-stu-id="726ec-105">In those cases, you still need to migrate to standards VMs, usually with just Windows and IIS.</span></span>

<span data-ttu-id="726ec-106">Nepodporované ve Windows kontejnery, od může 2018 případech:</span><span class="sxs-lookup"><span data-stu-id="726ec-106">Cases not supported in Windows Containers, as of May 2018:</span></span> 

-   <span data-ttu-id="726ec-107">Microsoft služby Řízení front zpráv (MSMQ) aktuálně je k dispozici pouze v kontejnerech Windows založené na Windows Server v1803 verze, ale není v jiných předchozích verzích.</span><span class="sxs-lookup"><span data-stu-id="726ec-107">Microsoft Message Queuing (MSMQ) currently is only available in Windows Containers based on Windows Server v1803 release, but not in any other prior releases.</span></span> 

    -   [<span data-ttu-id="726ec-108">Fórum požadavek UserVoice</span><span class="sxs-lookup"><span data-stu-id="726ec-108">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

    -   [<span data-ttu-id="726ec-109">Diskusní fórum</span><span class="sxs-lookup"><span data-stu-id="726ec-109">Discussion forum</span></span>](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

-   <span data-ttu-id="726ec-110">Microsoft Distributed Transaction Coordinator služba MSDTC () aktuálně není podporována v systému Windows kontejnerech.</span><span class="sxs-lookup"><span data-stu-id="726ec-110">Microsoft Distributed Transaction Coordinator (MSDTC) currently is not supported in Windows Containers.</span></span>

    -   [<span data-ttu-id="726ec-111">Problém Githubu</span><span class="sxs-lookup"><span data-stu-id="726ec-111">GitHub issue</span></span>](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

-   <span data-ttu-id="726ec-112">Aplikace Microsoft Office aktuálně nepodporuje kontejnery.</span><span class="sxs-lookup"><span data-stu-id="726ec-112">Microsoft Office currently does not support containers.</span></span>

    -   [<span data-ttu-id="726ec-113">Fórum požadavek UserVoice</span><span class="sxs-lookup"><span data-stu-id="726ec-113">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

-   <span data-ttu-id="726ec-114">Uživatelské rozhraní aplikace (aplikace klienta s visual uživatelským rozhraním) nejsou podporované scénáře.</span><span class="sxs-lookup"><span data-stu-id="726ec-114">UI apps (client apps with a visual user interface) are not supported scenarios.</span></span>

-   <span data-ttu-id="726ec-115">Role infrastruktury systému Windows (DNS, DHCP, řadič domény, NTP, tisk, souborový server, IAM atd.) nejsou podporované scénáře.</span><span class="sxs-lookup"><span data-stu-id="726ec-115">Windows infrastructure roles (DNS, DHCP, DC, NTP, PRINT, File server, IAM etc.) are not supported scenarios.</span></span>


<span data-ttu-id="726ec-116">Další-nepodporované scénáře a požadavky od komunity, najdete v části UserVoice fórum pro Windows kontejnery: <https://windowsserver.uservoice.com/forums/304624-containers>.</span><span class="sxs-lookup"><span data-stu-id="726ec-116">For additional not-supported scenarios and requests from the community, see the UserVoice forum for Windows Containers: <https://windowsserver.uservoice.com/forums/304624-containers>.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="726ec-117">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="726ec-117">Additional resources</span></span>

-   <span data-ttu-id="726ec-118">**Virtuální počítače a kontejnerů v Azure**</span><span class="sxs-lookup"><span data-stu-id="726ec-118">**Virtual machines and containers in Azure**</span></span>

    [https://docs.microsoft.com/azure/virtual-machines/windows/containers](https://docs.microsoft.com/azure/virtual-machines/windows/containers)

>[!div class="step-by-step"]
<span data-ttu-id="726ec-119">[Předchozí](deploy-existing-net-apps-as-windows-containers.md)
[další](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="726ec-119">[Previous](deploy-existing-net-apps-as-windows-containers.md)
[Next](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span></span>
