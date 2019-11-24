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

The Manifest Generation and Editing Tool (*Mage.exe*) is a command-line tool that supports the creation and editing of application and deployment manifests. As a command-line tool, *Mage.exe* can be run from both batch scripts and other Windows-based applications, including ASP.NET applications.

You can also use *MageUI.exe*, a graphical application, instead of *Mage.exe*. For more information, see [MageUI.exe (Manifest Generation and Editing Tool, Graphical Client)](mageui-exe-manifest-generation-and-editing-tool-graphical-client.md).

Tento nástroj je automaticky nainstalován se sadou Visual Studio. To run the tool, use Developer Command Prompt for Visual Studio. For more information, see [Command Prompts](developer-command-prompt-for-vs.md).

Two versions of *Mage.exe* and *MageUI.exe* are included with Visual Studio. To see version information, run *MageUI.exe*, select **Help**, and select **About**. This documentation describes version 4.0.x.x of *Mage.exe* and *MageUI.exe*.

## <a name="syntax"></a>Syntaxe

```console
Mage [commands] [commandOptions]
```

## <a name="parameters"></a>Parametry

The following table shows the commands supported by *Mage.exe*. For more information about the options supported by these commands, see [New and Update command options](#new-and-update-command-options) and [Sign command options](#sign-command-options).

|Příkaz|Popis|
|-------------|-----------------|
|**-cc, ClearApplicationCache**|Odstraní všechny aplikace fungující pouze v režimu online z mezipaměti stažených aplikací.|
|**-n, -New** *fileType [newOptions]*|Vytvoří nový soubor daného typu. Platnými typy jsou:<br /><br /> -   `Deployment`: Creates a new deployment manifest.<br />-   `Application`: Creates a new application manifest.<br /><br /> Nezadáte-li s tímto příkazem žádné další parametry, bude vytvořen soubor odpovídajícího typu s odpovídajícími výchozími značkami a hodnotami atributů.<br /><br /> Use the **-ToFile** option (see in the following table) to specify the file name and path of the new file.<br /><br /> Use the **-FromDirectory** option (see in the following table) to create an application manifest with all of the assemblies for an application added to the \<dependency> section of the manifest.|
|**-u, -Update** *[filePath] [updateOptions]*|Provede jednu nebo více změn souboru manifestu. Typ upravovaného souboru není třeba zadávat. Nástroj Mage.exe soubor zkontroluje sadou heuristik a určí, zda jde o manifest nasazení nebo manifest aplikace.<br /><br /> If you have already signed a file with a certificate, **-Update** will remove the key signature block. Důvodem je skutečnost, že podpis klíče obsahuje hodnotu hash souboru, která je úpravou souboru zneplatněna.<br /><br /> Use the **-ToFile** option (see in the following table) to specify a new file name and path instead of overwriting the existing file.|
|**-s, -Sign** `[signOptions]`|Použije k podpisu souboru pár klíčů nebo certifikát X509. Podpisy jsou do souboru vloženy jako prvky jazyka XML.<br /><br /> You must be connected to the Internet when signing a manifest that specifies a **-TimestampUri** value.|
|**-ver, -Verify** *[manifest-filename]*|Verifies that the manifest is signed correctly. Cannot be combined with other commands. <br/><br/>**Available in .NET Framework 4.7 and later versions.**|
|**-h, -?, -Help** *[verbose]*|Popíše všechny dostupné příkazy a jejich možnosti. Specify `verbose` to get detailed help.|

## <a name="new-and-update-command-options"></a>New and Update command options

The following table shows the options supported by the `-New` and `-Update` commands:

|Možnosti|Výchozí hodnota|Platí pro|Popis|
|-------------|-------------------|----------------|-----------------|
|**-a, -Algorithm**|sha1RSA|Manifesty aplikací.<br /><br /> Manifesty nasazení.|Určí algoritmus, jímž budou generovány přehledy závislostí. Hodnotou musí být „sha256RSA“ nebo „sha1RSA“.<br /><br /> Použijte s možností „-Update“. Při použití možnosti „-Sign“ je tato možnost ignorována.|
|**-appc, -AppCodeBase** `manifestReference`||Manifesty nasazení.|Vloží odkaz na adresu URL nebo cestu k souboru do souboru manifestu aplikace. Touto hodnotou musí být úplná cesta k manifestu aplikace.|
|**-appm, -AppManifest** `manifestPath`||Manifesty nasazení.|Vloží do manifestu nasazení odkaz na manifest aplikace tohoto nasazení.<br /><br /> The file indicated by `manifestPath` must exist, or *Mage.exe* will issue an error. If the file referenced by `manifestPath` is not an application manifest, *Mage.exe* will issue an error.|
|**-cf, -CertFile** `filePath`||Všechny typy souborů.|Specifies the location of an X509 digital certificate for signing a manifest or license file. This option can be used in conjunction with the **-Password** option if the certificate requires a password for Personal Information Exchange (PFX) files. Starting with .NET Framework 4.7, if the file does not contain a private key, a combination of the **-CryptoProvider** and **-KeyContainer** options is required.<br/><br/>Starting with .NET Framework 4.6.2, *Mage.exe* signs manifests with CNG as well as CAPI certificates.|
|**-ch, -CertHash** `hashSignature`||Všechny typy souborů.|Hodnota hash digitálního certifikátu uloženého v úložišti osobních certifikátů klientského počítače. Ta odpovídá řetězci kryptografického otisku digitálního certifikátu zobrazeného v Konzole certifikátů systému Windows.<br /><br /> `hashSignature` can be either uppercase or lowercase, and can be supplied either as a single string, or with each octet of the Thumbprint separated by spaces and the entire Thumbprint enclosed in quotation marks.|
|**-csp, -CryptoProvider** `provider-name`||Všechny typy souborů.|Specifies the name of a cryptographic service provider (CSP) that contains the private key container. This option requires the **-KeyContainer** option.<br/><br/>This option is available starting with .NET Framework 4.7.|
|**-fd, -FromDirectory** `directoryPath`||Manifesty aplikací.|Populates the application manifest with descriptions of all assemblies and files found in `directoryPath`, including all subdirectories, where `directoryPath` is the directory that contains the application that you want to deploy. For each file in the directory, *Mage.exe* decides whether the file is an assembly or a static file. If it is an assembly, it adds a `<dependency>` tag and `installFrom` attribute to the application with the assembly's name, code base, and version. If it is a static file, it adds a `<file>` tag. *Mage.exe* will also use a simple set of heuristics to detect the main executable for the application, and will mark it as the ClickOnce application's entry point in the manifest.<br /><br /> *Mage.exe* will never automatically mark a file as a "data" file. To je zapotřebí provést ručně. For more information, see [How to: Include a Data File in a ClickOnce Application](/visualstudio/deployment/how-to-include-a-data-file-in-a-clickonce-application).<br /><br /> *Mage.exe* also generates a hash for each file based on its size. Technologie ClickOnce těmito hodnotami hash zajišťuje, že se soubory nasazení nikdo od vytvoření manifestu nemanipuloval. If any of the files in your deployment change, you can run *Mage.exe* with the **-Update** command and the **-FromDirectory** option, and it will update the hashes and assembly versions of all referenced files.<br /><br /> **-FromDirectory** will include all files in all subdirectories found within `directoryPath`.<br /><br /> If you use **-FromDirectory** with the **-Update** command, *Mage.exe* will remove any files in the application manifest that no longer exist in the directory.|
|**-if, -IconFile**  `filePath`||Manifesty aplikací.|Určí úplnou cestu k souboru ikony .ICO. Tato ikona se zobrazuje vedle názvu aplikace v nabídce Start a v jejím záznamu v ovládacím panelu Přidat nebo odebrat programy. Není-li zadána žádná ikona, je použita ikona výchozí.|
|**-ip, -IncludeProviderURL**  `url`|true|Manifesty nasazení.|Indicates whether the deployment manifest includes the update location value set by **-ProviderURL**.|
|**-i, -Install** `willInstall`|true|Manifesty nasazení.|Označuje, zda by aplikace ClickOnce měla být nainstalována na místní počítač nebo spuštěna z webu. Installing an application gives that application a presence in the Windows **Start** menu. Platnými hodnotami jsou „true“ nebo „t“ a „false“ nebo „f“.<br /><br /> If you specify the **-MinVersion** option, and a user has a version less than **-MinVersion** installed, it will force the application to install, regardless of the value that you pass to **-Install**.<br /><br /> This option cannot be used with the **-BrowserHosted** option. Pokus zadat obě možnosti pro stejný manifest vyústí v chybu.|
|**-kc, -KeyContainer** `name`||Všechny typy souborů.|Specifies the key container that contains the name of the private key. This option requires the **CryptoProvider** option.<br/><br/>This option is available starting with .NET Framework 4.7.|
|**-mv, -MinVersion**  `[version]`|The version listed in the ClickOnce deployment manifest as specified by the **-Version** flag.|Manifesty nasazení.|Minimální verze aplikace, kterou uživatel může spustit. Tento příznak učiní pojmenovanou verzi aplikace požadovanou aktualizací. Vydáte-li verzi produktu s aktualizací proti narušující změně nebo závažné bezpečnostní chybě, lze pomocí tohoto příznaku určit, že aktualizace musí být nainstalována a že uživatel nemůže nadále používat dřívější verze.<br /><br /> `version` has the same semantics as the argument to the **-Version** flag.|
|**-n, -Name** `nameString`|Nasazení|Všechny typy souborů.|Název použitý pro identifikaci aplikace. ClickOnce will use this name to identify the application in the **Start** menu (if the application is configured to install itself) and in Permission Elevation dialog boxes. **Note:**  If you are updating an existing manifest and you do not specify a publisher name with this option, *Mage.exe* updates the manifest with the organization name defined on the computer. Chcete-li použít jiný název, použijte tuto možnost a zadejte požadovaný název vydavatele.|
|**-pwd, -Password** `passwd`||Všechny typy souborů.|Heslo použité pro podepsání manifestu digitálním certifikátem. Must be used in conjunction with the **-CertFile** option.|
|**-p, Processor** `processorValue`|Msil|Manifesty aplikací.<br /><br /> Manifesty nasazení.|Architektura mikroprocesoru, na níž bude distribuce spouštěna. Tato hodnota je vyžadována, pokud připravujete jednu nebo více instalací, jejichž sestavení byla předkompilována pro určitý mikroprocesor. Valid values include `msil`, `x86`, `ia64`, and `amd64`. `msil` is Microsoft intermediate language, which means all of your assemblies are platform-independent, and the common language runtime (CLR) will just-in-time compile them when your application is first run.|
|**-pu,** **-ProviderURL** `url`||Manifesty nasazení.|Určuje adresu URL, na které technologie ClickOnce vyhledá aktualizace aplikace.|
|**-pub, -Publisher** `publisherName`||Manifesty aplikací.<br /><br /> Manifesty nasazení.|Přidá název vydavatele do prvku popisu v manifestu nasazení nebo manifestu aplikace. When used on an application manifest, **-UseManifestForTrust** must also be specified with a value of "true" or "t"; otherwise, this parameter will raise an error.|
|**-s, -SupportURL**  `url`||Manifesty aplikací.<br /><br /> Manifesty nasazení.|Určí odkaz, který se pro aplikaci ClickOnce objeví v ovládacím panelu Přidat nebo odebrat programy.|
|**-ti, -TimestampUri** `uri`||Manifesty aplikací.<br /><br /> Manifesty nasazení.|Adresa URL služby vytváření digitálního časového razítka. Vytvoření časového razítka v manifestu umožňuje vyhnout se nutnosti znovu manifesty podepsat, pokud by digitální certifikát vypršel ještě před nasazením další verze aplikace. For more information, see [Windows root certificate program members](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn265983(v=ws.11)).|
|**-t, -ToFile** `filePath`|-   New:<br />-   Deployment: deploy.application<br />-   Application: application.exe.manifest<br />-   Update:<br />-   The input file.|Všechny typy souborů.|Určí výstupní cestu vytvořeného nebo upraveného souboru.<br /><br /> If **-ToFile** is not supplied when you use **-New**, the output is written to the current working directory. If **-ToFile** is not supplied when you use **-Update**, *Mage.exe* will write the file back to the input file.|
|**-tr, -TrustLevel** `level`|Dle zóny, v níž se adresa URL aplikace nachází.|Manifesty aplikací.|Úroveň důvěryhodnosti, která bude aplikacím udělena na klientských počítačích. Mezi hodnoty patří „Internet“, „Intranet“ a „FullTrust“.|
|**-um, -UseManifestForTrust** `willUseForTrust`|False|Manifesty aplikací.|Určí, zda bude při spuštění aplikace na klientském počítači použit pro rozhodování o důvěryhodnosti digitální podpis manifestu aplikace. Hodnota „true“ nebo „t“ určí, že pro rozhodnutí o důvěryhodnosti bude použit manifest aplikace. Hodnota „false“ nebo „f“ určí, že bude použit podpis manifestu nasazení.|
|**-v, -Version** `versionNumber`|1.0.0.0|Manifesty aplikací.<br /><br /> Manifesty nasazení.|Verze nasazení. The argument must be a valid version string of the format "*N.N.N.N*", where "*N*" is an unsigned 32-bit integer.|
|**-wpf, -WPFBrowserApp**  `isWPFApp`|false|Manifesty aplikací.<br /><br /> Manifesty nasazení.|Tento příznak použijte pouze tehdy, je-li aplikace aplikací Windows Presentation Foundation (WPF), která bude hostována v aplikaci Internet Explorer a není samostatně spustitelná. Platnými hodnotami jsou „true“ nebo „t“ a „false“ nebo „f“.<br /><br /> For application manifests, inserts the `hostInBrowser` attribute under the `entryPoint` element of the application manifest.<br /><br /> For deployment manifests, sets the `install` attribute on the `deployment` element to false, and saves the deployment manifest with a .xbap extension. Specifying this argument along with the **-Install** argument produces an error, because a browser-hosted application cannot be an installed, offline application.|

## <a name="sign-command-options"></a>Sign command options

The following table shows the options supported by the `-Sign` command, which apply to all types of files.

|Možnosti|Popis|
|-------------|-----------------|
|**-cf, -CertFile** `filePath`|Určí umístění digitálního certifikátu pro podpis manifestu. This option can be used in conjunction with the **-Password** option if the certificate requires a password for Personal Information Exchange (PFX) files. Starting with .NET Framework 4.7, if the file does not contain a private key, a combination of the **-CryptoProvider** and **-KeyContainer** options is required.<br/><br/>Starting with .NET Framework 4.6.2, *Mage.exe* signs manifests with CNG as well as CAPI certificates.|
|**-ch, -CertHash** `hashSignature`|Hodnota hash digitálního certifikátu uloženého v úložišti osobních certifikátů klientského počítače. Ta odpovídá vlastnosti kryptografického otisku digitálního certifikátu zobrazeného v Konzole certifikátů systému Windows.<br /><br /> `hashSignature` can be either uppercase or lowercase, and can be supplied either as a single string or with each octet of the Thumbprint separated by spaces and the entire Thumbprint enclosed in quotation marks.|
**-csp, -CryptoProvider** `provider-name`|Specifies the name of a cryptographic service provider (CSP) that contains the private key container. This option requires the **-KeyContainer** option.<br/><br/>This option is available starting with .NET Framework 4.7.|
|**-kc, -KeyContainer** `name`|Specifies the key container that contains the name of the private key. This option requires the **CryptoProvider** option.<br/><br/>This option is available starting with .NET Framework 4.7.|
|**-pwd, -Password** `passwd`|Heslo použité pro podepsání manifestu digitálním certifikátem. Must be used in conjunction with the **-CertFile** option.|
|**-t, -ToFile** `filePath`|Určí výstupní cestu vytvořeného nebo upraveného souboru.|

## <a name="remarks"></a>Poznámky

All arguments to *Mage.exe* are case-insensitive. Příkazy a možnosti mohou mít předponu pomlčky (-) nebo lomítka (/).

All of the arguments used with the **-Sign** command can be used at any time with the **-New** or **-Update** commands as well. Následující příkazy jsou ekvivalentní.

```console
mage -Sign c:\HelloWorldDeployment\HelloWorld.deploy -CertFile cert.pfx
mage -Update c:\HelloWorldDeployment\HelloWorld.deploy -CertFile cert.pfx
```

> [!NOTE]
> Beginning with .NET Framework version 4.6.2, CNG certificates are also supported.

 Podpis by měl být poslední provedený úkol, protože podepsaný dokument používá hodnotu hash souboru pro ověření, zda je podpis pro dokument platný. Provedete-li v podepsaném souboru nějaké změny, je zapotřebí soubor znovu podepsat. If you sign a document that was previously signed, *Mage.exe* will replace the old signature with the new.

 When you use the **-AppManifest** option to populate a deployment manifest, *Mage.exe* will assume that your application manifest will reside in the same directory as the deployment manifest within a subdirectory named after the current deployment version, and will configure your deployment manifest appropriately. If your application manifest will reside elsewhere, use the **-AppCodeBase** option to set the alternate location.

 Před nasazením aplikace musí být manifesty nasazení a aplikace podepsány. For guidance about signing manifests, see [Trusted Application Deployment Overview](/visualstudio/deployment/trusted-application-deployment-overview).

 The **-TrustLevel** option for application manifests describes the permission set an application requires to run on the client computer. By default, applications are assigned a trust level based on the *zone* in which their URL resides. Aplikace nasazené přes podnikovou síť jsou obecně umístěny do zóny Intranet, zatímco aplikace nasazené přes internet jsou umístěny do zóny Internet. Obě bezpečnostní zóny omezují přístup aplikace k místním prostředkům, přičemž zóna Intranet je méně restriktivní než zóna Internet. Zóna FullTrust dává aplikacím plný přístup k místním prostředkům počítače. If you use the **-TrustLevel** option to place an application in this zone, the Trust Manager component of the CLR will prompt the user to decide whether he or she wants to grant this higher level of trust. Nasazujete-li aplikace přes podnikovou síť, lze úroveň důvěryhodnosti aplikace zvýšit bez dotazování uživatele pomocí technologie Trusted Application Deployment.

 Manifesty aplikací také podporují vlastní oddíly trust. To pomáhá aplikacím podřídit se zásadě bezpečnosti požadovat nejmenší možná oprávnění, protože manifest lze nakonfigurovat tak, aby požadoval pouze specifická oprávnění potřebná ke spuštění aplikace. *Mage.exe* does not directly support adding a custom trust section. You can add one using a text editor, an XML parser, or the graphical tool *MageUI.exe*. For more information about how to use *MageUI.exe* to add custom trust sections, see [MageUI.exe (Manifest Generation and Editing Tool, Graphical Client)](mageui-exe-manifest-generation-and-editing-tool-graphical-client.md).

Visual Studio 2017 includes version 4.6.1 of *Mage.exe*. Manifests created with this version of *Mage.exe* target .NET Framework 4. To target older versions of the .NET Framework, use an earlier version of *Mage.exe*.

When you add or remove assemblies from an existing manifest, or re-sign an existing manifest, *Mage.exe* does not update the manifest to target .NET Framework 4.

The following tables show these features and restrictions:

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

 Mage.exe creates new manifests that target the [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]. ClickOnce applications that target the [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)] can run on both the [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)] and the full version of the .NET Framework 4. If your application targets the full version of the .NET Framework 4 and cannot run on the [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)], remove the client `<framework>` element by using a text editor and re-sign the manifest.

