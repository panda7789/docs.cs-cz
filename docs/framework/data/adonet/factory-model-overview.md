---
title: Přehled modelu objektu pro vytváření
ms.date: 03/30/2017
ms.assetid: b5dc81c4-7554-44b9-b513-769bd61e2e7b
ms.openlocfilehash: 9efe6deb484b15cef08f616c154c893f5e8869e8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32764915"
---
# <a name="factory-model-overview"></a>Přehled modelu objektu pro vytváření
ADO.NET 2.0 zavedeny nové základní třídy v <xref:System.Data.Common> oboru názvů. Základní třídy, je abstraktních, což znamená, že se nemůže být přímo vytvořeny instance. Patří mezi ně <xref:System.Data.Common.DbConnection>, <xref:System.Data.Common.DbCommand>, a <xref:System.Data.Common.DbDataAdapter> a jsou sdíleny zprostředkovatele dat .NET Framework, jako například <xref:System.Data.SqlClient> a <xref:System.Data.OleDb>. Přidání třídy base zjednodušuje přidání funkce do zprostředkovatele dat .NET Framework bez nutnosti vytvořit nové rozhraní.  
  
 ADO.NET 2.0 zavedli taky abstraktní základní třídy, které umožňují vývojáři psát kód obecných datových přístup, který není závislá na konkrétní data zprostředkovatele.  
  
## <a name="the-factory-design-pattern"></a>Vzor návrhu objektu pro vytváření  
 Programovací model pro psaní kódu nezávislé na zprostředkovatele je založen na použití vzoru návrhu s "factory", která využívá jediného rozhraní API pro přístup k databázím napříč více poskytovatelů. Tento vzor je vhodně pojmenované, jak se vyžaduje použití specializované objektu výhradně k vytvoření jiné objekty, podobně jako objekt pro vytváření reálných. Podrobnější popis tohoto vzoru návrhu factory najdete v tématu "[psaní kódu přístup obecná Data v technologii ASP.NET 2.0 a ADO.NET 2.0](http://go.microsoft.com/fwlink/?LinkId=55915)" a "Obecné kódování s the ADO.NET 2.0 základní třídy a objekty Factory" [ http://msdn.microsoft.com/library/default.asp?url=/library/dnvs05/html/vsgenerics.asp ](http://msdn.microsoft.com/library/default.asp?url=/library/dnvs05/html/vsgenerics.asp) na webu MSDN.  
  
 Od verze ADO.NET 2.0 <xref:System.Data.Common.DbProviderFactories> třída poskytuje `static` (nebo `Shared` v jazyce Visual Basic) metody pro vytváření <xref:System.Data.Common.DbProviderFactory> instance. Instance pak vrátí objekt správné silného typu na základě informací o zprostředkovateli služeb a připojovací řetězec zadaný v době běhu.  
  
## <a name="see-also"></a>Viz také  
 [Získání DbProviderFactory](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)  
 [DbConnection, DbCommand a DbException](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)  
 [Úpravy dat přes DbDataAdapter](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
