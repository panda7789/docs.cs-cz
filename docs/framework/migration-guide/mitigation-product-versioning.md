---
title: 'Zmírňující opatření: Správa verzí produktu'
ms.date: 03/30/2017
ms.assetid: 1c4de9d7-9aba-427a-8f38-0ab9bfb8f85e
ms.openlocfilehash: 64a68d2b79a0a3ccdd806949ffd6cb3760974390
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73457820"
---
# <a name="mitigation-product-versioning"></a><span data-ttu-id="73656-102">Zmírňující opatření: Správa verzí produktu</span><span class="sxs-lookup"><span data-stu-id="73656-102">Mitigation: Product Versioning</span></span>

<span data-ttu-id="73656-103">V .NET Framework 4,6 a novějších verzích se verze produktu změnila z předchozích verzí .NET Framework (.NET Framework 4, 4,5, 4.5.1 a 4.5.2).</span><span class="sxs-lookup"><span data-stu-id="73656-103">In the .NET Framework 4.6 and later, product versioning has changed from the previous releases of the .NET Framework (the .NET Framework 4, 4.5, 4.5.1, and 4.5.2).</span></span>

## <a name="product-versioning-changes"></a><span data-ttu-id="73656-104">Změny verzí produktu</span><span class="sxs-lookup"><span data-stu-id="73656-104">Product versioning changes</span></span>

<span data-ttu-id="73656-105">Níže jsou uvedené podrobné změny:</span><span class="sxs-lookup"><span data-stu-id="73656-105">The following are the detailed changes:</span></span>

