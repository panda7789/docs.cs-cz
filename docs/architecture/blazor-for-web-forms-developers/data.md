---
title: Přístup k datům a jejich správa
description: Naučte se, jak přistupovat k datům ve webových formulářích ASP.NET a pracovat s nimi Blazor .
author: csharpfritz
ms.author: jefritz
no-loc:
- Blazor
ms.date: 04/26/2020
ms.openlocfilehash: 4bf9bee21ce1db828dbe0aeb156d5e15cae4f703
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86173301"
---
# <a name="work-with-data"></a><span data-ttu-id="04400-103">Práce s daty</span><span class="sxs-lookup"><span data-stu-id="04400-103">Work with data</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="04400-104">Přístup k datům je páteř aplikace ASP.NET Web Forms.</span><span class="sxs-lookup"><span data-stu-id="04400-104">Data access is the backbone of an ASP.NET Web Forms app.</span></span> <span data-ttu-id="04400-105">Pokud vytváříte formuláře pro web, co se stane s těmito daty?</span><span class="sxs-lookup"><span data-stu-id="04400-105">If you're building forms for the web, what happens to that data?</span></span> <span data-ttu-id="04400-106">S webovými formuláři byly k dispozici různé techniky přístupu k datům, které byste mohli použít k interakci s databází:</span><span class="sxs-lookup"><span data-stu-id="04400-106">With Web Forms, there were multiple data access techniques you could use to interact with a database:</span></span>

- <span data-ttu-id="04400-107">Zdroje dat</span><span class="sxs-lookup"><span data-stu-id="04400-107">Data Sources</span></span>
- <span data-ttu-id="04400-108">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="04400-108">ADO.NET</span></span>
- <span data-ttu-id="04400-109">Entity Framework</span><span class="sxs-lookup"><span data-stu-id="04400-109">Entity Framework</span></span>

<span data-ttu-id="04400-110">Zdroje dat byly ovládací prvky, které by mohly být umístěny na stránce webového formuláře a nakonfigurované podobně jako jiné ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="04400-110">Data Sources were controls that you could place on a Web Forms page and configure like other controls.</span></span> <span data-ttu-id="04400-111">Sada Visual Studio poskytla uživatelsky přívětivou sadu dialogových oken pro konfiguraci a vázání ovládacích prvků na stránky webových formulářů.</span><span class="sxs-lookup"><span data-stu-id="04400-111">Visual Studio provided a friendly set of dialogs to configure and bind the controls to your Web Forms pages.</span></span> <span data-ttu-id="04400-112">Vývojáři, kteří při prvním vydání webových formulářů upřednostňují přístup "s nízkým kódem" nebo "bez kódu", mají přednost před touto technikí.</span><span class="sxs-lookup"><span data-stu-id="04400-112">Developers who enjoy a "low code" or "no code" approach preferred this technique when Web Forms was first released.</span></span>

![Zdroje dat](media/data/datasources.png)

<span data-ttu-id="04400-114">ADO.NET je přístup nízké úrovně k interakci s databází.</span><span class="sxs-lookup"><span data-stu-id="04400-114">ADO.NET is the low-level approach to interacting with a database.</span></span> <span data-ttu-id="04400-115">Vaše aplikace by mohly vytvořit připojení k databázi pomocí příkazů, sad záznamů a datových sad pro interakci.</span><span class="sxs-lookup"><span data-stu-id="04400-115">Your apps could create a connection to the database with Commands, Recordsets, and Datasets for interacting.</span></span> <span data-ttu-id="04400-116">Výsledky pak mohou být vázány na pole na obrazovce bez velkého množství kódu.</span><span class="sxs-lookup"><span data-stu-id="04400-116">The results could then be bound to fields on screen without much code.</span></span> <span data-ttu-id="04400-117">Nevýhodou tohoto přístupu bylo, že každá sada objektů ADO.NET ( `Connection` , a `Command` `Recordset` ) byla svázána s knihovnami poskytnutými dodavatelem databáze.</span><span class="sxs-lookup"><span data-stu-id="04400-117">The drawback of this approach was that each set of ADO.NET objects (`Connection`, `Command`, and `Recordset`) was bound to libraries provided by a database vendor.</span></span> <span data-ttu-id="04400-118">Použití těchto komponent vede k pevnému a obtížnému migraci kódu do jiné databáze.</span><span class="sxs-lookup"><span data-stu-id="04400-118">Use of these components made the code rigid and difficult to migrate to a different database.</span></span>

