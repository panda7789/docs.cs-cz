---
title: Nástroj Configuration Editor (SvcConfigEditor.exe)
ms.date: 03/30/2017
helpviewer_keywords:
- configuration files, creating
- configuration files
- Configuration file
- configuration file schema
ms.assetid: 2db21a57-5f64-426f-89df-fb0dc2d2def5
ms.openlocfilehash: b026524ad9579b2828765bed39b61383987108d6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928572"
---
# <a name="configuration-editor-tool-svcconfigeditorexe"></a>Nástroj Configuration Editor (SvcConfigEditor.exe)
Editor konfigurace služby Windows Communication Foundation (WCF) (SvcConfigEditor. exe) umožňuje správcům a vývojářům vytvářet a upravovat nastavení konfigurace služeb WCF pomocí grafického uživatelského rozhraní. Pomocí tohoto nástroje můžete spravovat nastavení vazeb WCF, chování, služeb a diagnostiky, aniž byste museli přímo upravovat konfigurační soubory XML.  
  
 Editor konfigurace služby najdete ve složce C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin.  
  
## <a name="the-wcf-configuration-editor"></a>Editor konfigurace WCF  
 Editor konfigurace služby se dodává s průvodcem, který vás provede všemi kroky v části Konfigurace služby WCF nebo klienta. Důrazně doporučujeme použít Průvodce místo toho přímo v editoru.  
  
 Pokud už máte nějaké konfigurační soubory, které vyhovují standardnímu schématu System. Configuration, můžete spravovat konkrétní nastavení pro vazby, chování, služby a diagnostiku s uživatelským rozhraním. Editor konfigurace služby umožňuje spravovat nastavení pro existující konfigurační soubory WCF i spustitelné soubory, služby modelu COM+ a služby hostované na webu. Při otevírání služby hostované na webu pomocí editoru konfigurace služby se zobrazí jak vlastní konfigurace služby, tak zděděné konfigurace uzlů nejvyšší úrovně.  
  
 Vzhledem k tomu, že nastavení konfigurace WCF `<system.serviceModel>` jsou umístěna v části konfiguračního souboru, Editor pracuje výhradně s obsahem tohoto prvku a nepřistupuje k ostatním prvkům ve stejném souboru. Můžete přímo přejít na existující konfigurační soubory nebo můžete vybrat sestavení, které obsahuje službu, virtuální adresář nebo službu COM+. Editor načte konfigurační soubor pro danou službu a umožní uživateli buď přidat nové prvky, nebo upravit existující prvky vnořené v `<system.serviceModel>` části konfiguračního souboru.  
  
 Editor podporuje technologii IntelliSense a vynutil dodržování předpisů schématu. Výsledný výstup je zaručený v dodržení schématu konfiguračního souboru a má syntakticky správné hodnoty dat. Editor však nezaručuje, že konfigurační soubor je sémanticky platný. Jinými slovy Editor nezaručuje, že konfigurační soubor může spolupracovat se službou, kterou konfiguruje.  
  
> [!CAUTION]
>  Editor nemůže po úpravě elementu odstranit konfigurační prvek z konfiguračního souboru. Pokud například použijete editor k nastavení názvu koncového bodu na neprázdný řetězec a uložíte ho, konfigurační soubor má následující obsah, jak je znázorněno v následujícím příkladu.  
>   
>  `<endpoint binding="basicHttpBinding" name="somename" />`  
>   
>  Pokud se pokusíte odebrat název nastavením na prázdný řetězec a uložit soubor, konfigurační soubor stále obsahuje `name` atribut, jak je znázorněno v následujícím příkladu.  
>   
>  `<endpoint binding="basicHttpBinding" name="" />`  
>   
>  Chcete-li tento atribut vyprázdnit, je nutné ručně upravit element pomocí jiného textového editoru.  
>   
>  Pokud použijete `issueToken` prvek `clientCredential` chování koncového bodu, měli byste být obzvláště opatrní u tohoto problému. Konkrétně atribut jeho `localIssuer` dílčího elementu nesmí být prázdným řetězcem. `address` Pokud jste změnili `address` atribut pomocí editoru konfigurace a chcete ho úplně odebrat, měli byste použít jiný nástroj než Editor. V opačném případě atribut obsahuje prázdný řetězec a vaše aplikace vyvolá výjimku.  
  
