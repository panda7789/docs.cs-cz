---
ms.openlocfilehash: c7500550cd9714a9788a7dea68af04823f000f7f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614532"
---
### <a name="stack-traces-obtained-when-using-portable-pdbs-now-include-source-file-and-line-information-if-requested"></a><span data-ttu-id="77677-101">Trasování zásobníku získané při použití přenosných soubory PDB nyní obsahuje zdrojový soubor a informace o řádku, pokud je požadováno</span><span class="sxs-lookup"><span data-stu-id="77677-101">Stack traces obtained when using portable PDBs now include source file and line information if requested</span></span>

#### <a name="details"></a><span data-ttu-id="77677-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="77677-102">Details</span></span>

<span data-ttu-id="77677-103">Počínaje .NET Framework 4.7.2, trasování zásobníku získané při použití přenosných soubory PDB zahrnují zdrojový soubor a informace o řádku, pokud je to požadováno.</span><span class="sxs-lookup"><span data-stu-id="77677-103">Starting with .NET Framework 4.7.2, stack traces obtained when using portable PDBs include source file and line information when requested.</span></span> <span data-ttu-id="77677-104">Ve verzích starších než .NET Framework 4.7.2 nebude při použití přenosného soubory PDB k dispozici informace o zdrojovém souboru a řádku, i když je výslovně požadováno.</span><span class="sxs-lookup"><span data-stu-id="77677-104">In versions prior to .NET Framework 4.7.2, source file and line information would be unavailable when using portable PDBs even if explicitly requested.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="77677-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="77677-105">Suggestion</span></span>

<span data-ttu-id="77677-106">Pro aplikace cílené na .NET Framework 4.7.2 můžete odhlásit zdrojový soubor a informace o řádku při použití přenosných soubory PDB, pokud to není žádoucí, a to tak, že do `<runtime>` části souboru přidáte následující `app.config` :</span><span class="sxs-lookup"><span data-stu-id="77677-106">For applications that target the .NET Framework 4.7.2, you can opt out of the source file and line information when using portable PDBs if it is not desirable by adding the following to the `<runtime>` section of your `app.config` file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Diagnostics.IgnorePortablePDBsInStackTraces=true" />
</runtime>
```

<span data-ttu-id="77677-107">Pro aplikace, které cílí na starší verze .NET Framework, ale běží na .NET Framework 4.7.2 nebo novějším, můžete při používání přenosných soubory PDB použít následující informace ke zdrojovému souboru a řádku, a to přidáním následujícího do `<runtime>` části `app.config` souboru:</span><span class="sxs-lookup"><span data-stu-id="77677-107">For applications that target earlier versions of the .NET Framework but run on the .NET Framework 4.7.2 or later, you can opt in to the source file and line information when using portable PDBs by adding the following to the `<runtime>` section of your `app.config` file:</span></span>

```xml
<runtime>
  <AppContextSwitchOverrides value="Switch.System.Diagnostics.IgnorePortablePDBsInStackTraces=false" />
</runtime>
```

| <span data-ttu-id="77677-108">Name</span><span class="sxs-lookup"><span data-stu-id="77677-108">Name</span></span>    | <span data-ttu-id="77677-109">Hodnota</span><span class="sxs-lookup"><span data-stu-id="77677-109">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="77677-110">Rozsah</span><span class="sxs-lookup"><span data-stu-id="77677-110">Scope</span></span>   | <span data-ttu-id="77677-111">Edge</span><span class="sxs-lookup"><span data-stu-id="77677-111">Edge</span></span>        |
| <span data-ttu-id="77677-112">Verze</span><span class="sxs-lookup"><span data-stu-id="77677-112">Version</span></span> | <span data-ttu-id="77677-113">4.7.2</span><span class="sxs-lookup"><span data-stu-id="77677-113">4.7.2</span></span>       |
| <span data-ttu-id="77677-114">Typ</span><span class="sxs-lookup"><span data-stu-id="77677-114">Type</span></span>    | <span data-ttu-id="77677-115">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="77677-115">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="77677-116">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="77677-116">Affected APIs</span></span>

- <xref:System.Diagnostics.StackTrace.%23ctor(System.Boolean)>
- <xref:System.Diagnostics.StackTrace.%23ctor(System.Exception,System.Boolean)>
- <xref:System.Diagnostics.StackTrace.%23ctor(System.Exception,System.Int32,System.Boolean)>
