---
title: Získání DbProviderFactory
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a16e4a4d-6a5b-45db-8635-19570e4572ae
ms.openlocfilehash: 9e9cf91559fe164fc42d5f9532428310fa1b16ed
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32759462"
---
# <a name="obtaining-a-dbproviderfactory"></a>Získání DbProviderFactory
Proces získání <xref:System.Data.Common.DbProviderFactory> zahrnuje předávání informací o zprostředkovatele dat pro <xref:System.Data.Common.DbProviderFactories> třídy. Na základě těchto informací <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> metoda vytvoří objekt pro vytváření zprostředkovatele silného typu. Chcete-li například vytvořit <xref:System.Data.SqlClient.SqlClientFactory>, můžete předat `GetFactory` řetězec s název zprostředkovatele, který je určený jako "System.Data.SqlClient". Další přetížení `GetFactory` trvá <xref:System.Data.DataRow>. Jakmile vytvoříte objekt pro vytváření zprostředkovatelů, pak můžete jeho metody vytvořit další objekty. Některé z metod `SqlClientFactory` zahrnují <xref:System.Data.SqlClient.SqlClientFactory.CreateConnection%2A>, <xref:System.Data.SqlClient.SqlClientFactory.CreateCommand%2A>, a <xref:System.Data.SqlClient.SqlClientFactory.CreateDataAdapter%2A>.  
  
> [!NOTE]
>  Rozhraní .NET Framework <xref:System.Data.OracleClient.OracleClientFactory>, <xref:System.Data.Odbc.OdbcFactory>, a <xref:System.Data.OleDb.OleDbFactory> třídy také poskytuje podobné funkce.  
  
## <a name="registering-dbproviderfactories"></a>Registrace DbProviderFactories  
 Každý zprostředkovatel dat .NET Framework, který podporuje třídu na základě objektu pro vytváření registruje informace o konfiguraci v **DbProviderFactories** části **machine.config** souboru v místním počítači. Následující fragment souboru konfigurace ukazuje syntaxi a formát pro <xref:System.Data.SqlClient>.  
  
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
  
 **Invariantní** atribut určuje výchozí zprostředkovatel data. Tuto syntaxi pojmenování třemi částmi se také používá při vytváření nový objekt pro vytváření a k identifikaci zprostředkovatele v konfiguračním souboru aplikace tak, aby název zprostředkovatele, společně s jeho přidružené připojovací řetězec, se dá načíst za běhu.  
  
## <a name="retrieving-provider-information"></a>Načítání informací o zprostředkovateli  
 Můžete načíst informace o všech zprostředkovatelů dat, který je nainstalován v místním počítači pomocí <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> metoda. Vrátí <xref:System.Data.DataTable> s názvem **DbProviderFactories** obsahující sloupce, které jsou popsané v následující tabulce.  
  
|Pořadí sloupce|Název sloupce|Příklad výstupu|Popis|  
|--------------------|-----------------|--------------------|-----------------|  
|0|**Jméno**|Zprostředkovatel dat SqlClient|Čitelný název pro poskytovatele dat.|  
|1|**Popis**|Zprostředkovatel dat .net framework pro SQL Server|Čitelný Popis zprostředkovatele dat|  
|2|**InvariantName**|System.Data.SqlClient|Název, které je možné programově odkazovat na poskytovatele dat.|  
|3|**AssemblyQualifiedName**|System.Data.SqlClient.SqlClientFactory System.Data, verze = 2.0.0.0, Culture = neutral, PublicKeyToken = b77a5c561934e089|Plně kvalifikovaný název objektu pro vytváření třídy, která obsahuje dostatek informací pro vytvoření instance objektu|  
  
 To `DataTable` umožňuje povolit uživateli vybrat <xref:System.Data.DataRow> za běhu. Vybraný `DataRow` může být předána do <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> metodu pro vytvoření silného typu <xref:System.Data.Common.DbProviderFactory>. Vybrané <xref:System.Data.DataRow> lze předat `GetFactory` metodu pro vytvoření požadovanou `DbProviderFactory` objektu.  
  
