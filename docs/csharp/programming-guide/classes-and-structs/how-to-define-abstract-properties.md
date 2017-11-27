---
title: "Postupy: Definování abstraktních vlastností (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- properties [C#], abstract
- abstract properties [C#]
ms.assetid: 672a90eb-47b9-4ae0-9914-af53852fddcb
caps.latest.revision: "13"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cd8a42c1040180c19bc58627ab0c6a21ace77773
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-abstract-properties-c-programming-guide"></a>Postupy: Definování abstraktních vlastností (Průvodce programováním v C#)
Následující příklad ukazuje, jak definovat [abstraktní](../../../csharp/language-reference/keywords/abstract.md) vlastnosti. Deklarace abstraktní vlastnosti neposkytuje implementace přístupové objekty vlastnosti – deklaruje, že podporuje vlastnosti třídy, ale ponechá přistupujícího objektu implementaci do odvozené třídy. Následující příklad ukazuje, jak implementovat abstraktní vlastnosti zděděn ze základní třídy.  
  
 Tato ukázka se skládá ze tří souborů, z nichž každý jednotlivě kompiluje a jeho výsledná sestavení odkazuje další kompilace:  
  
-   abstractshape.cs: `Shape` třídu, která obsahuje abstraktní `Area` vlastnost.  
  
-   Shapes.cs: podtříd `Shape` třídy.  
  
-   shapetest.cs: test program k zobrazení oblastí některých `Shape`-odvozené objekty.  
  
 Kompilace v příkladu, použijte následující příkaz:  
  
 `csc abstractshape.cs shapes.cs shapetest.cs`  
  
 Tím se vytvoří shapetest.exe spustitelný soubor.  
  
## <a name="example"></a>Příklad  
 Tento soubor deklaruje `Shape` třídu, která obsahuje `Area` vlastnost typu `double`.  
  
 [!code-csharp[csProgGuideInheritance#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_1.cs)]  
  
-   Modifikátory na vlastnosti jsou umístěny v deklaraci vlastnost sám sebe. Příklad:  
  
    ```  
    public abstract double Area  
    ```  
  
-   Pokud deklarace abstraktních vlastností (například `Area` v tomto příkladu), můžete jednoduše označují jaké přístupové objekty vlastnosti jsou k dispozici, ale není jejich implementaci. V tomto příkladu pouze [získat](../../../csharp/language-reference/keywords/get.md) přistupujícího objektu je k dispozici, takže vlastnost je jen pro čtení.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje tři měly podtřídy `Shape` a jak se přepsat `Area` vlastností a zadejte vlastní implementaci.  
  
 [!code-csharp[csProgGuideInheritance#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_2.cs)]  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje program test, který vytvoří několik `Shape`-odvozené objekty a vytiskne jejich oblasti.  
  
 [!code-csharp[csProgGuideInheritance#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_3.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [Abstraktní a uzavřené třídy a jejich členové](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
 [Vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [Postupy: vytvoření a použití sestavení s pomocí příkazového řádku](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4)
