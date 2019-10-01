---
title: String – datový typ (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.String
helpviewer_keywords:
- strings [Visual Basic], character
- strings [Visual Basic], fixed-length
- string keyword [Visual Basic]
- fixed-length strings [Visual Basic], string data type
- literals [Visual Basic], string
- text [Visual Basic], String data type
- $ identifier type character
- String data type
- fixed-length strings
- string literals [Visual Basic]
- data types [Visual Basic], assigning
- String literals [Visual Basic]
- identifier type characters [Visual Basic], $
ms.assetid: 15ac03f5-cabd-42cc-a754-1df3893c25d9
ms.openlocfilehash: 6d2fd226735622de5cd7197060c05b8ac12b69f1
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71696846"
---
# <a name="string-data-type-visual-basic"></a><span data-ttu-id="b5cf8-102">String – datový typ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b5cf8-102">String Data Type (Visual Basic)</span></span>
<span data-ttu-id="b5cf8-103">Obsahuje sekvence nepodepsaných 16bitových (2-bajtových) bodů kódu, které jsou v rozsahu od 0 do 65535.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-103">Holds sequences of unsigned 16-bit (2-byte) code points that range in value from 0 through 65535.</span></span> <span data-ttu-id="b5cf8-104">Každý *bod kódu*nebo kód znaku představuje jeden znak Unicode.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-104">Each *code point*, or character code, represents a single Unicode character.</span></span> <span data-ttu-id="b5cf8-105">Řetězec může obsahovat 0 až přibližně 2 000 000 000 (2 ^ 31) znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-105">A string can contain from 0 to approximately two billion (2 ^ 31) Unicode characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b5cf8-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b5cf8-106">Remarks</span></span>  
 <span data-ttu-id="b5cf8-107">Použijte datový typ `String` pro uložení více znaků bez režie správy pole `Char()`, pole prvků `Char`.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-107">Use the `String` data type to hold multiple characters without the array management overhead of `Char()`, an array of `Char` elements.</span></span>  
  
 <span data-ttu-id="b5cf8-108">Výchozí hodnota `String` je `Nothing` (odkaz s hodnotou null).</span><span class="sxs-lookup"><span data-stu-id="b5cf8-108">The default value of `String` is `Nothing` (a null reference).</span></span> <span data-ttu-id="b5cf8-109">Všimněte si, že se neshoduje s prázdným řetězcem (hodnota `""`).</span><span class="sxs-lookup"><span data-stu-id="b5cf8-109">Note that this is not the same as the empty string (value `""`).</span></span>  
  
## <a name="unicode-characters"></a><span data-ttu-id="b5cf8-110">Znaky Unicode</span><span class="sxs-lookup"><span data-stu-id="b5cf8-110">Unicode Characters</span></span>  
 <span data-ttu-id="b5cf8-111">Prvních 128 kódových bodů (0 – 127) Unicode odpovídá písmenům a symbolům na standardní americké klávesnici.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-111">The first 128 code points (0–127) of Unicode correspond to the letters and symbols on a standard U.S. keyboard.</span></span> <span data-ttu-id="b5cf8-112">Tyto první body kódu 128 jsou stejné jako ty, které definuje znaková sada ASCII.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-112">These first 128 code points are the same as those the ASCII character set defines.</span></span> <span data-ttu-id="b5cf8-113">Druhý bod kódu 128 (128 – 255) představuje speciální znaky, jako jsou písmena abecedy založená na latince, zvýraznění, symboly měn a zlomky.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-113">The second 128 code points (128–255) represent special characters, such as Latin-based alphabet letters, accents, currency symbols, and fractions.</span></span> <span data-ttu-id="b5cf8-114">Kódování Unicode používá zbývající body kódu (256-65535) pro širokou škálu symbolů.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-114">Unicode uses the remaining code points (256-65535) for a wide variety of symbols.</span></span> <span data-ttu-id="b5cf8-115">To zahrnuje celosvětově textové znaky, diakritická znaménka a matematické a technické symboly.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-115">This includes worldwide textual characters, diacritics, and mathematical and technical symbols.</span></span>  
  
 <span data-ttu-id="b5cf8-116">Můžete použít metody jako <xref:System.Char.IsDigit%2A> a <xref:System.Char.IsPunctuation%2A> na jednotlivém znaku v proměnné `String` k určení klasifikace Unicode.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-116">You can use methods such as <xref:System.Char.IsDigit%2A> and <xref:System.Char.IsPunctuation%2A> on an individual character in a `String` variable to determine its Unicode classification.</span></span>  
  
## <a name="format-requirements"></a><span data-ttu-id="b5cf8-117">Požadavky na formát</span><span class="sxs-lookup"><span data-stu-id="b5cf8-117">Format Requirements</span></span>  
 <span data-ttu-id="b5cf8-118">Literál `String` je nutné uzavřít do uvozovek (`" "`).</span><span class="sxs-lookup"><span data-stu-id="b5cf8-118">You must enclose a `String` literal within quotation marks (`" "`).</span></span> <span data-ttu-id="b5cf8-119">Pokud je nutné zadat uvozovky jako jeden ze znaků v řetězci, použijete dvě souvislé uvozovky (`""`).</span><span class="sxs-lookup"><span data-stu-id="b5cf8-119">If you must include a quotation mark as one of the characters in the string, you use two contiguous quotation marks (`""`).</span></span> <span data-ttu-id="b5cf8-120">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-120">The following example illustrates this.</span></span>  
  
```vb  
Dim j As String = "Joe said ""Hello"" to me."  
Dim h As String = "Hello"  
' The following messages all display the same thing:  
' "Joe said "Hello" to me."  
MsgBox(j)  
MsgBox("Joe said " & """" & h & """" & " to me.")  
MsgBox("Joe said """ & h & """ to me.")  
```  
  
 <span data-ttu-id="b5cf8-121">Všimněte si, že souvislé uvozovky, které představují uvozovky v řetězci, jsou nezávislé na uvozovkách, které začínají a končí literál `String`.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-121">Note that the contiguous quotation marks that represent a quotation mark in the string are independent of the quotation marks that begin and end the `String` literal.</span></span>  
  
## <a name="string-manipulations"></a><span data-ttu-id="b5cf8-122">Manipulace s řetězci</span><span class="sxs-lookup"><span data-stu-id="b5cf8-122">String Manipulations</span></span>  
 <span data-ttu-id="b5cf8-123">Jakmile přiřadíte řetězec proměnné `String`, jedná se o *neměnné*řetězce, což znamená, že nemůžete změnit jeho délku nebo obsah.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-123">Once you assign a string to a `String` variable, that string is *immutable*, which means you cannot change its length or contents.</span></span> <span data-ttu-id="b5cf8-124">Při změně řetězce jakýmkoli způsobem Visual Basic vytvoří nový řetězec a opustí předchozí.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-124">When you alter a string in any way, Visual Basic creates a new string and abandons the previous one.</span></span> <span data-ttu-id="b5cf8-125">Proměnná `String` následně odkazuje na nový řetězec.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-125">The `String` variable then points to the new string.</span></span>  
  
 <span data-ttu-id="b5cf8-126">Můžete manipulovat s obsahem proměnné `String` pomocí nejrůznějších řetězcových funkcí.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-126">You can manipulate the contents of a `String` variable by using a variety of string functions.</span></span> <span data-ttu-id="b5cf8-127">Následující příklad ukazuje funkci <xref:Microsoft.VisualBasic.Strings.Left%2A>.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-127">The following example illustrates the <xref:Microsoft.VisualBasic.Strings.Left%2A> function</span></span>  
  
```vb  
Dim S As String = "Database"  
' The following statement sets S to a new string containing "Data".  
S = Microsoft.VisualBasic.Left(S, 4)  
```  
  
 <span data-ttu-id="b5cf8-128">Řetězec vytvořený jinou komponentou může být doplněn mezerami na začátku nebo na konci.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-128">A string created by another component might be padded with leading or trailing spaces.</span></span> <span data-ttu-id="b5cf8-129">Pokud tento řetězec obdržíte, můžete k odebrání těchto prostorů použít funkce <xref:Microsoft.VisualBasic.Strings.Trim%2A>, <xref:Microsoft.VisualBasic.Strings.LTrim%2A> a <xref:Microsoft.VisualBasic.Strings.RTrim%2A>.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-129">If you receive such a string, you can use the <xref:Microsoft.VisualBasic.Strings.Trim%2A>, <xref:Microsoft.VisualBasic.Strings.LTrim%2A>, and <xref:Microsoft.VisualBasic.Strings.RTrim%2A> functions to remove these spaces.</span></span>  
  
 <span data-ttu-id="b5cf8-130">Další informace o manipulaci s řetězci naleznete v tématu [strings](../../../visual-basic/programming-guide/language-features/strings/index.md).</span><span class="sxs-lookup"><span data-stu-id="b5cf8-130">For more information about string manipulations, see [Strings](../../../visual-basic/programming-guide/language-features/strings/index.md).</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="b5cf8-131">Tipy k programování</span><span class="sxs-lookup"><span data-stu-id="b5cf8-131">Programming Tips</span></span>  
  
- <span data-ttu-id="b5cf8-132">**Záporná čísla.**</span><span class="sxs-lookup"><span data-stu-id="b5cf8-132">**Negative Numbers.**</span></span> <span data-ttu-id="b5cf8-133">Mějte na paměti, že znaky držené `String` jsou bez znaménka a nemohou představovat záporné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-133">Remember that the characters held by `String` are unsigned and cannot represent negative values.</span></span> <span data-ttu-id="b5cf8-134">V žádném případě byste neměli používat `String` pro uchování číselných hodnot.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-134">In any case, you should not use `String` to hold numeric values.</span></span>  
  
- <span data-ttu-id="b5cf8-135">**Problematika spolupráce.**</span><span class="sxs-lookup"><span data-stu-id="b5cf8-135">**Interop Considerations.**</span></span> <span data-ttu-id="b5cf8-136">Pokud procházejíte s komponentami, které nejsou napsané pro .NET Framework, například automatizace nebo objekty COM, pamatujte, že řetězcové znaky mají v jiných prostředích jinou šířku dat (8 bitů).</span><span class="sxs-lookup"><span data-stu-id="b5cf8-136">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, remember that string characters have a different data width (8 bits) in other environments.</span></span> <span data-ttu-id="b5cf8-137">Pokud předáváte jako součást řetězcový argument 8bitové znaky, deklarujte ji jako `Byte()`, pole prvků `Byte` místo `String` v novém kódu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-137">If you are passing a string argument of 8-bit characters to such a component, declare it as `Byte()`, an array of `Byte` elements, instead of `String` in your new Visual Basic code.</span></span>  
  
- <span data-ttu-id="b5cf8-138">**Znaky typu.**</span><span class="sxs-lookup"><span data-stu-id="b5cf8-138">**Type Characters.**</span></span> <span data-ttu-id="b5cf8-139">Připojení znaku typu identifikátoru `$` k jakémukoli identifikátoru vynutí datový typ `String`.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-139">Appending the identifier type character `$` to any identifier forces it to the `String` data type.</span></span> <span data-ttu-id="b5cf8-140">`String` nemá žádný znak typu literálu.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-140">`String` has no literal type character.</span></span> <span data-ttu-id="b5cf8-141">Nicméně kompilátor zpracovává literály uzavřené v uvozovkách (`" "`) jako `String`.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-141">However, the compiler treats literals enclosed in quotation marks (`" "`) as `String`.</span></span>  
  
- <span data-ttu-id="b5cf8-142">**Typ rozhraní.**</span><span class="sxs-lookup"><span data-stu-id="b5cf8-142">**Framework Type.**</span></span> <span data-ttu-id="b5cf8-143">Odpovídající typ ve .NET Framework je třída <xref:System.String?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b5cf8-143">The corresponding type in the .NET Framework is the <xref:System.String?displayProperty=nameWithType> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5cf8-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b5cf8-144">See also</span></span>

- <xref:System.String?displayProperty=nameWithType>
- [<span data-ttu-id="b5cf8-145">Datové typy</span><span class="sxs-lookup"><span data-stu-id="b5cf8-145">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="b5cf8-146">Datový typ Char</span><span class="sxs-lookup"><span data-stu-id="b5cf8-146">Char Data Type</span></span>](../../../visual-basic/language-reference/data-types/char-data-type.md)
- [<span data-ttu-id="b5cf8-147">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="b5cf8-147">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="b5cf8-148">Souhrn převodu</span><span class="sxs-lookup"><span data-stu-id="b5cf8-148">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="b5cf8-149">Postupy: Volání funkce systému Windows, která přebírá nepřiřazené typy</span><span class="sxs-lookup"><span data-stu-id="b5cf8-149">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="b5cf8-150">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="b5cf8-150">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
