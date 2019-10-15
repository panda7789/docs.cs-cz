---
title: Nástroj WS-AtomicTransaction Configuration Utility (wsatConfig.exe)
ms.date: 03/30/2017
ms.assetid: 1c56cf98-3963-46d5-a4e1-482deae58c58
ms.openlocfilehash: 5333c9c5caad502ce925fe4a45a039c553812ba6
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320203"
---
# <a name="ws-atomictransaction-configuration-utility-wsatconfigexe"></a>Nástroj WS-AtomicTransaction Configuration Utility (wsatConfig.exe)
Konfigurační nástroj WS-AtomicTransaction se používá ke konfiguraci základních nastavení podpory WS-AtomicTransaction.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
wsatConfig [Options]  
```  
  
## <a name="remarks"></a>Poznámky  
 Tento nástroj příkazového řádku lze použít ke konfiguraci základního nastavení WS-AT pouze v místním počítači. Pokud je nutné nakonfigurovat nastavení na místním i vzdáleném počítači, měli byste použít modul snap-in konzoly MMC, jak je popsáno v tématu [Konfigurace podpory transakcí WS-Atomic](./feature-details/configuring-ws-atomic-transaction-support.md).  
  
 Nástroj příkazového řádku najdete v umístění instalace Windows SDK, konkrétně  
  
 %SystemRoot%\Microsoft.Net\Framework\v3.0\Windows komunikace Foundation\wsatConfig.exe  
  
 Pokud používáte [!INCLUDE[wxp](../../../includes/wxp-md.md)] nebo [!INCLUDE[ws2003](../../../includes/ws2003-md.md)], je nutné před spuštěním WsatConfig. exe stáhnout aktualizaci. Další informace o této aktualizaci najdete v článku [aktualizace pro Commerce Server 2007 (KB912817)](https://go.microsoft.com/fwlink/?LinkId=95340) a [dostupnost kumulativního balíčku Windows XP com+ opravy hotfix](https://go.microsoft.com/fwlink/?LinkId=95341).  
  
 V následující tabulce jsou uvedeny možnosti, které lze použít s konfiguračním nástrojem WS-AtomicTransaction (wsatConfig. exe).  
  
> [!NOTE]
> Když nastavíte certifikát SSL pro vybraný port, přepíšete původní certifikát SSL přidružený k tomuto portu, pokud existuje.  
  
|Možnosti|Popis|  
|-------------|-----------------|  
|-Accounts: \<account, >|Určuje čárkami oddělený seznam účtů, které se mohou účastnit protokolu WS-AtomicTransaction. Platnost těchto účtů není zaškrtnuta.|  
|-accountsCerts: \<thumb >&#124;"Issuer\SubjectName", >|Určuje čárkami oddělený seznam certifikátů, které se mohou účastnit protokolu WS-AtomicTransaction. Certifikáty jsou označeny kryptografickým otiskem nebo dvojicí Issuer\SubjectName. Pokud je název předmětu prázdný, použijte {EMPTY}.|  
|-endpointCert: < Machine&#124;\<thumb >&#124;"Issuer\SubjectName" >|Používá certifikát počítače nebo jiný certifikát místního koncového bodu určený dvojicí kryptografický otisk nebo Issuer\SubjectName. Pokud je název subjektu prázdný, používá se {EMPTY}.|  
|-maxTimeout: \<sec >|Určuje maximální časový limit v sekundách. Platné hodnoty jsou od 0 do 3600.|  
|-Network: \<enable&#124;zakázat >|Povoluje nebo zakazuje podporu sítě WS-AtomicTransaction.|  
|-Port: \<portNum >|Nastaví port HTTPS pro WS-AtomicTransaction.<br /><br /> Pokud jste už před spuštěním tohoto nástroje povolili bránu firewall, port se automaticky zaregistruje v seznamu výjimek. Pokud před spuštěním tohoto nástroje není brána firewall vypnutá, není pro bránu firewall nakonfigurované žádné další.<br /><br /> Pokud povolíte bránu firewall po konfiguraci WS-AT, budete muset znovu spustit tento nástroj a zadejte číslo portu pomocí tohoto parametru. Pokud bránu firewall po konfiguraci zakážete, bude WS-AT nadále fungovat bez dalšího vstupu.|  
|-Timeout: \<sec >|Určuje výchozí časový limit v sekundách. Platné hodnoty jsou od 1 do 3600.|  
|-traceActivity: \<enable&#124;zakázat >|Povoluje nebo zakazuje trasování událostí aktivity.|  
|-traceLevel: @no__t-nepostradatelné&#124;informace&#124;o&#124; upozorněních&#124;chyby&#124;&#124;0Off vše >}|Určuje úroveň trasování.|  
|-tracePII: \<enable&#124;zakázat >|Povoluje nebo zakazuje trasování informací, které mohou vést k identifikaci osob.|  
|-traceProp: \<enable&#124;zakázat >|Povoluje nebo zakazuje trasování událostí šíření.|  
|-restart|Restartuje MSDTC, aby se změny aktivovaly hned. Pokud tento parametr nezadáte, změny se projeví při restartování služby MSDTC.|  
|-Zobrazit|Zobrazuje aktuální nastavení protokolu WS-AtomicTransaction.|  
|-virtualServer: \<virtualServer >|Určuje název clusteru prostředků DTC.|  
  
## <a name="see-also"></a>Viz také:

- [Používání protokolu WS-AtomicTransaction](./feature-details/using-ws-atomictransaction.md)
- [Konfigurace podpory protokolu WS-AtomicTransaction](./feature-details/configuring-ws-atomic-transaction-support.md)
