---
title: Kdy neprovádět nasazení do kontejnerů Windows
description: Modernizace stávajících aplikací .NET pomocí cloudu Azure a Windows kontejnery | Kdy neprovádět nasazení do kontejnerů Windows
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 04/28/2018
ms.openlocfilehash: e06793065d1fd55bbef855576174b07dc9ace4c8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64751398"
---
# <a name="when-not-to-deploy-to-windows-containers"></a><span data-ttu-id="bee4f-103">Kdy neprovádět nasazení do kontejnerů Windows</span><span class="sxs-lookup"><span data-stu-id="bee4f-103">When not to deploy to Windows Containers</span></span>

<span data-ttu-id="bee4f-104">Některé technologie Windows nejsou podporovány kontejnery Windows.</span><span class="sxs-lookup"><span data-stu-id="bee4f-104">Some Windows technologies are not supported by Windows Containers.</span></span> <span data-ttu-id="bee4f-105">V takových případech musíte stále migrovat na virtuální počítače standardy, obvykle pomocí právě Windows a služby IIS.</span><span class="sxs-lookup"><span data-stu-id="bee4f-105">In those cases, you still need to migrate to standards VMs, usually with just Windows and IIS.</span></span>

<span data-ttu-id="bee4f-106">Případy nejsou podporovány v kontejnerech Windows, od května 2018:</span><span class="sxs-lookup"><span data-stu-id="bee4f-106">Cases not supported in Windows Containers, as of May 2018:</span></span>

- <span data-ttu-id="bee4f-107">Microsoft Message Queuing (MSMQ) aktuálně dostupná jenom v kontejnerech Windows podle verze v1803 Windows serveru, ale ne ve všech předchozích verzích.</span><span class="sxs-lookup"><span data-stu-id="bee4f-107">Microsoft Message Queuing (MSMQ) currently is only available in Windows Containers based on Windows Server v1803 release, but not in any other prior releases.</span></span>

  - [<span data-ttu-id="bee4f-108">Fórum UserVoice žádosti</span><span class="sxs-lookup"><span data-stu-id="bee4f-108">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

  - [<span data-ttu-id="bee4f-109">Diskuzní fórum</span><span class="sxs-lookup"><span data-stu-id="bee4f-109">Discussion forum</span></span>](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

- <span data-ttu-id="bee4f-110">Microsoft distribuované transakce koordinátor (MSDTC) se aktuálně nepodporuje v kontejnerech Windows.</span><span class="sxs-lookup"><span data-stu-id="bee4f-110">Microsoft Distributed Transaction Coordinator (MSDTC) currently is not supported in Windows Containers.</span></span>

  - [<span data-ttu-id="bee4f-111">Problém Githubu</span><span class="sxs-lookup"><span data-stu-id="bee4f-111">GitHub issue</span></span>](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

- <span data-ttu-id="bee4f-112">Aplikace Microsoft Office v současné době nepodporuje kontejnery.</span><span class="sxs-lookup"><span data-stu-id="bee4f-112">Microsoft Office currently does not support containers.</span></span>

  - [<span data-ttu-id="bee4f-113">Fórum UserVoice žádosti</span><span class="sxs-lookup"><span data-stu-id="bee4f-113">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

- <span data-ttu-id="bee4f-114">Uživatelské rozhraní aplikace (visual uživatelského rozhraní klientských aplikací) nejsou podporované scénáře.</span><span class="sxs-lookup"><span data-stu-id="bee4f-114">UI apps (client apps with a visual user interface) are not supported scenarios.</span></span>

- <span data-ttu-id="bee4f-115">Infrastrukturu role Windows (DNS, DHCP, řadičů domény, NTP, tisk, souborový server, IAM atd.) nejsou podporované scénáře.</span><span class="sxs-lookup"><span data-stu-id="bee4f-115">Windows infrastructure roles (DNS, DHCP, DC, NTP, PRINT, File server, IAM etc.) are not supported scenarios.</span></span>

<span data-ttu-id="bee4f-116">Pro další nepodporované scénáře a požadavky komunity, podívejte se na fóru UserVoice pro kontejnery Windows: <https://windowsserver.uservoice.com/forums/304624-containers>.</span><span class="sxs-lookup"><span data-stu-id="bee4f-116">For additional not-supported scenarios and requests from the community, see the UserVoice forum for Windows Containers: <https://windowsserver.uservoice.com/forums/304624-containers>.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="bee4f-117">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="bee4f-117">Additional resources</span></span>

- <span data-ttu-id="bee4f-118">**Virtuální počítače a kontejnery v Azure**</span><span class="sxs-lookup"><span data-stu-id="bee4f-118">**Virtual machines and containers in Azure**</span></span>

    <https://azure.microsoft.com/overview/containers/>

> [!div class="step-by-step"]
> <span data-ttu-id="bee4f-119">[Předchozí](deploy-existing-net-apps-as-windows-containers.md)
> [další](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="bee4f-119">[Previous](deploy-existing-net-apps-as-windows-containers.md)
[Next](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span></span>
