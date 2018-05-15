---
title: 'Postupy: Zákaz funkce obejití silného názvu'
ms.date: 03/30/2017
helpviewer_keywords:
- strong-name bypass feature
- strong-named assemblies, loading into trusted application domains
ms.assetid: 234e088c-3b11-495a-8817-e0962be79d82
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e9604969ea073b07af0eca8d481f5459ee15d099
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-disable-the-strong-name-bypass-feature"></a><span data-ttu-id="bc7ad-102">Postupy: Zákaz funkce obejití silného názvu</span><span class="sxs-lookup"><span data-stu-id="bc7ad-102">How to: Disable the Strong-Name Bypass Feature</span></span>
<span data-ttu-id="bc7ad-103">Počínaje verzí rozhraní .NET Framework 3.5 Service Pack 1 (SP1), silné jméno – nedochází k ověřování podpisů při sestavení načtení do plné důvěryhodnosti <xref:System.AppDomain> objektu, například výchozí <xref:System.AppDomain> pro `MyComputer` zóny.</span><span class="sxs-lookup"><span data-stu-id="bc7ad-103">Starting with the .NET Framework version 3.5 Service Pack 1 (SP1), strong-name signatures are not validated when an assembly is loaded into a full-trust <xref:System.AppDomain> object, such as the default <xref:System.AppDomain> for the `MyComputer` zone.</span></span> <span data-ttu-id="bc7ad-104">Tento proces se označuje jako silné jméno – Nepoužívat funkce.</span><span class="sxs-lookup"><span data-stu-id="bc7ad-104">This is referred to as the strong-name bypass feature.</span></span> <span data-ttu-id="bc7ad-105">V prostředí plné důvěryhodnosti jsou požadavky na <xref:System.Security.Permissions.StrongNameIdentityPermission> vždy úspěšné pro podepsané, plné důvěryhodnosti sestavení bez ohledu na jejich podpisu.</span><span class="sxs-lookup"><span data-stu-id="bc7ad-105">In a full-trust environment, demands for <xref:System.Security.Permissions.StrongNameIdentityPermission> always succeed for signed, full-trust assemblies regardless of their signature.</span></span> <span data-ttu-id="bc7ad-106">Pouze omezení je, že sestavení musí být plně důvěryhodná, protože je plně důvěryhodný pro časového pásma.</span><span class="sxs-lookup"><span data-stu-id="bc7ad-106">The only restriction is that the assembly must be fully trusted because its zone is fully trusted.</span></span> <span data-ttu-id="bc7ad-107">Protože se silným názvem není určujícím faktorem za těchto podmínek, neexistuje žádný důvod pro něj má být ověřen.</span><span class="sxs-lookup"><span data-stu-id="bc7ad-107">Because the strong name is not a determining factor under these conditions, there is no reason for it to be validated.</span></span> <span data-ttu-id="bc7ad-108">Vynechání ověřování podpisů silných názvů poskytuje významné zlepšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="bc7ad-108">Bypassing the validation of strong-name signatures provides significant performance improvements.</span></span>  
  
 <span data-ttu-id="bc7ad-109">Funkce obcházení vztahuje na všechny plné důvěryhodnosti sestavení, která není zpoždění podepsaný a který je načten do jakékoli plné důvěryhodnosti <xref:System.AppDomain> z adresáře určeného jeho <xref:System.AppDomainSetup.ApplicationBase%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="bc7ad-109">The bypass feature applies to any full-trust assembly that is not delay-signed and that is loaded into any full-trust <xref:System.AppDomain> from the directory specified by its <xref:System.AppDomainSetup.ApplicationBase%2A> property.</span></span>  
  
 <span data-ttu-id="bc7ad-110">Funkce obcházení pro všechny aplikace v počítači můžete přepsat nastavením hodnoty klíče registru.</span><span class="sxs-lookup"><span data-stu-id="bc7ad-110">You can override the bypass feature for all applications on a computer by setting a registry key value.</span></span> <span data-ttu-id="bc7ad-111">Nastavení pro jednu aplikaci můžete přepsat pomocí konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="bc7ad-111">You can override the setting for a single application by using an application configuration file.</span></span> <span data-ttu-id="bc7ad-112">Funkce obcházení pro jednu aplikaci nelze obnovit, pokud je zakázaná pomocí klíče registru.</span><span class="sxs-lookup"><span data-stu-id="bc7ad-112">You cannot reinstate the bypass feature for a single application if it has been disabled by the registry key.</span></span>  
  
 <span data-ttu-id="bc7ad-113">Při přepsání funkce obejití silného názvu ověřován pouze pro správnost; není kontrolován pro <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span><span class="sxs-lookup"><span data-stu-id="bc7ad-113">When you override the bypass feature, the strong name is validated only for correctness; it is not checked for a <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span></span> <span data-ttu-id="bc7ad-114">Pokud chcete potvrdit konkrétní silným názvem, budete muset provést tuto kontrolu samostatně.</span><span class="sxs-lookup"><span data-stu-id="bc7ad-114">If you want to confirm a specific strong name, you have to perform that check separately.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bc7ad-115">Schopnost vynutit ověřování silných názvů závisí na klíč registru, jak je popsáno v následujícím postupu.</span><span class="sxs-lookup"><span data-stu-id="bc7ad-115">The ability to force strong-name validation depends on a registry key, as described in the following procedure.</span></span> <span data-ttu-id="bc7ad-116">Pokud aplikace běží pod účtem, který nemá oprávnění seznamu ACL řízení přístupu pro přístup k tomuto klíči registru, toto nastavení je neúčinné.</span><span class="sxs-lookup"><span data-stu-id="bc7ad-116">If an application is running under an account that does not have access control list (ACL) permission to access that registry key, the setting is ineffective.</span></span> <span data-ttu-id="bc7ad-117">Je nutné zajistit, že práva seznamu ACL jsou konfigurovány pro tento klíč tak, aby ho mohou číst pro všechna sestavení.</span><span class="sxs-lookup"><span data-stu-id="bc7ad-117">You must ensure that ACL rights are configured for this key so that it can be read for all assemblies.</span></span>  
  
