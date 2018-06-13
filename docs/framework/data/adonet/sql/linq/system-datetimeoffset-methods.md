---
title: System.DateTimeOffset metody
ms.date: 03/30/2017
ms.assetid: 25b3e5c0-7603-4a70-b3e5-2149e3da69a2
ms.openlocfilehash: 7fc6502f899e953637d23c0d54cc5fe615c38eea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33363309"
---
# <a name="systemdatetimeoffset-methods"></a>System.DateTimeOffset metody
Jakmile namapovány v modelu objektu nebo externí mapování souboru, technologie LINQ to SQL umožňuje volat většinu <xref:System.DateTimeOffset?displayProperty=nameWithType> metody, operátory a vlastnosti z vaší LINQ dotazy SQL.  
  
 Pouze metody není podporované jsou tyto zděděné z <xref:System.Object?displayProperty=nameWithType> , smysl v kontextu LINQ dotazy SQL, jako například: `Finalize`, `GetHashCode`, `GetType`, a `MemberwiseClone`. Tyto metody nejsou podporovány, protože technologie LINQ to SQL nemůže překládat pro spuštění systému SQL Server.  
  
> [!NOTE]
>  Modul CLR (CLR) <xref:System.DateTimeOffset?displayProperty=nameWithType> strukturu a možnost mapovat SQL `DATETIMEOFFSET` sloupec s technologie LINQ to SQL, vyžaduje rozhraní .NET Framework 3.5 SP1 nebo novější. SQL `DATETIMEOFFSET` sloupec je k dispozici v systému Microsoft SQL Server 2008 a nad rámec.  
  
## <a name="sqlmethods-date-and-time-methods"></a>SQLMethods datum a čas metody  
 Kromě metod, které nabízí <xref:System.DateTimeOffset> struktura, technologie LINQ to SQL nabízí metody uvedené v následující tabulce z <xref:System.Data.Linq.SqlClient.SqlMethods?displayProperty=nameWithType> třídy pro práci s datum a čas.  
  
||||  
|-|-|-|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffDay%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMillisecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffNanosecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffHour%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMinute%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffSecond%2A>|  
|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMicrosecond%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffMonth%2A>|<xref:System.Data.Linq.SqlClient.SqlMethods.DateDiffYear%2A>|  
  
## <a name="see-also"></a>Viz také  
 [Koncepty dotazů](../../../../../../docs/framework/data/adonet/sql/linq/query-concepts.md)  
 [Vytvoření objektového modelu](../../../../../../docs/framework/data/adonet/sql/linq/creating-the-object-model.md)  
 [Mapování typů SQL a CLR](../../../../../../docs/framework/data/adonet/sql/linq/sql-clr-type-mapping.md)
