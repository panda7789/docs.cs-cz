---
title: Caspol.exe (nástroj zásad zabezpečení přístupu kódu)
ms.date: 03/30/2017
helpviewer_keywords:
- permission sets, modifying security policy
- security policy [.NET Framework], Code Access Security Policy tool
- enterprise security policy
- referencing code groups and permission sets
- user security policy
- Caspol.exe
- Code Access Security Policy tool
- code groups, modifying security policy
- application development [.NET Framework], security
- machine security policy
- security policy [.NET Framework], modifying
- manually editing security configuration files
ms.assetid: d2bf6123-7b0c-4e60-87ad-a39a1c3eb2e0
ms.openlocfilehash: a5a4068d0bf6f6f158ea9b2880785e227f96243d
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645576"
---
# <a name="caspolexe-code-access-security-policy-tool"></a>Caspol.exe (nástroj zásad zabezpečení přístupu kódu)
Nástroj Code Access Security (CAS) Policy (Caspol.exe) umožňuje uživatelům a správcům měnit zásady zabezpečení pro úroveň zásad počítače, úroveň zásad uživatele a úroveň zásad podniku.  
  
> [!IMPORTANT]
> Počínaje rozhraním .NET Framework 4 nemá caspol.exe vliv na zásady CAS, pokud není nastaven [ \<a nenastaven na verzi legacyCasPolicy> element](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) . `true` Libovolná nastavení zobrazená nebo upravená pomocí nástroje CasPol.exe ovlivňují pouze aplikace, které se přihlašují pomocí zásad CAS. Další informace naleznete v [tématu Změny zabezpečení](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).  
  
> [!NOTE]
> 64bitové počítače obsahují 64bitové i 32bitové verze zásad zabezpečení. Aby bylo zajištěno, že změny v zásadách se aplikují na 32bitové i 64bitové aplikace, je třeba spustit 32bitovou i 64bitovou verzi nástroje Caspol.exe.  
  
 Nástroj zásad CAS je automaticky nainstalován společně s rozhraním .NET Framework a se sadou Visual Studio. Soubor Caspol.exe naleznete ve\\*verzi* %windir%\Microsoft.NET\Framework v 32bitových systémech nebo %windir%\Microsoft.NET\Framework64\\*verze* v 64bitových systémech. (Umístění je například %windir%\Microsoft.NET\Framework64\v4.030319\caspol.exe pro rozhraní .NET Framework 4 v 64bitovém systému.) Pokud je v počítači vedle sebe spuštěno více verzí rozhraní .NET Framework, může být nainstalováno více verzí nástroje . Nástroj lze spustit z instalačního adresáře. Doporučujeme však použít [příkazová zobrazení](developer-command-prompt-for-vs.md), která nevyžaduje přechod do instalační složky.  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```console
caspol [options]  
```  
  
## <a name="parameters"></a>Parametry  
  
