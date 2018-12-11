---
title: 'Postupy: Definování abstraktních a vlastností - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], abstract
- abstract properties [C#]
ms.assetid: 672a90eb-47b9-4ae0-9914-af53852fddcb
ms.openlocfilehash: 70f344fb4e5a74940219688190324beb8183d32b
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237308"
---
# <a name="how-to-define-abstract-properties-c-programming-guide"></a>Postupy: Definování abstraktních a vlastností (C# Průvodce programováním v)
Následující příklad ukazuje, jak definovat [abstraktní](../../../csharp/language-reference/keywords/abstract.md) vlastnosti. Deklarace abstraktní vlastnost neposkytuje implementaci pro přistupující objekty vlastnosti – deklaruje, že podporuje vlastnosti třídy, ale ponechá implementace přistupujícího objektu odvozené třídy. Následující příklad ukazuje, jak implementovat abstraktní vlastnosti zděděné ze základní třídy.  
  
 Tento příklad se skládá ze tří souborů, z nichž každý je kompilován samostatně a jeho výsledné sestavení se odkazuje na další kompilace:  
  
-   abstractshape.cs: `Shape` třídy obsahující abstraktní `Area` vlastnost.  
  
-   Shapes.cs: Podtřídy třídy `Shape` třídy.  
  
-   shapetest.cs: Testovací program do zobrazované oblasti některých `Shape`-odvozené objekty.  
  
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
- [Postupy: Vytvoření a použití sestavení s pomocí příkazového řádku](../concepts/assemblies-gac/how-to-create-and-use-assemblies-using-the-command-line.md)
