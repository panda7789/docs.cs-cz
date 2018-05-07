---
title: Mage.exe (generování manifestu a nástroj pro úpravy)
ms.date: 03/30/2017
helpviewer_keywords:
- Manifest Generation and Editing tool
- Mage.exe
ms.assetid: 77dfe576-2962-407e-af13-82255df725a1
ms.openlocfilehash: 551173a7ed8d60ca1870159cd7e533720275bd20
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="mageexe-manifest-generation-and-editing-tool"></a>Mage.exe (generování manifestu a nástroj pro úpravy)
Nástroj pro generování a úpravy manifestu (Mage.exe) je nástroj příkazového řádku podporující vytváření a úpravy manifestů aplikací a nasazení. Nástroj příkazového řádku, Mage.exe lze spustit z dávkové skripty a další aplikace pro systém Windows, včetně [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] aplikace.  
  
 Namísto nástroje Mage.exe lze také použít jeho grafickou aplikaci MageUI.exe. Další informace najdete v tématu [MageUI.exe (generování manifestu a nástroj pro úpravy, grafický klient)](../../../docs/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md).  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li spustit tento nástroj, použijte příkazový řádek vývojáře (nebo příkazový řádek Visual Studio v systému Windows 7). Další informace najdete v tématu [příkazového řádku](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 Dvě verze Mage.exe a MageUI.exe jsou zahrnuty jako součást sady [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)] instalační program. Pokud chcete zobrazit informace o verzi, spusťte MageUI.exe, vyberte **pomoci**a vyberte **o**. Tato dokumentace popisuje verzi 4.0.x.x nástrojů Mage.exe a MageUI.exe.  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```  
Mage [commands] [commandOptions]  
```  
  
