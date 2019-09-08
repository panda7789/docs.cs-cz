---
title: Zmírnění Správa verzí produktu
ms.date: 03/30/2017
ms.assetid: 1c4de9d7-9aba-427a-8f38-0ab9bfb8f85e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 91db9d8c6fccf75bc9025a9487517e8c55d016cc
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779206"
---
# <a name="mitigation-product-versioning"></a><span data-ttu-id="d507c-102">Zmírnění Správa verzí produktu</span><span class="sxs-lookup"><span data-stu-id="d507c-102">Mitigation: Product Versioning</span></span>

<span data-ttu-id="d507c-103">V .NET Framework 4,6 a novějších verzích se verze produktu změnila z předchozích verzí .NET Framework (.NET Framework 4, 4,5, 4.5.1 a 4.5.2).</span><span class="sxs-lookup"><span data-stu-id="d507c-103">In the .NET Framework 4.6 and later, product versioning has changed from the previous releases of the .NET Framework (the .NET Framework 4, 4.5, 4.5.1, and 4.5.2).</span></span>

## <a name="product-versioning-changes"></a><span data-ttu-id="d507c-104">Změny verzí produktu</span><span class="sxs-lookup"><span data-stu-id="d507c-104">Product versioning changes</span></span>

<span data-ttu-id="d507c-105">Níže jsou uvedené podrobné změny:</span><span class="sxs-lookup"><span data-stu-id="d507c-105">The following are the detailed changes:</span></span>

- <span data-ttu-id="d507c-106">Hodnota `Version` položky `4.7.` `4.6.` v klíči se změnila na xxxxx pro .NET Framework 4,6 a její verze a na xxxxx pro .NET Framework 4,7. `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full`</span><span class="sxs-lookup"><span data-stu-id="d507c-106">The value of the `Version` entry in the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` key has changed to `4.6.`*xxxxx* for the .NET Framework 4.6 and its point releases, and to `4.7.`*xxxxx* for the .NET Framework 4.7.</span></span> <span data-ttu-id="d507c-107">V .NET Framework 4,5, 4.5.1 a 4.5.2 má formát `4.5.` *xxxxx*.</span><span class="sxs-lookup"><span data-stu-id="d507c-107">In the .NET Framework 4.5, 4.5.1, and 4.5.2, it had the format `4.5.`*xxxxx*.</span></span>

- <span data-ttu-id="d507c-108">Verze souboru a produktu pro .NET Framework soubory se změnila ze staršího schématu `4.0.30319.x` správy verzí na `4.6.X.0` pro .NET Framework 4,6 a jeho vydání a na `4.7.X.0` pro .NET Framework 4,7 a jeho vydání.</span><span class="sxs-lookup"><span data-stu-id="d507c-108">The file and product versioning for .NET Framework files has changed from the earlier versioning scheme of `4.0.30319.x` to `4.6.X.0` for the .NET Framework 4.6 and its point releases, and to `4.7.X.0` for the .NET Framework 4.7 and its point releases.</span></span> <span data-ttu-id="d507c-109">Tyto nové hodnoty se zobrazí po kliknutí pravým tlačítkem myši na soubor po zobrazení **vlastností** souboru.</span><span class="sxs-lookup"><span data-stu-id="d507c-109">You can see these new values when you view the file's **Properties** after right-clicking on a file.</span></span>

- <span data-ttu-id="d507c-110"><xref:System.Version> `4.7.X.0` `4.6.X.0` Atributy a pro<xref:System.Reflection.AssemblyInformationalVersionAttribute> spravovaná sestavení mají hodnoty ve formátu pro .NET Framework 4,6 a jeho vydání a pro .NET Framework 4,7. <xref:System.Reflection.AssemblyFileVersionAttribute></span><span class="sxs-lookup"><span data-stu-id="d507c-110">The <xref:System.Reflection.AssemblyFileVersionAttribute> and <xref:System.Reflection.AssemblyInformationalVersionAttribute> attributes for managed assemblies have <xref:System.Version> values in the form `4.6.X.0` for the .NET Framework 4.6 and its point releases, and `4.7.X.0` for the .NET Framework 4.7.</span></span>

- <span data-ttu-id="d507c-111">Počínaje .NET Framework 4,6 <xref:System.Environment.Version%2A?displayProperty=nameWithType> vrátí vlastnost řetězec `4.0.30319.42000`pevné verze.</span><span class="sxs-lookup"><span data-stu-id="d507c-111">Starting with .NET Framework 4.6, the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property returns the fixed version string `4.0.30319.42000`.</span></span> <span data-ttu-id="d507c-112">V .NET Framework 4, 4,5, 4.5.1 a 4.5.2 vrátí řetězce verze ve formátu `4.0.30319.xxxxx` , kde `xxxxx` je méně než 42000 (například "4.0.30319.18010").</span><span class="sxs-lookup"><span data-stu-id="d507c-112">In the .NET Framework 4, 4.5, 4.5.1, and 4.5.2, it returns version strings in the format `4.0.30319.xxxxx` where `xxxxx` is less than 42000 (for example, "4.0.30319.18010").</span></span> <span data-ttu-id="d507c-113">Všimněte si, že nedoporučujeme, aby se <xref:System.Environment.Version%2A?displayProperty=nameWithType> kód aplikace připustil jakékoli nové závislosti na vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d507c-113">Note that we do not recommend application code taking any new dependency on the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property.</span></span>

### <a name="handling-the-product-versioning-changes"></a><span data-ttu-id="d507c-114">Zpracování změn verzí produktu</span><span class="sxs-lookup"><span data-stu-id="d507c-114">Handling the product versioning changes</span></span>

<span data-ttu-id="d507c-115">Obecně platí, že by aplikace měly záviset na doporučených technikách zjišťování, jako je běhová verze .NET Framework a instalační adresář:</span><span class="sxs-lookup"><span data-stu-id="d507c-115">In general, applications should depend on the recommended techniques for detecting such things as the runtime version of the .NET Framework and the installation directory:</span></span>

- <span data-ttu-id="d507c-116">Chcete-li zjistit verzi modulu runtime .NET Framework, přečtěte si téma [How to: Určete, které verze .NET Framework jsou](how-to-determine-which-versions-are-installed.md)nainstalovány.</span><span class="sxs-lookup"><span data-stu-id="d507c-116">To detect the runtime version of the .NET Framework, see [How to: Determine Which .NET Framework Versions Are Installed](how-to-determine-which-versions-are-installed.md).</span></span>

- <span data-ttu-id="d507c-117">Chcete-li určit instalační cestu pro .NET Framework, použijte hodnotu `InstallPath` položky `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` v klíči.</span><span class="sxs-lookup"><span data-stu-id="d507c-117">To determine the installation path for the .NET Framework, use the value of the `InstallPath` entry in the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` key.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="d507c-118">`NET Framework Setup` Název`.NET Framework Setup`podklíče není.</span><span class="sxs-lookup"><span data-stu-id="d507c-118">The subkey name is `NET Framework Setup`, not `.NET Framework Setup`.</span></span>

