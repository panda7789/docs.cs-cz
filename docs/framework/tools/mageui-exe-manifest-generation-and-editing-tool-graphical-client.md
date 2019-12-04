---
title: MageUI.exe (generování manifestu a nástroj pro úpravy, grafický klient)
ms.date: 03/30/2017
helpviewer_keywords:
- Manifest Generation and Editing tool
- MageUI.exe
ms.assetid: f9e130a6-8117-49c4-839c-c988f641dc14
ms.openlocfilehash: 7d09e1283be8ec75df89957e91f0d8411c125b3b
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714458"
---
# <a name="mageuiexe-manifest-generation-and-editing-tool-graphical-client"></a>MageUI.exe (generování manifestu a nástroj pro úpravy, grafický klient)

Nástroj MageUI.exe podporuje stejné funkce jako nástroj příkazového řádku Mage.exe, ale používá uživatelské rozhraní (UI) založené na systému Windows. Pomocí tohoto nástroje je možné vytvářet, upravovat a podepisovat manifesty nasazení a aplikací. Nové manifesty, které jsou vytvořeny pomocí nástroje MageUI. exe, cílí na profil klienta .NET Framework 4. Pro straší verze rozhraní .NET Framework byste měli použít starší verze nástroje MageUI.exe. Nástroj MageUI. exe při přidávání nebo odebírání sestavení z manifestu nebo opětovného podepisování stávajících manifestů neaktualizuje manifest na cílový profil klienta .NET Framework 4. Další informace naleznete v tématu [Mage. exe (Manifest Generation and Editing Tool)](mage-exe-manifest-generation-and-editing-tool.md).

 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li spustit nástroj, použijte Developer Command Prompt pro Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7). Další informace najdete v tématu [výzvy k zadání příkazu](developer-command-prompt-for-vs.md).

 Dvě verze Mage. exe a MageUI. exe jsou zahrnuty jako součást sady Visual Studio. Chcete-li zobrazit informace o verzi, spusťte nástroj MageUI. exe, vyberte možnost **nápovědu**a vyberte možnost **o produktu**. Tato dokumentace popisuje verzi 4.0.x.x nástrojů Mage.exe a MageUI.exe.

> [!NOTE]
> Nástroj MageUI. exe nepodporuje element [compatibleFrameworks](/visualstudio/deployment/compatibleframeworks-element-clickonce-deployment) při ukládání manifestu aplikace, který již byl podepsán certifikátem pomocí nástroje MageUI. exe. Místo toho je nutné použít nástroj [Mage. exe](mage-exe-manifest-generation-and-editing-tool.md).  
  
## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní  
 Následující tabulka obsahuje dostupné položky nabídek a panelu nástrojů.  
  
|Příkaz|Nabídka|Zástupce|Popis|  
|-------------|----------|--------------|-----------------|  
|**Manifest aplikace**|**Soubor, nový**||Vytvoří nový manifest aplikace.|  
|**Manifest nasazení**|**Soubor, nový**||Vytvoří nový manifest nasazení.|  
|**Otevírají**|**Souborů**|CTRL+O|Otevře existující manifest nasazení, manifest aplikace nebo důvěryhodnou licenci v režimu úprav.|  
|**Uzavírací**|**Souborů**|CTRL+F4|Zavře otevřený soubor.<br /><br /> Upravíte-li soubor před jeho uzavřením, požádá nástroj MageUI.exe o opětovné podepsání souboru veřejným klíčem, párem klíčů nebo uloženým certifikátem.|  
|**Uloží**|**Souborů**|CTRL+S|Uloží soubor, na který je aktuálně zaměřen uživatelský vstup, na disk.|  
|**Uložit jako**|**Souborů**||Uloží soubor na disk a umožní zadat název souboru nebo jeho umístění.|  
|**Uložit vše**|**Souborů**||Uloží změny pro všechny soubory otevřené v rámci nástroje MageUI.exe.|  
|**Předvolby**|**Souborů**||Otevře dialogové okno **Předvolby** . Další informace naleznete v následující části.|  
|**Akci**|**Souborů**|ALT+F4|Ukončí nástroj MageUI.exe.|  
|**Snížit**|**Úpravě**|CTRL+X|Odstraní aktuálně vybraný text z aplikace a uloží jej do schránky.|  
|**Kopií**|**Úpravě**|CTRL+C|Zkopíruje aktuálně vybraný text do schránky.|  
|**Vlož**|**Úpravě**|CTRL+V|Vloží text ze schránky do aktuálního textového prvku.|  
|**Delete**|**Úpravě**||Odstraní aktuálně vybraný prvek v seznamu, jako je například licence Trust na kartě **manifest nasazení** .|  
|**Zavřít vše**|**Okno**||Zavře všechny soubory otevřené v nástroji MageUI.exe. Pokud je zapotřebí některé ze souborů uložit, vyzve nástroj MageUI.exe k jejich uložení. Nástroj MageUI.exe také vyžaduje výběr podepsaného klíče pro každý nepodepsaný nebo změněný soubor.|  
|**Upozorňován**|**Pomoc**||Zobrazuje verzi a informace o autorských právech nástroje MageUI.exe.|  
  
