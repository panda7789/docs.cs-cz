---
ms.openlocfilehash: 87013a04f7ff975e40a3c49c41c1c5acc2374066
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620077"
---
### <a name="wf-serializes-expressionsliterallttgt-datetimes-differently-now-breaks-custom-xaml-parsers"></a><span data-ttu-id="c3018-101">WF serializace výrazy. literály T literály se &lt; &gt; teď liší (přerušují vlastní analyzátory XAML).</span><span class="sxs-lookup"><span data-stu-id="c3018-101">WF serializes Expressions.Literal&lt;T&gt; DateTimes differently now (breaks custom XAML parsers)</span></span>

#### <a name="details"></a><span data-ttu-id="c3018-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="c3018-102">Details</span></span>

<span data-ttu-id="c3018-103">Přidružený <xref:System.Windows.Markup.ValueSerializer> objekt převede <xref:System.DateTime?displayProperty=fullName> objekt nebo, <xref:System.DateTimeOffset?displayProperty=fullName> jehož sekunda a <xref:System.DateTime.Millisecond?displayProperty=fullName> komponenty jsou nenulové a (pro <xref:System.DateTime?displayProperty=fullName> hodnotu), jejíž vlastnost není <xref:System.DateTime.Kind> určena pro syntaxi elementu vlastnosti místo řetězce.</span><span class="sxs-lookup"><span data-stu-id="c3018-103">The associated <xref:System.Windows.Markup.ValueSerializer> object will convert a <xref:System.DateTime?displayProperty=fullName> or <xref:System.DateTimeOffset?displayProperty=fullName> object whose Second and <xref:System.DateTime.Millisecond?displayProperty=fullName> components are non-zero and (for a <xref:System.DateTime?displayProperty=fullName> value) whose <xref:System.DateTime.Kind> property is not Unspecified to property element syntax instead of a string.</span></span> <span data-ttu-id="c3018-104">Tato změna umožňuje <xref:System.DateTime?displayProperty=fullName> , <xref:System.DateTimeOffset?displayProperty=fullName> aby hodnoty a byly kulaté Trip.</span><span class="sxs-lookup"><span data-stu-id="c3018-104">This change allows <xref:System.DateTime?displayProperty=fullName> and <xref:System.DateTimeOffset?displayProperty=fullName> values to be round-tripped.</span></span> <span data-ttu-id="c3018-105">Vlastní analyzátory XAML, které předpokládají, že vstup XAML je v syntaxi atributu, nebudou pracovat správně.</span><span class="sxs-lookup"><span data-stu-id="c3018-105">Custom XAML parsers that assume that input XAML is in the attribute syntax will not function correctly.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="c3018-106">Návrh</span><span class="sxs-lookup"><span data-stu-id="c3018-106">Suggestion</span></span>

<span data-ttu-id="c3018-107">Tato změna umožňuje <xref:System.DateTime?displayProperty=fullName> , <xref:System.DateTimeOffset?displayProperty=fullName> aby hodnoty a byly kulaté Trip.</span><span class="sxs-lookup"><span data-stu-id="c3018-107">This change allows <xref:System.DateTime?displayProperty=fullName> and <xref:System.DateTimeOffset?displayProperty=fullName> values to be round-tripped.</span></span> <span data-ttu-id="c3018-108">Vlastní analyzátory XAML, které předpokládají, že vstup XAML je v syntaxi atributu, nebudou pracovat správně.</span><span class="sxs-lookup"><span data-stu-id="c3018-108">Custom XAML parsers that assume that input XAML is in the attribute syntax will not function correctly.</span></span>

| <span data-ttu-id="c3018-109">Name</span><span class="sxs-lookup"><span data-stu-id="c3018-109">Name</span></span>    | <span data-ttu-id="c3018-110">Hodnota</span><span class="sxs-lookup"><span data-stu-id="c3018-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="c3018-111">Rozsah</span><span class="sxs-lookup"><span data-stu-id="c3018-111">Scope</span></span>   |<span data-ttu-id="c3018-112">Edge</span><span class="sxs-lookup"><span data-stu-id="c3018-112">Edge</span></span>|
|<span data-ttu-id="c3018-113">Verze</span><span class="sxs-lookup"><span data-stu-id="c3018-113">Version</span></span>|<span data-ttu-id="c3018-114">4.5</span><span class="sxs-lookup"><span data-stu-id="c3018-114">4.5</span></span>|
|<span data-ttu-id="c3018-115">Typ</span><span class="sxs-lookup"><span data-stu-id="c3018-115">Type</span></span>|<span data-ttu-id="c3018-116">Modul runtime</span><span class="sxs-lookup"><span data-stu-id="c3018-116">Runtime</span></span>|
