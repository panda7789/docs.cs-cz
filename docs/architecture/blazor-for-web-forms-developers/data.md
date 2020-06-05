---
title: Přístup k datům a jejich správa
description: Naučte se, jak přistupovat k datům ve webových formulářích ASP.NET a Blazor a zpracovávat je.
author: csharpfritz
ms.author: jefritz
ms.date: 04/26/2020
ms.openlocfilehash: b9805da60722de1b5d4f91107e856f647f7564a7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/05/2020
ms.locfileid: "84446470"
---
# <a name="work-with-data"></a>Práce s daty

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Přístup k datům je páteř aplikace ASP.NET Web Forms. Pokud vytváříte formuláře pro web, co se stane s těmito daty? S webovými formuláři byly k dispozici různé techniky přístupu k datům, které byste mohli použít k interakci s databází:

- Zdroje dat
- ADO.NET
- Entity Framework

Zdroje dat byly ovládací prvky, které by mohly být umístěny na stránce webového formuláře a nakonfigurované podobně jako jiné ovládací prvky. Sada Visual Studio poskytla uživatelsky přívětivou sadu dialogových oken pro konfiguraci a vázání ovládacích prvků na stránky webových formulářů. Vývojáři, kteří při prvním vydání webových formulářů upřednostňují přístup "s nízkým kódem" nebo "bez kódu", mají přednost před touto technikí.

![Zdroje dat](media/data/datasources.png)

ADO.NET je přístup nízké úrovně k interakci s databází. Vaše aplikace by mohly vytvořit připojení k databázi pomocí příkazů, sad záznamů a datových sad pro interakci. Výsledky pak mohou být vázány na pole na obrazovce bez velkého množství kódu. Nevýhodou tohoto přístupu bylo, že každá sada objektů ADO.NET ( `Connection` , a `Command` `Recordset` ) byla svázána s knihovnami poskytnutými dodavatelem databáze. Použití těchto komponent vede k pevnému a obtížnému migraci kódu do jiné databáze.

## <a name="entity-framework"></a>Entity Framework

Entity Framework (EF) je open source objekt – relační mapování udržované rozhraním .NET Foundation. Původně vydaná s .NET Framework, EF umožňuje generování kódu pro databázová připojení, schémata úložišť a interakce. V této abstrakci se můžete soustředit na obchodní pravidla vaší aplikace a nechat databázi spravovat správcem důvěryhodné databáze. V rozhraní .NET Core můžete použít aktualizovanou verzi EF s názvem EF Core. EF Core pomáhá generovat a udržovat interakce mezi kódem a databází pomocí řady příkazů, které jsou k dispozici pro vás pomocí `dotnet ef` nástroje příkazového řádku. Pojďme se podívat na několik ukázek, které vám pomůžou pracovat s databází.

### <a name="ef-code-first"></a>EF Code First

Rychlý způsob, jak začít sestavovat interakce s databází, je začít s objekty třídy, se kterými chcete pracovat. EF poskytuje nástroj, který usnadňuje generování vhodného kódu databáze pro vaše třídy. Tento přístup se nazývá vývoj "Code First". Podívejte se na následující `Product` třídu pro ukázkovou aplikaci prezentace, kterou chceme uložit v relační databázi, jako je Microsoft SQL Server.

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

Produkt má primární klíč a tři další pole, která by se vytvořila v naší databázi:  

- EF identifikuje `Id` vlastnost jako primární klíč podle konvence.
- `Name`budou uloženy ve sloupci nakonfigurovaném pro textové úložiště. `[Required]`Atribut upravení touto vlastností přidá `not null` omezení, které pomůže vynutilit toto deklarované chování vlastnosti.
- `Description`uloží se do sloupce nakonfigurovaného pro textové úložiště a maximální povolená délka je 4000 znaků, jak je Určuje `[MaxLength]` atributem. Schéma databáze bude nakonfigurován se sloupcem s názvem s `MaxLength` použitím datového typu `varchar(4000)` .
- `Price`Vlastnost bude uložena jako měna. `[Range]`Atribut vygeneruje vhodná omezení, aby nedocházelo k ukládání dat mimo minimální a maximální deklarované hodnoty.

Musíme tuto `Product` třídu přidat do třídy kontextu databáze definující operace připojení a překladu s naší databází.

```csharp
public class MyDbContext : DbContext
{
    public DbSet<Product> Products { get; set; }
}
```

`MyDbContext`Třída poskytuje jednu vlastnost, která definuje přístup a překlad pro `Product` třídu.  Vaše aplikace konfiguruje tuto třídu pro interakci s databází pomocí následujících záznamů v `Startup` `ConfigureServices` metodě třídy:

