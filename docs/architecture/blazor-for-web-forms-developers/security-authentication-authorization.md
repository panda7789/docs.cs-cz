---
title: 'Zabezpečení: ověřování a autorizace ve webových formulářích ASP.NET a Blazor'
description: Naučte se, jak zpracovávat ověřování a autorizaci ve webových formulářích ASP.NET a Blazor .
author: ardalis
ms.author: daroth
no-loc:
- Blazor
ms.date: 09/11/2019
ms.openlocfilehash: 1cc82b14a940465c26377f9181a2e20b46b0783f
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/17/2020
ms.locfileid: "88267827"
---
# <a name="security-authentication-and-authorization-in-aspnet-web-forms-and-no-locblazor"></a>Zabezpečení: ověřování a autorizace ve webových formulářích ASP.NET a Blazor

Migrace z aplikace webových formulářů ASP.NET na Blazor bude téměř určitě vyžadovat aktualizaci způsobu ověřování a autorizace za předpokladu, že aplikace má nakonfigurované ověřování. Tato kapitola popisuje, jak migrovat z modelu univerzálního poskytovatele webových formulářů ASP.NET (pro členství, role a profily uživatelů) a jak pracovat s ASP.NET Core identitou z Blazor aplikací. I když tato kapitola pokryje nejdůležitější kroky a požadavky, najdete v odkazované dokumentaci podrobný postup a skripty.

## <a name="aspnet-universal-providers"></a>ASP.NET Universal Providers

