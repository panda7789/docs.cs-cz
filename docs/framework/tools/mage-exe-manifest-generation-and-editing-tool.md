---
title: Mage.exe (generování manifestu a nástroj pro úpravy)
ms.date: 12/06/2018
helpviewer_keywords:
- Manifest Generation and Editing tool
- Mage.exe
ms.assetid: 77dfe576-2962-407e-af13-82255df725a1
ms.openlocfilehash: b04fda81ae51462d9e686585de1477b4c9af4b26
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180393"
---
# <a name="mageexe-manifest-generation-and-editing-tool"></a>Mage.exe (generování manifestu a nástroj pro úpravy)

Nástroj generování a úpravy manifestu (*Mage.exe*) je nástroj příkazového řádku, který podporuje vytváření a úpravy manifestů aplikací a nasazení. Jako nástroj příkazového řádku lze nástroj *Mage.exe* spustit jak z dávkových skriptů, tak z jiných aplikací založených na systému Windows, včetně ASP.NET aplikací.

Můžete také použít *MageUI.exe*, grafickou aplikaci, namísto *Mage.exe*. Další informace naleznete v [tématu MageUI.exe (Nástroj pro generování a úpravy manifestu, grafický klient).](mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)

Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li nástroj spustit, použijte příkazový řádek pro vývojáře pro sadu Visual Studio. Další informace naleznete v [příkazových koncích](developer-command-prompt-for-vs.md).

Dvě verze *Mage.exe* a *MageUI.exe* jsou součástí sady Visual Studio. Chcete-li zobrazit informace o verzi, spusťte *soubor MageUI.exe*, vyberte **nápovědu**a vyberte **možnost O .** Tato dokumentace popisuje verzi 4.0.x.x *mage.exe* a *MageUI.exe*.

## <a name="syntax"></a>Syntaxe

```console
Mage [commands] [commandOptions]
```

## <a name="parameters"></a>Parametry

