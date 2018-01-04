---
title: "Nástroj WS-AtomicTransaction Configuration Utility (wsatConfig.exe)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c56cf98-3963-46d5-a4e1-482deae58c58
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: adb44bfee98d01594c9babcf19e19fbf11ba3878
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ws-atomictransaction-configuration-utility-wsatconfigexe"></a>Nástroj WS-AtomicTransaction Configuration Utility (wsatConfig.exe)
Nástroj WS-AtomicTransaction Configuration Utility slouží ke konfiguraci základní nastavení podpory protokolu WS-AtomicTransaction.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
wsatConfig [Options]  
```  
  
## <a name="remarks"></a>Poznámky  
 Tento nástroj příkazového řádku můžete použít ke konfiguraci základní WS-AT nastavení v místním počítači. Pokud budete muset nakonfigurovat nastavení na místních i vzdálených počítačích, se musí použít modul snap-in konzoly MMC jak je popsáno v [konfigurace podpory WS-Atomic Transactions](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md).  
  
 Nástroje příkazového řádku najdete v umístění instalace sady Windows SDK, konkrétně  
  
 Foundation\wsatConfig.exe %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows komunikace  
  
 Pokud používáte [!INCLUDE[wxp](../../../includes/wxp-md.md)] nebo [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], je nutné stáhnout aktualizace před spuštěním WsatConfig.exe. Další informace o této aktualizaci najdete v tématu [aktualizace pro Commerce Server 2007 (KB912817)](http://go.microsoft.com/fwlink/?LinkId=95340) a [dostupnosti systému Windows XP modelu COM + opravu Hotfix kumulativní balíček 13](http://go.microsoft.com/fwlink/?LinkId=95341).  
  
 V následující tabulce jsou uvedeny možnosti, které lze použít s WS-AtomicTransaction Configuration Utility (wsatConfig.exe).  
  
> [!NOTE]
>  Když nastavíte certifikát protokolu SSL pro vybraný port, můžete přepsat původní certifikát SSL přidružený tento port, pokud existuje.  
  
|Možnosti|Popis|  
|-------------|-----------------|  
|-účty:\<účet >|Určuje textový soubor s oddělovači seznam účtů, které se můžou zapojit v WS-AtomicTransaction. Platnost tyto účty není zaškrtnuto.|  
|-accountsCerts:\<jezdec > &#124; " Issuer\SubjectName">|Určuje textový soubor s oddělovači seznam certifikátů, které se můžou zapojit v WS-AtomicTransaction. Certifikáty jsou vypsány kryptografický otisk nebo pár Issuer\SubjectName. Použijte {prázdný} pro název subjektu, pokud je prázdná.|  
|-endpointCert: < počítač &#124; \<jezdec > &#124; " Issuer\SubjectName">|Používá certifikát počítače nebo jiné místní koncový bod certifikát určený kryptografickým otiskem nebo Issuer\SubjectName pár. {PRÁZDNÝ} používá pro název subjektu, pokud je prázdná.|  
|-maxTimeout:\<sekundu >|Určuje maximální časový limit v sekundách. Platné hodnoty jsou 0 až 3600.|  
|-sítě:\<povolit za &#124; zakázat >|Povolí nebo zakáže podporu WS-AtomicTransaction sítě.|  
|-port:\<portNum >|Nastaví HTTPS port pro WS-AtomicTransaction.<br /><br /> Pokud před spuštěním tohoto nástroje je již povolena brána firewall, port se automaticky registruje v seznamu výjimek. Pokud je brána firewall neaktivní před spuštěním tohoto nástroje, žádné další je nakonfigurovaná týkající se brány firewall.<br /><br /> Pokud povolíte bránu firewall po dokončení konfigurace služby WS-AT, budete muset znovu spustit tento nástroj a zadejte číslo portu pomocí tohoto parametru. Pokud zakážete po dokončení konfigurace brány firewall, WS-AT i nadále fungovat bez další vstup.|  
|-časový limit:\<sekundu >|Určuje výchozí časový limit v sekundách. Platné hodnoty jsou 1 až 3600.|  
|-traceActivity:\<povolit za &#124; zakázat >|Povolí nebo zakáže trasování událostí aktivity.|  
|-traceLevel:\<vypnout &#124; Chyba &#124; Kritické &#124; Upozornění &#124; informace o &#124; Podrobné &#124; Všechny >}|Určuje úroveň trasování.|  
|-tracePII:\<povolit za &#124; zakázat >|Povolí nebo zakáže trasování identifikovatelné osobní údaje.|  
|-traceProp:\<povolit za &#124; zakázat >|Povolí nebo zakáže trasování událostí šíření.|  
|– restartování|Restartování služby MSDTC aktivovat změny okamžitě. Pokud není zadáno, změny se projeví po restartování služby MS DTC.|  
|-Zobrazit|Zobrazí aktuální nastavení protokolu WS-AtomicTransaction.|  
|-virtuální_server:\<virtuální_server >|Určuje název prostředku clusteru DTC.|  
  
## <a name="see-also"></a>Viz také  
 [Používání protokolu WS-AtomicTransaction](../../../docs/framework/wcf/feature-details/using-ws-atomictransaction.md)  
 [Konfigurace podpory protokolu WS-AtomicTransaction](../../../docs/framework/wcf/feature-details/configuring-ws-atomic-transaction-support.md)
