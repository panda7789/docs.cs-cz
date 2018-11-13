---
title: Připojovací řetězce v ADO.NET
ms.date: 10/10/2018
ms.assetid: 745c5f95-2f02-4674-b378-6d51a7ec2490
ms.openlocfilehash: 078fdab257115296f9ff00330265cb14ff8674c8
ms.sourcegitcommit: 5fd80619c760fa8c25d33a6f5661247cb65da465
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50409454"
---
# <a name="connection-strings-in-adonet"></a><span data-ttu-id="70dc6-102">Připojovací řetězce v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="70dc6-102">Connection Strings in ADO.NET</span></span>

<span data-ttu-id="70dc6-103">Připojovací řetězec obsahuje informace o inicializaci, která je předána jako parametr od poskytovatele dat ke zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="70dc6-103">A connection string contains initialization information that is passed as a parameter from a data provider to a data source.</span></span> <span data-ttu-id="70dc6-104">Zprostředkovatel dat přijímá jako hodnotu připojovacího řetězce <xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="70dc6-104">The data provider receives the connection string as the value of the <xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="70dc6-105">Zprostředkovatel analyzuje připojovací řetězec a zajistí, že je syntaxe správná a že jsou podporované klíčová slova.</span><span class="sxs-lookup"><span data-stu-id="70dc6-105">The provider parses the connection string and ensures that the syntax is correct and that the keywords are supported.</span></span> <span data-ttu-id="70dc6-106">Pak bude <xref:System.Data.Common.DbConnection.Open?displayProperty=nameWithType> metoda předává parametry analyzovaný připojení ke zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="70dc6-106">Then the <xref:System.Data.Common.DbConnection.Open?displayProperty=nameWithType> method passes the parsed connection parameters to the data source.</span></span> <span data-ttu-id="70dc6-107">Zdroj dat provádí další ověřování a naváže připojení.</span><span class="sxs-lookup"><span data-stu-id="70dc6-107">The data source performs further validation and establishes a connection.</span></span>

## <a name="connection-string-syntax"></a><span data-ttu-id="70dc6-108">Syntaxe připojovacího řetězce</span><span class="sxs-lookup"><span data-stu-id="70dc6-108">Connection string syntax</span></span>

<span data-ttu-id="70dc6-109">Připojovací řetězec se středníkem oddělený seznam dvojic klíč/hodnota parametru:</span><span class="sxs-lookup"><span data-stu-id="70dc6-109">A connection string is a semicolon-delimited list of key/value parameter pairs:</span></span>
  
    keyword1=value; keyword2=value;
  