## <a name="using-the-configuration-editor"></a>Použití editoru konfigurace  
 Editor konfigurací služby najdete v následujících Windows SDK umístění instalace:  
  
 C:\Program Files\Microsoft SDKs\Windows\v6.0\Bin\SvcConfigEditor.exe  
  
 Po spuštění editoru konfigurace služby můžete pomocí nabídky **soubor/otevřít** vyhledat službu nebo sestavení, které chcete spravovat. Můžete otevřít konfigurační soubory přímo, vyhledat WCF/COM + Services a otevřít konfigurační soubory pro služby hostované na webu.  
  
 Uživatelské rozhraní editoru konfigurace služby je rozdělené do následujících oblastí:  
  
- Podokno stromového zobrazení, které zobrazuje prvky konfigurace ve stromové struktuře vlevo. Kliknutím pravým tlačítkem myši na uzly můžete provádět operace ve stromové struktuře.  
  
- Podokno úloh, které zobrazuje běžné úkoly pro aktuální prvky v levém dolním rohu okna  
  
- Podokno podrobností, které zobrazuje podrobné nastavení uzlu Konfigurace vybraného ve stromovém zobrazení vpravo.  
  
### <a name="opening-a-configuration-file"></a>Otevření konfiguračního souboru  
  
1. Spusťte editor konfigurace služby pomocí příkazového řádku a přejděte do umístění instalace WCF a pak zadejte `SvcConfigEditor.exe`.  
  
2. V nabídce **soubor** vyberte **otevřít** a klikněte na typ souboru, který chcete spravovat.  
  
3. V dialogovém okně **otevřít** přejděte na konkrétní soubor, který chcete spravovat, a dvakrát na něj klikněte.  
  
 Prohlížeč automaticky sleduje cestu sloučení konfigurace a vytvoří zobrazení sloučené konfigurace. Například skutečná konfigurace nehostované služby je kombinací souboru Machine. config a App. config. Všechny změny se aplikují na aktivní soubor v SvcConfigEditor. Pokud chcete upravit konkrétní soubor v cestě pro sloučení konfigurace, měli byste ho otevřít přímo.  
  
> [!NOTE]
> Editor konfigurací znovu načte aktuálně otevřený konfigurační soubor, když byl druhý upravený mimo editor. Pokud k tomu dojde, všechny změny, které nejsou uložené v editoru trvale, se ztratí. Pokud probíhá opětovné načítání konzistentně, nejpravděpodobnější příčinou je služba, která nepřetržitě přistupuje ke konfiguračnímu souboru, například antivirový software spuštěný na pozadí. Chcete-li tento problém vyřešit, zajistěte, aby byl Editor konfigurací jediným procesem, který má přístup k souboru při jeho otevření.  
  
### <a name="services"></a>Služby  
 Uzel **služby** zobrazí všechny služby, které jsou aktuálně přiřazeny k konfiguračnímu souboru. Každý dílčí uzel ve stromové struktuře odpovídá dílčímu elementu <`services`> elementu v konfiguračním souboru.  
  
 Když kliknete na uzel **služby** , můžete zobrazit nebo provádět úlohy na stránce Souhrn služby v podokně **podrobností** .  
  
#### <a name="creating-a-new-service-configuration"></a>Vytváří se nová konfigurace služby.  
 Novou konfiguraci služby můžete vytvořit následujícími způsoby:  
  
- Pomocí Průvodce: Klikněte na odkaz **vytvořit novou službu...** na stránce podokno úloh nebo souhrn spusťte průvodce. Můžete to provést také v nabídce **soubor** – > **Přidat novou položku**.  
  
- Vytvořit ručně: Můžete kliknout pravým tlačítkem myši na uzel **služby** a zvolit možnost **Nová služba**.  
  
