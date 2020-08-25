---
ms.openlocfilehash: 87f9cc03f334233ef286abd11e6f5ff82d7988c2
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811341"
---
### <a name="ca1831-use-asspan-or-asmemory-instead-of-range-based-indexer"></a><span data-ttu-id="09fd5-101">CA1831 místo indexeru založeného na rozsahu použijte AsSpan nebo AsMemory.</span><span class="sxs-lookup"><span data-stu-id="09fd5-101">CA1831 Use AsSpan or AsMemory instead of Range-based indexer</span></span>

<span data-ttu-id="09fd5-102">Ve výchozím nastavení je ve výchozím nastavení povolený [CA1831](/visualstudio/code-quality/ca1831) pravidla analyzátoru kódu .NET Počínaje rozhraním .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="09fd5-102">.NET code analyzer rule [CA1831](/visualstudio/code-quality/ca1831) is enabled, by default, starting in .NET 5.0.</span></span> <span data-ttu-id="09fd5-103">Vytvoří upozornění sestavení pro jakýkoliv kód <xref:System.Range> , kde je indexer založený na řetězci použit, ale nebyla určena žádná kopie.</span><span class="sxs-lookup"><span data-stu-id="09fd5-103">It produces a build warning for any code where a <xref:System.Range>-based indexer is used on a string, but no copy was intended.</span></span>

#### <a name="change-description"></a><span data-ttu-id="09fd5-104">Popis změny</span><span class="sxs-lookup"><span data-stu-id="09fd5-104">Change description</span></span>

<span data-ttu-id="09fd5-105">Počínaje platformou .NET 5,0 obsahuje sada .NET SDK [analyzátory zdrojového kódu .NET](../../../../docs/fundamentals/productivity/code-analysis.md).</span><span class="sxs-lookup"><span data-stu-id="09fd5-105">Starting in .NET 5.0, the .NET SDK includes [.NET source code analyzers](../../../../docs/fundamentals/productivity/code-analysis.md).</span></span> <span data-ttu-id="09fd5-106">Některé z těchto pravidel je ve výchozím nastavení povolené, včetně [CA1831](/visualstudio/code-quality/ca1831).</span><span class="sxs-lookup"><span data-stu-id="09fd5-106">Several of these rules are enabled, by default, including [CA1831](/visualstudio/code-quality/ca1831).</span></span> <span data-ttu-id="09fd5-107">Pokud váš projekt obsahuje kód, který porušuje toto pravidlo a je nakonfigurován tak, aby pocházel s upozorněními jako s chybami, může tato změna poškodit vaše sestavení.</span><span class="sxs-lookup"><span data-stu-id="09fd5-107">If your project contains code that violates this rule and is configured to treat warnings as errors, this change could break your build.</span></span>

<span data-ttu-id="09fd5-108">CA1831 pravidla vyhledá instance, ve kterých <xref:System.Range> je indexer založený na řetězci použit, ale nebyla určena žádná kopie.</span><span class="sxs-lookup"><span data-stu-id="09fd5-108">Rule CA1831 finds instances where a <xref:System.Range>-based indexer is used on a string, but no copy was intended.</span></span> <span data-ttu-id="09fd5-109">Pokud <xref:System.Range> je indexer založený na řetězci použit přímo na řetězec pro vytvoření implicitního přetypování, pak je vytvořena nepotřebná kopie požadované části řetězce.</span><span class="sxs-lookup"><span data-stu-id="09fd5-109">If the <xref:System.Range>-based indexer is used directly on a string to produce an implicit cast, then an unnecessary copy of the requested portion of the string is created.</span></span> <span data-ttu-id="09fd5-110">Příklad:</span><span class="sxs-lookup"><span data-stu-id="09fd5-110">For example:</span></span>

```csharp
ReadOnlySpan<char> slice = str[1..3];
```

<span data-ttu-id="09fd5-111">CA1831 navrhuje použití <xref:System.Range> indexeru založeného na *rozsahu* řetězce místo toho.</span><span class="sxs-lookup"><span data-stu-id="09fd5-111">CA1831 suggests using the <xref:System.Range>-based indexer on a *span* of the string, instead.</span></span> <span data-ttu-id="09fd5-112">Příklad:</span><span class="sxs-lookup"><span data-stu-id="09fd5-112">For example:</span></span>

```csharp
ReadOnlySpan<char> slice = str.AsSpan()[1..3];
```

#### <a name="version-introduced"></a><span data-ttu-id="09fd5-113">Představená verze</span><span class="sxs-lookup"><span data-stu-id="09fd5-113">Version introduced</span></span>

<span data-ttu-id="09fd5-114">5,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="09fd5-114">5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="09fd5-115">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="09fd5-115">Recommended action</span></span>

- <span data-ttu-id="09fd5-116">Chcete-li opravit kód a vyhnout se zbytečnému přidělení, zavolejte <xref:System.MemoryExtensions.AsSpan(System.String)> nebo <xref:System.MemoryExtensions.AsMemory(System.String)> před použitím <xref:System.Range> indexeru založeného na.</span><span class="sxs-lookup"><span data-stu-id="09fd5-116">To correct your code and avoid unnecessary allocations, call <xref:System.MemoryExtensions.AsSpan(System.String)> or <xref:System.MemoryExtensions.AsMemory(System.String)> before using the <xref:System.Range>-based indexer.</span></span> <span data-ttu-id="09fd5-117">Příklad:</span><span class="sxs-lookup"><span data-stu-id="09fd5-117">For example:</span></span>

  ```csharp
  ReadOnlySpan<char> slice = str.AsSpan()[1..3];
  ```

- <span data-ttu-id="09fd5-118">Pokud nechcete změnit kód, můžete pravidlo zakázat nastavením jeho závažnosti na `suggestion` nebo `none` .</span><span class="sxs-lookup"><span data-stu-id="09fd5-118">If you don't want to change your code, you can disable the rule by setting its severity to `suggestion` or `none`.</span></span> <span data-ttu-id="09fd5-119">Další informace naleznete v tématu [Configure Code Analysis Rules](../../../../docs/fundamentals/productivity/configure-code-analysis-rules.md).</span><span class="sxs-lookup"><span data-stu-id="09fd5-119">For more information, see [Configure code analysis rules](../../../../docs/fundamentals/productivity/configure-code-analysis-rules.md).</span></span>

- <span data-ttu-id="09fd5-120">Pro úplné vypnutí analýzy kódu nastavte `EnableNETAnalyzers` na hodnotu `false` v souboru projektu.</span><span class="sxs-lookup"><span data-stu-id="09fd5-120">To disable code analysis completely, set `EnableNETAnalyzers` to `false` in your project file.</span></span> <span data-ttu-id="09fd5-121">Další informace najdete v tématu [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span><span class="sxs-lookup"><span data-stu-id="09fd5-121">For more information, see [EnableNETAnalyzers](../../../../docs/core/project-sdk/msbuild-props.md#enablenetanalyzers).</span></span>

#### <a name="category"></a><span data-ttu-id="09fd5-122">Kategorie</span><span class="sxs-lookup"><span data-stu-id="09fd5-122">Category</span></span>

<span data-ttu-id="09fd5-123">Analýza kódu</span><span class="sxs-lookup"><span data-stu-id="09fd5-123">Code analysis</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="09fd5-124">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="09fd5-124">Affected APIs</span></span>

- <xref:System.Range?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Range`

-->
