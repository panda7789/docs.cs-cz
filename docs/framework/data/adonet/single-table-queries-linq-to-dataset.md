---
title: "Dotazy jedné tabulky (LINQ na DataSet)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 0b74bcf8-3f87-449f-bff7-6bcb0d69d212
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 103c7cde61350a1efaf0784964c3f31cc7d55e4b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="single-table-queries-linq-to-dataset"></a>Dotazy jedné tabulky (LINQ na DataSet)
[!INCLUDE[vbteclinqext](../../../../includes/vbteclinqext-md.md)]dotazy fungují v zdroje dat, které implementují <xref:System.Collections.Generic.IEnumerable%601> rozhraní nebo <xref:System.Linq.IQueryable%601> rozhraní. <xref:System.Data.DataTable> Třída neimplementuje buď rozhraní, takže je třeba volat <xref:System.Data.DataTableExtensions.AsEnumerable%2A> metoda, pokud chcete použít <xref:System.Data.DataTable> jako zdroj v `From` klauzuli [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] dotazu.  
  
 Následující příklad načte všechny online objednávky z tabulky SalesOrderHeader a výstupy ID pořadí, datu objednávky a číslo objednávky ke konzole.  
  
 [!code-csharp[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/CS/Program.cs#where1)]  
 [!code-vb[DP LINQ to DataSet Examples#Where1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DP LINQ to DataSet Examples/VB/Module1.vb#where1)] 
  
 Místní proměnné dotazu je inicializován s výrazu dotazu, který funguje na jeden nebo více zdrojů informace tak, že použití jednoho nebo více operátorů dotazu z buď standardní operátory dotazu nebo v případě [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)], operátory, které jsou specifické pro <xref:System.Data.DataSet>třídy. Výraz dotazu v předchozím příkladu používá dva standardních operátorů dotazu: `Where` a `Select`.  
  
 `Where` Klauzule filtry pořadí na základě podmínky, v tomto případě, že `OnlineOrderFlag` je nastaven na `true`. `Select` Operátor přiděluje a vrátí vyčíslitelný objekt, který zachycuje argumenty předávané operátor. V tomto výše příkladu se vytvoří anonymní typ s třemi vlastnostmi: `SalesOrderID`, `OrderDate`, a `SalesOrderNumber`. Hodnoty těchto tří vlastností jsou nastaveny na hodnoty `SalesOrderID`, `OrderDate`, a `SalesOrderNumber` sloupců z `SalesOrderHeader` tabulky.  
  
 `foreach` Smyčky pak zobrazí vyčíslitelný objekt vrácený `Select` a poskytuje výsledky dotazu. Vzhledem k tomu, že dotaz je <xref:System.Linq.Enumerable> typ, který implementuje <xref:System.Collections.Generic.IEnumerable%601>, po vyhodnocení dotazu je odložení, dokud je vstupní proměnné dotazu oproti použití `foreach` smyčky. Vyhodnocení odložené dotazu umožňuje vytvářet dotazy průběžně podle hodnoty, které lze vyhodnotit několikrát, pokaždé, když je potenciálně odlišným výsledkům.  
  
 <xref:System.Data.DataRowExtensions.Field%2A> Metoda poskytuje přístup k hodnotám sloupce <xref:System.Data.DataRow> a <xref:System.Data.DataRowExtensions.SetField%2A> (není zobrazen v předchozím příkladu) nastaví hodnoty ve sloupcích v <xref:System.Data.DataRow>. Obě <xref:System.Data.DataRowExtensions.Field%2A> metoda a <xref:System.Data.DataRowExtensions.SetField%2A> metoda zpracovat typy s možnou hodnotou Null, takže není nutné explicitně zkontrolovala hodnot null. Obě metody jsou obecné metody, také, tzn., není nutné návratový typ přetypování. Můžete použít existující přistupující objekt sloupce v <xref:System.Data.DataRow> (například `o["OrderDate"]`), ale to proto by vyžadují, abyste návratový objekt na příslušný typ přetypování.  Pokud je sloupec s možnou hodnotou Null, budete muset zkontrolovat, zda je hodnota null pomocí <xref:System.Data.DataRow.IsNull%2A> metoda. Další informace najdete v tématu [obecné pole a metody SetField](../../../../docs/framework/data/adonet/generic-field-and-setfield-methods-linq-to-dataset.md).  
  
 Všimněte si, že datový typ zadaný v parametru Obecné `T` z <xref:System.Data.DataRowExtensions.Field%2A> metoda a <xref:System.Data.DataRowExtensions.SetField%2A> metoda musí shodovat s typem základní hodnoty nebo <xref:System.InvalidCastException> bude vyvolána. Zadaný název sloupce taky musí shodovat s názvem sloupce v <xref:System.Data.DataSet> nebo <xref:System.ArgumentException> bude vyvolána. V obou případech je vyvolána výjimka v výčet datového běhu při spuštění dotazu.  
  
## <a name="see-also"></a>Viz také  
 [Dotazy na křížovou tabulku](../../../../docs/framework/data/adonet/cross-table-queries-linq-to-dataset.md)  
 [Dotazy na typové datové sady](../../../../docs/framework/data/adonet/querying-typed-datasets.md)  
 [Obecné pole a metody SetField](../../../../docs/framework/data/adonet/generic-field-and-setfield-methods-linq-to-dataset.md)
