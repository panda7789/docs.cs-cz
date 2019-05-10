---
title: 'Postupy: Zákaz funkce obejití silného názvu'
ms.date: 03/30/2017
helpviewer_keywords:
- strong-name bypass feature
- strong-named assemblies, loading into trusted application domains
ms.assetid: 234e088c-3b11-495a-8817-e0962be79d82
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 20b482ee94446ffa863697d8c25276658a4bb122
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64593617"
---
# <a name="how-to-disable-the-strong-name-bypass-feature"></a>Postupy: Zákaz funkce obejití silného názvu
Počínaje verzí rozhraní .NET Framework 3.5 Service Pack 1 (SP1), podpisy se silným názvem nejsou ověřovány, pokud je sestavení načteno do plně důvěryhodné <xref:System.AppDomain> objektu, například výchozí <xref:System.AppDomain> pro `MyComputer` zóny. To se označuje jako silného názvu obejít funkce. V prostředí úplného vztahu důvěryhodnosti vyžaduje pro <xref:System.Security.Permissions.StrongNameIdentityPermission> vždy úspěšné pro podepsané sestavení úplného vztahu důvěryhodnosti, bez ohledu na jejich podpisu. Jediným omezením je, že sestavení musí být plně důvěryhodné, protože jeho zóna je plně důvěryhodné. Protože silný název není určujícím faktorem za těchto podmínek, neexistuje žádný důvod pro něj má být ověřen. Vynechání ověřování podpisy se silným názvem poskytuje výrazné zlepšení výkonu.  
  
 Jednorázové přihlášení funkce se vztahuje na všechny sestavení úplného vztahu důvěryhodnosti, který se zpožděným podpisem a, který je načten do jakékoli úplného vztahu důvěryhodnosti <xref:System.AppDomain> z adresáře zadaného parametrem jeho <xref:System.AppDomainSetup.ApplicationBase%2A> vlastnost.  
  
 Funkce obejití pro všechny aplikace na počítači můžete přepsat tak, že nastavíte hodnotu klíče registru. Nastavení pro jednu aplikaci lze přepsat pomocí konfiguračního souboru aplikace. Funkce obejití pro jednu aplikaci nelze obnovit, pokud byla zakázaná pomocí klíče registru.  
  
 Při přepsání funkce obejití silného názvu je ověřen pouze pro správnosti; není zaškrtnuté políčko pro <xref:System.Security.Permissions.StrongNameIdentityPermission>. Pokud chcete potvrdit specifický silný název, budete muset provést kontroly samostatně.  
  
> [!IMPORTANT]
>  Schopnost vynutit ověřování silných názvů závisí na klíč registru, jak je popsáno v následujícím postupu. Pokud aplikace běží pod účtem, který nemá přístup k ovládacího prvku seznam (ACL) oprávnění pro přístup k tomuto klíči registru, nastavení je neefektivní. Musí zkontrolovat, jestli seznam ACL práva konfigurované pro tento klíč tak, že bude načtena pro všechna sestavení.  
  
### <a name="to-disable-the-strong-name-bypass-feature-for-all-applications"></a>Zakázat obejití silného názvu funkce pro všechny aplikace  
  
- Na 32bitových počítačích, v systémovém registru vytvořte položku DWORD s hodnotou 0 s názvem `AllowStrongNameBypass` pod HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework klíč.  
  
- Na 64bitových počítačích, v systémovém registru vytvořte položku DWORD s hodnotou 0 s názvem `AllowStrongNameBypass` pod HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework a HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework klíče.  
  
### <a name="to-disable-the-strong-name-bypass-feature-for-a-single-application"></a>Zakázat obejití silného názvu funkce pro jednu aplikaci  
  
1. Otevřete nebo vytvořte konfigurační soubor aplikace.  
  
     Další informace o tomto souboru najdete v části konfiguračních souborů aplikace v [konfigurace aplikace](../../../docs/framework/configure-apps/index.md).  
  
2. Přidejte následující položku:  
  
    ```xml  
    <configuration>  
      <runtime>  
        <bypassTrustedAppStrongNames enabled="false" />  
      </runtime>  
    </configuration>  
    ```  
  
 Funkce jednorázové přihlášení pro aplikaci můžete obnovit tak, že odeberete nastavení konfiguračního souboru nebo nastavením atributu na hodnotu "true".  
  
> [!NOTE]
>  Ověření silných názvů zapnutí a vypnutí pro aplikaci můžete vypnout jenom v případě, že je povolena funkce jednorázové přihlášení pro počítač. Pokud jsou vypnuté funkci jednorázové přihlášení pro počítač, se ověří silné názvy pro všechny aplikace a nemůže obejít ověření pro jednu aplikaci.  
  
## <a name="see-also"></a>Viz také:

- [Sn.exe (nástroj pro silný název)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)
- [\<bypassTrustedAppStrongNames> Element](../../../docs/framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)
- [Vytváření a používání sestavení se silným názvem](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
