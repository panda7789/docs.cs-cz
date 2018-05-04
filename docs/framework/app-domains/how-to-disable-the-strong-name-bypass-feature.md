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
# <a name="how-to-disable-the-strong-name-bypass-feature"></a>Postupy: Zákaz funkce obejití silného názvu
Počínaje verzí rozhraní .NET Framework 3.5 Service Pack 1 (SP1), silné jméno – nedochází k ověřování podpisů při sestavení načtení do plné důvěryhodnosti <xref:System.AppDomain> objektu, například výchozí <xref:System.AppDomain> pro `MyComputer` zóny. Tento proces se označuje jako silné jméno – Nepoužívat funkce. V prostředí plné důvěryhodnosti jsou požadavky na <xref:System.Security.Permissions.StrongNameIdentityPermission> vždy úspěšné pro podepsané, plné důvěryhodnosti sestavení bez ohledu na jejich podpisu. Pouze omezení je, že sestavení musí být plně důvěryhodná, protože je plně důvěryhodný pro časového pásma. Protože se silným názvem není určujícím faktorem za těchto podmínek, neexistuje žádný důvod pro něj má být ověřen. Vynechání ověřování podpisů silných názvů poskytuje významné zlepšení výkonu.  
  
 Funkce obcházení vztahuje na všechny plné důvěryhodnosti sestavení, která není zpoždění podepsaný a který je načten do jakékoli plné důvěryhodnosti <xref:System.AppDomain> z adresáře určeného jeho <xref:System.AppDomainSetup.ApplicationBase%2A> vlastnost.  
  
 Funkce obcházení pro všechny aplikace v počítači můžete přepsat nastavením hodnoty klíče registru. Nastavení pro jednu aplikaci můžete přepsat pomocí konfiguračního souboru aplikace. Funkce obcházení pro jednu aplikaci nelze obnovit, pokud je zakázaná pomocí klíče registru.  
  
 Při přepsání funkce obejití silného názvu ověřován pouze pro správnost; není kontrolován pro <xref:System.Security.Permissions.StrongNameIdentityPermission>. Pokud chcete potvrdit konkrétní silným názvem, budete muset provést tuto kontrolu samostatně.  
  
> [!IMPORTANT]
>  Schopnost vynutit ověřování silných názvů závisí na klíč registru, jak je popsáno v následujícím postupu. Pokud aplikace běží pod účtem, který nemá oprávnění seznamu ACL řízení přístupu pro přístup k tomuto klíči registru, toto nastavení je neúčinné. Je nutné zajistit, že práva seznamu ACL jsou konfigurovány pro tento klíč tak, aby ho mohou číst pro všechna sestavení.  
  
### <a name="to-disable-the-strong-name-bypass-feature-for-all-applications"></a>Chcete-li zakázat vynechat silné jméno – funkce pro všechny aplikace  
  
-   Na 32bitové počítače v registru systému vytvořte novou položku DWORD s hodnotou 0 s názvem `AllowStrongNameBypass` pod HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework klíč.  
  
-   Na 64bitových počítačích, v registru systému vytvořit záznam typu DWORD s hodnotou 0 s názvem `AllowStrongNameBypass` pod HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework a HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\. NETFramework klíče.  
  
### <a name="to-disable-the-strong-name-bypass-feature-for-a-single-application"></a>Chcete-li zakázat vynechání silné jméno – funkce pro jednu aplikaci  
  
1.  Otevřete nebo vytvořte konfigurační soubor aplikace.  
  
     Další informace o tomto souboru, najdete v části konfigurační soubory aplikace v [konfigurace aplikace](../../../docs/framework/configure-apps/index.md).  
  
2.  Přidejte následující položky:  
  
    ```xml  
    <configuration>  
      <runtime>  
        <bypassTrustedAppStrongNames enabled="false" />  
      </runtime>  
    </configuration>  
    ```  
  
 Funkci jednorázové přihlášení pro aplikaci můžete obnovit odebráním nastavení konfigurace souborů nebo nastavením atributu na hodnotu "true".  
  
> [!NOTE]
>  Ověřování silných názvů zapnout a vypnout pro aplikaci můžete zapnout pouze v případě, že je povolena funkce obcházení pro počítač. Pokud funkce obcházení bylo vypnuto pro počítač, se ověřují silné názvy pro všechny aplikace, a nemůžete vynechat ověření pro jednu aplikaci.  
  
## <a name="see-also"></a>Viz také  
 [Sn.exe (nástroj pro silný název)](../../../docs/framework/tools/sn-exe-strong-name-tool.md)  
 [\<bypasstrustedappstrongnames – > elementu](../../../docs/framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)  
 [Vytváření a používání sestavení se silným názvem](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
