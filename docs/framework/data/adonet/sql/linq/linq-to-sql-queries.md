---
title: Dotazy LINQ to SQL
ms.date: 03/30/2017
ms.assetid: f4897aaa-7f44-4c20-a471-b948c2971aae
ms.openlocfilehash: 534da029664af0babc3dff6226ff095b7222c34d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915835"
---
# <a name="linq-to-sql-queries"></a>Dotazy LINQ to SQL
Dotazy definujete [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pomocí stejné syntaxe jako v [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)]. Jediným rozdílem je, že objekty odkazované v dotazech jsou mapovány na prvky v databázi. Další informace najdete v tématu [Úvod do dotazů LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]přeloží dotazy, které zapisujete do ekvivalentních dotazů SQL, a odesílá je na server ke zpracování. Konkrétně vaše aplikace používá [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] rozhraní API k vyžádání provádění dotazů. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Zprostředkovatel pak transformuje dotaz na text SQL a deleguje provádění poskytovatele ADO. Poskytovatel ADO vrátí výsledky dotazu jako `DataReader`. Zprostředkovatel přeloží výsledky ADO <xref:System.Linq.IQueryable> na kolekci uživatelských objektů. [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]  
  
> [!NOTE]
> Většina metod a operátorů v .NET Framework předdefinovaných typů má přímé překlady do SQL. Ty, [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] které nemůžou přeložit generování výjimek za běhu. Další informace naleznete v tématu [mapování typu SQL-CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).  
  
 V následující tabulce jsou uvedeny podobnosti a rozdíly mezi [!INCLUDE[vbteclinq](../../../../../../includes/vbteclinq-md.md)] položkami [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] a dotazy.  
  
|Položka|Dotaz LINQ|[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]Zadávání|  
|----------|----------------|----------------------------------------------------------------------|  
|Návratový typ místní proměnné, která obsahuje dotaz (pro dotazy, které vracejí sekvence)|Obecněji`IEnumerable`|Obecněji`IQueryable`|  
|Určení zdroje dat|Používá klauzuli `from` (Visual Basic) nebo (C# `From`|Jedné|  
|Filtrování|`Where` Používáklauzuli/ `where`|Jedné|  
|Seskupování|`Group…By` Používáklauzuli/ `groupby`|Jedné|  
|Výběr (projektování)|`Select` Používáklauzuli/ `select`|Jedné|  
|Odložené versus okamžité provedení|Viz [Úvod do dotazů LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)|Jedné|  
|Implementace spojení|`Join` Používáklauzuli/ `join`|`Join` Může použít / <xref:System.Data.Linq.Mapping.AssociationAttribute> klauzuli, ale efektivněji používá atribut. `join` Další informace najdete v tématu [dotazování napříč relacemi](../../../../../../docs/framework/data/adonet/sql/linq/querying-across-relationships.md).|  
|Vzdálené porovnání a místní spuštění||Další informace najdete v tématu [Remote vs. Místní spuštění](../../../../../../docs/framework/data/adonet/sql/linq/remote-vs-local-execution.md).|  
|Streamování versus dotazování v mezipaměti|Nejde použít ve scénáři místní paměti.||  
  
## <a name="see-also"></a>Viz také:

- [Úvod do dotazů LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)
- [Základní operace dotazů LINQ](../../../../../csharp/programming-guide/concepts/linq/basic-linq-query-operations.md)
- [Vztahy typů v operacích dotazu LINQ](../../../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)
- [Koncepty dotazů](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