#### <a name="creating-a-new-service-endpoint-configuration"></a>Vytváří se nová konfigurace koncového bodu služby.  
 Novou konfiguraci koncového bodu služby můžete vytvořit následujícími způsoby:  
  
- Vytvořit pomocí Průvodce: klikněte na odkaz **vytvořit nový koncový bod služby...** na stránce podokno úloh nebo souhrn spusťte průvodce. Můžete to provést také v nabídce **soubor** – > **Přidat novou položku**.  
  
- Vytvořit ručně: Po vytvoření služby můžete kliknout pravým tlačítkem na uzel **koncové body** a zvolit**Nový koncový bod služby**.  
  
#### <a name="editing-a-service-configuration"></a>Úprava konfigurace služby  
  
1. Klikněte na uzel **služby** .  
  
2. Upravte nastavení v Gridech vlastností.  
  
#### <a name="editing-a-service-endpoint-configuration"></a>Úprava konfigurace koncového bodu služby  
  
1. Klikněte na uzel **koncového bodu služby** .  
  
2. Upravte nastavení v Gridech vlastností.  
  
#### <a name="adding-a-base-address"></a>Přidání základní adresy  
  
1. Klikněte na uzel **hostitele** .  
  
2. Klikněte na **Nový...** tlačítko v části **základní adresy** .  
  
3. Do dialogového okna zadejte identifikátor URI základní adresy.  
  
4. Klikněte na **OK**.  
  
> [!NOTE]
> V tomto nástroji nemůžete upravit hodnotu [ \<baseAddressPrefixFilters >](../../../docs/framework/configure-apps/file-schema/wcf/baseaddressprefixfilters.md) . Chcete-li přidat nebo upravit tento prvek, měli byste použít textový editor nebo Visual Studio.  
  
### <a name="client"></a>Klient  
 Uzel **klienta** zobrazí všechny koncové body klienta v konfiguračním souboru. Každý dílčí uzel ve stromové struktuře odpovídá dílčímu elementu <`client`> elementu v konfiguračním souboru.  
  
 Po kliknutí na uzel **klienta** můžete zobrazit nebo provádět úlohy na **stránce Souhrn** klienta v **podokně podrobností**.  
  
#### <a name="creating-a-new-client-endpoint-configuration"></a>Vytváří se nová konfigurace koncového bodu klienta.  
 Novou konfiguraci koncového bodu klienta můžete vytvořit následujícími způsoby:  
  
- Průvodce vytvořením: Klikněte na odkaz **vytvořit nového klienta...** v **podokně úloh** v levém dolním rohu okna nebo souhrnu spusťte průvodce . Můžete to provést také v nabídce **soubor** – > **Přidat novou položku**. Průvodce vás vyzve, abyste odkazovali na umístění konfigurace služby, ze které se vygenerovala konfigurace klienta. Pak můžete zvolit koncový bod služby, ke které se chcete připojit.  
  
- Vytvořit ručně: Klikněte pravým tlačítkem na uzel **koncové body** v části **klient**a vyberte **Nový koncový bod klienta**.  
  
#### <a name="editing-a-client-endpoint-configuration"></a>Úprava konfigurace koncového bodu klienta  
  
1. Klikněte na uzel **koncového bodu klienta** .  
  
2. Upravte nastavení v Gridech vlastností.  
  
### <a name="standard-endpoint"></a>Standardní koncový bod  
 Standardní koncové body jsou specializované koncové body, které mají jednu nebo více aspektů adresy, kontraktu a vazby nastavené na výchozí hodnoty.  
  
 Taková nastavení konfigurace se ukládají do uzlu **standardního koncového bodu** . Uzel **standardního koncového bodu** zobrazí všechna nastavení standardního koncového bodu v konfiguračním souboru. Každý dílčí uzel ve stromové struktuře odpovídá dílčímu prvku `<standardEndpoints>` v elementu v konfiguračním souboru.  
  
 Když kliknete na uzel **standardního koncového bodu** , můžete zobrazit nebo provádět úlohy na **stránce Souhrn** standardního koncového bodu v **podokně podrobností**.  
  
