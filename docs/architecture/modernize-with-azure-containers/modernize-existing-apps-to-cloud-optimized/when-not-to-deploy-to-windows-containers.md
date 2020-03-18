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
# <a name="when-not-to-deploy-to-windows-containers"></a><span data-ttu-id="1bb02-103">Kdy neprovádět nasazení do kontejnerů Windows</span><span class="sxs-lookup"><span data-stu-id="1bb02-103">When not to deploy to Windows Containers</span></span>

<span data-ttu-id="1bb02-104">Některé technologie systému Windows nejsou kontejnery systému Windows podporovány.</span><span class="sxs-lookup"><span data-stu-id="1bb02-104">Some Windows technologies are not supported by Windows Containers.</span></span> <span data-ttu-id="1bb02-105">V těchto případech stále potřebujete migrovat na virtuální servery standardy, obvykle pouze se systémem Windows a službou IIS.</span><span class="sxs-lookup"><span data-stu-id="1bb02-105">In those cases, you still need to migrate to standards VMs, usually with just Windows and IIS.</span></span>

<span data-ttu-id="1bb02-106">Případy, které nejsou podporovány v kontejnerech windows, od května 2018:</span><span class="sxs-lookup"><span data-stu-id="1bb02-106">Cases not supported in Windows Containers, as of May 2018:</span></span>

- <span data-ttu-id="1bb02-107">Služba Microsoft Message Queuing (MSMQ) je v současné době k dispozici pouze v kontejnerech systému Windows na základě verze windows server v1803, ale ne v jiných předchozích verzích.</span><span class="sxs-lookup"><span data-stu-id="1bb02-107">Microsoft Message Queuing (MSMQ) currently is only available in Windows Containers based on Windows Server v1803 release, but not in any other prior releases.</span></span>

  - [<span data-ttu-id="1bb02-108">Fórum pro žádosti uživatele UserVoice</span><span class="sxs-lookup"><span data-stu-id="1bb02-108">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

  - [<span data-ttu-id="1bb02-109">Diskuzní fórum</span><span class="sxs-lookup"><span data-stu-id="1bb02-109">Discussion forum</span></span>](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

- <span data-ttu-id="1bb02-110">Koordinátor distribuovaných transakcí společnosti Microsoft (MSDTC) není v kontejnerech systému Windows aktuálně podporován.</span><span class="sxs-lookup"><span data-stu-id="1bb02-110">Microsoft Distributed Transaction Coordinator (MSDTC) currently is not supported in Windows Containers.</span></span>

  - [<span data-ttu-id="1bb02-111">Problém githubu</span><span class="sxs-lookup"><span data-stu-id="1bb02-111">GitHub issue</span></span>](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

- <span data-ttu-id="1bb02-112">Sada Microsoft Office aktuálně nepodporuje kontejnery.</span><span class="sxs-lookup"><span data-stu-id="1bb02-112">Microsoft Office currently does not support containers.</span></span>

  - [<span data-ttu-id="1bb02-113">Fórum pro žádosti uživatele UserVoice</span><span class="sxs-lookup"><span data-stu-id="1bb02-113">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

- <span data-ttu-id="1bb02-114">Aplikace uživatelského rozhraní (klientské aplikace s vizuálním uživatelským rozhraním) nejsou podporované scénáře.</span><span class="sxs-lookup"><span data-stu-id="1bb02-114">UI apps (client apps with a visual user interface) are not supported scenarios.</span></span>

- <span data-ttu-id="1bb02-115">Role infrastruktury systému Windows (DNS, DHCP, DC, NTP, PRINT, souborový server, IAM atd.) nejsou podporovány scénáře.</span><span class="sxs-lookup"><span data-stu-id="1bb02-115">Windows infrastructure roles (DNS, DHCP, DC, NTP, PRINT, File server, IAM etc.) are not supported scenarios.</span></span>

<span data-ttu-id="1bb02-116">Další nepodporované scénáře a požadavky komunity najdete ve fóru UserVoice <https://windowsserver.uservoice.com/forums/304624-containers>pro kontejnery windows: .</span><span class="sxs-lookup"><span data-stu-id="1bb02-116">For additional not-supported scenarios and requests from the community, see the UserVoice forum for Windows Containers: <https://windowsserver.uservoice.com/forums/304624-containers>.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="1bb02-117">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="1bb02-117">Additional resources</span></span>

- <span data-ttu-id="1bb02-118">**Virtuální počítače a kontejnery v Azure**</span><span class="sxs-lookup"><span data-stu-id="1bb02-118">**Virtual machines and containers in Azure**</span></span>

    <https://azure.microsoft.com/overview/containers/>

> [!div class="step-by-step"]
> <span data-ttu-id="1bb02-119">[Předchozí](deploy-existing-net-apps-as-windows-containers.md)
> [další](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="1bb02-119">[Previous](deploy-existing-net-apps-as-windows-containers.md)
[Next](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span></span>
