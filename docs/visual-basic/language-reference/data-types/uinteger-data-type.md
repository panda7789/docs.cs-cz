---
title: "UInteger – datový typ"
ms.date: 04/20/2017
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.uinteger
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
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f3852bd56d11c19e327e6c2f3e23cfb082a54e0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="uinteger-data-type"></a>UInteger – datový typ

(Blokování nepodepsaných 32-bit 4bajtový) typ Integer v rozmezí od 0 do 4 294 967 295.  
  
## <a name="remarks"></a>Poznámky

 `UInteger` Datový typ poskytuje největší hodnotu bez znaménka nejúčinnější šířku data.  
  
 Výchozí hodnota `UInteger` je 0.  
  
## <a name="literal-assignments"></a>Literál přiřazení

Můžete deklarace a inicializace `UInteger` proměnné jeho přiřazení decimal literál, hexadecimální literál, osmičková literál, nebo (počínaje 2017 Visual Basic) binární literál. Pokud literálu celé číslo je mimo rozsah `UInteger` (tj. Pokud je menší než <xref:System.UInt32.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, dojde k chybě kompilace.

V následujícím příkladu, celá čísla rovno 3,000,000,000, která jsou reprezentovány jako decimal, šestnáctkové, a binární literály jsou přiřazeny k `UInteger` hodnoty.
  
[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UInt)]  

> [!NOTE] 
> Použijte předponu `&h` nebo `&H` k označení hexadecimální literál, předponu `&b` nebo `&B` k označení binární literál a předponu `&o` nebo `&O` k označení osmičková literál. Decimal literály mít žádná předpona.

Počínaje 2017 Visual Basic, můžete také použít znak podtržítka `_`, jako oddělovač číslice za účelem zlepšení čitelnosti jako následující příklad ukazuje.

[!code-vb[UInteger](../../../../samples/snippets/visualbasic/language-reference/data-types/numeric-literals.vb#UIntS)]  

Číselné literály může také obsahovat `UI` nebo `ui` [znak typu](../../programming-guide\language-features\data-types/type-characters.md) k označení `UInteger` datového typu, jak ukazuje následující příklad.

```vb
Dim number = &H0FAC14D7ui
```

## <a name="programming-tips"></a>Tipy pro programování

 `UInteger` a `Integer` datové typy poskytnout optimální výkon procesoru 32-bit, protože menší typy celého čísla (`UShort`, `Short`, `Byte`, a `SByte`), i když používají méně bits trvat déle načtení, uložení a načtení.  
  
-   **Záporná čísla.** Protože `UInteger` je typ bez znaménka, nelze ho představují záporné číslo. Pokud používáte Unární minus (`-`) operátor na výraz, který se vyhodnotí na typ `UInteger`, Visual Basic Převede výraz, který se `Long` první.  
  
-   **Souladu se specifikací CLS.** `UInteger` Datový typ není součástí [Common Language Specification](http://www.ecma-international.org/publications/standards/Ecma-335.htm) CLS (), takže kompatibilní se specifikací CLS kódu nemůže využívat komponenty, která se používá.
  
-   **Spolupráce aspekty.** Pokud jsou během propojení s součásti, které nejsou určeny pro rozhraní .NET Framework pro příklad objekty automatizace nebo COM, mějte na paměti, které typy, jako `uint` může mít různé datové šířka (16 bitů) v jiných prostředích. Argument 16bitové předáte pro tyto součásti, deklarujte ji jako `UShort` místo `UInteger` v spravovaného kódu jazyka Visual Basic.  
  
-   **Rozšíření.** `UInteger` Datový typ rozšiřuje na `Long`, `ULong`, `Decimal`, `Single`, a `Double`. To znamená, že můžete převést `UInteger` na některý z těchto typů bez zjištění <xref:System.OverflowException?displayProperty=nameWithType> chyby.  
  
-   **Znaky typu.** Připojování znaky typu literálu `UI` k literál vynutí, aby `UInteger` datového typu. `UInteger`nemá žádné – znak typu identifikátoru.  
  
-   **Typ Framework.** Typ odpovídající v rozhraní .NET Framework je <xref:System.UInt32?displayProperty=nameWithType> struktura.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.UInt32>  
 [Datové typy](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Souhrn konverze](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Postupy: volání funkce systému Windows, která přebírá nepřiřazené typy](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [Účinné používání datových typů](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
