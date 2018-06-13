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
ms.openlocfilehash: 894638bbe50dad2cae1f74a2f7b7fe006f029d1b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592116"
---
# <a name="string-data-type-visual-basic"></a><span data-ttu-id="e8c05-102">String – datový typ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e8c05-102">String Data Type (Visual Basic)</span></span>
<span data-ttu-id="e8c05-103">Obsahuje pořadí, bodů nepodepsaný kód (2bajtová) 16bitové rozsahu v rozmezí 0 až 65535.</span><span class="sxs-lookup"><span data-stu-id="e8c05-103">Holds sequences of unsigned 16-bit (2-byte) code points that range in value from 0 through 65535.</span></span> <span data-ttu-id="e8c05-104">Každý *code bodu*, nebo kód znaku, představuje jeden znak Unicode.</span><span class="sxs-lookup"><span data-stu-id="e8c05-104">Each *code point*, or character code, represents a single Unicode character.</span></span> <span data-ttu-id="e8c05-105">Řetězec může obsahovat od 0 do přibližně dvě miliardy (2 ^ 31) znaky znakové sady Unicode.</span><span class="sxs-lookup"><span data-stu-id="e8c05-105">A string can contain from 0 to approximately two billion (2 ^ 31) Unicode characters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e8c05-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e8c05-106">Remarks</span></span>  
 <span data-ttu-id="e8c05-107">Použití `String` datový typ pro uložení více znaky bez režie na správu pole těchto `Char()`, pole `Char` elementy.</span><span class="sxs-lookup"><span data-stu-id="e8c05-107">Use the `String` data type to hold multiple characters without the array management overhead of `Char()`, an array of `Char` elements.</span></span>  
  
 <span data-ttu-id="e8c05-108">Výchozí hodnota `String` je `Nothing` (odkaz s hodnotou null).</span><span class="sxs-lookup"><span data-stu-id="e8c05-108">The default value of `String` is `Nothing` (a null reference).</span></span> <span data-ttu-id="e8c05-109">Všimněte si, že to není stejný jako prázdný řetězec (hodnota `""`).</span><span class="sxs-lookup"><span data-stu-id="e8c05-109">Note that this is not the same as the empty string (value `""`).</span></span>  
  
## <a name="unicode-characters"></a><span data-ttu-id="e8c05-110">Znaky kódování Unicode</span><span class="sxs-lookup"><span data-stu-id="e8c05-110">Unicode Characters</span></span>  
 <span data-ttu-id="e8c05-111">První body 128 kódu (0 – 127) Unicode odpovídají písmena a symboly standardní klávesnicích.</span><span class="sxs-lookup"><span data-stu-id="e8c05-111">The first 128 code points (0–127) of Unicode correspond to the letters and symbols on a standard U.S. keyboard.</span></span> <span data-ttu-id="e8c05-112">Tyto první 128 kód body jsou stejné jako definuje znaková sada ASCII.</span><span class="sxs-lookup"><span data-stu-id="e8c05-112">These first 128 code points are the same as those the ASCII character set defines.</span></span> <span data-ttu-id="e8c05-113">Druhý body 128 kódu (128 – 255) představují speciální znaky, jako je například písmena abecedy latince, zvýraznění, tyto symboly a zlomků.</span><span class="sxs-lookup"><span data-stu-id="e8c05-113">The second 128 code points (128–255) represent special characters, such as Latin-based alphabet letters, accents, currency symbols, and fractions.</span></span> <span data-ttu-id="e8c05-114">Unicode používá zbývající body kódu (256 65 535) pro celou řadu symboly.</span><span class="sxs-lookup"><span data-stu-id="e8c05-114">Unicode uses the remaining code points (256-65535) for a wide variety of symbols.</span></span> <span data-ttu-id="e8c05-115">To zahrnuje po celém světě textové znaky, znaky s diakritikou a matematické a technické symboly.</span><span class="sxs-lookup"><span data-stu-id="e8c05-115">This includes worldwide textual characters, diacritics, and mathematical and technical symbols.</span></span>  
  
 <span data-ttu-id="e8c05-116">Můžete například použít metody <xref:System.Char.IsDigit%2A> a <xref:System.Char.IsPunctuation%2A> na jednotlivé znak v `String` proměnné můžete zjistit klasifikaci kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="e8c05-116">You can use methods such as <xref:System.Char.IsDigit%2A> and <xref:System.Char.IsPunctuation%2A> on an individual character in a `String` variable to determine its Unicode classification.</span></span>  
  
