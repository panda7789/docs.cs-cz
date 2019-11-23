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
# <a name="when-not-to-deploy-to-windows-containers"></a><span data-ttu-id="5e366-103">Kdy neprovádět nasazení do kontejnerů Windows</span><span class="sxs-lookup"><span data-stu-id="5e366-103">When not to deploy to Windows Containers</span></span>

<span data-ttu-id="5e366-104">Kontejnery Windows nepodporují některé technologie Windows.</span><span class="sxs-lookup"><span data-stu-id="5e366-104">Some Windows technologies are not supported by Windows Containers.</span></span> <span data-ttu-id="5e366-105">V těchto případech je stále potřeba migrovat na virtuální počítače Standard, obvykle jenom na Windows a IIS.</span><span class="sxs-lookup"><span data-stu-id="5e366-105">In those cases, you still need to migrate to standards VMs, usually with just Windows and IIS.</span></span>

<span data-ttu-id="5e366-106">Případy nepodporované v kontejnerech Windows, od května 2018:</span><span class="sxs-lookup"><span data-stu-id="5e366-106">Cases not supported in Windows Containers, as of May 2018:</span></span>

- <span data-ttu-id="5e366-107">Služba Řízení front zpráv (MSMQ) je aktuálně dostupná jenom v kontejnerech Windows, které jsou založené na verzi Windows serveru v1803, ale ne v jiných předchozích verzích.</span><span class="sxs-lookup"><span data-stu-id="5e366-107">Microsoft Message Queuing (MSMQ) currently is only available in Windows Containers based on Windows Server v1803 release, but not in any other prior releases.</span></span>

  - [<span data-ttu-id="5e366-108">Fórum žádosti UserVoice</span><span class="sxs-lookup"><span data-stu-id="5e366-108">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

  - [<span data-ttu-id="5e366-109">Diskuzní fórum</span><span class="sxs-lookup"><span data-stu-id="5e366-109">Discussion forum</span></span>](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

- <span data-ttu-id="5e366-110">Microsoft DTC (Distributed Transaction Coordinator) (MSDTC) aktuálně není v kontejnerech Windows podporován.</span><span class="sxs-lookup"><span data-stu-id="5e366-110">Microsoft Distributed Transaction Coordinator (MSDTC) currently is not supported in Windows Containers.</span></span>

  - [<span data-ttu-id="5e366-111">Problém GitHubu</span><span class="sxs-lookup"><span data-stu-id="5e366-111">GitHub issue</span></span>](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

- <span data-ttu-id="5e366-112">Systém Microsoft Office v současné době nepodporuje kontejnery.</span><span class="sxs-lookup"><span data-stu-id="5e366-112">Microsoft Office currently does not support containers.</span></span>

  - [<span data-ttu-id="5e366-113">Fórum žádosti UserVoice</span><span class="sxs-lookup"><span data-stu-id="5e366-113">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

- <span data-ttu-id="5e366-114">Aplikace uživatelského rozhraní (klientské aplikace s vizuálním uživatelským rozhraním) nepodporují scénáře.</span><span class="sxs-lookup"><span data-stu-id="5e366-114">UI apps (client apps with a visual user interface) are not supported scenarios.</span></span>

- <span data-ttu-id="5e366-115">Role infrastruktury systému Windows (DNS, DHCP, DC, NTP, tisk, souborový server, IAM atd.) nejsou podporované scénáře.</span><span class="sxs-lookup"><span data-stu-id="5e366-115">Windows infrastructure roles (DNS, DHCP, DC, NTP, PRINT, File server, IAM etc.) are not supported scenarios.</span></span>

<span data-ttu-id="5e366-116">Další nepodporované scénáře a požadavky od komunity najdete v tématu Fórum UserVoice pro kontejnery Windows: <https://windowsserver.uservoice.com/forums/304624-containers>.</span><span class="sxs-lookup"><span data-stu-id="5e366-116">For additional not-supported scenarios and requests from the community, see the UserVoice forum for Windows Containers: <https://windowsserver.uservoice.com/forums/304624-containers>.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="5e366-117">Další materiály a zdroje informací</span><span class="sxs-lookup"><span data-stu-id="5e366-117">Additional resources</span></span>

- <span data-ttu-id="5e366-118">**Virtuální počítače a kontejnery v Azure**</span><span class="sxs-lookup"><span data-stu-id="5e366-118">**Virtual machines and containers in Azure**</span></span>

    <https://azure.microsoft.com/overview/containers/>

> [!div class="step-by-step"]
> <span data-ttu-id="5e366-119">[Předchozí](deploy-existing-net-apps-as-windows-containers.md)
> [Další](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="5e366-119">[Previous](deploy-existing-net-apps-as-windows-containers.md)
[Next](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span></span>