#### <a name="creating-a-new-standard-endpoint-configuration"></a>Vytváří se nová konfigurace standardního koncového bodu.  
 Novou konfiguraci standardního koncového bodu můžete vytvořit následujícími způsoby:  
  
- Klikněte pravým tlačítkem na uzel **standardní koncový bod** a vyberte **Nová konfigurace standardního koncového bodu...** V dialogovém okně vyberte typ vazby a klikněte na **OK**.  
  
- Vyberte uzel **standardního koncového bodu** a klikněte na **nový standardní konfigurace koncového bodu...** v **podokně úloh** v levém dolním rohu okna.  
  
 Zobrazí se dialogové okno **Vytvoření nového standardního koncového bodu** , ve kterém jsou uvedeny všechny registrované standardní typy koncových bodů.  
  
#### <a name="viewing-and-editing-a-standard-endpoint-configuration"></a>Zobrazení a úprava konfigurace standardního koncového bodu  
 Konfiguraci standardního koncového bodu můžete otevřít pro zobrazení a úpravy následujícími způsoby:  
  
- Kliknutím rozbalte uzel **standardní koncový bod** a klikněte na příslušný dílčí uzel koncového bodu.  
  
- Klikněte na uzel **standardní koncový bod** a v podokně podrobností klikněte na příslušný koncový bod.  
  
 Atributy koncového bodu jsou zobrazeny v pravém podokně pro úpravy.  
  
#### <a name="deleting-a-standard-endpoint-configuration"></a>Odstraňuje se konfigurace standardního koncového bodu.  
 Konfiguraci standardních koncových bodů můžete odstranit následujícími způsoby:  
  
- Kliknutím rozbalte uzel **standardní koncový bod** a klikněte pravým tlačítkem myši na příslušný dílčí uzel koncového bodu. K odstranění koncového bodu použijte kontextový příkaz **Odstranit konfiguraci standardního koncového bodu** .  
  
- Klikněte na uzel **standardní koncový bod** . V podokně **úloh** klikněte na **Odstranit standardní konfiguraci koncového bodu**.  
  
 Pokud se používá standardní koncový bod, při pokusu o odstranění se zobrazí zpráva s upozorněním: **Standardní koncový bod se používá. Pokud ho odstraníte nyní, nezapomeňte odstranit všechny jeho odkazy v jiných částech konfigurace (například v koncovém bodu služby nebo koncovém bodu klienta). V opačném případě bude konfigurace neplatná a nedá se otevřít příště. Opravdu chcete odstranit standardní koncový bod? "**  
  
### <a name="binding"></a>Vazba  
 Konfigurace vazeb se používají ke konfiguraci vazeb u koncových bodů. Taková nastavení konfigurace jsou uložena v uzlu **vazby** . Konfigurace odkazu na koncové body podle názvu a více koncových bodů může odkazovat na konfiguraci jedné vazby.  
  
 Uzel **vazby** zobrazí všechna nastavení vazby v konfiguračním souboru. Každý dílčí uzel ve stromové struktuře odpovídá dílčímu prvku v prvku <`bindings`> v konfiguračním souboru.  
  
 Po kliknutí na uzel **vazby** můžete zobrazit nebo provádět úlohy na **stránce Souhrn** vazby v **podokně podrobností**.  
  
#### <a name="creating-a-new-binding-configuration"></a>Vytváří se nová konfigurace vazby.  
 Novou konfiguraci vazby můžete vytvořit následujícími způsoby.  
  
- Klikněte pravým tlačítkem myši na uzel **vazby** a vyberte možnost **Nová konfigurace vazby**... V dialogovém okně vyberte typ vazby a klikněte na **OK**.  
  
- Vyberte uzel **vazby** a klikněte na **Nová konfigurace vazby**... v **podokně úloh** v levém dolním rohu okna.  
  
- Na stránce Souhrn služby nebo klienta klikněte na **kliknutím na tlačítko vytvořit** v poli **Konfigurace vazby** vytvořte konfiguraci vazby pro odpovídající koncový bod.  
  
