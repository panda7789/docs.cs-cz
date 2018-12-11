---
title: O autorizaci v mikroslužbách a webových aplikací .NET
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | O autorizaci v mikroslužbách a webových aplikací .NET
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 53202d0f890df040480b9f54c54aaefdd025dffa
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53149559"
---
# <a name="about-authorization-in-net-microservices-and-web-applications"></a>O autorizaci v mikroslužbách a webových aplikací .NET

Po ověření ASP.NET Core webová rozhraní API nutné k autorizaci přístupu. Tento proces umožňuje službě vytvořit rozhraní API dostupné pro některé ověřeného uživatele, ale ne pro všechny. [Autorizace](https://docs.microsoft.com/aspnet/core/security/authorization/introduction) můžete provést podle role uživatelů nebo založená na vlastní zásadu, která by mohla obsahovat kontrola deklarace identity nebo jiných heuristické metody.

Omezení přístupu ASP.NET Core MVC směrovací je stejně jednoduché jako použití Authorize atributu na metodu akce (nebo do třídy kontroleru, pokud všechny kontroleru akce vyžadují autorizace), jako je znázorněno v následujícím příkladu:

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

Ve výchozím nastavení bude přidání atributu Authorize bez parametrů omezovat přístup ověřeným uživatelům pro tento kontroler nebo akce. Pro další omezení rozhraní API k dispozici pouze pro konkrétního uživatele, je možné rozšířit atribut zadejte požadované role nebo zásady, které uživatelé musí splňovat.

## <a name="implementing-role-based-authorization"></a>Implementace ověřování na základě role

ASP.NET Core Identity koncept předdefinovaných rolí. Kromě uživatelů ASP.NET Core Identity ukládá informace o různých rolích, které jsou využívané aplikací a kteří uživatelé jsou přiřazení rolím, které uchovává informace o. Tato přiřazení je možné programově měnit pomocí RoleManager typ (která aktualizuje role do trvalého úložiště) a typ objektu UserManager., (který může přiřazení nebo zrušení přiřazení uživatele z role).

Pokud ověřujete pomocí nosných tokenů JWT, naplníte ověřovací middleware nosiče ASP.NET Core JWT role uživatele na základě role deklarací identity v tokenu. Omezení přístupu k MVC akce nebo kontroleru pro uživatele v určitých rolích, můžete zahrnout parametr role v hlavičce autorizovat, jak je znázorněno v následujícím příkladu:

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

V tomto příkladu pouze uživatelé v rolích správce nebo PowerUser můžete přístup k rozhraním API v Ovládacích panelech kontroleru (jako je například provádění akce SetTime). Vypnutí API je další omezen na povolení přístupu jenom na uživatele v roli správce.

Tak, aby že se uživatel do více rolí, použijte více atributů autorizovat, jak je znázorněno v následujícím příkladu:

```csharp
[Authorize(Roles = "Administrator, PowerUser")]
[Authorize(Roles = "RemoteEmployee ")]
[Authorize(Policy = "CustomPolicy")]
public ActionResult API1 ()
{
}
```

V tomto příkladu volání API1, uživatel musí:

-   V na správce *nebo* PowerUser role *a*

-   V roli RemoteEmployee *a*

-   Vlastní obslužnou rutinu pro autorizaci CustomPolicy splňovat.

## <a name="implementing-policy-based-authorization"></a>Implementace ověřování na základě zásad

Vlastní ověřovací pravidla lze také zapsat pomocí [zásad autorizace](https://docs.asp.net/en/latest/security/authorization/policies.html). Tato část poskytuje přehled. Další podrobnosti najdete v online [seminář o autorizaci ASP.NET](https://github.com/blowdart/AspNetAuthorizationWorkshop).

Zásady autorizace zaregistrovaní v metodě Startup.ConfigureServices pomocí služby. Metoda AddAuthorization. Tato metoda přebírá delegáta, který konfiguruje AuthorizationOptions argument.

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

Jak je znázorněno v příkladu, lze přidružit různé druhy požadavky zásad. Po registraci se tyto zásady, se můžou uplatnit na akce nebo kontroleru předáním název vaší zásady jako argument zásad Authorize atributu (například \[Authorize(Policy="EmployeesOnly")\]) může mít zásady více požadavků, ne jenom jeden (jak je znázorněno v těchto příkladech).

V předchozím příkladu první volání AddPolicy je právě alternativní způsob autorizaci rolí. Pokud \[Authorize(Policy="AdministratorsOnly")\] platí pro rozhraní API, budou jenom uživatelé v roli správce k němu mít přístup.

Druhé volání AddPolicy ukazuje snadný způsob, jak vyžadovat, konkrétní deklarace identity by měl být k dispozici pro uživatele. Metoda RequireClaim také v případě potřeby použije očekávané hodnoty pro deklarace identity. Pokud jsou hodnoty zadané, požadavek se splní pouze v případě, že uživatel má nárok na správný typ i jeden ze zadaných hodnot. Pokud používáte middlewaru ověřování nosiče JWT, všechny vlastnosti JWT bude k dispozici jako deklarace identity uživatelů.

Zajímá nejvíce zásad je vidět tady je v metodě třetí AddPolicy, protože používá vlastní autorizace požadavku. S použitím autorizace požadavky, můžete mít žádnou velkou kontrolu nad jak se provádí autorizace. Aby to fungovalo musí implementovat tyto typy:

-   Požadavky na typ, který je odvozen od IAuthorizationRequirement a který obsahuje pole, zadáním podrobností požadavku. V tomto příkladu to je věk pole pro typ MinimumAgeRequirement vzorku.

-   Obslužná rutina, která implementuje AuthorizationHandler&lt;T&gt;, kde T je typ IAuthorizationRequirement, která vyhovuje obslužné rutiny. Obslužná rutina musí implementovat metodu HandleRequirementAsync, která kontroluje, zda zadaný kontext, který obsahuje informace o uživateli splňuje požadavek.

Pokud uživatel splňuje požadavek volání kontextu. Úspěšné bude znamenat, že je uživatel autorizován. Pokud existuje více způsobů, že uživatel může uspokojení požadavku na autorizaci, můžete vytvořit více obslužných rutin.

Kromě registrace vlastních zásad pro požadavky s voláními AddPolicy, budete také muset zaregistrovat vlastní požadavek obslužné rutiny prostřednictvím injektáž závislostí (služby. AddTransient&lt;IAuthorizationHandler, MinimumAgeHandler&gt;()).

Příklad vlastní autorizace požadavku a obslužné rutiny pro kontrolu věk uživatele (podle deklarací identity DateOfBirth) je k dispozici v ASP.NET Core [autorizace dokumentaci](https://docs.asp.net/en/latest/security/authorization/policies.html).

## <a name="additional-resources"></a>Další zdroje

-   **Ověřování ASP.NET Core**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)

-   **Ověřování ASP.NET Core**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/introduction*](https://docs.microsoft.com/aspnet/core/security/authorization/introduction)

-   **Autorizace na základě rolí**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/roles*](https://docs.microsoft.com/aspnet/core/security/authorization/roles)

-   **Autorizace na základě zásad**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/policies*](https://docs.microsoft.com/aspnet/core/security/authorization/policies)

>[!div class="step-by-step"]
>[Předchozí](index.md)
>[další](developer-app-secrets-storage.md)