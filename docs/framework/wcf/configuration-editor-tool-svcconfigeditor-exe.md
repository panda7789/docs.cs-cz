---
title: Nástroj Configuration Editor (SvcConfigEditor.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- configuration files, creating
- configuration files
- Configuration file
- configuration file schema
ms.assetid: 2db21a57-5f64-426f-89df-fb0dc2d2def5
ms.openlocfilehash: 75657786135fd13222c6c7edd5acfa122cc72e52
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="configuration-editor-tool-svcconfigeditorexe"></a>Nástroj Configuration Editor (SvcConfigEditor.exe)
Windows Communication Foundation (WCF) služba konfigurace Editor (SvcConfigEditor.exe) umožňuje správcům a vývojářům umožňuje vytvořit a upravit nastavení konfigurace pro služby WCF pomocí grafického uživatelského rozhraní. Pomocí tohoto nástroje můžete spravovat nastavení pro vazby WCF, chování, služeb a diagnostiky aniž by museli přímo upravit konfigurační soubory XML.  
  
 Editor konfigurací služby naleznete ve složce C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin.  
  
## <a name="the-wcf-configuration-editor"></a>Editor konfigurací WCF  
 Editor konfigurací služby se dodává s průvodce, který vás provede všechny kroky v konfiguraci služby WCF nebo klienta. Důrazně doporučujeme používat Průvodce místo editoru přímo.  
  
 Pokud již máte některé konfigurační soubory, které dodržovat standardní System.Configuration schéma, můžete spravovat nastavení specifická pro vazby, chování, služby a diagnostiku pomocí uživatelského rozhraní. Editor konfigurací služba umožňuje spravovat nastavení pro existující konfigurační soubory WCF a také spustitelné soubory, služby COM + a hostované webové služby. Při otevírání hostované webové služby pomocí služby Editor konfigurací, i službu na vlastní konfiguraci a zděděné konfigurace oddílů horní úrovni uzlů se zobrazí.  
  
 Protože nastavení konfigurace WCF se nachází v `<system.serviceModel>` oddílu konfiguračního souboru editoru funguje výhradně na obsah tohoto elementu a k další prvky ve stejném souboru. Můžete přejít na existující konfigurační soubory přímo, nebo můžete vybrat sestavení, které obsahuje službu, virtuální adresář nebo služby COM +. Editor načte konfiguračního souboru pro tento konkrétní službu a umožňuje uživateli přidat nové prvky nebo upravit stávající elementy vnořených v `<system.serviceModel>` oddílu konfiguračního souboru.  
  
 Editor podporuje technologii IntelliSense a vynucuje schématu dodržování předpisů. Výsledný výstup záruku, že se pro dosažení souladu s schéma konfiguračního souboru a syntakticky správnou datové hodnoty. Editor však nezaručuje, že konfigurační soubor je sémanticky neplatná. Jinými slovy editoru nezaručuje, že konfigurační soubor můžete pracovat na službu, kterou nakonfiguruje.  
  
> [!CAUTION]
>  Editor nelze vyprázdnit prvek konfigurace z konfiguračního souboru, jakmile změníte elementu. Například pokud chcete nastavit název koncového bodu na neprázdný řetězec a uložit ho použijete editoru, konfigurační soubor má následující obsah, jak je znázorněno v následujícím příkladu.  
>   
>  `<endpoint binding="basicHttpBinding" name="somename" />`  
>   
>  Pokud se pokusíte odebrat název podle jeho nastavení na prázdný řetězec a uložit soubor, stále konfigurační soubor obsahuje `name` atributu, jak je znázorněno v následujícím příkladu.  
>   
>  `<endpoint binding="basicHttpBinding" name="" />`  
>   
>  Vyprázdnit atribut, je nutné ručně upravit element pomocí jiném textovém editoru.  
>   
>  Byste měli být opatrní hlavně s tímto problémem, při použití `issueToken` element `clientCredential` chování koncového bodu. Konkrétně `address` atribut jeho `localIssuer` dílčí element nesmí být prázdný řetězec. Pokud jste změnili `address` atribut, pomocí editoru konfigurace a chcete ho úplně odebrat, by měl uděláte pomocí nástroje než editoru. Jinak atribut obsahuje prázdný řetězec a vyvolá výjimku, vaše aplikace.  
  
## <a name="using-the-configuration-editor"></a>Pomocí editoru konfigurace  
 Editor konfigurací služby najdete v následujícím umístění instalace sady Windows SDK:  
  
 C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin\SvcConfigEditor.exe  
  
 Po spuštění editoru konfigurace služby, můžete použít **otevřít** chcete vyhledat služby nebo sestavení, které chcete spravovat, v nabídce. Můžete otevřít konfigurační soubory přímo, procházet služby WCF /COM+ a otevřete konfigurační soubory pro hostované webové služby.  
  
 Editor konfigurací služby uživatelské rozhraní je rozdělené do následujících oblastech:  
  
-   Podokno se stromovým zobrazením, která zobrazuje konfigurace – elementy ve stromové struktuře na levé straně. Ve stromové struktuře můžete provádět operace kliknutím pravým tlačítkem na uzly.  
  
-   Podokna úloh, která zobrazuje Časté úlohy pro aktuální prvky vlevo dolní části okna  
  
-   Podokno podrobností, které zobrazuje podrobné nastavení konfigurace uzlu vybraný ve stromovém zobrazení na pravé straně.  
  
### <a name="opening-a-configuration-file"></a>Otevření konfiguračního souboru  
  
1.  Spusťte Editor konfigurací služby pomocí okno příkazového řádku přejděte do umístění instalace WCF a pak zadejte `SvcConfigEditor.exe`.  
  
2.  Z **soubor** nabídce vyberte možnost **otevřete** a klikněte na typ souboru, kterou chcete spravovat.  
  
3.  V **otevřete** dialogové okno pole, přejděte na konkrétní soubor, který chcete spravovat a poklikejte na něj.  
  
 Prohlížeč automaticky postupuje podle cesta ke konfiguračnímu sloučení a vytvoří zobrazení sloučené konfigurace. Například skutečné konfigurace služby bez hostitele je kombinace souboru Machine.config a App.config. Změny se použijí k active souboru v SvcConfigEditor. Pokud chcete upravit určitý soubor v cestě konfigurace sloučení, by ho otevřít přímo.  
  
> [!NOTE]
>  Editor konfigurace znovu načte aktuálně otevřenou konfiguračního souboru, pokud k tomu byl upraven mimo editoru. V takovém případě budou ztraceny všechny změny, které nejsou bezpečně uloženy v editoru. Pokud se opětovném načtení stane konzistentně, nejpravděpodobnější příčinou je služba, která přistupuje neustále konfiguračního souboru, například antivirový software spuštěný na pozadí. To vyřešit, zkontrolujte, zda Editor konfigurací pouze proces, který může přistupovat k souboru, když je otevřen.  
  
### <a name="services"></a>Služby  
 **Služby** uzlu zobrazí všechny služby, které jsou přiřazeny v konfiguračním souboru. Každý dílčí uzel ve stromové struktuře odpovídá dílčí element <`services`> element v konfiguračním souboru.  
  
 Po kliknutí **služby** uzlu, můžete zobrazit nebo provádět úlohy ve službě stránce Souhrn v **podrobností** podokně.  
  
#### <a name="creating-a-new-service-configuration"></a>Vytvořit novou konfiguraci služby  
 Můžete vytvořit novou konfiguraci služby následujícími způsoby:  
  
-   Pomocí průvodce: klikněte na odkaz **vytvoření nové služby...** v podokně úloh nebo na stránce Souhrn spusťte průvodce. Můžete také provést tak v **soubor** -> nabídky **přidat novou položku**.  
  
-   Ruční vytvoření: můžete kliknout pravým tlačítkem **služby** uzel a zvolte **novou službu**.  
  
#### <a name="creating-a-new-service-endpoint-configuration"></a>Vytvoření nové konfigurace koncového bodu služby  
 Můžete vytvořit novou konfiguraci koncového bodu služby následujícími způsoby:  
  
-   Vytvořit pomocí průvodce: klikněte na odkaz **vytvořit nový koncový bod služby...** v podokně úloh nebo na stránce Souhrn spusťte průvodce. Můžete také provést tak v **soubor** -> nabídky **přidat novou položku**.  
  
-   Ruční vytvoření: Po vytvoření služby, které můžete kliknout pravým tlačítkem **koncové body** uzel a zvolte "**nový koncový bod služby**".  
  
#### <a name="editing-a-service-configuration"></a>Úpravy konfigurace služby  
  
1.  Klikněte na tlačítko **služby** uzlu.  
  
2.  Upravte nastavení v mřížek vlastností.  
  
#### <a name="editing-a-service-endpoint-configuration"></a>Úpravy konfigurace koncového bodu služby  
  
1.  Klikněte na tlačítko **koncový bod služby** uzlu.  
  
2.  Upravte nastavení v mřížek vlastností.  
  
#### <a name="adding-a-base-address"></a>Přidání základní adresa  
  
1.  Klikněte **hostitele** uzlu.  
  
2.  Klikněte **nové...** tlačítko v **základní adresy** části.  
  
3.  Zadejte základní adresu identifikátoru URI v dialogovém okně.  
  
4.  Click **OK**.  
  
> [!NOTE]
>  Nelze upravit hodnotu [ \<baseAddressPrefixFilters >](../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md) uvnitř tohoto nástroje. Přidat nebo upravit tento element, měli byste použít textový editor nebo Visual Studio.  
  
### <a name="client"></a>Klient  
 **Klienta** uzlu zobrazí všechny koncové body klientů v konfiguračním souboru. Každý dílčí uzel ve stromové struktuře odpovídá dílčí element <`client`> element v konfiguračním souboru.  
  
 Když kliknete **klienta** uzlu, můžete zobrazit nebo provádět úlohy v klientovi **na stránce Souhrn** v **podokno Podrobnosti**.  
  
#### <a name="creating-a-new-client-endpoint-configuration"></a>Vytvoření nové konfigurace koncového bodu klienta  
 Můžete vytvořit novou konfiguraci koncového bodu klienta následujícími způsoby:  
  
-   Vytvořit pomocí průvodce: klikněte na odkaz **vytvořit nového klienta...** na **podokna úloh** vlevo dolní části okna, nebo **na stránce Souhrn** spusťte průvodce. Můžete také provést tak v **soubor** -> nabídky **přidat novou položku**. Průvodce vás vyzve k přejděte do umístění konfigurace služby, ze které se generuje konfigurace klienta. Potom můžete koncový bod služby pro připojení k.  
  
-   Ruční vytvoření: klikněte pravým tlačítkem myši **koncové body** pod uzlem **klienta**a zvolte **nový koncový bod klienta**.  
  
#### <a name="editing-a-client-endpoint-configuration"></a>Úpravy konfigurace koncového bodu klienta  
  
1.  Klikněte na tlačítko **klienta Endpoint** uzlu.  
  
2.  Upravte nastavení v mřížek vlastností.  
  
### <a name="standard-endpoint"></a>Standardní koncový bod  
 Standardní koncové body jsou specializované koncových bodů, které mají jednu nebo více aspektů adresu, kontrakt a vazba nastavit výchozí hodnoty.  
  
 Taková konfigurace nastavení jsou uložené v **standardní koncový bod** uzlu. **Standardní koncový bod** uzlu zobrazí všechna nastavení standardní koncového bodu v konfiguračním souboru. Každý dílčí uzel ve stromové struktuře odpovídá dílčí prvek, `<standardEndpoints>` element v konfiguračním souboru.  
  
 Po kliknutí **standardní koncový bod** uzlu, můžete zobrazit nebo provádět úlohy v koncovém bodě standardní **na stránce Souhrn** v **podokno Podrobnosti**.  
  
#### <a name="creating-a-new-standard-endpoint-configuration"></a>Vytvoření nové konfigurace standardní koncového bodu  
 Můžete vytvořit novou konfiguraci standardní koncový bod následujícími způsoby:  
  
-   Klikněte pravým tlačítkem myši **standardní koncový bod** uzel a vyberte možnost **nové standardní konfigurace koncového bodu...** Vyberte typ vazby v dialogovém okně a klikněte na **OK**.  
  
-   Vyberte **standardní koncový bod** uzel a klikněte na tlačítko **nové standardní konfigurace koncového bodu...** v **podokna úloh** vlevo dolní části okna.  
  
 **Vytvoření nového koncového bodu standardní** dialogové okno zobrazí a seznam všech registrovaných typy standardní koncových bodů.  
  
#### <a name="viewing-and-editing-a-standard-endpoint-configuration"></a>Prohlížení a úpravy konfigurace standardní koncového bodu  
 Můžete otevřít konfigurace standardní koncového bodu pro prohlížení a úpravy následujícími způsoby:  
  
-   Kliknutím rozbalte položku **standardní koncový bod** uzel a klikněte na uzel dílčí příslušného koncového bodu.  
  
-   Klikněte na tlačítko **standardní koncový bod** uzel a klikněte na příslušné koncový bod v podokně podrobností.  
  
 Atributy pro koncový bod se zobrazí v pravém podokně pro úpravy.  
  
#### <a name="deleting-a-standard-endpoint-configuration"></a>Odstraňuje se koncový bod standardní konfigurace  
 Konfigurace standardní koncového bodu můžete odstranit následujícími způsoby:  
  
-   Kliknutím rozbalte položku **standardní koncový bod** uzel a klikněte pravým tlačítkem na uzel dílčí příslušného koncového bodu. Použijte příkaz kontextu **odstranit standardní konfigurace koncového bodu** odstranit koncový bod.  
  
-   Klikněte **standardní koncový bod** uzlu. V **úloh** podokně klikněte na tlačítko **odstranit standardní konfigurace koncového bodu**.  
  
 Pokud se standardní koncový bod v používá, je při pokusu o odstranění se zobrazí zpráva s upozorněním: **standardní koncový bod je používán. Pokud je odstraníte nyní, prosím nezapomeňte odstranit všechny jeho odkazy v další části konfigurace (například v koncový bod služby nebo koncový bod klienta). Konfigurace, jinak budou neplatné a nelze otevřít další čas. Opravdu že chcete odstranit standardní koncový bod?"**  
  
### <a name="binding"></a>Vazba  
 Konfigurace vazeb se používají ke konfiguraci vazby u koncových bodů. Taková konfigurace nastavení jsou uložené v **vazby** uzlu. Koncové body-vazby konfigurace podle názvu a několik koncových bodů, můžete odkazovat konfigurace jedné vazby.  
  
 **Vazby** uzlu zobrazí všechna nastavení vazby v konfiguračním souboru. Každý dílčí uzel ve stromové struktuře odpovídá dílčí prvek, <`bindings`> element v konfiguračním souboru.  
  
 Když kliknete **vazby** uzlu, můžete zobrazit nebo provádět úlohy na vazby **na stránce Souhrn** v **podokno Podrobnosti**.  
  
#### <a name="creating-a-new-binding-configuration"></a>Vytvoření nové konfigurace vazeb  
 Následujícím způsobem můžete vytvořit novou konfiguraci vazby.  
  
-   Klikněte pravým tlačítkem myši **vazby** uzel a vyberte možnost **novou konfiguraci vazby**... Vyberte typ vazby v dialogovém okně a klikněte na **OK**.  
  
-   Vyberte **vazby** uzel a klikněte na tlačítko **novou konfiguraci vazby**... v **podokna úloh** vlevo dolní části okna.  
  
-   Na souhrnné stránce služba nebo klienta, klikněte na tlačítko **klikněte na tlačítko vytvořit** v **Konfigurace vazeb** pole pro vytvoření konfigurace vazeb pro odpovídající koncový bod.  
  
#### <a name="adding-binding-element-extensions-to-a-custom-binding"></a>Přidání rozšíření Element vytvoření vazby na vlastní vazby  
  
1.  Vyberte, chcete rozšíření prvek, který chcete přidat vazbu.  
  
2.  Klikněte na tlačítko **přidat**.  
  
3.  Ze seznamu dostupných rozšíření vyberte rozšíření element vazby, které chcete přidat. Pokud chcete vybrat více položek, stiskněte současně klávesu CTRL.  
  
4.  Klikněte na tlačítko **přidat**.  
  
#### <a name="adjusting-the-extension-position-in-a-custom-binding"></a>Úprava pozice rozšíření v vlastní vazby  
 Vlastní vazby je kolekce elementů, které vytvářejí zásobníku vazby. Každý prvek vazby v zásobníku má svou vlastní nastavení konfigurace. Pořadí rozšíření element vazby na vlastní vazby označuje jejich pozice v zásobníku. Elementy v horní části zásobníku se použije první. Chcete-li změnit pořadí:  
  
1.  Vyberte uzel vlastní vazby.  
  
2.  Vyberte jeden element rozšíření vazby ve **pozice rozšíření elementu vazby** části.  
  
3.  Použití **až** nebo **dolů** na levé straně seznamu můžete změnit umístění vybraného prvku tlačítko.  
  
#### <a name="editing-the-configuration-of-binding-element-extensions-in-a-custom-binding"></a>Úpravy konfigurace vazby Element rozšíření ve vlastní vazby  
  
1.  Vyberte vazbu uzel ve stromové struktuře.  
  
2.  Vyberte vlastní vazby, který obsahuje element, který chcete upravit.  
  
3.  Vyberte rozšíření element vazby, kterou chcete upravit. Nastavení elementu se zobrazí v pravém podokně, kde můžete upravit.  
  
### <a name="diagnostics"></a>Diagnostika  
 **Diagnostiky** uzlu zobrazí všechna nastavení pro diagnostiku v konfiguračním souboru. Umožňuje zapnout čítače výkonu nebo vypnout, povolení nebo zakázání služby Windows Management Instrumentation (WMI), konfigurovat trasování WCF a konfigurace protokolování zpráv WCF. Nastavení v **diagnostiky** uzlu odpovídají <`system.diagnostics`> části a `<diagnostics>` kapitoly `<system.serviceModel>` v konfiguračním souboru.  
  
 Když kliknete **diagnostiky** uzlu, můžete zobrazit nebo provádět úlohy v zobrazení diagnostické **na stránce Souhrn** v **podokno Podrobnosti**.  
  
#### <a name="configuring-performance-counters-and-wmi"></a>Konfigurace rozhraní WMI a čítače výkonu  
  
1.  Klikněte **diagnostiky** uzlu.  
  
2.  Klikněte na tlačítko **přepnutí čítače výkonu**. Čítače výkonu má tři stavy: Off (výchozí), ServiceOnly a všechny. Kliknutím na odkaz přepne nastavení mezi tyto tři stavy.  
  
#### <a name="configuring-wmi-provider"></a>Konfigurace zprostředkovatele rozhraní WMI  
  
1.  Klikněte **diagnostiky** uzlu.  
  
2.  Chcete-li povolit zprostředkovatele rozhraní WMI, klikněte na tlačítko **povolit zprostředkovatele rozhraní WMI** odkaz.  
  
#### <a name="enabling-wcf-tracing"></a>Povolení trasování WCF  
 Můžete vytvořit soubor trasování WCF s standardní vlastnosti nebo nastavit vlastní trasovací soubor.  
  
1.  Klikněte **diagnostiky** uzlu.  
  
2.  Klikněte na tlačítko **povolit trasování**.  
  
3.  Klikněte **úroveň trasování** odkaz upravit úroveň trasování. Existují šesti úrovně trasování: vypnuté, kritická, chyba, upozornění, informace a podrobné. **Trasování aktivit** a **rozšířit aktivity** možnost umožňují používat funkce trasování aktivity WCF.  
  
4.  Klikněte na název naslouchacího procesu trasování určete trasovacího souboru a možnosti.  
  
#### <a name="enabling-wcf-logging"></a>Povolení protokolování WCF  
 Můžete vytvořit soubor trasování WCF s standardní vlastnosti nebo nastavit vlastní trasovací soubor.  
  
1.  Klikněte **diagnostiky** uzlu.  
  
2.  Klikněte na tlačítko **povolit protokolování zpráv**.  
  
3.  Klikněte **úroveň protokolu** odkaz upravit úroveň protokolu. Existují tři úrovně protokolování: chybná, služby a přenosu.  
  
4.  Klikněte na název naslouchacího procesu určete soubor protokolu a možnosti.  
  
> [!NOTE]
>  Pokud chcete, aby v protokolech trasování a zpráva, aby povolte vyprázdněním automaticky při zavření aplikace **automaticky vyprázdní** možnost.  
  
 **Diagnostiky** **na stránce Souhrn** možné provádět běžné úkoly při konfiguraci diagnostiky. Ale pokud chcete ručně upravit nastavení naslouchací procesy a zdrojů, je třeba rozbalit **diagnostiky** uzel a upravit nastavení v **protokolování zpráv**, **naslouchací procesy** a **Zdroje** uzlu.  
  
#### <a name="enabling-wcf-custom-tracing-or-message-logging"></a>Povolení trasování WCF vlastní nebo protokolování zpráv  
  
1.  Klikněte **diagnostiky** uzel a rozbalte ho.  
  
2.  Klikněte pravým tlačítkem myši **naslouchací procesy** uzel a vyberte možnost **nový**.  
  
3.  Zadejte název trasovacího souboru v **InitData** pole. Kliknutím na tlačítko "..." a přejděte na cestu.  
  
4.  Kliknutím **TypeName** řádek zobrazí tlačítko "...". Kliknutím na toto tlačítko otevřete **prohlížeče typ naslouchací proces trasování**, který můžete použít k vyhledání trasování předkonfigurovaný naslouchací procesy, které jsou již nainstalovány.  
  
5.  Poznámka: **zdroj** části. Klikněte na tlačítko **přidat** v této části otevřete dialogové okno s rozevírací nabídce, která obsahuje seznam zdrojů k dispozici trasování. Vyberte zdroj trasování a klikněte na tlačítko **OK**.  
  
6.  Upravit nastavení protokolování zpráv, klikněte **protokolování zpráv** uzlu. Můžete upravit nastavení, v tabulce vlastností.  
  
### <a name="advanced"></a>Upřesnit  
  
#### <a name="behaviors"></a>Chování  
 **Chování** uzlu zobrazí chování, které jsou aktuálně definována v konfiguračním souboru.  
  
 Konfigurace chování se používají ke konfiguraci chování koncových bodů a služeb. Taková konfigurace nastavení jsou uložené v **Upřesnit** pod uzlem **chování služby** a **koncový bod chování**. Chování služby jsou používané službami; zatímco chování koncový bod pomocí koncových bodů.  
  
 Chování jsou kolekce elementy rozšíření, pro zásobníku. Element v horní části zásobníku se použije první. Každý prvek rozšíření může mít svůj vlastní konfigurace.  
  
##### <a name="creating-a-new-behavior-configuration"></a>Vytvoření nové konfigurace chování  
 Nová konfigurace chování můžete vytvořit dvěma způsoby.  
  
-   Klikněte pravým tlačítkem na jednom z uzlů chování a vyberte "**novou konfiguraci chování...**  
  
-   Vyberte jeden z uzlů chování a klikněte na **novou konfiguraci chování**... v **podokna úloh** vlevo dolní části okna.  
  
##### <a name="adding-behavior-element-extensions-to-a-behavior"></a>Přidání rozšíření Element chování chování  
  
1.  Vyberte jeden z uzlů chování.  
  
2.  Vyberte chování, které chcete upravit.  
  
3.  Klikněte na tlačítko **přidat**.  
  
4.  Ze seznamu dostupných rozšíření vyberte rozšíření element chování, které chcete přidat.  
  
5.  Klikněte na tlačítko **přidat**.  
  
##### <a name="adjusting-the-extension-position-in-a-behavior"></a>Úprava pozice rozšíření v chování  
 Chování jsou kolekce elementů, které vytvářejí zásobníku. Každý prvek v zásobníku má svou vlastní konfiguraci. Pořadí rozšíření element chování v chování označuje jejich pozice v zásobníku. Elementy v horní části zásobníku se použije první. Chcete-li změnit pořadí:  
  
1.  Vyberte jeden z uzlů chování.  
  
2.  Vyberte chování, které chcete upravit.  
  
3.  Vyberte chování rozšíření prvek, **pozice rozšíření elementu chování** části.  
  
4.  Použití **až** nebo **dolů** na levé straně seznamu můžete změnit umístění vybraného prvku tlačítko.  
  
##### <a name="editing-the-configuration-of-behavior-element-extensions"></a>Úpravy konfigurace chování Element rozšíření  
  
1.  Vyberte jeden z uzlů chování ve stromové struktuře.  
  
2.  Vyberte chování, který obsahuje element, který chcete upravit.  
  
3.  Vyberte požadované rozšíření element chování, které chcete upravit. Nastavení elementu se zobrazí v pravém podokně, kde můžete upravit.  
  
#### <a name="protocolmapping"></a>ProtocolMapping  
 V této části můžete nastavit výchozí typ vazby pro jiné protokoly, jako je například http, tcp, služby MSMQ nebo net.pipe prostřednictvím definované mapování mezi protokol adresu schémata a možné vazby. Můžete také přidat nové mapování pro jiné protokoly.  
  
#### <a name="extensions"></a>Rozšíření  
 Nová rozšíření vazby, vazba element rozšíření rozšíření standardní koncový bod a chování rozšíření se dají registrovat pro použití v konfiguraci WCF. Rozšíření jsou páry název/typu. Název definuje název rozšíření v konfiguraci, zatímco typ implementuje rozšíření. Existují čtyři typy rozšíření:  
  
-   Vazba rozšíření definovat typ celý vazby. Příklad: `basicHttpBinding`.  
  
-   Vazba element rozšíření definovat element vazby. Příklad: `textMessageEncoding`.  
  
-   Standardní koncový bod rozšíření definovat celý standardní koncový bod. Příklad: `discoveryEndpoint`.  
  
-   Chování element rozšíření definovat element chování. Příklad: `clientVia`.  
  
 Rozšíření, které byly zaregistrovány v konfiguraci můžete použít jako jakoukoli jinou součástí WCF stejného typu.  
  
##### <a name="adding-a-new-extension"></a>Přidání nové rozšíření  
 Vyberte jeden z uzlů rozšíření v pokročilé uzly:  
  
1.  Klikněte na tlačítko **nové**.  
  
2.  Zadejte název a typ.  
  
3.  Click **OK**.  
  
4.  Rozšíření se teď zobrazí na příslušné místo v editoru. Například pokud přidáte příponu element chování, zobrazí se v seznamu dostupných rozšíření.  
  
#### <a name="hosting-environment"></a>Hostování prostředí  
 V této části můžete zadat nastavení vytváření instancí služby hostování prostředí.  
  
### <a name="creating-a-configuration-file-using-the-wizard"></a>Vytvoření konfiguračního souboru pomocí Průvodce  
 Jeden způsob, jak vytvořit nový soubor konfigurace je pomocí Průvodce vytvořením Element služby. Průvodce vyhledá typů nainstalovaných služeb a další prvky kompatibilní s použitím technologie WCF v počítači, včetně modelu COM + a Web hostovaný virtuální adresáře a načte je, aby vytváření konfigurace mnohem víc zjednodušený.  
  
#### <a name="creating-a-configuration-file"></a>Vytvoření konfiguračního souboru  
  
1.  Spusťte Editor konfigurací služby pomocí okno příkazového řádku přejděte do umístění instalace WCF a pak zadejte `SvcConfigEditor.exe`.  
  
2.  Z **soubor** nabídce vyberte možnost **otevřete** a klikněte na tlačítko **spustitelný soubor**, **služby COM +**, nebo **WebHosted služby**, v závislosti na typu konfigurační soubor, který chcete vytvořit.  
  
3.  V **otevřete** dialogové okno pole, přejděte na konkrétní soubor, který chcete vytvořit konfigurační soubor pro a poklikejte na něj.  
  
4.  V **soubor** nabídky, přejděte na příkaz **přidat novou položku** a klikněte na tlačítko **služby**. Otevře se Průvodce vytvořením Element služby.  
  
5.  Postupujte podle kroků v průvodci vytvořit novou službu.  
  
> [!NOTE]
>  Pokud chcete použít NetPeerTcpBinding z konfiguračního souboru je vygenerovat průvodcem, budete muset ručně přidejte element konfigurace vazby a upravit `mode` atribut jeho `security` element "Žádný".  
  
## <a name="configuring-com"></a>Konfigurace modelu COM +  
 Editor konfigurací služby vám umožní vytvořit nový soubor konfigurace pro existující aplikace modelu COM +, nebo upravit existující konfigurace modelu COM +. **COM kontrakt** uzel se zobrazí, když <`comContract`> oddíl existuje v konfiguračním souboru.  
  
### <a name="creating-a-new-com-configuration"></a>Vytvoření nové konfigurace modelu COM +  
 Před vytvořením novou konfiguraci modelu COM +, ujistěte se, že vaše aplikace modelu COM + nainstalovaná v Služba komponent a zaregistrován v globální mezipaměti sestavení (GAC).  
  
1.  Vyberte **soubor** -> nabídky **integrací** -> **aplikace modelu COM +.** Tato operace zavře aktuální otevřený soubor. Pokud existuje je neuložená data v aktuálním souboru, zobrazí se dialogové okno Uložit. **Průvodce integračním modelu COM +** se pak spustí.  
  
2.  Na první stránce vyberte ve stromu aplikace modelu COM +. Pokud vaše aplikace modelu COM + nemůže najít ve stromu, ověřte, zda je nainstalována v služby komponent a zaregistrován v globální mezipaměti sestavení (GAC).  
  
3.  Na další stránce vyberte, které metody, kterou chcete vystavit jako služby WCF. Všechny podporované metody v aplikace modelu COM + se zobrazují a ve výchozím nastavení zaškrtnuto.  
  
4.  Zvolte hostitelský metodu.  
  
5.  V Průvodci nakonfigurujte další nastavení podle vodítka.  
  
6.  Editor konfigurací služby využívá ComSvcConfig.exe na pozadí pro generování konfigurační soubor. Po dokončení této, můžete zobrazit souhrn a ukončete průvodce. Vygenerovaný konfigurační soubor je otevřené, aby se dají upravovat přímo.  
  
### <a name="editing-an-existing-com-configuration"></a>Úprava existující konfigurace modelu COM +  
  
1.  Vyberte **soubor** -> nabídky **otevřete** -> **služby COM +**...  
  
2.  Vyberte modelu COM + službu, kterou chcete upravit ze seznamu.  
  
3.  Upravit nastavení konfigurace v **kontrakty COM** uzlu.  
  
    > [!NOTE]
    >  Můžete také přímo otevřít a upravit konfigurační soubor, který obsahuje kontrakty COM.  
  
## <a name="security"></a>Zabezpečení  
 Konfigurační soubor služby generované Editor konfigurací není zaručena bezpečnost pro zabezpečené. Podrobnosti najdete [zabezpečení](../../../docs/framework/wcf/feature-details/security.md) dokumentaci a zjistěte, jak zabezpečit služby WCF.  
  
 Kromě toho můžete Editor konfigurací použít pouze ke čtení a zápisu platný WCF konfigurace – elementy. Nástroj ignoruje kompatibilní se standardem schématu, uživatelsky definované prvky. Také nepokusí odeberte tyto prvky z konfigurace souboru nebo určit jejich dopadu na známé prvky WCF. Je zodpovědností uživatele k určení, zda tyto prvky představovat hrozbu pro aplikace nebo systému.
