---
title: 'Zmírňující opatření: Správa verzí produktu'
ms.date: 03/30/2017
ms.assetid: 1c4de9d7-9aba-427a-8f38-0ab9bfb8f85e
ms.openlocfilehash: 64a68d2b79a0a3ccdd806949ffd6cb3760974390
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73457820"
---
# <a name="mitigation-product-versioning"></a><span data-ttu-id="9731e-102">Zmírňující opatření: Správa verzí produktu</span><span class="sxs-lookup"><span data-stu-id="9731e-102">Mitigation: Product Versioning</span></span>

<span data-ttu-id="9731e-103">V rozhraní .NET Framework 4.6 a novější chod verze produktu se změnil z předchozích verzí rozhraní .NET Framework (rozhraní .NET Framework 4, 4.5, 4.5.1 a 4.5.2).</span><span class="sxs-lookup"><span data-stu-id="9731e-103">In the .NET Framework 4.6 and later, product versioning has changed from the previous releases of the .NET Framework (the .NET Framework 4, 4.5, 4.5.1, and 4.5.2).</span></span>

## <a name="product-versioning-changes"></a><span data-ttu-id="9731e-104">Změny správy verzí produktů</span><span class="sxs-lookup"><span data-stu-id="9731e-104">Product versioning changes</span></span>

<span data-ttu-id="9731e-105">Níže jsou uvedeny podrobné změny:</span><span class="sxs-lookup"><span data-stu-id="9731e-105">The following are the detailed changes:</span></span>

- <span data-ttu-id="9731e-106">Hodnota položky `Version` v `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` klíči se `4.6.`změnila na *xxxxx* pro rozhraní .NET Framework 4.6 a jeho bodové verze a `4.7.` *xxxxx* pro rozhraní .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="9731e-106">The value of the `Version` entry in the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` key has changed to `4.6.`*xxxxx* for the .NET Framework 4.6 and its point releases, and to `4.7.`*xxxxx* for the .NET Framework 4.7.</span></span> <span data-ttu-id="9731e-107">V rozhraní .NET Framework 4.5, 4.5.1 a 4.5.2 měl formát `4.5.` *xxxxx*.</span><span class="sxs-lookup"><span data-stu-id="9731e-107">In the .NET Framework 4.5, 4.5.1, and 4.5.2, it had the format `4.5.`*xxxxx*.</span></span>

- <span data-ttu-id="9731e-108">Správa verzí souborů a produktů pro soubory rozhraní .NET Framework `4.0.30319.x` `4.6.X.0` se změnila z dřívějšího schématu správy verzí `4.7.X.0` rozhraní .NET Framework 4.6 a jejích bodových verzí a na rozhraní .NET Framework 4.7 a jeho bodové verze.</span><span class="sxs-lookup"><span data-stu-id="9731e-108">The file and product versioning for .NET Framework files has changed from the earlier versioning scheme of `4.0.30319.x` to `4.6.X.0` for the .NET Framework 4.6 and its point releases, and to `4.7.X.0` for the .NET Framework 4.7 and its point releases.</span></span> <span data-ttu-id="9731e-109">Tyto nové hodnoty můžete zobrazit při zobrazení **vlastností** souboru po kliknutí pravým tlačítkem myši na soubor.</span><span class="sxs-lookup"><span data-stu-id="9731e-109">You can see these new values when you view the file's **Properties** after right-clicking on a file.</span></span>

- <span data-ttu-id="9731e-110"><xref:System.Reflection.AssemblyFileVersionAttribute> Atributy <xref:System.Reflection.AssemblyInformationalVersionAttribute> a pro spravovaná sestavení mají <xref:System.Version> hodnoty ve formuláři `4.6.X.0` pro rozhraní .NET Framework 4.6 a jeho bodové verze a `4.7.X.0` pro rozhraní .NET Framework 4.7.</span><span class="sxs-lookup"><span data-stu-id="9731e-110">The <xref:System.Reflection.AssemblyFileVersionAttribute> and <xref:System.Reflection.AssemblyInformationalVersionAttribute> attributes for managed assemblies have <xref:System.Version> values in the form `4.6.X.0` for the .NET Framework 4.6 and its point releases, and `4.7.X.0` for the .NET Framework 4.7.</span></span>

- <span data-ttu-id="9731e-111">Počínaje rozhraním .NET Framework <xref:System.Environment.Version%2A?displayProperty=nameWithType> 4.6 vrátí `4.0.30319.42000`vlastnost řetězec pevné verze .</span><span class="sxs-lookup"><span data-stu-id="9731e-111">Starting with .NET Framework 4.6, the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property returns the fixed version string `4.0.30319.42000`.</span></span> <span data-ttu-id="9731e-112">V rozhraní .NET Framework 4, 4.5, 4.5.1 a 4.5.2 vrátí `4.0.30319.xxxxx` `xxxxx` řetězce verze ve formátu, kde je menší než 42000 (například "4.0.30319.18010").</span><span class="sxs-lookup"><span data-stu-id="9731e-112">In the .NET Framework 4, 4.5, 4.5.1, and 4.5.2, it returns version strings in the format `4.0.30319.xxxxx` where `xxxxx` is less than 42000 (for example, "4.0.30319.18010").</span></span> <span data-ttu-id="9731e-113">Všimněte si, že nedoporučujeme kód aplikace <xref:System.Environment.Version%2A?displayProperty=nameWithType> s žádnou novou závislost na vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="9731e-113">Note that we do not recommend application code taking any new dependency on the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property.</span></span>

### <a name="handling-the-product-versioning-changes"></a><span data-ttu-id="9731e-114">Zpracování změn správy verzí produktu</span><span class="sxs-lookup"><span data-stu-id="9731e-114">Handling the product versioning changes</span></span>

<span data-ttu-id="9731e-115">Obecně platí, že aplikace by měly záviset na doporučených technikách pro detekci takových věcí, jako je runtime verze rozhraní .NET Framework a instalačního adresáře:</span><span class="sxs-lookup"><span data-stu-id="9731e-115">In general, applications should depend on the recommended techniques for detecting such things as the runtime version of the .NET Framework and the installation directory:</span></span>

- <span data-ttu-id="9731e-116">Chcete-li zjistit verzi rozhraní .NET Framework za běhu, [přečtěte si postup: Určení, které verze rozhraní .NET Framework jsou nainstalovány](how-to-determine-which-versions-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="9731e-116">To detect the runtime version of the .NET Framework, see [How to: Determine Which .NET Framework Versions Are Installed](how-to-determine-which-versions-are-installed.md).</span></span>

- <span data-ttu-id="9731e-117">Chcete-li určit instalační cestu pro rozhraní .NET `InstallPath` Framework, `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` použijte hodnotu položky v klíči.</span><span class="sxs-lookup"><span data-stu-id="9731e-117">To determine the installation path for the .NET Framework, use the value of the `InstallPath` entry in the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` key.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="9731e-118">Název podklíče `NET Framework Setup`je `.NET Framework Setup`, nikoli .</span><span class="sxs-lookup"><span data-stu-id="9731e-118">The subkey name is `NET Framework Setup`, not `.NET Framework Setup`.</span></span>

