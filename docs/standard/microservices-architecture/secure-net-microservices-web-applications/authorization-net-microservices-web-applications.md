---
title: O autorizaci v mikroslužbách a webových aplikací .NET
description: Zabezpečení v rozhraní .NET Mikroslužeb a webových aplikací – přehled možnosti hlavní autorizace v aplikacích ASP.NET Core – na základě rolí a na základě zásad.
author: mjrousos
ms.author: wiwagn
ms.date: 10/19/2018
ms.openlocfilehash: 36cd8eaf7ffe78a29762398044dc1803adc1b200
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2019
ms.locfileid: "58466358"
---
# <a name="about-authorization-in-net-microservices-and-web-applications"></a><span data-ttu-id="38445-103">O autorizaci v mikroslužbách a webových aplikací .NET</span><span class="sxs-lookup"><span data-stu-id="38445-103">About authorization in .NET microservices and web applications</span></span>

<span data-ttu-id="38445-104">Po ověření ASP.NET Core webová rozhraní API nutné k autorizaci přístupu.</span><span class="sxs-lookup"><span data-stu-id="38445-104">After authentication, ASP.NET Core Web APIs need to authorize access.</span></span> <span data-ttu-id="38445-105">Tento proces umožňuje službě vytvořit rozhraní API dostupné pro některé ověřeného uživatele, ale ne pro všechny.</span><span class="sxs-lookup"><span data-stu-id="38445-105">This process allows a service to make APIs available to some authenticated users, but not to all.</span></span> <span data-ttu-id="38445-106">[Autorizace](/aspnet/core/security/authorization/introduction) můžete provést podle role uživatelů nebo založená na vlastní zásadu, která by mohla obsahovat kontrola deklarace identity nebo jiných heuristické metody.</span><span class="sxs-lookup"><span data-stu-id="38445-106">[Authorization](/aspnet/core/security/authorization/introduction) can be done based on users’ roles or based on custom policy, which might include inspecting claims or other heuristics.</span></span>

<span data-ttu-id="38445-107">Omezení přístupu ASP.NET Core MVC směrovací je stejně jednoduché jako použití Authorize atributu na metodu akce (nebo do třídy kontroleru, pokud všechny kontroleru akce vyžadují autorizace), jako je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="38445-107">Restricting access to an ASP.NET Core MVC route is as easy as applying an Authorize attribute to the action method (or to the controller’s class if all the controller’s actions require authorization), as shown in following example:</span></span>

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

<span data-ttu-id="38445-108">Ve výchozím nastavení bude přidání atributu Authorize bez parametrů omezovat přístup ověřeným uživatelům pro tento kontroler nebo akce.</span><span class="sxs-lookup"><span data-stu-id="38445-108">By default, adding an Authorize attribute without parameters will limit access to authenticated users for that controller or action.</span></span> <span data-ttu-id="38445-109">Pro další omezení rozhraní API k dispozici pouze pro konkrétního uživatele, je možné rozšířit atribut zadejte požadované role nebo zásady, které uživatelé musí splňovat.</span><span class="sxs-lookup"><span data-stu-id="38445-109">To further restrict an API to be available for only specific users, the attribute can be expanded to specify required roles or policies that users must satisfy.</span></span>

## <a name="implement-role-based-authorization"></a><span data-ttu-id="38445-110">Autorizace na základě rolí implementujte</span><span class="sxs-lookup"><span data-stu-id="38445-110">Implement role-based authorization</span></span>

<span data-ttu-id="38445-111">ASP.NET Core Identity koncept předdefinovaných rolí.</span><span class="sxs-lookup"><span data-stu-id="38445-111">ASP.NET Core Identity has a built-in concept of roles.</span></span> <span data-ttu-id="38445-112">Kromě uživatelů ASP.NET Core Identity ukládá informace o různých rolích, které jsou využívané aplikací a kteří uživatelé jsou přiřazení rolím, které uchovává informace o.</span><span class="sxs-lookup"><span data-stu-id="38445-112">In addition to users, ASP.NET Core Identity stores information about different roles used by the application and keeps track of which users are assigned to which roles.</span></span> <span data-ttu-id="38445-113">Tato přiřazení je možné programově měnit pomocí `RoleManager` typ, který aktualizuje role do trvalého úložiště a `UserManager` typ, který může udělit nebo odvolat rolí uživatelů.</span><span class="sxs-lookup"><span data-stu-id="38445-113">These assignments can be changed programmatically with the `RoleManager` type that updates roles in persisted storage, and the `UserManager` type that can grant or revoke roles from users.</span></span>

