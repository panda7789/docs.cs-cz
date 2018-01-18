---
title: "Získání DbProviderFactory"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: a16e4a4d-6a5b-45db-8635-19570e4572ae
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: a018447b790dde047bd76e1319a13aa3f77ffc61
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="obtaining-a-dbproviderfactory"></a><span data-ttu-id="15799-102">Získání DbProviderFactory</span><span class="sxs-lookup"><span data-stu-id="15799-102">Obtaining a DbProviderFactory</span></span>
<span data-ttu-id="15799-103">Proces získání <xref:System.Data.Common.DbProviderFactory> zahrnuje předávání informací o zprostředkovatele dat pro <xref:System.Data.Common.DbProviderFactories> třídy.</span><span class="sxs-lookup"><span data-stu-id="15799-103">The process of obtaining a <xref:System.Data.Common.DbProviderFactory> involves passing information about a data provider to the <xref:System.Data.Common.DbProviderFactories> class.</span></span> <span data-ttu-id="15799-104">Na základě těchto informací <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> metoda vytvoří objekt pro vytváření zprostředkovatele silného typu.</span><span class="sxs-lookup"><span data-stu-id="15799-104">Based on this information, the <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> method creates a strongly typed provider factory.</span></span> <span data-ttu-id="15799-105">Chcete-li například vytvořit <xref:System.Data.SqlClient.SqlClientFactory>, můžete předat `GetFactory` řetězec s název zprostředkovatele, který je určený jako "System.Data.SqlClient".</span><span class="sxs-lookup"><span data-stu-id="15799-105">For example, to create a <xref:System.Data.SqlClient.SqlClientFactory>, you can pass `GetFactory` a string with the provider name specified as "System.Data.SqlClient".</span></span> <span data-ttu-id="15799-106">Další přetížení `GetFactory` trvá <xref:System.Data.DataRow>.</span><span class="sxs-lookup"><span data-stu-id="15799-106">The other overload of `GetFactory` takes a <xref:System.Data.DataRow>.</span></span> <span data-ttu-id="15799-107">Jakmile vytvoříte objekt pro vytváření zprostředkovatelů, pak můžete jeho metody vytvořit další objekty.</span><span class="sxs-lookup"><span data-stu-id="15799-107">Once you create the provider factory, you can then use its methods to create additional objects.</span></span> <span data-ttu-id="15799-108">Některé z metod `SqlClientFactory` zahrnují <xref:System.Data.SqlClient.SqlClientFactory.CreateConnection%2A>, <xref:System.Data.SqlClient.SqlClientFactory.CreateCommand%2A>, a <xref:System.Data.SqlClient.SqlClientFactory.CreateDataAdapter%2A>.</span><span class="sxs-lookup"><span data-stu-id="15799-108">Some of the methods of a `SqlClientFactory` include <xref:System.Data.SqlClient.SqlClientFactory.CreateConnection%2A>, <xref:System.Data.SqlClient.SqlClientFactory.CreateCommand%2A>, and <xref:System.Data.SqlClient.SqlClientFactory.CreateDataAdapter%2A>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="15799-109">Rozhraní .NET Framework <xref:System.Data.OracleClient.OracleClientFactory>, <xref:System.Data.Odbc.OdbcFactory>, a <xref:System.Data.OleDb.OleDbFactory> třídy také poskytuje podobné funkce.</span><span class="sxs-lookup"><span data-stu-id="15799-109">The .NET Framework <xref:System.Data.OracleClient.OracleClientFactory>, <xref:System.Data.Odbc.OdbcFactory>, and <xref:System.Data.OleDb.OleDbFactory> classes also provide similar functionality.</span></span>  
  
