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
ms.openlocfilehash: 3e6057d1ce6b5d0e961449ef298b1a50c7a407ef
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59200529"
---
# <a name="caspolexe-code-access-security-policy-tool"></a>Caspol.exe (nástroj zásad zabezpečení přístupu kódu)
Nástroj Code Access Security (CAS) Policy (Caspol.exe) umožňuje uživatelům a správcům měnit zásady zabezpečení pro úroveň zásad počítače, úroveň zásad uživatele a úroveň zásad podniku.  
  
> [!IMPORTANT]
>  Počínaje [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], Caspol.exe neovlivní zásady CAS, pokud [ \<legacyCasPolicy > element](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) je nastavena na `true`. Libovolná nastavení zobrazená nebo upravená pomocí nástroje CasPol.exe ovlivňují pouze aplikace, které se přihlašují pomocí zásad CAS. Další informace najdete v tématu [změny zabezpečení](../../../docs/framework/security/security-changes.md).  
  
> [!NOTE]
>  64bitové počítače obsahují 64bitové i 32bitové verze zásad zabezpečení. Aby bylo zajištěno, že změny v zásadách se aplikují na 32bitové i 64bitové aplikace, je třeba spustit 32bitovou i 64bitovou verzi nástroje Caspol.exe.  
  
 Nástroj zásad CAS je automaticky nainstalován společně s rozhraním .NET Framework a se sadou Visual Studio. Caspol.exe můžete najít v %windir%\Microsoft.NET\Framework\\*verze* na 32bitových systémech nebo %windir%\Microsoft.NET\Framework64\\*verze* v 64bitových systémech. (V případě rozhraní .NET Framework 4 v 64bitových systémech je to například %windir%\Microsoft.NET\Framework64\v4.030319\caspol.exe.) Pokud počítač obsahuje více verzí rozhraní .NET Framework, může zde být nainstalováno více verzí tohoto nástroje. Nástroj lze spustit z instalačního adresáře. Doporučujeme však, že používáte [příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md), který nevyžaduje Přesun do instalační složky.  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```  
caspol [options]  
```  
  
## <a name="parameters"></a>Parametry  
  
