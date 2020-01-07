---
title: Dotazy LINQ to SQL
ms.date: 03/30/2017
ms.assetid: f4897aaa-7f44-4c20-a471-b948c2971aae
ms.openlocfilehash: 478138d26d6cdf656b2487c637a5eb13784126e9
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75634377"
---
# <a name="linq-to-sql-queries"></a>Dotazy LINQ to SQL
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dotazy definujete pomocí stejné syntaxe jako v LINQ. Jediným rozdílem je, že objekty odkazované v dotazech jsou mapovány na prvky v databázi. Další informace najdete v tématu [Úvod do dotazů LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md).  
  
 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] překládá dotazy, které zapisujete do ekvivalentních dotazů SQL, a odesílá je na server ke zpracování. Konkrétně vaše aplikace používá rozhraní [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] API k vyžádání provádění dotazů. Poskytovatel [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pak transformuje dotaz na text SQL a deleguje provádění poskytovatele ADO. Poskytovatel ADO vrátí výsledky dotazu jako `DataReader`. Poskytovatel [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] překládá výsledky ADO do <xref:System.Linq.IQueryable> kolekce uživatelských objektů.  
  
> [!NOTE]
> Většina metod a operátorů v .NET Framework předdefinovaných typů má přímé překlady do SQL. Ty, které LINQ nemohou přeložit generování výjimek za běhu. Další informace naleznete v tématu [mapování typu SQL-CLR](sql-clr-type-mapping.md).  
  
 V následující tabulce jsou uvedeny podobnosti a rozdíly mezi položkami dotazů LINQ a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].  
  
|Položka|Dotaz LINQ|[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] dotaz|  
|----------|----------------|----------------------------------------------------------------------|  
|Návratový typ místní proměnné, která obsahuje dotaz (pro dotazy, které vracejí sekvence)|Obecné `IEnumerable`|Obecné `IQueryable`|  
|Určení zdroje dat|Používá klauzuli `From` (Visual Basic) nebo `from` (C#)|Jedné|  
|Filtrování|Používá klauzuli `Where`/`where`|Jedné|  
|Seskupování|Používá klauzuli `Group…By`/`groupby`|Jedné|  
|Výběr (projektování)|Používá klauzuli `Select`/`select`|Jedné|  
|Odložené versus okamžité provedení|Viz [Úvod do dotazů LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)|Jedné|  
|Implementace spojení|Používá klauzuli `Join`/`join`|Lze použít klauzuli `Join`/`join`, ale efektivněji používá atribut <xref:System.Data.Linq.Mapping.AssociationAttribute>. Další informace najdete v tématu [dotazování napříč relacemi](querying-across-relationships.md).|  
|Vzdálené porovnání a místní spuštění||Další informace najdete v tématu [vzdálené a místní spuštění](remote-vs-local-execution.md).|  
|Streamování versus dotazování v mezipaměti|Nejde použít ve scénáři místní paměti.||  
  
## <a name="see-also"></a>Viz také:

- [Úvod do dotazů LINQ (C#)](../../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md)
- [Základní operace dotazů LINQ](../../../../../csharp/programming-guide/concepts/linq/basic-linq-query-operations.md)
- [Vztahy typů v operacích dotazu LINQ](../../../../../csharp/programming-guide/concepts/linq/type-relationships-in-linq-query-operations.md)
- [Koncepty dotazů](query-concepts.md)
