---
title: 'Postupy: Přepsat metodu ToString – C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- ToString method, overriding in C#
- inheritance [C#], overriding OnPaint and ToString
ms.assetid: 8016db69-1f19-420c-8e17-98e8bebb7749
ms.openlocfilehash: a2cf05dc6b288ffdaf1a20cf594231f48046a724
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596743"
---
# <a name="how-to-override-the-tostring-method-c-programming-guide"></a>Postupy: Přepsání metody ToString (C# Průvodce programováním)

Každá třída nebo struktura v C# implicitně dědí <xref:System.Object> třídu. Proto každý objekt v C# <xref:System.Object.ToString%2A> metodě Získá metodu, která vrátí řetězcovou reprezentaci tohoto objektu. Například všechny proměnné typu `int` `ToString` mají metodu, která umožňuje, aby vrátila svůj obsah jako řetězec:  
  
 [!code-csharp[csProgGuideInheritance#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#37)]  
  
 Při vytváření vlastní třídy nebo struktury byste měli přepsat <xref:System.Object.ToString%2A> metodu, aby poskytovala informace o typu pro klientský kód.  
  
 Informace o tom, jak používat řetězce formátu a jiné typy vlastního formátování s `ToString` metodou, naleznete v tématu [Formatting Types](../../../standard/base-types/formatting-types.md).  
  
> [!IMPORTANT]
> Pokud se rozhodnete, jaké informace chcete poskytnout prostřednictvím této metody, zvažte, zda bude vaše třída nebo struktura někdy používána nedůvěryhodným kódem. Buďte opatrní, abyste se ujistili, že neposkytnete žádné informace, které by mohly být zneužity škodlivým kódem.  
  
Přepsání `ToString` metody ve vaší třídě nebo struktuře:
  
1. Deklarujte `ToString` metodu s následujícími modifikátory a návratovým typem:  
  
    ```csharp  
    public override string ToString(){}  
    ```  
  
2. Implementujte metodu tak, aby vracela řetězec.  
  
     Následující příklad vrátí název třídy kromě dat specifických pro konkrétní instanci třídy.  
  
     [!code-csharp[csProgGuideInheritance#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#36)]  
  
     Můžete testovat `ToString` metodu, jak je znázorněno v následujícím příkladu kódu:  
  
     [!code-csharp[csProgGuideInheritance#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#38)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IFormattable>
- [Průvodce programováním v jazyce C#](../index.md)
- [Třídy a struktury](./index.md)
- [Řetězce](../strings/index.md)
- [string](../../language-reference/keywords/string.md)
- [override](../../language-reference/keywords/override.md)
- [virtual](../../language-reference/keywords/virtual.md)
- [Typy formátování](../../../standard/base-types/formatting-types.md)