#### <a name="adding-binding-element-extensions-to-a-custom-binding"></a>Přidání rozšíření elementu vazby k vlastní vazbě  
  
1. Vyberte vazbu, do které chcete přidat prvek rozšíření.  
  
2. Klikněte na **Přidat**.  
  
3. V seznamu dostupných rozšíření vyberte rozšíření prvku vazby, které chcete přidat. Chcete-li vybrat více položek, stiskněte současně klávesu CTRL.  
  
4. Klikněte na **Přidat**.  
  
#### <a name="adjusting-the-extension-position-in-a-custom-binding"></a>Úprava pozice rozšíření ve vlastní vazbě  
 Vlastní vazba je kolekce elementů vazby, které tvoří zásobník. Každý prvek vazby v zásobníku má vlastní nastavení konfigurace. Pořadí rozšíření prvků vazby ve vlastní vazbě označuje jejich pozice v zásobníku. Jako první se aplikují prvky v horní části zásobníku. Postup změny řazení:  
  
1. Vyberte vlastní uzel vazby.  
  
2. Vyberte jeden prvek rozšíření vazby v oddílu **pozice rozšíření vazby elementu** .  
  
3. Chcete-li změnit pozici vybraného prvku, použijte tlačítko **nahoru** nebo **dolů** na levé straně seznamu.  
  
#### <a name="editing-the-configuration-of-binding-element-extensions-in-a-custom-binding"></a>Úprava konfigurace rozšíření elementu vazby ve vlastní vazbě  
  
1. Vyberte uzel vazby ve stromu.  
  
2. Vyberte vlastní vazbu obsahující prvek, který chcete upravit.  
  
3. Vyberte rozšíření prvku vazby, které chcete upravit. Nastavení prvku se zobrazí v pravém podokně, kde je lze upravovat.  
  
### <a name="diagnostics"></a>Diagnostika  
 V uzlu **Diagnostika** se zobrazí všechna nastavení diagnostiky v konfiguračním souboru. Umožňuje zapnout nebo vypnout čítače výkonu, povolit nebo zakázat rozhraní WMI (Windows Management Instrumentation) (WMI), nakonfigurovat trasování WCF a nakonfigurovat protokolování zpráv WCF. Nastavení v uzlu **Diagnostika** odpovídá oddílu <`system.diagnostics`> a `<diagnostics>` v konfiguračním souboru v `<system.serviceModel>` části.  
  
 Po kliknutí na uzel **Diagnostika** můžete zobrazit nebo provádět úlohy na **stránce Souhrn** diagnostiky v **podokně podrobností**.  
  
#### <a name="configuring-performance-counters-and-wmi"></a>Konfigurace čítačů výkonu a rozhraní WMI  
  
1. Klikněte na uzel **Diagnostika** .  
  
2. Klikněte na **Přepnout čítače výkonu**. Čítač výkonu má tři stavy: Off (default), ServiceOnly a All. Kliknutím na odkaz přepnete nastavení mezi těmito třemi stavy.  
  
#### <a name="configuring-wmi-provider"></a>Konfigurace zprostředkovatele rozhraní WMI  
  
1. Klikněte na uzel **Diagnostika** .  
  
2. Pokud chcete povolit zprostředkovatele rozhraní WMI, klikněte na odkaz **Povolit zprostředkovatele rozhraní WMI** .  
  
#### <a name="enabling-wcf-tracing"></a>Povolení trasování WCF  
 Můžete vytvořit trasovací soubor WCF se standardními vlastnostmi nebo nastavit vlastní trasovací soubor.  
  
1. Klikněte na uzel **Diagnostika** .  
  
2. Klikněte na **Povolit trasování**.  
  
3. Kliknutím na odkaz **úroveň trasování** upravíte úroveň trasování. Existuje šest úrovní trasování: Vypnuto, kritická, chyba, upozornění, informace a podrobné. Možnost **trasování aktivity** a **šíření** aktivity umožňuje použít funkci trasování aktivity WCF.  
  
4. Klikněte na název naslouchacího procesu trasování a určete trasovací soubor a možnosti.  
  
