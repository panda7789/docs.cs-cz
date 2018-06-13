---
title: protected (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- protected
- protected_CSharpKeyword
helpviewer_keywords:
- protected keyword [C#]
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
ms.openlocfilehash: a3115fe82b452f52ee75cf222302ece0fc67b330
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269567"
---
# <a name="protected-c-reference"></a>protected (Referenční dokumentace jazyka C#)
`protected` – Klíčové slovo je modifikátor přístupu členů. 

 > Tato stránka popisuje `protected` přístup. `protected` – Klíčové slovo je také součástí [ `protected internal` ](./protected-internal.md) a [ `private protected` ](./private-protected.md) přístup modifikátory. 

Chráněný člen je přístupný v rámci své třídy a instance odvozené třídy. 

Porovnání `protected` s další modifikátory přístupu, přečtěte si téma [úrovní přístupu](../../../csharp/language-reference/keywords/accessibility-levels.md). 
  
## <a name="example"></a>Příklad  
 Chráněný člen základní třídy je dostupné v odvozené třídě pouze v případě, že dojde k přístupu prostřednictvím typu odvozené třídy. Zvažte například následující segment kódu:  
  
 [!code-csharp[csrefKeywordsModifiers#11](../../../csharp/language-reference/keywords/codesnippet/CSharp/protected_1.cs)]  
  
 Příkaz `a.x = 10` vygeneruje chybu, protože se provádí v rámci statickou metodu Main, a ne instance třídy B.  
  
 Členové struktury nelze chránit, protože nelze zděděná struct.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu třída `DerivedPoint` je odvozený od `Point`. Proto můžete přistupovat chráněné členy základní třídy přímo z odvozené třídy.  
  
 [!code-csharp[csrefKeywordsModifiers#12](../../../csharp/language-reference/keywords/codesnippet/CSharp/protected_2.cs)]  
  
 Pokud změníte úrovněmi přístupu `x` a `y` k [privátní](../../../csharp/language-reference/keywords/private.md), kompilátor vydá chybové zprávy:  
  
 `'Point.y' is inaccessible due to its protection level.`  
  
 `'Point.x' is inaccessible due to its protection level.`  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Modifikátory přístupu](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [Úrovně přístupnosti](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [Modifikátory](../../../csharp/language-reference/keywords/modifiers.md)  
 [public](../../../csharp/language-reference/keywords/public.md)  
 [private](../../../csharp/language-reference/keywords/private.md)  
 [internal](../../../csharp/language-reference/keywords/internal.md)  
 [Otázky zabezpečení pro interní virtuální klíčová slova](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))