---
ms.openlocfilehash: 78faa5f4008b41bac75c94ce09a58c8227e5b485
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85614452"
---
### <a name="currentculture-and-currentuiculture-flow-across-tasks"></a><span data-ttu-id="1424a-101">Tok CurrentCulture a CurrentUICulture napříč úkoly</span><span class="sxs-lookup"><span data-stu-id="1424a-101">CurrentCulture and CurrentUICulture flow across tasks</span></span>

#### <a name="details"></a><span data-ttu-id="1424a-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="1424a-102">Details</span></span>

<span data-ttu-id="1424a-103">Počínaje .NET Framework 4,6 <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> a <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> jsou uloženy v vlákně <xref:System.Threading.ExecutionContext?displayProperty=fullName> , které pokračuje v rámci asynchronních operací. To znamená, že se změny <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> nebo <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> se projeví v úlohách, které se později spouštějí asynchronně.</span><span class="sxs-lookup"><span data-stu-id="1424a-103">Beginning in the .NET Framework 4.6, <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> and <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> are stored in the thread's <xref:System.Threading.ExecutionContext?displayProperty=fullName>, which flows across asynchronous operations.This means that changes to <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> or <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> will be reflected in tasks which are later run asynchronously.</span></span> <span data-ttu-id="1424a-104">To se liší od chování předchozí verze .NET Framework (která by se obnovila <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> a <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> ve všech asynchronních úlohách).</span><span class="sxs-lookup"><span data-stu-id="1424a-104">This is different from the behavior of previous .NET Framework versions (which would reset <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> and <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> in all asynchronous tasks).</span></span>

#### <a name="suggestion"></a><span data-ttu-id="1424a-105">Návrh</span><span class="sxs-lookup"><span data-stu-id="1424a-105">Suggestion</span></span>

<span data-ttu-id="1424a-106">Aplikace ovlivněné touto změnou se mohou obejít tak, že explicitně nastaví požadovanou <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> nebo <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> jako první operaci v asynchronní úloze.</span><span class="sxs-lookup"><span data-stu-id="1424a-106">Apps affected by this change may work around it by explicitly setting the desired <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> or <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> as the first operation in an async Task.</span></span> <span data-ttu-id="1424a-107">Další možností je, že staré chování (bez toku <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> / <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> ) může být zahozeno nastavením následujícího přepínače kompatibility:</span><span class="sxs-lookup"><span data-stu-id="1424a-107">Alternatively, the old behavior (of not flowing <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName>/<xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName>) may be opted into by setting the following compatibility switch:</span></span>

```csharp
AppContext.SetSwitch("Switch.System.Globalization.NoAsyncCurrentCulture", true);
```

<span data-ttu-id="1424a-108">Tento problém vyřešila WPF v .NET Framework 4.6.2.</span><span class="sxs-lookup"><span data-stu-id="1424a-108">This issue has been fixed by WPF in .NET Framework 4.6.2.</span></span> <span data-ttu-id="1424a-109">Byla také opravena v rozhraní .NET Framework 4,6, 4.6.1 až [KB 3139549](https://support.microsoft.com/kb/3139549).</span><span class="sxs-lookup"><span data-stu-id="1424a-109">It has also been fixed in .NET Frameworks 4.6, 4.6.1 through [KB 3139549](https://support.microsoft.com/kb/3139549).</span></span> <span data-ttu-id="1424a-110">Aplikace cílené na .NET Framework 4,6 nebo novějším budou automaticky dostávat správné chování v aplikacích WPF- <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName> / <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName> ) by se zachovaly napříč operacemi dispečera.</span><span class="sxs-lookup"><span data-stu-id="1424a-110">Applications targeting .NET Framework 4.6 or later will automatically get the right behavior in WPF applications - <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=fullName>/<xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=fullName>) would be preserved across Dispatcher operations.</span></span>

| <span data-ttu-id="1424a-111">Name</span><span class="sxs-lookup"><span data-stu-id="1424a-111">Name</span></span>    | <span data-ttu-id="1424a-112">Hodnota</span><span class="sxs-lookup"><span data-stu-id="1424a-112">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="1424a-113">Rozsah</span><span class="sxs-lookup"><span data-stu-id="1424a-113">Scope</span></span>   | <span data-ttu-id="1424a-114">Vedlejší</span><span class="sxs-lookup"><span data-stu-id="1424a-114">Minor</span></span>       |
| <span data-ttu-id="1424a-115">Verze</span><span class="sxs-lookup"><span data-stu-id="1424a-115">Version</span></span> | <span data-ttu-id="1424a-116">4.6</span><span class="sxs-lookup"><span data-stu-id="1424a-116">4.6</span></span>         |
| <span data-ttu-id="1424a-117">Typ</span><span class="sxs-lookup"><span data-stu-id="1424a-117">Type</span></span>    | <span data-ttu-id="1424a-118">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="1424a-118">Retargeting</span></span> |

#### <a name="affected-apis"></a><span data-ttu-id="1424a-119">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="1424a-119">Affected APIs</span></span>

- <xref:System.Globalization.CultureInfo.CurrentCulture?displayProperty=nameWithType>
- <xref:System.Threading.Thread.CurrentCulture?displayProperty=nameWithType>
- <xref:System.Globalization.CultureInfo.CurrentUICulture?displayProperty=nameWithType>
- <xref:System.Threading.Thread.CurrentUICulture?displayProperty=nameWithType>
