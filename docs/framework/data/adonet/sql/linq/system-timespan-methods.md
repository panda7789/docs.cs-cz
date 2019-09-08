---
title: Metody System.TimeSpan
ms.date: 03/30/2017
ms.assetid: 9333fee8-1454-4374-855b-8c14c002f48f
ms.openlocfilehash: 9a7eb3c979219003d497ec752b36ec54ef081b43
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70781041"
---
# <a name="systemtimespan-methods"></a>Metody System.TimeSpan
Podpora <xref:System.TimeSpan?displayProperty=nameWithType> členů značně závisí na verzích .NET Framework a Microsoft SQL Server, které používáte.  
  
 Pokud metoda, operátor nebo vlastnost není podporována; To znamená, že LINQ to SQL nemůže přeložit člena ke spuštění na SQL Server. Je možné, že bude možné tyto členy stále používat ve svém kódu. Nicméně musí být vyhodnoceny dříve, než je dotaz přeložen do jazyka Transact-SQL nebo po načtení výsledků z databáze.  
  
## <a name="previous-limitations"></a>Předchozí omezení  
 Pokud používáte LINQ to SQL s verzemi .NET Framework před .NET Framework 3,5 SP1, nelze mapovat pole SQL Server databáze na <xref:System.TimeSpan?displayProperty=nameWithType>. Operace na <xref:System.TimeSpan> jsou však podporovány, protože <xref:System.TimeSpan> hodnoty mohou být vráceny z <xref:System.DateTime> odčítání nebo zavedeny do výrazu jako literál nebo vázaná proměnná.  
  
## <a name="supported-systemtimespan-member-support"></a>Podporovaná podpora členů System. TimeSpan

 Následující LINQ to SQL podporované metody, operátory a vlastnosti jsou k dispozici pro použití v dotazech LINQ to SQL. Po namapování v objektovém modelu nebo v souboru externího mapování vám LINQ to SQL umožňuje volat mnoho <xref:System.TimeSpan?displayProperty=nameWithType> členů v rámci vašich LINQ to SQL dotazů.  
  
|Podporované <xref:System.TimeSpan> metody|Podporované <xref:System.TimeSpan> operátory|Podporované <xref:System.TimeSpan> vlastnosti|  
|------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|  
|<xref:System.TimeSpan.Compare%2A>|<xref:System.TimeSpan.op_Equality%2A>|<xref:System.TimeSpan.Days%2A>|  
|<xref:System.TimeSpan.CompareTo%28System.TimeSpan%29>|<xref:System.TimeSpan.op_GreaterThan%2A>|<xref:System.TimeSpan.Hours%2A>|  
|<xref:System.TimeSpan.Duration%2A>|<xref:System.TimeSpan.op_GreaterThanOrEqual%2A>|<xref:System.TimeSpan.MaxValue>|  
|<xref:System.TimeSpan.Equals%28System.TimeSpan%2CSystem.TimeSpan%29>|<xref:System.TimeSpan.op_Inequality%2A>|<xref:System.TimeSpan.Milliseconds%2A>|  
|<xref:System.TimeSpan.Equals%28System.TimeSpan%29>|<xref:System.TimeSpan.op_LessThan%2A>|<xref:System.TimeSpan.Minutes%2A>|  
||<xref:System.TimeSpan.op_LessThanOrEqual%2A>|<xref:System.TimeSpan.MinValue>|  
  
> [!NOTE]
> Možnost mapování <xref:System.TimeSpan?displayProperty=nameWithType> na sloupec SQL `TIME` s LINQ to SQL vyžaduje .NET Framework 3,5 SP1 a novější. Datový typ `TIME` SQL je k dispozici pouze v Microsoft SQL Server 2008 a novějších.  
  
### <a name="addition-and-subtraction"></a>Sčítání a odčítání  
 I když typ <xref:System.TimeSpan?displayProperty=nameWithType> CLR podporuje sčítání a odčítání, typ SQL `TIME` není. Z tohoto důvodu budou dotazy LINQ to SQL generovat chyby, pokud se pokusí přidat a odčítání, pokud jsou namapovány na typ `TIME` SQL. Další informace o tom, jak pracovat s typy data a času SQL v [mapování typu SQL-CLR](sql-clr-type-mapping.md), najdete v dalších ohledech.  
  
## <a name="see-also"></a>Viz také:

- [Koncepty dotazů](query-concepts.md)
- [Vytvoření objektového modelu](creating-the-object-model.md)
- [Mapování typů SQL a CLR](sql-clr-type-mapping.md)
- [Datové typy a funkce](data-types-and-functions.md)
