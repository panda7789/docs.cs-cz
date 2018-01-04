---
title: "MageUI.exe (generování manifestu a nástroj pro úpravy, grafický klient)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Manifest Generation and Editing tool
- MageUI.exe
ms.assetid: f9e130a6-8117-49c4-839c-c988f641dc14
caps.latest.revision: "38"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1450acd6c4b68be79ad769106dfebc7d89484525
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="mageuiexe-manifest-generation-and-editing-tool-graphical-client"></a>MageUI.exe (generování manifestu a nástroj pro úpravy, grafický klient)
Nástroj MageUI.exe podporuje stejné funkce jako nástroj příkazového řádku Mage.exe, ale používá uživatelské rozhraní (UI) založené na systému Windows. Pomocí tohoto nástroje je možné vytvářet, upravovat a podepisovat manifesty nasazení a aplikací. Nové manifesty, které jsou vytvořené s cílem MageUI.exe [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]. Pro straší verze rozhraní .NET Framework byste měli použít starší verze nástroje MageUI.exe. Při přidání nebo odebrání sestavení z manifestu nebo opětovné podepisování manifestů existující, MageUI.exe neaktualizuje manifest cíl [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]. Další informace najdete v tématu [Mage.exe (generování manifestu a nástroj pro úpravy)](../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md).  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li spustit tento nástroj, použijte příkazový řádek vývojáře (nebo příkazový řádek Visual Studio v systému Windows 7). Další informace najdete v tématu [příkazového řádku](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 Dvě verze Mage.exe a MageUI.exe jsou zahrnuty jako součást sady [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)] instalační program. Pokud chcete zobrazit informace o verzi, spusťte MageUI.exe, vyberte **pomoci**a vyberte **o**. Tato dokumentace popisuje verzi 4.0.x.x nástrojů Mage.exe a MageUI.exe.  
  
> [!NOTE]
>  MageUI.exe nepodporuje [compatibleFrameworks](/visualstudio/deployment/compatibleframeworks-element-clickonce-deployment) element při ukládání manifest aplikace, které již bylo provedeno s certifikátem pomocí MageUI.exe. Místo toho musíte použít [Mage.exe](../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md).  
  
## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní  
 Následující tabulka obsahuje dostupné položky nabídek a panelu nástrojů.  
  
|Příkaz|Nabídka|Zástupce|Popis|  
|-------------|----------|--------------|-----------------|  
|**Manifest aplikace**|**Soubor, nové**||Vytvoří nový manifest aplikace.|  
|**Manifest nasazení**|**Soubor, nové**||Vytvoří nový manifest nasazení.|  
|**Otevřete**|**Soubor**|CTRL+O|Otevře existující manifest nasazení, manifest aplikace nebo důvěryhodnou licenci v režimu úprav.|  
|**Zavřete**|**Soubor**|CTRL+F4|Zavře otevřený soubor.<br /><br /> Upravíte-li soubor před jeho uzavřením, požádá nástroj MageUI.exe o opětovné podepsání souboru veřejným klíčem, párem klíčů nebo uloženým certifikátem.|  
|**Uložit**|**Soubor**|CTRL+S|Uloží soubor, na který je aktuálně zaměřen uživatelský vstup, na disk.|  
|**Uložit jako**|**Soubor**||Uloží soubor na disk a umožní zadat název souboru nebo jeho umístění.|  
|**Uložte všechny**|**Soubor**||Uloží změny pro všechny soubory otevřené v rámci nástroje MageUI.exe.|  
|**Předvolby**|**Soubor**||Otevře se **Předvolby** dialogové okno. Další informace naleznete v následující části.|  
|**Ukončení**|**Soubor**|ALT+F4|Ukončí nástroj MageUI.exe.|  
|**Vyjmout**|**Upravit**|CTRL+X|Odstraní aktuálně vybraný text z aplikace a uloží jej do schránky.|  
|**Kopírování**|**Upravit**|CTRL+C|Zkopíruje aktuálně vybraný text do schránky.|  
|**Vložení**|**Upravit**|CTRL+V|Vloží text ze schránky do aktuálního textového prvku.|  
|**Odstranit**|**Upravit**||Odstraní aktuálně vybrané v seznamu, jako je například vztah důvěryhodnosti licenci na element **Manifest nasazení** kartě.|  
|**Zavřete všechny**|**Okno**||Zavře všechny soubory otevřené v nástroji MageUI.exe. Pokud je zapotřebí některé ze souborů uložit, vyzve nástroj MageUI.exe k jejich uložení. Nástroj MageUI.exe také vyžaduje výběr podepsaného klíče pro každý nepodepsaný nebo změněný soubor.|  
|**O**|**Pomoc**||Zobrazuje verzi a informace o autorských právech nástroje MageUI.exe.|  
  
