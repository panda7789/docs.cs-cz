---
title: "Char – datový typ (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Char
helpviewer_keywords:
- literal type characters [Visual Basic], C
- Char data type
- C literal type character [Visual Basic]
- data types [Visual Basic], assigning
- Char data type [Visual Basic], character literals
ms.assetid: cd7547a9-7855-4e8e-b216-35d74a362657
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 16ff547fccbf4481d31ca79537962cc7090fc9b0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="char-data-type-visual-basic"></a><span data-ttu-id="f4672-102">Char – datový typ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f4672-102">Char Data Type (Visual Basic)</span></span>
<span data-ttu-id="f4672-103">Blokování nepodepsaného kódu (2bajtová) 16bitové body v rozmezí od 0 do 65535.</span><span class="sxs-lookup"><span data-stu-id="f4672-103">Holds unsigned 16-bit (2-byte) code points ranging in value from 0 through 65535.</span></span> <span data-ttu-id="f4672-104">Každý *code bodu*, nebo kód znaku, představuje jeden znak Unicode.</span><span class="sxs-lookup"><span data-stu-id="f4672-104">Each *code point*, or character code, represents a single Unicode character.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f4672-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f4672-105">Remarks</span></span>  
 <span data-ttu-id="f4672-106">Použití `Char` datový typ, když potřebujete obsahovat jenom jeden znak a není nutné nároky na `String`.</span><span class="sxs-lookup"><span data-stu-id="f4672-106">Use the `Char` data type when you need to hold only a single character and do not need the overhead of `String`.</span></span> <span data-ttu-id="f4672-107">V některých případech můžete použít `Char()`, pole `Char` elementy pro uložení více znaků.</span><span class="sxs-lookup"><span data-stu-id="f4672-107">In some cases you can use `Char()`, an array of `Char` elements, to hold multiple characters.</span></span>  
  
 <span data-ttu-id="f4672-108">Výchozí hodnota `Char` je znak s bodem kód 0.</span><span class="sxs-lookup"><span data-stu-id="f4672-108">The default value of `Char` is the character with a code point of 0.</span></span>  
  
## <a name="unicode-characters"></a><span data-ttu-id="f4672-109">Znaky kódování Unicode</span><span class="sxs-lookup"><span data-stu-id="f4672-109">Unicode Characters</span></span>  
 <span data-ttu-id="f4672-110">První body 128 kódu (0 – 127) Unicode odpovídají písmena a symboly standardní klávesnicích.</span><span class="sxs-lookup"><span data-stu-id="f4672-110">The first 128 code points (0–127) of Unicode correspond to the letters and symbols on a standard U.S. keyboard.</span></span> <span data-ttu-id="f4672-111">Tyto první 128 kód body jsou stejné jako definuje znaková sada ASCII.</span><span class="sxs-lookup"><span data-stu-id="f4672-111">These first 128 code points are the same as those the ASCII character set defines.</span></span> <span data-ttu-id="f4672-112">Druhý body 128 kódu (128 – 255) představují speciální znaky, jako je například písmena abecedy latince, zvýraznění, tyto symboly a zlomků.</span><span class="sxs-lookup"><span data-stu-id="f4672-112">The second 128 code points (128–255) represent special characters, such as Latin-based alphabet letters, accents, currency symbols, and fractions.</span></span> <span data-ttu-id="f4672-113">Unicode používá zbývající body kódu (256 65 535) pro širokou škálu symboly, včetně po celém světě textové znaky, znaky s diakritikou a matematické a technické symboly.</span><span class="sxs-lookup"><span data-stu-id="f4672-113">Unicode uses the remaining code points (256-65535) for a wide variety of symbols, including worldwide textual characters, diacritics, and mathematical and technical symbols.</span></span>  
  
 <span data-ttu-id="f4672-114">Můžete použít metody, třeba <xref:System.Char.IsDigit%2A> a <xref:System.Char.IsPunctuation%2A> na `Char` proměnné můžete zjistit klasifikaci kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="f4672-114">You can use methods like <xref:System.Char.IsDigit%2A> and <xref:System.Char.IsPunctuation%2A> on a `Char` variable to determine its Unicode classification.</span></span>  
  
## <a name="type-conversions"></a><span data-ttu-id="f4672-115">Převody typu</span><span class="sxs-lookup"><span data-stu-id="f4672-115">Type Conversions</span></span>  
 <span data-ttu-id="f4672-116">Visual Basic nepřevede přímo mezi `Char` a číselnými typy.</span><span class="sxs-lookup"><span data-stu-id="f4672-116">Visual Basic does not convert directly between `Char` and the numeric types.</span></span> <span data-ttu-id="f4672-117">Můžete použít <xref:Microsoft.VisualBasic.Strings.Asc%2A> nebo <xref:Microsoft.VisualBasic.Strings.AscW%2A> funkce pro převod `Char` hodnotu `Integer` představující jeho bod kódu.</span><span class="sxs-lookup"><span data-stu-id="f4672-117">You can use the <xref:Microsoft.VisualBasic.Strings.Asc%2A> or <xref:Microsoft.VisualBasic.Strings.AscW%2A> function to convert a `Char` value to an `Integer` that represents its code point.</span></span> <span data-ttu-id="f4672-118">Můžete použít <xref:Microsoft.VisualBasic.Strings.Chr%2A> nebo <xref:Microsoft.VisualBasic.Strings.ChrW%2A> funkce pro převod `Integer` hodnotu `Char` obsahujícím bod tohoto kódu.</span><span class="sxs-lookup"><span data-stu-id="f4672-118">You can use the <xref:Microsoft.VisualBasic.Strings.Chr%2A> or <xref:Microsoft.VisualBasic.Strings.ChrW%2A> function to convert an `Integer` value to a `Char` that has that code point.</span></span>  
  
 <span data-ttu-id="f4672-119">Pokud kontrola typu přepínač ([Option Strict – příkaz](../../../visual-basic/language-reference/statements/option-strict-statement.md)) je na znak typu literálu musí připojit k délce jednoho znaku řetězcový literál pro identifikaci jako `Char` datového typu.</span><span class="sxs-lookup"><span data-stu-id="f4672-119">If the type checking switch ([Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)) is on, you must append the literal type character to a single-character string literal to identify it as the `Char` data type.</span></span> <span data-ttu-id="f4672-120">Toto dokládá následující příklad.</span><span class="sxs-lookup"><span data-stu-id="f4672-120">The following example illustrates this.</span></span>  
  
