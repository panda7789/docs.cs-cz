---
title: Úpravy dat přes DbDataAdapter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e35c7f9e-648b-4fcc-9361-d365c3e42c9a
ms.openlocfilehash: 3038e35947cd8f97266d374a367a77380df440dd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772174"
---
# <a name="modifying-data-with-a-dbdataadapter"></a>Úpravy dat přes DbDataAdapter
<xref:System.Data.Common.DbProviderFactory.CreateDataAdapter%2A> Metodu <xref:System.Data.Common.DbProviderFactory> objekt získáte <xref:System.Data.Common.DbDataAdapter> objekt, který je silně typováno do podkladového zprostředkovatele dat zadané v době vytváření továrny. Pak můžete použít <xref:System.Data.Common.DbCommandBuilder> vytvořit příkazy pro vložení, aktualizace a odstranění dat z <xref:System.Data.DataSet> ke zdroji dat.  
  
## <a name="retrieving-data-with-a-dbdataadapter"></a>Načítání dat přes DbDataAdapter  
 Tento příklad ukazuje, jak vytvořit silného typu `DbDataAdapter` podle poskytovatele název a připojovací řetězce. Tento kód použije <xref:System.Data.Common.DbProviderFactory.CreateConnection%2A> metodu <xref:System.Data.Common.DbProviderFactory> k vytvoření <xref:System.Data.Common.DbConnection>. Dále kód použije <xref:System.Data.Common.DbProviderFactory.CreateCommand%2A> metodu pro vytvoření <xref:System.Data.Common.DbCommand> vyberte data tak, že nastavíte její `CommandText` a `Connection` vlastnosti. Nakonec kód vytvoří <xref:System.Data.Common.DbDataAdapter> pomocí <xref:System.Data.Common.DbProviderFactory.CreateDataAdapter%2A> metoda a nastaví její `SelectCommand` vlastnost. `Fill` Metodu `DbDataAdapter` načte data do <xref:System.Data.DataTable>.  
  
 [!code-csharp[DataWorks DbProviderFactories.DbDataAdapter#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapter/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbDataAdapter#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapter/VB/source.vb#1)]  
  
## <a name="modifying-data-with-a-dbdataadapter"></a>Úpravy dat přes DbDataAdapter  
 Tento příklad ukazuje, jak upravovat data v `DataTable` pomocí <xref:System.Data.Common.DbDataAdapter> pomocí <xref:System.Data.Common.DbCommandBuilder> Generovat příkazy potřebné pro aktualizace dat ve zdroji dat. <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> z `DbDataAdapter` je nastavena na načtení CustomerID a CompanyName z tabulky Zákazníci. <xref:System.Data.Common.DbCommandBuilder.GetInsertCommand%2A> Metoda se používá k nastavení <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> vlastnost, <xref:System.Data.Common.DbCommandBuilder.GetUpdateCommand%2A> metoda se používá k nastavení <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> vlastnost a <xref:System.Data.Common.DbCommandBuilder.GetDeleteCommand%2A> metoda se používá k nastavení <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> vlastnost. Kód přidá nový řádek do tabulky Zákazníci a k aktualizaci ve zdroji dat. Kód poté vyhledá přidaný řádek to vyhledáním ID zákazníka, který je primárním klíčem definovaný pro tabulku zákazníků. Změní název společnosti a k aktualizaci ve zdroji dat. Kódu nakonec odstraní řádek.  
  
 [!code-csharp[DataWorks DbProviderFactories.DbDataAdapterModify#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapterModify/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbDataAdapterModify#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapterModify/VB/source.vb#1)]  
  
## <a name="handling-parameters"></a>Zpracování parametrů  
 Zprostředkovatelé dat .NET Framework zpracovat pojmenování a určení parametrů a proměnných parametrů odlišně. Tato syntaxe je přizpůsobená pro konkrétní zdroj, jak je popsáno v následující tabulce.  
  
|Zprostředkovatel dat|Pojmenování syntaxe parametru|  
|-------------------|-----------------------------|  
|`SqlClient`|Použití pojmenované parametry ve formátu `@` *parametername*.|  
|`OracleClient`|Použití pojmenované parametry ve formátu `:` *parmname* (nebo *parmname*).|  
|`OleDb`|Používá značky pozičních parametrů více dopředu označeny otazníkem (`?`).|  
|`Odbc`|Používá značky pozičních parametrů více dopředu označeny otazníkem (`?`).|  
  
 Objekt pro vytváření modelu není vhodné pro vytvoření parametrizovaného `DbCommand` a `DbDataAdapter` objekty. Je potřeba větev v kódu k vytvoření parametry, které jsou přizpůsobené ke zprostředkovateli dat.  
  
> [!IMPORTANT]
>  Jak se vyhnout parametry specifické pro zprostředkovatele úplně pomocí zřetězení řetězců k sestavení kompletních přímých příkazů jazyka SQL se nedoporučuje z bezpečnostních důvodů. Pomocí zřetězení řetězců místo parametry opustí vaši aplikaci ohrožen útoky prostřednictvím injektáže SQL.  
  
## <a name="see-also"></a>Viz také:

- [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)
- [Získání DbProviderFactory](../../../../docs/framework/data/adonet/obtaining-a-dbproviderfactory.md)
- [DbConnection, DbCommand a DbException](../../../../docs/framework/data/adonet/dbconnection-dbcommand-and-dbexception.md)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