## <a name="listing-the-installed-provider-factory-classes"></a>Výpis nainstalovaného zprostředkovatele objekt pro vytváření tříd  
 Tento příklad ukazuje, jak používat <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> metoda vrátí <xref:System.Data.DataTable> obsahující informace o poskytovateli nainstalované. Kód iteruje každý řádek `DataTable`, zobrazení informací o pro každého zprostředkovatele nainstalovaná v okně konzoly.  
  
 [!code-csharp[DataWorks DbProviderFactories#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories/VB/source.vb#1)]  
  
## <a name="using-application-configuration-files-to-store-factory-information"></a>Pomocí konfigurační soubory aplikace uložit informace o vytváření  
 Vzor návrhu používané pro práci s objekty Factory ukládání informací o řetězce zprostředkovatele a připojení v konfiguračním souboru aplikace, jako má za následek **app.config** pro aplikace systému Windows a **souboru web.config**  pro aplikaci ASP.NET.  
  
 Následující fragment souboru konfigurace ukazuje, jak uložit dva řetězce připojení s názvem "NorthwindSQL" pro připojení k databázi Northwind v systému SQL Server a "NorthwindAccess" pro připojení k databázi Northwind přístup/Jet. **Invariantní** název se používá pro **providerName** atribut.  
  
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
  
### <a name="retrieving-a-connection-string-by-provider-name"></a>Načítání podle názvu zprostředkovatele připojovací řetězec  
 Chcete-li vytvořit objekt pro vytváření zprostředkovatele, je třeba zadat připojovací řetězec, jakož i název zprostředkovatele. Tento příklad ukazuje, jak k získání připojovacího řetězce z konfiguračního souboru aplikace předáním název zprostředkovatele v neutrálním formátu "*System.Data.ProviderName*". Kód iteruje <xref:System.Configuration.ConnectionStringSettingsCollection>. Vrátí <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A> v případě úspěchu; v opačném případě `null` (`Nothing` v jazyce Visual Basic). Pokud existuje více položek pro zprostředkovatele, je vrácen první z nich najít. Další informace a příklady načítání připojovací řetězce z konfiguračních souborů najdete v tématu [připojovací řetězce a konfigurační soubory](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).  
  
> [!NOTE]
>  Odkaz na `System.Configuration.dll` je nutná pro kód pro spuštění.  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/VB/source.vb#1)]  
  
## <a name="creating-the-dbproviderfactory-and-dbconnection"></a>Vytváření DbProviderFactory a DbConnection  
 Tento příklad ukazuje, jak vytvořit <xref:System.Data.Common.DbProviderFactory> a <xref:System.Data.Common.DbConnection> objekt pomocí předání název zprostředkovatele ve formátu "*System.Data.ProviderName*" a připojovací řetězec. A `DbConnection` objektu se vrátí v případě úspěchu; `null` (`Nothing` v jazyce Visual Basic) na všechny chyby.  
  
 Získá kód `DbProviderFactory` voláním <xref:System.Data.Common.DbProviderFactories.GetFactory%2A>. Pak se <xref:System.Data.Common.DbProviderFactory.CreateConnection%2A> metoda vytvoří <xref:System.Data.Common.DbConnection> objektu a <xref:System.Data.Common.DbConnection.ConnectionString%2A> je nastavena na připojovací řetězec.  
  
 [!code-csharp[DataWorks DbProviderFactories.GetFactory#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.GetFactory/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.GetFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.GetFactory/VB/source.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 [Připojovací řetězce](../../../../docs/framework/data/adonet/connection-strings.md)  
 [Pomocí třídy konfigurace](http://msdn.microsoft.com/library/98d2b386-baf6-4a17-974b-76e3b4c87acc)  
 [ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady](http://go.microsoft.com/fwlink/?LinkId=217917)
