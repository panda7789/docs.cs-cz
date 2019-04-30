---
title: Dotazy LINQ to SQL
ms.date: 03/30/2017
ms.assetid: f4897aaa-7f44-4c20-a471-b948c2971aae
ms.openlocfilehash: 49106502dc58eef36ea0c910c627c9cf397f419e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61902873"
---
# <a name="linq-to-sql-queries"></a>Dotazy LINQ to SQL
Můžete definovat [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dotazy pomocí stejné syntaxe jako v [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)]. Jediným rozdílem je, že odkazované v dotazech objekty se mapují na prvky v databázi. Další informace najdete v tématu [Úvod do dotazů LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] překládá dotazy, které zápisu do odpovídající dotazy SQL a odesílá je do serveru pro zpracování. Přesněji řečeno, vaše aplikace používá [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] rozhraní API pro spuštění dotazu požadavku. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Poskytovatele pak transformuje dotaz na SQL text a provádění zprostředkovatel ADO delegátů. Vrátí výsledky dotazu jako zprostředkovatel ADO `DataReader`. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Zprostředkovatel ADO výsledky a překládá <xref:System.Linq.IQueryable> sadu uživatelských objektů.  
  
> [!NOTE]
>  Většina metod a operátory na [!INCLUDE[dnprdnshort](../../../../../../includes/dnprdnshort-md.md)] vestavěné typy mají přímé překlady SQL. Ty, které [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] nemůže překládat generovat výjimky za běhu. Další informace najdete v tématu [mapování typů SQL a CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).  
  
 Následující tabulka ukazuje, podobnosti a rozdíly mezi [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dotaz položek.  
  
|Položka|Dotaz LINQ|[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Dotaz|  
|----------|----------------|----------------------------------------------------------------------|  
|Návratový typ místní proměnné, která obsahuje dotaz (pro dotazy, které vracejí pořadí)|Obecné `IEnumerable`|Obecné `IQueryable`|  
|Určení zdroje dat|Používá `From` (Visual Basic) nebo `from` (C#) – klauzule|Stejné|  
|Filtrování|Používá `Where` / `where` – klauzule|Stejné|  
|Seskupování|Používá `Group…By` / `groupby` – klauzule|Stejné|  
|Výběr (projekce)|Používá `Select` / `select` – klauzule|Stejné|  
|Odložené versus okamžité spuštění|Zobrazit [Úvod do dotazů LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)|Stejné|  
|Implementace spojení|Používá `Join` / `join` – klauzule|Můžete použít `Join` / `join` klauzule, ale má efektivněji <xref:System.Data.Linq.Mapping.AssociationAttribute> atribut. Další informace najdete v tématu [dotazování napříč vztahy](../../../../../../docs/framework/data/adonet/sql/linq/querying-across-relationships.md).|  
|Vzdálené a místní spuštění||Další informace najdete v tématu [vzdálené vs. Místní spuštění](../../../../../../docs/framework/data/adonet/sql/linq/remote-vs-local-execution.md).|  
|Streamování a dotazování v mezipaměti|Není k dispozici v případě místní paměti||  
  
## <a name="see-also"></a>Viz také:

- [Úvod do dotazů LINQ (C#)](~/docs/csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)
- [Základní operace dotazů LINQ](~/docs/csharp/programming-guide/concepts/linq/basic-linq-query-operations.md)
- [Vztahy typů v operacích dotazu LINQ](~/docs/csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)
- [Koncepty dotazů](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
