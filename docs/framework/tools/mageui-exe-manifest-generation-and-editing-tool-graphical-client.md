---
title: MageUI.exe (generování manifestu a nástroj pro úpravy, grafický klient)
ms.date: 03/30/2017
helpviewer_keywords:
- Manifest Generation and Editing tool
- MageUI.exe
ms.assetid: f9e130a6-8117-49c4-839c-c988f641dc14
ms.openlocfilehash: 99f522181232d16b9913ba3c55f34274b75d8966
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449410"
---
# <a name="mageuiexe-manifest-generation-and-editing-tool-graphical-client"></a>MageUI.exe (generování manifestu a nástroj pro úpravy, grafický klient)

Nástroj MageUI.exe podporuje stejné funkce jako nástroj příkazového řádku Mage.exe, ale používá uživatelské rozhraní (UI) založené na systému Windows. Pomocí tohoto nástroje je možné vytvářet, upravovat a podepisovat manifesty nasazení a aplikací. New manifests that are created with MageUI.exe target the [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]. Pro straší verze rozhraní .NET Framework byste měli použít starší verze nástroje MageUI.exe. When adding or removing assemblies from a manifest, or re-signing existing manifests, MageUI.exe does not update the manifest to target [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]. For more information, see [Mage.exe (Manifest Generation and Editing Tool)](mage-exe-manifest-generation-and-editing-tool.md).

 Tento nástroj je automaticky nainstalován se sadou Visual Studio. To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7). For more information, see [Command Prompts](developer-command-prompt-for-vs.md).

 Two versions of Mage.exe and MageUI.exe are included as a component of Visual Studio. To see version information, run MageUI.exe, select **Help**, and select **About**. Tato dokumentace popisuje verzi 4.0.x.x nástrojů Mage.exe a MageUI.exe.

> [!NOTE]
> MageUI.exe does not support the [compatibleFrameworks](/visualstudio/deployment/compatibleframeworks-element-clickonce-deployment) element when saving an application manifest that has already been signed with a certificate using MageUI.exe. Instead, you must use [Mage.exe](mage-exe-manifest-generation-and-editing-tool.md).  
  
## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní  
 Následující tabulka obsahuje dostupné položky nabídek a panelu nástrojů.  
  
|Příkaz|Nabídka|Zástupce|Popis|  
|-------------|----------|--------------|-----------------|  
|**Application Manifest**|**File, New**||Vytvoří nový manifest aplikace.|  
|**Deployment Manifest**|**File, New**||Vytvoří nový manifest nasazení.|  
|**Open**|**File**|CTRL+O|Otevře existující manifest nasazení, manifest aplikace nebo důvěryhodnou licenci v režimu úprav.|  
|**Close**|**File**|CTRL+F4|Zavře otevřený soubor.<br /><br /> Upravíte-li soubor před jeho uzavřením, požádá nástroj MageUI.exe o opětovné podepsání souboru veřejným klíčem, párem klíčů nebo uloženým certifikátem.|  
|**Save**|**File**|CTRL+S|Uloží soubor, na který je aktuálně zaměřen uživatelský vstup, na disk.|  
|**Save As**|**File**||Uloží soubor na disk a umožní zadat název souboru nebo jeho umístění.|  
|**Save All**|**File**||Uloží změny pro všechny soubory otevřené v rámci nástroje MageUI.exe.|  
|**Předvolby**|**File**||Opens the **Preferences** dialog box. Další informace naleznete v následující části.|  
|**Exit**|**File**|ALT+F4|Ukončí nástroj MageUI.exe.|  
|**Cut**|**Edit**|CTRL+X|Odstraní aktuálně vybraný text z aplikace a uloží jej do schránky.|  
|**Copy**|**Edit**|CTRL+C|Zkopíruje aktuálně vybraný text do schránky.|  
|**Paste**|**Edit**|CTRL+V|Vloží text ze schránky do aktuálního textového prvku.|  
|**Delete**|**Edit**||Deletes an element currently selected in a list, such as a trust license on the **Deployment Manifest** tab.|  
|**Close All**|**Window**||Zavře všechny soubory otevřené v nástroji MageUI.exe. Pokud je zapotřebí některé ze souborů uložit, vyzve nástroj MageUI.exe k jejich uložení. Nástroj MageUI.exe také vyžaduje výběr podepsaného klíče pro každý nepodepsaný nebo změněný soubor.|  
|**About**|**Help**||Zobrazuje verzi a informace o autorských právech nástroje MageUI.exe.|  
  
