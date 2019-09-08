---
title: Připojovací řetězce v ADO.NET
ms.date: 10/10/2018
ms.assetid: 745c5f95-2f02-4674-b378-6d51a7ec2490
ms.openlocfilehash: 8f726ca71ba955ef542d15e0e8318c2b310e607e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784905"
---
# <a name="connection-strings-in-adonet"></a><span data-ttu-id="a0f3b-102">Připojovací řetězce v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a0f3b-102">Connection Strings in ADO.NET</span></span>

<span data-ttu-id="a0f3b-103">Připojovací řetězec obsahuje inicializační informace, které jsou předány jako parametr od poskytovatele dat ke zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="a0f3b-103">A connection string contains initialization information that is passed as a parameter from a data provider to a data source.</span></span> <span data-ttu-id="a0f3b-104">Zprostředkovatel dat přijímá připojovací řetězec jako hodnotu <xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a0f3b-104">The data provider receives the connection string as the value of the <xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="a0f3b-105">Zprostředkovatel analyzuje připojovací řetězec a ověří, zda je syntaxe správná a zda jsou klíčová slova podporována.</span><span class="sxs-lookup"><span data-stu-id="a0f3b-105">The provider parses the connection string and ensures that the syntax is correct and that the keywords are supported.</span></span> <span data-ttu-id="a0f3b-106"><xref:System.Data.Common.DbConnection.Open?displayProperty=nameWithType> Pak metoda předá analyzovaným parametrům připojení ke zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="a0f3b-106">Then the <xref:System.Data.Common.DbConnection.Open?displayProperty=nameWithType> method passes the parsed connection parameters to the data source.</span></span> <span data-ttu-id="a0f3b-107">Zdroj dat provádí další ověření a naváže připojení.</span><span class="sxs-lookup"><span data-stu-id="a0f3b-107">The data source performs further validation and establishes a connection.</span></span>

## <a name="connection-string-syntax"></a><span data-ttu-id="a0f3b-108">Syntaxe připojovacího řetězce</span><span class="sxs-lookup"><span data-stu-id="a0f3b-108">Connection string syntax</span></span>

<span data-ttu-id="a0f3b-109">Připojovací řetězec je seznam dvojic parametrů klíč/hodnota oddělených středníkem:</span><span class="sxs-lookup"><span data-stu-id="a0f3b-109">A connection string is a semicolon-delimited list of key/value parameter pairs:</span></span>

```
keyword1=value; keyword2=value;
```