## <a name="format-requirements"></a><span data-ttu-id="e8c05-117">Požadavky na formát</span><span class="sxs-lookup"><span data-stu-id="e8c05-117">Format Requirements</span></span>  
 <span data-ttu-id="e8c05-118">Je nutné uzavřít `String` literálu do uvozovek (`" "`).</span><span class="sxs-lookup"><span data-stu-id="e8c05-118">You must enclose a `String` literal within quotation marks (`" "`).</span></span> <span data-ttu-id="e8c05-119">Pokud jako jeden z znaků v řetězci musí zahrnovat uvozovky, můžete použít dva souvislý uvozovky (`""`).</span><span class="sxs-lookup"><span data-stu-id="e8c05-119">If you must include a quotation mark as one of the characters in the string, you use two contiguous quotation marks (`""`).</span></span> <span data-ttu-id="e8c05-120">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="e8c05-120">The following example illustrates this.</span></span>  
  
```  
Dim j As String = "Joe said ""Hello"" to me."  
Dim h As String = "Hello"  
' The following messages all display the same thing:  
' "Joe said "Hello" to me."  
MsgBox(j)  
MsgBox("Joe said " & """" & h & """" & " to me.")  
MsgBox("Joe said """ & h & """ to me.")  
```  
  
 <span data-ttu-id="e8c05-121">Upozorňujeme, že jsou souvislý uvozovky, které představují uvozovky v řetězci nezávislé na uvozovky, které začínají a končí `String` literálu.</span><span class="sxs-lookup"><span data-stu-id="e8c05-121">Note that the contiguous quotation marks that represent a quotation mark in the string are independent of the quotation marks that begin and end the `String` literal.</span></span>  
  
## <a name="string-manipulations"></a><span data-ttu-id="e8c05-122">Manipulace s řetězci</span><span class="sxs-lookup"><span data-stu-id="e8c05-122">String Manipulations</span></span>  
 <span data-ttu-id="e8c05-123">Po přiřazení řetězec tak, aby `String` proměnné, je tento řetězec *neměnné*, což znamená, že nelze změnit, jeho délka nebo obsah.</span><span class="sxs-lookup"><span data-stu-id="e8c05-123">Once you assign a string to a `String` variable, that string is *immutable*, which means you cannot change its length or contents.</span></span> <span data-ttu-id="e8c05-124">Když upravíte řetězec žádným způsobem, Visual Basic vytvoří nový řetězec a opustí předchozí.</span><span class="sxs-lookup"><span data-stu-id="e8c05-124">When you alter a string in any way, Visual Basic creates a new string and abandons the previous one.</span></span> <span data-ttu-id="e8c05-125">`String` Proměnná se pak odkazuje na nový řetězec.</span><span class="sxs-lookup"><span data-stu-id="e8c05-125">The `String` variable then points to the new string.</span></span>  
  
 <span data-ttu-id="e8c05-126">Můžete upravit obsah `String` proměnné pomocí celou řadu funkcí řetězec.</span><span class="sxs-lookup"><span data-stu-id="e8c05-126">You can manipulate the contents of a `String` variable by using a variety of string functions.</span></span> <span data-ttu-id="e8c05-127">Následující příklad ukazuje <xref:Microsoft.VisualBasic.Strings.Left%2A> – funkce</span><span class="sxs-lookup"><span data-stu-id="e8c05-127">The following example illustrates the <xref:Microsoft.VisualBasic.Strings.Left%2A> function</span></span>  
  
```  
Dim S As String = "Database"  
' The following statement sets S to a new string containing "Data".  
S = Microsoft.VisualBasic.Left(S, 4)  
```  
  
 <span data-ttu-id="e8c05-128">Řetězec vytvořený jinou součástí může být doplněno počáteční nebo koncové mezery.</span><span class="sxs-lookup"><span data-stu-id="e8c05-128">A string created by another component might be padded with leading or trailing spaces.</span></span> <span data-ttu-id="e8c05-129">Pokud se zobrazí tyto řetězce, můžete použít <xref:Microsoft.VisualBasic.Strings.Trim%2A>, <xref:Microsoft.VisualBasic.Strings.LTrim%2A>, a <xref:Microsoft.VisualBasic.Strings.RTrim%2A> funkce odebrat tyto prostory.</span><span class="sxs-lookup"><span data-stu-id="e8c05-129">If you receive such a string, you can use the <xref:Microsoft.VisualBasic.Strings.Trim%2A>, <xref:Microsoft.VisualBasic.Strings.LTrim%2A>, and <xref:Microsoft.VisualBasic.Strings.RTrim%2A> functions to remove these spaces.</span></span>  
  
 <span data-ttu-id="e8c05-130">Další informace o manipulace s řetězci najdete v tématu [řetězce](../../../visual-basic/programming-guide/language-features/strings/index.md).</span><span class="sxs-lookup"><span data-stu-id="e8c05-130">For more information about string manipulations, see [Strings](../../../visual-basic/programming-guide/language-features/strings/index.md).</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="e8c05-131">Tipy k programování</span><span class="sxs-lookup"><span data-stu-id="e8c05-131">Programming Tips</span></span>  
  
