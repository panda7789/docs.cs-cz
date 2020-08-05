---
ms.openlocfilehash: 2c8a5c1ec87918a91600a3557c679a42cae74896
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556324"
---
### <a name="principalpermissionattribute-is-obsolete-as-error"></a><span data-ttu-id="42ca6-101">PrincipalPermissionAttribute je zastaralá jako chyba.</span><span class="sxs-lookup"><span data-stu-id="42ca6-101">PrincipalPermissionAttribute is obsolete as error</span></span>

<span data-ttu-id="42ca6-102"><xref:System.Security.Permissions.PrincipalPermissionAttribute>Konstruktor je zastaralý a vytváří chybu při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="42ca6-102">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> constructor is obsolete and produces a compile-time error.</span></span> <span data-ttu-id="42ca6-103">Nemůžete vytvořit instanci tohoto atributu nebo ho použít pro metodu.</span><span class="sxs-lookup"><span data-stu-id="42ca6-103">You cannot instantiate this attribute or apply it to a method.</span></span>

#### <a name="change-description"></a><span data-ttu-id="42ca6-104">Popis změny</span><span class="sxs-lookup"><span data-stu-id="42ca6-104">Change description</span></span>

<span data-ttu-id="42ca6-105">Na .NET Framework a .NET Core můžete přidávat poznámky k metodám s <xref:System.Security.Permissions.PrincipalPermissionAttribute> atributem.</span><span class="sxs-lookup"><span data-stu-id="42ca6-105">On .NET Framework and .NET Core, you can annotate methods with the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute.</span></span> <span data-ttu-id="42ca6-106">Zde je příklad:</span><span class="sxs-lookup"><span data-stu-id="42ca6-106">For example:</span></span>

```csharp
[PrincipalPermission(SecurityAction.Demand, Role = "Administrators")]
public void MyMethod()
{
    // Code that should only run when the current user is an administrator.
}
```

<span data-ttu-id="42ca6-107">Od rozhraní .NET 5,0 nelze použít <xref:System.Security.Permissions.PrincipalPermissionAttribute> atribut pro metodu.</span><span class="sxs-lookup"><span data-stu-id="42ca6-107">Starting in .NET 5.0, you cannot apply the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to a method.</span></span> <span data-ttu-id="42ca6-108">Konstruktor pro atribut je zastaralý a vytváří chybu při kompilaci.</span><span class="sxs-lookup"><span data-stu-id="42ca6-108">The constructor for the attribute is obsolete and produces a compile-time error.</span></span> <span data-ttu-id="42ca6-109">Na rozdíl od jiných obsoletion upozornění nemůžete chybu potlačit.</span><span class="sxs-lookup"><span data-stu-id="42ca6-109">Unlike other obsoletion warnings, you can't suppress the error.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="42ca6-110">Důvod změny</span><span class="sxs-lookup"><span data-stu-id="42ca6-110">Reason for change</span></span>

<span data-ttu-id="42ca6-111"><xref:System.Security.Permissions.PrincipalPermissionAttribute>Typ, podobně jako jiné typy, je podtřída <xref:System.Security.Permissions.SecurityAttribute> součástí. Infrastruktura zabezpečení přístupu kódu k síti (CAS).</span><span class="sxs-lookup"><span data-stu-id="42ca6-111">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> type, like other types that subclass <xref:System.Security.Permissions.SecurityAttribute>, is part of .NET's Code Access Security (CAS) infrastructure.</span></span> <span data-ttu-id="42ca6-112">V .NET Framework 2. x-4. x modul runtime vynutil <xref:System.Security.Permissions.PrincipalPermissionAttribute> poznámky k položce metody, a to i v případě, že je aplikace spuštěná v plně důvěryhodném scénáři.</span><span class="sxs-lookup"><span data-stu-id="42ca6-112">In .NET Framework 2.x - 4.x, the runtime enforces <xref:System.Security.Permissions.PrincipalPermissionAttribute> annotations on method entry, even if the application is running under a full-trust scenario.</span></span> <span data-ttu-id="42ca6-113">.NET Core a .NET 5,0 a novější nepodporují atributy CAS a modul runtime je ignoruje.</span><span class="sxs-lookup"><span data-stu-id="42ca6-113">.NET Core and .NET 5.0 and later don't support CAS attributes, and the runtime ignores them.</span></span>

<span data-ttu-id="42ca6-114">Tento rozdíl v chování od .NET Framework k .NET Core a .NET 5,0 může mít za následek scénář "neúspěšné otevření", ve kterém by měl být zablokován přístup, ale místo toho byl povolen.</span><span class="sxs-lookup"><span data-stu-id="42ca6-114">This difference in behavior from .NET Framework to .NET Core and .NET 5.0 can result in a "fail open" scenario, where access should have been blocked but instead has been allowed.</span></span> <span data-ttu-id="42ca6-115">Chcete-li zabránit scénáři "neúspěšné otevření", nemůžete již použít atribut v kódu, který cílí na rozhraní .NET 5,0 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="42ca6-115">To prevent the "fail open" scenario, you can no longer apply the attribute in code that targets .NET 5.0 or later.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="42ca6-116">Představená verze</span><span class="sxs-lookup"><span data-stu-id="42ca6-116">Version introduced</span></span>

