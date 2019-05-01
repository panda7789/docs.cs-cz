---
title: Uinteger – datový typ (Visual Basic)
ms.date: 01/31/2018
f1_keywords:
- vb.uinteger
helpviewer_keywords:
- numbers [Visual Basic], whole
- UInteger data type
- literal type characters [Visual Basic], UI
- whole numbers
- integral data types [Visual Basic]
- integer numbers
- numbers [Visual Basic], integer
- integers [Visual Basic], data types
- integers [Visual Basic], types
- UI literal type characters [Visual Basic]
- data types [Visual Basic], integral
ms.assetid: db7ddd34-4f23-46f5-84dd-8b0f83bb8729
ms.openlocfilehash: 4d93b1e40371b00f9d1ff69ec31ad0983beb493f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61971727"
---
# <a name="uinteger-data-type"></a><span data-ttu-id="acab6-102">UInteger – datový typ</span><span class="sxs-lookup"><span data-stu-id="acab6-102">UInteger data type</span></span>

<span data-ttu-id="acab6-103">Obsahuje 32bitová (4bajtová) celá čísla bez znaménka v rozmezí od 0 do 4 294 967 295.</span><span class="sxs-lookup"><span data-stu-id="acab6-103">Holds unsigned 32-bit (4-byte) integers ranging in value from 0 through 4,294,967,295.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="acab6-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="acab6-104">Remarks</span></span>

 <span data-ttu-id="acab6-105">`UInteger` Datový typ poskytuje největší hodnoty bez znaménka na nejúčinnější šířku data.</span><span class="sxs-lookup"><span data-stu-id="acab6-105">The `UInteger` data type provides the largest unsigned value in the most efficient data width.</span></span>  
  
 <span data-ttu-id="acab6-106">Výchozí hodnota `UInteger` je 0.</span><span class="sxs-lookup"><span data-stu-id="acab6-106">The default value of `UInteger` is 0.</span></span>  
  
## <a name="literal-assignments"></a><span data-ttu-id="acab6-107">Literál přiřazení</span><span class="sxs-lookup"><span data-stu-id="acab6-107">Literal assignments</span></span>

<span data-ttu-id="acab6-108">Můžete deklarovat a inicializovat `UInteger` proměnnou ji přiřadíte desítkový literál, šestnáctkové literál, osmičkové literální, nebo (od verze 2017 jazyka Visual Basic) binární literál.</span><span class="sxs-lookup"><span data-stu-id="acab6-108">You can declare and initialize a `UInteger` variable by assigning it a decimal literal, a hexadecimal literal, an octal literal, or (starting with Visual Basic 2017) a binary literal.</span></span> <span data-ttu-id="acab6-109">Pokud celočíselný literál je mimo rozsah `UInteger` (tj. Pokud je menší než <xref:System.UInt32.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, dojde k chybě kompilace.</span><span class="sxs-lookup"><span data-stu-id="acab6-109">If the integer literal is outside the range of `UInteger` (that is, if it is less than <xref:System.UInt32.MinValue?displayProperty=nameWithType> or greater than <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, a compilation error occurs.</span></span>

<span data-ttu-id="acab6-110">V následujícím příkladu celých čísel je rovno 3,000,000,000, které jsou reprezentovány jako desítkové, hexadecimální, a binární literály jsou přiřazeny k `UInteger` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="acab6-110">In the following example, integers equal to 3,000,000,000 that are represented as decimal, hexadecimal, and binary literals are assigned to `UInteger` values.</span></span>
  
[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UInt)]  

> [!NOTE] 
> <span data-ttu-id="acab6-111">Použijte předponu `&h` nebo `&H` k označení šestnáctkové literálu předpona `&b` nebo `&B` k označení binárního typu literal a předponu `&o` nebo `&O` k označení osmičkové literální.</span><span class="sxs-lookup"><span data-stu-id="acab6-111">You use the prefix `&h` or `&H` to denote a hexadecimal literal, the prefix `&b` or `&B` to denote a binary literal, and the prefix `&o` or `&O` to denote an octal literal.</span></span> <span data-ttu-id="acab6-112">Desítkové literály mají žádná předpona.</span><span class="sxs-lookup"><span data-stu-id="acab6-112">Decimal literals have no prefix.</span></span>

<span data-ttu-id="acab6-113">Počínaje rokem 2017 jazyka Visual Basic, můžete použít také znak podtržítka `_`, jako oddělovač číslice za účelem zlepšení čitelnosti jako následující příklad ukazuje.</span><span class="sxs-lookup"><span data-stu-id="acab6-113">Starting with Visual Basic 2017, you can also use the underscore character, `_`, as a digit separator to enhance readability, as the following example shows.</span></span>

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UIntS)]  