```  
Option Strict On  
Dim charVar As Char  
' The following statement attempts to convert a String literal to Char.  
' Because Option Strict is On, it generates a compiler error.  
charVar = "Z"  
' The following statement succeeds because it specifies a Char literal.  
charVar = "Z"C  
```  
  
## <a name="programming-tips"></a><span data-ttu-id="f4672-121">Tipy k programování</span><span class="sxs-lookup"><span data-stu-id="f4672-121">Programming Tips</span></span>  
  
-   <span data-ttu-id="f4672-122">**Záporná čísla.**</span><span class="sxs-lookup"><span data-stu-id="f4672-122">**Negative Numbers.**</span></span> <span data-ttu-id="f4672-123">`Char`je typu bez znaménka a nemůže představují zápornou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f4672-123">`Char` is an unsigned type and cannot represent a negative value.</span></span> <span data-ttu-id="f4672-124">V každém případě byste neměli používat `Char` pro uložení číselné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f4672-124">In any case, you should not use `Char` to hold numeric values.</span></span>  
  
-   <span data-ttu-id="f4672-125">**Spolupráce aspekty.**</span><span class="sxs-lookup"><span data-stu-id="f4672-125">**Interop Considerations.**</span></span> <span data-ttu-id="f4672-126">Pokud rozhraní s komponentami nezapíše pro rozhraní .NET Framework pro příklad objekty automatizace nebo COM, mějte na paměti, že typy znaků mají různé datové šířka (8 bitů) v jiných prostředích.</span><span class="sxs-lookup"><span data-stu-id="f4672-126">If you interface with components not written for the .NET Framework, for example Automation or COM objects, remember that character types have a different data width (8 bits) in other environments.</span></span> <span data-ttu-id="f4672-127">Pokud předáte 8bitové argument pro tyto součásti, deklarujte ji jako `Byte` místo `Char` v váš nový kód jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="f4672-127">If you pass an 8-bit argument to such a component, declare it as `Byte` instead of `Char` in your new Visual Basic code.</span></span>  
  
-   <span data-ttu-id="f4672-128">**Rozšíření.**</span><span class="sxs-lookup"><span data-stu-id="f4672-128">**Widening.**</span></span> <span data-ttu-id="f4672-129">`Char` Datový typ rozšiřuje na `String`.</span><span class="sxs-lookup"><span data-stu-id="f4672-129">The `Char` data type widens to `String`.</span></span> <span data-ttu-id="f4672-130">To znamená, že můžete převést `Char` k `String` a nebude narazíte <xref:System.OverflowException?displayProperty=nameWithType> chyby.</span><span class="sxs-lookup"><span data-stu-id="f4672-130">This means you can convert `Char` to `String` and will not encounter a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
-   <span data-ttu-id="f4672-131">**Znaky typu.**</span><span class="sxs-lookup"><span data-stu-id="f4672-131">**Type Characters.**</span></span> <span data-ttu-id="f4672-132">Připojování znak typu literálu `C` na řetězec délce jednoho znaku literál vynutí, aby `Char` datového typu.</span><span class="sxs-lookup"><span data-stu-id="f4672-132">Appending the literal type character `C` to a single-character string literal forces it to the `Char` data type.</span></span> <span data-ttu-id="f4672-133">`Char`nemá žádné – znak typu identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="f4672-133">`Char` has no identifier type character.</span></span>  
  
-   <span data-ttu-id="f4672-134">**Typ Framework.**</span><span class="sxs-lookup"><span data-stu-id="f4672-134">**Framework Type.**</span></span> <span data-ttu-id="f4672-135">Typ odpovídající v rozhraní .NET Framework je <xref:System.Char?displayProperty=nameWithType> struktura.</span><span class="sxs-lookup"><span data-stu-id="f4672-135">The corresponding type in the .NET Framework is the <xref:System.Char?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4672-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="f4672-136">See Also</span></span>  
 <xref:System.Char?displayProperty=nameWithType>  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 <xref:Microsoft.VisualBasic.Strings.Chr%2A>  
 <xref:Microsoft.VisualBasic.Strings.ChrW%2A>  
 [<span data-ttu-id="f4672-137">Datové typy</span><span class="sxs-lookup"><span data-stu-id="f4672-137">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="f4672-138">String – datový typ</span><span class="sxs-lookup"><span data-stu-id="f4672-138">String Data Type</span></span>](../../../visual-basic/language-reference/data-types/string-data-type.md)  
 [<span data-ttu-id="f4672-139">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="f4672-139">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="f4672-140">Souhrn konverze</span><span class="sxs-lookup"><span data-stu-id="f4672-140">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="f4672-141">Postupy: volání funkce systému Windows, která přebírá nepřiřazené typy</span><span class="sxs-lookup"><span data-stu-id="f4672-141">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [<span data-ttu-id="f4672-142">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="f4672-142">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
