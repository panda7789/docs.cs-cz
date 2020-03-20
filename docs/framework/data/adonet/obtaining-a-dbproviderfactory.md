---
title: Získání DbProviderFactory
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a16e4a4d-6a5b-45db-8635-19570e4572ae
ms.openlocfilehash: 0e2efd593019199ff641610b8602825cc60d4661
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149463"
---
# <a name="obtaining-a-dbproviderfactory"></a>Získání DbProviderFactory
Proces získání <xref:System.Data.Common.DbProviderFactory> zahrnuje předávání informací o zprostředkovateli <xref:System.Data.Common.DbProviderFactories> dat do třídy. Na základě těchto <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> informací metoda vytvoří vytvoření zprostředkovatele silného typu. Chcete-li například <xref:System.Data.SqlClient.SqlClientFactory>vytvořit , `GetFactory` můžete předat řetězec s názvem zprostředkovatele zadaným jako "System.Data.SqlClient". Další přetížení `GetFactory` trvá <xref:System.Data.DataRow>. Po vytvoření zprostředkovatele továrny, pak můžete použít jeho metody k vytvoření další objekty. Některé metody `SqlClientFactory` patří <xref:System.Data.SqlClient.SqlClientFactory.CreateConnection%2A>, <xref:System.Data.SqlClient.SqlClientFactory.CreateCommand%2A>, <xref:System.Data.SqlClient.SqlClientFactory.CreateDataAdapter%2A>a .  
  
> [!NOTE]
> Rozhraní .NET <xref:System.Data.OracleClient.OracleClientFactory> <xref:System.Data.Odbc.OdbcFactory>Framework <xref:System.Data.OleDb.OleDbFactory> a třídy také poskytují podobné funkce.  
  
## <a name="registering-dbproviderfactories"></a>Registrace DbProviderFactories  
 Každý zprostředkovatel dat rozhraní .NET Framework, který podporuje třídu založenou na výrobě, registruje informace o konfiguraci v části **DbProviderFactories** souboru **machine.config** v místním počítači. Následující fragment konfiguračního souboru zobrazuje syntaxi a formát aplikace <xref:System.Data.SqlClient>.  
  
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
  
 **Invariantní** atribut identifikuje zprostředkovatele podkladových dat. Tato třídílná syntaxe pojmenování se také používá při vytváření nové továrny a pro identifikaci zprostředkovatele v konfiguračním souboru aplikace tak, aby název zprostředkovatele, spolu s jeho přidruženým připojovacím řetězcem, lze načíst za běhu.  
  
## <a name="retrieving-provider-information"></a>Načítání informací o zprostředkovateli  
 Pomocí metody můžete načíst informace o všech zprostředkovatelích <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> dat nainstalovaných v místním počítači. Vrátí <xref:System.Data.DataTable> pojmenovaný **DbProviderFactories,** který obsahuje sloupce popsané v následující tabulce.  
  
|Kolonové číslovky|Název sloupce|Příklad výstupu|Popis|  
|--------------------|-----------------|--------------------|-----------------|  
|0|**Název**|Zprostředkovatel dat sqlclient|Čitelný název pro poskytovatele dat|  
|1|**Popis**|Zprostředkovatel dat rozhraní .NET Framework pro sqlserver|Čitelný popis poskytovatele dat|  
|2|**InvariantName**|System.Data.SqlClient|Název, který lze programově použít k označení poskytovatele dat|  
|3|**Assemblyqualifiedname**|System.Data.SqlClient.SqlClientFactory, System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089|Plně kvalifikovaný název třídy výroby, který obsahuje dostatek informací k vytvoření instance objektu|  
  
 To `DataTable` lze použít k povolení uživatele <xref:System.Data.DataRow> vybrat za běhu. Vybraná `DataRow` možnost může být <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> předána metodě a <xref:System.Data.Common.DbProviderFactory>vytvořit tak silně zadaný soubor . Vybraná <xref:System.Data.DataRow> možnost může `GetFactory` být předána `DbProviderFactory` metodě k vytvoření požadovaného objektu.  
  
