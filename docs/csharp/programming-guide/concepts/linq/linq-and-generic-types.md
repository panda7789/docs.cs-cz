---
title: LINQ a obecné typy (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], generic types
- generic types [LINQ]
- generics [LINQ]
ms.assetid: 660e3799-25ca-462c-8c4a-8bce04fbb031
ms.openlocfilehash: 9a2d1ac72f70e7cd314d349e81ab2bc815a5bf13
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635571"
---
# <a name="linq-and-generic-types-c"></a>LINQ a obecné typy (C#)
Dotazy LINQ jsou založeny na obecných typech, které byly představeny ve verzi 2,0 .NET Framework. Než budete moct začít psát dotazy, nepotřebujete důkladné znalosti obecných typů. Můžete ale chtít pochopit dvě základní koncepty:  
  
1. Při vytváření instance třídy obecné kolekce, jako je například <xref:System.Collections.Generic.List%601>, nahradíte "T" typem objektů, které bude seznam obsahovat. Například seznam řetězců je vyjádřen jako `List<string>`a seznam objektů `Customer` je vyjádřen jako `List<Customer>`. Obecný seznam je silného typu a poskytuje mnoho výhod oproti kolekcím, které ukládají jejich prvky jako <xref:System.Object>. Pokud se pokusíte přidat `Customer` do `List<string>`, zobrazí se v době kompilace chyba. Je snadné použít obecné kolekce, protože není nutné provádět přetypování typu runtime.  
  
2. <xref:System.Collections.Generic.IEnumerable%601> je rozhraní, které umožňuje vytvořit výčet tříd obecných kolekcí pomocí příkazu `foreach`. Třídy obecných kolekcí podporují <xref:System.Collections.Generic.IEnumerable%601> stejně jako neobecné třídy kolekcí, jako je například podpora <xref:System.Collections.ArrayList> <xref:System.Collections.IEnumerable>.  
  
 Další informace o obecných typech naleznete v tématu [generické typy](../../generics/index.md).  
  
## <a name="ienumerablet-variables-in-linq-queries"></a>Proměnné IEnumerable < T\> v dotazech LINQ  
 Proměnné dotazů LINQ jsou zadány jako <xref:System.Collections.Generic.IEnumerable%601> nebo odvozený typ, jako je například <xref:System.Linq.IQueryable%601>. Když se zobrazí proměnná dotazu, která je zapsána jako `IEnumerable<Customer>`, znamená to pouze to, že dotaz, když je proveden, vytvoří posloupnost nula nebo více objektů `Customer`.  
  
 [!code-csharp[csLINQGettingStarted#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#34)]  
  
 Další informace najdete v tématu [vztahy typů v operacích dotazu LINQ](./type-relationships-in-linq-query-operations.md).  
  
## <a name="letting-the-compiler-handle-generic-type-declarations"></a>Umožnění kompilátoru zpracovat deklarace obecných typů  
 Pokud dáváte přednost, můžete se vyhnout obecné syntaxi pomocí klíčového slova [var](../../../language-reference/keywords/var.md) . Klíčové slovo `var` instruuje kompilátor, aby odvodí typ proměnné dotazu, a to tak, že prohlíží zdroj dat zadaný v klauzuli `from`. Následující příklad vytvoří stejný zkompilovaný kód jako předchozí příklad:  
  
 [!code-csharp[csLINQGettingStarted#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#35)]  
  
 Klíčové slovo `var` je užitečné, pokud je typ proměnné zjevný nebo není-li důležité explicitně zadat vnořené obecné typy, jako jsou ty, které jsou vytvářeny pomocí skupinových dotazů. Obecně doporučujeme, abyste při použití `var`zjistili, že je možné, že by váš kód byl obtížnější pro čtení ostatních. Další informace naleznete v tématu [implicitně typované lokální proměnné](../../classes-and-structs/implicitly-typed-local-variables.md).  
  
## <a name="see-also"></a>Viz také:

- [Obecné typy](../../generics/index.md)
