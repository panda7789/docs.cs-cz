---
title: Přehled modelu objekt pro vytváření
ms.date: 03/30/2017
ms.assetid: b5dc81c4-7554-44b9-b513-769bd61e2e7b
ms.openlocfilehash: 618a7c6d82facdda05517e4c201c266b84ac889c
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44083969"
---
# <a name="factory-model-overview"></a>Přehled modelu objekt pro vytváření
ADO.NET 2.0 zavedeny nové základní třídy v <xref:System.Data.Common> oboru názvů. Základní třídy jsou abstraktní, což znamená, že se nemůže být přímo vytvořeny instance. Patří mezi ně <xref:System.Data.Common.DbConnection>, <xref:System.Data.Common.DbCommand>, a <xref:System.Data.Common.DbDataAdapter> a sdílí zprostředkovatele dat .NET Framework, jako například <xref:System.Data.SqlClient> a <xref:System.Data.OleDb>. Přidání třídy base zjednodušuje přidáváme funkci pro zprostředkovatele dat .NET Framework bez nutnosti vytvářet nová rozhraní.  
  
 ADO.NET 2.0 zavedli abstraktní základní třídy, které umožňují vývojářům zapisovat obecných datových přístupový kód, který není závislý na konkrétní data zprostředkovatele.  
  
## <a name="the-factory-design-pattern"></a>Vzor návrhu objekt pro vytváření  
 Programovací model pro psaní kódu nezávislé na poskytovatele podle použití vzoru návrhu "factory", který používá jedno rozhraní API pro přístup k databázím napříč několika poskytovatelů. Tento model se jmenuje odpovídající, protože volá za použití specializovanou objekt výhradně pro vytvoření dalších objektů, podobně jako objekt pro vytváření skutečných. Podrobnější popis vzoru návrhu továrny najdete v tématu "[psaní obecného kód přístupu k datům v technologii ASP.NET 2.0 a ADO.NET 2.0](https://go.microsoft.com/fwlink/?LinkId=55915)" a "Obecný kódování pomocí rozhraní ADO.NET 2.0 základní třídy a objekty pro vytváření" [ http://msdn.microsoft.com/library/default.asp?url=/library/dnvs05/html/vsgenerics.asp ](https://msdn.microsoft.com/library/default.asp?url=/library/dnvs05/html/vsgenerics.asp) na webové stránce MSDN.  
  
 Spouštění pomocí technologie ADO.NET 2.0 <xref:System.Data.Common.DbProviderFactories> třída poskytuje `static` (nebo `Shared` v jazyce Visual Basic) metody pro vytváření <xref:System.Data.Common.DbProviderFactory> instance. Instance vrátí správné silně typovaných objektů na základě informací o zprostředkovateli a připojovací řetězec zadaný v době běhu.  
  
## <a name="see-also"></a>Viz také  
 [Získání DbProviderFactory](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)  
 [DbConnection, DbCommand a DbException](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)  
 [Úpravy dat přes DbDataAdapter](../../../../docs/framework/data/adonet/modifying-data-with-a-dbdataadapter.md)  
 [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
