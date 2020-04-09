---
title: O autorizaci v mikroslužbách a webových aplikacích v technologii .NET
description: Zabezpečení v .NET Microservices a webových aplikací – získat přehled o hlavních možnostech autorizace v ASP.NET základní aplikace – založené na rolích a na zásadách.
author: mjrousos
ms.date: 01/30/2020
ms.openlocfilehash: 27936a33ea2bb46cedb9d10ee47a2117e1843e14
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988203"
---
# <a name="about-authorization-in-net-microservices-and-web-applications"></a><span data-ttu-id="cad00-103">O autorizaci v mikroslužbách a webových aplikacích v technologii .NET</span><span class="sxs-lookup"><span data-stu-id="cad00-103">About authorization in .NET microservices and web applications</span></span>

<span data-ttu-id="cad00-104">Po ověření je třeba ASP.NET základní webová api autorizovat přístup.</span><span class="sxs-lookup"><span data-stu-id="cad00-104">After authentication, ASP.NET Core Web APIs need to authorize access.</span></span> <span data-ttu-id="cad00-105">Tento proces umožňuje službě zpřístupnit rozhraní API některým ověřeným uživatelům, ale ne všem.</span><span class="sxs-lookup"><span data-stu-id="cad00-105">This process allows a service to make APIs available to some authenticated users, but not to all.</span></span> <span data-ttu-id="cad00-106">[Autorizaci](/aspnet/core/security/authorization/introduction) lze provést na základě rolí uživatelů nebo na základě vlastních zásad, které mohou zahrnovat kontrolu deklarací nebo jiné heuristiky.</span><span class="sxs-lookup"><span data-stu-id="cad00-106">[Authorization](/aspnet/core/security/authorization/introduction) can be done based on users' roles or based on custom policy, which might include inspecting claims or other heuristics.</span></span>

<span data-ttu-id="cad00-107">Omezení přístupu k ASP.NET základní mvc trasy je stejně snadné jako použití Authorize atribut na metodu akce (nebo na třídu řadiče, pokud všechny akce řadiče vyžadují autorizaci), jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="cad00-107">Restricting access to an ASP.NET Core MVC route is as easy as applying an Authorize attribute to the action method (or to the controller's class if all the controller's actions require authorization), as shown in following example:</span></span>

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

<span data-ttu-id="cad00-108">Ve výchozím nastavení přidání atributu Authorize bez parametrů omezí přístup ověřeným uživatelům pro tento řadič nebo akci.</span><span class="sxs-lookup"><span data-stu-id="cad00-108">By default, adding an Authorize attribute without parameters will limit access to authenticated users for that controller or action.</span></span> <span data-ttu-id="cad00-109">Chcete-li dále omezit rozhraní API, které má být k dispozici pouze pro konkrétní uživatele, atribut lze rozbalit určit požadované role nebo zásady, které uživatelé musí splňovat.</span><span class="sxs-lookup"><span data-stu-id="cad00-109">To further restrict an API to be available for only specific users, the attribute can be expanded to specify required roles or policies that users must satisfy.</span></span>

## <a name="implement-role-based-authorization"></a><span data-ttu-id="cad00-110">Implementace autorizace založené na rolích</span><span class="sxs-lookup"><span data-stu-id="cad00-110">Implement role-based authorization</span></span>

<span data-ttu-id="cad00-111">ASP.NET Core Identity má předdefinovaný koncept rolí.</span><span class="sxs-lookup"><span data-stu-id="cad00-111">ASP.NET Core Identity has a built-in concept of roles.</span></span> <span data-ttu-id="cad00-112">Kromě uživatelů ASP.NET Core Identity ukládá informace o různých rolích používaných aplikací a sleduje, kteří uživatelé jsou přiřazeni ke kterým rolím.</span><span class="sxs-lookup"><span data-stu-id="cad00-112">In addition to users, ASP.NET Core Identity stores information about different roles used by the application and keeps track of which users are assigned to which roles.</span></span> <span data-ttu-id="cad00-113">Tato přiřazení lze programově změnit `RoleManager` s typem, který aktualizuje role `UserManager` v trvalém úložišti, a typu, který může udělit nebo odvolat role od uživatelů.</span><span class="sxs-lookup"><span data-stu-id="cad00-113">These assignments can be changed programmatically with the `RoleManager` type that updates roles in persisted storage, and the `UserManager` type that can grant or revoke roles from users.</span></span>

