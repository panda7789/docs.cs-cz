---
title: O autorizaci v mikroslužbách a webových aplikacích v technologii .NET
description: Zabezpečení v mikroslužbách a webových aplikacích .NET – získáte přehled o hlavních možnostech ověřování v ASP.NET Core aplikací – na základě rolí a na základě zásad.
author: mjrousos
ms.author: wiwagn
ms.date: 10/19/2018
ms.openlocfilehash: 36cd8eaf7ffe78a29762398044dc1803adc1b200
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296468"
---
# <a name="about-authorization-in-net-microservices-and-web-applications"></a><span data-ttu-id="e68b6-103">O autorizaci v mikroslužbách a webových aplikacích v technologii .NET</span><span class="sxs-lookup"><span data-stu-id="e68b6-103">About authorization in .NET microservices and web applications</span></span>

<span data-ttu-id="e68b6-104">Po ověření musí ASP.NET Core webových rozhraní API autorizovat přístup.</span><span class="sxs-lookup"><span data-stu-id="e68b6-104">After authentication, ASP.NET Core Web APIs need to authorize access.</span></span> <span data-ttu-id="e68b6-105">Tento proces umožňuje službě zpřístupnit rozhraní API některým ověřeným uživatelům, ale ne všem.</span><span class="sxs-lookup"><span data-stu-id="e68b6-105">This process allows a service to make APIs available to some authenticated users, but not to all.</span></span> <span data-ttu-id="e68b6-106">[Autorizaci](/aspnet/core/security/authorization/introduction) můžete provádět na základě rolí uživatelů nebo na základě vlastních zásad, které můžou zahrnovat kontrolu deklarací identity nebo jiné heuristiky.</span><span class="sxs-lookup"><span data-stu-id="e68b6-106">[Authorization](/aspnet/core/security/authorization/introduction) can be done based on users’ roles or based on custom policy, which might include inspecting claims or other heuristics.</span></span>

<span data-ttu-id="e68b6-107">Omezení přístupu k ASP.NET Core trasám MVC je stejně snadné jako použití autorizačního atributu na metodu akce (nebo na třídu kontroleru, pokud všechny akce kontroleru vyžadují autorizaci), jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="e68b6-107">Restricting access to an ASP.NET Core MVC route is as easy as applying an Authorize attribute to the action method (or to the controller’s class if all the controller’s actions require authorization), as shown in following example:</span></span>

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

<span data-ttu-id="e68b6-108">Při přidání autorizačního atributu bez parametrů se ve výchozím nastavení omezí přístup k ověřeným uživatelům daného kontroleru nebo akce.</span><span class="sxs-lookup"><span data-stu-id="e68b6-108">By default, adding an Authorize attribute without parameters will limit access to authenticated users for that controller or action.</span></span> <span data-ttu-id="e68b6-109">Chcete-li dále omezit rozhraní API k dispozici pro konkrétní uživatele, lze atribut rozšířit tak, aby určoval požadované role nebo zásady, které uživatelé musí splnit.</span><span class="sxs-lookup"><span data-stu-id="e68b6-109">To further restrict an API to be available for only specific users, the attribute can be expanded to specify required roles or policies that users must satisfy.</span></span>

## <a name="implement-role-based-authorization"></a><span data-ttu-id="e68b6-110">Implementace autorizace na základě rolí</span><span class="sxs-lookup"><span data-stu-id="e68b6-110">Implement role-based authorization</span></span>

<span data-ttu-id="e68b6-111">ASP.NET Core identita má integrovaný koncept rolí.</span><span class="sxs-lookup"><span data-stu-id="e68b6-111">ASP.NET Core Identity has a built-in concept of roles.</span></span> <span data-ttu-id="e68b6-112">Kromě uživatelů ASP.NET Core identita ukládá informace o různých rolích používaných aplikací a udržuje přehled o tom, kteří uživatelé jsou přiřazeni k rolím.</span><span class="sxs-lookup"><span data-stu-id="e68b6-112">In addition to users, ASP.NET Core Identity stores information about different roles used by the application and keeps track of which users are assigned to which roles.</span></span> <span data-ttu-id="e68b6-113">Tato přiřazení je možné změnit programově s `RoleManager` typem, který aktualizuje role v trvalém úložišti, `UserManager` a typu, který může udělit nebo odvolávat role uživatelů.</span><span class="sxs-lookup"><span data-stu-id="e68b6-113">These assignments can be changed programmatically with the `RoleManager` type that updates roles in persisted storage, and the `UserManager` type that can grant or revoke roles from users.</span></span>

