---
title: Nástroj Configuration Editor (SvcConfigEditor.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- configuration files, creating
- configuration files
- Configuration file
- configuration file schema
ms.assetid: 2db21a57-5f64-426f-89df-fb0dc2d2def5
ms.openlocfilehash: e2b28ae65c7c5769f3be5c294fc3667b5ba4a651
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64652128"
---
# <a name="configuration-editor-tool-svcconfigeditorexe"></a>Nástroj Configuration Editor (SvcConfigEditor.exe)
Windows Communication Foundation (WCF) Service Configuration Editor (SvcConfigEditor.exe) umožňuje správcům a vývojářům umožňuje vytvářet a upravovat nastavení konfigurace pro služby WCF pomocí grafického uživatelského rozhraní. Pomocí tohoto nástroje můžete spravovat nastavení pro vazby WCF, chování, služby a diagnostické nástroje bez nutnosti přímo upravit konfigurační soubory XML.  
  
 Editor konfigurace služby najdete ve složce C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin.  
  
## <a name="the-wcf-configuration-editor"></a>Editor konfigurace WCF  
 Editor konfigurace služby obsahuje průvodce, který vás provede všemi kroky při konfiguraci klienta a služby WCF. Důrazně doporučujeme použít Průvodce místo editoru přímo.  
  
 Pokud už máte některé konfigurační soubory, které splňují standard System.Configuration schématu, můžete spravovat specifická nastavení pro vazby, chování, služby a diagnostické nástroje s uživatelským rozhraním. Editor konfigurace služby umožňuje spravovat nastavení pro existující konfiguračních souborů WCF i spustitelné soubory, služby COM + a hostované webové služby. Při otevírání hostované webové služby s Editor konfigurace služby, jak službu pro vlastní konfiguraci a zděděné konfigurace oddílů horní úrovni uzly se zobrazí.  
  
 Protože nastavení konfigurace WCF najdete v `<system.serviceModel>` oddílu konfiguračního souboru, editoru funguje výhradně na obsah tohoto prvku a další prvky ve stejném souboru nepřistupuje. Můžete přejít na stávající konfigurační soubory přímo, nebo můžete vybrat sestavení, který obsahuje služby, virtuální adresář nebo služby COM +. Editor načte konfigurační soubor pro tento konkrétní službu a umožní uživateli přidat nové prvky nebo upravte stávající prvky, které jsou vnořené v `<system.serviceModel>` oddílu konfiguračního souboru.  
  
 Editor podporuje technologii IntelliSense a vynucuje dodržování předpisů schématu. Výsledný výstup je zaručeno, že pro dosažení souladu s schéma konfiguračního souboru a hodnoty syntakticky správná data. Editor však nezaručuje, že je konfigurační soubor sémanticky platný. Jinými slovy editoru nezaručuje, že konfigurační soubor může pracovat se službou, kterou nakonfiguruje.  
  
> [!CAUTION]
>  Editor nelze vymazat prvek konfigurace, z konfiguračního souboru, jakmile upravíte elementu. Například pokud chcete nastavit název koncového bodu na neprázdný řetězec a uložit ho používáte editoru, konfigurační soubor má následující obsah, jak je znázorněno v následujícím příkladu.  
>   
>  `<endpoint binding="basicHttpBinding" name="somename" />`  
>   
>  Při pokusu o odebrání názvy oddělte ji nastavíte na prázdný řetězec a ukládání souborů, nadále konfigurační soubor obsahuje `name` atributu, jak je znázorněno v následujícím příkladu.  
>   
>  `<endpoint binding="basicHttpBinding" name="" />`  
>   
>  Vymazání atribut, musíte ručně upravit element pomocí jiného textového editoru.  
>   
>  Měli byste být opatrní hlavně s tímto problémem, při použití `issueToken` elementu `clientCredential` chování koncového bodu. Konkrétně `address` atribut jeho `localIssuer` dílčí element nesmí být prázdný řetězec. Pokud jste změnili `address` atribut, pomocí editoru konfigurace a chcete ho úplně odeberte, proveďte to pomocí nástroje, kromě editoru. V opačném případě atribut obsahuje prázdný řetězec a vyvolá výjimku, vaše aplikace.  
  
## <a name="using-the-configuration-editor"></a>Pomocí editoru konfigurace  
 Editor konfigurace služby najdete v následujícím umístění instalace sady Windows SDK:  
  
 C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin\SvcConfigEditor.exe  
  
 Po spuštění Editor konfigurace služby, můžete použít **otevřít** nabídky procházení pro službu nebo sestavení, které chcete spravovat. Můžete otevřít konfigurační soubory přímo, procházet WCF /COM+ services a otevřete konfigurační soubory pro hostované webové služby.  
  
 Editor konfigurace služby uživatelské rozhraní je rozdělen do následujících oblastí:  
  
- Podokně se stromovým zobrazením, která zobrazuje konfigurační prvky ve stromové struktuře na levé straně. Ve stromové struktuře můžete provádět operace, kliknutím pravým tlačítkem myši uzly.  
  
- Podokna úloh, kde se zobrazují běžné úlohy pro aktuální prvky v levém dolním rohu okna  
  
- Podokno Podrobnosti, které zobrazí podrobné informace o nastavení konfigurace uzlu vybraném v zobrazení stromu na pravé straně.  
  
### <a name="opening-a-configuration-file"></a>Otevřete konfigurační soubor  
  
1. Spustit Service Configuration Editor pomocí příkazové okno a přejděte do umístění instalace WCF a pak zadejte `SvcConfigEditor.exe`.  
  
2. Z **souboru** nabídce vyberte možnost **otevřít** a klikněte na typ souboru, kterou chcete spravovat.  
  
3. V **otevřít** dialogové okno, přejděte na konkrétní soubor, který chcete spravovat a dvojím kliknutím ho.  
  
 Prohlížeč automaticky sleduje cestu sloučení konfigurace a vytvoří zobrazení sloučené konfigurace. Například Skutečná konfigurace jiné hostované služby je kombinací Machine.config a App.config. Všechny změny se použijí na aktivní soubor v editoru konfigurace služby. Pokud chcete upravit konkrétní soubor v cestě konfigurace sloučení, měli byste ho otevřít přímo.  
  
> [!NOTE]
>  Editor konfigurace znovu načte aktuálně otevřeném konfiguračním souboru, pokud druhá možnost byl změněn mimo Editor. Pokud k tomu dojde, budou ztraceny všechny změny, které nejsou trvale uložené v editoru. Pokud znovu načíst konzistentně dojde, nejpravděpodobnější příčinou je služba, která neustále přistupuje ke konfiguračním souboru, například antivirový software spuštěný na pozadí. Chcete-li tento problém vyřešit, zajistěte, aby byl Editor konfigurací jediný proces, který můžete získat přístup k souboru, když je otevřen.  
  
### <a name="services"></a>Služby  
 **Služby** uzel zobrazuje všechny aktuálně přiřazené v konfiguračním souboru služby. Každý dílčí uzel ve stromu odpovídá dílčí element <`services`> element v konfiguračním souboru.  
  
 Po kliknutí na **služby** uzlu, můžete zobrazit nebo provádět úkoly ve službě souhrn stránku **podrobností** podokně.  
  
#### <a name="creating-a-new-service-configuration"></a>Vytvořit novou konfiguraci služby  
 Můžete vytvořit novou konfiguraci služby následujícími způsoby:  
  
- Pomocí průvodce: Klikněte na odkaz **vytvořit novou službu...** Podokno úloh nebo stránka Souhrn spusťte průvodce. Můžete také provést, **souboru** nabídka -> **přidat novou položku**.  
  
- Ruční vytvoření: Můžete kliknout pravým tlačítkem **služby** uzlu a zvolte **novou službu**.  
  
#### <a name="creating-a-new-service-endpoint-configuration"></a>Vytváří se nová konfigurace koncového bodu služby  
 Můžete vytvořit nové konfigurace koncového bodu služby následujícími způsoby:  
  
- Vytvoření s použitím průvodce: klikněte na odkaz **vytvořit nový koncový bod služby...** Podokno úloh nebo stránka Souhrn spusťte průvodce. Můžete také provést, **souboru** nabídka -> **přidat novou položku**.  
  
- Ruční vytvoření: Po vytvoření služby kliknete pravým tlačítkem **koncové body** uzlu a zvolte možnost "**nový koncový bod služby**".  
  
#### <a name="editing-a-service-configuration"></a>Úprava konfigurace služby  
  
1. Klikněte na tlačítko **služby** uzlu.  
  
2. Upravte nastavení podle mřížek vlastností.  
  
#### <a name="editing-a-service-endpoint-configuration"></a>Úprava konfigurace koncového bodu služby  
  
1. Klikněte na tlačítko **koncový bod služby** uzlu.  
  
2. Upravte nastavení podle mřížek vlastností.  
  
#### <a name="adding-a-base-address"></a>Přidat základní adresu  
  
1. Klikněte na tlačítko **hostitele** uzlu.  
  
2. Klikněte na tlačítko **nové...** tlačítko **základní adresy** oddílu.  
  
3. Zadejte základní adresu identifikátoru URI v dialogovém okně.  
  
4. Klikněte na **OK**.  
  
> [!NOTE]
>  Nelze upravit hodnotu daného [ \<baseAddressPrefixFilters >](../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md) uvnitř tohoto nástroje. Přidat nebo upravit tento element, abyste používali textového editoru nebo sadě Visual Studio.  
  
### <a name="client"></a>Klient  
 **Klienta** uzel se zobrazí všechny koncové body klienta v konfiguračním souboru. Každý dílčí uzel ve stromu odpovídá dílčí element <`client`> element v konfiguračním souboru.  
  
 Po kliknutí **klienta** uzlu, můžete zobrazit nebo provádění úloh na straně klienta **stránka Souhrn** v **podokno Podrobnosti**.  
  
#### <a name="creating-a-new-client-endpoint-configuration"></a>Vytvoření nového koncového bodu konfigurace klienta  
 Můžete vytvořit novou konfiguraci koncových bodů klienta následujícími způsoby:  
  
- Vytvořte pomocí průvodce: Klikněte na odkaz **vytvořit nového klienta...** na **podokna úloh** na levém okraji okna, nebo **stránka Souhrn** spusťte průvodce. Můžete také provést, **souboru** nabídka -> **přidat novou položku**. Průvodce vás vyzve, abyste odkazovalo na umístění konfigurace služby, ze kterého se vygeneruje konfigurace klienta. Zvolte koncový bod služby pro připojení k.  
  
- Ruční vytvoření: Klikněte pravým tlačítkem myši **koncové body** pod uzlem **klienta**a zvolte **nový koncový bod klienta**.  
  
#### <a name="editing-a-client-endpoint-configuration"></a>Úprava konfigurace koncový bod klienta  
  
1. Klikněte na tlačítko **koncový bod klienta** uzlu.  
  
2. Upravte nastavení podle mřížek vlastností.  
  
### <a name="standard-endpoint"></a>Standardní koncový bod  
 Standardní koncové body jsou specializované koncové body, které mají jednu nebo více aspektů adresu, kontrakt a vazby nastavené na výchozí hodnoty.  
  
 Tyto konfigurační nastavení jsou uložena v **standardní koncový bod** uzlu. **Standardní koncový bod** uzel zobrazuje všechna nastavení standardní koncový bod v konfiguračním souboru. Odpovídá dílčí element v každé podřízený uzel ve stromu `<standardEndpoints>` element v konfiguračním souboru.  
  
 Po kliknutí **standardní koncový bod** uzlu, můžete zobrazit nebo provádět úlohy pro standardní koncový bod **stránka Souhrn** v **podokno Podrobnosti**.  
  
#### <a name="creating-a-new-standard-endpoint-configuration"></a>Vytváří se nová konfigurace standardní koncový bod  
 Můžete vytvořit novou konfiguraci standardní koncový bod následujícími způsoby:  
  
- Klikněte pravým tlačítkem myši **standardní koncový bod** uzel a vyberte možnost **nový standardní konfigurace koncového bodu...** V dialogovém okně vyberte typ vazby a klikněte na tlačítko **OK**.  
  
- Vyberte **standardní koncový bod** uzel a klikněte na tlačítko **nový standardní konfigurace koncového bodu...** v **podokna úloh** v levém dolním rohu okna.  
  
 **Vytváří se nový standardní koncový bod** dialogové okno zobrazí a zobrazí seznam všech registrovaných typů standardní koncový bod.  
  
#### <a name="viewing-and-editing-a-standard-endpoint-configuration"></a>Prohlížení a úpravy konfigurace standardního koncového bodu  
 Můžete otevřít konfiguraci standardní koncový bod pro prohlížení a úpravy následujícími způsoby:  
  
- Rozbalte kliknutím **standardní koncový bod** uzel a klikněte na uzel dílčí příslušný koncový bod.  
  
- Klikněte na tlačítko **standardní koncový bod** uzel a klikněte na příslušný koncový bod v podokně podrobností.  
  
 Atributy pro koncový bod se zobrazí v pravém podokně pro úpravy.  
  
#### <a name="deleting-a-standard-endpoint-configuration"></a>Odstraňuje se konfigurace standardní koncový bod  
 Standardní koncový bod konfigurace můžete odstranit následujícím způsobem:  
  
- Rozbalte kliknutím **standardní koncový bod** uzel a klikněte pravým tlačítkem na uzel dílčí příslušný koncový bod. Pomocí příkazu kontextové **odstranit standardní konfigurace koncového bodu** odstranit koncový bod.  
  
- Klikněte na tlačítko **standardní koncový bod** uzlu. V **úloh** podokně klikněte na tlačítko **odstranit standardní konfigurace koncového bodu**.  
  
 Pokud standardní koncový bod v používá, zobrazí se zpráva upozornění při pokusu odstranit: **Standardní koncový bod se používá. Pokud je odstraníte nyní, nezapomeňte odstranit všechny jeho odkazy v ostatních částech konfigurace (například v koncový bod služby nebo koncový bod klienta). Konfigurace v opačném případě budou neplatné a nelze otevřít další čas. Opravdu že chcete odstranit koncový bod standard?"**  
  
### <a name="binding"></a>Vazba  
 Konfigurace vazby se používají ke konfiguraci vazby na koncové body. Tyto konfigurační nastavení jsou uložena v **vazby** uzlu. Koncové body odkazovat konfiguracemi vazeb podle názvu a několik koncových bodů můžete odkazovat na jedné vazby konfigurace.  
  
 **Vazby** uzel zobrazuje všechna nastavení vazby v konfiguračním souboru. Odpovídá dílčí element v každé podřízený uzel ve stromu <`bindings`> element v konfiguračním souboru.  
  
 Po kliknutí **vazby** uzlu, můžete zobrazit nebo provádět úlohy v rámci vazby **stránka Souhrn** v **podokno Podrobnosti**.  
  
#### <a name="creating-a-new-binding-configuration"></a>Vytváří se nová konfigurace vazby  
 Takto můžete vytvořit novou konfiguraci vazby.  
  
- Klikněte pravým tlačítkem myši **vazby** uzel a vyberte možnost **novou konfiguraci vazby**... V dialogovém okně vyberte typ vazby a klikněte na tlačítko **OK**.  
  
- Vyberte **vazby** uzel a klikněte na tlačítko **novou konfiguraci vazby**... v **podokna úloh** v levém dolním rohu okna.  
  
- Služba nebo klient na stránce shrnutí, klikněte na tlačítko **klikněte na vytvořit** v **konfigurace vazby** pole, které chcete vytvořit konfiguraci vazby pro odpovídající koncový bod.  
  
#### <a name="adding-binding-element-extensions-to-a-custom-binding"></a>Přidání rozšíření elementu vazby k vlastní vazby  
  
1. Vyberte vazby, které chcete přidat element rozšíření.  
  
2. Klikněte na **Přidat**.  
  
3. Seznam dostupných rozšíření vyberte rozšíření elementu vazby, které chcete přidat. Vybrat více položek, stiskněte současně klávesu CTRL.  
  
4. Klikněte na **Přidat**.  
  
#### <a name="adjusting-the-extension-position-in-a-custom-binding"></a>Nastavení pozice rozšíření ve vlastní vazby  
 Vlastní vazby je kolekce elementů, které tvoří zásobníku vazby. Každý prvek vazby v zásobníku má svůj vlastní nastavení konfigurace. Pořadí rozšíření elementu vazby ve vlastní vazbu určuje pozice v zásobníku. Nejprve se použijí prvků v horní části zásobníku. Chcete-li změnit pořadí:  
  
1. Vyberte uzel pro vlastní vazbu.  
  
2. Vyberte jeden prvek rozšíření vazby **pozice rozšíření elementu vazby** oddílu.  
  
3. Použití **nahoru** nebo **dolů** na levé straně seznamu změní pozici vybraného prvku.  
  
#### <a name="editing-the-configuration-of-binding-element-extensions-in-a-custom-binding"></a>Úpravy konfigurace rozšíření elementu vazby ve vlastní vazby  
  
1. Vyberte uzel vazby ve stromové struktuře.  
  
2. Vyberte vlastní vazby, který obsahuje prvek, na který chcete upravit.  
  
3. Vyberte rozšíření elementu vazby, kterou chcete upravit. Nastavení elementu, který se zobrazí v pravém podokně, kde lze upravovat.  
  
### <a name="diagnostics"></a>Diagnostika  
 **Diagnostiky** uzel zobrazí všechna nastavení diagnostiky v konfiguračním souboru. Umožňuje vypnout nebo zapnout čítače výkonu, povolení nebo zakázání služby Windows Management Instrumentation (WMI), konfigurace trasování WCF a konfigurace protokolování zpráv WCF. Nastavení v **diagnostiky** uzel odpovídají <`system.diagnostics`> části, a `<diagnostics>` tématu `<system.serviceModel>` v konfiguračním souboru.  
  
 Po kliknutí na **diagnostiky** uzlu, můžete zobrazit nebo provádět úlohy v diagnostice **stránka Souhrn** v **podokno Podrobnosti**.  
  
#### <a name="configuring-performance-counters-and-wmi"></a>Konfiguraci čítačů výkonu a WMI  
  
1. Klikněte na tlačítko **diagnostiky** uzlu.  
  
2. Klikněte na tlačítko **přepnout čítače výkonu**. Čítače výkonu má tři stavy: Vypnuto (výchozí) ServiceOnly a všechny. Kliknutím na odkaz přepíná nastavení mezi tyto tři stavy.  
  
#### <a name="configuring-wmi-provider"></a>Konfigurace poskytovatele rozhraní WMI  
  
1. Klikněte na tlačítko **diagnostiky** uzlu.  
  
2. Chcete-li povolit zprostředkovatele rozhraní WMI, klikněte na tlačítko **povolit zprostředkovatele rozhraní WMI** odkaz.  
  
#### <a name="enabling-wcf-tracing"></a>Povolení trasování WCF  
 Můžete vytvořit soubor trasování WCF se standardní vlastnosti nebo nastavit vlastní trasovací soubor.  
  
1. Klikněte na tlačítko **diagnostiky** uzlu.  
  
2. Klikněte na tlačítko **povolit trasování**.  
  
3. Klikněte na tlačítko **úroveň trasování** odkaz upravit úroveň trasování. Existuje šest úrovní trasování: Vypnuto, kritické, chyba, upozornění, informace a podrobné. **Trasování činnosti** a **šíření činnosti** možnost umožňují používat funkce trasování WCF aktivity.  
  
4. Klikněte na název naslouchacího procesu trasování pro trasovacího souboru a možnosti určit.  
  
#### <a name="enabling-wcf-logging"></a>Povolení protokolování WCF  
 Můžete vytvořit soubor trasování WCF se standardní vlastnosti nebo nastavit vlastní trasovací soubor.  
  
1. Klikněte na tlačítko **diagnostiky** uzlu.  
  
2. Klikněte na tlačítko **povolilo protokolování zpráv**.  
  
3. Klikněte na tlačítko **úroveň protokolu** odkaz upravit úroveň protokolu. Existují tři úrovně protokolu: Chybný formát, služby a přenosu.  
  
4. Klikněte na název naslouchacího procesu určete soubor protokolu a možnosti.  
  
> [!NOTE]
>  Pokud chcete, aby protokoly trasování a zpráv a automaticky vyprázdní při zavření aplikace, povolte **automaticky vyprázdní** možnost.  
  
 **Diagnostiky** **stránka Souhrn** umožňuje provádět běžné úkoly v konfiguraci diagnostiky. Nicméně, pokud chcete ručně upravit nastavení naslouchacích procesů a zdrojů, je třeba rozbalit **diagnostiky** uzlu a upravit nastavení v **protokolování zpráv**, **naslouchacích procesů** a **Zdroje** uzlu.  
  
#### <a name="enabling-wcf-custom-tracing-or-message-logging"></a>Povolení trasování WCF vlastní nebo protokolování zpráv  
  
1. Klikněte na tlačítko **diagnostiky** uzel a rozbalte ho.  
  
2. Klikněte pravým tlačítkem myši **naslouchacích procesů** uzel a vyberte možnost **nový naslouchací proces**.  
  
3. Zadejte název souboru trasování **InitData** pole. Kliknutím "..." tlačítko vyhledat cestu.  
  
4. Kliknutím **TypeName** řádku zobrazí "..." tlačítko. Kliknutím na toto tlačítko otevřete **prohlížeč typů naslouchací proces trasování**, který můžete použít k vyhledání naslouchacími procesy trasování předem nakonfigurované, které jsou již nainstalovány.  
  
5. Poznámka: **zdroj** oddílu. Klikněte na tlačítko **přidat** v této části pro otevření dialogového okna s rozevírací nabídkou Vypíše seznam dostupných trasování zdrojů. Vyberte zdroj trasování a klikněte na tlačítko **OK**.  
  
6. Chcete-li upravit nastavení protokolování zpráv, klikněte na tlačítko **protokolování zpráv** uzlu. Můžete upravit nastavení v mřížce vlastností.  
  
### <a name="advanced"></a>Upřesnit  
  
#### <a name="behaviors"></a>Chování  
 **Chování** uzel zobrazuje chování, které jsou definovány v konfiguračním souboru.  
  
 Konfigurace chování slouží ke konfiguraci chování koncových bodů a služeb. Tyto konfigurační nastavení jsou uložena v **Upřesnit** pod uzlem **chování služby** a **chování koncového bodu**. Chování služby jsou používány služeb; vzhledem k tomu chování koncového bodu pomocí koncových bodů.  
  
 Chování jsou kolekce elementů rozšíření, která pro zásobník. Element v horní části zásobníku se použije první. Každý prvek rozšíření může mít svůj vlastní konfigurace.  
  
##### <a name="creating-a-new-behavior-configuration"></a>Vytváří se nová konfigurace chování  
 Nová konfigurace chování lze vytvořit dvěma způsoby.  
  
- Klikněte pravým tlačítkem na jednom z uzlů chování a vyberte "**novou konfiguraci chování...**  
  
- Vyberte jeden z uzlů chování a klikněte **novou konfiguraci chování**... v **podokna úloh** v levém dolním rohu okna.  
  
##### <a name="adding-behavior-element-extensions-to-a-behavior"></a>Přidání chování Element rozšíření k chování  
  
1. Vyberte jeden z uzlů chování.  
  
2. Vyberte chování, které chcete upravit.  
  
3. Klikněte na **Přidat**.  
  
4. Seznam dostupných rozšíření vyberte rozšíření elementu chování, které chcete přidat.  
  
5. Klikněte na **Přidat**.  
  
##### <a name="adjusting-the-extension-position-in-a-behavior"></a>Nastavení pozice rozšíření v chování  
 Chování jsou kolekce elementů, které tvoří zásobníku. Každý prvek v zásobníku má svou vlastní konfiguraci. Pořadí rozšíření elementu chování v chování označuje pozice v zásobníku. Nejprve se použijí prvků v horní části zásobníku. Chcete-li změnit pořadí:  
  
1. Vyberte jeden z uzlů chování.  
  
2. Vyberte chování, které chcete upravit.  
  
3. Vyberte prvek rozšíření chování **pozice rozšíření elementu chování** oddílu.  
  
4. Použití **nahoru** nebo **dolů** na levé straně seznamu změní pozici vybraného prvku.  
  
##### <a name="editing-the-configuration-of-behavior-element-extensions"></a>Úprava konfigurace chování Element rozšíření  
  
1. Vyberte jeden z uzlů chování ve stromové struktuře.  
  
2. Vyberte chování, které obsahuje prvek, na který chcete upravit.  
  
3. Vyberte rozšíření chování element, který chcete upravit. Nastavení elementu, který se zobrazí v pravém podokně, kde lze upravovat.  
  
#### <a name="protocolmapping"></a>protocolMapping  
 Tato část umožňuje nastavit výchozí typ vazby pro jiné protokoly, například http, tcp, služby MSMQ nebo net.pipe prostřednictvím definované mapování mezi režimy adresy protokolu a je to možné vazby. Můžete také přidat nové mapování na jiné protokoly.  
  
#### <a name="extensions"></a>Rozšíření  
 Nová rozšíření vazby, rozšíření elementu vazby, rozšíření standardní koncový bod a chování rozšíření může být zaregistrovaná pro použití v konfigurace WCF. Rozšíření jsou páry název/typu. Název definuje název rozšíření v konfiguraci, že typ implementuje rozšíření. Existují čtyři typy rozšíření:  
  
- Rozšíření vazby definice typu celého vazby. Příklad: `basicHttpBinding`.  
  
- Rozšíření elementu vazby definuje prvek vazby. Příklad: `textMessageEncoding`.  
  
- Standardní koncový bod rozšíření definovat celou standardní koncový bod. Příklad: `discoveryEndpoint`.  
  
- Element rozšíření chování definujte prvek chování. Příklad: `clientVia`.  
  
 Rozšíření, které jsou zaregistrovány v konfiguraci lze použít stejně jako ostatní součásti WCF stejného typu.  
  
##### <a name="adding-a-new-extension"></a>Přidání nové rozšíření  
 Vyberte jeden z uzlů rozšíření v pokročilé uzly:  
  
1. Klikněte na možnost **Nové**.  
  
2. Zadejte název a typ.  
  
3. Klikněte na **OK**.  
  
4. Rozšíření se teď zobrazí v příslušném umístění v editoru. Například pokud chcete přidat rozšíření elementu chování, zobrazí se v seznamu dostupných rozšíření.  
  
#### <a name="hosting-environment"></a>Hostitelské prostředí  
 Tato část umožňuje definovat nastavení instance služby hostování prostředí.  
  
### <a name="creating-a-configuration-file-using-the-wizard"></a>Vytvoření konfiguračního souboru pomocí Průvodce  
 Jeden způsob, jak vytvořit nový soubor konfigurace je použití Průvodce novým Element služby. Průvodce vyhledá typy nainstalované služby a další prvky kompatibilní s použitím technologie WCF v počítači, včetně modelu COM + a Web hostovaný virtuální adresáře a načte, aby vytváření konfigurace mnohem více zjednodušené.  
  
#### <a name="creating-a-configuration-file"></a>Vytvoření konfiguračního souboru  
  
1. Spustit Service Configuration Editor pomocí příkazové okno a přejděte do umístění instalace WCF a pak zadejte `SvcConfigEditor.exe`.  
  
2. Z **souboru** nabídce vyberte možnost **otevřít** a klikněte na tlačítko **spustitelný soubor**, **služby modelu COM +**, nebo **WebHosted služby**, v závislosti na typu konfiguračního souboru, kterou chcete vytvořit.  
  
3. V **otevřít** dialogové okno, přejděte na konkrétní soubor, který chcete vytvořit konfigurační soubor a dvojím kliknutím ho.  
  
4. V **souboru** nabídky, přejděte k **přidat novou položku** a klikněte na tlačítko **služby**. Otevře se Průvodce vytvořením Element služby.  
  
5. Postupujte podle pokynů v průvodci vytvořit novou službu.  
  
> [!NOTE]
>  Pokud chcete použít NetPeerTcpBinding z konfiguračního souboru generované průvodcem knihovnou, budete muset ručně přidat element konfigurace vazby a upravovat `mode` atribut jeho `security` prvku "None".  
  
## <a name="configuring-com"></a>Konfigurace modelu COM +  
 Editor konfigurace služby umožňuje vytvořit nový soubor konfigurace pro existující aplikace modelu COM +, nebo upravte stávající konfiguraci modelu COM +. **COM smlouvy** uzlu je viditelná jen v případě <`comContract`> oddíl existuje v konfiguračním souboru.  
  
### <a name="creating-a-new-com-configuration"></a>Vytváří se nová konfigurace modelu COM +  
 Před vytvořením nové konfigurace modelu COM +, ujistěte se, že aplikace modelu COM + je nainstalovaná ve službě komponent a zaregistrován v globální mezipaměti sestavení (GAC).  
  
1. Vyberte **souboru** nabídka -> **integrace** -> **aplikace modelu COM +.** Tato operace ukončí aktuální otevřený soubor. Pokud je zde neuložená data v aktuálním souboru, zobrazí se dialogové okno Uložit. **Průvodce integrace modelu COM +** se pak spustí.  
  
2. Na první stránce vyberte ze stromu modelu COM +. Pokud vaše aplikace modelu COM + nemůže najít ve stromové struktuře, ověřte, že je nainstalována součást služeb a zaregistrován v globální mezipaměti sestavení (GAC).  
  
3. Na další stránce vyberte metody, které chcete vystavit jako služba WCF. Všechny metody, které jsou podporované v aplikaci COM + se zobrazí a ve výchozím nastavení vybrané.  
  
4. Zvolte metodu hostování.  
  
5. V Průvodci nakonfigurujte další nastavení podle vodítka.  
  
6. Editor konfigurace služby využívá ComSvcConfig.exe na pozadí se vygenerovat konfigurační soubor. Až to uděláte, můžete zobrazit souhrn a ukončíte průvodce. Otevření souboru vygenerovanou konfiguraci tak, aby ji můžete upravovat přímo.  
  
### <a name="editing-an-existing-com-configuration"></a>Úprava existující konfigurace modelu COM +  
  
1. Vyberte **souboru** nabídka -> **otevřít** -> **služby modelu COM +**...  
  
2. Vyberte službu modelu COM + je zapotřebí upravit ze seznamu.  
  
3. Upravit nastavení konfigurace v **kontrakty COM** uzlu.  
  
    > [!NOTE]
    >  Můžete také přímo otevřít a upravit konfigurační soubor, který obsahuje kontrakty COM.  
  
## <a name="security"></a>Zabezpečení  
 Konfigurační soubor služby, vygeneruje Editor konfigurace není zaručeno zabezpečení. Najdete [zabezpečení](../../../docs/framework/wcf/feature-details/security.md) dokumentace a zjistěte, jak zabezpečit vaše služby WCF.  
  
 Kromě toho můžete Editor konfigurace použít jenom pro čtení a zápis platné prvky konfigurace WCF. Nástroj ignoruje odpovídající schématu, uživatelem definované prvky. Také nepokusí se odebrat tyto prvky z konfigurace souboru nebo zjistit, jejich dopady na známé prvky WCF. Zodpovídá za uživatele k určení, jestli tyto prvky představovat hrozbu pro aplikace nebo systému.
