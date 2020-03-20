---
title: MageUI.exe (generování manifestu a nástroj pro úpravy, grafický klient)
ms.date: 03/30/2017
helpviewer_keywords:
- Manifest Generation and Editing tool
- MageUI.exe
ms.assetid: f9e130a6-8117-49c4-839c-c988f641dc14
ms.openlocfilehash: 7d09e1283be8ec75df89957e91f0d8411c125b3b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74714458"
---
# <a name="mageuiexe-manifest-generation-and-editing-tool-graphical-client"></a>MageUI.exe (generování manifestu a nástroj pro úpravy, grafický klient)

Nástroj MageUI.exe podporuje stejné funkce jako nástroj příkazového řádku Mage.exe, ale používá uživatelské rozhraní (UI) založené na systému Windows. Pomocí tohoto nástroje je možné vytvářet, upravovat a podepisovat manifesty nasazení a aplikací. Nové manifesty, které jsou vytvořeny pomocí mageUI.exe cíl .NET Framework 4 profil klienta. Pro straší verze rozhraní .NET Framework byste měli použít starší verze nástroje MageUI.exe. Při přidávání nebo odebírání sestavení z manifestu nebo opětovném podepsání existujících manifestů mageUI.exe neaktualizuje manifest na cílový profil klienta rozhraní .NET Framework 4. Další informace naleznete v [tématu Mage.exe (Nástroj pro generování a úpravy manifestu).](mage-exe-manifest-generation-and-editing-tool.md)

 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li nástroj spustit, použijte příkazový řádek pro vývojáře pro sadu Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7). Další informace naleznete v [příkazových koncích](developer-command-prompt-for-vs.md).

 Dvě verze Mage.exe a MageUI.exe jsou součástí sady Visual Studio. Chcete-li zobrazit informace o verzi, spusťte soubor MageUI.exe, vyberte **nápovědu**a vyberte **možnost O .** Tato dokumentace popisuje verzi 4.0.x.x nástrojů Mage.exe a MageUI.exe.

> [!NOTE]
> MageUI.exe nepodporuje [prvek compatibleFrameworks](/visualstudio/deployment/compatibleframeworks-element-clickonce-deployment) při ukládání manifestu aplikace, který již byl podepsán certifikátem pomocí souboru MageUI.exe. Místo toho je nutné použít [mage.exe](mage-exe-manifest-generation-and-editing-tool.md).  
  
## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní  
 Následující tabulka obsahuje dostupné položky nabídek a panelu nástrojů.  
  
|Příkaz|Nabídka|Zástupce|Popis|  
|-------------|----------|--------------|-----------------|  
|**Manifest aplikace**|**Soubor, Nový**||Vytvoří nový manifest aplikace.|  
|**Manifest nasazení**|**Soubor, Nový**||Vytvoří nový manifest nasazení.|  
|**Otevřít**|**Soubor**|CTRL+O|Otevře existující manifest nasazení, manifest aplikace nebo důvěryhodnou licenci v režimu úprav.|  
|**Zavřít**|**Soubor**|CTRL+F4|Zavře otevřený soubor.<br /><br /> Upravíte-li soubor před jeho uzavřením, požádá nástroj MageUI.exe o opětovné podepsání souboru veřejným klíčem, párem klíčů nebo uloženým certifikátem.|  
|**Uložit**|**Soubor**|CTRL+S|Uloží soubor, na který je aktuálně zaměřen uživatelský vstup, na disk.|  
|**Uložit jako**|**Soubor**||Uloží soubor na disk a umožní zadat název souboru nebo jeho umístění.|  
|**Uložit vše**|**Soubor**||Uloží změny pro všechny soubory otevřené v rámci nástroje MageUI.exe.|  
|**Předvolby**|**Soubor**||Otevře dialogové okno **Předvolby.** Další informace naleznete v následující části.|  
|**Ukončit**|**Soubor**|ALT+F4|Ukončí nástroj MageUI.exe.|  
|**Vyjmout**|**Upravit**|CTRL+X|Odstraní aktuálně vybraný text z aplikace a uloží jej do schránky.|  
|**Kopírovat**|**Upravit**|CTRL+C|Zkopíruje aktuálně vybraný text do schránky.|  
|**Vložit**|**Upravit**|CTRL+V|Vloží text ze schránky do aktuálního textového prvku.|  
|**Odstranit**|**Upravit**||Odstraní prvek aktuálně vybraný v seznamu, například licenci důvěryhodnosti na kartě **Manifest nasazení.**|  
|**Zavřít vše**|**Okno**||Zavře všechny soubory otevřené v nástroji MageUI.exe. Pokud je zapotřebí některé ze souborů uložit, vyzve nástroj MageUI.exe k jejich uložení. Nástroj MageUI.exe také vyžaduje výběr podepsaného klíče pro každý nepodepsaný nebo změněný soubor.|  
|**O aplikaci**|**Nápověda**||Zobrazuje verzi a informace o autorských právech nástroje MageUI.exe.|  
  