<span data-ttu-id="acab6-114">Od verze 15.5 jazyka Visual Basic, můžete také použít znak podtržítka (`_`) jako počáteční oddělovač mezi prefix a šestnáctkové, binární nebo osmičkové číslice.</span><span class="sxs-lookup"><span data-stu-id="acab6-114">Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits.</span></span> <span data-ttu-id="acab6-115">Příklad:</span><span class="sxs-lookup"><span data-stu-id="acab6-115">For example:</span></span>

```vb
Dim number As UInteger = &H_0F8C_0326
```

[!INCLUDE [supporting-underscores](../../../../includes/vb-separator-langversion.md)]

<span data-ttu-id="acab6-116">Číselné literály může také zahrnovat `UI` nebo `ui` [znak](../../programming-guide/language-features/data-types/type-characters.md) k označení `UInteger` datového typu, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="acab6-116">Numeric literals can also include the `UI` or `ui` [type character](../../programming-guide/language-features/data-types/type-characters.md) to denote the `UInteger` data type, as the following example shows.</span></span>

```vb
Dim number = &H_0FAC_14D7ui
```

## <a name="programming-tips"></a><span data-ttu-id="acab6-117">Tipy pro programování</span><span class="sxs-lookup"><span data-stu-id="acab6-117">Programming tips</span></span>

 <span data-ttu-id="acab6-118">`UInteger` a `Integer` datových typů poskytuje optimální výkon na 32bitových procesorech, protože menší typy celých čísel (`UShort`, `Short`, `Byte`, a `SByte`), i když používají menší počet bitů, trvat déle načíst, uložit a načíst.</span><span class="sxs-lookup"><span data-stu-id="acab6-118">The `UInteger` and `Integer` data types provide optimal performance on a 32-bit processor, because the smaller integer types (`UShort`, `Short`, `Byte`, and `SByte`), even though they use fewer bits, take more time to load, store, and fetch.</span></span>  
  
- <span data-ttu-id="acab6-119">**Záporná čísla.**</span><span class="sxs-lookup"><span data-stu-id="acab6-119">**Negative Numbers.**</span></span> <span data-ttu-id="acab6-120">Protože `UInteger` typ bez znaménka, je ho nemůže představovat záporné číslo.</span><span class="sxs-lookup"><span data-stu-id="acab6-120">Because `UInteger` is an unsigned type, it cannot represent a negative number.</span></span> <span data-ttu-id="acab6-121">Pokud používáte Unární minus (`-`) operátor na výraz, který se vyhodnotí na typ `UInteger`, Visual Basic Převede výraz, který má `Long` první.</span><span class="sxs-lookup"><span data-stu-id="acab6-121">If you use the unary minus (`-`) operator on an expression that evaluates to type `UInteger`, Visual Basic converts the expression to `Long` first.</span></span>  
  
