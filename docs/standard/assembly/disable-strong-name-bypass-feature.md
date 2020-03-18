---
title: 'Postup: Zakázání funkce obejití silného názvu'
ms.date: 08/20/2019
helpviewer_keywords:
- strong-name bypass feature
- strong-named assemblies, loading into trusted application domains
ms.assetid: 234e088c-3b11-495a-8817-e0962be79d82
ms.openlocfilehash: a4c4ae7ea61a659d3bede532da3c1bdaea448873
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73141119"
---
# <a name="how-to-disable-the-strong-name-bypass-feature"></a><span data-ttu-id="8becf-102">Postup: Zakázání funkce obejití silného názvu</span><span class="sxs-lookup"><span data-stu-id="8becf-102">How to: Disable the strong-name bypass feature</span></span>
<span data-ttu-id="8becf-103">Počínaje rozhraním .NET Framework verze 3.5 Service Pack 1 (SP1) nejsou podpisy silného názvu <xref:System.AppDomain> ověřeny při <xref:System.AppDomain> načtení `MyComputer` sestavení do plně důvěryhodného objektu, například výchozího pro zónu.</span><span class="sxs-lookup"><span data-stu-id="8becf-103">Starting with the .NET Framework version 3.5 Service Pack 1 (SP1), strong-name signatures are not validated when an assembly is loaded into a full-trust <xref:System.AppDomain> object, such as the default <xref:System.AppDomain> for the `MyComputer` zone.</span></span> <span data-ttu-id="8becf-104">Tato funkce se označuje jako funkce obejití silného názvu.</span><span class="sxs-lookup"><span data-stu-id="8becf-104">This is referred to as the strong-name bypass feature.</span></span> <span data-ttu-id="8becf-105">V prostředí s plnou důvěryhodností požadavky na <xref:System.Security.Permissions.StrongNameIdentityPermission> vždy úspěšné pro podepsaná sestavení s plnou důvěryhodností bez ohledu na jejich podpis.</span><span class="sxs-lookup"><span data-stu-id="8becf-105">In a full-trust environment, demands for <xref:System.Security.Permissions.StrongNameIdentityPermission> always succeed for signed, full-trust assemblies regardless of their signature.</span></span> <span data-ttu-id="8becf-106">Jediným omezením je, že sestavení musí být plně důvěryhodné, protože jeho zóna je plně důvěryhodná.</span><span class="sxs-lookup"><span data-stu-id="8becf-106">The only restriction is that the assembly must be fully trusted because its zone is fully trusted.</span></span> <span data-ttu-id="8becf-107">Vzhledem k tomu, že silný název není určujícím faktorem za těchto podmínek, není důvod pro jeho ověření.</span><span class="sxs-lookup"><span data-stu-id="8becf-107">Because the strong name is not a determining factor under these conditions, there is no reason for it to be validated.</span></span> <span data-ttu-id="8becf-108">Vynechání ověření podpisů silného názvu poskytuje významné zlepšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="8becf-108">Bypassing the validation of strong-name signatures provides significant performance improvements.</span></span>  
  
 <span data-ttu-id="8becf-109">Funkce obchvatu se vztahuje na libovolné sestavení s plnou důvěryhodností, které <xref:System.AppDomain> není podepsáno <xref:System.AppDomainSetup.ApplicationBase%2A> zpožděním a které je načteno do libovolného úplného vztahu důvěryhodnosti z adresáře určeného jeho vlastností.</span><span class="sxs-lookup"><span data-stu-id="8becf-109">The bypass feature applies to any full-trust assembly that is not delay-signed and that is loaded into any full-trust <xref:System.AppDomain> from the directory specified by its <xref:System.AppDomainSetup.ApplicationBase%2A> property.</span></span>  
  
 <span data-ttu-id="8becf-110">Funkci přejezdu pro všechny aplikace v počítači můžete přepsat nastavením hodnoty klíče registru.</span><span class="sxs-lookup"><span data-stu-id="8becf-110">You can override the bypass feature for all applications on a computer by setting a registry key value.</span></span> <span data-ttu-id="8becf-111">Nastavení pro jednu aplikaci můžete přepsat pomocí konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="8becf-111">You can override the setting for a single application by using an application configuration file.</span></span> <span data-ttu-id="8becf-112">Funkci obejití pro jednu aplikaci nelze obnovit, pokud byla zakázána klíčem registru.</span><span class="sxs-lookup"><span data-stu-id="8becf-112">You cannot reinstate the bypass feature for a single application if it has been disabled by the registry key.</span></span>  
  
 <span data-ttu-id="8becf-113">Když přepíšete funkci obejití, silný název je ověřen pouze pro správnost; není kontrolována pro <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span><span class="sxs-lookup"><span data-stu-id="8becf-113">When you override the bypass feature, the strong name is validated only for correctness; it is not checked for a <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span></span> <span data-ttu-id="8becf-114">Chcete-li potvrdit konkrétní silný název, musíte tuto kontrolu provést samostatně.</span><span class="sxs-lookup"><span data-stu-id="8becf-114">If you want to confirm a specific strong name, you have to perform that check separately.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="8becf-115">Schopnost vynutit ověření silného názvu závisí na klíči registru, jak je popsáno v následujícím postupu.</span><span class="sxs-lookup"><span data-stu-id="8becf-115">The ability to force strong-name validation depends on a registry key, as described in the following procedure.</span></span> <span data-ttu-id="8becf-116">Pokud je aplikace spuštěna pod účtem, který nemá oprávnění seznamu řízení přístupu (ACL) pro přístup k tomuto klíči registru, je nastavení neúčinné.</span><span class="sxs-lookup"><span data-stu-id="8becf-116">If an application is running under an account that does not have access control list (ACL) permission to access that registry key, the setting is ineffective.</span></span> <span data-ttu-id="8becf-117">Je nutné zajistit, aby byla pro tento klíč nakonfigurována práva acl, aby jej bylo možné číst pro všechna sestavení.</span><span class="sxs-lookup"><span data-stu-id="8becf-117">You must ensure that ACL rights are configured for this key so that it can be read for all assemblies.</span></span>  
  
