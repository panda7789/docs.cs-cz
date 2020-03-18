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
# <a name="how-to-disable-the-strong-name-bypass-feature"></a>Postup: Zakázání funkce obejití silného názvu
Počínaje rozhraním .NET Framework verze 3.5 Service Pack 1 (SP1) nejsou podpisy silného názvu <xref:System.AppDomain> ověřeny při <xref:System.AppDomain> načtení `MyComputer` sestavení do plně důvěryhodného objektu, například výchozího pro zónu. Tato funkce se označuje jako funkce obejití silného názvu. V prostředí s plnou důvěryhodností požadavky na <xref:System.Security.Permissions.StrongNameIdentityPermission> vždy úspěšné pro podepsaná sestavení s plnou důvěryhodností bez ohledu na jejich podpis. Jediným omezením je, že sestavení musí být plně důvěryhodné, protože jeho zóna je plně důvěryhodná. Vzhledem k tomu, že silný název není určujícím faktorem za těchto podmínek, není důvod pro jeho ověření. Vynechání ověření podpisů silného názvu poskytuje významné zlepšení výkonu.  
  
 Funkce obchvatu se vztahuje na libovolné sestavení s plnou důvěryhodností, které <xref:System.AppDomain> není podepsáno <xref:System.AppDomainSetup.ApplicationBase%2A> zpožděním a které je načteno do libovolného úplného vztahu důvěryhodnosti z adresáře určeného jeho vlastností.  
  
 Funkci přejezdu pro všechny aplikace v počítači můžete přepsat nastavením hodnoty klíče registru. Nastavení pro jednu aplikaci můžete přepsat pomocí konfiguračního souboru aplikace. Funkci obejití pro jednu aplikaci nelze obnovit, pokud byla zakázána klíčem registru.  
  
 Když přepíšete funkci obejití, silný název je ověřen pouze pro správnost; není kontrolována pro <xref:System.Security.Permissions.StrongNameIdentityPermission>. Chcete-li potvrdit konkrétní silný název, musíte tuto kontrolu provést samostatně.  
  
> [!IMPORTANT]
> Schopnost vynutit ověření silného názvu závisí na klíči registru, jak je popsáno v následujícím postupu. Pokud je aplikace spuštěna pod účtem, který nemá oprávnění seznamu řízení přístupu (ACL) pro přístup k tomuto klíči registru, je nastavení neúčinné. Je nutné zajistit, aby byla pro tento klíč nakonfigurována práva acl, aby jej bylo možné číst pro všechna sestavení.  
  
## <a name="disable-the-strong-name-bypass-feature-for-all-applications"></a>Zakázání funkce obejití silného názvu pro všechny aplikace  
  
- V 32bitových počítačích vytvořte v systémovém registru položku `AllowStrongNameBypass` DWORD s hodnotou\\0 pojmenovanou pod HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft . NETFramework.  
  
- V 64bitových počítačích vytvořte v systémovém registru položku `AllowStrongNameBypass` DWORD s hodnotou\\0 pojmenovanou pod HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft . NETFramework a HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework klíče.  
  
## <a name="disable-the-strong-name-bypass-feature-for-a-single-application"></a>Zakázání funkce obejití silného názvu pro jednu aplikaci  
  
1. Otevřete nebo vytvořte konfigurační soubor aplikace.  
  
    Další informace o tomto souboru naleznete v části Soubory konfigurace aplikace v [tématu Konfigurace aplikací](../../framework/configure-apps/index.md).  
  
2. Přidejte následující položku:  
  
    ```xml  
    <configuration>  
      <runtime>  
        <bypassTrustedAppStrongNames enabled="false" />  
      </runtime>  
    </configuration>  
    ```  
  
 Funkci obejití aplikace můžete obnovit odebráním nastavení konfiguračního souboru nebo nastavením atributu na . `true`  
  
> [!NOTE]
> Ověření silného názvu můžete zapnout a vypnout pro aplikaci pouze v případě, že je pro počítač povolena funkce obejití. Pokud byla funkce obejití pro počítač vypnuta, silné názvy jsou ověřeny pro všechny aplikace a nelze obejít ověření pro jednu aplikaci.  
  
## <a name="see-also"></a>Viz také

- [Sn.exe (nástroj pro silný název)](../../framework/tools/sn-exe-strong-name-tool.md)
- [\<bypassTrustedAppStrongNames> element](../../framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)
- [Vytváření a používání sestavení se silným názvem](create-use-strong-named.md)