The following is a sample `<framework>` element that targets the [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]:

```xml
<framework targetVersion="4.0" profile="client" supportedRuntime="4.0.20506" />
```

## <a name="examples"></a>Příklady

The following example opens the user interface for Mage (*MageUI.exe*).

```console
mage
```

Následující příklady vytvoří výchozí manifest nasazení a manifest aplikace. Tyto soubory jsou vytvořeny v aktuálním pracovním adresáři a pojmenovány deploy.application a application.exe.manifest.

```console
mage -New Deployment
mage -New Application
```

The following example creates an application manifest populated with all of the assemblies and resource files from the current directory.

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

The following example creates an application manifest populated with all of the assemblies and resource files from the current directory and signs.

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

The following example signs an existing deployment manifest using a digital certificate and private key in the current working directory.

```console
mage -Sign deploy.application -CertFile cert.pfx -KeyContainer keyfile.snk -CryptoProvider "Microsoft Enhanced Cryptographic Provider v1.0"
```

## <a name="see-also"></a>Viz také:

- [ClickOnce – zabezpečení a nasazení](/visualstudio/deployment/clickonce-security-and-deployment)
- [Návod: Ruční nasazení aplikace ClickOnce](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)
- [Přehled nasazení důvěryhodných aplikací](/visualstudio/deployment/trusted-application-deployment-overview)
- [MageUI.exe (Manifest Generation and Editing Tool, grafický klient)](mageui-exe-manifest-generation-and-editing-tool-graphical-client.md)
- [Příkazové řádky](developer-command-prompt-for-vs.md)
