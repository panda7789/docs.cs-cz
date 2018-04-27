---
title: Deklarované názvy elementu (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 27
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ad883dd8e1de419c74b5bcdb8762994e762b4cf7
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="declared-element-names-visual-basic"></a><span data-ttu-id="9a63d-102">Deklarované názvy elementu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9a63d-102">Declared Element Names (Visual Basic)</span></span>
<span data-ttu-id="9a63d-103">Každý element, deklarované má název, označované taky jako *identifikátor*, což je kód používá na ni odkazuje.</span><span class="sxs-lookup"><span data-stu-id="9a63d-103">Every declared element has a name, also called an *identifier*, which is what the code uses to refer to it.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="9a63d-104">Pravidla</span><span class="sxs-lookup"><span data-stu-id="9a63d-104">Rules</span></span>  
 <span data-ttu-id="9a63d-105">Název elementu v jazyce Visual Basic musí odpovídat následujícím pravidlům:</span><span class="sxs-lookup"><span data-stu-id="9a63d-105">An element name in Visual Basic must observe the following rules:</span></span>  
  
-   <span data-ttu-id="9a63d-106">Musí začínat znakem abecedy nebo podtržítkem (`_`).</span><span class="sxs-lookup"><span data-stu-id="9a63d-106">It must begin with an alphabetic character or an underscore (`_`).</span></span>  
  
-   <span data-ttu-id="9a63d-107">Musí obsahovat pouze znaky abecedy, číslice desítkové soustavy a podtržítka.</span><span class="sxs-lookup"><span data-stu-id="9a63d-107">It must only contain alphabetic characters, decimal digits, and underscores.</span></span>  
  
-   <span data-ttu-id="9a63d-108">Musí obsahovat alespoň jeden znak abecedy nebo číslici desítkové soustavy Pokud začíná podtržítkem.</span><span class="sxs-lookup"><span data-stu-id="9a63d-108">It must contain at least one alphabetic character or decimal digit if it begins with an underscore.</span></span>  
  
-   <span data-ttu-id="9a63d-109">Nesmí být víc než 1023 znaků.</span><span class="sxs-lookup"><span data-stu-id="9a63d-109">It must not be more than 1023 characters long.</span></span>  
  
 <span data-ttu-id="9a63d-110">Maximální délku 1023 znaků platí také pro celý řetězec plně kvalifikovaný název, například `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`.</span><span class="sxs-lookup"><span data-stu-id="9a63d-110">The length limit of 1023 characters also applies to the entire string of a fully qualified name, such as `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`.</span></span>  
  
 <span data-ttu-id="9a63d-111">Následující příklad ukazuje některé názvy platný element.</span><span class="sxs-lookup"><span data-stu-id="9a63d-111">The following example shows some valid element names.</span></span>  
  
 `aB123__45`  
  
 `_567`  
  
 <span data-ttu-id="9a63d-112">Následující příklad ukazuje některé názvy neplatný element.</span><span class="sxs-lookup"><span data-stu-id="9a63d-112">The following example shows some invalid element names.</span></span> <span data-ttu-id="9a63d-113">První pouze podtržítko, druhý začíná desítková číslice a třetí obsahuje neplatný znak ($).</span><span class="sxs-lookup"><span data-stu-id="9a63d-113">The first contains only an underscore, the second begins with a decimal digit, and the third contains an invalid character ($).</span></span>  
  
 `' Three INVALID element names`  
  
 `_`  
  
 `12ABC`  
  
 `xyz$wv`  
  
> [!CAUTION]
>  <span data-ttu-id="9a63d-114">Názvy elementů začíná podtržítkem (`_`) jsou nejsou součástí [jazyková nezávislost a jazykově nezávislé komponenty](../../../../standard/language-independence-and-language-independent-components.md) CLS (), takže kompatibilní se specifikací CLS kód nelze použít komponenty, která definuje takové názvy.</span><span class="sxs-lookup"><span data-stu-id="9a63d-114">Element names starting with an underscore (`_`) are not part of the [Language Independence and Language-Independent Components](../../../../standard/language-independence-and-language-independent-components.md) (CLS), so CLS-compliant code cannot use a component that defines such names.</span></span> <span data-ttu-id="9a63d-115">Podtržítkem v každém místě v název elementu je však kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="9a63d-115">However, an underscore in any other position in an element name is CLS-compliant.</span></span>  
  
### <a name="name-length-guidelines"></a><span data-ttu-id="9a63d-116">Název délka pokyny</span><span class="sxs-lookup"><span data-stu-id="9a63d-116">Name Length Guidelines</span></span>  
 <span data-ttu-id="9a63d-117">Prakticky musí být název co nejkratší při identifikaci stále jasně povaha elementu.</span><span class="sxs-lookup"><span data-stu-id="9a63d-117">As a practical matter, your name should be as short as possible while still clearly identifying the nature of the element.</span></span> <span data-ttu-id="9a63d-118">Tím zlepšuje čitelnost kódu a snižuje velikost řádku délku a zdrojový soubor.</span><span class="sxs-lookup"><span data-stu-id="9a63d-118">This improves the readability of your code and reduces line length and source-file size.</span></span>  
  
 <span data-ttu-id="9a63d-119">Název nesmí být na druhé straně krátké tak, že nepopisuje adekvátní element reprezentuje a jak ji používá váš kód.</span><span class="sxs-lookup"><span data-stu-id="9a63d-119">On the other hand, your name should not be so short that it does not adequately describe what the element represents and how your code uses it.</span></span> <span data-ttu-id="9a63d-120">To je důležité pro čitelnost kódu.</span><span class="sxs-lookup"><span data-stu-id="9a63d-120">This is important for the readability of your code.</span></span> <span data-ttu-id="9a63d-121">Pokud někdo jiný pokouší porozumět, nebo pokud sami hledáte na to dlouhou dobu, po ho napsal, můžete uložit názvy vhodný elementu značné množství času.</span><span class="sxs-lookup"><span data-stu-id="9a63d-121">If somebody else is trying to understand it, or if you yourself are looking at it a long time after you wrote it, suitable element names can save a considerable amount of time.</span></span>  
  
## <a name="escaped-names"></a><span data-ttu-id="9a63d-122">Řídicí názvy</span><span class="sxs-lookup"><span data-stu-id="9a63d-122">Escaped Names</span></span>  
 <span data-ttu-id="9a63d-123">Název elementu obecně nesmí odpovídat některé z klíčových slov rezervován jazyka Visual Basic, jako například `Case` nebo `Friend`.</span><span class="sxs-lookup"><span data-stu-id="9a63d-123">Generally, an element name must not match any of the keywords reserved by Visual Basic, such as `Case` or `Friend`.</span></span> <span data-ttu-id="9a63d-124">Však můžete definovat *uvozené název*, který je do hranatých závorek (`[ ]`).</span><span class="sxs-lookup"><span data-stu-id="9a63d-124">However, you can define an *escaped name*, which is enclosed by brackets (`[ ]`).</span></span> <span data-ttu-id="9a63d-125">Uvozený název může odpovídat všechny klíčové slovo jazyka Visual Basic, vzhledem k tomu, že hranatých závorkách odebrat všechny nejednoznačnosti.</span><span class="sxs-lookup"><span data-stu-id="9a63d-125">An escaped name can match any Visual Basic keyword, since the brackets remove any ambiguity.</span></span> <span data-ttu-id="9a63d-126">Můžete také hranaté závorky odkazovat na název později v kódu.</span><span class="sxs-lookup"><span data-stu-id="9a63d-126">You also use the brackets when you refer to the name later in your code.</span></span>  
  
 <span data-ttu-id="9a63d-127">Obecně platí, měli byste použít řídicí názvy pouze tehdy, když:</span><span class="sxs-lookup"><span data-stu-id="9a63d-127">In general, you should use escaped names only when:</span></span>  
  
-   <span data-ttu-id="9a63d-128">Váš kód migroval z předchozí verze jazyka Visual Basic, který není rezervovat – klíčové slovo používá jako název; nebo</span><span class="sxs-lookup"><span data-stu-id="9a63d-128">Your code has migrated from a previous version of Visual Basic that did not reserve the keyword being used as a name; or</span></span>  
  
-   <span data-ttu-id="9a63d-129">Pracujete s kódem v jiném jazyce, ve kterém není vyhrazena daným klíčovým slovem.</span><span class="sxs-lookup"><span data-stu-id="9a63d-129">You are working with code written in another language in which the given keyword is not reserved.</span></span>  
  
 <span data-ttu-id="9a63d-130">Jinak byste měli zvážit, přejmenování elementu, pokud jeho název je v konfliktu s klíčovým slovem.</span><span class="sxs-lookup"><span data-stu-id="9a63d-130">Otherwise, you should consider renaming the element if its name conflicts with a keyword.</span></span> <span data-ttu-id="9a63d-131">Integrované vývojové prostředí (IDE) poskytuje snadný způsob, jak to udělat.</span><span class="sxs-lookup"><span data-stu-id="9a63d-131">The integrated development environment (IDE) provides an easy way to do this.</span></span> <span data-ttu-id="9a63d-132">Další informace najdete v tématu [Refactoring](/visualstudio/vb-ide/refactoring-vb).</span><span class="sxs-lookup"><span data-stu-id="9a63d-132">For more information, see [Refactoring](/visualstudio/vb-ide/refactoring-vb).</span></span>  
  
## <a name="case-sensitivity-in-names"></a><span data-ttu-id="9a63d-133">Malá a velká písmena v názvech</span><span class="sxs-lookup"><span data-stu-id="9a63d-133">Case Sensitivity in Names</span></span>  
 <span data-ttu-id="9a63d-134">Názvy elementů v jazyce Visual Basic jsou velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="9a63d-134">Element names in Visual Basic are case-insensitive.</span></span> <span data-ttu-id="9a63d-135">To znamená, že když kompilátor porovná dva názvy, které se liší v abecedním případě pouze, je je interpretuje jako se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="9a63d-135">This means that when the compiler compares two names that differ in alphabetic case only, it interprets them as the same name.</span></span> <span data-ttu-id="9a63d-136">Například považuje `ABC` a `abc` odkazovat na stejný element deklarovaný.</span><span class="sxs-lookup"><span data-stu-id="9a63d-136">For example, it considers `ABC` and `abc` to refer to the same declared element.</span></span>  
  
 <span data-ttu-id="9a63d-137">Modul CLR (CLR) ale používá vazba malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="9a63d-137">However, the common language runtime (CLR) uses case-sensitive binding.</span></span> <span data-ttu-id="9a63d-138">Proto při vytváření sestavení nebo knihovny DLL a zpřístupněte ho ostatních sestavení, názvy již nejsou velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="9a63d-138">Therefore, when you produce an assembly or a DLL and make it available to other assemblies, your names are no longer case-insensitive.</span></span> <span data-ttu-id="9a63d-139">Například, pokud definice třídy s prvek s názvem `ABC`, a ujistěte se, ostatních sestavení pomocí vaší třídy prostřednictvím modul common language runtime, musí odkazovat na prvek jako `ABC`.</span><span class="sxs-lookup"><span data-stu-id="9a63d-139">For example, if you define a class with an element called `ABC`, and other assemblies make use of your class through the common language runtime, they must refer to the element as `ABC`.</span></span> <span data-ttu-id="9a63d-140">Pokud následně znovu zkompiluje třídě a změňte název elementu `abc`, ostatních sestavení pomocí vlastní třídy již přístup tohoto prvku.</span><span class="sxs-lookup"><span data-stu-id="9a63d-140">If you subsequently recompile your class and change the element's name to `abc`, the other assemblies using your class could no longer access that element.</span></span> <span data-ttu-id="9a63d-141">Proto při uvolnění aktualizovanou verzi sestavení byste neměli měnit abecedním malá jakýchkoli veřejných složek.</span><span class="sxs-lookup"><span data-stu-id="9a63d-141">Therefore, when you release an updated version of an assembly, you should not change the alphabetic case of any public elements.</span></span>  
  
## <a name="names-and-locales"></a><span data-ttu-id="9a63d-142">Názvy a národní prostředí</span><span class="sxs-lookup"><span data-stu-id="9a63d-142">Names and Locales</span></span>  
 <span data-ttu-id="9a63d-143">Porovnávání názvů je nezávislé na národním prostředí.</span><span class="sxs-lookup"><span data-stu-id="9a63d-143">Comparison of names is independent of locale.</span></span> <span data-ttu-id="9a63d-144">Pokud se dva názvy shodují v jedné národního prostředí, jsou zaručit tak, aby odpovídaly ve všech národních prostředí.</span><span class="sxs-lookup"><span data-stu-id="9a63d-144">If two names match in one locale, they are guaranteed to match in all locales.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a63d-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="9a63d-145">See Also</span></span>  
 [<span data-ttu-id="9a63d-146">Deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="9a63d-146">Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)  
 [<span data-ttu-id="9a63d-147">Deklarované charakteristiky elementů</span><span class="sxs-lookup"><span data-stu-id="9a63d-147">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [<span data-ttu-id="9a63d-148">Odkazy na deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="9a63d-148">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [<span data-ttu-id="9a63d-149">Příkazy</span><span class="sxs-lookup"><span data-stu-id="9a63d-149">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)
