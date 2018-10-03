---
title: Připojovací řetězce v ADO.NET
ms.date: 03/30/2017
ms.assetid: 745c5f95-2f02-4674-b378-6d51a7ec2490
ms.openlocfilehash: 1e6e2b6870195c99279639e1f4576a30b7126d4d
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2018
ms.locfileid: "48029388"
---
# <a name="connection-strings-in-adonet"></a><span data-ttu-id="ed00f-102">Připojovací řetězce v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ed00f-102">Connection Strings in ADO.NET</span></span>
<span data-ttu-id="ed00f-103">Rozhraní .NET Framework 2.0 zavedeny nové funkce pro práci s řetězci připojení, včetně představení nových klíčových slov na tvůrce třídy řetězec připojení, které usnadňují vytváření platný připojovací řetězce v době běhu.</span><span class="sxs-lookup"><span data-stu-id="ed00f-103">The .NET Framework 2.0 introduced new capabilities for working with connection strings, including the introduction of new keywords to the connection string builder classes, which facilitate creating valid connection strings at run time.</span></span>  
  
<span data-ttu-id="ed00f-104">Připojovací řetězec obsahuje informace o inicializaci, která je předána jako parametr od poskytovatele dat ke zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="ed00f-104">A connection string contains initialization information that is passed as a parameter from a data provider to a data source.</span></span> <span data-ttu-id="ed00f-105">Syntaxe závisí na poskytovateli dat a připojovací řetězec je analyzován při pokusu o otevření připojení.</span><span class="sxs-lookup"><span data-stu-id="ed00f-105">The syntax depends on the data provider, and the connection string is parsed during the attempt to open a connection.</span></span> <span data-ttu-id="ed00f-106">Chyby syntaxe vygenerovat výjimku za běhu, ale až po informace o připojení obdrží zdroj dat dojít k jiným chybám.</span><span class="sxs-lookup"><span data-stu-id="ed00f-106">Syntax errors generate a run-time exception, but other errors occur only after the data source receives connection information.</span></span> <span data-ttu-id="ed00f-107">Jakmile ověříte, zdroj dat platí volby zadané v připojovacím řetězci a otevře připojení.</span><span class="sxs-lookup"><span data-stu-id="ed00f-107">Once validated, the data source applies the options specified in the connection string and opens the connection.</span></span>
  
<span data-ttu-id="ed00f-108">Formát připojovacího řetězce je středníkem oddělený seznam dvojic klíč/hodnota parametru:</span><span class="sxs-lookup"><span data-stu-id="ed00f-108">The format of a connection string is a semicolon-delimited list of key/value parameter pairs:</span></span>
  
    keyword1=value; keyword2=value;
  
