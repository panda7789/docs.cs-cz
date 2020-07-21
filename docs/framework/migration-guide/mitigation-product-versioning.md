---
title: 'Zmírňující opatření: Správa verzí produktu'
description: V tomto článku se dozvíte, jak se v předchozích verzích změnila .NET Framework 4,6 a novější verze produktu.
ms.date: 03/30/2017
ms.assetid: 1c4de9d7-9aba-427a-8f38-0ab9bfb8f85e
ms.openlocfilehash: 442c06446e763758d3a150ee9ff884a616541c07
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475395"
---
# <a name="mitigation-product-versioning"></a><span data-ttu-id="6f347-103">Zmírňující opatření: Správa verzí produktu</span><span class="sxs-lookup"><span data-stu-id="6f347-103">Mitigation: Product Versioning</span></span>

<span data-ttu-id="6f347-104">V .NET Framework 4,6 a novějších verzích se verze produktu změnila z předchozích verzí .NET Framework (.NET Framework 4, 4,5, 4.5.1 a 4.5.2).</span><span class="sxs-lookup"><span data-stu-id="6f347-104">In the .NET Framework 4.6 and later, product versioning has changed from the previous releases of the .NET Framework (the .NET Framework 4, 4.5, 4.5.1, and 4.5.2).</span></span>

## <a name="product-versioning-changes"></a><span data-ttu-id="6f347-105">Změny verzí produktu</span><span class="sxs-lookup"><span data-stu-id="6f347-105">Product versioning changes</span></span>

<span data-ttu-id="6f347-106">Níže jsou uvedené podrobné změny:</span><span class="sxs-lookup"><span data-stu-id="6f347-106">The following are the detailed changes:</span></span>

