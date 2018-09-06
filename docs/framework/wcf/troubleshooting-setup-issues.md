---
title: Odstraňování potíží s instalací
ms.date: 03/30/2017
ms.assetid: 1644f885-c408-4d5f-a5c7-a1a907bc8acd
ms.openlocfilehash: 0270bd8c1006b39805e3486c4fef0cb379089ea8
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43805127"
---
# <a name="troubleshooting-setup-issues"></a>Odstraňování potíží s instalací
Toto téma popisuje, jak řešit problémy, nastavte Windows Communication Foundation (WCF).  
  
## <a name="some-windows-communication-foundation-registry-keys-are-not-repaired-by-performing-an-msi-repair-operation-on-the-net-framework-30"></a>Některé klíče registru Windows Communication Foundation se opravila provedením operace opravy MSI v rozhraní .NET Framework 3.0  
 Pokud odstraníte některý z následujících klíčů registru:  
  
-   HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelService 3.0.0.0  
  
-   HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelOperation 3.0.0.0  
  
-   HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelEndpoint 3.0.0.0  
  
-   HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SMSvcHost 3.0.0.0  
  
-   Most HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSDTC 3.0.0.0  
  
 Klíče znovu nevytvoří Pokud nespustíte opravu pomocí spustit z instalačního programu .NET Framework 3.0 **přidat nebo odebrat programy** aplet v **ovládací panely**. Uživatel musí znovu vytvořit tyto klíče správně, odinstalujte a znovu nainstalovat rozhraní .NET Framework 3.0.  
  
## <a name="wmi-service-corruption-blocks-installation-of-the-windows-communication-foundation-wmi-provider-during-installation-of-net-framework-30-package"></a>Rozhraní WMI služby poškození blokuje instalaci zprostředkovatele služby Windows Communication Foundation WMI během instalace balíčku rozhraní .NET Framework 3.0  
 Poškození služby WMI může blokovat instalace zprostředkovatele služby Windows Communication Foundation WMI. Při instalaci Windows Communication Foundation nelze registrovat soubor MOF WCF pomocí mofcomp.exe komponenty instalačního programu. Následuje seznam příznaky:  
  
1.  Úspěšného dokončení instalace rozhraní .NET framework 3.0, ale není zaregistrovaný zprostředkovatel rozhraní WMI WCF.  
  
2.  Událost chyby se objeví v protokolu událostí aplikace, která odkazuje na problémy s registrací zprostředkovatele rozhraní WMI na WCF nebo systémem mofcomp.exe.  
  
3.  Soubor protokolu s názvem dd_wcf_retCA * v adresáři % temp % uživatele obsahuje odkazy na selhání se zaregistrovat poskytovatele služby WMI WCF.  
  
4.  Například následující výjimku mohou být uvedeny v souboru protokolu událostí nebo nastavení protokolu trasování:  
  
     ServiceModelReg [11:09:59:046]: System.ApplicationException: neočekávaný výsledek 3 provádění E:\WINDOWS\system32\wbem\mofcomp.exe s "Foundation\ServiceModel.mof E:\WINDOWS\Microsoft.NET\Framework\v3.0\Windows komunikaci"  
  
     nebo:  
  
     ServiceModelReg [07:19:33:843]: System.TypeInitializationException: Typ obsahuje inicializační proceduru "System.Management.ManagementPath" došlo k výjimce. ---> System.Runtime.InteropServices.COMException (0x80040154): načítání vytváření tříd modelu COM pro komponentu s identifikátorem CLSID {CF4CC405-E2C5-4DDD-B3CE-5E7582D8C9FA} se nezdařilo kvůli následující chybě: 80040154.  
  
     nebo:  
  
     ServiceModelReg [07:19:32:750]: System.IO.FileNotFoundException: nepovedlo se načíst soubor nebo sestavení 'C:\WINDOWS\system32\wbem\mofcomp.exe' nebo některou z jeho závislostí. Systém nemůže najít zadaný soubor.  
  
     Název souboru: "C:\WINDOWS\system32\wbem\mofcomp.exe  
  
 Následující kroky musí následovat problém, jak je popsáno výše.  
  
