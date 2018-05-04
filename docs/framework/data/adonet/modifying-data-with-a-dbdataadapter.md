---
title: Úprava dat s DbDataAdapter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e35c7f9e-648b-4fcc-9361-d365c3e42c9a
ms.openlocfilehash: 851c724d354b0e819ca320c32e98249f2ec66506
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="modifying-data-with-a-dbdataadapter"></a>Úprava dat s DbDataAdapter
<xref:System.Data.Common.DbProviderFactory.CreateDataAdapter%2A> Metodu <xref:System.Data.Common.DbProviderFactory> objekt získáte <xref:System.Data.Common.DbDataAdapter> objekt, který je pro základní data poskytovatele určeného v okamžiku vytvoření objektu pro vytváření silného typu. Pak můžete použít <xref:System.Data.Common.DbCommandBuilder> k vytvoření příkazů k vložení, aktualizace a odstranění dat z <xref:System.Data.DataSet> ke zdroji dat.  
  
## <a name="retrieving-data-with-a-dbdataadapter"></a>Načítání dat s DbDataAdapter  
 Tento příklad ukazuje, jak vytvořit silného typu `DbDataAdapter` podle zprostředkovatele název a připojovací řetězec. Kód používá <xref:System.Data.Common.DbProviderFactory.CreateConnection%2A> metodu <xref:System.Data.Common.DbProviderFactory> k vytvoření <xref:System.Data.Common.DbConnection>. V dalším kroku kód používá <xref:System.Data.Common.DbProviderFactory.CreateCommand%2A> metodu pro vytvoření <xref:System.Data.Common.DbCommand> vyberte data nastavením jeho `CommandText` a `Connection` vlastnosti. Nakonec kód vytvoří <xref:System.Data.Common.DbDataAdapter> pomocí <xref:System.Data.Common.DbProviderFactory.CreateDataAdapter%2A> metoda a nastaví její `SelectCommand` vlastnost. `Fill` Metodu `DbDataAdapter` načte data do <xref:System.Data.DataTable>.  
  
 [!code-csharp[DataWorks DbProviderFactories.DbDataAdapter#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapter/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbDataAdapter#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapter/VB/source.vb#1)]  
  
## <a name="modifying-data-with-a-dbdataadapter"></a>Úprava dat s DbDataAdapter  
 Tento příklad ukazuje, jak upravovat data v `DataTable` pomocí <xref:System.Data.Common.DbDataAdapter> pomocí <xref:System.Data.Common.DbCommandBuilder> ke generování příkazy potřebné pro aktualizace dat ve zdroji dat. <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> z `DbDataAdapter` je nastaven k načtení CustomerID a NázevSpolečnosti z tabulky zákazníků. <xref:System.Data.Common.DbCommandBuilder.GetInsertCommand%2A> Metoda se používá k nastavení <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> vlastnost, <xref:System.Data.Common.DbCommandBuilder.GetUpdateCommand%2A> metoda se používá k nastavení <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> vlastnost a <xref:System.Data.Common.DbCommandBuilder.GetDeleteCommand%2A> metoda se používá k nastavení <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> vlastnost. Kód přidá nový řádek do tabulky Zákazníci a aktualizuje zdroj dat. Kód poté vyhledá přidané řádek, a to vyhledáním ID zákazníka, která je definovaný primární klíč pro tabulku zákazníků. Ho změny název společnosti a aktualizace zdroje dat. Kódu nakonec odstraní řádek.  
  
 [!code-csharp[DataWorks DbProviderFactories.DbDataAdapterModify#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapterModify/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbDataAdapterModify#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapterModify/VB/source.vb#1)]  
  
## <a name="handling-parameters"></a>Zpracování parametrů  
 Zprostředkovatelé dat rozhraní .NET Framework zpracování pojmenování a určení parametrů a zástupné symboly parametrů jinak. Tato syntaxe je přizpůsobit konkrétní zdroj dat., jak je popsáno v následující tabulce.  
  
|Zprostředkovatel dat|Syntaxe parametru pojmenování|  
|-------------------|-----------------------------|  
|`SqlClient`|Používá pojmenované parametry ve formátu `@` *parametername*.|  
|`OracleClient`|Používá pojmenované parametry ve formátu `:` *parmname* (nebo *parmname*).|  
|`OleDb`|Používá značky poziční parametr indikován otazník (`?`).|  
|`Odbc`|Používá značky poziční parametr indikován otazník (`?`).|  
  
 Model objektu pro vytváření není vhodné pro vytvoření parametrizované `DbCommand` a `DbDataAdapter` objekty. Musíte větev ve vašem kódu parametry, které jsou přizpůsobené ke zprostředkovateli dat vytvořit.  
  
> [!IMPORTANT]
>  Zamezení specifický pro zprostředkovatele parametry zcela pomocí zřetězení řetězců můžete vytvořit přímých příkazů jazyka SQL není doporučeno z bezpečnostních důvodů. Pomocí zřetězení řetězců místo parametry opustí vaši aplikaci bude zranitelný vůči útoku prostřednictvím injektáže SQL.  
  
## <a name="see-also"></a>Viz také  
 [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 [Získání DbProviderFactory](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)  
 [DbConnection, DbCommand a DbException](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
