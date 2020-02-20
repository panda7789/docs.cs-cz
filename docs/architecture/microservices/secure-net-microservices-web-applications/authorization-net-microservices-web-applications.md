---
title: O autorizaci v mikroslužbách a webových aplikacích v technologii .NET
description: Zabezpečení v mikroslužbách a webových aplikacích .NET – získáte přehled o hlavních možnostech ověřování v ASP.NET Core aplikací – na základě rolí a na základě zásad.
author: mjrousos
ms.date: 01/30/2020
ms.openlocfilehash: f6b69faceac9a9b4819212cc04f89080f3ddad56
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77501770"
---
# <a name="about-authorization-in-net-microservices-and-web-applications"></a>O autorizaci v mikroslužbách a webových aplikacích v technologii .NET

Po ověření musí ASP.NET Core webových rozhraní API autorizovat přístup. Tento proces umožňuje službě zpřístupnit rozhraní API některým ověřeným uživatelům, ale ne všem. [Autorizaci](/aspnet/core/security/authorization/introduction) můžete provádět na základě rolí uživatelů nebo na základě vlastních zásad, které můžou zahrnovat kontrolu deklarací identity nebo jiné heuristiky.

Omezení přístupu k ASP.NET Core trasám MVC je stejně snadné jako použití autorizačního atributu na metodu akce (nebo na třídu kontroleru, pokud všechny akce kontroleru vyžadují autorizaci), jak je znázorněno v následujícím příkladu:

```csharp
public class AccountController : Controller
{
    public ActionResult Login()
    {
    }

    [Authorize]
    public ActionResult Logout()
    {
    }
}
```

Při přidání autorizačního atributu bez parametrů se ve výchozím nastavení omezí přístup k ověřeným uživatelům daného kontroleru nebo akce. Chcete-li dále omezit rozhraní API k dispozici pro konkrétní uživatele, lze atribut rozšířit tak, aby určoval požadované role nebo zásady, které uživatelé musí splnit.

## <a name="implement-role-based-authorization"></a>Implementace autorizace na základě rolí

ASP.NET Core identita má integrovaný koncept rolí. Kromě uživatelů ASP.NET Core identita ukládá informace o různých rolích používaných aplikací a udržuje přehled o tom, kteří uživatelé jsou přiřazeni k rolím. Tato přiřazení je možné změnit programově pomocí typu `RoleManager`, který aktualizuje role v trvalém úložišti, a `UserManager` typu, který může udělit nebo odvolávat role uživatelů.

Pokud ověřujete pomocí nosných tokenů JWT, naplní middleware ověřování Bearer ASP.NET Core JWT role uživatele na základě deklarací identity nalezených v tokenu. Chcete-li omezit přístup k akci nebo kontroler MVC na uživatele v konkrétních rolích, můžete do autorizační poznámky (atributu) zahrnout parametr role, jak je znázorněno v následujícím fragmentu kódu:

```csharp
[Authorize(Roles = "Administrator, PowerUser")]
public class ControlPanelController : Controller
{
    public ActionResult SetTime()
    {
    }

    [Authorize(Roles = "Administrator")]
    public ActionResult ShutDown()
    {
    }
}
```

V tomto příkladu mají přístup k rozhraním API v řadiči ControlPanel (například provádění akce SetTime –) jenom uživatelé v rolích správce nebo PowerUser. Rozhraní API pro vypnutí je dál omezené, aby povoloval přístup jenom uživatelům v roli správce.

Pro vyžadování uživatele v několika rolích použijte více autorizačních atributů, jak je znázorněno v následujícím příkladu:

```csharp
[Authorize(Roles = "Administrator, PowerUser")]
[Authorize(Roles = "RemoteEmployee ")]
[Authorize(Policy = "CustomPolicy")]
public ActionResult API1 ()
{
}
```

V tomto příkladu pro volání API1 musí uživatel:

- Být v roli správce *nebo* PowerUser *a*

- Být v roli RemoteEmployee *a*

- Vyhovět vlastní obslužné rutině pro autorizaci CustomPolicy

## <a name="implement-policy-based-authorization"></a>Implementace autorizace na základě zásad

