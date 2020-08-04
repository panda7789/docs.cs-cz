---
title: SignTool.exe (nástroj pro podpis)
description: Přečtěte si o SignTool.exe nástroje pro podepisování. Tento nástroj příkazového řádku digitálně podepíše soubory, ověří podpisy v souborech a použije časová razítka souborů.
ms.date: 03/30/2017
helpviewer_keywords:
- Sign tool
- SignTool.exe
ms.assetid: 0c25ff6c-bff3-422e-b017-146a3ee86cb9
ms.openlocfilehash: f1254f345a8b3bb796217442cbad36d2e942b403
ms.sourcegitcommit: b4f8849c47c1a7145eb26ce68bc9f9976e0dbec3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/03/2020
ms.locfileid: "87517201"
---
# <a name="signtoolexe-sign-tool"></a>SignTool.exe (nástroj pro podpis)
Sign Tool je nástroj příkazového řádku, který digitálně podepíše soubory, ověří podpisy v souborech a časová razítka souborů.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li spustit nástroj, použijte Developer Command Prompt pro Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7). Další informace najdete v tématu [výzvy k zadání příkazu](developer-command-prompt-for-vs.md).  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
signtool [command] [options] [file_name | ...]  
```  
  
## <a name="parameters"></a>Parametry  
  
|Argument|Description|  
|--------------|-----------------|  
|`command`|Jeden ze čtyř příkazů ( `catdb` , `sign` , `Timestamp` nebo `Verify` ), který určuje operaci, která má být provedena u souboru. Popis jednotlivých příkazů naleznete v následující tabulce.|  
|`options`|Volba, která upravuje příkaz. Kromě globálních `/q` `/v` možností a možnosti podporuje každý příkaz jedinečnou sadu možností.|  
|`file_name`|Cesta k souboru, který chcete podepsat.|  
  
 Následující příkazy jsou podporovány nástrojem Sign Tool. Každý příkaz se používá s různou sadou možností, které jsou uvedeny v příslušných oddílech.  
  
|Příkaz|Popis|  
|-------------|-----------------|  
|`catdb`|Přidá nebo odebere soubor katalogu z databáze katalogů. Databáze katalogů slouží k automatickému vyhledávání souborů katalogu a jsou označeny identifikátorem GUID. Seznam možností podporovaných `catdb` příkazem naleznete v tématu [CatDB Command Options](signtool-exe.md#catdb).|  
|`sign`|Digitálně podepíše soubory. Digitální podpisy chrání soubory před neoprávněnými změnami a umožňují uživatelům ověřit podpis na základě podpisového certifikátu. Seznam možností podporovaných `sign` příkazem najdete v tématu [Možnosti příkazu Sign](signtool-exe.md#sign).|  
|`Timestamp`|Opatří soubory časovým razítkem. Seznam možností podporovaných `TimeStamp` příkazem naleznete v tématu [Možnosti příkazu TimeStamp](signtool-exe.md#TimeStamp).|  
|`Verify`|Ověří digitální podpis souborů stanovením, zda podpisový certifikát byl vydán důvěryhodnou autoritou, zda podpisový certifikát nebyl odvolán, a případně zda podpisový certifikát je platný pro konkrétní zásady. Seznam možností podporovaných `Verify` příkazem najdete v tématu [ověření možností příkazu](signtool-exe.md#Verify).|  
  
 Tyto možnosti platí pro všechny příkazy nástroje pro podepisování.  
  
|Možnost Global|Description|  
|-------------------|-----------------|  
|**parametr**|Pokud se příkaz úspěšně spustí, nezobrazí se žádný výstup. Pokud se příkaz nezdaří, zobrazí se minimální výstup.|  
|**/v**|Zobrazí podrobný výstup bez ohledu na to, zda bude příkaz úspěšně spuštěn, nebo se nezdaří, a zobrazí upozornění.|  
|**/Debug**|Zobrazí informace o ladění.|  
  
<a name="catdb"></a>
## <a name="catdb-command-options"></a>Možnosti příkazu catdb  
 V následující tabulce jsou uvedeny možnosti, které lze použít s `catdb` příkazem.  
  
|Možnost Catdb|Description|  
|------------------|-----------------|  
|`/d`|Určuje, že výchozí databáze katalogů je aktualizována. Pokud ani jednu z `/d` `/g` možností není použita, nástroj Sign Tool aktualizuje součást systému a databázi ovladačů.|  
|`/g` *Identifikátor GUID*|Určuje, že je aktualizována databáze katalogu identifikovaná globálně jedinečným identifikátorem *GUID* .|  
|`/r`|Odebere zadané katalogy z databáze katalogů. Pokud není tato možnost zadána, nástroj Sign Tool přidá určené katalogy do databáze katalogů.|  
|`/u`|Určuje, že přidaným souborům katalogu bude přiřazen jedinečný název. V případě potřeby jsou soubory katalogu přejmenovány, aby se předešlo konfliktům názvů s existujícími soubory katalogu. Pokud není tato možnost zadána, přepíše nástroj Sign Tool jakýkoli existující katalog, který má stejný název jako přidávaný katalog.|  
  
<a name="sign"></a>
## <a name="sign-command-options"></a>Možnosti příkazu sign  
 V následující tabulce jsou uvedeny možnosti, které lze použít s `sign` příkazem.  
  
|Možnost příkazu sign|Description|  
|-------------------------|-----------------|  
|`/a`|Automaticky vybere nejlepší podpisový certifikát. Nástroj Sign Tool vyhledá všechny platné certifikáty, které splňují všechny zadané podmínky, a vybere ten, který je platný pro co nejdelší dobu. Pokud tato možnost není k dispozici, očekává nástroj Sign Tool pouze jeden platný podpisový certifikát.|  
|`/ac`  *souborů*|Přidá další certifikát ze *souboru* do bloku signatury.|  
|`/as`|Připojí tento podpis. Pokud neexistuje žádný primární podpis, tento podpis se stane primárním podpisem.|  
|`/c`  *CertTemplateName*|Určuje název šablony certifikátu (rozšíření Microsoft) pro podpisový certifikát.|  
|`/csp`  *CSPName*|Určuje poskytovatele CSP (Cryptographic Service Provider), který obsahuje kontejner soukromého klíče.|  
|`/d`  *Řetězec*|Určuje popis podepsaného obsahu.|  
|`/du`  *Adresa URL*|Určuje adresu URL (Uniform Resource Locator) pro rozšířený popis podepsaného obsahu.|  
|`/f`  *SignCertFile*|Určuje podpisový certifikát v souboru. Pokud je soubor ve formátu PFX (Personal Information Exchange) a je chráněn heslem, použijte `/p` k zadání hesla možnost. Pokud soubor neobsahuje soukromé klíče, použijte `/csp` Možnosti a a `/kc` Zadejte název kontejneru CSP a privátního klíče.|  
|`/fd`|Určuje soubor algoritmu digest pro vytváření podpisů souborů. Výchozím je SHA1.|  
|`/i`  *Název vystavitele*|Určuje název vystavitele podpisového certifikátu. Tato hodnota může být podřetězec celého jména vystavitele.|  
|`/kc`  *PrivKeyContainerName*|Určuje název kontejneru soukromého klíče.|  
|`/n`  *SubjectName*|Určuje název předmětu podpisového certifikátu. Tato hodnota může být podřetězec celého názvu subjektu.|  
|`/nph`|V případě podpory potlačuje hodnoty hash stránek pro spustitelné soubory. Výchozí hodnota je určena proměnnou prostředí SIGNTOOL_PAGE_HASHES a verzí wintrust.dll. Tato možnost je ignorována pro soubory, které nejsou typu PE.|  
|`/p`  *Heslo*|Určuje heslo, které má být použito při otevírání souboru PFX. ( `/f` K určení souboru PFX použijte možnost.)|  
|`/p7` *Cesta*|Určuje, že soubor PKCS (Public Key Cryptography Standards) #7 je vytvořen pro každý zadaný soubor obsahu. Soubory PKCS #7 mají název *cesta* \\ *filename*. P7.|  
|`/p7ce` *Hodnota*|Určuje volby pro podepsaný obsah PKCS #7. Nastavením *hodnoty* na "Embedded" vložte podepsaný obsah do souboru PKCS #7 nebo na "DetachedSignedData", čímž se vytvoří část podepsaného souboru PKCS #7 se znaménkem. Pokud se `/p7ce` možnost nepoužívá, bude ve výchozím nastavení vložen podepsaný obsah.|  
|`/p7co` *\<OID>*|Určuje identifikátor objektu (OID), který identifikuje podepsaný obsah PKCS #7.|  
|`/ph`|V případě podpory generuje hodnoty hash stránek pro spustitelné soubory.|  
|`/r`  *RootSubjectName*|Určuje název předmětu kořenového certifikátu, jehož článkem musí podpisový certifikát být. Tato hodnota může být podřetězec celého názvu předmětu kořenového certifikátu.|  
|`/s`  *StoreName*|Určuje úložiště k otevření při hledání certifikátu. Pokud není tato možnost zadána, `My` je úložiště otevřeno.|  
|`/sha1`  *Kontrole*|Určuje algoritmus hash SHA1 podpisového certifikátu. Algoritmus hash SHA1 je obvykle použit, když více certifikátů splňuje kritéria stanovená ve zbývajících přepínačích.|  
|`/sm`|Určuje použití úložiště počítače namísto úložiště uživatele.|  
|`/t`  *Adresa URL*|Určuje adresu URL časového razítka serveru. Pokud tato možnost (nebo `/tr` ) není k dispozici, nebude podepsaný soubor označen časovým razítkem. Pokud se opatření časovým razítkem nezdaří, vygeneruje se upozornění. Tuto možnost nelze použít s `/tr` možností.|  
|`/td`  *ALG*|Používá se s `/tr` možností pro vyžádání algoritmu Digest používaného serverem časového razítka RFC 3161.|  
|`/tr`  *Adresa URL*|Určuje adresu URL časového razítka serveru RFC 3161. Pokud tato možnost (nebo `/t` ) není k dispozici, nebude podepsaný soubor označen časovým razítkem. Pokud se opatření časovým razítkem nezdaří, vygeneruje se upozornění. Tuto možnost nelze použít s `/t` možností.|  
|`/u`  *Využití*|Určuje použití rozšířeného klíče (EKU), který musí být součástí podpisového certifikátu. Hodnotu použití lze zadat pomocí OID nebo řetězce. Výchozí použití je „Podepisování kódu“ (1.3.6.1.5.5.7.3.3).|  
|`/uw`|Určuje použití „Ověřování součástí systému Windows“ (1.3.6.1.4.1.311.10.3.6).|  
  
 Příklady použití najdete v tématu [použití nástroje SignTool k podepsání souboru](/windows/desktop/SecCrypto/using-signtool-to-sign-a-file).  
  
<a name="TimeStamp"></a>
## <a name="timestamp-command-options"></a>Možnosti příkazu TimeStamp  
 V následující tabulce jsou uvedeny možnosti, které lze použít s `TimeStamp` příkazem.  
  
|Možnost TimeStamp|Description|  
|----------------------|-----------------|  
|`/p7`|Opatří soubory PKCS #7 časovým razítkem.|  
|`/t`  *Adresa URL*|Určuje adresu URL časového razítka serveru. Soubor, který má být opatřen časovým razítkem, musí být nejprve podepsán. `/t` `/tr` Je vyžadována buď možnost, nebo.|  
|`/td`  *ALG*|Požaduje algoritmus digest používaný serverem časového razítka RFC 3161. `/td`se používá s `/tr` možností.|  
|`/tp`*index*|Časová razítka signatury v *indexu*.|  
|`/tr`  *Adresa URL*|Určuje adresu URL časového razítka serveru RFC 3161. Soubor, který má být opatřen časovým razítkem, musí být nejprve podepsán. `/tr` `/t` Je vyžadována buď možnost, nebo.|  
  
 Příklad použití naleznete v tématu [Přidání časových razítek do dříve podepsaných souborů](/windows/desktop/SecCrypto/adding-time-stamps-to-previously-signed-files).  
  
<a name="Verify"></a>
## <a name="verify-command-options"></a>Možnosti příkazu Verify  
  
|Možnost Verify|Description|  
|-------------------|-----------------|  
|`/a`|Určuje, že všechny metody lze použít k ověření souboru. Nejprve se prohledají databáze katalogu a určí se, zda je soubor v katalogu podepsán. Pokud soubor není podepsán v žádném katalogu, nástroj Sign Tool se pokusí ověřit vložený podpis souboru. Tato možnost je doporučena při ověřování souborů, které mohou nebo nemusí být podepsány v katalogu. Mezi tyto soubory patří soubory systému Windows nebo ovladače.|  
|`/ad`|Vyhledá katalog pomocí výchozí databáze katalogu.|  
|`/ag`*CatDBGUID*|Vyhledá katalog v databázi katalogu, který je identifikovaný z *CatDBGUID*.|  
|`/all`|Ověří všechny podpisy v souboru, který obsahuje více podpisů.|  
|`/as`|Vyhledá v katalogu pomocí databáze katalogů systémovou komponentu (ovladač).|  
|`/c`*CatFile*|Určuje soubor katalogu podle názvu.|  
|`/d`|Určuje, že má nástroj Sign Tool vytisknout popis a adresu URL popisu.|  
|`/ds`  *Index*|Ověřuje podpis na určené pozici.|  
|`/hash`( `SHA1`&#124;`SHA256` )|Určuje volitelný hashovací algoritmus k použití pro hledání souboru v katalogu.|  
|`/kp`|Určuje, že by mělo být provedeno ověření pomocí zásady podepisování ovladačů v režimu jádra.|  
|`/ms`|Používá několik sémantik pro ověřování. Toto je výchozí chování při volání funkce [WinVerifyTrust](/windows/desktop/api/wintrust/nf-wintrust-winverifytrust) ve Windows 8 a novějších verzích.|  
|`/o` *Verze*|Ověřuje soubor podle verze operačního systému. *Verze* má následující formát: *PlatformID*:*VerMajor*. *Škůdce*. *BuildNumber*. *PlatformID* představuje nadřazenou hodnotu <xref:System.PlatformID> člena výčtu. **Důležité informace:**  Doporučuje se použít `/o` přepínač. Pokud `/o` parametr není zadán, SignTool.exe mohou vracet neočekávané výsledky. Pokud například přepínač nezadáte `/o` , systémové katalogy, které jsou správně ověřeny ve starším operačním systému, nemusí být správně ověřeny v novějším operačním systému.|  
|`/p7`|Ověří soubory PKCS #7. Žádné existující zásady nejsou použity pro ověřování PKCS #7. Podpis je zkontrolován a řetězec je sestaven pro podpisový certifikát.|  
|`/pa`|Určuje, že mají být použity výchozí zásady ověření pomocí technologie Authenticode. Pokud `/pa` možnost není zadána, nástroj Sign Tool použije zásady ověřování ovladačů systému Windows. Tuto možnost nelze použít s `catdb` možnostmi.|  
|`/pg`*PolicyGUID*|Určuje zásady ověření podle identifikátoru GUID. *PolicyGUID* odpovídá ActionID zásad ověřování. Tuto možnost nelze použít s `catdb` možnostmi.|  
|`/ph`|Určuje, že nástroj Sign Tool má tisknout a ověřit hash hodnoty stránky.|  
|`/r`*RootSubjectName*|Určuje název předmětu kořenového certifikátu, jehož článkem musí podpisový certifikát být. Tato hodnota může být podřetězec celého názvu předmětu kořenového certifikátu.|  
|`/tw`|Určuje, že by mělo být vygenerováno upozornění, pokud podpis nemá časové razítko.|  
  
 Příklady použití najdete v tématu [použití nástroje SignTool k ověření podpisu souboru](/windows/desktop/SecCrypto/using-signtool-to-verify-a-file-signature).  
  
## <a name="return-value"></a>Návratová hodnota  
 Nástroj Sign Tool vrátí jeden z následujících ukončovacích kódů při svém ukončení.  
  
|Ukončovací kód|Popis|  
|---------------|-----------------|  
|0|Spuštění proběhlo úspěšně.|  
|1|Spuštění se nezdařilo.|  
|2|Spuštění bylo dokončeno s varováními.|  
  
## <a name="examples"></a>Příklady  
 Následující příkaz přidá soubor katalogu MyCatalogFileName.cat do systémové komponenty a databáze ovladačů. `/u`Možnost vygeneruje jedinečný název, pokud je to nutné, aby se zabránilo nahrazení existujícího souboru katalogu s názvem `MyCatalogFileName.cat` .  
  
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
  
 Následující příkaz podepíše soubor pomocí certifikátu uloženého v `My` úložišti, který má název subjektu `My Company Certificate` .  
  
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
  
 Následující příkaz ověří systémový soubor, který je podepsán v katalogu s názvem `MyCatalog.cat` .  
  
```console  
signtool verify /c MyCatalog.cat SystemFile.dll  
```  
  
## <a name="see-also"></a>Viz také

- [Nástroje](index.md)
- [Výzvy příkazového řádku](developer-command-prompt-for-vs.md)
