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
# <a name="security-authentication-and-authorization-in-aspnet-web-forms-and-no-locblazor"></a><span data-ttu-id="ea7e7-103">Zabezpečení: ověřování a autorizace ve webových formulářích ASP.NET a Blazor</span><span class="sxs-lookup"><span data-stu-id="ea7e7-103">Security: Authentication and Authorization in ASP.NET Web Forms and Blazor</span></span>

<span data-ttu-id="ea7e7-104">Migrace z aplikace webových formulářů ASP.NET na Blazor bude téměř určitě vyžadovat aktualizaci způsobu ověřování a autorizace za předpokladu, že aplikace má nakonfigurované ověřování.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-104">Migrating from an ASP.NET Web Forms application to Blazor will almost certainly require updating how authentication and authorization is performed, assuming the application had authentication configured.</span></span> <span data-ttu-id="ea7e7-105">Tato kapitola popisuje, jak migrovat z modelu univerzálního poskytovatele webových formulářů ASP.NET (pro členství, role a profily uživatelů) a jak pracovat s ASP.NET Core identitou z Blazor aplikací.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-105">This chapter will cover how to migrate from the ASP.NET Web Forms universal provider model (for membership, roles, and user profiles) and how to work with ASP.NET Core Identity from Blazor apps.</span></span> <span data-ttu-id="ea7e7-106">I když tato kapitola pokryje nejdůležitější kroky a požadavky, najdete v odkazované dokumentaci podrobný postup a skripty.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-106">While this chapter will cover the high level steps and considerations, the detailed steps and scripts may be found in the referenced documentation.</span></span>

## <a name="aspnet-universal-providers"></a><span data-ttu-id="ea7e7-107">ASP.NET Universal Providers</span><span class="sxs-lookup"><span data-stu-id="ea7e7-107">ASP.NET universal providers</span></span>

<span data-ttu-id="ea7e7-108">Vzhledem k tomu, že ASP.NET 2,0, platforma webových formulářů ASP.NET podporuje model poskytovatele pro celou řadu funkcí včetně členství.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-108">Since ASP.NET 2.0, the ASP.NET Web Forms platform has supported a provider model for a variety of features, including membership.</span></span> <span data-ttu-id="ea7e7-109">Univerzální poskytovatel členství, společně s volitelným poskytovatelem rolí, je velmi běžně nasazen s aplikacemi ASP.NET Web Forms.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-109">The universal membership provider, along with the optional role provider, is very commonly deployed with ASP.NET Web Forms applications.</span></span> <span data-ttu-id="ea7e7-110">Nabízí robustní a zabezpečený způsob, jak spravovat ověřování a autorizaci, které ještě pořád fungují dobře.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-110">It offers a robust and secure way to manage authentication and authorization that continues to work well today.</span></span> <span data-ttu-id="ea7e7-111">Poslední nabídka těchto univerzálních zprostředkovatelů je k dispozici jako balíček NuGet, [Microsoft. ASPNET. Providers](https://www.nuget.org/packages/Microsoft.AspNet.Providers).</span><span class="sxs-lookup"><span data-stu-id="ea7e7-111">The most recent offering of these universal providers is available as a NuGet package, [Microsoft.AspNet.Providers](https://www.nuget.org/packages/Microsoft.AspNet.Providers).</span></span>

