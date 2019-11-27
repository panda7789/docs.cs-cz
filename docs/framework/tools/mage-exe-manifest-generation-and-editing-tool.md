---
title: Mage.exe (generování manifestu a nástroj pro úpravy)
ms.date: 12/06/2018
helpviewer_keywords:
- Manifest Generation and Editing tool
- Mage.exe
ms.assetid: 77dfe576-2962-407e-af13-82255df725a1
ms.openlocfilehash: aa2ad9222460f8732397f8b1c72e36085bbe4a21
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449430"
---
# <a name="mageexe-manifest-generation-and-editing-tool"></a>Mage.exe (generování manifestu a nástroj pro úpravy)

Manifest Generation and Editing Tool (*Mage. exe*) je nástroj příkazového řádku, který podporuje vytváření a úpravy manifestů aplikace a nasazení. Nástroj *Mage. exe* je možné spustit jak v rámci nástroje příkazového řádku, tak i z jiných aplikací pro systém Windows, včetně aplikací ASP.NET.

Nástroj *MageUI. exe*, místo nástroje *Mage. exe*, lze použít také jako grafické aplikace. Další informace naleznete v tématu [MageUI. exe (Manifest Generation and Editing Tool, grafický klient)](mageui-exe-manifest-generation-and-editing-tool-graphical-client.md).

Tento nástroj je automaticky nainstalován se sadou Visual Studio. Pro spuštění tohoto nástroje použijte Developer Command Prompt pro Visual Studio. Další informace najdete v tématu [výzvy k zadání příkazu](developer-command-prompt-for-vs.md).

Součástí sady Visual Studio jsou dvě verze *Mage. exe* a *MageUI. exe* . Chcete-li zobrazit informace o verzi, spusťte nástroj *MageUI. exe*, vyberte možnost **nápovědu**a vyberte možnost **o produktu**. Tato dokumentace popisuje verzi 4.0. x. x z *Mage. exe* a *MageUI. exe*.

## <a name="syntax"></a>Syntaxe

```console
Mage [commands] [commandOptions]
```

## <a name="parameters"></a>Parametry

