---
title: Úpravy dat přes DbDataAdapter
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: e35c7f9e-648b-4fcc-9361-d365c3e42c9a
ms.openlocfilehash: cd1f5faa0efe141dc064f0150b94807b90e7e2b8
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794830"
---
# <a name="modifying-data-with-a-dbdataadapter"></a>Úpravy dat přes DbDataAdapter
<xref:System.Data.Common.DbProviderFactory.CreateDataAdapter%2A> Metoda objektu<xref:System.Data.Common.DbProviderFactory> poskytuje objekt,kterýjesilnýmtypemprozákladníhozprostředkovatele<xref:System.Data.Common.DbDataAdapter> dat zadaného při vytváření objektu pro vytváření. Pak můžete použít <xref:System.Data.Common.DbCommandBuilder> k vytvoření příkazů pro vložení, aktualizaci a odstranění dat z a <xref:System.Data.DataSet> do zdroje dat.  
  
## <a name="retrieving-data-with-a-dbdataadapter"></a>Načítání dat pomocí objekt DbDataAdapter  
 Tento příklad ukazuje, jak vytvořit silného typu `DbDataAdapter` na základě názvu poskytovatele a připojovacího řetězce. Kód používá <xref:System.Data.Common.DbProviderFactory.CreateConnection%2A> metodu <xref:System.Data.Common.DbProviderFactory> pro vytvoření <xref:System.Data.Common.DbConnection>. Dále kód používá <xref:System.Data.Common.DbProviderFactory.CreateCommand%2A> metodu k <xref:System.Data.Common.DbCommand> vytvoření pro `CommandText` výběr dat nastavením vlastností a `Connection` . Nakonec kód vytvoří <xref:System.Data.Common.DbDataAdapter> objekt <xref:System.Data.Common.DbProviderFactory.CreateDataAdapter%2A> pomocí metody a nastaví jeho `SelectCommand` vlastnost. `Fill` Metoda`DbDataAdapter`načtedata do .<xref:System.Data.DataTable>  
  
 [!code-csharp[DataWorks DbProviderFactories.DbDataAdapter#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapter/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbDataAdapter#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapter/VB/source.vb#1)]  
  
## <a name="modifying-data-with-a-dbdataadapter"></a>Úpravy dat přes DbDataAdapter  
 Tento příklad ukazuje, jak změnit data v s `DataTable` <xref:System.Data.Common.DbDataAdapter> použitím <xref:System.Data.Common.DbCommandBuilder> pomocí a k vygenerování příkazů požadovaných pro aktualizaci dat ve zdroji dat. <xref:System.Data.Common.DbDataAdapter.SelectCommand%2A> Zjenastavenátak,abyztabulkyCustomszískala`DbDataAdapter` CustomerID a CompanyName. <xref:System.Data.Common.DbCommandBuilder.GetUpdateCommand%2A> <xref:System.Data.Common.DbCommandBuilder.GetDeleteCommand%2A> <xref:System.Data.Common.DbDataAdapter.UpdateCommand%2A> <xref:System.Data.Common.DbDataAdapter.DeleteCommand%2A> Metoda slouží k <xref:System.Data.Common.DbDataAdapter.InsertCommand%2A> nastavení vlastnosti, metoda slouží k nastavení vlastnosti a metoda je použita k nastavení vlastnosti. <xref:System.Data.Common.DbCommandBuilder.GetInsertCommand%2A> Kód přidá nový řádek do tabulky Customers a aktualizuje zdroj dat. Kód pak vyhledá přidaný řádek hledáním CustomerID, což je primární klíč definovaný pro tabulku Customers. Změní CompanyName a aktualizuje zdroj dat. Nakonec kód odstraní řádek.  
  
 [!code-csharp[DataWorks DbProviderFactories.DbDataAdapterModify#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapterModify/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.DbDataAdapterModify#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.DbDataAdapterModify/VB/source.vb#1)]  
  
## <a name="handling-parameters"></a>Zpracování parametrů  
 Poskytovatelé dat .NET Framework řídí pojmenování a zadání parametrů a zástupných symbolů parametrů odlišně. Tato syntaxe je přizpůsobená konkrétnímu zdroji dat, jak je popsáno v následující tabulce.  
  
|Poskytovatel dat|Syntaxe pojmenovávání parametrů|  
|-------------------|-----------------------------|  
|`SqlClient`|Používá pojmenované parametry ve formátu `@` *ParameterName*.|  
|`OracleClient`|Používá pojmenované parametry ve formátu `:` *parmname* (nebo *parmname*).|  
|`OleDb`|Používá poziční značky parametrů, které jsou označeny otazníkem (`?`).|  
|`Odbc`|Používá poziční značky parametrů, které jsou označeny otazníkem (`?`).|  
  
 Model výroby není užitečný pro vytváření parametrizovaných `DbCommand` a `DbDataAdapter` objektů. K vytvoření parametrů, které jsou přizpůsobené vašemu poskytovateli dat, budete muset vytvořit větev ve svém kódu.  
  
> [!IMPORTANT]
> Vyloučení parametrů specifických pro konkrétního poskytovatele zcela pomocí zřetězení řetězců k vytvoření přímých příkazů SQL se z bezpečnostních důvodů nedoporučuje. Použití zřetězení řetězců namísto parametrů opustí vaši aplikaci proti útokům prostřednictvím injektáže SQL.  
  
## <a name="see-also"></a>Viz také:

- [DbProviderFactories](dbproviderfactories.md)
- [Získání DbProviderFactory](obtaining-a-dbproviderfactory.md)
- [DbConnection, DbCommand a DbException](dbconnection-dbcommand-and-dbexception.md)
- [Přehled ADO.NET](ado-net-overview.md)
