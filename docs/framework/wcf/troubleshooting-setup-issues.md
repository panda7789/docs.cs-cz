---
title: "Odstraňování potíží s instalací"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1644f885-c408-4d5f-a5c7-a1a907bc8acd
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 284805f8ca1fb9778dc6bccd9807fa86dc7e2d77
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="troubleshooting-setup-issues"></a>Odstraňování potíží s instalací
Toto téma popisuje postupy řešení [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] nastavit problémy.  
  
## <a name="some-windows-communication-foundation-registry-keys-are-not-repaired-by-performing-an-msi-repair-operation-on-the-net-framework-30"></a>Některé klíče registru Windows Communication Foundation nejsou opravit provedením operace opravy MSI v rozhraní .NET Framework 3.0  
 Pokud odstraníte všechny tyto klíče registru:  
  
-   HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelService 3.0.0.0  
  
-   HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelOperation 3.0.0.0  
  
-   HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelEndpoint 3.0.0.0  
  
-   HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SMSvcHost 3.0.0.0  
  
-   Most HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSDTC 3.0.0.0  
  
 Klíče nejsou vytvořeny znovu, pokud nespustíte opravu pomocí rozhraní .NET Framework 3.0 Instalační program spustit z **přidat nebo odebrat programy** aplet v **ovládací panely**. K opětovnému vytvoření těchto klíčů správně, musí uživatel odinstalovat a znovu nainstalujte rozhraní .NET Framework 3.0.  
  
## <a name="wmi-service-corruption-blocks-installation-of-the-windows-communication-foundation-wmi-provider-during-installation-of-net-framework-30-package"></a>Rozhraní WMI služby poškození blokuje instalaci zprostředkovatele rozhraní WMI Windows Communication Foundation při instalaci rozhraní .NET Framework 3.0 balíčku  
 Poškození služby WMI může blokovat instalaci zprostředkovatele rozhraní WMI Windows Communication Foundation. Během instalace služby Windows Communication Foundation je instalační program nemůže zaregistrovat soubor MOF WCF pomocí mofcomp.exe součásti. Následuje seznam příznaky:  
  
1.  Úspěšného dokončení instalace rozhraní .NET framework 3.0, ale není zaregistrovaný zprostředkovatel rozhraní WMI WCF.  
  
2.  Událost chyby se objeví v protokolu událostí aplikace, který odkazuje na problémy registrace zprostředkovatele rozhraní WMI na WCF, nebo spuštěné mofcomp.exe.  
  
3.  Soubor protokolu o instalaci s názvem dd_wcf_retCA * v adresáři % temp % uživatele obsahuje odkazy na selhání registrace zprostředkovatele rozhraní WCF WMI.  
  
4.  V souboru protokolu trasování v protokolu událostí nebo instalace nemusí být zobrazeny výjimku, například u takové, které jsou následující:  
  
     ServiceModelReg [11:09:59:046]: System.ApplicationException: neočekávaný výsledek 3 provádění E:\WINDOWS\system32\wbem\mofcomp.exe s "E:\WINDOWS\Microsoft.NET\Framework\v3.0\Windows komunikace Foundation\ServiceModel.mof"  
  
     nebo:  
  
     ServiceModelReg [07:19:33:843]: System.TypeInitializationException: typ inicializátoru pro 'System.Management.ManagementPath' došlo k výjimce. ---> System.Runtime.InteropServices.COMException (0x80040154): načítání objektu pro vytváření třídy COM pro součást s CLSID {CF4CC405-E2C5-4DDD-B3CE-5E7582D8C9FA} se nezdařilo z důvodu následující chyby: 80040154.  
  
     nebo:  
  
     ServiceModelReg [07:19:32:750]: System.IO.FileNotFoundException: Nelze načíst soubor nebo sestavení 'C:\WINDOWS\system32\wbem\mofcomp.exe nebo jednu ze závislostí. Systém nemůže najít zadaný soubor.  
  
     Název souboru: "C:\WINDOWS\system32\wbem\mofcomp.exe  
  
 Chcete-li vyřešit problém popsaný dřív musí být zadán následující kroky.  
  
