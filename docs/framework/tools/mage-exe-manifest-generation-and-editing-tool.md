---
title: Mage.exe (generování manifestu a nástroj pro úpravy)
ms.date: 12/06/2018
helpviewer_keywords:
- Manifest Generation and Editing tool
- Mage.exe
ms.assetid: 77dfe576-2962-407e-af13-82255df725a1
ms.openlocfilehash: 9ea293a3c96f193285f45f8d70ac038e785f548a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61921508"
---
# <a name="mageexe-manifest-generation-and-editing-tool"></a>Mage.exe (generování manifestu a nástroj pro úpravy)

Manifest Generation and Editing Tool (*Mage.exe*) je nástroj příkazového řádku, který podporuje vytváření a úpravy manifestů aplikací a nasazení. Jakožto nástroj příkazového řádku *Mage.exe* můžete spouštět z dávkových skriptů a aplikacím na základě Windows, včetně [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] aplikací.

Můžete také použít *MageUI.exe*, grafické aplikace namísto *Mage.exe*. Další informace najdete v tématu [MageUI.exe (Manifest Generation and Editing Tool, grafický klient)](../../../docs/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md).

Tento nástroj je automaticky nainstalován se sadou Visual Studio. Ke spuštění nástroje, pomocí příkazového řádku pro vývojáře pro sadu Visual Studio. Další informace najdete v tématu [příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md).

Dvě verze *Mage.exe* a *MageUI.exe* jsou součástí sady Visual Studio. Chcete-li zobrazit informace o verzi, spusťte *MageUI.exe*vyberte **pomáhají**a vyberte **o**. Tato dokumentace popisuje verzi 4.0.x.x nástrojů *Mage.exe* a *MageUI.exe*.

## <a name="syntax"></a>Syntaxe

```console
Mage [commands] [commandOptions]
```

## <a name="parameters"></a>Parametry

