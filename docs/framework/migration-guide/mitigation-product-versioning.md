---
title: "Zmírňující opatření: Správa verzí produktu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c4de9d7-9aba-427a-8f38-0ab9bfb8f85e
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 15648a3dfc115e55dd78eb1f074b9c4235b89f34
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="mitigation-product-versioning"></a><span data-ttu-id="a91a4-102">Zmírňující opatření: Správa verzí produktu</span><span class="sxs-lookup"><span data-stu-id="a91a4-102">Mitigation: Product Versioning</span></span>
<span data-ttu-id="a91a4-103">V [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] a novější, Správa verzí produktu se změnil z předchozích verzí rozhraní .NET Framework (rozhraní .NET Framework 4, 4.5, 4.5.1 a 4.5.2).</span><span class="sxs-lookup"><span data-stu-id="a91a4-103">In the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] and later, product versioning has changed from the previous releases of the .NET Framework (the .NET Framework 4, 4.5, 4.5.1, and 4.5.2).</span></span>  
  
## <a name="product-versioning-changes"></a><span data-ttu-id="a91a4-104">Změny Správa verzí produktu</span><span class="sxs-lookup"><span data-stu-id="a91a4-104">Product versioning changes</span></span>  
 <span data-ttu-id="a91a4-105">Tady jsou podrobné změny:</span><span class="sxs-lookup"><span data-stu-id="a91a4-105">The following are the detailed changes:</span></span>  
  