## <a name="preferences-dialog-box"></a>Dialogové okno Předvolby  
 The **Preferences** dialog box contains the following elements.  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Sign on save**|Při uložení změn vyžaduje podepsání souboru.|  
|**Use default signing certificate**|Uses the key entered in the **Certificate file** text box to sign all files. This eliminates the signing prompt that typically appears when you save a file and **Sign on Save** is selected. Use the ellipsis ( **…** ) button next to the **Certificate file** text box to select a key file.|  
|Algoritmus Digest|Určí algoritmus, jímž budou generovány přehledy závislostí. Hodnotou musí být „sha256RSA“ nebo „sha1RSA“. Použije SHA1 jako výchozí. Tato hodnota je použita v aplikaci i v manifestech nasazení. Pokud uživatel při ukládání manifestu zadá certifikát, použije se algoritmus v tomto certifikátu k vygenerování přehledu závislostí.|  
  
## <a name="signing-options-dialog-box"></a>Dialogové okno Možnosti podpisu  
 The **Signing Options** dialog box appears when you save a manifest or trust license for the first time, or when you change a manifest or trust license. It only appears if the **Sign on Save** option in the **Preferences** dialog box is selected. You must be connected to the Internet when signing a manifest that specifies a value in the **TimeStamping URI** text box.  
  
 Toto dialogové okno obsahuje následující prvky.  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Sign with certificate file**|Podepíše manifest digitálním certifikátem uloženým v systému souborů.|  
|**File**|Poskytuje prostor pro zadání cesty k souboru .pfx představujícímu certifikát.|  
|**...**|Opens a **Choose File** dialog box for selecting an existing .pfx file.|  
|**New**|Vytvoří nový soubor .pfx, který nelze ověřit skrze certifikační autoritu (CA). For more information about the types of certificates used for signing ClickOnce deployments, see [Trusted Application Deployment Overview](/visualstudio/deployment/trusted-application-deployment-overview).|  
|**Password**|Poskytuje prostor pro zadání hesla použitého k podepisování certifikátů. Pokud není použito, může být ponecháno prázdné.|  
|**Sign with stored certificate**|Zobrazí seznam s vlastním výběrem digitálních certifikátů uložených v úložišti certifikátů počítače.|  
|**TimeStamping URI**|Zobrazí adresu Uniform Resource Locator (URI) služby digitálního časového razítka. Vytvoření časového razítka v manifestu umožňuje vyhnout se nutnosti znovu manifesty podepisovat v případě, že digitální certifikát vyprší ještě před nasazením další verze aplikace. For more information, see [Windows root certificate program members](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn265983(v=ws.11)) and [ClickOnce and Authenticode](/visualstudio/deployment/clickonce-and-authenticode).|  
|**Don't Sign**|Umožňuje uložit manifest bez přidání podpisu z digitálního certifikátu.|  
  
## <a name="tab-and-panel-descriptions"></a>Popisy karet a panelů  
 Dokument se při otevření pomocí nástroje MageUI.exe zobrazí na vlastní kartě. Každá karta obsahuje sadu panelů vlastností. Panely obsahují seskupenou podmnožinu dat dokumentu.  
  
### <a name="application-manifest-tab"></a>Application Manifest Tab  
 The **Application Manifest** tab displays the contents of an application manifest. The application manifest describes all files included with the deployment, and the permissions required for the application to run on the client.  
  
 The **Application Manifest** tab contains the following tabs.  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Name**|Specifies identifying information about this deployment.|  
|**Popis**|Specifies publisher, product, and support information.|  
|**Application Options**|Specifies whether this is a browser application, and whether this manifest is the source of trust information.|  
|**Soubory**|Specifies all of the files that constitute this deployment.|  
|**Permissions Required**|Specifies the minimum permission set required by the application to run on a client.|  
  
### <a name="name-tab"></a>Name Tab  
 The **Name** tab is displayed when you first create or open an application manifest. It uniquely identifies the deployment, and optionally specifies a valid target platform.  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Name**|Požadováno. The name of the application manifest. Usually the same as the file name.|  
