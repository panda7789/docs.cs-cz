---
title: Připojovací řetězce
description: Přečtěte si o připojovacích řetězcích v ADO.NET, které obsahují inicializační informace předané jako parametr od poskytovatele dat ke zdroji dat.
ms.date: 10/10/2018
ms.assetid: 745c5f95-2f02-4674-b378-6d51a7ec2490
ms.openlocfilehash: baa6599a532746895cbb3920f2c623dd4c2be864
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287022"
---
# <a name="connection-strings-in-adonet"></a><span data-ttu-id="0d6df-103">Připojovací řetězce v ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0d6df-103">Connection Strings in ADO.NET</span></span>

<span data-ttu-id="0d6df-104">Připojovací řetězec obsahuje inicializační informace, které jsou předány jako parametr od poskytovatele dat ke zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="0d6df-104">A connection string contains initialization information that is passed as a parameter from a data provider to a data source.</span></span> <span data-ttu-id="0d6df-105">Zprostředkovatel dat přijímá připojovací řetězec jako hodnotu <xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="0d6df-105">The data provider receives the connection string as the value of the <xref:System.Data.Common.DbConnection.ConnectionString?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="0d6df-106">Zprostředkovatel analyzuje připojovací řetězec a ověří, zda je syntaxe správná a zda jsou klíčová slova podporována.</span><span class="sxs-lookup"><span data-stu-id="0d6df-106">The provider parses the connection string and ensures that the syntax is correct and that the keywords are supported.</span></span> <span data-ttu-id="0d6df-107">Pak <xref:System.Data.Common.DbConnection.Open?displayProperty=nameWithType> Metoda předá analyzovaným parametrům připojení ke zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="0d6df-107">Then the <xref:System.Data.Common.DbConnection.Open?displayProperty=nameWithType> method passes the parsed connection parameters to the data source.</span></span> <span data-ttu-id="0d6df-108">Zdroj dat provádí další ověření a naváže připojení.</span><span class="sxs-lookup"><span data-stu-id="0d6df-108">The data source performs further validation and establishes a connection.</span></span>

## <a name="connection-string-syntax"></a><span data-ttu-id="0d6df-109">Syntaxe připojovacího řetězce</span><span class="sxs-lookup"><span data-stu-id="0d6df-109">Connection string syntax</span></span>

<span data-ttu-id="0d6df-110">Připojovací řetězec je seznam dvojic parametrů klíč/hodnota oddělených středníkem:</span><span class="sxs-lookup"><span data-stu-id="0d6df-110">A connection string is a semicolon-delimited list of key/value parameter pairs:</span></span>

```csharp
keyword1=value; keyword2=value;
```

