---
title: "Tvůrci řetězců pro připojení"
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
ms.assetid: 8434b608-c4d3-43d3-8ae3-6d8c6b726759
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: a782969502509cb766e3a1d38222118a352dc3db
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="connection-string-builders"></a><span data-ttu-id="c561c-102">Tvůrci řetězců pro připojení</span><span class="sxs-lookup"><span data-stu-id="c561c-102">Connection String Builders</span></span>
<span data-ttu-id="c561c-103">V dřívějších verzích [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)], kompilace kontrola připojovací řetězce s spojený řetězec hodnoty se neuskutečnilo, tak, aby v době běhu nesprávné – klíčové slovo generované <xref:System.ArgumentException>.</span><span class="sxs-lookup"><span data-stu-id="c561c-103">In earlier versions of [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)], compile-time checking of connection strings with concatenated string values did not occur, so that at run time, an incorrect keyword generated an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="c561c-104">Každý z [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatelé dat podporována jinou syntaxi pro klíčová slova řetězec připojení, kterým vytváření obtížné platný připojovací řetězce, je-li provést ručně.</span><span class="sxs-lookup"><span data-stu-id="c561c-104">Each of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] data providers supported different syntax for connection string keywords, which made constructing valid connection strings difficult if done manually.</span></span> <span data-ttu-id="c561c-105">Chcete-li vyřešit tento problém [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 2.0 zavedl nový Tvůrci řetězců pro připojení pro každou [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dat zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="c561c-105">To address this problem, [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 2.0 introduced new connection string builders for each [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] data provider.</span></span> <span data-ttu-id="c561c-106">Každý poskytovatel dat zahrnuje třídy tvůrce řetězec silného typu připojení, která dědí z <xref:System.Data.Common.DbConnectionStringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="c561c-106">Each data provider includes a strongly typed connection string builder class that inherits from <xref:System.Data.Common.DbConnectionStringBuilder>.</span></span> <span data-ttu-id="c561c-107">Následující tabulka uvádí [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zprostředkovatelé dat a jejich přidružené připojení řetězec Tvůrce třídy.</span><span class="sxs-lookup"><span data-stu-id="c561c-107">The following table lists the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] data providers and their associated connection string builder classes.</span></span>  
  
|<span data-ttu-id="c561c-108">Zprostředkovatel</span><span class="sxs-lookup"><span data-stu-id="c561c-108">Provider</span></span>|<span data-ttu-id="c561c-109">ConnectionStringBuilder – třída</span><span class="sxs-lookup"><span data-stu-id="c561c-109">ConnectionStringBuilder class</span></span>|  
|--------------|-----------------------------------|  
|<xref:System.Data.SqlClient>|<xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OleDb>|<xref:System.Data.OleDb.OleDbConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.Odbc>|<xref:System.Data.Odbc.OdbcConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OracleClient>|<xref:System.Data.OracleClient.OracleConnectionStringBuilder?displayProperty=nameWithType>|  
  
## <a name="connection-string-injection-attacks"></a><span data-ttu-id="c561c-110">Prostřednictvím injektáže řetězec připojení</span><span class="sxs-lookup"><span data-stu-id="c561c-110">Connection String Injection Attacks</span></span>  
 <span data-ttu-id="c561c-111">Útok prostřednictvím injektáže řetězec připojení může dojít, když dynamické zřetězení slouží k vytvoření připojovací řetězce, které jsou založeny na vstup uživatele.</span><span class="sxs-lookup"><span data-stu-id="c561c-111">A connection string injection attack can occur when dynamic string concatenation is used to build connection strings that are based on user input.</span></span> <span data-ttu-id="c561c-112">Pokud řetězec není ověřená a škodlivý text nebo znaky není řídicí sekvencí, útočník mají přístup k citlivým datům nebo jiným prostředkům na serveru.</span><span class="sxs-lookup"><span data-stu-id="c561c-112">If the string is not validated and malicious text or characters not escaped, an attacker can potentially access sensitive data or other resources on the server.</span></span> <span data-ttu-id="c561c-113">Například útočník může připojit útoku zadávání středník a připojením algoritmu další hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c561c-113">For example, an attacker could mount an attack by supplying a semicolon and appending an additional value.</span></span> <span data-ttu-id="c561c-114">Připojovací řetězec je analyzován pomocí algoritmu "poslední jeden wins" a je nahrazena nepřátelských vstup pro hodnotu legitimní.</span><span class="sxs-lookup"><span data-stu-id="c561c-114">The connection string is parsed by using a "last one wins" algorithm, and the hostile input is substituted for a legitimate value.</span></span>  
  
 <span data-ttu-id="c561c-115">Připojovací řetězec Tvůrce třídy jsou navrženy pro vyloučení již nebudete muset odhadovat a chránit proti chyby syntaxe a ohrožení zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="c561c-115">The connection string builder classes are designed to eliminate guesswork and protect against syntax errors and security vulnerabilities.</span></span> <span data-ttu-id="c561c-116">Poskytuje metody a vlastnosti odpovídající páry známé klíč/hodnota, které jsou povolené každý poskytovatel dat.</span><span class="sxs-lookup"><span data-stu-id="c561c-116">They provide methods and properties corresponding to the known key/value pairs permitted by each data provider.</span></span> <span data-ttu-id="c561c-117">Každá třída udržuje pevné kolekci synonyma a může překládat z synonymum na odpovídající známý název klíče.</span><span class="sxs-lookup"><span data-stu-id="c561c-117">Each class maintains a fixed collection of synonyms and can translate from a synonym to the corresponding well-known key name.</span></span> <span data-ttu-id="c561c-118">Ověřování pro dvojice klíč/hodnota platná a vyvolá výjimku, dvojici neplatný.</span><span class="sxs-lookup"><span data-stu-id="c561c-118">Checks are performed for valid key/value pairs and an invalid pair throws an exception.</span></span> <span data-ttu-id="c561c-119">Kromě toho vloženého hodnoty jsou zpracovávány v nouzovém režimu.</span><span class="sxs-lookup"><span data-stu-id="c561c-119">In addition, injected values are handled in a safe manner.</span></span>  
  
 <span data-ttu-id="c561c-120">Následující příklad ukazuje, jak <xref:System.Data.SqlClient.SqlConnectionStringBuilder> zpracovává vložené navíc hodnotu pro `Initial Catalog` nastavení.</span><span class="sxs-lookup"><span data-stu-id="c561c-120">The following example demonstrates how the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> handles an inserted extra value for the `Initial Catalog` setting.</span></span>  
  
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
  
 <span data-ttu-id="c561c-121">Výstup ukazuje, že <xref:System.Data.SqlClient.SqlConnectionStringBuilder> to správně zpracovat uvozovací znaky navíc hodnotu do dvojitých uvozovek místo přidávání připojovací řetězec jako nový pár klíč/hodnota.</span><span class="sxs-lookup"><span data-stu-id="c561c-121">The output shows that the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> handled this correctly by escaping the extra value in double quotation marks instead of appending it to the connection string as a new key/value pair.</span></span>  
  
```  
data source=(local);Integrated Security=True;  
initial catalog="AdventureWorks;NewValue=Bad"  
```  
  
## <a name="building-connection-strings-from-configuration-files"></a><span data-ttu-id="c561c-122">Vytváření připojovacích řetězců z konfiguračních souborů</span><span class="sxs-lookup"><span data-stu-id="c561c-122">Building Connection Strings from Configuration Files</span></span>  
 <span data-ttu-id="c561c-123">Pokud některé prvky připojovacího řetězce jsou známé předem, může být uložené v konfiguračním souboru a načíst v době běhu vytvořit úplný připojovací řetězec.</span><span class="sxs-lookup"><span data-stu-id="c561c-123">If certain elements of a connection string are known beforehand, they can be stored in a configuration file and retrieved at run time to construct a complete connection string.</span></span> <span data-ttu-id="c561c-124">Název databáze může být například předem známé, ale není název serveru.</span><span class="sxs-lookup"><span data-stu-id="c561c-124">For example, the name of the database might be known in advance, but not the name of the server.</span></span> <span data-ttu-id="c561c-125">Nebo můžete chtít uživatele k zadání jména a hesla v době běhu aniž by bylo možné vložit další hodnoty do připojovacího řetězce.</span><span class="sxs-lookup"><span data-stu-id="c561c-125">Or you might want a user to supply a name and password at run time without being able to inject other values into the connection string.</span></span>  
  
 <span data-ttu-id="c561c-126">Jeden z přetížené konstruktory pro Tvůrce připojovacích řetězců trvá <xref:System.String> jako argument, který můžete zadat částečné připojovací řetězec, který je pak možné provést z vstup uživatele.</span><span class="sxs-lookup"><span data-stu-id="c561c-126">One of the overloaded constructors for a connection string builder takes a <xref:System.String> as an argument, which enables you to supply a partial connection string that can then be completed from user input.</span></span> <span data-ttu-id="c561c-127">Částečné připojovací řetězec lze uložené v konfiguračním souboru a načítat za běhu.</span><span class="sxs-lookup"><span data-stu-id="c561c-127">The partial connection string can be stored in a configuration file and retrieved at run time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c561c-128"><xref:System.Configuration> Obor názvů umožňuje programový přístup ke konfiguračním souborům, které používají <xref:System.Web.Configuration.WebConfigurationManager> pro webové aplikace a <xref:System.Configuration.ConfigurationManager> pro aplikace pro Windows.</span><span class="sxs-lookup"><span data-stu-id="c561c-128">The <xref:System.Configuration> namespace allows programmatic access to configuration files that use the <xref:System.Web.Configuration.WebConfigurationManager> for Web applications and the <xref:System.Configuration.ConfigurationManager> for Windows applications.</span></span> <span data-ttu-id="c561c-129">Další informace o práci s připojovací řetězce a konfigurační soubory, najdete v části [připojovací řetězce a konfigurační soubory](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).</span><span class="sxs-lookup"><span data-stu-id="c561c-129">For more information about working with connection strings and configuration files, see [Connection Strings and Configuration Files](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).</span></span>  
  
### <a name="example"></a><span data-ttu-id="c561c-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="c561c-130">Example</span></span>  
 <span data-ttu-id="c561c-131">Tento příklad ukazuje načítání částečné připojovacího řetězce z konfiguračního souboru a dokončení nastavením <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A>, <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserID%2A>, a <xref:System.Data.SqlClient.SqlConnectionStringBuilder.Password%2A> vlastnosti <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span><span class="sxs-lookup"><span data-stu-id="c561c-131">This example demonstrates retrieving a partial connection string from a configuration file and completing it by setting the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A>, <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserID%2A>, and <xref:System.Data.SqlClient.SqlConnectionStringBuilder.Password%2A> properties of the <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span></span> <span data-ttu-id="c561c-132">Konfigurační soubor je definován následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="c561c-132">The configuration file is defined as follows.</span></span>  
  
```xml  
<connectionStrings>  
  <clear/>  
  <add name="partialConnectString"   
    connectionString="Initial Catalog=Northwind;"  
    providerName="System.Data.SqlClient" />  
</connectionStrings>  
```  
  
> [!NOTE]
>  <span data-ttu-id="c561c-133">Je nutné nastavit odkaz na `System.Configuration.dll` ve vašem projektu pro kód pro spuštění.</span><span class="sxs-lookup"><span data-stu-id="c561c-133">You must set a reference to the `System.Configuration.dll` in your project for the code to run.</span></span>  
  
 [!code-csharp[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/CS/source.cs#1)]
 [!code-vb[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="c561c-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="c561c-134">See Also</span></span>  
 [<span data-ttu-id="c561c-135">Připojovací řetězce</span><span class="sxs-lookup"><span data-stu-id="c561c-135">Connection Strings</span></span>](../../../../docs/framework/data/adonet/connection-strings.md)  
 [<span data-ttu-id="c561c-136">Ochrana osobních údajů a zabezpečení dat</span><span class="sxs-lookup"><span data-stu-id="c561c-136">Privacy and Data Security</span></span>](../../../../docs/framework/data/adonet/privacy-and-data-security.md)  
 [<span data-ttu-id="c561c-137">ADO.NET spravované zprostředkovatelé a středisku pro vývojáře datové sady</span><span class="sxs-lookup"><span data-stu-id="c561c-137">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