#### <a name="parameters"></a>Parametry  
 Následující tabulka ukazuje příkazy podporované nástrojem Mage.exe. Další informace o možnostech nepodporuje těchto příkazů najdete v tématu [nové a možnosti příkazu aktualizace](#NewUpdate) a [parametry příkazu přihlašovací](#Sign).  
  
|Příkaz|Popis|  
|-------------|-----------------|  
|**-cc, ClearApplicationCache**|Odstraní všechny aplikace fungující pouze v režimu online z mezipaměti stažených aplikací.|  
|**-n, - nové** *typ souboru [newOptions]*|Vytvoří nový soubor daného typu. Platnými typy jsou:<br /><br /> -   `Deployment`: Vytvoří nové nasazení manifestu.<br />-   `Application`: Vytvoří nové manifest aplikace.<br /><br /> Nezadáte-li s tímto příkazem žádné další parametry, bude vytvořen soubor odpovídajícího typu s odpovídajícími výchozími značkami a hodnotami atributů.<br /><br /> Použití **- ToFile** možnost (viz následující tabulka) a zadat název souboru a cesta k souboru nové.<br /><br /> Použití **- FromDirectory** možnost (viz následující tabulka) k vytvoření manifest aplikace se všemi sestavení pro aplikaci přidat do \<závislostí > oddílu manifest.|  
|**-u,-aktualizace** *[filePath] [volby pro aktualizaci]*|Provede jednu nebo více změn souboru manifestu. Typ upravovaného souboru není třeba zadávat. Nástroj Mage.exe soubor zkontroluje sadou heuristik a určí, zda jde o manifest nasazení nebo manifest aplikace.<br /><br /> Pokud jste se zaregistrovali již soubor s certifikátem, **-aktualizace** bude odeberte blok signatury klíč. Důvodem je skutečnost, že podpis klíče obsahuje hodnotu hash souboru, která je úpravou souboru zneplatněna.<br /><br /> Použití **- ToFile** možnost (viz následující tabulka) a zadat nový název souboru a cesta místo přepsal existující soubor.|  
|**-s,-přihlášení** `[signOptions]`|Použije k podpisu souboru pár klíčů nebo certifikát X509. Podpisy jsou do souboru vloženy jako prvky jazyka XML.<br /><br /> Musíte být připojeni k Internetu při podepsání manifestu, který určuje **- TimestampUri** hodnotu.|  
|**-h,-?, - pomoci** *[verbose]*|Popíše všechny dostupné příkazy a jejich možnosti. Zadejte `verbose` podrobnou nápovědu.|  
  
<a name="NewUpdate"></a>   
## <a name="new-and-update-command-options"></a>Možnosti příkazů New a Update  
 V následující tabulce jsou uvedeny možnosti podporované `-New` a `-Update` příkazy.  
  
|Možnosti|Výchozí hodnota|Platí pro|Popis|  
|-------------|-------------------|----------------|-----------------|  
|**-a, – algoritmus**|sha1RSA|Manifesty aplikací.<br /><br /> Manifesty nasazení.|Určí algoritmus, jímž budou generovány přehledy závislostí. Hodnotou musí být „sha256RSA“ nebo „sha1RSA“.<br /><br /> Použijte s možností „-Update“. Při použití možnosti „-Sign“ je tato možnost ignorována.|  
|**-appc, - AppCodeBase** `manifestReference`||Manifesty nasazení.|Vloží odkaz na adresu URL nebo cestu k souboru do souboru manifestu aplikace. Touto hodnotou musí být úplná cesta k manifestu aplikace.|  
|**-appm, - AppManifest** `manifestPath`||Manifesty nasazení.|Vloží do manifestu nasazení odkaz na manifest aplikace tohoto nasazení.<br /><br /> Soubor indikován `manifestPath` musí existovat nebo Mage.exe dojde k chybě. Pokud soubor odkazuje `manifestPath` není aplikace manifestu, Mage.exe dojde k chybě.|  
|**-CR, - Soubor_certifikátu** `filePath`||Všechny typy souborů.|Určí umístění digitálního certifikátu X509 pro podpis manifestu. Tuto možnost lze použít ve spojení s **-heslo** možnost, pokud certifikát vyžaduje heslo.|  
|**-ch, - CertHash** `hashSignature`||Všechny typy souborů.|Hodnota hash digitálního certifikátu uloženého v úložišti osobních certifikátů klientského počítače. Ta odpovídá řetězci kryptografického otisku digitálního certifikátu zobrazeného v Konzole certifikátů systému Windows.<br /><br /> `hashSignature` může být buď velká nebo malá písmena a můžete je nutné zadat buď jako jeden řetězec, nebo s každou octet kryptografický otisk oddělených prostory a celý kryptografický otisk uzavřena v uvozovkách.|  
|**-fd, - FromDirectory** `directoryPath`||Manifesty aplikací.|Naplní manifest aplikace pomocí popisy všech sestavení a soubory, které jsou v `directoryPath`, včetně všechny podadresáře, kde `directoryPath` je adresář, který obsahuje aplikace, která chcete nasadit. Pro každý soubor v adresáři se nástroj Mage.exe rozhodne, zda jde o sestavení nebo o statický soubor. Pokud je sestavení, přidá `<dependency>` značky a `installFrom` atribut název sestavení, základu kódu a verzi aplikace. Pokud je statický soubor, přidá `<file>` značky. Nástroj Mage.exe také použije jednoduchou sadu heuristik a zjistí hlavní spustitelný soubor aplikace, který poté v manifestu označí jako vstupní bod aplikace ClickOnce.<br /><br /> Nástroj Mage.exe nikdy automaticky neoznačí soubor jako datový. To je zapotřebí provést ručně. Další informace najdete v tématu [postupy: zahrnutí datového souboru v aplikaci ClickOnce](/visualstudio/deployment/how-to-include-a-data-file-in-a-clickonce-application).<br /><br /> Nástroj Mage.exe také pro každý soubor vygeneruje hodnotu hash dle jeho velikosti. Technologie ClickOnce těmito hodnotami hash zajišťuje, že se soubory nasazení nikdo od vytvoření manifestu nemanipuloval. Pokud některý ze souborů ve vašem nasazení změnit, můžete spustit Mage.exe s **-aktualizovat** příkaz a **- FromDirectory** možnost ale bude aktualizovat hodnoty hash a verze sestavení všechny odkazované souborů.<br /><br /> **-FromDirectory** bude obsahovat všechny soubory v všechny podadresáře v rámci nalezen `directoryPath`.<br /><br /> Pokud používáte **- FromDirectory** s **-aktualizace** příkaz Mage.exe budou odebrány všechny soubory v manifestu aplikace, které v adresáři už existují.|  
|**-Pokud - IconFile**  `filePath`||Manifesty aplikací.|Určí úplnou cestu k souboru ikony .ICO. Tato ikona se zobrazuje vedle názvu aplikace v nabídce Start a v jejím záznamu v ovládacím panelu Přidat nebo odebrat programy. Není-li zadána žádná ikona, je použita ikona výchozí.|  
|**-IP adresy, - IncludeProviderURL**  `url`|true|Manifesty nasazení.|Určuje, zda manifest nasazení obsahuje aktualizace umístění hodnoty nastavené **- ProviderURL**.|  
|**-i,-instalace** `willInstall`|true|Manifesty nasazení.|Označuje, zda by aplikace ClickOnce měla být nainstalována na místní počítač nebo spuštěna z webu. Instalace aplikace poskytuje tuto aplikaci přítomnosti v systému Windows **spustit** nabídky. Platnými hodnotami jsou „true“ nebo „t“ a „false“ nebo „f“.<br /><br /> Pokud zadáte **- MinVersion** možnost a uživatel má verzi menší než **- MinVersion** nainstalovaná, vynutí aplikaci pro instalaci, bez ohledu na hodnotu, která je předat do **- Nainstalujte**.<br /><br /> Tuto možnost nelze použít s **- BrowserHosted** možnost. Pokus zadat obě možnosti pro stejný manifest vyústí v chybu.|  
|**-více hodnot, - MinVersion**  `[version]`|Verze uvedené v manifestu nasazení ClickOnce podle specifikace **-verze** příznak.|Manifesty nasazení.|Minimální verze aplikace, kterou uživatel může spustit. Tento příznak učiní pojmenovanou verzi aplikace požadovanou aktualizací. Vydáte-li verzi produktu s aktualizací proti narušující změně nebo závažné bezpečnostní chybě, lze pomocí tohoto příznaku určit, že aktualizace musí být nainstalována a že uživatel nemůže nadále používat dřívější verze.<br /><br /> `version` má stejnou sémantiku jako argument **-verze** příznak.|  
|**-n, – název** `nameString`|Nasazení|Všechny typy souborů.|Název použitý pro identifikaci aplikace. ClickOnce název bude použit k identifikaci aplikace **spustit** nabídky (Pokud je aplikace nastavena k instalaci sám sebe) a v dialogových oknech zvýšení oprávnění. **Poznámka:** Pokud aktualizujete stávající manifest a tato možnost nezadáte název vydavatele, Mage.exe aktualizuje manifest název organizace, které jsou definované v počítači. Chcete-li použít jiný název, použijte tuto možnost a zadejte požadovaný název vydavatele.|  
|**-pwd,-heslo** `passwd`||Všechny typy souborů.|Heslo použité pro podepsání manifestu digitálním certifikátem. Musí použít ve spojení s **- Soubor_certifikátu** možnost.|  
|**Procesor -p,** `processorValue`|Msil|Manifesty aplikací.<br /><br /> Manifesty nasazení.|Architektura mikroprocesoru, na níž bude distribuce spouštěna. Tato hodnota je vyžadována, pokud připravujete jednu nebo více instalací, jejichž sestavení byla předkompilována pro určitý mikroprocesor. Platné hodnoty patří `msil`, `x86`, `ia64`, a `amd64`. `msil` je Microsoft zprostředkující jazyka, což znamená, že všechny vaše sestavení jsou nezávislé na platformě a modul CLR (CLR) bude za běhu kompilovat při prvním spuštění je vaše aplikace.|  
|**-celofiremnímu,** **- ProviderURL** `url`||Manifesty nasazení.|Určuje adresu URL, na které technologie ClickOnce vyhledá aktualizace aplikace.|  
|**-pub,-vydavatele** `publisherName`||Manifesty aplikací.<br /><br /> Manifesty nasazení.|Přidá název vydavatele do prvku popisu v manifestu nasazení nebo manifestu aplikace. Pokud se používá na manifest aplikace **- UseManifestForTrust** musí být zadaná také s hodnotou "true" nebo "t"; jinak hodnota tohoto parametru vyvolá chybu.|  
|**-s, - SupportURL**  `url`||Manifesty aplikací.<br /><br /> Manifesty nasazení.|Určí odkaz, který se pro aplikaci ClickOnce objeví v ovládacím panelu Přidat nebo odebrat programy.|  
|**-ti, - TimestampUri** `uri`||Manifesty aplikací.<br /><br /> Manifesty nasazení.|Adresa URL služby vytváření digitálního časového razítka. Vytvoření časového razítka v manifestu umožňuje vyhnout se nutnosti znovu manifesty podepsat, pokud by digitální certifikát vypršel ještě před nasazením další verze aplikace. Další informace najdete v tématu [Windows root programu Certificate](http://go.microsoft.com/fwlink/?LinkId=159000).|  
|**-t, - ToFile** `filePath`|-Nové:<br />-Nasazení: deploy.application<br />-Aplikace: application.exe.manifest<br />-Aktualizace:<br />-Vstupní soubor.|Všechny typy souborů.|Určí výstupní cestu vytvořeného nebo upraveného souboru.<br /><br /> Pokud **- ToFile** se nedodává při použití **-nové**, je výstup zapsán do aktuální pracovní adresář. Pokud **- ToFile** se nedodává při použití **-aktualizace**, Mage.exe zapíše soubor zpět do vstupní soubor.|  
|**-tr, - TrustLevel** `level`|Dle zóny, v níž se adresa URL aplikace nachází.|Manifesty aplikací.|Úroveň důvěryhodnosti, která bude aplikacím udělena na klientských počítačích. Mezi hodnoty patří „Internet“, „Intranet“ a „FullTrust“.|  
|**-ální, - UseManifestForTrust** `willUseForTrust`|False|Manifesty aplikací.|Určí, zda bude při spuštění aplikace na klientském počítači použit pro rozhodování o důvěryhodnosti digitální podpis manifestu aplikace. Hodnota „true“ nebo „t“ určí, že pro rozhodnutí o důvěryhodnosti bude použit manifest aplikace. Hodnota „false“ nebo „f“ určí, že bude použit podpis manifestu nasazení.|  
|**-v,-verze** `versionNumber`|1.0.0.0|Manifesty aplikací.<br /><br /> Manifesty nasazení.|Verze nasazení. Argument musí být platný řetězec verze ve formátu "*N.N.N.N*", kde"*N*" 32bitové celé číslo bez znaménka.|  
|**-wpf, - WPFBrowserApp**  `isWPFApp`|false|Manifesty aplikací.<br /><br /> Manifesty nasazení.|Tento příznak použijte pouze tehdy, je-li aplikace aplikací Windows Presentation Foundation (WPF), která bude hostována v aplikaci Internet Explorer a není samostatně spustitelná. Platnými hodnotami jsou „true“ nebo „t“ a „false“ nebo „f“.<br /><br /> Manifesty aplikace vloží `hostInBrowser` atribut pod `entryPoint` element manifestu aplikace.<br /><br /> Manifesty nasazení, nastaví `install` atributu u `deployment` element na hodnotu false a uloží manifest nasazení s příponou .xbap. Zadáním tohoto argumentu spolu s **-nainstalovat** argument vytvoří chybu, protože aplikace hostované prohlížečem nesmí být offline, nainstalované aplikace.|  
  
<a name="Sign"></a>   
## <a name="sign-command-options"></a>Možnosti příkazu Sign  
 V následující tabulce jsou uvedeny možnosti podporované `-Sign` příkaz, který platí pro všechny typy souborů.  
  
|Možnosti|Popis|  
|-------------|-----------------|  
|**-CR, - Soubor_certifikátu** `filePath`|Určí umístění digitálního certifikátu pro podpis manifestu. Tuto možnost lze použít ve spojení s **-heslo** možnost.|  
|**-ch, - CertHash** `hashSignature`|Hodnota hash digitálního certifikátu uloženého v úložišti osobních certifikátů klientského počítače. Ta odpovídá vlastnosti kryptografického otisku digitálního certifikátu zobrazeného v Konzole certifikátů systému Windows.<br /><br /> `hashSignature` může být buď velká nebo malá písmena a můžete je nutné zadat buď jako jeden řetězec, nebo s každou octet kryptografický otisk oddělených prostory a celý kryptografický otisk uzavřena v uvozovkách.|  
|**-pwd,-heslo** `passwd`|Heslo použité pro podepsání manifestu digitálním certifikátem. Musí použít ve spojení s **- Soubor_certifikátu** možnost.|  
|**-t, - ToFile** `filePath`|Určí výstupní cestu vytvořeného nebo upraveného souboru.|  
  
## <a name="remarks"></a>Poznámky  
 Žádný argument nástroje Mage.exe nerozlišuje velká a malá písmena. Příkazy a možnosti mohou mít předponu pomlčky (-) nebo lomítka (/).  
  
 Všechny argumenty použít s **-přihlašovací** příkaz lze použít kdykoli bez **-nové** nebo **-aktualizace** také příkazy. Následující příkazy jsou ekvivalentní.  
  
```  
mage -Sign c:\HelloWorldDeployment\HelloWorld.deploy -CertFile cert.pfx  
mage -Update c:\HelloWorldDeployment\HelloWorld.deploy -CertFile cert.pfx  
```  
  
> [!NOTE]
>  Od verze rozhraní .NET Framework verze 4.6.2, CNG certifikáty jsou také podporovány.  
  
 Podpis by měl být poslední provedený úkol, protože podepsaný dokument používá hodnotu hash souboru pro ověření, zda je podpis pro dokument platný. Provedete-li v podepsaném souboru nějaké změny, je zapotřebí soubor znovu podepsat. Podepíšete-li dříve podepsaný dokument, nástroj Mage.exe přepíše starý podpis novým.  
  
 Při použití **- AppManifest** možnost k naplnění manifest nasazení, Mage.exe bude předpokládat, že manifest aplikace se bude nacházet ve stejném adresáři jako nasazení manifestu v podadresáři s názvem po aktuálním nasazení verze a bude odpovídajícím způsobem nakonfigurovat manifestu nasazení. Pokud manifest aplikace se bude nacházet jinde, použijte **- AppCodeBase** nastavit alternativní umístění.  
  
 Před nasazením aplikace musí být manifesty nasazení a aplikace podepsány. Informace o podepisování manifestů, najdete v části [Přehled nasazení důvěryhodných aplikací](/visualstudio/deployment/trusted-application-deployment-overview).  
  
 **- TrustLevel** možnost pro manifesty aplikace popisuje sadu oprávnění aplikace vyžaduje ke spuštění v klientském počítači. Ve výchozím nastavení, aplikace přiřazené úroveň důvěryhodnosti na základě *zóny* ve kterém se nachází jejich adresy URL. Aplikace nasazené přes podnikovou síť jsou obecně umístěny do zóny Intranet, zatímco aplikace nasazené přes internet jsou umístěny do zóny Internet. Obě bezpečnostní zóny omezují přístup aplikace k místním prostředkům, přičemž zóna Intranet je méně restriktivní než zóna Internet. Zóna FullTrust dává aplikacím plný přístup k místním prostředkům počítače. Pokud použijete **- TrustLevel** možnost umístit aplikaci v této zóně, správce vztahu důvěryhodnosti součást modulu CLR, vyzve uživatele k rozhodování, jestli uživatel chce udělit tato vyšší úroveň důvěryhodnosti. Nasazujete-li aplikace přes podnikovou síť, lze úroveň důvěryhodnosti aplikace zvýšit bez dotazování uživatele pomocí technologie Trusted Application Deployment.  
  
 Manifesty aplikací také podporují vlastní oddíly trust. To pomáhá aplikacím podřídit se zásadě bezpečnosti požadovat nejmenší možná oprávnění, protože manifest lze nakonfigurovat tak, aby požadoval pouze specifická oprávnění potřebná ke spuštění aplikace. Nástroj Mage.exe nepodporuje přidávání vlastních oddílů trust přímo. Oddíl lze přidat pomocí textového editoru, analyzátoru jazyka XML nebo grafického nástroje MageUI.exe. Další informace o tom, jak pomocí MageUI.exe můžete přidat vlastní důvěryhodnosti částech v tématu [MageUI.exe (generování manifestu a nástroj pro úpravy, grafický klient)](../../../docs/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md).  
  
 Nové manifesty, které jsou vytvořené pomocí verze 4 Mage.exe, který je součástí [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)], cíl [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]. Chcete-li cílit na dřívější verze rozhraní .NET Framework, je zapotřebí mít dřívější verzi nástroje Mage.exe. Při přidání nebo odebrání sestavení z existující manifest nebo opětovné podepsání manifestu existující, Mage.exe neaktualizuje manifest k cíli [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]. Následující tabulky ukazují tyto funkce a omezení.  
  
|Verze manifestu|Operace|Mage v2.0|Mage v4.0|  
|----------------------|---------------|---------------|---------------|  
|Manifest pro aplikace určené pro rozhraní .NET Framework verze 2.0 nebo 3.x|Otevřít|OK|OK|  
||Zavřít|OK|OK|  
||Uložit|OK|OK|  
||Znovu podepsat|OK|OK|  
||Nový|OK|Nepodporováno|  
||Aktualizovat (viz níže)|OK|OK|  
|Manifest pro aplikace cílené na rozhraní .NET Framework verze 4|Otevřít|OK|OK|  
||Zavřít|OK|OK|  
||Uložit|OK|OK|  
||Znovu podepsat|OK|OK|  
||Nový|Nepodporováno|OK|  
||Aktualizovat (viz níže)|Nepodporováno|OK|  
  
|Verze manifestu|Podrobnosti o operaci Aktualizovat|Mage v2.0|Mage v4.0|  
|----------------------|------------------------------|---------------|---------------|  
|Manifest pro aplikace určené pro rozhraní .NET Framework verze 2.0 nebo 3.x|Upravit sestavení|OK|OK|  
||Přidat sestavení|OK|OK|  
||Odstranit sestavení|OK|OK|  
|Manifest pro aplikace cílené na rozhraní .NET Framework verze 4|Upravit sestavení|Nepodporováno|OK|  
||Přidat sestavení|Nepodporováno|OK|  
||Odstranit sestavení|Nepodporováno|OK|  
  
 Mage.exe vytvoří nové manifesty cílených [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]. Aplikace ClickOnce, které cílí [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)] můžete spustit na [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)] a plnou verzi [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]. Pokud aplikace cílí plnou verzi [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] a nelze spustit [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)], odeberte klienta `<framework>` element pomocí textového editoru a opětovné podepsání manifestu. Tady je ukázka `<framework>` element, který se zaměřuje [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)].  
  
