---
title: 'Postupy: Definovat abstraktní vlastnosti – C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], abstract
- abstract properties [C#]
ms.assetid: 672a90eb-47b9-4ae0-9914-af53852fddcb
ms.openlocfilehash: 57fd2ed3a26bf5986f9c8a1a6cae6b041811e84c
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70970901"
---
# <a name="how-to-define-abstract-properties-c-programming-guide"></a>Postupy: Definování abstraktních vlastnostíC# (Průvodce programováním)
Následující příklad ukazuje, jak definovat [abstraktní](../../language-reference/keywords/abstract.md) vlastnosti. Deklarace abstraktní vlastnosti neposkytuje implementaci přistupujících objektů vlastnosti – deklaruje, že třída podporuje vlastnosti, ale ponechá implementaci přistupující objekty odvozeným třídám. Následující příklad ukazuje, jak implementovat abstraktní vlastnosti zděděné ze základní třídy.  
  
 Tato ukázka se skládá ze tří souborů, z nichž každá je zkompilována individuálně a na výsledné sestavení je odkazováno pomocí další kompilace:  
  
- abstractshape.cs: `Shape` třída, která obsahuje abstraktní `Area` vlastnost.  
  
- shapes.cs: Podtřídy `Shape` třídy.  
  
- shapetest.cs: Testovací program pro zobrazení oblastí objektů odvozených od `Shape`sebe.  
  
 Chcete-li zkompilovat příklad, použijte následující příkaz:  
  
 `csc abstractshape.cs shapes.cs shapetest.cs`  
  
 Tím se vytvoří spustitelný soubor shapetest. exe.  
  
## <a name="example"></a>Příklad  
 Tento soubor deklaruje `Shape` třídu, která `Area` obsahuje vlastnost typu `double`.  
  
 [!code-csharp[csProgGuideInheritance#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#1)]  
  
- Modifikátory vlastnosti jsou umístěny v samotné deklaraci vlastnosti. Příklad:  
  
    ```csharp  
    public abstract double Area  
    ```  
  
- Při deklaraci abstraktní vlastnosti ( `Area` jako v tomto příkladu) jednoduše označíte, jaké přístupové objekty vlastnosti jsou k dispozici, ale neimplementují. V tomto příkladu je k dispozici pouze přistupující objekt [Get](../../language-reference/keywords/get.md) , takže vlastnost je určena jen pro čtení.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje tři podtřídy `Shape` a způsob, jak `Area` přepisují vlastnost k poskytnutí vlastní implementace.  
  
 [!code-csharp[csProgGuideInheritance#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#2)]  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje testovací program, který vytváří mnoho `Shape`objektů odvozených a tiskne jejich oblasti.  
  
 [!code-csharp[csProgGuideInheritance#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#3)]  
  
## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Třídy a struktury](./index.md)
- [Abstraktní a uzavřené třídy a jejich členové](./abstract-and-sealed-classes-and-class-members.md)
- [Vlastnosti](./properties.md)