## <a name="registering-dbproviderfactories"></a><span data-ttu-id="15799-110">Registrace DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="15799-110">Registering DbProviderFactories</span></span>  
 <span data-ttu-id="15799-111">Každý zprostředkovatel dat .NET Framework, který podporuje třídu na základě objektu pro vytváření registruje informace o konfiguraci v **DbProviderFactories** části **machine.config** souboru v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="15799-111">Each .NET Framework data provider that supports a factory-based class registers configuration information in the **DbProviderFactories** section of the **machine.config** file on the local computer.</span></span> <span data-ttu-id="15799-112">Následující fragment souboru konfigurace ukazuje syntaxi a formát pro <xref:System.Data.SqlClient>.</span><span class="sxs-lookup"><span data-stu-id="15799-112">The following configuration file fragment shows the syntax and format for <xref:System.Data.SqlClient>.</span></span>  
  
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
  
 <span data-ttu-id="15799-113">**Invariantní** atribut určuje výchozí zprostředkovatel data.</span><span class="sxs-lookup"><span data-stu-id="15799-113">The **invariant** attribute identifies the underlying data provider.</span></span> <span data-ttu-id="15799-114">Tuto syntaxi pojmenování třemi částmi se také používá při vytváření nový objekt pro vytváření a k identifikaci zprostředkovatele v konfiguračním souboru aplikace tak, aby název zprostředkovatele, společně s jeho přidružené připojovací řetězec, se dá načíst za běhu.</span><span class="sxs-lookup"><span data-stu-id="15799-114">This three-part naming syntax is also used when creating a new factory and for identifying the provider in an application configuration file so that the provider name, along with its associated connection string, can be retrieved at run time.</span></span>  
  
## <a name="retrieving-provider-information"></a><span data-ttu-id="15799-115">Načítání informací o zprostředkovateli</span><span class="sxs-lookup"><span data-stu-id="15799-115">Retrieving Provider Information</span></span>  
 <span data-ttu-id="15799-116">Můžete načíst informace o všech zprostředkovatelů dat, který je nainstalován v místním počítači pomocí <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="15799-116">You can retrieve information about all of the data providers installed on the local computer by using the <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> method.</span></span> <span data-ttu-id="15799-117">Vrátí <xref:System.Data.DataTable> s názvem **DbProviderFactories** obsahující sloupce, které jsou popsané v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="15799-117">It returns a <xref:System.Data.DataTable> named **DbProviderFactories** that contains the columns described in the following table.</span></span>  
  