#### <a name="enabling-wcf-logging"></a>Povolení protokolování WCF  
 Můžete vytvořit trasovací soubor WCF se standardními vlastnostmi nebo nastavit vlastní trasovací soubor.  
  
1. Klikněte na uzel **Diagnostika** .  
  
2. Klikněte na **Povolit protokolování zpráv**.  
  
3. Kliknutím na odkaz **úroveň protokolu** upravíte úroveň protokolu. Existují tři úrovně protokolu: Chybně formátovaná, služba a přenos.  
  
4. Klikněte na název naslouchacího procesu a určete soubor protokolu a možnosti.  
  
> [!NOTE]
> Pokud chcete, aby se protokoly trasování a zpráv vyprázdny automaticky, když je vaše aplikace zavřená, povolte možnost **automatického** vyprázdnit.  
  
 **Stránka Souhrn** diagnostiky umožňuje provádět nejběžnější úlohy v konfiguraci diagnostiky. Pokud však chcete ručně upravit nastavení naslouchacího procesu a zdrojů, je nutné rozbalit uzel **Diagnostika** a upravit nastavení v uzlu **protokolování zpráv**, **naslouchací procesy** a **zdroje** .  
  
#### <a name="enabling-wcf-custom-tracing-or-message-logging"></a>Povolení vlastního trasování WCF nebo protokolování zpráv  
  
1. Klikněte na uzel **Diagnostika** a rozbalte ho.  
  
2. Klikněte pravým tlačítkem myši na uzel **naslouchací procesy** a vyberte možnost **nový naslouchací proces**.  
  
3. Do pole **InitData** zadejte název trasovacího souboru. Můžete kliknout na tlačítko "..." tlačítko pro procházení k cestě.  
  
4. Kliknutím na řádek **TypeName** se zobrazí znak "...". tlačítko. Kliknutím na toto tlačítko otevřete **prohlížeč typu naslouchacího procesu trasování**, který můžete použít k vyhledání předem nakonfigurovaných posluchačů trasování, které jsou již nainstalovány.  
  
5. Všimněte si **zdrojové** části. Kliknutím na **Přidat** v této části otevřete dialogové okno s rozevírací nabídkou, která obsahuje seznam dostupných zdrojů trasování. Vyberte zdroj trasování a klikněte na tlačítko **OK**.  
  
6. Chcete-li upravit nastavení protokolování zpráv, klikněte na uzel **protokolování zpráv** . Nastavení můžete upravit v mřížce vlastností.  
  
### <a name="advanced"></a>Upřesnit  
  
#### <a name="behaviors"></a>Chování  
 Uzel **chování** zobrazuje chování, která jsou aktuálně definována v konfiguračním souboru.  
  
 Konfigurace chování se používají ke konfiguraci chování koncových bodů a služeb. Tato nastavení konfigurace se ukládají v uzlu **Upřesnit** v části **chování služby** a **chování koncového bodu**. Služba používá chování služby; zatímco chování koncového bodu podle koncových bodů.  
  
 Chování jsou kolekce elementů rozšíření, které jsou pro zásobník. Nejprve se použije element v horní části zásobníku. Každý element rozšíření může mít svou vlastní konfiguraci.  
  
##### <a name="creating-a-new-behavior-configuration"></a>Vytváří se nová konfigurace chování.  
 Novou konfiguraci chování můžete vytvořit dvěma způsoby.  
  
- Klikněte pravým tlačítkem na jeden z uzlů chování a vyberte možnost "**Nová konfigurace chování...**  
  
- Vyberte jeden z uzlů chování a klikněte na **konfiguraci nového chování**... v **podokně úloh** v levém dolním rohu okna.  
  
##### <a name="adding-behavior-element-extensions-to-a-behavior"></a>Přidání rozšíření prvků chování k chování  
  
1. Vyberte jeden z uzlů chování.  
  
2. Vyberte chování, které chcete upravit.  
  
3. Klikněte na **Přidat**.  
  
4. V seznamu dostupných rozšíření vyberte rozšíření prvku chování, které chcete přidat.  
  