<span data-ttu-id="38445-114">Pokud se ověřování pomocí nosných tokenů JWT, naplníte ověřovací middleware nosiče ASP.NET Core JWT role uživatele na základě role deklarací identity v tokenu.</span><span class="sxs-lookup"><span data-stu-id="38445-114">If you're authenticating with JWT bearer tokens, the ASP.NET Core JWT bearer authentication middleware will populate a user’s roles based on role claims found in the token.</span></span> <span data-ttu-id="38445-115">Omezit přístup k MVC akce nebo kontroleru pro uživatele v určitých rolích, můžete zahrnout role parametr v poznámce Authorize (atribut), jak je znázorněno v následující fragment kódu:</span><span class="sxs-lookup"><span data-stu-id="38445-115">To limit access to an MVC action or controller to users in specific roles, you can include a Roles parameter in the Authorize annotation (attribute), as shown in the following code fragment:</span></span>

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

<span data-ttu-id="38445-116">V tomto příkladu pouze uživatelé v rolích správce nebo PowerUser můžete přístup k rozhraním API v Ovládacích panelech kontroleru (jako je například provádění akce SetTime).</span><span class="sxs-lookup"><span data-stu-id="38445-116">In this example, only users in the Administrator or PowerUser roles can access APIs in the ControlPanel controller (such as executing the SetTime action).</span></span> <span data-ttu-id="38445-117">Vypnutí API je další omezen na povolení přístupu jenom na uživatele v roli správce.</span><span class="sxs-lookup"><span data-stu-id="38445-117">The ShutDown API is further restricted to allow access only to users in the Administrator role.</span></span>

<span data-ttu-id="38445-118">Tak, aby že se uživatel do více rolí, použijte více atributů autorizovat, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="38445-118">To require a user be in multiple roles, you use multiple Authorize attributes, as shown in the following example:</span></span>

```csharp
[Authorize(Roles = "Administrator, PowerUser")]
[Authorize(Roles = "RemoteEmployee ")]
[Authorize(Policy = "CustomPolicy")]
public ActionResult API1 ()
{
}
```

<span data-ttu-id="38445-119">V tomto příkladu volání API1, uživatel musí:</span><span class="sxs-lookup"><span data-stu-id="38445-119">In this example, to call API1, a user must:</span></span>

- <span data-ttu-id="38445-120">V správce *nebo* PowerUser role *a*</span><span class="sxs-lookup"><span data-stu-id="38445-120">Be in the Administrator *or* PowerUser role, *and*</span></span>

- <span data-ttu-id="38445-121">V roli RemoteEmployee *a*</span><span class="sxs-lookup"><span data-stu-id="38445-121">Be in the RemoteEmployee role, *and*</span></span>

- <span data-ttu-id="38445-122">Vlastní obslužnou rutinu pro autorizaci CustomPolicy splňovat.</span><span class="sxs-lookup"><span data-stu-id="38445-122">Satisfy a custom handler for CustomPolicy authorization.</span></span>

## <a name="implement-policy-based-authorization"></a><span data-ttu-id="38445-123">Implementovat na základě zásad autorizace</span><span class="sxs-lookup"><span data-stu-id="38445-123">Implement policy-based authorization</span></span>

