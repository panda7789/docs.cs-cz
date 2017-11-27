---
title: "Interpretace kódů chyb vrácených nástrojem wsatConfig.exe"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ab65f22b-0d69-4c21-9aaf-74acef0ca102
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d8bd70d22b7088a936d3243f050a4ee077d0f5c3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="interpreting-error-codes-returned-by-wsatconfigexe"></a>Interpretace kódů chyb vrácených nástrojem wsatConfig.exe
Toto téma uvádí všechny kódy chyb generovaných nástroj WS-AtomicTransaction Configuration Utility (wsatConfig.exe) a doporučené akce, které se provedou.  
  
## <a name="list-of-error-codes"></a>Seznam kódů chyb  
  
|Kód chyby|Popis|Provést doporučenou akci|  
|----------------|-----------------|------------------------------------|  
|0|Operace byla úspěšná|Žádné|  
|1|Došlo k neočekávané chybě|Kontaktujte Microsoft|  
|2|Při pokusu o kontaktování služby MSDTC k načtení nastavení zabezpečení došlo k neočekávané chybě.|Zkontrolujte, zda služba koordinátoru MS DTC není vypnuta a vyřešte všechny problémy uvedené v vrácený výjimka.|  
|3|Účet, který spustil WsatConfig.exe neměl dostatečná oprávnění ke čtení nastavení zabezpečení sítě.|Spusťte WsatConfig.exe v rámci uživatelského účtu správce.|  
|4|Povolení "Síťového přístupu" pro služby MSDTC, než se pokusíte povolit podporu protokolu WS-AT.|Povolit "Síťového přístupu" pro služby MS DTC a znovu spusťte nástroj.|  
|5|Zadaný port je mimo rozsah. Hodnota musí být v rozsahu od 1 do 65 535.|Opravte`-port:<portNum>`<br /><br /> Možnosti příkazového řádku, které je uvedené v chybové zprávě.|  
|6|Na příkazovém řádku byla zadán certifikát neplatný koncový bod.  Certifikát nebyl nalezen nebo jej neuspěla v ověřování.|Opravte `-endpointCert` možnost příkazového řádku. Zajistěte, aby certifikát nemá privátní klíč, je určena k použití pro Ověřeníklienta i ServerAuthentication, je nainstalován v úložišti certifikátů LocalMachine\MY a je plně důvěryhodný.|  
|7|Certifikát neplatný účty byla zadána na příkazovém řádku.|Opravte `-accountsCerts` možnost příkazového řádku. Zadaný certifikát byl buď nesprávně zadán nebo nebylo možné najít.|  
|8|Výchozí hodnota časového limitu byla zadána mimo rozsah 1 do 3600 sekund.|Zadejte správný výchozí hodnotu časového limitu, které je uvedené.|  
|10|Při pokusu o přístup k registru došlo k neočekávané chybě.|Zkontrolujte chybovou zprávu a kód chyby pro nežádoucí položky|  
|11|Nelze zapsat do registru.|Zajistěte, aby byl klíč uvedený v chybové zprávě podporovat registru přístup z účtu, který WsatConfig.exe byl proveden v části.|  
|12|Při pokusu o přístup k úložišti certifikátů došlo k neočekávané chybě.|Použijte k mapování na příslušné systémová chyba vrátila kód chyby.|  
|13|Konfigurace ovladače http.sys se nezdařila. Nelze vytvořit novou rezervaci port HTTPS pro služby MS DTC.|Použijte k mapování na příslušné systémová chyba vrátila kód chyby.|  
|14|Konfigurace ovladače http.sys se nezdařila. Nelze odebrat předchozí vyhrazení portu HTTPS pro služby MS DTC.|Použijte k mapování na příslušné systémová chyba vrátila kód chyby.|  
|15|Konfigurace ovladače http.sys se nezdařila. Předchozí protokol HTTPS port rezervace již existuje pro zadaný port.|Jiná aplikace již převzetí vlastnictví těchto na konkrétní port. Změnit na jiný port nebo odinstalovat nebo změnit konfiguraci aktuální aplikace.|  
|16|Konfigurace ovladače http.sys se nezdařila. Nelze vytvořit vazbu zadaný certifikát na port.|Použijte k mapování na příslušné systémová chyba v chybové zprávě vrácený kód chyby:|  
|17|Konfigurace ovladače http.sys se nezdařila. Nelze zrušit vazbu certifikátu SSL od předchozí portu.|Kód chyby vrácený v chybové zprávě použijte k mapování na příslušné systémové chybě. V případě potřeby pomocí httpcfg.exe nebo netsh.exe rezervace chybné portu.|  
|18|Konfigurace ovladače http.sys se nezdařila. Nelze vytvořit vazbu zadaný certifikát na port, protože předchozí protokolu SSL vazby již existuje.|Jiná aplikace již převzetí vlastnictví těchto na konkrétní port. Změnit na jiný port nebo odinstalovat nebo změnit konfiguraci aktuální aplikace.|  
|19|Restartování služby MS DTC se nezdařilo|V případě potřeby ručně restartujte služby MS DTC. Pokud potíže potrvají, obraťte se na Microsoft.|  
|20|[!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)]není nainstalován na vzdáleném počítači, nebo není správně nainstalován.|Nainstalujte [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] na počítači.|  
|21|Vzdálená konfigurace se nezdařila z důvodu vypršení časového limitu pro operaci.|Konfigurace služby WS-AT ve vzdáleném počítači volání by měl trvat déle než 90 sekund.|  
|22|[!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)]není nainstalován na vzdáleném počítači, nebo není správně nainstalován.|Nainstalujte [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] na počítači.|  
|23|Vzdálená konfigurace se nezdařilo kvůli výjimce ve vzdáleném počítači.|Zkontrolujte chybové zprávy pro nežádoucí položky|  
|26|WsatConfig.exe byl předán neplatný argument.|Zkontrolujte chyby příkazového řádku.|  
|27|`-accounts` Možnost příkazového řádku byl neplatný.|Opravte-`accounts` možnost příkazového řádku správně zadat uživatelský účet.|  
|28|`-network` Možnost příkazového řádku byl neplatný.|Opravte `-network` možnost příkazového řádku správně zadat "Povolit" nebo "Zakázat".|  
|29|`-maxTimeout` Možnost příkazového řádku byl neplatný.|Opravte `-maxTimeout` možnost příkazového řádku, které je uvedené.|  
|30|`-timeout` Možnost příkazového řádku byl neplatný.|Opravte `-timeout` možnost příkazového řádku, které je uvedené.|  
|31|`-traceLevel` Možnost příkazového řádku byl neplatný.|Opravte `-traceLevel` možnost příkazového řádku zadejte platnou hodnotu z těchto hodnot,<br /><br /> -Vypnuto<br />– Chyba<br />-Kritické<br />-Upozornění<br />– Informace<br />-Verbose<br />– Všechny|  
|32|`-traceActivity` Možnost příkazového řádku byl neplatný.|Opravte `-traceActivity` možnost příkazového řádku zadáním "Povolit" nebo "Zakázat".|  
|33|`-traceProp` Možnost příkazového řádku byl neplatný.|Opravte `-traceProp` možnost příkazového řádku zadáním "Povolit" nebo "Zakázat".|  
|34|`-tracePII` Možnost příkazového řádku byl neplatný.|Opravte `-tracePII` možnost příkazového řádku zadáním "Povolit" nebo "Zakázat".|  
|37|WsatConfig.exe se nepodařilo určit certifikát přesný počítače. Tomu může dojít, když je více než jeden candidate, nebo když žádné neexistují.|Zadejte kryptografický otisk certifikátu nebo pár Issuer\SubjectName správně určit přesnou certifikát, který chcete konfigurovat.|  
|38|Proces nebo uživatel nemá dostatečná oprávnění ke změně konfigurace brány firewall.|Spusťte WsatConfig.exe v rámci uživatelského účtu správce.|  
|39|WsatConfig.exe došlo k chybě při aktualizaci konfigurace brány firewall.|Zkontrolujte chybové zprávy pro nežádoucí položky.|  
|40|WsatConfig.exe není schopen poskytnout přístup pro čtení služby MSDTC k soubor privátního klíče certifikátu|Spusťte WsatConfig.exe v rámci uživatelského účtu správce.|  
|41|Buď bez instalace [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] může být nalezen, nebo verze nalezen neodpovídá, co nástroj je schopen konfigurace.|Ujistěte se, [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] je správně nainstalovaná a pouze použijte nástroj WsatConfig.exe, které byly dodány s tuto verzi [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] konfigurace služby WS-AT.|  
|42|Argument byla zadána více než jednou na příkazovém řádku.|Pouze jednou zadejte všechny argumenty při provádění WsatConfig.exe.|  
|43|WsatConfig.exe nelze aktualizovat nastavení služby WS-AT, pokud není povolena WS-AT.|Zadejte `-network:enable` jako argument další příkazového řádku.|  
|44|Chybí požadovaná oprava hotfix a WS-AT nelze nakonfigurovat, dokud nebude nainstalována oprava hotfix.|Najdete v článku [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] poznámky k verzi pro pokyny k instalaci požadované opravy hotfix.|  
|45|`-virtualServer` Možnost příkazového řádku byl neplatný.|Opravte `-virtualServer` možnost příkazového řádku zadáním síťový název prostředku clusteru, ve které chcete nakonfigurovat.|  
|46|Došlo k neočekávané chybě při pokusu o spuštění relace trasování ETW|Použijte k mapování na příslušné systémová chyba vrátila kód chyby.|  
|47|Proces nebo uživatel nemá dostatečná oprávnění k povolení relaci trasování ETW.|Spusťte WsatConfig.exe v rámci uživatelského účtu správce.|  
|48|Při pokusu o spuštění relace trasování ETW došlo k neočekávané chybě.|Od společnosti Microsoft.|  
|49|Nelze vytvořit nový soubor protokolu z důvodu nedostatku místa pro svazek % systemdrive %|Zajistěte, aby vaše % systemdrive % dostatkem místa pro soubor protokolu.|  
|51|Při pokusu o spuštění relace trasování ETW došlo k neočekávané chybě.|Od společnosti Microsoft.|  
|52|Při pokusu o spuštění relace trasování ETW došlo k neočekávané chybě.|Od společnosti Microsoft.|  
|53|Zálohování souboru protokolu trasování událostí pro Windows bude předchozí relace nebyla úspěšná.|Zajistěte, aby vaše % systemdrive % dostatkem místa pro soubor protokolu a zálohování předchozího souboru protokolu (pokud existuje). Ručně odeberte předchozí soubor protokolu v případě potřeby.|  
|55|Při pokusu o spuštění relace trasování ETW došlo k neočekávané chybě.|Od společnosti Microsoft.|  
|56|Při pokusu o spuštění relace trasování ETW došlo k neočekávané chybě.|Od společnosti Microsoft.|  
  
## <a name="see-also"></a>Viz také  
 [WS-AtomicTransaction Configuration Utility (wsatConfig.exe)](../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)
