---
title: Odstraňování potíží s instalací
ms.date: 03/30/2017
ms.assetid: 1644f885-c408-4d5f-a5c7-a1a907bc8acd
ms.openlocfilehash: 586defea0f761f8b6dea691b778d221cff62c7cf
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2019
ms.locfileid: "74281609"
---
# <a name="troubleshooting-setup-issues"></a>Odstraňování potíží s instalací
Toto téma popisuje, jak řešit problémy s nastavením Windows Communication Foundation (WCF).  
  
## <a name="some-windows-communication-foundation-registry-keys-are-not-repaired-by-performing-an-msi-repair-operation-on-the-net-framework-30"></a>Některé klíče registru Windows Communication Foundation nelze opravit pomocí operace opravy MSI v .NET Framework 3,0  
 Pokud odstraníte některý z následujících klíčů registru:  
  
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelService 3.0.0.0  
  
- HKEY_LOCAL_MACHINE \SYSTEM\CurrentControlSet\Services\ServiceModelOperation 3.0.0.0  
  
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\ServiceModelEndpoint 3.0.0.0  
  
- HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\SMSvcHost 3.0.0.0  
  
- 3\.0.0.0 mostu HKEY_LOCAL_MACHINE \SYSTEM\CurrentControlSet\Services\MSDTC  
  
 Klíče se znovu nevytvoří, pokud spustíte opravu pomocí instalačního programu .NET Framework 3,0 spuštěného v apletu **Přidat nebo odebrat programy** v **Ovládacích panelech**. Aby bylo možné znovu vytvořit tyto klíče správně, musí uživatel odinstalovat a znovu nainstalovat .NET Framework 3,0.  
  
## <a name="wmi-service-corruption-blocks-installation-of-the-windows-communication-foundation-wmi-provider-during-installation-of-net-framework-30-package"></a>Poškození služby WMI blokuje instalaci zprostředkovatele Windows Communication Foundation WMI během instalace balíčku .NET Framework 3,0  
 Poškození služby WMI může zablokovat instalaci zprostředkovatele rozhraní WMI Windows Communication Foundation. Během instalace nemůže instalační program Windows Communication Foundation zaregistrovat soubor WCF. mof pomocí komponenty Mofcomp. exe. Níže je seznam příznaků:  
  
1. Instalace .NET Framework 3,0 byla úspěšně dokončena, ale zprostředkovatel WMI služby WCF není zaregistrován.  
  
2. V protokolu událostí aplikace se zobrazí chybová událost, která odkazuje na problémy s registrací zprostředkovatele WMI pro WCF nebo spuštěním Mofcomp. exe.  
  
3. Soubor protokolu instalace s názvem dd_wcf_retCA * v adresáři% Temp% uživatele obsahuje odkazy na selhání registrace zprostředkovatele WMI WCF.  
  
4. V protokolu událostí nebo v souboru protokolu trasování instalace může být uvedena výjimka, například jedna z následujících možností:  
  
     ServiceModelReg [11:09:59:046]: System. ApplicationException: Neočekávaný výsledek 3 provádění E:\WINDOWS\system32\wbem\mofcomp.exe s "E:\WINDOWS\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModel.mof"  
  
     nebo:  
  
     ServiceModelReg [07:19:33:843]: System. TypeInitializationException: inicializátor typu pro: System. Management. ManagementPath vyvolal výjimku. ---> System. Runtime. InteropServices. COMException (0x80040154): načtení objektu pro vytváření tříd modelu COM pro komponentu s identifikátorem CLSID {CF4CC405-E2C5-4DDD-B3CE-5E7582D8C9FA} se nezdařilo z důvodu následující chyby: 80040154.  
  
     nebo:  
  
     ServiceModelReg [07:19:32:750]: System. IO. FileNotFoundException: nelze načíst soubor nebo sestavení ' C:\WINDOWS\system32\wbem\mofcomp.exe ' nebo některou z jeho závislostí. Systém nemůže najít zadaný soubor.  
  
     Název souboru: ' C:\WINDOWS\system32\wbem\mofcomp.exe  
  
 Aby bylo možné vyřešit dříve popsané potíže, je nutné provést následující kroky.  
  
