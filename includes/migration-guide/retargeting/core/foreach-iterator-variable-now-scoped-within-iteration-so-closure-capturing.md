---
ms.openlocfilehash: 9a2d6a25a8ab1b8bf65b947557802e0805a7f826
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617198"
---
### <a name="foreach-iterator-variable-is-now-scoped-within-the-iteration-so-closure-capturing-semantics-are-different-in-c5"></a><span data-ttu-id="8b01c-101">Proměnná iterátoru foreach je teď vymezená v rámci iterace, takže se sémantika zachytávání uzávěry liší (v C# 5).</span><span class="sxs-lookup"><span data-stu-id="8b01c-101">Foreach iterator variable is now scoped within the iteration, so closure capturing semantics are different (in C#5)</span></span>

#### <a name="details"></a><span data-ttu-id="8b01c-102">Podrobnosti</span><span class="sxs-lookup"><span data-stu-id="8b01c-102">Details</span></span>

<span data-ttu-id="8b01c-103">Počínaje jazykem C# 5 (Visual Studio 2012) `foreach` jsou proměnné iterátoru vymezeny v rámci iterace.</span><span class="sxs-lookup"><span data-stu-id="8b01c-103">Beginning with C# 5 (Visual Studio 2012), `foreach` iterator variables are scoped within the iteration.</span></span> <span data-ttu-id="8b01c-104">To může způsobit přerušení v případě, že kód byl dříve v závislosti na proměnných, které nebudou zahrnuty do `foreach` ukončení.</span><span class="sxs-lookup"><span data-stu-id="8b01c-104">This can cause breaks if code was previously depending on the variables to not be included in the `foreach`'s closure.</span></span> <span data-ttu-id="8b01c-105">Příznakem této změny je, že proměnná iterátoru předaná delegátovi je považována za hodnotu, kterou má v době, kdy je delegát vytvořen, nikoli na hodnotu, která je v době volání delegáta.</span><span class="sxs-lookup"><span data-stu-id="8b01c-105">The symptom of this change is that an iterator variable passed to a delegate is treated as the value it has at the time the delegate is created, rather than the value it has at the time the delegate is invoked.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="8b01c-106">Návrh</span><span class="sxs-lookup"><span data-stu-id="8b01c-106">Suggestion</span></span>

<span data-ttu-id="8b01c-107">V ideálním případě by měl být kód aktualizován, aby bylo možné očekávat nové chování kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="8b01c-107">Ideally, code should be updated to expect the new compiler behavior.</span></span> <span data-ttu-id="8b01c-108">Pokud je vyžadována stará sémantika, může být proměnná iterátoru nahrazena samostatnou proměnnou, která je explicitně umístěna mimo rozsah smyčky.</span><span class="sxs-lookup"><span data-stu-id="8b01c-108">If the old semantics are required, the iterator variable can be replaced with a separate variable which is explicitly placed outside of the loop's scope.</span></span>

| <span data-ttu-id="8b01c-109">Name</span><span class="sxs-lookup"><span data-stu-id="8b01c-109">Name</span></span>    | <span data-ttu-id="8b01c-110">Hodnota</span><span class="sxs-lookup"><span data-stu-id="8b01c-110">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="8b01c-111">Rozsah</span><span class="sxs-lookup"><span data-stu-id="8b01c-111">Scope</span></span>   | <span data-ttu-id="8b01c-112">Hlavní</span><span class="sxs-lookup"><span data-stu-id="8b01c-112">Major</span></span>       |
| <span data-ttu-id="8b01c-113">Verze</span><span class="sxs-lookup"><span data-stu-id="8b01c-113">Version</span></span> | <span data-ttu-id="8b01c-114">4.5</span><span class="sxs-lookup"><span data-stu-id="8b01c-114">4.5</span></span>         |
| <span data-ttu-id="8b01c-115">Typ</span><span class="sxs-lookup"><span data-stu-id="8b01c-115">Type</span></span>    | <span data-ttu-id="8b01c-116">Změna cílení</span><span class="sxs-lookup"><span data-stu-id="8b01c-116">Retargeting</span></span> |