## <a name="preferences-dialog-box"></a>Dialogové okno Předvolby  
 Dialogové okno **Předvolby** obsahuje následující prvky.  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Přihlásit se k uložení**|Při uložení změn vyžaduje podepsání souboru.|  
|**Použití výchozího podpisový certifikát**|Používá klíč zadaný do textového pole **Soubor certifikátu** k podepsání všech souborů. Tím se eliminuje podpisová výzva, která se obvykle zobrazí při uložení souboru a je vybrána možnost **Přihlásit se při uložení.** Pomocí tlačítka tři tečky (**...**) vedle textového pole **Soubor certifikátu** vyberte soubor klíče.|  
|Algoritmus Digest|Určí algoritmus, jímž budou generovány přehledy závislostí. Hodnotou musí být „sha256RSA“ nebo „sha1RSA“. Použije SHA1 jako výchozí. Tato hodnota je použita v aplikaci i v manifestech nasazení. Pokud uživatel při ukládání manifestu zadá certifikát, použije se algoritmus v tomto certifikátu k vygenerování přehledu závislostí.|  
  
## <a name="signing-options-dialog-box"></a>Dialogové okno Možnosti podpisu  
 Dialogové okno **Možnosti podepisování** se zobrazí při prvním uložení licence manifestu nebo licence důvěryhodnosti nebo při změně licence manifestu nebo licence důvěryhodnosti. Zobrazí se pouze v případě, že je vybraná volba **Přihlásit se při uložení** v dialogovém okně **Předvolby.** Při podepisování manifestu, který určuje hodnotu v textovém poli **IDENTIFIKÁTOR URI časového razítka,** musíte být připojeni k Internetu.  
  
 Toto dialogové okno obsahuje následující prvky.  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Podepsat pomocí souboru certifikátu**|Podepíše manifest digitálním certifikátem uloženým v systému souborů.|  
|**Soubor**|Poskytuje prostor pro zadání cesty k souboru .pfx představujícímu certifikát.|  
|**...**|Otevře dialogové okno **Zvolit soubor** pro výběr existujícího souboru .pfx.|  
|**Nový**|Vytvoří nový soubor .pfx, který nelze ověřit skrze certifikační autoritu (CA). Další informace o typech certifikátů používaných k podepisování nasazení ClickOnce naleznete v [tématu Přehled nasazení důvěryhodných aplikací](/visualstudio/deployment/trusted-application-deployment-overview).|  
|**Heslo**|Poskytuje prostor pro zadání hesla použitého k podepisování certifikátů. Pokud není použito, může být ponecháno prázdné.|  
|**Podepisovat s uloženým certifikátem**|Zobrazí seznam s vlastním výběrem digitálních certifikátů uložených v úložišti certifikátů počítače.|  
|**Identifikátor URI pro časové razítko**|Zobrazí adresu Uniform Resource Locator (URI) služby digitálního časového razítka. Vytvoření časového razítka v manifestu umožňuje vyhnout se nutnosti znovu manifesty podepisovat v případě, že digitální certifikát vyprší ještě před nasazením další verze aplikace. Další informace naleznete v tématech [Členové programu kořenového certifikátu systému Windows](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn265983(v=ws.11)) a [ClickOnce a Authenticode](/visualstudio/deployment/clickonce-and-authenticode).|  
|**Nepodepisovat**|Umožňuje uložit manifest bez přidání podpisu z digitálního certifikátu.|  
  
## <a name="tab-and-panel-descriptions"></a>Popisy karet a panelů  
 Dokument se při otevření pomocí nástroje MageUI.exe zobrazí na vlastní kartě. Každá karta obsahuje sadu panelů vlastností. Panely obsahují seskupenou podmnožinu dat dokumentu.  
  
### <a name="application-manifest-tab"></a>Karta Manifest aplikace  
 Na kartě **Manifest aplikace** se zobrazí obsah manifestu aplikace. Manifest aplikace popisuje všechny soubory, které jsou součástí nasazení, a oprávnění potřebná pro spuštění aplikace v klientovi.  
  
 Karta **Manifest aplikace** obsahuje následující karty.  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Název**|Určuje identifikační informace o tomto nasazení.|  