```csharp
services.AddDbContext<MyDbContext>(options =>
    options.UseSqlServer("MY DATABASE CONNECTION STRING"));
```

Předchozí kód se připojí k databázi SQL Server se zadaným připojovacím řetězcem. Připojovací řetězec můžete umístit do souboru *appSettings. JSON* , proměnných prostředí nebo jiných umístění úložiště konfigurace a odpovídajícím způsobem nahradit tento vložený řetězec.

Pak můžete vygenerovat databázovou tabulku, která je vhodná pro tuto třídu, pomocí následujících příkazů:

```dotnetcli
dotnet ef migrations add 'Create Product table'
dotnet ef database update
```

První příkaz definuje změny, které provádíte ve schématu databáze, jako novou migraci EF `Create Product table` .  Migrace definuje, jak použít a odebrat nové změny databáze.

Po použití máte `Product` v databázi jednoduchou tabulku a některé nové třídy přidané do projektu, které vám pomůžou se správou schématu databáze.  Tyto vygenerované třídy můžete ve výchozím nastavení najít v nové složce s názvem *migrace*.  Když provedete změny ve `Product` třídě nebo přidáte další související třídy, které byste chtěli interaktivně pracovat s databází, je nutné znovu spustit příkazy příkazového řádku s novým názvem migrace.  Tento příkaz vygeneruje další sadu tříd migrace pro aktualizaci schématu databáze.

### <a name="ef-database-first"></a>EF Database First

Pro existující databáze můžete vygenerovat třídy pro EF Core pomocí nástrojů příkazového řádku .NET. K vytvoření uživatelského rozhraní tříd použijte variaci následujícího příkazu:

```dotnetcli
dotnet ef dbcontext scaffold "CONNECTION STRING" Microsoft.EntityFrameworkCore.SqlServer -c MyDbContext -t Product -t Customer
```

Předchozí příkaz se připojí k databázi pomocí zadaného připojovacího řetězce a `Microsoft.EntityFrameworkCore.SqlServer` poskytovatele. Po připojení se vytvoří třída kontextu databáze s názvem `MyDbContext` . Kromě toho jsou vytvořeny podpůrné třídy pro `Product` tabulky a `Customer` , které byly zadány s `-t` možnostmi. Pro tento příkaz existuje mnoho možností konfigurace, které vygenerují hierarchii tříd vhodnou pro vaši databázi. Úplný odkaz naleznete v dokumentaci k [příkazu](/ef/core/miscellaneous/cli/dotnet#dotnet-ef-dbcontext-scaffold).

Další informace o [EF Core](/ef/core/) najdete na webu Microsoft docs.

## <a name="interact-with-web-services"></a>Interakce s webovými službami

Při prvním vydání ASP.NET byly upřednostňovaným způsobem služby SOAP pro webové servery a klienty vyměňovat data. Většina se od té doby změnila a preferované interakce se službami se posunuly na přímé interakce klienta HTTP. Pomocí ASP.NET Core a Blazor můžete zaregistrovat konfiguraci `HttpClient` v `Startup` `ConfigureServices` metodě třídy. Tuto konfiguraci použijte v případě, že potřebujete pracovat s koncovým bodem HTTP. Vezměte v úvahu následující konfigurační kód:

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

Kdykoli potřebujete přístup k datům z GitHubu, vytvořte klienta s názvem `github` . Klient je nakonfigurován se základní adresou a hlavičky požadavku jsou nastaveny odpovídajícím způsobem. Zapněte `IHttpClientFactory` do komponent Blazor pomocí `@inject` direktivy nebo `[Inject]` atributu vlastnosti. Vytvořte svého pojmenovaného klienta a v interakci se službami použijte následující syntaxi:

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

Tato metoda vrátí řetězec popisující kolekci problémů v úložišti *dotnet/docs* GitHub. Vrátí obsah ve formátu JSON a deserializace do odpovídajících objektů problémů GitHubu. Existuje mnoho způsobů, jak můžete nakonfigurovat, `HttpClientFactory` aby poskytovaly předem nakonfigurované `HttpClient` objekty. Zkuste nakonfigurovat více `HttpClient` instancí s různými názvy a koncovými body pro různé webové služby, se kterými pracujete. Tento přístup usnadňuje práci s těmito službami na každé stránce. Další podrobnosti najdete v [dokumentaci k IHttpClientFactory](/aspnet/core/fundamentals/http-requests).

>[!div class="step-by-step"]
>[Předchozí](forms-validation.md) 
> [Další](middleware.md)
