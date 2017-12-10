---
title: "Deklarované názvy elementu (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
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
caps.latest.revision: "27"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 59fee9eb79af86df7f01bd77c27a929ef61fcfe2
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2017
---
# <a name="declared-element-names-visual-basic"></a><span data-ttu-id="51f60-102">Deklarované názvy elementu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="51f60-102">Declared Element Names (Visual Basic)</span></span>
<span data-ttu-id="51f60-103">Každý element, deklarované má název, označované taky jako *identifikátor*, což je kód používá na ni odkazuje.</span><span class="sxs-lookup"><span data-stu-id="51f60-103">Every declared element has a name, also called an *identifier*, which is what the code uses to refer to it.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="51f60-104">Pravidla</span><span class="sxs-lookup"><span data-stu-id="51f60-104">Rules</span></span>  
 <span data-ttu-id="51f60-105">Název elementu v [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] musí odpovídat následujícím pravidlům:</span><span class="sxs-lookup"><span data-stu-id="51f60-105">An element name in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] must observe the following rules:</span></span>  
  
-   <span data-ttu-id="51f60-106">Musí začínat znakem abecedy nebo podtržítkem (`_`).</span><span class="sxs-lookup"><span data-stu-id="51f60-106">It must begin with an alphabetic character or an underscore (`_`).</span></span>  
  
-   <span data-ttu-id="51f60-107">Musí obsahovat pouze znaky abecedy, číslice desítkové soustavy a podtržítka.</span><span class="sxs-lookup"><span data-stu-id="51f60-107">It must only contain alphabetic characters, decimal digits, and underscores.</span></span>  
  
-   <span data-ttu-id="51f60-108">Musí obsahovat alespoň jeden znak abecedy nebo číslici desítkové soustavy Pokud začíná podtržítkem.</span><span class="sxs-lookup"><span data-stu-id="51f60-108">It must contain at least one alphabetic character or decimal digit if it begins with an underscore.</span></span>  
  
-   <span data-ttu-id="51f60-109">Nesmí být víc než 1023 znaků.</span><span class="sxs-lookup"><span data-stu-id="51f60-109">It must not be more than 1023 characters long.</span></span>  
  
 <span data-ttu-id="51f60-110">Maximální délku 1023 znaků platí také pro celý řetězec plně kvalifikovaný název, například `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`.</span><span class="sxs-lookup"><span data-stu-id="51f60-110">The length limit of 1023 characters also applies to the entire string of a fully qualified name, such as `outerNamespace.middleNamespace.innerNamespace.thisClass.thisElement`.</span></span>  
  
 <span data-ttu-id="51f60-111">Následující příklad ukazuje některé názvy platný element.</span><span class="sxs-lookup"><span data-stu-id="51f60-111">The following example shows some valid element names.</span></span>  
  
 `aB123__45`  
  
 `_567`  
  
 <span data-ttu-id="51f60-112">Následující příklad ukazuje některé názvy neplatný element.</span><span class="sxs-lookup"><span data-stu-id="51f60-112">The following example shows some invalid element names.</span></span> <span data-ttu-id="51f60-113">První pouze podtržítko, druhý začíná desítková číslice a třetí obsahuje neplatný znak ($).</span><span class="sxs-lookup"><span data-stu-id="51f60-113">The first contains only an underscore, the second begins with a decimal digit, and the third contains an invalid character ($).</span></span>  
  
 `' Three INVALID element names`  
  
 `_`  
  
 `12ABC`  
  
 `xyz$wv`  
  
> [!CAUTION]
>  <span data-ttu-id="51f60-114">Názvy elementů začíná podtržítkem (`_`) jsou nejsou součástí [jazyková nezávislost a jazykově nezávislé komponenty](../../../../../docs/standard/language-independence-and-language-independent-components.md) CLS (), takže kompatibilní se specifikací CLS kód nelze použít komponenty, která definuje takové názvy.</span><span class="sxs-lookup"><span data-stu-id="51f60-114">Element names starting with an underscore (`_`) are not part of the [Language Independence and Language-Independent Components](../../../../../docs/standard/language-independence-and-language-independent-components.md) (CLS), so CLS-compliant code cannot use a component that defines such names.</span></span> <span data-ttu-id="51f60-115">Podtržítkem v každém místě v název elementu je však kompatibilní se specifikací CLS.</span><span class="sxs-lookup"><span data-stu-id="51f60-115">However, an underscore in any other position in an element name is CLS-compliant.</span></span>  
  