- <span data-ttu-id="acab6-122">**Dodržování specifikace CLS.**</span><span class="sxs-lookup"><span data-stu-id="acab6-122">**CLS Compliance.**</span></span> <span data-ttu-id="acab6-123">`UInteger` Datový typ není součástí [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), takže kód kompatibilní se Specifikací CLS nemůže využívat komponentu, která ji používá.</span><span class="sxs-lookup"><span data-stu-id="acab6-123">The `UInteger` data type is not part of the [Common Language Specification](https://www.ecma-international.org/publications/standards/Ecma-335.htm) (CLS), so CLS-compliant code cannot consume a component that uses it.</span></span>
  
- <span data-ttu-id="acab6-124">**Spolupráce aspekty.**</span><span class="sxs-lookup"><span data-stu-id="acab6-124">**Interop Considerations.**</span></span> <span data-ttu-id="acab6-125">Při vzájemném propojování součástí, které nejsou napsané pro rozhraní .NET Framework, například objekty automatizace nebo COM, mějte na paměti, že typy, jako `uint` může mít v jiných prostředích odlišnou datovou šířku (16 bitů).</span><span class="sxs-lookup"><span data-stu-id="acab6-125">If you are interfacing with components not written for the .NET Framework, for example Automation or COM objects, keep in mind that types such as `uint` can have a different data width (16 bits) in other environments.</span></span> <span data-ttu-id="acab6-126">Pokud takové součásti předáváte 16bitový argument, deklarujte ho jako `UShort` místo `UInteger` v spravovaného kódu jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="acab6-126">If you are passing a 16-bit argument to such a component, declare it as `UShort` instead of `UInteger` in your managed Visual Basic code.</span></span>  
  
- <span data-ttu-id="acab6-127">**Rozšíření.**</span><span class="sxs-lookup"><span data-stu-id="acab6-127">**Widening.**</span></span> <span data-ttu-id="acab6-128">`UInteger` Datový typ rozšiřuje na `Long`, `ULong`, `Decimal`, `Single`, a `Double`.</span><span class="sxs-lookup"><span data-stu-id="acab6-128">The `UInteger` data type widens to `Long`, `ULong`, `Decimal`, `Single`, and `Double`.</span></span> <span data-ttu-id="acab6-129">To znamená, že můžete převést `UInteger` ke kterékoli z těchto typů, aniž se objeví <xref:System.OverflowException?displayProperty=nameWithType> chyby.</span><span class="sxs-lookup"><span data-stu-id="acab6-129">This means you can convert `UInteger` to any of these types without encountering a <xref:System.OverflowException?displayProperty=nameWithType> error.</span></span>  
  
- <span data-ttu-id="acab6-130">**Znaky typu.**</span><span class="sxs-lookup"><span data-stu-id="acab6-130">**Type Characters.**</span></span> <span data-ttu-id="acab6-131">Přidávání znaky literálového typu `UI` k literálu se z něj stane `UInteger` datového typu.</span><span class="sxs-lookup"><span data-stu-id="acab6-131">Appending the literal type characters `UI` to a literal forces it to the `UInteger` data type.</span></span> <span data-ttu-id="acab6-132">`UInteger` nemá žádné – znak typu identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="acab6-132">`UInteger` has no identifier type character.</span></span>  
  
- <span data-ttu-id="acab6-133">**Typ architektury.**</span><span class="sxs-lookup"><span data-stu-id="acab6-133">**Framework Type.**</span></span> <span data-ttu-id="acab6-134">Odpovídajícím typem v rozhraní .NET Framework je <xref:System.UInt32?displayProperty=nameWithType> struktury.</span><span class="sxs-lookup"><span data-stu-id="acab6-134">The corresponding type in the .NET Framework is the <xref:System.UInt32?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acab6-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="acab6-135">See also</span></span>

- <xref:System.UInt32>
- [<span data-ttu-id="acab6-136">Datové typy</span><span class="sxs-lookup"><span data-stu-id="acab6-136">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="acab6-137">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="acab6-137">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="acab6-138">Souhrn převodu</span><span class="sxs-lookup"><span data-stu-id="acab6-138">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="acab6-139">Postupy: Volání funkce Windows, která přebírá typy bez znaménka</span><span class="sxs-lookup"><span data-stu-id="acab6-139">How to: Call a Windows Function that Takes Unsigned Types</span></span>](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [<span data-ttu-id="acab6-140">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="acab6-140">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