1. Spusťte [WMI Diagnosis Utility verze 2,0,](https://go.microsoft.com/fwlink/?LinkId=94685) abyste mohli opravit službu WMI. Další informace o použití tohoto nástroje najdete v tématu [WMI Diagnosis Utility](https://go.microsoft.com/fwlink/?LinkId=94686) .  
  
 Opravte instalaci .NET Framework 3,0 pomocí apletu **Přidat nebo odebrat programy** umístěného v **Ovládacích panelech**nebo odinstalujte nebo přeinstalujte .NET Framework 3,0.  
  
## <a name="repairing-net-framework-30-after-net-framework-35-installation-removes-configuration-elements-introduced-by-net-framework-35-in-machineconfig"></a>Oprava .NET Framework 3,0 po instalaci .NET Framework 3,5 Odebere prvky konfigurace zavedené .NET Framework 3,5 v souboru Machine. config.  
 Pokud po instalaci .NET Framework 3,5 provádíte opravu .NET Framework 3,0, odeberou se konfigurační prvky, které zavádějí .NET Framework 3,5 v souboru Machine. config. Soubor Web. config však zůstává beze změn. Alternativním řešením je opravit .NET Framework 3,5 po tomto protokolu ARP nebo použít [Nástroj pro registraci služby pracovního postupu (WFServicesReg. exe)](workflow-service-registration-tool-wfservicesreg-exe.md) s přepínačem `/c`.  
  
 [Nástroj pro registraci služby pracovního postupu (WFServicesReg. exe)](workflow-service-registration-tool-wfservicesreg-exe.md) najdete na adrese%windir%\Microsoft.Net\Framework\v3.5\ nebo%windir%\Microsoft.NET\framework64\v3.5\  
  
## <a name="configure-iis-properly-for-wcfwf-webhost-after-installing-net-framework-35"></a>Správná konfigurace IIS pro WCF/WF webhost po instalaci .NET Framework 3,5  
 Pokud se .NET Framework 3,5 instalace nepodaří nakonfigurovat další nastavení konfigurace služby IIS související s WCF, zaznamená chybu v protokolu instalace a pokračuje. Všechny pokusy o spuštění aplikací WorkflowServices selžou, protože chybí požadovaná nastavení konfigurace. Například načtení služby XOML nebo rules může selhat.  
  
 Pokud chcete tento problém vyřešit, použijte [Nástroj pro registraci služby pracovního postupu (WFServicesReg. exe)](workflow-service-registration-tool-wfservicesreg-exe.md) s přepínačem `/c` a správně nakonfigurujte mapy skriptů služby IIS v počítači. [Nástroj pro registraci služby pracovního postupu (WFServicesReg. exe)](workflow-service-registration-tool-wfservicesreg-exe.md) najdete na adrese%windir%\Microsoft.Net\Framework\v3.5\ nebo%windir%\Microsoft.NET\framework64\v3.5\  
  
## <a name="could-not-load-type-systemservicemodelactivationhttpmodule-from-assembly-systemservicemodel-version-3000-cultureneutral-publickeytokenb77a5c561934e089"></a>Typ System. ServiceModel. Activation. HttpModule nelze načíst ze sestavení System. ServiceModel, verze 3.0.0.0, Culture = neutral, PublicKeyToken = b77a5c561934e089.  
 K této chybě dochází, pokud je nainstalovaná .NET Framework 4 a pak je povolená aktivace WCF protokolu HTTP. Problém vyřešíte spuštěním následujícího příkazového řádku z Developer Command Prompt v rámci sady Visual Studio:  
  
```console
aspnet_regiis.exe -i -enable  
```  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k instalaci](./samples/set-up-instructions.md)