Vlastní autorizační pravidla se dají zapisovat taky pomocí [autorizačních zásad](https://docs.asp.net/en/latest/security/authorization/policies.html). V této části najdete přehled. Další informace najdete v tématu [ASP.NET Authorization Workshop](https://github.com/blowdart/AspNetAuthorizationWorkshop).

Vlastní zásady autorizace jsou registrovány v metodě Startup. ConfigureServices pomocí služby. Metoda AddAuthorization Tato metoda přebírá delegáta, který konfiguruje argument AuthorizationOptions.

```csharp
services.AddAuthorization(options =>
{
    options.AddPolicy("AdministratorsOnly", policy =>
        policy.RequireRole("Administrator"));

    options.AddPolicy("EmployeesOnly", policy =>
        policy.RequireClaim("EmployeeNumber"));

    options.AddPolicy("Over21", policy =>
        policy.Requirements.Add(new MinimumAgeRequirement(21)));
});
```

Jak je znázorněno v příkladu, mohou být zásady přidruženy k různým typům požadavků. Po registraci jsou zásady možné použít pro akci nebo kontroler předáním názvu zásady jako argumentu zásad autorizačního atributu (například `[Authorize(Policy="EmployeesOnly")]`), který může mít více požadavků, nikoli jenom jeden (jak je znázorněno v těchto příkladech).

V předchozím příkladu je první volání AddPolicy pouze alternativním způsobem autorizace rolí. Pokud se `[Authorize(Policy="AdministratorsOnly")]` aplikuje na rozhraní API, budou mít přístup jenom uživatelé v roli správce.

Druhý <xref:Microsoft.AspNetCore.Authorization.AuthorizationOptions.AddPolicy%2A> hovor ukazuje snadný způsob, jak vyžadovat, aby uživatel měl k dispozici konkrétní deklaraci identity. Metoda <xref:Microsoft.AspNetCore.Authorization.AuthorizationPolicyBuilder.RequireClaim%2A> taky volitelně přijímá očekávané hodnoty deklarace identity. Pokud jsou zadány hodnoty, je požadavek splněn pouze v případě, že uživatel má deklaraci identity správného typu a jednu ze zadaných hodnot. Pokud používáte middleware pro ověřování JWT Bearer, budou k dispozici všechny vlastnosti JWT jako deklarace identity uživatelů.

Nejzajímavější zásada uvedená tady je třetí `AddPolicy` metoda, protože používá vlastní požadavek na autorizaci. Pomocí vlastních autorizačních požadavků můžete mít velkou kontrolu nad tím, jak se provádí autorizace. Aby to fungovalo, je nutné implementovat tyto typy:

- Typ požadavků, který je odvozen od <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> a obsahuje pole určující Podrobnosti požadavku. V tomto příkladu je toto pole stáří pro vzorový `MinimumAgeRequirement` typ.

- Obslužná rutina, která implementuje <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601>, kde T je typ <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement>, který obslužná rutina může splnit. Obslužná rutina musí implementovat metodu <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601.HandleRequirementAsync%2A>, která kontroluje, zda zadaný kontext, který obsahuje informace o uživateli, splňuje požadavek.

Pokud uživatel splňuje požadavek, volání `context.Succeed` bude označovat, že uživatel má oprávnění. Existuje-li více způsobů, jak může uživatel splnit požadavek na autorizaci, lze vytvořit více obslužných rutin.

Kromě registrace požadavků na vlastní zásady pomocí `AddPolicy` volání je také potřeba zaregistrovat vlastní obslužné rutiny požadavků prostřednictvím injektáže závislosti (`services.AddTransient<IAuthorizationHandler, MinimumAgeHandler>()`).

Příkladem vlastního autorizačního požadavku a obslužné rutiny pro kontrolu stáří uživatele (na základě `DateOfBirth` deklarace) je k dispozici v dokumentaci k [autorizaci](https://docs.asp.net/en/latest/security/authorization/policies.html)ASP.NET Core.

## <a name="additional-resources"></a>Další zdroje

- **ASP.NET Core ověřování** \
  [https://docs.microsoft.com/aspnet/core/security/authentication/identity](/aspnet/core/security/authentication/identity)

- **ASP.NET Core autorizaci** \
  [https://docs.microsoft.com/aspnet/core/security/authorization/introduction](/aspnet/core/security/authorization/introduction)

-  \ **autorizace na základě rolí**
  [https://docs.microsoft.com/aspnet/core/security/authorization/roles](/aspnet/core/security/authorization/roles)

- **Vlastní ověřování na základě zásad** \
  [https://docs.microsoft.com/aspnet/core/security/authorization/policies](/aspnet/core/security/authorization/policies)

>[!div class="step-by-step"]
>[Předchozí](index.md)
>[Další](developer-app-secrets-storage.md)