1.  Spustit [diagnostická utilita WMI, verze 2.0](http://go.microsoft.com/fwlink/?LinkId=94685) k opravě služby WMI. [!INCLUDE[crabout](../../../includes/crabout-md.md)]Pomocí tohoto nástroje najdete v článku [diagnostická utilita WMI](http://go.microsoft.com/fwlink/?LinkId=94686) tématu.  
  
 Opravte instalaci rozhraní .NET Framework 3.0 pomocí **přidat nebo odebrat programy** aplet umístěný v **ovládací panely**, nebo odinstalování a nová instalace rozhraní .NET Framework 3.0.  
  
## <a name="repairing-net-framework-30-after-net-framework-35-installation-removes-configuration-elements-introduced-by-net-framework-35-in-machineconfig"></a>Oprava rozhraní .NET Framework 3.0 po instalaci rozhraní .NET Framework 3.5 odebere konfigurace – elementy zavedených v rozhraní .NET Framework 3.5 v souboru machine.config  
 Pokud je po dokončení instalace provést opravu systému rozhraní .NET Framework 3.0 [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)], konfigurace – elementy zaváděné [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] v souboru machine.config odebrané. Soubor web.config však zůstane beze změn. Řešením je oprava [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] po prostřednictvím protokolu ARP, nebo použijte [nástroj WorkFlow Service Registration (WFServicesReg.exe)](../../../docs/framework/wcf/workflow-service-registration-tool-wfservicesreg-exe.md) s `/c` přepínače.  
  
 [Nástroj workFlow Service Registration (WFServicesReg.exe)](../../../docs/framework/wcf/workflow-service-registration-tool-wfservicesreg-exe.md) najdete na %windir%\Microsoft.NET\framework\v3.5\ nebo %windir%\Microsoft.NET\framework64\v3.5\  
  
## <a name="configure-iis-properly-for-wcfwf-webhost-after-installing-net-framework-35"></a>Konfigurace služby IIS pro webového hostitele WCF/WF správně po instalaci rozhraní .NET Framework 3.5  
 Když [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] instalace se nedaří konfigurovat další [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]-související nastavení konfigurace služby IIS, je zaznamená chybu v protokolu instalace a pokračuje. Jakýkoli pokus o spuštění WorkflowServices aplikací se nezdaří, vzhledem k tomu, že chybí požadovaná konfigurační nastavení. Například může selhat načítání xoml nebo pravidla.  
  
 Chcete-li vyřešit tento problém, použijte [nástroj WorkFlow Service Registration (WFServicesReg.exe)](../../../docs/framework/wcf/workflow-service-registration-tool-wfservicesreg-exe.md) s `/c` přepínač tak, aby správně nakonfigurovat mapy skriptů služby IIS na počítači. [Nástroj workFlow Service Registration (WFServicesReg.exe)](../../../docs/framework/wcf/workflow-service-registration-tool-wfservicesreg-exe.md) najdete na %windir%\Microsoft.NET\framework\v3.5\ nebo %windir%\Microsoft.NET\framework64\v3.5\  
  
## <a name="could-not-load-type-systemservicemodelactivationhttpmodule-from-assembly-systemservicemodel-version-3000-cultureneutral-publickeytokenb77a5c561934e089"></a>Nelze načíst typ 'System.ServiceModel.Activation.HttpModule' ze sestavení ' System.ServiceModel, verze 3.0.0.0, Culture = neutral, PublicKeyToken = b77a5c561934e089.  
 K této chybě dojde, pokud [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] je nainstalován a potom [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] je povolená Aktivace protokolem HTTP. Řešení tohoto problému spusťte následující příkaz z příkazového řádku uvnitř [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] příkazového řádku:  
  
```Output  
aspnet_regiis.exe -i -enable  
```  
  
## <a name="see-also"></a>Viz také  
 [Pokyny k instalaci](../../../docs/framework/wcf/samples/set-up-instructions.md)
