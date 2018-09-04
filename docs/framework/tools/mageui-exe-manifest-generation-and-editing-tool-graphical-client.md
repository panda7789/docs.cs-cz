---
title: MageUI.exe (generování manifestu a nástroj pro úpravy, grafický klient)
ms.date: 03/30/2017
helpviewer_keywords:
- Manifest Generation and Editing tool
- MageUI.exe
ms.assetid: f9e130a6-8117-49c4-839c-c988f641dc14
ms.openlocfilehash: eb93e53e7b77ee2747bce3fb9a45d7061450e65c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43501658"
---
# <a name="mageuiexe-manifest-generation-and-editing-tool-graphical-client"></a>MageUI.exe (generování manifestu a nástroj pro úpravy, grafický klient)
Nástroj MageUI.exe podporuje stejné funkce jako nástroj příkazového řádku Mage.exe, ale používá uživatelské rozhraní (UI) založené na systému Windows. Pomocí tohoto nástroje je možné vytvářet, upravovat a podepisovat manifesty nasazení a aplikací. Nové manifesty vytvořené s cílem MageUI.exe [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]. Pro straší verze rozhraní .NET Framework byste měli použít starší verze nástroje MageUI.exe. Při přidávání nebo odstraňování sestavení z manifestu nebo při opětovném podepisování existujících manifestů, MageUI.exe neaktualizuje manifest do cíle [!INCLUDE[net_client_v40_long](../../../includes/net-client-v40-long-md.md)]. Další informace najdete v tématu [Mage.exe (Manifest Generation and Editing Tool)](../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md).  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li spustit tento nástroj, použijte příkazový řádek vývojáře (nebo příkazový řádek Visual Studio v systému Windows 7). Další informace najdete v tématu [příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 Dvě verze Mage.exe a MageUI.exe jsou zahrnuty jako součást sady [!INCLUDE[vs_dev10_long](../../../includes/vs-dev10-long-md.md)] instalační program. Pokud chcete zobrazit informace o verzi, spusťte MageUI.exe, vyberte **pomáhají**a vyberte **o**. Tato dokumentace popisuje verzi 4.0.x.x nástrojů Mage.exe a MageUI.exe.  
  
> [!NOTE]
>  MageUI.exe, nepodporuje [compatibleFrameworks](/visualstudio/deployment/compatibleframeworks-element-clickonce-deployment) element při ukládání manifestu aplikace, který již byl podepsán certifikátem nástroje MageUI.exe. Místo toho je nutné použít [Mage.exe](../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md).  
  
## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní  
 Následující tabulka obsahuje dostupné položky nabídek a panelu nástrojů.  
  
|Příkaz|Nabídka|Zástupce|Popis|  
|-------------|----------|--------------|-----------------|  
|**Manifest aplikace**|**Soubor, nový**||Vytvoří nový manifest aplikace.|  
|**Manifest nasazení**|**Soubor, nový**||Vytvoří nový manifest nasazení.|  
|**Otevřít**|**Soubor**|CTRL+O|Otevře existující manifest nasazení, manifest aplikace nebo důvěryhodnou licenci v režimu úprav.|  
|**Zavřít**|**Soubor**|CTRL+F4|Zavře otevřený soubor.<br /><br /> Upravíte-li soubor před jeho uzavřením, požádá nástroj MageUI.exe o opětovné podepsání souboru veřejným klíčem, párem klíčů nebo uloženým certifikátem.|  
|**Uložit**|**Soubor**|CTRL+S|Uloží soubor, na který je aktuálně zaměřen uživatelský vstup, na disk.|  
|**Uložit jako**|**Soubor**||Uloží soubor na disk a umožní zadat název souboru nebo jeho umístění.|  
|**Uložit vše**|**Soubor**||Uloží změny pro všechny soubory otevřené v rámci nástroje MageUI.exe.|  
|**Předvolby**|**Soubor**||Otevře **Předvolby** dialogové okno. Další informace naleznete v následující části.|  
|**ukončení**|**Soubor**|ALT+F4|Ukončí nástroj MageUI.exe.|  
|**Vyjmout**|**Upravit**|CTRL+X|Odstraní aktuálně vybraný text z aplikace a uloží jej do schránky.|  
|**kopírování**|**Upravit**|CTRL+C|Zkopíruje aktuálně vybraný text do schránky.|  
|**Vložit**|**Upravit**|CTRL+V|Vloží text ze schránky do aktuálního textového prvku.|  
|**Delete**|**Upravit**||Odstraní aktuálně vybraným v seznamu, například důvěryhodnou licenci v elementu **Manifest nasazení** kartu.|  
|**Zavřít vše**|**Window**||Zavře všechny soubory otevřené v nástroji MageUI.exe. Pokud je zapotřebí některé ze souborů uložit, vyzve nástroj MageUI.exe k jejich uložení. Nástroj MageUI.exe také vyžaduje výběr podepsaného klíče pro každý nepodepsaný nebo změněný soubor.|  
|**o**|**Pomoc**||Zobrazuje verzi a informace o autorských právech nástroje MageUI.exe.|  
  
## <a name="preferences-dialog-box"></a>Dialogové okno Předvolby  
 **Předvolby** dialogové okno obsahuje následující prvky.  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Podepsat při uložení**|Při uložení změn vyžaduje podepsání souboru.|  
|**Použít výchozí podpisový certifikát**|Použije klíč zadaný **soubor certifikátu** textové pole pro podepsání všech souborů. Tím se eliminují podepsání, který se obvykle zobrazuje při ukládání souboru a **podepsat při uložení** zaškrtnuto. Použít na tři tečky (**...** ) vedle **soubor certifikátu** textového pole a vyberte soubor klíče.|  
|Algoritmus Digest|Určí algoritmus, jímž budou generovány přehledy závislostí. Hodnotou musí být „sha256RSA“ nebo „sha1RSA“. Použije SHA1 jako výchozí. Tato hodnota je použita v aplikaci i v manifestech nasazení. Pokud uživatel při ukládání manifestu zadá certifikát, použije se algoritmus v tomto certifikátu k vygenerování přehledu závislostí.|  
  
## <a name="signing-options-dialog-box"></a>Dialogové okno Možnosti podpisu  
 **Možnosti podpisu** při prvním uložení manifestu nebo důvěryhodné licence či při jejich změně manifestu nebo důvěryhodné licence, zobrazí se dialogové okno. Se zobrazí pouze pokud je **podepsat při uložení** možnost **Předvolby** vybrali dialogové okno. Musíte být připojeni k Internetu při podpisu manifestu určujícího hodnotu v **identifikátor URI TimeStamping** textového pole.  
  
 Toto dialogové okno obsahuje následující prvky.  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Podepsat pomocí souboru certifikátu**|Podepíše manifest digitálním certifikátem uloženým v systému souborů.|  
|**Soubor**|Poskytuje prostor pro zadání cesty k souboru .pfx představujícímu certifikát.|  
|**...**|Otevře se **zvolit soubor** dialogové okno pro výběr existujícího souboru .pfx.|  
|**Nový**|Vytvoří nový soubor .pfx, který nelze ověřit skrze certifikační autoritu (CA). Další informace o typech použitých certifikátů pro podepisování [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] nasazení, najdete v článku [Trusted Application Deployment Overview](/visualstudio/deployment/trusted-application-deployment-overview).|  
|**Heslo**|Poskytuje prostor pro zadání hesla použitého k podepisování certifikátů. Pokud není použito, může být ponecháno prázdné.|  
|**Podepsání pomocí uloženého certifikátu**|Zobrazí seznam s vlastním výběrem digitálních certifikátů uložených v úložišti certifikátů počítače.|  
|**Identifikátor URI TimeStamping**|Zobrazí adresu Uniform Resource Locator (URI) služby digitálního časového razítka. Vytvoření časového razítka v manifestu umožňuje vyhnout se nutnosti znovu manifesty podepisovat v případě, že digitální certifikát vyprší ještě před nasazením další verze aplikace. Další informace najdete v tématu [Windows Členové programu kořenového certifikátu](https://go.microsoft.com/fwlink/?LinkId=159000) a [ClickOnce and Authenticode](/visualstudio/deployment/clickonce-and-authenticode).|  
|**Nepodepisovat**|Umožňuje uložit manifest bez přidání podpisu z digitálního certifikátu.|  
  
## <a name="tab-and-panel-descriptions"></a>Popisy karet a panelů  
 Dokument se při otevření pomocí nástroje MageUI.exe zobrazí na vlastní kartě. Každá karta obsahuje sadu panelů vlastností. Panely obsahují seskupenou podmnožinu dat dokumentu.  
  
### <a name="application-manifest-tab"></a>Karta s manifestem aplikace  
 **Manifest aplikace** karta zobrazuje obsah manifestu aplikace. Manifest aplikace popisuje všechny soubory, které jsou součástí nasazení a oprávněních pro aplikaci, aby běžela na straně klienta.  
  
 **Manifest aplikace** karta obsahuje následující karty.  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Jméno**|Určuje identifikační informace o tomto nasazení.|  
|**Popis**|Určuje vydavatele, produkt a podporu informace.|  
|**Možnosti aplikace**|Určuje, zda je to aplikace prohlížeče a zda tomto manifestu se zdrojové informace o vztahu důvěryhodnosti.|  
|**Soubory**|Určuje všechny soubory, které tvoří toto nasazení.|  
|**Oprávnění vyžadovaná**|Určuje sadu minimální oprávnění vyžadované aplikací ke spuštění v klientském počítači.|  
  
### <a name="name-tab"></a>Název karty  
 **Název** kartě se zobrazí při prvním vytvoření nebo otevření manifestu aplikace. Jednoznačně identifikuje nasazení a volitelně určuje platnou cílovou platformu.  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Jméno**|Požadováno. Název manifestu aplikace. Obvykle stejný jako název souboru.|  
|**Verze**|Požadováno. Číslo verze nasazení ve formě *N.N.N.N*. Pouze první hlavní číslo sestavení je povinný. Například pro verzi 1.0 rozhraní aplikace, bude obsahovat platné hodnoty `1`, `1.0`, `1.0.0`, a `1.0.0.0`.|  
|**Procesor**|Volitelné. Architektura počítače, na kterém můžete spustit toto nasazení. Výchozí hodnota je `msil`, nebo Microsoft Intermediate Language, což je výchozí formát pro všechna spravovaná sestavení. Toto pole změňte, pokud jste zkompilovali sestavení předem v aplikaci pro konkrétní architekturu. Další informace o předkompilace najdete v tématu [Ngen.exe (Generátor nativních obrázků)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).|  
|**Jazyková verze**|Volitelné. Dvě části země a oblasti kód ISO ve kterém tato aplikace funguje. Výchozí hodnota je `neutral`.|  
|**Token veřejného klíče**|Volitelné. Veřejný klíč, kterým byl podepsán tento manifest aplikace. Pokud je to manifestu do nové nebo bez znaménka, toto pole se zobrazí jako `Unsigned`.|  
  
### <a name="description-tab"></a>Popis karty  
 Tyto informace je obvykle poskytují v manifestu nasazení. Tato pole je možné upravit pouze pokud **použití aplikace Manifest informace o vztahu důvěryhodnosti** zaškrtnuté políčko na **možnosti aplikace** kartu.  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Publisher**|Název osoba nebo organizace odpovědná za aplikace. Tato hodnota se používá jako název složky nabídky Start.|  
|**Produkt**|Úplný název produktu. Pokud jste vybrali **nainstalovat místně** pro **typ aplikace** elementu na **možnosti nasazení** kartě manifest nasazení, tento název bude, co se zobrazuje v **Start** odkaz nabídky a v **přidat nebo odebrat programy** pro tuto aplikaci.|  
|**Podpora umístění**|Adresa URL, ze kterého můžou zákazníci získat pomoc a podpora pro aplikace.|  
  
### <a name="application-options-tab"></a>Možnosti aplikace  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Prohlížeč aplikace Windows Presentation Foundation**|Určuje, zda se jedná o aplikaci WPF, která běží v prohlížeči jako aplikace prohlížeče XAML (XBAP).|  
|**Použijte informace o důvěryhodnosti v manifestu aplikace**|Určuje, zda tento manifest obsahuje informace o vztahu důvěryhodnosti.|  
  
### <a name="files-tab"></a>Karta soubory  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Adresář aplikace**|Adresář, ve kterém jsou umístěny soubory aplikace. Použijte symbol tří teček (**...** ) tlačítko a vyberte adresář.|  
|**Naplnění**|Přidá všechny soubory v adresáři aplikace a jeho podadresářích do manifestu aplikace. Pokud MageUI.exe najde v adresáři jeden spustitelný soubor, automaticky označí to jako vstupní bod, což je soubor nejdřív nespustí při spuštění aplikace ClickOnce na straně klienta.|  
|**Soubory aplikace**|Obsahuje seznam všech souborů v aplikaci. Každý soubor má tři upravitelné atributy, které jsou popsány níže.|  
|**Typ souboru**|Typ souboru může být jednu ze čtyř hodnot:<br /><br /> -Žádný.<br />-Vstupní bod. Primární spustitelný soubor aplikace. Pouze jeden spustitelný soubor může být označený jako vstupní bod.<br />-Datový soubor. Soubor, jako je například soubor XML, poskytující data aplikaci.<br />-Soubor ikony. Aplikace, jako například se zobrazí ikona na ploše nebo v horním rohu okna aplikace.|  
|**Optional**|Soubory označené volitelné se nestáhnou počáteční instalace nebo aktualizace, ale za běhu pomocí rozhraní API na vyžádání System.Deployment stáhnout. Další informace najdete v tématu [návod: stahování sestavení na vyžádání pomocí technologie ClickOnce pomocí rozhraní API nasazení návrháře](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer).|  
|**Skupiny**|Popisek pro sadu volitelné soubory. Můžete použít popisek skupiny do sady souborů a stáhněte si batch souborů pomocí jediného volání rozhraní API pomocí rozhraní API na vyžádání.|  
  
### <a name="permissions-required-tab"></a>Karta požadovaná oprávnění  
 Použití **oprávněních** kartu, pokud je potřeba udělit větší přístup k místnímu počítači než je ve výchozím nastavení udělena vaší aplikace. Další informace najdete v tématu [zabezpečení aplikací ClickOnce](/visualstudio/deployment/securing-clickonce-applications).  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Nastavit typ oprávnění**|Nastavení minimální oprávnění požadují tuto aplikaci spustit v klientském počítači. Popis těchto sad oprávnění a oprávnění, která nemají nebo není vyžadují, najdete v článku [NIB: pojmenované sady oprávnění](https://msdn.microsoft.com/library/08250d67-c99d-4ab0-8d2b-b0e12019f6e3).|  
|**Podrobnosti**|XML vytvořené pro manifest aplikace pro reprezentaci oprávnění nastavena. Pokud nemáte dostatečné povědomí o formátu XML manifestu aplikace, neměli byste ručně upravovat tato konfigurace XML. Další informace najdete v tématu [Manifest aplikace ClickOnce](/visualstudio/deployment/clickonce-application-manifest).|  
  
### <a name="deployment-manifest-tab"></a>Karta s manifestem nasazení  
 **Manifest nasazení** karta obsahuje následující karty.  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Jméno**|Určuje identifikační informace o tomto nasazení.|  
|**Popis**|Určuje vydavatele, produkt a podporu informace.|  
|**Možnosti nasazení**|Určuje další informace o nasazení, jako je například typ aplikace a počáteční umístění.|  
|**Možnosti aktualizace**|Určuje, jak často [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] by měla vyhledávat aktualizace aplikace.|  
|**Odkaz na aplikaci**|Určuje manifest aplikace pro toto nasazení.|  
  
### <a name="name-tab"></a>Název karty  
 **Název** kartě se zobrazí při prvním vytvoření nebo otevření manifestu nasazení. Jednoznačně identifikuje nasazení a volitelně určuje platnou cílovou platformu.  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Jméno**|Požadováno. Název manifestu nasazení. Obvykle stejný jako název souboru.|  
|**Verze**|Požadováno. Číslo verze nasazení ve formě *N.N.N.N*. Pouze první hlavní číslo sestavení je povinný. Například pro verzi 1.0 rozhraní aplikace, bude obsahovat platné hodnoty `1`, `1.0`, `1.0.0`, a `1.0.0.0`.|  
|**Procesor**|Volitelné. Architektura počítače, na kterém můžete spustit toto nasazení. Výchozí hodnota je `msil`, nebo Microsoft Intermediate Language, výchozím formátu pro všechny spravované sestavení. Toto pole změňte, pokud kompilujete sestavení v aplikaci pro konkrétní architekturu.|  
|**Jazyková verze**|Volitelné. Kód pro zemi/oblast ISO se dvě části, ve kterém tato aplikace funguje. Výchozí hodnota je `neutral`.|  
|**Token veřejného klíče**|Volitelné. Veřejný klíč, kterým byl podepsán manifestu nasazení. Pokud je to manifestu do nové nebo bez znaménka, toto pole se zobrazí jako `Unsigned`.|  
  
### <a name="description-tab"></a>Popis karty  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Publisher**|Požadováno. Název osoba nebo organizace odpovědná za aplikace. Tato hodnota se používá jako název složky nabídky Start.|  
|**Produkt**|Požadováno. Úplný název produktu. Pokud jste vybrali **nainstalovat místně** pro **typ aplikace** elementu na **možnosti nasazení** kartu, tento název bude, co se zobrazuje v **Start** odkaz nabídky a v **přidat nebo odebrat programy** pro tuto aplikaci.|  
|**Podpora umístění**|Volitelné. Adresa URL, ze kterého můžou zákazníci získat pomoc a podpora pro aplikace.|  
  
### <a name="deployment-options-tab"></a>Možnosti nasazení  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Typ aplikace**|Volitelné. Určuje, jestli tato aplikace sám nainstalovat na klientský počítač (**nainstalovat místně**), spustí online (**pouze Online**), nebo je aplikace WPF, která běží v prohlížeči (**prohlížeče WPF Aplikace**). Výchozí hodnota je **nainstalovat místně**.|  
|**Počáteční umístění**|Volitelné. Adresa URL, ze kterého by ve skutečnosti spuštění aplikace. Užitečné při nasazování aplikace z disku CD, který by měl aktualizovat přímo z webu.|  
|**Zahrnutí do manifestu počáteční umístění (ProviderURL)**|Volitelné. Určuje adresu URL, která [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] prozkoumá aktualizací aplikace.|  
|**Po instalaci automaticky, spusťte aplikaci**|Požadováno. Určuje, že [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] aplikace by měl spustit okamžitě po počáteční instalaci z adresy URL. Výchozí hodnota je, že je zaškrtnuto zaškrtávací políčko.|  
|**Povolit parametry adresy URL, které se mají předat aplikaci**|Požadováno. Povoluje přenos dat parametru [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] aplikace pomocí řetězce dotazu připojí k adrese URL manifestu nasazení. Výchozí hodnota je, že je zrušeno zaškrtnutí políčka.|  
|**Použít příponu .deploy souborů**|Požadováno. Pokud je vybráno, všechny soubory v manifestu aplikace musí mít příponu .deploy odstraní. Výchozí hodnota je, že je zrušeno zaškrtnutí políčka.|  
  
### <a name="update-options-tab"></a>Aktualizovat kartu Možnosti  
 **Možnosti aktualizace** karta obsahuje pouze možnosti při uvedeným **typ aplikace** výběr pole na **název** karty nastavená na **nainstalovat místně** .  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Tato aplikace by měla vyhledávat aktualizace**|Určuje, zda [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] by měla vyhledávat aktualizace aplikace. Pokud toto políčko není zaškrtnuto, aplikace nebude kontrolovat aktualizace, pokud ho aktualizujete programově pomocí rozhraní API v <xref:System.Deployment.Application> oboru názvů.|  
|**Zvolte, pokud by měla aplikace vyhledávat aktualizace**|Poskytuje dvě možnosti pro kontroly aktualizací:<br /><br /> -   **Před spuštěním aplikace**. Kontrola aktualizací se provádí před spuštění aplikace.<br />-   **Po spuštění aplikace**. Kontrola aktualizací začíná, jakmile byla inicializována hlavního formuláře aplikace a spustí při příštím spuštění aplikace.|  
|**Četnost kontroly aktualizací**|Určuje, jak často [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] by měla vyhledávat aktualizace:<br /><br /> -   **Zkontrolovat při každém spuštění aplikace**. [!INCLUDE[ndptecclick](../../../includes/ndptecclick-md.md)] provede kontrolu aktualizace pokaždé, když uživatel otevře aplikaci.<br />-   **Zkontrolujte každé**: vyberte časový interval a jednotka (hodiny, dny nebo týdny), která musí uplynout před vyhledávají se aktualizace.|  
|**Zadejte minimální požadovanou verzi této aplikace**|Volitelné. Určuje, že konkrétní verzi aplikace požadovanou instalaci, bránit uživatelům v práci se starší verzí.|  
|**Verze**|Požadováno pokud **zadat minimální požadovanou verzi této aplikace** zaškrtávací políčko je zaškrtnuto. Číslo verze musí být ve tvaru *N.N.N.N*. Pouze první hlavní číslo sestavení je povinný. Například pro verzi 1.0 rozhraní aplikace, bude obsahovat platné hodnoty `1`, `1.0`, `1.0.0`, a `1.0.0.0`.|  
  
### <a name="application-reference-tab"></a>Odkaz na kartě aplikace  
 **Odkaz na aplikaci** karta obsahuje stejné pole, jako **název** kartu popsané dříve v tomto tématu. Jedinou výjimkou jsou následující pole.  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Vyberte manifestu**|Umožňuje zvolit manifest aplikace. Všechna ostatní pole na této stránce se vyplní při výběru manifest aplikace.|  
  
## <a name="see-also"></a>Viz také  
 [ClickOnce – zabezpečení a nasazení](/visualstudio/deployment/clickonce-security-and-deployment)  
 [Návod: Ruční nasazení aplikace ClickOnce](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)  
 [Mage.exe (Manifest Generation and Editing Tool)](../../../docs/framework/tools/mage-exe-manifest-generation-and-editing-tool.md)
