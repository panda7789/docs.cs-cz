---
title: "Vnořené typy (Průvodce programováním v C#)"
ms.date: 07/10/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: nested types [C#]
ms.assetid: f2e1b315-e3d1-48ce-977f-7bae0960ba99
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ab13c68b638062ab89c90dbfc51b51b8d72d3bde
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="nested-types-c-programming-guide"></a>Vnořené typy (Průvodce programováním v C#)
Typem definovaným v rámci [třída](../../../csharp/language-reference/keywords/class.md) nebo [struktura](../../../csharp/language-reference/keywords/struct.md) nazývá vnořené typy. Příklad:  
  
[!code-csharp[csProgGuideObjects#68](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_1.cs)]  
  
Bez ohledu na to, jestli je vnější typ třídy nebo struktury, jako výchozí vnořené typy [privátní](../../../csharp/language-reference/keywords/private.md); jsou přístupné pouze z jejich nadřazeného typu. V předchozím příkladu `Nested` třída je dostupná pro externí typy. 

Můžete také určit, [– modifikátor přístupu](../../language-reference/keywords/access-modifiers.md) k usnadnění vnořeného typu, definujte takto:

- Vnořené typy **třída** může být [veřejné](../../../csharp/language-reference/keywords/public.md), [chráněné](../../../csharp/language-reference/keywords/protected.md), [interní](../../../csharp/language-reference/keywords/internal.md), [chráněné interní](../../../csharp/language-reference/keywords/protected-internal.md), [privátní](../../../csharp/language-reference/keywords/private.md) nebo [privátní chráněné](../../../csharp/language-reference/keywords/private-protected.md). 

   Definování však `protected`, `protected internal` nebo `private protected` vnořené třídy uvnitř [zapečetěné třídy](../../language-reference/keywords/sealed.md) vygeneruje upozornění kompilátoru [CS0628](../../misc/cs0628.md), "nové chráněného člena deklarovaná ve třídě zapečetěné."
  
- Vnořené typy **struktura** může být [veřejné](../../../csharp/language-reference/keywords/public.md), [interní](../../../csharp/language-reference/keywords/internal.md), nebo [privátní](../../../csharp/language-reference/keywords/private.md).
  
Následující příklad vytvoří `Nested` veřejné třídy:
  
[!code-csharp[csProgGuideObjects#69](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_2.cs)]  
  
 Typ vnořené nebo vnitřní, můžete přistupovat obsahující nebo vnější typu. Pro přístup k obsahující typ, předejte jako argument konstruktoru typu vnořené. Příklad:  
  
 [!code-csharp[csProgGuideObjects#70](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_3.cs)]  
  
 Vnořené typy má přístup do všech členů, které jsou přístupné pro jeho nadřazeného typu. Má přístup k privátním a chráněné členy obsahující typu, včetně všech zděděné chráněné členy.  
  
 V předchozích deklaraci, úplný název třídy `Nested` je `Container.Nested`. Toto je název sloužící k vytvoření nové instance vnořené třídy následujícím způsobem:  
  
 [!code-csharp[csProgGuideObjects#71](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_4.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)
