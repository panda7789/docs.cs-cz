---
title: Tvůrci připojovacích řetězců
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 8434b608-c4d3-43d3-8ae3-6d8c6b726759
ms.openlocfilehash: a29efbc1b4d886afe4329df011b522e4d589e2ee
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949495"
---
# <a name="connection-string-builders"></a><span data-ttu-id="0efc8-102">Tvůrci připojovacích řetězců</span><span class="sxs-lookup"><span data-stu-id="0efc8-102">Connection String Builders</span></span>
<span data-ttu-id="0efc8-103">V dřívějších verzích ADO.NET se neobjevila kontrola připojovacích řetězců s zřetězenými řetězcovými hodnotami, takže v době běhu se nesprávné klíčové slovo vygenerovalo jako <xref:System.ArgumentException>nesprávné.</span><span class="sxs-lookup"><span data-stu-id="0efc8-103">In earlier versions of ADO.NET, compile-time checking of connection strings with concatenated string values did not occur, so that at run time, an incorrect keyword generated an <xref:System.ArgumentException>.</span></span> <span data-ttu-id="0efc8-104">Každé z zprostředkovatelů .NET Framework dat podporuje odlišnou syntaxi pro klíčová slova připojovacích řetězců, která vytvořila v případě ručního vytvoření platných připojovacích řetězců.</span><span class="sxs-lookup"><span data-stu-id="0efc8-104">Each of the .NET Framework data providers supported different syntax for connection string keywords, which made constructing valid connection strings difficult if done manually.</span></span> <span data-ttu-id="0efc8-105">Pro vyřešení tohoto problému ADO.NET 2,0 pro každého poskytovatele dat .NET Framework zavedla nové tvůrci připojovacích řetězců.</span><span class="sxs-lookup"><span data-stu-id="0efc8-105">To address this problem, ADO.NET 2.0 introduced new connection string builders for each .NET Framework data provider.</span></span> <span data-ttu-id="0efc8-106">Každý poskytovatel dat obsahuje třídu Tvůrce připojovacích řetězců silného typu, která <xref:System.Data.Common.DbConnectionStringBuilder>dědí z.</span><span class="sxs-lookup"><span data-stu-id="0efc8-106">Each data provider includes a strongly typed connection string builder class that inherits from <xref:System.Data.Common.DbConnectionStringBuilder>.</span></span> <span data-ttu-id="0efc8-107">V následující tabulce jsou uvedeny poskytovatelé dat .NET Framework a jejich přidružené třídy Tvůrce připojovacích řetězců.</span><span class="sxs-lookup"><span data-stu-id="0efc8-107">The following table lists the .NET Framework data providers and their associated connection string builder classes.</span></span>  
  
|<span data-ttu-id="0efc8-108">Poskytovatel</span><span class="sxs-lookup"><span data-stu-id="0efc8-108">Provider</span></span>|<span data-ttu-id="0efc8-109">ConnectionStringBuilder – třída</span><span class="sxs-lookup"><span data-stu-id="0efc8-109">ConnectionStringBuilder class</span></span>|  
|--------------|-----------------------------------|  
|<xref:System.Data.SqlClient>|<xref:System.Data.SqlClient.SqlConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OleDb>|<xref:System.Data.OleDb.OleDbConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.Odbc>|<xref:System.Data.Odbc.OdbcConnectionStringBuilder?displayProperty=nameWithType>|  
|<xref:System.Data.OracleClient>|<xref:System.Data.OracleClient.OracleConnectionStringBuilder?displayProperty=nameWithType>|  
  
