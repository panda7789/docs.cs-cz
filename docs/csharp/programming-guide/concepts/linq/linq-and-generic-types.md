---
title: LINQ a obecné typy (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], generic types
- generic types [LINQ]
- generics [LINQ]
ms.assetid: 660e3799-25ca-462c-8c4a-8bce04fbb031
ms.openlocfilehash: 9a2d1ac72f70e7cd314d349e81ab2bc815a5bf13
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75635571"
---
# <a name="linq-and-generic-types-c"></a>LINQ a obecné typy (C#)
Linq dotazy jsou založeny na obecných typech, které byly zavedeny ve verzi 2.0 rozhraní .NET Framework. Před zahájením psaní dotazů nepotřebujete podrobné znalosti o obecných souborech. Můžete však chtít pochopit dva základní pojmy:  
  
1. Při vytváření instance třídy obecné kolekce, jako <xref:System.Collections.Generic.List%601>je například , nahradíte "T" typem objektů, které bude seznam obsahovat. Například seznam řetězců je vyjádřen jako `List<string>`, a `Customer` seznam objektů je `List<Customer>`vyjádřen jako . Obecný seznam je silně zadaný a poskytuje mnoho výhod oproti <xref:System.Object>kolekcím, které ukládají jejich prvky jako . Pokud se pokusíte `Customer` přidat `List<string>`do , zobrazí se chyba v době kompilace. Je snadné použít obecné kolekce, protože není nutné provádět přetypování typu za běhu.  
  
2. <xref:System.Collections.Generic.IEnumerable%601>je rozhraní, které umožňuje obecné třídy kolekce, `foreach` které mají být výčtu pomocí příkazu. Obecné kolekce <xref:System.Collections.Generic.IEnumerable%601> třídy podporují stejně jako <xref:System.Collections.ArrayList> <xref:System.Collections.IEnumerable>neobecné kolekce třídy, jako je například podpora .  
  
 Další informace o obecných souborech naleznete [v tématu Generics](../../generics/index.md).  
  
## <a name="ienumerablet-variables-in-linq-queries"></a>IEnumerable<\> T proměnné v linq dotazy  
 Proměnné dotazu LINQ jsou <xref:System.Collections.Generic.IEnumerable%601> zadány jako odvozený typ, například <xref:System.Linq.IQueryable%601>. Když se zobrazí proměnná dotazu, která je zadána jako `IEnumerable<Customer>`, znamená to pouze, že `Customer` dotaz při spuštění vytvoří posloupnost nula nebo více objektů.  
  
 [!code-csharp[csLINQGettingStarted#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#34)]  
  
 Další informace naleznete [v tématu Type Relationships in LINQ Query Operations](./type-relationships-in-linq-query-operations.md).  
  
## <a name="letting-the-compiler-handle-generic-type-declarations"></a>Nechat kompilátor zpracovávat deklarace obecného typu  
 Pokud dáváte přednost, můžete se vyhnout obecné syntaxi pomocí klíčového slova [var.](../../../language-reference/keywords/var.md) Klíčové `var` slovo pokyn kompilátorod odvodit typ proměnné dotazu při `from` pohledu na zdroj dat zadaný v klauzuli. Následující příklad vytvoří stejný zkompilovaný kód jako předchozí příklad:  
  
 [!code-csharp[csLINQGettingStarted#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#35)]  
  
 Klíčové `var` slovo je užitečné, pokud je typ proměnné zřejmý nebo pokud není tak důležité explicitně zadat vnořené obecné typy, jako jsou ty, které jsou vytvářeny skupinovými dotazy. Obecně doporučujeme, že pokud `var`používáte , uvědomit si, že může ztížit váš kód pro ostatní číst. Další informace naleznete [v tématu Implicitně zadané místní proměnné](../../classes-and-structs/implicitly-typed-local-variables.md).  
  
## <a name="see-also"></a>Viz také

- [Obecné typy](../../generics/index.md)
