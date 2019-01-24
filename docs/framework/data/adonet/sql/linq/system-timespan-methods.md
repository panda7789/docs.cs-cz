---
title: Metody System.TimeSpan
ms.date: 03/30/2017
ms.assetid: 9333fee8-1454-4374-855b-8c14c002f48f
ms.openlocfilehash: a3f3c82f9f8db4b72588f165ed4d897b974eb076
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54539906"
---
# <a name="systemtimespan-methods"></a>Metody System.TimeSpan
Podpora člen <xref:System.TimeSpan?displayProperty=nameWithType> značně závisí na verzích rozhraní .NET Framework a Microsoft SQL Server, kterou používáte.  
  
 Pokud metoda, operátor nebo vlastnost není podporována; To znamená, že technologie LINQ to SQL: nelze převést člena pro spuštění systému SQL Server. Může být stále moct používat tyto členy ve vašem kódu. Však musí být vyhodnocují před dotazu je přeložen příkazů jazyka Transact-SQL nebo po výsledky byly načteny z databáze.  
  
## <a name="previous-limitations"></a>Z předchozích omezení  
 Při použití technologie LINQ to SQL s verzemi rozhraní .NET Framework před rozhraní .NET Framework 3.5 SP1, nelze mapovat pole databáze systému SQL Server na <xref:System.TimeSpan?displayProperty=nameWithType>. Však operace <xref:System.TimeSpan> jsou podporované, protože <xref:System.TimeSpan> hodnoty mohou být vráceny od <xref:System.DateTime> odčítání nebo zařadit do výrazu jako literál nebo vazby proměnné.  
  
## <a name="supported-systemtimespan-member-support"></a>Podporované System.TimeSpan člen podpory

 Následující technologie LINQ to SQL podporované metody, operátory a vlastnosti jsou k dispozici pro použití ve vašich dotazech LINQ to SQL. Jakmile mapován v objektovém modelu nebo externí mapování souboru LINQ to SQL umožňuje volat řadu <xref:System.TimeSpan?displayProperty=nameWithType> členy ve vašich dotazech LINQ to SQL.  
  
|Podporované <xref:System.TimeSpan> metody|Podporované <xref:System.TimeSpan> operátory|Podporované <xref:System.TimeSpan> vlastnosti|  
|------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.TimeSpan.Compare%2A>|<xref:System.TimeSpan.op_Equality%2A>|<xref:System.TimeSpan.Days%2A>|  
|<xref:System.TimeSpan.CompareTo%28System.TimeSpan%29>|<xref:System.TimeSpan.op_GreaterThan%2A>|<xref:System.TimeSpan.Hours%2A>|  
|<xref:System.TimeSpan.Duration%2A>|<xref:System.TimeSpan.op_GreaterThanOrEqual%2A>|<xref:System.TimeSpan.MaxValue>|  
|<xref:System.TimeSpan.Equals%28System.TimeSpan%2CSystem.TimeSpan%29>|<xref:System.TimeSpan.op_Inequality%2A>|<xref:System.TimeSpan.Milliseconds%2A>|  
|<xref:System.TimeSpan.Equals%28System.TimeSpan%29>|<xref:System.TimeSpan.op_LessThan%2A>|<xref:System.TimeSpan.Minutes%2A>|  
||<xref:System.TimeSpan.op_LessThanOrEqual%2A>|<xref:System.TimeSpan.MinValue>|  
  
> [!NOTE]
>  Umožňuje mapovat <xref:System.TimeSpan?displayProperty=nameWithType> SQL `TIME` sloupec s LINQ to SQL se vyžaduje rozhraní .NET Framework 3.5 SP1 a novější. SQL `TIME` datový typ je k dispozici v systému Microsoft SQL Server 2008 a nad rámec.  
  
### <a name="addition-and-subtraction"></a>Sčítání a odčítání  
 I když CLR <xref:System.TimeSpan?displayProperty=nameWithType> typů podporuje sčítání a odčítání, SQL `TIME` typ nepodporuje. Z tohoto důvodu vašich dotazech LINQ to SQL se generují chyby se pokoušejí sčítání a odčítání, když jsou mapovány na SQL `TIME` typu. Můžete najít další důležité informace pro práci s typy data a času SQL v [mapování typů SQL a CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md).  
  
## <a name="see-also"></a>Viz také:
- [Koncepty dotazů](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [Vytvoření objektového modelu](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
- [Mapování typů SQL a CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)
- [Datové typy a funkce](../../../../../../docs/framework/data/adonet/sql/linq/data-types-and-functions.md)
