---
title: LINQ a obecné typy (C#)
ms.date: 07/20/2015
helpviewer_keywords:
- LINQ [C#], generic types
- generic types [LINQ]
- generics [LINQ]
ms.assetid: 660e3799-25ca-462c-8c4a-8bce04fbb031
ms.openlocfilehash: cd0fae0c7d99491f21e5e1fb265e4aabafaa63c4
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59332679"
---
# <a name="linq-and-generic-types-c"></a>LINQ a obecné typy (C#)
[!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] dotazy jsou založeny na obecné typy, které jsou nově ve verzi 2.0 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Předtím, než můžete začít psát dotazy nepotřebujete hlubokou znalost obecných typů. Však může být vhodné pochopit dvě základní koncepty:  
  
1. Při vytváření instance třídy obecné kolekce, jako <xref:System.Collections.Generic.List%601>, je typ objektů, které bude obsahovat seznam nahradit "T". Například seznam řetězců je vyjádřena jako `List<string>`a seznam `Customer` objekty je vyjádřena jako `List<Customer>`. Obecný seznam silného typu a má spoustu výhod nad kolekcí, které ukládají jejich prvky jako <xref:System.Object>. Pokud se pokusíte přidat `Customer` k `List<string>`, obdržíte chybu v době kompilace. Je snadné použití obecných kolekcí, protože není nutné provádět za běhu přetypování.  
  
2. <xref:System.Collections.Generic.IEnumerable%601> je rozhraní, které umožňuje obecné kolekce tříd pro provedení výčtu pomocí `foreach` příkazu. Obecné kolekce tříd podporu <xref:System.Collections.Generic.IEnumerable%601> stejně jako negenerická kolekce tříd, například <xref:System.Collections.ArrayList> podporují <xref:System.Collections.IEnumerable>.  
  
 Další informace o obecných typech najdete v tématu [obecných typů](../../../../csharp/programming-guide/generics/index.md).  
  
## <a name="ienumerablet-variables-in-linq-queries"></a>IEnumerable < T\> proměnné v dotazech LINQ  
 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] proměnné dotazu jsou zadány jako <xref:System.Collections.Generic.IEnumerable%601> nebo odvozeným typem, jako <xref:System.Linq.IQueryable%601>. Když se zobrazí proměnné dotazu, který je zadán jako `IEnumerable<Customer>`, znamená to je to, že dotazu, pokud je spuštěn, vytvoří posloupnost nula nebo více `Customer` objekty.  
  
 [!code-csharp[csLINQGettingStarted#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#34)]  
  
 Další informace najdete v tématu [vztahy typů v operacích dotazu LINQ](../../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md).  
  
## <a name="letting-the-compiler-handle-generic-type-declarations"></a>Umožňuje kompilátoru popisovač obecného typu deklarace  
 Pokud dáváte přednost, můžete se vyhnout Obecná syntaxe pomocí [var](../../../../csharp/language-reference/keywords/var.md) – klíčové slovo. `var` – Klíčové slovo instruuje kompilátor, aby zobrazením datovému zdroji zadanému v odvození typu proměnné dotazu `from` klauzuli. Následující příklad vytvoří stejný zkompilovaný kód jako v předchozím příkladu:  
  
 [!code-csharp[csLINQGettingStarted#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQGettingStarted/CS/Class1.cs#35)]  
  
 `var` – Klíčové slovo je užitečné, když je typ proměnné zřejmý nebo když není důležité to s ohledem na vnořených obecných typech, jako jsou ty, které vytváří skupiny dotazů. Obecně doporučujeme, pokud používáte `var`, dobré si uvědomit, že ji může ztížit kódu pro ostatní uživatele. Další informace najdete v tématu [implicitně typované lokální proměnné](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
## <a name="see-also"></a>Viz také:

- [Začínáme s dotazy LINQ v jazyce C#](../../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)
- [Obecné typy](../../../../csharp/programming-guide/generics/index.md)