<span data-ttu-id="ea7e7-112">Univerzální poskytovatelé pracují se schématem SQL Database, které obsahuje tabulky jako `aspnet_Applications` , `aspnet_Membership` , `aspnet_Roles` a `aspnet_Users` .</span><span class="sxs-lookup"><span data-stu-id="ea7e7-112">The Universal Providers work with a SQL database schema that includes tables like `aspnet_Applications`, `aspnet_Membership`, `aspnet_Roles`, and `aspnet_Users`.</span></span> <span data-ttu-id="ea7e7-113">Když nakonfigurujete spuštěním [ příkazuaspnet_regsql.exe](https://docs.microsoft.com/previous-versions/ms229862(v=vs.140)), nainstalují se tabulky a uložené procedury, které poskytují všechny nezbytné dotazy a příkazy potřebné pro práci s podkladovým datům.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-113">When configured by running the [aspnet_regsql.exe command](https://docs.microsoft.com/previous-versions/ms229862(v=vs.140)), the providers install tables and stored procedures that provide all of the necessary queries and commands necessary to work with the underlying data.</span></span> <span data-ttu-id="ea7e7-114">Schéma databáze a tyto uložené procedury nejsou kompatibilní s novějšími ASP.NET Identity a ASP.NET Core systémy identit, takže stávající data musí být migrována do nového systému.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-114">The database schema and these stored procedures are not compatible with newer ASP.NET Identity and ASP.NET Core Identity systems, so existing data must be migrated into the new system.</span></span> <span data-ttu-id="ea7e7-115">Obrázek 1 ukazuje příklad schématu tabulky nakonfigurovaného pro univerzální poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-115">Figure 1 shows an example table schema configured for universal providers.</span></span>

![schéma univerzálních zprostředkovatelů](./media/security/membership-tables.png)

<span data-ttu-id="ea7e7-117">Univerzální poskytovatel zpracovává uživatele, členství, role a profily.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-117">The universal provider handles users, membership, roles, and profiles.</span></span> <span data-ttu-id="ea7e7-118">Uživatelům jsou přiřazeni globálně jedinečné identifikátory a v tabulce jsou uloženy velmi základní informace (ID uživatele, uživatelské jméno) `aspnet_Users` .</span><span class="sxs-lookup"><span data-stu-id="ea7e7-118">Users are assigned globally unique identifiers and very basic information (userId, userName) is stored in the `aspnet_Users` table.</span></span> <span data-ttu-id="ea7e7-119">V tabulce jsou uloženy informace o ověřování, jako je například heslo, formát hesla, heslo Salt, čítače uzamčení a podrobnosti atd. `aspnet_Membership`</span><span class="sxs-lookup"><span data-stu-id="ea7e7-119">Authentication information, such as password, password format, password salt, lockout counters and details, etc. are stored in the `aspnet_Membership` table.</span></span> <span data-ttu-id="ea7e7-120">Role se skládají pouze z názvů a jedinečných identifikátorů, které jsou přiřazeny uživatelům prostřednictvím `aspnet_UsersInRoles` tabulky přidružení a poskytují relaci n:n.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-120">Roles consist simply of names and unique identifiers, which are assigned to users via the `aspnet_UsersInRoles` association table, providing a many-to-many relationship.</span></span>

<span data-ttu-id="ea7e7-121">Pokud váš stávající systém používá role kromě členství, budete muset migrovat uživatelské účty, přidružená hesla, role a členství role do ASP.NET Core identity.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-121">If your existing system is using roles in addition to membership, you will need to migrate the user accounts, the associated passwords, the roles, and the role membership into ASP.NET Core Identity.</span></span> <span data-ttu-id="ea7e7-122">Pravděpodobně budete také muset aktualizovat kód, ve kterém aktuálně provádíte kontroly rolí pomocí příkazů if, aby místo toho využily deklarativní filtry, atributy nebo pomocníky značek.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-122">You will also most likely need to update your code where you're currently performing role checks using if statements to instead leverage declarative filters, attributes, and/or tag helpers.</span></span> <span data-ttu-id="ea7e7-123">Na konci této kapitoly si podrobněji prozkoumáme předpoklady migrace.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-123">We will review migration considerations in greater detail at the end of this chapter.</span></span>

### <a name="authorization-configuration-in-web-forms"></a><span data-ttu-id="ea7e7-124">Konfigurace autorizace ve webových formulářích</span><span class="sxs-lookup"><span data-stu-id="ea7e7-124">Authorization configuration in Web Forms</span></span>

<span data-ttu-id="ea7e7-125">Chcete-li nakonfigurovat autorizovaný přístup k určitým stránkám v aplikaci webových formulářů ASP.NET, obvykle zadáte, že určité stránky nebo složky jsou nepřístupné anonymním uživatelům.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-125">To configure authorized access to certain pages in an ASP.NET Web Forms application, typically you specify that certain pages or folders are inaccessible to anonymous users.</span></span> <span data-ttu-id="ea7e7-126">To se provádí v souboru web.config:</span><span class="sxs-lookup"><span data-stu-id="ea7e7-126">This is done in the web.config file:</span></span>

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

<span data-ttu-id="ea7e7-127">`authentication`Konfigurační oddíl nastaví pro aplikaci ověřování formulářů.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-127">The `authentication` configuration section sets up forms authentication for the application.</span></span> <span data-ttu-id="ea7e7-128">`authorization`Oddíl slouží k zákazu anonymních uživatelů pro celou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-128">The `authorization` section is used to disallow anonymous users for the entire application.</span></span> <span data-ttu-id="ea7e7-129">Můžete ale zadat přesnější pravidla autorizace na základě jednotlivých umístění a použít kontroly autorizace na základě rolí.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-129">However, you can provide more granular authorization rules on a per-location basis as well as apply role based authorization checks.</span></span>

```xml
<location path="login.aspx">
  <system.web>
    <authorization>
      <allow users="*" />
    </authorization>
  </system.web>
</location>
```

<span data-ttu-id="ea7e7-130">Výše uvedená konfigurace, která je v kombinaci s první, by umožňovala anonymním uživatelům přístup k přihlašovací stránce a přepsání omezení v rámci lokality na neověřené uživatele.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-130">The above configuration, when combined with the first one, would allow anonymous users to access the login page, overriding the site-wide restriction on non-authenticated users.</span></span>

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

<span data-ttu-id="ea7e7-131">Výše uvedená konfigurace v kombinaci s ostatními omezuje přístup ke `/admin` složce a všem prostředkům v rámci této konfigurace na členy role Administrators.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-131">The above configuration, when combined with the others, restricts access to the `/admin` folder and all resources within it to members of the "Administrators" role.</span></span> <span data-ttu-id="ea7e7-132">To může být také použito umístěním samostatného `web.config` souboru do `/admin` kořene složky.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-132">This could also be applied by placing a separate `web.config` file within the `/admin` folder root.</span></span>

### <a name="authorization-code-in-web-forms"></a><span data-ttu-id="ea7e7-133">Autorizační kód ve webových formulářích</span><span class="sxs-lookup"><span data-stu-id="ea7e7-133">Authorization code in Web Forms</span></span>

<span data-ttu-id="ea7e7-134">Kromě konfigurace přístupu pomocí nástroje `web.config` můžete také programově nakonfigurovat přístup a chování v aplikaci webových formulářů.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-134">In addition to configuring access using `web.config`, you can also programmatically configure access and behavior in your Web Forms application.</span></span> <span data-ttu-id="ea7e7-135">Můžete například omezit schopnost provádět určité operace nebo zobrazit určitá data na základě role uživatele.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-135">For instance, you can restrict the ability to perform certain operations or view certain data based on the user's role.</span></span>

<span data-ttu-id="ea7e7-136">Tento kód lze použít v logice CodeBehind i na samotné stránce:</span><span class="sxs-lookup"><span data-stu-id="ea7e7-136">This code can be used both in codebehind logic as well as in the page itself:</span></span>

```html
<% if (HttpContext.Current.User.IsInRole("Administrators")) { %>
  <a href="/admin">Go To Admin</a>
<% } %>
```

<span data-ttu-id="ea7e7-137">Kromě kontroly členství uživatele v rolích můžete také zjistit, jestli jsou ověřené (i když to často je lepší s použitím konfigurace na základě umístění uvedeného výše).</span><span class="sxs-lookup"><span data-stu-id="ea7e7-137">In addition to checking user role membership, you can also determine if they are authenticated (though often this is better done using the location-based configuration covered above).</span></span> <span data-ttu-id="ea7e7-138">Níže je uveden příklad tohoto přístupu.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-138">Below is an example of this approach.</span></span>

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

<span data-ttu-id="ea7e7-139">V kódu výše se používá řízení přístupu na základě role (RBAC) k určení, zda jsou určité prvky stránky, například a `SecretPanel` , viditelné na základě role aktuálního uživatele.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-139">In the code above, role-based access control (RBAC) is used to determine whether certain elements of the page, such as a `SecretPanel`, are visible based on the current user's role.</span></span>

<span data-ttu-id="ea7e7-140">Aplikace webových formulářů ASP.NET obvykle konfigurují zabezpečení v rámci `web.config` souboru a následně přidávají další kontroly tam, kde je to potřeba na `.aspx` stránkách a jejich souvisejících `.aspx.cs` souborech CodeBehind.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-140">Typically, ASP.NET Web Forms applications configure security within the `web.config` file and then add additional checks where needed in `.aspx` pages and their related `.aspx.cs` codebehind files.</span></span> <span data-ttu-id="ea7e7-141">Většina aplikací využívá univerzálního poskytovatele členství, často u dalšího poskytovatele rolí.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-141">Most applications leverage the universal membership provider, frequently with the additional role provider.</span></span>

## <a name="aspnet-core-identity"></a><span data-ttu-id="ea7e7-142">ASP.NET Core identity</span><span class="sxs-lookup"><span data-stu-id="ea7e7-142">ASP.NET Core Identity</span></span>

<span data-ttu-id="ea7e7-143">I když se i nadále pracuje s ověřováním a autorizací, ASP.NET Core identita používá v porovnání s univerzálními poskytovateli jinou sadu abstrakcí a předpokladů.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-143">Although still tasked with authentication and authorization, ASP.NET Core Identity uses a different set of abstractions and assumptions when compared to the universal providers.</span></span> <span data-ttu-id="ea7e7-144">Nový model identity například podporuje ověřování třetí strany, které umožňuje uživatelům ověřování pomocí účtu na sociálních médiích nebo jiného zprostředkovatele důvěryhodného ověřování.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-144">For example, the new Identity model supports third party authentication, allowing users to authenticate using a social media account or other trusted authentication provider.</span></span> <span data-ttu-id="ea7e7-145">ASP.NET Core identity podporuje uživatelské rozhraní pro běžně potřebné stránky, jako je přihlášení, odhlášení a registrace.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-145">ASP.NET Core Identity supports UI for commonly needed pages like login, logout, and register.</span></span> <span data-ttu-id="ea7e7-146">Využívá EF Core pro přístup k datům a používá EF Core migrace k vygenerování potřebného schématu potřebného pro podporu jeho datového modelu.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-146">It leverages EF Core for its data access, and uses EF Core migrations to generate the necessary schema required to supports its data model.</span></span> <span data-ttu-id="ea7e7-147">Tento [Úvod k identitě v ASP.NET Core](https://docs.microsoft.com/aspnet/core/security/authentication/identity) poskytuje dobrý přehled o tom, co je součástí ASP.NET Core identity a jak začít s ní pracovat.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-147">This [introduction to Identity on ASP.NET Core](https://docs.microsoft.com/aspnet/core/security/authentication/identity) provides a good overview of what is included with ASP.NET Core Identity and how to get started working with it.</span></span> <span data-ttu-id="ea7e7-148">Pokud jste ještě nevytvořili ASP.NET Core identitu ve své aplikaci a její databázi, pomůže vám to začít.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-148">If you haven't already set up ASP.NET Core Identity in your application and its database, it will help you get started.</span></span>

### <a name="roles-claims-and-policies"></a><span data-ttu-id="ea7e7-149">Role, deklarace identity a zásady</span><span class="sxs-lookup"><span data-stu-id="ea7e7-149">Roles, claims, and policies</span></span>

<span data-ttu-id="ea7e7-150">Poskytovatelé Universal Provider a ASP.NET Core identity podporují pojem rolí.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-150">Both the universal providers and ASP.NET Core Identity support the concept of roles.</span></span> <span data-ttu-id="ea7e7-151">Můžete vytvářet role pro uživatele a přiřazovat uživatele k rolím.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-151">You can create roles for users and assign users to roles.</span></span> <span data-ttu-id="ea7e7-152">Uživatelé můžou patřit do libovolného počtu rolí a v rámci implementace autorizace můžete ověřit členství v roli.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-152">Users can belong to any number of roles, and you can verify role membership as part of your authorization implementation.</span></span>

<span data-ttu-id="ea7e7-153">Kromě rolí ASP.NET Core identita podporuje koncepty deklarací identity a zásad.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-153">In addition to roles, ASP.NET Core identity supports the concepts of claims and policies.</span></span> <span data-ttu-id="ea7e7-154">I když by role měla konkrétně odpovídat sadě prostředků, ke kterým by měl mít uživatel v této roli přístup, deklarace identity je jednoduše součástí identity uživatele.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-154">While a role should specifically correspond to a set of resources a user in that role should be able to access, a claim is simply part of a user's identity.</span></span> <span data-ttu-id="ea7e7-155">Deklarace identity je dvojice název hodnota, která představuje, co je předmět, a ne co může předmět dělat.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-155">A claim is a name value pair that represents what the subject is, not what the subject can do.</span></span>

<span data-ttu-id="ea7e7-156">Je možné přímo zkontrolovat deklarace identity uživatele a určit, jestli se má uživatel udělit přístup k prostředku.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-156">It is possible to directly inspect a user's claims and determine based on these whether a user should be given access to a resource.</span></span> <span data-ttu-id="ea7e7-157">Tyto kontroly jsou však často opakující se a rozptýleny v celém systému.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-157">However, such checks are often repetitive and scattered throughout the system.</span></span> <span data-ttu-id="ea7e7-158">Lepším přístupem je definování *zásad*.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-158">A better approach is to define a *policy*.</span></span>

<span data-ttu-id="ea7e7-159">Zásady autorizace se skládají z jednoho nebo více požadavků.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-159">An authorization policy consists of one or more requirements.</span></span> <span data-ttu-id="ea7e7-160">Zásady se registrují jako součást konfigurace autorizační služby v `ConfigureServices` metodě `Startup.cs` .</span><span class="sxs-lookup"><span data-stu-id="ea7e7-160">Policies are registered as part of the authorization service configuration in the `ConfigureServices` method of `Startup.cs`.</span></span> <span data-ttu-id="ea7e7-161">Například následující fragment kódu nakonfiguruje zásadu nazvanou "CanadiansOnly", která má požadavek, aby uživatel měl nárok země s hodnotou "Kanada".</span><span class="sxs-lookup"><span data-stu-id="ea7e7-161">For example, the following code snippet configures a policy called "CanadiansOnly" which has the requirement that the user have the Country claim with the value of "Canada".</span></span>

```csharp
services.AddAuthorization(options =>
{
    options.AddPolicy("CanadiansOnly", policy => policy.RequireClaim(ClaimTypes.Country, "Canada"));
});
```

<span data-ttu-id="ea7e7-162">[Další informace o tom, jak vytvářet vlastní zásady, najdete v dokumentaci](https://docs.microsoft.com/aspnet/core/security/authorization/policies).</span><span class="sxs-lookup"><span data-stu-id="ea7e7-162">You can [learn more about how to create custom policies in the documentation](https://docs.microsoft.com/aspnet/core/security/authorization/policies).</span></span>

<span data-ttu-id="ea7e7-163">Bez ohledu na to, jestli používáte zásady nebo role, můžete určit, že konkrétní stránka v Blazor aplikaci bude vyžadovat tuto roli nebo zásadu s `[Authorize]` atributem použitým s `@attribute` direktivou.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-163">Whether you're using policies or roles, you can specify that a particular page in your Blazor application require that role or policy with the `[Authorize]` attribute, applied with the `@attribute` directive.</span></span>

<span data-ttu-id="ea7e7-164">Vyžadování role:</span><span class="sxs-lookup"><span data-stu-id="ea7e7-164">Requiring a role:</span></span>

```csharp
@attribute [Authorize(Roles ="administrators")]
```

<span data-ttu-id="ea7e7-165">Vyžaduje se splnění zásady:</span><span class="sxs-lookup"><span data-stu-id="ea7e7-165">Requiring a policy be satisfied:</span></span>

```csharp
@attribute [Authorize(Policy ="CanadiansOnly")]
```

<span data-ttu-id="ea7e7-166">Pokud potřebujete přístup ke stavu, rolím nebo deklaracím identity uživatele v kódu, existují dva základní způsoby, jak toho dosáhnout.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-166">If you need access to a user's authentication state, roles, or claims in your code, there are two primary ways to achieve this.</span></span> <span data-ttu-id="ea7e7-167">První je přijmout stav ověřování jako kaskádový parametr.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-167">The first is to receive the authentication state as a cascading parameter.</span></span> <span data-ttu-id="ea7e7-168">Druhým je přístup ke stavu pomocí vloženého `AuthenticationStateProvider` .</span><span class="sxs-lookup"><span data-stu-id="ea7e7-168">The second is to access the state using an injected `AuthenticationStateProvider`.</span></span> <span data-ttu-id="ea7e7-169">Podrobnosti o každém z těchto přístupů jsou popsány v [ Blazor dokumentaci zabezpečení](https://docs.microsoft.com/aspnet/core/blazor/security/).</span><span class="sxs-lookup"><span data-stu-id="ea7e7-169">The details of each of these approaches are described in the [Blazor Security documentation](https://docs.microsoft.com/aspnet/core/blazor/security/).</span></span>

<span data-ttu-id="ea7e7-170">Následující kód ukazuje, jak přijmout `AuthenticationState` jako kaskádový parametr:</span><span class="sxs-lookup"><span data-stu-id="ea7e7-170">The following code shows how to receive the `AuthenticationState` as a cascading parameter:</span></span>

```csharp
[CascadingParameter]
private Task<AuthenticationState> authenticationStateTask { get; set; }
```

<span data-ttu-id="ea7e7-171">Když použijete tento parametr, můžete získat uživatele pomocí tohoto kódu:</span><span class="sxs-lookup"><span data-stu-id="ea7e7-171">With this parameter in place, you can get the user using this code:</span></span>

```csharp
var authState = await authenticationStateTask;
var user = authState.User;
```

<span data-ttu-id="ea7e7-172">Následující kód ukazuje, jak vložit `AuthenticationStateProvider` :</span><span class="sxs-lookup"><span data-stu-id="ea7e7-172">The following code shows how to inject the `AuthenticationStateProvider`:</span></span>

```csharp
@using Microsoft.AspNetCore.Components.Authorization
@inject AuthenticationStateProvider AuthenticationStateProvider
```

<span data-ttu-id="ea7e7-173">Když je poskytovatel na místě, můžete získat přístup k uživateli pomocí následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="ea7e7-173">With the provider in place, you can gain access to the user with the following code:</span></span>

```csharp
AuthenticationState authState = await AuthenticationStateProvider.GetAuthenticationStateAsync();
ClaimsPrincipal user = authState.User;

if (user.Identity.IsAuthenticated)
{
  // work with user.Claims and/or user.Roles
}
```

<span data-ttu-id="ea7e7-174">**Poznámka:** `AuthorizeView` Komponenta, na kterou se vztahuje později v této kapitole, poskytuje deklarativní způsob, jak řídit, co uživatel uvidí na stránce nebo na komponentě.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-174">**Note:** The `AuthorizeView` component, covered later in this chapter, provides a declarative way to control what a user sees on a page or component.</span></span>

<span data-ttu-id="ea7e7-175">Pokud chcete pracovat s uživateli a deklaracemi (v Blazor serverových aplikacích), budete možná muset vložit `UserManager<T>` (použít `IdentityUser` pro výchozí), které můžete použít k vytvoření výčtu a úpravě deklarací identity pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-175">To work with users and claims (in Blazor Server applications) you may also need to inject a `UserManager<T>` (use `IdentityUser` for default) which you can use to enumerate and modify claims for a user.</span></span> <span data-ttu-id="ea7e7-176">Nejdřív zadejte typ a přiřaďte ho k vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="ea7e7-176">First inject the type and assign it to a property:</span></span>

```csharp
@inject UserManager<IdentityUser> MyUserManager
```

<span data-ttu-id="ea7e7-177">Pak ji použijte pro práci s deklaracemi uživatele.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-177">Then use it to work with the user's claims.</span></span> <span data-ttu-id="ea7e7-178">Následující příklad ukazuje, jak přidat a zachovat deklaraci identity na uživatele:</span><span class="sxs-lookup"><span data-stu-id="ea7e7-178">The following sample shows how to add and persist a claim on a user:</span></span>

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

<span data-ttu-id="ea7e7-179">Pokud potřebujete pracovat s rolemi, postupujte podle stejného přístupu.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-179">If you need to work with roles, follow the same approach.</span></span> <span data-ttu-id="ea7e7-180">Je možné, že budete muset vložit `RoleManager<T>` (použít `IdentityRole` výchozí typ) k vypsání a správě samotných rolí.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-180">You may need to inject a `RoleManager<T>` (use `IdentityRole` for default type) to list and manage the roles themselves.</span></span>

<span data-ttu-id="ea7e7-181">**Poznámka:** V Blazor projektech WebAssembly budete muset zadat rozhraní API serveru pro provedení těchto operací (místo použití `UserManager<T>` nebo `RoleManager<T>` přímo).</span><span class="sxs-lookup"><span data-stu-id="ea7e7-181">**Note:** In Blazor WebAssembly projects, you will need to provide server APIs to perform these operations (instead of using `UserManager<T>` or `RoleManager<T>` directly).</span></span> <span data-ttu-id="ea7e7-182">BlazorKlientská aplikace pro WebAssembly by mohla spravovat deklarace identity nebo role díky bezpečnému volání koncových bodů rozhraní API vystavených pro tento účel.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-182">A Blazor WebAssembly client application would manage claims and/or roles by securely calling API endpoints exposed for this purpose.</span></span>

### <a name="migration-guide"></a><span data-ttu-id="ea7e7-183">Průvodce migrací</span><span class="sxs-lookup"><span data-stu-id="ea7e7-183">Migration guide</span></span>

<span data-ttu-id="ea7e7-184">Migrace z webových formulářů ASP.NET a univerzálních poskytovatelů na ASP.NET Core identity vyžaduje několik kroků:</span><span class="sxs-lookup"><span data-stu-id="ea7e7-184">Migrating from ASP.NET Web Forms and universal providers to ASP.NET Core Identity requires several steps:</span></span>

1. <span data-ttu-id="ea7e7-185">Vytvořit ASP.NET Core schéma databáze identit v cílové databázi</span><span class="sxs-lookup"><span data-stu-id="ea7e7-185">Create ASP.NET Core Identity database schema in destination database</span></span>
2. <span data-ttu-id="ea7e7-186">Migrace dat ze schématu Universal Provider na ASP.NET Core schéma identity</span><span class="sxs-lookup"><span data-stu-id="ea7e7-186">Migrate data from universal provider schema to ASP.NET Core Identity schema</span></span>
3. <span data-ttu-id="ea7e7-187">Migrace konfigurace z web.config na middleware a služby, obvykle v `Startup.cs`</span><span class="sxs-lookup"><span data-stu-id="ea7e7-187">Migrate configuration from web.config to middleware and services, typically in `Startup.cs`</span></span>
4. <span data-ttu-id="ea7e7-188">Aktualizujte jednotlivé stránky pomocí ovládacích prvků a podmíněných pro použití pomocníků značek a nových rozhraní API identity.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-188">Update individual pages using controls and conditionals to use tag helpers and new identity APIs.</span></span>

<span data-ttu-id="ea7e7-189">Každý z těchto kroků je podrobně popsán v následujících částech.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-189">Each of these steps is described in detail in the following sections.</span></span>

### <a name="creating-the-aspnet-core-identity-schema"></a><span data-ttu-id="ea7e7-190">Vytváření schématu ASP.NET Core identity</span><span class="sxs-lookup"><span data-stu-id="ea7e7-190">Creating the ASP.NET Core Identity schema</span></span>

<span data-ttu-id="ea7e7-191">K dispozici je několik způsobů, jak vytvořit potřebné struktury tabulek používané pro ASP.NET Core identity.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-191">There are several ways to create the necessary table structure used for ASP.NET Core Identity.</span></span> <span data-ttu-id="ea7e7-192">Nejjednodušší je vytvořit novou ASP.NET Core webovou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-192">The simplest is to create a new ASP.NET Core Web application.</span></span> <span data-ttu-id="ea7e7-193">Zvolte Webová aplikace a pak změňte ověřování tak, aby používalo jednotlivé uživatelské účty.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-193">Choose Web Application and then change Authentication to use Individual User Accounts.</span></span>

![Nový projekt s jednotlivými uživatelskými účty](./media/security/individual-user-accounts.png)

<span data-ttu-id="ea7e7-195">Z příkazového řádku můžete stejné věci provést spuštěním příkazu `dotnet new webapp -au Individual` .</span><span class="sxs-lookup"><span data-stu-id="ea7e7-195">From the command line, you can do the same thing by running `dotnet new webapp -au Individual`.</span></span> <span data-ttu-id="ea7e7-196">Jakmile je aplikace vytvořená, spusťte ji a zaregistrujte ji na webu.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-196">Once the app has been created, run it and register on the site.</span></span> <span data-ttu-id="ea7e7-197">Měli byste aktivovat stránku, jako je ta zobrazená níže:</span><span class="sxs-lookup"><span data-stu-id="ea7e7-197">You should trigger a page like the one shown below:</span></span>

![Stránka použít migrace](./media/security/apply-migrations-page.png)

<span data-ttu-id="ea7e7-199">Klikněte na tlačítko použít migrace a pro vás by měly být vytvořeny potřebné tabulky databáze.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-199">Click on the "Apply Migrations" button and the necessary database tables should be created for you.</span></span> <span data-ttu-id="ea7e7-200">Kromě toho by se soubory migrace měly zobrazit ve vašem projektu, jak je znázorněno níže:</span><span class="sxs-lookup"><span data-stu-id="ea7e7-200">In addition, the migration files should appear in your project, as shown:</span></span>

![soubory migrace](./media/security/migration-files.png)

<span data-ttu-id="ea7e7-202">Migraci můžete spustit sami, aniž byste museli webovou aplikaci spouštět, pomocí tohoto nástroje příkazového řádku:</span><span class="sxs-lookup"><span data-stu-id="ea7e7-202">You can run the migration yourself, without running the web application, using this command line tool:</span></span>

```powershell
dotnet ef database update
```

<span data-ttu-id="ea7e7-203">Pokud místo toho chcete skript použít pro použití nového schématu pro existující databázi, můžete tyto migrace provést z příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-203">If you would rather run a script to apply the new schema to an existing database, you can script these migrations from the command line.</span></span> <span data-ttu-id="ea7e7-204">Spuštěním tohoto příkazu vygenerujte skript:</span><span class="sxs-lookup"><span data-stu-id="ea7e7-204">Run this command to generate the script:</span></span>

```powershell
dotnet ef migrations script -o auth.sql
```

<span data-ttu-id="ea7e7-205">Tím se vytvoří skript SQL ve výstupním souboru, `auth.sql` který pak bude možné spustit na libovolné databázi, kterou chcete použít.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-205">This will produce a SQL script in the output file `auth.sql` which can then be run against whatever database you like.</span></span> <span data-ttu-id="ea7e7-206">Pokud máte potíže se spouštěním `dotnet ef` příkazů, ujistěte se, že [máte v systému nainstalované nástroje EF Core](https://docs.microsoft.com/ef/core/miscellaneous/cli/dotnet).</span><span class="sxs-lookup"><span data-stu-id="ea7e7-206">If you have any trouble running `dotnet ef` commands, [make sure you have the EF Core tools installed on your system](https://docs.microsoft.com/ef/core/miscellaneous/cli/dotnet).</span></span>

<span data-ttu-id="ea7e7-207">V případě, že máte ve zdrojových tabulkách další sloupce, budete muset určit nejlepší umístění pro tyto sloupce v novém schématu.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-207">In the event you have additional columns on your source tables, you will need to identify the best location for these columns in the new schema.</span></span> <span data-ttu-id="ea7e7-208">Obecně by sloupce nalezené v `aspnet_Membership` tabulce měly být namapovány na `AspNetUsers` tabulku.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-208">Generally, columns found on the `aspnet_Membership` table should be mapped to the `AspNetUsers` table.</span></span> <span data-ttu-id="ea7e7-209">Sloupce `aspnet_Roles` by měly být namapovány na `AspNetRoles` .</span><span class="sxs-lookup"><span data-stu-id="ea7e7-209">Columns on `aspnet_Roles` should be mapped to `AspNetRoles`.</span></span> <span data-ttu-id="ea7e7-210">`aspnet_UsersInRoles`Do tabulky by se přidaly všechny další sloupce v tabulce `AspNetUserRoles` .</span><span class="sxs-lookup"><span data-stu-id="ea7e7-210">Any additional columns on the `aspnet_UsersInRoles` table would be added to the `AspNetUserRoles` table.</span></span>

<span data-ttu-id="ea7e7-211">Je také vhodné zvážit, že všechny další sloupce v samostatných tabulkách, aby budoucí migrace nemusely brát v úvahu taková Přizpůsobení výchozího schématu identity.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-211">It's also worth considering putting any additional columns on separate tables, so that future migrations won't need to take into account such customizations of the default identity schema.</span></span>

### <a name="migrating-data-from-universal-providers-to-aspnet-core-identity"></a><span data-ttu-id="ea7e7-212">Migrace dat z univerzálních zprostředkovatelů do ASP.NET Core identity</span><span class="sxs-lookup"><span data-stu-id="ea7e7-212">Migrating data from universal providers to ASP.NET Core Identity</span></span>

<span data-ttu-id="ea7e7-213">Jakmile budete mít místo na začátku schéma cílové tabulky, bude dalším krokem migrace záznamů uživatelů a rolí do nového schématu.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-213">Once you have the destination table schema in place, the next step is to migrate your user and role records to the new schema.</span></span> <span data-ttu-id="ea7e7-214">Úplný seznam rozdílů schémat, včetně toho, které sloupce se mapují na nové sloupce, najdete [tady](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/membership-to-core-identity).</span><span class="sxs-lookup"><span data-stu-id="ea7e7-214">A complete list of the schema differences, including which columns map to which new columns, can be found [here](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/membership-to-core-identity).</span></span>

<span data-ttu-id="ea7e7-215">Chcete-li migrovat uživatele z členství na nové tabulky identit, [postupujte podle kroků popsaných v dokumentaci](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/membership-to-core-identity).</span><span class="sxs-lookup"><span data-stu-id="ea7e7-215">To migrate your users from membership to the new identity tables, you should [follow the steps described in the documentation](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/membership-to-core-identity).</span></span> <span data-ttu-id="ea7e7-216">Po provedení těchto kroků a zadaného skriptu budou uživatelé při příštím přihlášení muset změnit heslo.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-216">After following these steps and the script provided, your users will need to change their password the next time they log in.</span></span>

<span data-ttu-id="ea7e7-217">Je možné migrovat uživatelská hesla, ale proces je mnohem více zapojen.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-217">It is possible to migrate user passwords but the process is much more involved.</span></span> <span data-ttu-id="ea7e7-218">Vyžadování aktualizace hesel uživateli v rámci procesu migrace a jejich posílení pro použití nových jedinečných hesel, bude nejspíš zvýšit celkové zabezpečení aplikace.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-218">Requiring users to update their passwords as part of the migration process, and encouraging them to use new, unique passwords, is likely to enhance the overall security of the application.</span></span>

### <a name="migrating-security-settings-from-webconfig-to-startupcs"></a><span data-ttu-id="ea7e7-219">Migrace nastavení zabezpečení z web.config do Startup.cs</span><span class="sxs-lookup"><span data-stu-id="ea7e7-219">Migrating security settings from web.config to Startup.cs</span></span>

<span data-ttu-id="ea7e7-220">Jak bylo uvedeno výše, ASP.NET členství a zprostředkovatelé rolí jsou nakonfigurovány v souboru web.config aplikace.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-220">As noted above, ASP.NET membership and role providers are configured in the application's web.config file.</span></span> <span data-ttu-id="ea7e7-221">Vzhledem k tomu, že aplikace ASP.NET Core nejsou vázané na službu IIS a používají pro konfiguraci samostatný systém, je nutné tato nastavení nakonfigurovat jinde.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-221">Since ASP.NET Core apps are not tied to IIS and use a separate system for configuration, these settings must be configured elsewhere.</span></span> <span data-ttu-id="ea7e7-222">Ve většině případů je ASP.NET Core identita nakonfigurovaná v `Startup.cs` souboru.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-222">For the most part, ASP.NET Core Identity is configured in the `Startup.cs` file.</span></span> <span data-ttu-id="ea7e7-223">Otevřete webový projekt, který byl vytvořen dříve (pro generování schématu tabulky identity) a zkontrolujte jeho `Startup.cs` soubor.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-223">Open the web project that was created earlier (to generate the identity table schema) and review its `Startup.cs` file.</span></span>

<span data-ttu-id="ea7e7-224">Výchozí metoda ConfigureServices přidává podporu pro EF Core a identitu:</span><span class="sxs-lookup"><span data-stu-id="ea7e7-224">The default ConfigureServices method adds support for EF Core and Identity:</span></span>

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

<span data-ttu-id="ea7e7-225">`AddDefaultIdentity`Metoda rozšíření slouží ke konfiguraci identity pro použití výchozího `ApplicationDbContext` a `IdentityUser` typu rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-225">The `AddDefaultIdentity` extension method is used to configure Identity to use the default `ApplicationDbContext` and the framework's `IdentityUser` type.</span></span> <span data-ttu-id="ea7e7-226">Pokud používáte vlastní `IdentityUser` , nezapomeňte sem zadat svůj typ.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-226">If you're using a custom `IdentityUser`, be sure to specify its type here.</span></span> <span data-ttu-id="ea7e7-227">Pokud tyto metody rozšíření nefungují ve vaší aplikaci, ověřte, zda máte příslušné příkazy using a zda máte potřebné odkazy na balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-227">If these extension methods aren't working in your application, check that you have the appropriate using statements and that you have the necessary NuGet package references.</span></span> <span data-ttu-id="ea7e7-228">Například váš projekt by měl mít určitou verzi `Microsoft.AspNetCore.Identity.EntityFrameworkCore` balíčku a, na `Microsoft.AspNetCore.Identity.UI` kterou se odkazuje.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-228">For example, your project should have some version of the `Microsoft.AspNetCore.Identity.EntityFrameworkCore` and `Microsoft.AspNetCore.Identity.UI` packages referenced.</span></span>

<span data-ttu-id="ea7e7-229">Také `Startup.cs` byste měli vidět potřebný middleware nakonfigurovaný pro lokalitu.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-229">Also in `Startup.cs` you should see the necessary middleware configured for the site.</span></span> <span data-ttu-id="ea7e7-230">Konkrétně `UseAuthentication` a `UseAuthorization` měli byste nastavit a ve správném umístění.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-230">Specifically, `UseAuthentication` and `UseAuthorization` should be set up, and in the proper location.</span></span>

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

<span data-ttu-id="ea7e7-231">ASP.NET Identity nekonfiguruje anonymní nebo přístup na základě role k umístěním z `Startup.cs` .</span><span class="sxs-lookup"><span data-stu-id="ea7e7-231">ASP.NET Identity does not configure anonymous or role-based access to locations from `Startup.cs`.</span></span> <span data-ttu-id="ea7e7-232">Pro filtry v ASP.NET Core budete muset migrovat všechna data konfigurace autorizace specifická pro konkrétní umístění.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-232">You will need to migrate any location-specific authorization configuration data to filters in ASP.NET Core.</span></span> <span data-ttu-id="ea7e7-233">Poznamenejte si, které složky a stránky budou tyto aktualizace vyžadovat.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-233">Make note of which folders and pages will require such updates.</span></span> <span data-ttu-id="ea7e7-234">Tyto změny provedete v další části.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-234">You will make these changes in the next section.</span></span>

### <a name="updating-individual-pages-to-use-aspnet-core-identity-abstractions"></a><span data-ttu-id="ea7e7-235">Aktualizace jednotlivých stránek, které se mají použít ASP.NET Core abstrakce identity</span><span class="sxs-lookup"><span data-stu-id="ea7e7-235">Updating individual pages to use ASP.NET Core Identity abstractions</span></span>

<span data-ttu-id="ea7e7-236">Pokud jste v aplikaci webových formulářů ASP.NET web.config nastavení pro odepření přístupu k určitým stránkám nebo složkám anonymním uživatelům, můžete je migrovat pouhým přidáním `[Authorize]` atributu na tyto stránky:</span><span class="sxs-lookup"><span data-stu-id="ea7e7-236">In your ASP.NET Web Forms application, if you had web.config settings to deny access to certain pages or folders to anonymous users, you would migrate these by simply adding the `[Authorize]` attribute to such pages:</span></span>

```razor
@attribute [Authorize]
```

<span data-ttu-id="ea7e7-237">Pokud jste dál odepřeli přístup s výjimkou uživatelů, kteří patří do určité role, můžete to také provést tak, že přidáte atribut určující roli:</span><span class="sxs-lookup"><span data-stu-id="ea7e7-237">If you further had denied access except to those users belonging to a certain role, you would likewise migrate this by adding an attribute specifying a role:</span></span>

```razor
@attribute [Authorize(Roles ="administrators")]
```

<span data-ttu-id="ea7e7-238">Všimněte si, že `[Authorize]` atribut pracuje pouze na `@page` součástech, které jsou dosaženy přes Blazor směrovač.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-238">Note that the `[Authorize]` attribute only works on `@page` components that are reached via the Blazor Router.</span></span> <span data-ttu-id="ea7e7-239">Atribut nefunguje s podřízenými komponentami, které by měly být použity místo toho `AuthorizeView` .</span><span class="sxs-lookup"><span data-stu-id="ea7e7-239">The attribute does not work with child components, which should instead use `AuthorizeView`.</span></span>

<span data-ttu-id="ea7e7-240">Pokud máte logiku v rámci značek stránky k určení toho, jestli se má nějaký kód zobrazit pro určitého uživatele, můžete ho nahradit `AuthorizeView` komponentou.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-240">If you have logic within page markup for determining whether to display some code to a certain user, you can replace this with the `AuthorizeView` component.</span></span> <span data-ttu-id="ea7e7-241">[Komponenta AuthorizeView](https://docs.microsoft.com/aspnet/core/blazor/security#authorizeview-component) selektivně zobrazuje uživatelské rozhraní v závislosti na tom, jestli je uživatel autorizovaný k jeho zobrazení.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-241">The [AuthorizeView component](https://docs.microsoft.com/aspnet/core/blazor/security#authorizeview-component) selectively displays UI depending on whether the user is authorized to see it.</span></span> <span data-ttu-id="ea7e7-242">Také zpřístupňuje `context` proměnnou, která se dá použít pro přístup k informacím o uživateli.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-242">It also exposes a `context` variable that can be used to access user information.</span></span>

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

<span data-ttu-id="ea7e7-243">Přístup k stavu ověřování v procedurální logice získáte přístupem uživatele z `Task<AuthenticationState` nakonfigurovaného s `[CascadingParameter]` atributem.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-243">You can access authentication state within procedural logic by accessing the user from a `Task<AuthenticationState` configured with the `[CascadingParameter]` attribute.</span></span> <span data-ttu-id="ea7e7-244">Tím získáte přístup k uživateli, který vám umožní určit, jestli jsou ověřeni a jestli patří do konkrétní role.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-244">This will get you access to the user, which can let you determine if they are authenticated and if they belong to a particular role.</span></span> <span data-ttu-id="ea7e7-245">Pokud potřebujete zásadu vyhodnotit v procedurálním případě, můžete vložit instanci `IAuthorizationService` a volat `AuthorizeAsync` metodu.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-245">If you need to evaluate a policy procedurally, you can inject an instance of the `IAuthorizationService` and calls the `AuthorizeAsync` method on it.</span></span> <span data-ttu-id="ea7e7-246">Následující vzorový kód ukazuje, jak získat informace o uživateli a povolit oprávněnému uživateli provést úlohu, kterou zásada omezila `content-editor` .</span><span class="sxs-lookup"><span data-stu-id="ea7e7-246">The following sample code demonstrates how to get user information and allow an authorized user to perform a task restricted by the `content-editor` policy.</span></span>

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

<span data-ttu-id="ea7e7-247">`AuthenticationState`Nejprve musí být nastaven jako kaskádová hodnota, aby bylo možné vytvořit vazbu na kaskádový parametr, jako je to.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-247">The `AuthenticationState` does first need to be setup as a cascading value before it can be bound to a cascading parameter like this.</span></span> <span data-ttu-id="ea7e7-248">To se obvykle provádí pomocí `CascadingAuthenticationState` komponenty.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-248">That's typically done using the `CascadingAuthenticationState` component.</span></span> <span data-ttu-id="ea7e7-249">To se obvykle provádí v těchto případech `App.razor` :</span><span class="sxs-lookup"><span data-stu-id="ea7e7-249">This is typically done in `App.razor`:</span></span>

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

## <a name="summary"></a><span data-ttu-id="ea7e7-250">Shrnutí</span><span class="sxs-lookup"><span data-stu-id="ea7e7-250">Summary</span></span>

<span data-ttu-id="ea7e7-251">Blazor používá stejný model zabezpečení jako ASP.NET Core, což je ASP.NET Core identita.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-251">Blazor uses the same security model as ASP.NET Core, which is ASP.NET Core Identity.</span></span> <span data-ttu-id="ea7e7-252">Migrace od univerzálních zprostředkovatelů do ASP.NET Core identity je poměrně jednoduchá a za předpokladu, že se pro původní schéma dat nepoužilo příliš mnoho přizpůsobení.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-252">Migrating from universal providers to ASP.NET Core Identity is relatively straightforward, assuming not too much customization was applied to the original data schema.</span></span> <span data-ttu-id="ea7e7-253">Po migraci dat je práce s ověřováním a autorizací v Blazor aplikacích dobře dokumentováná, a to s možností konfigurace a programovou podporou pro většinu požadavků na zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="ea7e7-253">Once the data has been migrated, working with authentication and authorization in Blazor apps is well-documented, with configurable as well as programmatic support for most security requirements.</span></span>

## <a name="references"></a><span data-ttu-id="ea7e7-254">Odkazy</span><span class="sxs-lookup"><span data-stu-id="ea7e7-254">References</span></span>

- [<span data-ttu-id="ea7e7-255">Úvod do identity na ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ea7e7-255">Introduction to Identity on ASP.NET Core</span></span>](https://docs.microsoft.com/aspnet/core/security/authentication/identity)
- [<span data-ttu-id="ea7e7-256">Migrace z ověřování členství ASP.NET do identity ASP.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="ea7e7-256">Migrate from ASP.NET Membership authentication to ASP.NET Core 2.0 Identity</span></span>](https://docs.microsoft.com/aspnet/core/migration/proper-to-2x/membership-to-core-identity)
- [<span data-ttu-id="ea7e7-257">Migrace ověřování a identity na ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ea7e7-257">Migrate Authentication and Identity to ASP.NET Core</span></span>](https://docs.microsoft.com/aspnet/core/migration/identity)
- [<span data-ttu-id="ea7e7-258">ASP.NET Core Blazor ověřování a autorizace</span><span class="sxs-lookup"><span data-stu-id="ea7e7-258">ASP.NET Core Blazor authentication and authorization</span></span>](https://docs.microsoft.com/aspnet/core/blazor/security/)

>[!div class="step-by-step"]
><span data-ttu-id="ea7e7-259">[Předchozí](config.md) 
> [Další](migration.md)</span><span class="sxs-lookup"><span data-stu-id="ea7e7-259">[Previous](config.md)
[Next](migration.md)</span></span>