<span data-ttu-id="e68b6-114">Pokud ověřujete pomocí nosných tokenů JWT, naplní middleware ověřování Bearer ASP.NET Core JWT role uživatele na základě deklarací identity nalezených v tokenu.</span><span class="sxs-lookup"><span data-stu-id="e68b6-114">If you're authenticating with JWT bearer tokens, the ASP.NET Core JWT bearer authentication middleware will populate a user’s roles based on role claims found in the token.</span></span> <span data-ttu-id="e68b6-115">Chcete-li omezit přístup k akci nebo kontroler MVC na uživatele v konkrétních rolích, můžete do autorizační poznámky (atributu) zahrnout parametr role, jak je znázorněno v následujícím fragmentu kódu:</span><span class="sxs-lookup"><span data-stu-id="e68b6-115">To limit access to an MVC action or controller to users in specific roles, you can include a Roles parameter in the Authorize annotation (attribute), as shown in the following code fragment:</span></span>

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

<span data-ttu-id="e68b6-116">V tomto příkladu mají přístup k rozhraním API v řadiči ControlPanel (například provádění akce SetTime –) jenom uživatelé v rolích správce nebo PowerUser.</span><span class="sxs-lookup"><span data-stu-id="e68b6-116">In this example, only users in the Administrator or PowerUser roles can access APIs in the ControlPanel controller (such as executing the SetTime action).</span></span> <span data-ttu-id="e68b6-117">Rozhraní API pro vypnutí je dál omezené, aby povoloval přístup jenom uživatelům v roli správce.</span><span class="sxs-lookup"><span data-stu-id="e68b6-117">The ShutDown API is further restricted to allow access only to users in the Administrator role.</span></span>

<span data-ttu-id="e68b6-118">Pro vyžadování uživatele v několika rolích použijte více autorizačních atributů, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="e68b6-118">To require a user be in multiple roles, you use multiple Authorize attributes, as shown in the following example:</span></span>

```csharp
[Authorize(Roles = "Administrator, PowerUser")]
[Authorize(Roles = "RemoteEmployee ")]
[Authorize(Policy = "CustomPolicy")]
public ActionResult API1 ()
{
}
```

<span data-ttu-id="e68b6-119">V tomto příkladu pro volání API1 musí uživatel:</span><span class="sxs-lookup"><span data-stu-id="e68b6-119">In this example, to call API1, a user must:</span></span>

- <span data-ttu-id="e68b6-120">Být v roli správce *nebo* PowerUser *a*</span><span class="sxs-lookup"><span data-stu-id="e68b6-120">Be in the Administrator *or* PowerUser role, *and*</span></span>

- <span data-ttu-id="e68b6-121">Být v roli RemoteEmployee *a*</span><span class="sxs-lookup"><span data-stu-id="e68b6-121">Be in the RemoteEmployee role, *and*</span></span>

- <span data-ttu-id="e68b6-122">Vyhovět vlastní obslužné rutině pro autorizaci CustomPolicy</span><span class="sxs-lookup"><span data-stu-id="e68b6-122">Satisfy a custom handler for CustomPolicy authorization.</span></span>

## <a name="implement-policy-based-authorization"></a><span data-ttu-id="e68b6-123">Implementace autorizace na základě zásad</span><span class="sxs-lookup"><span data-stu-id="e68b6-123">Implement policy-based authorization</span></span>

