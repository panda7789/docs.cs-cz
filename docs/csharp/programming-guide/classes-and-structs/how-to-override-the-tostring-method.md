---
title: 'Postupy: Potlačení metody ToString - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- ToString method, overriding in C#
- inheritance [C#], overriding OnPaint and ToString
ms.assetid: 8016db69-1f19-420c-8e17-98e8bebb7749
ms.openlocfilehash: c28712a3969c8b0143f90b1e733738bf74464d9a
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56980474"
---
# <a name="how-to-override-the-tostring-method-c-programming-guide"></a>Postupy: Potlačení metody ToString (C# Průvodce programováním v)
Implicitně dědí všechny třídy nebo struktury v jazyce C# <xref:System.Object> třídy. Proto, získá každý objekt v jazyce C# <xref:System.Object.ToString%2A> metodu, která vrátí řetězcovou reprezentaci tohoto objektu. Například všechny proměnné typu `int` mít `ToString` metodu, která umožňuje k návratu jejich obsah jako řetězec:  
  
 [!code-csharp[csProgGuideInheritance#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#37)]  
  
 Když vytvoříte vlastní třídy nebo struktury, kterou byste měli přepsat <xref:System.Object.ToString%2A> metodu za účelem poskytnutí informací o typu pro klientský kód.  
  
 Informace o tom, jak používat formátovacích řetězců a dalších typů vlastní formátování pomocí `ToString` metodu, najdete v článku [Formatting Types](../../../standard/base-types/formatting-types.md).  
  
> [!IMPORTANT]
>  Při rozhodování, jaké informace, které poskytují prostřednictvím této metody, zvažte, zda třídy nebo struktury se někdy použije nedůvěryhodným kódem. Pečlivě zkontrolujte neposkytují žádné informace, které by se dala zneužít škodlivým kódem.  
  
### <a name="to-override-the-tostring-method-in-your-class-or-struct"></a>Přepsání metody ToString ve třídě nebo struktuře  
  
1.  Deklarace `ToString` pomocí následujících parametrů a návratový typ metody:  
  
    ```csharp  
    public override string ToString(){}  
    ```  
  
2.  Implementujte metodu tak, aby vrátil řetězec.  
  
     Následující příklad vrátí název třídy, kromě dat podle konkrétní instance třídy.  
  
     [!code-csharp[csProgGuideInheritance#36](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-override-the-tostring-method_2.cs)]  
  
     Můžete testovat `ToString` způsob, jak je znázorněno v následujícím příkladu kódu:  
  
     [!code-csharp[csProgGuideInheritance#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#38)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IFormattable>
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Třídy a struktury](../../../csharp/programming-guide/classes-and-structs/index.md)
- [Řetězce](../../../csharp/programming-guide/strings/index.md)
- [string](../../../csharp/language-reference/keywords/string.md)
- [new](../../../csharp/language-reference/keywords/new.md)
- [override](../../../csharp/language-reference/keywords/override.md)
- [virtual](../../../csharp/language-reference/keywords/virtual.md)
- [Typy formátování](../../../standard/base-types/formatting-types.md)
