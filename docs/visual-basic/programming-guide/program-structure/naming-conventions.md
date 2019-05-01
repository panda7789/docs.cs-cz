---
title: Zásady vytváření názvů jazyka Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- names [Visual Basic], Visual Basic rules
- naming conventions
- naming conventions [Visual Basic], Visual Basic
- Visual Basic code, naming conventions
- conventions [Visual Basic], Visual Basic coding
- names [Visual Basic], naming conventions
- naming conventions [Visual Basic], classes
ms.assetid: 164949a4-2a7c-4736-9d82-9c3078e2e56c
ms.openlocfilehash: 46f59403feced4baafef4662065cb7daedbeaa7b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62050373"
---
# <a name="visual-basic-naming-conventions"></a><span data-ttu-id="63023-102">Zásady vytváření názvů jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="63023-102">Visual Basic Naming Conventions</span></span>
<span data-ttu-id="63023-103">Pokud název elementu v aplikaci Visual Basic, první znak s tímto názvem musí být abecední znak nebo podtržítko.</span><span class="sxs-lookup"><span data-stu-id="63023-103">When you name an element in your Visual Basic application, the first character of that name must be an alphabetic character or an underscore.</span></span> <span data-ttu-id="63023-104">Upozorňujeme, že názvy začínající podtržítkem jsou nekompatibilní s [jazyková nezávislost a jazykově nezávislé komponenty](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span><span class="sxs-lookup"><span data-stu-id="63023-104">Note, however, that names beginning with an underscore are not compliant with the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS).</span></span>  
  
 <span data-ttu-id="63023-105">Následující doporučení platí pro pojmenování.</span><span class="sxs-lookup"><span data-stu-id="63023-105">The following suggestions apply to naming.</span></span>  
  
- <span data-ttu-id="63023-106">Začněte všech samostatných slov v názvu s velkým písmenem, stejně jako v `FindLastRecord` a `RedrawMyForm`.</span><span class="sxs-lookup"><span data-stu-id="63023-106">Begin each separate word in a name with a capital letter, as in `FindLastRecord` and `RedrawMyForm`.</span></span>  
  
- <span data-ttu-id="63023-107">Začněte názvy funkce a metody s operací, jako v `InitNameArray` nebo `CloseDialog`.</span><span class="sxs-lookup"><span data-stu-id="63023-107">Begin function and method names with a verb, as in `InitNameArray` or `CloseDialog`.</span></span>  
  
- <span data-ttu-id="63023-108">Začněte třída, struktura, modul a názvy vlastností s podstatné jméno, stejně jako v `EmployeeName` nebo `CarAccessory`.</span><span class="sxs-lookup"><span data-stu-id="63023-108">Begin class, structure, module, and property names with a noun, as in `EmployeeName` or `CarAccessory`.</span></span>  
  
- <span data-ttu-id="63023-109">Začněte názvy rozhraní s předponou "I", za nímž následuje podstatné jméno nebo fráze podstatné jméno, jako je třeba `IComponent`, nebo s přídavné popisující chování rozhraní, jako je třeba `IPersistable`.</span><span class="sxs-lookup"><span data-stu-id="63023-109">Begin interface names with the prefix "I", followed by a noun or a noun phrase, like `IComponent`, or with an adjective describing the interface's behavior, like `IPersistable`.</span></span> <span data-ttu-id="63023-110">Nepoužívají podtržítko a zkratky používejte opatrně, protože zkratky, může způsobit zmatení.</span><span class="sxs-lookup"><span data-stu-id="63023-110">Do not use the underscore, and use abbreviations sparingly, because abbreviations can cause confusion.</span></span>  
  
- <span data-ttu-id="63023-111">Názvy obslužných rutin událostí začínat podstatné jméno popisující typ události, za nímž následuje "`EventHandler`"příponu, například"`MouseEventHandler`".</span><span class="sxs-lookup"><span data-stu-id="63023-111">Begin event handler names with a noun describing the type of event followed by the "`EventHandler`" suffix, as in "`MouseEventHandler`".</span></span>  
  
