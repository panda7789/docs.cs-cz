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
# <a name="about-authorization-in-net-microservices-and-web-applications"></a><span data-ttu-id="20e4e-103">O autorizaci v mikroslužbách a webových aplikací .NET</span><span class="sxs-lookup"><span data-stu-id="20e4e-103">About authorization in .NET microservices and web applications</span></span>

<span data-ttu-id="20e4e-104">Po ověření ASP.NET Core webová rozhraní API nutné k autorizaci přístupu.</span><span class="sxs-lookup"><span data-stu-id="20e4e-104">After authentication, ASP.NET Core Web APIs need to authorize access.</span></span> <span data-ttu-id="20e4e-105">Tento proces umožňuje službě vytvořit rozhraní API dostupné pro některé ověřeného uživatele, ale ne pro všechny.</span><span class="sxs-lookup"><span data-stu-id="20e4e-105">This process allows a service to make APIs available to some authenticated users, but not to all.</span></span> <span data-ttu-id="20e4e-106">[Autorizace](https://docs.microsoft.com/aspnet/core/security/authorization/introduction) můžete provést podle role uživatelů nebo založená na vlastní zásadu, která by mohla obsahovat kontrola deklarace identity nebo jiných heuristické metody.</span><span class="sxs-lookup"><span data-stu-id="20e4e-106">[Authorization](https://docs.microsoft.com/aspnet/core/security/authorization/introduction) can be done based on users’ roles or based on custom policy, which might include inspecting claims or other heuristics.</span></span>

<span data-ttu-id="20e4e-107">Omezení přístupu ASP.NET Core MVC směrovací je stejně jednoduché jako použití Authorize atributu na metodu akce (nebo do třídy kontroleru, pokud všechny kontroleru akce vyžadují autorizace), jako je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="20e4e-107">Restricting access to an ASP.NET Core MVC route is as easy as applying an Authorize attribute to the action method (or to the controller’s class if all the controller’s actions require authorization), as shown in following example:</span></span>

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

<span data-ttu-id="20e4e-108">Ve výchozím nastavení bude přidání atributu Authorize bez parametrů omezovat přístup ověřeným uživatelům pro tento kontroler nebo akce.</span><span class="sxs-lookup"><span data-stu-id="20e4e-108">By default, adding an Authorize attribute without parameters will limit access to authenticated users for that controller or action.</span></span> <span data-ttu-id="20e4e-109">Pro další omezení rozhraní API k dispozici pouze pro konkrétního uživatele, je možné rozšířit atribut zadejte požadované role nebo zásady, které uživatelé musí splňovat.</span><span class="sxs-lookup"><span data-stu-id="20e4e-109">To further restrict an API to be available for only specific users, the attribute can be expanded to specify required roles or policies that users must satisfy.</span></span>

## <a name="implementing-role-based-authorization"></a><span data-ttu-id="20e4e-110">Implementace ověřování na základě role</span><span class="sxs-lookup"><span data-stu-id="20e4e-110">Implementing role-based authorization</span></span>

<span data-ttu-id="20e4e-111">ASP.NET Core Identity koncept předdefinovaných rolí.</span><span class="sxs-lookup"><span data-stu-id="20e4e-111">ASP.NET Core Identity has a built-in concept of roles.</span></span> <span data-ttu-id="20e4e-112">Kromě uživatelů ASP.NET Core Identity ukládá informace o různých rolích, které jsou využívané aplikací a kteří uživatelé jsou přiřazení rolím, které uchovává informace o.</span><span class="sxs-lookup"><span data-stu-id="20e4e-112">In addition to users, ASP.NET Core Identity stores information about different roles used by the application and keeps track of which users are assigned to which roles.</span></span> <span data-ttu-id="20e4e-113">Tato přiřazení je možné programově měnit pomocí RoleManager typ (která aktualizuje role do trvalého úložiště) a typ objektu UserManager., (který může přiřazení nebo zrušení přiřazení uživatele z role).</span><span class="sxs-lookup"><span data-stu-id="20e4e-113">These assignments can be changed programmatically with the RoleManager type (which updates roles in persisted storage) and UserManager type (which can assign or unassign users from roles).</span></span>

<span data-ttu-id="20e4e-114">Pokud ověřujete pomocí nosných tokenů JWT, naplníte ověřovací middleware nosiče ASP.NET Core JWT role uživatele na základě role deklarací identity v tokenu.</span><span class="sxs-lookup"><span data-stu-id="20e4e-114">If you are authenticating with JWT bearer tokens, the ASP.NET Core JWT bearer authentication middleware will populate a user’s roles based on role claims found in the token.</span></span> <span data-ttu-id="20e4e-115">Omezení přístupu k MVC akce nebo kontroleru pro uživatele v určitých rolích, můžete zahrnout parametr role v hlavičce autorizovat, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="20e4e-115">To limit access to an MVC action or controller to users in specific roles, you can include a Roles parameter in the Authorize header, as shown in the following example:</span></span>

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

<span data-ttu-id="20e4e-116">V tomto příkladu pouze uživatelé v rolích správce nebo PowerUser můžete přístup k rozhraním API v Ovládacích panelech kontroleru (jako je například provádění akce SetTime).</span><span class="sxs-lookup"><span data-stu-id="20e4e-116">In this example, only users in the Administrator or PowerUser roles can access APIs in the ControlPanel controller (such as executing the SetTime action).</span></span> <span data-ttu-id="20e4e-117">Vypnutí API je další omezen na povolení přístupu jenom na uživatele v roli správce.</span><span class="sxs-lookup"><span data-stu-id="20e4e-117">The ShutDown API is further restricted to allow access only to users in the Administrator role.</span></span>

<span data-ttu-id="20e4e-118">Tak, aby že se uživatel do více rolí, použijte více atributů autorizovat, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="20e4e-118">To require a user be in multiple roles, you use multiple Authorize attributes, as shown in the following example:</span></span>

```csharp
[Authorize(Roles = "Administrator, PowerUser")]
[Authorize(Roles = "RemoteEmployee ")]
[Authorize(Policy = "CustomPolicy")]
public ActionResult API1 ()
{
}
```

<span data-ttu-id="20e4e-119">V tomto příkladu volání API1, uživatel musí:</span><span class="sxs-lookup"><span data-stu-id="20e4e-119">In this example, to call API1, a user must:</span></span>

-   <span data-ttu-id="20e4e-120">V na správce *nebo* PowerUser role *a*</span><span class="sxs-lookup"><span data-stu-id="20e4e-120">Be in the Adminstrator *or* PowerUser role, *and*</span></span>

-   <span data-ttu-id="20e4e-121">V roli RemoteEmployee *a*</span><span class="sxs-lookup"><span data-stu-id="20e4e-121">Be in the RemoteEmployee role, *and*</span></span>

-   <span data-ttu-id="20e4e-122">Vlastní obslužnou rutinu pro autorizaci CustomPolicy splňovat.</span><span class="sxs-lookup"><span data-stu-id="20e4e-122">Satisfy a custom handler for CustomPolicy authorization.</span></span>

## <a name="implementing-policy-based-authorization"></a><span data-ttu-id="20e4e-123">Implementace ověřování na základě zásad</span><span class="sxs-lookup"><span data-stu-id="20e4e-123">Implementing policy-based authorization</span></span>

<span data-ttu-id="20e4e-124">Vlastní ověřovací pravidla lze také zapsat pomocí [zásad autorizace](https://docs.asp.net/en/latest/security/authorization/policies.html).</span><span class="sxs-lookup"><span data-stu-id="20e4e-124">Custom authorization rules can also be written using [authorization policies](https://docs.asp.net/en/latest/security/authorization/policies.html).</span></span> <span data-ttu-id="20e4e-125">Tato část poskytuje přehled.</span><span class="sxs-lookup"><span data-stu-id="20e4e-125">In this section we provide an overview.</span></span> <span data-ttu-id="20e4e-126">Další podrobnosti najdete v online [seminář o autorizaci ASP.NET](https://github.com/blowdart/AspNetAuthorizationWorkshop).</span><span class="sxs-lookup"><span data-stu-id="20e4e-126">More detail is available in the online [ASP.NET Authorization Workshop](https://github.com/blowdart/AspNetAuthorizationWorkshop).</span></span>

<span data-ttu-id="20e4e-127">Zásady autorizace zaregistrovaní v metodě Startup.ConfigureServices pomocí služby. Metoda AddAuthorization.</span><span class="sxs-lookup"><span data-stu-id="20e4e-127">Custom authorization policies are registered in the Startup.ConfigureServices method using the service.AddAuthorization method.</span></span> <span data-ttu-id="20e4e-128">Tato metoda přebírá delegáta, který konfiguruje AuthorizationOptions argument.</span><span class="sxs-lookup"><span data-stu-id="20e4e-128">This method takes a delegate that configures an AuthorizationOptions argument.</span></span>

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

<span data-ttu-id="20e4e-129">Jak je znázorněno v příkladu, lze přidružit různé druhy požadavky zásad.</span><span class="sxs-lookup"><span data-stu-id="20e4e-129">As shown in the example, policies can be associated with different types of requirements.</span></span> <span data-ttu-id="20e4e-130">Po registraci se tyto zásady, se můžou uplatnit na akce nebo kontroleru předáním název vaší zásady jako argument zásad Authorize atributu (například \[Authorize(Policy="EmployeesOnly")\]) může mít zásady více požadavků, ne jenom jeden (jak je znázorněno v těchto příkladech).</span><span class="sxs-lookup"><span data-stu-id="20e4e-130">After the policies are registered, they can be applied to an action or controller by passing the policy’s name as the Policy argument of the Authorize attribute (for example, \[Authorize(Policy="EmployeesOnly")\]) Policies can have multiple requirements, not just one (as shown in these examples).</span></span>

<span data-ttu-id="20e4e-131">V předchozím příkladu první volání AddPolicy je právě alternativní způsob autorizaci rolí.</span><span class="sxs-lookup"><span data-stu-id="20e4e-131">In the previous example, the first AddPolicy call is just an alternative way of authorizing by role.</span></span> <span data-ttu-id="20e4e-132">Pokud \[Authorize(Policy="AdministratorsOnly")\] platí pro rozhraní API, budou jenom uživatelé v roli správce k němu mít přístup.</span><span class="sxs-lookup"><span data-stu-id="20e4e-132">If \[Authorize(Policy="AdministratorsOnly")\] is applied to an API, only users in the Administrator role will be able to access it.</span></span>

<span data-ttu-id="20e4e-133">Druhé volání AddPolicy ukazuje snadný způsob, jak vyžadovat, konkrétní deklarace identity by měl být k dispozici pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="20e4e-133">The second AddPolicy call demonstrates an easy way to require that a particular claim should be present for the user.</span></span> <span data-ttu-id="20e4e-134">Metoda RequireClaim také v případě potřeby použije očekávané hodnoty pro deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="20e4e-134">The RequireClaim method also optionally takes expected values for the claim.</span></span> <span data-ttu-id="20e4e-135">Pokud jsou hodnoty zadané, požadavek se splní pouze v případě, že uživatel má nárok na správný typ i jeden ze zadaných hodnot.</span><span class="sxs-lookup"><span data-stu-id="20e4e-135">If values are specified, the requirement is met only if the user has both a claim of the correct type and one of the specified values.</span></span> <span data-ttu-id="20e4e-136">Pokud používáte middlewaru ověřování nosiče JWT, všechny vlastnosti JWT bude k dispozici jako deklarace identity uživatelů.</span><span class="sxs-lookup"><span data-stu-id="20e4e-136">If you are using the JWT bearer authentication middleware, all JWT properties will be available as user claims.</span></span>

<span data-ttu-id="20e4e-137">Zajímá nejvíce zásad je vidět tady je v metodě třetí AddPolicy, protože používá vlastní autorizace požadavku.</span><span class="sxs-lookup"><span data-stu-id="20e4e-137">The most interesting policy shown here is in the third AddPolicy method, because it uses a custom authorization requirement.</span></span> <span data-ttu-id="20e4e-138">S použitím autorizace požadavky, můžete mít žádnou velkou kontrolu nad jak se provádí autorizace.</span><span class="sxs-lookup"><span data-stu-id="20e4e-138">By using custom authorization requirements, you can have a great deal of control over how authorization is performed.</span></span> <span data-ttu-id="20e4e-139">Aby to fungovalo musí implementovat tyto typy:</span><span class="sxs-lookup"><span data-stu-id="20e4e-139">For this to work, you must implement these types:</span></span>

-   <span data-ttu-id="20e4e-140">Požadavky na typ, který je odvozen od IAuthorizationRequirement a který obsahuje pole, zadáním podrobností požadavku.</span><span class="sxs-lookup"><span data-stu-id="20e4e-140">A Requirements type that derives from IAuthorizationRequirement and that contains fields specifying the details of the requirement.</span></span> <span data-ttu-id="20e4e-141">V tomto příkladu to je věk pole pro typ MinimumAgeRequirement vzorku.</span><span class="sxs-lookup"><span data-stu-id="20e4e-141">In the example, this is an age field for the sample MinimumAgeRequirement type.</span></span>

-   <span data-ttu-id="20e4e-142">Obslužná rutina, která implementuje AuthorizationHandler&lt;T&gt;, kde T je typ IAuthorizationRequirement, která vyhovuje obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="20e4e-142">A handler that implements AuthorizationHandler&lt;T&gt;, where T is the type of IAuthorizationRequirement that the handler can satisfy.</span></span> <span data-ttu-id="20e4e-143">Obslužná rutina musí implementovat metodu HandleRequirementAsync, která kontroluje, zda zadaný kontext, který obsahuje informace o uživateli splňuje požadavek.</span><span class="sxs-lookup"><span data-stu-id="20e4e-143">The handler must implement the HandleRequirementAsync method, which checks whether a specified context that contains information about the user satisfies the requirement.</span></span>

<span data-ttu-id="20e4e-144">Pokud uživatel splňuje požadavek volání kontextu. Úspěšné bude znamenat, že je uživatel autorizován.</span><span class="sxs-lookup"><span data-stu-id="20e4e-144">If the user meets the requirement, a call to context.Succeed will indicate that the user is authorized.</span></span> <span data-ttu-id="20e4e-145">Pokud existuje více způsobů, že uživatel může uspokojení požadavku na autorizaci, můžete vytvořit více obslužných rutin.</span><span class="sxs-lookup"><span data-stu-id="20e4e-145">If there are multiple ways that a user might satisfy an authorization requirement, multiple handlers can be created.</span></span>

<span data-ttu-id="20e4e-146">Kromě registrace vlastních zásad pro požadavky s voláními AddPolicy, budete také muset zaregistrovat vlastní požadavek obslužné rutiny prostřednictvím injektáž závislostí (služby. AddTransient&lt;IAuthorizationHandler, MinimumAgeHandler&gt;()).</span><span class="sxs-lookup"><span data-stu-id="20e4e-146">In addition to registering custom policy requirements with AddPolicy calls, you also need to register custom requirement handlers via Dependency Injection (services.AddTransient&lt;IAuthorizationHandler, MinimumAgeHandler&gt;()).</span></span>

<span data-ttu-id="20e4e-147">Příklad vlastní autorizace požadavku a obslužné rutiny pro kontrolu věk uživatele (podle deklarací identity DateOfBirth) je k dispozici v ASP.NET Core [autorizace dokumentaci](https://docs.asp.net/en/latest/security/authorization/policies.html).</span><span class="sxs-lookup"><span data-stu-id="20e4e-147">An example of a custom authorization requirement and handler for checking a user’s age (based on a DateOfBirth claim) is available in the ASP.NET Core [authorization documentation](https://docs.asp.net/en/latest/security/authorization/policies.html).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="20e4e-148">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="20e4e-148">Additional resources</span></span>

-   <span data-ttu-id="20e4e-149">**Ověřování ASP.NET Core**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)</span><span class="sxs-lookup"><span data-stu-id="20e4e-149">**ASP.NET Core Authentication**
[*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)</span></span>

-   <span data-ttu-id="20e4e-150">**Ověřování ASP.NET Core**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/introduction*](https://docs.microsoft.com/aspnet/core/security/authorization/introduction)</span><span class="sxs-lookup"><span data-stu-id="20e4e-150">**ASP.NET Core Authorization**
[*https://docs.microsoft.com/aspnet/core/security/authorization/introduction*](https://docs.microsoft.com/aspnet/core/security/authorization/introduction)</span></span>

-   <span data-ttu-id="20e4e-151">**Autorizace na základě rolí**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/roles*](https://docs.microsoft.com/aspnet/core/security/authorization/roles)</span><span class="sxs-lookup"><span data-stu-id="20e4e-151">**Role based Authorization**
[*https://docs.microsoft.com/aspnet/core/security/authorization/roles*](https://docs.microsoft.com/aspnet/core/security/authorization/roles)</span></span>

-   <span data-ttu-id="20e4e-152">**Autorizace na základě zásad**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/policies*](https://docs.microsoft.com/aspnet/core/security/authorization/policies)</span><span class="sxs-lookup"><span data-stu-id="20e4e-152">**Custom Policy-Based Authorization**
[*https://docs.microsoft.com/aspnet/core/security/authorization/policies*](https://docs.microsoft.com/aspnet/core/security/authorization/policies)</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="20e4e-153">[Předchozí](index.md)
>[další](developer-app-secrets-storage.md)</span><span class="sxs-lookup"><span data-stu-id="20e4e-153">[Previous](index.md)
[Next](developer-app-secrets-storage.md)</span></span>