|**Popis**|Určuje informace o vydavateli, produktu a podpoře.|  
|**Možnosti aplikace**|Určuje, zda se jedná o aplikaci prohlížeče a zda je tento manifest zdrojem informací o důvěryhodnosti.|  
|**Soubory**|Určuje všechny soubory, které tvoří toto nasazení.|  
|**Je vyžadována oprávnění.**|Určuje minimální sadu oprávnění požadovanou aplikací ke spuštění v klientovi.|  
  
### <a name="name-tab"></a>Karta Název  
 Karta **Název** se zobrazí při prvním vytvoření nebo otevření manifestu aplikace. Jednoznačně identifikuje nasazení a volitelně určuje platnou cílovou platformu.  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Název**|Povinná hodnota. Název manifestu aplikace. Obvykle stejný jako název souboru.|  
|**Verze**|Povinná hodnota. Číslo verze nasazení ve formuláři *N.N.N.N*. Je vyžadováno pouze první hlavní číslo sestavení. Například pro verzi 1.0 aplikace by platné `1` `1.0`hodnoty `1.0.0`zahrnovaly , , a `1.0.0.0`.|  
|**Procesor**|Nepovinný parametr. Architektura počítače, na kterém lze spustit toto nasazení. Výchozí hodnota `msil`je nebo Microsoft Intermediate Language, což je výchozí formát všech spravovaných sestavení. Toto pole změňte, pokud jste předkompilovali sestavení v aplikaci pro konkrétní architekturu. Další informace o předkompilaci naleznete v [tématu Ngen.exe (Native Image Generator)](ngen-exe-native-image-generator.md).|  
|**Kultury**|Nepovinný parametr. Dvoudílný kód země a oblasti ISO, ve kterém je tato aplikace spuštěna. Výchozí formát je `neutral`.|  
|**Token veřejného klíče**|Nepovinný parametr. Veřejný klíč, se kterým byl podepsán manifest této aplikace. Pokud se jedná o nový nebo nepodepsaný `Unsigned`manifest, bude toto pole zobrazeno jako .|  
  
### <a name="description-tab"></a>Karta Popis  
 Tyto informace jsou obvykle k dispozici v manifestu nasazení. Tato pole lze změnit pouze v případě, že je na kartě Možnosti aplikace zaškrtnuto políčko **Použít informace o důvěryhodnosti manifestu** **aplikace.**  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Vydavatel**|Jméno osoby nebo organizace odpovědné za aplikaci. Tato hodnota se používá jako název složky nabídky Start.|  
|**Produktu**|Úplný název produktu. Pokud jste vybrali **možnost Instalovat místně** pro prvek Typ **aplikace** na kartě **Možnosti nasazení** manifestu nasazení, bude tento název uveden v odkazu nabídky **Start** a v části Přidat **nebo odebrat programy** pro tuto aplikaci.|  
|**Umístění podpory**|Adresa URL, ze které mohou zákazníci získat nápovědu a podporu pro aplikaci.|  
  
### <a name="application-options-tab"></a>Karta Možnosti aplikace  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Aplikace prohlížeče Windows Presentation Foundation**|Určuje, zda se jedná o aplikaci WPF, která se spouští v prohlížeči jako aplikace prohlížeče XAML (XBAP).|  
|**Použít informace o důvěryhodnosti manifestu aplikace**|Určuje, zda tento manifest obsahuje informace o důvěryhodnosti.|  
  
### <a name="files-tab"></a>Karta Soubory  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Adresář aplikace**|Adresář, ve kterém jsou umístěny soubory aplikace. Pomocí tlačítka elipsy (**...**) vyberte adresář.|  
|**Naplnění**|Přidá všechny soubory v adresáři aplikace a podadresáře do manifestu aplikace. Pokud program MageUI.exe najde v adresáři jeden spustitelný soubor, automaticky jej označí jako vstupní bod, což je soubor, který byl poprvé spuštěn při spuštění aplikace ClickOnce v klientovi.|  
|**Soubory aplikací**|Zobrazí seznam všech souborů v aplikaci. Každý soubor má tři upravitelné atributy, popsané níže.|  
|**Typ souboru**|Typ souboru může být jedna ze čtyř hodnot:<br /><br /> - Žádné.<br />- Vstupní bod. Primární spustitelný soubor aplikace. Jako vstupní bod lze označit pouze jeden spustitelný soubor.<br />- Datový soubor. Soubor, například soubor XML, který do aplikace dodává data.<br />- Soubor ikon. Ikona aplikace, například na ploše nebo v rohu okna aplikace.|  
|**Volitelné**|Soubory označené jako volitelné nejsou staženy při počáteční instalaci nebo aktualizaci, ale mohou být staženy za běhu pomocí rozhraní API System.Deployment On-Demand. Další informace naleznete [v tématu Návod: Stahování sestavení na vyžádání pomocí rozhraní API pro nasazení ClickOnce pomocí návrháře](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer).|  
|**Skupiny**|Popisek pro sadu volitelných souborů. Popisek skupiny můžete použít na sadu souborů a pomocí rozhraní API na vyžádání stáhnout dávku souborů s jedním voláním rozhraní API.|  
  