<span data-ttu-id="a0f3b-110">V klíčových slovech se nerozlišují malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="a0f3b-110">Keywords are not case-sensitive.</span></span> <span data-ttu-id="a0f3b-111">V závislosti na zdroji dat ale můžou v nich být rozlišována velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="a0f3b-111">Values, however, may be case-sensitive, depending on the data source.</span></span> <span data-ttu-id="a0f3b-112">Klíčová slova a hodnoty mohou obsahovat [prázdné znaky](https://en.wikipedia.org/wiki/Whitespace_character#Unicode).</span><span class="sxs-lookup"><span data-stu-id="a0f3b-112">Both keywords and values may contain [whitespace characters](https://en.wikipedia.org/wiki/Whitespace_character#Unicode).</span></span> <span data-ttu-id="a0f3b-113">Úvodní a koncové prázdné znaky jsou ignorovány v klíčových slovech a hodnotách v uvozovkách.</span><span class="sxs-lookup"><span data-stu-id="a0f3b-113">Leading and trailing white space is ignored in keywords and unquoted values.</span></span>

<span data-ttu-id="a0f3b-114">Pokud hodnota obsahuje středník, [řídicí znaky sady Unicode](https://en.wikipedia.org/wiki/Unicode_control_characters)nebo úvodní nebo koncové prázdné znaky, musí být uzavřeny v jednoduchých nebo dvojitých uvozovkách.</span><span class="sxs-lookup"><span data-stu-id="a0f3b-114">If a value contains the semicolon, [Unicode control characters](https://en.wikipedia.org/wiki/Unicode_control_characters), or leading or trailing white space, it must be enclosed in single or double quotation marks.</span></span> <span data-ttu-id="a0f3b-115">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a0f3b-115">For example:</span></span>

```
Keyword=" whitespace  ";
Keyword='special;character';
```

<span data-ttu-id="a0f3b-116">Ohraničující znak se nesmí nacházet v rámci hodnoty, kterou obklopuje.</span><span class="sxs-lookup"><span data-stu-id="a0f3b-116">The enclosing character may not occur within the value it encloses.</span></span> <span data-ttu-id="a0f3b-117">Proto lze hodnotu obsahující jednoduché uvozovky uzavřít pouze do dvojitých uvozovek a naopak:</span><span class="sxs-lookup"><span data-stu-id="a0f3b-117">Therefore, a value containing single quotation marks can be enclosed only in double quotation marks, and vice versa:</span></span>

```
Keyword='double"quotation;mark';
Keyword="single'quotation;mark";
```

<span data-ttu-id="a0f3b-118">Ohraničující znak můžete také vložit pomocí dvou z nich dohromady:</span><span class="sxs-lookup"><span data-stu-id="a0f3b-118">You can also escape the enclosing character by using two of them together:</span></span>

```
Keyword="double""quotation";
Keyword='single''quotation';
```

<span data-ttu-id="a0f3b-119">Citace samotné a stejně jako znaménko rovná se nevyžadují uvozovací znaky, takže jsou platné následující připojovací řetězce:</span><span class="sxs-lookup"><span data-stu-id="a0f3b-119">The quotation marks themselves, as well as the equals sign, do not require escaping, so the following connection strings are valid:</span></span>

```
Keyword=no "escaping" 'required';
Keyword=a=b=c
```

<span data-ttu-id="a0f3b-120">Vzhledem k tomu, že každá hodnota je čtena do následujícího středníku nebo konce řetězce, hodnota v druhém příkladu `a=b=c`je a poslední středník je nepovinný.</span><span class="sxs-lookup"><span data-stu-id="a0f3b-120">Since each value is read till the next semicolon or the end of string, the value in the latter example is `a=b=c`, and the final semicolon is optional.</span></span>

<span data-ttu-id="a0f3b-121">Všechny připojovací řetězce sdílejí stejnou základní syntaxi popsanou výše.</span><span class="sxs-lookup"><span data-stu-id="a0f3b-121">All connection strings share the same basic syntax described above.</span></span> <span data-ttu-id="a0f3b-122">Sada rozpoznaných klíčových slov závisí na poskytovateli, ale na těchto letech se vyvinula z dřívějších rozhraní API, jako je například *ODBC*.</span><span class="sxs-lookup"><span data-stu-id="a0f3b-122">The set of recognized keywords depends on the provider, however, and has evolved over the years from earlier APIs such as *ODBC*.</span></span> <span data-ttu-id="a0f3b-123">Zprostředkovatel dat *.NET Framework* pro *SQL Server* (`SqlClient`) podporuje mnoho klíčových slov ze starších rozhraní API, ale je obecně flexibilnější a přijímá synonyma pro mnoho běžných klíčových slov řetězce připojení.</span><span class="sxs-lookup"><span data-stu-id="a0f3b-123">The *.NET Framework* data provider for *SQL Server* (`SqlClient`) supports many keywords from older APIs, but is generally more flexible and accepts synonyms for many of the common connection string keywords.</span></span>

<span data-ttu-id="a0f3b-124">Psaní chyb může způsobit chyby.</span><span class="sxs-lookup"><span data-stu-id="a0f3b-124">Typing mistakes can cause errors.</span></span> <span data-ttu-id="a0f3b-125">Například `Integrated Security=true` je platný, ale `IntegratedSecurity=true` způsobí chybu.</span><span class="sxs-lookup"><span data-stu-id="a0f3b-125">For example, `Integrated Security=true` is valid, but `IntegratedSecurity=true` causes an error.</span></span>

<span data-ttu-id="a0f3b-126">Připojovací řetězce konstruované ručně v době spuštění z neověřeného vstupu uživatele jsou zranitelné vůči útokům prostřednictvím injektáže řetězce a ohrožení zabezpečení ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="a0f3b-126">Connection strings constructed manually at run time from unvalidated user input are vulnerable to string-injection attacks and jeopardize security at the data source.</span></span> <span data-ttu-id="a0f3b-127">Pro řešení těchto problémů zavedlo *ADO.NET* 2,0 [tvůrci připojovacích řetězců](connection-string-builders.md) pro každého poskytovatele dat *.NET Framework* .</span><span class="sxs-lookup"><span data-stu-id="a0f3b-127">To address these problems, *ADO.NET* 2.0 introduced [connection string builders](connection-string-builders.md) for each *.NET Framework* data provider.</span></span> <span data-ttu-id="a0f3b-128">Tyto tvůrci připojovacích řetězců zpřístupňují parametry jako vlastnosti silného typu a umožňují ověření připojovacího řetězce před jeho odesláním do zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="a0f3b-128">These connection string builders expose parameters as strongly-typed properties, and make it possible to validate the connection string before it's sent to the data source.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="a0f3b-129">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="a0f3b-129">In This Section</span></span>

<span data-ttu-id="a0f3b-130">[Tvůrci připojovacích řetězců](connection-string-builders.md)</span><span class="sxs-lookup"><span data-stu-id="a0f3b-130">[Connection String Builders](connection-string-builders.md)</span></span>\
<span data-ttu-id="a0f3b-131">Ukazuje, jak použít `ConnectionStringBuilder` třídy pro vytvoření platných připojovacích řetězců za běhu.</span><span class="sxs-lookup"><span data-stu-id="a0f3b-131">Demonstrates how to use the `ConnectionStringBuilder` classes to construct valid connection strings at run time.</span></span>

<span data-ttu-id="a0f3b-132">[Připojovací řetězce a konfigurační soubory](connection-strings-and-configuration-files.md)</span><span class="sxs-lookup"><span data-stu-id="a0f3b-132">[Connection Strings and Configuration Files](connection-strings-and-configuration-files.md)</span></span>\
<span data-ttu-id="a0f3b-133">Ukazuje, jak ukládat a načítat připojovací řetězce v konfiguračních souborech.</span><span class="sxs-lookup"><span data-stu-id="a0f3b-133">Demonstrates how to store and retrieve connection strings in configuration files.</span></span>

<span data-ttu-id="a0f3b-134">[Syntaxe připojovacího řetězce](connection-string-syntax.md)</span><span class="sxs-lookup"><span data-stu-id="a0f3b-134">[Connection String Syntax](connection-string-syntax.md)</span></span>\
<span data-ttu-id="a0f3b-135">Popisuje postup konfigurace připojovacích řetězců specifických pro konkrétní poskytovatele `SqlClient`pro `OracleClient`, `OleDb`, a `Odbc`.</span><span class="sxs-lookup"><span data-stu-id="a0f3b-135">Describes how to configure provider-specific connection strings for `SqlClient`, `OracleClient`, `OleDb`, and `Odbc`.</span></span>

<span data-ttu-id="a0f3b-136">[Ochrana informací o připojení](protecting-connection-information.md)</span><span class="sxs-lookup"><span data-stu-id="a0f3b-136">[Protecting Connection Information](protecting-connection-information.md)</span></span>\
<span data-ttu-id="a0f3b-137">Ukazuje techniky ochrany informací používaných pro připojení ke zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="a0f3b-137">Demonstrates techniques for protecting information used to connect to a data source.</span></span>

## <a name="see-also"></a><span data-ttu-id="a0f3b-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a0f3b-138">See also</span></span>

- [<span data-ttu-id="a0f3b-139">Připojení ke zdroji dat</span><span class="sxs-lookup"><span data-stu-id="a0f3b-139">Connecting to a Data Source</span></span>](/cpp/data/odbc/connecting-to-a-data-source)
- [<span data-ttu-id="a0f3b-140">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="a0f3b-140">ADO.NET Overview</span></span>](ado-net-overview.md)
