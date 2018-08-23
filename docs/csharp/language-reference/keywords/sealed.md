---
title: sealed (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- sealed
- sealed_CSharpKeyword
helpviewer_keywords:
- sealed keyword [C#]
ms.assetid: 8e4ed5d3-10be-47db-9488-0da2008e6f3f
ms.openlocfilehash: be13e04dce12dfb60a1179e05a0a47eca1df1af4
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2018
ms.locfileid: "42753984"
---
# <a name="sealed-c-reference"></a>sealed (Referenční dokumentace jazyka C#)
Při použití na třídu, `sealed` modifikátor zabrání ostatním třídám z něj dědí. V následujícím příkladu třída `B` dědí z třídy `A`, ale žádná třída může dědit z třídy `B`.  
  
```csharp  
class A {}      
sealed class B : A {}  
```  
  
 Můžete také použít `sealed` modifikátor na metodu nebo vlastnost, která přepíše virtuální metody nebo vlastnosti v základní třídě. To umožňuje povolit třídy, které jsou odvozeny z vaší třídy a zabránili jejich přepsání konkrétní virtuální metody nebo vlastnosti.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `Z` dědí z `Y` ale `Z` nemůže přepsat virtuální funkci `F` , která je deklarována v `X` a uzavřené v `Y`.  
  
 [!code-csharp[csrefKeywordsModifiers#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/sealed_1.cs)]  
  
 Při definování nové metody nebo vlastnosti ve třídě, můžete zabránit odvozená třídy přepsání není deklarací je jako [virtuální](../../../csharp/language-reference/keywords/virtual.md).  
  
 Jedná se o chybu používat [abstraktní](../../../csharp/language-reference/keywords/abstract.md) modifikátor zapečetěnou třídu, protože abstraktní třídy musí být zděděny třídu, která poskytuje implementaci abstraktní metody nebo vlastnosti.  
  
 Při použití na metodu nebo vlastnost, `sealed` modifikátor musí být vždy použit s [přepsat](../../../csharp/language-reference/keywords/override.md).  
  
 Protože struktury jsou implicitně zapečetěná, nelze dědit.  
  
 Další informace najdete v tématu [dědičnosti](../../../csharp/programming-guide/classes-and-structs/inheritance.md).  
  
 Další příklady najdete v tématu [abstraktní a zapečetěné třídy a členové](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csrefKeywordsModifiers#17](../../../csharp/language-reference/keywords/codesnippet/CSharp/sealed_2.cs)]  
  
 V předchozím příkladu můžete vyzkoušet dědit od zapečetěné třídy pomocí následujícího příkazu:  
  
 `class MyDerivedC: SealedClass {}   // Error`  
  
 Výsledek se zobrazí chybová zpráva:  
  
 `'MyDerivedC': cannot derive from sealed type 'SealedClass'`  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="remarks"></a>Poznámky  
 Pokud chcete zjistit, jestli se má zapečetit třídy, metody nebo vlastnosti, obecně byste měli zvážit následující dva body:  
  
-   Potenciálních výhod, že odvozené třídy mohou získat prostřednictvím možnost přizpůsobit si své třídy.  
  
-   Potenciál odvozené třídy může změnit tříd takovým způsobem, že by už nebude fungovat správně nebo jako očekává.  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Statické třídy a jejich členové](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md)  
 [Abstraktní a uzavřené třídy a jejich členové](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
 [Modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [Modifikátory](../../../csharp/language-reference/keywords/modifiers.md)  
 [override](../../../csharp/language-reference/keywords/override.md)  
 [virtual](../../../csharp/language-reference/keywords/virtual.md)