## <a name="preferences-dialog-box"></a>Dialogové okno Předvolby  
 Dialogové okno **Předvolby** obsahuje následující prvky.  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Přihlášení – uložit**|Při uložení změn vyžaduje podepsání souboru.|  
|**Použít výchozí podpisový certifikát**|Pro podepsání všech souborů používá klíč zadaný v textovém poli **soubor certifikátu** . Tím se eliminuje výzva k podepisování, která se obvykle zobrazuje při uložení souboru a když se **přihlásí možnost Uložit** . Chcete-li vybrat soubor klíče, použijte tlačítko se třemi tečkami ( **...** ) vedle textového pole **soubor certifikátu** .|  
|Algoritmus Digest|Určí algoritmus, jímž budou generovány přehledy závislostí. Hodnotou musí být „sha256RSA“ nebo „sha1RSA“. Použije SHA1 jako výchozí. Tato hodnota je použita v aplikaci i v manifestech nasazení. Pokud uživatel při ukládání manifestu zadá certifikát, použije se algoritmus v tomto certifikátu k vygenerování přehledu závislostí.|  
  
## <a name="signing-options-dialog-box"></a>Dialogové okno Možnosti podpisu  
 Dialogové okno **možnosti podepisování** se zobrazí, když uložíte manifest nebo důvěryhodnou licenci poprvé nebo když změníte manifest nebo důvěryhodnou licenci. Zobrazí se pouze v případě, že je vybrána možnost **přihlášení při uložení** v dialogovém okně **Předvolby** . Při podepisování manifestu, který určuje hodnotu v textovém poli **identifikátor URI časového razítka** , musíte být připojeni k Internetu.  
  
 Toto dialogové okno obsahuje následující prvky.  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Podepsat souborem certifikátu**|Podepíše manifest digitálním certifikátem uloženým v systému souborů.|  
|**Souborů**|Poskytuje prostor pro zadání cesty k souboru .pfx představujícímu certifikát.|  
|**...**|Otevře dialogové okno **zvolit soubor** pro výběr existujícího souboru. pfx.|  
|**New**|Vytvoří nový soubor .pfx, který nelze ověřit skrze certifikační autoritu (CA). Další informace o typech certifikátů používaných k podepisování nasazení ClickOnce naleznete v tématu [Přehled nasazení důvěryhodných aplikací](/visualstudio/deployment/trusted-application-deployment-overview).|  
|**Zadáno**|Poskytuje prostor pro zadání hesla použitého k podepisování certifikátů. Pokud není použito, může být ponecháno prázdné.|  
|**Podepsat uloženým certifikátem**|Zobrazí seznam s vlastním výběrem digitálních certifikátů uložených v úložišti certifikátů počítače.|  
|**Identifikátor URI pro časové razítko**|Zobrazí adresu Uniform Resource Locator (URI) služby digitálního časového razítka. Vytvoření časového razítka v manifestu umožňuje vyhnout se nutnosti znovu manifesty podepisovat v případě, že digitální certifikát vyprší ještě před nasazením další verze aplikace. Další informace naleznete v tématu [Členové programu kořenového certifikátu systému Windows](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn265983(v=ws.11)) a [ClickOnce a technologie Authenticode](/visualstudio/deployment/clickonce-and-authenticode).|  
|**Nepodepisovat**|Umožňuje uložit manifest bez přidání podpisu z digitálního certifikátu.|  
  
## <a name="tab-and-panel-descriptions"></a>Popisy karet a panelů  
 Dokument se při otevření pomocí nástroje MageUI.exe zobrazí na vlastní kartě. Každá karta obsahuje sadu panelů vlastností. Panely obsahují seskupenou podmnožinu dat dokumentu.  
  
### <a name="application-manifest-tab"></a>Karta manifest aplikace  
 Karta **manifest aplikace** zobrazuje obsah manifestu aplikace. Manifest aplikace popisuje všechny soubory, které jsou součástí nasazení, a oprávnění potřebná ke spuštění aplikace na klientovi.  
  
 Karta **manifest aplikace** obsahuje následující karty.  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Jméno**|Určuje identifikační informace o tomto nasazení.|  