### <a name="name-length-guidelines"></a><span data-ttu-id="51f60-116">Název délka pokyny</span><span class="sxs-lookup"><span data-stu-id="51f60-116">Name Length Guidelines</span></span>  
 <span data-ttu-id="51f60-117">Prakticky musí být název co nejkratší při identifikaci stále jasně povaha elementu.</span><span class="sxs-lookup"><span data-stu-id="51f60-117">As a practical matter, your name should be as short as possible while still clearly identifying the nature of the element.</span></span> <span data-ttu-id="51f60-118">Tím zlepšuje čitelnost kódu a snižuje velikost řádku délku a zdrojový soubor.</span><span class="sxs-lookup"><span data-stu-id="51f60-118">This improves the readability of your code and reduces line length and source-file size.</span></span>  
  
 <span data-ttu-id="51f60-119">Název nesmí být na druhé straně krátké tak, že nepopisuje adekvátní element reprezentuje a jak ji používá váš kód.</span><span class="sxs-lookup"><span data-stu-id="51f60-119">On the other hand, your name should not be so short that it does not adequately describe what the element represents and how your code uses it.</span></span> <span data-ttu-id="51f60-120">To je důležité pro čitelnost kódu.</span><span class="sxs-lookup"><span data-stu-id="51f60-120">This is important for the readability of your code.</span></span> <span data-ttu-id="51f60-121">Pokud někdo jiný pokouší porozumět, nebo pokud sami hledáte na to dlouhou dobu, po ho napsal, můžete uložit názvy vhodný elementu značné množství času.</span><span class="sxs-lookup"><span data-stu-id="51f60-121">If somebody else is trying to understand it, or if you yourself are looking at it a long time after you wrote it, suitable element names can save a considerable amount of time.</span></span>  
  
## <a name="escaped-names"></a><span data-ttu-id="51f60-122">Řídicí názvy</span><span class="sxs-lookup"><span data-stu-id="51f60-122">Escaped Names</span></span>  
 <span data-ttu-id="51f60-123">Název elementu obecně nesmí odpovídat některé z klíčových slov rezervován [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], jako například `Case` nebo `Friend`.</span><span class="sxs-lookup"><span data-stu-id="51f60-123">Generally, an element name must not match any of the keywords reserved by [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], such as `Case` or `Friend`.</span></span> <span data-ttu-id="51f60-124">Však můžete definovat *uvozené název*, který je do hranatých závorek (`[ ]`).</span><span class="sxs-lookup"><span data-stu-id="51f60-124">However, you can define an *escaped name*, which is enclosed by brackets (`[ ]`).</span></span> <span data-ttu-id="51f60-125">Uvozený název může odpovídat žádné [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] – klíčové slovo, protože hranatých závorkách odebrat všechny nejednoznačnosti.</span><span class="sxs-lookup"><span data-stu-id="51f60-125">An escaped name can match any [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] keyword, since the brackets remove any ambiguity.</span></span> <span data-ttu-id="51f60-126">Můžete také hranaté závorky odkazovat na název později v kódu.</span><span class="sxs-lookup"><span data-stu-id="51f60-126">You also use the brackets when you refer to the name later in your code.</span></span>  
  
 <span data-ttu-id="51f60-127">Obecně platí, měli byste použít řídicí názvy pouze tehdy, když:</span><span class="sxs-lookup"><span data-stu-id="51f60-127">In general, you should use escaped names only when:</span></span>  
  
-   <span data-ttu-id="51f60-128">Váš kód migroval z předchozí verze [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] , není rezervovat – klíčové slovo používá jako název; nebo</span><span class="sxs-lookup"><span data-stu-id="51f60-128">Your code has migrated from a previous version of [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] that did not reserve the keyword being used as a name; or</span></span>  
  
-   <span data-ttu-id="51f60-129">Pracujete s kódem v jiném jazyce, ve kterém není vyhrazena daným klíčovým slovem.</span><span class="sxs-lookup"><span data-stu-id="51f60-129">You are working with code written in another language in which the given keyword is not reserved.</span></span>  
  
 <span data-ttu-id="51f60-130">Jinak byste měli zvážit, přejmenování elementu, pokud jeho název je v konfliktu s klíčovým slovem.</span><span class="sxs-lookup"><span data-stu-id="51f60-130">Otherwise, you should consider renaming the element if its name conflicts with a keyword.</span></span> <span data-ttu-id="51f60-131">Integrované vývojové prostředí (IDE) poskytuje snadný způsob, jak to udělat.</span><span class="sxs-lookup"><span data-stu-id="51f60-131">The integrated development environment (IDE) provides an easy way to do this.</span></span> <span data-ttu-id="51f60-132">Další informace najdete v tématu [Refactoring](/visualstudio/vb-ide/refactoring-vb).</span><span class="sxs-lookup"><span data-stu-id="51f60-132">For more information, see [Refactoring](/visualstudio/vb-ide/refactoring-vb).</span></span>  
  