V následující tabulce jsou uvedeny příkazy podporované nástrojem *Mage. exe*. Další informace o možnostech podporovaných těmito příkazy najdete v tématu možnosti pro [příkazy nové a aktualizace](#new-and-update-command-options) a [Možnosti příkazu Sign](#sign-command-options).

|Příkaz|Popis|
|-------------|-----------------|
|**-CC, ClearApplicationCache**|Odstraní všechny aplikace fungující pouze v režimu online z mezipaměti stažených aplikací.|
|**-n,-nový** *typ souboru [newOptions]*|Vytvoří nový soubor daného typu. Platnými typy jsou:<br /><br /> -   `Deployment`: vytvoří nový manifest nasazení.<br />-   `Application`: vytvoří nový manifest aplikace.<br /><br /> Nezadáte-li s tímto příkazem žádné další parametry, bude vytvořen soubor odpovídajícího typu s odpovídajícími výchozími značkami a hodnotami atributů.<br /><br /> Použijte možnost **-ToFile** (viz následující tabulka) a zadejte název souboru a cestu k novému souboru.<br /><br /> Použijte možnost **-FromDirectory** (viz následující tabulka) k vytvoření manifestu aplikace se všemi sestaveními pro aplikaci přidanou do > části manifestu \<závislostí.|
|**-u,-Update** *[FilePath] [updateOptions]*|Provede jednu nebo více změn souboru manifestu. Typ upravovaného souboru není třeba zadávat. Nástroj Mage.exe soubor zkontroluje sadou heuristik a určí, zda jde o manifest nasazení nebo manifest aplikace.<br /><br /> Pokud jste už soubor s certifikátem podepsali, **příkaz Update** odebere blok signatury klíče. Důvodem je skutečnost, že podpis klíče obsahuje hodnotu hash souboru, která je úpravou souboru zneplatněna.<br /><br /> Použijte možnost **-ToFile** (viz následující tabulka) a zadejte nový název souboru a cestu namísto přepsání stávajícího souboru.|
|**-s,-Sign** `[signOptions]`|Použije k podpisu souboru pár klíčů nebo certifikát X509. Podpisy jsou do souboru vloženy jako prvky jazyka XML.<br /><br /> Při podepisování manifestu, který určuje hodnotu **-TimestampUri** , musíte být připojeni k Internetu.|
|**-ver,-Verify** *[manifest-filename]*|Ověřuje, jestli je manifest správně podepsaný. Nelze kombinovat s jinými příkazy. <br/><br/>**K dispozici v .NET Framework 4,7 a novějších verzích.**|
|**-h,-?,-help** *[verbose]*|Popíše všechny dostupné příkazy a jejich možnosti. Pokud chcete získat podrobnou nápovědu, zadejte `verbose`.|

## <a name="new-and-update-command-options"></a>Možnosti příkazu New a Update

Následující tabulka ukazuje možnosti podporované příkazy `-New` a `-Update`:

|Možnosti|Výchozí hodnota|Platí pro|Popis|
|-------------|-------------------|----------------|-----------------|
|**-a,-Algorithm**|sha1RSA|Manifesty aplikací.<br /><br /> Manifesty nasazení.|Určí algoritmus, jímž budou generovány přehledy závislostí. Hodnotou musí být „sha256RSA“ nebo „sha1RSA“.<br /><br /> Použijte s možností „-Update“. Při použití možnosti „-Sign“ je tato možnost ignorována.|
|**-technologie APPC,-AppCodeBase** `manifestReference`||Manifesty nasazení.|Vloží odkaz na adresu URL nebo cestu k souboru do souboru manifestu aplikace. Touto hodnotou musí být úplná cesta k manifestu aplikace.|
|**-APPM,-AppManifest** `manifestPath`||Manifesty nasazení.|Vloží do manifestu nasazení odkaz na manifest aplikace tohoto nasazení.<br /><br /> Soubor, který je uveden `manifestPath` musí existovat, nebo *Mage. exe* vydá chybu. Pokud soubor odkazovaný `manifestPath` není manifest aplikace, program *Mage. exe* vydá chybu.|
|**-CF,-soubor_certifikátu** `filePath`||Všechny typy souborů.|Určuje umístění digitálního certifikátu x509 pro podepsání manifestu nebo souboru s licencí. Tuto možnost lze použít společně s možností **-Password** , pokud certifikát vyžaduje heslo pro soubory PFX (Personal Information Exchange). Pokud soubor neobsahuje privátní klíč, počínaje .NET Framework 4,7, je třeba zadat kombinaci možností **-CryptoProvider** a **-** Key.<br/><br/>Počínaje .NET Framework 4.6.2 nástroj *Mage. exe* podepisuje manifesty s CNG a také certifikáty rozhraní CAPI.|
|**-ch, – CertHash** `hashSignature`||Všechny typy souborů.|Hodnota hash digitálního certifikátu uloženého v úložišti osobních certifikátů klientského počítače. Ta odpovídá řetězci kryptografického otisku digitálního certifikátu zobrazeného v Konzole certifikátů systému Windows.<br /><br /> `hashSignature` může být buď velká, nebo malá písmena a lze je zadat buď jako jeden řetězec, nebo s každým oktetem kryptografického otisku odděleného mezerami a celým otiskem uzavřeným v uvozovkách.|
|**-CSP,-CryptoProvider** `provider-name`||Všechny typy souborů.|Určuje název zprostředkovatele kryptografických služeb (CSP), který obsahuje kontejner privátního klíče. Tato možnost vyžaduje možnost **-na omezení** .<br/><br/>Tato možnost je k dispozici od .NET Framework 4,7.|
|**-FD,-FromDirectory** `directoryPath`||Manifesty aplikací.|Naplní manifest aplikace popisy všech sestavení a souborů nalezených v `directoryPath`, včetně všech podadresářů, kde `directoryPath` je adresář, který obsahuje aplikaci, kterou chcete nasadit. Pro každý soubor v adresáři nástroj *Mage. exe* rozhodne, zda je soubor sestavením nebo statickým souborem. Pokud se jedná o sestavení, přidá značku `<dependency>` a `installFrom` atributu do aplikace s názvem sestavení, základem kódu a verzí. Pokud se jedná o statický soubor, přidá značku `<file>`. Nástroj *Mage. exe* také používá jednoduchou sadu heuristik pro detekci hlavního spustitelného souboru aplikace a označí ho jako vstupní bod aplikace ClickOnce v manifestu.<br /><br /> Nástroj *Mage. exe* nikdy nebude automaticky označovat soubor jako datový. To je zapotřebí provést ručně. Další informace naleznete v tématu [How to: include a data File in a ClickOnce Application](/visualstudio/deployment/how-to-include-a-data-file-in-a-clickonce-application).<br /><br /> Nástroj *Mage. exe* také generuje hodnotu hash pro každý soubor na základě jeho velikosti. Technologie ClickOnce těmito hodnotami hash zajišťuje, že se soubory nasazení nikdo od vytvoření manifestu nemanipuloval. Pokud se některý ze souborů v nasazení změní, můžete spustit nástroj *Mage. exe* pomocí příkazu **-Update** a parametru **-FromDirectory** a bude aktualizovat hodnoty hash a verze sestavení všech odkazovaných souborů.<br /><br /> **– FromDirectory** bude obsahovat všechny soubory ve všech podadresářích nalezených v rámci `directoryPath`.<br /><br /> Použijete-li příkaz **-FromDirectory** s příkazem **-Update** , nástroj *Mage. exe* odstraní všechny soubory v manifestu aplikace, který již v adresáři neexistuje.|
|**-if,-IconFile**`filePath`||Manifesty aplikací.|Určí úplnou cestu k souboru ikony .ICO. Tato ikona se zobrazuje vedle názvu aplikace v nabídce Start a v jejím záznamu v ovládacím panelu Přidat nebo odebrat programy. Není-li zadána žádná ikona, je použita ikona výchozí.|
|**-IP,-IncludeProviderURL**`url`|true|Manifesty nasazení.|Určuje, zda manifest nasazení zahrnuje hodnotu umístění aktualizace nastavenou na **-providerUrl**.|
|**-i,-instalace** `willInstall`|true|Manifesty nasazení.|Označuje, zda by aplikace ClickOnce měla být nainstalována na místní počítač nebo spuštěna z webu. Instalace aplikace zajišťuje přítomnost aplikace v nabídce **Start** systému Windows. Platnými hodnotami jsou „true“ nebo „t“ a „false“ nebo „f“.<br /><br /> Zadáte-li možnost **-MinVersion** a uživatel má nainstalovanou verzi nižší než **-MinVersion** , aplikace bude aplikaci instalovat, a to bez ohledu na hodnotu, kterou předáte do **instalace**.<br /><br /> Tuto možnost nelze použít s možností **-BrowserHosted** . Pokus zadat obě možnosti pro stejný manifest vyústí v chybu.|
|**-KC,-`name` obsahující**||Všechny typy souborů.|Určuje kontejner klíčů, který obsahuje název privátního klíče. Tato možnost vyžaduje možnost **CryptoProvider** .<br/><br/>Tato možnost je k dispozici od .NET Framework 4,7.|
|**-MV,-MinVersion**`[version]`|Verze uvedená v manifestu nasazení ClickOnce, jak je specifikováno příznakem **-Version** .|Manifesty nasazení.|Minimální verze aplikace, kterou uživatel může spustit. Tento příznak učiní pojmenovanou verzi aplikace požadovanou aktualizací. Vydáte-li verzi produktu s aktualizací proti narušující změně nebo závažné bezpečnostní chybě, lze pomocí tohoto příznaku určit, že aktualizace musí být nainstalována a že uživatel nemůže nadále používat dřívější verze.<br /><br /> `version` má stejnou sémantiku jako argument příznaku **-Version** .|
|**-n,-Name** `nameString`|Nasazení|Všechny typy souborů.|Název použitý pro identifikaci aplikace. ClickOnce použije tento název k identifikaci aplikace v nabídce **Start** (Pokud je aplikace nakonfigurovaná k instalaci samotného) a v dialogových oknech zvýšení úrovně oprávnění. **Poznámka:**  Pokud aktualizujete existující manifest a neurčíte název vydavatele pomocí této možnosti, nástroj *Mage. exe* aktualizuje manifest s názvem organizace definovaným v počítači. Chcete-li použít jiný název, použijte tuto možnost a zadejte požadovaný název vydavatele.|
|**-PWD,-Password** `passwd`||Všechny typy souborů.|Heslo použité pro podepsání manifestu digitálním certifikátem. Musí se používat ve spojení s parametrem **-Soubor_certifikátu** .|
|**-p, `processorValue` procesoru**|Msil|Manifesty aplikací.<br /><br /> Manifesty nasazení.|Architektura mikroprocesoru, na níž bude distribuce spouštěna. Tato hodnota je vyžadována, pokud připravujete jednu nebo více instalací, jejichž sestavení byla předkompilována pro určitý mikroprocesor. Platné hodnoty zahrnují `msil`, `x86`, `ia64`a `amd64`. `msil` je Microsoft Intermediate Language, což znamená, že všechna vaše sestavení jsou nezávislá na platformě a modul CLR (Common Language Runtime) bude při prvním spuštění aplikace kompilovat v čase.|
|**-PU,** **-providerUrl** `url`||Manifesty nasazení.|Určuje adresu URL, na které technologie ClickOnce vyhledá aktualizace aplikace.|
|**-Pub,-publish** `publisherName`||Manifesty aplikací.<br /><br /> Manifesty nasazení.|Přidá název vydavatele do prvku popisu v manifestu nasazení nebo manifestu aplikace. Při použití v manifestu aplikace musí být parametr **-UseManifestForTrust** také zadán s hodnotou "true" nebo "t"; v opačném případě bude tento parametr vyvolat chybu.|
|**-s,-SupportURL**`url`||Manifesty aplikací.<br /><br /> Manifesty nasazení.|Určí odkaz, který se pro aplikaci ClickOnce objeví v ovládacím panelu Přidat nebo odebrat programy.|
|**-ti,-TimestampUri** `uri`||Manifesty aplikací.<br /><br /> Manifesty nasazení.|Adresa URL služby vytváření digitálního časového razítka. Vytvoření časového razítka v manifestu umožňuje vyhnout se nutnosti znovu manifesty podepsat, pokud by digitální certifikát vypršel ještě před nasazením další verze aplikace. Další informace naleznete v tématu [Členové programu kořenového certifikátu systému Windows](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn265983(v=ws.11)).|
|**-t,-ToFile** `filePath`|New<br />-Deployment: Deploy. Application<br />-Application: Application. exe. manifest<br />Update<br />– Vstupní soubor.|Všechny typy souborů.|Určí výstupní cestu vytvořeného nebo upraveného souboru.<br /><br /> Pokud **-ToFile** není k dispozici při použití **-New**, výstup se zapíše do aktuálního pracovního adresáře. Pokud není zadán **příkaz-ToFile** při použití **-Update**, nástroj *Mage. exe* zapíše soubor zpět do vstupního souboru.|
|**-TR,-TrustLevel** `level`|Dle zóny, v níž se adresa URL aplikace nachází.|Manifesty aplikací.|Úroveň důvěryhodnosti, která bude aplikacím udělena na klientských počítačích. Mezi hodnoty patří „Internet“, „Intranet“ a „FullTrust“.|
|**– um, – UseManifestForTrust** `willUseForTrust`|False|Manifesty aplikací.|Určí, zda bude při spuštění aplikace na klientském počítači použit pro rozhodování o důvěryhodnosti digitální podpis manifestu aplikace. Hodnota „true“ nebo „t“ určí, že pro rozhodnutí o důvěryhodnosti bude použit manifest aplikace. Hodnota „false“ nebo „f“ určí, že bude použit podpis manifestu nasazení.|
|**-v, verze** `versionNumber`|1.0.0.0|Manifesty aplikací.<br /><br /> Manifesty nasazení.|Verze nasazení. Argument musí být platný řetězec verze formátu "*n. n. n. n*", kde "*n*" je celé číslo bez znaménka 32-bit.|
|**– WPF,-WPFBrowserApp**`isWPFApp`|false (nepravda)|Manifesty aplikací.<br /><br /> Manifesty nasazení.|Tento příznak použijte pouze tehdy, je-li aplikace aplikací Windows Presentation Foundation (WPF), která bude hostována v aplikaci Internet Explorer a není samostatně spustitelná. Platnými hodnotami jsou „true“ nebo „t“ a „false“ nebo „f“.<br /><br /> Pro manifesty aplikace vloží atribut `hostInBrowser` pod element `entryPoint` manifestu aplikace.<br /><br /> V případě manifestů nasazení nastaví atribut `install` u elementu `deployment` na hodnotu false a uloží manifest nasazení s příponou. XBAP. Zadáním tohoto argumentu spolu s argumentem **-install** dojde k chybě, protože aplikace hostovaná v prohlížeči nemůže být nainstalovaná, offline aplikace.|

## <a name="sign-command-options"></a>Možnosti příkazu Sign

Následující tabulka ukazuje možnosti podporované příkazem `-Sign`, které platí pro všechny typy souborů.

|Možnosti|Popis|
|-------------|-----------------|
|**-CF,-soubor_certifikátu** `filePath`|Určí umístění digitálního certifikátu pro podpis manifestu. Tuto možnost lze použít společně s možností **-Password** , pokud certifikát vyžaduje heslo pro soubory PFX (Personal Information Exchange). Pokud soubor neobsahuje privátní klíč, počínaje .NET Framework 4,7, je třeba zadat kombinaci možností **-CryptoProvider** a **-** Key.<br/><br/>Počínaje .NET Framework 4.6.2 nástroj *Mage. exe* podepisuje manifesty s CNG a také certifikáty rozhraní CAPI.|
|**-ch, – CertHash** `hashSignature`|Hodnota hash digitálního certifikátu uloženého v úložišti osobních certifikátů klientského počítače. Ta odpovídá vlastnosti kryptografického otisku digitálního certifikátu zobrazeného v Konzole certifikátů systému Windows.<br /><br /> `hashSignature` může být buď velká, nebo malá písmena a lze je zadat buď jako jeden řetězec, nebo s každým oktetem kryptografického otisku odděleného mezerami a celým otiskem uzavřeným v uvozovkách.|
**-CSP,-CryptoProvider** `provider-name`|Určuje název zprostředkovatele kryptografických služeb (CSP), který obsahuje kontejner privátního klíče. Tato možnost vyžaduje možnost **-na omezení** .<br/><br/>Tato možnost je k dispozici od .NET Framework 4,7.|
|**-KC,-`name` obsahující**|Určuje kontejner klíčů, který obsahuje název privátního klíče. Tato možnost vyžaduje možnost **CryptoProvider** .<br/><br/>Tato možnost je k dispozici od .NET Framework 4,7.|
|**-PWD,-Password** `passwd`|Heslo použité pro podepsání manifestu digitálním certifikátem. Musí se používat ve spojení s parametrem **-Soubor_certifikátu** .|
|**-t,-ToFile** `filePath`|Určí výstupní cestu vytvořeného nebo upraveného souboru.|

## <a name="remarks"></a>Poznámky

Všechny argumenty pro *Mage. exe* nerozlišují velká a malá písmena. Příkazy a možnosti mohou mít předponu pomlčky (-) nebo lomítka (/).

Všechny argumenty použité s příkazem **-Sign** lze kdykoli použít spolu s příkazy **-New** a **-Update** . Následující příkazy jsou ekvivalentní.

```console
mage -Sign c:\HelloWorldDeployment\HelloWorld.deploy -CertFile cert.pfx
mage -Update c:\HelloWorldDeployment\HelloWorld.deploy -CertFile cert.pfx
```

> [!NOTE]
> Počínaje .NET Framework verzí 4.6.2 jsou také podporovány certifikáty CNG.

 Podpis by měl být poslední provedený úkol, protože podepsaný dokument používá hodnotu hash souboru pro ověření, zda je podpis pro dokument platný. Provedete-li v podepsaném souboru nějaké změny, je zapotřebí soubor znovu podepsat. Pokud podepíšete dokument, který byl dříve podepsaný, nástroj *Mage. exe* nahradí starý podpis novým.

 Použijete-li možnost **-AppManifest** k naplnění manifestu nasazení, nástroj *Mage. exe* bude předpokládat, že se manifest vaší aplikace nachází ve stejném adresáři jako manifest nasazení v podadresáři s názvem po aktuální verzi nasazení a bude správně nakonfigurován manifest nasazení. Pokud se váš manifest aplikace nachází jinde, použijte možnost **-AppCodeBase** k nastavení alternativního umístění.

 Před nasazením aplikace musí být manifesty nasazení a aplikace podepsány. Pokyny k podepisování manifestů naleznete v tématu [Přehled nasazení důvěryhodných aplikací](/visualstudio/deployment/trusted-application-deployment-overview).

 Možnost **-TrustLevel** pro manifesty aplikací popisuje nastavení oprávnění, které aplikace vyžaduje ke spuštění v klientském počítači. Ve výchozím nastavení jsou aplikacím přiřazeny úrovně důvěryhodnosti založené na *zóně* , ve které se nachází jejich adresa URL. Aplikace nasazené přes podnikovou síť jsou obecně umístěny do zóny Intranet, zatímco aplikace nasazené přes internet jsou umístěny do zóny Internet. Obě bezpečnostní zóny omezují přístup aplikace k místním prostředkům, přičemž zóna Intranet je méně restriktivní než zóna Internet. Zóna FullTrust dává aplikacím plný přístup k místním prostředkům počítače. Použijete-li možnost **-TrustLevel** k umístění aplikace do této zóny, komponenta správce vztahu důvěryhodnosti modulu CLR vyzve uživatele k rozhodnutí, zda chce tuto vyšší úroveň důvěry udělit. Nasazujete-li aplikace přes podnikovou síť, lze úroveň důvěryhodnosti aplikace zvýšit bez dotazování uživatele pomocí technologie Trusted Application Deployment.

 Manifesty aplikací také podporují vlastní oddíly trust. To pomáhá aplikacím podřídit se zásadě bezpečnosti požadovat nejmenší možná oprávnění, protože manifest lze nakonfigurovat tak, aby požadoval pouze specifická oprávnění potřebná ke spuštění aplikace. Nástroj *Mage. exe* přímo nepodporuje přidávání vlastních oddílů Trust. Můžete ji přidat pomocí textového editoru, analyzátoru jazyka XML nebo grafického nástroje *MageUI. exe*. Další informace o tom, jak pomocí nástroje *MageUI. exe* přidat vlastní oddíly důvěryhodnosti, naleznete v tématu [MageUI. exe (Manifest Generation and Editing Tool, grafický klient)](mageui-exe-manifest-generation-and-editing-tool-graphical-client.md).

Visual Studio 2017 obsahuje verzi 4.6.1 souboru *Mage. exe*. Manifesty vytvořené s touto verzí *Mage. exe* Target .NET Framework 4. Chcete-li cílit na starší verze .NET Framework, použijte starší verzi nástroje *Mage. exe*.

Když přidáváte nebo odebíráte sestavení z existujícího manifestu nebo znovu podepíšete existující manifest, nástroj *Mage. exe* neaktualizuje manifest na cílovou .NET Framework 4.

Následující tabulky obsahují tyto funkce a omezení:

|Verze manifestu|Funkce|Mage v2.0|Mage v4.0|
|----------------------|---------------|---------------|---------------|
|Manifest pro aplikace určené pro rozhraní .NET Framework verze 2.0 nebo 3.x|Otevřenost|OK|OK|
||Zavřít|OK|OK|
||Uložit|OK|OK|
||Znovu podepsat|OK|OK|
||Nová|OK|Nepodporuje se|
||Aktualizovat (viz níže)|OK|OK|
|Manifest pro aplikace cílené na rozhraní .NET Framework verze 4|Otevřenost|OK|OK|
||Zavřít|OK|OK|
||Uložit|OK|OK|
||Znovu podepsat|OK|OK|
||Nová|Nepodporuje se|OK|
||Aktualizovat (viz níže)|Nepodporuje se|OK|

|Verze manifestu|Podrobnosti o operaci Aktualizovat|Mage v2.0|Mage v4.0|
|----------------------|------------------------------|---------------|---------------|
|Manifest pro aplikace určené pro rozhraní .NET Framework verze 2.0 nebo 3.x|Upravit sestavení|OK|OK|
||Přidat sestavení|OK|OK|
||Odstranit sestavení|OK|OK|
|Manifest pro aplikace cílené na rozhraní .NET Framework verze 4|Upravit sestavení|Nepodporuje se|OK|
||Přidat sestavení|Nepodporuje se|OK|
||Odstranit sestavení|Nepodporuje se|OK|

 Nástroj Mage. exe vytvoří nové manifesty, které cílí na [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]. Aplikace ClickOnce cílené na [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)] lze spustit jak v [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)], tak i v plné verzi .NET Framework 4. Pokud je vaše aplikace cílena na plnou verzi .NET Framework 4 a nelze ji spustit v [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)], odeberte prvek `<framework>` klienta pomocí textového editoru a znovu podepište manifest.