|Možnost|Popis|  
|------------|-----------------|  
|**-addfulltrust** *assembly_file*<br /><br /> – nebo –<br /><br /> **-af** *assembly_file*|Přidá sestavení implementující vlastní bezpečnostní objekt (jako je vlastní povolení nebo vlastní stav členství) na seznam sestavení úplné důvěryhodnosti pro konkrétní úroveň zásad. Argument *assembly_file* určuje sestavení, které má být přidat. Tento soubor musí být podepsán [silným názvem](../../standard/assembly/strong-named.md). Sestavení se silným názvem můžete podepsat pomocí [nástroje Silný název (Sn.exe).](sn-exe-strong-name-tool.md)<br /><br /> Pokaždé, když je sada oprávnění obsahující vlastní oprávnění přidána k zásadě, musí být sestavení implementující vlastní oprávnění přidáno na seznam úplné důvěryhodnosti pro danou úroveň zásad. Sestavení, která implementují vlastní bezpečnostní objekty (jako jsou vlastní skupiny kódů nebo podmínky členství) používaná v bezpečnostních zásadách (jako je například zásada počítače), by měla být vždy přidána na seznam sestavení úplné důvěryhodnosti. **Pozor:**  Pokud sestavení implementující vlastní objekt zabezpečení odkazuje na jiná sestavení, musíte nejprve přidat odkazovaná sestavení do seznamu sestavení s úplným vztahem důvěryhodnosti. Vlastní objekty zabezpečení vytvořené pomocí jazyka Visual Basic, C++ nebo JScript se odkazují na knihovny Microsoft.VisualBasic.dll, Microsoft.VisualC.dll nebo Microsoft.JScript.dll. Tato sestavení nejsou v seznamu sestavení úplné důvěryhodnosti ve výchozím nastavení obsažena. Před přidáním vlastního objektu zabezpečení musíte příslušné sestavení přidat do seznamu úplné důvěryhodnosti. Pokud tak neučiníte, přerušíte tím systém zabezpečení, což povede k selhání načtení všech sestavení. V takovém případě Caspol.exe **-all -reset** možnost nebude opravovat zabezpečení. Chcete-li opravit zabezpečení, musíte ručně odebrat vlastní objekt zabezpečení ze souborů zabezpečení.|  
|**-addgroup** {*parent_label &#124; parent_name*} *mship pset_name* [*vlajky*]<br /><br /> – nebo –<br /><br /> **-ag** {*parent_label &#124; parent_name*} *mship pset_name* [*vlajky*]|Přidá do hierarchie skupin kódu novou skupinu kódu. Můžete určit *parent_label* nebo *parent_name*. Argument *parent_label* určuje popisek (například 1. nebo 1.1.) skupiny kódu, která je nadřazenou přidanou kódovou skupinou. Argument *parent_name* určuje název skupiny kódu, která je nadřazenou přidanou skupinou kódu. Vzhledem k tomu, *parent_label* a *parent_name* lze zaměnitelně, caspol.exe musí být schopen rozlišovat mezi nimi. Proto *parent_name* nelze začínat číslem. Navíc *parent_name* může obsahovat pouze A-Z, 0-9 a podtržítko znak.<br /><br /> Argument *mship* určuje podmínku členství pro novou skupinu kódu. Další informace naleznete v tabulce argumentů *mship* dále v této části.<br /><br /> Argument *pset_name* je název sady oprávnění, která bude přidružena k nové skupině kódu. Můžete také nastavit jeden nebo více *příznaků* pro novou skupinu. Další informace naleznete v tabulce argumentů *příznaků* dále v této části.|  
|**-addpset** {*psfile* &#124; *psfile* p*set_name*}<br /><br /> – nebo –<br /><br /> **-ap** {*s názvem*_*psfile* &#124; *psfile* *pset_name*}|Přidá do zásad pojmenovanou sadu oprávnění. Sada oprávnění musí být napsána v jazyce XML a uložena do souboru .xml. Pokud soubor XML obsahuje název sady oprávnění, je určen pouze tento soubor (*psfile*). Pokud soubor XML neobsahuje název sady oprávnění, je nutné zadat název souboru XML (*psfile*) a název sady oprávnění (*pset_name*).<br /><br /> Všechna oprávnění použitá v sadě oprávnění musí být definována v sestaveních obsažených v globální mezipaměti sestavení (GAC).|  
|**-a**[**ll**]|Značí, že jsou všechny možnosti následující za touto možností aplikovány na zásady počítače, uživatele a podniku. Možnost **-all** vždy odkazuje na zásady aktuálně přihlášeného uživatele. Viz **-customall** možnost odkazovat na zásady uživatele jiného než aktuální ho uživatele.|  
|**-chggroup** {*label &#124;name*} {*mship* &#124; *pset_name* &#124;<br /><br /> *příznaky* `}`<br /><br /> – nebo –<br /><br /> **-cg** {*název &#124;_*{*mship* &#124; *pset_name* &#124;<br /><br /> *příznaky* `}`|Změní podmínku členství skupiny kódu, sadu oprávnění nebo nastavení **výhradních**příznaků , **levelfinal**, **name**nebo **description.** Můžete zadat *popisek* nebo *název*. Argument *popisku* určuje popisek (například 1. nebo 1.1.) kódové skupiny. Argument *název* určuje název kódové skupiny, kterou chcete změnit. Vzhledem k tomu, *že popisek* a *název* lze zaměnitelně, musí být caspol.exe schopen mezi nimi rozlišovat. *Název* proto nemůže začínat číslem. Kromě toho *název* může obsahovat pouze A-Z, 0-9 a podtržítko znak.<br /><br /> Argument *pset_name* určuje název sady oprávnění, která má být přidružena ke skupině kódu. Informace o argumentech *mship* a *flags* naleznete v tabulkách dále v této části.|  
|**-chgpset**  *psfile pset_name*<br /><br /> – nebo –<br /><br /> **-cp** *psfile pset_name*|Mění pojmenovanou sadu oprávnění. Argument *psfile* poskytuje novou definici pro sadu oprávnění; jedná se o serializovaný soubor sady oprávnění ve formátu XML. Argument *pset_name* určuje název sady oprávnění, kterou chcete změnit.|  
|**-customall**  *cesta*<br /><br /> – nebo –<br /><br /> **-ca**  *cesta*|Značí, že jsou všechny možnosti následující za touto možností aplikovány na zásady počítače, podniku a určeného vlastního uživatele. Je nutné zadat umístění konfiguračního souboru zabezpečení vlastního uživatele s argumentem *cesty.*|  
|**-cu**[**stomuser**] *cesta*|Umožňuje spravovat zásadu vlastního uživatele, která nepatří uživateli, jenž aktuálně spouští nástroj Caspol.exe. Je nutné zadat umístění konfiguračního souboru zabezpečení vlastního uživatele s argumentem *cesty.*|  
|**-podnik**<br /><br /> – nebo –<br /><br /> **-en**|Značí, že jsou všechny možnosti následující za touto možností aplikovány na zásady na úrovni podniku. Uživatelé, kteří nejsou podnikovými administrátory, nemají dostatečná práva pro modifikaci podnikové zásady, přestože si ji mohou zobrazit. V nepodnikových scénářích nebude tato zásada ve výchozím nastavení ovlivňovat zásadu počítače ani uživatele.|  
|**-e**[**xecution**] {**na** &#124; **off**}|Vypíná nebo zapíná mechanismus, jenž ověřuje, která oprávnění se mají před spuštěním kódu provést. **Poznámka:**  Tento přepínač je odebrán v rozhraní .NET Framework 4 a novějších verzích. Další informace naleznete v [tématu Změny zabezpečení](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes).|  
|**-f**[**orce**]|Zakáže, aby nástroj provedl autodestruktivní test a změní zásadu dle zadání uživatele. Nástroj Caspol.exe běžně ověřuje, zda může jakákoli změna zásady zabránit nástroji Caspol.exe ve správném spuštění. Pokud tomu tak je, nástroj Caspol.exe změnu zásady neuloží a zobrazí chybovou zprávu. Chcete-li vynutit Caspol.exe změnit zásady i v případě, že to brání Caspol.exe sám o sobě spuštění, použijte možnost **-force.**|  
|**-h**[**elp**]|Zobrazí syntaxi a možnosti příkazu pro nástroj Caspol.exe.|  
|**-l**[**ist**]|Vypíše hierarchii skupiny kódu a sad oprávnění konkrétního počítače, uživatele, podniku nebo všech úrovní zásad. Nástroj Caspol.exe zobrazuje nejprve popisek skupiny kódu a poté název, pokud není null.|  
|**-popis seznamu**<br /><br /> – nebo –<br /><br /> **-ld**|Vypíše všechny popisy skupiny kódu pro zadanou úroveň zásad.|  
|**-listfulltrust**<br /><br /> – nebo –<br /><br /> **-Pokud**|Vypíše obsah sestavení úplného vztahu důvěryhodnosti pro zadanou úroveň zásad.|  
|**-listgroups**<br /><br /> – nebo –<br /><br /> **-Lg**|Zobrazuje skupiny kódu konkrétní úrovně nebo všech úrovní zásad. Nástroj Caspol.exe zobrazuje nejprve popisek skupiny kódu a poté název, pokud není null.|  
|**-listpset** nebo **-lp**|Zobrazí sady oprávnění konkrétní úrovně nebo všech úrovní zásad.|  
|**-m**[**achine**]|Značí, že jsou všechny možnosti následující za touto možností aplikovány na zásady na úrovni počítače. Uživatelé, kteří nejsou administrátory, nemají dostatečná práva pro modifikaci zásady počítače, přestože si ji mohou zobrazit. Pro správce **-machine** je výchozí.|  
|**-polchgprompt** {**na** &#124; **off**}<br /><br /> – nebo –<br /><br /> **-pp** {**na** &#124; **vypnuto**}|Povoluje nebo zakazuje dotaz, který se zobrazí vždy, když je nástroj Caspol.exe spuštěn pomocí možnosti, která může způsobit změnu zásad.|  
|**-quiet**<br /><br /> – nebo –<br /><br /> **-q**|Dočasně zakazuje dotaz, který se normálně zobrazí pro možnost způsobující změny zásad. Globální nastavení dotazu na změnu se nezmění. Tuto možnost použijte pouze u samostatných příkazů, aby bylo zabráněno zakázání výzev pro všechny příkazy nástroje Caspol.exe.|  
|**-r**[**ecover**]|Obnoví zásady ze záložního souboru. Kdykoli je provedena změna zásady, uloží nástroj Caspol.exe starou zásadu do záložního souboru.|  
|**-remfulltrust** *assembly_file*<br /><br /> – nebo –<br /><br /> **-rf**  *assembly_file*|Odstraní sestavení ze seznamu úplné důvěryhodnosti na úrovni zásad. Tato operace by měla být provedena, pokud sada oprávnění obsahující vlastní oprávnění již není zásadou používána. Sestavení implementující vlastní oprávnění byste však měli odstranit ze seznamu úplné důvěryhodnosti pouze tehdy, pokud sestavení neimplementuje žádná další vlastní oprávnění, která jsou stále používána. Po odstranění sestavení ze seznamu by měla být rovněž odstraněna další sestavení, která jsou na něm závislá.|  
|**-remgroup** {*název &#124;popisku*}<br /><br /> – nebo –<br /><br /> **-rg** {l*abel &#124; jméno*}|Odstraňuje skupinu kódu zadanou popiskem nebo názvem. Pokud má zadaná skupina kódu podřízenou skupinu kódu, nástroj Caspol.exe odstraní rovněž všechny podřízené skupiny kódu.|  
|**-rempset** *pset_name*<br /><br /> – nebo –<br /><br /> **-rp** *pset_name*|Odstraní ze zásady zadanou sadu oprávnění. Argument *pset_name* označuje, která sada oprávnění k odebrání. Nástroj Caspol.exe odstraňuje sadu oprávnění pouze tehdy, pokud není asociována se skupinou kódu. Výchozí (vestavěné) sady oprávnění nemohou být odstraněny.|  
|**-reset**<br /><br /> – nebo –<br /><br /> **-rs**|Vrátí zásadu do původního stavu a uloží ji na disk. To se hodí vždy při podezření, že je změněná zásada neopravitelně poškozena a když je zapotřebí začít znovu s výchozími nastaveními instalace. Resetování se může rovněž hodit, když má být jako výchozí bod pro modifikaci konkrétních konfiguračních souborů zabezpečení použita výchozí zásada. Další informace naleznete [v tématu Ruční úprava konfiguračních souborů zabezpečení](#cpgrfcodeaccesssecuritypolicyutilitycaspolexeanchor1).|  
|**-resetlockdown**<br /><br /> – nebo –<br /><br /> **-rsld řekl:**|Vrátí zásadu do více omezující verze výchozího stavu a zachová ji na disk; vytvoří zálohu předchozí zásady počítače a zachová `security.config.bac`ji do souboru s názvem .  Uzamčená zásada je podobná výchozí zásadě s tím rozdílem, `Local Intranet`že `Trusted Sites`zásada neuděluje žádné oprávnění kódu z , a `Internet` zóny a odpovídající kódové skupiny nemají žádné podřízené kódové skupiny.|  
|**-resolvegroup** *assembly_file*<br /><br /> – nebo –<br /><br /> **-rsg**  *assembly_file*|Zobrazuje skupiny kódu, do kterých patří určité sestavení (*assembly_file).* Ve výchozím nastavení tato možnost zobrazuje úrovně zásad počítače, uživatele a podniku, ke kterým sestavení patří. Chcete-li zobrazit pouze jednu úroveň zásad, použijte tuto možnost s možností **-machine**, **-user**nebo **-enterprise.**|  
|**-resolveperm** *assembly_file*<br /><br /> – nebo –<br /><br /> **-rsp** *assembly_file*|Zobrazuje všechna oprávnění, která zadaná (nebo výchozí) úroveň zásady zabezpečení může poskytnout sestavení, pokud je sestavením povoleno spuštění. Assembly_file *assembly_file* argument určuje sestavení. Pokud zadáte možnost **-all,** nástroj Caspol.exe vypočítá oprávnění pro sestavení na základě zásad uživatele, počítače a organizace. v opačném případě platí výchozí pravidla chování.|  
|**-s**[**ecurity**] {**na** &#124; **off**}|Vypne nebo zapne zabezpečení přístupu kódu. Zadání **mj.** **Poznámka:**  Tento přepínač je odebrán v rozhraní .NET Framework 4 a novějších verzích. Další informace naleznete v [tématu Změny zabezpečení](https://docs.microsoft.com/previous-versions/dotnet/framework/security/security-changes). **Pozor:**  Pokud je zabezpečení přístupu kódu zakázáno, všechny požadavky na přístup kódu jsou úspěšné. Zakázání zabezpečení přístupu kódu způsobí, že bude systém zranitelný vůči útokům škodlivým kódem, jako jsou například viry nebo červi. Vypnutí zabezpečení přinese zlepšení výkonu, ale mělo by být použito pouze tehdy, pokud byla přijata další bezpečnostní opatření, která pomohou zajistit, aby celková bezpečnost systému nebyla narušena. Mezi příklady dalších bezpečnostních opatření patří: odpojení od veřejné sítě, fyzické zabezpečení počítačů atd.|  
|**-u**[**ser**]|Značí, že jsou všechny možnosti následující po této možnosti aplikovány na zásadu na uživatelské úrovni pro uživatele, který nástroj Caspol.exe spustil. Pro uživatele bez oprávnění správce je **-user** výchozí.|  
|**-?**|Zobrazí syntaxi a možnosti příkazu pro nástroj Caspol.exe.|  
  
 *Argument mship,* který určuje podmínku členství pro kódovou skupinu, lze použít s možnostmi **-addgroup** a **-chggroup.** Každý argument *mship* je implementován jako třída rozhraní .NET Framework. Chcete-li určit *mship,* použijte jednu z následujících možností.  
  
|Argument|Popis|  
|--------------|-----------------|  
|**-allcode**|Specifikuje veškerý kód. Další informace o této podmínce členství naleznete v tématu <xref:System.Security.Policy.AllMembershipCondition?displayProperty=nameWithType>.|  
|**-appdir**|Určuje adresář aplikace. Pokud zadáte **–appdir** jako podmínku členství, je důkaz adresy URL kódu porovnán s důkazem adresáře aplikace tohoto kódu. Pokud jsou obě hodnoty evidence stejné, byly podmínky členství splněny. Další informace o této podmínce členství naleznete v tématu <xref:System.Security.Policy.ApplicationDirectoryMembershipCondition?displayProperty=nameWithType>.|  
|**-vlastní**  *soubor XML*|Přidá vlastní podmínku členství. Povinný argument *xmlfile* určuje soubor XML, který obsahuje serializaci vlastní podmínky členství XML.|  
|**-hashhas** *hashAlg* {**-hex** *hashValue* &#124; **-file** *assembly_file* }|Určuje kód, který obsahuje zadanou hodnotu hash sestavení. Pro použití hodnoty hash jako podmínky členství ve skupině kódu je nutné zadat hodnotu hash nebo soubor sestavení. Další informace o této podmínce členství naleznete v tématu <xref:System.Security.Policy.HashMembershipCondition?displayProperty=nameWithType>.|  
|**-hospoda** { **-cert** *cert_file_name* &#124;<br /><br /> **-soubor** *signed_file_name* &#124; **-hex**  *hex_string* }|Určuje kód, který obsahuje zadaného vydavatele softwaru, jak je označeno souborem certifikátu, podpisem na souboru nebo šestnáctkovou reprezentací certifikátu X509. Další informace o této podmínce členství naleznete v tématu <xref:System.Security.Policy.PublisherMembershipCondition?displayProperty=nameWithType>.|  
|**-site** *web*|Určuje kód, který obsahuje zadanou webovou stránku původu. Příklad:<br /><br /> `-site** www.proseware.com`<br /><br /> Další informace o této podmínce členství naleznete v tématu <xref:System.Security.Policy.SiteMembershipCondition?displayProperty=nameWithType>.|  
|**-strong -file** *file_name* {*name* &#124; **-noname**} {*verze* &#124; **-noversion**}|Určuje kód, který má určitý silný název označený názvem souboru, názvem sestavení jako řetězec a verzí sestavení ve formátu *major*. *nezletilá*. *stavět*. *revize*. Příklad:<br /><br /> **-strong -file** myAssembly.exe myAssembly 1.2.3.4<br /><br /> Další informace o této podmínce členství naleznete v tématu <xref:System.Security.Policy.StrongNameMembershipCondition?displayProperty=nameWithType>.|  
|**-URL** *URL*|Určuje kód pocházející ze zadané adresy URL. Adresa URL musí obsahovat `http://` protokol, například nebo `ftp://`. Znak se zástupným znakem (\*) lze navíc použít k určení více sestavení z určité adresy URL. **Poznámka:**  Vzhledem k tomu, že adresu URL lze identifikovat pomocí více názvů, použití adresy URL jako podmínky členství není bezpečný způsob, jak zjistit identitu kódu. Kdykoli je to možné, použijte podmínku členství silného názvu, podmínku vydavatele nebo podmínku hodnoty hash. <br /><br /> Další informace o této podmínce členství naleznete v tématu <xref:System.Security.Policy.UrlMembershipCondition?displayProperty=nameWithType>.|  
|**-zone** *zonename*|Určuje kód pomocí zadané zóny původu. Argument *název zóny* může být jedna z následujících hodnot: **MyComputer**, **Intranet**, **Trusted**, **Internet**nebo **Untrusted**. Další informace o této podmínce členství naleznete v části <xref:System.Security.Policy.ZoneMembershipCondition> Třída.|  
  
 Argument *příznaky,* který lze použít s možnostmi **–addgroup** a **–chggroup,** je určen pomocí jedné z následujících možností.  
  
|Argument|Popis|  
|--------------|-----------------|  
|**-popis** "*popis*"|Pokud se používá s volbou **–addgroup,** určuje popis skupiny kódu, kterou chcete přidat. Pokud se používá s volbou **–chggroup,** určuje popis kódové skupiny, kterou chcete upravit. Argument *popisu* musí být uzavřen v uvozovkách.|  
|**-exkluzivní** {**na**&#124;**off**}|Pokud je nastavena **na**na , označuje, že pouze sada oprávnění přidružená ke skupině kódu, kterou přidáváte nebo upravujete, je považována, pokud určitý kód odpovídá podmínce členství skupiny kódu. Pokud je tato možnost nastavena na **vypnuto**, caspol.exe bere v úvahu sady oprávnění všech odpovídajících skupin kódu na úrovni zásad.|  
|**-levelfinal** {**na**&#124;**off**}|Pokud je nastavena **na na**, označuje, že žádná úroveň zásad pod úrovní, ve které se vyskytuje přidaná nebo upravená skupina kódu. Tato možnost je obvykle používaná na úrovni zásad počítače. Pokud je tento příznak například nastaven pro skupinu kódu na úrovni počítače a některý kód odpovídá podmínce členství této skupiny kódu, nástroj Caspol.exe nevypočítá a neaplikuje pro tento kód zásadu na uživatelské úrovni.|  
|**-název** "*jméno*"|Pokud se používá s volbou **–addgroup,** určuje název skriptování pro skupinu kódu, kterou chcete přidat. Pokud se používá s volbou **-chggroup,** určuje název skriptování pro kódovou skupinu, kterou chcete upravit. Argument *název* musí být uzavřen v uvozovkách. Argument *název* nemůže začínat číslem a může obsahovat pouze A-Z, 0-9 a znak podtržítka. Kódové skupiny mohou být odkazovány tímto *názvem* namísto jejich číselného popisku. *Název* je také velmi užitečné pro účely skriptování.|  
  
## <a name="remarks"></a>Poznámky  
 Zásada zabezpečení je vyjádřena pomocí tří úrovní zásad: počítačová, uživatelská a podniková. Sada oprávnění, kterou sestavení přijímá, je určena průnikem sad oprávnění povolených těmito třemi úrovněmi zásad. Každá úroveň zásad je reprezentována hierarchickou strukturou skupin kódu. Každá skupina kódu má podmínku členství, která určuje, který kód je členem této skupiny. Sada pojmenovaných oprávnění je rovněž asociována s každou skupinou kódu. Tato sada oprávnění určuje oprávnění, která modul runtime povoluje kódu splňujícímu podmínku členství. Hierarchie skupin kódu, společně se souvisejícími pojmenovanými sadami oprávnění, definuje a spravuje každou úroveň zásad zabezpečení. Pomocí možností **–user**, **-customuser**, **-machine** a **-enterprise** můžete nastavit úroveň zásad zabezpečení.  
  
 Další informace o zásadách zabezpečení a způsobu, jakým doba běhu určuje oprávnění k udělení kódu, naleznete v [tématu Správa zásad zabezpečení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c1k0eed6(v=vs.100)).  
  
## <a name="referencing-code-groups-and-permission-sets"></a>Odkazování na skupiny kódu a sady oprávnění  
 Chcete-li usnadnit odkazy na kódové skupiny v hierarchii, možnost **-list** zobrazí odsazený seznam kódových skupin spolu s jejich číselnými popisky (1, 1.1, 1.1.1 a tak dále). Další operace příkazového řádku zaměřené na skupiny kódu využívají k odkazování na specifické skupiny kódu také číselné popisky.  
  
 Pojmenované sady jsou odkazovány podle svých názvů. Možnost **–list** zobrazí seznam kódových skupin následovaný seznamem pojmenovaných sad oprávnění dostupných v této zásadě.  
  
## <a name="caspolexe-behavior"></a>Chování nástroje Caspol.exe  
 Všechny možnosti kromě **-s**[**ecurity**] {**na** &#124; **off**} použijte verzi rozhraní .NET Framework, se kterou byl caspol.exe nainstalován. Pokud spustíte soubor Caspol.exe, který byl nainstalován s verzí *X* za běhu, změny se vztahují pouze na tuto verzi. Jiné souběžné instalace modulu runtime, pokud nějaké existují, nejsou ovlivněny. Pokud je nástroj Caspol.exe spuštěn z příkazového řádku, aniž by se nacházel v adresáři konkrétní verze modulu runtime, bude spuštěn z prvního adresáře verze modulu runtime v cestě (obvykle to bývá poslední nainstalovaná verze).  
  
 Možnost **-s**[**ecurity**] {**on** &#124; **off**} je operace pro celý počítač. Vypnutí zabezpečení přístupu kódu ukončí kontroly zabezpečení veškerého spravovaného kódu pro všechny uživatele na počítači. Pokud jsou na počítači současně nainstalovány různé verze rozhraní .NET Framework, vypne tento příkaz zabezpečení pro všechny verze nainstalované na počítači. Přestože možnost **-list** ukazuje, že zabezpečení je vypnuto, nic jiného jasně neukazuje pro ostatní uživatele, že zabezpečení bylo vypnuto.  
  
 Pokud uživatel bez práv správce spustí soubor Caspol.exe, všechny možnosti odkazují na zásady na úrovni uživatele, pokud není zadána možnost **–machine.** Když správce spustí Soubor Caspol.exe, všechny možnosti odkazují na zásady počítače, pokud není zadána možnost **–user.**  
  
 Caspol.exe musí být udělena ekvivalent **Vše** oprávnění nastavena na funkci. Nástroj má ochranný mechanismus, který zabraňuje zásadě, aby byla modifikována způsobem, který by nástroji Caspol.exe znemožnil získat oprávnění nutná pro jeho spuštění. Pokud se o takovou změnu pokusíte, nástroj Caspol.exe oznámí, že požadovaná změna zásady nástroj poškodí a změna zásady bude zamítnuta. Tento ochranný mechanismus můžete vypnout pro daný příkaz pomocí volby **–force.**  
  
<a name="cpgrfcodeaccesssecuritypolicyutilitycaspolexeanchor1"></a>
## <a name="manually-editing-the-security-configuration-files"></a>Ruční úprava konfiguračních souborů zabezpečení  
 Tři konfigurační soubory zabezpečení odpovídají třem úrovním zásad podporovaných nástrojem Caspol.exe: jeden je pro zásadu počítače, jeden pro zásadu daného uživatele a jeden pro zásadu podniku. Tyto soubory jsou vytvořeny na disku, když je zásada počítače, uživatele nebo podniku změněna pomocí nástroje Caspol.exe. Možnost **–reset** v souboru Caspol.exe můžete v případě potřeby uložit výchozí zásady zabezpečení na disk.  
  
 Ve většině případů není manuální úprava těchto konfiguračních souborů zabezpečení doporučena. Mohou se však vyskytnout scénáře, ve kterých je úprava těchto souborů nezbytná. Například, když chce správce upravit konfiguraci zabezpečení pro konkrétního uživatele.  
  
## <a name="examples"></a>Příklady  
 **-addfulltrust**  
  
 Předpokládejme, že byla do zásady počítače přidána sada oprávnění obsahující vlastní oprávnění. Toto vlastní oprávnění `MyPerm.exe`je `MyPerm.exe` implementováno `MyOther.exe`v oblasti a odkazuje na třídy v . Obě sestavení musí být přidána do seznamu sestavení úplné důvěryhodnosti. Následující příkaz přidá `MyPerm.exe` sestavení do úplného seznamu důvěryhodných klientů pro zásady počítače.  
  
```console  
caspol -machine -addfulltrust MyPerm.exe  
```  
  
 Následující příkaz přidá `MyOther.exe` sestavení do úplného seznamu důvěryhodných klientů pro zásady počítače.  
  
```console  
caspol -machine -addfulltrust MyOther.exe  
```  
  
 **-přidat skupinu**  
  
 Následující příkaz přidá do kořene hierarchie skupin kódu zásady počítače podřízenou skupinu kódu. Nová skupina kódů je členem zóny **Internet** a je přidružena k sadě oprávnění **Spuštění.**  
  
```console  
caspol -machine -addgroup 1.  -zone Internet Execution  
```  
  
 Následující příkaz přidá podřízenou skupinu \\kódů, která poskytuje share \netserver\netshare oprávnění místní intranetu.  
  
```console  
caspol -machine -addgroup 1. -url \\netserver\netshare\* LocalIntranet  
```  
  
 **-addpset**  
  
 Následující příkaz přidá `Mypset` sadu oprávnění do zásad uživatele.  
  
```console  
caspol -user -addpset Mypset.xml Mypset  
```  
  
 **-chggroup**  
  
 Následující příkaz změní oprávnění nastavená v zásadách uživatele skupiny kódů označené 1.2. do sady oprávnění **spuštění.**  
  
```console  
caspol -user -chggroup 1.2. Execution  
```  
  
 Následující příkaz změní podmínku členství ve výchozí zásadě skupiny kódů označené 1.2.1. a změní nastavení **výhradní** ho příznaku. Podmínka členství je definována jako kód, který pochází ze zóny **Internet** a je zapnutý **výhradní** příznak.  
  
```console  
caspol -chggroup 1.2.1. -zone Internet -exclusive on  
```  
  
 **-chgpset**  
  
 Následující příkaz změní sadu oprávnění `Mypset` s názvem na `newpset.xml`sadu oprávnění obsaženou v . Aktuální verze nepodporuje změnu sady oprávnění, která je používána hierarchií skupiny kódu.  
  
```console  
caspol -chgpset Mypset newpset.xml  
```  
  
 **-síla**  
  
 Následující příkaz způsobí, že kořenová kódová skupina zásad y uživatele (označená 1) bude přidružena k sadě pojmenovaných oprávnění **Nothing.** To zabrání nástroji Caspol.exe ve spuštění.  
  
```console  
caspol -force -user -chggroup 1 Nothing  
```  
  
 **-obnovit**  
  
 Následující příkaz obnoví poslední uloženou zásadu počítače.  
  
```console  
caspol -machine -recover  
```  
  
 **-remgroup**  
  
 Následující příkaz odstraní skupinu kódu označenou 1.1. Pokud má tato skupina kódu podřízené skupiny kódu, jsou tyto skupiny rovněž smazány.  
  
```console  
caspol -remgroup 1.1.  
```  
  
 **-rempset**  
  
 Následující příkaz odebere sadu oprávnění **spuštění** ze zásad uživatele.  
  
```console  
caspol -user -rempset Execution  
```  
  
 Následující příkaz odebere `Mypset` z úrovně zásad uživatele.  
  
```console  
caspol -rempset MyPset  
```  
  
 **-resolvegroup**  
  
 Následující příkaz zobrazuje všechny kódové skupiny zásad počítače, které `myassembly` patří.  
  
```console  
caspol -machine -resolvegroup myassembly  
```  
  
 Následující příkaz zobrazuje všechny skupiny kódu počítače, rozlehlé sítě `myassembly` a zadané vlastní uživatelské zásady, které patří.  
  
```console  
caspol -customall "c:\config_test\security.config" -resolvegroup myassembly  
```  
  
 **-resolveperm**  
  
 Následující příkaz vypočítá oprávnění `testassembly` pro na základě úrovně zásad počítače a uživatele.  
  
```console  
caspol -all -resolveperm testassembly  
```  
  
## <a name="see-also"></a>Viz také

- [nástroje](index.md)
- [Příkazová zobrazení](developer-command-prompt-for-vs.md)