- <span data-ttu-id="63023-112">V názvech tříd argument události, zahrnout "`EventArgs`" příponu.</span><span class="sxs-lookup"><span data-stu-id="63023-112">In names of event argument classes, include the "`EventArgs`" suffix.</span></span>  
  
- <span data-ttu-id="63023-113">Pokud událost obsahuje koncept "before" nebo "after", je nutné použít příponu v přítomný a minulý čas, stejně jako v "`ControlAdd`"nebo"`ControlAdded`".</span><span class="sxs-lookup"><span data-stu-id="63023-113">If an event has a concept of "before" or "after," use a suffix in present or past tense, as in "`ControlAdd`" or "`ControlAdded`".</span></span>  
  
- <span data-ttu-id="63023-114">Dlouhé nebo často používané termíny použijte zkratky zachovat název délky přiměřenou, například "HTML" místo "Jazyk HTML".</span><span class="sxs-lookup"><span data-stu-id="63023-114">For long or frequently used terms, use abbreviations to keep name lengths reasonable, for example, "HTML", instead of "Hypertext Markup Language".</span></span> <span data-ttu-id="63023-115">Obecně jsou delší než 32 znaků. názvy proměnných mohou ztížit čtení na monitoru nastavit s nízkým rozlišením.</span><span class="sxs-lookup"><span data-stu-id="63023-115">In general, variable names greater than 32 characters are difficult to read on a monitor set to a low resolution.</span></span> <span data-ttu-id="63023-116">Také ujistěte se, že vaše zkratky jsou konzistentní vzhledem k aplikacím v celé aplikaci.</span><span class="sxs-lookup"><span data-stu-id="63023-116">Also, make sure your abbreviations are consistent throughout the entire application.</span></span> <span data-ttu-id="63023-117">V projektu mezi "HTML" a "Jazyk" náhodně přepínání může vést k nejasnostem.</span><span class="sxs-lookup"><span data-stu-id="63023-117">Randomly switching in a project between "HTML" and "Hypertext Markup Language" can lead to confusion.</span></span>  
  
- <span data-ttu-id="63023-118">Nepoužívejte názvy ve vnitřním oboru, které jsou stejné jako názvy ve vnějším oboru.</span><span class="sxs-lookup"><span data-stu-id="63023-118">Avoid using names in an inner scope that are the same as names in an outer scope.</span></span> <span data-ttu-id="63023-119">K chybám může dojít, pokud nesprávné proměnnou přistupuje.</span><span class="sxs-lookup"><span data-stu-id="63023-119">Errors can result if the wrong variable is accessed.</span></span> <span data-ttu-id="63023-120">Pokud dojde ke konfliktu mezi proměnnou a klíčové slovo se stejným názvem, je nutné určit klíčového slova před s knihovnou příslušného typu.</span><span class="sxs-lookup"><span data-stu-id="63023-120">If a conflict occurs between a variable and the keyword of the same name, you must identify the keyword by preceding it with the appropriate type library.</span></span> <span data-ttu-id="63023-121">Například, pokud máte proměnnou s názvem `Date`, můžete použít vnitřní objekt `Date` funkce pouze voláním <xref:System.DateTime.Date%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="63023-121">For example, if you have a variable called `Date`, you can use the intrinsic `Date` function only by calling <xref:System.DateTime.Date%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63023-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="63023-122">See also</span></span>

- [<span data-ttu-id="63023-123">Klíčová slova jako názvy elementů v kódu</span><span class="sxs-lookup"><span data-stu-id="63023-123">Keywords as Element Names in Code</span></span>](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)
- [<span data-ttu-id="63023-124">Me, My, MyBase a MyClass</span><span class="sxs-lookup"><span data-stu-id="63023-124">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [<span data-ttu-id="63023-125">Deklarované názvy elementů</span><span class="sxs-lookup"><span data-stu-id="63023-125">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)
- [<span data-ttu-id="63023-126">Struktura programu a zásady týkající se kódu</span><span class="sxs-lookup"><span data-stu-id="63023-126">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)
- [<span data-ttu-id="63023-127">Referenční příručka jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="63023-127">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)