<span data-ttu-id="ed00f-109">Klíčová slova nerozlišují malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="ed00f-109">Keywords are not case-sensitive.</span></span> <span data-ttu-id="ed00f-110">Hodnoty, ale mohou být velká a malá písmena, v závislosti na zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="ed00f-110">Values, however, may be case-sensitive, depending on the data source.</span></span> <span data-ttu-id="ed00f-111">Klíčová slova a hodnoty mohou obsahovat [prázdné znaky](https://en.wikipedia.org/wiki/Whitespace_character#Unicode), i když úvodní a koncové mezery bude ignorován v klíčových slov a nekotované hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ed00f-111">Both keywords and values may contain [whitespace characters](https://en.wikipedia.org/wiki/Whitespace_character#Unicode), although leading and trailing whitespace is ignored in keywords and unquoted values.</span></span>

<span data-ttu-id="ed00f-112">Obsahuje-li hodnota středník, [řídící znaky Unicode](https://en.wikipedia.org/wiki/Unicode_control_characters), úvodní a koncové prázdné znaky musí být uzavřen v jednoduchých nebo dvojitých uvozovek, například:</span><span class="sxs-lookup"><span data-stu-id="ed00f-112">If a value contains the semicolon, [Unicode control characters](https://en.wikipedia.org/wiki/Unicode_control_characters), leading or trailing whitespace it must be enclosed in single or double quotation marks, e.g.:</span></span>

    Keyword=" whitespace  ";
    Keyword='special;character';

<span data-ttu-id="ed00f-113">Nadřazené znak nedojde v rámci hodnoty, který ji obklopuje.</span><span class="sxs-lookup"><span data-stu-id="ed00f-113">The enclosing character may not occur within the value it encloses.</span></span> <span data-ttu-id="ed00f-114">Proto můžou být uzavřená hodnotu obsahující jednoduchých uvozovek pouze dvojité uvozovky a naopak:</span><span class="sxs-lookup"><span data-stu-id="ed00f-114">Therefore, a value containing single quotation marks can be enclosed only in double quotation marks and vice versa:</span></span>

    Keyword='double"quotation;mark';
    Keyword="single'quotation;mark";

<span data-ttu-id="ed00f-115">Uvozovky sami, stejně jako znaménko rovná se nevyžadují, aby uvozovací znaky, takže následující připojovací řetězce jsou platné:</span><span class="sxs-lookup"><span data-stu-id="ed00f-115">The quotation marks themselves, as well as the equals sign, do not require escaping, so the following connection strings are valid:</span></span>

    Keyword=no "escaping" 'required';
    Keyword=a=b=c

<span data-ttu-id="ed00f-116">Protože každá hodnota je pro čtení do další středníkem nebo konec řetězce, je hodnota v druhém příkladu `a=b=c`, a poslední středník je volitelné.</span><span class="sxs-lookup"><span data-stu-id="ed00f-116">Since each value is read till the next semicolon or the end of string, the value in the latter example is `a=b=c`, and the final semicolon is optional.</span></span>

<span data-ttu-id="ed00f-117">Platný připojovací řetězec syntaxe závisí na poskytovateli a v průběhu let ze starší rozhraní API, jako je rozhraní ODBC se vyvinula.</span><span class="sxs-lookup"><span data-stu-id="ed00f-117">Valid connection string syntax depends on the provider, and has evolved over the years from earlier APIs like ODBC.</span></span> <span data-ttu-id="ed00f-118">Zprostředkovatel dat .NET Framework pro SQL Server (SqlClient) zahrnuje mnoho prvků ze starší syntaxi a je obecně flexibilnější s běžné syntaxe připojovacího řetězce.</span><span class="sxs-lookup"><span data-stu-id="ed00f-118">The .NET Framework Data Provider for SQL Server (SqlClient) incorporates many elements from older syntax and is generally more flexible with common connection string syntax.</span></span> <span data-ttu-id="ed00f-119">Jsou často stejně platná synonyma pro elementy syntaxe připojovacího řetězce, ale některé syntaxe a pravopisné chyby může způsobit problémy.</span><span class="sxs-lookup"><span data-stu-id="ed00f-119">There are frequently equally valid synonyms for connection string syntax elements, but some syntax and spelling errors can cause problems.</span></span> <span data-ttu-id="ed00f-120">Například "`Integrated Security=true`" platí, že "`IntegratedSecurity=true`" způsobí chybu.</span><span class="sxs-lookup"><span data-stu-id="ed00f-120">For example, "`Integrated Security=true`" is valid, whereas "`IntegratedSecurity=true`" causes an error.</span></span> <span data-ttu-id="ed00f-121">Kromě toho připojovací řetězce vytvořeným za běhu z neověřený vstup uživatele může vést k útokům prostřednictvím injektáže řetězec, ohrožující zabezpečení ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="ed00f-121">In addition, connection strings constructed at run time from unvalidated user input can lead to string injection attacks, jeopardizing security at the data source.</span></span>
  
<span data-ttu-id="ed00f-122">K řešení těchto problémů, ADO.NET 2.0 zavedeny nové tvůrci připojovacích řetězců pro každého poskytovatele dat .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ed00f-122">To address these problems, ADO.NET 2.0 introduced new connection string builders for each .NET Framework data provider.</span></span> <span data-ttu-id="ed00f-123">Klíčová slova jsou vystaveny jako vlastnosti, povolení syntaxe připojovacího řetězce k ověření před odesláním do zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="ed00f-123">Keywords are exposed as properties, enabling connection string syntax to be validated before submission to the data source.</span></span>
  
## <a name="in-this-section"></a><span data-ttu-id="ed00f-124">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="ed00f-124">In This Section</span></span>  
 [<span data-ttu-id="ed00f-125">Tvůrci připojovacích řetězců</span><span class="sxs-lookup"><span data-stu-id="ed00f-125">Connection String Builders</span></span>](../../../../docs/framework/data/adonet/connection-string-builders.md)  
 <span data-ttu-id="ed00f-126">Popisuje způsob použití `ConnectionStringBuilder` třídy sestavit platný připojovací řetězce v běhu.</span><span class="sxs-lookup"><span data-stu-id="ed00f-126">Demonstrates how to use the `ConnectionStringBuilder` classes to construct valid connection strings at run time.</span></span>
  
 [<span data-ttu-id="ed00f-127">Připojovací řetězce a konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="ed00f-127">Connection Strings and Configuration Files</span></span>](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md)  
 <span data-ttu-id="ed00f-128">Ukazuje, jak k ukládání a načítání připojovacích řetězců v konfiguračních souborech.</span><span class="sxs-lookup"><span data-stu-id="ed00f-128">Demonstrates how to store and retrieve connection strings in configuration files.</span></span>
  
 [<span data-ttu-id="ed00f-129">Syntaxe připojovacího řetězce</span><span class="sxs-lookup"><span data-stu-id="ed00f-129">Connection String Syntax</span></span>](../../../../docs/framework/data/adonet/connection-string-syntax.md)  
 <span data-ttu-id="ed00f-130">Popisuje postup konfigurace specifickým pro zprostředkovatele připojovací řetězce pro `SqlClient`, `OracleClient`, `OleDb`, a `Odbc`.</span><span class="sxs-lookup"><span data-stu-id="ed00f-130">Describes how to configure provider-specific connection strings for `SqlClient`, `OracleClient`, `OleDb`, and `Odbc`.</span></span>
  
 [<span data-ttu-id="ed00f-131">Ochrana informací o připojení</span><span class="sxs-lookup"><span data-stu-id="ed00f-131">Protecting Connection Information</span></span>](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 <span data-ttu-id="ed00f-132">Ukazuje postupy ochrany osobních údajů pro připojení ke zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="ed00f-132">Demonstrates techniques for protecting information used to connect to a data source.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ed00f-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="ed00f-133">See Also</span></span>  
 [<span data-ttu-id="ed00f-134">Připojení ke zdroji dat</span><span class="sxs-lookup"><span data-stu-id="ed00f-134">Connecting to a Data Source</span></span>](/cpp/data/odbc/connecting-to-a-data-source)  
 [<span data-ttu-id="ed00f-135">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="ed00f-135">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
