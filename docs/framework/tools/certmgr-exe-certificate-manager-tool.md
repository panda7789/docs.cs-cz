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
ms.openlocfilehash: 06fe3a78d0b19720d4f83111980b88806312205f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73129877"
---
# <a name="certmgrexe-certificate-manager-tool"></a>Certmgr.exe (nástroj Certificate Manager)
Nástroj Správce certifikátů (Certmgr.exe) spravuje certifikáty, seznamy důvěryhodných certifikátů (CTL) a seznamy odvolaných certifikátů (CRL).  
  
 Správce certifikátů je automaticky nainstalován při instalaci sady Visual Studio. Chcete-li nástroj spustit, použijte [příkazové příkazy](developer-command-prompt-for-vs.md).  
  
> [!NOTE]
> Správce certifikátů (Certmgr.exe) je nástroj příkazového řádku, zatímco Certifikáty (Certmgr.msc) jsou modulem snap-in konzoly MMC (Microsoft Management Console). Vzhledem k tomu, že se nástroj Certmgr.msc obvykle nachází v adresáři systému Windows, může zadání `certmgr` na příkazovém řádku načíst modul snap-in MMC certifikátů, i když jste otevřeli příkazový řádek pro vývojáře pro aplikaci Visual Studio. K tomuto případu může dojít, protože cesta k modulu snap-in předchází cestě nástroje Správce certifikátů v proměnné prostředí PATH. Setkáte-li se s tímto problémem, můžete zadáním cesty ke spustitelnému souboru spustit příkazy Certmgr.exe.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li nástroj spustit, použijte příkazový řádek pro vývojáře pro sadu Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7). Další informace naleznete v [příkazových koncích](developer-command-prompt-for-vs.md).  
  
 Přehled certifikátů X.509 naleznete v tématu [Práce s certifikáty](../wcf/feature-details/working-with-certificates.md).  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
      certmgr [/add | /del | /put] [options]  
