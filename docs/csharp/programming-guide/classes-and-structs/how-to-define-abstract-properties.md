---
title: Definování abstraktních vlastností – Průvodce programováním v C#
description: Naučte se definovat abstraktní vlastnosti v jazyce C#. Deklarace abstraktní vlastnosti znamená, že třída podporuje vlastnost. Odvozené třídy implementují přistupující objekty.
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], abstract
- abstract properties [C#]
ms.assetid: 672a90eb-47b9-4ae0-9914-af53852fddcb
ms.openlocfilehash: 4db71721495857c634e8090b986704d8a592b4e2
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864394"
---
# <a name="how-to-define-abstract-properties-c-programming-guide"></a>Definování abstraktních vlastností (Průvodce programováním v C#)
Následující příklad ukazuje, jak definovat [abstraktní](../../language-reference/keywords/abstract.md) vlastnosti. Deklarace abstraktní vlastnosti neposkytuje implementaci přistupujících objektů vlastnosti – deklaruje, že třída podporuje vlastnosti, ale ponechá implementaci přistupující objekty odvozeným třídám. Následující příklad ukazuje, jak implementovat abstraktní vlastnosti zděděné ze základní třídy.  
  
 Tato ukázka se skládá ze tří souborů, z nichž každá je zkompilována individuálně a na výsledné sestavení je odkazováno pomocí další kompilace:  
  
- abstractshape.cs: `Shape` třída, která obsahuje abstraktní `Area` vlastnost.  
  
- shapes.cs: podtřídy `Shape` třídy.  
  
- shapetest.cs: testovací program pro zobrazení oblastí `Shape` objektů odvozených od sebe.  
  
 Chcete-li zkompilovat příklad, použijte následující příkaz:  
  
 `csc abstractshape.cs shapes.cs shapetest.cs`  
  
 Tím se vytvoří spustitelný soubor shapetest.exe.  
  
## <a name="example"></a>Příklad  
 Tento soubor deklaruje `Shape` třídu, která obsahuje `Area` vlastnost typu `double` .  
  
 [!code-csharp[csProgGuideInheritance#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#1)]  
  
- Modifikátory vlastnosti jsou umístěny v samotné deklaraci vlastnosti. Příklad:  
  
    ```csharp  
    public abstract double Area  
    ```  
  
- Při deklaraci abstraktní vlastnosti (jako `Area` v tomto příkladu) jednoduše označíte, jaké přístupové objekty vlastnosti jsou k dispozici, ale neimplementují. V tomto příkladu je k dispozici pouze přistupující objekt [Get](../../language-reference/keywords/get.md) , takže vlastnost je určena jen pro čtení.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje tři podtřídy `Shape` a způsob, jak přepisují `Area` vlastnost k poskytnutí vlastní implementace.  
  
 [!code-csharp[csProgGuideInheritance#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#2)]  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje testovací program, který vytváří mnoho `Shape` objektů odvozených a tiskne jejich oblasti.  
  
 [!code-csharp[csProgGuideInheritance#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#3)]  
  
## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
- [Třídy a struktury](./index.md)
- [Abstraktní a uzavřené třídy a jejich členové](./abstract-and-sealed-classes-and-class-members.md)
- [Vlastnosti](./properties.md)
