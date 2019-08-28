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
ms.openlocfilehash: 8a1b4869588c8dd030cf6276969063ec99b79e33
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046587"
---
# <a name="declared-element-names-visual-basic"></a><span data-ttu-id="430ff-102">Deklarované názvy elementu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="430ff-102">Declared Element Names (Visual Basic)</span></span>
<span data-ttu-id="430ff-103">Každý deklarovaný element má název, který se označuje také jako *identifikátor*, který kód používá pro odkazování na něj.</span><span class="sxs-lookup"><span data-stu-id="430ff-103">Every declared element has a name, also called an *identifier*, which is what the code uses to refer to it.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="430ff-104">Pravidly</span><span class="sxs-lookup"><span data-stu-id="430ff-104">Rules</span></span>  
 <span data-ttu-id="430ff-105">Název elementu v Visual Basic musí splňovat následující pravidla:</span><span class="sxs-lookup"><span data-stu-id="430ff-105">An element name in Visual Basic must observe the following rules:</span></span>  
  
- <span data-ttu-id="430ff-106">Musí začínat znakem abecedy nebo podtržítkem (`_`).</span><span class="sxs-lookup"><span data-stu-id="430ff-106">It must begin with an alphabetic character or an underscore (`_`).</span></span>  
  
- <span data-ttu-id="430ff-107">Musí obsahovat jenom abecední znaky, desítkové číslice a podtržítka.</span><span class="sxs-lookup"><span data-stu-id="430ff-107">It must only contain alphabetic characters, decimal digits, and underscores.</span></span>  
  
- <span data-ttu-id="430ff-108">Musí obsahovat alespoň jeden abecední znak nebo desítkovou číslici, pokud začíná podtržítkem.</span><span class="sxs-lookup"><span data-stu-id="430ff-108">It must contain at least one alphabetic character or decimal digit if it begins with an underscore.</span></span>  
  
- <span data-ttu-id="430ff-109">Nesmí být delší než 1023 znaků.</span><span class="sxs-lookup"><span data-stu-id="430ff-109">It must not be more than 1023 characters long.</span></span>  
  
 <span data-ttu-id="430ff-110">Omezení délky 1023 znaků platí také pro celý řetězec plně kvalifikovaného názvu, například `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`.</span><span class="sxs-lookup"><span data-stu-id="430ff-110">The length limit of 1023 characters also applies to the entire string of a fully qualified name, such as `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`.</span></span>  
  
 <span data-ttu-id="430ff-111">Následující příklad ukazuje některé platné názvy elementů.</span><span class="sxs-lookup"><span data-stu-id="430ff-111">The following example shows some valid element names.</span></span>  
  
 `aB123__45`  
  
 `_567`  
  
 <span data-ttu-id="430ff-112">Následující příklad ukazuje některé neplatné názvy elementů.</span><span class="sxs-lookup"><span data-stu-id="430ff-112">The following example shows some invalid element names.</span></span> <span data-ttu-id="430ff-113">První obsahuje pouze podtržítko, druhý začíná desítkovou číslicí a třetí obsahuje neplatný znak ($).</span><span class="sxs-lookup"><span data-stu-id="430ff-113">The first contains only an underscore, the second begins with a decimal digit, and the third contains an invalid character ($).</span></span>  
  
 `' Three INVALID element names`  
  
 `_`  
  
 `12ABC`  
  
 `xyz$wv`  
  
> [!CAUTION]
> <span data-ttu-id="430ff-114">Názvy prvků začínající podtržítkem (`_`) nejsou součástí nezávislého [jazyka a jazykově nezávislých komponent](../../../../standard/language-independence-and-language-independent-components.md) (CLS), takže kód kompatibilní se specifikací CLS nemůže použít komponentu, která tyto názvy definuje.</span><span class="sxs-lookup"><span data-stu-id="430ff-114">Element names starting with an underscore (`_`) are not part of the [Language Independence and Language-Independent Components](../../../../standard/language-independence-and-language-independent-components.md) (CLS), so CLS-compliant code cannot use a component that defines such names.</span></span> <span data-ttu-id="430ff-115">Podtržítko na jakékoli jiné pozici v názvu elementu však je kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="430ff-115">However, an underscore in any other position in an element name is CLS-compliant.</span></span>  
  
