---
ms.openlocfilehash: 2c8a5c1ec87918a91600a3557c679a42cae74896
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556324"
---
### <a name="principalpermissionattribute-is-obsolete-as-error"></a>PrincipalPermissionAttribute je zastaralá jako chyba.

<xref:System.Security.Permissions.PrincipalPermissionAttribute>Konstruktor je zastaralý a vytváří chybu při kompilaci. Nemůžete vytvořit instanci tohoto atributu nebo ho použít pro metodu.

#### <a name="change-description"></a>Popis změny

Na .NET Framework a .NET Core můžete přidávat poznámky k metodám s <xref:System.Security.Permissions.PrincipalPermissionAttribute> atributem. Příklad:

```csharp
[PrincipalPermission(SecurityAction.Demand, Role = "Administrators")]
public void MyMethod()
{
    // Code that should only run when the current user is an administrator.
}
```

Od rozhraní .NET 5,0 nelze použít <xref:System.Security.Permissions.PrincipalPermissionAttribute> atribut pro metodu. Konstruktor pro atribut je zastaralý a vytváří chybu při kompilaci. Na rozdíl od jiných obsoletion upozornění nemůžete chybu potlačit.

#### <a name="reason-for-change"></a>Důvod změny

<xref:System.Security.Permissions.PrincipalPermissionAttribute>Typ, podobně jako jiné typy, je podtřída <xref:System.Security.Permissions.SecurityAttribute> součástí. Infrastruktura zabezpečení přístupu kódu k síti (CAS). V .NET Framework 2. x-4. x modul runtime vynutil <xref:System.Security.Permissions.PrincipalPermissionAttribute> poznámky k položce metody, a to i v případě, že je aplikace spuštěná v plně důvěryhodném scénáři. .NET Core a .NET 5,0 a novější nepodporují atributy CAS a modul runtime je ignoruje.

Tento rozdíl v chování od .NET Framework k .NET Core a .NET 5,0 může mít za následek scénář "neúspěšné otevření", ve kterém by měl být zablokován přístup, ale místo toho byl povolen. Chcete-li zabránit scénáři "neúspěšné otevření", nemůžete již použít atribut v kódu, který cílí na rozhraní .NET 5,0 nebo novější.

#### <a name="version-introduced"></a>Představená verze

5,0 Preview 7

#### <a name="recommended-action"></a>Doporučená akce

Pokud dojde k chybě obsoletion, musíte provést akci.

- **Pokud aplikujete atribut na metodu akce ASP.NET MVC:**

  Zvažte použití ASP. Vestavěnou autorizační infrastrukturu sítě. Následující kód ukazuje, jak opatřit ovladačem pomocí <xref:System.Web.Mvc.AuthorizeAttribute> atributu. Modul runtime ASP.NET autorizuje uživatele před provedením akce.

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

  Další informace najdete v tématu [autorizace na základě rolí v ASP.NET Core](/aspnet/core/security/authorization/roles) a [Úvod k autorizaci v ASP.NET Core](/aspnet/core/security/authorization/introduction).

- **Pokud aplikujete atribut na kód knihovny mimo kontext webové aplikace:**

  Kontroly proveďte ručně na začátku vaší metody. To lze provést pomocí <xref:System.Security.Principal.IPrincipal.IsInRole(System.String)?displayProperty=nameWithType> metody.

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

#### <a name="category"></a>Kategorie

- Knihovny Core .NET
- Zabezpečení

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

- <xref:System.Security.Permissions.PrincipalPermissionAttribute?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.Security.Permissions.PrincipalPermissionAttribute`

-->
