---
title: 'Postupy: Definování abstraktních vlastností (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], abstract
- abstract properties [C#]
ms.assetid: 672a90eb-47b9-4ae0-9914-af53852fddcb
ms.openlocfilehash: 549867cac99784ce885b8fce8a1638c40ad88cec
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44180767"
---
# <a name="how-to-define-abstract-properties-c-programming-guide"></a>Postupy: Definování abstraktních vlastností (Průvodce programováním v C#)
Následující příklad ukazuje, jak definovat [abstraktní](../../../csharp/language-reference/keywords/abstract.md) vlastnosti. Deklarace abstraktní vlastnost neposkytuje implementaci pro přistupující objekty vlastnosti – deklaruje, že podporuje vlastnosti třídy, ale ponechá implementace přistupujícího objektu odvozené třídy. Následující příklad ukazuje, jak implementovat abstraktní vlastnosti zděděné ze základní třídy.  
  
 Tento příklad se skládá ze tří souborů, z nichž každý je kompilován samostatně a jeho výsledné sestavení se odkazuje na další kompilace:  
  
-   abstractshape.cs: `Shape` třídy obsahující abstraktní `Area` vlastnost.  
  
-   Shapes.cs: podtřídy třídy `Shape` třídy.  
  
-   shapetest.cs: testovací program do zobrazované oblasti některých `Shape`-odvozené objekty.  
  
 Chcete-li příklad zkompilovat, použijte následující příkaz:  
  
 `csc abstractshape.cs shapes.cs shapetest.cs`  
  
 Tím se vytvoří shapetest.exe spustitelný soubor.  
  
## <a name="example"></a>Příklad  
 Deklaruje tento soubor `Shape` třídu, která obsahuje `Area` vlastnost typu `double`.  
  
 [!code-csharp[csProgGuideInheritance#1](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_1.cs)]  
  
-   Modifikátory pro vlastnost jsou umístěny v deklaraci vlastnosti. Příklad:  
  
    ```csharp  
    public abstract double Area  
    ```  
  
-   Při deklarování abstraktní vlastnosti (například `Area` v tomto příkladu), můžete jednoduše označit, jaký přistupující objekty vlastnosti jsou k dispozici, ale neimplementují je. V tomto příkladu, pouze [získat](../../../csharp/language-reference/keywords/get.md) přístupový objekt není k dispozici, tak vlastnost je jen pro čtení.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje tři podtřídy třídy `Shape` a jak mohou přepsat `Area` vlastnost poskytli vlastní implementaci.  
  
 [!code-csharp[csProgGuideInheritance#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_2.cs)]  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje testovací program, který vytváří celou řadou `Shape`-odvozené objekty a vytiskne jejich oblasti.  
  
 [!code-csharp[csProgGuideInheritance#3](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-abstract-properties_3.cs)]  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
- [Třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md)  
- [Abstraktní a uzavřené třídy a jejich členové](../../../csharp/programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)  
- [Vlastnosti](../../../csharp/programming-guide/classes-and-structs/properties.md)  
- [Postupy: Vytváření a použití sestavení s pomocí příkazového řádku](../concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md)
