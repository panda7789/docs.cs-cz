---
title: Nástroj WS-AtomicTransaction Configuration Utility (wsatConfig.exe)
ms.date: 03/30/2017
ms.assetid: 1c56cf98-3963-46d5-a4e1-482deae58c58
ms.openlocfilehash: 31b2b3cf16857bf08a4f8d09f47f80d9b34a53b8
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43659957"
---
# <a name="ws-atomictransaction-configuration-utility-wsatconfigexe"></a>Nástroj WS-AtomicTransaction Configuration Utility (wsatConfig.exe)
Nástroj pro konfiguraci WS-AtomicTransaction slouží ke konfiguraci základní nastavení WS-AtomicTransaction podpory.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
wsatConfig [Options]  
```  
  
## <a name="remarks"></a>Poznámky  
 Tento nástroj příkazového řádku můžete použít ke konfiguraci základních nastavení WS-AT v místním počítači. Pokud budete muset nakonfigurovat nastavení na místních i vzdálených počítačích, používejte modulu snap-in konzoly MMC podle popisu v [konfigurace WS-Atomic podpora transakcí](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md).  
  
 Nástroje příkazového řádku najdete v umístění instalace sady Windows SDK, konkrétně  
  
 Foundation\wsatConfig.exe %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows komunikace  
  
 Pokud používáte [!INCLUDE[wxp](../../../includes/wxp-md.md)] nebo [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], je nutné stáhnout aktualizace před spuštěním WsatConfig.exe. Další informace o této aktualizaci najdete v tématu [aktualizace pro Commerce Server 2007 (KB912817)](https://go.microsoft.com/fwlink/?LinkId=95340) a [dostupnost systému Windows XP modelu COM + opravu Hotfix kumulativní balíček 13](https://go.microsoft.com/fwlink/?LinkId=95341).  
  
 V následující tabulce jsou uvedeny možnosti, které lze použít s WS-AtomicTransaction Configuration Utility (wsatConfig.exe).  
  
> [!NOTE]
>  Při nastavení certifikátu SSL pro vybraný port přepsat původní certifikát SSL přidružený tento port, pokud existuje.  
  
|Možnosti|Popis|  
|-------------|-----------------|  
|-účty:\<účet >|Určuje čárkami oddělený seznam účty, které se mohou účastnit v WS-AtomicTransaction. Platnost těchto účtů není povolená.|  
|-accountsCerts:\<thumb >&#124;"Issuer\SubjectName" >|Určuje čárkami oddělený seznam certifikáty, které se mohou účastnit v WS-AtomicTransaction. Certifikáty jsou označeny kryptografickým otiskem nebo párem Issuer\SubjectName. Použijte {EMPTY} pro název subjektu, pokud je prázdný.|  
|-endpointCert: < počítač&#124;\<thumb >&#124;"Issuer\SubjectName" >|Používá certifikát počítače nebo jiný certifikát místního koncového bodu určeného kryptografickým otiskem nebo Issuer\SubjectName pár. {EMPTY} používá pro název subjektu, pokud je prázdný.|  
|-maxTimeout:\<sekundu >|Určuje maximální časový limit v sekundách. Platné hodnoty jsou od 0 do 3600.|  
|– network:\<povolit&#124;zakázat >|Povoluje nebo zakazuje podporu sítě WS-AtomicTransaction.|  
|– port:\<portNum >|Nastavuje HTTPS port pro WS-AtomicTransaction.<br /><br /> Pokud už jste povolili brány firewall před spuštěním tohoto nástroje, port, který se automaticky registruje v seznamu výjimek. Pokud brána firewall je zakázaná před spuštěním tohoto nástroje, další není nic nakonfigurované týkající se brány firewall.<br /><br /> Pokud po nakonfigurování WS-AT povolíte bránu firewall, budete muset znovu spustit tento nástroj a zadejte číslo portu, který pomocí tohoto parametru. Pokud zakážete po dokončení konfigurace brány firewall, WS-AT i nadále fungovat bez další vstupy.|  
|-časový limit:\<sekundu >|Určuje výchozí časový limit v sekundách. Platné hodnoty jsou 1 až 3600.|  
|-traceActivity:\<povolit&#124;zakázat >|Povoluje nebo zakazuje trasování událostí činností.|  
|-traceLevel:\<vypnout&#124;chyba&#124;kritické&#124;upozornění&#124;informace&#124; podrobné&#124;všechny >}|Určuje úroveň trasování.|  
|-tracePII:\<povolit&#124;zakázat >|Povoluje nebo zakazuje trasování identifikovatelné osobní údaje.|  
|-traceProp:\<povolit&#124;zakázat >|Povoluje nebo zakazuje trasování událostí šíření.|  
|– restartování|Restartuje službu MSDTC, okamžitě aktivovat změny. Pokud není tento parametr zadán, pak změny budou účinné, při restartování služby MSDTC.|  
|– zobrazení|Zobrazí aktuální nastavení protokolu WS-AtomicTransaction.|  
|-virtualServer:\<virtualServer >|Určuje název clusteru prostředků DTC.|  
  
## <a name="see-also"></a>Viz také  
 [Používání protokolu WS-AtomicTransaction](../../../docs/framework/wcf/feature-details/using-ws-atomictransaction.md)  
 [Konfigurace podpory protokolu WS-AtomicTransaction](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)