-   <span data-ttu-id="a91a4-106">Hodnota `Version` položku v `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` klíče se změnila na `4.6.` *xxxxx* pro rozhraní .NET Framework 4.6 a jeho verze bodu a `4.7.` *xxxxx* pro. NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="a91a4-106">The value of the `Version` entry in the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` key has changed to `4.6.`*xxxxx* for the .NET Framework 4.6 and its point releases, and to `4.7.`*xxxxx* for the .NET Framework 4.7.</span></span> <span data-ttu-id="a91a4-107">V rozhraní .NET Framework 4.5 a 4.5.1, 4.5.2, měl formát `4.5.` *xxxxx*.</span><span class="sxs-lookup"><span data-stu-id="a91a4-107">In the .NET Framework 4.5, 4.5.1, and 4.5.2, it had the format `4.5.`*xxxxx*.</span></span>  
  
-   <span data-ttu-id="a91a4-108">Správa verzí souborů a produktu pro soubory rozhraní .NET Framework změnil ze starší verze schéma `4.0.30319.x` k `4.6.X.0` pro rozhraní .NET Framework 4.6 a jeho verze bodu a `4.7.X.0` 4.7 rozhraní .NET Framework a jeho bod uvolní.</span><span class="sxs-lookup"><span data-stu-id="a91a4-108">The file and product versioning for .NET Framework files has changed from the earlier versioning scheme of `4.0.30319.x` to `4.6.X.0` for the .NET Framework 4.6 and its point releases, and to `4.7.X.0` for the .NET Framework 4.7 and its point releases.</span></span> <span data-ttu-id="a91a4-109">Zobrazí se tyto nové hodnoty při zobrazení souboru **vlastnosti** po pravým tlačítkem myši na soubor.</span><span class="sxs-lookup"><span data-stu-id="a91a4-109">You can see these new values when you view the file's **Properties** after right-clicking on a file.</span></span>  
  
-   <span data-ttu-id="a91a4-110"><xref:System.Reflection.AssemblyFileVersionAttribute> a <xref:System.Reflection.AssemblyInformationalVersionAttribute> atributy pro spravovaná sestavení mít <xref:System.Version> hodnoty ve formuláři `4.6.X.0` pro rozhraní .NET Framework 4.6 a jeho verze bodu a `4.7.X.0` pro 4.7 rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a91a4-110">The <xref:System.Reflection.AssemblyFileVersionAttribute> and <xref:System.Reflection.AssemblyInformationalVersionAttribute> attributes for managed assemblies have <xref:System.Version> values in the form `4.6.X.0` for the .NET Framework 4.6 and its point releases, and `4.7.X.0` for the .NET Framework 4.7.</span></span>  
  
-   <span data-ttu-id="a91a4-111">V [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], 4.6.1, 4.6.2 a 4.7, <xref:System.Environment.Version%2A?displayProperty=nameWithType> vlastnost vrací řetězec pevné verze `4.0.30319.42000`.</span><span class="sxs-lookup"><span data-stu-id="a91a4-111">In the [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], 4.6.1, 4.6.2, and 4.7, the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property returns the fixed version string `4.0.30319.42000`.</span></span> <span data-ttu-id="a91a4-112">V rozhraní .NET Framework 4, 4.5, 4.5.1 a 4.5.2, vrátí verze řetězce ve formátu `4.0.30319.xxxxx` (například "4.0.30319.18010").</span><span class="sxs-lookup"><span data-stu-id="a91a4-112">In the .NET Framework 4, 4.5, 4.5.1, and 4.5.2, it returns version strings in the format `4.0.30319.xxxxx` (for example, "4.0.30319.18010").</span></span> <span data-ttu-id="a91a4-113">Všimněte si, že nedoporučujeme trvá žádné nové závislosti kód aplikace <xref:System.Environment.Version%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a91a4-113">Note that we do not recommend application code taking any new dependency on the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property.</span></span>  
  
### <a name="handling-the-product-versioning-changes"></a><span data-ttu-id="a91a4-114">Zpracování změny Správa verzí produktu</span><span class="sxs-lookup"><span data-stu-id="a91a4-114">Handling the product versioning changes</span></span>  
 <span data-ttu-id="a91a4-115">Obecně platí aplikace by měla závisí na doporučené postupy pro zjišťování prvků jako verzi modulu runtime rozhraní .NET Framework a instalační adresář:</span><span class="sxs-lookup"><span data-stu-id="a91a4-115">In general, applications should depend on the recommended techniques for detecting such things as the runtime version of the .NET Framework and the installation directory:</span></span>  
  
-   <span data-ttu-id="a91a4-116">Pokud chcete zjistit verzi modulu runtime rozhraní .NET Framework, přečtěte si téma [postupy: určení rozhraní .NET Framework verze jsou nainstalované](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="a91a4-116">To detect the runtime version of the .NET Framework, see [How to: Determine Which .NET Framework Versions Are Installed](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span></span>  
  
-   <span data-ttu-id="a91a4-117">Pokud chcete zjistit instalační cesta pro rozhraní .NET Framework, použijte hodnotu `InstallPath` položku v `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` klíč.</span><span class="sxs-lookup"><span data-stu-id="a91a4-117">To determine the installation path for the .NET Framework, use the value of the `InstallPath` entry in the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` key.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="a91a4-118">Název podklíče je `NET Framework Setup`, nikoli `.NET Framework Setup`.</span><span class="sxs-lookup"><span data-stu-id="a91a4-118">The subkey name is `NET Framework Setup`, not `.NET Framework Setup`.</span></span>  
  
-   <span data-ttu-id="a91a4-119">Chcete-li zjistit, cesta k adresáři modulu CLR rozhraní .NET Framework, zavolejte <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="a91a4-119">To determine the directory path to the .NET Framework common language runtime, call the <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType> method.</span></span>  
  
-   <span data-ttu-id="a91a4-120">Chcete-li získat verze CLR, zavolejte <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="a91a4-120">To get the CLR version, call the <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType> method.</span></span>   <span data-ttu-id="a91a4-121">Pro rozhraní .NET Framework 4 a jeho bod uvolní (rozhraní .NET Framework 4.5, 4.5.1, 4.5.2, a [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], 4.6.1, 4.6.2 a 4.7), vrátí řetězec `v4.0.30319`.</span><span class="sxs-lookup"><span data-stu-id="a91a4-121">For the .NET Framework 4 and its point releases (the .NET Framework 4.5, 4.5.1, 4.5.2, and [!INCLUDE[net_v46](../../../includes/net-v46-md.md)], 4.6.1, 4.6.2, and 4.7), it returns the string `v4.0.30319`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a91a4-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="a91a4-122">See Also</span></span>  
 [<span data-ttu-id="a91a4-123">Změny v modulu runtime</span><span class="sxs-lookup"><span data-stu-id="a91a4-123">Runtime Changes</span></span>](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)
 
