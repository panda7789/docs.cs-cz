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
ms.openlocfilehash: 3e87dc6527b4351467b1155439ee8266157c16ff
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58842288"
---
# <a name="string-data-type-visual-basic"></a><span data-ttu-id="db0ef-102">String – datový typ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="db0ef-102">String Data Type (Visual Basic)</span></span>
<span data-ttu-id="db0ef-103">Obsahuje pořadí bodů kódu (2bajtových) bez znaménka 16bitové tohoto rozsahu v rozmezí 0 až 65535.</span><span class="sxs-lookup"><span data-stu-id="db0ef-103">Holds sequences of unsigned 16-bit (2-byte) code points that range in value from 0 through 65535.</span></span> <span data-ttu-id="db0ef-104">Každý *kódu bodu*, nebo kód znaku, představuje jeden znak Unicode.</span><span class="sxs-lookup"><span data-stu-id="db0ef-104">Each *code point*, or character code, represents a single Unicode character.</span></span> <span data-ttu-id="db0ef-105">Řetězec se může skládat z 0 až přibližně dvě miliardy (2 ^ 31) znaků Unicode.</span><span class="sxs-lookup"><span data-stu-id="db0ef-105">A string can contain from 0 to approximately two billion (2 ^ 31) Unicode characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="db0ef-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="db0ef-106">Remarks</span></span>  
 <span data-ttu-id="db0ef-107">Použití `String` datový typ pro uložení více znaků bez režie na správu pole těchto `Char()`, pole `Char` elementy.</span><span class="sxs-lookup"><span data-stu-id="db0ef-107">Use the `String` data type to hold multiple characters without the array management overhead of `Char()`, an array of `Char` elements.</span></span>  
  
 <span data-ttu-id="db0ef-108">Výchozí hodnota `String` je `Nothing` (odkaz s hodnotou null).</span><span class="sxs-lookup"><span data-stu-id="db0ef-108">The default value of `String` is `Nothing` (a null reference).</span></span> <span data-ttu-id="db0ef-109">Všimněte si, že to není stejné jako prázdný řetězec (hodnota `""`).</span><span class="sxs-lookup"><span data-stu-id="db0ef-109">Note that this is not the same as the empty string (value `""`).</span></span>  
  
## <a name="unicode-characters"></a><span data-ttu-id="db0ef-110">Znaky kódování Unicode</span><span class="sxs-lookup"><span data-stu-id="db0ef-110">Unicode Characters</span></span>  
 <span data-ttu-id="db0ef-111">První body 128 kódu (0 – 127) Unicode odpovídají písmena a symboly na standardní klávesnici USA.</span><span class="sxs-lookup"><span data-stu-id="db0ef-111">The first 128 code points (0–127) of Unicode correspond to the letters and symbols on a standard U.S. keyboard.</span></span> <span data-ttu-id="db0ef-112">Tyto první body 128 kódu jsou stejné jako definuje znakové sady ASCII.</span><span class="sxs-lookup"><span data-stu-id="db0ef-112">These first 128 code points are the same as those the ASCII character set defines.</span></span> <span data-ttu-id="db0ef-113">Druhý body 128 kódu (128 – 255) představují speciální znaky, jako je například písmena abecedy latince, zvýraznění, symboly měny a podíly.</span><span class="sxs-lookup"><span data-stu-id="db0ef-113">The second 128 code points (128–255) represent special characters, such as Latin-based alphabet letters, accents, currency symbols, and fractions.</span></span> <span data-ttu-id="db0ef-114">Unicode používá pro širokou škálu symboly zbývající body kódu (256 – 65535).</span><span class="sxs-lookup"><span data-stu-id="db0ef-114">Unicode uses the remaining code points (256-65535) for a wide variety of symbols.</span></span> <span data-ttu-id="db0ef-115">To zahrnuje po celém světě textové znaky, znaky s diakritikou a technické a matematické symboly.</span><span class="sxs-lookup"><span data-stu-id="db0ef-115">This includes worldwide textual characters, diacritics, and mathematical and technical symbols.</span></span>  
  
 <span data-ttu-id="db0ef-116">Můžete například použít metody <xref:System.Char.IsDigit%2A> a <xref:System.Char.IsPunctuation%2A> na jednotlivý znak ve `String` proměnnou k určení jeho klasifikace kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="db0ef-116">You can use methods such as <xref:System.Char.IsDigit%2A> and <xref:System.Char.IsPunctuation%2A> on an individual character in a `String` variable to determine its Unicode classification.</span></span>  
  
