---
title: Vnořené typy – C# Průvodce programováním
ms.date: 07/10/2017
helpviewer_keywords:
- nested types [C#]
ms.assetid: f2e1b315-e3d1-48ce-977f-7bae0960ba99
ms.openlocfilehash: 982eeceb2088dd6e1e57fe796b38e46c0f2d4de8
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705493"
---
# <a name="nested-types-c-programming-guide"></a>Vnořené typy (Průvodce programováním v C#)
Typ definovaný v rámci [třídy](../../language-reference/keywords/class.md) nebo [struktury](../../language-reference/keywords/struct.md) se nazývá vnořený typ. Příklad:  
  
 [!code-csharp[csProgGuideObjects#68](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#68)]  
  
Bez ohledu na to, zda je vnější typ třída nebo struktura, vnořené typy jsou standardně [soukromé](../../language-reference/keywords/private.md); jsou přístupné pouze z jejich nadřazeného typu. V předchozím příkladu je třída `Nested` nepřístupná externím typům. 

Můžete také zadat [modifikátor přístupu](../../language-reference/keywords/access-modifiers.md) pro definování přístupnosti vnořeného typu, a to následujícím způsobem:

- Vnořené typy **třídy** můžou být [veřejné](../../language-reference/keywords/public.md), [chráněné](../../language-reference/keywords/protected.md), [interní](../../language-reference/keywords/internal.md), [chráněné interní](../../language-reference/keywords/protected-internal.md), [privátní](../../language-reference/keywords/private.md) nebo [privátní](../../language-reference/keywords/private-protected.md). 

   Nicméně definování `protected`, `protected internal` nebo `private protected` vnořené třídy v [zapečetěné třídě](../../language-reference/keywords/sealed.md) vygeneruje upozornění kompilátoru [CS0628](../../misc/cs0628.md), v zapečetěné třídě je deklarovaný nový chráněný člen.
  
- Vnořené typy **struktury** můžou být [veřejné](../../language-reference/keywords/public.md), [interní](../../language-reference/keywords/internal.md)nebo [soukromé](../../language-reference/keywords/private.md).
  
Následující příklad nastaví `Nested` třídy jako veřejné:
  
 [!code-csharp[csProgGuideObjects#69](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#69)]  
  
 Vnořený nebo vnitřní typ může přistupovat k typu, který obsahuje, nebo vnějšímu typu. Chcete-li získat přístup k nadřazenému typu, předejte jej jako argument konstruktoru vnořeného typu. Příklad:  
  
 [!code-csharp[csProgGuideObjects#70](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#70)]  
  
 Vnořený typ má přístup ke všem členům, kteří mají přístup k jeho nadřazenému typu. Má přístup k soukromým a chráněným členům nadřazeného typu, včetně všech zděděných chráněných členů.  
  
 V předchozí deklaraci je úplný název třídy `Nested` `Container.Nested`. Toto je název, který se používá k vytvoření nové instance vnořené třídy následujícím způsobem:  
  
 [!code-csharp[csProgGuideObjects#71](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#71)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Třídy a struktury](./index.md)
- [Modifikátory přístupu](./access-modifiers.md)
- [Konstruktory](./constructors.md)
