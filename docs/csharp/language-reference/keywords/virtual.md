---
title: virtual (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- virtual_CSharpKeyword
- virtual
helpviewer_keywords:
- virtual keyword [C#]
ms.assetid: 5da9abae-bc1e-434f-8bea-3601b8dcb3b2
caps.latest.revision: 26
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: dce3333646bca6f558e3760849b6cffdb34a6c0b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Modifikátory](../../../csharp/language-reference/keywords/modifiers.md)  
 [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)  
 [Polymorfismus](../../../csharp/programming-guide/classes-and-structs/polymorphism.md)  
 [abstraktní](../../../csharp/language-reference/keywords/abstract.md)  
 [přepsání](../../../csharp/language-reference/keywords/override.md)  
 [Nový](../../../csharp/language-reference/keywords/new.md)