## <a name="connection-string-injection-attacks"></a><span data-ttu-id="0efc8-110">Útoky prostřednictvím injektáže připojovacího řetězce</span><span class="sxs-lookup"><span data-stu-id="0efc8-110">Connection String Injection Attacks</span></span>  
 <span data-ttu-id="0efc8-111">Útok injektáže připojovacího řetězce může nastat, pokud se k sestavení připojovacích řetězců, které jsou založeny na vstupu uživatele, používá dynamická zřetězení řetězců.</span><span class="sxs-lookup"><span data-stu-id="0efc8-111">A connection string injection attack can occur when dynamic string concatenation is used to build connection strings that are based on user input.</span></span> <span data-ttu-id="0efc8-112">Pokud není řetězec ověřený a škodlivý text nebo znaky nejsou uvozeny, útočník může potenciálně přistupovat k citlivým datům nebo jiným prostředkům na serveru.</span><span class="sxs-lookup"><span data-stu-id="0efc8-112">If the string is not validated and malicious text or characters not escaped, an attacker can potentially access sensitive data or other resources on the server.</span></span> <span data-ttu-id="0efc8-113">Útočník by například mohl připojit útok tím, že dodá středník a připojí další hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0efc8-113">For example, an attacker could mount an attack by supplying a semicolon and appending an additional value.</span></span> <span data-ttu-id="0efc8-114">Připojovací řetězec je analyzován pomocí algoritmu "poslední jeden server WINS" a nepřátelský vstup je nahrazen legitimní hodnotou.</span><span class="sxs-lookup"><span data-stu-id="0efc8-114">The connection string is parsed by using a "last one wins" algorithm, and the hostile input is substituted for a legitimate value.</span></span>  
  
 <span data-ttu-id="0efc8-115">Třídy Tvůrce připojovacích řetězců jsou navržené tak, aby se vyloučila přibližná a chráněná proti chybám syntaxe a chybám zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="0efc8-115">The connection string builder classes are designed to eliminate guesswork and protect against syntax errors and security vulnerabilities.</span></span> <span data-ttu-id="0efc8-116">Poskytují metody a vlastnosti, které odpovídají známým dvojicím klíč/hodnota povolených každým poskytovatelem dat.</span><span class="sxs-lookup"><span data-stu-id="0efc8-116">They provide methods and properties corresponding to the known key/value pairs permitted by each data provider.</span></span> <span data-ttu-id="0efc8-117">Každá třída udržuje pevnou kolekci synonym a může překládat z synonyma na odpovídající název dobře známého klíče.</span><span class="sxs-lookup"><span data-stu-id="0efc8-117">Each class maintains a fixed collection of synonyms and can translate from a synonym to the corresponding well-known key name.</span></span> <span data-ttu-id="0efc8-118">Kontroly jsou prováděny pro platné páry klíč/hodnota a neplatný pár vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="0efc8-118">Checks are performed for valid key/value pairs and an invalid pair throws an exception.</span></span> <span data-ttu-id="0efc8-119">Vložené hodnoty jsou navíc zpracovávány bezpečným způsobem.</span><span class="sxs-lookup"><span data-stu-id="0efc8-119">In addition, injected values are handled in a safe manner.</span></span>  
  
 <span data-ttu-id="0efc8-120">Následující příklad ukazuje, <xref:System.Data.SqlClient.SqlConnectionStringBuilder> jak zpracovává vloženou další hodnotu `Initial Catalog` pro nastavení.</span><span class="sxs-lookup"><span data-stu-id="0efc8-120">The following example demonstrates how the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> handles an inserted extra value for the `Initial Catalog` setting.</span></span>  
  
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
  
 <span data-ttu-id="0efc8-121">Výstup ukazuje, že je <xref:System.Data.SqlClient.SqlConnectionStringBuilder> správně zpracován pomocí uvozovací hodnoty v uvozovkách místo připojení k připojovacímu řetězci jako nový pár klíč/hodnota.</span><span class="sxs-lookup"><span data-stu-id="0efc8-121">The output shows that the <xref:System.Data.SqlClient.SqlConnectionStringBuilder> handled this correctly by escaping the extra value in double quotation marks instead of appending it to the connection string as a new key/value pair.</span></span>  
  
```  
data source=(local);Integrated Security=True;  
initial catalog="AdventureWorks;NewValue=Bad"  
```  
  
