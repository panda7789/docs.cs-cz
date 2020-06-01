---
title: LINQ a obecné typy (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], generic types
- generic types [LINQ]
- generics [LINQ]
ms.assetid: 660e3799-25ca-462c-8c4a-8bce04fbb031
ms.openlocfilehash: 2cbff0b31cac091a57ea35cbd01535b7d0c4b78a
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241757"
---
# <a name="linq-and-generic-types-c"></a>LINQ a obecné typy (C#)
Dotazy LINQ jsou založeny na obecných typech, které byly představeny ve verzi 2,0 .NET Framework. Než budete moct začít psát dotazy, nepotřebujete důkladné znalosti obecných typů. Můžete ale chtít pochopit dvě základní koncepty:  
  
1. Při vytváření instance třídy obecné kolekce, jako je <xref:System.Collections.Generic.List%601> , nahraďte "T" typem objektů, které bude seznam obsahovat. Například seznam řetězců je vyjádřen jako `List<string>` a seznam `Customer` objektů je vyjádřen jako `List<Customer>` . Obecný seznam je silného typu a poskytuje mnoho výhod oproti kolekcím, které ukládají jejich prvky jako <xref:System.Object> . Pokud se pokusíte přidat `Customer` do, zobrazí `List<string>` se chyba v době kompilace. Je snadné použít obecné kolekce, protože není nutné provádět přetypování typu runtime.  
  
2. <xref:System.Collections.Generic.IEnumerable%601>je rozhraní, které umožňuje vytvořit výčet tříd obecných kolekcí pomocí `foreach` příkazu. Třídy obecných kolekcí podporují <xref:System.Collections.Generic.IEnumerable%601> stejné jako neobecné třídy kolekcí, jako je například <xref:System.Collections.ArrayList> Podpora <xref:System.Collections.IEnumerable> .  
  
 Další informace o obecných typech naleznete v tématu [generické typy](../../generics/index.md).  
  
## <a name="ienumerablet-variables-in-linq-queries"></a>Proměnné IEnumerable<T \> v dotazech LINQ  
 Proměnné dotazu LINQ jsou zadány jako <xref:System.Collections.Generic.IEnumerable%601> nebo odvozený typ, například <xref:System.Linq.IQueryable%601> . Když vidíte proměnnou dotazu, která je zapsána jako `IEnumerable<Customer>` , znamená to pouze to, že dotaz, když je spuštěn, vytvoří posloupnost nula nebo více `Customer` objektů.  
  
 [!code-csharp[csLINQGettingStarted#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#34)]  
  
 Další informace najdete v tématu [vztahy typů v operacích dotazu LINQ](./type-relationships-in-linq-query-operations.md).  
  
## <a name="letting-the-compiler-handle-generic-type-declarations"></a>Umožnění kompilátoru zpracovat deklarace obecných typů  
 Pokud dáváte přednost, můžete se vyhnout obecné syntaxi pomocí klíčového slova [var](../../../language-reference/keywords/var.md) . `var`Klíčové slovo instruuje kompilátor, aby odvodí typ proměnné dotazu tím, že prohlíží zdroj dat zadaný v `from` klauzuli. Následující příklad vytvoří stejný zkompilovaný kód jako předchozí příklad:  
  
 [!code-csharp[csLINQGettingStarted#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#35)]  
  
 `var`Klíčové slovo je užitečné, pokud je typ proměnné zjevný nebo není-li to důležité pro explicitní určení vnořených obecných typů, například těch, které jsou vytvářeny pomocí skupinových dotazů. Obecně platí, že pokud použijete, je vhodné si uvědomit, že pokud chcete `var` , aby byl váš kód obtížnější číst ostatní. Další informace naleznete v tématu [implicitně typované lokální proměnné](../../classes-and-structs/implicitly-typed-local-variables.md).  
  
## <a name="see-also"></a>Viz také

- [Obecné typy](../../generics/index.md)