<span data-ttu-id="38445-124">Vlastní ověřovací pravidla lze také zapsat pomocí [zásad autorizace](https://docs.asp.net/en/latest/security/authorization/policies.html).</span><span class="sxs-lookup"><span data-stu-id="38445-124">Custom authorization rules can also be written using [authorization policies](https://docs.asp.net/en/latest/security/authorization/policies.html).</span></span> <span data-ttu-id="38445-125">Tato část obsahuje přehled.</span><span class="sxs-lookup"><span data-stu-id="38445-125">This section provides an overview.</span></span> <span data-ttu-id="38445-126">Další informace najdete v tématu [seminář o autorizaci ASP.NET](https://github.com/blowdart/AspNetAuthorizationWorkshop).</span><span class="sxs-lookup"><span data-stu-id="38445-126">For more information, see the [ASP.NET Authorization Workshop](https://github.com/blowdart/AspNetAuthorizationWorkshop).</span></span>

<span data-ttu-id="38445-127">Zásady autorizace zaregistrovaní v metodě Startup.ConfigureServices pomocí služby. Metoda AddAuthorization.</span><span class="sxs-lookup"><span data-stu-id="38445-127">Custom authorization policies are registered in the Startup.ConfigureServices method using the service.AddAuthorization method.</span></span> <span data-ttu-id="38445-128">Tato metoda přebírá delegáta, který konfiguruje AuthorizationOptions argument.</span><span class="sxs-lookup"><span data-stu-id="38445-128">This method takes a delegate that configures an AuthorizationOptions argument.</span></span>

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

<span data-ttu-id="38445-129">Jak je znázorněno v příkladu, lze přidružit různé druhy požadavky zásad.</span><span class="sxs-lookup"><span data-stu-id="38445-129">As shown in the example, policies can be associated with different types of requirements.</span></span> <span data-ttu-id="38445-130">Po registraci se tyto zásady, se můžou uplatnit na akce nebo kontroleru předáním název vaší zásady jako argument zásad Authorize atributu (například `[Authorize(Policy="EmployeesOnly")]`) zásad může mít několik požadavků, ne jenom jeden (jak je znázorněno v těchto Příklady).</span><span class="sxs-lookup"><span data-stu-id="38445-130">After the policies are registered, they can be applied to an action or controller by passing the policy’s name as the Policy argument of the Authorize attribute (for example, `[Authorize(Policy="EmployeesOnly")]`) Policies can have multiple requirements, not just one (as shown in these examples).</span></span>

<span data-ttu-id="38445-131">V předchozím příkladu první volání AddPolicy je právě alternativní způsob autorizaci rolí.</span><span class="sxs-lookup"><span data-stu-id="38445-131">In the previous example, the first AddPolicy call is just an alternative way of authorizing by role.</span></span> <span data-ttu-id="38445-132">Pokud `[Authorize(Policy="AdministratorsOnly")]` platí pro rozhraní API, budou jenom uživatelé v roli správce k němu mít přístup.</span><span class="sxs-lookup"><span data-stu-id="38445-132">If `[Authorize(Policy="AdministratorsOnly")]` is applied to an API, only users in the Administrator role will be able to access it.</span></span>

<span data-ttu-id="38445-133">Druhá <xref:Microsoft.AspNetCore.Authorization.AuthorizationOptions.AddPolicy%2A> volání ukazuje snadný způsob, jak vyžadovat, konkrétní deklarace identity by měl být k dispozici pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="38445-133">The second <xref:Microsoft.AspNetCore.Authorization.AuthorizationOptions.AddPolicy%2A> call demonstrates an easy way to require that a particular claim should be present for the user.</span></span> <span data-ttu-id="38445-134"><xref:Microsoft.AspNetCore.Authorization.AuthorizationPolicyBuilder.RequireClaim%2A> Metoda přijímá také v případě potřeby očekávané hodnoty pro deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="38445-134">The <xref:Microsoft.AspNetCore.Authorization.AuthorizationPolicyBuilder.RequireClaim%2A> method also optionally takes expected values for the claim.</span></span> <span data-ttu-id="38445-135">Pokud jsou hodnoty zadané, požadavek se splní pouze v případě, že uživatel má nárok na správný typ i jeden ze zadaných hodnot.</span><span class="sxs-lookup"><span data-stu-id="38445-135">If values are specified, the requirement is met only if the user has both a claim of the correct type and one of the specified values.</span></span> <span data-ttu-id="38445-136">Pokud používáte middlewaru ověřování nosiče JWT, všechny vlastnosti JWT bude k dispozici jako deklarace identity uživatelů.</span><span class="sxs-lookup"><span data-stu-id="38445-136">If you're using the JWT bearer authentication middleware, all JWT properties will be available as user claims.</span></span>

<span data-ttu-id="38445-137">Zajímá nejvíce zásad je znázorněno zde je v třetí `AddPolicy` metody, protože používá vlastní autorizace požadavku.</span><span class="sxs-lookup"><span data-stu-id="38445-137">The most interesting policy shown here is in the third `AddPolicy` method, because it uses a custom authorization requirement.</span></span> <span data-ttu-id="38445-138">S použitím autorizace požadavky, můžete mít žádnou velkou kontrolu nad jak se provádí autorizace.</span><span class="sxs-lookup"><span data-stu-id="38445-138">By using custom authorization requirements, you can have a great deal of control over how authorization is performed.</span></span> <span data-ttu-id="38445-139">Aby to fungovalo musí implementovat tyto typy:</span><span class="sxs-lookup"><span data-stu-id="38445-139">For this to work, you must implement these types:</span></span>

- <span data-ttu-id="38445-140">Požadavky na typ, který je odvozen od <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> a který obsahuje pole, zadáním podrobností požadavku.</span><span class="sxs-lookup"><span data-stu-id="38445-140">A Requirements type that derives from <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> and that contains fields specifying the details of the requirement.</span></span> <span data-ttu-id="38445-141">V tomto příkladu to je věk pole pro ukázku `MinimumAgeRequirement` typu.</span><span class="sxs-lookup"><span data-stu-id="38445-141">In the example, this is an age field for the sample `MinimumAgeRequirement` type.</span></span>

- <span data-ttu-id="38445-142">Obslužná rutina, která implementuje <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601>, kde T je typ <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> , která vyhovuje obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="38445-142">A handler that implements <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601>, where T is the type of <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> that the handler can satisfy.</span></span> <span data-ttu-id="38445-143">Obslužná rutina musí implementovat <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601.HandleRequirementAsync%2A> metodu, která kontroluje, zda zadaný kontext, který obsahuje informace o uživateli splňuje požadavek.</span><span class="sxs-lookup"><span data-stu-id="38445-143">The handler must implement the <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601.HandleRequirementAsync%2A> method, which checks whether a specified context that contains information about the user satisfies the requirement.</span></span>

<span data-ttu-id="38445-144">Pokud uživatel splňuje požadavky, volání `context.Succeed` indikuje, že je uživatel autorizován.</span><span class="sxs-lookup"><span data-stu-id="38445-144">If the user meets the requirement, a call to `context.Succeed` will indicate that the user is authorized.</span></span> <span data-ttu-id="38445-145">Pokud existuje více způsobů, že uživatel může uspokojení požadavku na autorizaci, můžete vytvořit více obslužných rutin.</span><span class="sxs-lookup"><span data-stu-id="38445-145">If there are multiple ways that a user might satisfy an authorization requirement, multiple handlers can be created.</span></span>

<span data-ttu-id="38445-146">Kromě registrace vlastních zásad pro požadavky s `AddPolicy` volání, budete také muset zaregistrovat vlastní požadavek obslužné rutiny prostřednictvím injektáž závislostí (`services.AddTransient<IAuthorizationHandler, MinimumAgeHandler>()`).</span><span class="sxs-lookup"><span data-stu-id="38445-146">In addition to registering custom policy requirements with `AddPolicy` calls, you also need to register custom requirement handlers via Dependency Injection (`services.AddTransient<IAuthorizationHandler, MinimumAgeHandler>()`).</span></span>

<span data-ttu-id="38445-147">Příklad vlastní autorizace požadavku a obslužné rutiny pro kontrolu věk uživatele (na základě `DateOfBirth` deklarace identity) je k dispozici v ASP.NET Core [autorizace dokumentaci](https://docs.asp.net/en/latest/security/authorization/policies.html).</span><span class="sxs-lookup"><span data-stu-id="38445-147">An example of a custom authorization requirement and handler for checking a user’s age (based on a `DateOfBirth` claim) is available in the ASP.NET Core [authorization documentation](https://docs.asp.net/en/latest/security/authorization/policies.html).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="38445-148">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="38445-148">Additional resources</span></span>

- <span data-ttu-id="38445-149">**ASP.NET Core Authentication** \\</span><span class="sxs-lookup"><span data-stu-id="38445-149">**ASP.NET Core Authentication** \\</span></span>
  [https://docs.microsoft.com/aspnet/core/security/authentication/identity](/aspnet/core/security/authentication/identity)

- <span data-ttu-id="38445-150">**Ověřování ASP.NET Core** \\</span><span class="sxs-lookup"><span data-stu-id="38445-150">**ASP.NET Core Authorization** \\</span></span>
  [https://docs.microsoft.com/aspnet/core/security/authorization/introduction](/aspnet/core/security/authorization/introduction)

- <span data-ttu-id="38445-151">**Autorizace na základě rolí** \\</span><span class="sxs-lookup"><span data-stu-id="38445-151">**Role-based Authorization** \\</span></span>
  [https://docs.microsoft.com/aspnet/core/security/authorization/roles](/aspnet/core/security/authorization/roles)

- <span data-ttu-id="38445-152">**Autorizace na základě zásad** \\</span><span class="sxs-lookup"><span data-stu-id="38445-152">**Custom Policy-Based Authorization** \\</span></span>
  [https://docs.microsoft.com/aspnet/core/security/authorization/policies](/aspnet/core/security/authorization/policies)

>[!div class="step-by-step"]
><span data-ttu-id="38445-153">[Předchozí](index.md)
>[další](developer-app-secrets-storage.md)</span><span class="sxs-lookup"><span data-stu-id="38445-153">[Previous](index.md)
[Next](developer-app-secrets-storage.md)</span></span>
