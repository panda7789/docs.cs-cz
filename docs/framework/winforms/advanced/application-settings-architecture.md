---
title: Architektura nastavení aplikace
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application settings [Windows Forms], architecture
ms.assetid: c8eb2ad0-fac6-4ea2-9140-675a4a44d562
ms.openlocfilehash: f686fa00662ad29323c1883c45ed0e790b133f2c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59099778"
---
# <a name="application-settings-architecture"></a>Architektura nastavení aplikace
Toto téma popisuje, jak funguje nastavení aplikace architektury a zkoumá možnosti pokročilých funkcích sady architektury, jako jsou seskupené nastavení a nastavení klíče.  
  
 Architektura nastavení aplikace podporuje definující silného typu nastavení aplikace nebo oboru uživatele, a uložením nastavení mezi relacemi aplikace. Tato architektura poskytuje výchozí web trvalosti pro nastavení pro ukládání a načítání z místního systému souborů. Tato architektura také definuje rozhraní pro zadávání vlastního modulu.  
  
 Rozhraní jsou k dispozici, které umožňují vlastní komponenty se zachovat své vlastní nastavení, když jsou hostované v aplikaci. Pomocí nastavení klíče součásti můžete oddělit nastavení pro víc instancí komponenty.  
  
## <a name="defining-settings"></a>Definování nastavení  
 Architektura nastavení aplikace se používá v rámci obou [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] a Windows Forms, který obsahuje řadu základních tříd, které jsou sdíleny mezi oběma prostředími. Nejdůležitější je <xref:System.Configuration.SettingsBase>, který poskytuje přístup k nastavení prostřednictvím kolekce a poskytuje nízké úrovně metody pro načítání a ukládání nastavení. Každé prostředí implementuje své vlastní třídy odvozené od <xref:System.Configuration.SettingsBase> nakonfigurovánu další nastavení pro toto prostředí. V aplikaci na základě formulářů Windows, všechna nastavení aplikace musí být definován ve třídě odvozené z <xref:System.Configuration.ApplicationSettingsBase> třídu, která přidá následující funkce na základní třídu:  
  
-   Vyšší úrovně načítání a ukládání operace  
  
-   Podpora pro nastavení rozsahu uživatele  
  
-   Při vrácení nastavení uživatele do předdefinované nastavení  
  
-   Upgrade nastavení z předchozí verze aplikace  
  