5. Klikněte na **Přidat**.  
  
##### <a name="adjusting-the-extension-position-in-a-behavior"></a>Úprava pozice rozšíření v chování  
 Chování jsou kolekce prvků, které tvoří zásobník. Každý prvek v zásobníku má svou vlastní konfiguraci. Pořadí rozšíření prvků chování v chování určuje jejich pozice v zásobníku. Jako první se aplikují prvky v horní části zásobníku. Postup změny řazení:  
  
1. Vyberte jeden z uzlů chování.  
  
2. Vyberte chování, které chcete upravit.  
  
3. Vyberte prvek rozšíření chování v oddílu **pozice rozšíření chování elementu** .  
  
4. Chcete-li změnit pozici vybraného prvku, použijte tlačítko **nahoru** nebo **dolů** na levé straně seznamu.  
  
##### <a name="editing-the-configuration-of-behavior-element-extensions"></a>Úprava konfigurace rozšíření prvků chování  
  
1. Vyberte jeden z uzlů chování ve stromu.  
  
2. Vyberte chování, které obsahuje prvek, který chcete upravit.  
  
3. Vyberte rozšíření prvku chování, které chcete upravit. Nastavení prvku se zobrazí v pravém podokně, kde je lze upravovat.  
  
#### <a name="protocolmapping"></a>ProtocolMapping  
 V této části můžete nastavit výchozí typy vazeb pro různé protokoly, jako jsou http, TCP, MSMQ nebo NET. pipe, prostřednictvím definovaného mapování mezi schématy adres protokolů a možnými vazbami. Můžete také přidat nová mapování na jiné protokoly.  
  
#### <a name="extensions"></a>Rozšíření  
 Nová rozšíření vazby, rozšíření elementů vazby, standardní rozšíření koncových bodů a rozšíření chování lze zaregistrovat pro použití v konfiguraci služby WCF. Rozšíření jsou páry název/typ. Název definuje název rozšíření v konfiguraci, zatímco typ implementuje rozšíření. Existují čtyři typy rozšíření:  
  
- Rozšíření vazby definují celý typ vazby. Příklad: `basicHttpBinding`.  
  
- Rozšíření elementu vazby definují prvek vazby. Příklad: `textMessageEncoding`.  
  
- Rozšíření Standard Endpoint Extensions definují celý standardní koncový bod. Příklad: `discoveryEndpoint`.  
  
- Rozšíření prvků chování definují prvek chování. Příklad: `clientVia`.  
  
 Rozšíření, která byla registrována v konfiguraci, lze použít jako jakoukoli jinou komponentu WCF stejného typu.  
  
##### <a name="adding-a-new-extension"></a>Přidání nového rozšíření  
 Vyberte jeden z uzlů rozšíření v pokročilých uzlech:  
  
1. Klikněte na možnost **Nové**.  
  
2. Zadejte název a typ.  
  
3. Klikněte na **OK**.  
  
4. Rozšíření se nyní zobrazí na příslušném místě v editoru. Například pokud přidáte rozšíření prvku chování, zobrazí se v seznamu dostupných rozšíření.  
  
#### <a name="hosting-environment"></a>Hostitelské prostředí  
 Tato část umožňuje definovat nastavení vytváření instancí pro hostitelské prostředí služby.  
  
### <a name="creating-a-configuration-file-using-the-wizard"></a>Vytvoření konfiguračního souboru pomocí Průvodce  
 Jedním ze způsobů, jak vytvořit nový konfigurační soubor, je použít Průvodce novým prvkem služby. Průvodce najde nainstalované typy služeb a další prvky kompatibilní s WCF v počítači, včetně virtuálních adresářů služby COM+ a webhost, a načítají je, aby bylo možné konfiguraci mnohem zefektivnit.  
  
#### <a name="creating-a-configuration-file"></a>Vytváření konfiguračního souboru  
  
1. Spusťte editor konfigurace služby pomocí příkazového řádku a přejděte do umístění instalace WCF a pak zadejte `SvcConfigEditor.exe`.  
  