<span data-ttu-id="70dc6-110">Klíčová slova nerozlišují malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="70dc6-110">Keywords are not case-sensitive.</span></span> <span data-ttu-id="70dc6-111">Hodnoty, ale mohou být velká a malá písmena, v závislosti na zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="70dc6-111">Values, however, may be case-sensitive, depending on the data source.</span></span> <span data-ttu-id="70dc6-112">Klíčová slova a hodnoty mohou obsahovat [prázdné znaky](https://en.wikipedia.org/wiki/Whitespace_character#Unicode).</span><span class="sxs-lookup"><span data-stu-id="70dc6-112">Both keywords and values may contain [whitespace characters](https://en.wikipedia.org/wiki/Whitespace_character#Unicode).</span></span> <span data-ttu-id="70dc6-113">Počáteční a koncové mezery bude ignorován v klíčových slov a nekotované hodnoty.</span><span class="sxs-lookup"><span data-stu-id="70dc6-113">Leading and trailing white space is ignored in keywords and unquoted values.</span></span>

<span data-ttu-id="70dc6-114">Obsahuje-li hodnota středník, [řídící znaky Unicode](https://en.wikipedia.org/wiki/Unicode_control_characters), nebo úvodní a koncové prázdné znaky, musí být uzavřen v jednoduchých nebo dvojitých uvozovek.</span><span class="sxs-lookup"><span data-stu-id="70dc6-114">If a value contains the semicolon, [Unicode control characters](https://en.wikipedia.org/wiki/Unicode_control_characters), or leading or trailing white space, it must be enclosed in single or double quotation marks.</span></span> <span data-ttu-id="70dc6-115">Příklad:</span><span class="sxs-lookup"><span data-stu-id="70dc6-115">For example:</span></span>

    Keyword=" whitespace  ";
    Keyword='special;character';

<span data-ttu-id="70dc6-116">Nadřazené znak nedojde v rámci hodnoty, který ji obklopuje.</span><span class="sxs-lookup"><span data-stu-id="70dc6-116">The enclosing character may not occur within the value it encloses.</span></span> <span data-ttu-id="70dc6-117">Proto můžou být uzavřená hodnotu obsahující jednoduchých uvozovek pouze do dvojitých uvozovek a naopak:</span><span class="sxs-lookup"><span data-stu-id="70dc6-117">Therefore, a value containing single quotation marks can be enclosed only in double quotation marks, and vice versa:</span></span>

    Keyword='double"quotation;mark';
    Keyword="single'quotation;mark";

<span data-ttu-id="70dc6-118">Uvozovky sami, stejně jako znaménko rovná se nevyžadují, aby uvozovací znaky, takže následující připojovací řetězce jsou platné:</span><span class="sxs-lookup"><span data-stu-id="70dc6-118">The quotation marks themselves, as well as the equals sign, do not require escaping, so the following connection strings are valid:</span></span>

    Keyword=no "escaping" 'required';
    Keyword=a=b=c

<span data-ttu-id="70dc6-119">Protože každá hodnota je pro čtení do další středníkem nebo konec řetězce, je hodnota v druhém příkladu `a=b=c`, a poslední středník je volitelné.</span><span class="sxs-lookup"><span data-stu-id="70dc6-119">Since each value is read till the next semicolon or the end of string, the value in the latter example is `a=b=c`, and the final semicolon is optional.</span></span>

<span data-ttu-id="70dc6-120">Všechny řetězce připojení sdílet stejnou základní syntaxi popsané výše.</span><span class="sxs-lookup"><span data-stu-id="70dc6-120">All connection strings share the same basic syntax described above.</span></span> <span data-ttu-id="70dc6-121">Sada rozpoznaný klíčová slova závisí na poskytovateli, ale a průběžně vyvíjel let ze starší rozhraní API, jako *ODBC*.</span><span class="sxs-lookup"><span data-stu-id="70dc6-121">The set of recognized keywords depends on the provider, however, and has evolved over the years from earlier APIs such as *ODBC*.</span></span> <span data-ttu-id="70dc6-122">*Rozhraní .NET Framework* zprostředkovatel dat pro *systému SQL Server* (`SqlClient`) podporuje mnoho klíčových slov z starší rozhraní API, ale je obecně flexibilnější a přijímá synonyma pro spoustu běžných připojovací řetězec klíčová slova.</span><span class="sxs-lookup"><span data-stu-id="70dc6-122">The *.NET Framework* data provider for *SQL Server* (`SqlClient`) supports many keywords from older APIs, but is generally more flexible and accepts synonyms for many of the common connection string keywords.</span></span>

<span data-ttu-id="70dc6-123">Překlepů mohou způsobit chyby.</span><span class="sxs-lookup"><span data-stu-id="70dc6-123">Typing mistakes can cause errors.</span></span> <span data-ttu-id="70dc6-124">Například `Integrated Security=true` je platný, ale `IntegratedSecurity=true` způsobí chybu.</span><span class="sxs-lookup"><span data-stu-id="70dc6-124">For example, `Integrated Security=true` is valid, but `IntegratedSecurity=true` causes an error.</span></span>

<span data-ttu-id="70dc6-125">Připojovací řetězce s ručně vytvořeným za běhu z neověřený vstup uživatele je ohrožen útoky prostřednictvím injektáže řetězec a by mohly ohrozit zabezpečení ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="70dc6-125">Connection strings constructed manually at run time from unvalidated user input are vulnerable to string-injection attacks and jeopardize security at the data source.</span></span> <span data-ttu-id="70dc6-126">K řešení těchto problémů *ADO.NET* 2.0 zavedl [tvůrci připojovacích řetězců](../../../../docs/framework/data/adonet/connection-string-builders.md) pro každou *rozhraní .NET Framework* poskytovatele dat služeb.</span><span class="sxs-lookup"><span data-stu-id="70dc6-126">To address these problems, *ADO.NET* 2.0 introduced [connection string builders](../../../../docs/framework/data/adonet/connection-string-builders.md) for each *.NET Framework* data provider.</span></span> <span data-ttu-id="70dc6-127">Tyto tvůrci připojovacích řetězců vystavit parametry jako vlastnosti silného typu a bude možné ověřit připojovací řetězec před odesláním do zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="70dc6-127">These connection string builders expose parameters as strongly-typed properties, and make it possible to validate the connection string before it's sent to the data source.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="70dc6-128">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="70dc6-128">In This Section</span></span>  
 [<span data-ttu-id="70dc6-129">Tvůrci připojovacích řetězců</span><span class="sxs-lookup"><span data-stu-id="70dc6-129">Connection String Builders</span></span>](../../../../docs/framework/data/adonet/connection-string-builders.md)  
 <span data-ttu-id="70dc6-130">Popisuje způsob použití `ConnectionStringBuilder` třídy sestavit platný připojovací řetězce v běhu.</span><span class="sxs-lookup"><span data-stu-id="70dc6-130">Demonstrates how to use the `ConnectionStringBuilder` classes to construct valid connection strings at run time.</span></span>
  
 [<span data-ttu-id="70dc6-131">Připojovací řetězce a konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="70dc6-131">Connection Strings and Configuration Files</span></span>](../../../../docs/framework/data/adonet/connection-strings-and-configuration-files.md)  
 <span data-ttu-id="70dc6-132">Ukazuje, jak k ukládání a načítání připojovacích řetězců v konfiguračních souborech.</span><span class="sxs-lookup"><span data-stu-id="70dc6-132">Demonstrates how to store and retrieve connection strings in configuration files.</span></span>
  
 [<span data-ttu-id="70dc6-133">Syntaxe připojovacího řetězce</span><span class="sxs-lookup"><span data-stu-id="70dc6-133">Connection String Syntax</span></span>](../../../../docs/framework/data/adonet/connection-string-syntax.md)  
 <span data-ttu-id="70dc6-134">Popisuje postup konfigurace specifickým pro zprostředkovatele připojovací řetězce pro `SqlClient`, `OracleClient`, `OleDb`, a `Odbc`.</span><span class="sxs-lookup"><span data-stu-id="70dc6-134">Describes how to configure provider-specific connection strings for `SqlClient`, `OracleClient`, `OleDb`, and `Odbc`.</span></span>
  
 [<span data-ttu-id="70dc6-135">Ochrana informací o připojení</span><span class="sxs-lookup"><span data-stu-id="70dc6-135">Protecting Connection Information</span></span>](../../../../docs/framework/data/adonet/protecting-connection-information.md)  
 <span data-ttu-id="70dc6-136">Ukazuje postupy ochrany osobních údajů pro připojení ke zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="70dc6-136">Demonstrates techniques for protecting information used to connect to a data source.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="70dc6-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="70dc6-137">See Also</span></span>  
 [<span data-ttu-id="70dc6-138">Připojení ke zdroji dat</span><span class="sxs-lookup"><span data-stu-id="70dc6-138">Connecting to a Data Source</span></span>](/cpp/data/odbc/connecting-to-a-data-source)  
 [<span data-ttu-id="70dc6-139">ADO.NET spravovaných zprostředkovatelích a datové sady pro vývojáře</span><span class="sxs-lookup"><span data-stu-id="70dc6-139">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
