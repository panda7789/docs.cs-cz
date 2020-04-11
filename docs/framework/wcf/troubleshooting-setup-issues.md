---
title: Odstraňování potíží s instalací
ms.date: 03/30/2017
ms.assetid: 1644f885-c408-4d5f-a5c7-a1a907bc8acd
ms.openlocfilehash: 2cd9ced4f0780b1a6f63e4a5833e20ac91870121
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121584"
---
# <a name="troubleshoot-setup-issues"></a>Poradce při potížích s instalací

Tento článek popisuje, jak řešit problémy Windows Communication Foundation (WCF).  
  
## <a name="some-windows-communication-foundation-registry-keys-are-not-repaired-by-performing-an-msi-repair-operation-on-the-net-framework-30"></a>Některé klíče registru Windows Communication Foundation nejsou opraveny provedením operace opravy MSI v rozhraní .NET Framework 3.0  
 Pokud odstraníte některý z následujících klíčů registru:  
  
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelService 3.0.0.0  
  
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelOperation 3.0.0.0  
  
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelEndpoint 3.0.0.0  
  
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SMSvcHost 3.0.0.0  
  
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\MSDTC Bridge 3.0.0  
  
 Klíče nejsou znovu vytvořeny, pokud spustíte opravu pomocí instalačního programu rozhraní .NET Framework 3.0 spuštěného z ovládacího **panelu** **Přidat nebo odebrat programy** . Chcete-li znovu vytvořit tyto klíče správně, musí uživatel odinstalovat a znovu nainstalovat rozhraní .NET Framework 3.0.  
  
## <a name="wmi-service-corruption-blocks-installation-of-the-windows-communication-foundation-wmi-provider-during-installation-of-net-framework-30-package"></a>Poškození služby WMI Blokuje instalace zprostředkovatele wmi služby Windows Communication Foundation během instalace balíčku rozhraní .NET Framework 3.0  
 Poškození služby WMI může blokovat instalaci zprostředkovatele wmi služby WMI služby Windows Communication Foundation. Během instalace instalační program Windows Communication Foundation nemůže zaregistrovat soubor WCF.mof pomocí součásti mofcomp.exe. Následuje seznam příznaků:  
  
1. Instalace rozhraní .NET Framework 3.0 byla úspěšně dokončena, ale zprostředkovatel wmi wcf není zaregistrován.  
  
2. V protokolu událostí aplikace se zobrazí chybová událost, která odkazuje na problémy s registrací zprostředkovatele služby WMI pro wcf nebo spuštění mofcomp.exe.  
  
3. Soubor protokolu instalace s názvem dd_wcf_retCA* v adresáři %temp% uživatele obsahuje odkazy na selhání registrace zprostředkovatele wcf wmi.  
  
4. Výjimka, například jedna, může být uvedena následující v protokolu událostí nebo v souboru protokolu trasování instalace:  
  
     ServiceModelReg [11:09:59:046]: System.ApplicationException: Neočekávaný výsledek 3 spuštění E:\WINDOWS\system32\wbem\mofcomp.exe s "E:\WINDOWS\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModel.mof"  
  
     nebo:  
  
     ServiceModelReg [07:19:33:843]: System.TypeInitializationException: Typ inicializátoru pro 'System.Management.ManagementPath' vyvolal výjimku. ---> System.Runtime.InteropServices.COMException (0x80040154): Načítání továrny třídy COM pro komponenty s CLSID {CF4CC405-E2C5-4DDD-B3CE-5E7582D8C9FA} se nezdařilo z důvodu následující chyby: 80040154.  
  
     nebo:  
  
     ServiceModelReg [07:19:32:750]: System.IO.FileNotFoundException: Nelze načíst soubor nebo sestavení C:\WINDOWS\system32\wbem\mofcomp.exe nebo jednu z jeho závislostí. Systém nemůže najít zadaný soubor.  
  
     Název souboru: 'C:\WINDOWS\system32\wbem\mofcomp.exe  
  
 Chcete-li vyřešit problém popsaný výše, je třeba je vyřešit následující kroky.  
  
1. Spusťte [nástroj pro diagnostiku služby WMI a](https://www.microsoft.com/download/details.aspx?id=7684) opravte službu WMI. Další informace o použití tohoto nástroje naleznete v tématu [WMI Diagnosis Utility](https://docs.microsoft.com/previous-versions/tn-archive/ff404265(v%3dmsdn.10)).  
  
 Opravte instalaci rozhraní .NET Framework 3.0 pomocí apletu **Přidat nebo odebrat programy** umístěného v **Ovládacích panelech**nebo odinstalujte/přeinstalujte rozhraní .NET Framework 3.0.  
  
## <a name="repairing-net-framework-30-after-net-framework-35-installation-removes-configuration-elements-introduced-by-net-framework-35-in-machineconfig"></a>Oprava rozhraní .NET Framework 3.0 po instalaci rozhraní .NET Framework 3.5 odebere konfigurační prvky zavedené rozhraním .NET Framework 3.5 v souboru machine.config  
 Pokud po instalaci rozhraní .NET Framework 3.5 opravíte rozhraní .NET Framework 3.0, budou odebrány konfigurační prvky zavedené rozhraním .NET Framework 3.5 v souboru machine.config. Web.config však zůstane beze změny. Řešení je opravit rozhraní .NET Framework 3.5 po tomto přes ARP nebo použijte [Nástroj pro registraci služby WorkFlow (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) s přepínačem. `/c`  
  
 [Nástroj pro registraci služby WorkFlow (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) naleznete na adrese %windir%\Microsoft.NET\framework\v3.5\ nebo %windir%\Microsoft.NET\framework64\v3.5\  
  
## <a name="configure-iis-properly-for-wcfwf-webhost-after-installing-net-framework-35"></a>Konfigurace služby IIS správně pro webhosting WCF/WF po instalaci rozhraní .NET Framework 3.5  
 Pokud se instalaci rozhraní .NET Framework 3.5 nepodaří nakonfigurovat další nastavení konfigurace služby IIS související s protokolem WCF, zaznamená chybu v protokolu instalace a pokračuje. Jakýkoli pokus o spuštění aplikací WorkflowServices se nezdaří, protože chybí požadované nastavení konfigurace. Například načítání xoml nebo pravidla služby může selhat.  
  
 Chcete-li tento problém vyřešit, použijte [nástroj pro registraci služby WorkFlow (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) s přepínačem `/c` pro správnou konfiguraci map skriptů služby IIS v počítači. [Nástroj pro registraci služby WorkFlow (WFServicesReg.exe)](workflow-service-registration-tool-wfservicesreg-exe.md) naleznete na adrese %windir%\Microsoft.NET\framework\v3.5\ nebo %windir%\Microsoft.NET\framework64\v3.5\  
  
## <a name="could-not-load-type-systemservicemodelactivationhttpmodule-from-assembly-systemservicemodel-version-3000-cultureneutral-publickeytokenb77a5c561934e089"></a>Nelze načíst typ System.ServiceModel.Activation.HttpModule z sestavení System.ServiceModel, verze 3.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089.  
 K této chybě dochází, pokud je nainstalována rozhraní .NET Framework 4 a potom je povolena aktivace protokolu HTTP WCF. Chcete-li tento problém vyřešit, spusťte následující příkazový řádek z příkazového řádku pro vývojáře pro sady Visual Studio:  
  
```console
aspnet_regiis.exe -i -enable  
```  
  
## <a name="see-also"></a>Viz také

- [Pokyny k instalaci](./samples/set-up-instructions.md)
