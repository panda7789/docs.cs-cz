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
# <a name="how-to-disable-the-strong-name-bypass-feature"></a>Postupy: Zakázat funkci obcházení silného názvu
.NET Framework počínaje verzí 3,5 a Service Pack 1 (SP1) se signatury silného názvu neověřují, pokud je sestavení načteno do objektu s úplným <xref:System.AppDomain> vztahem důvěryhodnosti, jako je <xref:System.AppDomain> například výchozí `MyComputer` hodnota pro zónu. To se označuje jako funkce obcházení silného názvu. V prostředí s úplným vztahem důvěryhodnosti požadavky <xref:System.Security.Permissions.StrongNameIdentityPermission> vždy úspěšné pro podepsaná, plně důvěryhodná sestavení bez ohledu na jejich podpis. Jediným omezením je, že sestavení musí být plně důvěryhodné, protože jeho zóna je plně důvěryhodná. Vzhledem k tomu, že silný název není určujícím faktorem za těchto podmínek, neexistuje žádný důvod, aby jej bylo možné ověřit. Obejít ověřování podpisů se silným názvem přináší významná vylepšení výkonu.  
  
 Funkce bypass se vztahuje na jakékoli sestavení s úplným vztahem důvěryhodnosti, které není podepsané zpožděním a které je načteno do <xref:System.AppDomain> jakékoli plně důvěryhodné z adresáře určeného <xref:System.AppDomainSetup.ApplicationBase%2A> jeho vlastností.  
  
 Funkci obcházení můžete pro všechny aplikace v počítači přepsat nastavením hodnoty klíče registru. Nastavení pro jednu aplikaci můžete přepsat pomocí konfiguračního souboru aplikace. Funkci vynechání nemůžete obnovit pro jednu aplikaci, pokud byla zakázána klíčem registru.  
  
 Pokud přepíšete funkci bypass, silný název se ověří jenom pro správnost. není zaškrtnuta <xref:System.Security.Permissions.StrongNameIdentityPermission>. Pokud chcete potvrdit konkrétní silný název, je nutné provést tuto kontrolu samostatně.  
  
> [!IMPORTANT]
> Možnost vynutit ověřování silného názvu závisí na klíči registru, jak je popsáno v následujícím postupu. Pokud aplikace běží pod účtem, který nemá oprávnění seznamu řízení přístupu (ACL) pro přístup k tomuto klíči registru, nastavení se neprojeví. Je nutné zajistit, aby byla pro tento klíč nakonfigurovaná oprávnění ACL, aby je bylo možné číst pro všechna sestavení.  
  
## <a name="disable-the-strong-name-bypass-feature-for-all-applications"></a>Zakázat funkci obcházení silného názvu pro všechny aplikace  
  
- Na 32 počítačích v systémovém registru vytvořte položku DWORD s hodnotou 0 s názvem `AllowStrongNameBypass` v rámci HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft.\\ NETFramework klíč.  
  
- Na 64 počítačích v systémovém registru vytvořte položku DWORD s hodnotou 0 s názvem `AllowStrongNameBypass` v rámci HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft.\\ NETFramework a HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework klíče.  
  
## <a name="disable-the-strong-name-bypass-feature-for-a-single-application"></a>Zakázání funkce obcházení silného názvu pro jednu aplikaci  
  
1. Otevřete nebo vytvořte konfigurační soubor aplikace.  
  
     Další informace o tomto souboru naleznete v části konfigurační soubory aplikace v tématu [Konfigurace aplikací](../../framework/configure-apps/index.md).  
  
2. Přidejte následující položku:  
  
    ```xml  
    <configuration>  
      <runtime>  
        <bypassTrustedAppStrongNames enabled="false" />  
      </runtime>  
    </configuration>  
    ```  
  
 Funkci pro obejití aplikace můžete obnovit odebráním nastavení konfiguračního souboru nebo nastavením atributu na `true`.  
  
> [!NOTE]
> Ověřování silných názvů můžete u aplikace zapnout a vypnout jenom v případě, že je pro počítač povolená funkce obcházení. Pokud byla funkce obcházení pro počítač vypnuta, silné názvy jsou ověřeny pro všechny aplikace a nelze obejít ověřování pro jednu aplikaci.  
  
## <a name="see-also"></a>Viz také:

- [Sn.exe (nástroj pro silný název)](../../framework/tools/sn-exe-strong-name-tool.md)
- [\<bypassTrustedAppStrongNames – element >](../../framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)
- [Vytváření a používání sestavení se silným názvem](create-use-strong-named.md)
