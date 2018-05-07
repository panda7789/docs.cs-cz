---
title: System.TimeSpan metody
ms.date: 03/30/2017
ms.assetid: 9333fee8-1454-4374-855b-8c14c002f48f
ms.openlocfilehash: 2cb7201c113fe72ce03d0308ab8f97dca585e602
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="systemtimespan-methods"></a>System.TimeSpan metody
Podpora člen <xref:System.TimeSpan?displayProperty=nameWithType> výrazně závisí na verze rozhraní .NET Framework a Microsoft SQL Server, který používáte.  
  
 Když metoda, operátor nebo vlastnost není podporována; znamená to, že technologie LINQ to SQL nemůže překládat člena pro spuštění systému SQL Server. Může být stále moct používat tyto členy ve vašem kódu. Ale že musí být vyhodnocena před dotaz převádějí do jazyka Transact-SQL nebo po výsledky byly získány z databáze.  
  
## <a name="previous-limitations"></a>Předchozí omezení  
 Při použití technologie LINQ to SQL s verze rozhraní .NET Framework před rozhraní .NET Framework 3.5 SP1, nelze mapovat pole databáze systému SQL Server k <xref:System.TimeSpan?displayProperty=nameWithType>. Ale operací na <xref:System.TimeSpan> jsou podporována, protože <xref:System.TimeSpan> hodnoty lze vrátit ze <xref:System.DateTime> odčítání nebo zasaženo výraz jako literál nebo vázané proměnnou.  
  
## <a name="supported-systemtimespan-method-support"></a>Podporovanou metodou System.TimeSpan podpory  
 Následující technologie LINQ to SQL podporované metody, operátory a vlastnosti jsou k dispozici pro použití v vaše dotazy LINQ to SQL. Jakmile namapovány v modelu objektu nebo externí mapování souboru, technologie LINQ to SQL umožňuje volat řadu <xref:System.TimeSpan?displayProperty=nameWithType> členy uvnitř vaší dotazy LINQ to SQL.  
  
|Podporované <xref:System.TimeSpan> metody|Podporované <xref:System.TimeSpan> operátory|Podporované <xref:System.TimeSpan> vlastnosti|  
|------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.TimeSpan.Compare%2A>|<xref:System.TimeSpan.op_Equality%2A>|<xref:System.TimeSpan.Days%2A>|  
|<xref:System.TimeSpan.CompareTo%28System.TimeSpan%29>|<xref:System.TimeSpan.op_GreaterThan%2A>|<xref:System.TimeSpan.Hours%2A>|  
|<xref:System.TimeSpan.Duration%2A>|<xref:System.TimeSpan.op_GreaterThanOrEqual%2A>|<xref:System.TimeSpan.MaxValue>|  
|<xref:System.TimeSpan.Equals%28System.TimeSpan%2CSystem.TimeSpan%29>|<xref:System.TimeSpan.op_Inequality%2A>|<xref:System.TimeSpan.Milliseconds%2A>|  
|<xref:System.TimeSpan.Equals%28System.TimeSpan%29>|<xref:System.TimeSpan.op_LessThan%2A>|<xref:System.TimeSpan.Minutes%2A>|  
||<xref:System.TimeSpan.op_LessThanOrEqual%2A>|<!--zz <xref:System.TimeSpan.MinValue%2A>-->|  
  
> [!NOTE]
>  Možnost mapovat <xref:System.TimeSpan?displayProperty=nameWithType> SQL `TIME` sloupec s technologie LINQ to SQL vyžaduje rozhraní .NET Framework 3.5 SP1 a dále. SQL `TIME` datový typ je k dispozici v systému Microsoft SQL Server 2008 a nad rámec.  
  
### <a name="addition-and-subtraction"></a>Sčítání a odečítání  
 I když modulu CLR <xref:System.TimeSpan?displayProperty=nameWithType> typu podporuje sčítání a odečítání SQL `TIME` typ neexistuje. Z toho důvodu vaše dotazy LINQ to SQL vygeneruje chyby, pokud pokoušejí sčítání a odečítání, když jsou namapované na SQL `TIME` typu. Můžete najít další důležité informace pro práci s typy SQL data a času v [mapování typu SQL CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).  
  
## <a name="see-also"></a>Viz také  
 [Koncepty dotazů](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 [Vytvoření objektového modelu](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)  
 [Mapování typů SQL a CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)  
 [Datové typy a funkce](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
