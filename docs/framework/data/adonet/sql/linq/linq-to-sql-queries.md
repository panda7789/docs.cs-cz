---
title: Dotazy LINQ to SQL
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f4897aaa-7f44-4c20-a471-b948c2971aae
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a080dd13f4e9950c9e65b8031ffc77ddf18eaf9d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="linq-to-sql-queries"></a>Dotazy LINQ to SQL
Můžete definovat [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dotazy pomocí stejnou syntaxi jako v [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)]. Jediným rozdílem je, že odkazované v dotazech objekty jsou namapované na elementy v databázi. Další informace najdete v tématu [Úvod do dotazů LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Přeloží dotazy, které můžete psát na ekvivalentní dotazy SQL a odešle je server pro zpracování. Přesněji řečeno, vaše aplikace používá [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] rozhraní API pro žádost o spuštění dotazu. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Zprostředkovatele pak transformuje dotaz na SQL text a deleguje na poskytovatele rozhraní ADO provedení. Vrátí výsledky dotazu jako poskytovatele ADO `DataReader`. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Zprostředkovatel překládá ADO výsledky do <xref:System.Linq.IQueryable> kolekce objektů uživatele.  
  
> [!NOTE]
>  Většina metody a operátory na [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] vestavěné typy mít přímý překlady do SQL. Ty, které [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] nemůže překládat generovat výjimky v době běhu. Další informace najdete v tématu [mapování typu SQL CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).  
  
 Následující tabulka ukazuje podobnosti a rozdíly mezi [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dotaz položky.  
  
|Položka|Dotaz LINQ|[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Dotaz|  
|----------|----------------|----------------------------------------------------------------------|  
|Návratový typ místní proměnné, která obsahuje dotaz (pro dotazy, které vracejí pořadí)|Obecné`IEnumerable`|Obecné`IQueryable`|  
|Zadání zdroje dat|Používá `From` ([!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)]) nebo `from` – klauzule (C#)|stejné|  
|Filtrování|Používá `Where` / `where` – klauzule|stejné|  
|Seskupování|Používá `Group…By` / `groupby` – klauzule|stejné|  
|Výběr (projekce)|Používá `Select` / `select` – klauzule|stejné|  
|Odložení versus okamžité spuštění|V tématu [Úvod do dotazů LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)|stejné|  
|Implementace spojení|Používá `Join` / `join` – klauzule|Můžete použít `Join` / `join` klauzule, ale efektivněji používá <xref:System.Data.Linq.Mapping.AssociationAttribute> atribut. Další informace najdete v tématu [dotazování napříč vztahy](../../../../../../docs/framework/data/adonet/sql/linq/querying-across-relationships.md).|  
|Vzdálené versus místní provádění||Další informace najdete v tématu [vzdálené vs. Místní spuštění](../../../../../../docs/framework/data/adonet/sql/linq/remote-vs-local-execution.md).|  
|Streamování a dotazování v mezipaměti|Není k dispozici v případě místní paměti||  
  
## <a name="see-also"></a>Viz také  
 [Úvod do dotazů LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)  
 [Základní operace dotazů LINQ](~/docs/csharp/programming-guide/concepts/linq/basic-linq-query-operations.md)  
 [Vztahy typů v operacích dotazu LINQ](~/docs/csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)  
 [Koncepty dotazu](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
