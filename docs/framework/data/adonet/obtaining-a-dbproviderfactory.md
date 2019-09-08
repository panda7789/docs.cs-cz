---
title: Získání DbProviderFactory
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a16e4a4d-6a5b-45db-8635-19570e4572ae
ms.openlocfilehash: bde442e344ae8aa710d75c61d0957bff9264bf01
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783544"
---
# <a name="obtaining-a-dbproviderfactory"></a>Získání DbProviderFactory
Proces získání a <xref:System.Data.Common.DbProviderFactory> zahrnuje předávání informací o poskytovateli dat <xref:System.Data.Common.DbProviderFactories> do třídy. Na základě těchto informací <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> metoda vytvoří továrnu poskytovatele silného typu. Například pro vytvoření <xref:System.Data.SqlClient.SqlClientFactory>můžete předat `GetFactory` řetězec s názvem poskytovatele zadaným jako "System. data. SqlClient". Druhé přetížení `GetFactory` <xref:System.Data.DataRow>přebírá. Po vytvoření továrny poskytovatele pak můžete použít jeho metody k vytvoření dalších objektů. Některé metody `SqlClientFactory` zahrnutí <xref:System.Data.SqlClient.SqlClientFactory.CreateConnection%2A>, <xref:System.Data.SqlClient.SqlClientFactory.CreateCommand%2A>, a <xref:System.Data.SqlClient.SqlClientFactory.CreateDataAdapter%2A>.  
  
> [!NOTE]
> Třídy .NET Framework <xref:System.Data.OracleClient.OracleClientFactory>, <xref:System.Data.Odbc.OdbcFactory>a <xref:System.Data.OleDb.OleDbFactory> také poskytují podobné funkce.  
  
## <a name="registering-dbproviderfactories"></a>Registrace DbProviderFactories  
 Každý zprostředkovatel dat .NET Framework, který podporuje třídu založenou na výrobě, registruje informace o konfiguraci v části **DbProviderFactories** souboru **Machine. config** v místním počítači. Následující fragment konfiguračního souboru ukazuje syntaxi a formát pro <xref:System.Data.SqlClient>.  
  
```xml  
<system.data>  
  <DbProviderFactories>  
    <add name="SqlClient Data Provider"  
     invariant="System.Data.SqlClient"   
     description=".Net Framework Data Provider for SqlServer"   
     type="System.Data.SqlClient.SqlClientFactory, System.Data,   
     Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"  
    />  
  </DbProviderFactories>  
</system.data>  
```  
  
 **Invariantní** atribut identifikuje základního zprostředkovatele dat. Tato syntaxe názvů se třemi částmi se používá také při vytváření nového objektu pro vytváření a identifikaci poskytovatele v konfiguračním souboru aplikace tak, aby se v době běhu mohl načíst název poskytovatele společně s jeho přidruženým připojovacím řetězcem.  
  
## <a name="retrieving-provider-information"></a>Načítání informací o poskytovateli  
 Informace o všech poskytovatelích dat nainstalovaných v místním počítači můžete získat pomocí <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> metody. Vrátí <xref:System.Data.DataTable> název s názvem **DbProviderFactories** , který obsahuje sloupce popsané v následující tabulce.  
  
|Ordinální číslo sloupce|Název sloupce|Příklad výstupu|Popis|  
|--------------------|-----------------|--------------------|-----------------|  
|0|**Název**|Zprostředkovatel dat SqlClient|Čitelný název poskytovatele dat|  
|1|**Popis**|Zprostředkovatel dat rozhraní .NET Framework pro SqlServer|Čitelný Popis poskytovatele dat|  
|2|**InvariantName**|System.Data.SqlClient|Název, který se dá použít programově pro odkazování na poskytovatele dat|  
|3|**AssemblyQualifiedName**|System. data. SqlClient. SqlClientFactory, System. data, verze = 2.0.0.0, Culture = neutral, PublicKeyToken = b77a5c561934e089|Plně kvalifikovaný název třídy Factory, která obsahuje dostatek informací pro vytvoření instance objektu|  
  
 Dá se použít k tomu, aby uživatel mohl <xref:System.Data.DataRow> vybrat v době běhu. `DataTable` Vybraný `DataRow` lze následně předat <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> metodě pro vytvoření silného typu <xref:System.Data.Common.DbProviderFactory>. Vybraná <xref:System.Data.DataRow> `GetFactory` metoda může být předána metodě pro vytvoření požadovaného `DbProviderFactory` objektu.  
  