### <a name="to-disable-the-strong-name-bypass-feature-for-all-applications"></a><span data-ttu-id="bc7ad-118">Chcete-li zakázat vynechat silné jméno – funkce pro všechny aplikace</span><span class="sxs-lookup"><span data-stu-id="bc7ad-118">To disable the strong-name bypass feature for all applications</span></span>  
  
-   <span data-ttu-id="bc7ad-119">Na 32bitové počítače v registru systému vytvořte novou položku DWORD s hodnotou 0 s názvem `AllowStrongNameBypass` pod HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework klíč.</span><span class="sxs-lookup"><span data-stu-id="bc7ad-119">On 32-bit computers, in the system registry, create a DWORD entry with a value of 0 named `AllowStrongNameBypass` under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
-   <span data-ttu-id="bc7ad-120">Na 64bitových počítačích, v registru systému vytvořit záznam typu DWORD s hodnotou 0 s názvem `AllowStrongNameBypass` pod HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework a HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework klíče.</span><span class="sxs-lookup"><span data-stu-id="bc7ad-120">On 64-bit computers, in the system registry, create a DWORD entry with a value of 0 named `AllowStrongNameBypass` under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework and HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework keys.</span></span>  
  
### <a name="to-disable-the-strong-name-bypass-feature-for-a-single-application"></a><span data-ttu-id="bc7ad-121">Chcete-li zakázat vynechání silné jméno – funkce pro jednu aplikaci</span><span class="sxs-lookup"><span data-stu-id="bc7ad-121">To disable the strong-name bypass feature for a single application</span></span>  
  
1.  <span data-ttu-id="bc7ad-122">Otevřete nebo vytvořte konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="bc7ad-122">Open or create the application configuration file.</span></span>  
  
     <span data-ttu-id="bc7ad-123">Další informace o tomto souboru, najdete v části konfigurační soubory aplikace v [konfigurace aplikace](../../../docs/framework/configure-apps/index.md).</span><span class="sxs-lookup"><span data-stu-id="bc7ad-123">For more information about this file, see the Application Configuration Files section in [Configuring Apps](../../../docs/framework/configure-apps/index.md).</span></span>  
  
2.  <span data-ttu-id="bc7ad-124">Přidejte následující položky:</span><span class="sxs-lookup"><span data-stu-id="bc7ad-124">Add the following entry:</span></span>  
  
    ```xml  
    <configuration>  
      <runtime>  
        <bypassTrustedAppStrongNames enabled="false" />  
      </runtime>  
    </configuration>  
    ```  
  
 <span data-ttu-id="bc7ad-125">Funkci jednorázové přihlášení pro aplikaci můžete obnovit odebráním nastavení konfigurace souborů nebo nastavením atributu na hodnotu "true".</span><span class="sxs-lookup"><span data-stu-id="bc7ad-125">You can restore the bypass feature for the application by removing the configuration file setting or by setting the attribute to "true".</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bc7ad-126">Ověřování silných názvů zapnout a vypnout pro aplikaci můžete zapnout pouze v případě, že je povolena funkce obcházení pro počítač.</span><span class="sxs-lookup"><span data-stu-id="bc7ad-126">You can turn strong-name validation on and off for an application only if the bypass feature is enabled for the computer.</span></span> <span data-ttu-id="bc7ad-127">Pokud funkce obcházení bylo vypnuto pro počítač, se ověřují silné názvy pro všechny aplikace, a nemůžete vynechat ověření pro jednu aplikaci.</span><span class="sxs-lookup"><span data-stu-id="bc7ad-127">If the bypass feature has been turned off for the computer, strong names are validated for all applications and you cannot bypass validation for a single application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc7ad-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="bc7ad-128">See Also</span></span>  
 [<span data-ttu-id="bc7ad-129">Sn.exe (nástroj pro silný název)</span><span class="sxs-lookup"><span data-stu-id="bc7ad-129">Sn.exe (Strong Name Tool)</span></span>](../../../docs/framework/tools/sn-exe-strong-name-tool.md)  
 [<span data-ttu-id="bc7ad-130">\<bypasstrustedappstrongnames – > elementu</span><span class="sxs-lookup"><span data-stu-id="bc7ad-130">\<bypassTrustedAppStrongNames> Element</span></span>](../../../docs/framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)  
 [<span data-ttu-id="bc7ad-131">Vytváření a používání sestavení se silným názvem</span><span class="sxs-lookup"><span data-stu-id="bc7ad-131">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
