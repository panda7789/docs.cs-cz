---
title: "Zásady vytváření názvů jazyka Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- names [Visual Basic], Visual Basic rules
- naming conventions
- naming conventions [Visual Basic], Visual Basic
- Visual Basic code, naming conventions
- conventions [Visual Basic], Visual Basic coding
- names [Visual Basic], naming conventions
- naming conventions [Visual Basic], classes
ms.assetid: 164949a4-2a7c-4736-9d82-9c3078e2e56c
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a59139b57568810de80de764388eeffa5f8d7ac9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="visual-basic-naming-conventions"></a><span data-ttu-id="d96b6-102">Zásady vytváření názvů jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d96b6-102">Visual Basic Naming Conventions</span></span>
<span data-ttu-id="d96b6-103">Pokud zadáte název elementu v aplikaci Visual Basic, musí být první znak tohoto názvu znakem abecedy nebo podtržítkem.</span><span class="sxs-lookup"><span data-stu-id="d96b6-103">When you name an element in your Visual Basic application, the first character of that name must be an alphabetic character or an underscore.</span></span> <span data-ttu-id="d96b6-104">Upozorňujeme však, že nejsou kompatibilní s názvy počínaje podtržítkem [jazyková nezávislost a jazykově nezávislé komponenty](https://msdn.microsoft.com/library/12a7a7h3) (CLS).</span><span class="sxs-lookup"><span data-stu-id="d96b6-104">Note, however, that names beginning with an underscore are not compliant with the [Language Independence and Language-Independent Components](https://msdn.microsoft.com/library/12a7a7h3) (CLS).</span></span>  
  
 <span data-ttu-id="d96b6-105">Následující návrhy se vztahují na názvy.</span><span class="sxs-lookup"><span data-stu-id="d96b6-105">The following suggestions apply to naming.</span></span>  
  
-   <span data-ttu-id="d96b6-106">Začněte všech samostatných slov v názvu s velkým písmenem, jako v `FindLastRecord` a `RedrawMyForm`.</span><span class="sxs-lookup"><span data-stu-id="d96b6-106">Begin each separate word in a name with a capital letter, as in `FindLastRecord` and `RedrawMyForm`.</span></span>  
  
-   <span data-ttu-id="d96b6-107">Začněte funkce a metoda názvy s operaci, jako v `InitNameArray` nebo `CloseDialog`.</span><span class="sxs-lookup"><span data-stu-id="d96b6-107">Begin function and method names with a verb, as in `InitNameArray` or `CloseDialog`.</span></span>  
  
-   <span data-ttu-id="d96b6-108">Begin – třída, struktura, modulu a názvy vlastností s podstatné jméno, jako v `EmployeeName` nebo `CarAccessory`.</span><span class="sxs-lookup"><span data-stu-id="d96b6-108">Begin class, structure, module, and property names with a noun, as in `EmployeeName` or `CarAccessory`.</span></span>  
  
-   <span data-ttu-id="d96b6-109">Začněte názvy rozhraní s předponou "I", za nímž následuje spojení podstatného jména nebo frázi podstatné jméno, jako je třeba `IComponent`, nebo s přídavné jméno popisující chování rozhraní, jako je třeba `IPersistable`.</span><span class="sxs-lookup"><span data-stu-id="d96b6-109">Begin interface names with the prefix "I", followed by a noun or a noun phrase, like `IComponent`, or with an adjective describing the interface's behavior, like `IPersistable`.</span></span> <span data-ttu-id="d96b6-110">Podtržítko a nepoužíváte zkratky používejte opatrně, protože zkratky může způsobit nejasnostem.</span><span class="sxs-lookup"><span data-stu-id="d96b6-110">Do not use the underscore, and use abbreviations sparingly, because abbreviations can cause confusion.</span></span>  
  
-   <span data-ttu-id="d96b6-111">Názvy obslužné rutiny událostí začínat spojení podstatného jména popisující typ události, za nímž následuje "`EventHandler`"v přípona"`MouseEventHandler`".</span><span class="sxs-lookup"><span data-stu-id="d96b6-111">Begin event handler names with a noun describing the type of event followed by the "`EventHandler`" suffix, as in "`MouseEventHandler`".</span></span>  
  
-   <span data-ttu-id="d96b6-112">V názvech třídy argument události, zahrnout "`EventArgs`" příponu.</span><span class="sxs-lookup"><span data-stu-id="d96b6-112">In names of event argument classes, include the "`EventArgs`" suffix.</span></span>  
  
-   <span data-ttu-id="d96b6-113">Pokud událost obsahuje koncept "před" nebo "po", použijte příponu v současné době nebo minulost, jako v "`ControlAdd`"nebo"`ControlAdded`".</span><span class="sxs-lookup"><span data-stu-id="d96b6-113">If an event has a concept of "before" or "after," use a suffix in present or past tense, as in "`ControlAdd`" or "`ControlAdded`".</span></span>  
  
-   <span data-ttu-id="d96b6-114">Dlouhá nebo často používaných podmínky použijte zkratky zachovat název délky rozumné řešení, například "HTML", místo "Jazyk HTML".</span><span class="sxs-lookup"><span data-stu-id="d96b6-114">For long or frequently used terms, use abbreviations to keep name lengths reasonable, for example, "HTML", instead of "Hypertext Markup Language".</span></span> <span data-ttu-id="d96b6-115">Větší než 32 znaků názvy proměnných jsou obecně obtížné číst na nízkou rozlišení monitoru.</span><span class="sxs-lookup"><span data-stu-id="d96b6-115">In general, variable names greater than 32 characters are difficult to read on a monitor set to a low resolution.</span></span> <span data-ttu-id="d96b6-116">Taky se ujistěte, že vaše zkratky jsou konzistentní v celé aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d96b6-116">Also, make sure your abbreviations are consistent throughout the entire application.</span></span> <span data-ttu-id="d96b6-117">Náhodně přepínání v projektu mezi "HTML" a "Jazyk HTML" může vést k nejasnostem.</span><span class="sxs-lookup"><span data-stu-id="d96b6-117">Randomly switching in a project between "HTML" and "Hypertext Markup Language" can lead to confusion.</span></span>  
  
-   <span data-ttu-id="d96b6-118">Nepoužívejte názvy v informacích o vnitřní oboru, které jsou stejné jako názvy ve vnějším oboru.</span><span class="sxs-lookup"><span data-stu-id="d96b6-118">Avoid using names in an inner scope that are the same as names in an outer scope.</span></span> <span data-ttu-id="d96b6-119">Chyby může způsobit Pokud proměnnou nesprávný přistupuje.</span><span class="sxs-lookup"><span data-stu-id="d96b6-119">Errors can result if the wrong variable is accessed.</span></span> <span data-ttu-id="d96b6-120">Pokud dojde ke konfliktu mezi proměnnou a klíčového slova se stejným názvem, musí identifikovat klíčové slovo tak, že před s knihovnou příslušného typu.</span><span class="sxs-lookup"><span data-stu-id="d96b6-120">If a conflict occurs between a variable and the keyword of the same name, you must identify the keyword by preceding it with the appropriate type library.</span></span> <span data-ttu-id="d96b6-121">Například, pokud máte proměnnou s názvem `Date`, můžete použít vnitřní `Date` funkce pouze voláním <xref:System.DateTime.Date%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d96b6-121">For example, if you have a variable called `Date`, you can use the intrinsic `Date` function only by calling <xref:System.DateTime.Date%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d96b6-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="d96b6-122">See Also</span></span>  
 [<span data-ttu-id="d96b6-123">Klíčová slova jako názvy elementu v kódu</span><span class="sxs-lookup"><span data-stu-id="d96b6-123">Keywords as Element Names in Code</span></span>](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)  
 [<span data-ttu-id="d96b6-124">ME, My, MyBase a MyClass</span><span class="sxs-lookup"><span data-stu-id="d96b6-124">Me, My, MyBase, and MyClass</span></span>](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [<span data-ttu-id="d96b6-125">Deklarované názvy elementů</span><span class="sxs-lookup"><span data-stu-id="d96b6-125">Declared Element Names</span></span>](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [<span data-ttu-id="d96b6-126">Struktura programu a pravidla týkající se kódu</span><span class="sxs-lookup"><span data-stu-id="d96b6-126">Program Structure and Code Conventions</span></span>](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)  
 [<span data-ttu-id="d96b6-127">Referenční dokumentace jazyka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d96b6-127">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)