<span data-ttu-id="cad00-114">Pokud ověřujete pomocí tokenů nosiče JWT, ASP.NET middleware pro ověřování nosiče JWT jádra JWT naplní role uživatele na základě deklarací rolí nalezených v tokenu.</span><span class="sxs-lookup"><span data-stu-id="cad00-114">If you're authenticating with JWT bearer tokens, the ASP.NET Core JWT bearer authentication middleware will populate a user's roles based on role claims found in the token.</span></span> <span data-ttu-id="cad00-115">Chcete-li omezit přístup k akci MVC nebo kontroleru pro uživatele v určitých rolích, můžete zahrnout parametr Role do poznámky (atributu Autorizovat), jak je znázorněno v následujícím fragmentu kódu:</span><span class="sxs-lookup"><span data-stu-id="cad00-115">To limit access to an MVC action or controller to users in specific roles, you can include a Roles parameter in the Authorize annotation (attribute), as shown in the following code fragment:</span></span>

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

<span data-ttu-id="cad00-116">V tomto příkladu mají k rozhraním API v řadiči ControlPanel pouze uživatelé v rolích Administrator nebo PowerUser (například spuštění akce SetTime).</span><span class="sxs-lookup"><span data-stu-id="cad00-116">In this example, only users in the Administrator or PowerUser roles can access APIs in the ControlPanel controller (such as executing the SetTime action).</span></span> <span data-ttu-id="cad00-117">Rozhraní SHUTDown API je dále omezeno tak, aby umožňovalo přístup pouze uživatelům v roli správce.</span><span class="sxs-lookup"><span data-stu-id="cad00-117">The ShutDown API is further restricted to allow access only to users in the Administrator role.</span></span>

<span data-ttu-id="cad00-118">Chcete-li vyžadovat, aby byl uživatel ve více rolích, použijte více atributů Authorize, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="cad00-118">To require a user be in multiple roles, you use multiple Authorize attributes, as shown in the following example:</span></span>

```csharp
[Authorize(Roles = "Administrator, PowerUser")]
[Authorize(Roles = "RemoteEmployee ")]
[Authorize(Policy = "CustomPolicy")]
public ActionResult API1 ()
{
}
```

<span data-ttu-id="cad00-119">V tomto příkladu pro volání rozhraní API1 musí uživatel:</span><span class="sxs-lookup"><span data-stu-id="cad00-119">In this example, to call API1, a user must:</span></span>

- <span data-ttu-id="cad00-120">Buďte v roli správce *nebo* PowerUser *a*</span><span class="sxs-lookup"><span data-stu-id="cad00-120">Be in the Administrator *or* PowerUser role, *and*</span></span>

- <span data-ttu-id="cad00-121">Buďte v roli RemoteEmployee *a*</span><span class="sxs-lookup"><span data-stu-id="cad00-121">Be in the RemoteEmployee role, *and*</span></span>

- <span data-ttu-id="cad00-122">Uspokojte vlastní obslužnou rutinu pro autorizaci CustomPolicy.</span><span class="sxs-lookup"><span data-stu-id="cad00-122">Satisfy a custom handler for CustomPolicy authorization.</span></span>

## <a name="implement-policy-based-authorization"></a><span data-ttu-id="cad00-123">Implementace autorizace založené na zásadách</span><span class="sxs-lookup"><span data-stu-id="cad00-123">Implement policy-based authorization</span></span>

