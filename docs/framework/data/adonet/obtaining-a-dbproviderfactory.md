---
title: Získání DbProviderFactory
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a16e4a4d-6a5b-45db-8635-19570e4572ae
ms.openlocfilehash: daaa93c4da16ac67b7f7018fdafdc2b2d9f0784a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54692779"
---
# <a name="obtaining-a-dbproviderfactory"></a>Získání DbProviderFactory
Proces získání <xref:System.Data.Common.DbProviderFactory> zahrnuje předávání informací o zprostředkovateli dat k <xref:System.Data.Common.DbProviderFactories> třídy. Na základě těchto informací, <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> metoda vytvoří objekt pro vytváření zprostředkovatele silného typu. Například, chcete-li vytvořit <xref:System.Data.SqlClient.SqlClientFactory>, můžete předat `GetFactory` řetězec s názvem zprostředkovatele zadán jako "System.Data.SqlClient". Další přetížení `GetFactory` přijímá <xref:System.Data.DataRow>. Jakmile vytvoříte objekt pro vytváření zprostředkovatele, pak můžete jeho metody vytvářet další objekty. Některé z metod `SqlClientFactory` zahrnují <xref:System.Data.SqlClient.SqlClientFactory.CreateConnection%2A>, <xref:System.Data.SqlClient.SqlClientFactory.CreateCommand%2A>, a <xref:System.Data.SqlClient.SqlClientFactory.CreateDataAdapter%2A>.  
  
> [!NOTE]
>  Rozhraní .NET Framework <xref:System.Data.OracleClient.OracleClientFactory>, <xref:System.Data.Odbc.OdbcFactory>, a <xref:System.Data.OleDb.OleDbFactory> třídy také poskytuje podobné funkce.  
  
## <a name="registering-dbproviderfactories"></a>Registrace DbProviderFactories  
 Každý zprostředkovatele dat .NET Framework, která podporuje třídy založený na objekt pro vytváření zaregistruje informace o konfiguraci v **DbProviderFactories** část **machine.config** souboru na místním počítači. Následující fragment konfigurační soubor ukazuje syntaxi a formát pro <xref:System.Data.SqlClient>.  
  
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
  
 **Invariantní** atribut identifikuje základní data zprostředkovatele. Tato syntaxe názvů třemi částmi slouží také při vytváření nový objekt pro vytváření a k identifikaci zprostředkovatele v konfiguračním souboru aplikace tak, aby název zprostředkovatele, společně s jeho přidružený připojovací řetězec, je možné načíst za běhu.  
  
## <a name="retrieving-provider-information"></a>Načítají se informace o poskytovateli  
 Můžete načíst informace o všech nainstalované na místním počítači pomocí zprostředkovatele dat <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> metody. Vrátí <xref:System.Data.DataTable> s názvem **DbProviderFactories** , která obsahuje sloupce, které jsou popsané v následující tabulce.  
  
|Pořadí sloupce|Název sloupce|Příklad výstupu|Popis|  
|--------------------|-----------------|--------------------|-----------------|  
|0|**Název**|Zprostředkovatel dat SqlClient|Čitelný název pro poskytovatele dat.|  
|1|**Popis**|.NET framework Data Provider pro SqlServer|Čitelný Popis zprostředkovatele dat|  
|2|**InvariantName**|System.Data.SqlClient|Název, který je možné prostřednictvím kódu programu k odkazování na poskytovatele dat|  
|3|**AssemblyQualifiedName**|System.Data.SqlClient.SqlClientFactory, System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089|Plně kvalifikovaný název třídy factory, který obsahuje dostatek informací pro vytvoření instance objektu|  
  
 To `DataTable` je možné povolit uživateli, aby vybral <xref:System.Data.DataRow> v době běhu. Vybrané `DataRow` je pak možné předat do <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> metodu pro vytvoření silného typu <xref:System.Data.Common.DbProviderFactory>. Vybrané <xref:System.Data.DataRow> mohou být předány `GetFactory` metodu pro vytvoření požadované `DbProviderFactory` objektu.  
  