Následuje vzorový `<framework>` element, který cílí na [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]:

```xml
<framework targetVersion="4.0" profile="client" supportedRuntime="4.0.20506" />
```

## <a name="examples"></a>Příklady

Následující příklad otevře uživatelské rozhraní pro Mage (*MageUI. exe*).

```console
mage
```

Následující příklady vytvoří výchozí manifest nasazení a manifest aplikace. Tyto soubory jsou vytvořeny v aktuálním pracovním adresáři a pojmenovány deploy.application a application.exe.manifest.

```console
mage -New Deployment
mage -New Application
```

Následující příklad vytvoří manifest aplikace naplněný všemi sestaveními a soubory prostředků z aktuálního adresáře.

```console
mage -New Application -FromDirectory . -Version 1.0.0.0
```

Následující příklad navazuje na předchozí příklad zadáním názvu nasazení a cílového mikroprocesoru. Také určuje adresu URL, na které má technologie ClickOnce hledat aktualizace.

```console
mage -New Application -FromDirectory . -Name "Hello, World! Application" -Version 1.0.0.0 -Processor "x86" -ProviderUrl http://internalserver/HelloWorld/
```

Následující příklady ukazují, jak vytvořit dvojici manifestů pro nasazení aplikace WPF hostované v aplikaci Internet Explorer.

