---
title: Tvůrci připojovacích řetězců
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8434b608-c4d3-43d3-8ae3-6d8c6b726759
ms.openlocfilehash: 8cadeac0bcbf301f7d973e93435885de82052603
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151660"
---
# <a name="connection-string-builders"></a><span data-ttu-id="40bf5-102">Tvůrci připojovacích řetězců</span><span class="sxs-lookup"><span data-stu-id="40bf5-102">Connection String Builders</span></span>
<span data-ttu-id="40bf5-103">V dřívějších verzích ADO.NET nedocházelo ke kontrole připojovacích řetězců s hodnotami zřetězených řetězců, <xref:System.ArgumentException>takže za běhu vygenerovalo nesprávné klíčové slovo .</span><span class="sxs-lookup"><span data-stu-id="40bf5-103">In earlier versions of ADO.NET, compile-time checking of connection strings with concatenated string values did not occur, so that at run time, an incorrect keyword generated an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="40bf5-104">Každý z poskytovatelů dat rozhraní .NET Framework podporoval jinou syntaxi pro klíčová slova připojovacího řetězce, což ztížilo vytváření platných připojovacích řetězců, pokud se provádí ručně.</span><span class="sxs-lookup"><span data-stu-id="40bf5-104">Each of the .NET Framework data providers supported different syntax for connection string keywords, which made constructing valid connection strings difficult if done manually.</span></span> <span data-ttu-id="40bf5-105">K vyřešení tohoto problému ADO.NET 2.0 zavedla nové tvůrce připojovacího řetězce pro každého zprostředkovatele dat rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="40bf5-105">To address this problem, ADO.NET 2.0 introduced new connection string builders for each .NET Framework data provider.</span></span> <span data-ttu-id="40bf5-106">Každý zprostředkovatel dat obsahuje třídu tvůrce připojovacího řetězce silného typu, která dědí z <xref:System.Data.Common.DbConnectionStringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="40bf5-106">Each data provider includes a strongly typed connection string builder class that inherits from <xref:System.Data.Common.DbConnectionStringBuilder>.</span></span> <span data-ttu-id="40bf5-107">V následující tabulce jsou uvedeny zprostředkovatele dat rozhraní .NET Framework a jejich přidružené třídy tvůrce připojovacího řetězce.</span><span class="sxs-lookup"><span data-stu-id="40bf5-107">The following table lists the .NET Framework data providers and their associated connection string builder classes.</span></span>  
  
|<span data-ttu-id="40bf5-108">Poskytovatel</span><span class="sxs-lookup"><span data-stu-id="40bf5-108">Provider</span></span>|<span data-ttu-id="40bf5-109">Třída ConnectionStringBuilder</span><span class="sxs-lookup"><span data-stu-id="40bf5-109">ConnectionStringBuilder class</span></span>|  
|--------------|-----------------------------------|  
|<xref:System.Data.SqlClient>|<xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OleDb>|<xref:System.Data.OleDb.OleDbConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.Odbc>|<xref:System.Data.Odbc.OdbcConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OracleClient>|<xref:System.Data.OracleClient.OracleConnectionStringBuilder?displayProperty=nameWithType>|  
  