<span data-ttu-id="42ca6-117">5,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="42ca6-117">5.0 Preview 7</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="42ca6-118">Doporučená akce</span><span class="sxs-lookup"><span data-stu-id="42ca6-118">Recommended action</span></span>

<span data-ttu-id="42ca6-119">Pokud dojde k chybě obsoletion, musíte provést akci.</span><span class="sxs-lookup"><span data-stu-id="42ca6-119">If you encounter the obsoletion error, you must take action.</span></span>

- <span data-ttu-id="42ca6-120">**Pokud aplikujete atribut na metodu akce ASP.NET MVC:**</span><span class="sxs-lookup"><span data-stu-id="42ca6-120">**If you're applying the attribute to an ASP.NET MVC action method:**</span></span>

  <span data-ttu-id="42ca6-121">Zvažte použití ASP. Vestavěnou autorizační infrastrukturu sítě.</span><span class="sxs-lookup"><span data-stu-id="42ca6-121">Consider using ASP.NET's built-in authorization infrastructure.</span></span> <span data-ttu-id="42ca6-122">Následující kód ukazuje, jak opatřit ovladačem pomocí <xref:System.Web.Mvc.AuthorizeAttribute> atributu.</span><span class="sxs-lookup"><span data-stu-id="42ca6-122">The following code demonstrates how to annotate a controller with an <xref:System.Web.Mvc.AuthorizeAttribute> attribute.</span></span> <span data-ttu-id="42ca6-123">Modul runtime ASP.NET autorizuje uživatele před provedením akce.</span><span class="sxs-lookup"><span data-stu-id="42ca6-123">The ASP.NET runtime will authorize the user before performing the action.</span></span>

  ```csharp
  using Microsoft.AspNetCore.Authorization;

  namespace MySampleApp
  {
      [Authorize(Roles = "Administrator")]
      public class AdministrationController : Controller
      {
          public ActionResult MyAction()
          {
              // This code won't run unless the current user
              // is in the 'Administrator' role.
          }
      }
  }
  ```

  <span data-ttu-id="42ca6-124">Další informace najdete v tématu [autorizace na základě rolí v ASP.NET Core](/aspnet/core/security/authorization/roles) a [Úvod k autorizaci v ASP.NET Core](/aspnet/core/security/authorization/introduction).</span><span class="sxs-lookup"><span data-stu-id="42ca6-124">For more information, see [Role-based authorization in ASP.NET Core](/aspnet/core/security/authorization/roles) and [Introduction to authorization in ASP.NET Core](/aspnet/core/security/authorization/introduction).</span></span>

- <span data-ttu-id="42ca6-125">**Pokud aplikujete atribut na kód knihovny mimo kontext webové aplikace:**</span><span class="sxs-lookup"><span data-stu-id="42ca6-125">**If you're applying the attribute to library code outside the context of a web app:**</span></span>

  <span data-ttu-id="42ca6-126">Kontroly proveďte ručně na začátku vaší metody.</span><span class="sxs-lookup"><span data-stu-id="42ca6-126">Perform the checks manually at the beginning of your method.</span></span> <span data-ttu-id="42ca6-127">To lze provést pomocí <xref:System.Security.Principal.IPrincipal.IsInRole(System.String)?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="42ca6-127">This can be done by using the <xref:System.Security.Principal.IPrincipal.IsInRole(System.String)?displayProperty=nameWithType> method.</span></span>

  ```csharp
  using System.Threading;

  void DoSomething()
  {
      if (Thread.CurrentPrincipal == null
          || !Thread.CurrentPrincipal.IsInRole("Administrators"))
      {
          throw new Exception("User is anonymous or isn't an admin.");
      }

      // Code that should run only when user is an administrator.
  }
  ```

#### <a name="category"></a><span data-ttu-id="42ca6-128">Kategorie</span><span class="sxs-lookup"><span data-stu-id="42ca6-128">Category</span></span>

- <span data-ttu-id="42ca6-129">Knihovny Core .NET</span><span class="sxs-lookup"><span data-stu-id="42ca6-129">Core .NET libraries</span></span>
- <span data-ttu-id="42ca6-130">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="42ca6-130">Security</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="42ca6-131">Ovlivněná rozhraní API</span><span class="sxs-lookup"><span data-stu-id="42ca6-131">Affected APIs</span></span>

- <xref:System.Security.Permissions.PrincipalPermissionAttribute?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Security.Permissions.PrincipalPermissionAttribute`

-->
