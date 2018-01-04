---
title: "Spuštění rozhraní .NET Framework 1.1 aplikace na Windows 8, Windows 8.1 nebo Windows 10"
ms.custom: 
ms.date: 05/26/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows 8, running .NET Framework 1.1 apps
- .NET Framework 1.1, running on Windows 8
ms.assetid: fb14e195-fea5-4561-b9a8-60a67283edb9
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9d5b99390e62984b37b0d7267c40b1221f556f60
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="run-net-framework-11-apps-on-windows-8-windows-81-or-windows-10"></a><span data-ttu-id="12607-102">Spuštění rozhraní .NET Framework 1.1 aplikace na Windows 8, Windows 8.1 nebo Windows 10</span><span class="sxs-lookup"><span data-stu-id="12607-102">Run .NET Framework 1.1 apps on Windows 8, Windows 8.1, or Windows 10</span></span>

<span data-ttu-id="12607-103">Nepodporuje rozhraní .NET Framework 1.1 [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)], [!INCLUDE[winserver8](../../../includes/winserver8-md.md)], [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)], nebo operační systémy Windows 10.</span><span class="sxs-lookup"><span data-stu-id="12607-103">The .NET Framework 1.1 is not supported on the [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)], [!INCLUDE[winserver8](../../../includes/winserver8-md.md)], [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)], or the Windows 10 operating systems.</span></span> <span data-ttu-id="12607-104">V některých případech je rozhraní .NET Framework 1.1 konkrétně identifikovat podle potřeby pro aplikaci, ke spuštění.</span><span class="sxs-lookup"><span data-stu-id="12607-104">In some cases, the .NET Framework 1.1 is specifically identified as required for an app to run.</span></span> <span data-ttu-id="12607-105">V těchto případech, měli byste požádat vašeho nezávislý dodavatel softwaru (ISV) tak, aby měl aplikaci upgradovat ke spuštění na [!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)] nebo novější verze.</span><span class="sxs-lookup"><span data-stu-id="12607-105">In those cases, you should contact your independent software vendor (ISV) to have the app upgraded to run on the [!INCLUDE[net_v35SP1_short](../../../includes/net-v35sp1-short-md.md)] or later version.</span></span> <span data-ttu-id="12607-106">Další informace najdete v tématu [migrace z verze rozhraní .NET Framework 1.1](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md).</span><span class="sxs-lookup"><span data-stu-id="12607-106">For additional information, see [Migrating from the .NET Framework 1.1](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md).</span></span>

## <a name="install-the-net-framework-11-from-a-cd-or-download-center"></a><span data-ttu-id="12607-107">Nainstalujte rozhraní .NET Framework 1.1 z disku CD nebo stažení softwaru společnosti Microsoft</span><span class="sxs-lookup"><span data-stu-id="12607-107">Install the .NET Framework 1.1 from a CD or Download Center</span></span>

<span data-ttu-id="12607-108">Není možné ručně nainstalovat rozhraní .NET Framework 1.1 [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)], [!INCLUDE[winserver8](../../../includes/winserver8-md.md)], [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)], nebo Windows 10.</span><span class="sxs-lookup"><span data-stu-id="12607-108">It isn't possible to manually install the .NET Framework 1.1 on [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)], [!INCLUDE[winserver8](../../../includes/winserver8-md.md)], [!INCLUDE[winblue_server_2](../../../includes/winblue-server-2-md.md)], or Windows 10.</span></span> <span data-ttu-id="12607-109">Už se nepodporuje.</span><span class="sxs-lookup"><span data-stu-id="12607-109">It is no longer supported.</span></span> <span data-ttu-id="12607-110">Pokud se pokusíte nainstalovat balíček, zobrazí se následující chybová zpráva: "Instalační program nemůže pokračovat, protože tato verze rozhraní .NET Framework je kompatibilní s dříve nainstalované jeden."</span><span class="sxs-lookup"><span data-stu-id="12607-110">If you try to install the package, the following error message is displayed: "Setup cannot continue because this version of the .NET Framework is incompatible with a previously installed one."</span></span> <span data-ttu-id="12607-111">Chcete-li tento problém vyřešit, nainstalujte [rozhraní .NET Framework 3.5 SP1](http://www.microsoft.com/download/details.aspx?id=22).</span><span class="sxs-lookup"><span data-stu-id="12607-111">To solve this problem, install the [.NET Framework 3.5 SP1](http://www.microsoft.com/download/details.aspx?id=22).</span></span> <span data-ttu-id="12607-112">Tato verze zahrnuje rozhraní .NET Framework 2.0 (verze, která následuje rozhraní .NET Framework 1.1), který není podporován na [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)]a Windows 10.</span><span class="sxs-lookup"><span data-stu-id="12607-112">This version includes the .NET Framework 2.0 (the release that follows the .NET Framework 1.1), which is supported on [!INCLUDE[win8](../../../includes/win8-md.md)], [!INCLUDE[win81](../../../includes/win81-md.md)], and Windows 10.</span></span> <span data-ttu-id="12607-113">Musí se vždy pokusí nainstalovat aplikaci nejprve k určení, pokud ho se automaticky aktualizují na novější verzi rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="12607-113">You should always try to install the app first to determine if it will automatically be updated to a later version of the .NET Framework.</span></span> <span data-ttu-id="12607-114">Pokud ne, obraťte se na vaše ISV pro aktualizaci aplikace.</span><span class="sxs-lookup"><span data-stu-id="12607-114">If it does not, contact your ISV for an app update.</span></span>

## <a name="see-also"></a><span data-ttu-id="12607-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="12607-115">See also</span></span>

<span data-ttu-id="12607-116">[Migrace z rozhraní .NET Framework 1.1](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md)
[instalaci rozhraní .NET Framework 3.5 ve Windows 10, Windows 8.1 a Windows 8](../../../docs/framework/install/dotnet-35-windows-10.md)</span><span class="sxs-lookup"><span data-stu-id="12607-116">[Migrating from the .NET Framework 1.1](../../../docs/framework/migration-guide/migrating-from-the-net-framework-1-1.md)
[Install the .NET Framework 3.5 on Windows 10, Windows 8.1, and Windows 8](../../../docs/framework/install/dotnet-35-windows-10.md)</span></span>