## <a name="connection-string-injection-attacks"></a><span data-ttu-id="40bf5-110">Útoky injektáží řetězce připojení</span><span class="sxs-lookup"><span data-stu-id="40bf5-110">Connection String Injection Attacks</span></span>  
 <span data-ttu-id="40bf5-111">K útoku injektáží připojovacího řetězce může dojít při zřetězení dynamického řetězce k vytvoření připojovacích řetězců, které jsou založeny na vstupu uživatele.</span><span class="sxs-lookup"><span data-stu-id="40bf5-111">A connection string injection attack can occur when dynamic string concatenation is used to build connection strings that are based on user input.</span></span> <span data-ttu-id="40bf5-112">Pokud řetězec není ověřen a škodlivý text nebo znaky nejsou uvozeny, útočník může potenciálně přistupovat k citlivým datům nebo jiným prostředkům na serveru.</span><span class="sxs-lookup"><span data-stu-id="40bf5-112">If the string is not validated and malicious text or characters not escaped, an attacker can potentially access sensitive data or other resources on the server.</span></span> <span data-ttu-id="40bf5-113">Útočník by například mohl připojit útok poskytnutím středníku a připojením další hodnoty.</span><span class="sxs-lookup"><span data-stu-id="40bf5-113">For example, an attacker could mount an attack by supplying a semicolon and appending an additional value.</span></span> <span data-ttu-id="40bf5-114">Připojovací řetězec je analyzován pomocí algoritmu "poslední vyhrává" a nepřátelský vstup je nahrazen legitimní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="40bf5-114">The connection string is parsed by using a "last one wins" algorithm, and the hostile input is substituted for a legitimate value.</span></span>  
  
 <span data-ttu-id="40bf5-115">Třídy tvůrce připojovacího řetězce jsou navrženy tak, aby eliminovaly dohady a chránily před chybami syntaxe a chybami zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="40bf5-115">The connection string builder classes are designed to eliminate guesswork and protect against syntax errors and security vulnerabilities.</span></span> <span data-ttu-id="40bf5-116">Poskytují metody a vlastnosti odpovídající známé dvojice klíč/hodnota povolené jednotlivými zprostředkovateli dat.</span><span class="sxs-lookup"><span data-stu-id="40bf5-116">They provide methods and properties corresponding to the known key/value pairs permitted by each data provider.</span></span> <span data-ttu-id="40bf5-117">Každá třída udržuje pevnou kolekci synonym a lze přeložit ze synonyma na odpovídající známý název klíče.</span><span class="sxs-lookup"><span data-stu-id="40bf5-117">Each class maintains a fixed collection of synonyms and can translate from a synonym to the corresponding well-known key name.</span></span> <span data-ttu-id="40bf5-118">Kontroly jsou prováděny pro platné dvojice klíč/hodnota a neplatný pár vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="40bf5-118">Checks are performed for valid key/value pairs and an invalid pair throws an exception.</span></span> <span data-ttu-id="40bf5-119">Kromě toho jsou vstřikované hodnoty zpracovány bezpečným způsobem.</span><span class="sxs-lookup"><span data-stu-id="40bf5-119">In addition, injected values are handled in a safe manner.</span></span>  
  
 <span data-ttu-id="40bf5-120">Následující příklad ukazuje, <xref:System.Data.SqlClient.SqlConnectionStringBuilder> jak zpracovává vložené extra `Initial Catalog` hodnotu pro nastavení.</span><span class="sxs-lookup"><span data-stu-id="40bf5-120">The following example demonstrates how the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> handles an inserted extra value for the `Initial Catalog` setting.</span></span>  
  
```vb  
Dim builder As New System.Data.SqlClient.SqlConnectionStringBuilder  
builder("Data Source") = "(local)"  
builder("Integrated Security") = True  
builder("Initial Catalog") = "AdventureWorks;NewValue=Bad"  
Console.WriteLine(builder.ConnectionString)  
```  
  
```csharp  
System.Data.SqlClient.SqlConnectionStringBuilder builder =  
  new System.Data.SqlClient.SqlConnectionStringBuilder();  
builder["Data Source"] = "(local)";  
builder["integrated Security"] = true;  
builder["Initial Catalog"] = "AdventureWorks;NewValue=Bad";  
Console.WriteLine(builder.ConnectionString);  
```  
  
 <span data-ttu-id="40bf5-121">Výstup ukazuje, <xref:System.Data.SqlClient.SqlConnectionStringBuilder> že zpracovány správně uvozením extra hodnotu v uvozovkách namísto připojení k připojovacířetězec jako nový klíč/hodnota dvojice.</span><span class="sxs-lookup"><span data-stu-id="40bf5-121">The output shows that the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> handled this correctly by escaping the extra value in double quotation marks instead of appending it to the connection string as a new key/value pair.</span></span>  
  
```output  
data source=(local);Integrated Security=True;  
initial catalog="AdventureWorks;NewValue=Bad"  
```  
  
