---
title: SignTool.exe (nástroj pro podpis)
ms.date: 03/30/2017
helpviewer_keywords:
- Sign tool
- SignTool.exe
ms.assetid: 0c25ff6c-bff3-422e-b017-146a3ee86cb9
ms.openlocfilehash: 8ce31b1399700906d6d6e2a369dcfc4b61fe9646
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180328"
---
# <a name="signtoolexe-sign-tool"></a>SignTool.exe (nástroj pro podpis)
Sign Tool je nástroj příkazového řádku, který digitálně podepíše soubory, ověří podpisy v souborech a časová razítka souborů.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li nástroj spustit, použijte příkazový řádek pro vývojáře pro sadu Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7). Další informace naleznete v [příkazových koncích](developer-command-prompt-for-vs.md).  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
signtool [command] [options] [file_name | ...]  
```  
  
## <a name="parameters"></a>Parametry  
  
|Argument|Popis|  
|--------------|-----------------|  
|`command`|Jeden ze čtyř`catdb`příkazů `sign` `Timestamp`( `Verify`, , , nebo ), který určuje operaci, která má být se souborem provedena. Popis jednotlivých příkazů naleznete v následující tabulce.|  
|`options`|Volba, která upravuje příkaz. Kromě globální `/q` a `/v` možnosti, každý příkaz podporuje jedinečnou sadu možností.|  
|`file_name`|Cesta k souboru, který chcete podepsat.|  
  
 Následující příkazy jsou podporovány nástrojem Sign Tool. Každý příkaz se používá s různou sadou možností, které jsou uvedeny v příslušných oddílech.  
  
|Příkaz|Popis|  
|-------------|-----------------|  
|`catdb`|Přidá nebo odebere soubor katalogu z databáze katalogů. Databáze katalogů slouží k automatickému vyhledávání souborů katalogu a jsou označeny identifikátorem GUID. Seznam možností podporovaných příkazem `catdb` naleznete v [tématu catdb Command Options](signtool-exe.md#catdb).|  
|`sign`|Digitálně podepíše soubory. Digitální podpisy chrání soubory před neoprávněnými změnami a umožňují uživatelům ověřit podpis na základě podpisového certifikátu. Seznam možností podporovaných příkazem `sign` naleznete v [tématu Command Options sign](signtool-exe.md#sign).|  
|`Timestamp`|Opatří soubory časovým razítkem. Seznam možností podporovaných příkazem `TimeStamp` naleznete v tématu [Možnosti příkazu časového razítka](signtool-exe.md#TimeStamp).|  
|`Verify`|Ověří digitální podpis souborů stanovením, zda podpisový certifikát byl vydán důvěryhodnou autoritou, zda podpisový certifikát nebyl odvolán, a případně zda podpisový certifikát je platný pro konkrétní zásady. Seznam možností podporovaných příkazem `Verify` naleznete v tématu [Ověření možností příkazu](signtool-exe.md#Verify).|  
  
 Tyto možnosti platí pro všechny příkazy nástroje pro podepisování.  
  
|Možnost Global|Popis|  
|-------------------|-----------------|  
|**/q**|Pokud se příkaz úspěšně spustí, nezobrazí se žádný výstup. Pokud se příkaz nezdaří, zobrazí se minimální výstup.|  
|**/v**|Zobrazí podrobný výstup bez ohledu na to, zda bude příkaz úspěšně spuštěn, nebo se nezdaří, a zobrazí upozornění.|  
|**/ladění**|Zobrazí informace o ladění.|  
  
<a name="catdb"></a>
## <a name="catdb-command-options"></a>Možnosti příkazu catdb  
 V následující tabulce jsou uvedeny možnosti, které lze použít s příkazem. `catdb`  
  
|Možnost Catdb|Popis|  
|------------------|-----------------|  
|`/d`|Určuje, že výchozí databáze katalogů je aktualizována. Pokud není `/d` použita `/g` možnost ani možnost, nástroj Sign Tool aktualizuje systémovou součást a databázi ovladačů.|  
|`/g`*Identifikátor GUID*|Určuje, že databáze katalogu identifikovaná globálně jedinečným identifikátorem GUID je *aktualizována.*|  
|`/r`|Odebere zadané katalogy z databáze katalogů. Pokud není tato možnost zadána, nástroj Sign Tool přidá určené katalogy do databáze katalogů.|  
|`/u`|Určuje, že přidaným souborům katalogu bude přiřazen jedinečný název. V případě potřeby jsou soubory katalogu přejmenovány, aby se předešlo konfliktům názvů s existujícími soubory katalogu. Pokud není tato možnost zadána, přepíše nástroj Sign Tool jakýkoli existující katalog, který má stejný název jako přidávaný katalog.|  
  
<a name="sign"></a>
## <a name="sign-command-options"></a>Možnosti příkazu sign  
 V následující tabulce jsou uvedeny možnosti, které lze použít s příkazem. `sign`  
  
|Možnost příkazu sign|Popis|  
|-------------------------|-----------------|  
|`/a`|Automaticky vybere nejlepší podpisový certifikát. Nástroj Sign Tool vyhledá všechny platné certifikáty, které splňují všechny zadané podmínky, a vybere ten, který je platný pro co nejdelší dobu. Pokud tato možnost není k dispozici, očekává nástroj Sign Tool pouze jeden platný podpisový certifikát.|  
|`/ac`  *Soubor*|Přidá další certifikát ze *souboru* do bloku podpisu.|  
|`/as`|Připojí tento podpis. Pokud neexistuje žádný primární podpis, tento podpis se stane primárním podpisem.|  
|`/c`  *Název šablony cert*|Určuje název šablony certifikátu (rozšíření Microsoft) pro podpisový certifikát.|  
|`/csp`  *CSPName*|Určuje poskytovatele CSP (Cryptographic Service Provider), který obsahuje kontejner soukromého klíče.|  
|`/d`  *Desc*|Určuje popis podepsaného obsahu.|  
|`/du`  *Adresu url*|Určuje adresu URL (Uniform Resource Locator) pro rozšířený popis podepsaného obsahu.|  
|`/f`  *Soubor SignCert*|Určuje podpisový certifikát v souboru. Pokud je soubor ve formátu PFX (Výměna osobních informací) `/p` a je chráněn heslem, použijte možnost pro zadání hesla. Pokud soubor neobsahuje soukromé klíče, `/csp` `/kc` použijte možnosti a k určení názvu kontejneru CSP a soukromého klíče.|  
|`/fd`|Určuje soubor algoritmu digest pro vytváření podpisů souborů. Výchozím je SHA1.|  
|`/i`  *Issuername*|Určuje název vystavitele podpisového certifikátu. Tato hodnota může být podřetězec celého jména vystavitele.|  
|`/kc`  *Název privKeyContainerName*|Určuje název kontejneru soukromého klíče.|  
|`/n`  *Název předmětu*|Určuje název předmětu podpisového certifikátu. Tato hodnota může být podřetězec celého názvu subjektu.|  
|`/nph`|V případě podpory potlačuje hodnoty hash stránek pro spustitelné soubory. Výchozí hodnota je určena proměnnou prostředí SIGNTOOL_PAGE_HASHES a verzí wintrust.dll. Tato možnost je ignorována pro soubory, které nejsou typu PE.|  
|`/p`  *Heslo*|Určuje heslo, které má být použito při otevírání souboru PFX. (Použijte `/f` možnost k zadání souboru PFX.)|  
|`/p7`*Cesta*|Určuje, že soubor PKCS (Public Key Cryptography Standards) #7 je vytvořen pro každý zadaný soubor obsahu. Soubory #7 PKCS mají *název*\\*souboru*s názvem cesta .p7.|  
|`/p7ce`*Hodnota*|Určuje volby pro podepsaný obsah PKCS #7. Nastavte *hodnotu* na vložený pro vložení podepsaného obsahu do souboru #7 PKCS nebo na "DetachedSignedData" k vytvoření podepsané datové části odpojeného souboru #7 PKCS. Pokud `/p7ce` tato možnost není použita, je podepsaný obsah ve výchozím nastavení vložen.|  
|`/p7co`* \<OID>*|Určuje identifikátor objektu (OID), který identifikuje podepsaný obsah PKCS #7.|  
|`/ph`|V případě podpory generuje hodnoty hash stránek pro spustitelné soubory.|  
|`/r`  *Kořenový název_předmětu*|Určuje název předmětu kořenového certifikátu, jehož článkem musí podpisový certifikát být. Tato hodnota může být podřetězec celého názvu předmětu kořenového certifikátu.|  
|`/s`  *Storename*|Určuje úložiště k otevření při hledání certifikátu. Pokud tato možnost není `My` zadána, úložiště se otevře.|  
|`/sha1`  *Hodnota hash*|Určuje algoritmus hash SHA1 podpisového certifikátu. Algoritmus hash SHA1 je obvykle použit, když více certifikátů splňuje kritéria stanovená ve zbývajících přepínačích.|  
|`/sm`|Určuje použití úložiště počítače namísto úložiště uživatele.|  
|`/t`  *Adresu url*|Určuje adresu URL časového razítka serveru. Pokud tato možnost `/tr`(nebo ) není k dispozici, podepsaný soubor nebude označen časem. Pokud se opatření časovým razítkem nezdaří, vygeneruje se upozornění. Tuto možnost nelze s `/tr` touto volbou použít.|  
|`/td`  *Alg*|Používá se `/tr` s možností požádat o algoritmus digest používaný serverem časového razítka RFC 3161.|  
|`/tr`  *Adresu url*|Určuje adresu URL časového razítka serveru RFC 3161. Pokud tato možnost `/t`(nebo ) není k dispozici, podepsaný soubor nebude označen časem. Pokud se opatření časovým razítkem nezdaří, vygeneruje se upozornění. Tuto možnost nelze s `/t` touto volbou použít.|  
|`/u`  *Použití*|Určuje použití rozšířeného klíče (EKU), který musí být součástí podpisového certifikátu. Hodnotu použití lze zadat pomocí OID nebo řetězce. Výchozí použití je „Podepisování kódu“ (1.3.6.1.5.5.7.3.3).|  
|`/uw`|Určuje použití „Ověřování součástí systému Windows“ (1.3.6.1.4.1.311.10.3.6).|  
  
 Příklady použití najdete [v tématu Použití signtoolu k podepsání souboru](/windows/desktop/SecCrypto/using-signtool-to-sign-a-file).  
  
<a name="TimeStamp"></a>
## <a name="timestamp-command-options"></a>Možnosti příkazu TimeStamp  
 V následující tabulce jsou uvedeny možnosti, které lze použít s příkazem. `TimeStamp`  
  
|Možnost TimeStamp|Popis|  
|----------------------|-----------------|  
|`/p7`|Opatří soubory PKCS #7 časovým razítkem.|  
|`/t`  *Adresu url*|Určuje adresu URL časového razítka serveru. Soubor, který má být opatřen časovým razítkem, musí být nejprve podepsán. Je `/t` požadována `/tr` možnost nebo možnost.|  
|`/td`  *Alg*|Požaduje algoritmus digest používaný serverem časového razítka RFC 3161. `/td`se používá `/tr` s možností.|  
|`/tp`*index*|Čas ováže podpis v *indexu*.|  
|`/tr`  *Adresu url*|Určuje adresu URL časového razítka serveru RFC 3161. Soubor, který má být opatřen časovým razítkem, musí být nejprve podepsán. Je `/tr` požadována `/t` možnost nebo možnost.|  
  
 Příklad použití naleznete v tématu [Přidání časových razítek do dříve podepsaných souborů](/windows/desktop/SecCrypto/adding-time-stamps-to-previously-signed-files).  
  
<a name="Verify"></a>
## <a name="verify-command-options"></a>Možnosti příkazu Verify  
  
|Možnost Verify|Popis|  
|-------------------|-----------------|  
|`/a`|Určuje, že všechny metody lze použít k ověření souboru. Nejprve se prohledají databáze katalogu a určí se, zda je soubor v katalogu podepsán. Pokud soubor není podepsán v žádném katalogu, nástroj Sign Tool se pokusí ověřit vložený podpis souboru. Tato možnost je doporučena při ověřování souborů, které mohou nebo nemusí být podepsány v katalogu. Mezi tyto soubory patří soubory systému Windows nebo ovladače.|  
|`/ad`|Vyhledá katalog pomocí výchozí databáze katalogu.|  
|`/ag`*CatDBGUID*|Najde katalog v databázi katalogu, který je identifikován *CatDBGUID*.|  
|`/all`|Ověří všechny podpisy v souboru, který obsahuje více podpisů.|  
|`/as`|Vyhledá v katalogu pomocí databáze katalogů systémovou komponentu (ovladač).|  
|`/c`*Soubor CatFile*|Určuje soubor katalogu podle názvu.|  
|`/d`|Určuje, že má nástroj Sign Tool vytisknout popis a adresu URL popisu.|  
|`/ds`  *Index*|Ověřuje podpis na určené pozici.|  
|`/hash`(`SHA1` `SHA256`&#124;)|Určuje volitelný hashovací algoritmus k použití pro hledání souboru v katalogu.|  
|`/kp`|Určuje, že by mělo být provedeno ověření pomocí zásady podepisování ovladačů v režimu jádra.|  
|`/ms`|Používá několik sémantik pro ověřování. Toto je výchozí chování volání [WinVerifyTrust](/windows/desktop/api/wintrust/nf-wintrust-winverifytrust) v systému Windows 8 a vyšší.|  
|`/o`*Verze*|Ověřuje soubor podle verze operačního systému. *Verze* má následující formu: *PlatformID*:*VerMajor*. *VerMinor*. *BuildNumber*. *PlatformID* představuje základní hodnotu člena výčtu. <xref:System.PlatformID> **Důležité:**  Doporučuje se `/o` použití spínače. Pokud `/o` není zadán, SignTool.exe může vrátit neočekávané výsledky. Pokud například nezahrnete `/o` přepínač, nemusí se systémové katalogy, které správně ověřují ve starším operačním systému, v novějším operačním systému ověřit správně.|  
|`/p7`|Ověří soubory PKCS #7. Žádné existující zásady nejsou použity pro ověřování PKCS #7. Podpis je zkontrolován a řetězec je sestaven pro podpisový certifikát.|  
|`/pa`|Určuje, že mají být použity výchozí zásady ověření pomocí technologie Authenticode. Pokud `/pa` tato možnost není zadána, nástroj Sign Tool používá zásady ověřování ovladačů systému Windows. Tuto možnost nelze použít `catdb` s možnostmi.|  
|`/pg`*PolicyGUID*|Určuje zásady ověření podle identifikátoru GUID. *PolicyGUID* odpovídá ActionID ověřovací politiky. Tuto možnost nelze použít `catdb` s možnostmi.|  
|`/ph`|Určuje, že nástroj Sign Tool má tisknout a ověřit hash hodnoty stránky.|  
|`/r`*Kořenový název_předmětu*|Určuje název předmětu kořenového certifikátu, jehož článkem musí podpisový certifikát být. Tato hodnota může být podřetězec celého názvu předmětu kořenového certifikátu.|  
|`/tw`|Určuje, že by mělo být vygenerováno upozornění, pokud podpis nemá časové razítko.|  
  
 Příklady použití naleznete [v tématu Použití nástroje SignTool k ověření podpisu souboru](/windows/desktop/SecCrypto/using-signtool-to-verify-a-file-signature).  
  
## <a name="return-value"></a>Návratová hodnota  
 Nástroj Sign Tool vrátí jeden z následujících ukončovacích kódů při svém ukončení.  
  
|Ukončovací kód|Popis|  
|---------------|-----------------|  
|0|Spuštění proběhlo úspěšně.|  
|1|Spuštění se nezdařilo.|  
|2|Spuštění bylo dokončeno s varováními.|  
  
## <a name="examples"></a>Příklady  
 Následující příkaz přidá soubor katalogu MyCatalogFileName.cat do systémové komponenty a databáze ovladačů. Tato `/u` možnost vpřípadě potřeby vygeneruje jedinečný název, `MyCatalogFileName.cat`aby se zabránilo nahrazení existujícího souboru katalogu s názvem .  
  
```console  
signtool catdb /v /u MyCatalogFileName.cat  
```  
  
 Následující příkaz podepíše soubor automaticky pomocí nejvhodnějšího certifikátu.  
  
```console  
signtool sign /a MyFile.exe  
```  
  
 Následující příkaz digitálně podepisuje soubor pomocí certifikátu uloženého v souboru PFX chráněném heslem.  
  
```console  
signtool sign /f MyCert.pfx /p MyPassword MyFile.exe  
```  
  
 Následující příkaz digitálně podepíše soubor a opatří ho časovým razítkem. Certifikát použitý k podepsání souboru je uložen v souboru PFX.  
  
```console  
signtool sign /f MyCert.pfx /t http://timestamp.digicert.com MyFile.exe  
```  
  
 Následující příkaz podepisuje soubor pomocí `My` certifikátu umístěného `My Company Certificate`v úložišti, který má název subjektu .  
  
```console  
signtool sign /n "My Company Certificate" MyFile.exe  
```  
  
 Následující příkaz podepíše ovládací prvek ActiveX a poskytuje informace, které aplikace Internet Explorer zobrazí, když je uživatel vyzván k instalaci ovládacího prvku.  
  
```console  
Signtool sign /f MyCert.pfx /d: "MyControl" /du http://www.example.com/MyControl/info.html MyControl.exe  
```  
  
 Následující příkaz opatří digitálně podepsaný soubor časovým razítkem.  
  
```console  
signtool timestamp /t http://timestamp.digicert.com MyFile.exe  
```  
  
 Následující příkaz ověří, že soubor byl podepsán.  
  
```console  
signtool verify MyFile.exe  
```  
  
 Následující příkaz ověří systémový soubor, který může být podepsán v katalogu.  
  
```console  
signtool verify /a SystemFile.dll  
```  
  
 Následující příkaz ověří systémový soubor, který je `MyCatalog.cat`podepsán v katalogu s názvem .  
  
```console  
signtool verify /c MyCatalog.cat SystemFile.dll  
```  
  
## <a name="see-also"></a>Viz také

- [Nástroje](index.md)
- [Příkazové řádky](developer-command-prompt-for-vs.md)
