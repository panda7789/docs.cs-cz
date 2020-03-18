---
title: Jak přepsat metodu ToString - Průvodce programováním jazyka C#
ms.date: 07/20/2015
helpviewer_keywords:
- ToString method, overriding in C#
- inheritance [C#], overriding OnPaint and ToString
ms.assetid: 8016db69-1f19-420c-8e17-98e8bebb7749
ms.openlocfilehash: 7c7196df56821c134b31982d7956a75039e9f929
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705571"
---
# <a name="how-to-override-the-tostring-method-c-programming-guide"></a>Jak přepsat metodu ToString (Průvodce programováním jazyka C#)

Každá třída nebo struktura v jazyce <xref:System.Object> C# implicitně dědí třídu. Proto každý objekt v C# získá metodu, <xref:System.Object.ToString%2A> která vrátí řetězcovou reprezentaci tohoto objektu. Například všechny proměnné typu `int` mají `ToString` metodu, která jim umožňuje vrátit jejich obsah jako řetězec:  
  
 [!code-csharp[csProgGuideInheritance#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#37)]  
  
 Při vytváření vlastní třídy nebo struktury, měli <xref:System.Object.ToString%2A> byste přepsat metodu za účelem poskytnutí informací o typu klientského kódu.  
  
 Informace o použití formátovacích řetězců a dalších typů `ToString` vlastního formátování s metodou naleznete v [tématu Typy formátování](../../../standard/base-types/formatting-types.md).  
  
> [!IMPORTANT]
> Při rozhodování o tom, jaké informace poskytnout prostřednictvím této metody, zvažte, zda vaše třída nebo struktura bude někdy použit nedůvěryhodný kód. Dbejte na to, abyste neposkytovali žádné informace, které by mohly být zneužity škodlivým kódem.  
  
Chcete-li `ToString` přepsat metodu ve třídě nebo struktuře:
  
1. Deklarujte metodu `ToString` s následujícími modifikátory a návratovým typem:  
  
    ```csharp  
    public override string ToString(){}  
    ```  
  
2. Implementujte metodu tak, aby vrátí řetězec.  
  
     Následující příklad vrátí název třídy kromě dat specifických pro konkrétní instanci třídy.  
  
     [!code-csharp[csProgGuideInheritance#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#36)]  
  
     Metodu můžete `ToString` otestovat, jak je znázorněno v následujícím příkladu kódu:  
  
     [!code-csharp[csProgGuideInheritance#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#38)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.IFormattable>
- [Programovací příručka jazyka C#](../index.md)
- [Třídy a struky](./index.md)
- [Řetězce](../strings/index.md)
- [Řetězec](../../language-reference/builtin-types/reference-types.md)
- [override](../../language-reference/keywords/override.md)
- [virtual](../../language-reference/keywords/virtual.md)
- [Typy formátování](../../../standard/base-types/formatting-types.md)
