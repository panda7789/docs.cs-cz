---
title: Certmgr.exe (nástroj Certificate Manager)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- certificates, managing
- CRLs
- certificate trust lists
- Certmgr.exe
- Certificate Manager tool
- CTLs
- certificate revocation lists
ms.assetid: 7e953b43-1374-4bbc-814f-53ca1b6b52bb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ad7ce5dd3739b1edcf8a8a03a2f57376ceba138
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948586"
---
# <a name="certmgrexe-certificate-manager-tool"></a>Certmgr.exe (nástroj Certificate Manager)
Nástroj Správce certifikátů (Certmgr.exe) spravuje certifikáty, seznamy důvěryhodných certifikátů (CTL) a seznamy odvolaných certifikátů (CRL).  
  
 Správce certifikátů je automaticky nainstalován při instalaci sady Visual Studio. Chcete-li spustit nástroj, použijte [příkaz s výzvou](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
> [!NOTE]
> Správce certifikátů (Certmgr.exe) je nástroj příkazového řádku, zatímco Certifikáty (Certmgr.msc) jsou modulem snap-in konzoly MMC (Microsoft Management Console). Vzhledem k tomu, že certmgr. msc se obvykle nachází v systémovém `certmgr` adresáři Windows, může se při zadávání do příkazového řádku načíst modul snap-in Certifikáty konzoly MMC i v případě, že jste otevřeli Developer Command Prompt pro Visual Studio. K tomuto případu může dojít, protože cesta k modulu snap-in předchází cestě nástroje Správce certifikátů v proměnné prostředí PATH. Setkáte-li se s tímto problémem, můžete zadáním cesty ke spustitelnému souboru spustit příkazy Certmgr.exe.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li spustit nástroj, použijte Developer Command Prompt pro Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7). Další informace najdete v tématu [výzvy k zadání příkazu](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 Přehled certifikátů X. 509 najdete v tématu [práce s certifikáty](../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```  
      certmgr [/add | /del | /put] [options]  
[/s[/r registryLocation]] [sourceStorename]  
[/s[/r registryLocation]] [destinationStorename]  
```  
  
## <a name="parameters"></a>Parametry  
  
|Argument|Popis|  
|--------------|-----------------|  
|*sourceStorename*|Úložiště certifikátů obsahuje aktuální certifikáty, soubory CTL nebo CRL, které lze přidat, odstranit, uložit nebo zobrazit. To může představovat soubor úložiště nebo systémové úložiště.|  
|*destinationStorename*|Výstupní úložiště certifikátů nebo soubor.|  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/Add**|Přidá certifikáty, soubory CTL a CRL do úložiště certifikátů.|  
|**/All**|Přidá všechny položky při použití s **/Add**. Odstraní všechny položky při použití s **/del**. Zobrazí všechny položky, pokud jsou použity bez možností **/Add** nebo **/del** . Možnost **/All** nelze použít s **/Put**.|  
|**/c**|Přidá certifikáty při použití s **/Add**. Odstraní certifikáty při použití s **/del**. Ukládá certifikáty při použití s **/Put**. Zobrazí certifikáty při použití bez možnosti **/Add**, **/del**nebo **/Put** .|  
|**/CRL**|Přidá seznam CRL při použití s **/Add**. Odstraní seznamy odvolaných certifikátů při použití s **/del**. Při použití s **/Put**ukládá seznamy CRL. Zobrazí seznam CRL při použití bez možnosti **/Add**, **/del**nebo **/Put** .|  
|**/CTL**|Přidá seznamy CTL při použití s **/Add**. Odstraní seznamy CTL při použití s **/del**. Při použití s **/Put**ukládá seznamy CTL. Zobrazí seznam CTL při použití bez možnosti **/Add**, **/del**nebo **/Put** .|  
|**/del**|Odstraní certifikáty, soubory CTL a CRL z úložiště certifikátů.|  
|**/e** *encodingType*|Určuje typ kódování certifikátu. Výchozí hodnota je `X509_ASN_ENCODING`.|  
|**/f** *dwFlags*|Určuje příznak pro otevření úložiště. Toto je parametr *dwFlags* předaný do **CertOpenStore**. Výchozí hodnota je CERT_SYSTEM_STORE_CURRENT_USER. Tato možnost je zvážena pouze v případě, že je použita možnost **/y** .|  
|**/h**[**elp**]|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|**/n** .|Určuje obecný název certifikátu, který se má přidat, odstranit nebo uložit. Tuto možnost lze použít u certifikátů. Nelze ji použít u souborů CTL nebo u CRL.|  
|**/Put**|Uloží do souboru certifikát X.509, soubor CTL nebo CRL z úložiště certifikátů. Soubor je uložen ve formátu X.509. K uložení souboru ve formátu PKCS #7 můžete použít možnost **/7** s možností **/Put** . Pro možnost **/Put** musí následovat buď **/c**, **/CTL**nebo **/CRL**. Možnost **/All** nelze použít s **/Put**.|  
|**/r** *umístění*|Určuje umístění registru v rámci systémového úložiště. Tato možnost je zvážena pouze v případě, že zadáte možnost **/s** . *umístění* musí být jedna z následujících:<br /><br /> -   `currentUser`označuje, že úložiště certifikátů je pod klíčem HKEY_CURRENT_USER. Toto nastavení je výchozí.<br />-   `localMachine`označuje, že úložiště certifikátů je pod klíčem HKEY_LOCAL_MACHINE.|  
|**/s**|Určuje, že je úložiště certifikátů systémovým úložištěm. Pokud tuto možnost nezadáte, považuje se za úložiště za **StoreFile**.|  
|**/SHA1** *sha1Hash*|Určuje hodnotu hash SHA1 certifikátu, souboru CTl nebo CRl, který se má přidat, odstranit nebo uložit.|  
|**/v**|Určuje podrobný režim. Zobrazí detailní informace o certifikátech, souborech CTL a CRL. Tuto možnost nelze použít s možnostmi **/Add**, **/del**nebo **/Put** .|  
|**/y** *poskytovatel*|Určuje název poskytovatele úložiště.|  
|**/7**|Ukládá cílové úložiště jako objekt PKCS #7.|  
|**/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
  
## <a name="remarks"></a>Poznámky  
 Nástroj Certmgr.exe vykonává následující základní funkce:  
  
- Zobrazí certifikáty, soubory CTL a CRL do konzoly.  
  
- Přidá certifikáty, soubory CTL a CRL do úložiště certifikátů.  
  
- Odstraní certifikáty, soubory CTL a CRL z úložiště certifikátů.  
  
- Uloží do souboru certifikát X.509, soubor CTL nebo CRL z úložiště certifikátů.  
  
 Certmgr. exe pracuje se dvěma typy úložišť certifikátů: **StoreFile** a systémové úložiště. Není nutné zadávat typ úložiště certifikátů. Certmgr.exe dokáže rozpoznat typ úložiště a vykonat příslušné operace.  
  
 Spuštěním nástroje Certmgr.exe bez určení jakýchkoli možností dojde ke spuštění modulu snap-in certmgr.msc, který obsahuje uživatelské rozhraní, které pomáhá s úlohami správy certifikátů, které jsou dostupné také z příkazového řádku. Uživatelské rozhraní poskytuje průvodce importováním, který zkopíruje certifikáty, soubory CTL a CRL z disku do úložiště certifikátů.  
  
 Názvy úložišť certifikátu x509 pro `sourceStorename` parametry a `destinationStorename` můžete najít zkompilováním a spuštěním následujícího kódu.  
  
 [!code-csharp[Tools.CertMgr#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tools.certmgr/cs/storenames1.cs#1)]
 [!code-vb[Tools.CertMgr#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tools.certmgr/vb/storenames1.vb#1)]  
  
 Další informace o certifikátech najdete v tématu [práce s certifikáty](../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## <a name="examples"></a>Příklady  
 Následující příkaz zobrazí výchozí úložiště s názvem `my` s podrobným výstupem.  
  
```  
certmgr /v /s my  
```  
  
 Následující příkaz přidá všechny certifikáty do souboru s názvem `myFile.ext` do nového souboru s názvem. `newFile.ext`  
  
```  
certmgr /add /all /c myFile.ext newFile.ext  
```  
  
 Následující příkaz přidá certifikát do souboru s názvem `testcert.cer` `my` do úložiště systému.  
  
```  
certmgr /add /c testcert.cer /s my  
```  
  
 Následující příkaz přidá certifikát do souboru s názvem `TrustedCert.cer` do kořenového úložiště certifikátů.  
  
```  
certmgr /c /add TrustedCert.cer /s root  
```  
  
 Následující příkaz uloží certifikát s běžným názvem `myCert` `my` do systémového úložiště do souboru s názvem `newCert.cer`.  
  
```  
certmgr /add /c /n myCert /s my newCert.cer  
```  
  
 Následující příkaz odstraní všechny seznamy CTL v `my` úložišti systému a uloží výsledné úložiště do souboru s názvem. `newStore.str`  
  
```  
certmgr /del /all /ctl /s my newStore.str  
```  
  
 Následující příkaz uloží certifikát do `my` systémového úložiště v souboru. `newFile` Zobrazí se výzva k zadání čísla certifikátu z aplikace `my` do `newFile`umístění.  
  
```  
certmgr /put /c /s my newFile  
```  
  
## <a name="see-also"></a>Viz také:

- [Nástroje](../../../docs/framework/tools/index.md)
- [Makecert. exe (Nástroj pro vytvoření certifikátu)](/windows/desktop/SecCrypto/makecert)
- [Příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