## <a name="building-connection-strings-from-configuration-files"></a><span data-ttu-id="0efc8-122">Sestavování připojovacích řetězců z konfiguračních souborů</span><span class="sxs-lookup"><span data-stu-id="0efc8-122">Building Connection Strings from Configuration Files</span></span>  
 <span data-ttu-id="0efc8-123">Pokud jsou některé prvky připojovacího řetězce známy předem, mohou být uloženy do konfiguračního souboru a načteny v době běhu pro vytvoření kompletního připojovacího řetězce.</span><span class="sxs-lookup"><span data-stu-id="0efc8-123">If certain elements of a connection string are known beforehand, they can be stored in a configuration file and retrieved at run time to construct a complete connection string.</span></span> <span data-ttu-id="0efc8-124">Například název databáze může být známý předem, ale ne název serveru.</span><span class="sxs-lookup"><span data-stu-id="0efc8-124">For example, the name of the database might be known in advance, but not the name of the server.</span></span> <span data-ttu-id="0efc8-125">Nebo můžete chtít, aby uživatel zadal jméno a heslo v době běhu, aniž by bylo možné do připojovacího řetězce vložit další hodnoty.</span><span class="sxs-lookup"><span data-stu-id="0efc8-125">Or you might want a user to supply a name and password at run time without being able to inject other values into the connection string.</span></span>  
  
 <span data-ttu-id="0efc8-126">Jeden z přetížených konstruktorů pro Tvůrce připojovacích řetězců přijímá <xref:System.String> jako argument, který umožňuje zadat částečný připojovací řetězec, který lze následně dokončit ze vstupu uživatele.</span><span class="sxs-lookup"><span data-stu-id="0efc8-126">One of the overloaded constructors for a connection string builder takes a <xref:System.String> as an argument, which enables you to supply a partial connection string that can then be completed from user input.</span></span> <span data-ttu-id="0efc8-127">Částečný připojovací řetězec může být uložen do konfiguračního souboru a načten v době běhu.</span><span class="sxs-lookup"><span data-stu-id="0efc8-127">The partial connection string can be stored in a configuration file and retrieved at run time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0efc8-128">Obor názvů umožňuje programový přístup ke konfiguračním souborům, které <xref:System.Web.Configuration.WebConfigurationManager> používají <xref:System.Configuration.ConfigurationManager> pro webové aplikace a aplikace systému Windows. <xref:System.Configuration></span><span class="sxs-lookup"><span data-stu-id="0efc8-128">The <xref:System.Configuration> namespace allows programmatic access to configuration files that use the <xref:System.Web.Configuration.WebConfigurationManager> for Web applications and the <xref:System.Configuration.ConfigurationManager> for Windows applications.</span></span> <span data-ttu-id="0efc8-129">Další informace o práci s připojovacími řetězci a konfiguračními soubory najdete v tématu [připojovací řetězce a konfigurační soubory](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).</span><span class="sxs-lookup"><span data-stu-id="0efc8-129">For more information about working with connection strings and configuration files, see [Connection Strings and Configuration Files](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md).</span></span>  
  
### <a name="example"></a><span data-ttu-id="0efc8-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="0efc8-130">Example</span></span>  
 <span data-ttu-id="0efc8-131">Tento příklad ukazuje načtení částečného připojovacího řetězce z konfiguračního souboru a jeho dokončení <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A>nastavením vlastností <xref:System.Data.SqlClient.SqlConnectionStringBuilder>, <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserID%2A>a <xref:System.Data.SqlClient.SqlConnectionStringBuilder.Password%2A> .</span><span class="sxs-lookup"><span data-stu-id="0efc8-131">This example demonstrates retrieving a partial connection string from a configuration file and completing it by setting the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.DataSource%2A>, <xref:System.Data.SqlClient.SqlConnectionStringBuilder.UserID%2A>, and <xref:System.Data.SqlClient.SqlConnectionStringBuilder.Password%2A> properties of the <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span></span> <span data-ttu-id="0efc8-132">Konfigurační soubor je definován následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="0efc8-132">The configuration file is defined as follows.</span></span>  
  
```xml  
<connectionStrings>  
  <clear/>  
  <add name="partialConnectString"   
    connectionString="Initial Catalog=Northwind;"  
    providerName="System.Data.SqlClient" />  
</connectionStrings>  
```  
  
> [!NOTE]
> <span data-ttu-id="0efc8-133">Chcete-li spustit kód, musíte `System.Configuration.dll` nastavit odkaz na v projektu.</span><span class="sxs-lookup"><span data-stu-id="0efc8-133">You must set a reference to the `System.Configuration.dll` in your project for the code to run.</span></span>  
  
 [!code-csharp[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/CS/source.cs#1)]
 [!code-vb[DataWorks SqlConnectionStringBuilder.UserNamePwd#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlConnectionStringBuilder.UserNamePwd/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="0efc8-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0efc8-134">See also</span></span>

- [<span data-ttu-id="0efc8-135">Připojovací řetězce</span><span class="sxs-lookup"><span data-stu-id="0efc8-135">Connection Strings</span></span>](../../../../docs/framework/data/adonet/connection-strings.md)
- [<span data-ttu-id="0efc8-136">Ochrana osobních údajů a zabezpečení dat</span><span class="sxs-lookup"><span data-stu-id="0efc8-136">Privacy and Data Security</span></span>](../../../../docs/framework/data/adonet/privacy-and-data-security.md)
- [<span data-ttu-id="0efc8-137">ADO.NET spravované zprostředkovatele a sady dat – středisko pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="0efc8-137">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
