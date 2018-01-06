---
title: "SignTool.exe (nástroj pro podpis)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Sign tool
- SignTool.exe
ms.assetid: 0c25ff6c-bff3-422e-b017-146a3ee86cb9
caps.latest.revision: "33"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 326b952b742dc3400b7a84ba35594b61aeaabb6c
ms.sourcegitcommit: 2142a4732bb4ff519b9817db4c24a237b9810d4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/05/2018
---
# <a name="signtoolexe-sign-tool"></a>SignTool.exe (nástroj pro podpis)
Sign Tool je nástroj příkazového řádku, který digitálně podepíše soubory, ověří podpisy v souborech a časová razítka souborů.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li spustit tento nástroj, použijte příkazový řádek vývojáře (nebo příkazový řádek Visual Studio v systému Windows 7). Další informace najdete v tématu [příkazového řádku](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```  
signtool [command] [options] [file_name | ...]  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Argument|Popis|  
|--------------|-----------------|  
|`command`|Čtyři příkazy (`catdb`, `sign`, `Timestamp`, nebo `Verify`), který určuje operace provádět na soubor. Popis jednotlivých příkazů naleznete v následující tabulce.|  
|`options`|Volba, která upravuje příkaz. Kromě na globální `/q` a `/v` podporuje možnosti, každý příkaz jedinečnou sadu voleb.|  
|`file_name`|Cesta k souboru, který chcete podepsat.|  
  
 Následující příkazy jsou podporovány nástrojem Sign Tool. Každý příkaz se používá s různou sadou možností, které jsou uvedeny v příslušných oddílech.  
  
|Příkaz|Popis|  
|-------------|-----------------|  
|`catdb`|Přidá nebo odebere soubor katalogu z databáze katalogů. Databáze katalogů slouží k automatickému vyhledávání souborů katalogu a jsou označeny identifikátorem GUID. Seznam možnosti podporované `catdb` příkazů najdete v tématu [ukázky catdb parametry příkazu](../../../docs/framework/tools/signtool-exe.md#catdb).|  
|`sign`|Digitálně podepíše soubory. Digitální podpisy chrání soubory před neoprávněnými změnami a umožňují uživatelům ověřit podpis na základě podpisového certifikátu. Seznam možnosti podporované `sign` příkazů najdete v tématu [přihlásit parametry příkazu](../../../docs/framework/tools/signtool-exe.md#sign).|  
|`Timestamp`|Opatří soubory časovým razítkem. Seznam možnosti podporované `TimeStamp` příkazů najdete v tématu [parametry příkazu časové razítko](../../../docs/framework/tools/signtool-exe.md#TimeStamp).|  
|`Verify`|Ověří digitální podpis souborů stanovením, zda podpisový certifikát byl vydán důvěryhodnou autoritou, zda podpisový certifikát nebyl odvolán, a případně zda podpisový certifikát je platný pro konkrétní zásady. Seznam možnosti podporované `Verify` příkazů najdete v tématu [Zkontrolujte parametry příkazu](../../../docs/framework/tools/signtool-exe.md#Verify).|  
  
 Tyto možnosti platí pro všechny příkazy nástroje pro podepisování.  
  
|Možnost Global|Popis|  
|-------------------|-----------------|  
|**/q**|Pokud se příkaz úspěšně spustí, nezobrazí se žádný výstup. Pokud se příkaz nezdaří, zobrazí se minimální výstup.|  
|**/v**|Zobrazí podrobný výstup bez ohledu na to, zda bude příkaz úspěšně spuštěn, nebo se nezdaří, a zobrazí upozornění.|  
|**/debug**|Zobrazí informace o ladění.|  
  
<a name="catdb"></a>   
## <a name="catdb-command-options"></a>Možnosti příkazu catdb  
 V následující tabulce jsou uvedeny možnosti, které lze použít s `catdb` příkaz.  
  
|Možnost Catdb|Popis|  
|------------------|-----------------|  
|`/d`|Určuje, že výchozí databáze katalogů je aktualizována. Pokud `/d` ani `/g` možnost se používá, nástroj pro podpis aktualizuje databázi součásti a ovladače systému.|  
|`/g`*IDENTIFIKÁTOR GUID*|Určuje, že databáze katalogu identifikovaný globálně jedinečný identifikátor *GUID* se aktualizuje.|  
|`/r`|Odebere zadané katalogy z databáze katalogů. Pokud není tato možnost zadána, nástroj Sign Tool přidá určené katalogy do databáze katalogů.|  
|`/u`|Určuje, že přidaným souborům katalogu bude přiřazen jedinečný název. V případě potřeby jsou soubory katalogu přejmenovány, aby se předešlo konfliktům názvů s existujícími soubory katalogu. Pokud není tato možnost zadána, přepíše nástroj Sign Tool jakýkoli existující katalog, který má stejný název jako přidávaný katalog.|  
  
<a name="sign"></a>   
## <a name="sign-command-options"></a>Možnosti příkazu sign  
 V následující tabulce jsou uvedeny možnosti, které lze použít s `sign` příkaz.  
  
|Možnost příkazu sign|Popis|  
|-------------------------|-----------------|  
|`/a`|Automaticky vybere nejlepší podpisový certifikát. Nástroj Sign Tool vyhledá všechny platné certifikáty, které splňují všechny zadané podmínky, a vybere ten, který je platný pro co nejdelší dobu. Pokud tato možnost není k dispozici, očekává nástroj Sign Tool pouze jeden platný podpisový certifikát.|  
|`/ac`  *soubor*|Přidá další certifikát z *souboru* na blok signatury.|  
|`/as`|Připojí tento podpis. Pokud neexistuje žádný primární podpis, tento podpis se stane primárním podpisem.|  
|`/c`  *CertTemplateName*|Určuje název šablony certifikátu (rozšíření Microsoft) pro podpisový certifikát.|  
|`/csp`  *Název_csp*|Určuje poskytovatele CSP (Cryptographic Service Provider), který obsahuje kontejner soukromého klíče.|  
|`/d`  *Desc*|Určuje popis podepsaného obsahu.|  
|`/du`  *ADRESA URL*|Určuje adresu URL (Uniform Resource Locator) pro rozšířený popis podepsaného obsahu.|  
|`/f`  *SignCertFile*|Určuje podpisový certifikát v souboru. Pokud soubor má formát Personal Information Exchange (PFX) a chráněný heslem, použijte `/p` možnost zadat heslo. Pokud soubor neobsahuje privátních klíčů, použijte `/csp` a `/kc` možností určíte název kontejneru privátní klíče a CSP.|  
|`/fd`|Určuje soubor algoritmu digest pro vytváření podpisů souborů. Výchozím je SHA1.|  
|`/i`  *IssuerName*|Určuje název vystavitele podpisového certifikátu. Tato hodnota může být podřetězec celého jména vystavitele.|  
|`/kc`  *PrivKeyContainerName*|Určuje název kontejneru soukromého klíče.|  
|`/n`  *SubjectName*|Určuje název předmětu podpisového certifikátu. Tato hodnota může být podřetězec celého názvu subjektu.|  
|`/nph`|V případě podpory potlačuje hodnoty hash stránek pro spustitelné soubory. Výchozí hodnota je určena proměnnou prostředí SIGNTOOL_PAGE_HASHES a verzí wintrust.dll. Tato možnost je ignorována pro soubory, které nejsou typu PE.|  
|`/p`  *Heslo*|Určuje heslo, které má být použito při otevírání souboru PFX. (Použití `/f` můžete určit soubor PFX.)|  
|`/p7`*Cesta*|Určuje, že soubor PKCS (Public Key Cryptography Standards) #7 je vytvořen pro každý zadaný soubor obsahu. Soubory PKCS #7 jsou pojmenované *cesta*\\*filename*.p7.|  
|`/p7ce`*Hodnota*|Určuje volby pro podepsaný obsah PKCS #7. Nastavit *hodnotu* "Vložených" Vložit podepsaný obsah do souboru PKCS #7, nebo "DetachedSignedData" k vytvoření podepsaná data část odpojit souboru PKCS #7. Pokud `/p7ce` není možnost použít, je ve výchozím nastavení vložených podepsaného obsahu.|  
|`/p7co` *\<OID >*|Určuje identifikátor objektu (OID), který identifikuje podepsaný obsah PKCS #7.|  
|`/ph`|V případě podpory generuje hodnoty hash stránek pro spustitelné soubory.|  
|`/r`  *RootSubjectName*|Určuje název předmětu kořenového certifikátu, jehož článkem musí podpisový certifikát být. Tato hodnota může být podřetězec celého názvu předmětu kořenového certifikátu.|  
|`/s`  *StoreName*|Určuje úložiště k otevření při hledání certifikátu. Pokud není tato možnost zadána, `My` otevřít úložiště.|  
|`/sha1`  *Hodnota hash*|Určuje algoritmus hash SHA1 podpisového certifikátu. Algoritmus hash SHA1 je obvykle použit, když více certifikátů splňuje kritéria stanovená ve zbývajících přepínačích.|  
|`/sm`|Určuje použití úložiště počítače namísto úložiště uživatele.|  
|`/t`  *ADRESA URL*|Určuje adresu URL časového razítka serveru. Pokud tato možnost (nebo `/tr`) nejsou k dispozici, podepsaný soubor nebude časovým razítkem. Pokud se opatření časovým razítkem nezdaří, vygeneruje se upozornění. Tuto možnost nelze použít s `/tr` možnost.|  
|`/td`  *alg*|Používá se `/tr` možnost požadavku digest algoritmus používaný RFC 3161 časového razítka serveru.|  
|`/tr`  *ADRESA URL*|Určuje adresu URL časového razítka serveru RFC 3161. Pokud tato možnost (nebo `/t`) nejsou k dispozici, podepsaný soubor nebude časovým razítkem. Pokud se opatření časovým razítkem nezdaří, vygeneruje se upozornění. Tuto možnost nelze použít s `/t` možnost.|  
|`/u`  *Využití*|Určuje použití rozšířeného klíče (EKU), který musí být součástí podpisového certifikátu. Hodnotu použití lze zadat pomocí OID nebo řetězce. Výchozí použití je „Podepisování kódu“ (1.3.6.1.5.5.7.3.3).|  
|`/uw`|Určuje použití „Ověřování součástí systému Windows“ (1.3.6.1.4.1.311.10.3.6).|  
  
 Příklady použití najdete v tématu [pomocí SignTool k podpisu souboru](http://msdn.microsoft.com/library/windows/desktop/aa388170.aspx).  
  
<a name="TimeStamp"></a>   
## <a name="timestamp-command-options"></a>Možnosti příkazu TimeStamp  
 V následující tabulce jsou uvedeny možnosti, které lze použít s `TimeStamp` příkaz.  
  
|Možnost TimeStamp|Popis|  
|----------------------|-----------------|  
|`/p7`|Opatří soubory PKCS #7 časovým razítkem.|  
|`/t`  *ADRESA URL*|Určuje adresu URL časového razítka serveru. Soubor, který má být opatřen časovým razítkem, musí být nejprve podepsán. Buď `/t` nebo `/tr` možnost je povinná.|  
|`/td`  *alg*|Požaduje algoritmus digest používaný serverem časového razítka RFC 3161. `/td`se používá s `/tr` možnost.|  
|`/tp`*indexu*|Časové značky podpisu v *index*.|  
|`/tr`  *ADRESA URL*|Určuje adresu URL časového razítka serveru RFC 3161. Soubor, který má být opatřen časovým razítkem, musí být nejprve podepsán. Buď `/tr` nebo `/t` možnost je povinná.|  
  
 Příklad použití naleznete v tématu [přidání časová razítka na dříve podepsané soubory](http://msdn.microsoft.com/library/windows/desktop/aa375542.aspx).  
  
<a name="Verify"></a>   
## <a name="verify-command-options"></a>Možnosti příkazu Verify  
  
|Možnost Verify|Popis|  
|-------------------|-----------------|  
|`/a`|Určuje, že všechny metody lze použít k ověření souboru. Nejprve se prohledají databáze katalogu a určí se, zda je soubor v katalogu podepsán. Pokud soubor není podepsán v žádném katalogu, nástroj Sign Tool se pokusí ověřit vložený podpis souboru. Tato možnost je doporučena při ověřování souborů, které mohou nebo nemusí být podepsány v katalogu. Mezi tyto soubory patří soubory systému Windows nebo ovladače.|  
|`/ad`|Vyhledá katalog pomocí výchozí databáze katalogu.|  
|`/ag`*CatDBGUID*|Vyhledá katalogu v databázi katalogu, která je identifikovaná *CatDBGUID*.|  
|`/all`|Ověří všechny podpisy v souboru, který obsahuje více podpisů.|  
|`/as`|Vyhledá v katalogu pomocí databáze katalogů systémovou komponentu (ovladač).|  
|`/c`*CatFile*|Určuje soubor katalogu podle názvu.|  
|`/d`|Určuje, že má nástroj Sign Tool vytisknout popis a adresu URL popisu.|  
|`/ds`  *Index*|Ověřuje podpis na určené pozici.|  
|`/hash` (`SHA1`&#124;`SHA256`)|Určuje volitelný hash algoritmus k použití pro hledání souboru v katalogu.|  
|`/kp`|Určuje, že by mělo být provedeno ověření pomocí zásady podepisování ovladačů v režimu jádra.|  
|`/ms`|Používá několik sémantik pro ověřování. Toto je výchozí chování [WinVerifyTrust](http://msdn.microsoft.com/library/windows/desktop/aa388208.aspx) volání na [!INCLUDE[win8](../../../includes/win8-md.md)] a vyšší.|  
|`/o`*Verze*|Ověřuje soubor podle verze operačního systému. *Verze* má následující formát: *PlatformID*:*VerMajor*. *VerMinor*. *BuildNumber*. *PlatformID* představuje základní hodnotu <xref:System.PlatformID> – člen výčtu. **Důležité:** použití `/o` přepínače doporučujeme. Pokud `/o` není zadán, SignTool.exe může vrátit neočekávané výsledky. Například, pokud neuvedete `/o` přepínače, systémových katalogů, které ověřit správně na se starším operačním systémem nemusí správně ověřit na novější operační systém.|  
|`/p7`|Ověří soubory PKCS #7. Žádné existující zásady nejsou použity pro ověřování PKCS #7. Podpis je zkontrolován a řetězec je sestaven pro podpisový certifikát.|  
|`/pa`|Určuje, že mají být použity výchozí zásady ověření pomocí technologie Authenticode. Pokud `/pa` není určena možnost, nástroj pro podpis využívá zásady ověřování ovladačů systému Windows. Tuto možnost nelze použít s `catdb` možnosti.|  
|`/pg`*PolicyGUID*|Určuje zásady ověření podle identifikátoru GUID. *PolicyGUID* odpovídá ActionID zásad ověření. Tuto možnost nelze použít s `catdb` možnosti.|  
|`/ph`|Určuje, že nástroj Sign Tool má tisknout a ověřit hash hodnoty stránky.|  
|`/r`*RootSubjectName*|Určuje název předmětu kořenového certifikátu, jehož článkem musí podpisový certifikát být. Tato hodnota může být podřetězec celého názvu předmětu kořenového certifikátu.|  
|`/tw`|Určuje, že by mělo být vygenerováno upozornění, pokud podpis nemá časové razítko.|  
  
 Příklady použití najdete v tématu [pomocí SignTool k ověření podpisu souboru](http://msdn.microsoft.com/library/windows/desktop/aa388171.aspx).  
  
## <a name="return-value"></a>Návratová hodnota  
 Nástroj Sign Tool vrátí jeden z následujících ukončovacích kódů při svém ukončení.  
  
|Ukončovací kód|Popis|  
|---------------|-----------------|  
|0|Spuštění proběhlo úspěšně.|  
|1|Spuštění se nezdařilo.|  
|2|Spuštění bylo dokončeno s varováními.|  
  
## <a name="examples"></a>Příklady  
 Následující příkaz přidá soubor katalogu MyCatalogFileName.cat do systémové komponenty a databáze ovladačů. `/u` Možnost vygeneruje jedinečný název v případě potřeby, aby se zabránilo nahrazení stávající katalogu soubor s názvem `MyCatalogFileName.cat`.  
  
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
  
 Tento příkaz podepíše soubor pomocí certifikát umístěný v `My` úložiště, který obsahuje název subjektu z `My Company Certificate`.  
  
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
  
 Následující příkaz ověřuje systémový soubor, který je přihlášený katalog s názvem `MyCatalog.cat`.  
  
```  
signtool verify /c MyCatalog.cat SystemFile.dll  
```  
  
## <a name="see-also"></a>Viz také  
 [Nástroje](../../../docs/framework/tools/index.md)  
 [Příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