## <a name="entity-framework"></a><span data-ttu-id="04400-119">Entity Framework</span><span class="sxs-lookup"><span data-stu-id="04400-119">Entity Framework</span></span>

<span data-ttu-id="04400-120">Entity Framework (EF) je open source objekt – relační mapování udržované rozhraním .NET Foundation.</span><span class="sxs-lookup"><span data-stu-id="04400-120">Entity Framework (EF) is the open source object-relational mapping framework maintained by the .NET Foundation.</span></span> <span data-ttu-id="04400-121">Původně vydaná s .NET Framework, EF umožňuje generování kódu pro databázová připojení, schémata úložišť a interakce.</span><span class="sxs-lookup"><span data-stu-id="04400-121">Initially released with .NET Framework, EF allows for generating code for the database connections, storage schemas, and interactions.</span></span> <span data-ttu-id="04400-122">V této abstrakci se můžete soustředit na obchodní pravidla vaší aplikace a nechat databázi spravovat správcem důvěryhodné databáze.</span><span class="sxs-lookup"><span data-stu-id="04400-122">With this abstraction, you can focus on your app's business rules and allow the database to be managed by a trusted database administrator.</span></span> <span data-ttu-id="04400-123">V rozhraní .NET Core můžete použít aktualizovanou verzi EF s názvem EF Core.</span><span class="sxs-lookup"><span data-stu-id="04400-123">In .NET Core, you can use an updated version of EF called EF Core.</span></span> <span data-ttu-id="04400-124">EF Core pomáhá generovat a udržovat interakce mezi kódem a databází pomocí řady příkazů, které jsou k dispozici pro vás pomocí `dotnet ef` nástroje příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="04400-124">EF Core helps generate and maintain the interactions between your code and the database with a series of commands that are available for you using the `dotnet ef` command-line tool.</span></span> <span data-ttu-id="04400-125">Pojďme se podívat na několik ukázek, které vám pomůžou pracovat s databází.</span><span class="sxs-lookup"><span data-stu-id="04400-125">Let's take a look at a few samples to get you working with a database.</span></span>

### <a name="ef-code-first"></a><span data-ttu-id="04400-126">EF Code First</span><span class="sxs-lookup"><span data-stu-id="04400-126">EF Code First</span></span>

<span data-ttu-id="04400-127">Rychlý způsob, jak začít sestavovat interakce s databází, je začít s objekty třídy, se kterými chcete pracovat.</span><span class="sxs-lookup"><span data-stu-id="04400-127">A quick way to get started building your database interactions is to start with the class objects you want to work with.</span></span> <span data-ttu-id="04400-128">EF poskytuje nástroj, který usnadňuje generování vhodného kódu databáze pro vaše třídy.</span><span class="sxs-lookup"><span data-stu-id="04400-128">EF provides a tool to help generate the appropriate database code for your classes.</span></span> <span data-ttu-id="04400-129">Tento přístup se nazývá vývoj "Code First".</span><span class="sxs-lookup"><span data-stu-id="04400-129">This approach is called "Code First" development.</span></span> <span data-ttu-id="04400-130">Podívejte se na následující `Product` třídu pro ukázkovou aplikaci prezentace, kterou chceme uložit v relační databázi, jako je Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="04400-130">Consider the following `Product` class for a sample storefront app that we want to store in a relational database like Microsoft SQL Server.</span></span>