-   Ověřují se nastavení, než se mění nebo před jejich uložením  
  
 Tato nastavení můžete popsaná s počtem atributů definovaných v rámci <xref:System.Configuration> obor názvů; tyto možnosti jsou popsány v [atributy nastavení aplikace](application-settings-attributes.md). Při definování nastavení, musí ho použít s oběma <xref:System.Configuration.ApplicationScopedSettingAttribute> nebo <xref:System.Configuration.UserScopedSettingAttribute>, která popisuje, zda nastavení platí pro celou aplikaci nebo jenom pro aktuálního uživatele.  
  
 Následující příklad kódu definuje vlastní nastavení třída s atributem jedno nastavení `BackgroundColor`.  
  
 [!code-csharp[ApplicationSettings.Create#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/MyAppSettings.cs#1)]
 [!code-vb[ApplicationSettings.Create#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/MyAppSettings.vb#1)]  
  
## <a name="settings-persistence"></a>Nastavení trvalosti  
 <xref:System.Configuration.ApplicationSettingsBase> Třída nemá sama zachovat nebo načíst nastavení; tato úloha přejde k nastavení zprostředkovatele, třídy, která je odvozena z <xref:System.Configuration.SettingsProvider>. Pokud odvozenou třídu <xref:System.Configuration.ApplicationSettingsBase> neurčuje zprostředkovatele nastavení prostřednictvím <xref:System.Configuration.SettingsProviderAttribute>, pak výchozí zprostředkovatel <xref:System.Configuration.LocalFileSettingsProvider>, se používá.  
  
 Konfigurační systém, který byl poprvé uveden s [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] podporuje poskytování statických aplikace konfigurační data místním počítači během procházení souboru machine.config nebo v rámci `app.`exe.config soubor, který nasazujete s vaše aplikace. <xref:System.Configuration.LocalFileSettingsProvider> Třída rozšiřuje tato nativní podpora následujícími způsoby:  
  
-   Nastavení oboru aplikace mohou být uloženy v obou souboru machine.config nebo `app.`exe.config soubory. Machine.config je vždy jen pro čtení, při `app`. exe.config omezil aspekty zabezpečení jen pro čtení pro většinu aplikací.  
  
-   Nastavení rozsahu uživatele mohou být uloženy v `app`. exe.config souborů, v takovém případě jsou považovány za statické výchozí hodnoty.  
  
-   Nestandardní nastavení rozsahu uživatele jsou uloženy v novém souboru *uživatele*.config, kde *uživatele* je uživatelské jméno osoby, běžící aplikaci. Můžete určit výchozí hodnoty pro nastavení rozsahu uživatele s <xref:System.Configuration.DefaultSettingValueAttribute>. Protože nastavení rozsahu uživatele při spuštění aplikace, často mění `user`.config je vždy čtení a zápisu.  
  
 Všechny tři konfigurační soubory uložit nastavení je ve formátu XML. Element XML nejvyšší úrovně pro nastavení oboru aplikace je `<appSettings>`, zatímco `<userSettings>` se používá pro nastavení rozsahu uživatele. `app`. Exe.config soubor, který obsahuje nastavení oboru aplikace a výchozí hodnoty pro nastavení rozsahu uživatele bude vypadat takto:  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
    <configSections>  
        <sectionGroup name="applicationSettings" type="System.Configuration.ApplicationSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" >  
            <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
        </sectionGroup>  
        <sectionGroup name="userSettings" type="System.Configuration.UserSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" >  
            <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" allowExeDefinition="MachineToLocalUser" />  
        </sectionGroup>  
    </configSections>  
    <applicationSettings>  
        <WindowsApplication1.Properties.Settings>  
            <setting name="Cursor" serializeAs="String">  
                <value>Default</value>  
            </setting>  
            <setting name="DoubleBuffering" serializeAs="String">  
                <value>False</value>  
            </setting>  
        </WindowsApplication1.Properties.Settings>  
    </applicationSettings>  
    <userSettings>  
        <WindowsApplication1.Properties.Settings>  
            <setting name="FormTitle" serializeAs="String">  
                <value>Form1</value>  
            </setting>  
            <setting name="FormSize" serializeAs="String">  
                <value>595, 536</value>  
            </setting>  
        </WindowsApplication1.Properties.Settings>  
    </userSettings>  
</configuration>  
```  
  
 Definice prvků v sekci nastavení aplikace konfiguračního souboru, naleznete v tématu [schéma nastavení aplikace](../../configure-apps/file-schema/application-settings-schema.md).  
  
### <a name="settings-bindings"></a>Nastavení vazby  
 Nastavení aplikace používá architekturu vazby Windows Forms data pro zajištění obousměrná komunikace aktualizace nastavení mezi objekt nastavení a komponenty. Pokud používáte sadu Visual Studio můžete vytvořit nastavení aplikace a přiřadit je k vlastnosti komponenty, tyto vazby automaticky generovány.  
  
 Nastavení aplikace lze vázat jenom na komponentu, která podporuje <xref:System.Windows.Forms.IBindableComponent> rozhraní. Navíc komponenty musí implementovat událost změny pro konkrétní vázat vlastnosti nebo nastavení aplikace, která je změněna vlastnost prostřednictvím oznámení <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní. Pokud součást neimplementuje <xref:System.Windows.Forms.IBindableComponent> a připojujete pomocí sady Visual Studio, nastaví se při prvním vázané vlastnosti, ale nebude aktualizovat. Pokud komponenta implementuje <xref:System.Windows.Forms.IBindableComponent> , ale nezmění není vlastnost podpora oznámení, vazba se nebude aktualizovat v souboru s nastaveními, když je změněna vlastnost.  
  
 Některé součásti Windows Forms, jako například <xref:System.Windows.Forms.ToolStripItem>, nepodporuje nastavení vazby.  
  
### <a name="settings-serialization"></a>Nastavení serializace  
 Když <xref:System.Configuration.LocalFileSettingsProvider> nastavení musíte uložit na disk, provede následující akce:  
  
1.  Používá reflexi ke kontrole všechny vlastnosti definované ve vašich <xref:System.Configuration.ApplicationSettingsBase> odvozené třídy, jak najít ty, které se použijí s oběma <xref:System.Configuration.ApplicationScopedSettingAttribute> nebo <xref:System.Configuration.UserScopedSettingAttribute>.  
  
2.  Serializuje vlastnost na disk. Prvním pokusu o volání <xref:System.ComponentModel.TypeConverter.ConvertToString%2A> nebo <xref:System.ComponentModel.TypeConverter.ConvertFromString%2A> na typ přidružený k tomuto <xref:System.ComponentModel.TypeConverter>. Pokud se to nezdaří, pomocí serializace XML místo.  
  
3.  Určuje které nastavení přejděte v které soubory na základě nastavení atributu.  
  
 Pokud se rozhodnete implementovat vlastní třídu nastavení, můžete použít <xref:System.Configuration.SettingsSerializeAsAttribute> k označení nastavení buď pomocí binární nebo vlastní serializace <xref:System.Configuration.SettingsSerializeAs> výčtu. Další informace o vytváření vlastních nastavení třídy v kódu, naleznete v tématu [jak: Vytvořit nastavení aplikace](how-to-create-application-settings.md).  
  
### <a name="settings-file-locations"></a>Umístění souboru nastavení  
 Umístění `app`. exe.config a *uživatele*souborech .config se liší v závislosti na tom, jak se aplikace nainstaluje. Pro aplikace založené na formulářích Windows zkopírovat do místního počítače `app`. exe.config se bude nacházet ve stejném adresáři jako základní adresář aplikace hlavní spustitelný soubor, a *uživatele*.config se bude nacházet v umístění určeného proměnnou <xref:System.Windows.Forms.Application.LocalUserAppDataPath%2A?displayProperty=nameWithType> vlastnost. Pro aplikace nainstalované prostřednictvím [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)], oba tyto soubory se bude nacházet v [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] adresář dat pod %InstallRoot%\Documents a nastavení\\*uživatelské jméno*\Local nastavení.  
  
 Umístění úložiště těchto souborů se mírně liší, pokud uživatel má povolen cestovní profily, díky čemuž by uživatelé k definování různých Windows a nastavení aplikace, když uživatel používá jiné počítače v rámci domény. V takovém případě obě [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] aplikace a bez-[!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] aplikace budou mít jejich `app`. exe.config a *uživatele*.config soubory uložené v části Nastavení a %InstallRoot%\Documents\\ *uživatelské jméno*\Application Data.  
  
 Další informace o tom, jak funguje funkce nastavení aplikace s novou technologií nasazení najdete v tématu [ClickOnce a nastavení aplikace](/visualstudio/deployment/clickonce-and-application-settings). Další informace o [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] adresář dat, naleznete v tématu [Accessing Local and Remote Data in ClickOnce Applications](/visualstudio/deployment/accessing-local-and-remote-data-in-clickonce-applications).  
  
## <a name="application-settings-and-security"></a>Nastavení aplikace a zabezpečení  
 Nastavení aplikace jsou navrženy pro práci v částečném vztahu důvěryhodnosti, prostředí s omezeným přístupem, které je výchozí nastavení pro aplikace Windows Forms hostovaná přes Internet nebo intranet. K použití nastavení aplikace se ve výchozím nastavení jsou požadována žádná zvláštní oprávnění nad rámec částečným vztahem důvěryhodnosti.  
  
 Při použití nastavení aplikace v [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] aplikace, `user`soubor .config je uložený v [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] datový adresář. Velikost aplikace `user`soubor .config nesmí překročit kvóta adresáře data nastavením [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)]. Další informace najdete v tématu [ClickOnce a nastavení aplikace](/visualstudio/deployment/clickonce-and-application-settings).  
  
## <a name="custom-settings-providers"></a>Vlastní nastavení zprostředkovatelů  
 V nastavení aplikace architektury, je volné párování mezi nastavení aplikace obálkovou třídu odvozenou z <xref:System.Configuration.ApplicationSettingsBase>, a související nastavení zprostředkovatele nebo zprostředkovatele, odvozený z <xref:System.Configuration.SettingsProvider>. Toto přidružení je definována pouze <xref:System.Configuration.SettingsProviderAttribute> použitý pro obálkovou třídu nebo jeho jednotlivé vlastnosti. Pokud nastavení poskytovatele není explicitně zadán, výchozí zprostředkovatel <xref:System.Configuration.LocalFileSettingsProvider>, se používá. V důsledku toho tato architektura podporuje vytváření a používání vlastních nastavení zprostředkovatele.  
  
 Předpokládejme například, chcete-li k vývoji a použít `SqlSettingsProvider`, zprostředkovatel, který uloží všechna nastavení data v databázi Microsoft SQL Server. Vaše <xref:System.Configuration.SettingsProvider>-odvozené třídy získá tuto informaci v jeho `Initialize` metodu jako parametr typu <xref:System.Collections.Specialized.NameValueCollection?displayProperty=nameWithType>. Pak byste implementovali <xref:System.Configuration.SettingsProvider.GetPropertyValues%2A> metodu pro načtení z úložiště dat, nastavení a <xref:System.Configuration.SettingsProvider.SetPropertyValues%2A> k jejich uložení. Můžete použít poskytovatele <xref:System.Configuration.SettingsPropertyCollection> předaná <xref:System.Configuration.SettingsProvider.GetPropertyValues%2A> k určení názvu vlastnosti, typ a oboru, stejně jako ostatní nastavení atributy definované pro tuto vlastnost.  
  
 Váš poskytovatel bude nutné implementovat jednou vlastností a metod, jejichž implementace nemusí být samozřejmé. <xref:System.Configuration.SettingsProvider.ApplicationName%2A> Je abstraktní vlastnost z <xref:System.Configuration.SettingsProvider>; by se vrátit následující program:  
  
 [!code-csharp[ApplicationSettings.Architecture#2](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#2)]
 [!code-vb[ApplicationSettings.Architecture#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#2)]  
  
 Odvozené třídy musí implementovat taky `Initialize` metodu, která nepřijímá žádné argumenty a nevrací žádnou hodnotu. Tato metoda není definována <xref:System.Configuration.SettingsProvider>.  
  
 Nakonec můžete implementovat <xref:System.Configuration.IApplicationSettingsProvider> ve zprostředkovateli k poskytování podpory pro aktualizaci nastavení vracení nastavení na výchozí nastavení a nastavení upgrade z verze jednu aplikaci do jiného.  
  
 Po implementovat a kompilaci vašeho poskytovatele, je potřeba dát pokyn k používání tohoto poskytovatele místo výchozího nastavení třídu. Toho dosáhnete pomocí <xref:System.Configuration.SettingsProviderAttribute>. Pokud se použije pro celou třídu nastavení zprostředkovatele se používá pro každé nastavení, která definuje třídu; Pokud individuální nastavení, použije architektura nastavení aplikace používá zprostředkovatele pro tato nastavení jenom a používá <xref:System.Configuration.LocalFileSettingsProvider> pro ostatní. Následující příklad kódu ukazuje, jak dát pokyn třídu nastavení vlastního zprostředkovatele.  
  
 [!code-csharp[ApplicationSettings.Architecture#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#1)]
 [!code-vb[ApplicationSettings.Architecture#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#1)]  
  
 Zprostředkovatel může být volána z více vláken současně, ale bude vždy zapisovat do stejného umístění úložiště; Architektura nastavení aplikace, proto vytvoří instanci vždy jen jednu instanci třídy zprostředkovatele.  
  
> [!IMPORTANT]
>  Měli byste zajistit, že váš poskytovatel je bezpečná pro vlákno a povoluje pouze jedno vlákno v době zapisovat do konfigurační soubory.  
  
 Váš poskytovatel nemusí podporovat všechny atributy definované v nastavení <xref:System.Configuration?displayProperty=nameWithType> obor názvů, ale musí být minimální podpory <xref:System.Configuration.ApplicationScopedSettingAttribute> a <xref:System.Configuration.UserScopedSettingAttribute>a také podporovat <xref:System.Configuration.DefaultSettingValueAttribute>. Pro tyto atributy, které nepodporuje váš poskytovatel by měl pouze selhat a oznámení; ji by neměla vyvolávat výjimky. Pokud třída nastavení používá neplatnou kombinaci atributů, ale – například při použití <xref:System.Configuration.ApplicationScopedSettingAttribute> a <xref:System.Configuration.UserScopedSettingAttribute> stejné nastavení, váš poskytovatel by měl vyvolat výjimku a zastavit provádění operací.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Configuration.ApplicationSettingsBase>
- <xref:System.Configuration.SettingsProvider>
- <xref:System.Configuration.LocalFileSettingsProvider>
- [Přehled nastavení aplikace](application-settings-overview.md)
- [Nastavení aplikace pro vlastní ovládací prvky](application-settings-for-custom-controls.md)
- [ClickOnce a nastavení aplikace](/visualstudio/deployment/clickonce-and-application-settings)
- [Schéma nastavení aplikace](../../configure-apps/file-schema/application-settings-schema.md)
