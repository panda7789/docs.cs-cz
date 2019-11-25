---
title: Jak přepsat metodu ToString – C# Průvodce programováním
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- ToString method, overriding in C#
- inheritance [C#], overriding OnPaint and ToString
ms.assetid: 8016db69-1f19-420c-8e17-98e8bebb7749
ms.openlocfilehash: 3d5b63609ea61764d4042d534c40d8032fb82841
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73970477"
---
# <a name="how-to-override-the-tostring-method-c-programming-guide"></a>Jak přepsat metodu ToString (C# Průvodce programováním)

Každá třída nebo struktura v C# implicitně dědí třídu <xref:System.Object>. Proto každý objekt v C# získá metodu <xref:System.Object.ToString%2A>, která vrátí řetězcovou reprezentaci tohoto objektu. Například všechny proměnné typu `int` mají metodu `ToString`, která umožňuje, aby vrátila svůj obsah jako řetězec:  
  
 [!code-csharp[csProgGuideInheritance#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#37)]  
  
 Při vytváření vlastní třídy nebo struktury byste měli přepsat metodu <xref:System.Object.ToString%2A>, aby poskytovala informace o typu pro klientský kód.  
  
 Informace o tom, jak používat formátovací řetězce a jiné typy vlastního formátování s metodou `ToString`, naleznete v tématu [typy formátování](../../../standard/base-types/formatting-types.md).  
  
> [!IMPORTANT]
> Pokud se rozhodnete, jaké informace chcete poskytnout prostřednictvím této metody, zvažte, zda bude vaše třída nebo struktura někdy používána nedůvěryhodným kódem. Buďte opatrní, abyste se ujistili, že neposkytnete žádné informace, které by mohly být zneužity škodlivým kódem.  
  
Chcete-li přepsat metodu `ToString` ve vaší třídě nebo struktuře:
  
1. Deklarujte metodu `ToString` s následujícími modifikátory a návratovým typem:  
  
    ```csharp  
    public override string ToString(){}  
    ```  
  
2. Implementujte metodu tak, aby vracela řetězec.  
  
     Následující příklad vrátí název třídy kromě dat specifických pro konkrétní instanci třídy.  
  
     [!code-csharp[csProgGuideInheritance#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#36)]  
  
     Můžete testovat metodu `ToString`, jak je znázorněno v následujícím příkladu kódu:  
  
     [!code-csharp[csProgGuideInheritance#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInheritance/CS/Inheritance.cs#38)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IFormattable>
- [Průvodce programováním v jazyce C#](../index.md)
- [Třídy a struktury](./index.md)
- [Řetězce](../strings/index.md)
- [string](../../language-reference/builtin-types/reference-types.md)
- [override](../../language-reference/keywords/override.md)
- [virtual](../../language-reference/keywords/virtual.md)
- [Typy formátování](../../../standard/base-types/formatting-types.md)
