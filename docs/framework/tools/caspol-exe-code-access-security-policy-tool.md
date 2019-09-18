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
ms.openlocfilehash: bc4dd2703f32f2983a207d5990a6e8e646de8c17
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71044865"
---
# <a name="caspolexe-code-access-security-policy-tool"></a>Caspol.exe (nástroj zásad zabezpečení přístupu kódu)
Nástroj Code Access Security (CAS) Policy (Caspol.exe) umožňuje uživatelům a správcům měnit zásady zabezpečení pro úroveň zásad počítače, úroveň zásad uživatele a úroveň zásad podniku.  
  
> [!IMPORTANT]
> Počínaje .NET Framework 4 nástroj Caspol. exe neovlivňuje zásady CAS, pokud `true` [ \<není element > legacyCasPolicy](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) nastaven na hodnotu. Libovolná nastavení zobrazená nebo upravená pomocí nástroje CasPol.exe ovlivňují pouze aplikace, které se přihlašují pomocí zásad CAS. Další informace najdete v tématu [změny zabezpečení](../security/security-changes.md).  
  
> [!NOTE]
> 64bitové počítače obsahují 64bitové i 32bitové verze zásad zabezpečení. Aby bylo zajištěno, že změny v zásadách se aplikují na 32bitové i 64bitové aplikace, je třeba spustit 32bitovou i 64bitovou verzi nástroje Caspol.exe.  
  
 Nástroj zásad CAS je automaticky nainstalován společně s rozhraním .NET Framework a se sadou Visual Studio. Caspol. exe můžete najít\\v%windir%\Microsoft.NET\Framework*verzi* v 32 systémech nebo%windir%\Microsoft.NET\Framework64\\*verze* v systémech 64. (V případě rozhraní .NET Framework 4 v 64bitových systémech je to například %windir%\Microsoft.NET\Framework64\v4.030319\caspol.exe.) Pokud počítač obsahuje více verzí rozhraní .NET Framework, může zde být nainstalováno více verzí tohoto nástroje. Nástroj lze spustit z instalačního adresáře. Doporučujeme však použít [příkazy](developer-command-prompt-for-vs.md), které nevyžadují přechod do instalační složky.  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```console
caspol [options]  
```  
  
## <a name="parameters"></a>Parametry  
  