- <span data-ttu-id="73656-106">Hodnota položky `Version` v klíči `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` se změnila na `4.6.`*xxxxx* pro .NET Framework 4,6 a jeho vydání a na `4.7.`*xxxxx* pro .NET Framework 4,7.</span><span class="sxs-lookup"><span data-stu-id="73656-106">The value of the `Version` entry in the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` key has changed to `4.6.`*xxxxx* for the .NET Framework 4.6 and its point releases, and to `4.7.`*xxxxx* for the .NET Framework 4.7.</span></span> <span data-ttu-id="73656-107">V .NET Framework 4,5, 4.5.1 a 4.5.2 má formát `4.5.`*xxxxx*.</span><span class="sxs-lookup"><span data-stu-id="73656-107">In the .NET Framework 4.5, 4.5.1, and 4.5.2, it had the format `4.5.`*xxxxx*.</span></span>

- <span data-ttu-id="73656-108">Verze souboru a produktu pro .NET Framework se změnila ze staršího schématu verze `4.0.30319.x` na `4.6.X.0` pro .NET Framework 4,6 a jeho vydání a na `4.7.X.0` .NET Framework 4,7 a jeho vydání.</span><span class="sxs-lookup"><span data-stu-id="73656-108">The file and product versioning for .NET Framework files has changed from the earlier versioning scheme of `4.0.30319.x` to `4.6.X.0` for the .NET Framework 4.6 and its point releases, and to `4.7.X.0` for the .NET Framework 4.7 and its point releases.</span></span> <span data-ttu-id="73656-109">Tyto nové hodnoty se zobrazí po kliknutí pravým tlačítkem myši na soubor po zobrazení **vlastností** souboru.</span><span class="sxs-lookup"><span data-stu-id="73656-109">You can see these new values when you view the file's **Properties** after right-clicking on a file.</span></span>

- <span data-ttu-id="73656-110">Atributy <xref:System.Reflection.AssemblyFileVersionAttribute> a <xref:System.Reflection.AssemblyInformationalVersionAttribute> pro spravovaná sestavení mají <xref:System.Version> hodnoty ve tvaru `4.6.X.0` pro .NET Framework 4,6 a jeho vydání a `4.7.X.0` .NET Framework 4,7.</span><span class="sxs-lookup"><span data-stu-id="73656-110">The <xref:System.Reflection.AssemblyFileVersionAttribute> and <xref:System.Reflection.AssemblyInformationalVersionAttribute> attributes for managed assemblies have <xref:System.Version> values in the form `4.6.X.0` for the .NET Framework 4.6 and its point releases, and `4.7.X.0` for the .NET Framework 4.7.</span></span>

- <span data-ttu-id="73656-111">Počínaje .NET Framework 4,6 vlastnost <xref:System.Environment.Version%2A?displayProperty=nameWithType> vrací `4.0.30319.42000`řetězce pevné verze.</span><span class="sxs-lookup"><span data-stu-id="73656-111">Starting with .NET Framework 4.6, the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property returns the fixed version string `4.0.30319.42000`.</span></span> <span data-ttu-id="73656-112">V .NET Framework 4, 4,5, 4.5.1 a 4.5.2 vrátí řetězce verze ve formátu `4.0.30319.xxxxx`, kde `xxxxx` je menší než 42000 (například "4.0.30319.18010").</span><span class="sxs-lookup"><span data-stu-id="73656-112">In the .NET Framework 4, 4.5, 4.5.1, and 4.5.2, it returns version strings in the format `4.0.30319.xxxxx` where `xxxxx` is less than 42000 (for example, "4.0.30319.18010").</span></span> <span data-ttu-id="73656-113">Všimněte si, že kód aplikace nedoporučujeme mít žádnou novou závislost na vlastnosti <xref:System.Environment.Version%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="73656-113">Note that we do not recommend application code taking any new dependency on the <xref:System.Environment.Version%2A?displayProperty=nameWithType> property.</span></span>

### <a name="handling-the-product-versioning-changes"></a><span data-ttu-id="73656-114">Zpracování změn verzí produktu</span><span class="sxs-lookup"><span data-stu-id="73656-114">Handling the product versioning changes</span></span>

<span data-ttu-id="73656-115">Obecně platí, že by aplikace měly záviset na doporučených technikách zjišťování, jako je běhová verze .NET Framework a instalační adresář:</span><span class="sxs-lookup"><span data-stu-id="73656-115">In general, applications should depend on the recommended techniques for detecting such things as the runtime version of the .NET Framework and the installation directory:</span></span>

- <span data-ttu-id="73656-116">Chcete-li zjistit verzi modulu runtime .NET Framework, přečtěte si téma [How to: Určete, které verze .NET Framework jsou nainstalovány](how-to-determine-which-versions-are-installed.md).</span><span class="sxs-lookup"><span data-stu-id="73656-116">To detect the runtime version of the .NET Framework, see [How to: Determine Which .NET Framework Versions Are Installed](how-to-determine-which-versions-are-installed.md).</span></span>

- <span data-ttu-id="73656-117">Chcete-li určit instalační cestu pro .NET Framework, použijte hodnotu položky `InstallPath` v klíči `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full`.</span><span class="sxs-lookup"><span data-stu-id="73656-117">To determine the installation path for the .NET Framework, use the value of the `InstallPath` entry in the `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` key.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="73656-118">Název podklíče je `NET Framework Setup`, nikoli `.NET Framework Setup`.</span><span class="sxs-lookup"><span data-stu-id="73656-118">The subkey name is `NET Framework Setup`, not `.NET Framework Setup`.</span></span>

- <span data-ttu-id="73656-119">Chcete-li určit cestu k adresáři .NET Framework modulu CLR (Common Language Runtime), zavolejte metodu <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="73656-119">To determine the directory path to the .NET Framework common language runtime, call the <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetRuntimeDirectory%2A?displayProperty=nameWithType> method.</span></span>

- <span data-ttu-id="73656-120">Chcete-li získat verzi CLR, zavolejte metodu <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="73656-120">To get the CLR version, call the <xref:System.Runtime.InteropServices.RuntimeEnvironment.GetSystemVersion%2A?displayProperty=nameWithType> method.</span></span>   <span data-ttu-id="73656-121">Pro .NET Framework 4 a jeho vydání (.NET Framework 4,5, 4.5.1, 4.5.2 a .NET Framework 4,6, 4.6.1, 4.6.2 a 4,7) vrátí řetězec `v4.0.30319`.</span><span class="sxs-lookup"><span data-stu-id="73656-121">For the .NET Framework 4 and its point releases (the .NET Framework 4.5, 4.5.1, 4.5.2, and .NET Framework 4.6, 4.6.1, 4.6.2, and 4.7), it returns the string `v4.0.30319`.</span></span>

## <a name="see-also"></a><span data-ttu-id="73656-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="73656-122">See also</span></span>

- [<span data-ttu-id="73656-123">Kompatibilita aplikací</span><span class="sxs-lookup"><span data-stu-id="73656-123">Application compatibility</span></span>](application-compatibility.md)