## <a name="preferences-dialog-box"></a>Dialogové okno Předvolby  
 **Předvolby** dialogové okno obsahuje následující prvky.  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Přihlaste na Uložit.**|Při uložení změn vyžaduje podepsání souboru.|  
|**Použít výchozí podpisový certifikát**|Používá klíč zadaný v **soubor certifikátu** textové pole k podepsání všechny soubory. Tím se eliminuje podepisování řádku které obvykle se zobrazí po uložení souboru a **přihlásit na Uložit** je vybrána. Použít se třemi tečkami (**...** ) vedle položky **soubor certifikátu** textového pole a vyberte soubor klíče.|  
|Algoritmus Digest|Určí algoritmus, jímž budou generovány přehledy závislostí. Hodnotou musí být „sha256RSA“ nebo „sha1RSA“. Použije SHA1 jako výchozí. Tato hodnota je použita v aplikaci i v manifestech nasazení. Pokud uživatel při ukládání manifestu zadá certifikát, použije se algoritmus v tomto certifikátu k vygenerování přehledu závislostí.|  
  
## <a name="signing-options-dialog-box"></a>Dialogové okno Možnosti podpisu  
 **Možnosti podepisování** při ukládání licenci manifest nebo vztahu důvěryhodnosti poprvé, nebo při změně licenci manifest nebo vztahu důvěryhodnosti, zobrazí se dialogové okno. Zobrazuje se pouze **přihlásit na Uložit** možnost v **Předvolby** dialogové okno je vybrána. Musíte být připojeni k Internetu při podepsání manifestu, který určuje hodnotu v **TimeStamping URI** textové pole.  
  
 Toto dialogové okno obsahuje následující prvky.  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Podepsat soubor certifikátu**|Podepíše manifest digitálním certifikátem uloženým v systému souborů.|  