```xml  
<framework targetVersion="4.0" profile="client" supportedRuntime="4.0.20506" />  
```  
  
## <a name="examples"></a>Příklady  
 Následující příklad otevře uživatelské rozhraní nástroje Mage (MageUI.exe).  
  
```  
mage  
```  
  
 Následující příklady vytvoří výchozí manifest nasazení a manifest aplikace. Tyto soubory jsou vytvořeny v aktuálním pracovním adresáři a pojmenovány deploy.application a application.exe.manifest.  
  
```  
mage -New Deployment  
mage -New Application  
```  
  
 Následující příklad vytvoří manifest aplikace naplněný všechny sestavení a soubory prostředků z thecurrent adresáře.  
  
```  
mage -New Application -FromDirectory . -Version 1.0.0.0  
```  
  
 Následující příklad navazuje na předchozí příklad zadáním názvu nasazení a cílového mikroprocesoru. Také určuje adresu URL, na které má technologie ClickOnce hledat aktualizace.  
  
```  
mage -New Application -FromDirectory . -Name "Hello, World! Application" -Version 1.0.0.0 -Processor "x86" -ProviderUrl http://internalserver/HelloWorld/  
```  
  
 Následující příklady ukazují, jak vytvořit dvojici manifestů pro nasazení aplikace WPF hostované v aplikaci Internet Explorer.  
  
