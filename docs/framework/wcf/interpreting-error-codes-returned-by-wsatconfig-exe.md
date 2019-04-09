---
title: Interpretace kódů chyb vrácených nástrojem wsatConfig.exe
ms.date: 03/30/2017
ms.assetid: ab65f22b-0d69-4c21-9aaf-74acef0ca102
ms.openlocfilehash: 47db39f2b350c2fa8c655a041ec0239e5d297644
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59151629"
---
# <a name="interpreting-error-codes-returned-by-wsatconfigexe"></a>Interpretace kódů chyb vrácených nástrojem wsatConfig.exe
Toto téma obsahuje seznam všech kódů chyb generovaných WS-AtomicTransaction Configuration Utility (wsatConfig.exe) a doporučené akce, jež mají být provedeny.  
  
## <a name="list-of-error-codes"></a>Seznam kódů chyb  
  
|Kód chyby|Popis|Provést doporučenou akci|  
|----------------|-----------------|------------------------------------|  
|0|Operace byla úspěšná|Žádné|  
|1|Došlo k neočekávané chybě|Kontaktujte Microsoft|  
|2|Při pokusu o kontaktování služby MSDTC k načtení nastavení zabezpečení došlo k neočekávané chybě.|Ujistěte se, že není zakázaná služba MSDTC a vyřešit všechny problémy uvedené ve vrácené výjimce.|  
|3|Účet, pod kterým byl spuštěn WsatConfig.exe nemá dostatečná oprávnění ke čtení nastavení zabezpečení sítě.|Spusťte WsatConfig.exe uživatelského účtu správce.|  
|4|Povolte "Přístup k síti služby DTC" nástroje MSDTC před pokusem o povolení podpory WS-AT.|Povolit "Přístup k síti služby DTC" nástroje MSDTC a znovu spusťte nástroj.|  
|5|Zadaný port je mimo rozsah. Hodnota musí být v rozsahu 1 až 65535.|Opravte `-port:<portNum>`<br /><br /> Možnosti příkazového řádku, jak je uvedeno v chybové zprávě.|  
|6|Certifikát neplatný koncový bod byl zadán v příkazovém řádku.  Certifikát se nenašel nebo ho neuspěl při ověření.|Opravte `-endpointCert` možnost příkazového řádku. Ujistěte se, že certifikát nemá privátní klíč, je určena pro použití pro Ověřeníklienta a ServerAuthentication, je nainstalován v úložišti certifikátů LocalMachine\MY a je plně důvěryhodné.|  
|7|Certifikát neplatný účty byl zadán v příkazovém řádku.|Opravte `-accountsCerts` možnost příkazového řádku. Zadaný certifikát byl buď nesprávně zadán nebo se nenašel.|  
|8|Výchozí hodnota časového limitu byl zadán mimo rozsah 1-3600 sekund.|Zadejte správnou výchozí hodnotu časového limitu, jak je uvedeno.|  
|10|Při pokusu o přístup k registru došlo k neočekávané chybě.|Zkontrolujte chybovou zprávu a kód chyby pro užitečné položky|  
|11|Nelze zapisovat do registru.|Ujistěte se, že je schopný zajistit podporu přístup k registru z účtu, který WsatConfig.exe byl spuštěn pod klíč uvedený v chybové zprávě.|  
|12|Při pokusu o přístup k úložišti certifikátů došlo k neočekávané chybě.|Použijte kód chyby vrácený pro mapování na příslušné systémové chybě.|  
|13|Nepovedlo se nakonfigurovat ovladač http.sys. Nejde vytvořit nové vyhrazení portu HTTPS pro příkaz MSDTC.|Použijte kód chyby vrácený pro mapování na příslušné systémové chybě.|  
|14|Nepovedlo se nakonfigurovat ovladač http.sys. Nelze odebrat předchozí vyhrazení portu HTTPS pro příkaz MSDTC.|Použijte kód chyby vrácený pro mapování na příslušné systémové chybě.|  
|15|Nepovedlo se nakonfigurovat ovladač http.sys. Protokol HTTPS port existuje předchozí vyhrazení již pro zadaný port.|Jiná aplikace je již zabraný vlastnictví specifického portu. Změnit na jiný port nebo odinstalovat nebo změnit konfiguraci aktuální aplikace.|  
|16|Nepovedlo se nakonfigurovat ovladač http.sys. Nelze vytvořit vazbu zadaný certifikát na port.|Použijte k mapování na příslušné systémová chyba chybový kód vrácený v chybové zprávě|  
|17|Nepovedlo se nakonfigurovat ovladač http.sys. Nelze zrušit vazbu certifikátu SSL z předchozí portu.|Použijte kód chyby vrácený v chybové zprávě k mapování na příslušné systémové chybě. V případě potřeby použijte k odebrání rezervace chybné port httpcfg.exe nebo netsh.exe.|  
|18|Nepovedlo se nakonfigurovat ovladač http.sys. Nelze vytvořit vazbu zadaný certifikát na port, protože předchozí SSL vazby již existuje.|Jiná aplikace je již zabraný vlastnictví specifického portu. Změnit na jiný port nebo odinstalovat nebo změnit konfiguraci aktuální aplikace.|  
|19|Restartování služby MSDTC se nezdařilo|Manuálně restartujte služby MSDTC v případě potřeby. Pokud se problém nevyřeší, obraťte se na Microsoft.|  
|20|[!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] není nainstalována na vzdáleném počítači, nebo není správně nainstalován.|Nainstalujte [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] na počítači.|  
|21|Vzdálená konfigurace se nezdařila z důvodu operace vypršení časového limitu.|Volání konfigurace WS-AT ve vzdáleném počítači, by měla trvat déle než 90 sekund.|  
|22|[!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] není nainstalována na vzdáleném počítači, nebo není správně nainstalován.|Nainstalujte [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] na počítači.|  
|23|Vzdálená konfigurace se nezdařila z důvodu výjimky na vzdáleném počítači.|Najdete v chybové zprávě užitečných položek|  
|26|WsatConfig.exe byl předán neplatný argument.|Zkontrolujte příkazový řádek pro chyby.|  
|27|`-accounts` Možnost příkazového řádku byl neplatný.|Opravte-`accounts` možnost příkazového řádku správně zadaný uživatelský účet.|  
|28|`-network` Možnost příkazového řádku byl neplatný.|Opravte `-network` možnost příkazového řádku správně zadaný "zapnout" nebo "Zakázat".|  
|29|`-maxTimeout` Možnost příkazového řádku byl neplatný.|Opravte `-maxTimeout` možnost příkazového řádku, jak je uvedeno.|  
|30|`-timeout` Možnost příkazového řádku byl neplatný.|Opravte `-timeout` možnost příkazového řádku, jak je uvedeno.|  
|31|`-traceLevel` Možnost příkazového řádku byl neplatný.|Opravte `-traceLevel` možnost příkazového řádku zadejte platnou hodnotu z těchto hodnot,<br /><br /> -Vypnuto<br />– Chyba<br />– Kritické<br />-Upozornění<br />– Informace<br />-Verbose<br />-Všechny|  
|32|`-traceActivity` Možnost příkazového řádku byl neplatný.|Opravte `-traceActivity` možnost příkazového řádku zadáním "zapnout" nebo "Zakázat".|  
|33|`-traceProp` Možnost příkazového řádku byl neplatný.|Opravte `-traceProp` možnost příkazového řádku zadáním "zapnout" nebo "Zakázat".|  
|34|`-tracePII` Možnost příkazového řádku byl neplatný.|Opravte `-tracePII` možnost příkazového řádku zadáním "zapnout" nebo "Zakázat".|  
|37|WsatConfig.exe nebyl schopen určit certifikát počítače přesná. To může dojít, pokud existuje více než jeden Release candidate, nebo pokud žádný neexistuje.|Zadejte kryptografický otisk certifikátu nebo dvojici Issuer\SubjectName pro zajištění správné identifikace přesné certifikát pro konfiguraci.|  
|38|Proces nebo uživatel nemá dostatečná oprávnění ke změně konfigurace brány firewall.|Spusťte WsatConfig.exe uživatelského účtu správce.|  
|39|WsatConfig.exe došlo k chybě při aktualizaci konfigurace brány firewall.|Najdete v chybové zprávě užitečných položek.|  
|40|WsatConfig.exe není schopen poskytnout oprávnění ke čtení služby MSDTC k souboru privátního klíče certifikátu|Spusťte WsatConfig.exe uživatelského účtu správce.|  
|41|Buď žádné instalace [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] nenašlo nebo nalezená verze neodpovídá, co nástroj je schopen konfigurace.|Zajištění [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] je správně nainstalován a pouze použití nástrojem WsatConfig.exe dodané s touto verzí [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] WS-AT konfigurace.|  
|42|Argument byl zadán více než jednou v příkazovém řádku.|Pouze jednou Zadejte každý argument při provádění WsatConfig.exe.|  
|43|WsatConfig.exe nelze aktualizovat nastavení WS-AT, pokud WS-AT není povolené.|Zadejte `-network:enable` jako argument další příkazového řádku.|  
|44|Chybí požadovaná oprava hotfix a nedá se konfigurovat WS-AT, dokud nebude nainstalována oprava hotfix.|Zobrazit [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] poznámky k verzi pro pokyny k instalaci požadované opravy hotfix.|  
|45|`-virtualServer` Možnost příkazového řádku byl neplatný.|Opravte `-virtualServer` možnost příkazového řádku tak, že zadáte název sítě prostředku clusteru, ve kterém chcete konfigurovat.|  
|46|Při pokusu o spuštění relace trasování událostí pro Windows trasování došlo k neočekávané chybě.|Použijte kód chyby vrácený pro mapování na příslušné systémové chybě.|  
|47|Proces nebo uživatel nemá dostatečná oprávnění k povolení relaci sledování ETW.|Spusťte WsatConfig.exe uživatelského účtu správce.|  
|48|Při pokusu o spuštění relace trasování událostí pro Windows trasování došlo k neočekávané chybě.|Získáte od Microsoftu.|  
|49|Nelze vytvořit nový soubor protokolu, protože není dost místa pro % systemdrive % musí být %|Zajistěte, aby vaše % systemdrive % musí být dostatek místa pro soubor protokolu.|  
|51|Při pokusu o spuštění relace trasování událostí pro Windows trasování došlo k neočekávané chybě.|Získáte od Microsoftu.|  
|52|Při pokusu o spuštění relace trasování událostí pro Windows trasování došlo k neočekávané chybě.|Získáte od Microsoftu.|  
|53|Zálohování souboru protokolu předchozí relace trasování událostí pro Windows neúspěšné.|Zajistěte, aby vaše % systemdrive % musí být dostatek místa pro soubor protokolu a zálohu předchozí soubor protokolu (pokud existuje). Ručně odeberte předchozí soubor protokolu v případě potřeby.|  
|55|Při pokusu o spuštění relace trasování událostí pro Windows trasování došlo k neočekávané chybě.|Získáte od Microsoftu.|  
|56|Při pokusu o spuštění relace trasování událostí pro Windows trasování došlo k neočekávané chybě.|Získáte od Microsoftu.|  
  
## <a name="see-also"></a>Viz také:

- [Nástroj WS-AtomicTransaction Configuration Utility (wsatConfig.exe)](../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)