-   <span data-ttu-id="e8c05-132">**Záporná čísla.**</span><span class="sxs-lookup"><span data-stu-id="e8c05-132">**Negative Numbers.**</span></span> <span data-ttu-id="e8c05-133">Mějte na paměti, že znaky držené `String` nejsou podepsané a nemůže představují záporné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e8c05-133">Remember that the characters held by `String` are unsigned and cannot represent negative values.</span></span> <span data-ttu-id="e8c05-134">V každém případě byste neměli používat `String` pro uložení číselné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e8c05-134">In any case, you should not use `String` to hold numeric values.</span></span>  
  
-   <span data-ttu-id="e8c05-135">**Spolupráce aspekty.**</span><span class="sxs-lookup"><span data-stu-id="e8c05-135">**Interop Considerations.**</span></span> <span data-ttu-id="e8c05-136">Pokud jsou během propojení s součásti, které nejsou určeny pro rozhraní .NET Framework pro příklad objekty automatizace nebo COM, mějte na paměti, že řetězec znaků mají odlišné datové šířka (8 bitů) v jiných prostředích.</span><span class="sxs-lookup"><span data-stu-id="e8c05-136">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, remember that string characters have a different data width (8 bits) in other environments.</span></span> <span data-ttu-id="e8c05-137">Argument řetězce znaků 8bitové předáte pro tyto součásti, deklarujte ji jako `Byte()`, pole `Byte` elementy, místo `String` v váš nový kód jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e8c05-137">If you are passing a string argument of 8-bit characters to such a component, declare it as `Byte()`, an array of `Byte` elements, instead of `String` in your new Visual Basic code.</span></span>  
  
-   <span data-ttu-id="e8c05-138">**Znaky typu.**</span><span class="sxs-lookup"><span data-stu-id="e8c05-138">**Type Characters.**</span></span> <span data-ttu-id="e8c05-139">Připojování znak typu identifikátoru `$` na všechny identifikátor vynutí ho k `String` datového typu.</span><span class="sxs-lookup"><span data-stu-id="e8c05-139">Appending the identifier type character `$` to any identifier forces it to the `String` data type.</span></span> <span data-ttu-id="e8c05-140">`String` nemá žádné – znak typu literálu.</span><span class="sxs-lookup"><span data-stu-id="e8c05-140">`String` has no literal type character.</span></span> <span data-ttu-id="e8c05-141">Ale kompilátor zpracovává literály uzavřena v uvozovkách (`" "`) jako `String`.</span><span class="sxs-lookup"><span data-stu-id="e8c05-141">However, the compiler treats literals enclosed in quotation marks (`" "`) as `String`.</span></span>  
  
-   <span data-ttu-id="e8c05-142">**Typ Framework.**</span><span class="sxs-lookup"><span data-stu-id="e8c05-142">**Framework Type.**</span></span> <span data-ttu-id="e8c05-143">Typ odpovídající v rozhraní .NET Framework je <xref:System.String?displayProperty=nameWithType> třídy.</span><span class="sxs-lookup"><span data-stu-id="e8c05-143">The corresponding type in the .NET Framework is the <xref:System.String?displayProperty=nameWithType> class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8c05-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="e8c05-144">See Also</span></span>  
 <xref:System.String?displayProperty=nameWithType>  
 [<span data-ttu-id="e8c05-145">Datové typy</span><span class="sxs-lookup"><span data-stu-id="e8c05-145">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="e8c05-146">Datový typ Char</span><span class="sxs-lookup"><span data-stu-id="e8c05-146">Char Data Type</span></span>](../../../visual-basic/language-reference/data-types/char-data-type.md)  
 [<span data-ttu-id="e8c05-147">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="e8c05-147">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="e8c05-148">Souhrn převodu</span><span class="sxs-lookup"><span data-stu-id="e8c05-148">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="e8c05-149">Postupy: Volání funkce systému Windows, která přebírá nepřiřazené typy</span><span class="sxs-lookup"><span data-stu-id="e8c05-149">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [<span data-ttu-id="e8c05-150">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="e8c05-150">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
