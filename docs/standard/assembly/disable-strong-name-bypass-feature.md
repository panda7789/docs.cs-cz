---
title: 'Postupy: Zakázat funkci obcházení silného názvu'
ms.date: 08/20/2019
helpviewer_keywords:
- strong-name bypass feature
- strong-named assemblies, loading into trusted application domains
ms.assetid: 234e088c-3b11-495a-8817-e0962be79d82
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f8cdc700ecc8195da1b5e0975f00a4dc6785d330
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973290"
---
# <a name="how-to-disable-the-strong-name-bypass-feature"></a><span data-ttu-id="32afe-102">Postupy: Zakázat funkci obcházení silného názvu</span><span class="sxs-lookup"><span data-stu-id="32afe-102">How to: Disable the strong-name bypass feature</span></span>
<span data-ttu-id="32afe-103">.NET Framework počínaje verzí 3,5 a Service Pack 1 (SP1) se signatury silného názvu neověřují, pokud je sestavení načteno do objektu s úplným <xref:System.AppDomain> vztahem důvěryhodnosti, jako je <xref:System.AppDomain> například výchozí `MyComputer` hodnota pro zónu.</span><span class="sxs-lookup"><span data-stu-id="32afe-103">Starting with the .NET Framework version 3.5 Service Pack 1 (SP1), strong-name signatures are not validated when an assembly is loaded into a full-trust <xref:System.AppDomain> object, such as the default <xref:System.AppDomain> for the `MyComputer` zone.</span></span> <span data-ttu-id="32afe-104">To se označuje jako funkce obcházení silného názvu.</span><span class="sxs-lookup"><span data-stu-id="32afe-104">This is referred to as the strong-name bypass feature.</span></span> <span data-ttu-id="32afe-105">V prostředí s úplným vztahem důvěryhodnosti požadavky <xref:System.Security.Permissions.StrongNameIdentityPermission> vždy úspěšné pro podepsaná, plně důvěryhodná sestavení bez ohledu na jejich podpis.</span><span class="sxs-lookup"><span data-stu-id="32afe-105">In a full-trust environment, demands for <xref:System.Security.Permissions.StrongNameIdentityPermission> always succeed for signed, full-trust assemblies regardless of their signature.</span></span> <span data-ttu-id="32afe-106">Jediným omezením je, že sestavení musí být plně důvěryhodné, protože jeho zóna je plně důvěryhodná.</span><span class="sxs-lookup"><span data-stu-id="32afe-106">The only restriction is that the assembly must be fully trusted because its zone is fully trusted.</span></span> <span data-ttu-id="32afe-107">Vzhledem k tomu, že silný název není určujícím faktorem za těchto podmínek, neexistuje žádný důvod, aby jej bylo možné ověřit.</span><span class="sxs-lookup"><span data-stu-id="32afe-107">Because the strong name is not a determining factor under these conditions, there is no reason for it to be validated.</span></span> <span data-ttu-id="32afe-108">Obejít ověřování podpisů se silným názvem přináší významná vylepšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="32afe-108">Bypassing the validation of strong-name signatures provides significant performance improvements.</span></span>  
  
 <span data-ttu-id="32afe-109">Funkce bypass se vztahuje na jakékoli sestavení s úplným vztahem důvěryhodnosti, které není podepsané zpožděním a které je načteno do <xref:System.AppDomain> jakékoli plně důvěryhodné z adresáře určeného <xref:System.AppDomainSetup.ApplicationBase%2A> jeho vlastností.</span><span class="sxs-lookup"><span data-stu-id="32afe-109">The bypass feature applies to any full-trust assembly that is not delay-signed and that is loaded into any full-trust <xref:System.AppDomain> from the directory specified by its <xref:System.AppDomainSetup.ApplicationBase%2A> property.</span></span>  
  
 <span data-ttu-id="32afe-110">Funkci obcházení můžete pro všechny aplikace v počítači přepsat nastavením hodnoty klíče registru.</span><span class="sxs-lookup"><span data-stu-id="32afe-110">You can override the bypass feature for all applications on a computer by setting a registry key value.</span></span> <span data-ttu-id="32afe-111">Nastavení pro jednu aplikaci můžete přepsat pomocí konfiguračního souboru aplikace.</span><span class="sxs-lookup"><span data-stu-id="32afe-111">You can override the setting for a single application by using an application configuration file.</span></span> <span data-ttu-id="32afe-112">Funkci vynechání nemůžete obnovit pro jednu aplikaci, pokud byla zakázána klíčem registru.</span><span class="sxs-lookup"><span data-stu-id="32afe-112">You cannot reinstate the bypass feature for a single application if it has been disabled by the registry key.</span></span>  
  
 <span data-ttu-id="32afe-113">Pokud přepíšete funkci bypass, silný název se ověří jenom pro správnost. není zaškrtnuta <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span><span class="sxs-lookup"><span data-stu-id="32afe-113">When you override the bypass feature, the strong name is validated only for correctness; it is not checked for a <xref:System.Security.Permissions.StrongNameIdentityPermission>.</span></span> <span data-ttu-id="32afe-114">Pokud chcete potvrdit konkrétní silný název, je nutné provést tuto kontrolu samostatně.</span><span class="sxs-lookup"><span data-stu-id="32afe-114">If you want to confirm a specific strong name, you have to perform that check separately.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="32afe-115">Možnost vynutit ověřování silného názvu závisí na klíči registru, jak je popsáno v následujícím postupu.</span><span class="sxs-lookup"><span data-stu-id="32afe-115">The ability to force strong-name validation depends on a registry key, as described in the following procedure.</span></span> <span data-ttu-id="32afe-116">Pokud aplikace běží pod účtem, který nemá oprávnění seznamu řízení přístupu (ACL) pro přístup k tomuto klíči registru, nastavení se neprojeví.</span><span class="sxs-lookup"><span data-stu-id="32afe-116">If an application is running under an account that does not have access control list (ACL) permission to access that registry key, the setting is ineffective.</span></span> <span data-ttu-id="32afe-117">Je nutné zajistit, aby byla pro tento klíč nakonfigurovaná oprávnění ACL, aby je bylo možné číst pro všechna sestavení.</span><span class="sxs-lookup"><span data-stu-id="32afe-117">You must ensure that ACL rights are configured for this key so that it can be read for all assemblies.</span></span>  
  