```csharp
public class Product
{
    public int Id { get; set; }

    [Required]
    public string Name { get; set; }

    [MaxLength(4000)]
    public string Description { get; set; }

    [Range(0, 99999,99)]
    [DataType(DataType.Currency)]
    public decimal Price { get; set; }
}
```

<span data-ttu-id="04400-131">Produkt má primární klíč a tři další pole, která by se vytvořila v naší databázi:</span><span class="sxs-lookup"><span data-stu-id="04400-131">Product has a primary key and three additional fields that would be created in our database:</span></span>  

- <span data-ttu-id="04400-132">EF identifikuje `Id` vlastnost jako primární klíč podle konvence.</span><span class="sxs-lookup"><span data-stu-id="04400-132">EF will identify the `Id` property as a primary key by convention.</span></span>
- <span data-ttu-id="04400-133">`Name`budou uloženy ve sloupci nakonfigurovaném pro textové úložiště.</span><span class="sxs-lookup"><span data-stu-id="04400-133">`Name` will be stored in a column configured for text storage.</span></span> <span data-ttu-id="04400-134">`[Required]`Atribut upravení touto vlastností přidá `not null` omezení, které pomůže vynutilit toto deklarované chování vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="04400-134">The `[Required]` attribute decorating this property will add a `not null` constraint to help enforce this declared behavior of the property.</span></span>
- <span data-ttu-id="04400-135">`Description`uloží se do sloupce nakonfigurovaného pro textové úložiště a maximální povolená délka je 4000 znaků, jak je Určuje `[MaxLength]` atributem.</span><span class="sxs-lookup"><span data-stu-id="04400-135">`Description` will be stored in a column configured for text storage, and have a maximum length configured of 4000 characters as dictated by the `[MaxLength]` attribute.</span></span> <span data-ttu-id="04400-136">Schéma databáze bude nakonfigurován se sloupcem s názvem s `MaxLength` použitím datového typu `varchar(4000)` .</span><span class="sxs-lookup"><span data-stu-id="04400-136">The database schema will be configured with a column named `MaxLength` using data type `varchar(4000)`.</span></span>
- <span data-ttu-id="04400-137">`Price`Vlastnost bude uložena jako měna.</span><span class="sxs-lookup"><span data-stu-id="04400-137">The `Price` property will be stored as currency.</span></span> <span data-ttu-id="04400-138">`[Range]`Atribut vygeneruje vhodná omezení, aby nedocházelo k ukládání dat mimo minimální a maximální deklarované hodnoty.</span><span class="sxs-lookup"><span data-stu-id="04400-138">The `[Range]` attribute will generate appropriate constraints to prevent data storage outside of the minimum and maximum values declared.</span></span>

<span data-ttu-id="04400-139">Musíme tuto `Product` třídu přidat do třídy kontextu databáze definující operace připojení a překladu s naší databází.</span><span class="sxs-lookup"><span data-stu-id="04400-139">We need to add this `Product` class to a database context class that defines the connection and translation operations with our database.</span></span>

```csharp
public class MyDbContext : DbContext
{
    public DbSet<Product> Products { get; set; }
}
```

<span data-ttu-id="04400-140">`MyDbContext`Třída poskytuje jednu vlastnost, která definuje přístup a překlad pro `Product` třídu.</span><span class="sxs-lookup"><span data-stu-id="04400-140">The `MyDbContext` class provides the one property that defines the access and translation for the `Product` class.</span></span>  <span data-ttu-id="04400-141">Vaše aplikace konfiguruje tuto třídu pro interakci s databází pomocí následujících záznamů v `Startup` `ConfigureServices` metodě třídy:</span><span class="sxs-lookup"><span data-stu-id="04400-141">Your application configures this class for interaction with the database using the following entries in the `Startup` class's `ConfigureServices` method:</span></span>

