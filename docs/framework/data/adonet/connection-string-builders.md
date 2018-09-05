---
title: Tvůrci připojovacích řetězců
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8434b608-c4d3-43d3-8ae3-6d8c6b726759
ms.openlocfilehash: 1c65b0c2c9ae19aa008ecd8fb453d8e41b7c4167
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43737500"
---
# <a name="connection-string-builders"></a><span data-ttu-id="7c0f4-102">Tvůrci připojovacích řetězců</span><span class="sxs-lookup"><span data-stu-id="7c0f4-102">Connection String Builders</span></span>
<span data-ttu-id="7c0f4-103">V dřívějších verzích [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)], kompilace kontrola připojovacích řetězců s spojený řetězec hodnoty nedošlo, tak, aby v době běhu, vygeneruje nesprávná klíčové slovo <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="7c0f4-103">In earlier versions of [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)], compile-time checking of connection strings with concatenated string values did not occur, so that at run time, an incorrect keyword generated an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="7c0f4-104">Každá z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatelé dat nepodporuje jinou syntaxi pro klíčová slova řetězec připojení, které vytváření obtížné platný připojovací řetězce, je-li provést ručně.</span><span class="sxs-lookup"><span data-stu-id="7c0f4-104">Each of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] data providers supported different syntax for connection string keywords, which made constructing valid connection strings difficult if done manually.</span></span> <span data-ttu-id="7c0f4-105">Chcete-li vyřešit tento problém [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 2.0 zavedeny nové tvůrci připojovacích řetězců pro každou [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] poskytovatele dat služeb.</span><span class="sxs-lookup"><span data-stu-id="7c0f4-105">To address this problem, [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 2.0 introduced new connection string builders for each [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] data provider.</span></span> <span data-ttu-id="7c0f4-106">Každý poskytovatel dat zahrnuje třídu Tvůrce řetězec silného typu připojení, která dědí z <xref:System.Data.Common.DbConnectionStringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="7c0f4-106">Each data provider includes a strongly typed connection string builder class that inherits from <xref:System.Data.Common.DbConnectionStringBuilder>.</span></span> <span data-ttu-id="7c0f4-107">Následující tabulce jsou uvedeny [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] poskytovatelé dat a jejich přidružený připojovací řetězec Tvůrce třídy.</span><span class="sxs-lookup"><span data-stu-id="7c0f4-107">The following table lists the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] data providers and their associated connection string builder classes.</span></span>  
  
|<span data-ttu-id="7c0f4-108">Zprostředkovatel</span><span class="sxs-lookup"><span data-stu-id="7c0f4-108">Provider</span></span>|<span data-ttu-id="7c0f4-109">Třída ConnectionStringBuilder</span><span class="sxs-lookup"><span data-stu-id="7c0f4-109">ConnectionStringBuilder class</span></span>|  
|--------------|-----------------------------------|  
|<xref:System.Data.SqlClient>|<xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OleDb>|<xref:System.Data.OleDb.OleDbConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.Odbc>|<xref:System.Data.Odbc.OdbcConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OracleClient>|<xref:System.Data.OracleClient.OracleConnectionStringBuilder?displayProperty=nameWithType>|  
  
## <a name="connection-string-injection-attacks"></a><span data-ttu-id="7c0f4-110">Útoky prostřednictvím injektáže připojovací řetězec</span><span class="sxs-lookup"><span data-stu-id="7c0f4-110">Connection String Injection Attacks</span></span>  
 <span data-ttu-id="7c0f4-111">Útok prostřednictvím injektáže řetězec připojení může dojít, když dynamická zřetězení sloužící k vytvoření připojovací řetězce, které jsou založeny na vstup uživatele.</span><span class="sxs-lookup"><span data-stu-id="7c0f4-111">A connection string injection attack can occur when dynamic string concatenation is used to build connection strings that are based on user input.</span></span> <span data-ttu-id="7c0f4-112">Pokud řetězec není ověřená a škodlivý text nebo znaky nejsou uvozeny řídicími znaky, útočník můžou mít přístup k citlivým datům nebo další prostředky na serveru.</span><span class="sxs-lookup"><span data-stu-id="7c0f4-112">If the string is not validated and malicious text or characters not escaped, an attacker can potentially access sensitive data or other resources on the server.</span></span> <span data-ttu-id="7c0f4-113">Útočník může například připojte útoku zadáním středník a přidávání další hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7c0f4-113">For example, an attacker could mount an attack by supplying a semicolon and appending an additional value.</span></span> <span data-ttu-id="7c0f4-114">Připojovací řetězec je analyzován pomocí algoritmu "posledním místě wins" a nebezpečný vstup je nahrazen legitimní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7c0f4-114">The connection string is parsed by using a "last one wins" algorithm, and the hostile input is substituted for a legitimate value.</span></span>  
  
 <span data-ttu-id="7c0f4-115">Třídy tvůrce řetězec připojení jsou navrženy tak, aby obsahoval jenom izolovat a chránit proti chyby syntaxe a ohrožení zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7c0f4-115">The connection string builder classes are designed to eliminate guesswork and protect against syntax errors and security vulnerabilities.</span></span> <span data-ttu-id="7c0f4-116">Poskytuje metody a vlastnosti odpovídající dvojice klíč/hodnota známé od každého poskytovatele dat.</span><span class="sxs-lookup"><span data-stu-id="7c0f4-116">They provide methods and properties corresponding to the known key/value pairs permitted by each data provider.</span></span> <span data-ttu-id="7c0f4-117">Každá třída udržuje pevné kolekce synonym a může překládat z synonymum pro odpovídající dobře známý název klíče.</span><span class="sxs-lookup"><span data-stu-id="7c0f4-117">Each class maintains a fixed collection of synonyms and can translate from a synonym to the corresponding well-known key name.</span></span> <span data-ttu-id="7c0f4-118">Kontroly jsou prováděny pro páry klíč/hodnota platný a vyvolá výjimku, neplatný pár.</span><span class="sxs-lookup"><span data-stu-id="7c0f4-118">Checks are performed for valid key/value pairs and an invalid pair throws an exception.</span></span> <span data-ttu-id="7c0f4-119">Kromě toho jsou zpracovány vloženého hodnoty bezpečným způsobem.</span><span class="sxs-lookup"><span data-stu-id="7c0f4-119">In addition, injected values are handled in a safe manner.</span></span>  
  
 <span data-ttu-id="7c0f4-120">Následující příklad ukazuje, jak <xref:System.Data.SqlClient.SqlConnectionStringBuilder> zpracovává vložený hodnotu navíc pro `Initial Catalog` nastavení.</span><span class="sxs-lookup"><span data-stu-id="7c0f4-120">The following example demonstrates how the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> handles an inserted extra value for the `Initial Catalog` setting.</span></span>  
  
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
  
 <span data-ttu-id="7c0f4-121">Výstup ukazuje, že <xref:System.Data.SqlClient.SqlConnectionStringBuilder> to správně zpracovat uvozovací znaky navíc hodnotu do dvojitých uvozovek místo připojování na připojovací řetězec jako nové dvojice klíč/hodnota.</span><span class="sxs-lookup"><span data-stu-id="7c0f4-121">The output shows that the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> handled this correctly by escaping the extra value in double quotation marks instead of appending it to the connection string as a new key/value pair.</span></span>  
  
```  
data source=(local);Integrated Security=True;  
initial catalog="AdventureWorks;NewValue=Bad"  
```  
  
## <a name="building-connection-strings-from-configuration-files"></a><span data-ttu-id="7c0f4-122">Vytváření připojovacích řetězců z konfiguračních souborů</span><span class="sxs-lookup"><span data-stu-id="7c0f4-122">Building Connection Strings from Configuration Files</span></span>  
 <span data-ttu-id="7c0f4-123">Pokud některé prvky připojovacího řetězce je znám předem, můžou být uložené v konfiguračním souboru a načíst za běhu a sestavit úplný připojovací řetězec.</span><span class="sxs-lookup"><span data-stu-id="7c0f4-123">If certain elements of a connection string are known beforehand, they can be stored in a configuration file and retrieved at run time to construct a complete connection string.</span></span> <span data-ttu-id="7c0f4-124">Název databáze může být například předem známé, ale ne názvu serveru.</span><span class="sxs-lookup"><span data-stu-id="7c0f4-124">For example, the name of the database might be known in advance, but not the name of the server.</span></span> <span data-ttu-id="7c0f4-125">Nebo může být vhodné uživatele k zadání jména a hesla v době běhu aniž by bylo možné vložit další hodnoty do připojovacího řetězce.</span><span class="sxs-lookup"><span data-stu-id="7c0f4-125">Or you might want a user to supply a name and password at run time without being able to inject other values into the connection string.</span></span>  
  
 <span data-ttu-id="7c0f4-126">Přijímá jednu z přetížených konstruktorů pro Tvůrce připojovacích řetězců <xref:System.String> jako argument, což vám umožní zadat částečné připojovací řetězec, který lze pak provést ze vstupu uživatele.</span><span class="sxs-lookup"><span data-stu-id="7c0f4-126">One of the overloaded constructors for a connection string builder takes a <xref:System.String> as an argument, which enables you to supply a partial connection string that can then be completed from user input.</span></span> <span data-ttu-id="7c0f4-127">Částečné připojovací řetězec můžete uložené v konfiguračním souboru a načíst za běhu.</span><span class="sxs-lookup"><span data-stu-id="7c0f4-127">The partial connection string can be stored in a configuration file and retrieved at run time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7c0f4-128"><xref:System.Configuration> Obor názvů umožňuje programový přístup ke konfiguračním souborům, které používají <xref:System.Web.Configuration.WebConfigurationManager> pro webové aplikace a <xref:System.Configuration.ConfigurationManager> pro aplikace Windows.</span><span class="sxs-lookup"><span data-stu-id="7c0f4-128">The <xref:System.Configuration> namespace allows programmatic access to configuration files that use the <xref:System.Web.Configuration.WebConfigurationManager> for Web applications and the <xref:System.Configuration.ConfigurationManager> for Windows applications.</span></span> <span data-ttu-id="7c0f4-129">Další informace o práci s připojovací řetězce a konfigurační soubory, naleznete v tématu [připojovací řetězce a konfigurační soubory](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).</span><span class="sxs-lookup"><span data-stu-id="7c0f4-129">For more information about working with connection strings and configuration files, see [Connection Strings and Configuration Files](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).</span></span>  
  
### <a name="example"></a><span data-ttu-id="7c0f4-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="7c0f4-130">Example</span></span>  
 <span data-ttu-id="7c0f4-131">Tento příklad ukazuje načítání částečné připojovacího řetězce z konfiguračního souboru a jeho dokončení nastavením <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A>, <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserID%2A>, a <xref:System.Data.SqlClient.SqlConnectionStringBuilder.Password%2A> vlastnosti <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="7c0f4-131">This example demonstrates retrieving a partial connection string from a configuration file and completing it by setting the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A>, <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserID%2A>, and <xref:System.Data.SqlClient.SqlConnectionStringBuilder.Password%2A> properties of the <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span></span> <span data-ttu-id="7c0f4-132">Konfigurační soubor je definovaná následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="7c0f4-132">The configuration file is defined as follows.</span></span>  
  
```xml  
<connectionStrings>  
  <clear/>  
  <add name="partialConnectString"   
    connectionString="Initial Catalog=Northwind;"  
    providerName="System.Data.SqlClient" />  
</connectionStrings>  
```  
  
> [!NOTE]
>  <span data-ttu-id="7c0f4-133">Je nutné nastavit odkaz na `System.Configuration.dll` ve vašem projektu pro spuštění kódu.</span><span class="sxs-lookup"><span data-stu-id="7c0f4-133">You must set a reference to the `System.Configuration.dll` in your project for the code to run.</span></span>  
  
 [!code-csharp[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/CS/source.cs#1)]
 [!code-vb[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="7c0f4-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="7c0f4-134">See Also</span></span>  
 [<span data-ttu-id="7c0f4-135">Připojovací řetězce</span><span class="sxs-lookup"><span data-stu-id="7c0f4-135">Connection Strings</span></span>](../../../../docs/framework/data/adonet/connection-strings.md)  
 [<span data-ttu-id="7c0f4-136">Ochrana osobních údajů a zabezpečení dat</span><span class="sxs-lookup"><span data-stu-id="7c0f4-136">Privacy and Data Security</span></span>](../../../../docs/framework/data/adonet/privacy-and-data-security.md)  
 [<span data-ttu-id="7c0f4-137">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="7c0f4-137">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