|**Verze**|Požadováno. The version number of the deployment in the form *N.N.N.N*. Only the first major build number is required. For example, for version 1.0 of an application, valid values would include `1`, `1.0`, `1.0.0`, and `1.0.0.0`.|  
|**Processor**|Volitelné. The machine architecture on which this deployment can run. The default is `msil`, or Microsoft Intermediate Language, which is the default format of all managed assemblies. Change this field if you have pre-compiled the assemblies in your application for a specific architecture. For more information about pre-compilation, see [Ngen.exe (Native Image Generator)](ngen-exe-native-image-generator.md).|  
|**Culture**|Volitelné. The two-part ISO country and region code in which this application runs. Výchozí hodnota je `neutral`.|  
|**Public key token**|Volitelné. The public key with which this application manifest has been signed. If this is a new or unsigned manifest, this field will appear as `Unsigned`.|  
  
### <a name="description-tab"></a>Description Tab  
 This information is usually provided within the deployment manifest. These fields can only be modified if the **Use Application Manifest Trust Information** check box is selected on the **Application Options** tab.  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Publisher**|The name of the person or organization responsible for the application. This value is used as the Start menu folder name.|  
|**Product**|The full product name. If you selected **Install Locally** for the **Application Type** element on the **Deployment Options** tab of the deployment manifest, this name will be what appears in the **Start** menu link and in **Add or Remove Programs** for this application.|  
|**Support Location**|The URL from which customers can obtain help and support for the application.|  
  
### <a name="application-options-tab"></a>Application Options Tab  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Windows Presentation Foundation Browser Application**|Specifies whether this is a WPF application that runs in the browser as a XAML browser application (XBAP).|  
|**Use Application Manifest Trust Information**|Specifies whether this manifest contains trust information.|  
  
### <a name="files-tab"></a>Files Tab  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Application directory**|The directory in which the application's files reside. Use the ellipses ( **…** ) button to select the directory.|  
|**Populate**|Adds all of the files in the application directory and subdirectories to the application manifest. If MageUI.exe finds a single executable file in the directory, it automatically marks this as the Entry Point, which is the file first executed when the ClickOnce application is launched on the client.|  
|**Application Files**|Lists all of the files in the application. Each file has three editable attributes, discussed below.|  
|**File Type**|File Type can be one of four values:<br /><br /> -   None.<br />-   Entry Point. The application's primary executable. Only one executable file can be marked as the entry point.<br />-   Data File. A file, such as an XML file, that supplies data to the application.<br />-   Icon File. An application icon, such as appears on the desktop or in the corner of an application's window.|  
|**Optional**|Files marked optional are not downloaded on initial install or update, but may be downloaded at run time using the System.Deployment On-Demand API. For more information, see [Walkthrough: Downloading Assemblies on Demand with the ClickOnce Deployment API Using the Designer](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer).|  
|**Group**|A label for a set of optional files. You can apply a Group label to a set of files, and use the On-Demand API to download a batch of files with a single API call.|  
  
### <a name="permissions-required-tab"></a>Permissions Required Tab  
 Use the **Permissions Required** tab if you need to grant your application more access to the local computer than is granted by default. For more information, see [Securing ClickOnce Applications](/visualstudio/deployment/securing-clickonce-applications).  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Permission set type**|The minimum permission set required by this application to run on the client. For a description of these permission sets and which permissions they do or do not demand, see [Named Permission Sets](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).|  
|**Details**|The XML created for the application manifest to represent the permission set. Unless you have a good understanding of the application manifest XML format, you should not edit this XML manually. For more information, see [ClickOnce Application Manifest](/visualstudio/deployment/clickonce-application-manifest).|  
  
### <a name="deployment-manifest-tab"></a>Deployment Manifest Tab  
 The **Deployment Manifest** tab contains the following tabs.  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Name**|Specifies identifying information about this deployment.|  
|**Popis**|Specifies publisher, product, and support information.|  
|**Deployment Options**|Specifies additional information about the deployment, such as the application type and the start location.|  
|**Update Options**|Specifies how often ClickOnce should check for application updates.|  
|**Application Reference**|Specifies the application manifest for this deployment.|  
  
### <a name="name-tab"></a>Name Tab  
 The **Name** tab is displayed when you first create or open a deployment manifest. It uniquely identifies the deployment, and optionally specifies a valid target platform.  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Name**|Požadováno. The name of the deployment manifest. Usually the same as the file name.|  