```csharp
services.AddDbContext<MyDbContext>(options =>
    options.UseSqlServer("MY DATABASE CONNECTION STRING"));
```

<span data-ttu-id="04400-142">Předchozí kód se připojí k databázi SQL Server se zadaným připojovacím řetězcem.</span><span class="sxs-lookup"><span data-stu-id="04400-142">The preceding code will connect to a SQL Server database with the specified connection string.</span></span> <span data-ttu-id="04400-143">Připojovací řetězec můžete umístit do *appsettings.js* do souboru, proměnných prostředí nebo jiných umístění úložiště konfigurace a odpovídajícím způsobem nahradit tento vložený řetězec.</span><span class="sxs-lookup"><span data-stu-id="04400-143">You can place the connection string in your *appsettings.json* file, environment variables, or other configuration storage locations and replace this embedded string appropriately.</span></span>

<span data-ttu-id="04400-144">Pak můžete vygenerovat databázovou tabulku, která je vhodná pro tuto třídu, pomocí následujících příkazů:</span><span class="sxs-lookup"><span data-stu-id="04400-144">You can then generate the database table appropriate for this class using the following commands:</span></span>

```dotnetcli
dotnet ef migrations add 'Create Product table'
dotnet ef database update
```

<span data-ttu-id="04400-145">První příkaz definuje změny, které provádíte ve schématu databáze, jako novou migraci EF `Create Product table` .</span><span class="sxs-lookup"><span data-stu-id="04400-145">The first command defines the changes you're making to the database schema as a new EF Migration called `Create Product table`.</span></span>  <span data-ttu-id="04400-146">Migrace definuje, jak použít a odebrat nové změny databáze.</span><span class="sxs-lookup"><span data-stu-id="04400-146">A Migration defines how to apply and remove your new database changes.</span></span>

<span data-ttu-id="04400-147">Po použití máte `Product` v databázi jednoduchou tabulku a některé nové třídy přidané do projektu, které vám pomůžou se správou schématu databáze.</span><span class="sxs-lookup"><span data-stu-id="04400-147">Once applied, you have a simple `Product` table in your database and some new classes added to the project that help manage the database schema.</span></span>  <span data-ttu-id="04400-148">Tyto vygenerované třídy můžete ve výchozím nastavení najít v nové složce s názvem *migrace*.</span><span class="sxs-lookup"><span data-stu-id="04400-148">You can find these generated classes, by default, in a new folder called *Migrations*.</span></span>  <span data-ttu-id="04400-149">Když provedete změny ve `Product` třídě nebo přidáte další související třídy, které byste chtěli interaktivně pracovat s databází, je nutné znovu spustit příkazy příkazového řádku s novým názvem migrace.</span><span class="sxs-lookup"><span data-stu-id="04400-149">When you make changes to the `Product` class or add more related classes you would like interacting with your database, you need to run the command-line commands again with a new name of the migration.</span></span>  <span data-ttu-id="04400-150">Tento příkaz vygeneruje další sadu tříd migrace pro aktualizaci schématu databáze.</span><span class="sxs-lookup"><span data-stu-id="04400-150">This command will generate another set of migration classes to update your database schema.</span></span>

### <a name="ef-database-first"></a><span data-ttu-id="04400-151">EF Database First</span><span class="sxs-lookup"><span data-stu-id="04400-151">EF Database First</span></span>

<span data-ttu-id="04400-152">Pro existující databáze můžete vygenerovat třídy pro EF Core pomocí nástrojů příkazového řádku .NET.</span><span class="sxs-lookup"><span data-stu-id="04400-152">For existing databases, you can generate the classes for EF Core by using the .NET command-line tools.</span></span> <span data-ttu-id="04400-153">K vytvoření uživatelského rozhraní tříd použijte variaci následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="04400-153">To scaffold the classes, use a variation of the following command:</span></span>

