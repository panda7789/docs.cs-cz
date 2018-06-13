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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f2306d51d88ab2d3b74ed6381a6de0acebf1e62c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33410095"
---
# <a name="caspolexe-code-access-security-policy-tool"></a>Caspol.exe (nástroj zásad zabezpečení přístupu kódu)
Nástroj Code Access Security (CAS) Policy (Caspol.exe) umožňuje uživatelům a správcům měnit zásady zabezpečení pro úroveň zásad počítače, úroveň zásad uživatele a úroveň zásad podniku.  
  
> [!IMPORTANT]
>  Počínaje [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Caspol.exe neovlivní zásady certifikační Autority, pokud [ \<legacyCasPolicy > element](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) je nastaven na `true`. Libovolná nastavení zobrazená nebo upravená pomocí nástroje CasPol.exe ovlivňují pouze aplikace, které se přihlašují pomocí zásad CAS. Další informace najdete v tématu [změny zabezpečení](../../../docs/framework/security/security-changes.md).  
  
> [!NOTE]
>  64bitové počítače obsahují 64bitové i 32bitové verze zásad zabezpečení. Aby bylo zajištěno, že změny v zásadách se aplikují na 32bitové i 64bitové aplikace, je třeba spustit 32bitovou i 64bitovou verzi nástroje Caspol.exe.  
  
 Nástroj zásad CAS je automaticky nainstalován společně s rozhraním .NET Framework a se sadou Visual Studio. Caspol.exe můžete najít v %windir%\Microsoft.NET\Framework\\*verze* na 32bitové systémy nebo %windir%\Microsoft.NET\Framework64\\*verze* na 64bitových systémech. (V případě rozhraní .NET Framework 4 v 64bitových systémech je to například %windir%\Microsoft.NET\Framework64\v4.030319\caspol.exe.) Pokud počítač obsahuje více verzí rozhraní .NET Framework, může zde být nainstalováno více verzí tohoto nástroje. Nástroj lze spustit z instalačního adresáře. Doporučujeme však používat [příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md), který nevyžaduje přejděte do složky pro instalaci.  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```  
caspol [options]  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Možnost|Popis|  
|------------|-----------------|  
|**-addfulltrust** *assembly_file*<br /><br /> or<br /><br /> **-af** *assembly_file*|Přidá sestavení implementující vlastní bezpečnostní objekt (jako je vlastní povolení nebo vlastní stav členství) na seznam sestavení úplné důvěryhodnosti pro konkrétní úroveň zásad. *Assembly_file* argument určuje sestavení, které chcete přidat. Tento soubor musí být podepsané [silným názvem](../../../docs/framework/app-domains/strong-named-assemblies.md). Sestavení se silným názvem pomocí se můžete přihlásit [Strong Name Tool (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md).<br /><br /> Pokaždé, když je sada oprávnění obsahující vlastní oprávnění přidána k zásadě, musí být sestavení implementující vlastní oprávnění přidáno na seznam úplné důvěryhodnosti pro danou úroveň zásad. Sestavení, která implementují vlastní bezpečnostní objekty (jako jsou vlastní skupiny kódů nebo podmínky členství) používaná v bezpečnostních zásadách (jako je například zásada počítače), by měla být vždy přidána na seznam sestavení úplné důvěryhodnosti. **Upozornění:** Pokud sestavení implementace vlastního objektu zabezpečení odkazuje na ostatních sestavení, je nejprve nutno přidat odkazovaná sestavení do seznamu sestavení úplný vztah důvěryhodnosti. Vlastní objekty zabezpečení vytvořené pomocí jazyka Visual Basic, C++ nebo JScript se odkazují na knihovny Microsoft.VisualBasic.dll, Microsoft.VisualC.dll nebo Microsoft.JScript.dll. Tato sestavení nejsou v seznamu sestavení úplné důvěryhodnosti ve výchozím nastavení obsažena. Před přidáním vlastního objektu zabezpečení musíte příslušné sestavení přidat do seznamu úplné důvěryhodnosti. Pokud tak neučiníte, přerušíte tím systém zabezpečení, což povede k selhání načtení všech sestavení. V takovém případě Caspol.exe **-všechny - resetovat** možnost nemůže opravit zabezpečení. Chcete-li opravit zabezpečení, musíte ručně odebrat vlastní objekt zabezpečení ze souborů zabezpečení.|  
|**-addgroup** {*parent_label &#124; parent_name*} *mship pset_name* [*příznaky*]<br /><br /> or<br /><br /> **-ag** {*parent_label &#124; parent_name*} *mship pset_name* [*příznaky*]|Přidá do hierarchie skupin kódu novou skupinu kódu. Můžete zadat buď *parent_label* nebo *parent_name*. *Parent_label* argument určuje popisek (například 1. nebo 1.1.) skupiny kódu, která je nadřazené skupině kód, který je přidáván. *Parent_name* argument určuje název skupiny kódu, který je nadřazené skupině kód, který je přidáván. Protože *parent_label* a *parent_name* může být místo používán Caspol.exe musí být schopen rozlišit mezi nimi. Proto *parent_name* nemůže začínat číslem. Kromě toho *parent_name* může obsahovat pouze A-Z, 0-9 nebo podtržítko.<br /><br /> *Mship* argument určuje podmínku členství pro nové skupiny kódu. Další informace najdete v tématu tabulky *mship* argumenty dál v této části.<br /><br /> *Pset_name* argument je název sady oprávnění, která bude přidružena do nové skupiny kódu. Můžete také nastavit jeden nebo více *příznaky* do nové skupiny. Další informace najdete v tématu tabulky *příznaky* argumenty dál v této části.|  
|**-addpset** {*psfile* &#124; *psfile* p*set_name*}<br /><br /> or<br /><br /> **-ap** {*named*_*psfile* &#124; *psfile* *pset_name*}|Přidá do zásad pojmenovanou sadu oprávnění. Sada oprávnění musí být napsána v jazyce XML a uložena do souboru .xml. Pokud soubor XML obsahuje název oprávnění nastavit, pouze tento soubor (*psfile*) je zadán. Pokud soubor XML neobsahuje název sady oprávnění, musíte zadat oba název souboru XML (*psfile*) a název sady oprávnění (*pset_name*).<br /><br /> Všechna oprávnění použitá v sadě oprávnění musí být definována v sestaveních obsažených v globální mezipaměti sestavení (GAC).|  
|**-a**[**ll**]|Značí, že jsou všechny možnosti následující za touto možností aplikovány na zásady počítače, uživatele a podniku. **– Všechny** možnost vždycky určí na základě zásad aktuálně přihlášeného uživatele. Najdete v článku **- customall** možnost k odkazování na zásady uživatele uživatele, než je aktuální uživatel.|  
|**-chggroup** {*popisek &#124;název*} {*mship* &#124; *pset_name*&#124;<br /><br /> *Příznaky* `}`<br /><br /> or<br /><br /> **-cg** {*popisek &#124;název*} {*mship* &#124; *pset_name*&#124;<br /><br /> *Příznaky* `}`|Změní podmínka členství skupiny kódu, sadě oprávnění nebo nastavení **výhradní**, **levelfinal**, **název**, nebo **popis**příznaky. Můžete zadat buď *popisek* nebo *název*. *Popisek* argument určuje popisek (například 1. nebo 1.1.) skupiny kódu. *Název* argument určuje název skupiny kódu můžete změnit. Protože *popisek* a *název* může být místo používán Caspol.exe musí být schopen rozlišit mezi nimi. Proto *název* nemůže začínat číslem. Kromě toho *název* může obsahovat pouze A-Z, 0-9 nebo podtržítko.<br /><br /> *Pset_name* argument určuje název sady přidružení ke skupině kódu oprávnění. Podívejte se na tabulky dál v této části informace na *mship* a *příznaky* argumenty.|  
|**-chgpset***psfile pset_name*<br /><br /> or<br /><br /> **-cp** *psfile pset_name*|Mění pojmenovanou sadu oprávnění. *Psfile* argument poskytuje novou definici pro sadu oprávnění, je soubor serializovaných oprávnění sady ve formátu XML. *Pset_name* argument určuje název sady oprávnění, kterou chcete změnit.|  
|**-customall***cesta*<br /><br /> or<br /><br /> **-ca***cesta*|Značí, že jsou všechny možnosti následující za touto možností aplikovány na zásady počítače, podniku a určeného vlastního uživatele. Je nutné zadat umístění souboru konfigurace zabezpečení vlastní uživatele s *cesta* argument.|  
|**-cu**[**stomuser**] *path*|Umožňuje spravovat zásadu vlastního uživatele, která nepatří uživateli, jenž aktuálně spouští nástroj Caspol.exe. Je nutné zadat umístění souboru konfigurace zabezpečení vlastní uživatele s *cesta* argument.|  
|**-enterprise**<br /><br /> or<br /><br /> **-en**|Značí, že jsou všechny možnosti následující za touto možností aplikovány na zásady na úrovni podniku. Uživatelé, kteří nejsou podnikovými administrátory, nemají dostatečná práva pro modifikaci podnikové zásady, přestože si ji mohou zobrazit. V nepodnikových scénářích nebude tato zásada ve výchozím nastavení ovlivňovat zásadu počítače ani uživatele.|  
|**-e**[**xecution**] {**na** &#124; **vypnout**}|Vypíná nebo zapíná mechanismus, jenž ověřuje, která oprávnění se mají před spuštěním kódu provést. **Poznámka:** tento přepínač odstraněno [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] a novějších verzích. Další informace najdete v tématu [změny zabezpečení](../../../docs/framework/security/security-changes.md).|  
|**-f**[**orce**]|Zakáže, aby nástroj provedl autodestruktivní test a změní zásadu dle zadání uživatele. Nástroj Caspol.exe běžně ověřuje, zda může jakákoli změna zásady zabránit nástroji Caspol.exe ve správném spuštění. Pokud tomu tak je, nástroj Caspol.exe změnu zásady neuloží a zobrazí chybovou zprávu. Chcete-li vynutit Caspol.exe změna zásad, i když to brání spuštění Caspol.exe sám sebe, použijte **– vynutit** možnost.|  
|**-h**[**nápovědu**]|Zobrazí syntaxi a možnosti příkazu pro nástroj Caspol.exe.|  
|**-l**[**ist**]|Vypíše hierarchii skupiny kódu a sad oprávnění konkrétního počítače, uživatele, podniku nebo všech úrovní zásad. Nástroj Caspol.exe zobrazuje nejprve popisek skupiny kódu a poté název, pokud není null.|  
|**-listdescription Zobrazí**<br /><br /> or<br /><br /> **-ld**|Vypíše všechny popisy skupiny kódu pro zadanou úroveň zásad.|  
|**-listfulltrust Zobrazí**<br /><br /> or<br /><br /> **-lf**|Vypíše obsah sestavení úplného vztahu důvěryhodnosti pro zadanou úroveň zásad.|  
|**-Vypisovat skupiny**<br /><br /> or<br /><br /> **kontaktní-skupina**|Zobrazuje skupiny kódu konkrétní úrovně nebo všech úrovní zásad. Nástroj Caspol.exe zobrazuje nejprve popisek skupiny kódu a poté název, pokud není null.|  
|**-listpset Zobrazí** nebo **-lineárního programování úloh**|Zobrazí sady oprávnění konkrétní úrovně nebo všech úrovní zásad.|  
|**-m**[**achine**]|Značí, že jsou všechny možnosti následující za touto možností aplikovány na zásady na úrovni počítače. Uživatelé, kteří nejsou administrátory, nemají dostatečná práva pro modifikaci zásady počítače, přestože si ji mohou zobrazit. Pro správce **-počítače** je výchozí.|  
|**-polchgprompt** {**na** &#124; **vypnout**}<br /><br /> or<br /><br /> **-pp** {**na** &#124; **vypnout**}|Povoluje nebo zakazuje dotaz, který se zobrazí vždy, když je nástroj Caspol.exe spuštěn pomocí možnosti, která může způsobit změnu zásad.|  
|**-quiet**<br /><br /> or<br /><br /> **-q**|Dočasně zakazuje dotaz, který se normálně zobrazí pro možnost způsobující změny zásad. Globální nastavení dotazu na změnu se nezmění. Tuto možnost použijte pouze u samostatných příkazů, aby bylo zabráněno zakázání výzev pro všechny příkazy nástroje Caspol.exe.|  
|**-r**[**ecover**]|Obnoví zásady ze záložního souboru. Kdykoli je provedena změna zásady, uloží nástroj Caspol.exe starou zásadu do záložního souboru.|  
|**-remfulltrust** *assembly_file*<br /><br /> or<br /><br /> **-rf***assembly_file*|Odstraní sestavení ze seznamu úplné důvěryhodnosti na úrovni zásad. Tato operace by měla být provedena, pokud sada oprávnění obsahující vlastní oprávnění již není zásadou používána. Sestavení implementující vlastní oprávnění byste však měli odstranit ze seznamu úplné důvěryhodnosti pouze tehdy, pokud sestavení neimplementuje žádná další vlastní oprávnění, která jsou stále používána. Po odstranění sestavení ze seznamu by měla být rovněž odstraněna další sestavení, která jsou na něm závislá.|  
|**-remgroup** {*popisek &#124;název*}<br /><br /> or<br /><br /> **-rg** {l*opisek &#124; název*}|Odstraňuje skupinu kódu zadanou popiskem nebo názvem. Pokud má zadaná skupina kódu podřízenou skupinu kódu, nástroj Caspol.exe odstraní rovněž všechny podřízené skupiny kódu.|  
|**-rempset** *pset_name*<br /><br /> or<br /><br /> **-rp** *pset_name*|Odstraní ze zásady zadanou sadu oprávnění. *Pset_name* argument určuje oprávnění, která nastaveny na odebrání. Nástroj Caspol.exe odstraňuje sadu oprávnění pouze tehdy, pokud není asociována se skupinou kódu. Výchozí (vestavěné) sady oprávnění nemohou být odstraněny.|  
|**-reset**<br /><br /> or<br /><br /> **-rs**|Vrátí zásadu do původního stavu a uloží ji na disk. To se hodí vždy při podezření, že je změněná zásada neopravitelně poškozena a když je zapotřebí začít znovu s výchozími nastaveními instalace. Resetování se může rovněž hodit, když má být jako výchozí bod pro modifikaci konkrétních konfiguračních souborů zabezpečení použita výchozí zásada. Další informace najdete v tématu [ruční úprava konfiguračních souborů zabezpečení](#cpgrfcodeaccesssecuritypolicyutilitycaspolexeanchor1).|  
|**-resetlockdown**<br /><br /> or<br /><br /> **-rsld**|Vrátí více omezující verzi výchozí stav zásad a zachová jej na disk; Vytvoří zálohy předchozí zásad počítače a zachová jej do souboru s názvem `security.config.bac`.  Zásady uzamčení dolů je podobná výchozí zásady, s tím rozdílem, že zásady uděluje oprávnění k kód z `Local Intranet`, `Trusted Sites`, a `Internet` zóny a odpovídající skupiny kódu mít žádné podřízené skupiny kódu.|  
|**-resolvegroup** *assembly_file*<br /><br /> or<br /><br /> **-rsg***assembly_file*|Skupiny kódu ukazuje, že konkrétní sestavení (*assembly_file*) patří do. Ve výchozím nastavení tato možnost zobrazuje úrovně zásad počítače, uživatele a podniku, ke kterým sestavení patří. Pokud chcete zobrazit pouze jedna úroveň zásad, použijte tuto možnost se buď **-počítače**, **-uživatele**, nebo **-enterprise** možnost.|  
|**-resolveperm** *assembly_file*<br /><br /> or<br /><br /> **– konfigurace** *assembly_file*|Zobrazuje všechna oprávnění, která zadaná (nebo výchozí) úroveň zásady zabezpečení může poskytnout sestavení, pokud je sestavením povoleno spuštění. *Assembly_file* argument určuje sestavení. Pokud zadáte **– všechny** možnost Caspol.exe vypočítá oprávnění pro sestavení na základě zásad uživatele, počítače a enterprise; jinak, platí výchozí chování pravidla.|  
|**-s**[**ecurity**] {**na** &#124; **vypnout**}|Vypne nebo zapne zabezpečení přístupu kódu. Určení **-s vypnout** možnost nezakazovat na základě rolí zabezpečení. **Poznámka:** tento přepínač odstraněno [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] a novějších verzích. Další informace najdete v tématu [změny zabezpečení](../../../docs/framework/security/security-changes.md). **Upozornění:** při zabezpečení přístupu kódu je zakázaná, všechny požadavky přístup kódu úspěšné. Zakázání zabezpečení přístupu kódu způsobí, že bude systém zranitelný vůči útokům škodlivým kódem, jako jsou například viry nebo červi. Vypnutí zabezpečení přinese zlepšení výkonu, ale mělo by být použito pouze tehdy, pokud byla přijata další bezpečnostní opatření, která pomohou zajistit, aby celková bezpečnost systému nebyla narušena. Mezi příklady dalších bezpečnostních opatření patří: odpojení od veřejné sítě, fyzické zabezpečení počítačů atd.|  
|**-u**[**pož**]|Značí, že jsou všechny možnosti následující po této možnosti aplikovány na zásadu na uživatelské úrovni pro uživatele, který nástroj Caspol.exe spustil. Pro běžní uživatelé **-uživatele** je výchozí.|  
|**-?**|Zobrazí syntaxi a možnosti příkazu pro nástroj Caspol.exe.|  
  
 *Mship* argument, který určuje členství podmínku pro skupinu kódu, lze použít s **- addgroup** a **- chggroup** možnosti. Každý *mship* argument je implementovaný jako třídu rozhraní .NET Framework. Chcete-li určit *mship,* použijte jednu z následujících akcí.  
  
|Argument|Popis|  
|--------------|-----------------|  
|**-allcode**|Specifikuje veškerý kód. Další informace o tuto podmínku členství, najdete v článku <xref:System.Security.Policy.AllMembershipCondition>.|  
|**-appdir**|Určuje adresář aplikace. Pokud zadáte **– appdir** jako podmínka, členství, adresa URL důkaz kódu se porovná se aplikace directory důkazy o tento kód. Pokud jsou obě hodnoty evidence stejné, byly podmínky členství splněny. Další informace o tuto podmínku členství, najdete v článku <xref:System.Security.Policy.ApplicationDirectoryMembershipCondition>.|  
|**-vlastní***xmlfile*|Přidá vlastní podmínku členství. Povinné *xmlfile* argument určuje soubor .xml, který obsahuje XML serializace podmínky vlastní členství.|  
|**-hash** *Algoritmus_hash* {**-šestnáctkových** *hashValue* &#124; **-soubor** *assembly_file* }|Určuje kód, který obsahuje zadanou hodnotu hash sestavení. Pro použití hodnoty hash jako podmínky členství ve skupině kódu je nutné zadat hodnotu hash nebo soubor sestavení. Další informace o tuto podmínku členství, najdete v článku <xref:System.Security.Policy.HashMembershipCondition>.|  
|**-pub** { **-cert** *cert_file_name*&#124;<br /><br /> **-soubor** *signed_file_name* &#124; **-šestnáctkových***hex_string* }  |Určuje kód, který obsahuje zadaného vydavatele softwaru, jak je označeno souborem certifikátu, podpisem na souboru nebo šestnáctkovou reprezentací certifikátu X509. Další informace o tuto podmínku členství, najdete v článku <xref:System.Security.Policy.PublisherMembershipCondition>.|  
|**-lokality** *webu*|Určuje kód, který obsahuje zadanou webovou stránku původu. Příklad:<br /><br /> **-lokality** www.proseware.com<br /><br /> Další informace o tuto podmínku členství, najdete v článku <xref:System.Security.Policy.SiteMembershipCondition>.|  
|**-silné - souboru** *název_souboru* {*název* &#124; **- noname**} {*verze* &#124; **- noversion**}|Určuje kód, který má konkrétní silným názvem, jako je určený podle názvu souboru, název sestavení jako řetězec a verze sestavení ve formátu *hlavní*. *méně závažné*. *sestavení*. *Revize*. Příklad:<br /><br /> **-silné - souboru** myAssembly.exe myAssembly 1.2.3.4<br /><br /> Další informace o tuto podmínku členství, najdete v článku <xref:System.Security.Policy.StrongNameMembershipCondition>.|  
|**-Adresa url** *adresy URL*|Určuje kód pocházející ze zadané adresy URL. Adresa URL musí obsahovat protokol, jako je například http:// nebo ftp://. Kromě toho zástupný znak (\*) lze zadat více sestavení z konkrétní adresu URL. **Poznámka:** protože adresu URL lze identifikovat pomocí více názvů, pomocí adresy URL jako podmínku členství není bezpečné způsob, jak zjistit identitu kódu. Kdykoli je to možné, použijte podmínku členství silného názvu, podmínku vydavatele nebo podmínku hodnoty hash. <br /><br /> Další informace o tuto podmínku členství, najdete v článku <xref:System.Security.Policy.UrlMembershipCondition>.|  
|**-zóny** *Název_zóny*|Určuje kód pomocí zadané zóny původu. *Název_zóny* argument může mít jednu z následujících hodnot: **tento počítač**, **intranetu**, **důvěryhodné**, **Internetu** , nebo **nedůvěryhodné**. Další informace o tuto podmínku členství, najdete v článku <xref:System.Security.Policy.ZoneMembershipCondition> třídy.|  
  
 *Příznaky* argument, který lze použít s **– addgroup** a **– chggroup** možnosti, je zadán pomocí jedné z následujících akcí.  
  
|Argument|Popis|  
|--------------|-----------------|  
|**– Popis "** *popis* **"**|Pokud se používá s **– addgroup** možnost, určuje popis pro skupinu kódu na Přidat. Pokud se používá s **– chggroup** možnost, určuje popis pro skupinu kódu na Upravit. *Popis* argument musí být uzavřena do uvozovek.|  
|**-výhradní** {**na**&#124;**vypnout**}|Pokud nastavíte hodnotu **na**, označuje, že pouze sadu oprávnění přidružených ke skupině kódu, které přidáváte nebo úprava považuje za když nějaký kód vyhovuje podmínky členství ve skupině kódu. Pokud je tato možnost nastavená na **vypnout**, Caspol.exe považovat všechny odpovídající kód skupiny na úrovni zásady sady oprávnění.|  
|**-levelfinal** {**na**&#124;**vypnout**}|Pokud nastavíte hodnotu **na**, označuje, že se považuje za žádné zásady úroveň pod úrovní dojde k kódu přidaném nebo upravené skupiny. Tato možnost je obvykle používaná na úrovni zásad počítače. Pokud je tento příznak například nastaven pro skupinu kódu na úrovni počítače a některý kód odpovídá podmínce členství této skupiny kódu, nástroj Caspol.exe nevypočítá a neaplikuje pro tento kód zásadu na uživatelské úrovni.|  
|**-name "** *název* **"**|Pokud se používá s **– addgroup** možnost, určuje skriptování název pro skupinu kódu na Přidat. Pokud se používá s **- chggroup** možnost, určuje skriptování název pro skupinu kódu na Upravit. *Název* argument musí být uzavřena do uvozovek. *Název* argument nesmí začínat číslem a může obsahovat pouze A-Z, 0-9 nebo podtržítko. Skupiny kódu lze odkazovat to *název* místo podle jejich číselného popisek. *Název* je také velmi užitečné při vytváření skriptů.|  
  
## <a name="remarks"></a>Poznámky  
 Zásada zabezpečení je vyjádřena pomocí tří úrovní zásad: počítačová, uživatelská a podniková. Sada oprávnění, kterou sestavení přijímá, je určena průnikem sad oprávnění povolených těmito třemi úrovněmi zásad. Každá úroveň zásad je reprezentována hierarchickou strukturou skupin kódu. Každá skupina kódu má podmínku členství, která určuje, který kód je členem této skupiny. Sada pojmenovaných oprávnění je rovněž asociována s každou skupinou kódu. Tato sada oprávnění určuje oprávnění, která modul runtime povoluje kódu splňujícímu podmínku členství. Hierarchie skupin kódu, společně se souvisejícími pojmenovanými sadami oprávnění, definuje a spravuje každou úroveň zásad zabezpečení. Můžete použít **– uživatel**, **- customuser**, **– počítač** a **-enterprise** možnosti můžete nastavit úroveň zásady zabezpečení.  
  
 Další informace o zásadách zabezpečení a jak modul runtime určuje, jaká oprávnění udělit kódu najdete v tématu [Správa zásad zabezpečení](http://msdn.microsoft.com/library/d754e05d-29dc-4d3a-a2c2-95eaaf1b82b9).  
  
## <a name="referencing-code-groups-and-permission-sets"></a>Odkazování na skupiny kódu a sady oprávnění  
 Pro usnadnění odkazy na skupiny kódu v hierarchii, **-seznamu** možnost zobrazí zobrazují odsazené seznam skupiny kódu spolu s jejich číselné popisky (1, 1.1, 1.1.1 a tak dále). Další operace příkazového řádku zaměřené na skupiny kódu využívají k odkazování na specifické skupiny kódu také číselné popisky.  
  
 Pojmenované sady jsou odkazovány podle svých názvů. **– Seznam** možnost zobrazí seznam skupin kódu následuje seznam pojmenovaných oprávnění nastaví dostupné v této zásadě.  
  
## <a name="caspolexe-behavior"></a>Chování nástroje Caspol.exe  
 Všechny možnosti s výjimkou **-s**[**ecurity**] {**na** &#124; **vypnout**} použijte verzi rozhraní .NET Framework, že byl nainstalován Caspol.exe s. Pokud spustíte Caspol.exe nainstalovanou verzí *X* modulu runtime změny platí pouze pro tuto verzi. Jiné souběžné instalace modulu runtime, pokud nějaké existují, nejsou ovlivněny. Pokud je nástroj Caspol.exe spuštěn z příkazového řádku, aniž by se nacházel v adresáři konkrétní verze modulu runtime, bude spuštěn z prvního adresáře verze modulu runtime v cestě (obvykle to bývá poslední nainstalovaná verze).  
  
 **-S**[**ecurity**] {**na** &#124; **vypnout**} možnost je platná pro celý počítač operace. Vypnutí zabezpečení přístupu kódu ukončí kontroly zabezpečení veškerého spravovaného kódu pro všechny uživatele na počítači. Pokud jsou na počítači současně nainstalovány různé verze rozhraní .NET Framework, vypne tento příkaz zabezpečení pro všechny verze nainstalované na počítači. I když **-seznamu** možnost ukazuje, že je vypnuto zabezpečení, nic jiného jasně označuj pro ostatní uživatele, které zabezpečení byla vypnuta.  
  
 Když uživatel bez práv správce spustí Caspol.exe, všechny možnosti odkazovat na úrovni zásad uživatele, pokud **– počítač** je zadána možnost. Když správce spustí Caspol.exe, všechny možnosti naleznete zásady počítače, pokud **– uživatel** je zadána možnost.  
  
 Caspol.exe musí mít udělen ekvivalent **všechno, co** sadě oprávnění funkce. Nástroj má ochranný mechanismus, který zabraňuje zásadě, aby byla modifikována způsobem, který by nástroji Caspol.exe znemožnil získat oprávnění nutná pro jeho spuštění. Pokud se o takovou změnu pokusíte, nástroj Caspol.exe oznámí, že požadovaná změna zásady nástroj poškodí a změna zásady bude zamítnuta. Můžete vypnout tento ochranný mechanismus pro daný příkaz s použitím **– vynutit** možnost.  
  
<a name="cpgrfcodeaccesssecuritypolicyutilitycaspolexeanchor1"></a>   
## <a name="manually-editing-the-security-configuration-files"></a>Ruční úprava konfiguračních souborů zabezpečení  
 Tři konfigurační soubory zabezpečení odpovídají třem úrovním zásad podporovaných nástrojem Caspol.exe: jeden je pro zásadu počítače, jeden pro zásadu daného uživatele a jeden pro zásadu podniku. Tyto soubory jsou vytvořeny na disku, když je zásada počítače, uživatele nebo podniku změněna pomocí nástroje Caspol.exe. Můžete použít **– resetovat** možnost v Caspol.exe uložení výchozí zásady zabezpečení na disk, v případě potřeby.  
  
 Ve většině případů není manuální úprava těchto konfiguračních souborů zabezpečení doporučena. Mohou se však vyskytnout scénáře, ve kterých je úprava těchto souborů nezbytná. Například, když chce správce upravit konfiguraci zabezpečení pro konkrétního uživatele.  
  
## <a name="examples"></a>Příklady  
 **-addfulltrust**  
  
 Předpokládejme, že byla do zásady počítače přidána sada oprávnění obsahující vlastní oprávnění. Tato vlastní oprávnění je implementována ve `MyPerm.exe`, a `MyPerm.exe` odkazuje na třídy v `MyOther.exe`. Obě sestavení musí být přidána do seznamu sestavení úplné důvěryhodnosti. Následující příkaz přidá `MyPerm.exe` sestavení do seznamu úplný vztah důvěryhodnosti pro zásady počítače.  
  
```  
caspol -machine -addfulltrust MyPerm.exe  
```  
  
 Následující příkaz přidá `MyOther.exe` sestavení do seznamu úplný vztah důvěryhodnosti pro zásady počítače.  
  
```  
caspol -machine -addfulltrust MyOther.exe  
```  
  
 **-addgroup**  
  
 Následující příkaz přidá do kořene hierarchie skupin kódu zásady počítače podřízenou skupinu kódu. Do nové skupiny kódu je členem skupiny **Internet** zón a je přidružen **provádění** sadu oprávnění.  
  
```  
caspol -machine -addgroup 1.  -zone Internet Execution  
```  
  
 Následující příkaz přidá podřízené skupiny kódu, která nabízí sdílené složky \\\netserver\netshare místní intranet oprávnění.  
  
```  
caspol -machine -addgroup 1. -url \\netserver\netshare\* LocalIntranet  
```  
  
 **-addpset**  
  
 Následující příkaz přidá `Mypset` nastavení oprávnění pro zásad uživatele.  
  
```  
caspol -user -addpset Mypset.xml Mypset  
```  
  
 **-chggroup**  
  
 Následující příkaz změny oprávnění nastavené do zásad uživatele skupiny kódu označené 1.2. na **provádění** sadu oprávnění.  
  
```  
caspol -user -chggroup 1.2. Execution  
```  
  
 Následující změny příkaz podmínky členství ve skupině kódu ve výchozích zásadách 1.2.1 s popiskem. změny nastavení a **výhradní** příznak. Podmínka členství je definován jako kód, který pochází z **Internet** zóny a **výhradní** příznak je zapnutá.  
  
```  
caspol -chggroup 1.2.1. -zone Internet -exclusive on  
```  
  
 **-chgpset**  
  
 Tento příkaz změní sadu s názvem oprávnění `Mypset` sadou obsažené v oprávnění `newpset.xml`. Aktuální verze nepodporuje změnu sady oprávnění, která je používána hierarchií skupiny kódu.  
  
```  
caspol -chgpset Mypset newpset.xml  
```  
  
 **-force**  
  
 Následující příkaz způsobí, že zásady uživatele root kód skupiny (s popiskem 1) má být spojen s **nic** pojmenovanou sadu oprávnění. To zabrání nástroji Caspol.exe ve spuštění.  
  
```  
caspol -force -user -chggroup 1 Nothing  
```  
  
 **-obnovení**  
  
 Následující příkaz obnoví poslední uloženou zásadu počítače.  
  
```  
caspol -machine -recover  
```  
  
 **-remgroup**  
  
 Následující příkaz odstraní skupinu kódu označenou 1.1. Pokud má tato skupina kódu podřízené skupiny kódu, jsou tyto skupiny rovněž smazány.  
  
```  
caspol -remgroup 1.1.  
```  
  
 **-rempset**  
  
 Následující příkaz odebere **provádění** oprávnění nastavené ze zásad uživatele.  
  
```  
caspol -user -rempset Execution  
```  
  
 Následující příkaz odebere `Mypset` na úrovni zásad uživatele.  
  
```  
caspol -rempset MyPset  
```  
  
 **-resolvegroup**  
  
 Následující příkaz ukazuje všechny skupiny kódu zásady počítače, který `myassembly` patří.  
  
```  
caspol -machine -resolvegroup myassembly  
```  
  
 Následující příkaz ukazuje všechny skupiny kódu počítače, enterprise a zásady zadaný vlastní uživatele, že `myassembly` patří.  
  
```  
caspol -customall "c:\config_test\security.config" -resolvegroup myassembly  
```  
  
 **-resolveperm**  
  
 Následující příkaz vypočítá oprávnění pro `testassembly` podle úrovně zásad počítače a uživatele.  
  
```  
caspol -all -resolveperm testassembly  
```  
  
## <a name="see-also"></a>Viz také  
 [Nástroje](../../../docs/framework/tools/index.md)  
 [Příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
