---
title: "Přehled modelu objektu pro vytváření"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b5dc81c4-7554-44b9-b513-769bd61e2e7b
caps.latest.revision: "4"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 0194cd6789ae6ddebeeee65abf1a4fca4a2bc0d6
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="factory-model-overview"></a>Přehled modelu objektu pro vytváření
ADO.NET 2.0 zavedeny nové základní třídy v <xref:System.Data.Common> oboru názvů. Základní třídy, je abstraktních, což znamená, že se nemůže být přímo vytvořeny instance. Patří mezi ně <xref:System.Data.Common.DbConnection>, <xref:System.Data.Common.DbCommand>, a <xref:System.Data.Common.DbDataAdapter> a jsou sdíleny zprostředkovatele dat .NET Framework, jako například <xref:System.Data.SqlClient> a <xref:System.Data.OleDb>. Přidání třídy base zjednodušuje přidání funkce do zprostředkovatele dat .NET Framework bez nutnosti vytvořit nové rozhraní.  
  
 ADO.NET 2.0 zavedli taky abstraktní základní třídy, které umožňují vývojáři psát kód obecných datových přístup, který není závislá na konkrétní data zprostředkovatele.  
  
## <a name="the-factory-design-pattern"></a>Vzor návrhu objektu pro vytváření  
 Programovací model pro psaní kódu nezávislé na zprostředkovatele je založen na použití vzoru návrhu s "factory", která využívá jediného rozhraní API pro přístup k databázím napříč více poskytovatelů. Tento vzor je vhodně pojmenované, jak se vyžaduje použití specializované objektu výhradně k vytvoření jiné objekty, podobně jako objekt pro vytváření reálných. Podrobnější popis tohoto vzoru návrhu factory najdete v tématu "[psaní kódu přístup obecná Data v technologii ASP.NET 2.0 a ADO.NET 2.0](http://go.microsoft.com/fwlink/?LinkId=55915)" a "Obecné kódování s the ADO.NET 2.0 základní třídy a objekty Factory" [http:// MSDN.microsoft.com/library/default.asp?url=/library/dnvs05/HTML/vsgenerics.asp](http://msdn.microsoft.com/library/default.asp?url=/library/dnvs05/html/vsgenerics.asp) na webu MSDN.  
  
 Od verze ADO.NET 2.0 <xref:System.Data.Common.DbProviderFactories> třída poskytuje `static` (nebo `Shared` v jazyce Visual Basic) metody pro vytváření <xref:System.Data.Common.DbProviderFactory> instance. Instance pak vrátí objekt správné silného typu na základě informací o zprostředkovateli služeb a připojovací řetězec zadaný v době běhu.  
  
## <a name="see-also"></a>Viz také  
 [Získání DbProviderFactory](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)  
 [DbConnection, DbCommand a DbException](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)  
 [Úpravy dat přes DbDataAdapter](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