## <a name="listing-the-installed-provider-factory-classes"></a>Výpis instalovaných tříd objektů pro vytváření zprostředkovatele  
 Tento příklad ukazuje, jak použít <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> metodu k <xref:System.Data.DataTable> vrácení obsahující informace o nainstalovaných poskytovatelích. Kód projde každým řádkem v `DataTable`a zobrazí informace pro každého nainstalovaného poskytovatele v okně konzoly.  
  
 [!code-csharp[DataWorks DbProviderFactories#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories/VB/source.vb#1)]  
  
## <a name="using-application-configuration-files-to-store-factory-information"></a>Použití konfiguračních souborů aplikace k ukládání informací o výrobě  
 Vzor návrhu používaný pro práci s továrnami zahrnuje ukládání informací o poskytovateli a připojovacím řetězci do konfiguračního souboru aplikace, jako je například **App. config** pro aplikace systému Windows a **Web. config** pro aplikaci ASP.NET.  
  
 Následující fragment konfiguračního souboru ukazuje, jak uložit dva pojmenované připojovací řetězce, "NorthwindSQL" pro připojení k databázi Northwind v SQL Server a "NorthwindAccess" pro připojení k databázi Northwind v Accessu a stroji Jet. **Neutrální** název se používá pro atribut **ProviderName** .  
  
```xml  
<configuration>  
  <connectionStrings>  
    <clear/>  
    <add name="NorthwindSQL"   
     providerName="System.Data.SqlClient"   
     connectionString=  
     "Data Source=MSSQL1;Initial Catalog=Northwind;Integrated Security=true"  
    />  
  
    <add name="NorthwindAccess"   
     providerName="System.Data.OleDb"   
     connectionString=  
     "Provider=Microsoft.Jet.OLEDB.4.0;Data Source=C:\Data\Northwind.mdb;"  
    />  
  </connectionStrings>  
</configuration>  
```  
  
### <a name="retrieving-a-connection-string-by-provider-name"></a>Načítání připojovacího řetězce podle názvu poskytovatele  
 Aby bylo možné vytvořit továrnu poskytovatele, je nutné dodat připojovací řetězec i název poskytovatele. Tento příklad ukazuje, jak načíst připojovací řetězec z konfiguračního souboru aplikace předáním názvu poskytovatele v neutrálním formátu "*System. data. ProviderName*". Kód prochází pomocí <xref:System.Configuration.ConnectionStringSettingsCollection>. Vrátí <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A> při úspěchu, jinak `null` (`Nothing` v Visual Basic). Pokud je pro poskytovatele k dispozici více položek, vrátí se první nalezený. Další informace a příklady načítání připojovacích řetězců z konfiguračních souborů najdete v tématu [připojovací řetězce a konfigurační soubory](connection-strings-and-configuration-files.md).  
  
> [!NOTE]
> Odkaz na `System.Configuration.dll` je vyžadován, aby bylo možné kód spustit.  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/VB/source.vb#1)]  
  
## <a name="creating-the-dbproviderfactory-and-dbconnection"></a>Vytváření DbProviderFactory a DbConnection  
 Tento příklad ukazuje, jak vytvořit <xref:System.Data.Common.DbProviderFactory> objekt a <xref:System.Data.Common.DbConnection> pomocí předání názvu poskytovatele ve formátu "*System. data. ProviderName*" a připojovací řetězec. `DbConnection` Objekt je vrácen při úspěchu; `null` (`Nothing` v Visual Basic) na jakékoli chybě.  
  
 Kód získá `DbProviderFactory` voláním <xref:System.Data.Common.DbProviderFactories.GetFactory%2A>. Pak metoda vytvoří objekt a <xref:System.Data.Common.DbConnection.ConnectionString%2A> vlastnost je nastavena na připojovací řetězec. <xref:System.Data.Common.DbConnection> <xref:System.Data.Common.DbProviderFactory.CreateConnection%2A>  
  
 [!code-csharp[DataWorks DbProviderFactories.GetFactory#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.GetFactory/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.GetFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.GetFactory/VB/source.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- [DbProviderFactories](dbproviderfactories.md)
- [Připojovací řetězce](connection-strings.md)
- [Použití tříd konfigurace](https://docs.microsoft.com/previous-versions/aspnet/ms228063(v=vs.100))
- [Přehled ADO.NET](ado-net-overview.md)
