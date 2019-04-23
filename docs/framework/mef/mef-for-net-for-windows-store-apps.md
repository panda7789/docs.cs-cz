---
title: Rozhraní MEF pro .NET pro aplikace pro Windows Store
ms.date: 03/30/2017
ms.assetid: 7667770e-d163-4ad6-a303-085cf73db2f2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b47af2955d0ad8e618d0143d7eedff7c74278fbd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59150992"
---
# <a name="mef-for-net-for-windows-store-apps"></a><span data-ttu-id="50328-102">Rozhraní MEF pro .NET pro aplikace pro Windows Store</span><span class="sxs-lookup"><span data-stu-id="50328-102">MEF for .NET for Windows Store Apps</span></span>
<span data-ttu-id="50328-103"><xref:System.Composition?displayProperty=nameWithType> a jeho podřízené obory názvů obsahují typy pro vývoj rozšiřitelných [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikací pomocí Managed Extensibility Framework (MEF).</span><span class="sxs-lookup"><span data-stu-id="50328-103"><xref:System.Composition?displayProperty=nameWithType> and its child namespaces contain types for developing extensible [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps with Managed Extensibility Framework (MEF).</span></span> <span data-ttu-id="50328-104">Tyto obory názvů jsou součástí [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] dílčí pro [!INCLUDE[win8](../../../includes/win8-md.md)] operačního systému.</span><span class="sxs-lookup"><span data-stu-id="50328-104">These namespaces are part of the [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] subset for the [!INCLUDE[win8](../../../includes/win8-md.md)] operating system.</span></span>  
  
 <span data-ttu-id="50328-105">Tyto obory názvů nejsou součástí základní knihovny tříd distribuované s rozhraním .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="50328-105">These namespaces are not part of the core class library distributed with the .NET Framework.</span></span> <span data-ttu-id="50328-106">Pokud chcete nainstalovat tyto obory názvů, otevřete projekt v sadě Visual Studio, zvolte **spravovat balíčky NuGet** z **projektu** nabídky a vyhledejte online balíček Microsoft.Composition.</span><span class="sxs-lookup"><span data-stu-id="50328-106">To install these namespaces, open your project in Visual Studio, choose **Manage NuGet Packages** from the **Project** menu, and search online for the Microsoft.Composition package.</span></span>  
  
-   <span data-ttu-id="50328-107"><xref:System.Composition?displayProperty=nameWithType> poskytuje třídy, které tvoří základní rozhraní MEF pro [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="50328-107"><xref:System.Composition?displayProperty=nameWithType> provides classes that constitute the core MEF for [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps.</span></span>  
  
-   <span data-ttu-id="50328-108"><xref:System.Composition.Convention?displayProperty=nameWithType> poskytuje typy, které podporují model podle úmluvy konfigurace pomocí MEF.</span><span class="sxs-lookup"><span data-stu-id="50328-108"><xref:System.Composition.Convention?displayProperty=nameWithType> provides types that support using MEF with a convention-based configuration model.</span></span>  
  
-   <span data-ttu-id="50328-109"><xref:System.Composition.Hosting?displayProperty=nameWithType> obsahuje typy MEF, které jsou užitečné pro vývojáře aplikací na hostitele.</span><span class="sxs-lookup"><span data-stu-id="50328-109"><xref:System.Composition.Hosting?displayProperty=nameWithType> provides MEF types that are useful to developers of host applications.</span></span>  
  
-   <span data-ttu-id="50328-110"><xref:System.Composition.Hosting.Core?displayProperty=nameWithType> poskytuje interně modulem složení MEF typů.</span><span class="sxs-lookup"><span data-stu-id="50328-110"><xref:System.Composition.Hosting.Core?displayProperty=nameWithType> provides MEF types used internally by the composition engine.</span></span>  
  
 <span data-ttu-id="50328-111">Další informace o [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] a zobrazit seznam oborů názvů a typy, které obsahuje, [.NET pro Windows Store apps – přehled](https://go.microsoft.com/fwlink/p/?LinkID=238312) Windows Dev Center.</span><span class="sxs-lookup"><span data-stu-id="50328-111">For more information about [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] and a list of namespaces and types that it contains, see [.NET for Windows Store apps overview](https://go.microsoft.com/fwlink/p/?LinkID=238312) in the Windows Dev Center.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50328-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="50328-112">See also</span></span>

- [<span data-ttu-id="50328-113">.NET pro Windows Store apps – přehled</span><span class="sxs-lookup"><span data-stu-id="50328-113">.NET for Windows Store apps overview</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=238312)
- [<span data-ttu-id="50328-114">Aplikace .NET pro Windows Store – podporována rozhraní API</span><span class="sxs-lookup"><span data-stu-id="50328-114">.NET for Windows Store apps – supported APIs</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=247912)
- [<span data-ttu-id="50328-115">MEF (Managed Extensibility Framework)</span><span class="sxs-lookup"><span data-stu-id="50328-115">Managed Extensibility Framework (MEF)</span></span>](../../../docs/framework/mef/index.md)
