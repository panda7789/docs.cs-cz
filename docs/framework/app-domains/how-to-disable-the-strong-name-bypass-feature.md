---
title: 'Postupy: Zákaz funkce obejití silného názvu'
ms.date: 03/30/2017
helpviewer_keywords:
- strong-name bypass feature
- strong-named assemblies, loading into trusted application domains
ms.assetid: 234e088c-3b11-495a-8817-e0962be79d82
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 86fc35ae20211bd32a21d60b7313074361aef671
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59296170"
---
# <a name="how-to-disable-the-strong-name-bypass-feature"></a><span data-ttu-id="824e1-102">Postupy: Zákaz funkce obejití silného názvu</span><span class="sxs-lookup"><span data-stu-id="824e1-102">How to: Disable the Strong-Name Bypass Feature</span></span>
<span data-ttu-id="824e1-103">Počínaje verzí rozhraní .NET Framework 3.5 Service Pack 1 (SP1), podpisy se silným názvem nejsou ověřovány, pokud je sestavení načteno do plně důvěryhodné <xref:System.AppDomain> objektu, například výchozí <xref:System.AppDomain> pro `MyComputer` zóny.</span><span class="sxs-lookup"><span data-stu-id="824e1-103">Starting with the .NET Framework version 3.5 Service Pack 1 (SP1), strong-name signatures are not validated when an assembly is loaded into a full-trust <xref:System.AppDomain> object, such as the default <xref:System.AppDomain> for the `MyComputer` zone.</span></span> <span data-ttu-id="824e1-104">To se označuje jako silného názvu obejít funkce.</span><span class="sxs-lookup"><span data-stu-id="824e1-104">This is referred to as the strong-name bypass feature.</span></span> <span data-ttu-id="824e1-105">V prostředí úplného vztahu důvěryhodnosti vyžaduje pro <xref:System.Security.Permissions.StrongNameIdentityPermission> vždy úspěšné pro podepsané sestavení úplného vztahu důvěryhodnosti, bez ohledu na jejich podpisu.</span><span class="sxs-lookup"><span data-stu-id="824e1-105">In a full-trust environment, demands for <xref:System.Security.Permissions.StrongNameIdentityPermission> always succeed for signed, full-trust assemblies regardless of their signature.</span></span> <span data-ttu-id="824e1-106">Jediným omezením je, že sestavení musí být plně důvěryhodné, protože jeho zóna je plně důvěryhodné.</span><span class="sxs-lookup"><span data-stu-id="824e1-106">The only restriction is that the assembly must be fully trusted because its zone is fully trusted.</span></span> <span data-ttu-id="824e1-107">Protože silný název není určujícím faktorem za těchto podmínek, neexistuje žádný důvod pro něj má být ověřen.</span><span class="sxs-lookup"><span data-stu-id="824e1-107">Because the strong name is not a determining factor under these conditions, there is no reason for it to be validated.</span></span> <span data-ttu-id="824e1-108">Vynechání ověřování podpisy se silným názvem poskytuje výrazné zlepšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="824e1-108">Bypassing the validation of strong-name signatures provides significant performance improvements.</span></span>  
  
 <span data-ttu-id="824e1-109">Jednorázové přihlášení funkce se vztahuje na všechny sestavení úplného vztahu důvěryhodnosti, který se zpožděným podpisem a, který je načten do jakékoli úplného vztahu důvěryhodnosti <xref:System.AppDomain> z adresáře zadaného parametrem jeho <xref:System.AppDomainSetup.ApplicationBase%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="824e1-109">The bypass feature applies to any full-trust assembly that is not delay-signed and that is loaded into any full-trust <xref:System.AppDomain> from the directory specified by its <xref:System.AppDomainSetup.ApplicationBase%2A> property.</span></span>  
  
 <span data-ttu-id="824e1-110">Funkce obejití pro všechny aplikace na počítači můžete přepsat tak, že nastavíte hodnotu klíče registru.</span><span class="sxs-lookup"><span data-stu-id="824e1-110">You can override the bypass feature for all applications on a computer by setting a registry key value.</span></span> <span data-ttu-id="824e1-111">Nastavení pro jednu aplikaci lze přepsat pomocí konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="824e1-111">You can override the setting for a single application by using an application configuration file.</span></span> <span data-ttu-id="824e1-112">Funkce obejití pro jednu aplikaci nelze obnovit, pokud byla zakázaná pomocí klíče registru.</span><span class="sxs-lookup"><span data-stu-id="824e1-112">You cannot reinstate the bypass feature for a single application if it has been disabled by the registry key.</span></span>  
  
 <span data-ttu-id="824e1-113">Při přepsání funkce obejití silného názvu je ověřen pouze pro správnosti; není zaškrtnuté políčko pro <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span><span class="sxs-lookup"><span data-stu-id="824e1-113">When you override the bypass feature, the strong name is validated only for correctness; it is not checked for a <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span></span> <span data-ttu-id="824e1-114">Pokud chcete potvrdit specifický silný název, budete muset provést kontroly samostatně.</span><span class="sxs-lookup"><span data-stu-id="824e1-114">If you want to confirm a specific strong name, you have to perform that check separately.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="824e1-115">Schopnost vynutit ověřování silných názvů závisí na klíč registru, jak je popsáno v následujícím postupu.</span><span class="sxs-lookup"><span data-stu-id="824e1-115">The ability to force strong-name validation depends on a registry key, as described in the following procedure.</span></span> <span data-ttu-id="824e1-116">Pokud aplikace běží pod účtem, který nemá přístup k ovládacího prvku seznam (ACL) oprávnění pro přístup k tomuto klíči registru, nastavení je neefektivní.</span><span class="sxs-lookup"><span data-stu-id="824e1-116">If an application is running under an account that does not have access control list (ACL) permission to access that registry key, the setting is ineffective.</span></span> <span data-ttu-id="824e1-117">Musí zkontrolovat, jestli seznam ACL práva konfigurované pro tento klíč tak, že bude načtena pro všechna sestavení.</span><span class="sxs-lookup"><span data-stu-id="824e1-117">You must ensure that ACL rights are configured for this key so that it can be read for all assemblies.</span></span>  
  