- <span data-ttu-id="9731e-119">Chcete-li určit cestu k adresáři ke spuštění <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType> běžného jazyka rozhraní .NET Framework, zavolejte metodu.</span><span class="sxs-lookup"><span data-stu-id="9731e-119">To determine the directory path to the .NET Framework common language runtime, call the <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType> method.</span></span>

- <span data-ttu-id="9731e-120">Chcete-li získat clr <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType> verzi, volání metody.</span><span class="sxs-lookup"><span data-stu-id="9731e-120">To get the CLR version, call the <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType> method.</span></span>   <span data-ttu-id="9731e-121">Pro rozhraní .NET Framework 4 a jeho bodové verze (rozhraní .NET Framework 4.5, 4.5.1, 4.5.2 a .NET Framework 4.6, 4.6.1, 4.6.2 a 4.7) vrátí řetězec `v4.0.30319`.</span><span class="sxs-lookup"><span data-stu-id="9731e-121">For the .NET Framework 4 and its point releases (the .NET Framework 4.5, 4.5.1, 4.5.2, and .NET Framework 4.6, 4.6.1, 4.6.2, and 4.7), it returns the string `v4.0.30319`.</span></span>

## <a name="see-also"></a><span data-ttu-id="9731e-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="9731e-122">See also</span></span>

- [<span data-ttu-id="9731e-123">Kompatibilita aplikací</span><span class="sxs-lookup"><span data-stu-id="9731e-123">Application compatibility</span></span>](application-compatibility.md)