|Možnost|Popis|  
|------------|-----------------|  
|**– addfulltrust** *assembly_file*<br /><br /> or<br /><br /> **-AF** *assembly_file*|Přidá sestavení implementující vlastní bezpečnostní objekt (jako je vlastní povolení nebo vlastní stav členství) na seznam sestavení úplné důvěryhodnosti pro konkrétní úroveň zásad. Argument *assembly_file* určuje sestavení, které chcete přidat. Tento soubor musí být podepsán se [silným názvem](../../standard/assembly/strong-named.md). Sestavení se silným názvem můžete podepsat pomocí [nástroje Strong Name (Sn. exe)](sn-exe-strong-name-tool.md).<br /><br /> Pokaždé, když je sada oprávnění obsahující vlastní oprávnění přidána k zásadě, musí být sestavení implementující vlastní oprávnění přidáno na seznam úplné důvěryhodnosti pro danou úroveň zásad. Sestavení, která implementují vlastní bezpečnostní objekty (jako jsou vlastní skupiny kódů nebo podmínky členství) používaná v bezpečnostních zásadách (jako je například zásada počítače), by měla být vždy přidána na seznam sestavení úplné důvěryhodnosti. **Upozornění**  Pokud sestavení implementuje vlastní odkazy objektů zabezpečení jiných sestavení, je třeba nejprve přidat odkazovaná sestavení do seznamu plně důvěryhodných sestavení. Vlastní objekty zabezpečení vytvořené pomocí jazyka Visual Basic, C++ nebo JScript se odkazují na knihovny Microsoft.VisualBasic.dll, Microsoft.VisualC.dll nebo Microsoft.JScript.dll. Tato sestavení nejsou v seznamu sestavení úplné důvěryhodnosti ve výchozím nastavení obsažena. Před přidáním vlastního objektu zabezpečení musíte příslušné sestavení přidat do seznamu úplné důvěryhodnosti. Pokud tak neučiníte, přerušíte tím systém zabezpečení, což povede k selhání načtení všech sestavení. V této situaci nebude možnost Caspol. exe **-all-reset** opravovat zabezpečení. Chcete-li opravit zabezpečení, musíte ručně odebrat vlastní objekt zabezpečení ze souborů zabezpečení.|  
|**– AddGroup** {*parent_label &#124; parent_name*} *mship pset_name* [*příznaky*]<br /><br /> or<br /><br /> **– AG** {*parent_label &#124; parent_name*} *mship pset_name* [*příznaky*]|Přidá do hierarchie skupin kódu novou skupinu kódu. Můžete zadat buď *parent_label* , nebo *parent_name*. Argument *parent_label* Určuje popisek (například 1. nebo 1,1.) skupiny kódu, která je nadřazena přidávané skupině kódu. Argument *parent_name* Určuje název skupiny kódu, která je nadřazena přidávané skupině kódu. Vzhledem k tomu, že *parent_label* a *parent_name* lze použít zaměnitelné, nástroj Caspol. exe musí být schopný rozlišovat mezi nimi. Proto *parent_name* nemůže začínat číslicí. Kromě toho *parent_name* může obsahovat pouze znaky a – Z, 0-9 a podtržítko.<br /><br /> Argument *mship* Určuje podmínku členství pro novou skupinu kódu. Další informace najdete v tabulce argumentů *mship* dále v této části.<br /><br /> Argument *pset_name* je název sady oprávnění, která bude přidružena k nové skupině kódu. Pro novou skupinu můžete také nastavit jeden nebo více *příznaků* . Další informace najdete v tabulce *příznaků příznaků* dále v této části.|  
|**-addpset** {*psfile* &#124; *psfile* p*set_name*}<br /><br /> or<br /><br /> **-ap** {*named*_*psfile* &#124; *psfile* *pset_name*}|Přidá do zásad pojmenovanou sadu oprávnění. Sada oprávnění musí být napsána v jazyce XML a uložena do souboru .xml. Pokud soubor XML obsahuje název sady oprávnění, je určen pouze tento soubor (*PsFile*). Pokud soubor XML neobsahuje název sady oprávnění, je nutné zadat název souboru XML (*PsFile*) a název sady oprávnění (*pset_name*).<br /><br /> Všechna oprávnění použitá v sadě oprávnění musí být definována v sestaveních obsažených v globální mezipaměti sestavení (GAC).|  
|**-a**[**ll**]|Značí, že jsou všechny možnosti následující za touto možností aplikovány na zásady počítače, uživatele a podniku. Možnost **-All** vždy odkazuje na zásadu aktuálně přihlášeného uživatele. Pokud chcete odkazovat na zásady uživatele jiné než aktuální uživatel, použijte možnost **-customall** .|  
|**– chggroup** {*Label &#124;Name*} {*mship* &#124; *pset_name*&#124;<br /><br /> *příznaky*`}`<br /><br /> or<br /><br /> **-** v {*Label &#124;Name*} {*mship* &#124; *pset_name*&#124;<br /><br /> *příznaky*`}`|Změní podmínku členství ve skupině kódu, sadu oprávnění nebo nastavení příznaků **Exclusive**, **LevelFinal**, **Name**nebo **Description** . Můžete zadat buď *popisek* , nebo *název*. Argument *Label* Určuje popisek (například 1. nebo 1,1.) skupiny kódu. Argument *Name* Určuje název skupiny kódu, která se má změnit. Vzhledem k tomu, že *popisek* a *název* lze použít zaměnitelné, nástroj Caspol. exe musí být schopný rozlišovat mezi nimi. Proto *název* nemůže začínat číslicí. Kromě toho *název* může obsahovat pouze znaky a – Z, 0-9 a podtržítko.<br /><br /> Argument *pset_name* Určuje název sady oprávnění, která se má přidružit ke skupině kódu. V tabulkách níže v této části najdete informace o argumentech *mship* a *Flags* .|  
|**– chgpset** *PsFile pset_name*<br /><br /> or<br /><br /> **-CP** *PsFile pset_name*|Mění pojmenovanou sadu oprávnění. Argument *PsFile* poskytuje novou definici pro sadu oprávnění. Jedná se o serializovaný soubor sady oprávnění ve formátu XML. Argument *pset_name* Určuje název sady oprávnění, kterou chcete změnit.|  
|**-customall**  *cesta*<br /><br /> or<br /><br /> **– ca**  *cesta*|Značí, že jsou všechny možnosti následující za touto možností aplikovány na zásady počítače, podniku a určeného vlastního uživatele. Je nutné zadat umístění souboru konfigurace zabezpečení vlastního uživatele s argumentem *path* .|  
|**-cu**[**stomuser**] *path*|Umožňuje spravovat zásadu vlastního uživatele, která nepatří uživateli, jenž aktuálně spouští nástroj Caspol.exe. Je nutné zadat umístění souboru konfigurace zabezpečení vlastního uživatele s argumentem *path* .|  
|**– Enterprise**<br /><br /> or<br /><br /> **-EN**|Značí, že jsou všechny možnosti následující za touto možností aplikovány na zásady na úrovni podniku. Uživatelé, kteří nejsou podnikovými administrátory, nemají dostatečná práva pro modifikaci podnikové zásady, přestože si ji mohou zobrazit. V nepodnikových scénářích nebude tato zásada ve výchozím nastavení ovlivňovat zásadu počítače ani uživatele.|  
|**-e** [**xecution**] &#124; { **vypnuto**}|Vypíná nebo zapíná mechanismus, jenž ověřuje, která oprávnění se mají před spuštěním kódu provést. **Poznámka:**  Tento přepínač je odebraný v .NET Framework 4 a novějších verzích. Další informace najdete v tématu [změny zabezpečení](../security/security-changes.md).|  
|**-f** [**Orce**]|Zakáže, aby nástroj provedl autodestruktivní test a změní zásadu dle zadání uživatele. Nástroj Caspol.exe běžně ověřuje, zda může jakákoli změna zásady zabránit nástroji Caspol.exe ve správném spuštění. Pokud tomu tak je, nástroj Caspol.exe změnu zásady neuloží a zobrazí chybovou zprávu. Chcete-li vynutit změnu zásad pomocí nástroje Caspol. exe, i když to brání spuštění nástroje Caspol. exe, použijte možnost **– Force** .|  
|**-h** [**ELP**]|Zobrazí syntaxi a možnosti příkazu pro nástroj Caspol.exe.|  
|**-l**[**ist**]|Vypíše hierarchii skupiny kódu a sad oprávnění konkrétního počítače, uživatele, podniku nebo všech úrovní zásad. Nástroj Caspol.exe zobrazuje nejprve popisek skupiny kódu a poté název, pokud není null.|  
|**-listdescription**<br /><br /> or<br /><br /> **-ld**|Vypíše všechny popisy skupiny kódu pro zadanou úroveň zásad.|  
|**-listfulltrust**<br /><br /> or<br /><br /> **-LF**|Vypíše obsah sestavení úplného vztahu důvěryhodnosti pro zadanou úroveň zásad.|  
|**-listgroups**<br /><br /> or<br /><br /> **– LG**|Zobrazuje skupiny kódu konkrétní úrovně nebo všech úrovní zásad. Nástroj Caspol.exe zobrazuje nejprve popisek skupiny kódu a poté název, pokud není null.|  
|**-listpset** nebo **-LP**|Zobrazí sady oprávnění konkrétní úrovně nebo všech úrovní zásad.|  
|**-m**[**achine**]|Značí, že jsou všechny možnosti následující za touto možností aplikovány na zásady na úrovni počítače. Uživatelé, kteří nejsou administrátory, nemají dostatečná práva pro modifikaci zásady počítače, přestože si ji mohou zobrazit. Pro správce je výchozí hodnota **Machine** .|  
|**-polchgprompt** {**on** &#124; **off**}<br /><br /> or<br /><br /> **-PP** &#124; { **vypnuto**}|Povoluje nebo zakazuje dotaz, který se zobrazí vždy, když je nástroj Caspol.exe spuštěn pomocí možnosti, která může způsobit změnu zásad.|  
|**-quiet**<br /><br /> or<br /><br /> **-q**|Dočasně zakazuje dotaz, který se normálně zobrazí pro možnost způsobující změny zásad. Globální nastavení dotazu na změnu se nezmění. Tuto možnost použijte pouze u samostatných příkazů, aby bylo zabráněno zakázání výzev pro všechny příkazy nástroje Caspol.exe.|  
|**-r** [**Ecover**]|Obnoví zásady ze záložního souboru. Kdykoli je provedena změna zásady, uloží nástroj Caspol.exe starou zásadu do záložního souboru.|  
|**– remfulltrust** *assembly_file*<br /><br /> or<br /><br /> **-rf**  *assembly_file*|Odstraní sestavení ze seznamu úplné důvěryhodnosti na úrovni zásad. Tato operace by měla být provedena, pokud sada oprávnění obsahující vlastní oprávnění již není zásadou používána. Sestavení implementující vlastní oprávnění byste však měli odstranit ze seznamu úplné důvěryhodnosti pouze tehdy, pokud sestavení neimplementuje žádná další vlastní oprávnění, která jsou stále používána. Po odstranění sestavení ze seznamu by měla být rovněž odstraněna další sestavení, která jsou na něm závislá.|  
|**– remgroup** {*Label &#124;Name*}<br /><br /> or<br /><br /> **– RG** {l*Abel &#124; jméno*}|Odstraňuje skupinu kódu zadanou popiskem nebo názvem. Pokud má zadaná skupina kódu podřízenou skupinu kódu, nástroj Caspol.exe odstraní rovněž všechny podřízené skupiny kódu.|  
|**-rempset** *pset_name*<br /><br /> or<br /><br /> **-rp** *pset_name*|Odstraní ze zásady zadanou sadu oprávnění. Argument *pset_name* určuje, která sada oprávnění má být odebrána. Nástroj Caspol.exe odstraňuje sadu oprávnění pouze tehdy, pokud není asociována se skupinou kódu. Výchozí (vestavěné) sady oprávnění nemohou být odstraněny.|  
|**-reset**<br /><br /> or<br /><br /> **-rs**|Vrátí zásadu do původního stavu a uloží ji na disk. To se hodí vždy při podezření, že je změněná zásada neopravitelně poškozena a když je zapotřebí začít znovu s výchozími nastaveními instalace. Resetování se může rovněž hodit, když má být jako výchozí bod pro modifikaci konkrétních konfiguračních souborů zabezpečení použita výchozí zásada. Další informace najdete v tématu [Ruční úprava konfiguračních souborů zabezpečení](#cpgrfcodeaccesssecuritypolicyutilitycaspolexeanchor1).|  
|**-resetlockdown**<br /><br /> or<br /><br /> **-rsld**|Vrátí zásady do více omezující verze výchozího stavu a uloží je na disk. vytvoří zálohu předchozí zásady počítače a uloží ji do souboru s názvem `security.config.bac`.  Uzamčené zásady jsou podobné výchozím zásadám, s tím rozdílem, že zásady neudělují žádné oprávnění ke kódu z `Local Intranet` `Internet` zón `Trusted Sites`, a a odpovídající skupiny kódu nemají žádné podřízené skupiny kódu.|  
|**– Resolve** *assembly_file*<br /><br /> or<br /><br /> **-rsg**  *assembly_file*|Zobrazuje skupiny kódu, ke kterým patří konkrétní sestavení (*assembly_file*). Ve výchozím nastavení tato možnost zobrazuje úrovně zásad počítače, uživatele a podniku, ke kterým sestavení patří. Pokud chcete zobrazit jenom jednu úroveň zásad, použijte tuto možnost s možností **-Machine**, **-User**nebo **-Enterprise** .|  
|**– resolveperm** *assembly_file*<br /><br /> or<br /><br /> **– RSP** *assembly_file*|Zobrazuje všechna oprávnění, která zadaná (nebo výchozí) úroveň zásady zabezpečení může poskytnout sestavení, pokud je sestavením povoleno spuštění. Argument *assembly_file* určuje sestavení. Pokud zadáte možnost **-All** , nástroj Caspol. exe vypočítá oprávnění pro sestavení na základě zásad uživatele, počítače a podniku. jinak se použijí výchozí pravidla chování.|  
|**-s** [**ecurity**] &#124; { **vypnuto**}|Vypne nebo zapne zabezpečení přístupu kódu. Zadáním možnosti **-s off** nezakážete zabezpečení na základě rolí. **Poznámka:**  Tento přepínač je odebraný v .NET Framework 4 a novějších verzích. Další informace najdete v tématu [změny zabezpečení](../security/security-changes.md). **Upozornění**  Pokud je zabezpečení přístupu kódu zakázáno, všechny přístupy ke kódu budou úspěšné. Zakázání zabezpečení přístupu kódu způsobí, že bude systém zranitelný vůči útokům škodlivým kódem, jako jsou například viry nebo červi. Vypnutí zabezpečení přinese zlepšení výkonu, ale mělo by být použito pouze tehdy, pokud byla přijata další bezpečnostní opatření, která pomohou zajistit, aby celková bezpečnost systému nebyla narušena. Mezi příklady dalších bezpečnostních opatření patří: odpojení od veřejné sítě, fyzické zabezpečení počítačů atd.|  
|**-u** [**ser**]|Značí, že jsou všechny možnosti následující po této možnosti aplikovány na zásadu na uživatelské úrovni pro uživatele, který nástroj Caspol.exe spustil. Pro uživatele, kteří nejsou správci, je výchozím **uživatelem** .|  
|**-?**|Zobrazí syntaxi a možnosti příkazu pro nástroj Caspol.exe.|  
  
 Argument *mship* , který určuje podmínku členství pro skupinu kódu, lze použít s možnostmi **-AddGroup** a **-chggroup** . Každý argument *mship* je implementován jako třída .NET Framework. K určení *mship* použijte jednu z následujících možností.  
  
|Argument|Popis|  
|--------------|-----------------|  
|**– Allcode veškerý**|Specifikuje veškerý kód. Další informace o této podmínce členství naleznete v <xref:System.Security.Policy.AllMembershipCondition?displayProperty=nameWithType>tématu.|  
|**-appdir**|Určuje adresář aplikace. Pokud zadáte **– appdir** jako podmínku členství, adresa URL legitimace kódu je porovnána s legitimací adresáře aplikace daného kódu. Pokud jsou obě hodnoty evidence stejné, byly podmínky členství splněny. Další informace o této podmínce členství naleznete v <xref:System.Security.Policy.ApplicationDirectoryMembershipCondition?displayProperty=nameWithType>tématu.|  
|**–vlastní**  *soubor XML*|Přidá vlastní podmínku členství. Povinný argument *XMLFile* určuje soubor. XML, který obsahuje XML serializaci vlastní podmínky členství.|  
|**hodnota hash** *hashAlg* { **-hex** *hashValue* &#124; **– soubor** *assembly_file* }|Určuje kód, který obsahuje zadanou hodnotu hash sestavení. Pro použití hodnoty hash jako podmínky členství ve skupině kódu je nutné zadat hodnotu hash nebo soubor sestavení. Další informace o této podmínce členství naleznete v <xref:System.Security.Policy.HashMembershipCondition?displayProperty=nameWithType>tématu.|  
|**– Pub** { **-CERT** *cert_file_name*&#124;<br /><br /> **-soubor** *název_podepsaného_souboru* &#124; **-hex**  *šestnáctkový_řetězec* }|Určuje kód, který obsahuje zadaného vydavatele softwaru, jak je označeno souborem certifikátu, podpisem na souboru nebo šestnáctkovou reprezentací certifikátu X509. Další informace o této podmínce členství naleznete v <xref:System.Security.Policy.PublisherMembershipCondition?displayProperty=nameWithType>tématu.|  
|**– lokalita** *webové stránky*|Určuje kód, který obsahuje zadanou webovou stránku původu. Příklad:<br /><br /> `-site** www.proseware.com`<br /><br /> Další informace o této podmínce členství naleznete v <xref:System.Security.Policy.SiteMembershipCondition?displayProperty=nameWithType>tématu.|  
|**– Strong – soubor** *název_souboru* {*Name* &#124; **-NONAME**} {*Version* &#124; **– verze**}|Určuje kód, který má konkrétní silný název, jak je určen názvem souboru, název sestavení jako řetězec a verze sestavení ve formátu *Hlavní*. *vedlejší*. *sestavení*. *Revize*. Příklad:<br /><br /> **– Strong-File** MyAssembly. exe, MyAssembly 1.2.3.4<br /><br /> Další informace o této podmínce členství naleznete v <xref:System.Security.Policy.StrongNameMembershipCondition?displayProperty=nameWithType>tématu.|  
|**– Adresa URL** *Adresa URL*|Určuje kód pocházející ze zadané adresy URL. Adresa URL musí obsahovat protokol, například `http://` nebo. `ftp://` Kromě toho lze použít zástupný znak\*() k určení více sestavení z konkrétní adresy URL. **Poznámka:**  Jelikož adresa URL může být identifikována pomocí více názvů, použití adresy URL jako podmínky členství není bezpečným způsobem pro zjištění identity kódu. Kdykoli je to možné, použijte podmínku členství silného názvu, podmínku vydavatele nebo podmínku hodnoty hash. <br /><br /> Další informace o této podmínce členství naleznete v <xref:System.Security.Policy.UrlMembershipCondition?displayProperty=nameWithType>tématu.|  
|**-Zone** *Název_zóny*|Určuje kód pomocí zadané zóny původu. Argument *Název_zóny* může být jedna z následujících hodnot: **MyComputer**, **intranet**, **Trusted**, **Internet**nebo **nedůvěryhodný**. Další informace o této podmínce členství naleznete v tématu <xref:System.Security.Policy.ZoneMembershipCondition> třída.|  
  
 Argument *Flags* , který lze použít s možnostmi **– AddGroup** a **– chggroup** , je zadán pomocí jedné z následujících možností.  
  
|Argument|Popis|  
|--------------|-----------------|  
|**-Description** *Popis*|Pokud se používá s možností **– AddGroup** , určuje popis pro skupinu kódu, který se má přidat. Pokud se používá s možností **– chggroup** , určuje popis pro skupinu kódu, který se má upravit. Argument *Description* musí být uzavřený v dvojitých uvozovkách.|  
|**– výhradně** &#124;{**vypnuto**}|Pokud je nastaveno na **on**, označuje, že pouze sada oprávnění přidružená ke skupině kódu, kterou přidáváte nebo upravujete, je považována za kód, který odpovídá podmínce členství ve skupině kódu. Je-li tato možnost nastavena na hodnotu **off**, nástroj Caspol. exe považuje sady oprávnění pro všechny vyhovující skupiny kódu na úrovni zásad.|  
|**-LevelFinal** &#124;{**vypnuto**}|Pokud je nastaveno na **on**, označuje, že se nepovažuje žádná úroveň zásad pod úroveň, ve které se přidaná nebo upravená kódová skupina vyskytuje. Tato možnost je obvykle používaná na úrovni zásad počítače. Pokud je tento příznak například nastaven pro skupinu kódu na úrovni počítače a některý kód odpovídá podmínce členství této skupiny kódu, nástroj Caspol.exe nevypočítá a neaplikuje pro tento kód zásadu na uživatelské úrovni.|  
|**– název** "*název*"|Pokud se používá s možností **– AddGroup** , určuje název skriptování pro skupinu kódu, která se má přidat. Pokud se používá s možností **-chggroup** , určuje název skriptování pro skupinu kódu, kterou chcete upravit. Argument *Name* musí být uzavřený v dvojitých uvozovkách. Argument *Name* nemůže začínat číslem a může obsahovat jenom znaky a – Z, 0-9 a podtržítko. Na skupiny kódu se dá odkazovat pomocí tohoto *názvu* místo podle jejich číselného popisku. *Název* je také velmi užitečný pro účely skriptování.|  
  
## <a name="remarks"></a>Poznámky  
 Zásada zabezpečení je vyjádřena pomocí tří úrovní zásad: počítačová, uživatelská a podniková. Sada oprávnění, kterou sestavení přijímá, je určena průnikem sad oprávnění povolených těmito třemi úrovněmi zásad. Každá úroveň zásad je reprezentována hierarchickou strukturou skupin kódu. Každá skupina kódu má podmínku členství, která určuje, který kód je členem této skupiny. Sada pojmenovaných oprávnění je rovněž asociována s každou skupinou kódu. Tato sada oprávnění určuje oprávnění, která modul runtime povoluje kódu splňujícímu podmínku členství. Hierarchie skupin kódu, společně se souvisejícími pojmenovanými sadami oprávnění, definuje a spravuje každou úroveň zásad zabezpečení. K nastavení úrovně zásad zabezpečení můžete použít možnosti **– uživatel**, **-customuser**, **– počítač** a **-Enterprise** .  
  
 Další informace o zásadách zabezpečení a o tom, jak modul runtime určuje, která oprávnění udělit kódu, najdete v tématu [Správa zásad zabezpečení](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/c1k0eed6(v=vs.100)).  
  
## <a name="referencing-code-groups-and-permission-sets"></a>Odkazování na skupiny kódu a sady oprávnění  
 Chcete-li usnadnit odkazy na skupiny kódu v hierarchii, možnost **-list** zobrazí odsazený seznam skupin kódu spolu s jejich číselnými popisky (1, 1,1, 1.1.1 a tak dále). Další operace příkazového řádku zaměřené na skupiny kódu využívají k odkazování na specifické skupiny kódu také číselné popisky.  
  
 Pojmenované sady jsou odkazovány podle svých názvů. Možnost **– seznam** zobrazuje seznam kódových skupin následovaný seznamem pojmenovaných sad oprávnění dostupných v těchto zásadách.  
  
## <a name="caspolexe-behavior"></a>Chování nástroje Caspol.exe  
 Všechny možnosti s výjimkou **-s**[**ecurity**] {**on** &#124; **off**} používají verzi .NET Framework, se kterou program Caspol. exe nainstaloval. Pokud spustíte nástroj Caspol. exe, který byl nainstalován s verzí *X* modulu runtime, změny se vztahují pouze na tuto verzi. Jiné souběžné instalace modulu runtime, pokud nějaké existují, nejsou ovlivněny. Pokud je nástroj Caspol.exe spuštěn z příkazového řádku, aniž by se nacházel v adresáři konkrétní verze modulu runtime, bude spuštěn z prvního adresáře verze modulu runtime v cestě (obvykle to bývá poslední nainstalovaná verze).  
  
 Možnost **-s**[**ecurity**] {**on** &#124; **off**} je operace platná pro počítač. Vypnutí zabezpečení přístupu kódu ukončí kontroly zabezpečení veškerého spravovaného kódu pro všechny uživatele na počítači. Pokud jsou na počítači současně nainstalovány různé verze rozhraní .NET Framework, vypne tento příkaz zabezpečení pro všechny verze nainstalované na počítači. I když možnost **-list** ukazuje, že je zabezpečení vypnuté, nic jiného jasně neindikuje ostatním uživatelům, kteří zabezpečení vypnuli.  
  
 Pokud uživatel bez oprávnění správce spustí nástroj Caspol. exe, všechny možnosti odkazují na zásadu na úrovni uživatele, pokud není zadána možnost **– Machine** . Když správce spustí nástroj Caspol. exe, budou se všechny možnosti vztahovat na zásady počítače, pokud není zadána možnost **– uživatel** .  
  
 Nástroj Caspol. exe musí mít udělen ekvivalent **všech** oprávnění nastavených na funkci. Nástroj má ochranný mechanismus, který zabraňuje zásadě, aby byla modifikována způsobem, který by nástroji Caspol.exe znemožnil získat oprávnění nutná pro jeho spuštění. Pokud se o takovou změnu pokusíte, nástroj Caspol.exe oznámí, že požadovaná změna zásady nástroj poškodí a změna zásady bude zamítnuta. Tento ochranný mechanismus můžete pro daný příkaz vypnout pomocí možnosti **– Force** .  
  
<a name="cpgrfcodeaccesssecuritypolicyutilitycaspolexeanchor1"></a>   
## <a name="manually-editing-the-security-configuration-files"></a>Ruční úprava konfiguračních souborů zabezpečení  
 Tři konfigurační soubory zabezpečení odpovídají třem úrovním zásad podporovaných nástrojem Caspol.exe: jeden je pro zásadu počítače, jeden pro zásadu daného uživatele a jeden pro zásadu podniku. Tyto soubory jsou vytvořeny na disku, když je zásada počítače, uživatele nebo podniku změněna pomocí nástroje Caspol.exe. V případě potřeby můžete použít možnost **– reset** v nástroji Caspol. exe k uložení výchozích zásad zabezpečení na disk.  
  
 Ve většině případů není manuální úprava těchto konfiguračních souborů zabezpečení doporučena. Mohou se však vyskytnout scénáře, ve kterých je úprava těchto souborů nezbytná. Například, když chce správce upravit konfiguraci zabezpečení pro konkrétního uživatele.  
  
## <a name="examples"></a>Příklady  
 **-addfulltrust**  
  
 Předpokládejme, že byla do zásady počítače přidána sada oprávnění obsahující vlastní oprávnění. Toto vlastní oprávnění je implementováno `MyPerm.exe`v a `MyPerm.exe` odkazuje na třídy `MyOther.exe`v. Obě sestavení musí být přidána do seznamu sestavení úplné důvěryhodnosti. Následující příkaz přidá `MyPerm.exe` sestavení do seznamu úplných vztahů důvěryhodnosti pro zásady počítače.  
  
```console  
caspol -machine -addfulltrust MyPerm.exe  
```  
  
 Následující příkaz přidá `MyOther.exe` sestavení do seznamu úplných vztahů důvěryhodnosti pro zásady počítače.  
  
```console  
caspol -machine -addfulltrust MyOther.exe  
```  
  
 **-addgroup**  
  
 Následující příkaz přidá do kořene hierarchie skupin kódu zásady počítače podřízenou skupinu kódu. Nová skupina kódu je členem zóny **Internet** a je přidružena k sadě oprávnění ke **spuštění** .  
  
```console  
caspol -machine -addgroup 1.  -zone Internet Execution  
```  
  
 Následující příkaz přidá podřízenou skupinu kódu, která poskytne sdílené složce \\\netserver\netshare oprávnění místního intranetu.  
  
```console  
caspol -machine -addgroup 1. -url \\netserver\netshare\* LocalIntranet  
```  
  
 **-addpset**  
  
 Následující příkaz přidá `Mypset` sadu oprávnění do zásad uživatele.  
  
```console  
caspol -user -addpset Mypset.xml Mypset  
```  
  
 **-chggroup**  
  
 Následující příkaz změní sadu oprávnění v zásadách uživatele skupiny kódu s označením 1,2. do sady oprávnění ke **spuštění** .  
  
```console  
caspol -user -chggroup 1.2. Execution  
```  
  
 Následující příkaz změní podmínku členství ve výchozích zásadách skupiny kódu označené jako 1.2.1. a mění nastavení příznaku **Exclusive** . Podmínka členství je definována tak, že se jedná o kód, který pochází z zóny **Internet** , a příznak **exkluzivní** je zapnutý.  
  
```console  
caspol -chggroup 1.2.1. -zone Internet -exclusive on  
```  
  
 **-chgpset**  
  
 Následující příkaz změní sadu oprávnění s názvem `Mypset` na sadu oprávnění, která je obsažena v. `newpset.xml` Aktuální verze nepodporuje změnu sady oprávnění, která je používána hierarchií skupiny kódu.  
  
```console  
caspol -chgpset Mypset newpset.xml  
```  
  
 **-Force**  
  
 Následující příkaz způsobí, že kořenová skupina kódu (označená 1) zásad uživatele je přidružená k **žádné** pojmenované sadě oprávnění. To zabrání nástroji Caspol.exe ve spuštění.  
  
```console  
caspol -force -user -chggroup 1 Nothing  
```  
  
 **– obnovení**  
  
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
  
 Následující příkaz odebere sadu oprávnění **spouštění** ze zásad uživatele.  
  
```console  
caspol -user -rempset Execution  
```  
  
 Následující příkaz odeberete `Mypset` z úrovně zásady uživatele.  
  
```console  
caspol -rempset MyPset  
```  
  
 **-resolvegroup**  
  
 Následující příkaz zobrazí všechny kódové skupiny zásad počítače, do kterých `myassembly` patří.  
  
```console  
caspol -machine -resolvegroup myassembly  
```  
  
 Následující příkaz zobrazí všechny kódové skupiny počítačů, podnikových a zadaných vlastních uživatelských zásad, které `myassembly` patří do.  
  
```console  
caspol -customall "c:\config_test\security.config" -resolvegroup myassembly  
```  
  
 **-resolveperm**  
  
 Následující příkaz vypočítá oprávnění pro `testassembly` závislosti na úrovni zásad počítače a uživatele.  
  
```console  
caspol -all -resolveperm testassembly  
```  
  
## <a name="see-also"></a>Viz také:

- [Nástroje](index.md)
- [Příkazové řádky](developer-command-prompt-for-vs.md)
