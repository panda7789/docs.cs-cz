---
title: Základní informace o řetězcích
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Like operator
- strings [Visual Basic], Visual Basic
- strings [Visual Basic], regular expressions
ms.assetid: 5674418d-f00d-4f72-9f98-d15897793350
ms.openlocfilehash: 7141966e3c8a8cbce42111c56a85a00709e8fe1a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344281"
---
# <a name="string-basics-in-visual-basic"></a><span data-ttu-id="ee824-102">Základní informace o řetězcích v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ee824-102">String Basics in Visual Basic</span></span>
<span data-ttu-id="ee824-103">Datový typ `String` představuje řadu znaků (každý, který představuje v instanci datového typu `Char`).</span><span class="sxs-lookup"><span data-stu-id="ee824-103">The `String` data type represents a series of characters (each representing in turn an instance of the `Char` data type).</span></span> <span data-ttu-id="ee824-104">V tomto tématu se seznámíte se základními koncepty řetězců v Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ee824-104">This topic introduces the basic concepts of strings in Visual Basic.</span></span>  
  
## <a name="string-variables"></a><span data-ttu-id="ee824-105">Řetězcové proměnné</span><span class="sxs-lookup"><span data-stu-id="ee824-105">String Variables</span></span>  
 <span data-ttu-id="ee824-106">Instanci řetězce lze přiřadit literální hodnotu, která představuje řadu znaků.</span><span class="sxs-lookup"><span data-stu-id="ee824-106">An instance of a string can be assigned a literal value that represents a series of characters.</span></span> <span data-ttu-id="ee824-107">Příklad:</span><span class="sxs-lookup"><span data-stu-id="ee824-107">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#63)]  
  
 <span data-ttu-id="ee824-108">`String` proměnná může také přijmout libovolný výraz, který se vyhodnotí jako řetězec.</span><span class="sxs-lookup"><span data-stu-id="ee824-108">A `String` variable can also accept any expression that evaluates to a string.</span></span> <span data-ttu-id="ee824-109">Příklady:</span><span class="sxs-lookup"><span data-stu-id="ee824-109">Examples are shown below:</span></span>  
  
 [!code-vb[VbVbalrStrings#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#64)]  
  
 <span data-ttu-id="ee824-110">Jakýkoli literál, který je přiřazen proměnné `String`, musí být uzavřen v uvozovkách ("").</span><span class="sxs-lookup"><span data-stu-id="ee824-110">Any literal that is assigned to a `String` variable must be enclosed in quotation marks ("").</span></span> <span data-ttu-id="ee824-111">To znamená, že znak citace v rámci řetězce nemůže být reprezentován uvozovkami.</span><span class="sxs-lookup"><span data-stu-id="ee824-111">This means that a quotation mark within a string cannot be represented by a quotation mark.</span></span> <span data-ttu-id="ee824-112">Například následující kód způsobí chybu kompilátoru:</span><span class="sxs-lookup"><span data-stu-id="ee824-112">For example, the following code causes a compiler error:</span></span>  
  
 [!code-vb[VbVbalrStrings#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#65)]  
  
 <span data-ttu-id="ee824-113">Tento kód způsobí chybu, protože kompilátor ukončí řetězec za druhou uvozovku a zbytek řetězce je interpretován jako kód.</span><span class="sxs-lookup"><span data-stu-id="ee824-113">This code causes an error because the compiler terminates the string after the second quotation mark, and the remainder of the string is interpreted as code.</span></span> <span data-ttu-id="ee824-114">Chcete-li tento problém vyřešit, Visual Basic interpretuje v řetězci v řetězcové literály dvě uvozovky jako jeden znak uvozovky.</span><span class="sxs-lookup"><span data-stu-id="ee824-114">To solve this problem, Visual Basic interprets two quotation marks in a string literal as one quotation mark in the string.</span></span> <span data-ttu-id="ee824-115">Následující příklad ukazuje správný způsob, jak zahrnout uvozovky do řetězce:</span><span class="sxs-lookup"><span data-stu-id="ee824-115">The following example demonstrates the correct way to include a quotation mark in a string:</span></span>  
  
 [!code-vb[VbVbalrStrings#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#66)]  
  
 <span data-ttu-id="ee824-116">V předchozím příkladu se dvě uvozovky před slovem `Look` v řetězci staly jedním znakem uvozovek.</span><span class="sxs-lookup"><span data-stu-id="ee824-116">In the preceding example, the two quotation marks preceding the word `Look` become one quotation mark in the string.</span></span> <span data-ttu-id="ee824-117">Tři uvozovky na konci řádku zastupují jednu uvozovku v řetězci a znak ukončení řetězce.</span><span class="sxs-lookup"><span data-stu-id="ee824-117">The three quotation marks at the end of the line represent one quotation mark in the string and the string termination character.</span></span>  
  
 <span data-ttu-id="ee824-118">Řetězcové literály mohou obsahovat více řádků:</span><span class="sxs-lookup"><span data-stu-id="ee824-118">String literals can contain multiple lines:</span></span>  
  
```vb  
Dim x = "hello  
world"  
```  
  
 <span data-ttu-id="ee824-119">Výsledný řetězec obsahuje sekvence nového řádku, které jste použili v řetězcovém literálu (vbCr, vbCrLf atd.).</span><span class="sxs-lookup"><span data-stu-id="ee824-119">The resulting string contains newline sequences that you used in your string literal (vbcr, vbcrlf, etc.).</span></span>  <span data-ttu-id="ee824-120">Už nemusíte používat staré alternativní řešení:</span><span class="sxs-lookup"><span data-stu-id="ee824-120">You no longer need to use the old workaround:</span></span>  
  
```vb  
Dim x = <xml><![CDATA[Hello  
World]]></xml>.Value  
```  
  
## <a name="characters-in-strings"></a><span data-ttu-id="ee824-121">Znaky v řetězcích</span><span class="sxs-lookup"><span data-stu-id="ee824-121">Characters in Strings</span></span>  
 <span data-ttu-id="ee824-122">Řetězec lze představit jako řadu `Char` hodnot a typ `String` obsahuje integrované funkce, které umožňují provádět mnoho manipulací na řetězci, který se podobá manipulaci povolených poli.</span><span class="sxs-lookup"><span data-stu-id="ee824-122">A string can be thought of as a series of `Char` values, and the `String` type has built-in functions that allow you to perform many manipulations on a string that resemble the manipulations allowed by arrays.</span></span> <span data-ttu-id="ee824-123">Podobně jako u všech polí v .NET Framework jsou pole založená na nule.</span><span class="sxs-lookup"><span data-stu-id="ee824-123">Like all array in .NET Framework, these are zero-based arrays.</span></span> <span data-ttu-id="ee824-124">Můžete odkazovat na konkrétní znak v řetězci prostřednictvím vlastnosti `Chars`, která poskytuje způsob, jak získat přístup k znaku podle pozice, ve které se zobrazí v řetězci.</span><span class="sxs-lookup"><span data-stu-id="ee824-124">You may refer to a specific character in a string through the `Chars` property, which provides a way to access a character by the position in which it appears in the string.</span></span> <span data-ttu-id="ee824-125">Příklad:</span><span class="sxs-lookup"><span data-stu-id="ee824-125">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#67)]  
  
 <span data-ttu-id="ee824-126">V předchozím příkladu vlastnost `Chars` řetězce vrátí čtvrtý znak v řetězci, který je `D`a přiřadí jej `myChar`.</span><span class="sxs-lookup"><span data-stu-id="ee824-126">In the above example, the `Chars` property of the string returns the fourth character in the string, which is `D`, and assigns it to `myChar`.</span></span> <span data-ttu-id="ee824-127">Můžete také získat délku určitého řetězce prostřednictvím vlastnosti `Length`.</span><span class="sxs-lookup"><span data-stu-id="ee824-127">You can also get the length of a particular string through the `Length` property.</span></span> <span data-ttu-id="ee824-128">Pokud potřebujete provést více manipulací typu pole na řetězec, můžete ho převést na pole instancí `Char` pomocí funkce `ToCharArray` řetězce.</span><span class="sxs-lookup"><span data-stu-id="ee824-128">If you need to perform multiple array-type manipulations on a string, you can convert it to an array of `Char` instances using the `ToCharArray` function of the string.</span></span> <span data-ttu-id="ee824-129">Příklad:</span><span class="sxs-lookup"><span data-stu-id="ee824-129">For example:</span></span>  
  
 [!code-vb[VbVbalrStrings#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#68)]  
  
 <span data-ttu-id="ee824-130">Proměnná `myArray` nyní obsahuje pole hodnot `Char`, z nichž každý představuje znak z `myString`.</span><span class="sxs-lookup"><span data-stu-id="ee824-130">The variable `myArray` now contains an array of `Char` values, each representing a character from `myString`.</span></span>  
  
## <a name="the-immutability-of-strings"></a><span data-ttu-id="ee824-131">Neměnnosti řetězců</span><span class="sxs-lookup"><span data-stu-id="ee824-131">The Immutability of Strings</span></span>  
 <span data-ttu-id="ee824-132">Řetězec je *neměnný*, což znamená, že jeho hodnotu nelze po vytvoření změnit.</span><span class="sxs-lookup"><span data-stu-id="ee824-132">A string is *immutable*, which means its value cannot be changed once it has been created.</span></span> <span data-ttu-id="ee824-133">To však nebrání přiřazení více než jedné hodnoty k proměnné řetězce.</span><span class="sxs-lookup"><span data-stu-id="ee824-133">However, this does not prevent you from assigning more than one value to a string variable.</span></span> <span data-ttu-id="ee824-134">Vezměte v úvahu v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="ee824-134">Consider the following example:</span></span>  
  
 [!code-vb[VbVbalrStrings#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#69)]  
  
 <span data-ttu-id="ee824-135">Zde je vytvořena řetězcová proměnná s ohledem na hodnotu a její hodnota se změní.</span><span class="sxs-lookup"><span data-stu-id="ee824-135">Here, a string variable is created, given a value, and then its value is changed.</span></span>  
  
 <span data-ttu-id="ee824-136">Konkrétně v prvním řádku je vytvořena instance typu `String` a je zadána hodnota `This string is immutable`.</span><span class="sxs-lookup"><span data-stu-id="ee824-136">More specifically, in the first line, an instance of type `String` is created and given the value `This string is immutable`.</span></span> <span data-ttu-id="ee824-137">V druhém řádku příkladu je vytvořena nová instance a s hodnotou `Or is it?`a proměnná řetězce zahodí svůj odkaz na první instanci a ukládá odkaz na novou instanci.</span><span class="sxs-lookup"><span data-stu-id="ee824-137">In the second line of the example, a new instance is created and given the value `Or is it?`, and the string variable discards its reference to the first instance and stores a reference to the new instance.</span></span>  
  
 <span data-ttu-id="ee824-138">Na rozdíl od jiných vnitřních datových typů je `String` odkazovým typem.</span><span class="sxs-lookup"><span data-stu-id="ee824-138">Unlike other intrinsic data types, `String` is a reference type.</span></span> <span data-ttu-id="ee824-139">Pokud je proměnná typu odkazu předána jako argument funkci nebo podprogramu, odkaz na adresu paměti, kde jsou uložena data, se předává místo skutečné hodnoty řetězce.</span><span class="sxs-lookup"><span data-stu-id="ee824-139">When a variable of reference type is passed as an argument to a function or subroutine, a reference to the memory address where the data is stored is passed instead of the actual value of the string.</span></span> <span data-ttu-id="ee824-140">Takže v předchozím příkladu název proměnné zůstane stejný, ale odkazuje na novou a jinou instanci třídy `String`, která obsahuje novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ee824-140">So in the previous example, the name of the variable remains the same, but it points to a new and different instance of the `String` class, which holds the new value.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee824-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ee824-141">See also</span></span>

- [<span data-ttu-id="ee824-142">Seznámení s řetězci v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ee824-142">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
- [<span data-ttu-id="ee824-143">Datový typ String</span><span class="sxs-lookup"><span data-stu-id="ee824-143">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)
- [<span data-ttu-id="ee824-144">Datový typ Char</span><span class="sxs-lookup"><span data-stu-id="ee824-144">Char Data Type</span></span>](../../../../visual-basic/language-reference/data-types/char-data-type.md)
- [<span data-ttu-id="ee824-145">Základní operace s řetězci</span><span class="sxs-lookup"><span data-stu-id="ee824-145">Basic String Operations</span></span>](../../../../standard/base-types/basic-string-operations.md)
