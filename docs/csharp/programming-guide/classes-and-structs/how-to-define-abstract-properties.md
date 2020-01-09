---
title: Definování abstraktních vlastností – C# Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], abstract
- abstract properties [C#]
ms.assetid: 672a90eb-47b9-4ae0-9914-af53852fddcb
ms.openlocfilehash: c46f36133b68a550a17cf882844fd2481eee8851
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705610"
---
# <a name="how-to-define-abstract-properties-c-programming-guide"></a>Definování abstraktních vlastností (C# Průvodce programováním)
Následující příklad ukazuje, jak definovat [abstraktní](../../language-reference/keywords/abstract.md) vlastnosti. Deklarace abstraktní vlastnosti neposkytuje implementaci přistupujících objektů vlastnosti – deklaruje, že třída podporuje vlastnosti, ale ponechá implementaci přistupující objekty odvozeným třídám. Následující příklad ukazuje, jak implementovat abstraktní vlastnosti zděděné ze základní třídy.  
  
 Tato ukázka se skládá ze tří souborů, z nichž každá je zkompilována individuálně a na výsledné sestavení je odkazováno pomocí další kompilace:  
  
- abstractshape.cs: třída `Shape`, která obsahuje abstraktní vlastnost `Area`.  
  
- shapes.cs: podtřídy třídy `Shape`.  
  
- shapetest.cs: testovací program pro zobrazení oblastí některých objektů odvozených od `Shape`.  
  
 Chcete-li zkompilovat příklad, použijte následující příkaz:  
  
 `csc abstractshape.cs shapes.cs shapetest.cs`  
  
 Tím se vytvoří spustitelný soubor shapetest. exe.  
  
## <a name="example"></a>Příklad  
 Tento soubor deklaruje třídu `Shape`, která obsahuje vlastnost `Area` typu `double`.  
  
 [!code-csharp[csProgGuideInheritance#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#1)]  
  
- Modifikátory vlastnosti jsou umístěny v samotné deklaraci vlastnosti. Příklad:  
  
    ```csharp  
    public abstract double Area  
    ```  
  
- Při deklaraci abstraktní vlastnosti (například `Area` v tomto příkladu) jednoduše označíte, jaké přístupové objekty vlastnosti jsou k dispozici, ale neimplementují. V tomto příkladu je k dispozici pouze přistupující objekt [Get](../../language-reference/keywords/get.md) , takže vlastnost je určena jen pro čtení.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje tři podtřídy `Shape` a způsob, jak přepíší vlastnost `Area` k poskytnutí vlastní implementace.  
  
 [!code-csharp[csProgGuideInheritance#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#2)]  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje testovací program, který vytvoří mnoho objektů odvozených od `Shape`a vytiskne své oblasti.  
  
 [!code-csharp[csProgGuideInheritance#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#3)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Třídy a struktury](./index.md)
- [Abstraktní a uzavřené třídy a jejich členové](./abstract-and-sealed-classes-and-class-members.md)
- [Vlastnosti](./properties.md)
