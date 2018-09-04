---
title: Vnořené typy (Průvodce programováním v C#)
ms.date: 07/10/2017
helpviewer_keywords:
- nested types [C#]
ms.assetid: f2e1b315-e3d1-48ce-977f-7bae0960ba99
ms.openlocfilehash: f99b84d5b21261fa81c02d028d1f913be7290dbb
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43564366"
---
# <a name="nested-types-c-programming-guide"></a>Vnořené typy (Průvodce programováním v C#)
Typ definovaný v rámci [třídy](../../../csharp/language-reference/keywords/class.md) nebo [struktura](../../../csharp/language-reference/keywords/struct.md) se nazývá vnořený typ. Příklad:  
  
[!code-csharp[csProgGuideObjects#68](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_1.cs)]  
  
Bez ohledu na to, zda je vnější typ třída nebo struktura, vnořené typy jsou přednastaveny na [privátní](../../../csharp/language-reference/keywords/private.md); jsou přístupné jenom z jeho nadřazeného typu. V předchozím příkladu `Nested` třídy je nedostupný pro externí typy. 

Můžete také určit, [modifikátor přístupu](../../language-reference/keywords/access-modifiers.md) k definování přístupnost vnořeného typu, následujícím způsobem:

- Vnořené typy **třídy** může být [veřejné](../../../csharp/language-reference/keywords/public.md), [chráněné](../../../csharp/language-reference/keywords/protected.md), [interní](../../../csharp/language-reference/keywords/internal.md), [interní chráněné](../../../csharp/language-reference/keywords/protected-internal.md), [privátní](../../../csharp/language-reference/keywords/private.md) nebo [private, protected](../../../csharp/language-reference/keywords/private-protected.md). 

   Ale definování `protected`, `protected internal` nebo `private protected` vnořenou třídu uvnitř [zapečetěná třída](../../language-reference/keywords/sealed.md) generuje upozornění kompilátoru [CS0628](../../misc/cs0628.md), "deklarovaný nový chráněný člen v zapečetěné třídě."
  
- Vnořené typy **struktura** může být [veřejné](../../../csharp/language-reference/keywords/public.md), [interní](../../../csharp/language-reference/keywords/internal.md), nebo [privátní](../../../csharp/language-reference/keywords/private.md).
  
Následující příklad provede `Nested` veřejné třídy:
  
[!code-csharp[csProgGuideObjects#69](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_2.cs)]  
  
 Typ vnořený nebo vnitřní, můžete získat přístup k obsahujícímu nebo vnějšímu, typu. Pro přístup k nadřazeného typu, předejte ji jako argument konstruktoru vnořeného typu. Příklad:  
  
 [!code-csharp[csProgGuideObjects#70](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_3.cs)]  
  
 Vnořený typ má přístup ke všem členům, kteří jsou k dispozici k jeho nadřazeného typu. Má přístup k soukromým a chráněným členům nadřazeného typu, včetně všech zděděných chráněných členů.  
  
 V předchozí prohlášení, úplný název třídy `Nested` je `Container.Nested`. Toto je název používaný k vytvoření nové instance vnořené třídy takto:  
  
 [!code-csharp[csProgGuideObjects#71](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/nested-types_4.cs)]  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [Modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
- [Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md)