## <a name="listing-the-installed-provider-factory-classes"></a>Seznam tříd objektů pro vytváření nainstalovaného poskytovatele  
 Tento příklad ukazuje, jak používat <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> metodu pro návrat <xref:System.Data.DataTable> obsahující informace o nainstalovaných zprostředkovatelů. Kód prochází každý řádek `DataTable`, zobrazení informací pro každý nainstalovaný poskytovatel v okně konzoly.  
  
 [!code-csharp[DataWorks DbProviderFactories#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories/VB/source.vb#1)]  
  
## <a name="using-application-configuration-files-to-store-factory-information"></a>Použití konfiguračních souborů aplikace pro Store Factory informace  
 Vzor návrhu používané pro práci s objekty pro vytváření zahrnuje ukládání zprostředkovatel a řetězec informace o připojení v konfiguračním souboru aplikace, jako například **app.config** pro aplikace Windows a **web.config**  pro aplikaci ASP.NET.  
  
 Následující fragment konfigurační soubor ukazuje, jak uložit dva pojmenovaného připojovacího řetězce "NorthwindSQL" pro připojení k databázi Northwind v systému SQL Server a "NorthwindAccess" pro připojení k databázi Northwind v přístup/Jet. **Invariantní** název se používá pro **providerName** atribut.  
  
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
  
### <a name="retrieving-a-connection-string-by-provider-name"></a>Načtení připojovacího řetězce podle názvu zprostředkovatele  
 Chcete-li vytvořit objekt poskytovatele, musíte zadat připojovací řetězec jako název zprostředkovatele. Tento příklad ukazuje, jak se načtení připojovacího řetězce z konfiguračního souboru aplikace předáním názvu zprostředkovatele v neutrálním formátu "*System.Data.ProviderName*". Kód prochází <xref:System.Configuration.ConnectionStringSettingsCollection>. Vrátí <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A> v případě úspěchu; jinak `null` (`Nothing` v jazyce Visual Basic). Pokud existuje více položek pro zprostředkovatele, vrátí se první z nich najít. Další informace a příklady načítání připojovacích řetězců z konfiguračních souborů naleznete v tématu [připojovací řetězce a konfigurační soubory](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).  
  
> [!NOTE]
>  Odkaz na `System.Configuration.dll` je nutná pro spuštění kódu.  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/VB/source.vb#1)]  
  
## <a name="creating-the-dbproviderfactory-and-dbconnection"></a>Vytváření DbProviderFactory a DbConnection  
 Tento příklad ukazuje, jak vytvořit <xref:System.Data.Common.DbProviderFactory> a <xref:System.Data.Common.DbConnection> objektu s předáním názvu zprostředkovatele rozhraní ve formátu "*System.Data.ProviderName*" a připojovací řetězec. A `DbConnection` objekt je vrácen v případě úspěchu; `null` (`Nothing` v jazyce Visual Basic) na všechny chyby.  
  
 Získá kód `DbProviderFactory` voláním <xref:System.Data.Common.DbProviderFactories.GetFactory%2A>. Pak bude <xref:System.Data.Common.DbProviderFactory.CreateConnection%2A> metoda vytvoří <xref:System.Data.Common.DbConnection> objektu a <xref:System.Data.Common.DbConnection.ConnectionString%2A> je nastavena na připojovací řetězec.  
  
 [!code-csharp[DataWorks DbProviderFactories.GetFactory#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.GetFactory/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.GetFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.GetFactory/VB/source.vb#1)]  
  
## <a name="see-also"></a>Viz také:
- [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)
- [Připojovací řetězce](../../../../docs/framework/data/adonet/connection-strings.md)
- [Použití tříd konfigurace](https://msdn.microsoft.com/library/98d2b386-baf6-4a17-974b-76e3b4c87acc)
- [ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře](https://go.microsoft.com/fwlink/?LinkId=217917)
