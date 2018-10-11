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
ms.openlocfilehash: 0a4cb3f126a51d6bf7027edb88b8fec74c6785d2
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/11/2018
ms.locfileid: "49086319"
---
# <a name="certmgrexe-certificate-manager-tool"></a>Certmgr.exe (nástroj Certificate Manager)
Nástroj Správce certifikátů (Certmgr.exe) spravuje certifikáty, seznamy důvěryhodných certifikátů (CTL) a seznamy odvolaných certifikátů (CRL).  
  
 Správce certifikátů je automaticky nainstalován při instalaci sady Visual Studio. Chcete-li spustit nástroj, použijte [příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
> [!NOTE]
>  Správce certifikátů (Certmgr.exe) je nástroj příkazového řádku, zatímco Certifikáty (Certmgr.msc) jsou modulem snap-in konzoly MMC (Microsoft Management Console). Protože Certmgr.msc obvykle nachází v adresáři systému Windows, zadávání `certmgr` na příkazovém řádku se může načíst modul snap-in Certifikáty konzoly MMC i v případě, že máte otevřený příkazový řádek sady Visual Studio. K tomuto případu může dojít, protože cesta k modulu snap-in předchází cestě nástroje Správce certifikátů v proměnné prostředí PATH. Setkáte-li se s tímto problémem, můžete zadáním cesty ke spustitelnému souboru spustit příkazy Certmgr.exe.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li spustit tento nástroj, použijte příkazový řádek vývojáře (nebo příkazový řádek Visual Studio v systému Windows 7). Další informace najdete v tématu [příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 Přehled certifikátů X.509 naleznete v tématu [Working with Certificates](../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```  
      certmgr [/add | /del | /put] [options]  
[/s[/r registryLocation]] [sourceStorename]  
[/s[/r registryLocation]] [destinationStorename]  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Argument|Popis|  
|--------------|-----------------|  
|*sourceStorename*|Úložiště certifikátů obsahuje aktuální certifikáty, soubory CTL nebo CRL, které lze přidat, odstranit, uložit nebo zobrazit. To může představovat soubor úložiště nebo systémové úložiště.|  
|*destinationStorename*|Výstupní úložiště certifikátů nebo soubor.|  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/ add**|Přidá certifikáty, soubory CTL a CRL do úložiště certifikátů.|  
|**/ all**|Přidá všechny záznamy zadáním možnosti **/ add**. Odstraní všechny záznamy zadáním možnosti **/del**. Zobrazí všechny záznamy zadáním bez **/ add** nebo **/del** možnosti. **/All** možnost nelze použít s **/put**.|  
|**/c**|Přidá certifikáty zadáním **/ add**. Odstraní certifikáty zadáním **/del**. Uloží certifikáty zadáním **/put**. Zobrazí certifikáty při použití bez **/ add**, **/del**, nebo **/put** možnost.|  
|**/ CRL**|Přidá soubory CRL zadáním pomocí možnosti **/ add**. Odstraní soubory CRL zadáním pomocí možnosti **/del**. Uloží soubory CRL zadáním pomocí možnosti **/put**. Zobrazí soubory CRL zadáním bez možnosti **/ add**, **/del**, nebo **/put** možnost.|  
|**/ CTL**|Přidá soubory CTL zadáním **/ add**. Odstraní soubory CTL zadáním **/del**. Uloží soubory CTL zadáním **/put**. Zobrazí soubory CTL zadáním bez **/ add**, **/del**, nebo **/put** možnost.|  
|**/ del**|Odstraní certifikáty, soubory CTL a CRL z úložiště certifikátů.|  
|**/e** *encodingType*|Určuje typ kódování certifikátu. Výchozí hodnota je `X509_ASN_ENCODING`.|  
|**/f** *dwFlags*|Určuje příznak pro otevření úložiště. Toto je *dwFlags* byl předán parametr **CertOpenStore**. Výchozí hodnota je CERT_SYSTEM_STORE_CURRENT_USER. Tato možnost je zvážena pouze v případě, **/y** možnost se používá.|  
|**/h**[**elp**]|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|**/n** *název*|Určuje obecný název certifikátu, který se má přidat, odstranit nebo uložit. Tuto možnost lze použít u certifikátů. Nelze ji použít u souborů CTL nebo u CRL.|  
|**/ put**|Uloží do souboru certifikát X.509, soubor CTL nebo CRL z úložiště certifikátů. Soubor je uložen ve formátu X.509. Můžete použít **/7** spolu s možností **/put** uložit soubor ve formátu PKCS #7. **/Put** možnost musí být následována buď **/c**, **/CTL**, nebo **/CRL**. **/All** možnost nelze použít s **/put**.|  
|**/r** *umístění*|Určuje umístění registru v rámci systémového úložiště. Tato možnost je zvážena pouze v případě, že zadáte **/s** možnost. *umístění* musí být jedna z následujících akcí:<br /><br /> -   `currentUser` Označuje, že se úložiště certifikátů nachází pod klíčem HKEY_CURRENT_USER. Toto nastavení je výchozí.<br />-   `localMachine` Označuje, že se úložiště certifikátů nachází pod klíčem HKEY_LOCAL_MACHINE.|  
|**/s**|Určuje, že je úložiště certifikátů systémovým úložištěm. Pokud tuto možnost nezadáte, bude považován za úložiště **StoreFile**.|  
|**/SHA1** *sha1Hash*|Určuje hodnotu hash SHA1 certifikátu, souboru CTl nebo CRl, který se má přidat, odstranit nebo uložit.|  
|**/v**|Určuje podrobný režim. Zobrazí detailní informace o certifikátech, souborech CTL a CRL. Tento parametr nelze použít s **/ add**, **/del**, nebo **/put** možnosti.|  
|**/y** *zprostředkovatele*|Určuje název poskytovatele úložiště.|  
|**/7**|Ukládá cílové úložiště jako objekt PKCS #7.|  
|**/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
  
## <a name="remarks"></a>Poznámky  
 Nástroj Certmgr.exe vykonává následující základní funkce:  
  
-   Zobrazí certifikáty, soubory CTL a CRL do konzoly.  
  
-   Přidá certifikáty, soubory CTL a CRL do úložiště certifikátů.  
  
-   Odstraní certifikáty, soubory CTL a CRL z úložiště certifikátů.  
  
-   Uloží do souboru certifikát X.509, soubor CTL nebo CRL z úložiště certifikátů.  
  
 Certmgr.exe pracuje se dvěma typy úložišť certifikátů: **StoreFile** a systémové úložiště. Není nutné zadávat typ úložiště certifikátů. Certmgr.exe dokáže rozpoznat typ úložiště a vykonat příslušné operace.  
  
 Spuštěním nástroje Certmgr.exe bez určení jakýchkoli možností dojde ke spuštění modulu snap-in certmgr.msc, který obsahuje uživatelské rozhraní, které pomáhá s úlohami správy certifikátů, které jsou dostupné také z příkazového řádku. Uživatelské rozhraní poskytuje průvodce importováním, který zkopíruje certifikáty, soubory CTL a CRL z disku do úložiště certifikátů.  
  
 Název úložiště certifikátu x 509 pro můžete najít `sourceStorename` a `destinationStorename` parametry zkompilováním a spuštěním následujícího kódu.  
  
 [!code-csharp[Tools.CertMgr#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tools.certmgr/cs/storenames1.cs#1)]
 [!code-vb[Tools.CertMgr#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tools.certmgr/vb/storenames1.vb#1)]  
  
 Další informace o certifikátech najdete v tématu [Working with Certificates](../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## <a name="examples"></a>Příklady  
 Následující příkaz zobrazí výchozí systémové úložiště s názvem `my` s podrobným výstupem.  
  
```  
certmgr /v /s my  
```  
  
 Následující příkaz přidá všechny certifikáty do souboru s názvem `myFile.ext` nový soubor s názvem `newFile.ext`.  
  
```  
certmgr /add /all /c myFile.ext newFile.ext  
```  
  
 Následující příkaz přidá certifikát do souboru s názvem `testcert.cer` k `my` systémového úložiště.  
  
```  
certmgr /add /c testcert.cer /s my  
```  
  
 Následující příkaz přidá certifikát do souboru s názvem `TrustedCert.cer` do kořenového úložiště certifikátů.  
  
```  
certmgr /c /add TrustedCert.cer /s root  
```  
  
 Následující příkaz uloží certifikát s běžným názvem `myCert` v `my` názvem systémového úložiště do souboru `newCert.cer`.  
  
```  
certmgr /add /c /n myCert /s my newCert.cer  
```  
  
 Následující příkaz odstraní všechny soubory CTL `my` úložiště systému a uloží výsledné úložiště do souboru volá `newStore.str`.  
  
```  
certmgr /del /all /ctl /s my newStore.str  
```  
  
 Následující příkaz uloží certifikát do `my` systémového úložiště v souboru `newFile`. Zobrazí se výzva k zadání číslo certifikátu z `my` vložit `newFile`.  
  
```  
certmgr /put /c /s my newFile  
```  
  
## <a name="see-also"></a>Viz také  
 [Nástroje](../../../docs/framework/tools/index.md)  
 [MakeCert.exe (nástroj pro vytvoření certifikátu)](https://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d)  
 [Příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
