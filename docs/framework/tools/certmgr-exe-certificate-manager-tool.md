---
title: "Certmgr.exe (nástroj Certificate Manager)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "27"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9612603642a38083aba30c1c6dc931031d1d04e8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="certmgrexe-certificate-manager-tool"></a>Certmgr.exe (nástroj Certificate Manager)
Nástroj Správce certifikátů (Certmgr.exe) spravuje certifikáty, seznamy důvěryhodných certifikátů (CTL) a seznamy odvolaných certifikátů (CRL).  
  
 Správce certifikátů je automaticky nainstalován při instalaci sady Visual Studio. Spusťte nástroj pomocí [příkazového řádku](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
> [!NOTE]
>  Správce certifikátů (Certmgr.exe) je nástroj příkazového řádku, zatímco Certifikáty (Certmgr.msc) jsou modulem snap-in konzoly MMC (Microsoft Management Console). Protože Certmgr.msc je obvykle najde v adresáři systému Windows, zadávání `certmgr` na příkazovém řádku může načíst modul snap-in Certifikáty konzoly MMC i v případě, že máte otevřený příkazový řádek sady Visual Studio. K tomuto případu může dojít, protože cesta k modulu snap-in předchází cestě nástroje Správce certifikátů v proměnné prostředí PATH. Setkáte-li se s tímto problémem, můžete zadáním cesty ke spustitelnému souboru spustit příkazy Certmgr.exe.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li spustit tento nástroj, použijte příkazový řádek vývojáře (nebo příkazový řádek Visual Studio v systému Windows 7). Další informace najdete v tématu [příkazového řádku](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 Přehled certifikátů X.509 najdete v tématu [práce s certifikáty](../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
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
|**/ all**|Přidá všechny položky při použití s **/ add**. Umožňuje odstranit všechny položky při použití s **/del**. Zobrazí všechny položky při použití bez **/ add** nebo **/del** možnosti. **Nebo všechny** možnost nelze použít s **/put**.|  
|**/c**|Přidá certifikáty při použití s **/ add**. Odstraní certifikáty při použití s **/del**. Uloží certifikáty při použití s **/put**. Zobrazí certifikáty při použití bez **/ add**, **/del**, nebo **/put** možnost.|  
|**NEBO SEZNAMU ODVOLANÝCH CERTIFIKÁTŮ**|Přidá seznamy CRL při použití s **/ add**. Odstraní seznamy CRL při použití s **/del**. Uloží seznamy CRL při použití s **/put**. Zobrazí seznamy CRL při použití bez **/ add**, **/del**, nebo **/put** možnost.|  
|**/ CTL**|Přidá seznamy CTL při použití s **/ add**. Odstraní seznamy CTL při použití s **/del**. Uloží seznamy CTL při použití s **/put**. Zobrazí seznamy CTL při použití bez **/ add**, **/del**, nebo **/put** možnost.|  
|**/ del**|Odstraní certifikáty, soubory CTL a CRL z úložiště certifikátů.|  
|**/e** *encodingType*|Určuje typ kódování certifikátu. Výchozí hodnota je `X509_ASN_ENCODING`.|  
|**/f** *dwFlags*|Určuje příznak pro otevření úložiště. Toto je *dwFlags* byl předán parametr **příkaz CertOpenStore**. Výchozí hodnota je CERT_SYSTEM_STORE_CURRENT_USER. Tato možnost je považován za pouze, pokud **/y** možnost se používá.|  
|**/h**[**nápovědu**]|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|**/n***osoby*|Určuje obecný název certifikátu, který se má přidat, odstranit nebo uložit. Tuto možnost lze použít u certifikátů. Nelze ji použít u souborů CTL nebo u CRL.|  
|**/ Vložení**|Uloží do souboru certifikát X.509, soubor CTL nebo CRL z úložiště certifikátů. Soubor je uložen ve formátu X.509. Můžete použít **/7** možnost s **/put** možnost uložení souboru ve formátu PKCS #7. **/Put** možnost musí být následováno buď **/c**, **/CTL**, nebo **/CRL**. **Nebo všechny** možnost nelze použít s **/put**.|  
|**/r** *umístění*|Určuje umístění registru v rámci systémového úložiště. Tato možnost je považován za pouze v případě, že zadáte **/s** možnost. *umístění* musí mít jednu z následujících akcí:<br /><br /> -   `currentUser`Označuje, že úložiště certifikátů je pod klíčem HKEY_CURRENT_USER. Toto nastavení je výchozí.<br />-   `localMachine`Označuje, že úložiště certifikátů je pod klíčem HKEY_LOCAL_MACHINE.|  
|**/s**|Určuje, že je úložiště certifikátů systémovým úložištěm. Pokud nezadáte tuto možnost, se považuje za úložiště **StoreFile**.|  
|**/SHA1** *sha1Hash*|Určuje hodnotu hash SHA1 certifikátu, souboru CTl nebo CRl, který se má přidat, odstranit nebo uložit.|  
|**/v**|Určuje podrobný režim. Zobrazí detailní informace o certifikátech, souborech CTL a CRL. Tuto možnost nelze použít s **/ add**, **/del**, nebo **/put** možnosti.|  
|**/y** *zprostředkovatele*|Určuje název poskytovatele úložiště.|  
|**/7**|Ukládá cílové úložiště jako objekt PKCS #7.|  
|**/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
  
## <a name="remarks"></a>Poznámky  
 Nástroj Certmgr.exe vykonává následující základní funkce:  
  
-   Zobrazí certifikáty, soubory CTL a CRL do konzoly.  
  
-   Přidá certifikáty, soubory CTL a CRL do úložiště certifikátů.  
  
-   Odstraní certifikáty, soubory CTL a CRL z úložiště certifikátů.  
  
-   Uloží do souboru certifikát X.509, soubor CTL nebo CRL z úložiště certifikátů.  
  
 Certmgr.exe funguje s dva typy úložišť certifikátů: **StoreFile** a úložiště systému. Není nutné zadávat typ úložiště certifikátů. Certmgr.exe dokáže rozpoznat typ úložiště a vykonat příslušné operace.  
  
 Spuštěním nástroje Certmgr.exe bez určení jakýchkoli možností dojde ke spuštění modulu snap-in certmgr.msc, který obsahuje uživatelské rozhraní, které pomáhá s úlohami správy certifikátů, které jsou dostupné také z příkazového řádku. Uživatelské rozhraní poskytuje průvodce importováním, který zkopíruje certifikáty, soubory CTL a CRL z disku do úložiště certifikátů.  
  
 Názvy úložiště certifikátu x 509 pro můžete najít `sourceStorename` a `destinationStorename` parametry kompilování a spuštěním následující kód.  
  
 [!code-csharp[Tools.CertMgr#1](../../../samples/snippets/csharp/VS_Snippets_CLR/tools.certmgr/cs/storenames1.cs#1)]
 [!code-vb[Tools.CertMgr#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/tools.certmgr/vb/storenames1.vb#1)]  
  
 Další informace o certifikátech najdete v tématu [práce s certifikáty](../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
## <a name="examples"></a>Příklady  
 Následující příkaz zobrazí výchozí úložiště systému, který volá `my` s podrobným výstupem.  
  
```  
certmgr /v /s my  
```  
  
 Následující příkaz přidá všechny certifikáty v souboru s názvem `myFile.ext` nový soubor s názvem `newFile.ext`.  
  
```  
certmgr /add /all /c myFile.ext newFile.ext  
```  
  
 Následující příkaz přidá certifikát do souboru s názvem `testcert.cer` k `my` úložiště systému.  
  
```  
certmgr /add /c testcert.cer /s my  
```  
  
 Následující příkaz přidá certifikát do souboru s názvem `TrustedCert.cer` do kořenového úložiště certifikátů.  
  
```  
certmgr /c /add TrustedCert.cer /s root  
```  
  
 Následující příkaz uloží certifikát s běžným názvem `myCert` v `my` volá úložiště systému do souboru `newCert.cer`.  
  
```  
certmgr /add /c /n myCert /s my newCert.cer  
```  
  
 Následující příkaz odstraní všechny seznamy CTL v `my` úložiště systému a uloží výsledné úložiště do souboru názvem `newStore.str`.  
  
```  
certmgr /del /all /ctl /s my newStore.str  
```  
  
 Následující příkaz uloží v certifikát `my` úložiště systému v souboru `newFile`. Zobrazí se výzva k zadání číslo certifikátu z `my` uvést do `newFile`.  
  
```  
certmgr /put /c /s my newFile  
```  
  
## <a name="see-also"></a>Viz také  
 [Nástroje](../../../docs/framework/tools/index.md)  
 [MakeCert.exe (nástroj pro vytvoření certifikátu)](http://msdn.microsoft.com/library/b0343f8e-9c41-4852-a85c-f8a0c408cf0d)  
 [Příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