- <span data-ttu-id="6f347-107">Hodnota `Version` položky v `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` klíči se změnila na `4.6.` *xxxxx* pro .NET Framework 4,6 a její verze a na `4.7.` *xxxxx* pro .NET Framework 4,7.</span><span class="sxs-lookup"><span data-stu-id="6f347-107">The value of the `Version` entry in the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` key has changed to `4.6.`*xxxxx* for the .NET Framework 4.6 and its point releases, and to `4.7.`*xxxxx* for the .NET Framework 4.7.</span></span> <span data-ttu-id="6f347-108">V .NET Framework 4,5, 4.5.1 a 4.5.2 má formát `4.5.` *xxxxx*.</span><span class="sxs-lookup"><span data-stu-id="6f347-108">In the .NET Framework 4.5, 4.5.1, and 4.5.2, it had the format `4.5.`*xxxxx*.</span></span>

- <span data-ttu-id="6f347-109">Verze souboru a produktu pro .NET Framework soubory se změnila ze staršího schématu správy verzí `4.0.30319.x` na `4.6.X.0` pro .NET Framework 4,6 a jeho vydání a na `4.7.X.0` pro .NET Framework 4,7 a jeho vydání.</span><span class="sxs-lookup"><span data-stu-id="6f347-109">The file and product versioning for .NET Framework files has changed from the earlier versioning scheme of `4.0.30319.x` to `4.6.X.0` for the .NET Framework 4.6 and its point releases, and to `4.7.X.0` for the .NET Framework 4.7 and its point releases.</span></span> <span data-ttu-id="6f347-110">Tyto nové hodnoty se zobrazí po kliknutí pravým tlačítkem myši na soubor po zobrazení **vlastností** souboru.</span><span class="sxs-lookup"><span data-stu-id="6f347-110">You can see these new values when you view the file's **Properties** after right-clicking on a file.</span></span>

- <span data-ttu-id="6f347-111"><xref:System.Reflection.AssemblyFileVersionAttribute>Atributy a <xref:System.Reflection.AssemblyInformationalVersionAttribute> pro spravovaná sestavení mají <xref:System.Version> hodnoty ve formátu `4.6.X.0` pro .NET Framework 4,6 a jeho vydání a `4.7.X.0` pro .NET Framework 4,7.</span><span class="sxs-lookup"><span data-stu-id="6f347-111">The <xref:System.Reflection.AssemblyFileVersionAttribute> and <xref:System.Reflection.AssemblyInformationalVersionAttribute> attributes for managed assemblies have <xref:System.Version> values in the form `4.6.X.0` for the .NET Framework 4.6 and its point releases, and `4.7.X.0` for the .NET Framework 4.7.</span></span>

- <span data-ttu-id="6f347-112">Počínaje .NET Framework 4,6 <xref:System.Environment.Version%2A?displayProperty=nameWithType> vrátí vlastnost řetězec pevné verze `4.0.30319.42000` .</span><span class="sxs-lookup"><span data-stu-id="6f347-112">Starting with .NET Framework 4.6, the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property returns the fixed version string `4.0.30319.42000`.</span></span> <span data-ttu-id="6f347-113">V .NET Framework 4, 4,5, 4.5.1 a 4.5.2 vrátí řetězce verze ve formátu `4.0.30319.xxxxx` , kde `xxxxx` je méně než 42000 (například "4.0.30319.18010").</span><span class="sxs-lookup"><span data-stu-id="6f347-113">In the .NET Framework 4, 4.5, 4.5.1, and 4.5.2, it returns version strings in the format `4.0.30319.xxxxx` where `xxxxx` is less than 42000 (for example, "4.0.30319.18010").</span></span> <span data-ttu-id="6f347-114">Všimněte si, že nedoporučujeme, aby se kód aplikace připustil jakékoli nové závislosti na <xref:System.Environment.Version%2A?displayProperty=nameWithType> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6f347-114">Note that we do not recommend application code taking any new dependency on the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property.</span></span>

### <a name="handling-the-product-versioning-changes"></a><span data-ttu-id="6f347-115">Zpracování změn verzí produktu</span><span class="sxs-lookup"><span data-stu-id="6f347-115">Handling the product versioning changes</span></span>

<span data-ttu-id="6f347-116">Obecně platí, že by aplikace měly záviset na doporučených technikách zjišťování, jako je běhová verze .NET Framework a instalační adresář:</span><span class="sxs-lookup"><span data-stu-id="6f347-116">In general, applications should depend on the recommended techniques for detecting such things as the runtime version of the .NET Framework and the installation directory:</span></span>

- <span data-ttu-id="6f347-117">Chcete-li zjistit verzi modulu runtime .NET Framework, přečtěte si téma [How to: Určete, které verze .NET Framework jsou nainstalovány](how-to-determine-which-versions-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="6f347-117">To detect the runtime version of the .NET Framework, see [How to: Determine Which .NET Framework Versions Are Installed](how-to-determine-which-versions-are-installed.md).</span></span>

- <span data-ttu-id="6f347-118">Chcete-li určit instalační cestu pro .NET Framework, použijte hodnotu `InstallPath` položky v `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` klíči.</span><span class="sxs-lookup"><span data-stu-id="6f347-118">To determine the installation path for the .NET Framework, use the value of the `InstallPath` entry in the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` key.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="6f347-119">Název podklíče není `NET Framework Setup` `.NET Framework Setup` .</span><span class="sxs-lookup"><span data-stu-id="6f347-119">The subkey name is `NET Framework Setup`, not `.NET Framework Setup`.</span></span>

- <span data-ttu-id="6f347-120">Chcete-li určit cestu k adresáři .NET Framework modulu CLR (Common Language Runtime), zavolejte <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType> metodu.</span><span class="sxs-lookup"><span data-stu-id="6f347-120">To determine the directory path to the .NET Framework common language runtime, call the <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType> method.</span></span>

- <span data-ttu-id="6f347-121">Chcete-li získat verzi CLR, zavolejte <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType> metodu.</span><span class="sxs-lookup"><span data-stu-id="6f347-121">To get the CLR version, call the <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType> method.</span></span>   <span data-ttu-id="6f347-122">Pro .NET Framework 4 a jeho vydání (.NET Framework 4,5, 4.5.1, 4.5.2 a .NET Framework 4,6, 4.6.1, 4.6.2 a 4,7) vrátí řetězec `v4.0.30319` .</span><span class="sxs-lookup"><span data-stu-id="6f347-122">For the .NET Framework 4 and its point releases (the .NET Framework 4.5, 4.5.1, 4.5.2, and .NET Framework 4.6, 4.6.1, 4.6.2, and 4.7), it returns the string `v4.0.30319`.</span></span>

## <a name="see-also"></a><span data-ttu-id="6f347-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="6f347-123">See also</span></span>

- [<span data-ttu-id="6f347-124">Kompatibilita aplikací</span><span class="sxs-lookup"><span data-stu-id="6f347-124">Application compatibility</span></span>](application-compatibility.md)
