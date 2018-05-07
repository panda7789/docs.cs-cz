---
title: virtual (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- virtual_CSharpKeyword
- virtual
helpviewer_keywords:
- virtual keyword [C#]
ms.assetid: 5da9abae-bc1e-434f-8bea-3601b8dcb3b2
ms.openlocfilehash: 4e1a65455df9b0a9272bc5cef257f0d00b36b500
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="virtual-c-reference"></a>virtual (Referenční dokumentace jazyka C#)
`virtual` – Klíčové slovo slouží k úpravě deklaraci metoda, vlastnost, indexer nebo událostí a povolit pro ni k přepsání v odvozené třídě. Například tuto metodu je možné přepsat všechny třídy, která dědí ho:  
  
```  
public virtual double Area()   
{  
    return x * y;  
}  
```  
  
 Implementace člena virtuální může změnit [přepsání člena](../../../csharp/language-reference/keywords/override.md) v odvozené třídě. Další informace o tom, jak používat `virtual` – klíčové slovo, najdete v části [Správa verzí pomocí nové klíčových slov Override a](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) a [zároveň budete vědět, když pomocí přepsání a nová klíčová slova](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).  
  
## <a name="remarks"></a>Poznámky  
 Když se virtuální metoda je volána, běhového typu objektu, se kontroluje přepsání člena. Přepsání člena nejvíce odvozené třídy se nazývá, původní člena, který může být pokud žádné odvozené třídy přepsal člena.  
  
 Ve výchozím nastavení jsou bez virtuální metody. Nejde přepsat bez virtuální metody.  
  
 Nelze použít `virtual` modifikátor s `static`, `abstract`, `private`, nebo `override` modifikátory. Následující příklad ukazuje virtuální vlastnost:  
  
 [!code-csharp[csrefKeywordsModifiers#26](../../../csharp/language-reference/keywords/codesnippet/CSharp/virtual_1.cs)]  
  
 Vlastnosti virtuálního chovat jako abstraktní metody, s výjimkou rozdíly v syntaxi deklarace a volání.  
  
-   Jedná se o chybu používat `virtual` modifikátor na pomocí statické vlastnosti.  
  
-   Virtuální zděděnou vlastnost je možné přepsat v odvozené třídě včetně deklarace vlastnosti, která používá `override` modifikátor.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `Shape` třída obsahuje dvě souřadnice `x`, `y`a `Area()` virtuální metoda. Různé tvar třídy, jako `Circle`, `Cylinder`, a `Sphere` dědění `Shape` třídy a možnosti útoku se počítá pro každý obrázek. Každý odvozené třídy je vlastní implementaci přepsání `Area()`.  
  
 Všimněte si, že zděděné třídy `Circle`, `Sphere`, a `Cylinder` všichni používají konstruktory, které inicializaci základní třídy, jak je znázorněno v následující prohlášení.  
  
```  
public Cylinder(double r, double h): base(r, h) {}  
```  
  
 Následující program vypočítá a zobrazí příslušné oblasti pro každý obrázek vyvoláním příslušné implementace `Area()` metoda, podle objektu, která je přidružená metoda.  
  
 [!code-csharp[csrefKeywordsModifiers#23](../../../csharp/language-reference/keywords/codesnippet/CSharp/virtual_2.cs)]  
  
## <a name="c-language-specification"></a>Specifikace jazyka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Modifikátory](../../../csharp/language-reference/keywords/modifiers.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Polymorfismus](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)  
 [abstract](../../../csharp/language-reference/keywords/abstract.md)  
 [override](../../../csharp/language-reference/keywords/override.md)  
 [new](../../../csharp/language-reference/keywords/new.md)