## <a name="building-connection-strings-from-configuration-files"></a><span data-ttu-id="40bf5-122">Vytváření připojovacích řetězců z konfiguračních souborů</span><span class="sxs-lookup"><span data-stu-id="40bf5-122">Building Connection Strings from Configuration Files</span></span>  
 <span data-ttu-id="40bf5-123">Pokud jsou předem známy určité prvky připojovacího řetězce, mohou být uloženy v konfiguračním souboru a načteny za běhu, aby se vytvořil úplný připojovací řetězec.</span><span class="sxs-lookup"><span data-stu-id="40bf5-123">If certain elements of a connection string are known beforehand, they can be stored in a configuration file and retrieved at run time to construct a complete connection string.</span></span> <span data-ttu-id="40bf5-124">Například název databáze může být znám předem, ale ne název serveru.</span><span class="sxs-lookup"><span data-stu-id="40bf5-124">For example, the name of the database might be known in advance, but not the name of the server.</span></span> <span data-ttu-id="40bf5-125">Nebo můžete chtít, aby uživatel zadat jméno a heslo za běhu, aniž by bylo možné vložit další hodnoty do připojovacího řetězce.</span><span class="sxs-lookup"><span data-stu-id="40bf5-125">Or you might want a user to supply a name and password at run time without being able to inject other values into the connection string.</span></span>  
  
 <span data-ttu-id="40bf5-126">Jeden z přetížených konstruktorů pro tvůrce <xref:System.String> připojovacího řetězce přebírá jako argument, který umožňuje zadat částečný připojovací řetězec, který pak lze dokončit ze vstupu uživatele.</span><span class="sxs-lookup"><span data-stu-id="40bf5-126">One of the overloaded constructors for a connection string builder takes a <xref:System.String> as an argument, which enables you to supply a partial connection string that can then be completed from user input.</span></span> <span data-ttu-id="40bf5-127">Částečný připojovací řetězec lze uložit do konfiguračního souboru a načíst za běhu.</span><span class="sxs-lookup"><span data-stu-id="40bf5-127">The partial connection string can be stored in a configuration file and retrieved at run time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="40bf5-128">Obor <xref:System.Configuration> názvů umožňuje programový přístup ke <xref:System.Web.Configuration.WebConfigurationManager> konfiguračním <xref:System.Configuration.ConfigurationManager> souborům, které používají pro webové aplikace a aplikace systému Windows.</span><span class="sxs-lookup"><span data-stu-id="40bf5-128">The <xref:System.Configuration> namespace allows programmatic access to configuration files that use the <xref:System.Web.Configuration.WebConfigurationManager> for Web applications and the <xref:System.Configuration.ConfigurationManager> for Windows applications.</span></span> <span data-ttu-id="40bf5-129">Další informace o práci s připojovacími řetězci a konfiguračními soubory naleznete [v tématu Connection Strings and Configuration Files](connection-strings-and-configuration-files.md).</span><span class="sxs-lookup"><span data-stu-id="40bf5-129">For more information about working with connection strings and configuration files, see [Connection Strings and Configuration Files](connection-strings-and-configuration-files.md).</span></span>  
  
### <a name="example"></a><span data-ttu-id="40bf5-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="40bf5-130">Example</span></span>  
 <span data-ttu-id="40bf5-131">Tento příklad ukazuje načtení částečného připojovacího řetězce <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A>z <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserID%2A>konfiguračního souboru a jeho dokončení nastavením vlastností <xref:System.Data.SqlClient.SqlConnectionStringBuilder.Password%2A> <xref:System.Data.SqlClient.SqlConnectionStringBuilder>, a .</span><span class="sxs-lookup"><span data-stu-id="40bf5-131">This example demonstrates retrieving a partial connection string from a configuration file and completing it by setting the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A>, <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserID%2A>, and <xref:System.Data.SqlClient.SqlConnectionStringBuilder.Password%2A> properties of the <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span></span> <span data-ttu-id="40bf5-132">Konfigurační soubor je definován následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="40bf5-132">The configuration file is defined as follows.</span></span>  
  
```xml  
<connectionStrings>  
  <clear/>  
  <add name="partialConnectString"
    connectionString="Initial Catalog=Northwind;"  
    providerName="System.Data.SqlClient" />  
</connectionStrings>  
```  
  
> [!NOTE]
> <span data-ttu-id="40bf5-133">Je nutné nastavit odkaz `System.Configuration.dll` na v projektu pro spuštění kódu.</span><span class="sxs-lookup"><span data-stu-id="40bf5-133">You must set a reference to the `System.Configuration.dll` in your project for the code to run.</span></span>  
  
 [!code-csharp[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/CS/source.cs#1)]
 [!code-vb[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="40bf5-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="40bf5-134">See also</span></span>

- [<span data-ttu-id="40bf5-135">Připojovací řetězce</span><span class="sxs-lookup"><span data-stu-id="40bf5-135">Connection Strings</span></span>](connection-strings.md)
- [<span data-ttu-id="40bf5-136">Ochrana osobních údajů a zabezpečení dat</span><span class="sxs-lookup"><span data-stu-id="40bf5-136">Privacy and Data Security</span></span>](privacy-and-data-security.md)
- [<span data-ttu-id="40bf5-137">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="40bf5-137">ADO.NET Overview</span></span>](ado-net-overview.md)