<span data-ttu-id="e68b6-124">Vlastní autorizační pravidla se dají zapisovat taky pomocí [autorizačních zásad](https://docs.asp.net/en/latest/security/authorization/policies.html).</span><span class="sxs-lookup"><span data-stu-id="e68b6-124">Custom authorization rules can also be written using [authorization policies](https://docs.asp.net/en/latest/security/authorization/policies.html).</span></span> <span data-ttu-id="e68b6-125">V této části najdete přehled.</span><span class="sxs-lookup"><span data-stu-id="e68b6-125">This section provides an overview.</span></span> <span data-ttu-id="e68b6-126">Další informace najdete v tématu [ASP.NET Authorization Workshop](https://github.com/blowdart/AspNetAuthorizationWorkshop).</span><span class="sxs-lookup"><span data-stu-id="e68b6-126">For more information, see the [ASP.NET Authorization Workshop](https://github.com/blowdart/AspNetAuthorizationWorkshop).</span></span>

<span data-ttu-id="e68b6-127">Vlastní zásady autorizace jsou registrovány v metodě Startup. ConfigureServices pomocí služby. Metoda AddAuthorization</span><span class="sxs-lookup"><span data-stu-id="e68b6-127">Custom authorization policies are registered in the Startup.ConfigureServices method using the service.AddAuthorization method.</span></span> <span data-ttu-id="e68b6-128">Tato metoda přebírá delegáta, který konfiguruje argument AuthorizationOptions.</span><span class="sxs-lookup"><span data-stu-id="e68b6-128">This method takes a delegate that configures an AuthorizationOptions argument.</span></span>

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

<span data-ttu-id="e68b6-129">Jak je znázorněno v příkladu, mohou být zásady přidruženy k různým typům požadavků.</span><span class="sxs-lookup"><span data-stu-id="e68b6-129">As shown in the example, policies can be associated with different types of requirements.</span></span> <span data-ttu-id="e68b6-130">Po zaregistrování zásad je můžete použít pro akci nebo kontroler tak, že název této zásady předáte jako argument zásad autorizačního atributu (například `[Authorize(Policy="EmployeesOnly")]`), které mohou mít více požadavků, nikoli jen jeden (jak je uvedeno v těchto příklady).</span><span class="sxs-lookup"><span data-stu-id="e68b6-130">After the policies are registered, they can be applied to an action or controller by passing the policy’s name as the Policy argument of the Authorize attribute (for example, `[Authorize(Policy="EmployeesOnly")]`) Policies can have multiple requirements, not just one (as shown in these examples).</span></span>

<span data-ttu-id="e68b6-131">V předchozím příkladu je první volání AddPolicy pouze alternativním způsobem autorizace rolí.</span><span class="sxs-lookup"><span data-stu-id="e68b6-131">In the previous example, the first AddPolicy call is just an alternative way of authorizing by role.</span></span> <span data-ttu-id="e68b6-132">Pokud `[Authorize(Policy="AdministratorsOnly")]` se použije na rozhraní API, budou mít přístup jenom uživatelé v roli správce.</span><span class="sxs-lookup"><span data-stu-id="e68b6-132">If `[Authorize(Policy="AdministratorsOnly")]` is applied to an API, only users in the Administrator role will be able to access it.</span></span>

<span data-ttu-id="e68b6-133">Druhé <xref:Microsoft.AspNetCore.Authorization.AuthorizationOptions.AddPolicy%2A> volání ukazuje snadný způsob, jak vyžadovat, aby uživatel měl k dispozici konkrétní deklaraci identity.</span><span class="sxs-lookup"><span data-stu-id="e68b6-133">The second <xref:Microsoft.AspNetCore.Authorization.AuthorizationOptions.AddPolicy%2A> call demonstrates an easy way to require that a particular claim should be present for the user.</span></span> <span data-ttu-id="e68b6-134">Tato <xref:Microsoft.AspNetCore.Authorization.AuthorizationPolicyBuilder.RequireClaim%2A> metoda také volitelně přijímá očekávané hodnoty pro deklaraci identity.</span><span class="sxs-lookup"><span data-stu-id="e68b6-134">The <xref:Microsoft.AspNetCore.Authorization.AuthorizationPolicyBuilder.RequireClaim%2A> method also optionally takes expected values for the claim.</span></span> <span data-ttu-id="e68b6-135">Pokud jsou zadány hodnoty, je požadavek splněn pouze v případě, že uživatel má deklaraci identity správného typu a jednu ze zadaných hodnot.</span><span class="sxs-lookup"><span data-stu-id="e68b6-135">If values are specified, the requirement is met only if the user has both a claim of the correct type and one of the specified values.</span></span> <span data-ttu-id="e68b6-136">Pokud používáte middleware pro ověřování JWT Bearer, budou k dispozici všechny vlastnosti JWT jako deklarace identity uživatelů.</span><span class="sxs-lookup"><span data-stu-id="e68b6-136">If you're using the JWT bearer authentication middleware, all JWT properties will be available as user claims.</span></span>

<span data-ttu-id="e68b6-137">Nejzajímavější zásada uvedená tady je třetí `AddPolicy` metoda, protože používá vlastní autorizační požadavek.</span><span class="sxs-lookup"><span data-stu-id="e68b6-137">The most interesting policy shown here is in the third `AddPolicy` method, because it uses a custom authorization requirement.</span></span> <span data-ttu-id="e68b6-138">Pomocí vlastních autorizačních požadavků můžete mít velkou kontrolu nad tím, jak se provádí autorizace.</span><span class="sxs-lookup"><span data-stu-id="e68b6-138">By using custom authorization requirements, you can have a great deal of control over how authorization is performed.</span></span> <span data-ttu-id="e68b6-139">Aby to fungovalo, je nutné implementovat tyto typy:</span><span class="sxs-lookup"><span data-stu-id="e68b6-139">For this to work, you must implement these types:</span></span>

- <span data-ttu-id="e68b6-140">Typ požadavků, který je odvozen z <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> a obsahující pole určující Podrobnosti požadavku.</span><span class="sxs-lookup"><span data-stu-id="e68b6-140">A Requirements type that derives from <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> and that contains fields specifying the details of the requirement.</span></span> <span data-ttu-id="e68b6-141">V tomto příkladu je toto pole stáří pro typ vzorku `MinimumAgeRequirement` .</span><span class="sxs-lookup"><span data-stu-id="e68b6-141">In the example, this is an age field for the sample `MinimumAgeRequirement` type.</span></span>

- <span data-ttu-id="e68b6-142">Obslužná rutina, <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601>která implementuje, kde T je <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> typ, který obslužná rutina může splnit.</span><span class="sxs-lookup"><span data-stu-id="e68b6-142">A handler that implements <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601>, where T is the type of <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> that the handler can satisfy.</span></span> <span data-ttu-id="e68b6-143">Obslužná rutina musí implementovat <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601.HandleRequirementAsync%2A> metodu, která ověří, zda zadaný kontext, který obsahuje informace o uživateli, splňuje požadavek.</span><span class="sxs-lookup"><span data-stu-id="e68b6-143">The handler must implement the <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601.HandleRequirementAsync%2A> method, which checks whether a specified context that contains information about the user satisfies the requirement.</span></span>

<span data-ttu-id="e68b6-144">Pokud uživatel splňuje požadavek, volání metody `context.Succeed` indikuje, že uživatel je autorizován.</span><span class="sxs-lookup"><span data-stu-id="e68b6-144">If the user meets the requirement, a call to `context.Succeed` will indicate that the user is authorized.</span></span> <span data-ttu-id="e68b6-145">Existuje-li více způsobů, jak může uživatel splnit požadavek na autorizaci, lze vytvořit více obslužných rutin.</span><span class="sxs-lookup"><span data-stu-id="e68b6-145">If there are multiple ways that a user might satisfy an authorization requirement, multiple handlers can be created.</span></span>

<span data-ttu-id="e68b6-146">Kromě registrace požadavků na vlastní zásady s `AddPolicy` voláními musíte také registrovat vlastní obslužné rutiny požadavků prostřednictvím injektáže závislosti (`services.AddTransient<IAuthorizationHandler, MinimumAgeHandler>()`).</span><span class="sxs-lookup"><span data-stu-id="e68b6-146">In addition to registering custom policy requirements with `AddPolicy` calls, you also need to register custom requirement handlers via Dependency Injection (`services.AddTransient<IAuthorizationHandler, MinimumAgeHandler>()`).</span></span>

<span data-ttu-id="e68b6-147">Příkladem vlastního autorizačního požadavku a obslužné rutiny pro kontrolu stáří uživatele (na základě `DateOfBirth` deklarace) je k dispozici v dokumentaci k [autorizaci](https://docs.asp.net/en/latest/security/authorization/policies.html)ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="e68b6-147">An example of a custom authorization requirement and handler for checking a user’s age (based on a `DateOfBirth` claim) is available in the ASP.NET Core [authorization documentation](https://docs.asp.net/en/latest/security/authorization/policies.html).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="e68b6-148">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="e68b6-148">Additional resources</span></span>

- <span data-ttu-id="e68b6-149">**Ověřování ASP.NET Core** </span><span class="sxs-lookup"><span data-stu-id="e68b6-149">**ASP.NET Core Authentication** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authentication/identity](/aspnet/core/security/authentication/identity)

- <span data-ttu-id="e68b6-150">**ASP.NET Core autorizaci** </span><span class="sxs-lookup"><span data-stu-id="e68b6-150">**ASP.NET Core Authorization** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authorization/introduction](/aspnet/core/security/authorization/introduction)

- <span data-ttu-id="e68b6-151">**Autorizace na základě rolí** </span><span class="sxs-lookup"><span data-stu-id="e68b6-151">**Role-based Authorization** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authorization/roles](/aspnet/core/security/authorization/roles)

- <span data-ttu-id="e68b6-152">**Vlastní autorizace na základě zásad** </span><span class="sxs-lookup"><span data-stu-id="e68b6-152">**Custom Policy-Based Authorization** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authorization/policies](/aspnet/core/security/authorization/policies)

>[!div class="step-by-step"]
><span data-ttu-id="e68b6-153">[Předchozí](index.md)Další
>[](developer-app-secrets-storage.md)</span><span class="sxs-lookup"><span data-stu-id="e68b6-153">[Previous](index.md)
[Next](developer-app-secrets-storage.md)</span></span>
