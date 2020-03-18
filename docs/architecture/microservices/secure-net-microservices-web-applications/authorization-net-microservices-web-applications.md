---
title: O autorizaci v mikroslužbách a webových aplikacích v technologii .NET
description: Zabezpečení v .NET Microservices a webových aplikací – získat přehled o hlavních možnostech autorizace v ASP.NET základní aplikace – založené na rolích a na zásadách.
author: mjrousos
ms.date: 01/30/2020
ms.openlocfilehash: f6b69faceac9a9b4819212cc04f89080f3ddad56
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77501770"
---
# <a name="about-authorization-in-net-microservices-and-web-applications"></a>O autorizaci v mikroslužbách a webových aplikacích v technologii .NET

Po ověření je třeba ASP.NET základní webová api autorizovat přístup. Tento proces umožňuje službě zpřístupnit rozhraní API některým ověřeným uživatelům, ale ne všem. [Autorizaci](/aspnet/core/security/authorization/introduction) lze provést na základě rolí uživatelů nebo na základě vlastních zásad, které mohou zahrnovat kontrolu deklarací nebo jiné heuristiky.

Omezení přístupu k ASP.NET základní mvc trasy je stejně snadné jako použití Authorize atribut na metodu akce (nebo na třídu řadiče, pokud všechny akce řadiče vyžadují autorizaci), jak je znázorněno v následujícím příkladu:

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

Ve výchozím nastavení přidání atributu Authorize bez parametrů omezí přístup ověřeným uživatelům pro tento řadič nebo akci. Chcete-li dále omezit rozhraní API, které má být k dispozici pouze pro konkrétní uživatele, atribut lze rozbalit určit požadované role nebo zásady, které uživatelé musí splňovat.

## <a name="implement-role-based-authorization"></a>Implementace autorizace založené na rolích

ASP.NET Core Identity má předdefinovaný koncept rolí. Kromě uživatelů ASP.NET Core Identity ukládá informace o různých rolích používaných aplikací a sleduje, kteří uživatelé jsou přiřazeni ke kterým rolím. Tato přiřazení lze programově změnit `RoleManager` s typem, který aktualizuje role `UserManager` v trvalém úložišti, a typu, který může udělit nebo odvolat role od uživatelů.

Pokud ověřujete pomocí tokenů nosiče JWT, ASP.NET middleware pro ověřování nosiče JWT jádra JWT naplní role uživatele na základě deklarací rolí nalezených v tokenu. Chcete-li omezit přístup k akci MVC nebo kontroleru pro uživatele v určitých rolích, můžete zahrnout parametr Role do poznámky (atributu Autorizovat), jak je znázorněno v následujícím fragmentu kódu:

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

V tomto příkladu mají k rozhraním API v řadiči ControlPanel pouze uživatelé v rolích Administrator nebo PowerUser (například spuštění akce SetTime). Rozhraní SHUTDown API je dále omezeno tak, aby umožňovalo přístup pouze uživatelům v roli správce.

Chcete-li vyžadovat, aby byl uživatel ve více rolích, použijte více atributů Authorize, jak je znázorněno v následujícím příkladu:

```csharp
[Authorize(Roles = "Administrator, PowerUser")]
[Authorize(Roles = "RemoteEmployee ")]
[Authorize(Policy = "CustomPolicy")]
public ActionResult API1 ()
{
}
```

V tomto příkladu pro volání rozhraní API1 musí uživatel:

- Buďte v roli správce *nebo* PowerUser *a*

- Buďte v roli RemoteEmployee *a*

- Uspokojte vlastní obslužnou rutinu pro autorizaci CustomPolicy.

## <a name="implement-policy-based-authorization"></a>Implementace autorizace založené na zásadách

