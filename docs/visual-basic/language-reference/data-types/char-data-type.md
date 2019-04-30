---
title: Char – datový typ (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Char
helpviewer_keywords:
- literal type characters [Visual Basic], C
- Char data type
- C literal type character [Visual Basic]
- data types [Visual Basic], assigning
- Char data type [Visual Basic], character literals
ms.assetid: cd7547a9-7855-4e8e-b216-35d74a362657
ms.openlocfilehash: b50c902f69f7602dbad4663dc35bf0a2b932973f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61796978"
---
# <a name="char-data-type-visual-basic"></a><span data-ttu-id="bd7f9-102">Char – datový typ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bd7f9-102">Char Data Type (Visual Basic)</span></span>
<span data-ttu-id="bd7f9-103">Body bez znaménka 16bitový kódů (2bajtových) obsahuje v rozmezí od 0 do 65535.</span><span class="sxs-lookup"><span data-stu-id="bd7f9-103">Holds unsigned 16-bit (2-byte) code points ranging in value from 0 through 65535.</span></span> <span data-ttu-id="bd7f9-104">Každý *kódu bodu*, nebo kód znaku, představuje jeden znak Unicode.</span><span class="sxs-lookup"><span data-stu-id="bd7f9-104">Each *code point*, or character code, represents a single Unicode character.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bd7f9-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bd7f9-105">Remarks</span></span>  
 <span data-ttu-id="bd7f9-106">Použití `Char` datového typu, když budete chtít obsahovat pouze jeden znak a není nutné režii `String`.</span><span class="sxs-lookup"><span data-stu-id="bd7f9-106">Use the `Char` data type when you need to hold only a single character and do not need the overhead of `String`.</span></span> <span data-ttu-id="bd7f9-107">V některých případech můžete použít `Char()`, pole `Char` prvků pro uložení více znaků.</span><span class="sxs-lookup"><span data-stu-id="bd7f9-107">In some cases you can use `Char()`, an array of `Char` elements, to hold multiple characters.</span></span>  
  
 <span data-ttu-id="bd7f9-108">Výchozí hodnota `Char` je znak s bodem kódu 0.</span><span class="sxs-lookup"><span data-stu-id="bd7f9-108">The default value of `Char` is the character with a code point of 0.</span></span>  
  
## <a name="unicode-characters"></a><span data-ttu-id="bd7f9-109">Znaky kódování Unicode</span><span class="sxs-lookup"><span data-stu-id="bd7f9-109">Unicode Characters</span></span>  
 <span data-ttu-id="bd7f9-110">První body 128 kódu (0 – 127) Unicode odpovídají písmena a symboly na standardní klávesnici USA.</span><span class="sxs-lookup"><span data-stu-id="bd7f9-110">The first 128 code points (0–127) of Unicode correspond to the letters and symbols on a standard U.S. keyboard.</span></span> <span data-ttu-id="bd7f9-111">Tyto první body 128 kódu jsou stejné jako definuje znakové sady ASCII.</span><span class="sxs-lookup"><span data-stu-id="bd7f9-111">These first 128 code points are the same as those the ASCII character set defines.</span></span> <span data-ttu-id="bd7f9-112">Druhý body 128 kódu (128 – 255) představují speciální znaky, jako je například písmena abecedy latince, zvýraznění, symboly měny a podíly.</span><span class="sxs-lookup"><span data-stu-id="bd7f9-112">The second 128 code points (128–255) represent special characters, such as Latin-based alphabet letters, accents, currency symbols, and fractions.</span></span> <span data-ttu-id="bd7f9-113">Unicode používá pro širokou škálu symboly, včetně po celém světě textové znaky, diakritická znaménka a symboly technické a matematické zbývající body kódu (256 – 65535).</span><span class="sxs-lookup"><span data-stu-id="bd7f9-113">Unicode uses the remaining code points (256-65535) for a wide variety of symbols, including worldwide textual characters, diacritics, and mathematical and technical symbols.</span></span>  
  
 <span data-ttu-id="bd7f9-114">Můžete použít metody, jako je <xref:System.Char.IsDigit%2A> a <xref:System.Char.IsPunctuation%2A> na `Char` proměnnou k určení jeho klasifikace kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="bd7f9-114">You can use methods like <xref:System.Char.IsDigit%2A> and <xref:System.Char.IsPunctuation%2A> on a `Char` variable to determine its Unicode classification.</span></span>  
  
## <a name="type-conversions"></a><span data-ttu-id="bd7f9-115">Převody typu</span><span class="sxs-lookup"><span data-stu-id="bd7f9-115">Type Conversions</span></span>  
 <span data-ttu-id="bd7f9-116">Visual Basic nelze převést přímo mezi `Char` a číselné typy.</span><span class="sxs-lookup"><span data-stu-id="bd7f9-116">Visual Basic does not convert directly between `Char` and the numeric types.</span></span> <span data-ttu-id="bd7f9-117">Můžete použít <xref:Microsoft.VisualBasic.Strings.Asc%2A> nebo <xref:Microsoft.VisualBasic.Strings.AscW%2A> funkce pro převod `Char` hodnota, která se `Integer` , který představuje jeho bod kódu.</span><span class="sxs-lookup"><span data-stu-id="bd7f9-117">You can use the <xref:Microsoft.VisualBasic.Strings.Asc%2A> or <xref:Microsoft.VisualBasic.Strings.AscW%2A> function to convert a `Char` value to an `Integer` that represents its code point.</span></span> <span data-ttu-id="bd7f9-118">Můžete použít <xref:Microsoft.VisualBasic.Strings.Chr%2A> nebo <xref:Microsoft.VisualBasic.Strings.ChrW%2A> funkce pro převod `Integer` hodnota, která se `Char` , který má tento bod kódu.</span><span class="sxs-lookup"><span data-stu-id="bd7f9-118">You can use the <xref:Microsoft.VisualBasic.Strings.Chr%2A> or <xref:Microsoft.VisualBasic.Strings.ChrW%2A> function to convert an `Integer` value to a `Char` that has that code point.</span></span>  
  
 <span data-ttu-id="bd7f9-119">Pokud kontrola typu ([Option Strict – příkaz](../../../visual-basic/language-reference/statements/option-strict-statement.md)) je, – znak typu literálu musí připojit k literálu jedním znakem pro identifikaci jako `Char` datového typu.</span><span class="sxs-lookup"><span data-stu-id="bd7f9-119">If the type checking switch ([Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)) is on, you must append the literal type character to a single-character string literal to identify it as the `Char` data type.</span></span> <span data-ttu-id="bd7f9-120">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="bd7f9-120">The following example illustrates this.</span></span>  
  
```  
Option Strict On  
Dim charVar As Char  
' The following statement attempts to convert a String literal to Char.  
' Because Option Strict is On, it generates a compiler error.  
charVar = "Z"  
' The following statement succeeds because it specifies a Char literal.  
charVar = "Z"C  
```  
  
## <a name="programming-tips"></a><span data-ttu-id="bd7f9-121">Tipy k programování</span><span class="sxs-lookup"><span data-stu-id="bd7f9-121">Programming Tips</span></span>  
  
- <span data-ttu-id="bd7f9-122">**Záporná čísla.**</span><span class="sxs-lookup"><span data-stu-id="bd7f9-122">**Negative Numbers.**</span></span> <span data-ttu-id="bd7f9-123">`Char` je typ bez znaménka a nemůže představovat záporné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="bd7f9-123">`Char` is an unsigned type and cannot represent a negative value.</span></span> <span data-ttu-id="bd7f9-124">V každém případě byste neměli používat `Char` pro uložení číselné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="bd7f9-124">In any case, you should not use `Char` to hold numeric values.</span></span>  
  
- <span data-ttu-id="bd7f9-125">**Spolupráce aspekty.**</span><span class="sxs-lookup"><span data-stu-id="bd7f9-125">**Interop Considerations.**</span></span> <span data-ttu-id="bd7f9-126">Pokud používáte rozhraní s komponentami, které nejsou napsané pro rozhraní .NET Framework pro příklad objekty automatizace nebo COM, mějte na paměti, že typy znaků mají odlišnou datovou šířku (8 bitů) v jiných prostředích.</span><span class="sxs-lookup"><span data-stu-id="bd7f9-126">If you interface with components not written for the .NET Framework, for example Automation or COM objects, remember that character types have a different data width (8 bits) in other environments.</span></span> <span data-ttu-id="bd7f9-127">Pokud takové součásti předáváte 8bitové argument, deklarujte ho jako `Byte` místo `Char` v váš nový kód jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="bd7f9-127">If you pass an 8-bit argument to such a component, declare it as `Byte` instead of `Char` in your new Visual Basic code.</span></span>  
  
- <span data-ttu-id="bd7f9-128">**Rozšíření.**</span><span class="sxs-lookup"><span data-stu-id="bd7f9-128">**Widening.**</span></span> <span data-ttu-id="bd7f9-129">`Char` Datový typ rozšiřuje na `String`.</span><span class="sxs-lookup"><span data-stu-id="bd7f9-129">The `Char` data type widens to `String`.</span></span> <span data-ttu-id="bd7f9-130">To znamená, že můžete převést `Char` k `String` a nebude narazíte <xref:System.OverflowException?displayProperty=nameWithType> chyby.</span><span class="sxs-lookup"><span data-stu-id="bd7f9-130">This means you can convert `Char` to `String` and will not encounter a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="bd7f9-131">**Znaky typu.**</span><span class="sxs-lookup"><span data-stu-id="bd7f9-131">**Type Characters.**</span></span> <span data-ttu-id="bd7f9-132">Přidávání znak typu literálu `C` jeden znak řetězec literálu se z něj stane `Char` datového typu.</span><span class="sxs-lookup"><span data-stu-id="bd7f9-132">Appending the literal type character `C` to a single-character string literal forces it to the `Char` data type.</span></span> <span data-ttu-id="bd7f9-133">`Char` nemá žádné – znak typu identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="bd7f9-133">`Char` has no identifier type character.</span></span>  
  
- <span data-ttu-id="bd7f9-134">**Typ architektury.**</span><span class="sxs-lookup"><span data-stu-id="bd7f9-134">**Framework Type.**</span></span> <span data-ttu-id="bd7f9-135">Odpovídajícím typem v rozhraní .NET Framework je <xref:System.Char?displayProperty=nameWithType> struktury.</span><span class="sxs-lookup"><span data-stu-id="bd7f9-135">The corresponding type in the .NET Framework is the <xref:System.Char?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd7f9-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bd7f9-136">See also</span></span>

- <xref:System.Char?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [<span data-ttu-id="bd7f9-137">Datové typy</span><span class="sxs-lookup"><span data-stu-id="bd7f9-137">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="bd7f9-138">Datový typ String</span><span class="sxs-lookup"><span data-stu-id="bd7f9-138">String Data Type</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)
- [<span data-ttu-id="bd7f9-139">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="bd7f9-139">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="bd7f9-140">Souhrn převodu</span><span class="sxs-lookup"><span data-stu-id="bd7f9-140">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="bd7f9-141">Postupy: Volání funkce Windows, která přebírá typy bez znaménka</span><span class="sxs-lookup"><span data-stu-id="bd7f9-141">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="bd7f9-142">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="bd7f9-142">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