## <a name="format-requirements"></a><span data-ttu-id="db0ef-117">Požadavky na formát</span><span class="sxs-lookup"><span data-stu-id="db0ef-117">Format Requirements</span></span>  
 <span data-ttu-id="db0ef-118">Je nutné uzavřít `String` literál v uvozovkách (`" "`).</span><span class="sxs-lookup"><span data-stu-id="db0ef-118">You must enclose a `String` literal within quotation marks (`" "`).</span></span> <span data-ttu-id="db0ef-119">Pokud jako jeden ze znaků v řetězci musí obsahovat znak uvozovek, je použít dva souvislých uvozovky (`""`).</span><span class="sxs-lookup"><span data-stu-id="db0ef-119">If you must include a quotation mark as one of the characters in the string, you use two contiguous quotation marks (`""`).</span></span> <span data-ttu-id="db0ef-120">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="db0ef-120">The following example illustrates this.</span></span>  
  
```  
Dim j As String = "Joe said ""Hello"" to me."  
Dim h As String = "Hello"  
' The following messages all display the same thing:  
' "Joe said "Hello" to me."  
MsgBox(j)  
MsgBox("Joe said " & """" & h & """" & " to me.")  
MsgBox("Joe said """ & h & """ to me.")  
```  
  
 <span data-ttu-id="db0ef-121">Mějte na paměti, že jsou souvislé uvozovky, které představují uvozovka v řetězci nezávislé na uvozovky, které začínají i končí `String` literálu.</span><span class="sxs-lookup"><span data-stu-id="db0ef-121">Note that the contiguous quotation marks that represent a quotation mark in the string are independent of the quotation marks that begin and end the `String` literal.</span></span>  
  
## <a name="string-manipulations"></a><span data-ttu-id="db0ef-122">Manipulace s řetězci</span><span class="sxs-lookup"><span data-stu-id="db0ef-122">String Manipulations</span></span>  
 <span data-ttu-id="db0ef-123">Po přiřazení řetězec `String` proměnné, je tento řetězec *neměnné*, což znamená, že nelze změnit jeho délka nebo obsah.</span><span class="sxs-lookup"><span data-stu-id="db0ef-123">Once you assign a string to a `String` variable, that string is *immutable*, which means you cannot change its length or contents.</span></span> <span data-ttu-id="db0ef-124">Při změně řetězec žádným způsobem jazyka Visual Basic vytvoří nový řetězec a opustí předchozí.</span><span class="sxs-lookup"><span data-stu-id="db0ef-124">When you alter a string in any way, Visual Basic creates a new string and abandons the previous one.</span></span> <span data-ttu-id="db0ef-125">`String` Proměnná se pak odkazuje na nový řetězec.</span><span class="sxs-lookup"><span data-stu-id="db0ef-125">The `String` variable then points to the new string.</span></span>  
  
 <span data-ttu-id="db0ef-126">Můžete manipulovat s obsahem `String` proměnné pomocí celé řady funkcí řetězec.</span><span class="sxs-lookup"><span data-stu-id="db0ef-126">You can manipulate the contents of a `String` variable by using a variety of string functions.</span></span> <span data-ttu-id="db0ef-127">Následující příklad ukazuje, <xref:Microsoft.VisualBasic.Strings.Left%2A> – funkce</span><span class="sxs-lookup"><span data-stu-id="db0ef-127">The following example illustrates the <xref:Microsoft.VisualBasic.Strings.Left%2A> function</span></span>  
  
```  
Dim S As String = "Database"  
' The following statement sets S to a new string containing "Data".  
S = Microsoft.VisualBasic.Left(S, 4)  
```  
  
 <span data-ttu-id="db0ef-128">Řetězec vytvořené jinou komponentou může být, aby bylo vytvořeno úvodní a koncové mezery.</span><span class="sxs-lookup"><span data-stu-id="db0ef-128">A string created by another component might be padded with leading or trailing spaces.</span></span> <span data-ttu-id="db0ef-129">Pokud obdržíte takový řetězec, můžete použít <xref:Microsoft.VisualBasic.Strings.Trim%2A>, <xref:Microsoft.VisualBasic.Strings.LTrim%2A>, a <xref:Microsoft.VisualBasic.Strings.RTrim%2A> funkce odebrat tyto mezery.</span><span class="sxs-lookup"><span data-stu-id="db0ef-129">If you receive such a string, you can use the <xref:Microsoft.VisualBasic.Strings.Trim%2A>, <xref:Microsoft.VisualBasic.Strings.LTrim%2A>, and <xref:Microsoft.VisualBasic.Strings.RTrim%2A> functions to remove these spaces.</span></span>  
  
 <span data-ttu-id="db0ef-130">Další informace o manipulace s řetězci, naleznete v tématu [řetězce](../../../visual-basic/programming-guide/language-features/strings/index.md).</span><span class="sxs-lookup"><span data-stu-id="db0ef-130">For more information about string manipulations, see [Strings](../../../visual-basic/programming-guide/language-features/strings/index.md).</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="db0ef-131">Tipy k programování</span><span class="sxs-lookup"><span data-stu-id="db0ef-131">Programming Tips</span></span>  
  