Vzhledem k tomu, že ASP.NET 2,0, platforma webových formulářů ASP.NET podporuje model poskytovatele pro celou řadu funkcí včetně členství. Univerzální poskytovatel členství, společně s volitelným poskytovatelem rolí, je velmi běžně nasazen s aplikacemi ASP.NET Web Forms. Nabízí robustní a zabezpečený způsob, jak spravovat ověřování a autorizaci, které ještě pořád fungují dobře. Poslední nabídka těchto univerzálních zprostředkovatelů je k dispozici jako balíček NuGet, [Microsoft. ASPNET. Providers](https://www.nuget.org/packages/Microsoft.AspNet.Providers).

Univerzální poskytovatelé pracují se schématem SQL Database, které obsahuje tabulky jako `aspnet_Applications` , `aspnet_Membership` , `aspnet_Roles` a `aspnet_Users` . Když nakonfigurujete spuštěním [ příkazuaspnet_regsql.exe](https://docs.microsoft.com/previous-versions/ms229862(v=vs.140)), nainstalují se tabulky a uložené procedury, které poskytují všechny nezbytné dotazy a příkazy potřebné pro práci s podkladovým datům. Schéma databáze a tyto uložené procedury nejsou kompatibilní s novějšími ASP.NET Identity a ASP.NET Core systémy identit, takže stávající data musí být migrována do nového systému. Obrázek 1 ukazuje příklad schématu tabulky nakonfigurovaného pro univerzální poskytovatele.

![schéma univerzálních zprostředkovatelů](./media/security/membership-tables.png)

Univerzální poskytovatel zpracovává uživatele, členství, role a profily. Uživatelům jsou přiřazeni globálně jedinečné identifikátory a v tabulce jsou uloženy velmi základní informace (ID uživatele, uživatelské jméno) `aspnet_Users` . V tabulce jsou uloženy informace o ověřování, jako je například heslo, formát hesla, heslo Salt, čítače uzamčení a podrobnosti atd. `aspnet_Membership` Role se skládají pouze z názvů a jedinečných identifikátorů, které jsou přiřazeny uživatelům prostřednictvím `aspnet_UsersInRoles` tabulky přidružení a poskytují relaci n:n.

Pokud váš stávající systém používá role kromě členství, budete muset migrovat uživatelské účty, přidružená hesla, role a členství role do ASP.NET Core identity. Pravděpodobně budete také muset aktualizovat kód, ve kterém aktuálně provádíte kontroly rolí pomocí příkazů if, aby místo toho využily deklarativní filtry, atributy nebo pomocníky značek. Na konci této kapitoly si podrobněji prozkoumáme předpoklady migrace.

### <a name="authorization-configuration-in-web-forms"></a>Konfigurace autorizace ve webových formulářích

Chcete-li nakonfigurovat autorizovaný přístup k určitým stránkám v aplikaci webových formulářů ASP.NET, obvykle zadáte, že určité stránky nebo složky jsou nepřístupné anonymním uživatelům. To se provádí v souboru web.config:

```xml
<?xml version="1.0"?>
<configuration>
    <system.web>
      <authentication mode="Forms">
        <forms defaultUrl="~/home.aspx" loginUrl="~/login.aspx"
          slidingExpiration="true" timeout="2880"></forms>
      </authentication>

      <authorization>
        <deny users="?" />
      </authorization>
    </system.web>
</configuration>
```

`authentication`Konfigurační oddíl nastaví pro aplikaci ověřování formulářů. `authorization`Oddíl slouží k zákazu anonymních uživatelů pro celou aplikaci. Můžete ale zadat přesnější pravidla autorizace na základě jednotlivých umístění a použít kontroly autorizace na základě rolí.

```xml
<location path="login.aspx">
  <system.web>
    <authorization>
      <allow users="*" />
    </authorization>
  </system.web>
</location>
```

Výše uvedená konfigurace, která je v kombinaci s první, by umožňovala anonymním uživatelům přístup k přihlašovací stránce a přepsání omezení v rámci lokality na neověřené uživatele.

```xml
<location path="/admin">
  <system.web>
    <authorization>
      <allow roles="Administrators" />
      <deny users="*" />
    </authorization>
  </system.web>
</location>
```

Výše uvedená konfigurace v kombinaci s ostatními omezuje přístup ke `/admin` složce a všem prostředkům v rámci této konfigurace na členy role Administrators. To může být také použito umístěním samostatného `web.config` souboru do `/admin` kořene složky.

### <a name="authorization-code-in-web-forms"></a>Autorizační kód ve webových formulářích

Kromě konfigurace přístupu pomocí nástroje `web.config` můžete také programově nakonfigurovat přístup a chování v aplikaci webových formulářů. Můžete například omezit schopnost provádět určité operace nebo zobrazit určitá data na základě role uživatele.

Tento kód lze použít v logice CodeBehind i na samotné stránce:

```html
<% if (HttpContext.Current.User.IsInRole("Administrators")) { %>
  <a href="/admin">Go To Admin</a>
<% } %>
```

Kromě kontroly členství uživatele v rolích můžete také zjistit, jestli jsou ověřené (i když to často je lepší s použitím konfigurace na základě umístění uvedeného výše). Níže je uveden příklad tohoto přístupu.

```csharp
protected void Page_Load(object sender, EventArgs e)
{
    if (!User.Identity.IsAuthenticated)
    {
        FormsAuthentication.RedirectToLoginPage();
    }
    if (!Roles.IsUserInRole(User.Identity.Name, "Administrators"))
    {
        MessageLabel.Text = "Only administrators can view this.";
        SecretPanel.Visible = false;
    }
}
```

V kódu výše se používá řízení přístupu na základě role (RBAC) k určení, zda jsou určité prvky stránky, například a `SecretPanel` , viditelné na základě role aktuálního uživatele.

Aplikace webových formulářů ASP.NET obvykle konfigurují zabezpečení v rámci `web.config` souboru a následně přidávají další kontroly tam, kde je to potřeba na `.aspx` stránkách a jejich souvisejících `.aspx.cs` souborech CodeBehind. Většina aplikací využívá univerzálního poskytovatele členství, často u dalšího poskytovatele rolí.

## <a name="aspnet-core-identity"></a>ASP.NET Core identity

I když se i nadále pracuje s ověřováním a autorizací, ASP.NET Core identita používá v porovnání s univerzálními poskytovateli jinou sadu abstrakcí a předpokladů. Nový model identity například podporuje ověřování třetí strany, které umožňuje uživatelům ověřování pomocí účtu na sociálních médiích nebo jiného zprostředkovatele důvěryhodného ověřování. ASP.NET Core identity podporuje uživatelské rozhraní pro běžně potřebné stránky, jako je přihlášení, odhlášení a registrace. Využívá EF Core pro přístup k datům a používá EF Core migrace k vygenerování potřebného schématu potřebného pro podporu jeho datového modelu. Tento [Úvod k identitě v ASP.NET Core](https://docs.microsoft.com/aspnet/core/security/authentication/identity) poskytuje dobrý přehled o tom, co je součástí ASP.NET Core identity a jak začít s ní pracovat. Pokud jste ještě nevytvořili ASP.NET Core identitu ve své aplikaci a její databázi, pomůže vám to začít.

### <a name="roles-claims-and-policies"></a>Role, deklarace identity a zásady

Poskytovatelé Universal Provider a ASP.NET Core identity podporují pojem rolí. Můžete vytvářet role pro uživatele a přiřazovat uživatele k rolím. Uživatelé můžou patřit do libovolného počtu rolí a v rámci implementace autorizace můžete ověřit členství v roli.

Kromě rolí ASP.NET Core identita podporuje koncepty deklarací identity a zásad. I když by role měla konkrétně odpovídat sadě prostředků, ke kterým by měl mít uživatel v této roli přístup, deklarace identity je jednoduše součástí identity uživatele. Deklarace identity je dvojice název hodnota, která představuje, co je předmět, a ne co může předmět dělat.

Je možné přímo zkontrolovat deklarace identity uživatele a určit, jestli se má uživatel udělit přístup k prostředku. Tyto kontroly jsou však často opakující se a rozptýleny v celém systému. Lepším přístupem je definování *zásad*.

Zásady autorizace se skládají z jednoho nebo více požadavků. Zásady se registrují jako součást konfigurace autorizační služby v `ConfigureServices` metodě `Startup.cs` . Například následující fragment kódu nakonfiguruje zásadu nazvanou "CanadiansOnly", která má požadavek, aby uživatel měl nárok země s hodnotou "Kanada".

```csharp
services.AddAuthorization(options =>
{
    options.AddPolicy("CanadiansOnly", policy => policy.RequireClaim(ClaimTypes.Country, "Canada"));
});
```

[Další informace o tom, jak vytvářet vlastní zásady, najdete v dokumentaci](https://docs.microsoft.com/aspnet/core/security/authorization/policies).

Bez ohledu na to, jestli používáte zásady nebo role, můžete určit, že konkrétní stránka v Blazor aplikaci bude vyžadovat tuto roli nebo zásadu s `[Authorize]` atributem použitým s `@attribute` direktivou.

Vyžadování role:

```csharp
@attribute [Authorize(Roles ="administrators")]
```

Vyžaduje se splnění zásady:

```csharp
@attribute [Authorize(Policy ="CanadiansOnly")]
```

Pokud potřebujete přístup ke stavu, rolím nebo deklaracím identity uživatele v kódu, existují dva základní způsoby, jak toho dosáhnout. První je přijmout stav ověřování jako kaskádový parametr. Druhým je přístup ke stavu pomocí vloženého `AuthenticationStateProvider` . Podrobnosti o každém z těchto přístupů jsou popsány v [ Blazor dokumentaci zabezpečení](https://docs.microsoft.com/aspnet/core/blazor/security/).

Následující kód ukazuje, jak přijmout `AuthenticationState` jako kaskádový parametr:

```csharp
[CascadingParameter]
private Task<AuthenticationState> authenticationStateTask { get; set; }
```

Když použijete tento parametr, můžete získat uživatele pomocí tohoto kódu:

```csharp
var authState = await authenticationStateTask;
var user = authState.User;
```

Následující kód ukazuje, jak vložit `AuthenticationStateProvider` :

```csharp
@using Microsoft.AspNetCore.Components.Authorization
@inject AuthenticationStateProvider AuthenticationStateProvider
```

Když je poskytovatel na místě, můžete získat přístup k uživateli pomocí následujícího kódu:

```csharp
AuthenticationState authState = await AuthenticationStateProvider.GetAuthenticationStateAsync();
ClaimsPrincipal user = authState.User;

if (user.Identity.IsAuthenticated)
{
  // work with user.Claims and/or user.Roles
}
```

**Poznámka:** `AuthorizeView` Komponenta, na kterou se vztahuje později v této kapitole, poskytuje deklarativní způsob, jak řídit, co uživatel uvidí na stránce nebo na komponentě.

Pokud chcete pracovat s uživateli a deklaracemi (v Blazor serverových aplikacích), budete možná muset vložit `UserManager<T>` (použít `IdentityUser` pro výchozí), které můžete použít k vytvoření výčtu a úpravě deklarací identity pro uživatele. Nejdřív zadejte typ a přiřaďte ho k vlastnosti:

```csharp
@inject UserManager<IdentityUser> MyUserManager
```

Pak ji použijte pro práci s deklaracemi uživatele. Následující příklad ukazuje, jak přidat a zachovat deklaraci identity na uživatele:

```csharp
private async Task AddCountryClaim()
{
    var authState = await AuthenticationStateProvider.GetAuthenticationStateAsync();
    var user = authState.User;
    var identityUser = await MyUserManager.FindByNameAsync(user.Identity.Name);

    if (!user.HasClaim(c => c.Type == ClaimTypes.Country))
    {
        // stores the claim in the cookie
        ClaimsIdentity id = new ClaimsIdentity();
        id.AddClaim(new Claim(ClaimTypes.Country, "Canada"));
        user.AddIdentity(id);

        // save the claim in the database
        await MyUserManager.AddClaimAsync(identityUser, new Claim(ClaimTypes.Country, "Canada"));
    }
}
```

Pokud potřebujete pracovat s rolemi, postupujte podle stejného přístupu. Je možné, že budete muset vložit `RoleManager<T>` (použít `IdentityRole` výchozí typ) k vypsání a správě samotných rolí.

**Poznámka:** V Blazor projektech WebAssembly budete muset zadat rozhraní API serveru pro provedení těchto operací (místo použití `UserManager<T>` nebo `RoleManager<T>` přímo). BlazorKlientská aplikace pro WebAssembly by mohla spravovat deklarace identity nebo role díky bezpečnému volání koncových bodů rozhraní API vystavených pro tento účel.

### <a name="migration-guide"></a>Průvodce migrací

Migrace z webových formulářů ASP.NET a univerzálních poskytovatelů na ASP.NET Core identity vyžaduje několik kroků:

1. Vytvořit ASP.NET Core schéma databáze identit v cílové databázi
2. Migrace dat ze schématu Universal Provider na ASP.NET Core schéma identity
3. Migrace konfigurace z web.config na middleware a služby, obvykle v `Startup.cs`
4. Aktualizujte jednotlivé stránky pomocí ovládacích prvků a podmíněných pro použití pomocníků značek a nových rozhraní API identity.

Každý z těchto kroků je podrobně popsán v následujících částech.

### <a name="creating-the-aspnet-core-identity-schema"></a>Vytváření schématu ASP.NET Core identity

K dispozici je několik způsobů, jak vytvořit potřebné struktury tabulek používané pro ASP.NET Core identity. Nejjednodušší je vytvořit novou ASP.NET Core webovou aplikaci. Zvolte Webová aplikace a pak změňte ověřování tak, aby používalo jednotlivé uživatelské účty.

![Nový projekt s jednotlivými uživatelskými účty](./media/security/individual-user-accounts.png)

Z příkazového řádku můžete stejné věci provést spuštěním příkazu `dotnet new webapp -au Individual` . Jakmile je aplikace vytvořená, spusťte ji a zaregistrujte ji na webu. Měli byste aktivovat stránku, jako je ta zobrazená níže:

![Stránka použít migrace](./media/security/apply-migrations-page.png)

Klikněte na tlačítko použít migrace a pro vás by měly být vytvořeny potřebné tabulky databáze. Kromě toho by se soubory migrace měly zobrazit ve vašem projektu, jak je znázorněno níže:

![soubory migrace](./media/security/migration-files.png)

Migraci můžete spustit sami, aniž byste museli webovou aplikaci spouštět, pomocí tohoto nástroje příkazového řádku:

```powershell
dotnet ef database update
```

Pokud místo toho chcete skript použít pro použití nového schématu pro existující databázi, můžete tyto migrace provést z příkazového řádku. Spuštěním tohoto příkazu vygenerujte skript:

```powershell
dotnet ef migrations script -o auth.sql
```

Tím se vytvoří skript SQL ve výstupním souboru, `auth.sql` který pak bude možné spustit na libovolné databázi, kterou chcete použít. Pokud máte potíže se spouštěním `dotnet ef` příkazů, ujistěte se, že [máte v systému nainstalované nástroje EF Core](https://docs.microsoft.com/ef/core/miscellaneous/cli/dotnet).

V případě, že máte ve zdrojových tabulkách další sloupce, budete muset určit nejlepší umístění pro tyto sloupce v novém schématu. Obecně by sloupce nalezené v `aspnet_Membership` tabulce měly být namapovány na `AspNetUsers` tabulku. Sloupce `aspnet_Roles` by měly být namapovány na `AspNetRoles` . `aspnet_UsersInRoles`Do tabulky by se přidaly všechny další sloupce v tabulce `AspNetUserRoles` .

Je také vhodné zvážit, že všechny další sloupce v samostatných tabulkách, aby budoucí migrace nemusely brát v úvahu taková Přizpůsobení výchozího schématu identity.

### <a name="migrating-data-from-universal-providers-to-aspnet-core-identity"></a>Migrace dat z univerzálních zprostředkovatelů do ASP.NET Core identity

Jakmile budete mít místo na začátku schéma cílové tabulky, bude dalším krokem migrace záznamů uživatelů a rolí do nového schématu. Úplný seznam rozdílů schémat, včetně toho, které sloupce se mapují na nové sloupce, najdete [tady](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/membership-to-core-identity).

Chcete-li migrovat uživatele z členství na nové tabulky identit, [postupujte podle kroků popsaných v dokumentaci](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/membership-to-core-identity). Po provedení těchto kroků a zadaného skriptu budou uživatelé při příštím přihlášení muset změnit heslo.

Je možné migrovat uživatelská hesla, ale proces je mnohem více zapojen. Vyžadování aktualizace hesel uživateli v rámci procesu migrace a jejich posílení pro použití nových jedinečných hesel, bude nejspíš zvýšit celkové zabezpečení aplikace.

### <a name="migrating-security-settings-from-webconfig-to-startupcs"></a>Migrace nastavení zabezpečení z web.config do Startup.cs

Jak bylo uvedeno výše, ASP.NET členství a zprostředkovatelé rolí jsou nakonfigurovány v souboru web.config aplikace. Vzhledem k tomu, že aplikace ASP.NET Core nejsou vázané na službu IIS a používají pro konfiguraci samostatný systém, je nutné tato nastavení nakonfigurovat jinde. Ve většině případů je ASP.NET Core identita nakonfigurovaná v `Startup.cs` souboru. Otevřete webový projekt, který byl vytvořen dříve (pro generování schématu tabulky identity) a zkontrolujte jeho `Startup.cs` soubor.

Výchozí metoda ConfigureServices přidává podporu pro EF Core a identitu:

```csharp
// This method gets called by the runtime. Use this method to add services to the container.
public void ConfigureServices(IServiceCollection services)
{
    services.AddDbContext<ApplicationDbContext>(options =>
        options.UseSqlServer(
            Configuration.GetConnectionString("DefaultConnection")));

    services.AddDefaultIdentity<IdentityUser>(options => options.SignIn.RequireConfirmedAccount = true)
        .AddEntityFrameworkStores<ApplicationDbContext>();

    services.AddRazorPages();
}
```

`AddDefaultIdentity`Metoda rozšíření slouží ke konfiguraci identity pro použití výchozího `ApplicationDbContext` a `IdentityUser` typu rozhraní. Pokud používáte vlastní `IdentityUser` , nezapomeňte sem zadat svůj typ. Pokud tyto metody rozšíření nefungují ve vaší aplikaci, ověřte, zda máte příslušné příkazy using a zda máte potřebné odkazy na balíček NuGet. Například váš projekt by měl mít určitou verzi `Microsoft.AspNetCore.Identity.EntityFrameworkCore` balíčku a, na `Microsoft.AspNetCore.Identity.UI` kterou se odkazuje.

Také `Startup.cs` byste měli vidět potřebný middleware nakonfigurovaný pro lokalitu. Konkrétně `UseAuthentication` a `UseAuthorization` měli byste nastavit a ve správném umístění.

```csharp

// This method gets called by the runtime. Use this method to configure the HTTP request pipeline.
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
        app.UseDatabaseErrorPage();
    }
    else
    {
        app.UseExceptionHandler("/Error");
        // The default HSTS value is 30 days. You may want to change this for production scenarios, see https://aka.ms/aspnetcore-hsts.
        app.UseHsts();
    }

    app.UseHttpsRedirection();
    app.UseStaticFiles();

    app.UseRouting();

    app.UseAuthentication();
    app.UseAuthorization();

    app.UseEndpoints(endpoints =>
    {
        endpoints.MapRazorPages();
    });
}
```

ASP.NET Identity nekonfiguruje anonymní nebo přístup na základě role k umístěním z `Startup.cs` . Pro filtry v ASP.NET Core budete muset migrovat všechna data konfigurace autorizace specifická pro konkrétní umístění. Poznamenejte si, které složky a stránky budou tyto aktualizace vyžadovat. Tyto změny provedete v další části.

### <a name="updating-individual-pages-to-use-aspnet-core-identity-abstractions"></a>Aktualizace jednotlivých stránek, které se mají použít ASP.NET Core abstrakce identity

Pokud jste v aplikaci webových formulářů ASP.NET web.config nastavení pro odepření přístupu k určitým stránkám nebo složkám anonymním uživatelům, můžete je migrovat pouhým přidáním `[Authorize]` atributu na tyto stránky:

```razor
@attribute [Authorize]
```

Pokud jste dál odepřeli přístup s výjimkou uživatelů, kteří patří do určité role, můžete to také provést tak, že přidáte atribut určující roli:

```razor
@attribute [Authorize(Roles ="administrators")]
```

Všimněte si, že `[Authorize]` atribut pracuje pouze na `@page` součástech, které jsou dosaženy přes Blazor směrovač. Atribut nefunguje s podřízenými komponentami, které by měly být použity místo toho `AuthorizeView` .

Pokud máte logiku v rámci značek stránky k určení toho, jestli se má nějaký kód zobrazit pro určitého uživatele, můžete ho nahradit `AuthorizeView` komponentou. [Komponenta AuthorizeView](https://docs.microsoft.com/aspnet/core/blazor/security#authorizeview-component) selektivně zobrazuje uživatelské rozhraní v závislosti na tom, jestli je uživatel autorizovaný k jeho zobrazení. Také zpřístupňuje `context` proměnnou, která se dá použít pro přístup k informacím o uživateli.

```razor
<AuthorizeView>
    <Authorized>
        <h1>Hello, @context.User.Identity.Name!</h1>
        <p>You can only see this content if you are authenticated.</p>
    </Authorized>
    <NotAuthorized>
        <h1>Authentication Failure!</h1>
        <p>You are not signed in.</p>
    </NotAuthorized>
</AuthorizeView>
```

Přístup k stavu ověřování v procedurální logice získáte přístupem uživatele z `Task<AuthenticationState` nakonfigurovaného s `[CascadingParameter]` atributem. Tím získáte přístup k uživateli, který vám umožní určit, jestli jsou ověřeni a jestli patří do konkrétní role. Pokud potřebujete zásadu vyhodnotit v procedurálním případě, můžete vložit instanci `IAuthorizationService` a volat `AuthorizeAsync` metodu. Následující vzorový kód ukazuje, jak získat informace o uživateli a povolit oprávněnému uživateli provést úlohu, kterou zásada omezila `content-editor` .

```razor
@using Microsoft.AspNetCore.Authorization
@inject IAuthorizationService AuthorizationService

<button @onclick="@DoSomething">Do something important</button>

@code {
    [CascadingParameter]
    private Task<AuthenticationState> authenticationStateTask { get; set; }

    private async Task DoSomething()
    {
        var user = (await authenticationStateTask).User;

        if (user.Identity.IsAuthenticated)
        {
            // Perform an action only available to authenticated (signed-in) users.
        }

        if (user.IsInRole("admin"))
        {
            // Perform an action only available to users in the 'admin' role.
        }

        if ((await AuthorizationService.AuthorizeAsync(user, "content-editor"))
            .Succeeded)
        {
            // Perform an action only available to users satisfying the
            // 'content-editor' policy.
        }
    }
}
```

`AuthenticationState`Nejprve musí být nastaven jako kaskádová hodnota, aby bylo možné vytvořit vazbu na kaskádový parametr, jako je to. To se obvykle provádí pomocí `CascadingAuthenticationState` komponenty. To se obvykle provádí v těchto případech `App.razor` :

```razor
<CascadingAuthenticationState>
    <Router AppAssembly="@typeof(Program).Assembly">
        <Found Context="routeData">
            <AuthorizeRouteView RouteData="@routeData"
                DefaultLayout="@typeof(MainLayout)" />
        </Found>
        <NotFound>
            <LayoutView Layout="@typeof(MainLayout)">
                <p>Sorry, there's nothing at this address.</p>
            </LayoutView>
        </NotFound>
    </Router>
</CascadingAuthenticationState>
```

## <a name="summary"></a>Shrnutí

Blazor používá stejný model zabezpečení jako ASP.NET Core, což je ASP.NET Core identita. Migrace od univerzálních zprostředkovatelů do ASP.NET Core identity je poměrně jednoduchá a za předpokladu, že se pro původní schéma dat nepoužilo příliš mnoho přizpůsobení. Po migraci dat je práce s ověřováním a autorizací v Blazor aplikacích dobře dokumentováná, a to s možností konfigurace a programovou podporou pro většinu požadavků na zabezpečení.

## <a name="references"></a>Odkazy

- [Úvod do identity na ASP.NET Core](https://docs.microsoft.com/aspnet/core/security/authentication/identity)
- [Migrace z ověřování členství ASP.NET do identity ASP.NET Core 2,0](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/membership-to-core-identity)
- [Migrace ověřování a identity na ASP.NET Core](https://docs.microsoft.com/aspnet/core/migration/identity)
- [ASP.NET Core Blazor ověřování a autorizace](https://docs.microsoft.com/aspnet/core/blazor/security/)

>[!div class="step-by-step"]
>[Předchozí](config.md) 
> [Další](migration.md)