## <a name="disable-the-strong-name-bypass-feature-for-all-applications"></a><span data-ttu-id="32afe-118">Zakázat funkci obcházení silného názvu pro všechny aplikace</span><span class="sxs-lookup"><span data-stu-id="32afe-118">Disable the strong-name bypass feature for all applications</span></span>  
  
- <span data-ttu-id="32afe-119">Na 32 počítačích v systémovém registru vytvořte položku DWORD s hodnotou 0 s názvem `AllowStrongNameBypass` v rámci HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft.\\ NETFramework klíč.</span><span class="sxs-lookup"><span data-stu-id="32afe-119">On 32-bit computers, in the system registry, create a DWORD entry with a value of 0 named `AllowStrongNameBypass` under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework key.</span></span>  
  
- <span data-ttu-id="32afe-120">Na 64 počítačích v systémovém registru vytvořte položku DWORD s hodnotou 0 s názvem `AllowStrongNameBypass` v rámci HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft.\\ NETFramework a HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework klíče.</span><span class="sxs-lookup"><span data-stu-id="32afe-120">On 64-bit computers, in the system registry, create a DWORD entry with a value of 0 named `AllowStrongNameBypass` under the HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework and HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework keys.</span></span>  
  
## <a name="disable-the-strong-name-bypass-feature-for-a-single-application"></a><span data-ttu-id="32afe-121">Zakázání funkce obcházení silného názvu pro jednu aplikaci</span><span class="sxs-lookup"><span data-stu-id="32afe-121">Disable the strong-name bypass feature for a single application</span></span>  
  
1. <span data-ttu-id="32afe-122">Otevřete nebo vytvořte konfigurační soubor aplikace.</span><span class="sxs-lookup"><span data-stu-id="32afe-122">Open or create the application configuration file.</span></span>  
  
     <span data-ttu-id="32afe-123">Další informace o tomto souboru naleznete v části konfigurační soubory aplikace v tématu [Konfigurace aplikací](../../framework/configure-apps/index.md).</span><span class="sxs-lookup"><span data-stu-id="32afe-123">For more information about this file, see the Application Configuration Files section in [Configure apps](../../framework/configure-apps/index.md).</span></span>  
  
2. <span data-ttu-id="32afe-124">Přidejte následující položku:</span><span class="sxs-lookup"><span data-stu-id="32afe-124">Add the following entry:</span></span>  
  
    ```xml  
    <configuration>  
      <runtime>  
        <bypassTrustedAppStrongNames enabled="false" />  
      </runtime>  
    </configuration>  
    ```  
  
 <span data-ttu-id="32afe-125">Funkci pro obejití aplikace můžete obnovit odebráním nastavení konfiguračního souboru nebo nastavením atributu na `true`.</span><span class="sxs-lookup"><span data-stu-id="32afe-125">You can restore the bypass feature for the application by removing the configuration file setting or by setting the attribute to `true`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="32afe-126">Ověřování silných názvů můžete u aplikace zapnout a vypnout jenom v případě, že je pro počítač povolená funkce obcházení.</span><span class="sxs-lookup"><span data-stu-id="32afe-126">You can turn strong-name validation on and off for an application only if the bypass feature is enabled for the computer.</span></span> <span data-ttu-id="32afe-127">Pokud byla funkce obcházení pro počítač vypnuta, silné názvy jsou ověřeny pro všechny aplikace a nelze obejít ověřování pro jednu aplikaci.</span><span class="sxs-lookup"><span data-stu-id="32afe-127">If the bypass feature has been turned off for the computer, strong names are validated for all applications and you cannot bypass validation for a single application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32afe-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="32afe-128">See also</span></span>

- [<span data-ttu-id="32afe-129">Sn.exe (nástroj pro silný název)</span><span class="sxs-lookup"><span data-stu-id="32afe-129">Sn.exe (Strong Name Tool)</span></span>](../../framework/tools/sn-exe-strong-name-tool.md)
- [<span data-ttu-id="32afe-130">\<bypassTrustedAppStrongNames – element ></span><span class="sxs-lookup"><span data-stu-id="32afe-130">\<bypassTrustedAppStrongNames> element</span></span>](../../framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)
- [<span data-ttu-id="32afe-131">Vytváření a používání sestavení se silným názvem</span><span class="sxs-lookup"><span data-stu-id="32afe-131">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