### <a name="name-length-guidelines"></a><span data-ttu-id="430ff-116">Pokyny pro délku názvu</span><span class="sxs-lookup"><span data-stu-id="430ff-116">Name Length Guidelines</span></span>  
 <span data-ttu-id="430ff-117">V důsledku praktického hlediska by mělo být vaše jméno co nejkratší, přičemž stále jasně identifikujete povahu prvku.</span><span class="sxs-lookup"><span data-stu-id="430ff-117">As a practical matter, your name should be as short as possible while still clearly identifying the nature of the element.</span></span> <span data-ttu-id="430ff-118">To zlepšuje čitelnost kódu a zkracuje délku řádku a velikost zdrojového souboru.</span><span class="sxs-lookup"><span data-stu-id="430ff-118">This improves the readability of your code and reduces line length and source-file size.</span></span>  
  
 <span data-ttu-id="430ff-119">Na druhé straně vaše jméno by nemělo být tak krátké, že není dostatečně důležité, co element představuje a jak ho váš kód používá.</span><span class="sxs-lookup"><span data-stu-id="430ff-119">On the other hand, your name should not be so short that it does not adequately describe what the element represents and how your code uses it.</span></span> <span data-ttu-id="430ff-120">To je důležité pro čitelnost kódu.</span><span class="sxs-lookup"><span data-stu-id="430ff-120">This is important for the readability of your code.</span></span> <span data-ttu-id="430ff-121">Pokud se někdo jiný snaží ho pochopit, nebo pokud si ho po jeho zapsání sami napíšete, můžete vhodný název prvku ušetřit značnou dobu.</span><span class="sxs-lookup"><span data-stu-id="430ff-121">If somebody else is trying to understand it, or if you yourself are looking at it a long time after you wrote it, suitable element names can save a considerable amount of time.</span></span>  
  
## <a name="escaped-names"></a><span data-ttu-id="430ff-122">Řídicí názvy</span><span class="sxs-lookup"><span data-stu-id="430ff-122">Escaped Names</span></span>  
 <span data-ttu-id="430ff-123">Obecně platí, že název elementu nesmí odpovídat žádnému z klíčových slov rezervovaných Visual Basic, například `Case` nebo `Friend`.</span><span class="sxs-lookup"><span data-stu-id="430ff-123">Generally, an element name must not match any of the keywords reserved by Visual Basic, such as `Case` or `Friend`.</span></span> <span data-ttu-id="430ff-124">Můžete však definovat *řídicí název*, který je uzavřen hranatými závorkami (`[ ]`).</span><span class="sxs-lookup"><span data-stu-id="430ff-124">However, you can define an *escaped name*, which is enclosed by brackets (`[ ]`).</span></span> <span data-ttu-id="430ff-125">Název řídicího panelu může odpovídat libovolnému klíčovému slovu Visual Basic, protože hranaté závorky odstraňují jakoukoli nejednoznačnost.</span><span class="sxs-lookup"><span data-stu-id="430ff-125">An escaped name can match any Visual Basic keyword, since the brackets remove any ambiguity.</span></span> <span data-ttu-id="430ff-126">Hranaté závorky můžete použít také při odkazování na název později v kódu.</span><span class="sxs-lookup"><span data-stu-id="430ff-126">You also use the brackets when you refer to the name later in your code.</span></span>  
  
 <span data-ttu-id="430ff-127">Obecně byste měli používat řídicí názvy pouze v případě, že:</span><span class="sxs-lookup"><span data-stu-id="430ff-127">In general, you should use escaped names only when:</span></span>  
  
- <span data-ttu-id="430ff-128">Váš kód se migruje z předchozí verze Visual Basic, která nerezervovala klíčové slovo, které se používá jako název; ani</span><span class="sxs-lookup"><span data-stu-id="430ff-128">Your code has migrated from a previous version of Visual Basic that did not reserve the keyword being used as a name; or</span></span>  
  
- <span data-ttu-id="430ff-129">Pracujete s kódem napsaným v jiném jazyce, ve kterém dané klíčové slovo není rezervované.</span><span class="sxs-lookup"><span data-stu-id="430ff-129">You are working with code written in another language in which the given keyword is not reserved.</span></span>  
  
 <span data-ttu-id="430ff-130">V opačném případě byste měli zvážit přejmenování elementu, je-li jeho název v konfliktu s klíčovým slovem.</span><span class="sxs-lookup"><span data-stu-id="430ff-130">Otherwise, you should consider renaming the element if its name conflicts with a keyword.</span></span> <span data-ttu-id="430ff-131">Integrované vývojové prostředí (IDE) poskytuje snadný způsob, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="430ff-131">The integrated development environment (IDE) provides an easy way to do this.</span></span> <span data-ttu-id="430ff-132">Další informace najdete v tématu [](/visualstudio/vb-ide/refactoring-vb)refaktoring.</span><span class="sxs-lookup"><span data-stu-id="430ff-132">For more information, see [Refactoring](/visualstudio/vb-ide/refactoring-vb).</span></span>  
  