V následující tabulce jsou uvedeny příkazy podporované programem *Mage.exe*. Další informace o možnostech podporovaných těmito příkazy naleznete v tématech [Nové a Aktualizovat možnosti příkazů](#new-and-update-command-options) a [Možnosti příkazů Podepsat](#sign-command-options).

|Příkaz|Popis|
|-------------|-----------------|
|**-cc, ClearApplicationCache**|Odstraní všechny aplikace fungující pouze v režimu online z mezipaměti stažených aplikací.|
|**-n, -Nový** *typ souboru [newOptions]*|Vytvoří nový soubor daného typu. Platnými typy jsou:<br /><br /> -   `Deployment`: Vytvoří nový manifest nasazení.<br />-   `Application`: Vytvoří nový manifest aplikace.<br /><br /> Nezadáte-li s tímto příkazem žádné další parametry, bude vytvořen soubor odpovídajícího typu s odpovídajícími výchozími značkami a hodnotami atributů.<br /><br /> Pomocí možnosti **-ToFile** (viz v následující tabulce) určete název souboru a cestu k novému souboru.<br /><br /> Pomocí možnosti **-FromDirectory** (viz v následující tabulce) vytvořte manifest aplikace se všemi \<sestaveními aplikace přidanou do sekce závislost> manifestu.|
|**-u, -Update** *[filePath] [updateOptions]*|Provede jednu nebo více změn souboru manifestu. Typ upravovaného souboru není třeba zadávat. Nástroj Mage.exe soubor zkontroluje sadou heuristik a určí, zda jde o manifest nasazení nebo manifest aplikace.<br /><br /> Pokud jste již podepsali soubor s certifikátem, **-Update** odebere blok podpisu klíče. Důvodem je skutečnost, že podpis klíče obsahuje hodnotu hash souboru, která je úpravou souboru zneplatněna.<br /><br /> Pomocí možnosti **-ToFile** (viz v následující tabulce) určete nový název souboru a cestu namísto přepsání existujícího souboru.|
|**-s, -Podepsat**`[signOptions]`|Použije k podpisu souboru pár klíčů nebo certifikát X509. Podpisy jsou do souboru vloženy jako prvky jazyka XML.<br /><br /> Při podepisování manifestu, který určuje hodnotu **-TimestampUri,** musíte být připojeni k Internetu.|
|**-ver, -Verify** *[manifest-filename]*|Ověří, zda je manifest podepsán správně. Nelze kombinovat s jinými příkazy. <br/><br/>**K dispozici v rozhraní .NET Framework 4.7 a novějších verzích.**|
|**-h, -?, -Help** *[verbose]*|Popíše všechny dostupné příkazy a jejich možnosti. Zadejte, `verbose` chcete-li získat podrobnou nápovědu.|

## <a name="new-and-update-command-options"></a>Nové a aktualizovat možnosti příkazu

V následující tabulce jsou uvedeny možnosti `-New` podporované příkazy a: `-Update`

|Možnosti|Výchozí hodnota|Platí pro|Popis|
|-------------|-------------------|----------------|-----------------|
|**-a, -Algoritmus**|sha1RSA|Manifesty aplikací.<br /><br /> Manifesty nasazení.|Určí algoritmus, jímž budou generovány přehledy závislostí. Hodnotou musí být „sha256RSA“ nebo „sha1RSA“.<br /><br /> Použijte s možností „-Update“. Při použití možnosti „-Sign“ je tato možnost ignorována.|
|**-appc, -AppCodeBase**`manifestReference`||Manifesty nasazení.|Vloží odkaz na adresu URL nebo cestu k souboru do souboru manifestu aplikace. Touto hodnotou musí být úplná cesta k manifestu aplikace.|
|**-appm, -AppManifest**`manifestPath`||Manifesty nasazení.|Vloží do manifestu nasazení odkaz na manifest aplikace tohoto nasazení.<br /><br /> Soubor označený musí `manifestPath` existovat nebo *mage.exe* vydá chybu. Pokud soubor, na `manifestPath` který odkazuje, není manifestem aplikace, *vydá nástroj Mage.exe* chybu.|
|**-cf, -CertFile**`filePath`||Všechny typy souborů.|Určuje umístění digitálního certifikátu X509 pro podepisování manifestu nebo licenčního souboru. Tuto možnost lze použít ve spojení s volbou **-Password,** pokud certifikát vyžaduje heslo pro soubory PFX (Personal Information Exchange). Počínaje rozhraním .NET Framework 4.7, pokud soubor neobsahuje soukromý klíč, je vyžadována kombinace možností **-CryptoProvider** a **-KeyContainer.**<br/><br/>Počínaje rozhraním .NET Framework 4.6.2 se *mage.exe* projevuje s certifikáty CNG a capi.|
|**-ch, -CertHash**`hashSignature`||Všechny typy souborů.|Hodnota hash digitálního certifikátu uloženého v úložišti osobních certifikátů klientského počítače. Ta odpovídá řetězci kryptografického otisku digitálního certifikátu zobrazeného v Konzole certifikátů systému Windows.<br /><br /> `hashSignature`může být velká nebo malá písmena a může být dodána buď jako jeden řetězec, nebo s každým oktetem thumbprintu odděleným mezerami a celým thumbprintem uzavřeným v uvozovkách.|
|**-csp, -CryptoProvider**`provider-name`||Všechny typy souborů.|Určuje název zprostředkovatele kryptografických služeb (CSP), který obsahuje kontejner soukromého klíče. Tato možnost vyžaduje možnost **-KeyContainer.**<br/><br/>Tato možnost je k dispozici počínaje rozhraním .NET Framework 4.7.|
|**-fd, -FromDirectory**`directoryPath`||Manifesty aplikací.|Naplní manifest aplikace popisy všech sestavení a `directoryPath`souborů nalezených v aplikaci , včetně všech podadresářů, kde `directoryPath` je adresář obsahující aplikaci, kterou chcete nasadit. Pro každý soubor v adresáři *mage.exe* rozhodne, zda je soubor sestavení nebo statický soubor. Pokud se jedná o sestavení, přidá `<dependency>` značku a `installFrom` atribut do aplikace s názvem sestavení, základem kódu a verzí. Pokud se jedná o statický `<file>` soubor, přidá značku. *Mage.exe* také použije jednoduchou sadu heuristiky k detekci hlavního spustitelného souboru pro aplikaci a označí jej jako vstupní bod aplikace ClickOnce v manifestu.<br /><br /> *Mage.exe* nikdy automaticky neoznačí soubor jako "datový" soubor. To je zapotřebí provést ručně. Další informace naleznete [v tématu How to: Include a Data File in a ClickOnce Application](/visualstudio/deployment/how-to-include-a-data-file-in-a-clickonce-application).<br /><br /> *Mage.exe* také generuje hash pro každý soubor na základě jeho velikosti. Technologie ClickOnce těmito hodnotami hash zajišťuje, že se soubory nasazení nikdo od vytvoření manifestu nemanipuloval. Pokud se některý ze souborů ve vašem nasazení změní, můžete spustit *mage.exe* pomocí příkazu **-Update** a **možnosti -FromDirectory** a aktualizuje hodnoty hash a verze sestavení všech odkazovaných souborů.<br /><br /> **-FromDirectory** bude obsahovat všechny soubory ve `directoryPath`všech podadresářích nalezených v rámci .<br /><br /> Pokud použijete **-FromDirectory** s příkazem **-Update,** *mage.exe* odebere všechny soubory v manifestu aplikace, které již v adresáři neexistují.|
|**-if, -IconFile**  `filePath`||Manifesty aplikací.|Určí úplnou cestu k souboru ikony .ICO. Tato ikona se zobrazuje vedle názvu aplikace v nabídce Start a v jejím záznamu v ovládacím panelu Přidat nebo odebrat programy. Není-li zadána žádná ikona, je použita ikona výchozí.|
|**-ip, -IncludeProviderURL**  `url`|true|Manifesty nasazení.|Označuje, zda manifest nasazení obsahuje hodnotu umístění aktualizace nastavenou společností **-ProviderURL**.|
|**-i, -Instalace**`willInstall`|true|Manifesty nasazení.|Označuje, zda by aplikace ClickOnce měla být nainstalována na místní počítač nebo spuštěna z webu. Instalace aplikace poskytuje této aplikaci přítomnost v nabídce **Start** systému Windows. Platnými hodnotami jsou „true“ nebo „t“ a „false“ nebo „f“.<br /><br /> Pokud zadáte možnost **-MinVersion** a uživatel má nainstalovanou verzi menší než **-MinVersion,** vynutí instalaci aplikace bez ohledu na hodnotu, kterou předáte **-Install**.<br /><br /> Tuto možnost nelze použít s volbou **-BrowserHosted.** Pokus zadat obě možnosti pro stejný manifest vyústí v chybu.|
|**-kc, -KeyContainer**`name`||Všechny typy souborů.|Určuje kontejner klíčů, který obsahuje název soukromého klíče. Tato možnost vyžaduje možnost **CryptoProvider.**<br/><br/>Tato možnost je k dispozici počínaje rozhraním .NET Framework 4.7.|
|**-mv, -MinVersion**  `[version]`|Verze uvedená v manifestu nasazení ClickOnce, jak je určeno příznakem **-Version.**|Manifesty nasazení.|Minimální verze aplikace, kterou uživatel může spustit. Tento příznak učiní pojmenovanou verzi aplikace požadovanou aktualizací. Vydáte-li verzi produktu s aktualizací proti narušující změně nebo závažné bezpečnostní chybě, lze pomocí tohoto příznaku určit, že aktualizace musí být nainstalována a že uživatel nemůže nadále používat dřívější verze.<br /><br /> `version`má stejnou sémantiku jako argument příznaku **-Version.**|
|**-n, -Jméno**`nameString`|Nasazení|Všechny typy souborů.|Název použitý pro identifikaci aplikace. ClickOnce použije tento název k identifikaci aplikace v nabídce **Start** (pokud je aplikace nakonfigurována pro samotnou instalaci) a v dialogových oknech Zvýšení oprávnění. **Poznámka:**  Pokud aktualizujete existující manifest a nezadáte název vydavatele s touto volbou, *program Mage.exe* aktualizuje manifest s názvem organizace definovaným v počítači. Chcete-li použít jiný název, použijte tuto možnost a zadejte požadovaný název vydavatele.|
|**-pwd, -Heslo**`passwd`||Všechny typy souborů.|Heslo použité pro podepsání manifestu digitálním certifikátem. Musí být použit ve spojení s volbou **-CertFile.**|
|**-p, Procesor**`processorValue`|Msil|Manifesty aplikací.<br /><br /> Manifesty nasazení.|Architektura mikroprocesoru, na níž bude distribuce spouštěna. Tato hodnota je vyžadována, pokud připravujete jednu nebo více instalací, jejichž sestavení byla předkompilována pro určitý mikroprocesor. Platné hodnoty `msil` `x86`zahrnují `ia64`, `amd64`, a . `msil`je zprostředkující jazyk společnosti Microsoft, což znamená, že všechna sestavení jsou nezávislé na platformě a clr (COMMON Language runtime) bude právě v čase zkompilovat při prvním spuštění aplikace.|
|**-pu,** **-ProviderURL**`url`||Manifesty nasazení.|Určuje adresu URL, na které technologie ClickOnce vyhledá aktualizace aplikace.|
|**-pub, -Vydavatel**`publisherName`||Manifesty aplikací.<br /><br /> Manifesty nasazení.|Přidá název vydavatele do prvku popisu v manifestu nasazení nebo manifestu aplikace. Při použití v manifestu aplikace **-UseManifestForTrust** musí být také zadán s hodnotou "true" nebo "t"; v opačném případě tento parametr vyvolá chybu.|
|**-s, -SupportURL**  `url`||Manifesty aplikací.<br /><br /> Manifesty nasazení.|Určí odkaz, který se pro aplikaci ClickOnce objeví v ovládacím panelu Přidat nebo odebrat programy.|
|**-ti, -TimestampUri**`uri`||Manifesty aplikací.<br /><br /> Manifesty nasazení.|Adresa URL služby vytváření digitálního časového razítka. Vytvoření časového razítka v manifestu umožňuje vyhnout se nutnosti znovu manifesty podepsat, pokud by digitální certifikát vypršel ještě před nasazením další verze aplikace. Další informace naleznete v tématu [Členové programu kořenového certifikátu systému Windows](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn265983(v=ws.11)).|
|**-t, -ToFile**`filePath`|- Nové:<br />- Nasazení: deploy.application<br />- Aplikace: application.exe.manifest<br />- Aktualizace:<br />- Vstupní soubor.|Všechny typy souborů.|Určí výstupní cestu vytvořeného nebo upraveného souboru.<br /><br /> Pokud **-ToFile** není zadán při použití **-New**, výstup je zapsán do aktuálního pracovního adresáře. Pokud **-ToFile** není zadán při použití **-Update**, *Mage.exe* zapíše soubor zpět do vstupního souboru.|
|**-tr, -Úroveň důvěry**`level`|Dle zóny, v níž se adresa URL aplikace nachází.|Manifesty aplikací.|Úroveň důvěryhodnosti, která bude aplikacím udělena na klientských počítačích. Mezi hodnoty patří „Internet“, „Intranet“ a „FullTrust“.|
|**-um, -UseManifestForTrust**`willUseForTrust`|False|Manifesty aplikací.|Určí, zda bude při spuštění aplikace na klientském počítači použit pro rozhodování o důvěryhodnosti digitální podpis manifestu aplikace. Hodnota „true“ nebo „t“ určí, že pro rozhodnutí o důvěryhodnosti bude použit manifest aplikace. Hodnota „false“ nebo „f“ určí, že bude použit podpis manifestu nasazení.|
|**-v, -Verze**`versionNumber`|1.0.0.0|Manifesty aplikací.<br /><br /> Manifesty nasazení.|Verze nasazení. Argument emituje platný řetězec verze formátu*N.N.N.N,,* kde "*N*" je nepodepsané 32bitové celé číslo.|
|**-wpf, -WPFBrowserApp**  `isWPFApp`|false (nepravda)|Manifesty aplikací.<br /><br /> Manifesty nasazení.|Tento příznak použijte pouze tehdy, je-li aplikace aplikací Windows Presentation Foundation (WPF), která bude hostována v aplikaci Internet Explorer a není samostatně spustitelná. Platnými hodnotami jsou „true“ nebo „t“ a „false“ nebo „f“.<br /><br /> Pro manifesty aplikace vloží `hostInBrowser` atribut `entryPoint` pod prvek manifestu aplikace.<br /><br /> Pro manifesty nasazení `install` nastaví `deployment` atribut na prvek na false a uloží manifest nasazení s příponou .xbap. Zadání tohoto argumentu spolu s argumentem **-Install** způsobí chybu, protože aplikace hostovaná prohlížečem nemůže být nainstalovanou offline aplikací.|

## <a name="sign-command-options"></a>Možnosti příkazů Podepsat

V následující tabulce jsou uvedeny možnosti podporované `-Sign` příkazem, které platí pro všechny typy souborů.

|Možnosti|Popis|
|-------------|-----------------|
|**-cf, -CertFile**`filePath`|Určí umístění digitálního certifikátu pro podpis manifestu. Tuto možnost lze použít ve spojení s volbou **-Password,** pokud certifikát vyžaduje heslo pro soubory PFX (Personal Information Exchange). Počínaje rozhraním .NET Framework 4.7, pokud soubor neobsahuje soukromý klíč, je vyžadována kombinace možností **-CryptoProvider** a **-KeyContainer.**<br/><br/>Počínaje rozhraním .NET Framework 4.6.2 se *mage.exe* projevuje s certifikáty CNG a capi.|
|**-ch, -CertHash**`hashSignature`|Hodnota hash digitálního certifikátu uloženého v úložišti osobních certifikátů klientského počítače. Ta odpovídá vlastnosti kryptografického otisku digitálního certifikátu zobrazeného v Konzole certifikátů systému Windows.<br /><br /> `hashSignature`může být velká nebo malá písmena a může být poskytnuta buď jako jeden řetězec nebo s každým oktetem kryptografického potisku odděleného mezerami a celý kryptografický otisk uzavřený v uvozovkách.|
**-csp, -CryptoProvider**`provider-name`|Určuje název zprostředkovatele kryptografických služeb (CSP), který obsahuje kontejner soukromého klíče. Tato možnost vyžaduje možnost **-KeyContainer.**<br/><br/>Tato možnost je k dispozici počínaje rozhraním .NET Framework 4.7.|
|**-kc, -KeyContainer**`name`|Určuje kontejner klíčů, který obsahuje název soukromého klíče. Tato možnost vyžaduje možnost **CryptoProvider.**<br/><br/>Tato možnost je k dispozici počínaje rozhraním .NET Framework 4.7.|
|**-pwd, -Heslo**`passwd`|Heslo použité pro podepsání manifestu digitálním certifikátem. Musí být použit ve spojení s volbou **-CertFile.**|
|**-t, -ToFile**`filePath`|Určí výstupní cestu vytvořeného nebo upraveného souboru.|

## <a name="remarks"></a>Poznámky

Všechny argumenty *pro Mage.exe* jsou malá a velká písmena. Příkazy a možnosti mohou mít předponu pomlčky (-) nebo lomítka (/).

Všechny argumenty použité s příkazem **-Sign** lze použít kdykoli s příkazy **-New** nebo **-Update.** Následující příkazy jsou ekvivalentní.

```console
mage -Sign c:\HelloWorldDeployment\HelloWorld.deploy -CertFile cert.pfx
mage -Update c:\HelloWorldDeployment\HelloWorld.deploy -CertFile cert.pfx
```

> [!NOTE]
> Počínaje rozhraním .NET Framework verze 4.6.2 jsou podporovány také certifikáty CNG.

 Podpis by měl být poslední provedený úkol, protože podepsaný dokument používá hodnotu hash souboru pro ověření, zda je podpis pro dokument platný. Provedete-li v podepsaném souboru nějaké změny, je zapotřebí soubor znovu podepsat. Pokud podepíšete dokument, který byl dříve podepsán, *mage.exe* nahradí starý podpis novým.

 Při použití **-AppManifest** možnost naplnit manifest nasazení, *Mage.exe* bude předpokládat, že manifest aplikace bude umístěn ve stejném adresáři jako manifest nasazení v rámci podadresáře pojmenované po aktuální verzi nasazení a bude nakonfigurovat manifest nasazení odpovídajícím způsobem. Pokud manifest aplikace bude umístěn jinde, použijte možnost **-AppCodeBase** k nastavení alternativního umístění.

 Před nasazením aplikace musí být manifesty nasazení a aplikace podepsány. Pokyny k podepisování manifestů naleznete v [tématu Přehled nasazení důvěryhodných aplikací](/visualstudio/deployment/trusted-application-deployment-overview).

 Možnost **-TrustLevel** pro manifesty aplikací popisuje sadu oprávnění, kterou aplikace vyžaduje ke spuštění v klientském počítači. Ve výchozím nastavení je aplikacím přiřazena úroveň důvěryhodnosti na základě *zóny,* ve které je umístěna jejich adresa URL. Aplikace nasazené přes podnikovou síť jsou obecně umístěny do zóny Intranet, zatímco aplikace nasazené přes internet jsou umístěny do zóny Internet. Obě bezpečnostní zóny omezují přístup aplikace k místním prostředkům, přičemž zóna Intranet je méně restriktivní než zóna Internet. Zóna FullTrust dává aplikacím plný přístup k místním prostředkům počítače. Pokud použijete možnost **-TrustLevel** k umístění aplikace do této zóny, součást Správce důvěryhodnosti clr vyzve uživatele, aby se rozhodl, zda chce udělit tuto vyšší úroveň důvěryhodnosti. Nasazujete-li aplikace přes podnikovou síť, lze úroveň důvěryhodnosti aplikace zvýšit bez dotazování uživatele pomocí technologie Trusted Application Deployment.

 Manifesty aplikací také podporují vlastní oddíly trust. To pomáhá aplikacím podřídit se zásadě bezpečnosti požadovat nejmenší možná oprávnění, protože manifest lze nakonfigurovat tak, aby požadoval pouze specifická oprávnění potřebná ke spuštění aplikace. *Mage.exe* nepodporuje přímo přidání oddílu vlastní důvěryhodnosti. Můžete přidat pomocí textového editoru, analyzátoru XML nebo grafického nástroje *MageUI.exe*. Další informace o použití nástroje *MageUI.exe* k přidání oddílů vlastnídůvěryhodnosti naleznete v [tématu MageUI.exe (Nástroj pro generování a úpravy manifestu, Grafický klient).](mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)

Visual Studio 2017 obsahuje verzi 4.6.1 *programu Mage.exe*. Manifesty vytvořené pomocí této verze cíle *Mage.exe* .NET Framework 4. Chcete-li cílit na starší verze rozhraní .NET Framework, použijte starší verzi programu *Mage.exe*.

Při přidání nebo odebrání sestavení z existujícího manifestu nebo znovu podepsat existující manifest, *Mage.exe* neaktualizuje manifest na cíl .NET Framework 4.

V následujících tabulkách jsou uvedeny tyto funkce a omezení:

|Verze manifestu|Operace|Mage v2.0|Mage v4.0|
|----------------------|---------------|---------------|---------------|
|Manifest pro aplikace určené pro rozhraní .NET Framework verze 2.0 nebo 3.x|Otevřít|OK|OK|
||Zavřít|OK|OK|
||Uložit|OK|OK|
||Znovu podepsat|OK|OK|
||Nová|OK|Nepodporuje se|
||Aktualizovat (viz níže)|OK|OK|
|Manifest pro aplikace cílené na rozhraní .NET Framework verze 4|Otevřít|OK|OK|
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

 Nástroj Mage.exe vytvoří nové manifesty, které cílí na profil klienta rozhraní .NET Framework 4. Aplikace ClickOnce, které cílí na profil klienta rozhraní .NET Framework 4, mohou být spuštěny v profilu klienta rozhraní .NET Framework 4 i v plné verzi rozhraní .NET Framework 4. Pokud vaše aplikace cílí na plnou verzi rozhraní .NET Framework 4 a nelze `<framework>` ji spustit v profilu klienta rozhraní .NET Framework 4, odeberte klientský prvek pomocí textového editoru a znovu podepište manifest.

Následuje ukázkový `<framework>` prvek, který cílí na profil klienta rozhraní .NET Framework 4:

```xml
<framework targetVersion="4.0" profile="client" supportedRuntime="4.0.20506" />
```

## <a name="examples"></a>Příklady

Následující příklad otevře uživatelské rozhraní pro Mage (*MageUI.exe*).

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

Následující příklad vytvoří manifest aplikace naplněný všemi sestaveními a soubory prostředků z aktuálního adresáře a znaménky.

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

Následující příklad podepisuje existující manifest nasazení pomocí digitálního certifikátu a soukromého klíče v aktuálním pracovním adresáři.

```console
mage -Sign deploy.application -CertFile cert.pfx -KeyContainer keyfile.snk -CryptoProvider "Microsoft Enhanced Cryptographic Provider v1.0"
```

## <a name="see-also"></a>Viz také

- [ClickOnce Zabezpečení a nasazení](/visualstudio/deployment/clickonce-security-and-deployment)
- [Návod: Ruční nasazení aplikace ClickOnce](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)
- [Přehled nasazení důvěryhodných aplikací](/visualstudio/deployment/trusted-application-deployment-overview)
- [MageUI.exe (Manifest Generation and Editing Tool, grafický klient)](mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)
- [Příkazové řádky](developer-command-prompt-for-vs.md)