|<span data-ttu-id="15799-118">Pořadí sloupce</span><span class="sxs-lookup"><span data-stu-id="15799-118">Column ordinal</span></span>|<span data-ttu-id="15799-119">Název sloupce</span><span class="sxs-lookup"><span data-stu-id="15799-119">Column name</span></span>|<span data-ttu-id="15799-120">Příklad výstupu</span><span class="sxs-lookup"><span data-stu-id="15799-120">Example output</span></span>|<span data-ttu-id="15799-121">Popis</span><span class="sxs-lookup"><span data-stu-id="15799-121">Description</span></span>|  
|--------------------|-----------------|--------------------|-----------------|  
|<span data-ttu-id="15799-122">0</span><span class="sxs-lookup"><span data-stu-id="15799-122">0</span></span>|<span data-ttu-id="15799-123">**Jméno**</span><span class="sxs-lookup"><span data-stu-id="15799-123">**Name**</span></span>|<span data-ttu-id="15799-124">Zprostředkovatel dat SqlClient</span><span class="sxs-lookup"><span data-stu-id="15799-124">SqlClient Data Provider</span></span>|<span data-ttu-id="15799-125">Čitelný název pro poskytovatele dat.</span><span class="sxs-lookup"><span data-stu-id="15799-125">Readable name for the data provider</span></span>|  
|<span data-ttu-id="15799-126">1</span><span class="sxs-lookup"><span data-stu-id="15799-126">1</span></span>|<span data-ttu-id="15799-127">**Popis**</span><span class="sxs-lookup"><span data-stu-id="15799-127">**Description**</span></span>|<span data-ttu-id="15799-128">Zprostředkovatel dat .net framework pro SQL Server</span><span class="sxs-lookup"><span data-stu-id="15799-128">.Net Framework Data Provider for SqlServer</span></span>|<span data-ttu-id="15799-129">Čitelný Popis zprostředkovatele dat</span><span class="sxs-lookup"><span data-stu-id="15799-129">Readable description of the data provider</span></span>|  
|<span data-ttu-id="15799-130">2</span><span class="sxs-lookup"><span data-stu-id="15799-130">2</span></span>|<span data-ttu-id="15799-131">**InvariantName**</span><span class="sxs-lookup"><span data-stu-id="15799-131">**InvariantName**</span></span>|<span data-ttu-id="15799-132">System.Data.SqlClient</span><span class="sxs-lookup"><span data-stu-id="15799-132">System.Data.SqlClient</span></span>|<span data-ttu-id="15799-133">Název, které je možné programově odkazovat na poskytovatele dat.</span><span class="sxs-lookup"><span data-stu-id="15799-133">Name that can be used programmatically to refer to the data provider</span></span>|  
|<span data-ttu-id="15799-134">3</span><span class="sxs-lookup"><span data-stu-id="15799-134">3</span></span>|<span data-ttu-id="15799-135">**AssemblyQualifiedName**</span><span class="sxs-lookup"><span data-stu-id="15799-135">**AssemblyQualifiedName**</span></span>|<span data-ttu-id="15799-136">System.Data.SqlClient.SqlClientFactory, System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089</span><span class="sxs-lookup"><span data-stu-id="15799-136">System.Data.SqlClient.SqlClientFactory, System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089</span></span>|<span data-ttu-id="15799-137">Plně kvalifikovaný název objektu pro vytváření třídy, která obsahuje dostatek informací pro vytvoření instance objektu</span><span class="sxs-lookup"><span data-stu-id="15799-137">Fully qualified name of the factory class, which contains enough information to instantiate the object</span></span>|  
  
 <span data-ttu-id="15799-138">To `DataTable` umožňuje povolit uživateli vybrat <xref:System.Data.DataRow> za běhu.</span><span class="sxs-lookup"><span data-stu-id="15799-138">This `DataTable` can be used to enable a user to select a <xref:System.Data.DataRow> at run time.</span></span> <span data-ttu-id="15799-139">Vybraný `DataRow` může být předána do <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> metodu pro vytvoření silného typu <xref:System.Data.Common.DbProviderFactory>.</span><span class="sxs-lookup"><span data-stu-id="15799-139">The selected `DataRow` can then be passed to the <xref:System.Data.Common.DbProviderFactories.GetFactory%2A> method to create a strongly typed <xref:System.Data.Common.DbProviderFactory>.</span></span> <span data-ttu-id="15799-140">Vybrané <xref:System.Data.DataRow> lze předat `GetFactory` metodu pro vytvoření požadovanou `DbProviderFactory` objektu.</span><span class="sxs-lookup"><span data-stu-id="15799-140">A selected <xref:System.Data.DataRow> can be passed to the `GetFactory` method to create the desired `DbProviderFactory` object.</span></span>  
  