## <a name="case-sensitivity-in-names"></a><span data-ttu-id="430ff-133">Rozlišování velkých a malých písmen v názvech</span><span class="sxs-lookup"><span data-stu-id="430ff-133">Case Sensitivity in Names</span></span>  
 <span data-ttu-id="430ff-134">Názvy elementů v Visual Basic rozlišují malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="430ff-134">Element names in Visual Basic are case-insensitive.</span></span> <span data-ttu-id="430ff-135">To znamená, že když kompilátor Porovná dva názvy, které se liší pouze v abecedním případě, interpretuje je jako stejný název.</span><span class="sxs-lookup"><span data-stu-id="430ff-135">This means that when the compiler compares two names that differ in alphabetic case only, it interprets them as the same name.</span></span> <span data-ttu-id="430ff-136">Například zvažuje `ABC` a `abc` odkazuje na stejný deklarovaný element.</span><span class="sxs-lookup"><span data-stu-id="430ff-136">For example, it considers `ABC` and `abc` to refer to the same declared element.</span></span>  
  
 <span data-ttu-id="430ff-137">Modul CLR (Common Language Runtime) však používá vazby s rozlišováním velkých a malých písmen.</span><span class="sxs-lookup"><span data-stu-id="430ff-137">However, the common language runtime (CLR) uses case-sensitive binding.</span></span> <span data-ttu-id="430ff-138">Proto při vytváření sestavení nebo knihovny DLL a zpřístupnění pro jiná sestavení, vaše jména nebudou rozlišovat velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="430ff-138">Therefore, when you produce an assembly or a DLL and make it available to other assemblies, your names are no longer case-insensitive.</span></span> <span data-ttu-id="430ff-139">Například pokud definujete třídu s názvem `ABC`a další sestavení využívají třídu pomocí modulu CLR (Common Language Runtime), musí odkazovat na prvek jako. `ABC`</span><span class="sxs-lookup"><span data-stu-id="430ff-139">For example, if you define a class with an element called `ABC`, and other assemblies make use of your class through the common language runtime, they must refer to the element as `ABC`.</span></span> <span data-ttu-id="430ff-140">Pokud následně znovu zkompilujete třídu a změníte název prvku na `abc`, další sestavení, která používají vaši třídu, již nebudou mít přístup k tomuto prvku.</span><span class="sxs-lookup"><span data-stu-id="430ff-140">If you subsequently recompile your class and change the element's name to `abc`, the other assemblies using your class could no longer access that element.</span></span> <span data-ttu-id="430ff-141">Proto při vydání aktualizované verze sestavení byste neměli měnit abecední případ všech veřejných prvků.</span><span class="sxs-lookup"><span data-stu-id="430ff-141">Therefore, when you release an updated version of an assembly, you should not change the alphabetic case of any public elements.</span></span>  
  
## <a name="names-and-locales"></a><span data-ttu-id="430ff-142">Názvy a národní prostředí</span><span class="sxs-lookup"><span data-stu-id="430ff-142">Names and Locales</span></span>  
 <span data-ttu-id="430ff-143">Porovnání názvů je nezávislé na národním prostředí.</span><span class="sxs-lookup"><span data-stu-id="430ff-143">Comparison of names is independent of locale.</span></span> <span data-ttu-id="430ff-144">Pokud se dva názvy shodují v jednom národním prostředí, je zaručeno, že budou odpovídat ve všech národních prostředích.</span><span class="sxs-lookup"><span data-stu-id="430ff-144">If two names match in one locale, they are guaranteed to match in all locales.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="430ff-145">Viz také:</span><span class="sxs-lookup"><span data-stu-id="430ff-145">See also</span></span>

- [<span data-ttu-id="430ff-146">Deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="430ff-146">Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)
- [<span data-ttu-id="430ff-147">Deklarované charakteristiky elementů</span><span class="sxs-lookup"><span data-stu-id="430ff-147">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [<span data-ttu-id="430ff-148">Odkazy na deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="430ff-148">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [<span data-ttu-id="430ff-149">Příkazy</span><span class="sxs-lookup"><span data-stu-id="430ff-149">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)
