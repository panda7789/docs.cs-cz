---
title: O autorizace v rozhraní .NET mikroslužeb a webové aplikace
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | O autorizace v rozhraní .NET mikroslužeb a webové aplikace
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 2ea56f5a28d115fc5d91a98604b82565c8bf5c78
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="about-authorization-in-net-microservices-and-web-applications"></a>O autorizace v rozhraní .NET mikroslužeb a webové aplikace

Po ověření ASP.NET Core webovým rozhraním API nutné k autorizaci přístupu. Tento postup umožňuje službě aby rozhraní API dostupné některé ověřeným uživatelům, ale ne všechny. [Autorizace](https://docs.microsoft.com/aspnet/core/security/authorization/introduction) můžete provést podle role uživatelů nebo na základě vlastní zásad, která by mohla obsahovat zkontrolujete deklarace identity nebo jiné heuristiky.

Omezení přístupu k trasu ASP.NET Core MVC je stejně snadná jako použití autorizovat atribut do metody akce (nebo do třídy kontroleru, pokud autorizace vyžadovat akce všechny kontroleru) jako uvedené v následujícím příkladu:

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

Ve výchozím nastavení přidání atributu autorizovat bez parametrů omezí přístup ověřeným uživatelům pro tento kontroler nebo akce. Pro další omezení rozhraní API k dispozici jenom pro konkrétní uživatele, můžete rozšířit atribut určete požadované role nebo zásady, které uživatelé musí splňovat.

## <a name="implementing-role-based-authorization"></a>Implementace ověřování na základě rolí

Identita ASP.NET Core má integrovanou koncept rolí. Kromě uživatelů ASP.NET Core Identity ukládá informace o různých rolích, které používá aplikace a uchovává informace o uživatele, kteří jsou přiřazeny k jednotlivé role. Tato přiřazení lze změnit prostřednictvím kódu programu s RoleManager typu (který aktualizace rolí v trvalého úložiště) a typ nastavení UserManager, (který může přiřazení nebo zrušení přiřazení uživatele z role).

Pokud ověřujete pomocí nosných tokenů JWT, naplní middlewaru ověřování nosiče ASP.NET Core JWT role uživatele na základě role deklarací nalezen v tokenu. Omezit přístup k MVC akce nebo kontroleru pro uživatele v určitých rolích, můžete zahrnout parametr role v hlavičce autorizovat, jak je znázorněno v následujícím příkladu:

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

V tomto příkladu přístup pouze uživatelé v rolích správce nebo PowerUser rozhraní API v kontroleru ControlPanel (např. provádění akce SetTime). Rozhraní API vypnutí je další omezen na povolit přístup pouze uživatelům v roli správce.

Pokud chcete vyžadovat, že uživatel být ve více rolí, použijte několik atributů autorizovat, jak je znázorněno v následujícím příkladu:

```csharp
[Authorize(Roles = "Administrator, PowerUser")]
[Authorize(Roles = "RemoteEmployee ")]
[Authorize(Policy = "CustomPolicy")]
public ActionResult API1 ()
{
}
```

V tomto příkladu volání API1, uživatel musí:

-   V správce *nebo* PowerUser role *a*

-   V roli RemoteEmployee *a*

-   Splňovat vlastní obslužnou rutinu pro CustomPolicy autorizace.

## <a name="implementing-policy-based-authorization"></a>Implementace založená na zásadách autorizace

Vlastní autorizační pravidla můžete zapsat také pomocí [zásady autorizace](https://docs.asp.net/en/latest/security/authorization/policies.html). V této části poskytujeme Přehled. Další podrobnosti najdete v online [ASP.NET autorizace dílny](https://github.com/blowdart/AspNetAuthorizationWorkshop).

Zásady autorizace je zaregistrovaný v metodě Startup.ConfigureServices pomocí služby. Metoda AddAuthorization. Tato metoda přebírá delegáta, který nakonfiguruje AuthorizationOptions argument.

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

Jak je znázorněno v příkladu, zásady je možné přidružit s různými typy požadavků. Po registraci jsou zásady, se můžou uplatnit na akce nebo kontroleru předáním název zásad jako argument zásad atributu autorizovat (například \[Authorize(Policy="EmployeesOnly")\]) může mít zásady více požadavků, ne jenom jeden (jak je znázorněno v těchto příkladech).

V předchozím příkladu první volání AddPolicy je právě alternativní způsob autorizace role. Pokud \[Authorize(Policy="AdministratorsOnly")\] se použije pro rozhraní API pouze k přístupu budou mít uživatelé v roli správce.

Druhé volání AddPolicy představuje snadný způsob, jak vyžadovat, že konkrétní deklaraci identity by měla být k dispozici pro uživatele. Metoda RequireClaim volitelně přebírá očekávaných hodnot pro deklarace identity. Pokud jsou hodnoty zadané, požadavek se splní pouze v případě, že uživatel má oba správného typu deklarace identity a jedna ze zadaných hodnot. Pokud používáte middlewaru ověřování nosiče JWT, budou všechny vlastnosti JWT k dispozici jako deklarace identity uživatelů.

Nejvíce zajímavé zásady, které jsou tady uvedené je v metodě třetí AddPolicy, protože používá vlastní autorizace požadavek. Pomocí vlastní autorizace požadavky, můžete mít značnou část ovládat, jak se provádí autorizace. Tento postup vyžaduje je nutné implementovat tyto typy:

-   Požadavky na typ, která je odvozena od IAuthorizationRequirement a který obsahuje podrobnosti o požadavek na zadání pole. V příkladu je to na stáří pole pro typ MinimumAgeRequirement ukázka.

-   Obslužná rutina, která implementuje AuthorizationHandler&lt;T&gt;, kde T představuje typ IAuthorizationRequirement, která se může stát odpovědí obslužná rutina. Obslužná rutina musí implementovat metodu HandleRequirementAsync, která kontroluje, zda zadaný kontext, který obsahuje informace o uživateli splňuje požadavek.

Pokud uživatel splňuje požadavky, volání kontextu. Úspěšné bude znamenat, že je uživatel autorizovaný. V případě, že uživatel může uspokojení požadavku na autorizaci několika způsoby, můžete vytvořit více obslužných rutin.

Kromě registrace vlastních zásad pro požadavky s AddPolicy volání, musíte také zaregistrovat vlastní požadavek obslužné rutiny pomocí vkládání závislostí (služby. AddTransient&lt;IAuthorizationHandler, MinimumAgeHandler&gt;()).

Příklad vlastní autorizace požadavku a obslužné rutiny pro kontrolu stáří uživatele (podle deklaraci identity DateOfBirth) je k dispozici v ASP.NET Core [dokumentaci autorizačních](https://docs.asp.net/en/latest/security/authorization/policies.html).

## <a name="additional-resources"></a>Další zdroje

-   **Ověřování ASP.NET Core**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)

-   **Autorizace ASP.NET Core**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/introduction*](https://docs.microsoft.com/aspnet/core/security/authorization/introduction)

-   **Autorizace podle rolí**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/roles*](https://docs.microsoft.com/aspnet/core/security/authorization/roles)

-   **Autorizace uživatele na základě zásad**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/policies*](https://docs.microsoft.com/aspnet/core/security/authorization/policies)




>[!div class="step-by-step"]
[Předchozí] (index.md) [Další] (vývojáře app-tajné klíče storage.md)