### <a name="permissions-required-tab"></a>Karta Požadovaná oprávnění  
 Pokud potřebujete aplikaci udělit větší přístup k místnímu počítači, než je ve výchozím nastavení uděleno, použijte kartu **Požadovaná oprávnění.** Další informace naleznete [v tématu Zabezpečení aplikací ClickOnce](/visualstudio/deployment/securing-clickonce-applications).  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Typ sady oprávnění**|Minimální sada oprávnění vyžadovaná touto aplikací ke spuštění na straně klienta. Popis těchto sad oprávnění a oprávnění, která nepožadují nebo nepožadují, naleznete [v tématu Pojmenované sady oprávnění](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).|  
|**Podrobnosti**|Jazyk XML vytvořený pro manifest aplikace představuje sadu oprávnění. Pokud dobře neporozumíte formátu XML manifestu aplikace, neměli byste tento jazyk XML upravovat ručně. Další informace naleznete v tématu [ClickOnce Application Manifest](/visualstudio/deployment/clickonce-application-manifest).|  
  
### <a name="deployment-manifest-tab"></a>Karta Manifest nasazení  
 Karta **Manifest nasazení** obsahuje následující karty.  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Název**|Určuje identifikační informace o tomto nasazení.|  
|**Popis**|Určuje informace o vydavateli, produktu a podpoře.|  
|**Možnosti nasazení**|Určuje další informace o nasazení, jako je například typ aplikace a počáteční umístění.|  
|**Možnosti aktualizace**|Určuje, jak často by měl ClickOnce kontrolovat aktualizace aplikací.|  
|**Odkaz na aplikaci**|Určuje manifest aplikace pro toto nasazení.|  
  
### <a name="name-tab"></a>Karta Název  
 Karta **Název** se zobrazí při prvním vytvoření nebo otevření manifestu nasazení. Jednoznačně identifikuje nasazení a volitelně určuje platnou cílovou platformu.  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Název**|Povinná hodnota. Název manifestu nasazení. Obvykle stejný jako název souboru.|  
|**Verze**|Povinná hodnota. Číslo verze nasazení ve formuláři *N.N.N.N*. Je vyžadováno pouze první hlavní číslo sestavení. Například pro verzi 1.0 aplikace by platné `1` `1.0`hodnoty `1.0.0`zahrnovaly , , a `1.0.0.0`.|  
|**Procesor**|Nepovinný parametr. Architektura počítače, na kterém lze spustit toto nasazení. Výchozí hodnota `msil`je , nebo Microsoft Intermediate Language, výchozí formát všech spravovaných sestavení. Toto pole změňte, pokud jste zkompilovali sestavení v aplikaci pro určitou architekturu.|  
|**Kultury**|Nepovinný parametr. Dvoudílný kód země nebo oblasti ISO, ve kterém je tato aplikace spuštěna. Výchozí formát je `neutral`.|  
|**Token veřejného klíče**|Nepovinný parametr. Veřejný klíč, se kterým byl podepsán tento manifest nasazení. Pokud se jedná o nový nebo nepodepsaný `Unsigned`manifest, bude toto pole zobrazeno jako .|  
  
### <a name="description-tab"></a>Karta Popis  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Vydavatel**|Povinná hodnota. Jméno osoby nebo organizace odpovědné za aplikaci. Tato hodnota se používá jako název složky nabídky Start.|  
|**Produktu**|Povinná hodnota. Úplný název produktu. Pokud jste na kartě **Možnosti nasazení** vybrali **instalovat místně** pro prvek **Typ aplikace,** bude tento název uveden v odkazu **Nabídky Start** a v **polích Přidat nebo odebrat programy** pro tuto aplikaci.|  
|**Umístění podpory**|Nepovinný parametr. Adresa URL, ze které mohou zákazníci získat nápovědu a podporu pro aplikaci.|  
  