## <a name="disable-the-strong-name-bypass-feature-for-all-applications"></a><span data-ttu-id="8becf-118">Zakázání funkce obejití silného názvu pro všechny aplikace</span><span class="sxs-lookup"><span data-stu-id="8becf-118">Disable the strong-name bypass feature for all applications</span></span>  
  
- <span data-ttu-id="8becf-119">V 32bitových počítačích vytvořte v systémovém registru položku `AllowStrongNameBypass` DWORD s hodnotou\\0 pojmenovanou pod HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft . NETFramework.</span><span class="sxs-lookup"><span data-stu-id="8becf-119">On 32-bit computers, in the system registry, create a DWORD entry with a value of 0 named `AllowStrongNameBypass` under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
- <span data-ttu-id="8becf-120">V 64bitových počítačích vytvořte v systémovém registru položku `AllowStrongNameBypass` DWORD s hodnotou\\0 pojmenovanou pod HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft . NETFramework a HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework klíče.</span><span class="sxs-lookup"><span data-stu-id="8becf-120">On 64-bit computers, in the system registry, create a DWORD entry with a value of 0 named `AllowStrongNameBypass` under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework and HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework keys.</span></span>  
  
## <a name="disable-the-strong-name-bypass-feature-for-a-single-application"></a><span data-ttu-id="8becf-121">Zakázání funkce obejití silného názvu pro jednu aplikaci</span><span class="sxs-lookup"><span data-stu-id="8becf-121">Disable the strong-name bypass feature for a single application</span></span>  
  
1. <span data-ttu-id="8becf-122">Otevřete nebo vytvořte konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="8becf-122">Open or create the application configuration file.</span></span>  
  
    <span data-ttu-id="8becf-123">Další informace o tomto souboru naleznete v části Soubory konfigurace aplikace v [tématu Konfigurace aplikací](../../framework/configure-apps/index.md).</span><span class="sxs-lookup"><span data-stu-id="8becf-123">For more information about this file, see the Application Configuration Files section in [Configure apps](../../framework/configure-apps/index.md).</span></span>  
  
2. <span data-ttu-id="8becf-124">Přidejte následující položku:</span><span class="sxs-lookup"><span data-stu-id="8becf-124">Add the following entry:</span></span>  
  
    ```xml  
    <configuration>  
      <runtime>  
        <bypassTrustedAppStrongNames enabled="false" />  
      </runtime>  
    </configuration>  
    ```  
  
 <span data-ttu-id="8becf-125">Funkci obejití aplikace můžete obnovit odebráním nastavení konfiguračního souboru nebo nastavením atributu na . `true`</span><span class="sxs-lookup"><span data-stu-id="8becf-125">You can restore the bypass feature for the application by removing the configuration file setting or by setting the attribute to `true`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8becf-126">Ověření silného názvu můžete zapnout a vypnout pro aplikaci pouze v případě, že je pro počítač povolena funkce obejití.</span><span class="sxs-lookup"><span data-stu-id="8becf-126">You can turn strong-name validation on and off for an application only if the bypass feature is enabled for the computer.</span></span> <span data-ttu-id="8becf-127">Pokud byla funkce obejití pro počítač vypnuta, silné názvy jsou ověřeny pro všechny aplikace a nelze obejít ověření pro jednu aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8becf-127">If the bypass feature has been turned off for the computer, strong names are validated for all applications and you cannot bypass validation for a single application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8becf-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="8becf-128">See also</span></span>

- [<span data-ttu-id="8becf-129">Sn.exe (nástroj pro silný název)</span><span class="sxs-lookup"><span data-stu-id="8becf-129">Sn.exe (Strong Name Tool)</span></span>](../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="8becf-130">\<bypassTrustedAppStrongNames> element</span><span class="sxs-lookup"><span data-stu-id="8becf-130">\<bypassTrustedAppStrongNames> element</span></span>](../../framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)
- [<span data-ttu-id="8becf-131">Vytváření a používání sestavení se silným názvem</span><span class="sxs-lookup"><span data-stu-id="8becf-131">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