|Možnost|Popis|  
|------------|-----------------|  
|**-addfulltrust** *assembly_file*<br /><br /> or<br /><br /> **-af** *assembly_file*|Přidá sestavení implementující vlastní bezpečnostní objekt (jako je vlastní povolení nebo vlastní stav členství) na seznam sestavení úplné důvěryhodnosti pro konkrétní úroveň zásad. *Assembly_file* argument určuje sestavení, které chcete přidat. Tento soubor musí být podepsán [silným názvem](../../../docs/framework/app-domains/strong-named-assemblies.md). Sestavení se silným názvem pomocí se můžete přihlásit [nástroj Strong Name (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md).<br /><br /> Pokaždé, když je sada oprávnění obsahující vlastní oprávnění přidána k zásadě, musí být sestavení implementující vlastní oprávnění přidáno na seznam úplné důvěryhodnosti pro danou úroveň zásad. Sestavení, která implementují vlastní bezpečnostní objekty (jako jsou vlastní skupiny kódů nebo podmínky členství) používaná v bezpečnostních zásadách (jako je například zásada počítače), by měla být vždy přidána na seznam sestavení úplné důvěryhodnosti. **Upozornění:**  Pokud sestavení implementuje vlastní odkazy objektů zabezpečení jiných sestavení, je třeba nejprve přidat odkazovaná sestavení do seznamu plně důvěryhodných sestavení. Vlastní objekty zabezpečení vytvořené pomocí jazyka Visual Basic, C++ nebo JScript se odkazují na knihovny Microsoft.VisualBasic.dll, Microsoft.VisualC.dll nebo Microsoft.JScript.dll. Tato sestavení nejsou v seznamu sestavení úplné důvěryhodnosti ve výchozím nastavení obsažena. Před přidáním vlastního objektu zabezpečení musíte příslušné sestavení přidat do seznamu úplné důvěryhodnosti. Pokud tak neučiníte, přerušíte tím systém zabezpečení, což povede k selhání načtení všech sestavení. V takovém případě nástroj Caspol.exe **-all - reset** neopraví zabezpečení. Chcete-li opravit zabezpečení, musíte ručně odebrat vlastní objekt zabezpečení ze souborů zabezpečení.|  
|**-addgroup** {*parent_label &#124; parent_name*} *mship pset_name* [*příznaky*]<br /><br /> or<br /><br /> **-ag** {*parent_label &#124; parent_name*} *mship pset_name* [*příznaky*]|Přidá do hierarchie skupin kódu novou skupinu kódu. Můžete zadat buď *parent_label* nebo *parent_name*. *Parent_label* argument určuje popisek (jako je například 1. nebo 1.1.) skupiny kódu, která je nadřazena přidávané skupině kódu. *Parent_name* argument určuje název skupiny kódu, která je nadřazena přidávané skupině kódu. Protože *parent_label* a *parent_name* lze používat Zaměnitelně, Caspol.exe musí být schopen mezi nimi rozlišovat. Proto *parent_name* nemůže začínat číslicí. Kromě toho *parent_name* může obsahovat jenom A-Z, 0-9 a podtržítko.<br /><br /> *Mship* argument určuje podmínku členství pro novou skupinu kódu. Další informace najdete v tabulce *mship* argumenty dál v této části.<br /><br /> *Pset_name* argumentem je název sady oprávnění, která mají být asociována s novou skupinou kódu. Můžete také nastavit jeden nebo více *příznaky* nové skupiny. Další informace najdete v tabulce *příznaky* argumenty dál v této části.|  
|**-addpset** {*psfile* &#124; *psfile* p*set_name*}<br /><br /> or<br /><br /> **-ap** {*named*_*psfile* &#124; *psfile* *pset_name*}|Přidá do zásad pojmenovanou sadu oprávnění. Sada oprávnění musí být napsána v jazyce XML a uložena do souboru .xml. Pokud soubor XML obsahuje název sady oprávnění nastavit, pouze tento soubor (*psfile*) je zadán. Pokud soubor XML neobsahuje název sady oprávnění, musíte zadat název souboru XML (*psfile*) a název sady oprávnění (*pset_name*).<br /><br /> Všechna oprávnění použitá v sadě oprávnění musí být definována v sestaveních obsažených v globální mezipaměti sestavení (GAC).|  
|**-a**[**ll**]|Značí, že jsou všechny možnosti následující za touto možností aplikovány na zásady počítače, uživatele a podniku. **– Všechny** možnost vždy označuje zásadu aktuálně přihlášeného uživatele. Zobrazit **- customall** možnost pro uživatelskou zásadu jiného než aktuálního uživatele.|  
|**-chggroup** {*label &#124;name*} {*mship* &#124; *pset_name* &#124;<br /><br /> *příznaky* `}`<br /><br /> or<br /><br /> **-cg** {*label &#124;name*} {*mship* &#124; *pset_name* &#124;<br /><br /> *příznaky* `}`|Změní podmínku členství skupiny kódu, sadu oprávnění nebo nastavení **exkluzivní**, **levelfinal**, **název**, nebo **popis**příznaky. Můžete zadat buď *popisek* nebo *název*. *Popisek* argument určuje popisek (jako je například 1. nebo 1.1.) skupiny kódu. *Název* argument určuje název skupiny kódu, chcete-li změnit. Protože *popisek* a *název* lze používat Zaměnitelně, Caspol.exe musí být schopen mezi nimi rozlišovat. Proto *název* nemůže začínat číslicí. Kromě toho *název* může obsahovat jenom A-Z, 0-9 a podtržítko.<br /><br /> *Pset_name* argument určuje název sady oprávnění pro přidružení k skupiny kódu. Zobrazit v tabulkách dále v této části pro informace na *mship* a *příznaky* argumenty.|  
|**-chgpset**  *psfile pset_name*<br /><br /> or<br /><br /> **-prohlášení cp** *psfile pset_name*|Mění pojmenovanou sadu oprávnění. *Psfile* argument zadává novou definici sady oprávnění, je serializovaný soubor sady oprávnění ve formátu XML. *Pset_name* argument určuje název sady oprávnění chcete změnit.|  
|**-customall**  *cesta*<br /><br /> or<br /><br /> **– ca**  *cesta*|Značí, že jsou všechny možnosti následující za touto možností aplikovány na zásady počítače, podniku a určeného vlastního uživatele. Je nutné zadat umístění souboru konfigurace zabezpečení vlastního uživatele s *cesta* argument.|  
|**-cu**[**stomuser**] *path*|Umožňuje spravovat zásadu vlastního uživatele, která nepatří uživateli, jenž aktuálně spouští nástroj Caspol.exe. Je nutné zadat umístění souboru konfigurace zabezpečení vlastního uživatele s *cesta* argument.|  
|**-enterprise**<br /><br /> or<br /><br /> **-en**|Značí, že jsou všechny možnosti následující za touto možností aplikovány na zásady na úrovni podniku. Uživatelé, kteří nejsou podnikovými administrátory, nemají dostatečná práva pro modifikaci podnikové zásady, přestože si ji mohou zobrazit. V nepodnikových scénářích nebude tato zásada ve výchozím nastavení ovlivňovat zásadu počítače ani uživatele.|  
|**-e**[**zpracování**] {**na** &#124; **vypnout**}|Vypíná nebo zapíná mechanismus, jenž ověřuje, která oprávnění se mají před spuštěním kódu provést. **Poznámka:**  Tento přepínač byl ve [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] a novějších verzích. Další informace najdete v tématu [změny zabezpečení](../../../docs/framework/security/security-changes.md).|  
|**-f**[**orce**]|Zakáže, aby nástroj provedl autodestruktivní test a změní zásadu dle zadání uživatele. Nástroj Caspol.exe běžně ověřuje, zda může jakákoli změna zásady zabránit nástroji Caspol.exe ve správném spuštění. Pokud tomu tak je, nástroj Caspol.exe změnu zásady neuloží a zobrazí chybovou zprávu. Chcete-li vynutit Caspol.exe ke změně zásady, i když to zabrání nástroji Caspol.exe spouštění, použijte **– platnost** možnost.|  
|**-h**[**elp**]|Zobrazí syntaxi a možnosti příkazu pro nástroj Caspol.exe.|  
|**-l**[**ist**]|Vypíše hierarchii skupiny kódu a sad oprávnění konkrétního počítače, uživatele, podniku nebo všech úrovní zásad. Nástroj Caspol.exe zobrazuje nejprve popisek skupiny kódu a poté název, pokud není null.|  
|**-listdescription**<br /><br /> or<br /><br /> **-ld**|Vypíše všechny popisy skupiny kódu pro zadanou úroveň zásad.|  
|**-listfulltrust**<br /><br /> or<br /><br /> **-lf**|Vypíše obsah sestavení úplného vztahu důvěryhodnosti pro zadanou úroveň zásad.|  
|**-listgroups**<br /><br /> or<br /><br /> **-lg**|Zobrazuje skupiny kódu konkrétní úrovně nebo všech úrovní zásad. Nástroj Caspol.exe zobrazuje nejprve popisek skupiny kódu a poté název, pokud není null.|  
|**-listpset Zobrazí** nebo **-lp**|Zobrazí sady oprávnění konkrétní úrovně nebo všech úrovní zásad.|  
|**-m**[**achine**]|Značí, že jsou všechny možnosti následující za touto možností aplikovány na zásady na úrovni počítače. Uživatelé, kteří nejsou administrátory, nemají dostatečná práva pro modifikaci zásady počítače, přestože si ji mohou zobrazit. Pro správce **-machine** je výchozí nastavení.|  
|**-polchgprompt** {**on** &#124; **off**}<br /><br /> or<br /><br /> **-pp** {**on** &#124; **off**}|Povoluje nebo zakazuje dotaz, který se zobrazí vždy, když je nástroj Caspol.exe spuštěn pomocí možnosti, která může způsobit změnu zásad.|  
|**-quiet**<br /><br /> or<br /><br /> **-q**|Dočasně zakazuje dotaz, který se normálně zobrazí pro možnost způsobující změny zásad. Globální nastavení dotazu na změnu se nezmění. Tuto možnost použijte pouze u samostatných příkazů, aby bylo zabráněno zakázání výzev pro všechny příkazy nástroje Caspol.exe.|  
|**-r**[**ecover**]|Obnoví zásady ze záložního souboru. Kdykoli je provedena změna zásady, uloží nástroj Caspol.exe starou zásadu do záložního souboru.|  
|**-remfulltrust** *assembly_file*<br /><br /> or<br /><br /> **-rf**  *assembly_file*|Odstraní sestavení ze seznamu úplné důvěryhodnosti na úrovni zásad. Tato operace by měla být provedena, pokud sada oprávnění obsahující vlastní oprávnění již není zásadou používána. Sestavení implementující vlastní oprávnění byste však měli odstranit ze seznamu úplné důvěryhodnosti pouze tehdy, pokud sestavení neimplementuje žádná další vlastní oprávnění, která jsou stále používána. Po odstranění sestavení ze seznamu by měla být rovněž odstraněna další sestavení, která jsou na něm závislá.|  
|**-remgroup** {*popisek &#124;název*}<br /><br /> or<br /><br /> **-rg** {l*abel &#124; název*}|Odstraňuje skupinu kódu zadanou popiskem nebo názvem. Pokud má zadaná skupina kódu podřízenou skupinu kódu, nástroj Caspol.exe odstraní rovněž všechny podřízené skupiny kódu.|  
|**-rempset** *pset_name*<br /><br /> or<br /><br /> **-rp** *pset_name*|Odstraní ze zásady zadanou sadu oprávnění. *Pset_name* argument určuje, která sada oprávnění k odebrání. Nástroj Caspol.exe odstraňuje sadu oprávnění pouze tehdy, pokud není asociována se skupinou kódu. Výchozí (vestavěné) sady oprávnění nemohou být odstraněny.|  
|**-reset**<br /><br /> or<br /><br /> **-rs**|Vrátí zásadu do původního stavu a uloží ji na disk. To se hodí vždy při podezření, že je změněná zásada neopravitelně poškozena a když je zapotřebí začít znovu s výchozími nastaveními instalace. Resetování se může rovněž hodit, když má být jako výchozí bod pro modifikaci konkrétních konfiguračních souborů zabezpečení použita výchozí zásada. Další informace najdete v tématu [ruční úprava konfiguračních souborů zabezpečení](#cpgrfcodeaccesssecuritypolicyutilitycaspolexeanchor1).|  
|**-resetlockdown**<br /><br /> or<br /><br /> **-rsld**|Vrátí zásadu do více omezující verze výchozího stavu a uloží ji na disk. vytvoří zálohu předchozí zásady počítače a uloží ji do souboru s názvem `security.config.bac`.  Uzamčená zásada je podobná výchozí zásadě, s tím rozdílem, že tato zásada neposkytuje žádná oprávnění pro kódování ze `Local Intranet`, `Trusted Sites`, a `Internet` zóny a odpovídajících skupin kódu mít žádné podřízené skupiny kódu.|  
|**-resolvegroup** *assembly_file*<br /><br /> or<br /><br /> **-rsg**  *assembly_file*|Zobrazuje skupiny kódu konkrétní sestavení (*assembly_file*) patří. Ve výchozím nastavení tato možnost zobrazuje úrovně zásad počítače, uživatele a podniku, ke kterým sestavení patří. Chcete-li zobrazit pouze jedné úrovně zásad, tuto možnost použijte buď **– počítače**, **– uživatele**, nebo **– enterprise** možnost.|  
|**-resolveperm** *assembly_file*<br /><br /> or<br /><br /> **-rsp** *assembly_file*|Zobrazuje všechna oprávnění, která zadaná (nebo výchozí) úroveň zásady zabezpečení může poskytnout sestavení, pokud je sestavením povoleno spuštění. *Assembly_file* argument určuje sestavení. Pokud zadáte **– všechny** možnost Caspol.exe vypočítá oprávnění pro sestavení na základě zásad uživatele, počítače a podniku; v opačném případě jsou aplikována výchozí pravidla chování.|  
|**-s**[**ecurity**] {**na** &#124; **vypnout**}|Vypne nebo zapne zabezpečení přístupu kódu. Zadání **-s off** možnost nezakáže zabezpečení založené na rolích. **Poznámka:**  Tento přepínač byl ve [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] a novějších verzích. Další informace najdete v tématu [změny zabezpečení](../../../docs/framework/security/security-changes.md). **Upozornění:**  Pokud je zabezpečení přístupu kódu zakázáno, všechny přístupy ke kódu budou úspěšné. Zakázání zabezpečení přístupu kódu způsobí, že bude systém zranitelný vůči útokům škodlivým kódem, jako jsou například viry nebo červi. Vypnutí zabezpečení přinese zlepšení výkonu, ale mělo by být použito pouze tehdy, pokud byla přijata další bezpečnostní opatření, která pomohou zajistit, aby celková bezpečnost systému nebyla narušena. Mezi příklady dalších bezpečnostních opatření patří: odpojení od veřejné sítě, fyzické zabezpečení počítačů atd.|  
|**-u**[**ser**]|Značí, že jsou všechny možnosti následující po této možnosti aplikovány na zásadu na uživatelské úrovni pro uživatele, který nástroj Caspol.exe spustil. Běžní uživatelé **-uživatel** je výchozí nastavení.|  
|**-?**|Zobrazí syntaxi a možnosti příkazu pro nástroj Caspol.exe.|  
  
 *Mship* argument, který určuje podmínku členství pro skupinu kódu, je možné s **- addgroup** a **- chggroup** možnosti. Každý *mship* argument je implementován jako třída rozhraní .NET Framework. Chcete-li určit *mship,* použijte jednu z následujících akcí.  
  
|Argument|Popis|  
|--------------|-----------------|  
|**-allcode**|Specifikuje veškerý kód. Další informace o této podmínce členství najdete v tématu <xref:System.Security.Policy.AllMembershipCondition?displayProperty=nameWithType>.|  
|**-appdir**|Určuje adresář aplikace. Pokud zadáte **– appdir** jako podmínky členství, adresa URL evidence kódu porovnána s evidencí adresáře aplikace daného kódu. Pokud jsou obě hodnoty evidence stejné, byly podmínky členství splněny. Další informace o této podmínce členství najdete v tématu <xref:System.Security.Policy.ApplicationDirectoryMembershipCondition?displayProperty=nameWithType>.|  
|**–vlastní**  *soubor XML*|Přidá vlastní podmínku členství. Povinné *xmlfile* argument určuje soubor .xml obsahující XML serializaci vlastní podmínky členství.|  
|**-hash** *hashAlg* {**-hex** *Hodnota_hash* &#124; **– soubor** *assembly_file* }|Určuje kód, který obsahuje zadanou hodnotu hash sestavení. Pro použití hodnoty hash jako podmínky členství ve skupině kódu je nutné zadat hodnotu hash nebo soubor sestavení. Další informace o této podmínce členství najdete v tématu <xref:System.Security.Policy.HashMembershipCondition?displayProperty=nameWithType>.|  
|**-pub** { **-cert** *název_souboru_certifikátu*&#124;<br /><br /> **-soubor** *název_podepsaného_souboru* &#124; **-hex**  *šestnáctkový_řetězec* }|Určuje kód, který obsahuje zadaného vydavatele softwaru, jak je označeno souborem certifikátu, podpisem na souboru nebo šestnáctkovou reprezentací certifikátu X509. Další informace o této podmínce členství najdete v tématu <xref:System.Security.Policy.PublisherMembershipCondition?displayProperty=nameWithType>.|  
|**– lokality** *webu*|Určuje kód, který obsahuje zadanou webovou stránku původu. Příklad:<br /><br /> `-site** www.proseware.com`<br /><br /> Další informace o této podmínce členství najdete v tématu <xref:System.Security.Policy.SiteMembershipCondition?displayProperty=nameWithType>.|  
|**-strong – soubor** *název_souboru* {*název* &#124; **- noname**} {*verze* &#124; **- noversion**}|Určuje kód, který má specifický silný název určený název souboru, název sestavení jako řetězec a verze sestavení ve formátu *hlavní*. *vedlejší*. *sestavení*. *Revize*. Příklad:<br /><br /> **-strong – soubor** myAssembly.exe myAssembly. 1.2.3.4.<br /><br /> Další informace o této podmínce členství najdete v tématu <xref:System.Security.Policy.StrongNameMembershipCondition?displayProperty=nameWithType>.|  
|**-url** *adresy URL*|Určuje kód pocházející ze zadané adresy URL. Adresa URL musí obsahovat protokol, jako například `http://` nebo `ftp://`. Kromě toho zástupný znak (\*) slouží k určení více sestavení z určité adresy URL. **Poznámka:**  Jelikož adresa URL může být identifikována pomocí více názvů, použití adresy URL jako podmínky členství není bezpečným způsobem pro zjištění identity kódu. Kdykoli je to možné, použijte podmínku členství silného názvu, podmínku vydavatele nebo podmínku hodnoty hash. <br /><br /> Další informace o této podmínce členství najdete v tématu <xref:System.Security.Policy.UrlMembershipCondition?displayProperty=nameWithType>.|  
|**-zóny** *Název_zóny*|Určuje kód pomocí zadané zóny původu. *Zonename* argument může být jedna z následujících hodnot: **Tento počítač**, **intranetu**, **důvěryhodné**, **Internet**, nebo **nedůvěryhodné**. Další informace o této podmínce členství najdete v tématu <xref:System.Security.Policy.ZoneMembershipCondition> třídy.|  
  
 *Příznaky* argument, který lze použít s **– addgroup** a **– chggroup** volby, je specifikován pomocí jedné z následujících akcí.  
  
|Argument|Popis|  
|--------------|-----------------|  
|**– Popis** "*popis*"|Pokud je použita s **– addgroup** možnost, určuje popis skupiny kódu pro přidání. Pokud je použita s **– chggroup** možnost, určuje popis skupiny kódu pro úpravu. *Popis* argument musí být umístěn do dvojitých uvozovek.|  
|**– exkluzivní** {**na**&#124;**vypnout**}|Pokud je nastavena na **na**, označuje, že pouze sada oprávnění asociovaná s skupiny kódu, které přidáváte nebo úpravy se považuje za když nějaký kód odpovídá podmínce členství skupiny kódu. Když je tato možnost nastavená na **vypnout**, Caspol.exe bere v úvahu sadu oprávnění všech odpovídajících skupin kódu na úrovni zásad.|  
|**-levelfinal** {**na**&#124;**vypnout**}|Pokud je nastavena na **na**, označuje, že se považuje za žádná úroveň zásad pod úrovní, ve kterém dochází přidání nebo modifikaci skupiny kódu. Tato možnost je obvykle používaná na úrovni zásad počítače. Pokud je tento příznak například nastaven pro skupinu kódu na úrovni počítače a některý kód odpovídá podmínce členství této skupiny kódu, nástroj Caspol.exe nevypočítá a neaplikuje pro tento kód zásadu na uživatelské úrovni.|  
|**-název** "*název*"|Pokud je použita s **– addgroup** možnost, určuje skriptovací název skupiny kódu pro přidání. Pokud je použita s **- chggroup** možnost, určuje skriptovací název skupiny kódu pro úpravu. *Název* argument musí být umístěn do dvojitých uvozovek. *Název* argument nemůže začínat číslicí a může obsahovat pouze A-Z, 0-9 a podtržítko. Skupiny kódu může být odkazováno pomocí *název* namísto číselného popisku. *Název* je také velmi užitečné pro účely skriptování.|  
  
## <a name="remarks"></a>Poznámky  
 Zásada zabezpečení je vyjádřena pomocí tří úrovní zásad: počítačová, uživatelská a podniková. Sada oprávnění, kterou sestavení přijímá, je určena průnikem sad oprávnění povolených těmito třemi úrovněmi zásad. Každá úroveň zásad je reprezentována hierarchickou strukturou skupin kódu. Každá skupina kódu má podmínku členství, která určuje, který kód je členem této skupiny. Sada pojmenovaných oprávnění je rovněž asociována s každou skupinou kódu. Tato sada oprávnění určuje oprávnění, která modul runtime povoluje kódu splňujícímu podmínku členství. Hierarchie skupin kódu, společně se souvisejícími pojmenovanými sadami oprávnění, definuje a spravuje každou úroveň zásad zabezpečení. Můžete použít **– uživatel**, **- customuser**, **– počítače** a **– enterprise** možnosti nastavení úrovně zásady zabezpečení.  
  
 Další informace o zásadách zabezpečení a jak modul runtime určuje, jaká oprávnění udělit kódu najdete v tématu [Správa zásad zabezpečení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c1k0eed6(v=vs.100)).  
  
## <a name="referencing-code-groups-and-permission-sets"></a>Odkazování na skupiny kódu a sady oprávnění  
 Pro usnadnění odkazování na skupiny kódu v hierarchii, **– seznam** možnost zobrazí odsazený seznam skupin kódu společně s jejich číselnými popisky (1, 1.1, 1.1.1 atd.). Další operace příkazového řádku zaměřené na skupiny kódu využívají k odkazování na specifické skupiny kódu také číselné popisky.  
  
 Pojmenované sady jsou odkazovány podle svých názvů. **– Seznam** možnost zobrazí seznam skupin kódu následovaný seznamem pojmenovaných oprávnění nastaví k dispozici v dané zásadě.  
  
## <a name="caspolexe-behavior"></a>Chování nástroje Caspol.exe  
 Všechny možnosti kromě možnosti **-s**[**ecurity**] {**na** &#124; **vypnout**} používají verzi rozhraní .NET Framework, zda byl nainstalován Caspol.exe s. Pokud je spuštěn nástroj Caspol.exe, který byl nainstalován s verzí *X* modulu runtime, změny se aplikují pouze na tuto verzi. Jiné souběžné instalace modulu runtime, pokud nějaké existují, nejsou ovlivněny. Pokud je nástroj Caspol.exe spuštěn z příkazového řádku, aniž by se nacházel v adresáři konkrétní verze modulu runtime, bude spuštěn z prvního adresáře verze modulu runtime v cestě (obvykle to bývá poslední nainstalovaná verze).  
  
 **-S**[**ecurity**] {**na** &#124; **vypnout**} možnost je operací pro celý počítač. Vypnutí zabezpečení přístupu kódu ukončí kontroly zabezpečení veškerého spravovaného kódu pro všechny uživatele na počítači. Pokud jsou na počítači současně nainstalovány různé verze rozhraní .NET Framework, vypne tento příkaz zabezpečení pro všechny verze nainstalované na počítači. I když **– seznam** možnost ukazuje, že je zabezpečení vypnuto, nic dalšího jasně označuj pro ostatní uživatele, které bylo zabezpečení vypnuto.  
  
 Když uživatel bez oprávnění správce spustí Caspol.exe, všechny možnosti vztahovat na úroveň zásad uživatele, pokud **– počítače** je zadána možnost. Když správce spustí Caspol.exe, všechny možnosti vztahovat na zásady počítače, pokud **– uživatel** je zadána možnost.  
  
 Caspol.exe musí být udělena ekvivalent **všechno, co** oprávnění. Nástroj má ochranný mechanismus, který zabraňuje zásadě, aby byla modifikována způsobem, který by nástroji Caspol.exe znemožnil získat oprávnění nutná pro jeho spuštění. Pokud se o takovou změnu pokusíte, nástroj Caspol.exe oznámí, že požadovaná změna zásady nástroj poškodí a změna zásady bude zamítnuta. Můžete vypnout tento ochranný mechanizmus pro zadaný příkaz s použitím **– platnost** možnost.  
  
<a name="cpgrfcodeaccesssecuritypolicyutilitycaspolexeanchor1"></a>   
## <a name="manually-editing-the-security-configuration-files"></a>Ruční úprava konfiguračních souborů zabezpečení  
 Tři konfigurační soubory zabezpečení odpovídají třem úrovním zásad podporovaných nástrojem Caspol.exe: jeden je pro zásadu počítače, jeden pro zásadu daného uživatele a jeden pro zásadu podniku. Tyto soubory jsou vytvořeny na disku, když je zásada počítače, uživatele nebo podniku změněna pomocí nástroje Caspol.exe. Můžete použít **– resetování** možnost v Caspol.exe uložení výchozí zásady zabezpečení na disk, v případě potřeby.  
  
 Ve většině případů není manuální úprava těchto konfiguračních souborů zabezpečení doporučena. Mohou se však vyskytnout scénáře, ve kterých je úprava těchto souborů nezbytná. Například, když chce správce upravit konfiguraci zabezpečení pro konkrétního uživatele.  
  
## <a name="examples"></a>Příklady  
 **-addfulltrust**  
  
 Předpokládejme, že byla do zásady počítače přidána sada oprávnění obsahující vlastní oprávnění. Tato vlastní oprávnění je implementováno v `MyPerm.exe`, a `MyPerm.exe` odkazuje na třídy v `MyOther.exe`. Obě sestavení musí být přidána do seznamu sestavení úplné důvěryhodnosti. Následující příkaz přidá `MyPerm.exe` sestavení do seznamu úplné důvěryhodnosti pro zásadu počítače.  
  
```console  
caspol -machine -addfulltrust MyPerm.exe  
```  
  
 Následující příkaz přidá `MyOther.exe` sestavení do seznamu úplné důvěryhodnosti pro zásadu počítače.  
  
```console  
caspol -machine -addfulltrust MyOther.exe  
```  
  
 **-addgroup**  
  
 Následující příkaz přidá do kořene hierarchie skupin kódu zásady počítače podřízenou skupinu kódu. Nová skupina kódu je členem skupiny **Internet** zónu a souvisí s **provádění** sadu oprávnění.  
  
```console  
caspol -machine -addgroup 1.  -zone Internet Execution  
```  
  
 Následující příkaz přidá podřízenou skupinu kódu, který poskytuje sdílené složky \\\netserver\netshare oprávnění sdílení místního intranetu.  
  
```console  
caspol -machine -addgroup 1. -url \\netserver\netshare\* LocalIntranet  
```  
  
 **-addpset**  
  
 Následující příkaz přidá `Mypset` oprávnění nastaveno na zásady uživatele.  
  
```console  
caspol -user -addpset Mypset.xml Mypset  
```  
  
 **-chggroup**  
  
 Následující příkaz změní sadu oprávnění v zásadě uživatele skupiny kódu označené jako 1.2. Chcete **provádění** sadu oprávnění.  
  
```console  
caspol -user -chggroup 1.2. Execution  
```  
  
 Následující příkaz změní podmínku členství ve výchozí zásadě skupiny kódu označené jako 1.2.1. a změní nastavení **exkluzivní** příznak. Podmínka členství je definován jako kód, který pochází z **Internet** zóny a **exkluzivní** příznak je zapnuté.  
  
```console  
caspol -chggroup 1.2.1. -zone Internet -exclusive on  
```  
  
 **-chgpset**  
  
 Následující příkaz změní sadu oprávnění s názvem `Mypset` na sadu oprávnění obsaženou v `newpset.xml`. Aktuální verze nepodporuje změnu sady oprávnění, která je používána hierarchií skupiny kódu.  
  
```console  
caspol -chgpset Mypset newpset.xml  
```  
  
 **-force**  
  
 Následující příkaz způsobí, že bude Kořenová skupina kódu (označená jako 1) asociována s **nic** pojmenovanou sadu oprávnění. To zabrání nástroji Caspol.exe ve spuštění.  
  
```console  
caspol -force -user -chggroup 1 Nothing  
```  
  
 **-recover**  
  
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
  
 Následující příkaz odstraní **provádění** ze zásady uživatele sadu oprávnění.  
  
```console  
caspol -user -rempset Execution  
```  
  
 Následující příkaz odstraní `Mypset` z úroveň zásad uživatele.  
  
```console  
caspol -rempset MyPset  
```  
  
 **-resolvegroup**  
  
 Následující příkaz ukáže všechny skupiny kódu zásady počítače, který `myassembly` patří.  
  
```console  
caspol -machine -resolvegroup myassembly  
```  
  
 Následující příkaz ukáže všechny skupiny kódu počítače, podniku a určeného vlastního uživatele zásad, `myassembly` patří.  
  
```console  
caspol -customall "c:\config_test\security.config" -resolvegroup myassembly  
```  
  
 **-resolveperm**  
  
 Následující příkaz vypočítá oprávnění pro `testassembly` podle úrovně zásad počítače a uživatele.  
  
```console  
caspol -all -resolveperm testassembly  
```  
  
## <a name="see-also"></a>Viz také:

- [Nástroje](index.md)
- [Příkazové řádky](developer-command-prompt-for-vs.md)
