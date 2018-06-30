---
title: O autorizace v rozhraní .NET mikroslužeb a webové aplikace
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | O autorizace v rozhraní .NET mikroslužeb a webové aplikace
author: mjrousos
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 7b2981579f28c083a31d7af6ae42f4e3ca8bbd88
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37105498"
---
# <a name="about-authorization-in-net-microservices-and-web-applications"></a><span data-ttu-id="bebdc-103">O autorizace v rozhraní .NET mikroslužeb a webové aplikace</span><span class="sxs-lookup"><span data-stu-id="bebdc-103">About authorization in .NET microservices and web applications</span></span>

<span data-ttu-id="bebdc-104">Po ověření ASP.NET Core webovým rozhraním API nutné k autorizaci přístupu.</span><span class="sxs-lookup"><span data-stu-id="bebdc-104">After authentication, ASP.NET Core Web APIs need to authorize access.</span></span> <span data-ttu-id="bebdc-105">Tento postup umožňuje službě aby rozhraní API dostupné některé ověřeným uživatelům, ale ne všechny.</span><span class="sxs-lookup"><span data-stu-id="bebdc-105">This process allows a service to make APIs available to some authenticated users, but not to all.</span></span> <span data-ttu-id="bebdc-106">[Autorizace](https://docs.microsoft.com/aspnet/core/security/authorization/introduction) můžete provést podle role uživatelů nebo na základě vlastní zásad, která by mohla obsahovat zkontrolujete deklarace identity nebo jiné heuristiky.</span><span class="sxs-lookup"><span data-stu-id="bebdc-106">[Authorization](https://docs.microsoft.com/aspnet/core/security/authorization/introduction) can be done based on users’ roles or based on custom policy, which might include inspecting claims or other heuristics.</span></span>

<span data-ttu-id="bebdc-107">Omezení přístupu k trasu ASP.NET Core MVC je stejně snadná jako použití autorizovat atribut do metody akce (nebo do třídy kontroleru, pokud autorizace vyžadovat akce všechny kontroleru) jako uvedené v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="bebdc-107">Restricting access to an ASP.NET Core MVC route is as easy as applying an Authorize attribute to the action method (or to the controller’s class if all the controller’s actions require authorization), as shown in following example:</span></span>

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

<span data-ttu-id="bebdc-108">Ve výchozím nastavení přidání atributu autorizovat bez parametrů omezí přístup ověřeným uživatelům pro tento kontroler nebo akce.</span><span class="sxs-lookup"><span data-stu-id="bebdc-108">By default, adding an Authorize attribute without parameters will limit access to authenticated users for that controller or action.</span></span> <span data-ttu-id="bebdc-109">Pro další omezení rozhraní API k dispozici jenom pro konkrétní uživatele, můžete rozšířit atribut určete požadované role nebo zásady, které uživatelé musí splňovat.</span><span class="sxs-lookup"><span data-stu-id="bebdc-109">To further restrict an API to be available for only specific users, the attribute can be expanded to specify required roles or policies that users must satisfy.</span></span>

## <a name="implementing-role-based-authorization"></a><span data-ttu-id="bebdc-110">Implementace ověřování na základě rolí</span><span class="sxs-lookup"><span data-stu-id="bebdc-110">Implementing role-based authorization</span></span>

<span data-ttu-id="bebdc-111">Identita ASP.NET Core má integrovanou koncept rolí.</span><span class="sxs-lookup"><span data-stu-id="bebdc-111">ASP.NET Core Identity has a built-in concept of roles.</span></span> <span data-ttu-id="bebdc-112">Kromě uživatelů ASP.NET Core Identity ukládá informace o různých rolích, které používá aplikace a uchovává informace o uživatele, kteří jsou přiřazeny k jednotlivé role.</span><span class="sxs-lookup"><span data-stu-id="bebdc-112">In addition to users, ASP.NET Core Identity stores information about different roles used by the application and keeps track of which users are assigned to which roles.</span></span> <span data-ttu-id="bebdc-113">Tato přiřazení lze změnit prostřednictvím kódu programu s RoleManager typu (který aktualizace rolí v trvalého úložiště) a typ nastavení UserManager, (který může přiřazení nebo zrušení přiřazení uživatele z role).</span><span class="sxs-lookup"><span data-stu-id="bebdc-113">These assignments can be changed programmatically with the RoleManager type (which updates roles in persisted storage) and UserManager type (which can assign or unassign users from roles).</span></span>

<span data-ttu-id="bebdc-114">Pokud ověřujete pomocí nosných tokenů JWT, naplní middlewaru ověřování nosiče ASP.NET Core JWT role uživatele na základě role deklarací nalezen v tokenu.</span><span class="sxs-lookup"><span data-stu-id="bebdc-114">If you are authenticating with JWT bearer tokens, the ASP.NET Core JWT bearer authentication middleware will populate a user’s roles based on role claims found in the token.</span></span> <span data-ttu-id="bebdc-115">Omezit přístup k MVC akce nebo kontroleru pro uživatele v určitých rolích, můžete zahrnout parametr role v hlavičce autorizovat, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="bebdc-115">To limit access to an MVC action or controller to users in specific roles, you can include a Roles parameter in the Authorize header, as shown in the following example:</span></span>

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

<span data-ttu-id="bebdc-116">V tomto příkladu přístup pouze uživatelé v rolích správce nebo PowerUser rozhraní API v kontroleru ControlPanel (např. provádění akce SetTime).</span><span class="sxs-lookup"><span data-stu-id="bebdc-116">In this example, only users in the Administrator or PowerUser roles can access APIs in the ControlPanel controller (such as executing the SetTime action).</span></span> <span data-ttu-id="bebdc-117">Rozhraní API vypnutí je další omezen na povolit přístup pouze uživatelům v roli správce.</span><span class="sxs-lookup"><span data-stu-id="bebdc-117">The ShutDown API is further restricted to allow access only to users in the Administrator role.</span></span>

<span data-ttu-id="bebdc-118">Pokud chcete vyžadovat, že uživatel být ve více rolí, použijte několik atributů autorizovat, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="bebdc-118">To require a user be in multiple roles, you use multiple Authorize attributes, as shown in the following example:</span></span>

```csharp
[Authorize(Roles = "Administrator, PowerUser")]
[Authorize(Roles = "RemoteEmployee ")]
[Authorize(Policy = "CustomPolicy")]
public ActionResult API1 ()
{
}
```

<span data-ttu-id="bebdc-119">V tomto příkladu volání API1, uživatel musí:</span><span class="sxs-lookup"><span data-stu-id="bebdc-119">In this example, to call API1, a user must:</span></span>

-   <span data-ttu-id="bebdc-120">V správce *nebo* PowerUser role *a*</span><span class="sxs-lookup"><span data-stu-id="bebdc-120">Be in the Adminstrator *or* PowerUser role, *and*</span></span>

-   <span data-ttu-id="bebdc-121">V roli RemoteEmployee *a*</span><span class="sxs-lookup"><span data-stu-id="bebdc-121">Be in the RemoteEmployee role, *and*</span></span>

-   <span data-ttu-id="bebdc-122">Splňovat vlastní obslužnou rutinu pro CustomPolicy autorizace.</span><span class="sxs-lookup"><span data-stu-id="bebdc-122">Satisfy a custom handler for CustomPolicy authorization.</span></span>

## <a name="implementing-policy-based-authorization"></a><span data-ttu-id="bebdc-123">Implementace založená na zásadách autorizace</span><span class="sxs-lookup"><span data-stu-id="bebdc-123">Implementing policy-based authorization</span></span>

<span data-ttu-id="bebdc-124">Vlastní autorizační pravidla můžete zapsat také pomocí [zásady autorizace](https://docs.asp.net/en/latest/security/authorization/policies.html).</span><span class="sxs-lookup"><span data-stu-id="bebdc-124">Custom authorization rules can also be written using [authorization policies](https://docs.asp.net/en/latest/security/authorization/policies.html).</span></span> <span data-ttu-id="bebdc-125">V této části poskytujeme Přehled.</span><span class="sxs-lookup"><span data-stu-id="bebdc-125">In this section we provide an overview.</span></span> <span data-ttu-id="bebdc-126">Další podrobnosti najdete v online [ASP.NET autorizace dílny](https://github.com/blowdart/AspNetAuthorizationWorkshop).</span><span class="sxs-lookup"><span data-stu-id="bebdc-126">More detail is available in the online [ASP.NET Authorization Workshop](https://github.com/blowdart/AspNetAuthorizationWorkshop).</span></span>

<span data-ttu-id="bebdc-127">Zásady autorizace je zaregistrovaný v metodě Startup.ConfigureServices pomocí služby. Metoda AddAuthorization.</span><span class="sxs-lookup"><span data-stu-id="bebdc-127">Custom authorization policies are registered in the Startup.ConfigureServices method using the service.AddAuthorization method.</span></span> <span data-ttu-id="bebdc-128">Tato metoda přebírá delegáta, který nakonfiguruje AuthorizationOptions argument.</span><span class="sxs-lookup"><span data-stu-id="bebdc-128">This method takes a delegate that configures an AuthorizationOptions argument.</span></span>

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

<span data-ttu-id="bebdc-129">Jak je znázorněno v příkladu, zásady je možné přidružit s různými typy požadavků.</span><span class="sxs-lookup"><span data-stu-id="bebdc-129">As shown in the example, policies can be associated with different types of requirements.</span></span> <span data-ttu-id="bebdc-130">Po registraci jsou zásady, se můžou uplatnit na akce nebo kontroleru předáním název zásad jako argument zásad atributu autorizovat (například \[Authorize(Policy="EmployeesOnly")\]) může mít zásady více požadavků, ne jenom jeden (jak je znázorněno v těchto příkladech).</span><span class="sxs-lookup"><span data-stu-id="bebdc-130">After the policies are registered, they can be applied to an action or controller by passing the policy’s name as the Policy argument of the Authorize attribute (for example, \[Authorize(Policy="EmployeesOnly")\]) Policies can have multiple requirements, not just one (as shown in these examples).</span></span>

<span data-ttu-id="bebdc-131">V předchozím příkladu první volání AddPolicy je právě alternativní způsob autorizace role.</span><span class="sxs-lookup"><span data-stu-id="bebdc-131">In the previous example, the first AddPolicy call is just an alternative way of authorizing by role.</span></span> <span data-ttu-id="bebdc-132">Pokud \[Authorize(Policy="AdministratorsOnly")\] se použije pro rozhraní API pouze k přístupu budou mít uživatelé v roli správce.</span><span class="sxs-lookup"><span data-stu-id="bebdc-132">If \[Authorize(Policy="AdministratorsOnly")\] is applied to an API, only users in the Administrator role will be able to access it.</span></span>

<span data-ttu-id="bebdc-133">Druhé volání AddPolicy představuje snadný způsob, jak vyžadovat, že konkrétní deklaraci identity by měla být k dispozici pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="bebdc-133">The second AddPolicy call demonstrates an easy way to require that a particular claim should be present for the user.</span></span> <span data-ttu-id="bebdc-134">Metoda RequireClaim volitelně přebírá očekávaných hodnot pro deklarace identity.</span><span class="sxs-lookup"><span data-stu-id="bebdc-134">The RequireClaim method also optionally takes expected values for the claim.</span></span> <span data-ttu-id="bebdc-135">Pokud jsou hodnoty zadané, požadavek se splní pouze v případě, že uživatel má oba správného typu deklarace identity a jedna ze zadaných hodnot.</span><span class="sxs-lookup"><span data-stu-id="bebdc-135">If values are specified, the requirement is met only if the user has both a claim of the correct type and one of the specified values.</span></span> <span data-ttu-id="bebdc-136">Pokud používáte middlewaru ověřování nosiče JWT, budou všechny vlastnosti JWT k dispozici jako deklarace identity uživatelů.</span><span class="sxs-lookup"><span data-stu-id="bebdc-136">If you are using the JWT bearer authentication middleware, all JWT properties will be available as user claims.</span></span>

<span data-ttu-id="bebdc-137">Nejvíce zajímavé zásady, které jsou tady uvedené je v metodě třetí AddPolicy, protože používá vlastní autorizace požadavek.</span><span class="sxs-lookup"><span data-stu-id="bebdc-137">The most interesting policy shown here is in the third AddPolicy method, because it uses a custom authorization requirement.</span></span> <span data-ttu-id="bebdc-138">Pomocí vlastní autorizace požadavky, můžete mít značnou část ovládat, jak se provádí autorizace.</span><span class="sxs-lookup"><span data-stu-id="bebdc-138">By using custom authorization requirements, you can have a great deal of control over how authorization is performed.</span></span> <span data-ttu-id="bebdc-139">Tento postup vyžaduje je nutné implementovat tyto typy:</span><span class="sxs-lookup"><span data-stu-id="bebdc-139">For this to work, you must implement these types:</span></span>

-   <span data-ttu-id="bebdc-140">Požadavky na typ, která je odvozena od IAuthorizationRequirement a který obsahuje podrobnosti o požadavek na zadání pole.</span><span class="sxs-lookup"><span data-stu-id="bebdc-140">A Requirements type that derives from IAuthorizationRequirement and that contains fields specifying the details of the requirement.</span></span> <span data-ttu-id="bebdc-141">V příkladu je to na stáří pole pro typ MinimumAgeRequirement ukázka.</span><span class="sxs-lookup"><span data-stu-id="bebdc-141">In the example, this is an age field for the sample MinimumAgeRequirement type.</span></span>

-   <span data-ttu-id="bebdc-142">Obslužná rutina, která implementuje AuthorizationHandler&lt;T&gt;, kde T představuje typ IAuthorizationRequirement, která se může stát odpovědí obslužná rutina.</span><span class="sxs-lookup"><span data-stu-id="bebdc-142">A handler that implements AuthorizationHandler&lt;T&gt;, where T is the type of IAuthorizationRequirement that the handler can satisfy.</span></span> <span data-ttu-id="bebdc-143">Obslužná rutina musí implementovat metodu HandleRequirementAsync, která kontroluje, zda zadaný kontext, který obsahuje informace o uživateli splňuje požadavek.</span><span class="sxs-lookup"><span data-stu-id="bebdc-143">The handler must implement the HandleRequirementAsync method, which checks whether a specified context that contains information about the user satisfies the requirement.</span></span>

<span data-ttu-id="bebdc-144">Pokud uživatel splňuje požadavky, volání kontextu. Úspěšné bude znamenat, že je uživatel autorizovaný.</span><span class="sxs-lookup"><span data-stu-id="bebdc-144">If the user meets the requirement, a call to context.Succeed will indicate that the user is authorized.</span></span> <span data-ttu-id="bebdc-145">V případě, že uživatel může uspokojení požadavku na autorizaci několika způsoby, můžete vytvořit více obslužných rutin.</span><span class="sxs-lookup"><span data-stu-id="bebdc-145">If there are multiple ways that a user might satisfy an authorization requirement, multiple handlers can be created.</span></span>

<span data-ttu-id="bebdc-146">Kromě registrace vlastních zásad pro požadavky s AddPolicy volání, musíte také zaregistrovat vlastní požadavek obslužné rutiny pomocí vkládání závislostí (služby. AddTransient&lt;IAuthorizationHandler, MinimumAgeHandler&gt;()).</span><span class="sxs-lookup"><span data-stu-id="bebdc-146">In addition to registering custom policy requirements with AddPolicy calls, you also need to register custom requirement handlers via Dependency Injection (services.AddTransient&lt;IAuthorizationHandler, MinimumAgeHandler&gt;()).</span></span>

<span data-ttu-id="bebdc-147">Příklad vlastní autorizace požadavku a obslužné rutiny pro kontrolu stáří uživatele (podle deklaraci identity DateOfBirth) je k dispozici v ASP.NET Core [dokumentaci autorizačních](https://docs.asp.net/en/latest/security/authorization/policies.html).</span><span class="sxs-lookup"><span data-stu-id="bebdc-147">An example of a custom authorization requirement and handler for checking a user’s age (based on a DateOfBirth claim) is available in the ASP.NET Core [authorization documentation](https://docs.asp.net/en/latest/security/authorization/policies.html).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="bebdc-148">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="bebdc-148">Additional resources</span></span>

-   <span data-ttu-id="bebdc-149">**Ověřování ASP.NET Core**
    [*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)</span><span class="sxs-lookup"><span data-stu-id="bebdc-149">**ASP.NET Core Authentication**
[*https://docs.microsoft.com/aspnet/core/security/authentication/identity*](https://docs.microsoft.com/aspnet/core/security/authentication/identity)</span></span>

-   <span data-ttu-id="bebdc-150">**Autorizace ASP.NET Core**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/introduction*](https://docs.microsoft.com/aspnet/core/security/authorization/introduction)</span><span class="sxs-lookup"><span data-stu-id="bebdc-150">**ASP.NET Core Authorization**
[*https://docs.microsoft.com/aspnet/core/security/authorization/introduction*](https://docs.microsoft.com/aspnet/core/security/authorization/introduction)</span></span>

-   <span data-ttu-id="bebdc-151">**Autorizace podle rolí**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/roles*](https://docs.microsoft.com/aspnet/core/security/authorization/roles)</span><span class="sxs-lookup"><span data-stu-id="bebdc-151">**Role based Authorization**
[*https://docs.microsoft.com/aspnet/core/security/authorization/roles*](https://docs.microsoft.com/aspnet/core/security/authorization/roles)</span></span>

-   <span data-ttu-id="bebdc-152">**Autorizace uživatele na základě zásad**
    [*https://docs.microsoft.com/aspnet/core/security/authorization/policies*](https://docs.microsoft.com/aspnet/core/security/authorization/policies)</span><span class="sxs-lookup"><span data-stu-id="bebdc-152">**Custom Policy-Based Authorization**
[*https://docs.microsoft.com/aspnet/core/security/authorization/policies*](https://docs.microsoft.com/aspnet/core/security/authorization/policies)</span></span>




>[!div class="step-by-step"]
<span data-ttu-id="bebdc-153">[Předchozí](index.md)
[další](developer-app-secrets-storage.md)</span><span class="sxs-lookup"><span data-stu-id="bebdc-153">[Previous](index.md)
[Next](developer-app-secrets-storage.md)</span></span>
