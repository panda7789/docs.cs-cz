---
title: Interpretace kódů chyb vrácených nástrojem wsatConfig.exe
ms.date: 03/30/2017
ms.assetid: ab65f22b-0d69-4c21-9aaf-74acef0ca102
ms.openlocfilehash: 0a65bea68f595e5e28c05a142ecdd9589f12bed5
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72321039"
---
# <a name="interpreting-error-codes-returned-by-wsatconfigexe"></a>Interpretace kódů chyb vrácených nástrojem wsatConfig.exe
Toto téma obsahuje seznam všech chybových kódů generovaných konfiguračním nástrojem WS-AtomicTransaction (wsatConfig. exe) a doporučené akce, které je třeba provést.  
  
## <a name="list-of-error-codes"></a>Seznam kódů chyb  
  
|Kód chyby|Popis|Doporučená akce, která má být provedena|  
|----------------|-----------------|------------------------------------|  
|0,8|Operace byla úspěšná.|Žádné|  
|první|Neočekávaná chyba|Kontaktujte Microsoft|  
|odst|Došlo k neočekávané chybě při pokusu o kontaktování služby MSDTC, aby bylo možné načíst nastavení zabezpečení.|Zajistěte, aby Služba MSDTC nebyla zakázaná, a vyřešte všechny problémy uvedené v vrácené výjimce.|  
|3|Účet, pod kterým běžel WsatConfig. exe, nemá dostatečná oprávnění ke čtení nastavení zabezpečení sítě.|Spusťte WsatConfig. exe v uživatelském účtu správce.|  
|4|Před pokusem povolit podporu WS-AT povolte službu MSDTC "přístup k síti DTC".|Povolte položku "přístup k síti DTC" pro službu MSDTC a spusťte nástroj znovu.|  
|5|Zadaný port je mimo rozsah. Hodnota musí být v rozsahu od 1 do 65535.|Opravte `-port:<portNum>`.<br /><br /> možnost příkazového řádku, jak je uvedeno v chybové zprávě.|  
|6|V příkazovém řádku byl zadán neplatný certifikát koncového bodu.  Certifikát se nepovedlo najít nebo neuspěl při ověřování.|Opravte možnost příkazového řádku `-endpointCert`. Ujistěte se, že certifikát má privátní klíč, který je určen pro použití pro Ověřeníklienta i ServerAuthentication, je nainstalován v úložišti certifikátů úložišti LocalMachine\MY a je plně důvěryhodný.|  
|čl|Na příkazovém řádku byl zadán neplatný certifikát účtů.|Opravte možnost příkazového řádku `-accountsCerts`. Zadaný certifikát byl buď nesprávně zadán, nebo nebyl nalezen.|  
|8|Byl zadán výchozí časový limit mimo rozsah 1 až 3600 sekund.|Zadejte správnou výchozí hodnotu časového limitu, jak je uvedeno níže.|  
|10pruhový|Při pokusu o přístup k registru došlo k neočekávané chybě.|Podívejte se na chybovou zprávu a kód chyby pro položky, které je možné provést.|  
|odst|Do registru nejde zapisovat.|Ujistěte se, že klíč uvedený v chybové zprávě je schopný podporovat přístup k registru z účtu WsatConfig. exe, který se spustil v rámci.|  
|12,5|Při pokusu o přístup k úložišti certifikátů došlo k neočekávané chybě.|Použijte kód chyby vrácený k namapování na příslušnou systémovou chybu.|  
|13,5|Konfigurace HTTP. sys se nezdařila. Pro MSDTC nelze vytvořit novou rezervaci portu HTTPS.|Použijte kód chyby vrácený k namapování na příslušnou systémovou chybu.|  
|čtrnáct|Konfigurace HTTP. sys se nezdařila. Nejde odebrat předchozí rezervaci portu HTTPS pro MSDTC.|Použijte kód chyby vrácený k namapování na příslušnou systémovou chybu.|  
|15|Konfigurace HTTP. sys se nezdařila. Předchozí rezervace portu HTTPS již pro zadaný port existuje.|Jiná aplikace již převzala vlastnictví konkrétního portu. Přejděte na jiný port nebo odinstalujte nebo překonfigurujte aktuální aplikaci.|  
|16bitovém|Konfigurace HTTP. sys se nezdařila. Zadaný certifikát se nedá navazovat na port.|Pomocí kódu chyby vráceného v chybové zprávě namapujte na odpovídající systémové chyby.|  
|sedmnáct|Konfigurace HTTP. sys se nezdařila. Nelze zrušit vazbu certifikátu SSL z předchozího portu.|Pomocí kódu chyby vráceného v chybové zprávě namapujte na příslušnou systémovou chybu. V případě potřeby pomocí Httpcfg. exe nebo Netsh. exe odeberte chybné rezervace portů.|  
|let|Konfigurace HTTP. sys se nezdařila. Zadaný certifikát nelze svázat s portem, protože již existuje předchozí vazba SSL.|Jiná aplikace již převzala vlastnictví konkrétního portu. Přejděte na jiný port nebo odinstalujte nebo překonfigurujte aktuální aplikaci.|  
|čl|Restart služby MSDTC se nezdařil.|V případě potřeby ručně restartujte MSDTC. Pokud potíže potrvají, obraťte se na společnost Microsoft.|  
|20o|WinFX není nainstalován na vzdáleném počítači nebo není správně nainstalován.|Nainstalujte do počítače WinFX.|  
|20|Vzdálená konfigurace se nezdařila z důvodu vypršení časového limitu operace.|Volání ke konfiguraci WS-AT na vzdáleném počítači by mělo trvat déle než 90 sekund.|  
|22|WinFX není nainstalován na vzdáleném počítači nebo není správně nainstalován.|Nainstalujte do počítače WinFX.|  
|listopadu|Vzdálená konfigurace se nezdařila z důvodu výjimky na vzdáleném počítači.|Podívejte se na chybovou zprávu pro nenapadnutelné položky.|  
|26|Do souboru WsatConfig. exe byl předán neplatný argument.|Vyhledejte chyby v příkazovém řádku.|  
|dlouhý|Možnost příkazového řádku `-accounts` byla neplatná.|Opravte možnost příkazového řádku-`accounts` pro správné zadání uživatelského účtu.|  
|28|Možnost příkazového řádku `-network` byla neplatná.|Opravte možnost příkazového řádku `-network` pro správné zadání možnosti "Enable" nebo "Disable".|  
|29|Možnost příkazového řádku `-maxTimeout` byla neplatná.|Opravte možnost příkazového řádku `-maxTimeout`, jak je uvedeno níže.|  
|30|Možnost příkazového řádku `-timeout` byla neplatná.|Opravte možnost příkazového řádku `-timeout`, jak je uvedeno níže.|  
|čl|Možnost příkazového řádku `-traceLevel` byla neplatná.|Opravte možnost příkazového řádku `-traceLevel` a zadejte platnou hodnotu z následujících možností:<br /><br /> -Vypnuto<br />– Chyba<br />– Kritické<br />– Upozornění<br />-Informace<br />– Verbose<br />– Vše|  
|32|Možnost příkazového řádku `-traceActivity` byla neplatná.|Opravte možnost příkazového řádku `-traceActivity` tak, že zadáte buď Enable, nebo Disable.|  
|33|Možnost příkazového řádku `-traceProp` byla neplatná.|Opravte možnost příkazového řádku `-traceProp` tak, že zadáte buď Enable, nebo Disable.|  
|34|Možnost příkazového řádku `-tracePII` byla neplatná.|Opravte možnost příkazového řádku `-tracePII` tak, že zadáte buď Enable, nebo Disable.|  
|37|WsatConfig. exe nedokázal určit přesný certifikát počítače. K tomu může dojít v případě, že existuje více kandidátů nebo pokud žádná neexistuje.|Zadejte kryptografický otisk certifikátu nebo dvojici Issuer\SubjectName, abyste správně identifikovali přesný certifikát, který se má nakonfigurovat.|  
|38|Proces nebo uživatel nemá dostatečná oprávnění ke změně konfigurace brány firewall.|Spusťte WsatConfig. exe v uživatelském účtu správce.|  
|39|V WsatConfig. exe došlo k chybě při aktualizaci konfigurace brány firewall.|Podívejte se na chybovou zprávu s položkami, které jsou k.|  
|40|WsatConfig. exe nemůže povolit přístup pro čtení MSDTC k souboru privátního klíče certifikátu.|Spusťte WsatConfig. exe v uživatelském účtu správce.|  
|41|Buď se nenašla žádná instalace WinFX, nebo se verze, která se našla, neshoduje s tím, co nástroj dokáže nakonfigurovat.|Ujistěte se, že je WinFX správně nainstalovaný, a použijte nástroj WsatConfig. exe, který byl dodán s touto verzí WinFX ke konfiguraci WS-AT.|  
|42|Argument byl na příkazovém řádku zadán více než jednou.|Při spuštění WsatConfig. exe zadejte pouze každý argument.|  
|43|WsatConfig. exe nemůže aktualizovat nastavení WS-AT, pokud není povolen protokol WS-AT.|Jako další argument příkazového řádku zadejte `-network:enable`.|  
|44|Požadovaná oprava hotfix chybí a služba WS-AT se nedá nakonfigurovat, dokud není nainstalovaná oprava hotfix.|Pokyny k instalaci požadované opravy hotfix najdete v poznámkách k vydání verze WinFX.|  
|45|Možnost příkazového řádku `-virtualServer` byla neplatná.|Opravte možnost příkazového řádku `-virtualServer` zadáním názvu sítě prostředku clusteru, ve kterém se má konfigurovat.|  
|46|Při pokusu o spuštění relace trasování ETW došlo k neočekávané chybě.|Použijte kód chyby vrácený k namapování na příslušnou systémovou chybu.|  
|47|Proces nebo uživatel nemá dostatečná oprávnění k povolení relace trasování ETW.|Spusťte WsatConfig. exe v uživatelském účtu správce.|  
|48|Při pokusu o spuštění relace trasování ETW došlo k neočekávané chybě.|Kontaktujte Microsoft.|  
|49|Nelze vytvořit nový soubor protokolu z důvodu nedostatku místa na disku% systemdrive%.|Ujistěte se, že vaše% systemdrive% má dostatek místa pro soubor protokolu.|  
|51|Při pokusu o spuštění relace trasování ETW došlo k neočekávané chybě.|Kontaktujte Microsoft.|  
|52|Při pokusu o spuštění relace trasování ETW došlo k neočekávané chybě.|Kontaktujte Microsoft.|  
|53|Zálohování předchozího souboru protokolu relace trasování událostí pro Windows bylo neúspěšné.|Ujistěte se, že vaše% systemdrive% má dostatek místa pro soubor protokolu a zálohu předchozího souboru protokolu (pokud existuje). V případě potřeby odeberte předchozí soubor protokolu ručně.|  
|55|Při pokusu o spuštění relace trasování ETW došlo k neočekávané chybě.|Kontaktujte Microsoft.|  
|56|Při pokusu o spuštění relace trasování ETW došlo k neočekávané chybě.|Kontaktujte Microsoft.|  
  
## <a name="see-also"></a>Viz také:

- [Nástroj pro konfiguraci WS-AtomicTransaction (wsatConfig.exe)](ws-atomictransaction-configuration-utility-wsatconfig-exe.md)