## <a name="listing-the-installed-provider-factory-classes"></a>Výpis nainstalovaných výrobních tříd zprostředkovatele  
 Tento příklad ukazuje, jak <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> použít metodu vrátit <xref:System.Data.DataTable> obsahující informace o nainstalovaných zprostředkovatelů. Kód itetuje každý `DataTable`řádek v , zobrazení informací pro každého nainstalovaného zprostředkovatele v okně konzoly.  
  
 [!code-csharp[DataWorks DbProviderFactories#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories/VB/source.vb#1)]  
  
## <a name="using-application-configuration-files-to-store-factory-information"></a>Použití konfiguračních souborů aplikace k ukládání informací z výroby  
 Návrhový vzor používaný pro práci s továrnami zahrnuje ukládání informací o zprostředkovateli a připojovacím řetězci v konfiguračním souboru aplikace, jako je **například application.config** pro aplikaci systému Windows a **web.config** pro ASP.NET aplikaci.  
  
 Následující fragment konfiguračního souboru ukazuje, jak uložit dva pojmenované připojovací řetězce, "NorthwindSQL" pro připojení k databázi Northwind v SQL Server a "NorthwindAccess" pro připojení k databázi Northwind v Access/Jet. Název **invarianty** se používá pro atribut **providerName.**  
  
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
  
### <a name="retrieving-a-connection-string-by-provider-name"></a>Načítání připojovacího řetězce podle názvu zprostředkovatele  
 Chcete-li vytvořit zprostředkovatele továrny, musíte zadat připojovací řetězec, jakož i název zprostředkovatele. Tento příklad ukazuje, jak načíst připojovací řetězec z konfiguračního souboru aplikace předáním názvu zprostředkovatele v invariantním formátu*System.Data.ProviderName*. Kód iterates prostřednictvím <xref:System.Configuration.ConnectionStringSettingsCollection>. Vrací na <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A> úspěch; v `null` `Nothing` jiném jazyce ( v jazyce Visual Basic). Pokud existuje více položek pro zprostředkovatele, první nalezen je vrácena. Další informace a příklady načítání připojovacích řetězců z konfiguračních souborů naleznete [v tématu Connection Strings and Configuration Files](connection-strings-and-configuration-files.md).  
  
> [!NOTE]
> Odkaz na `System.Configuration.dll` je nutné, aby kód spustit.  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/VB/source.vb#1)]  
  
## <a name="creating-the-dbproviderfactory-and-dbconnection"></a>Vytvoření dbProviderFactory a dbconnection  
 Tento příklad ukazuje, jak <xref:System.Data.Common.DbProviderFactory> <xref:System.Data.Common.DbConnection> vytvořit a objekt předáním názvu zprostředkovatele ve formátu*System.Data.ProviderName*" a připojovacího řetězce. Objekt `DbConnection` je vrácena na úspěch; `null` (`Nothing` v jazyce Visual Basic) na jakékoli chybě.  
  
 Kód získá `DbProviderFactory` voláním <xref:System.Data.Common.DbProviderFactories.GetFactory%2A>. Potom <xref:System.Data.Common.DbProviderFactory.CreateConnection%2A> metoda vytvoří <xref:System.Data.Common.DbConnection> objekt <xref:System.Data.Common.DbConnection.ConnectionString%2A> a vlastnost je nastavena na připojovací řetězec.  
  
 [!code-csharp[DataWorks DbProviderFactories.GetFactory#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.GetFactory/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.GetFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.GetFactory/VB/source.vb#1)]  
  
## <a name="see-also"></a>Viz také

- [DbProviderFactories](dbproviderfactories.md)
- [Připojovací řetězce](connection-strings.md)
- [Použití konfiguračních tříd](https://docs.microsoft.com/previous-versions/aspnet/ms228063(v=vs.100))
- [Přehled ADO.NET](ado-net-overview.md)
