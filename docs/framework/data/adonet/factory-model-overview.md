---
title: Přehled modelu objektu pro vytváření
ms.date: 03/30/2017
ms.assetid: b5dc81c4-7554-44b9-b513-769bd61e2e7b
ms.openlocfilehash: 7d50ddd3b02b66a5b2be41eaba5cf9a497b5f1b3
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795084"
---
# <a name="factory-model-overview"></a>Přehled modelu objektu pro vytváření
ADO.NET 2,0 zavedl v <xref:System.Data.Common> oboru názvů nové základní třídy. Základní třídy jsou abstraktní, což znamená, že nelze vytvořit instanci přímo. Zahrnují <xref:System.Data.Common.DbConnection>, <xref:System.Data.Common.DbCommand> <xref:System.Data.OleDb>a a jsou sdíleny .NET Framework poskytovateli dat, <xref:System.Data.SqlClient> <xref:System.Data.Common.DbDataAdapter> jako jsou a. Přidání základních tříd zjednodušuje přidávání funkcí zprostředkovatelům dat .NET Framework bez nutnosti vytvářet nová rozhraní.  
  
 ADO.NET 2,0 také zavedl abstraktní základní třídy, které vývojářům umožňují psát obecný kód přístupu k datům, který není závislý na konkrétním poskytovateli dat.  
  
## <a name="the-factory-design-pattern"></a>Vzor návrhu výroby  
 Programovací model pro psaní kódu nezávislého na poskytovateli je založen na použití vzoru návrhu "továrna", který používá jedno rozhraní API pro přístup k databázím napříč více zprostředkovateli. Tento model je aptly s názvem, protože volá pro použití specializovaného objektu výhradně pro vytváření jiných objektů, podobně jako reálné továrny. Podrobnější popis modelu návrhu továrny najdete v tématu [zápis obecného kódu přístupu k datům v ASP.NET 2,0 a ADO.NET 2,0](https://go.microsoft.com/fwlink/?LinkId=55915).
  
 Počínaje verzí ADO.NET <xref:System.Data.Common.DbProviderFactories> 2,0 poskytuje `static` třída (nebo `Shared` v Visual Basic) metody pro vytvoření <xref:System.Data.Common.DbProviderFactory> instance. Instance pak vrátí správný objekt silného typu na základě informací o zprostředkovateli a připojovací řetězec zadaný v době běhu.  
  
## <a name="see-also"></a>Viz také:

- [Získání DbProviderFactory](obtaining-a-dbproviderfactory.md)
- [DbConnection, DbCommand a DbException](dbconnection-dbcommand-and-dbexception.md)
- [Úpravy dat přes DbDataAdapter](modifying-data-with-a-dbdataadapter.md)
- [Přehled ADO.NET](ado-net-overview.md)
