---
title: Jak definovat abstraktní vlastnosti - C# Programovací průvodce
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], abstract
- abstract properties [C#]
ms.assetid: 672a90eb-47b9-4ae0-9914-af53852fddcb
ms.openlocfilehash: c46f36133b68a550a17cf882844fd2481eee8851
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705610"
---
# <a name="how-to-define-abstract-properties-c-programming-guide"></a>Jak definovat abstraktní vlastnosti (Průvodce programováním jazyka C#)
Následující příklad ukazuje, jak definovat [abstraktní](../../language-reference/keywords/abstract.md) vlastnosti. Deklarace abstraktní vlastnosti neposkytuje implementaci přistupující objekty vlastnosti – deklaruje, že třída podporuje vlastnosti, ale ponechá implementaci přistupujícího objektu na odvozené třídy. Následující příklad ukazuje, jak implementovat abstraktní vlastnosti zděděné ze základní třídy.  
  
 Tato ukázka se skládá ze tří souborů, z nichž každý je zkompilován jednotlivě a jeho výsledné sestavení je odkazováno další kompilací:  
  
- abstractshape.cs: `Shape` třída, která `Area` obsahuje abstraktní vlastnost.  
  
- shapes.cs: Podtřídy `Shape` třídy.  
  
- shapetest.cs: Testovací program pro zobrazení `Shape`oblastí některých odvozených objektů.  
  
 Chcete-li zkompilovat příklad, použijte následující příkaz:  
  
 `csc abstractshape.cs shapes.cs shapetest.cs`  
  
 Tím vytvoříte spustitelný soubor shapetest.exe.  
  
## <a name="example"></a>Příklad  
 Tento soubor deklaruje třídu, `Shape` která obsahuje `Area` vlastnost typu `double`.  
  
 [!code-csharp[csProgGuideInheritance#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#1)]  
  
- Modifikátory na vlastnost jsou umístěny na deklaraci vlastnosti samotné. Například:  
  
    ```csharp  
    public abstract double Area  
    ```  
  
- Při deklarování abstraktní `Area` vlastnosti (například v tomto příkladu) jednoduše označíte, jaké přístupové objekty vlastností jsou k dispozici, ale neimplementujte je. V tomto příkladu je k dispozici pouze přístupový objekt [get,](../../language-reference/keywords/get.md) takže vlastnost je jen pro čtení.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje tři `Shape` podtřídy a `Area` jak přepsat vlastnost poskytnout vlastní implementaci.  
  
 [!code-csharp[csProgGuideInheritance#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#2)]  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje testovací program, který `Shape`vytvoří počet odvozených objektů a vytiskne jejich oblasti.  
  
 [!code-csharp[csProgGuideInheritance#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#3)]  
  
## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
- [Třídy a struky](./index.md)
- [Abstraktní a uzavřené třídy a jejich členové](./abstract-and-sealed-classes-and-class-members.md)
- [Vlastnosti](./properties.md)