## <a name="listing-the-installed-provider-factory-classes"></a><span data-ttu-id="15799-141">Výpis nainstalovaného zprostředkovatele objekt pro vytváření tříd</span><span class="sxs-lookup"><span data-stu-id="15799-141">Listing the Installed Provider Factory Classes</span></span>  
 <span data-ttu-id="15799-142">Tento příklad ukazuje, jak používat <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> metoda vrátí <xref:System.Data.DataTable> obsahující informace o poskytovateli nainstalované.</span><span class="sxs-lookup"><span data-stu-id="15799-142">This example demonstrates how to use the <xref:System.Data.Common.DbProviderFactories.GetFactoryClasses%2A> method to return a <xref:System.Data.DataTable> containing information about the installed providers.</span></span> <span data-ttu-id="15799-143">Kód iteruje každý řádek `DataTable`, zobrazení informací o pro každého zprostředkovatele nainstalovaná v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="15799-143">The code iterates through each row in the `DataTable`, displaying information for each installed provider in the console window.</span></span>  
  
 [!code-csharp[DataWorks DbProviderFactories#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories/VB/source.vb#1)]  
  
## <a name="using-application-configuration-files-to-store-factory-information"></a><span data-ttu-id="15799-144">Pomocí konfigurační soubory aplikace uložit informace o vytváření</span><span class="sxs-lookup"><span data-stu-id="15799-144">Using Application Configuration Files to Store Factory Information</span></span>  
 <span data-ttu-id="15799-145">Vzor návrhu používané pro práci s objekty Factory ukládání informací o řetězce zprostředkovatele a připojení v konfiguračním souboru aplikace, jako má za následek **app.config** pro aplikace systému Windows a **souboru web.config**  pro aplikaci ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="15799-145">The design pattern used for working with factories entails storing provider and connection string information in an application configuration file, such as **app.config** for a Windows application, and **web.config** for an ASP.NET application.</span></span>  
  
 <span data-ttu-id="15799-146">Následující fragment souboru konfigurace ukazuje, jak uložit dva řetězce připojení s názvem "NorthwindSQL" pro připojení k databázi Northwind v systému SQL Server a "NorthwindAccess" pro připojení k databázi Northwind přístup/Jet.</span><span class="sxs-lookup"><span data-stu-id="15799-146">The following configuration file fragment demonstrates how to save two named connection strings, "NorthwindSQL" for a connection to the Northwind database in SQL Server, and "NorthwindAccess" for a connection to the Northwind database in Access/Jet.</span></span> <span data-ttu-id="15799-147">**Invariantní** název se používá pro **providerName** atribut.</span><span class="sxs-lookup"><span data-stu-id="15799-147">The **invariant** name is used for the **providerName** attribute.</span></span>  
  
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
  
### <a name="retrieving-a-connection-string-by-provider-name"></a><span data-ttu-id="15799-148">Načítání podle názvu zprostředkovatele připojovací řetězec</span><span class="sxs-lookup"><span data-stu-id="15799-148">Retrieving a Connection String by Provider Name</span></span>  
 <span data-ttu-id="15799-149">Chcete-li vytvořit objekt pro vytváření zprostředkovatele, je třeba zadat připojovací řetězec, jakož i název zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="15799-149">In order to create a provider factory, you must supply a connection string as well as the provider name.</span></span> <span data-ttu-id="15799-150">Tento příklad ukazuje, jak k získání připojovacího řetězce z konfiguračního souboru aplikace předáním název zprostředkovatele v neutrálním formátu "*System.Data.ProviderName*".</span><span class="sxs-lookup"><span data-stu-id="15799-150">This example demonstrates how to retrieve a connection string from an application configuration file by passing the provider name in the invariant format "*System.Data.ProviderName*".</span></span> <span data-ttu-id="15799-151">Kód iteruje <xref:System.Configuration.ConnectionStringSettingsCollection>.</span><span class="sxs-lookup"><span data-stu-id="15799-151">The code iterates through the <xref:System.Configuration.ConnectionStringSettingsCollection>.</span></span> <span data-ttu-id="15799-152">Vrátí <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A> v případě úspěchu; v opačném případě `null` (`Nothing` v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="15799-152">It returns the <xref:System.Configuration.ConnectionStringSettings.ProviderName%2A> on success; otherwise `null` (`Nothing` in Visual Basic).</span></span> <span data-ttu-id="15799-153">Pokud existuje více položek pro zprostředkovatele, je vrácen první z nich najít.</span><span class="sxs-lookup"><span data-stu-id="15799-153">If there are multiple entries for a provider, the first one found is returned.</span></span> <span data-ttu-id="15799-154">Další informace a příklady načítání připojovací řetězce z konfiguračních souborů najdete v tématu [připojovací řetězce a konfigurační soubory](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).</span><span class="sxs-lookup"><span data-stu-id="15799-154">For more information and examples of retrieving connection strings from configuration files, see [Connection Strings and Configuration Files](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="15799-155">Odkaz na `System.Configuration.dll` je nutná pro kód pro spuštění.</span><span class="sxs-lookup"><span data-stu-id="15799-155">A reference to `System.Configuration.dll` is required in order for the code to run.</span></span>  
  
 [!code-csharp[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/CS/source.cs#1)]
 [!code-vb[DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks ConnectionStringSettings.RetrieveFromConfigByProvider/VB/source.vb#1)]  
  
## <a name="creating-the-dbproviderfactory-and-dbconnection"></a><span data-ttu-id="15799-156">Vytváření DbProviderFactory a DbConnection</span><span class="sxs-lookup"><span data-stu-id="15799-156">Creating the DbProviderFactory and DbConnection</span></span>  
 <span data-ttu-id="15799-157">Tento příklad ukazuje, jak vytvořit <xref:System.Data.Common.DbProviderFactory> a <xref:System.Data.Common.DbConnection> objekt pomocí předání název zprostředkovatele ve formátu "*System.Data.ProviderName*" a připojovací řetězec.</span><span class="sxs-lookup"><span data-stu-id="15799-157">This example demonstrates how to create a <xref:System.Data.Common.DbProviderFactory> and <xref:System.Data.Common.DbConnection> object by passing it the provider name in the format "*System.Data.ProviderName*" and a connection string.</span></span> <span data-ttu-id="15799-158">A `DbConnection` objektu se vrátí v případě úspěchu; `null` (`Nothing` v jazyce Visual Basic) na všechny chyby.</span><span class="sxs-lookup"><span data-stu-id="15799-158">A `DbConnection` object is returned on success; `null` (`Nothing` in Visual Basic) on any error.</span></span>  
  
 <span data-ttu-id="15799-159">Získá kód `DbProviderFactory` voláním <xref:System.Data.Common.DbProviderFactories.GetFactory%2A>.</span><span class="sxs-lookup"><span data-stu-id="15799-159">The code obtains the `DbProviderFactory` by calling <xref:System.Data.Common.DbProviderFactories.GetFactory%2A>.</span></span> <span data-ttu-id="15799-160">Pak se <xref:System.Data.Common.DbProviderFactory.CreateConnection%2A> metoda vytvoří <xref:System.Data.Common.DbConnection> objektu a <xref:System.Data.Common.DbConnection.ConnectionString%2A> je nastavena na připojovací řetězec.</span><span class="sxs-lookup"><span data-stu-id="15799-160">Then the <xref:System.Data.Common.DbProviderFactory.CreateConnection%2A> method creates the <xref:System.Data.Common.DbConnection> object and the <xref:System.Data.Common.DbConnection.ConnectionString%2A> property is set to the connection string.</span></span>  
  
 [!code-csharp[DataWorks DbProviderFactories.GetFactory#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.GetFactory/CS/source.cs#1)]
 [!code-vb[DataWorks DbProviderFactories.GetFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks DbProviderFactories.GetFactory/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="15799-161">Viz také</span><span class="sxs-lookup"><span data-stu-id="15799-161">See Also</span></span>  
 [<span data-ttu-id="15799-162">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="15799-162">DbProviderFactories</span></span>](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 [<span data-ttu-id="15799-163">Připojovací řetězce</span><span class="sxs-lookup"><span data-stu-id="15799-163">Connection Strings</span></span>](../../../../docs/framework/data/adonet/connection-strings.md)  
 [<span data-ttu-id="15799-164">Pomocí třídy konfigurace</span><span class="sxs-lookup"><span data-stu-id="15799-164">Using the Configuration Classes</span></span>](http://msdn.microsoft.com/library/98d2b386-baf6-4a17-974b-76e3b4c87acc)  
 [<span data-ttu-id="15799-165">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="15799-165">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