|**Popis**|Určuje informace o vydavateli, produktu a podpoře.|  
|**Možnosti aplikace**|Určuje, zda se jedná o aplikaci prohlížeče a zda je tento manifest zdrojem informací o důvěryhodnosti.|  
|**Soubory**|Určuje všechny soubory, které tvoří toto nasazení.|  
|**Požadovaná oprávnění**|Určuje minimální sadu oprávnění, kterou aplikace vyžaduje ke spuštění na klientovi.|  
  
### <a name="name-tab"></a>Karta název  
 Karta **název** se zobrazí při prvním vytvoření nebo otevření manifestu aplikace. Jednoznačně identifikuje nasazení a volitelně určuje platnou cílovou platformu.  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Jméno**|Požadováno. Název manifestu aplikace. Obvykle je stejný jako název souboru.|  
|**Verze**|Požadováno. Číslo verze nasazení ve formátu n. n. *n*. n. Vyžaduje se pouze první hlavní číslo buildu. Například pro verzi 1,0 aplikace, platné hodnoty by zahrnovaly `1`, `1.0`, `1.0.0`a `1.0.0.0`.|  
|**Mobilních**|Volitelné. Architektura počítače, na které se dá toto nasazení spustit Výchozí hodnota je `msil`nebo převodní jazyk Microsoft, což je výchozí formát všech spravovaných sestavení. Toto pole změňte, pokud jste předem zkompilováni sestavení v aplikaci pro konkrétní architekturu. Další informace o předběžné kompilaci naleznete v souboru [Ngen. exe (generátor nativních imagí)](ngen-exe-native-image-generator.md).|  
|**Jazykových**|Volitelné. Kód země a oblasti ve dvou částech, ve kterých se tato aplikace spouští. Výchozí hodnota je `neutral`.|  
|**Token veřejného klíče**|Volitelné. Veřejný klíč, se kterým byl podepsán tento manifest aplikace. Pokud se jedná o nový nebo nepodepsaný manifest, toto pole se zobrazí jako `Unsigned`.|  
  
### <a name="description-tab"></a>Karta Popis  
 Tyto informace jsou obvykle k dispozici v manifestu nasazení. Tato pole lze změnit pouze v případě, že je na kartě **Možnosti aplikace** zaškrtnuto políčko **použít informace o důvěryhodnosti manifestu aplikace** .  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Microsoft**|Jméno osoby nebo organizace zodpovědné za aplikaci. Tato hodnota se používá jako název složky nabídky Start.|  
|**Produktu**|Úplný název produktu Pokud jste vybrali možnost **instalovat místně** pro prvek **Typ aplikace** na kartě **Možnosti nasazení** manifestu nasazení, bude tento název zobrazen v odkazu nabídky **Start** a v části **Přidat nebo odebrat programy** pro tuto aplikaci.|  
|**Umístění podpory**|Adresa URL, ze které mohou zákazníci získat nápovědu a podporu pro aplikaci.|  
  
### <a name="application-options-tab"></a>Karta Možnosti aplikace  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Aplikace Windows Presentation Foundation Browser**|Určuje, zda se jedná o aplikaci WPF, která běží v prohlížeči jako aplikace prohlížeče XAML (XBAP).|  
|**Použití informací o důvěryhodnosti manifestu aplikace**|Určuje, zda tento manifest obsahuje informace o důvěryhodnosti.|  
  
### <a name="files-tab"></a>Karta Soubory  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Adresář aplikace**|Adresář, ve kterém jsou umístěny soubory aplikace K výběru adresáře použijte tlačítko se třemi tečkami ( **...** ).|  
|**Fulltext**|Přidá všechny soubory v adresáři aplikace a podadresářích do manifestu aplikace. Pokud MageUI. exe najde jeden spustitelný soubor v adresáři, automaticky ho označí jako vstupní bod, což je soubor, který se poprvé spustí při spuštění aplikace ClickOnce na klientovi.|  
|**Soubory aplikace**|Zobrazí seznam všech souborů v aplikaci. Každý soubor má tři upravitelné atributy, které jsou popsány níže.|  
|**Typ souboru**|Typ souboru může být jedna ze čtyř hodnot:<br /><br /> NTato.<br />– Vstupní bod. Primární spustitelný soubor aplikace. Pouze jeden spustitelný soubor může být označen jako vstupní bod.<br />-Datový soubor. Soubor, jako je například soubor XML, který dodává data do aplikace.<br />– Ikona souboru. Ikona aplikace, například, se zobrazí na ploše nebo v rohu okna aplikace.|  
|**Optional**|Soubory označené jako volitelné se nestáhnou při počáteční instalaci nebo aktualizaci, ale můžou se stáhnout za běhu pomocí rozhraní API System. Deployment na vyžádání. Další informace naleznete v tématu [Návod: stahování sestavení na vyžádání pomocí rozhraní API nasazení ClickOnce pomocí návrháře](/visualstudio/deployment/walkthrough-downloading-assemblies-on-demand-with-the-clickonce-deployment-api-using-the-designer).|  
|**Skupiny**|Popisek pro sadu volitelných souborů. Můžete použít popisek skupiny pro sadu souborů a pomocí rozhraní API na vyžádání stáhnout dávku souborů s jedním voláním rozhraní API.|  
  
