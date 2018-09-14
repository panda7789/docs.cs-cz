---
title: SignTool.exe (nástroj pro podpis)
ms.date: 03/30/2017
helpviewer_keywords:
- Sign tool
- SignTool.exe
ms.assetid: 0c25ff6c-bff3-422e-b017-146a3ee86cb9
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b4cece1227b5210cf839aff0658267ae480b23b6
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2018
ms.locfileid: "45583765"
---
# <a name="signtoolexe-sign-tool"></a>SignTool.exe (nástroj pro podpis)
Sign Tool je nástroj příkazového řádku, který digitálně podepíše soubory, ověří podpisy v souborech a časová razítka souborů.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li spustit tento nástroj, použijte příkazový řádek vývojáře (nebo příkazový řádek Visual Studio v systému Windows 7). Další informace najdete v tématu [příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```  
signtool [command] [options] [file_name | ...]  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Argument|Popis|  
|--------------|-----------------|  
|`command`|Jeden ze čtyř příkazů (`catdb`, `sign`, `Timestamp`, nebo `Verify`), která určuje, jaká operace k provedení u souboru. Popis jednotlivých příkazů naleznete v následující tabulce.|  
|`options`|Volba, která upravuje příkaz. Kromě globálních `/q` a `/v` podporuje možnosti, každý příkaz jedinečnou sadu možností.|  
|`file_name`|Cesta k souboru, který chcete podepsat.|  
  
 Následující příkazy jsou podporovány nástrojem Sign Tool. Každý příkaz se používá s různou sadou možností, které jsou uvedeny v příslušných oddílech.  
  
|Příkaz|Popis|  
|-------------|-----------------|  
|`catdb`|Přidá nebo odebere soubor katalogu z databáze katalogů. Databáze katalogů slouží k automatickému vyhledávání souborů katalogu a jsou označeny identifikátorem GUID. Seznam možností podporovaných příkazem `catdb` naleznete [možnosti příkazu catbd](../../../docs/framework/tools/signtool-exe.md#catdb).|  
|`sign`|Digitálně podepíše soubory. Digitální podpisy chrání soubory před neoprávněnými změnami a umožňují uživatelům ověřit podpis na základě podpisového certifikátu. Seznam možností podporovaných příkazem `sign` naleznete [možnosti příkazu sign](../../../docs/framework/tools/signtool-exe.md#sign).|  
|`Timestamp`|Opatří soubory časovým razítkem. Seznam možností podporovaných příkazem `TimeStamp` naleznete [možnosti příkazu TimeStamp](../../../docs/framework/tools/signtool-exe.md#TimeStamp).|  
|`Verify`|Ověří digitální podpis souborů stanovením, zda podpisový certifikát byl vydán důvěryhodnou autoritou, zda podpisový certifikát nebyl odvolán, a případně zda podpisový certifikát je platný pro konkrétní zásady. Seznam možností podporovaných příkazem `Verify` naleznete [možnosti příkazu Verify](../../../docs/framework/tools/signtool-exe.md#Verify).|  
  
 Tyto možnosti platí pro všechny příkazy nástroje pro podepisování.  
  
|Možnost Global|Popis|  
|-------------------|-----------------|  
|**/q**|Pokud se příkaz úspěšně spustí, nezobrazí se žádný výstup. Pokud se příkaz nezdaří, zobrazí se minimální výstup.|  
|**/v**|Zobrazí podrobný výstup bez ohledu na to, zda bude příkaz úspěšně spuštěn, nebo se nezdaří, a zobrazí upozornění.|  
|**/debug**|Zobrazí informace o ladění.|  
  
<a name="catdb"></a>   
## <a name="catdb-command-options"></a>Možnosti příkazu catdb  
 V následující tabulce jsou uvedeny možnosti, které lze použít s `catdb` příkazu.  
  
|Možnost Catdb|Popis|  
|------------------|-----------------|  
|`/d`|Určuje, že výchozí databáze katalogů je aktualizována. Pokud ani `/d` ani `/g` možnost se používá, nástroj Sign Tool aktualizuje systémové součásti a ovladače databázi.|  
|`/g` *IDENTIFIKÁTOR GUID*|Určuje, že databáze katalogů identifikovaná globálně jedinečným identifikátorem *GUID* se aktualizuje.|  
|`/r`|Odebere zadané katalogy z databáze katalogů. Pokud není tato možnost zadána, nástroj Sign Tool přidá určené katalogy do databáze katalogů.|  
|`/u`|Určuje, že přidaným souborům katalogu bude přiřazen jedinečný název. V případě potřeby jsou soubory katalogu přejmenovány, aby se předešlo konfliktům názvů s existujícími soubory katalogu. Pokud není tato možnost zadána, přepíše nástroj Sign Tool jakýkoli existující katalog, který má stejný název jako přidávaný katalog.|  
  
<a name="sign"></a>   
## <a name="sign-command-options"></a>Možnosti příkazu sign  
 V následující tabulce jsou uvedeny možnosti, které lze použít s `sign` příkazu.  
  
|Možnost příkazu sign|Popis|  
|-------------------------|-----------------|  
|`/a`|Automaticky vybere nejlepší podpisový certifikát. Nástroj Sign Tool vyhledá všechny platné certifikáty, které splňují všechny zadané podmínky, a vybere ten, který je platný pro co nejdelší dobu. Pokud tato možnost není k dispozici, očekává nástroj Sign Tool pouze jeden platný podpisový certifikát.|  
|`/ac`  *Soubor*|Přidá další certifikát z *souboru* do bloku podpisu.|  
|`/as`|Připojí tento podpis. Pokud neexistuje žádný primární podpis, tento podpis se stane primárním podpisem.|  
|`/c`  *CertTemplateName*|Určuje název šablony certifikátu (rozšíření Microsoft) pro podpisový certifikát.|  
|`/csp`  *Název_csp*|Určuje poskytovatele CSP (Cryptographic Service Provider), který obsahuje kontejner soukromého klíče.|  
|`/d`  *desc*|Určuje popis podepsaného obsahu.|  
|`/du`  *ADRESA URL*|Určuje adresu URL (Uniform Resource Locator) pro rozšířený popis podepsaného obsahu.|  
|`/f`  *SignCertFile*|Určuje podpisový certifikát v souboru. Pokud soubor ve formátu Personal Information Exchange (PFX) a je chráněn heslem, použijte `/p` můžete zadat heslo. Pokud soubor neobsahuje soukromé klíče, použijte `/csp` a `/kc` možností, které určují CSP a název kontejneru soukromého klíče.|  
|`/fd`|Určuje soubor algoritmu digest pro vytváření podpisů souborů. Výchozím je SHA1.|  
|`/i`  *IssuerName*|Určuje název vystavitele podpisového certifikátu. Tato hodnota může být podřetězec celého jména vystavitele.|  
|`/kc`  *PrivKeyContainerName*|Určuje název kontejneru soukromého klíče.|  
|`/n`  *SubjectName*|Určuje název předmětu podpisového certifikátu. Tato hodnota může být podřetězec celého názvu subjektu.|  
|`/nph`|V případě podpory potlačuje hodnoty hash stránek pro spustitelné soubory. Výchozí hodnota je určena proměnnou prostředí SIGNTOOL_PAGE_HASHES a verzí wintrust.dll. Tato možnost je ignorována pro soubory, které nejsou typu PE.|  
|`/p`  *Heslo*|Určuje heslo, které má být použito při otevírání souboru PFX. (Použijte `/f` můžete určit soubor PFX.)|  
|`/p7` *Cesta*|Určuje, že soubor PKCS (Public Key Cryptography Standards) #7 je vytvořen pro každý zadaný soubor obsahu. Soubory PKCS #7 jsou pojmenovány *cesta*\\*filename*.p7.|  
|`/p7ce` *Hodnota*|Určuje volby pro podepsaný obsah PKCS #7. Nastavte *hodnota* na "Embedded", chcete-li vložit podepsaný obsah do souboru PKCS #7, nebo "DetachedSignedData" k výrobě podepsané datové části odpojit soubor PKCS #7. Pokud `/p7ce` není použita možnost, je standardně vložen podepsaný obsah.|  
|`/p7co` *\<IDENTIFIKÁTOR OBJEKTU &GT;*|Určuje identifikátor objektu (OID), který identifikuje podepsaný obsah PKCS #7.|  
|`/ph`|V případě podpory generuje hodnoty hash stránek pro spustitelné soubory.|  
|`/r`  *RootSubjectName*|Určuje název předmětu kořenového certifikátu, jehož článkem musí podpisový certifikát být. Tato hodnota může být podřetězec celého názvu předmětu kořenového certifikátu.|  
|`/s`  *storeName*|Určuje úložiště k otevření při hledání certifikátu. Pokud není tato možnost zadána, `My` otevřeno úložiště.|  
|`/sha1`  *Hodnota hash*|Určuje algoritmus hash SHA1 podpisového certifikátu. Algoritmus hash SHA1 je obvykle použit, když více certifikátů splňuje kritéria stanovená ve zbývajících přepínačích.|  
|`/sm`|Určuje použití úložiště počítače namísto úložiště uživatele.|  
|`/t`  *ADRESA URL*|Určuje adresu URL časového razítka serveru. Pokud tato možnost (nebo `/tr`) není k dispozici, nebude podepsaný soubor označen časovým razítkem. Pokud se opatření časovým razítkem nezdaří, vygeneruje se upozornění. Tento parametr nelze použít s `/tr` možnost.|  
|`/td`  *alg*|Použít s `/tr` možnost požádat o algoritmus digest používaný serverem časového razítka RFC 3161.|  
|`/tr`  *ADRESA URL*|Určuje adresu URL časového razítka serveru RFC 3161. Pokud tato možnost (nebo `/t`) není k dispozici, nebude podepsaný soubor označen časovým razítkem. Pokud se opatření časovým razítkem nezdaří, vygeneruje se upozornění. Tento parametr nelze použít s `/t` možnost.|  
|`/u`  *Využití*|Určuje použití rozšířeného klíče (EKU), který musí být součástí podpisového certifikátu. Hodnotu použití lze zadat pomocí OID nebo řetězce. Výchozí použití je „Podepisování kódu“ (1.3.6.1.5.5.7.3.3).|  
|`/uw`|Určuje použití „Ověřování součástí systému Windows“ (1.3.6.1.4.1.311.10.3.6).|  
  
 Příklady využití naleznete v tématu [pomocí SignTool k podepsání souboru](/windows/desktop/SecCrypto/using-signtool-to-sign-a-file).  
  
<a name="TimeStamp"></a>   
## <a name="timestamp-command-options"></a>Možnosti příkazu TimeStamp  
 V následující tabulce jsou uvedeny možnosti, které lze použít s `TimeStamp` příkazu.  
  
|Možnost TimeStamp|Popis|  
|----------------------|-----------------|  
|`/p7`|Opatří soubory PKCS #7 časovým razítkem.|  
|`/t`  *ADRESA URL*|Určuje adresu URL časového razítka serveru. Soubor, který má být opatřen časovým razítkem, musí být nejprve podepsán. Buď `/t` nebo `/tr` možnost je vyžadována.|  
|`/td`  *alg*|Požaduje algoritmus digest používaný serverem časového razítka RFC 3161. `/td` se používá s `/tr` možnost.|  
|`/tp` *Index*|Označit časovou značkou podpis na *index*.|  
|`/tr`  *ADRESA URL*|Určuje adresu URL časového razítka serveru RFC 3161. Soubor, který má být opatřen časovým razítkem, musí být nejprve podepsán. Buď `/tr` nebo `/t` možnost je vyžadována.|  
  
 Příklad použití, naleznete v tématu [přidávání časových razítek dříve podepsané soubory](/windows/desktop/SecCrypto/adding-time-stamps-to-previously-signed-files).  
  
<a name="Verify"></a>   
## <a name="verify-command-options"></a>Možnosti příkazu Verify  
  
|Možnost Verify|Popis|  
|-------------------|-----------------|  
|`/a`|Určuje, že všechny metody lze použít k ověření souboru. Nejprve se prohledají databáze katalogu a určí se, zda je soubor v katalogu podepsán. Pokud soubor není podepsán v žádném katalogu, nástroj Sign Tool se pokusí ověřit vložený podpis souboru. Tato možnost je doporučena při ověřování souborů, které mohou nebo nemusí být podepsány v katalogu. Mezi tyto soubory patří soubory systému Windows nebo ovladače.|  
|`/ad`|Vyhledá katalog pomocí výchozí databáze katalogu.|  
|`/ag` *CatDBGUID*|Vyhledá katalog v databázi katalogu, která je identifikovaná *CatDBGUID*.|  
|`/all`|Ověří všechny podpisy v souboru, který obsahuje více podpisů.|  
|`/as`|Vyhledá v katalogu pomocí databáze katalogů systémovou komponentu (ovladač).|  
|`/c` *CatFile*|Určuje soubor katalogu podle názvu.|  
|`/d`|Určuje, že má nástroj Sign Tool vytisknout popis a adresu URL popisu.|  
|`/ds`  *Index*|Ověřuje podpis na určené pozici.|  
|`/hash` (`SHA1`&#124;`SHA256`)|Určuje volitelný hashovací algoritmus k použití pro hledání souboru v katalogu.|  
|`/kp`|Určuje, že by mělo být provedeno ověření pomocí zásady podepisování ovladačů v režimu jádra.|  
|`/ms`|Používá několik sémantik pro ověřování. Toto je výchozí chování [WinVerifyTrust](/windows/desktop/api/wintrust/nf-wintrust-winverifytrust) volat [!INCLUDE[win8](../../../includes/win8-md.md)] a vyšší.|  
|`/o` *Verze*|Ověřuje soubor podle verze operačního systému. *Verze* má následující formát: *PlatformID*:*VerMajor*. *VerMinor*. *BuildNumber*. *PlatformID* představuje podkladovou hodnotu <xref:System.PlatformID> člena výčtu. **Důležité:** použití `/o` přepínače doporučujeme. Pokud `/o` není zadán, SignTool.exe může vrátit neočekávané výsledky. Například, pokud není zadána `/o` přepínače, systémové katalogy, které byly správně ověřeny ve starším operačním systému nemusí být správně ověřeny v novějším operačním systému.|  
|`/p7`|Ověří soubory PKCS #7. Žádné existující zásady nejsou použity pro ověřování PKCS #7. Podpis je zkontrolován a řetězec je sestaven pro podpisový certifikát.|  
|`/pa`|Určuje, že mají být použity výchozí zásady ověření pomocí technologie Authenticode. Pokud `/pa` možnost nezadáte, nástroj Sign Tool použije zásady ověřování ovladačů Windows. Tento parametr nelze použít s `catdb` možnosti.|  
|`/pg` *PolicyGUID*|Určuje zásady ověření podle identifikátoru GUID. *PolicyGUID* odpovídá ActionID zásadám ověřování. Tento parametr nelze použít s `catdb` možnosti.|  
|`/ph`|Určuje, že nástroj Sign Tool má tisknout a ověřit hash hodnoty stránky.|  
|`/r` *RootSubjectName*|Určuje název předmětu kořenového certifikátu, jehož článkem musí podpisový certifikát být. Tato hodnota může být podřetězec celého názvu předmětu kořenového certifikátu.|  
|`/tw`|Určuje, že by mělo být vygenerováno upozornění, pokud podpis nemá časové razítko.|  
  
 Příklady využití naleznete v tématu [SignTool pomocí ověření podpisu souboru](/windows/desktop/SecCrypto/using-signtool-to-verify-a-file-signature).  
  
## <a name="return-value"></a>Návratová hodnota  
 Nástroj Sign Tool vrátí jeden z následujících ukončovacích kódů při svém ukončení.  
  
|Ukončovací kód|Popis|  
|---------------|-----------------|  
|0|Spuštění proběhlo úspěšně.|  
|1|Spuštění se nezdařilo.|  
|2|Spuštění bylo dokončeno s varováními.|  
  
## <a name="examples"></a>Příklady  
 Následující příkaz přidá soubor katalogu MyCatalogFileName.cat do systémové komponenty a databáze ovladačů. `/u` Možnost generuje jedinečný název, pokud je nutné zabránit nahrazení existujícího souboru katalogu s názvem `MyCatalogFileName.cat`.  
  
```  
signtool catdb /v /u MyCatalogFileName.cat  
```  
  
 Následující příkaz podepíše soubor automaticky pomocí nejvhodnějšího certifikátu.  
  
```  
signtool sign /a MyFile.exe  
```  
  
 Následující příkaz digitálně podepisuje soubor pomocí certifikátu uloženého v souboru PFX chráněném heslem.  
  
```  
signtool sign /f MyCert.pfx /p MyPassword MyFile.exe  
```  
  
 Následující příkaz digitálně podepíše soubor a opatří ho časovým razítkem. Certifikát použitý k podepsání souboru je uložen v souboru PFX.  
  
```  
signtool sign /f MyCert.pfx /t http://timestamp.verisign.com/scripts/timstamp.dll MyFile.exe  
```  
  
 Následující příkaz podepíše soubor pomocí certifikátu uloženého v `My` úložiště, který má název předmětu `My Company Certificate`.  
  
```  
signtool sign /n "My Company Certificate" MyFile.exe  
```  
  
 Následující příkaz podepíše ovládací prvek ActiveX a poskytuje informace, které aplikace Internet Explorer zobrazí, když je uživatel vyzván k instalaci ovládacího prvku.  
  
```  
Signtool sign /f MyCert.pfx /d: "MyControl" /du http://www.example.com/MyControl/info.html MyControl.exe  
```  
  
 Následující příkaz opatří digitálně podepsaný soubor časovým razítkem.  
  
```  
signtool timestamp /t http://timestamp.verisign.com/scripts/timstamp.dll MyFile.exe  
```  
  
 Následující příkaz ověří, že soubor byl podepsán.  
  
```  
signtool verify MyFile.exe  
```  
  
 Následující příkaz ověří systémový soubor, který může být podepsán v katalogu.  
  
```  
signtool verify /a SystemFile.dll  
```  
  
 Následující příkaz ověří systémový soubor, který je podepsán v katalogu s názvem `MyCatalog.cat`.  
  
```  
signtool verify /c MyCatalog.cat SystemFile.dll  
```  
  
## <a name="see-also"></a>Viz také  
 [Nástroje](../../../docs/framework/tools/index.md)  
 [Příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