```  
mage -New Application -FromDirectory . -Version 1.0.0.0 -WPFBrowserApp true  
mage -New Deployment -AppManifest 1.0.0.0\application.manifest -WPFBrowserApp true  
```  
  
 Následující příklad aktualizuje manifest sestavení informacemi z manifestu aplikace a nastaví základ kódu pro umístění manifestu aplikace.  
  
```  
mage -Update HelloWorld.deploy -AppManifest 1.0.0.0\application.manifest -AppCodeBase http://internalserver/HelloWorld.deploy  
```  
  
 Následující příklad upraví manifest nasazení tak, aby byla vynucena aktualizace verze, kterou má uživatel nainstalovánu.  
  
```  
mage -Update c:\HelloWorldDeployment\HelloWorld.deploy -MinVersion 1.1.0.0  
```  
  
 Následující příklad dává manifestu nasazení pokyn k načtení manifestu aplikace z jiného adresáře.  
  
```  
mage -Update HelloWorld.deploy -AppCodeBase http://anotherserver/HelloWorld/1.1.0.0/  
```  
  
 Následující příklad podepíše existující manifest nasazení pomocí digitálního certifikátu v aktuálním pracovním adresáři.  
  
```  
mage -Sign deploy.application -CertFile cert.pfx -Password <passwd>  
```  
  
## <a name="see-also"></a>Viz také  
 [ClickOnce – zabezpečení a nasazení](/visualstudio/deployment/clickonce-security-and-deployment)  
 [Návod: Ruční nasazení aplikace ClickOnce](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)  
 [Přehled nasazení důvěryhodných aplikací](/visualstudio/deployment/trusted-application-deployment-overview)  
 [MageUI.exe (Manifest Generation and Editing Tool, grafický klient)](../../../docs/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)  
 [Příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