### <a name="permissions-required-tab"></a>Karta požadovaná oprávnění  
 Kartu **požadovaná oprávnění** použijte v případě, že potřebujete udělit aplikaci větší přístup k místnímu počítači, než který je ve výchozím nastavení povolený. Další informace najdete v tématu [zabezpečení aplikací ClickOnce](/visualstudio/deployment/securing-clickonce-applications).  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Typ sady oprávnění**|Minimální sada oprávnění, kterou tato aplikace vyžaduje ke spuštění na klientovi. Popis těchto sad oprávnění a oprávnění, která dělají nebo nepožadují, najdete v tématu [pojmenované sady oprávnění](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/4652tyx7(v=vs.100)).|  
|**Zobrazí**|KÓD XML vytvořený pro manifest aplikace, který představuje sadu oprávnění Pokud nemáte dobrý význam formátu XML manifestu aplikace, neměli byste tento kód XML upravovat ručně. Další informace naleznete v tématu [manifest aplikace ClickOnce](/visualstudio/deployment/clickonce-application-manifest).|  
  
### <a name="deployment-manifest-tab"></a>Karta manifest nasazení  
 Karta **manifest nasazení** obsahuje následující karty.  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Jméno**|Určuje identifikační informace o tomto nasazení.|  
|**Popis**|Určuje informace o vydavateli, produktu a podpoře.|  
|**Možnosti nasazení**|Určuje další informace o nasazení, jako je například typ aplikace a počáteční umístění.|  
|**Možnosti aktualizace**|Určuje, jak často má ClickOnce kontrolovat aktualizace aplikací.|  
|**Odkaz na aplikaci**|Určuje manifest aplikace pro toto nasazení.|  
  
### <a name="name-tab"></a>Karta název  
 Karta **název** se zobrazí při prvním vytvoření nebo otevření manifestu nasazení. Jednoznačně identifikuje nasazení a volitelně určuje platnou cílovou platformu.  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Jméno**|Požadováno. Název manifestu nasazení. Obvykle je stejný jako název souboru.|  
|**Verze**|Požadováno. Číslo verze nasazení ve formátu n. n. *n*. n. Vyžaduje se pouze první hlavní číslo buildu. Například pro verzi 1,0 aplikace, platné hodnoty by zahrnovaly `1`, `1.0`, `1.0.0`a `1.0.0.0`.|  
|**Mobilních**|Volitelné. Architektura počítače, na které se dá toto nasazení spustit Výchozí hodnota je `msil`, nebo Microsoft Intermediate Language, což je výchozí formát všech spravovaných sestavení. Toto pole změňte, pokud jste v aplikaci zkompilováni sestavení pro konkrétní architekturu.|  
|**Jazykových**|Volitelné. Kód země/oblasti ve dvou částech, ve kterém se tato aplikace spouští. Výchozí hodnota je `neutral`.|  
|**Token veřejného klíče**|Volitelné. Veřejný klíč, se kterým byl podepsán tento manifest nasazení. Pokud se jedná o nový nebo nepodepsaný manifest, toto pole se zobrazí jako `Unsigned`.|  
  
### <a name="description-tab"></a>Karta Popis  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Microsoft**|Požadováno. Jméno osoby nebo organizace zodpovědné za aplikaci. Tato hodnota se používá jako název složky nabídky Start.|  
|**Produktu**|Požadováno. Úplný název produktu Pokud jste vybrali možnost **instalovat místně** pro prvek **Typ aplikace** na kartě **Možnosti nasazení** , bude tento název zobrazen v odkazu nabídky **Start** a v části **Přidat nebo odebrat programy** pro tuto aplikaci.|  
|**Umístění podpory**|Volitelné. Adresa URL, ze které mohou zákazníci získat nápovědu a podporu pro aplikaci.|  
  
