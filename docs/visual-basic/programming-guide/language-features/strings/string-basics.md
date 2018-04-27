---
title: Základní informace o řetězcích v jazyce Visual Basic
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- strings [Visual Basic], Like operator
- strings [Visual Basic], Visual Basic
- strings [Visual Basic], regular expressions
ms.assetid: 5674418d-f00d-4f72-9f98-d15897793350
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4a40435b76b0eee4f4eca15d5ba1a31cc58698ab
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="string-basics-in-visual-basic"></a><span data-ttu-id="d21fd-102">Základní informace o řetězcích v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d21fd-102">String Basics in Visual Basic</span></span>
<span data-ttu-id="d21fd-103">`String` Datový typ reprezentuje řadu znaků (každý představuje zase instanci `Char` datový typ).</span><span class="sxs-lookup"><span data-stu-id="d21fd-103">The `String` data type represents a series of characters (each representing in turn an instance of the `Char` data type).</span></span> <span data-ttu-id="d21fd-104">Toto téma představuje základní koncepty řetězců v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="d21fd-104">This topic introduces the basic concepts of strings in Visual Basic.</span></span>  
  
## <a name="string-variables"></a><span data-ttu-id="d21fd-105">Řetězec proměnné</span><span class="sxs-lookup"><span data-stu-id="d21fd-105">String Variables</span></span>  
 <span data-ttu-id="d21fd-106">Instance řetězce lze přiřadit hodnotu literálu, která představuje posloupnost znaků.</span><span class="sxs-lookup"><span data-stu-id="d21fd-106">An instance of a string can be assigned a literal value that represents a series of characters.</span></span> <span data-ttu-id="d21fd-107">Příklad:</span><span class="sxs-lookup"><span data-stu-id="d21fd-107">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#63](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_1.vb)]  
  
 <span data-ttu-id="d21fd-108">A `String` proměnná může také přijmout všechny výraz, který se vyhodnotí na řetězec.</span><span class="sxs-lookup"><span data-stu-id="d21fd-108">A `String` variable can also accept any expression that evaluates to a string.</span></span> <span data-ttu-id="d21fd-109">Příklady:</span><span class="sxs-lookup"><span data-stu-id="d21fd-109">Examples are shown below:</span></span>  
  
 [!code-vb[VbVbalrStrings#64](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_2.vb)]  
  
 <span data-ttu-id="d21fd-110">Všechny literál, který je přiřazen `String` proměnná musí být uzavřena v uvozovkách ("").</span><span class="sxs-lookup"><span data-stu-id="d21fd-110">Any literal that is assigned to a `String` variable must be enclosed in quotation marks ("").</span></span> <span data-ttu-id="d21fd-111">To znamená, že uvozovky v rámci řetězec nemůže být reprezentovaná uvozovky.</span><span class="sxs-lookup"><span data-stu-id="d21fd-111">This means that a quotation mark within a string cannot be represented by a quotation mark.</span></span> <span data-ttu-id="d21fd-112">Chyba kompilátoru způsobí například následující kód:</span><span class="sxs-lookup"><span data-stu-id="d21fd-112">For example, the following code causes a compiler error:</span></span>  
  
 [!code-vb[VbVbalrStrings#65](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_3.vb)]  
  
 <span data-ttu-id="d21fd-113">Tento kód způsobí chybu, protože kompilátor ukončí řetězec po druhé uvozovky a zbytek řetězce byl interpretován jako kód.</span><span class="sxs-lookup"><span data-stu-id="d21fd-113">This code causes an error because the compiler terminates the string after the second quotation mark, and the remainder of the string is interpreted as code.</span></span> <span data-ttu-id="d21fd-114">Chcete-li tento problém vyřešit, Visual Basic interpretuje dva znaky uvozovek v řetězcový literál jako jeden znak uvozovek do řetězce.</span><span class="sxs-lookup"><span data-stu-id="d21fd-114">To solve this problem, Visual Basic interprets two quotation marks in a string literal as one quotation mark in the string.</span></span> <span data-ttu-id="d21fd-115">Následující příklad ukazuje správný způsob zahrnout znak uvozovek do řetězce:</span><span class="sxs-lookup"><span data-stu-id="d21fd-115">The following example demonstrates the correct way to include a quotation mark in a string:</span></span>  
  
 [!code-vb[VbVbalrStrings#66](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_4.vb)]  
  
 <span data-ttu-id="d21fd-116">V předchozím příkladu, dva znaky uvozovek předcházející slovo `Look` stane jeden znak uvozovek do řetězce.</span><span class="sxs-lookup"><span data-stu-id="d21fd-116">In the preceding example, the two quotation marks preceding the word `Look` become one quotation mark in the string.</span></span> <span data-ttu-id="d21fd-117">Tři uvozovky na konci řádku představují jeden znak uvozovek v řetězce a znak ukončení řetězec.</span><span class="sxs-lookup"><span data-stu-id="d21fd-117">The three quotation marks at the end of the line represent one quotation mark in the string and the string termination character.</span></span>  
  
 <span data-ttu-id="d21fd-118">Textové literály může obsahovat více řádků:</span><span class="sxs-lookup"><span data-stu-id="d21fd-118">String literals can contain multiple lines:</span></span>  
  
```vb  
Dim x = "hello  
world"  
```  
  
 <span data-ttu-id="d21fd-119">Výsledný řetězec obsahuje nový řádek pořadí, které jste použili v vaší řetězcový literál (vbcr, vbcrlf atd.).</span><span class="sxs-lookup"><span data-stu-id="d21fd-119">The resulting string contains newline sequences that you used in your string literal (vbcr, vbcrlf, etc.).</span></span>  <span data-ttu-id="d21fd-120">Už budete muset použít staré alternativní řešení:</span><span class="sxs-lookup"><span data-stu-id="d21fd-120">You no longer need to use the old workaround:</span></span>  
  
```vb  
Dim x = <xml><![CDATA[Hello  
World]]></xml>.Value  
```  
  
## <a name="characters-in-strings"></a><span data-ttu-id="d21fd-121">Znaků v řetězcích</span><span class="sxs-lookup"><span data-stu-id="d21fd-121">Characters in Strings</span></span>  
 <span data-ttu-id="d21fd-122">Řetězec si lze představit jako řadu `Char` hodnoty a `String` typ má integrované funkce, které vám umožní provádět mnoho manipulace na řetězec podobné manipulaci s povolenou pole.</span><span class="sxs-lookup"><span data-stu-id="d21fd-122">A string can be thought of as a series of `Char` values, and the `String` type has built-in functions that allow you to perform many manipulations on a string that resemble the manipulations allowed by arrays.</span></span> <span data-ttu-id="d21fd-123">Jako všechna pole v [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], jedná se o pole s nulovým základem.</span><span class="sxs-lookup"><span data-stu-id="d21fd-123">Like all array in [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], these are zero-based arrays.</span></span> <span data-ttu-id="d21fd-124">Můžete použít odkaz na konkrétní znak v řetězci prostřednictvím `Chars` vlastnost, která poskytuje přístup k znak podle umístění, ve kterých se vyskytuje v řetězci.</span><span class="sxs-lookup"><span data-stu-id="d21fd-124">You may refer to a specific character in a string through the `Chars` property, which provides a way to access a character by the position in which it appears in the string.</span></span> <span data-ttu-id="d21fd-125">Příklad:</span><span class="sxs-lookup"><span data-stu-id="d21fd-125">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#67](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_5.vb)]  
  
 <span data-ttu-id="d21fd-126">V předchozím příkladu `Chars` vlastnost řetězce, který vrátí čtvrtou znak v řetězci, který je `D`a přiřadí ji k `myChar`.</span><span class="sxs-lookup"><span data-stu-id="d21fd-126">In the above example, the `Chars` property of the string returns the fourth character in the string, which is `D`, and assigns it to `myChar`.</span></span> <span data-ttu-id="d21fd-127">Můžete také získat délka určitý řetězec prostřednictvím `Length` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="d21fd-127">You can also get the length of a particular string through the `Length` property.</span></span> <span data-ttu-id="d21fd-128">Pokud je třeba provést několik manipulace typ pole na řetězec, můžete ji převést na pole `Char` instance pomocí `ToCharArray` funkce řetězec.</span><span class="sxs-lookup"><span data-stu-id="d21fd-128">If you need to perform multiple array-type manipulations on a string, you can convert it to an array of `Char` instances using the `ToCharArray` function of the string.</span></span> <span data-ttu-id="d21fd-129">Příklad:</span><span class="sxs-lookup"><span data-stu-id="d21fd-129">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#68](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_6.vb)]  
  
 <span data-ttu-id="d21fd-130">Proměnná `myArray` nyní obsahuje pole `Char` hodnoty, každý představující znak z `myString`.</span><span class="sxs-lookup"><span data-stu-id="d21fd-130">The variable `myArray` now contains an array of `Char` values, each representing a character from `myString`.</span></span>  
  
## <a name="the-immutability-of-strings"></a><span data-ttu-id="d21fd-131">Neměnitelnosti řetězce</span><span class="sxs-lookup"><span data-stu-id="d21fd-131">The Immutability of Strings</span></span>  
 <span data-ttu-id="d21fd-132">Řetězec je *neměnné*, což znamená, že jeho hodnotu nelze změnit po jeho vytvoření.</span><span class="sxs-lookup"><span data-stu-id="d21fd-132">A string is *immutable*, which means its value cannot be changed once it has been created.</span></span> <span data-ttu-id="d21fd-133">Ale to není zabránit vám v přiřazení více než jednu hodnotu na proměnnou string.</span><span class="sxs-lookup"><span data-stu-id="d21fd-133">However, this does not prevent you from assigning more than one value to a string variable.</span></span> <span data-ttu-id="d21fd-134">Podívejte se na následující příklad:</span><span class="sxs-lookup"><span data-stu-id="d21fd-134">Consider the following example:</span></span>  
  
 [!code-vb[VbVbalrStrings#69](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_7.vb)]  
  
 <span data-ttu-id="d21fd-135">Zde proměnnou string se vytvoří, přiřadit hodnotu, a pak je jeho hodnota změněna.</span><span class="sxs-lookup"><span data-stu-id="d21fd-135">Here, a string variable is created, given a value, and then its value is changed.</span></span>  
  
 <span data-ttu-id="d21fd-136">Přesněji řečeno, v prvním řádku, instance typu `String` se vytvoří a zadány hodnota `This string is immutable`.</span><span class="sxs-lookup"><span data-stu-id="d21fd-136">More specifically, in the first line, an instance of type `String` is created and given the value `This string is immutable`.</span></span> <span data-ttu-id="d21fd-137">Na druhém řádku v příkladu se vytvoří a zadány hodnota novou instanci `Or is it?`, a proměnnou řetězce zruší její odkaz na první instanci a ukládá odkaz na novou instanci.</span><span class="sxs-lookup"><span data-stu-id="d21fd-137">In the second line of the example, a new instance is created and given the value `Or is it?`, and the string variable discards its reference to the first instance and stores a reference to the new instance.</span></span>  
  
 <span data-ttu-id="d21fd-138">Na rozdíl od jiných vnitřní datové typy `String` typem je odkaz.</span><span class="sxs-lookup"><span data-stu-id="d21fd-138">Unlike other intrinsic data types, `String` is a reference type.</span></span> <span data-ttu-id="d21fd-139">Když proměnné typu odkaz je předána jako argument funkce nebo podprogramu, odkaz na adresu paměti se uloží data předán namísto skutečné hodnoty řetězce.</span><span class="sxs-lookup"><span data-stu-id="d21fd-139">When a variable of reference type is passed as an argument to a function or subroutine, a reference to the memory address where the data is stored is passed instead of the actual value of the string.</span></span> <span data-ttu-id="d21fd-140">Proto v předchozím příkladu název proměnné zůstane stejný, ale odkazuje na nové a jinou instanci systému `String` třídy, která obsahuje novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d21fd-140">So in the previous example, the name of the variable remains the same, but it points to a new and different instance of the `String` class, which holds the new value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d21fd-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="d21fd-141">See Also</span></span>  
 [<span data-ttu-id="d21fd-142">Představení řetězců v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d21fd-142">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)  
 [<span data-ttu-id="d21fd-143">Datový typ String</span><span class="sxs-lookup"><span data-stu-id="d21fd-143">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)  
 [<span data-ttu-id="d21fd-144">Datový typ Char</span><span class="sxs-lookup"><span data-stu-id="d21fd-144">Char Data Type</span></span>](../../../../visual-basic/language-reference/data-types/char-data-type.md)  
 [<span data-ttu-id="d21fd-145">Základní operace s řetězci</span><span class="sxs-lookup"><span data-stu-id="d21fd-145">Basic String Operations</span></span>](../../../../standard/base-types/basic-string-operations.md)