- <span data-ttu-id="d507c-119">Chcete-li určit cestu k adresáři .NET Framework modulu CLR (Common Language Runtime <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType> ), zavolejte metodu.</span><span class="sxs-lookup"><span data-stu-id="d507c-119">To determine the directory path to the .NET Framework common language runtime, call the <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType> method.</span></span>

- <span data-ttu-id="d507c-120">Chcete-li získat verzi CLR, zavolejte <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType> metodu.</span><span class="sxs-lookup"><span data-stu-id="d507c-120">To get the CLR version, call the <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType> method.</span></span>   <span data-ttu-id="d507c-121">Pro .NET Framework 4 a jeho vydání (.NET Framework 4,5, 4.5.1, 4.5.2 a .NET Framework 4,6, 4.6.1, 4.6.2 a 4,7) vrátí řetězec `v4.0.30319`.</span><span class="sxs-lookup"><span data-stu-id="d507c-121">For the .NET Framework 4 and its point releases (the .NET Framework 4.5, 4.5.1, 4.5.2, and .NET Framework 4.6, 4.6.1, 4.6.2, and 4.7), it returns the string `v4.0.30319`.</span></span>

## <a name="see-also"></a><span data-ttu-id="d507c-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d507c-122">See also</span></span>

- [<span data-ttu-id="d507c-123">Změny v modulu runtime</span><span class="sxs-lookup"><span data-stu-id="d507c-123">Runtime Changes</span></span>](runtime-changes-in-the-net-framework-4-6.md)
