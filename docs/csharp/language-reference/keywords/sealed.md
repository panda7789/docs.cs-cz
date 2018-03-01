---
title: "sealed (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- sealed
- sealed_CSharpKeyword
helpviewer_keywords:
- sealed keyword [C#]
ms.assetid: 8e4ed5d3-10be-47db-9488-0da2008e6f3f
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8248b451f0431286fdaba3583fc2031eb6cdbcd7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="sealed-c-reference"></a>sealed (Referenční dokumentace jazyka C#)
Při použití třídy, `sealed` modifikátor zabrání ostatním třídám dědění z něj. V následujícím příkladu třída `B` dědí z třídy `A`, ale neexistuje žádná třída může dědit vlastnosti z třídy `B`.  
  
```  
class A {}      
sealed class B : A {}  
```  
  
 Můžete také `sealed` modifikátor na metody nebo vlastnosti, která přepisuje virtuální metody nebo vlastnosti v základní třídě. Umožňuje povolit třídy odvozovat z vaší třídy a zabránit přepsání konkrétní virtuální metody nebo vlastnosti.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `Z` dědí z `Y` ale `Z` nelze přepsat virtuální funkce `F` deklarovaného v souboru `X` a uzavřené v `Y`.  
  
 [!code-csharp[csrefKeywordsModifiers#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/sealed_1.cs)]  
  
 Když definujete nové metody nebo vlastnosti ve třídě, můžete zabránit v odvozující třídy je přepsání není deklarativně jako pomocí [virtuální](../../../csharp/language-reference/keywords/virtual.md).  
  
 Jedná se o chybu používat [abstraktní](../../../csharp/language-reference/keywords/abstract.md) modifikátor pomocí zapečetěné třídy, protože je abstraktní třída musí být zdědí třídu, která poskytuje implementaci abstraktní metody nebo vlastnosti.  
  
 Při použití metody nebo vlastnosti, `sealed` modifikátor musí být vždy používá s [přepsat](../../../csharp/language-reference/keywords/override.md).  
  
 Protože struktury jsou implicitně zapečetěná, nelze zděděná.  
  
 Další informace najdete v tématu [dědičnosti](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
 Další příklady najdete v tématu [abstraktní a zapečetěné třídy a jejich členové](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csrefKeywordsModifiers#17](../../../csharp/language-reference/keywords/codesnippet/CSharp/sealed_2.cs)]  
  
 V předchozím příkladu mohou zkuste zapečetěné třídy dědí pomocí následujícího příkazu:  
  
 `class MyDerivedC: SealedClass {}   // Error`  
  
 Výsledkem je chybová zpráva:  
  
 `'MyDerivedC' cannot inherit from sealed class 'SealedClass'.`  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="remarks"></a>Poznámky  
 Pokud chcete zjistit, jestli se má zapečetit třídy, metody nebo vlastnosti, obecně je třeba zvážit následující dva body:  
  
-   Potenciální výhody, že odvozování tříd může získat prostřednictvím přizpůsobit třídu.  
  
-   Potenciální odvozování tříd může změnit třídy v například tak, by přestane fungovat správně, nebo jako očekává.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Statické třídy a jejich členové](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)  
 [Abstraktní a uzavřené třídy a jejich členové](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
 [Modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [Modifikátory](../../../csharp/language-reference/keywords/modifiers.md)  
 [přepsání](../../../csharp/language-reference/keywords/override.md)  
 [virtuální](../../../csharp/language-reference/keywords/virtual.md)