```dotnetcli
dotnet ef dbcontext scaffold "CONNECTION STRING" Microsoft.EntityFrameworkCore.SqlServer -c MyDbContext -t Product -t Customer
```

<span data-ttu-id="04400-154">Předchozí příkaz se připojí k databázi pomocí zadaného připojovacího řetězce a `Microsoft.EntityFrameworkCore.SqlServer` poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="04400-154">The preceding command connects to the database using the specified connection string and the `Microsoft.EntityFrameworkCore.SqlServer` provider.</span></span> <span data-ttu-id="04400-155">Po připojení se vytvoří třída kontextu databáze s názvem `MyDbContext` .</span><span class="sxs-lookup"><span data-stu-id="04400-155">Once connected, a database context class named `MyDbContext` is created.</span></span> <span data-ttu-id="04400-156">Kromě toho jsou vytvořeny podpůrné třídy pro `Product` tabulky a `Customer` , které byly zadány s `-t` možnostmi.</span><span class="sxs-lookup"><span data-stu-id="04400-156">Additionally, supporting classes are created for the `Product` and `Customer` tables that were specified with the `-t` options.</span></span> <span data-ttu-id="04400-157">Pro tento příkaz existuje mnoho možností konfigurace, které vygenerují hierarchii tříd vhodnou pro vaši databázi.</span><span class="sxs-lookup"><span data-stu-id="04400-157">There are many configuration options for this command to generate the class hierarchy appropriate for your database.</span></span> <span data-ttu-id="04400-158">Úplný odkaz naleznete v dokumentaci k [příkazu](/ef/core/miscellaneous/cli/dotnet#dotnet-ef-dbcontext-scaffold).</span><span class="sxs-lookup"><span data-stu-id="04400-158">For a complete reference, see [the command's documentation](/ef/core/miscellaneous/cli/dotnet#dotnet-ef-dbcontext-scaffold).</span></span>

<span data-ttu-id="04400-159">Další informace o [EF Core](/ef/core/) najdete na webu Microsoft docs.</span><span class="sxs-lookup"><span data-stu-id="04400-159">More information about [EF Core](/ef/core/) can be found on the Microsoft Docs site.</span></span>

## <a name="interact-with-web-services"></a><span data-ttu-id="04400-160">Interakce s webovými službami</span><span class="sxs-lookup"><span data-stu-id="04400-160">Interact with web services</span></span>

<span data-ttu-id="04400-161">Při prvním vydání ASP.NET byly upřednostňovaným způsobem služby SOAP pro webové servery a klienty vyměňovat data.</span><span class="sxs-lookup"><span data-stu-id="04400-161">When ASP.NET was first released, SOAP services were the preferred way for web servers and clients to exchange data.</span></span> <span data-ttu-id="04400-162">Většina se od té doby změnila a preferované interakce se službami se posunuly na přímé interakce klienta HTTP.</span><span class="sxs-lookup"><span data-stu-id="04400-162">Much has changed since that time, and the preferred interactions with services have shifted to direct HTTP client interactions.</span></span> <span data-ttu-id="04400-163">Pomocí ASP.NET Core a Blazor můžete zaregistrovat konfiguraci `HttpClient` v `Startup` `ConfigureServices` metodě třídy.</span><span class="sxs-lookup"><span data-stu-id="04400-163">With ASP.NET Core and Blazor, you can register the configuration of your `HttpClient` in the `Startup` class's `ConfigureServices` method.</span></span> <span data-ttu-id="04400-164">Tuto konfiguraci použijte v případě, že potřebujete pracovat s koncovým bodem HTTP.</span><span class="sxs-lookup"><span data-stu-id="04400-164">Use that configuration when you need to interact with the HTTP endpoint.</span></span> <span data-ttu-id="04400-165">Vezměte v úvahu následující konfigurační kód:</span><span class="sxs-lookup"><span data-stu-id="04400-165">Consider the following configuration code:</span></span>

```csharp
services.AddHttpClient("github", client =>
{
    client.BaseAddress = new Uri("http://api.github.com/");
    // Github API versioning
    client.DefaultRequestHeaders.Add("Accept", "application/vnd.github.v3+json");
    // Github requires a user-agent
    client.DefaultRequestHeaders.Add("User-Agent", "BlazorWebForms-Sample");
});
```

<span data-ttu-id="04400-166">Kdykoli potřebujete přístup k datům z GitHubu, vytvořte klienta s názvem `github` .</span><span class="sxs-lookup"><span data-stu-id="04400-166">Whenever you need to access data from GitHub, create a client with a name of `github`.</span></span> <span data-ttu-id="04400-167">Klient je nakonfigurován se základní adresou a hlavičky požadavku jsou nastaveny odpovídajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="04400-167">The client is configured with the base address, and the request headers are set appropriately.</span></span> <span data-ttu-id="04400-168">Zapněte `IHttpClientFactory` do svých Blazor komponent pomocí `@inject` direktivy nebo `[Inject]` atributu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="04400-168">Inject the `IHttpClientFactory` into your Blazor components with the `@inject` directive or an `[Inject]` attribute on a property.</span></span> <span data-ttu-id="04400-169">Vytvořte svého pojmenovaného klienta a v interakci se službami použijte následující syntaxi:</span><span class="sxs-lookup"><span data-stu-id="04400-169">Create your named client and interact with services using the following syntax:</span></span>

```razor
@inject IHttpClientFactory factory

...

@code {
    protected override async Task OnInitializedAsync()
    {
        var client = factory.CreateClient("github");
        var response = await client.GetAsync("repos/dotnet/docs/issues");
        response.EnsureStatusCode();
        var content = async response.Content.ReadAsStringAsync();
    }
}
```

<span data-ttu-id="04400-170">Tato metoda vrátí řetězec popisující kolekci problémů v úložišti *dotnet/docs* GitHub.</span><span class="sxs-lookup"><span data-stu-id="04400-170">This method returns the string describing the collection of issues in the *dotnet/docs* GitHub repository.</span></span> <span data-ttu-id="04400-171">Vrátí obsah ve formátu JSON a deserializace do odpovídajících objektů problémů GitHubu.</span><span class="sxs-lookup"><span data-stu-id="04400-171">It returns content in JSON format and is deserialized into appropriate GitHub issue objects.</span></span> <span data-ttu-id="04400-172">Existuje mnoho způsobů, jak můžete nakonfigurovat, `HttpClientFactory` aby poskytovaly předem nakonfigurované `HttpClient` objekty.</span><span class="sxs-lookup"><span data-stu-id="04400-172">There are many ways that you can configure the `HttpClientFactory` to deliver preconfigured `HttpClient` objects.</span></span> <span data-ttu-id="04400-173">Zkuste nakonfigurovat více `HttpClient` instancí s různými názvy a koncovými body pro různé webové služby, se kterými pracujete.</span><span class="sxs-lookup"><span data-stu-id="04400-173">Try configuring multiple `HttpClient` instances with different names and endpoints for the various web services you work with.</span></span> <span data-ttu-id="04400-174">Tento přístup usnadňuje práci s těmito službami na každé stránce.</span><span class="sxs-lookup"><span data-stu-id="04400-174">This approach will make your interactions with those services easier to work with on each page.</span></span> <span data-ttu-id="04400-175">Další podrobnosti najdete v [dokumentaci k IHttpClientFactory](/aspnet/core/fundamentals/http-requests).</span><span class="sxs-lookup"><span data-stu-id="04400-175">For more details, read [the documentation for the IHttpClientFactory](/aspnet/core/fundamentals/http-requests).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="04400-176">[Předchozí](forms-validation.md) 
> [Další](middleware.md)</span><span class="sxs-lookup"><span data-stu-id="04400-176">[Previous](forms-validation.md)
[Next](middleware.md)</span></span>
