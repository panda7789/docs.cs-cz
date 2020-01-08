---
title: Přehled modelu objektu pro vytváření
ms.date: 03/30/2017
ms.assetid: b5dc81c4-7554-44b9-b513-769bd61e2e7b
ms.openlocfilehash: f344502453acbbb5c08e49b7c21a0f4e84a29ffa
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75348389"
---
# <a name="factory-model-overview"></a>Přehled modelu objektu pro vytváření
ADO.NET 2,0 zavedl nové základní třídy v oboru názvů <xref:System.Data.Common>. Základní třídy jsou abstraktní, což znamená, že nelze vytvořit instanci přímo. Zahrnují <xref:System.Data.Common.DbConnection>, <xref:System.Data.Common.DbCommand>a <xref:System.Data.Common.DbDataAdapter> a sdílí je .NET Framework poskytovatelé dat, jako je například <xref:System.Data.SqlClient> a <xref:System.Data.OleDb>. Přidání základních tříd zjednodušuje přidávání funkcí zprostředkovatelům dat .NET Framework bez nutnosti vytvářet nová rozhraní.  
  
 ADO.NET 2,0 také zavedl abstraktní základní třídy, které vývojářům umožňují psát obecný kód přístupu k datům, který není závislý na konkrétním poskytovateli dat.  
  
## <a name="the-factory-design-pattern"></a>Vzor návrhu výroby  
 Programovací model pro psaní kódu nezávislého na poskytovateli je založen na použití vzoru návrhu "továrna", který používá jedno rozhraní API pro přístup k databázím napříč více zprostředkovateli. Tento model je aptly s názvem, protože volá pro použití specializovaného objektu výhradně pro vytváření jiných objektů, podobně jako reálné továrny. Podrobnější popis modelu návrhu továrny najdete v tématu [zápis obecného kódu přístupu k datům v ASP.NET 2,0 a ADO.NET 2,0](https://docs.microsoft.com/previous-versions/dotnet/articles/ms971499(v=msdn.10)).
  
 Počínaje verzí ADO.NET 2,0 poskytuje třída <xref:System.Data.Common.DbProviderFactories> `static` (nebo `Shared` v Visual Basic) metody pro vytvoření instance <xref:System.Data.Common.DbProviderFactory>. Instance pak vrátí správný objekt silného typu na základě informací o zprostředkovateli a připojovací řetězec zadaný v době běhu.  
  
## <a name="see-also"></a>Viz také:

- [Získání DbProviderFactory](obtaining-a-dbproviderfactory.md)
- [DbConnection, DbCommand a DbException](dbconnection-dbcommand-and-dbexception.md)
- [Úpravy dat přes DbDataAdapter](modifying-data-with-a-dbdataadapter.md)
- [Přehled ADO.NET](ado-net-overview.md)