1.  Spustit [diagnostická utilita WMI, verze 2.0](https://go.microsoft.com/fwlink/?LinkId=94685) opravte službu WMI. Další informace o použití tohoto nástroje najdete v tématu [diagnostická utilita WMI](https://go.microsoft.com/fwlink/?LinkId=94686) tématu.  
  
 Opravte instalaci rozhraní .NET Framework 3.0 pomocí **přidat nebo odebrat programy** aplet umístěný v **ovládací panely**, nebo odinstalování a nová instalace rozhraní .NET Framework 3.0.  
  
## <a name="repairing-net-framework-30-after-net-framework-35-installation-removes-configuration-elements-introduced-by-net-framework-35-in-machineconfig"></a>Oprava rozhraní .NET Framework 3.0 po instalaci rozhraní .NET Framework 3.5 odebere konfigurační prvky zavedené rozhraním .NET Framework 3.5 v souboru machine.config  
 Pokud je po instalaci provést opravu rozhraní .NET Framework 3.0 [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)], konfigurační prvky zavedené [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] v souboru machine.config se odeberou. Ale zůstane beze změny souboru web.config. Alternativním řešením je oprava [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] po prostřednictvím protokolu ARP, nebo použijte [nástroj WorkFlow Service Registration (WFServicesReg.exe)](../../../docs/framework/wcf/workflow-service-registration-tool-wfservicesreg-exe.md) s `/c` přepnout.  
  
 [Nástroj workFlow Service Registration (WFServicesReg.exe)](../../../docs/framework/wcf/workflow-service-registration-tool-wfservicesreg-exe.md) lze nalézt v %windir%\Microsoft.NET\framework\v3.5\ nebo %windir%\Microsoft.NET\framework64\v3.5\  
  
## <a name="configure-iis-properly-for-wcfwf-webhost-after-installing-net-framework-35"></a>Konfigurace služby IIS pro Webhost WCF/WF správně po instalaci rozhraní .NET Framework 3.5  
 Když [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] instalace se nedaří konfigurovat další nastavení konfigurace související s WCF služby IIS, zaznamená chybu do protokolu v protokolu instalace a bude pokračovat. Jakékoli pokusy o spuštění WorkflowServices aplikací se nezdaří, protože chybí požadovaná nastavení konfigurace. Například může selhat načítání služby xoml nebo pravidla.  
  
 Chcete-li vyřešit tento problém, použijte [nástroj WorkFlow Service Registration (WFServicesReg.exe)](../../../docs/framework/wcf/workflow-service-registration-tool-wfservicesreg-exe.md) s `/c` přepínač tak, aby správně nakonfigurovat mapy skriptů služby IIS na počítači. [Nástroj workFlow Service Registration (WFServicesReg.exe)](../../../docs/framework/wcf/workflow-service-registration-tool-wfservicesreg-exe.md) lze nalézt v %windir%\Microsoft.NET\framework\v3.5\ nebo %windir%\Microsoft.NET\framework64\v3.5\  
  
## <a name="could-not-load-type-systemservicemodelactivationhttpmodule-from-assembly-systemservicemodel-version-3000-cultureneutral-publickeytokenb77a5c561934e089"></a>Nelze načíst typ 'System.ServiceModel.Activation.HttpModule' ze sestavení ' System.ServiceModel, verze 3.0.0.0, Culture = neutral, PublicKeyToken = b77a5c561934e089 "  
 K této chybě dochází, pokud [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] je nainstalován a pak je povolená aktivace WCF protokolem HTTP. Řešení tohoto problému spusťte následující příkaz z příkazového řádku uvnitř [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] příkazového řádku:  
  
```Output  
aspnet_regiis.exe -i -enable  
```  
  
## <a name="see-also"></a>Viz také  
 [Pokyny k instalaci](../../../docs/framework/wcf/samples/set-up-instructions.md)