```console
mage -New Application -FromDirectory . -Version 1.0.0.0 -WPFBrowserApp true
mage -New Deployment -AppManifest 1.0.0.0\application.manifest -WPFBrowserApp true
```

Následující příklad vytvoří manifest aplikace naplněný všemi sestaveními a soubory prostředků z aktuálního adresáře a znaménka.

```console
mage -New Application -FromDirectory . -Version 1.0.0.0 -KeyContainer keypair.snk -CryptoProvider "Microsoft Enhanced Cryptographic Provider v1.0"
```

Následující příklad aktualizuje manifest sestavení informacemi z manifestu aplikace a nastaví základ kódu pro umístění manifestu aplikace.

```console
mage -Update HelloWorld.deploy -AppManifest 1.0.0.0\application.manifest -AppCodeBase http://internalserver/HelloWorld.deploy
```

Následující příklad upraví manifest nasazení tak, aby byla vynucena aktualizace verze, kterou má uživatel nainstalovánu.

```console
mage -Update c:\HelloWorldDeployment\HelloWorld.deploy -MinVersion 1.1.0.0
```

Následující příklad dává manifestu nasazení pokyn k načtení manifestu aplikace z jiného adresáře.

```console
mage -Update HelloWorld.deploy -AppCodeBase http://anotherserver/HelloWorld/1.1.0.0/
```

Následující příklad podepíše existující manifest nasazení pomocí digitálního certifikátu v aktuálním pracovním adresáři.

```console
mage -Sign deploy.application -CertFile cert.pfx -Password <passwd>
```

Následující příklad podepíše existující manifest nasazení pomocí digitálního certifikátu a privátního klíče v aktuálním pracovním adresáři.

```console
mage -Sign deploy.application -CertFile cert.pfx -KeyContainer keyfile.snk -CryptoProvider "Microsoft Enhanced Cryptographic Provider v1.0"
```

## <a name="see-also"></a>Viz také:

- [ClickOnce – zabezpečení a nasazení](/visualstudio/deployment/clickonce-security-and-deployment)
- [Návod: Ruční nasazení aplikace ClickOnce](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)
- [Přehled nasazení důvěryhodných aplikací](/visualstudio/deployment/trusted-application-deployment-overview)
- [MageUI.exe (Manifest Generation and Editing Tool, grafický klient)](mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)
- [Příkazové řádky](developer-command-prompt-for-vs.md)
