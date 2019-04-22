---
title: Deklarované názvy elementu (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declared elements [Visual Basic], case sensitivity
- names [Visual Basic], Visual Basic rules
- naming conventions [Visual Basic]
- element names [Visual Basic]
- declared elements [Visual Basic], identifiers
- declarations [Visual Basic], elements
- declared elements [Visual Basic], valid names
- '[] escape characters [Visual Basic]'
- names [Visual Basic], elements
- declaration statements [Visual Basic], declared elements
- declaring elements [Visual Basic]
- identifiers [Visual Basic], declared elements
- case sensitivity, declared element names
- escape characters [Visual Basic]
- names [Visual Basic], declared elements
- declared elements [Visual Basic], about declared elements
- escaped names [Visual Basic]
- declared elements [Visual Basic], names
- names [Visual Basic], naming conventions
- identifiers [Visual Basic], elements
ms.assetid: 09d8843b-c0dc-4afe-9dab-87c439a69e66
ms.openlocfilehash: 5b1f8ccc402f7f5928a33f434664b0f28d108e6d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58814065"
---
# <a name="declared-element-names-visual-basic"></a><span data-ttu-id="318b9-102">Deklarované názvy elementu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="318b9-102">Declared Element Names (Visual Basic)</span></span>
<span data-ttu-id="318b9-103">Každý element deklarovaný má název, také označovaný jako *identifikátor*, což je tento kód použije na ni odkazuje.</span><span class="sxs-lookup"><span data-stu-id="318b9-103">Every declared element has a name, also called an *identifier*, which is what the code uses to refer to it.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="318b9-104">pravidla</span><span class="sxs-lookup"><span data-stu-id="318b9-104">Rules</span></span>  
 <span data-ttu-id="318b9-105">Název elementu v jazyce Visual Basic musí odpovídat následujícím pravidlům:</span><span class="sxs-lookup"><span data-stu-id="318b9-105">An element name in Visual Basic must observe the following rules:</span></span>  
  
-   <span data-ttu-id="318b9-106">Musí začínat znakem abecedy nebo podtržítkem (`_`).</span><span class="sxs-lookup"><span data-stu-id="318b9-106">It must begin with an alphabetic character or an underscore (`_`).</span></span>  
  
-   <span data-ttu-id="318b9-107">Musí obsahovat jenom abecední znaky, desítkové číslice a podtržítka.</span><span class="sxs-lookup"><span data-stu-id="318b9-107">It must only contain alphabetic characters, decimal digits, and underscores.</span></span>  
  
-   <span data-ttu-id="318b9-108">Pokud začíná podtržítkem musí obsahovat alespoň jeden znak abecedy nebo číslici desítkové soustavy.</span><span class="sxs-lookup"><span data-stu-id="318b9-108">It must contain at least one alphabetic character or decimal digit if it begins with an underscore.</span></span>  
  
-   <span data-ttu-id="318b9-109">Nesmí být větší než 1023 znaků.</span><span class="sxs-lookup"><span data-stu-id="318b9-109">It must not be more than 1023 characters long.</span></span>  
  
 <span data-ttu-id="318b9-110">Limit délky 1023 znaků platí také pro celý řetězec plně kvalifikovaný název, jako například `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`.</span><span class="sxs-lookup"><span data-stu-id="318b9-110">The length limit of 1023 characters also applies to the entire string of a fully qualified name, such as `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`.</span></span>  
  
 <span data-ttu-id="318b9-111">Následující příklad ukazuje některé názvy platný prvek.</span><span class="sxs-lookup"><span data-stu-id="318b9-111">The following example shows some valid element names.</span></span>  
  
 `aB123__45`  
  
 `_567`  
  
 <span data-ttu-id="318b9-112">Následující příklad ukazuje některé názvy neplatný element.</span><span class="sxs-lookup"><span data-stu-id="318b9-112">The following example shows some invalid element names.</span></span> <span data-ttu-id="318b9-113">První obsahuje pouze podtržítko, druhý začíná desítková číslice a třetí obsahuje neplatný znak ($).</span><span class="sxs-lookup"><span data-stu-id="318b9-113">The first contains only an underscore, the second begins with a decimal digit, and the third contains an invalid character ($).</span></span>  
  
 `' Three INVALID element names`  
  
 `_`  
  
 `12ABC`  
  
 `xyz$wv`  
  
> [!CAUTION]
>  <span data-ttu-id="318b9-114">Element názvy začínající podtržítkem (`_`) nejsou součástí [jazyková nezávislost a jazykově nezávislé komponenty](../../../../standard/language-independence-and-language-independent-components.md) (CLS), takže kód kompatibilní se Specifikací CLS nemůže použít komponentu, která definuje tyto názvy.</span><span class="sxs-lookup"><span data-stu-id="318b9-114">Element names starting with an underscore (`_`) are not part of the [Language Independence and Language-Independent Components](../../../../standard/language-independence-and-language-independent-components.md) (CLS), so CLS-compliant code cannot use a component that defines such names.</span></span> <span data-ttu-id="318b9-115">Podtržítka v jiné pozice v název elementu je však kompatibilní se Specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="318b9-115">However, an underscore in any other position in an element name is CLS-compliant.</span></span>  
  
### <a name="name-length-guidelines"></a><span data-ttu-id="318b9-116">Pokyny pro délka názvu</span><span class="sxs-lookup"><span data-stu-id="318b9-116">Name Length Guidelines</span></span>  
 <span data-ttu-id="318b9-117">Prakticky, váš název by měl být co nejkratší při identifikaci zjevně povaze elementu.</span><span class="sxs-lookup"><span data-stu-id="318b9-117">As a practical matter, your name should be as short as possible while still clearly identifying the nature of the element.</span></span> <span data-ttu-id="318b9-118">To zlepšuje čitelnost vašeho kódu a zmenší velikost řádku délku a zdrojový soubor.</span><span class="sxs-lookup"><span data-stu-id="318b9-118">This improves the readability of your code and reduces line length and source-file size.</span></span>  
  
 <span data-ttu-id="318b9-119">Na druhé straně váš název by neměl být tak krátký, nezabývá se odpovídajícím způsobem element představuje a jak se váš kód používá.</span><span class="sxs-lookup"><span data-stu-id="318b9-119">On the other hand, your name should not be so short that it does not adequately describe what the element represents and how your code uses it.</span></span> <span data-ttu-id="318b9-120">To je důležité pro čitelnost kódu.</span><span class="sxs-lookup"><span data-stu-id="318b9-120">This is important for the readability of your code.</span></span> <span data-ttu-id="318b9-121">Pokud někdo jiný se snaží ho chápat, nebo pokud chcete sami se na něj dlouhou dobu, po ho napsal, můžete uložit názvy elementů vhodný značné množství času.</span><span class="sxs-lookup"><span data-stu-id="318b9-121">If somebody else is trying to understand it, or if you yourself are looking at it a long time after you wrote it, suitable element names can save a considerable amount of time.</span></span>  
  
## <a name="escaped-names"></a><span data-ttu-id="318b9-122">Řídicí názvy</span><span class="sxs-lookup"><span data-stu-id="318b9-122">Escaped Names</span></span>  
 <span data-ttu-id="318b9-123">Obecně platí, název elementu nesmí shodují s některým z klíčových slov, jako vyhrazená v jazyce Visual Basic `Case` nebo `Friend`.</span><span class="sxs-lookup"><span data-stu-id="318b9-123">Generally, an element name must not match any of the keywords reserved by Visual Basic, such as `Case` or `Friend`.</span></span> <span data-ttu-id="318b9-124">Ale můžete definovat *uvozeny řídicími znaky názvu*, což je uzavřená v hranatých závorkách (`[ ]`).</span><span class="sxs-lookup"><span data-stu-id="318b9-124">However, you can define an *escaped name*, which is enclosed by brackets (`[ ]`).</span></span> <span data-ttu-id="318b9-125">Uvozený uvozovacím znakem název může odpovídat všechny klíčové slovo jazyka Visual Basic, protože závorky odebrat veškerou nejednoznačnost.</span><span class="sxs-lookup"><span data-stu-id="318b9-125">An escaped name can match any Visual Basic keyword, since the brackets remove any ambiguity.</span></span> <span data-ttu-id="318b9-126">Použijete také závorky, při odkazování na název později ve vašem kódu.</span><span class="sxs-lookup"><span data-stu-id="318b9-126">You also use the brackets when you refer to the name later in your code.</span></span>  
  
 <span data-ttu-id="318b9-127">Obecně platí, abyste používali únikové názvy pouze tehdy, když:</span><span class="sxs-lookup"><span data-stu-id="318b9-127">In general, you should use escaped names only when:</span></span>  
  
-   <span data-ttu-id="318b9-128">Váš kód se migroval z předchozí verze jazyka Visual Basic, která není rezervovat – klíčové slovo se používá jako název; nebo</span><span class="sxs-lookup"><span data-stu-id="318b9-128">Your code has migrated from a previous version of Visual Basic that did not reserve the keyword being used as a name; or</span></span>  
  
-   <span data-ttu-id="318b9-129">Pracujete s kódem v jiném jazyce, ve kterém není vyhrazena daným klíčovým slovem.</span><span class="sxs-lookup"><span data-stu-id="318b9-129">You are working with code written in another language in which the given keyword is not reserved.</span></span>  
  
 <span data-ttu-id="318b9-130">V opačném případě byste měli zvážit, pokud jeho název je v konfliktu s klíčovým slovem přejmenování elementu.</span><span class="sxs-lookup"><span data-stu-id="318b9-130">Otherwise, you should consider renaming the element if its name conflicts with a keyword.</span></span> <span data-ttu-id="318b9-131">Integrované vývojové prostředí (IDE) poskytuje snadný způsob, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="318b9-131">The integrated development environment (IDE) provides an easy way to do this.</span></span> <span data-ttu-id="318b9-132">Další informace najdete v tématu [refaktoringu](/visualstudio/vb-ide/refactoring-vb).</span><span class="sxs-lookup"><span data-stu-id="318b9-132">For more information, see [Refactoring](/visualstudio/vb-ide/refactoring-vb).</span></span>  
  
## <a name="case-sensitivity-in-names"></a><span data-ttu-id="318b9-133">Rozlišování velikosti písmen v názvech</span><span class="sxs-lookup"><span data-stu-id="318b9-133">Case Sensitivity in Names</span></span>  
 <span data-ttu-id="318b9-134">Názvy elementů v jazyce Visual Basic jsou malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="318b9-134">Element names in Visual Basic are case-insensitive.</span></span> <span data-ttu-id="318b9-135">To znamená, že když kompilátor porovná dva názvy, které se liší abecední pouze velikostí písmen, to je interpretuje jako se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="318b9-135">This means that when the compiler compares two names that differ in alphabetic case only, it interprets them as the same name.</span></span> <span data-ttu-id="318b9-136">Například považuje `ABC` a `abc` odkazovat na stejný element deklarovaný.</span><span class="sxs-lookup"><span data-stu-id="318b9-136">For example, it considers `ABC` and `abc` to refer to the same declared element.</span></span>  
  
 <span data-ttu-id="318b9-137">Ale common language runtime (CLR) používá vazbu malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="318b9-137">However, the common language runtime (CLR) uses case-sensitive binding.</span></span> <span data-ttu-id="318b9-138">Proto se při vytvoření sestavení nebo knihovny DLL a ji dejte k dispozici pro jiná sestavení, názvy už nejsou velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="318b9-138">Therefore, when you produce an assembly or a DLL and make it available to other assemblies, your names are no longer case-insensitive.</span></span> <span data-ttu-id="318b9-139">Například pokud definujete třídu s názvem elementu `ABC`, a jiných sestavení pomocí třídy přes modul common language runtime, musí odkazovat na prvek jako `ABC`.</span><span class="sxs-lookup"><span data-stu-id="318b9-139">For example, if you define a class with an element called `ABC`, and other assemblies make use of your class through the common language runtime, they must refer to the element as `ABC`.</span></span> <span data-ttu-id="318b9-140">Pokud následně znovu zkompilovat vaší třídy a změňte název elementu na `abc`, ostatních sestavení pomocí vaší třídy by už přístup k prvku.</span><span class="sxs-lookup"><span data-stu-id="318b9-140">If you subsequently recompile your class and change the element's name to `abc`, the other assemblies using your class could no longer access that element.</span></span> <span data-ttu-id="318b9-141">Proto při uvolnění aktualizovanou verzi sestavení, byste neměli měnit abecední případ veřejné elementy.</span><span class="sxs-lookup"><span data-stu-id="318b9-141">Therefore, when you release an updated version of an assembly, you should not change the alphabetic case of any public elements.</span></span>  
  
## <a name="names-and-locales"></a><span data-ttu-id="318b9-142">Názvy a národní prostředí</span><span class="sxs-lookup"><span data-stu-id="318b9-142">Names and Locales</span></span>  
 <span data-ttu-id="318b9-143">Porovnávání názvů je nezávislý na národním prostředí.</span><span class="sxs-lookup"><span data-stu-id="318b9-143">Comparison of names is independent of locale.</span></span> <span data-ttu-id="318b9-144">Pokud se dva názvy se shodují v jedné národní prostředí, je zaručena tak, aby odpovídaly ve všech národních prostředích.</span><span class="sxs-lookup"><span data-stu-id="318b9-144">If two names match in one locale, they are guaranteed to match in all locales.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="318b9-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="318b9-145">See also</span></span>

- [<span data-ttu-id="318b9-146">Deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="318b9-146">Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)
- [<span data-ttu-id="318b9-147">Deklarované charakteristiky elementů</span><span class="sxs-lookup"><span data-stu-id="318b9-147">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [<span data-ttu-id="318b9-148">Odkazy na deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="318b9-148">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="318b9-149">Příkazy</span><span class="sxs-lookup"><span data-stu-id="318b9-149">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)