## <a name="case-sensitivity-in-names"></a><span data-ttu-id="51f60-133">Malá a velká písmena v názvech</span><span class="sxs-lookup"><span data-stu-id="51f60-133">Case Sensitivity in Names</span></span>  
 <span data-ttu-id="51f60-134">Názvy elementu v [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] se velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="51f60-134">Element names in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] are case-insensitive.</span></span> <span data-ttu-id="51f60-135">To znamená, že když kompilátor porovná dva názvy, které se liší v abecedním případě pouze, je je interpretuje jako se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="51f60-135">This means that when the compiler compares two names that differ in alphabetic case only, it interprets them as the same name.</span></span> <span data-ttu-id="51f60-136">Například považuje `ABC` a `abc` odkazovat na stejný element deklarovaný.</span><span class="sxs-lookup"><span data-stu-id="51f60-136">For example, it considers `ABC` and `abc` to refer to the same declared element.</span></span>  
  
 <span data-ttu-id="51f60-137">Modul CLR (CLR) ale používá vazba malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="51f60-137">However, the common language runtime (CLR) uses case-sensitive binding.</span></span> <span data-ttu-id="51f60-138">Proto při vytváření sestavení nebo knihovny DLL a zpřístupněte ho ostatních sestavení, názvy již nejsou velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="51f60-138">Therefore, when you produce an assembly or a DLL and make it available to other assemblies, your names are no longer case-insensitive.</span></span> <span data-ttu-id="51f60-139">Například, pokud definice třídy s prvek s názvem `ABC`, a ujistěte se, ostatních sestavení pomocí vaší třídy prostřednictvím modul common language runtime, musí odkazovat na prvek jako `ABC`.</span><span class="sxs-lookup"><span data-stu-id="51f60-139">For example, if you define a class with an element called `ABC`, and other assemblies make use of your class through the common language runtime, they must refer to the element as `ABC`.</span></span> <span data-ttu-id="51f60-140">Pokud následně znovu zkompiluje třídě a změňte název elementu `abc`, ostatních sestavení pomocí vlastní třídy již přístup tohoto prvku.</span><span class="sxs-lookup"><span data-stu-id="51f60-140">If you subsequently recompile your class and change the element's name to `abc`, the other assemblies using your class could no longer access that element.</span></span> <span data-ttu-id="51f60-141">Proto při uvolnění aktualizovanou verzi sestavení byste neměli měnit abecedním malá jakýchkoli veřejných složek.</span><span class="sxs-lookup"><span data-stu-id="51f60-141">Therefore, when you release an updated version of an assembly, you should not change the alphabetic case of any public elements.</span></span>  
  
## <a name="names-and-locales"></a><span data-ttu-id="51f60-142">Názvy a národní prostředí</span><span class="sxs-lookup"><span data-stu-id="51f60-142">Names and Locales</span></span>  
 <span data-ttu-id="51f60-143">Porovnávání názvů je nezávislé na národním prostředí.</span><span class="sxs-lookup"><span data-stu-id="51f60-143">Comparison of names is independent of locale.</span></span> <span data-ttu-id="51f60-144">Pokud se dva názvy shodují v jedné národního prostředí, jsou zaručit tak, aby odpovídaly ve všech národních prostředí.</span><span class="sxs-lookup"><span data-stu-id="51f60-144">If two names match in one locale, they are guaranteed to match in all locales.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51f60-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="51f60-145">See Also</span></span>  
 [<span data-ttu-id="51f60-146">Deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="51f60-146">Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/index.md)  
 [<span data-ttu-id="51f60-147">Deklarované charakteristiky elementu</span><span class="sxs-lookup"><span data-stu-id="51f60-147">Declared Element Characteristics</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)  
 [<span data-ttu-id="51f60-148">Odkazy na deklarované elementy</span><span class="sxs-lookup"><span data-stu-id="51f60-148">References to Declared Elements</span></span>](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [<span data-ttu-id="51f60-149">Příkazy</span><span class="sxs-lookup"><span data-stu-id="51f60-149">Statements</span></span>](../../../../visual-basic/language-reference/statements/index.md)