<span data-ttu-id="0d6df-111">V klíčových slovech se nerozlišují malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="0d6df-111">Keywords are not case-sensitive.</span></span> <span data-ttu-id="0d6df-112">V závislosti na zdroji dat ale můžou v nich být rozlišována velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="0d6df-112">Values, however, may be case-sensitive, depending on the data source.</span></span> <span data-ttu-id="0d6df-113">Klíčová slova a hodnoty mohou obsahovat [prázdné znaky](https://en.wikipedia.org/wiki/Whitespace_character#Unicode).</span><span class="sxs-lookup"><span data-stu-id="0d6df-113">Both keywords and values may contain [whitespace characters](https://en.wikipedia.org/wiki/Whitespace_character#Unicode).</span></span> <span data-ttu-id="0d6df-114">Úvodní a koncové prázdné znaky jsou ignorovány v klíčových slovech a hodnotách v uvozovkách.</span><span class="sxs-lookup"><span data-stu-id="0d6df-114">Leading and trailing white space is ignored in keywords and unquoted values.</span></span>

<span data-ttu-id="0d6df-115">Pokud hodnota obsahuje středník, [řídicí znaky sady Unicode](https://en.wikipedia.org/wiki/Unicode_control_characters)nebo úvodní nebo koncové prázdné znaky, musí být uzavřeny v jednoduchých nebo dvojitých uvozovkách.</span><span class="sxs-lookup"><span data-stu-id="0d6df-115">If a value contains the semicolon, [Unicode control characters](https://en.wikipedia.org/wiki/Unicode_control_characters), or leading or trailing white space, it must be enclosed in single or double quotation marks.</span></span> <span data-ttu-id="0d6df-116">Například:</span><span class="sxs-lookup"><span data-stu-id="0d6df-116">For example:</span></span>

```csharp
Keyword=" whitespace  ";
Keyword='special;character';
```

<span data-ttu-id="0d6df-117">Ohraničující znak se nesmí nacházet v rámci hodnoty, kterou obklopuje.</span><span class="sxs-lookup"><span data-stu-id="0d6df-117">The enclosing character may not occur within the value it encloses.</span></span> <span data-ttu-id="0d6df-118">Proto lze hodnotu obsahující jednoduché uvozovky uzavřít pouze do dvojitých uvozovek a naopak:</span><span class="sxs-lookup"><span data-stu-id="0d6df-118">Therefore, a value containing single quotation marks can be enclosed only in double quotation marks, and vice versa:</span></span>

```csharp
Keyword='double"quotation;mark';
Keyword="single'quotation;mark";
```

<span data-ttu-id="0d6df-119">Ohraničující znak můžete také vložit pomocí dvou z nich dohromady:</span><span class="sxs-lookup"><span data-stu-id="0d6df-119">You can also escape the enclosing character by using two of them together:</span></span>

```csharp
Keyword="double""quotation";
Keyword='single''quotation';
```

<span data-ttu-id="0d6df-120">Citace samotné a stejně jako znaménko rovná se nevyžadují uvozovací znaky, takže jsou platné následující připojovací řetězce:</span><span class="sxs-lookup"><span data-stu-id="0d6df-120">The quotation marks themselves, as well as the equals sign, do not require escaping, so the following connection strings are valid:</span></span>

```csharp
Keyword=no "escaping" 'required';
Keyword=a=b=c
```

<span data-ttu-id="0d6df-121">Vzhledem k tomu, že každá hodnota je čtena do následujícího středníku nebo konce řetězce, hodnota v druhém příkladu je `a=b=c` a poslední středník je nepovinný.</span><span class="sxs-lookup"><span data-stu-id="0d6df-121">Since each value is read till the next semicolon or the end of string, the value in the latter example is `a=b=c`, and the final semicolon is optional.</span></span>

<span data-ttu-id="0d6df-122">Všechny připojovací řetězce sdílejí stejnou základní syntaxi popsanou výše.</span><span class="sxs-lookup"><span data-stu-id="0d6df-122">All connection strings share the same basic syntax described above.</span></span> <span data-ttu-id="0d6df-123">Sada rozpoznaných klíčových slov závisí na poskytovateli, ale na těchto letech se vyvinula z dřívějších rozhraní API, jako je například *ODBC*.</span><span class="sxs-lookup"><span data-stu-id="0d6df-123">The set of recognized keywords depends on the provider, however, and has evolved over the years from earlier APIs such as *ODBC*.</span></span> <span data-ttu-id="0d6df-124">Zprostředkovatel dat *.NET Framework* pro *SQL Server* ( `SqlClient` ) podporuje mnoho klíčových slov ze starších rozhraní API, ale je obecně flexibilnější a přijímá synonyma pro mnoho běžných klíčových slov řetězce připojení.</span><span class="sxs-lookup"><span data-stu-id="0d6df-124">The *.NET Framework* data provider for *SQL Server* (`SqlClient`) supports many keywords from older APIs, but is generally more flexible and accepts synonyms for many of the common connection string keywords.</span></span>

<span data-ttu-id="0d6df-125">Psaní chyb může způsobit chyby.</span><span class="sxs-lookup"><span data-stu-id="0d6df-125">Typing mistakes can cause errors.</span></span> <span data-ttu-id="0d6df-126">Například `Integrated Security=true` je platný, ale `IntegratedSecurity=true` způsobí chybu.</span><span class="sxs-lookup"><span data-stu-id="0d6df-126">For example, `Integrated Security=true` is valid, but `IntegratedSecurity=true` causes an error.</span></span>

<span data-ttu-id="0d6df-127">Připojovací řetězce konstruované ručně v době spuštění z neověřeného vstupu uživatele jsou zranitelné vůči útokům prostřednictvím injektáže řetězce a ohrožení zabezpečení ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="0d6df-127">Connection strings constructed manually at run time from unvalidated user input are vulnerable to string-injection attacks and jeopardize security at the data source.</span></span> <span data-ttu-id="0d6df-128">Pro řešení těchto problémů zavedlo *ADO.NET* 2,0 [tvůrci připojovacích řetězců](connection-string-builders.md) pro každého poskytovatele dat *.NET Framework* .</span><span class="sxs-lookup"><span data-stu-id="0d6df-128">To address these problems, *ADO.NET* 2.0 introduced [connection string builders](connection-string-builders.md) for each *.NET Framework* data provider.</span></span> <span data-ttu-id="0d6df-129">Tyto tvůrci připojovacích řetězců zpřístupňují parametry jako vlastnosti silného typu a umožňují ověření připojovacího řetězce před jeho odesláním do zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="0d6df-129">These connection string builders expose parameters as strongly typed properties, and make it possible to validate the connection string before it's sent to the data source.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="0d6df-130">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="0d6df-130">In This Section</span></span>

<span data-ttu-id="0d6df-131">[Tvůrci připojovacích řetězců](connection-string-builders.md)</span><span class="sxs-lookup"><span data-stu-id="0d6df-131">[Connection String Builders](connection-string-builders.md)</span></span>\
<span data-ttu-id="0d6df-132">Ukazuje, jak použít `ConnectionStringBuilder` třídy pro vytvoření platných připojovacích řetězců za běhu.</span><span class="sxs-lookup"><span data-stu-id="0d6df-132">Demonstrates how to use the `ConnectionStringBuilder` classes to construct valid connection strings at run time.</span></span>

<span data-ttu-id="0d6df-133">[Připojovací řetězce a konfigurační soubory](connection-strings-and-configuration-files.md)</span><span class="sxs-lookup"><span data-stu-id="0d6df-133">[Connection Strings and Configuration Files](connection-strings-and-configuration-files.md)</span></span>\
<span data-ttu-id="0d6df-134">Ukazuje, jak ukládat a načítat připojovací řetězce v konfiguračních souborech.</span><span class="sxs-lookup"><span data-stu-id="0d6df-134">Demonstrates how to store and retrieve connection strings in configuration files.</span></span>

<span data-ttu-id="0d6df-135">[Syntaxe připojovacího řetězce](connection-string-syntax.md)</span><span class="sxs-lookup"><span data-stu-id="0d6df-135">[Connection String Syntax](connection-string-syntax.md)</span></span>\
<span data-ttu-id="0d6df-136">Popisuje postup konfigurace připojovacích řetězců specifických pro konkrétní poskytovatele pro `SqlClient` , `OracleClient` , `OleDb` a `Odbc` .</span><span class="sxs-lookup"><span data-stu-id="0d6df-136">Describes how to configure provider-specific connection strings for `SqlClient`, `OracleClient`, `OleDb`, and `Odbc`.</span></span>

<span data-ttu-id="0d6df-137">[Ochrana informací o připojení](protecting-connection-information.md)</span><span class="sxs-lookup"><span data-stu-id="0d6df-137">[Protecting Connection Information](protecting-connection-information.md)</span></span>\
<span data-ttu-id="0d6df-138">Ukazuje techniky ochrany informací používaných pro připojení ke zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="0d6df-138">Demonstrates techniques for protecting information used to connect to a data source.</span></span>

## <a name="see-also"></a><span data-ttu-id="0d6df-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="0d6df-139">See also</span></span>

- [<span data-ttu-id="0d6df-140">Připojení ke zdroji dat</span><span class="sxs-lookup"><span data-stu-id="0d6df-140">Connecting to a Data Source</span></span>](/cpp/data/odbc/connecting-to-a-data-source)
- [<span data-ttu-id="0d6df-141">Přehled ADO.NET</span><span class="sxs-lookup"><span data-stu-id="0d6df-141">ADO.NET Overview</span></span>](ado-net-overview.md)