[/s[/r registryLocation]] [sourceStorename]  
[/s[/r registryLocation]] [destinationStorename]  
```  
  
## <a name="parameters"></a>Parametry  
  
|Argument|Popis|  
|--------------|-----------------|  
|*sourceStorename*|Úložiště certifikátů obsahuje aktuální certifikáty, soubory CTL nebo CRL, které lze přidat, odstranit, uložit nebo zobrazit. To může představovat soubor úložiště nebo systémové úložiště.|  
|*destinationNázev*|Výstupní úložiště certifikátů nebo soubor.|  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/přidat**|Přidá certifikáty, soubory CTL a CRL do úložiště certifikátů.|  
|**/vše**|Přidá všechny položky při použití s **/add**. Odstraní všechny položky při použití s **/del**. Zobrazí všechny položky při použití bez možností **/add** nebo **/del.** Možnost **/all** nelze použít s **parametrem /put**.|  
|**/c**|Přidá certifikáty při použití s **/add**. Odstraní certifikáty při použití s **/del**. Uloží certifikáty při použití s **/put**. Zobrazí certifikáty při použití bez možnosti **/add**, **/del**nebo **/put.**|  
|**/CRL**|Přidá seznamy odvolaná vod při použití s **parametrem /add**. Odstraní seznamy CRL při použití s **parametrem /del**. Uloží seznamy CRL při použití s **/put**. Zobrazí seznamy CRL při použití bez možnosti **/add**, **/del**nebo **/put.**|  
|**/CTL**|Přidá ctlpři použití s **/add**. Odstraní ctl při použití s **/del**. Uloží ctls při použití s **/put**. Zobrazí hodnoty CTL při použití bez možnosti **/add**, **/del**nebo **/put.**|  
|**/del**|Odstraní certifikáty, soubory CTL a CRL z úložiště certifikátů.|  
|**/e** *kódovací typ*|Určuje typ kódování certifikátu. Výchozí formát je `X509_ASN_ENCODING`.|  
|**/f** *dwFlags*|Určuje příznak pro otevření úložiště. Jedná se o parametr *dwFlags* předaný **certOpenstore**. Výchozí hodnota je CERT_SYSTEM_STORE_CURRENT_USER. Tato možnost je zvažována pouze v případě, že je použita možnost **/y.**|  
|**/h**[**elp**]|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|**/n** *nam*|Určuje obecný název certifikátu, který se má přidat, odstranit nebo uložit. Tuto možnost lze použít u certifikátů. Nelze ji použít u souborů CTL nebo u CRL.|  
|**/put**|Uloží do souboru certifikát X.509, soubor CTL nebo CRL z úložiště certifikátů. Soubor je uložen ve formátu X.509. Můžete použít **možnost /7** s volbou **/put** k uložení souboru ve formátu PKCS #7. Za parametrem **/put** musí následovat **parametr /c**, **/CTL**nebo **/CRL**. Možnost **/all** nelze použít s **parametrem /put**.|  
|**/r** *umístění*|Určuje umístění registru v rámci systémového úložiště. Tato možnost je zvažována pouze v případě, že zadáte možnost **/s.** *umístění* musí být jedno z následujících:<br /><br /> -   `currentUser`označuje, že úložiště certifikátů je pod HKEY_CURRENT_USER klíčem. Toto nastavení je výchozí.<br />-   `localMachine`označuje, že úložiště certifikátů je pod HKEY_LOCAL_MACHINE klíčem.|  
|**/s**|Určuje, že je úložiště certifikátů systémovým úložištěm. Pokud tuto možnost nezadáte, úložiště se považuje za **soubor StoreFile**.|  
|**/sha1** *sha1Hash*|Určuje hodnotu hash SHA1 certifikátu, souboru CTl nebo CRl, který se má přidat, odstranit nebo uložit.|  
|**/v**|Určuje podrobný režim. Zobrazí detailní informace o certifikátech, souborech CTL a CRL. Tuto možnost nelze použít s možnostmi **/add**, **/del**nebo **/put.**|  
|**/y** *zprostředkovatele*|Určuje název poskytovatele úložiště.|  
|**/7**|Ukládá cílové úložiště jako objekt PKCS #7.|  
|**/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
  
## <a name="remarks"></a>Poznámky  
 Nástroj Certmgr.exe vykonává následující základní funkce:  
  
- Zobrazí certifikáty, soubory CTL a CRL do konzoly.  
  
- Přidá certifikáty, soubory CTL a CRL do úložiště certifikátů.  
  
- Odstraní certifikáty, soubory CTL a CRL z úložiště certifikátů.  
  
- Uloží do souboru certifikát X.509, soubor CTL nebo CRL z úložiště certifikátů.  
  
 Certmgr.exe pracuje se dvěma typy úložišť certifikátů: **StoreFile** a systémové úložiště. Není nutné zadávat typ úložiště certifikátů. Certmgr.exe dokáže rozpoznat typ úložiště a vykonat příslušné operace.  
  
 Spuštěním nástroje Certmgr.exe bez určení jakýchkoli možností dojde ke spuštění modulu snap-in certmgr.msc, který obsahuje uživatelské rozhraní, které pomáhá s úlohami správy certifikátů, které jsou dostupné také z příkazového řádku. Uživatelské rozhraní poskytuje průvodce importováním, který zkopíruje certifikáty, soubory CTL a CRL z disku do úložiště certifikátů.  
  
 Názvy úložišť X509Certificate pro `sourceStorename` parametry a `destinationStorename` můžete najít kompilací a spuštěním následujícího kódu.  
  
 [!code-csharp[Tools.CertMgr#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tools.certmgr/cs/storenames1.cs#1)]
 [!code-vb[Tools.CertMgr#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tools.certmgr/vb/storenames1.vb#1)]  
  
 Další informace o certifikátech naleznete v [tématu Práce s certifikáty](../wcf/feature-details/working-with-certificates.md).  
  
## <a name="examples"></a>Příklady  
 Následující příkaz zobrazí výchozí systémové `my` úložiště s názvem s podrobným výstupem.  
  
```console  
certmgr /v /s my  
```  
  
 Následující příkaz přidá všechny certifikáty v `myFile.ext` souboru volaný do nového souboru s názvem `newFile.ext`.  
  
```console  
certmgr /add /all /c myFile.ext newFile.ext  
```  
  
 Následující příkaz přidá certifikát v `testcert.cer` souboru `my` pojmenovaném do systémového úložiště.  
  
```console  
certmgr /add /c testcert.cer /s my  
```  
  
 Následující příkaz přidá certifikát v `TrustedCert.cer` souboru pojmenovaném do kořenového úložiště certifikátů.  
  
```console  
certmgr /c /add TrustedCert.cer /s root  
```  
  
 Následující příkaz uloží certifikát s běžným `myCert` `my` názvem v systémovém `newCert.cer`úložišti do souboru s názvem .  
  
```console  
certmgr /add /c /n myCert /s my newCert.cer  
```  
  
 Následující příkaz odstraní všechny seznamy `my` CTL v systémovém úložišti a `newStore.str`uloží výsledné úložiště do souboru s názvem .  
  
```console  
certmgr /del /all /ctl /s my newStore.str  
```  
  
 Následující příkaz uloží certifikát do `my` systémového úložiště `newFile`v souboru . Budete vyzváni k zadání čísla `my` certifikátu `newFile`z do .  
  
```console  
certmgr /put /c /s my newFile  
```  
  
## <a name="see-also"></a>Viz také

- [Nástroje](index.md)
- [Makecert.exe (Nástroj pro vytváření certifikátů)](/windows/desktop/SecCrypto/makecert)
- [Příkazové řádky](developer-command-prompt-for-vs.md)