|**Soubor**|Poskytuje prostor pro zadání cesty k souboru .pfx představujícímu certifikát.|  
|**...**|Otevře **zvolit soubor** dialogové okno pro výběr existující soubor .pfx.|  
|**Nový**|Vytvoří nový soubor .pfx, který nelze ověřit skrze certifikační autoritu (CA). Další informace o typech certifikátů používaných pro podpis [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] nasazení, najdete v části [Přehled nasazení důvěryhodných aplikací](/visualstudio/deployment/trusted-application-deployment-overview).|  
|**Heslo**|Poskytuje prostor pro zadání hesla použitého k podepisování certifikátů. Pokud není použito, může být ponecháno prázdné.|  
|**Přihlaste se s uložený certifikát**|Zobrazí seznam s vlastním výběrem digitálních certifikátů uložených v úložišti certifikátů počítače.|  
|**Identifikátor URI pro vytvoření časového razítka**|Zobrazí adresu Uniform Resource Locator (URI) služby digitálního časového razítka. Vytvoření časového razítka v manifestu umožňuje vyhnout se nutnosti znovu manifesty podepisovat v případě, že digitální certifikát vyprší ještě před nasazením další verze aplikace. Další informace najdete v tématu [Windows root programu Certificate](http://go.microsoft.com/fwlink/?LinkId=159000) a [ClickOnce a kód Authenticode](/visualstudio/deployment/clickonce-and-authenticode).|  
|**Nemáte přihlášení**|Umožňuje uložit manifest bez přidání podpisu z digitálního certifikátu.|  
  
## <a name="tab-and-panel-descriptions"></a>Popisy karet a panelů  
 Dokument se při otevření pomocí nástroje MageUI.exe zobrazí na vlastní kartě. Každá karta obsahuje sadu panelů vlastností. Panely obsahují seskupenou podmnožinu dat dokumentu.  
  
### <a name="application-manifest-tab"></a>Karta manifestu aplikace  
 **Application Manifest** karta zobrazuje obsah manifest aplikace. Manifest aplikace popisuje všechny soubory, které jsou součástí nasazení a oprávnění potřebná pro spuštění v klientovi aplikace.  
  
 **Application Manifest** karta obsahuje následující karty.  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Jméno**|Určuje identifikační informace o tomto nasazení.|  
|**Popis**|Určuje vydavatel, produktu a podpora informace.|  
|**Možnosti aplikace**|Určuje, jestli to je aplikace prohlížeče a zda tento manifestu je zdroj informací, vztah důvěryhodnosti.|  
|**Soubory**|Určuje, všechny soubory, které tvoří toto nasazení.|  
|**Oprávnění vyžadovaná**|Určuje minimální oprávnění sadu požadované aplikací ke spuštění v klientském počítači.|  
  
### <a name="name-tab"></a>Název karty  
 **Název** karta se zobrazí při prvním vytvoření nebo otevření manifest aplikace. Jednoznačně identifikuje nasazení a volitelně můžete určit platnou cílovou platformu.  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Jméno**|Požadováno. Název manifestu aplikace. Obvykle stejný jako název souboru.|  
|**Verze**|Požadováno. Číslo verze nasazení ve formě *N.N.N.N*. Pouze první hlavní číslo sestavení je požadovaná. Například pro verzi 1.0 aplikace, by mělo zahrnovat platné hodnoty `1`, `1.0`, `1.0.0`, a `1.0.0.0`.|  
|**Procesor**|Volitelné. Architektura počítače, ve kterém můžete spustit toto nasazení. Výchozí hodnota je `msil`, nebo zprostředkující jazyka Microsoft, což je výchozí formát všechny spravované sestavení. Toto pole změňte, pokud jste sestavili předem sestavení v aplikaci pro konkrétní architekturu. Další informace o předkompilaci najdete v tématu [Ngen.exe (Generátor nativních obrázků)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).|  
|**Jazyková verze**|Volitelné. Dvě části ISO zemí a oblastí kód, ve kterém se tato aplikace funguje. Výchozí hodnota je `neutral`.|  
|**Token veřejného klíče**|Volitelné. Veřejný klíč, pomocí kterého bylo provedeno tento manifest aplikace. Pokud je to manifestu nové nebo bez znaménka, v tomto poli se zobrazí jako `Unsigned`.|  
  
### <a name="description-tab"></a>Karta popis  
 Tyto informace je obvykle uvedené v manifestu nasazení. Tato pole lze změnit pouze v případě **použití aplikace Manifest informace o vztahu důvěryhodnosti** na je zaškrtnuté políčko **možnosti aplikace** kartě.  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Vydavatele**|Název osoba nebo organizace odpovědná za aplikace. Tato hodnota se používá jako název složky nabídky Start.|  
|**Produktu**|Úplný název produktu. Pokud jste vybrali **nainstalovat místně** pro **typ aplikace** elementu na **možnosti nasazení** kartě manifest nasazení, tento název bude, co se zobrazí v **Spustit** odkaz nabídky a v **přidat nebo odebrat programy** pro tuto aplikaci.|  
|**Podpora umístění**|Adresa URL, ze kterého můžete získat zákazníkům nápovědě a podpoře pro aplikaci.|  
  
### <a name="application-options-tab"></a>Karta Možnosti aplikace  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Aplikace Windows Presentation Foundation prohlížeče**|Určuje, zda se jedná o aplikaci WPF, který běží v prohlížeči jako aplikace prohlížeče XAML (XBAP).|  
|**Pomocí informací o aplikaci manifestu důvěryhodnosti**|Určuje, zda tento manifest obsahuje informace o vztahu důvěryhodnosti.|  
  
### <a name="files-tab"></a>Karta soubory  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Adresář aplikace**|Adresář, ve kterém jsou umístěny soubory aplikace. Použít na symbol tří teček (**...** ) tlačítko vyberte adresář.|  
|**Naplnění**|Přidá všechny soubory v adresáři aplikace a podadresáře manifest aplikace. Pokud MageUI.exe najde jeden spustitelný soubor v adresáři, automaticky označí to jako vstupní bod, který je soubor nejdřív provést při spuštění aplikace ClickOnce na straně klienta.|  
|**Soubory aplikace**|Zobrazí seznam všech souborů v aplikaci. Každý soubor má tři upravitelné atributy, které jsou popsané níže.|  
|**Typ souboru**|Typ souboru může být jednu ze čtyř hodnot:<br /><br /> -None.<br />-Vstupní bod. Primární spustitelný soubor aplikace. Jenom pro jeden spustitelný soubor může být označený jako vstupní bod.<br />-Datový soubor. Souboru, jako je soubor XML, který poskytuje data do aplikace.<br />-Soubor ikony. Ikony aplikace, jako například se zobrazí na ploše nebo v horním rohu okna aplikace.|  
|**Optional**|Soubory označené volitelné nestahují na počáteční instalace nebo aktualizace, ale může stáhnout v době běhu pomocí rozhraní API System.Deployment na vyžádání. Další informace najdete v tématu [návod: stahování sestavení na vyžádání pomocí ClickOnce pomocí rozhraní API nasazení návrháře](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer).|  
|**Skupiny**|Popisek pro sadu volitelné soubory. Můžete použít skupiny štítek na určitou sadu souborů a stáhnout dávky souborů na základě jednoho volání rozhraní API pomocí rozhraní API na vyžádání.|  
  
### <a name="permissions-required-tab"></a>Karta požadovaná oprávnění  
 Použití **oprávněních** kartě, pokud je potřeba udělit větší přístup k místnímu počítači, než je ve výchozím nastavení udělit vaší aplikace. Další informace najdete v tématu [zabezpečení aplikací ClickOnce](/visualstudio/deployment/securing-clickonce-applications).  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Typ sady oprávnění**|Sada minimální oprávnění, které vyžadují tuto aplikaci spustit v klientském počítači. Popis těchto sady oprávnění a oprávnění, která nemají nebo není potřebují, najdete v části [NIB: s názvem nastaví oprávnění](http://msdn.microsoft.com/en-us/08250d67-c99d-4ab0-8d2b-b0e12019f6e3).|  
|**Podrobnosti**|Soubor XML pro manifest aplikace vytvořit představují oprávnění nastavit. Pokud nemáte dostatečné povědomí o manifest aplikace formátu XML, byste neměli upravovat tento XML ručně. Další informace najdete v tématu [Manifest aplikace ClickOnce](/visualstudio/deployment/clickonce-application-manifest).|  
  
### <a name="deployment-manifest-tab"></a>Karta manifestu nasazení  
 **Manifest nasazení** karta obsahuje následující karty.  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Jméno**|Určuje identifikační informace o tomto nasazení.|  
|**Popis**|Určuje vydavatel, produktu a podpora informace.|  
|**Možnosti nasazení**|Určuje další informace o nasazení, například typ aplikace a počáteční umístění.|  
|**Možnosti aktualizace**|Určuje, jak často [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] by kontrola aktualizací aplikace.|  
|**Odkaz na aplikaci**|Určuje manifest aplikace pro toto nasazení.|  
  
### <a name="name-tab"></a>Název karty  
 **Název** karta se zobrazí při prvním vytvoření nebo otevření manifestu nasazení. Jednoznačně identifikuje nasazení a volitelně můžete určit platnou cílovou platformu.  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Jméno**|Požadováno. Název manifestu nasazení. Obvykle stejný jako název souboru.|  
|**Verze**|Požadováno. Číslo verze nasazení ve formě *N.N.N.N*. Pouze první hlavní číslo sestavení je požadovaná. Například pro verzi 1.0 aplikace, by mělo zahrnovat platné hodnoty `1`, `1.0`, `1.0.0`, a `1.0.0.0`.|  
|**Procesor**|Volitelné. Architektura počítače, ve kterém můžete spustit toto nasazení. Výchozí hodnota je `msil`, nebo Microsoft Intermediate Language, výchozí formát všechny spravované sestavení. Toto pole změňte, pokud jste sestavili sestavení v aplikaci pro konkrétní architekturu.|  
|**Jazyková verze**|Volitelné. Kód pro země nebo oblasti ISO se dvě části, ve kterém se tato aplikace funguje. Výchozí hodnota je `neutral`.|  
|**Token veřejného klíče**|Volitelné. Veřejný klíč, pomocí kterého byla podepsána tuto – manifest nasazení. Pokud je to manifestu nové nebo bez znaménka, v tomto poli se zobrazí jako `Unsigned`.|  
  
### <a name="description-tab"></a>Karta popis  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Vydavatele**|Požadováno. Název osoba nebo organizace odpovědná za aplikace. Tato hodnota se používá jako název složky nabídky Start.|  
|**Produktu**|Požadováno. Úplný název produktu. Pokud jste vybrali **nainstalovat místně** pro **typ aplikace** elementu na **možnosti nasazení** kartě, bude tento název, co se zobrazí v **spustit** odkaz nabídky a v **přidat nebo odebrat programy** pro tuto aplikaci.|  
|**Podpora umístění**|Volitelné. Adresa URL, ze kterého můžete získat zákazníkům nápovědě a podpoře pro aplikaci.|  
  
### <a name="deployment-options-tab"></a>Karta Možnosti nasazení  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Typ aplikace**|Volitelné. Určuje, zda tato aplikace sám nainstalovat do klientského počítače (**nainstalovat místně**), spustí online (**Online pouze**), nebo je WPF aplikace, která běží v prohlížeči (**prohlížeče WPF Aplikace**). Výchozí hodnota je **nainstalovat místně**.|  
|**Počáteční umístění**|Volitelné. Adresa URL, ze kterého má ve skutečnosti spuštěna aplikace. To užitečné, pokud nasazení aplikace z disku CD, který by měl sám sebe aktualizovat z webu.|  
|**Spustit umístění (ProviderURL) zahrnout do manifestu**|Volitelné. Určuje adresu URL, která [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] prozkoumá aktualizací aplikace.|  
|**Automaticky spouštět aplikace po instalaci**|Požadováno. Určuje, že [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] aplikace by měl spustit okamžitě po počáteční instalaci z adresy URL. Výchozí hodnota je, že je zaškrtnuté políčko.|  
|**Povolit adresu URL parametry předávané do aplikace**|Požadováno. Umožňuje přenos dat parametr [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] aplikace pomocí řetězce dotazu připojí k adrese URL manifest nasazení. Výchozí hodnota je, že není zaškrtnuté políčko.|  
|**Používat příponu souboru .deploy**|Požadováno. Pokud vybraná, všechny soubory v manifestu aplikace musí mít příponu .deploy. Výchozí hodnota je, že není zaškrtnuté políčko.|  
  
### <a name="update-options-tab"></a>Karta Možnosti aktualizace  
 **Možnosti aktualizace** karta obsahuje pouze možnosti Pokud zde uvedeným **typ aplikace** výběr pole na **název** karta je nastaven na **nainstalovat místně** .  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Tato aplikace by měla vyhledat aktualizace**|Určuje, zda [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] by kontrola aktualizací aplikace. Pokud není toto políčko zaškrtnuto, aplikace nebude aktualizace vyhledávat pokud ho aktualizujete programově pomocí rozhraní API v <xref:System.Deployment.Application> oboru názvů.|  
|**Vyberte, pokud aplikace by měla vyhledat aktualizace**|Nabízí dvě možnosti pro aktualizaci kontroly:<br /><br /> -   **Před spuštěním aplikace**. Kontrola aktualizace se provádí před provádění aplikací.<br />-   **Po spuštění aplikace**. Kontrola aktualizace začíná, jakmile byla inicializována hlavní formulář aplikace a bude spuštěna při příštím spuštění aplikace.|  
|**Četnost kontroly aktualizací**|Určuje, jak často [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] vyhledávat aktualizace:<br /><br /> -   **Zkontrolujte pokaždé, když je aplikace spuštěná**. [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)]pokaždé, když uživatel otevře aplikaci, provede kontrolu aktualizace.<br />-   **Zkontrolujte všechny**: vyberte časový interval a jednotka (hodiny, dny nebo týdny), které musí uplynout před vyhledáním aktualizace.|  
|**Zadejte minimální požadovaná verze pro tuto aplikaci**|Volitelné. Určuje, že konkrétní verzi vaší aplikace je požadovanou instalaci, neumožňuje uživatelům z předchozích verzí.|  
|**Verze**|Požadováno pokud **zadejte minimální požadovaná verze pro tuto aplikaci** je zaškrtnuté políčko. Zadané číslo verze musí být ve tvaru *N.N.N.N*. Pouze první hlavní číslo sestavení je požadovaná. Například pro verzi 1.0 aplikace, by mělo zahrnovat platné hodnoty `1`, `1.0`, `1.0.0`, a `1.0.0.0`.|  
  
### <a name="application-reference-tab"></a>Odkaz na kartě aplikace  
 **Odkaz aplikace** karta obsahuje pole stejné jako **název** kartě popsané dříve v tomto tématu. Jedinou výjimkou je následující pole.  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Vyberte manifestu**|Umožňuje zvolit manifest aplikace. Všechna ostatní pole na této stránce naplní, když zvolíte manifest aplikace.|  
  
## <a name="see-also"></a>Viz také  
 [ClickOnce – zabezpečení a nasazení](/visualstudio/deployment/clickonce-security-and-deployment)  
 [Návod: Ruční nasazení aplikace ClickOnce](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)  
 [Mage.exe (Manifest Generation and Editing Tool)](../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md)
