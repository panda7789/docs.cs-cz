---
title: Architektura nastavení aplikace
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application settings [Windows Forms], architecture
ms.assetid: c8eb2ad0-fac6-4ea2-9140-675a4a44d562
ms.openlocfilehash: 078b5f3fc1cd4273af282580f41e68ca9bd8ff51
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182628"
---
# <a name="application-settings-architecture"></a>Architektura nastavení aplikace
Toto téma popisuje, jak funguje architektura Nastavení aplikace, a zkoumá pokročilé funkce architektury, jako jsou seskupená nastavení a klíče nastavení.

 Architektura nastavení aplikace podporuje definování nastavení silného typu s rozsahem aplikace nebo uživatele a zachování nastavení mezi relacemi aplikací. Architektura poskytuje výchozí modul trvalosti pro ukládání nastavení a načítání z místního systému souborů. Architektura také definuje rozhraní pro poskytování vlastní modul trvalosti.

 K dispozici jsou rozhraní, která umožňují vlastním součástem zachovat vlastní nastavení, když jsou hostovány v aplikaci. Pomocí klíčů nastavení mohou součásti zachovat nastavení pro více instancí součásti odděleně.

## <a name="defining-settings"></a>Definování nastavení
 Architektura nastavení aplikace se používá v rámci ASP.NET i Windows Forms a obsahuje řadu základních tříd, které jsou sdíleny v obou prostředích. Nejdůležitější je <xref:System.Configuration.SettingsBase>, který poskytuje přístup k nastavení prostřednictvím kolekce a poskytuje metody nižší úrovně pro načítání a ukládání nastavení. Každé prostředí implementuje vlastní <xref:System.Configuration.SettingsBase> třídu odvozenou z poskytnout další funkce nastavení pro toto prostředí. V aplikaci založené na formulářích systému Windows musí být <xref:System.Configuration.ApplicationSettingsBase> všechna nastavení aplikace definována na třídě odvozené z třídy, která přidává následující funkce do základní třídy:

- Operace načítání a ukládání na vyšší úrovni

- Podpora nastavení s rozsahem uživatele

- Návrat nastavení uživatele k předdefinovaným výchozím hodnotám

- Inovace nastavení z předchozí verze aplikace