### <a name="to-disable-the-strong-name-bypass-feature-for-all-applications"></a><span data-ttu-id="824e1-118">Zakázat obejití silného názvu funkce pro všechny aplikace</span><span class="sxs-lookup"><span data-stu-id="824e1-118">To disable the strong-name bypass feature for all applications</span></span>  
  
-   <span data-ttu-id="824e1-119">Na 32bitových počítačích, v systémovém registru vytvořte položku DWORD s hodnotou 0 s názvem `AllowStrongNameBypass` pod HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework klíč.</span><span class="sxs-lookup"><span data-stu-id="824e1-119">On 32-bit computers, in the system registry, create a DWORD entry with a value of 0 named `AllowStrongNameBypass` under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
-   <span data-ttu-id="824e1-120">Na 64bitových počítačích, v systémovém registru vytvořte položku DWORD s hodnotou 0 s názvem `AllowStrongNameBypass` pod HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework a HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework klíče.</span><span class="sxs-lookup"><span data-stu-id="824e1-120">On 64-bit computers, in the system registry, create a DWORD entry with a value of 0 named `AllowStrongNameBypass` under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework and HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework keys.</span></span>  
  
### <a name="to-disable-the-strong-name-bypass-feature-for-a-single-application"></a><span data-ttu-id="824e1-121">Zakázat obejití silného názvu funkce pro jednu aplikaci</span><span class="sxs-lookup"><span data-stu-id="824e1-121">To disable the strong-name bypass feature for a single application</span></span>  
  
1. <span data-ttu-id="824e1-122">Otevřete nebo vytvořte konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="824e1-122">Open or create the application configuration file.</span></span>  
  
     <span data-ttu-id="824e1-123">Další informace o tomto souboru najdete v části konfiguračních souborů aplikace v [konfigurace aplikace](../../../docs/framework/configure-apps/index.md).</span><span class="sxs-lookup"><span data-stu-id="824e1-123">For more information about this file, see the Application Configuration Files section in [Configuring Apps](../../../docs/framework/configure-apps/index.md).</span></span>  
  
2. <span data-ttu-id="824e1-124">Přidejte následující položku:</span><span class="sxs-lookup"><span data-stu-id="824e1-124">Add the following entry:</span></span>  
  
    ```xml  
    <configuration>  
      <runtime>  
        <bypassTrustedAppStrongNames enabled="false" />  
      </runtime>  
    </configuration>  
    ```  
  
 <span data-ttu-id="824e1-125">Funkce jednorázové přihlášení pro aplikaci můžete obnovit tak, že odeberete nastavení konfiguračního souboru nebo nastavením atributu na hodnotu "true".</span><span class="sxs-lookup"><span data-stu-id="824e1-125">You can restore the bypass feature for the application by removing the configuration file setting or by setting the attribute to "true".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="824e1-126">Ověření silných názvů zapnutí a vypnutí pro aplikaci můžete vypnout jenom v případě, že je povolena funkce jednorázové přihlášení pro počítač.</span><span class="sxs-lookup"><span data-stu-id="824e1-126">You can turn strong-name validation on and off for an application only if the bypass feature is enabled for the computer.</span></span> <span data-ttu-id="824e1-127">Pokud jsou vypnuté funkci jednorázové přihlášení pro počítač, se ověří silné názvy pro všechny aplikace a nemůže obejít ověření pro jednu aplikaci.</span><span class="sxs-lookup"><span data-stu-id="824e1-127">If the bypass feature has been turned off for the computer, strong names are validated for all applications and you cannot bypass validation for a single application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="824e1-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="824e1-128">See also</span></span>

- [<span data-ttu-id="824e1-129">Sn.exe (nástroj pro silný název)</span><span class="sxs-lookup"><span data-stu-id="824e1-129">Sn.exe (Strong Name Tool)</span></span>](../../../docs/framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="824e1-130">\<bypassTrustedAppStrongNames> Element</span><span class="sxs-lookup"><span data-stu-id="824e1-130">\<bypassTrustedAppStrongNames> Element</span></span>](../../../docs/framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)
- [<span data-ttu-id="824e1-131">Vytváření a používání sestavení se silným názvem</span><span class="sxs-lookup"><span data-stu-id="824e1-131">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