|**Verze**|Požadováno. The version number of the deployment in the form *N.N.N.N*. Only the first major build number is required. For example, for version 1.0 of an application, valid values would include `1`, `1.0`, `1.0.0`, and `1.0.0.0`.|  
|**Processor**|Volitelné. The machine architecture on which this deployment can run. The default is `msil`, or Microsoft Intermediate Language, the default format of all managed assemblies. Change this field if you have compiled the assemblies in your application for a specific architecture.|  
|**Culture**|Volitelné. The two-part ISO country/region code in which this application runs. Výchozí hodnota je `neutral`.|  
|**Public key token**|Volitelné. The public key with which this deployment manifest has been signed. If this is a new or unsigned manifest, this field will appear as `Unsigned`.|  
  
### <a name="description-tab"></a>Description Tab  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Publisher**|Požadováno. The name of the person or organization responsible for the application. This value is used as the Start menu folder name.|  
|**Product**|Požadováno. The full product name. If you selected **Install Locally** for the **Application Type** element on the **Deployment Options** tab, this name will be what appears in the **Start** menu link and in **Add or Remove Programs** for this application.|  
|**Support Location**|Volitelné. The URL from which customers can obtain help and support for the application.|  
  
### <a name="deployment-options-tab"></a>Deployment Options Tab  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Application Type**|Volitelné. Specifies whether this application installs itself to the client computer (**Install Locally**), runs online (**Online Only**), or is a WPF application that runs in the browser (**WPF Browser Application**). The default is **Install Locally**.|  
|**Start Location**|Volitelné. The URL from which the application should actually be started. Useful when deploying an application from a CD that should update itself from the Web.|  
|**Include Start Location (ProviderURL) in the manifest**|Volitelné. Určuje adresu URL, na které technologie ClickOnce vyhledá aktualizace aplikace.|  
|**Automatically run application after installing**|Požadováno. Specifies that the ClickOnce application should run immediately after the initial installation from a URL. The default is the check box is selected.|  
|**Allow URL parameters to be passed to application**|Požadováno. Permits the transfer of parameter data to the ClickOnce application through a query string appended to the deployment manifest's URL. The default is the check box is cleared.|  
|**Use .deploy file extension**|Požadováno. When selected, all files in the application manifest must have the .deploy extension. The default is the check box is cleared.|  
  
### <a name="update-options-tab"></a>Update Options Tab  
 The **Update Options** tab only contains options mentioned here when the **Application Type** selection box on the **Name** tab is set to **Install Locally**.  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**This application should check for updates**|Specifies whether ClickOnce should check for application updates. If this check box is not selected, the application will not check for updates unless you update it programmatically by using the APIs in the <xref:System.Deployment.Application> namespace.|  
|**Choose when the application should check for updates**|Provides two options for update checks:<br /><br /> -   **Before the application starts**. The update check is performed prior to application execution.<br />-   **After the application starts**. The update check begins once the main form of the application has initialized, and will run the next time the application starts.|  
|**Update check frequency**|Determines how often ClickOnce should check for updates:<br /><br /> -   **Check every time the application runs**. ClickOnce will perform an update check every time the user opens the application.<br />-   **Check every**: Select a time interval and a unit (hours, days, or weeks) that must elapse before checking for updates.|  
|**Specify a minimum required version for this application**|Volitelné. Specifies that a specific version of your application is a required installation, preventing your users from working with an earlier version.|  
|**Verze**|Required if **Specify a minimum required version for this application** check box is selected. The version number supplied must be of the form *N.N.N.N*. Only the first major build number is required. For example, for version 1.0 of an application, valid values would include `1`, `1.0`, `1.0.0`, and `1.0.0.0`.|  
  
### <a name="application-reference-tab"></a>Application Reference Tab  
 The **Application Reference** tab contains the same fields as the **Name** tab described earlier in this topic. The one exception is the following field.  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Select Manifest**|Allows you to choose the application manifest. All of the other fields on this page will populate when you choose an application manifest.|  
  
## <a name="see-also"></a>Viz také:

- [ClickOnce – zabezpečení a nasazení](/visualstudio/deployment/clickonce-security-and-deployment)
- [Návod: Ruční nasazení aplikace ClickOnce](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)
- [Mage.exe (Manifest Generation and Editing Tool)](mage-exe-manifest-generation-and-editing-tool.md)