2. V nabídce **soubor** vyberte **otevřít** a klikněte na **spustitelný**soubor, **službu com+** nebo službu webhosted **Service**v závislosti na typu konfiguračního souboru, který chcete vytvořit.  
  
3. V dialogovém okně **otevřít** přejděte do konkrétního souboru, pro který chcete vytvořit konfigurační soubor, a dvakrát na něj klikněte.  
  
4. V nabídce **soubor** přejděte na příkaz **Přidat novou položku** a klikněte na možnost **Služba**. Otevře se Průvodce novým prvkem služby.  
  
5. Pomocí kroků v průvodci vytvořte novou službu.  
  
> [!NOTE]
> Chcete-li použít NetPeerTcpBinding z konfiguračního souboru vygenerovaného průvodcem, je nutné ručně přidat prvek konfigurace vazby a upravit `mode` atribut jeho `security` elementu na hodnotu None.  
  
## <a name="configuring-com"></a>Konfigurace modelu COM+  
 Editor konfigurace služby umožňuje vytvořit nový konfigurační soubor pro existující aplikaci modelu COM+ nebo upravit existující konfiguraci modelu COM+. Uzel **kontraktu com** je zobrazen pouze v případě,`comContract`že oddíl < > existuje v konfiguračním souboru.  
  
### <a name="creating-a-new-com-configuration"></a>Vytváří se nová konfigurace COM+.  
 Před vytvořením nové konfigurace COM+ se ujistěte, že je vaše aplikace COM+ nainstalovaná v rámci služby komponent a zaregistrovaná v globální mezipaměti sestavení (GAC).  
  
1. Výběr nabídky **soubor** – > **integraci** -> **aplikace modelu COM+.** Tato operace zavře aktuální otevřený soubor. Pokud se v aktuálním souboru nacházejí neuložená data, zobrazí se dialogové okno Uložit. Pak se spustí **Průvodce integrací com+** .  
  
2. Na první stránce vyberte aplikaci COM+ ze stromu. Pokud ve stromové struktuře nemůžete najít aplikaci modelu COM+, ověřte, zda je nainstalována do služby komponent a registrována v globální mezipaměti sestavení (GAC).  
  
3. Na další stránce vyberte, které metody chcete zveřejnit jako služby WCF. Ve výchozím nastavení se zobrazí všechny podporované metody v aplikaci modelu COM+ a vybrané.  
  
4. Vyberte metodu hostování.  
  
5. Nakonfigurujte další nastavení podle průvodců v průvodci.  
  
6. Editor konfigurace služby používá ComSvcConfig. exe na pozadí ke generování konfiguračního souboru. Po dokončení můžete zobrazit souhrn a ukončit průvodce. Vygenerovaný konfigurační soubor je otevřen, aby jej bylo možné přímo upravit.  
  
### <a name="editing-an-existing-com-configuration"></a>Úprava existující konfigurace modelu COM+  
  
1. Vybrat nabídku **souborů** – > **otevřít** -> **službu com+** ...  
  
2. V seznamu vyberte službu COM+, kterou chcete upravit.  
  
3. Upravte nastavení konfigurace v uzlu **kontrakty com** .  
  
    > [!NOTE]
    > Můžete také přímo otevřít a upravit konfigurační soubor, který obsahuje smlouvy COM.  
  
## <a name="security"></a>Zabezpečení  
 Není zaručeno zabezpečení konfiguračního souboru služby vygenerovaného editorem konfigurace. Informace o tom, jak zabezpečit služby WCF, najdete v dokumentaci k [zabezpečení](../../../docs/framework/wcf/feature-details/security.md) .  
  
 Kromě toho lze editor konfigurace použít pouze ke čtení a zápisu platných konfiguračních elementů WCF. Nástroj ignoruje uživatelsky definované prvky, které odpovídají schématu. Nepokouší se také odebrat tyto prvky z konfiguračního souboru nebo určit jejich účinky na známé elementy WCF. Je zodpovědností uživatele určit, zda tyto prvky představují hrozbu pro aplikaci nebo systém.