- Ověření nastavení před jejich změnou nebo před uložením

 Nastavení lze popsat pomocí několika atributů definovaných <xref:System.Configuration> v oboru názvů; Ty jsou popsány v [atributech nastavení aplikace](application-settings-attributes.md). Při definování nastavení je nutné jej <xref:System.Configuration.ApplicationScopedSettingAttribute> použít <xref:System.Configuration.UserScopedSettingAttribute>buď nebo , který popisuje, zda se nastavení vztahuje na celou aplikaci nebo pouze pro aktuálního uživatele.

 Následující příklad kódu definuje vlastní třídu nastavení `BackgroundColor`s jedním nastavením .

 [!code-csharp[ApplicationSettings.Create#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/MyAppSettings.cs#1)]
 [!code-vb[ApplicationSettings.Create#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/MyAppSettings.vb#1)]

## <a name="settings-persistence"></a>Trvalosti nastavení
 Třída <xref:System.Configuration.ApplicationSettingsBase> není sama o sobě zachovat nebo načíst nastavení; tato úloha spadá do nastavení zprostředkovatele, <xref:System.Configuration.SettingsProvider>třídy, která je odvozena od . Pokud odvozené třídy <xref:System.Configuration.ApplicationSettingsBase> neurčuje zprostředkovatele <xref:System.Configuration.SettingsProviderAttribute>nastavení prostřednictvím , <xref:System.Configuration.LocalFileSettingsProvider>pak se použije výchozí zprostředkovatel, , .

 Konfigurační systém, který byl původně vydán s rozhraním .NET Framework, podporuje poskytování statických `app.`konfiguračních dat aplikací prostřednictvím souboru machine.config místního počítače nebo v rámci souboru exe.config, který nasadíte s aplikací. Třída <xref:System.Configuration.LocalFileSettingsProvider> rozšiřuje tuto nativní podporu následujícími způsoby:

- Nastavení s rozsahem aplikace lze uložit v souborech machine.config nebo `app.`exe.config. Machine.config je vždy jen `app`pro čtení, zatímco .exe.config je omezen aspekty zabezpečení pro většinu aplikací.

- Nastavení s uživatelským rozsahem `app`lze uložit do souborů .exe.config, v takovém případě jsou považována za statické výchozí hodnoty.

- Nastavení s nevýchozím uživatelským rozsahem jsou uložena v novém souboru *user*.config, kde *uživatelem* je uživatelské jméno osoby, která právě provádí aplikaci. Můžete určit výchozí nastavení s rozsahem <xref:System.Configuration.DefaultSettingValueAttribute>uživatele s . Vzhledem k tomu, že nastavení `user`s rozsahem uživatele se často mění během provádění aplikace, .config je vždy čtení a zápis.

 Všechny tři konfigurační soubory ukládají nastavení ve formátu XML. Element XML nejvyšší úrovně pro nastavení s `<appSettings>`rozsahem aplikace je , zatímco `<userSettings>` se používá pro nastavení s rozsahem uživatele. Soubor `app`.exe.config, který obsahuje jak nastavení s rozsahem aplikace, tak výchozí hodnoty pro nastavení s rozsahem uživatele, bude vypadat takto:

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

 Definici prvků v části Nastavení aplikace v konfiguračním souboru naleznete [v tématu Schéma nastavení aplikace](../../configure-apps/file-schema/application-settings-schema.md).

### <a name="settings-bindings"></a>Vazby nastavení
 Nastavení aplikace používá architekturu datové vazby windows forms k poskytování obousměrné komunikace aktualizací nastavení mezi objektem nastavení a součástmi. Pokud použijete Visual Studio k vytvoření nastavení aplikace a přiřadit je k vlastnostem komponenty, tyto vazby jsou generovány automaticky.

 Nastavení aplikace lze svázat pouze s <xref:System.Windows.Forms.IBindableComponent> komponentou, která podporuje rozhraní. Komponenta musí také implementovat událost změny pro určitou vázanou vlastnost nebo <xref:System.ComponentModel.INotifyPropertyChanged> upozornit nastavení aplikace, že vlastnost změnila prostřednictvím rozhraní. Pokud součást neimplementuje <xref:System.Windows.Forms.IBindableComponent> a jsou vazby prostřednictvím sady Visual Studio, vázané vlastnosti budou nastaveny poprvé, ale nebude aktualizovat. Pokud komponenta <xref:System.Windows.Forms.IBindableComponent> implementuje, ale nepodporuje oznámení o změně vlastností, vazba se při změně vlastnosti neaktualizuje v souboru nastavení.

 Některé součásti windows forms, například <xref:System.Windows.Forms.ToolStripItem>, nepodporují vazby nastavení.

### <a name="settings-serialization"></a>Serializace nastavení
 Když <xref:System.Configuration.LocalFileSettingsProvider> je nutné uložit nastavení na disk, provede následující akce:

1. Používá reflexe prozkoumat všechny vlastnosti definované na <xref:System.Configuration.ApplicationSettingsBase> odvozené třídy, hledání těch, které jsou použity s buď <xref:System.Configuration.ApplicationScopedSettingAttribute> nebo <xref:System.Configuration.UserScopedSettingAttribute>.

2. Serializuje vlastnost na disk. Nejprve se pokusí <xref:System.ComponentModel.TypeConverter.ConvertToString%2A> volat <xref:System.ComponentModel.TypeConverter.ConvertFromString%2A> nebo na typ <xref:System.ComponentModel.TypeConverter>je přidružený . Pokud se to nepodaří, použije serializaci XML místo.

3. Určuje, která nastavení se na základě atributu nastavení přejdou do kterých souborů.

 Pokud implementujete vlastní třídu <xref:System.Configuration.SettingsSerializeAsAttribute> nastavení, můžete použít k označení nastavení <xref:System.Configuration.SettingsSerializeAs> pro binární nebo vlastní serializace pomocí výčtu. Další informace o vytvoření vlastní třídy nastavení v kódu naleznete v [tématu How to: Create Application Settings](how-to-create-application-settings.md).

### <a name="settings-file-locations"></a>Nastavení umístění souborů
 Umístění souborů `app`.exe.config a *user*.config se bude lišit v závislosti na způsobu instalace aplikace. U aplikace založené na formulářích Windows Forms `app`zkopírované do místního počítače bude soubor .exe.config umístěn ve stejném adresáři jako základní adresář hlavního <xref:System.Windows.Forms.Application.LocalUserAppDataPath%2A?displayProperty=nameWithType> spustitelného souboru aplikace a *uživatel*.config bude umístěn v umístění určeném vlastností. Pro aplikaci nainstalovanou pomocí ClickOnce budou oba tyto soubory umístěny v datovém adresáři\\ClickOnce pod*uživatelem*%InstallRoot%\Documents and Settings \Local Settings.

 Umístění těchto souborů v úložišti se mírně liší, pokud uživatel povolil cestovní profily, což umožňuje uživateli definovat různá nastavení systému Windows a aplikací, pokud používají jiné počítače v doméně. V takovém případě budou mít aplikace ClickOnce i `app`aplikace bez funkce ClickOnce uložené soubory .exe.config a\\ *uživatelské*soubory .config pod položkou %InstallRoot%\Documents and Settings*s uživatelským jménem*\Application Data.

 Další informace o tom, jak funkce Nastavení aplikace funguje s novou technologií nasazení, naleznete v [tématu ClickOnce a Application Settings](/visualstudio/deployment/clickonce-and-application-settings). Další informace o adresáři dat ClickOnce naleznete [v tématu Přístup k místním a vzdáleným datům v aplikacích ClickOnce](/visualstudio/deployment/accessing-local-and-remote-data-in-clickonce-applications).

## <a name="application-settings-and-security"></a>Nastavení aplikace a zabezpečení
 Nastavení aplikace jsou navržena tak, aby fungovala v částečném vztahu důvěryhodnosti, což je prostředí s omezeným přístupem, které je výchozí pro aplikace systému Windows Forms hostované přes Internet nebo intranet. K použití nastavení aplikace s výchozím poskytovatelem nastavení nejsou potřebná žádná zvláštní oprávnění nad rámec částečné důvěryhodnosti.

 Při použití nastavení aplikace clickonce v `user`aplikaci ClickOnce je soubor .config uložen v datovém adresáři ClickOnce. Velikost souboru `user`.config aplikace nesmí překročit kvótu datového adresáře nastavenou službou ClickOnce. Další informace naleznete v [tématech ClickOnce a Application Settings](/visualstudio/deployment/clickonce-and-application-settings).

## <a name="custom-settings-providers"></a>Zprostředkovatelé vlastních nastavení
 V architektuře Nastavení aplikace je volná vazba mezi třídou obálky nastavení aplikací odvozenou z <xref:System.Configuration.ApplicationSettingsBase>aplikace <xref:System.Configuration.SettingsProvider>a přidruženým zprostředkovatelem nebo zprostředkovateli nastavení odvozeným z . Toto přidružení je <xref:System.Configuration.SettingsProviderAttribute> definováno pouze aplikovanou třídou obálky nebo jejími jednotlivými vlastnostmi. Pokud není explicitně zadán poskytovatel nastavení, <xref:System.Configuration.LocalFileSettingsProvider>použije se výchozí zprostředkovatel , . V důsledku toho tato architektura podporuje vytváření a používání vlastních poskytovatelů nastavení.

 Předpokládejme například, že chcete `SqlSettingsProvider`vyvíjet a používat zprostředkovatele , který bude ukládat všechna data nastavení v databázi serveru Microsoft SQL Server. Vaše <xref:System.Configuration.SettingsProvider>-derived třídy obdrží `Initialize` tyto informace ve <xref:System.Collections.Specialized.NameValueCollection?displayProperty=nameWithType>své metodě jako parametr typu . Potom byste implementovat metodu <xref:System.Configuration.SettingsProvider.GetPropertyValues%2A> načíst nastavení z <xref:System.Configuration.SettingsProvider.SetPropertyValues%2A> úložiště dat a uložit je. Váš poskytovatel můžete <xref:System.Configuration.SettingsPropertyCollection> použít <xref:System.Configuration.SettingsProvider.GetPropertyValues%2A> zadaný k určení názvu vlastnosti, typ a obor, stejně jako všechny další atributy nastavení definované pro tuto vlastnost.

 Váš zprostředkovatel bude muset implementovat jednu vlastnost a jednu metodu, jejíž implementace nemusí být zřejmé. Vlastnost <xref:System.Configuration.SettingsProvider.ApplicationName%2A> je abstraktní vlastností <xref:System.Configuration.SettingsProvider>; měli byste jej naprogramovat tak, aby vrátil následující:

 [!code-csharp[ApplicationSettings.Architecture#2](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#2)]
 [!code-vb[ApplicationSettings.Architecture#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#2)]

 Odvozená třída musí také `Initialize` implementovat metodu, která nepřijímá žádné argumenty a vrací žádnou hodnotu. Tato metoda není <xref:System.Configuration.SettingsProvider>definována .

 Nakonec implementujete <xref:System.Configuration.IApplicationSettingsProvider> na poskytovatele poskytovat podporu pro aktualizaci nastavení, obnovení nastavení na jejich výchozí nastavení a upgrade nastavení z jedné verze aplikace do jiné.

 Po implementaci a kompilaci zprostředkovatele, budete muset pokyn vaše nastavení třídy používat tohoto zprostředkovatele namísto výchozí. Můžete dosáhnout prostřednictvím <xref:System.Configuration.SettingsProviderAttribute>. Pokud se použije na celou třídu nastavení, zprostředkovatel se používá pro každé nastavení, které definuje třídu; Pokud se použije na jednotlivá nastavení, architektura Nastavení <xref:System.Configuration.LocalFileSettingsProvider> aplikace používá tohoto zprostředkovatele pouze pro tato nastavení a používá pro zbytek. Následující příklad kódu ukazuje, jak dát pokyn třídě nastavení, aby používala vlastního zprostředkovatele.

 [!code-csharp[ApplicationSettings.Architecture#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#1)]
 [!code-vb[ApplicationSettings.Architecture#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#1)]

 Zprostředkovatel může být volána z více vláken současně, ale bude vždy zapisovat do stejného umístění úložiště; proto architektura nastavení aplikace bude vždy vytvořit instanci pouze jednu instanci třídy vašeho zprostředkovatele.

> [!IMPORTANT]
> Měli byste zajistit, že váš zprostředkovatel je bezpečný pro přístup z více vláken a umožňuje pouze jedno vlákno najednou zapisovat do konfiguračních souborů.

 Zprostředkovatel nemusí podporovat všechny atributy nastavení definované v <xref:System.Configuration?displayProperty=nameWithType> oboru názvů, i když <xref:System.Configuration.ApplicationScopedSettingAttribute> musí <xref:System.Configuration.UserScopedSettingAttribute>podporovat minimální <xref:System.Configuration.DefaultSettingValueAttribute>a , a měl by také podporovat . Pro tyto atributy, které nepodporuje, váš poskytovatel by měl prostě selhat bez oznámení; by neměl vyvolat výjimku. Pokud třída nastavení používá neplatnou kombinaci atributů, ale – například použití <xref:System.Configuration.ApplicationScopedSettingAttribute> a <xref:System.Configuration.UserScopedSettingAttribute> stejné nastavení – zprostředkovatel by měl vyvolat výjimku a ukončit provoz.

## <a name="see-also"></a>Viz také

- <xref:System.Configuration.ApplicationSettingsBase>
- <xref:System.Configuration.SettingsProvider>
- <xref:System.Configuration.LocalFileSettingsProvider>
- [Přehled nastavení aplikace](application-settings-overview.md)
- [Nastavení aplikace pro vlastní ovládací prvky](application-settings-for-custom-controls.md)
- [ClickOnce a nastavení aplikace](/visualstudio/deployment/clickonce-and-application-settings)
- [Schéma nastavení aplikace](../../configure-apps/file-schema/application-settings-schema.md)