-   <span data-ttu-id="db0ef-132">**Záporná čísla.**</span><span class="sxs-lookup"><span data-stu-id="db0ef-132">**Negative Numbers.**</span></span> <span data-ttu-id="db0ef-133">Mějte na paměti, že znaky drží `String` jsou bez znaménka a nemůže představovat záporné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="db0ef-133">Remember that the characters held by `String` are unsigned and cannot represent negative values.</span></span> <span data-ttu-id="db0ef-134">V každém případě byste neměli používat `String` pro uložení číselné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="db0ef-134">In any case, you should not use `String` to hold numeric values.</span></span>  
  
-   <span data-ttu-id="db0ef-135">**Spolupráce aspekty.**</span><span class="sxs-lookup"><span data-stu-id="db0ef-135">**Interop Considerations.**</span></span> <span data-ttu-id="db0ef-136">Při vzájemném propojování součástí, které nejsou napsané pro rozhraní .NET Framework pro příklad objekty automatizace nebo COM, mějte na paměti, že řetězec znaků mít odlišnou datovou šířku (8 bitů) v jiných prostředích.</span><span class="sxs-lookup"><span data-stu-id="db0ef-136">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, remember that string characters have a different data width (8 bits) in other environments.</span></span> <span data-ttu-id="db0ef-137">Pokud takové součásti předáváte argument řetězec znaků 8 bitů, deklarujte ho jako `Byte()`, pole `Byte` prvků, místo `String` v váš nový kód jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="db0ef-137">If you are passing a string argument of 8-bit characters to such a component, declare it as `Byte()`, an array of `Byte` elements, instead of `String` in your new Visual Basic code.</span></span>  
  
-   <span data-ttu-id="db0ef-138">**Znaky typu.**</span><span class="sxs-lookup"><span data-stu-id="db0ef-138">**Type Characters.**</span></span> <span data-ttu-id="db0ef-139">Přidávání znak typu identifikátoru `$` k libovolnému identifikátoru se z něj stane `String` datového typu.</span><span class="sxs-lookup"><span data-stu-id="db0ef-139">Appending the identifier type character `$` to any identifier forces it to the `String` data type.</span></span> <span data-ttu-id="db0ef-140">`String` nemá žádné – znak typu literálu.</span><span class="sxs-lookup"><span data-stu-id="db0ef-140">`String` has no literal type character.</span></span> <span data-ttu-id="db0ef-141">Ale kompilátor zpracovává literály uzavřena v uvozovkách (`" "`) jako `String`.</span><span class="sxs-lookup"><span data-stu-id="db0ef-141">However, the compiler treats literals enclosed in quotation marks (`" "`) as `String`.</span></span>  
  
-   <span data-ttu-id="db0ef-142">**Typ architektury.**</span><span class="sxs-lookup"><span data-stu-id="db0ef-142">**Framework Type.**</span></span> <span data-ttu-id="db0ef-143">Odpovídajícím typem v rozhraní .NET Framework je <xref:System.String?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="db0ef-143">The corresponding type in the .NET Framework is the <xref:System.String?displayProperty=nameWithType> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db0ef-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="db0ef-144">See also</span></span>

- <xref:System.String?displayProperty=nameWithType>
- [<span data-ttu-id="db0ef-145">Datové typy</span><span class="sxs-lookup"><span data-stu-id="db0ef-145">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="db0ef-146">Datový typ Char</span><span class="sxs-lookup"><span data-stu-id="db0ef-146">Char Data Type</span></span>](../../../visual-basic/language-reference/data-types/char-data-type.md)
- [<span data-ttu-id="db0ef-147">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="db0ef-147">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="db0ef-148">Souhrn převodu</span><span class="sxs-lookup"><span data-stu-id="db0ef-148">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="db0ef-149">Postupy: Volání funkce Windows, která přebírá typy bez znaménka</span><span class="sxs-lookup"><span data-stu-id="db0ef-149">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="db0ef-150">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="db0ef-150">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