<span data-ttu-id="cad00-124">Vlastní autorizační pravidla lze také zapsat pomocí [zásad autorizace](https://docs.asp.net/en/latest/security/authorization/policies.html).</span><span class="sxs-lookup"><span data-stu-id="cad00-124">Custom authorization rules can also be written using [authorization policies](https://docs.asp.net/en/latest/security/authorization/policies.html).</span></span> <span data-ttu-id="cad00-125">Tato část obsahuje přehled.</span><span class="sxs-lookup"><span data-stu-id="cad00-125">This section provides an overview.</span></span> <span data-ttu-id="cad00-126">Další informace naleznete v [ASP.NET Autorizační workshop](https://github.com/blowdart/AspNetAuthorizationWorkshop).</span><span class="sxs-lookup"><span data-stu-id="cad00-126">For more information, see the [ASP.NET Authorization Workshop](https://github.com/blowdart/AspNetAuthorizationWorkshop).</span></span>

<span data-ttu-id="cad00-127">Vlastní zásady autorizace jsou registrovány v Metodě Startup.ConfigureServices pomocí služby. AddAuthorization metoda.</span><span class="sxs-lookup"><span data-stu-id="cad00-127">Custom authorization policies are registered in the Startup.ConfigureServices method using the service.AddAuthorization method.</span></span> <span data-ttu-id="cad00-128">Tato metoda trvá delegáta, který konfiguruje Argument AuthorizationOptions.</span><span class="sxs-lookup"><span data-stu-id="cad00-128">This method takes a delegate that configures an AuthorizationOptions argument.</span></span>

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

<span data-ttu-id="cad00-129">Jak je znázorněno v příkladu, zásady mohou být přidruženy k různým typům požadavků.</span><span class="sxs-lookup"><span data-stu-id="cad00-129">As shown in the example, policies can be associated with different types of requirements.</span></span> <span data-ttu-id="cad00-130">Po zaregistrování zásad je lze použít na akci nebo řadič předáním názvu zásady jako argument `[Authorize(Policy="EmployeesOnly")]`zásad atributu Authorize (například ) Zásady mohou mít více požadavků, nikoli pouze jeden (jak je znázorněno v těchto příkladech).</span><span class="sxs-lookup"><span data-stu-id="cad00-130">After the policies are registered, they can be applied to an action or controller by passing the policy's name as the Policy argument of the Authorize attribute (for example, `[Authorize(Policy="EmployeesOnly")]`) Policies can have multiple requirements, not just one (as shown in these examples).</span></span>

<span data-ttu-id="cad00-131">V předchozím příkladu první AddPolicy volání je pouze alternativní způsob autorizace podle role.</span><span class="sxs-lookup"><span data-stu-id="cad00-131">In the previous example, the first AddPolicy call is just an alternative way of authorizing by role.</span></span> <span data-ttu-id="cad00-132">Pokud `[Authorize(Policy="AdministratorsOnly")]` je použito rozhraní API, budou k němu mít přístup pouze uživatelé v roli správce.</span><span class="sxs-lookup"><span data-stu-id="cad00-132">If `[Authorize(Policy="AdministratorsOnly")]` is applied to an API, only users in the Administrator role will be able to access it.</span></span>

<span data-ttu-id="cad00-133">Druhý <xref:Microsoft.AspNetCore.Authorization.AuthorizationOptions.AddPolicy%2A> hovor ukazuje snadný způsob, jak vyžadovat, aby konkrétní deklarace měla být přítomna pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="cad00-133">The second <xref:Microsoft.AspNetCore.Authorization.AuthorizationOptions.AddPolicy%2A> call demonstrates an easy way to require that a particular claim should be present for the user.</span></span> <span data-ttu-id="cad00-134">Metoda <xref:Microsoft.AspNetCore.Authorization.AuthorizationPolicyBuilder.RequireClaim%2A> také volitelně přebírá očekávané hodnoty deklarace.</span><span class="sxs-lookup"><span data-stu-id="cad00-134">The <xref:Microsoft.AspNetCore.Authorization.AuthorizationPolicyBuilder.RequireClaim%2A> method also optionally takes expected values for the claim.</span></span> <span data-ttu-id="cad00-135">Pokud jsou zadány hodnoty, požadavek je splněn pouze v případě, že uživatel má deklaraci správného typu a jednu ze zadaných hodnot.</span><span class="sxs-lookup"><span data-stu-id="cad00-135">If values are specified, the requirement is met only if the user has both a claim of the correct type and one of the specified values.</span></span> <span data-ttu-id="cad00-136">Pokud používáte middleware pro ověřování nosiče JWT, všechny vlastnosti JWT budou k dispozici jako deklarace identity uživatelů.</span><span class="sxs-lookup"><span data-stu-id="cad00-136">If you're using the JWT bearer authentication middleware, all JWT properties will be available as user claims.</span></span>

<span data-ttu-id="cad00-137">Nejzajímavější zásady zde je ve `AddPolicy` třetí metodě, protože používá požadavek na vlastní autorizaci.</span><span class="sxs-lookup"><span data-stu-id="cad00-137">The most interesting policy shown here is in the third `AddPolicy` method, because it uses a custom authorization requirement.</span></span> <span data-ttu-id="cad00-138">Pomocí vlastních požadavků na autorizaci můžete mít velkou kontrolu nad tím, jak se autorizace provádí.</span><span class="sxs-lookup"><span data-stu-id="cad00-138">By using custom authorization requirements, you can have a great deal of control over how authorization is performed.</span></span> <span data-ttu-id="cad00-139">Aby to fungovalo, je nutné implementovat tyto typy:</span><span class="sxs-lookup"><span data-stu-id="cad00-139">For this to work, you must implement these types:</span></span>

- <span data-ttu-id="cad00-140">A Požadavky typ, <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> který je odvozen od a který obsahuje pole určující podrobnosti požadavku.</span><span class="sxs-lookup"><span data-stu-id="cad00-140">A Requirements type that derives from <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> and that contains fields specifying the details of the requirement.</span></span> <span data-ttu-id="cad00-141">V příkladu se jedná o věkové `MinimumAgeRequirement` pole pro typ vzorku.</span><span class="sxs-lookup"><span data-stu-id="cad00-141">In the example, this is an age field for the sample `MinimumAgeRequirement` type.</span></span>

- <span data-ttu-id="cad00-142">Obslužná <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601>rutina, která <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> implementuje , kde T je typ, který obslužná rutina může uspokojit.</span><span class="sxs-lookup"><span data-stu-id="cad00-142">A handler that implements <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601>, where T is the type of <xref:Microsoft.AspNetCore.Authorization.IAuthorizationRequirement> that the handler can satisfy.</span></span> <span data-ttu-id="cad00-143">Obslužná <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601.HandleRequirementAsync%2A> rutina musí implementovat metodu, která zkontroluje, zda zadaný kontext, který obsahuje informace o uživateli, splňuje požadavek.</span><span class="sxs-lookup"><span data-stu-id="cad00-143">The handler must implement the <xref:Microsoft.AspNetCore.Authorization.AuthorizationHandler%601.HandleRequirementAsync%2A> method, which checks whether a specified context that contains information about the user satisfies the requirement.</span></span>

<span data-ttu-id="cad00-144">Pokud uživatel splňuje požadavek, `context.Succeed` volání bude znamenat, že uživatel je oprávněn.</span><span class="sxs-lookup"><span data-stu-id="cad00-144">If the user meets the requirement, a call to `context.Succeed` will indicate that the user is authorized.</span></span> <span data-ttu-id="cad00-145">Pokud existuje více způsobů, které uživatel může splňovat požadavek na autorizaci, lze vytvořit více obslužných rutin.</span><span class="sxs-lookup"><span data-stu-id="cad00-145">If there are multiple ways that a user might satisfy an authorization requirement, multiple handlers can be created.</span></span>

<span data-ttu-id="cad00-146">Kromě registrace vlastních požadavků `AddPolicy` zásad s voláními je také nutné zaregistrovat`services.AddTransient<IAuthorizationHandler, MinimumAgeHandler>()`vlastní obslužné rutiny požadavků prostřednictvím vkládání závislostí ( ).</span><span class="sxs-lookup"><span data-stu-id="cad00-146">In addition to registering custom policy requirements with `AddPolicy` calls, you also need to register custom requirement handlers via Dependency Injection (`services.AddTransient<IAuthorizationHandler, MinimumAgeHandler>()`).</span></span>

<span data-ttu-id="cad00-147">Příklad požadavku na vlastní autorizaci a obslužné rutiny `DateOfBirth` pro kontrolu věku uživatele (na základě deklarace) je k dispozici v dokumentaci k [autorizaci](https://docs.asp.net/en/latest/security/authorization/policies.html)ASP.NET jádra .</span><span class="sxs-lookup"><span data-stu-id="cad00-147">An example of a custom authorization requirement and handler for checking a user's age (based on a `DateOfBirth` claim) is available in the ASP.NET Core [authorization documentation](https://docs.asp.net/en/latest/security/authorization/policies.html).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="cad00-148">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="cad00-148">Additional resources</span></span>

- <span data-ttu-id="cad00-149">**ověřování ASP.NET jádra** </span><span class="sxs-lookup"><span data-stu-id="cad00-149">**ASP.NET Core Authentication** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authentication/identity](/aspnet/core/security/authentication/identity)

- <span data-ttu-id="cad00-150">**ASP.NET základní autorizace** </span><span class="sxs-lookup"><span data-stu-id="cad00-150">**ASP.NET Core Authorization** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authorization/introduction](/aspnet/core/security/authorization/introduction)

- <span data-ttu-id="cad00-151">**Autorizace založená na rolích** </span><span class="sxs-lookup"><span data-stu-id="cad00-151">**Role-based Authorization** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authorization/roles](/aspnet/core/security/authorization/roles)

- <span data-ttu-id="cad00-152">**Vlastní autorizace založená na zásadách** </span><span class="sxs-lookup"><span data-stu-id="cad00-152">**Custom Policy-Based Authorization** </span></span>\
  [https://docs.microsoft.com/aspnet/core/security/authorization/policies](/aspnet/core/security/authorization/policies)

>[!div class="step-by-step"]
><span data-ttu-id="cad00-153">[Předchozí](index.md)
>[další](developer-app-secrets-storage.md)</span><span class="sxs-lookup"><span data-stu-id="cad00-153">[Previous](index.md)
[Next](developer-app-secrets-storage.md)</span></span>