Následující tabulka ukazuje příkazy podporované *Mage.exe*. Další informace o možnostech podporovaných těmito příkazy naleznete v tématu [možnosti příkazu New a Update](#new-and-update-command-options) a [možnosti příkazu Sign](#sign-command-options).

|Příkaz|Popis|
|-------------|-----------------|
|**-cc, ClearApplicationCache**|Odstraní všechny aplikace fungující pouze v režimu online z mezipaměti stažených aplikací.|
|**-n, - nové** *fileType [newOptions]*|Vytvoří nový soubor daného typu. Platnými typy jsou:<br /><br /> -   `Deployment`: Vytvoří nový manifest nasazení.<br />-   `Application`: Vytvoří nový manifest aplikace.<br /><br /> Nezadáte-li s tímto příkazem žádné další parametry, bude vytvořen soubor odpovídajícího typu s odpovídajícími výchozími značkami a hodnotami atributů.<br /><br /> Použití **- ToFile** možnost (dle následující tabulky) a zadat název souboru a cestu nového souboru.<br /><br /> Použití **- FromDirectory** možnost (dle následující tabulky) k vytvoření manifestu aplikace se všemi sestaveními aplikace přidanými do \<závislost > části manifestu.|
|**-u,-aktualizace** *[cesta] [volby pro aktualizaci]*|Provede jednu nebo více změn souboru manifestu. Typ upravovaného souboru není třeba zadávat. Nástroj Mage.exe soubor zkontroluje sadou heuristik a určí, zda jde o manifest nasazení nebo manifest aplikace.<br /><br /> Pokud jste se už zaregistrovali soubor s certifikátem, **– aktualizace** odebere blok s podpisem klíče. Důvodem je skutečnost, že podpis klíče obsahuje hodnotu hash souboru, která je úpravou souboru zneplatněna.<br /><br /> Použití **- ToFile** možnost (dle následující tabulky) a zadat nový název souboru a cestu, místo abyste přepsali tu stávající soubor.|
|**-s,-Sign** `[signOptions]`|Použije k podpisu souboru pár klíčů nebo certifikát X509. Podpisy jsou do souboru vloženy jako prvky jazyka XML.<br /><br /> Musíte být připojeni k Internetu při podpisu manifestu určujícího **- TimestampUri** hodnotu.|
|**-ver, -Verify** *[manifest-filename]*|Ověřuje, jestli je správně podepsaný manifestu. Nelze kombinovat s jinými příkazy. <br/><br/>**K dispozici v rozhraní .NET Framework 4.7 a novějších verzích.**|
|**-h,-? –, pomáhají** *[podrobné]*|Popíše všechny dostupné příkazy a jejich možnosti. Zadejte `verbose` podrobnou nápovědu.|

## <a name="new-and-update-command-options"></a>Nové a aktualizovat možnosti příkazu

V následující tabulce jsou uvedeny možnosti podporované `-New` a `-Update` příkazy:

|Možnosti|Výchozí hodnota|Platí pro|Popis|
|-------------|-------------------|----------------|-----------------|
|**-a-algoritmus**|sha1RSA|Manifesty aplikací.<br /><br /> Manifesty nasazení.|Určí algoritmus, jímž budou generovány přehledy závislostí. Hodnotou musí být „sha256RSA“ nebo „sha1RSA“.<br /><br /> Použijte s možností „-Update“. Při použití možnosti „-Sign“ je tato možnost ignorována.|
|**-appc, -AppCodeBase** `manifestReference`||Manifesty nasazení.|Vloží odkaz na adresu URL nebo cestu k souboru do souboru manifestu aplikace. Touto hodnotou musí být úplná cesta k manifestu aplikace.|
|**-appm, -AppManifest** `manifestPath`||Manifesty nasazení.|Vloží do manifestu nasazení odkaz na manifest aplikace tohoto nasazení.<br /><br /> Soubor indikován `manifestPath` musí existovat nebo *Mage.exe* dojde k chybě. Je-li soubor odkazovaný parametrem `manifestPath` není manifest aplikace *Mage.exe* dojde k chybě.|
|**-cf, -CertFile** `filePath`||Všechny typy souborů.|Určuje umístění x X509 digitálního certifikátu pro podpis manifestu nebo licenční soubor. Tato možnost se dá použít ve spojení s **– heslo** pokud certifikátu vyžaduje heslo pro soubory Personal Information Exchange (PFX). Od verze rozhraní .NET Framework 4.7, pokud soubor neobsahuje privátní klíč, kombinaci **- CryptoProvider** a **- KeyContainer** možnosti je povinný.<br/><br/>Od verze rozhraní .NET Framework 4.6.2, *Mage.exe* manifesty znaménka s CNG, jakož i CAPI certifikáty.|
|**-ch, -CertHash** `hashSignature`||Všechny typy souborů.|Hodnota hash digitálního certifikátu uloženého v úložišti osobních certifikátů klientského počítače. Ta odpovídá řetězci kryptografického otisku digitálního certifikátu zobrazeného v Konzole certifikátů systému Windows.<br /><br /> `hashSignature` může být buď velká nebo malá písmena a může být zadán buď jako jeden řetězec, nebo kryptografický otisk odděleny mezer a kryptografický otisk uzavřený do uvozovek, jehož každý.|
|**-csp, -CryptoProvider** `provider-name`||Všechny typy souborů.|Určuje název zprostředkovatele kryptografických služeb (CSP), který obsahuje kontejner soukromého klíče. Tato možnost vyžaduje **- KeyContainer** možnost.<br/><br/>Tato možnost je k dispozici od verze rozhraní .NET Framework 4.7.|
|**-fd, -FromDirectory** `directoryPath`||Manifesty aplikací.|Naplní manifest aplikace popisy všech sestavení a souborů nalezených v `directoryPath`, včetně všech podadresářů, kde `directoryPath` je adresář obsahující aplikaci, kterou chcete nasadit. Pro každý soubor v adresáři *Mage.exe* rozhodne, zda je soubor sestavení nebo o statický soubor. Pokud je sestavení, přidá `<dependency>` značky a `installFrom` atribut k aplikaci s názvem, základem kódu a verzí sestavení. Pokud jde o statický soubor, přidá `<file>` značky. *Mage.exe* také použije jednoduchou sadu heuristik ke zjištění hlavního spustitelného souboru pro aplikaci a označí jako vstupní bod aplikace ClickOnce v manifestu.<br /><br /> *Mage.exe* se nikdy automaticky označit soubor jako soubor "data". To je zapotřebí provést ručně. Další informace najdete v tématu [jak: Zahrnutí datového souboru do aplikace ClickOnce](/visualstudio/deployment/how-to-include-a-data-file-in-a-clickonce-application).<br /><br /> *Mage.exe* také vygeneruje hodnotu hash pro každý soubor na základě jeho velikosti. Technologie ClickOnce těmito hodnotami hash zajišťuje, že se soubory nasazení nikdo od vytvoření manifestu nemanipuloval. Je-li změnit některý ze souborů ve vašem nasazení, můžete spustit *Mage.exe* s **– aktualizovat** příkazu a **- FromDirectory** možnost a aktualizuje hodnoty hash a sestavení verze všech odkazovaných souborů.<br /><br /> **-FromDirectory** zahrne všechny soubory ve všech podadresářích v rámci nebyl nalezen `directoryPath`.<br /><br /> Pokud používáte **- FromDirectory** s **– aktualizace** příkazu *Mage.exe* odebere všechny soubory v manifestu aplikace, která již existuje v adresáři.|
|**-if - IconFile**  `filePath`||Manifesty aplikací.|Určí úplnou cestu k souboru ikony .ICO. Tato ikona se zobrazuje vedle názvu aplikace v nabídce Start a v jejím záznamu v ovládacím panelu Přidat nebo odebrat programy. Není-li zadána žádná ikona, je použita ikona výchozí.|
|**-ip, -IncludeProviderURL**  `url`|true|Manifesty nasazení.|Označuje, zda manifest nasazení zahrnuje hodnotu umístění aktualizace nastavenou **- ProviderURL**.|
|**-i,-instalace** `willInstall`|true|Manifesty nasazení.|Označuje, zda by aplikace ClickOnce měla být nainstalována na místní počítač nebo spuštěna z webu. Instalace aplikace jí umožňuje mít zástupce v Windows **Start** nabídky. Platnými hodnotami jsou „true“ nebo „t“ a „false“ nebo „f“.<br /><br /> Pokud zadáte **- MinVersion** možnost a uživatel má verzi nižší než **- MinVersion** nainstalované, vynutí aplikaci pro instalaci, bez ohledu na hodnotu, kterou předat **– Nainstalujte**.<br /><br /> Tento parametr nelze použít s **- BrowserHosted** možnost. Pokus zadat obě možnosti pro stejný manifest vyústí v chybu.|
|**-kc, -KeyContainer** `name`||Všechny typy souborů.|Určuje kontejner klíčů, který obsahuje název privátní klíč. Tato možnost vyžaduje **CyproProvider** možnost.<br/><br/>Tato možnost je k dispozici od verze rozhraní .NET Framework 4.7.|
|**-mv - MinVersion**  `[version]`|Verze uvedená v manifestu nasazení ClickOnce tak jak jsou určené **– verze** příznak.|Manifesty nasazení.|Minimální verze aplikace, kterou uživatel může spustit. Tento příznak učiní pojmenovanou verzi aplikace požadovanou aktualizací. Vydáte-li verzi produktu s aktualizací proti narušující změně nebo závažné bezpečnostní chybě, lze pomocí tohoto příznaku určit, že aktualizace musí být nainstalována a že uživatel nemůže nadále používat dřívější verze.<br /><br /> `version` má stejnou sémantiku jako argument **– verze** příznak.|
|**-n, – název** `nameString`|Nasazení|Všechny typy souborů.|Název použitý pro identifikaci aplikace. Technologie ClickOnce použije tento název k identifikaci aplikace v **Start** nabídce (Pokud je aplikace nakonfigurována k instalaci) a v dialogových oknech zvýšení oprávnění. **Poznámka:**  Pokud aktualizujete existující manifest a nezadáte s touto možností název vydavatele *Mage.exe* aktualizuje manifest názvem organizace definovaným v počítači. Chcete-li použít jiný název, použijte tuto možnost a zadejte požadovaný název vydavatele.|
|**-pwd, -Password** `passwd`||Všechny typy souborů.|Heslo použité pro podepsání manifestu digitálním certifikátem. Je potřeba použít ve spojení s **- CertFile** možnost.|
|**Procesor -p,** `processorValue`|Msil|Manifesty aplikací.<br /><br /> Manifesty nasazení.|Architektura mikroprocesoru, na níž bude distribuce spouštěna. Tato hodnota je vyžadována, pokud připravujete jednu nebo více instalací, jejichž sestavení byla předkompilována pro určitý mikroprocesor. Platné hodnoty jsou `msil`, `x86`, `ia64`, a `amd64`. `msil` je Microsoft intermediate language, což znamená, že sestavení jsou nezávislá na platformě a common language runtime (CLR) bude just-in-time jejich kompilace, když je vaše aplikace při prvním spuštění.|
|**-pu,** **- ProviderURL** `url`||Manifesty nasazení.|Určuje adresu URL, na které technologie ClickOnce vyhledá aktualizace aplikace.|
|**-pub, -Publisher** `publisherName`||Manifesty aplikací.<br /><br /> Manifesty nasazení.|Přidá název vydavatele do prvku popisu v manifestu nasazení nebo manifestu aplikace. Pokud se použije pro manifest aplikace **- UseManifestForTrust** musí být také zadána s hodnotu "true" nebo "t"; v opačném případě tento parametr vyvolá chybu.|
|**-s, - SupportURL**  `url`||Manifesty aplikací.<br /><br /> Manifesty nasazení.|Určí odkaz, který se pro aplikaci ClickOnce objeví v ovládacím panelu Přidat nebo odebrat programy.|
|**-ti, -TimestampUri** `uri`||Manifesty aplikací.<br /><br /> Manifesty nasazení.|Adresa URL služby vytváření digitálního časového razítka. Vytvoření časového razítka v manifestu umožňuje vyhnout se nutnosti znovu manifesty podepsat, pokud by digitální certifikát vypršel ještě před nasazením další verze aplikace. Další informace najdete v tématu [Windows Členové programu kořenového certifikátu](https://go.microsoft.com/fwlink/?LinkId=159000).|
|**-t, -ToFile** `filePath`|-Nové:<br />-Nasazení: deploy.application<br />-Aplikace: application.exe.manifest<br />-Aktualizace:<br />-Vstupní soubor.|Všechny typy souborů.|Určí výstupní cestu vytvořeného nebo upraveného souboru.<br /><br /> Pokud **- ToFile** není zadán, pokud použijete **– nové**, výstup bude zapsán do aktuálního pracovního adresáře. Pokud **- ToFile** není zadán, pokud použijete **– aktualizace**, *Mage.exe* zapíše soubor zpět do vstupního souboru.|
|**-tr, - TrustLevel** `level`|Dle zóny, v níž se adresa URL aplikace nachází.|Manifesty aplikací.|Úroveň důvěryhodnosti, která bude aplikacím udělena na klientských počítačích. Mezi hodnoty patří „Internet“, „Intranet“ a „FullTrust“.|
|**-um, -UseManifestForTrust** `willUseForTrust`|False|Manifesty aplikací.|Určí, zda bude při spuštění aplikace na klientském počítači použit pro rozhodování o důvěryhodnosti digitální podpis manifestu aplikace. Hodnota „true“ nebo „t“ určí, že pro rozhodnutí o důvěryhodnosti bude použit manifest aplikace. Hodnota „false“ nebo „f“ určí, že bude použit podpis manifestu nasazení.|
|**-v, -Version** `versionNumber`|1.0.0.0|Manifesty aplikací.<br /><br /> Manifesty nasazení.|Verze nasazení. Argument musí být platný řetězec verze ve formátu "*N.N.N.N*", kde"*N*" je 32bitové celé číslo bez znaménka.|
|**-wpf, -WPFBrowserApp**  `isWPFApp`|false|Manifesty aplikací.<br /><br /> Manifesty nasazení.|Tento příznak použijte pouze tehdy, je-li aplikace aplikací Windows Presentation Foundation (WPF), která bude hostována v aplikaci Internet Explorer a není samostatně spustitelná. Platnými hodnotami jsou „true“ nebo „t“ a „false“ nebo „f“.<br /><br /> Pro manifesty aplikací vloží `hostInBrowser` atribut `entryPoint` elementu v manifestu aplikace.<br /><br /> Manifesty nasazení nastaví `install` atribut na `deployment` prvku na hodnotu false a uloží manifest s příponou .xbap. Zadání tohoto argumentu spolu s **– instalace** dojde k chybě, protože aplikace hostované prohlížečem nemůže být instalovanou offline aplikací.|

## <a name="sign-command-options"></a>Možnosti příkazu Sign

V následující tabulce jsou uvedeny možnosti podporované `-Sign` příkaz, který platí pro všechny typy souborů.

|Možnosti|Popis|
|-------------|-----------------|
|**-cf, -CertFile** `filePath`|Určí umístění digitálního certifikátu pro podpis manifestu. Tato možnost se dá použít ve spojení s **– heslo** pokud certifikátu vyžaduje heslo pro soubory Personal Information Exchange (PFX). Od verze rozhraní .NET Framework 4.7, pokud soubor neobsahuje privátní klíč, kombinaci **- CryptoProvider** a **- KeyContainer** možnosti je povinný.<br/><br/>Od verze rozhraní .NET Framework 4.6.2, *Mage.exe* manifesty znaménka s CNG, jakož i CAPI certifikáty.|
|**-ch, -CertHash** `hashSignature`|Hodnota hash digitálního certifikátu uloženého v úložišti osobních certifikátů klientského počítače. Ta odpovídá vlastnosti kryptografického otisku digitálního certifikátu zobrazeného v Konzole certifikátů systému Windows.<br /><br /> `hashSignature` může být buď velká nebo malá písmena a může být zadán buď jako jeden řetězec, nebo kryptografický otisk odděleny mezer a kryptografický otisk uzavřený do uvozovek, jehož každý.|
**-csp, -CryptoProvider** `provider-name`|Určuje název zprostředkovatele kryptografických služeb (CSP), který obsahuje kontejner soukromého klíče. Tato možnost vyžaduje **- KeyContainer** možnost.<br/><br/>Tato možnost je k dispozici od verze rozhraní .NET Framework 4.7.|
|**-kc, -KeyContainer** `name`|Určuje kontejner klíčů, který obsahuje název privátní klíč. Tato možnost vyžaduje **CyproProvider** možnost.<br/><br/>Tato možnost je k dispozici od verze rozhraní .NET Framework 4.7.|
|**-pwd, -Password** `passwd`|Heslo použité pro podepsání manifestu digitálním certifikátem. Je potřeba použít ve spojení s **- CertFile** možnost.|
|**-t, -ToFile** `filePath`|Určí výstupní cestu vytvořeného nebo upraveného souboru.|

## <a name="remarks"></a>Poznámky

Všechny argumenty *Mage.exe* rozlišují velikost písmen. Příkazy a možnosti mohou mít předponu pomlčky (-) nebo lomítka (/).

Všechny argumenty použité s **-Sign** příkazu je možné kdykoli s **– nové** nebo **– aktualizace** i příkazy. Následující příkazy jsou ekvivalentní.

```console
mage -Sign c:\HelloWorldDeployment\HelloWorld.deploy -CertFile cert.pfx
mage -Update c:\HelloWorldDeployment\HelloWorld.deploy -CertFile cert.pfx
```

> [!NOTE]
> Od verze rozhraní .NET Framework verze 4.6.2, CNG certifikáty jsou také podporovány.

 Podpis by měl být poslední provedený úkol, protože podepsaný dokument používá hodnotu hash souboru pro ověření, zda je podpis pro dokument platný. Provedete-li v podepsaném souboru nějaké změny, je zapotřebí soubor znovu podepsat. Pokud se dokument, který byl dříve podepsaný *Mage.exe* nahradí starý podpis s novými.

 Při použití **- AppManifest** možnost k naplnění manifestu nasazení, *Mage.exe* bude předpokládat, že manifest aplikace se bude nacházet ve stejném adresáři jako nasazení v rámci manifestu podadresář s názvem po aktuální verze nasazení a bude odpovídajícím způsobem nakonfigurovat manifestu nasazení. Pokud manifest aplikace bude umístěn jinde, použijte **- AppCodeBase** možnost nastavit alternativního umístění.

 Před nasazením aplikace musí být manifesty nasazení a aplikace podepsány. Informace o podepisování manifestů naleznete v tématu [Trusted Application Deployment Overview](/visualstudio/deployment/trusted-application-deployment-overview).

 **- TrustLevel** možnost pro manifesty aplikací popisuje sadu oprávnění, která aplikace vyžaduje pro spuštění v klientském počítači. Ve výchozím nastavení je aplikacím přiřazena úroveň důvěryhodnosti dle *zóny* ve kterém se nachází jejich adresa URL. Aplikace nasazené přes podnikovou síť jsou obecně umístěny do zóny Intranet, zatímco aplikace nasazené přes internet jsou umístěny do zóny Internet. Obě bezpečnostní zóny omezují přístup aplikace k místním prostředkům, přičemž zóna Intranet je méně restriktivní než zóna Internet. Zóna FullTrust dává aplikacím plný přístup k místním prostředkům počítače. Pokud používáte **- TrustLevel** umožňuje umístění aplikace do této zóny, komponenta správce důvěryhodnosti modulu CLR se zobrazí výzva se rozhodnout, jestli uživatel chce tuto vyšší úroveň důvěryhodnosti. Nasazujete-li aplikace přes podnikovou síť, lze úroveň důvěryhodnosti aplikace zvýšit bez dotazování uživatele pomocí technologie Trusted Application Deployment.

 Manifesty aplikací také podporují vlastní oddíly trust. To pomáhá aplikacím podřídit se zásadě bezpečnosti požadovat nejmenší možná oprávnění, protože manifest lze nakonfigurovat tak, aby požadoval pouze specifická oprávnění potřebná ke spuštění aplikace. *Mage.exe* přímo nepodporuje přidávání vlastních oddílů trust. Můžete přidat pomocí textového editoru, analyzátoru jazyka XML nebo grafického nástroje *MageUI.exe*. Další informace o tom, jak používat *MageUI.exe* přidání vlastních oddílů trust naleznete v tématu [MageUI.exe (Manifest Generation and Editing Tool, grafický klient)](../../../docs/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md).

Visual Studio 2017 obsahuje verzi 4.6.1 *Mage.exe*. Manifesty vytvořené v této verzi *Mage.exe* cílit na .NET Framework 4. Pokud chcete cíleny na starší verze rozhraní .NET Framework, použijte dřívější verzi *Mage.exe*.

Při přidání nebo odebrání sestavení z existujícího manifestu nebo znovu podepsat manifest existující *Mage.exe* neaktualizuje manifest pro cílové rozhraní .NET Framework 4.

Následující tabulky ukazují tyto funkce a omezení:

|Verze manifestu|Operace|Mage v2.0|Mage v4.0|
|----------------------|---------------|---------------|---------------|
|Manifest pro aplikace určené pro rozhraní .NET Framework verze 2.0 nebo 3.x|Otevřít|OK|OK|
||Zavřít|OK|OK|
||Uložit|OK|OK|
||Znovu podepsat|OK|OK|
||Nový|OK|Není podporováno|
||Aktualizovat (viz níže)|OK|OK|
|Manifest pro aplikace cílené na rozhraní .NET Framework verze 4|Otevřít|OK|OK|
||Zavřít|OK|OK|
||Uložit|OK|OK|
||Znovu podepsat|OK|OK|
||Nový|Není podporováno|OK|
||Aktualizovat (viz níže)|Není podporováno|OK|

|Verze manifestu|Podrobnosti o operaci Aktualizovat|Mage v2.0|Mage v4.0|
|----------------------|------------------------------|---------------|---------------|
|Manifest pro aplikace určené pro rozhraní .NET Framework verze 2.0 nebo 3.x|Upravit sestavení|OK|OK|
||Přidat sestavení|OK|OK|
||Odstranit sestavení|OK|OK|
|Manifest pro aplikace cílené na rozhraní .NET Framework verze 4|Upravit sestavení|Není podporováno|OK|
||Přidat sestavení|Není podporováno|OK|
||Odstranit sestavení|Není podporováno|OK|

 Mage.exe vytváří nové manifesty, které se zaměřují [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]. Aplikace ClickOnce, které se zaměřují [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)] mohou být spuštěny v rozhraní [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)] a plnou verzi rozhraní .NET Framework 4. Pokud vaše aplikace cílí na plnou verzi rozhraní .NET Framework 4 a nelze je spustit na [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)], odeberte klienta `<framework>` element pomocí textového editoru a znovu podepište manifest.

Tady je ukázka `<framework>` element, který se zaměřuje [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]:

```xml
<framework targetVersion="4.0" profile="client" supportedRuntime="4.0.20506" />
```

## <a name="examples"></a>Příklady

Následující příklad otevře uživatelské rozhraní nástroje Mage (*MageUI.exe*).

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

Následující příklad vytvoří manifest aplikace naplněný všemi sestaveními a soubory prostředků z aktuálního adresáře a symboly.

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
mage -Sign deploy.application -CertFile cert.pfx -KeyContainer keyfile.snk -CryptoProvider "Microsoft Enghanced Cryptographic Provider v1.0"
```

## <a name="see-also"></a>Viz také:

- [ClickOnce – zabezpečení a nasazení](/visualstudio/deployment/clickonce-security-and-deployment)
- [Návod: Ruční nasazení aplikace ClickOnce](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)
- [Přehled nasazení důvěryhodných aplikací](/visualstudio/deployment/trusted-application-deployment-overview)
- [MageUI.exe (Manifest Generation and Editing Tool, grafický klient)](../../../docs/framework/tools/mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)
- [Příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md)