### <a name="deployment-options-tab"></a>Karta Možnosti nasazení  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Typ aplikace**|Nepovinný parametr. Určuje, zda se tato aplikace nainstaluje do klientského počítače (**Install Local ),** bude spuštěna online ( pouze**online**), nebo zda se jedná o aplikaci WPF, která se spouští v prohlížeči (**WPF Browser Application**). Výchozí nastavení je **Instalovat místně**.|  
|**Počáteční umístění**|Nepovinný parametr. Adresa URL, ze které by měla být aplikace skutečně spuštěna. Užitečné při nasazování aplikace z disku CD-ROM, který by se měl aktualizovat z webu.|  
|**Zahrnout počáteční umístění (ProviderURL) do manifestu**|Nepovinný parametr. Určuje adresu URL, na které technologie ClickOnce vyhledá aktualizace aplikace.|  
|**Automatické spuštění aplikace po instalaci**|Povinná hodnota. Určuje, že aplikace ClickOnce by měla být spuštěna ihned po počáteční instalaci z adresy URL. Výchozí je políčko je zaškrtnuto.|  
|**Povolit předání parametrů adresy URL aplikaci**|Povinná hodnota. Umožňuje přenos dat parametrů do aplikace ClickOnce prostřednictvím řetězce dotazu připojeného k adrese URL manifestu nasazení. Výchozí nastavení je políčko není zaškrtnuto.|  
|**Použít příponu .deploy file extension**|Povinná hodnota. Pokud je tato možnost vybrána, musí mít všechny soubory v manifestu aplikace příponu .deploy. Výchozí nastavení je políčko není zaškrtnuto.|  
  
### <a name="update-options-tab"></a>Karta Aktualizovat možnosti  
 Karta **Možnosti aktualizace** obsahuje pouze zde uvedené možnosti, pokud je pole **Výběr typu aplikace** na kartě **Název** nastaveno na možnost **Instalovat místně**.  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Tato aplikace by měla vyhledat aktualizace**|Určuje, zda má funkce ClickOnce vyhledat aktualizace aplikací. Pokud toto políčko není zaškrtnuto, aplikace nebude kontrolovat aktualizace, pokud jej aktualizovat <xref:System.Deployment.Application> programově pomocí api v oboru názvů.|  
|**Zvolte, kdy má aplikace vyhledat aktualizace**|Obsahuje dvě možnosti pro kontrolu aktualizací:<br /><br /> -   **Před spuštěním aplikace**. Kontrola aktualizace se provádí před spuštěním aplikace.<br />-   **Po spuštění aplikace**. Kontrola aktualizace začíná, jakmile je inicializována hlavní forma aplikace, a spustí se při příštím spuštění aplikace.|  
|**Frekvence kontroly aktualizace**|Určuje, jak často by měl ClickOnce vyhledat aktualizace:<br /><br /> -   **Zkontrolujte při každém spuštění aplikace**. ClickOnce provede kontrolu aktualizace pokaždé, když uživatel otevře aplikaci.<br />-   **Kontrola každé**: Vyberte časový interval a jednotku (hodiny, dny nebo týdny), která musí uplynout před kontrolou aktualizací.|  
|**Zadejte minimální požadovanou verzi pro tuto aplikaci.**|Nepovinný parametr. Určuje, že určitá verze aplikace je požadovanou instalací, která uživatelům brání v práci s dřívější verzí.|  
|**Verze**|Povinné, pokud je **zaškrtnuto políčko Zadat minimální požadovanou verzi pro tuto aplikaci.** Zadané číslo verze musí být ve tvaru *N.N.N.N*. Je vyžadováno pouze první hlavní číslo sestavení. Například pro verzi 1.0 aplikace by platné `1` `1.0`hodnoty `1.0.0`zahrnovaly , , a `1.0.0.0`.|  
  
### <a name="application-reference-tab"></a>Karta Odkaz na aplikaci  
 Karta **Odkaz na aplikaci** obsahuje stejná pole jako karta **Název** popsaná dříve v tomto tématu. Jedinou výjimkou je následující pole.  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Vybrat manifest**|Umožňuje zvolit manifest aplikace. Všechna ostatní pole na této stránce se naplní, když zvolíte manifest aplikace.|  
  
## <a name="see-also"></a>Viz také

- [ClickOnce Zabezpečení a nasazení](/visualstudio/deployment/clickonce-security-and-deployment)
- [Návod: Ruční nasazení aplikace ClickOnce](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)
- [Mage.exe (Manifest Generation and Editing Tool)](mage-exe-manifest-generation-and-editing-tool.md)
