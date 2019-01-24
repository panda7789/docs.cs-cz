---
title: Metody System.DateTimeOffset
ms.date: 03/30/2017
ms.assetid: 25b3e5c0-7603-4a70-b3e5-2149e3da69a2
ms.openlocfilehash: 46b1622cdc8a38544f1c8a8104abb935c9ff1269
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54637200"
---
# <a name="systemdatetimeoffset-methods"></a>Metody System.DateTimeOffset
Jakmile mapován v objektovém modelu nebo externí mapování souboru LINQ to SQL umožňuje volat většinu <xref:System.DateTimeOffset?displayProperty=nameWithType> metody, operátory a vlastností z LINQ na dotazy SQL.  
  
 Pouze metody nejsou podporovány jsou tyto zděděné z <xref:System.Object?displayProperty=nameWithType> , který nedávají smysl v kontextu technologie LINQ dotazy SQL, například: `Finalize`, `GetHashCode`, `GetType`, a `MemberwiseClone`. Tyto metody nejsou podporovány, protože technologie LINQ to SQL nelze přeložit spuštěn na serveru SQL Server.  
  
> [!NOTE]
>  Modul CLR (CLR) <xref:System.DateTimeOffset?displayProperty=nameWithType> strukturu a schopnost mapování na SQL `DATETIMEOFFSET` sloupec s LINQ to SQL, vyžaduje rozhraní .NET Framework 3.5 SP1 nebo novější. SQL `DATETIMEOFFSET` sloupec je k dispozici v systému Microsoft SQL Server 2008 a nad rámec.  
  
## <a name="sqlmethods-date-and-time-methods"></a>SQLMethods datum a čas metody  
 Kromě metod, které nabízí <xref:System.DateTimeOffset> strukturu, LINQ to SQL nabízí metody uvedené v následující tabulce z <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> tříd pro práci s datem a časem.  
  
||||  
|-|-|-|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffDay%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMillisecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffNanosecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffHour%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMinute%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffSecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMicrosecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMonth%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffYear%2A>|  
  
## <a name="see-also"></a>Viz také:
- [Koncepty dotazů](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)
- [Vytvoření objektového modelu](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)
- [Mapování typů SQL a CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)
