---
title: MEF pro aplikace .NET pro Windows Store
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7667770e-d163-4ad6-a303-085cf73db2f2
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8436bff3b6ca1061621a67eb45bdc8aedea33f2c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="mef-for-net-for-windows-store-apps"></a><span data-ttu-id="fe90b-102">MEF pro aplikace .NET pro Windows Store</span><span class="sxs-lookup"><span data-stu-id="fe90b-102">MEF for .NET for Windows Store Apps</span></span>
<span data-ttu-id="fe90b-103"><xref:System.Composition?displayProperty=nameWithType>a jeho podřízené obory názvů obsahují typy pro vývoj extensible [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace s Managed Extensibility Framework (MEF).</span><span class="sxs-lookup"><span data-stu-id="fe90b-103"><xref:System.Composition?displayProperty=nameWithType> and its child namespaces contain types for developing extensible [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps with Managed Extensibility Framework (MEF).</span></span> <span data-ttu-id="fe90b-104">Tyto obory názvů jsou součástí [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] podmnožina pro [!INCLUDE[win8](../../../includes/win8-md.md)] operačního systému.</span><span class="sxs-lookup"><span data-stu-id="fe90b-104">These namespaces are part of the [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] subset for the [!INCLUDE[win8](../../../includes/win8-md.md)] operating system.</span></span>  
  
 <span data-ttu-id="fe90b-105">Tyto obory názvů nejsou součástí základní knihovny tříd distribuované s rozhraním .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fe90b-105">These namespaces are not part of the core class library distributed with the .NET Framework.</span></span> <span data-ttu-id="fe90b-106">Chcete-li nainstalovat tyto obory názvů, otevřete projekt v [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], zvolte **spravovat balíčky NuGet** z **projektu** nabídce a vyhledejte online balíček Microsoft.Composition.</span><span class="sxs-lookup"><span data-stu-id="fe90b-106">To install these namespaces, open your project in [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choose **Manage NuGet Packages** from the **Project** menu, and search online for the Microsoft.Composition package.</span></span>  
  
-   <span data-ttu-id="fe90b-107"><xref:System.Composition?displayProperty=nameWithType>poskytuje třídy, které tvoří jádro MEF pro [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="fe90b-107"><xref:System.Composition?displayProperty=nameWithType> provides classes that constitute the core MEF for [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps.</span></span>  
  
-   <span data-ttu-id="fe90b-108"><xref:System.Composition.Convention?displayProperty=nameWithType>obsahuje typy, které podporují rozhraní MEF pomocí založené na konvenci konfigurační model.</span><span class="sxs-lookup"><span data-stu-id="fe90b-108"><xref:System.Composition.Convention?displayProperty=nameWithType> provides types that support using MEF with a convention-based configuration model.</span></span>  
  
-   <span data-ttu-id="fe90b-109"><xref:System.Composition.Hosting?displayProperty=nameWithType>poskytuje rozhraní MEF typů, které jsou užitečné pro vývojáře aplikací hostitele.</span><span class="sxs-lookup"><span data-stu-id="fe90b-109"><xref:System.Composition.Hosting?displayProperty=nameWithType> provides MEF types that are useful to developers of host applications.</span></span>  
  
-   <span data-ttu-id="fe90b-110"><xref:System.Composition.Hosting.Core?displayProperty=nameWithType>obsahuje typy MEF interně používá modul složení.</span><span class="sxs-lookup"><span data-stu-id="fe90b-110"><xref:System.Composition.Hosting.Core?displayProperty=nameWithType> provides MEF types used internally by the composition engine.</span></span>  
  
 <span data-ttu-id="fe90b-111">Další informace o [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] a seznam obory názvů a typy, které obsahuje, najdete v části [přehled aplikace .NET pro Windows Store](http://go.microsoft.com/fwlink/p/?LinkID=238312) ve službě Windows Dev Center.</span><span class="sxs-lookup"><span data-stu-id="fe90b-111">For more information about [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] and a list of namespaces and types that it contains, see [.NET for Windows Store apps overview](http://go.microsoft.com/fwlink/p/?LinkID=238312) in the Windows Dev Center.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe90b-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="fe90b-112">See Also</span></span>  
 [<span data-ttu-id="fe90b-113">Přehled aplikace .NET pro Windows Store</span><span class="sxs-lookup"><span data-stu-id="fe90b-113">.NET for Windows Store apps overview</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=238312)  
 [<span data-ttu-id="fe90b-114">Aplikace .NET pro Windows Store – podporované rozhraní API</span><span class="sxs-lookup"><span data-stu-id="fe90b-114">.NET for Windows Store apps – supported APIs</span></span>](http://go.microsoft.com/fwlink/p/?LinkID=247912)  
 [<span data-ttu-id="fe90b-115">MEF (Managed Extensibility Framework)</span><span class="sxs-lookup"><span data-stu-id="fe90b-115">Managed Extensibility Framework (MEF)</span></span>](../../../docs/framework/mef/index.md)