### <a name="deployment-options-tab"></a>Karta Možnosti nasazení  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Typ aplikace**|Volitelné. Určuje, jestli se tato aplikace nainstaluje do klientského počítače (**místně se nainstaluje**), běží online (**jenom online**), nebo je aplikace WPF, která běží v prohlížeči (**aplikace prohlížeče WPF**). Výchozí nastavení se **instaluje místně**.|  
|**Počáteční umístění**|Volitelné. Adresa URL, ze které má být aplikace skutečně spuštěna. Užitečné při nasazování aplikace z disku CD, který by se měl aktualizovat z webu.|  
|**Zahrnout počáteční umístění (ProviderURL) v manifestu**|Volitelné. Určuje adresu URL, na které technologie ClickOnce vyhledá aktualizace aplikace.|  
|**Automaticky spouštět aplikaci po instalaci**|Požadováno. Určuje, že aplikace ClickOnce by se měla spustit hned po počáteční instalaci z adresy URL. Ve výchozím nastavení je zaškrtnuté políčko.|  
|**Povolení parametrů adresy URL, které se mají předat aplikaci**|Požadováno. Povoluje přenos parametrů dat do aplikace ClickOnce prostřednictvím řetězce dotazu, který je připojený k adrese URL manifestu nasazení. Výchozím nastavením je zaškrtnutí políčka zrušeno.|  
|**Použít příponu souboru. deploy**|Požadováno. Pokud je tato možnost vybrána, všechny soubory v manifestu aplikace musí mít příponu. deploy. Výchozím nastavením je zaškrtnutí políčka zrušeno.|  
  
### <a name="update-options-tab"></a>Karta Možnosti aktualizace  
 Karta **Možnosti aktualizace** obsahuje jenom zde uvedené možnosti, když je pole pro výběr **typu aplikace** na kartě **název** nastavené na **místní instalaci**.  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Tato aplikace by měla vyhledávat aktualizace**|Určuje, zda má ClickOnce vyhledat aktualizace aplikace. Pokud toto políčko není zaškrtnuté, aplikace nebude kontrolovat aktualizace, pokud ji neaktualizujete programově pomocí rozhraní API v oboru názvů <xref:System.Deployment.Application>.|  
|**Vyberte, kdy má aplikace vyhledat aktualizace.**|Poskytuje dvě možnosti pro kontroly aktualizací:<br /><br /> -   **před spuštěním aplikace**. Tato aktualizace je provedena před spuštěním aplikace.<br />-   **po spuštění aplikace**. Po inicializaci hlavní formy aplikace se spustí Tato aktualizace a spustí se při příštím spuštění aplikace.|  
|**Aktualizace frekvence kontroly**|Určuje, jak často by měla technologie ClickOnce vyhledávat aktualizace:<br /><br /> -   **kontrolovat při každém spuštění aplikace**. ClickOnce provede kontrolu aktualizace pokaždé, když uživatel otevře aplikaci.<br />-   **kontrolovat každých**: vyberte časový interval a jednotku (hodiny, dny nebo týdny), které musí uplynout před kontrolou aktualizací.|  
|**Zadat minimální požadovanou verzi této aplikace**|Volitelné. Určuje, že konkrétní verze aplikace je požadovaná instalace, která uživatelům brání v práci se starší verzí.|  
|**Verze**|Povinné, pokud je zaškrtnuté políčko **pro tuto aplikaci zadat minimální požadovanou verzi** . Zadané číslo verze musí být ve formátu *n. n. n*. n. Vyžaduje se pouze první hlavní číslo buildu. Například pro verzi 1,0 aplikace, platné hodnoty by zahrnovaly `1`, `1.0`, `1.0.0`a `1.0.0.0`.|  
  
### <a name="application-reference-tab"></a>Karta odkaz na aplikaci  
 Karta **odkaz na aplikaci** obsahuje stejná pole jako na kartě **název** popsané dříve v tomto tématu. Jedinou výjimkou je následující pole.  
  
|Prvek uživatelského rozhraní (UI)|Popis|  
|----------------|-----------------|  
|**Vybrat manifest**|Umožňuje zvolit manifest aplikace. Všechna ostatní pole na této stránce budou naplněna při výběru manifestu aplikace.|  
  
## <a name="see-also"></a>Viz také:

- [ClickOnce – zabezpečení a nasazení](/visualstudio/deployment/clickonce-security-and-deployment)
- [Návod: Ruční nasazení aplikace ClickOnce](/visualstudio/deployment/walkthrough-manually-deploying-a-clickonce-application)
- [Mage.exe (Manifest Generation and Editing Tool)](mage-exe-manifest-generation-and-editing-tool.md)
