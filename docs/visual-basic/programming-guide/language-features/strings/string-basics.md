---
title: Základní informace o řetězcích v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Like operator
- strings [Visual Basic], Visual Basic
- strings [Visual Basic], regular expressions
ms.assetid: 5674418d-f00d-4f72-9f98-d15897793350
ms.openlocfilehash: 9d2d3c82f5512bc1e37e3b05086fbd364ee12298
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58820882"
---
# <a name="string-basics-in-visual-basic"></a><span data-ttu-id="ac1ca-102">Základní informace o řetězcích v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ac1ca-102">String Basics in Visual Basic</span></span>
<span data-ttu-id="ac1ca-103">`String` Datový typ představuje posloupnost znaků (nichž každý představuje zase instance `Char` datový typ).</span><span class="sxs-lookup"><span data-stu-id="ac1ca-103">The `String` data type represents a series of characters (each representing in turn an instance of the `Char` data type).</span></span> <span data-ttu-id="ac1ca-104">Toto téma představuje základní koncepty řetězců v jazyce Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ac1ca-104">This topic introduces the basic concepts of strings in Visual Basic.</span></span>  
  
## <a name="string-variables"></a><span data-ttu-id="ac1ca-105">Proměnné typu řetězec</span><span class="sxs-lookup"><span data-stu-id="ac1ca-105">String Variables</span></span>  
 <span data-ttu-id="ac1ca-106">Instance řetězce je možné přiřadit hodnotu literálu, který představuje posloupnost znaků.</span><span class="sxs-lookup"><span data-stu-id="ac1ca-106">An instance of a string can be assigned a literal value that represents a series of characters.</span></span> <span data-ttu-id="ac1ca-107">Příklad:</span><span class="sxs-lookup"><span data-stu-id="ac1ca-107">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#63)]  
  
 <span data-ttu-id="ac1ca-108">A `String` proměnnou můžete také přijmout libovolný výraz, který se vyhodnotí jako řetězec.</span><span class="sxs-lookup"><span data-stu-id="ac1ca-108">A `String` variable can also accept any expression that evaluates to a string.</span></span> <span data-ttu-id="ac1ca-109">Příklady:</span><span class="sxs-lookup"><span data-stu-id="ac1ca-109">Examples are shown below:</span></span>  
  
 [!code-vb[VbVbalrStrings#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#64)]  
  
 <span data-ttu-id="ac1ca-110">Žádné literál, který je přiřazen k `String` proměnná musí být uzavřen v uvozovkách ("").</span><span class="sxs-lookup"><span data-stu-id="ac1ca-110">Any literal that is assigned to a `String` variable must be enclosed in quotation marks ("").</span></span> <span data-ttu-id="ac1ca-111">To znamená, že uvozovka v řetězci nemůže být reprezentována znak uvozovek.</span><span class="sxs-lookup"><span data-stu-id="ac1ca-111">This means that a quotation mark within a string cannot be represented by a quotation mark.</span></span> <span data-ttu-id="ac1ca-112">Například následující kód způsobí chybu kompilátoru:</span><span class="sxs-lookup"><span data-stu-id="ac1ca-112">For example, the following code causes a compiler error:</span></span>  
  
 [!code-vb[VbVbalrStrings#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#65)]  
  
 <span data-ttu-id="ac1ca-113">Tento kód způsobí chybu, protože kompilátor ukončí řetězec po druhé uvozovky a zbývající řetězec je interpretován jako kód.</span><span class="sxs-lookup"><span data-stu-id="ac1ca-113">This code causes an error because the compiler terminates the string after the second quotation mark, and the remainder of the string is interpreted as code.</span></span> <span data-ttu-id="ac1ca-114">Pokud chcete tento problém vyřešit, Visual Basic interpretuje dvě uvozovek v řetězcovém literálu jako jeden znak uvozovek do řetězce.</span><span class="sxs-lookup"><span data-stu-id="ac1ca-114">To solve this problem, Visual Basic interprets two quotation marks in a string literal as one quotation mark in the string.</span></span> <span data-ttu-id="ac1ca-115">Následující příklad ukazuje správný způsob vložení uvozovek do řetězce:</span><span class="sxs-lookup"><span data-stu-id="ac1ca-115">The following example demonstrates the correct way to include a quotation mark in a string:</span></span>  
  
 [!code-vb[VbVbalrStrings#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#66)]  
  
 <span data-ttu-id="ac1ca-116">V předchozím příkladu dvě uvozovek předchozí slovo `Look` stát jeden uvozovka v řetězci.</span><span class="sxs-lookup"><span data-stu-id="ac1ca-116">In the preceding example, the two quotation marks preceding the word `Look` become one quotation mark in the string.</span></span> <span data-ttu-id="ac1ca-117">Tři uvozovky na konci řádku představují jeden znak uvozovek do řetězce a znak ukončení řetězce.</span><span class="sxs-lookup"><span data-stu-id="ac1ca-117">The three quotation marks at the end of the line represent one quotation mark in the string and the string termination character.</span></span>  
  
 <span data-ttu-id="ac1ca-118">Řetězcové literály může obsahovat více řádků:</span><span class="sxs-lookup"><span data-stu-id="ac1ca-118">String literals can contain multiple lines:</span></span>  
  
```vb  
Dim x = "hello  
world"  
```  
  
 <span data-ttu-id="ac1ca-119">Výsledný řetězec obsahuje sekvence znaku nového řádku, které jste použili do řetězce literálu (vbcr, vbcrlf atd.).</span><span class="sxs-lookup"><span data-stu-id="ac1ca-119">The resulting string contains newline sequences that you used in your string literal (vbcr, vbcrlf, etc.).</span></span>  <span data-ttu-id="ac1ca-120">Už nemusíte používat staré alternativní řešení:</span><span class="sxs-lookup"><span data-stu-id="ac1ca-120">You no longer need to use the old workaround:</span></span>  
  
```vb  
Dim x = <xml><![CDATA[Hello  
World]]></xml>.Value  
```  
  
## <a name="characters-in-strings"></a><span data-ttu-id="ac1ca-121">Znakům v řetězcích</span><span class="sxs-lookup"><span data-stu-id="ac1ca-121">Characters in Strings</span></span>  
 <span data-ttu-id="ac1ca-122">Řetězec si lze představit jako řadu objektů `Char` hodnoty a `String` typ má integrované funkce, které můžete provádět mnoho manipulace na řetězec, které se podobají manipulaci s povolenou pole.</span><span class="sxs-lookup"><span data-stu-id="ac1ca-122">A string can be thought of as a series of `Char` values, and the `String` type has built-in functions that allow you to perform many manipulations on a string that resemble the manipulations allowed by arrays.</span></span> <span data-ttu-id="ac1ca-123">Stejně jako všechna pole v [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], jde o pole od nuly.</span><span class="sxs-lookup"><span data-stu-id="ac1ca-123">Like all array in [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], these are zero-based arrays.</span></span> <span data-ttu-id="ac1ca-124">Mohou odkazovat na konkrétní znak v řetězci prostřednictvím `Chars` vlastnost, která umožňuje přístup ke znakům podle umístění, ve kterém se zobrazí v řetězci.</span><span class="sxs-lookup"><span data-stu-id="ac1ca-124">You may refer to a specific character in a string through the `Chars` property, which provides a way to access a character by the position in which it appears in the string.</span></span> <span data-ttu-id="ac1ca-125">Příklad:</span><span class="sxs-lookup"><span data-stu-id="ac1ca-125">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#67)]  
  
 <span data-ttu-id="ac1ca-126">Ve výše uvedeném příkladu `Chars` vlastnost řetězce vrátí čtvrtou znak v řetězci, který je `D`a přiřadí ji k `myChar`.</span><span class="sxs-lookup"><span data-stu-id="ac1ca-126">In the above example, the `Chars` property of the string returns the fourth character in the string, which is `D`, and assigns it to `myChar`.</span></span> <span data-ttu-id="ac1ca-127">Můžete také získat délku znamének určitého řetězce prostřednictvím `Length` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ac1ca-127">You can also get the length of a particular string through the `Length` property.</span></span> <span data-ttu-id="ac1ca-128">Pokud je potřeba manipulace s více typ pole na řetězec, můžete ji převést na pole `Char` instance pomocí `ToCharArray` funkce řetězec.</span><span class="sxs-lookup"><span data-stu-id="ac1ca-128">If you need to perform multiple array-type manipulations on a string, you can convert it to an array of `Char` instances using the `ToCharArray` function of the string.</span></span> <span data-ttu-id="ac1ca-129">Příklad:</span><span class="sxs-lookup"><span data-stu-id="ac1ca-129">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#68)]  
  
 <span data-ttu-id="ac1ca-130">Proměnná `myArray` nyní obsahuje celou řadu `Char` hodnoty, každý představující znak z `myString`.</span><span class="sxs-lookup"><span data-stu-id="ac1ca-130">The variable `myArray` now contains an array of `Char` values, each representing a character from `myString`.</span></span>  
  
## <a name="the-immutability-of-strings"></a><span data-ttu-id="ac1ca-131">Neměnnost řetězce</span><span class="sxs-lookup"><span data-stu-id="ac1ca-131">The Immutability of Strings</span></span>  
 <span data-ttu-id="ac1ca-132">Řetězec je *neměnné*, což znamená, že jeho hodnotu nelze změnit po vytvoření.</span><span class="sxs-lookup"><span data-stu-id="ac1ca-132">A string is *immutable*, which means its value cannot be changed once it has been created.</span></span> <span data-ttu-id="ac1ca-133">Ale to není vám bránit v přiřazení více než jednu hodnotu k proměnné řetězce.</span><span class="sxs-lookup"><span data-stu-id="ac1ca-133">However, this does not prevent you from assigning more than one value to a string variable.</span></span> <span data-ttu-id="ac1ca-134">Vezměte v úvahu v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="ac1ca-134">Consider the following example:</span></span>  
  
 [!code-vb[VbVbalrStrings#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#69)]  
  
 <span data-ttu-id="ac1ca-135">Tady se vytvoří proměnnou s řetězcem, zadána hodnota, a pak se změní jeho hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ac1ca-135">Here, a string variable is created, given a value, and then its value is changed.</span></span>  
  
 <span data-ttu-id="ac1ca-136">Přesněji řečeno v prvním řádku instanci typu `String` se vytvoří a předána hodnota `This string is immutable`.</span><span class="sxs-lookup"><span data-stu-id="ac1ca-136">More specifically, in the first line, an instance of type `String` is created and given the value `This string is immutable`.</span></span> <span data-ttu-id="ac1ca-137">Na druhém řádku v příkladu se vytvoří a předána hodnota novou instanci `Or is it?`, a proměnné řetězce zahodí svůj odkaz na první instanci a uchovává odkaz na novou instanci.</span><span class="sxs-lookup"><span data-stu-id="ac1ca-137">In the second line of the example, a new instance is created and given the value `Or is it?`, and the string variable discards its reference to the first instance and stores a reference to the new instance.</span></span>  
  
 <span data-ttu-id="ac1ca-138">Na rozdíl od jiných vnitřních datových typů `String` je typem odkazu.</span><span class="sxs-lookup"><span data-stu-id="ac1ca-138">Unlike other intrinsic data types, `String` is a reference type.</span></span> <span data-ttu-id="ac1ca-139">Když proměnné typu odkazu je předán jako argument funkce nebo podprogramu, je předána odkazem na adresu paměti, kde jsou data uložená namísto skutečné hodnoty řetězce.</span><span class="sxs-lookup"><span data-stu-id="ac1ca-139">When a variable of reference type is passed as an argument to a function or subroutine, a reference to the memory address where the data is stored is passed instead of the actual value of the string.</span></span> <span data-ttu-id="ac1ca-140">Takže v předchozím příkladu název proměnné zůstala stejná, ale odkazuje na jiný instanci `String` třídu, která obsahuje novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ac1ca-140">So in the previous example, the name of the variable remains the same, but it points to a new and different instance of the `String` class, which holds the new value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ac1ca-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ac1ca-141">See also</span></span>

- [<span data-ttu-id="ac1ca-142">Úvod do řetězců v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ac1ca-142">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
- [<span data-ttu-id="ac1ca-143">Datový typ String</span><span class="sxs-lookup"><span data-stu-id="ac1ca-143">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)
- [<span data-ttu-id="ac1ca-144">Datový typ Char</span><span class="sxs-lookup"><span data-stu-id="ac1ca-144">Char Data Type</span></span>](../../../../visual-basic/language-reference/data-types/char-data-type.md)
- [<span data-ttu-id="ac1ca-145">Základní operace s řetězci</span><span class="sxs-lookup"><span data-stu-id="ac1ca-145">Basic String Operations</span></span>](../../../../standard/base-types/basic-string-operations.md)
