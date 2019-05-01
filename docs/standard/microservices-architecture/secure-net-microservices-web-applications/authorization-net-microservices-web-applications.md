---
title: O autorizaci v mikroslužbách a webových aplikacích v technologii .NET
description: Zabezpečení v rozhraní .NET Mikroslužeb a webových aplikací – přehled možnosti hlavní autorizace v aplikacích ASP.NET Core – na základě rolí a na základě zásad.
author: mjrousos
ms.author: wiwagn
ms.date: 10/19/2018
ms.openlocfilehash: 36cd8eaf7ffe78a29762398044dc1803adc1b200
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62019500"
---
# <a name="about-authorization-in-net-microservices-and-web-applications"></a>O autorizaci v mikroslužbách a webových aplikacích v technologii .NET

Po ověření ASP.NET Core webová rozhraní API nutné k autorizaci přístupu. Tento proces umožňuje službě vytvořit rozhraní API dostupné pro některé ověřeného uživatele, ale ne pro všechny. [Autorizace](/aspnet/core/security/authorization/introduction) můžete provést podle role uživatelů nebo založená na vlastní zásadu, která by mohla obsahovat kontrola deklarace identity nebo jiných heuristické metody.

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

## <a name="implement-role-based-authorization"></a>Autorizace na základě rolí implementujte

ASP.NET Core Identity koncept předdefinovaných rolí. Kromě uživatelů ASP.NET Core Identity ukládá informace o různých rolích, které jsou využívané aplikací a kteří uživatelé jsou přiřazení rolím, které uchovává informace o. Tato přiřazení je možné programově měnit pomocí `RoleManager` typ, který aktualizuje role do trvalého úložiště a `UserManager` typ, který může udělit nebo odvolat rolí uživatelů.

Pokud se ověřování pomocí nosných tokenů JWT, naplníte ověřovací middleware nosiče ASP.NET Core JWT role uživatele na základě role deklarací identity v tokenu. Omezit přístup k MVC akce nebo kontroleru pro uživatele v určitých rolích, můžete zahrnout role parametr v poznámce Authorize (atribut), jak je znázorněno v následující fragment kódu:

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

- V správce *nebo* PowerUser role *a*

- V roli RemoteEmployee *a*

- Vlastní obslužnou rutinu pro autorizaci CustomPolicy splňovat.

## <a name="implement-policy-based-authorization"></a>Implementovat na základě zásad autorizace

Vlastní ověřovací pravidla lze také zapsat pomocí [zásad autorizace](https://docs.asp.net/en/latest/security/authorization/policies.html). Tato část obsahuje přehled. Další informace najdete v tématu [seminář o autorizaci ASP.NET](https://github.com/blowdart/AspNetAuthorizationWorkshop).

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

Jak je znázorněno v příkladu, lze přidružit různé druhy požadavky zásad. Po registraci se tyto zásady, se můžou uplatnit na akce nebo kontroleru předáním název vaší zásady jako argument zásad Authorize atributu (například `[Authorize(Policy="EmployeesOnly")]`) zásad může mít několik požadavků, ne jenom jeden (jak je znázorněno v těchto Příklady).

V předchozím příkladu první volání AddPolicy je právě alternativní způsob autorizaci rolí. Pokud `[Authorize(Policy="AdministratorsOnly")]` platí pro rozhraní API, budou jenom uživatelé v roli správce k němu mít přístup.

Druhá <xref:Microsoft.AspNetCore.Authorization.AuthorizationOptions.AddPolicy%2A> volání ukazuje snadný způsob, jak vyžadovat, konkrétní deklarace identity by měl být k dispozici pro uživatele. <xref:Microsoft.AspNetCore.Authorization.AuthorizationPolicyBuilder.RequireClaim%2A> Metoda přijímá také v případě potřeby očekávané hodnoty pro deklarace identity. Pokud jsou hodnoty zadané, požadavek se splní pouze v případě, že uživatel má nárok na správný typ i jeden ze zadaných hodnot. Pokud používáte middlewaru ověřování nosiče JWT, všechny vlastnosti JWT bude k dispozici jako deklarace identity uživatelů.

Zajímá nejvíce zásad je znázorněno zde je v třetí `AddPolicy` metody, protože používá vlastní autorizace požadavku. S použitím autorizace požadavky, můžete mít žádnou velkou kontrolu nad jak se provádí autorizace. Aby to fungovalo musí implementovat tyto typy:

- Požadavky na typ, který je odvozen od <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> a který obsahuje pole, zadáním podrobností požadavku. V tomto příkladu to je věk pole pro ukázku `MinimumAgeRequirement` typu.

- Obslužná rutina, která implementuje <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601>, kde T je typ <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> , která vyhovuje obslužné rutiny. Obslužná rutina musí implementovat <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601.HandleRequirementAsync%2A> metodu, která kontroluje, zda zadaný kontext, který obsahuje informace o uživateli splňuje požadavek.

Pokud uživatel splňuje požadavky, volání `context.Succeed` indikuje, že je uživatel autorizován. Pokud existuje více způsobů, že uživatel může uspokojení požadavku na autorizaci, můžete vytvořit více obslužných rutin.

Kromě registrace vlastních zásad pro požadavky s `AddPolicy` volání, budete také muset zaregistrovat vlastní požadavek obslužné rutiny prostřednictvím injektáž závislostí (`services.AddTransient<IAuthorizationHandler, MinimumAgeHandler>()`).

Příklad vlastní autorizace požadavku a obslužné rutiny pro kontrolu věk uživatele (na základě `DateOfBirth` deklarace identity) je k dispozici v ASP.NET Core [autorizace dokumentaci](https://docs.asp.net/en/latest/security/authorization/policies.html).

## <a name="additional-resources"></a>Další zdroje

- **ASP.NET Core Authentication** \
  [https://docs.microsoft.com/aspnet/core/security/authentication/identity](/aspnet/core/security/authentication/identity)

- **Ověřování ASP.NET Core** \
  [https://docs.microsoft.com/aspnet/core/security/authorization/introduction](/aspnet/core/security/authorization/introduction)

- **Autorizace na základě rolí** \
  [https://docs.microsoft.com/aspnet/core/security/authorization/roles](/aspnet/core/security/authorization/roles)

- **Autorizace na základě zásad** \
  [https://docs.microsoft.com/aspnet/core/security/authorization/policies](/aspnet/core/security/authorization/policies)

>[!div class="step-by-step"]
>[Předchozí](index.md)
>[další](developer-app-secrets-storage.md)