Vlastní autorizační pravidla lze také zapsat pomocí [zásad autorizace](https://docs.asp.net/en/latest/security/authorization/policies.html). Tato část obsahuje přehled. Další informace naleznete v [ASP.NET Autorizační workshop](https://github.com/blowdart/AspNetAuthorizationWorkshop).

Vlastní zásady autorizace jsou registrovány v Metodě Startup.ConfigureServices pomocí služby. AddAuthorization metoda. Tato metoda trvá delegáta, který konfiguruje Argument AuthorizationOptions.

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

Jak je znázorněno v příkladu, zásady mohou být přidruženy k různým typům požadavků. Po zaregistrování zásad je lze použít na akci nebo řadič předáním názvu zásady jako argument `[Authorize(Policy="EmployeesOnly")]`zásad atributu Authorize (například ) Zásady mohou mít více požadavků, nikoli pouze jeden (jak je znázorněno v těchto příkladech).

V předchozím příkladu první AddPolicy volání je pouze alternativní způsob autorizace podle role. Pokud `[Authorize(Policy="AdministratorsOnly")]` je použito rozhraní API, budou k němu mít přístup pouze uživatelé v roli správce.

Druhý <xref:Microsoft.AspNetCore.Authorization.AuthorizationOptions.AddPolicy%2A> hovor ukazuje snadný způsob, jak vyžadovat, aby konkrétní deklarace měla být přítomna pro uživatele. Metoda <xref:Microsoft.AspNetCore.Authorization.AuthorizationPolicyBuilder.RequireClaim%2A> také volitelně přebírá očekávané hodnoty deklarace. Pokud jsou zadány hodnoty, požadavek je splněn pouze v případě, že uživatel má deklaraci správného typu a jednu ze zadaných hodnot. Pokud používáte middleware pro ověřování nosiče JWT, všechny vlastnosti JWT budou k dispozici jako deklarace identity uživatelů.

Nejzajímavější zásady zde je ve `AddPolicy` třetí metodě, protože používá požadavek na vlastní autorizaci. Pomocí vlastních požadavků na autorizaci můžete mít velkou kontrolu nad tím, jak se autorizace provádí. Aby to fungovalo, je nutné implementovat tyto typy:

- A Požadavky typ, <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> který je odvozen od a který obsahuje pole určující podrobnosti požadavku. V příkladu se jedná o věkové `MinimumAgeRequirement` pole pro typ vzorku.

- Obslužná <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601>rutina, která <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> implementuje , kde T je typ, který obslužná rutina může uspokojit. Obslužná <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601.HandleRequirementAsync%2A> rutina musí implementovat metodu, která zkontroluje, zda zadaný kontext, který obsahuje informace o uživateli, splňuje požadavek.

Pokud uživatel splňuje požadavek, `context.Succeed` volání bude znamenat, že uživatel je oprávněn. Pokud existuje více způsobů, které uživatel může splňovat požadavek na autorizaci, lze vytvořit více obslužných rutin.

Kromě registrace vlastních požadavků `AddPolicy` zásad s voláními je také nutné zaregistrovat`services.AddTransient<IAuthorizationHandler, MinimumAgeHandler>()`vlastní obslužné rutiny požadavků prostřednictvím vkládání závislostí ( ).

Příklad požadavku na vlastní autorizaci a obslužné rutiny `DateOfBirth` pro kontrolu věku uživatele (na základě deklarace) je k dispozici v dokumentaci k [autorizaci](https://docs.asp.net/en/latest/security/authorization/policies.html)ASP.NET jádra .

## <a name="additional-resources"></a>Další zdroje

- **ověřování ASP.NET jádra** \
  [https://docs.microsoft.com/aspnet/core/security/authentication/identity](/aspnet/core/security/authentication/identity)

- **ASP.NET základní autorizace** \
  [https://docs.microsoft.com/aspnet/core/security/authorization/introduction](/aspnet/core/security/authorization/introduction)

- **Autorizace založená na rolích** \
  [https://docs.microsoft.com/aspnet/core/security/authorization/roles](/aspnet/core/security/authorization/roles)

- **Vlastní autorizace založená na zásadách** \
  [https://docs.microsoft.com/aspnet/core/security/authorization/policies](/aspnet/core/security/authorization/policies)

>[!div class="step-by-step"]
>[Předchozí](index.md)
>[další](developer-app-secrets-storage.md)
