---
title: Architektura nastavení aplikace
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- application settings [Windows Forms], architecture
ms.assetid: c8eb2ad0-fac6-4ea2-9140-675a4a44d562
ms.openlocfilehash: b5d5a4456bef925cd8093fe9c696145aff83660e
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039421"
---
# <a name="application-settings-architecture"></a>Architektura nastavení aplikace
Toto téma popisuje, jak funguje architektura nastavení aplikace, a prozkoumá pokročilé funkce architektury, jako jsou například seskupená nastavení a klíče nastavení.

 Architektura nastavení aplikace podporuje definování silně typovaného nastavení s aplikací nebo uživatelským rozsahem a uchovává nastavení mezi relacemi aplikace. Architektura poskytuje výchozí modul pro trvalost pro ukládání a načítání nastavení do místního systému souborů. Architektura také definuje rozhraní pro poskytnutí vlastního modulu trvalosti.

 Rozhraní jsou k dispozici, která umožňuje vlastním součástem zachovat vlastní nastavení při jejich hostování v aplikaci. Pomocí klíčů nastavení můžou komponenty zachovat nastavení pro více instancí komponenty oddělené.

## <a name="defining-settings"></a>Definování nastavení
 Architektura nastavení aplikace se používá v rámci ASP.NET i model Windows Forms a obsahuje několik základních tříd, které jsou sdíleny napříč oběma prostředími. Nejdůležitější je <xref:System.Configuration.SettingsBase>, který poskytuje přístup k nastavením prostřednictvím kolekce, a poskytuje metody nízké úrovně pro načítání a ukládání nastavení. Každé prostředí implementuje svou vlastní třídu odvozenou <xref:System.Configuration.SettingsBase> z a poskytuje další funkce nastavení pro toto prostředí. V model Windows Forms aplikaci musí být všechna nastavení aplikace definována pro třídu odvozenou z <xref:System.Configuration.ApplicationSettingsBase> třídy, která do základní třídy přidává následující funkci:

- Operace načítání a ukládání vyšší úrovně

- Podpora nastavení s rozsahem uživatelů

- Vrácení nastavení uživatele do předdefinovaných výchozích hodnot

- Upgrade nastavení z předchozí verze aplikace

- Ověření nastavení před jejich změnou nebo před uložením

 Nastavení lze popsat pomocí určitého počtu atributů definovaných v rámci <xref:System.Configuration> oboru názvů, které jsou popsány v tématu [atributy nastavení aplikace](application-settings-attributes.md). Pokud definujete nastavení, je nutné jej použít buď <xref:System.Configuration.ApplicationScopedSettingAttribute> pomocí, nebo <xref:System.Configuration.UserScopedSettingAttribute>, který popisuje, zda nastavení platí pro celou aplikaci nebo pouze pro aktuálního uživatele.

 Následující příklad kódu definuje vlastní třídu nastavení s jedním nastavením, `BackgroundColor`.

 [!code-csharp[ApplicationSettings.Create#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/MyAppSettings.cs#1)]
 [!code-vb[ApplicationSettings.Create#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/MyAppSettings.vb#1)]

## <a name="settings-persistence"></a>Trvalá nastavení
 Třída <xref:System.Configuration.ApplicationSettingsBase> sám o sobě netrvala ani nenačítá nastavení; tato úloha spadá do zprostředkovatele nastavení, třídy, která je odvozena z. <xref:System.Configuration.SettingsProvider> Pokud odvozená třída <xref:System.Configuration.ApplicationSettingsBase> neurčuje poskytovatele nastavení <xref:System.Configuration.SettingsProviderAttribute>prostřednictvím, je použit výchozí zprostředkovatel <xref:System.Configuration.LocalFileSettingsProvider>.

 Konfigurační systém, který byl původně vydaný pomocí .NET Framework podporuje poskytování konfiguračních dat statických aplikací prostřednictvím souboru Machine. config v místním počítači nebo v `app.`souboru exe. config, který nasazujete pomocí nástroje. vaše aplikace. <xref:System.Configuration.LocalFileSettingsProvider> Třída rozšiřuje tuto nativní podporu následujícími způsoby:

- Nastavení s rozsahem aplikace může být uloženo buď v souboru Machine. config, `app.`nebo v souborech exe. config. Machine. config je vždy jen pro čtení, zatímco `app`soubor. exe. config je omezený o bezpečnostní hlediska pro většinu aplikací jen pro čtení.

- Nastavení s rozsahem uživatele lze uložit do `app`souborů. exe. config. v takovém případě jsou považovány za statické výchozí hodnoty.

- Nevýchozí nastavení s rozsahem uživatele se ukládají do nového souboru *User*. config, kde *uživatel* je uživatelské jméno osoby, která aktuálně spouští aplikaci. Pro nastavení s <xref:System.Configuration.DefaultSettingValueAttribute>rozsahem uživatele můžete zadat výchozí hodnotu. Vzhledem k tomu, že nastavení s rozsahem uživatele se často `user`mění během provádění aplikace,. config je vždy čtení a zápis.

 Všechny tři konfigurační soubory ukládají nastavení ve formátu XML. Element XML nejvyšší úrovně pro nastavení s rozsahem aplikace je `<appSettings>`, zatímco `<userSettings>` se používá pro nastavení s rozsahem uživatele. Soubor `app`. exe. config, který obsahuje nastavení s rozsahem aplikace a výchozí hodnoty pro nastavení vymezená uživatelem, by vypadal takto:

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

 Definici prvků v části nastavení aplikace konfiguračního souboru najdete v tématu [schéma nastavení aplikace](../../configure-apps/file-schema/application-settings-schema.md).

### <a name="settings-bindings"></a>Vazby nastavení
 Nastavení aplikace používá architekturu model Windows Forms datovou vazbu k zajištění obousměrné komunikace aktualizací nastavení mezi objektem nastavení a komponentami. Pokud použijete Visual Studio k vytvoření nastavení aplikace a přiřadíte je k vlastnostem komponenty, tyto vazby se generují automaticky.

 Nastavení aplikace můžete navazovat jenom na součást, která <xref:System.Windows.Forms.IBindableComponent> rozhraní podporuje. Komponenta také musí implementovat událost změny pro konkrétní vázanou vlastnost nebo upozorní nastavení aplikace, že se vlastnost prostřednictvím <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní změnila. Pokud komponenta neimplementuje <xref:System.Windows.Forms.IBindableComponent> a vytváříte vazbu prostřednictvím sady Visual Studio, vlastnosti vazeb budou nastaveny poprvé, ale nebudou aktualizovány. Pokud komponenta implementuje <xref:System.Windows.Forms.IBindableComponent> , ale nepodporuje upozornění na změnu vlastností, vazba nebude aktualizována v souboru nastavení při změně vlastnosti.

 Některé součásti model Windows Forms, například <xref:System.Windows.Forms.ToolStripItem>, nepodporují vazby nastavení.

### <a name="settings-serialization"></a>Serializace nastavení
 Pokud <xref:System.Configuration.LocalFileSettingsProvider> musí nastavení uložit na disk, provede následující akce:

1. Používá reflexi k prohlédnutí všech vlastností definovaných v <xref:System.Configuration.ApplicationSettingsBase> odvozené třídě a hledání těch, které jsou použity s <xref:System.Configuration.ApplicationScopedSettingAttribute> buď <xref:System.Configuration.UserScopedSettingAttribute>nebo.

2. Zaserializace vlastnosti na disk. Nejprve se pokusí zavolat <xref:System.ComponentModel.TypeConverter.ConvertToString%2A> nebo <xref:System.ComponentModel.TypeConverter.ConvertFromString%2A> na přidruženém <xref:System.ComponentModel.TypeConverter>typu. Pokud tato operace není úspěšná, používá místo toho serializaci XML.

3. Určuje, která nastavení se mají použít v závislosti na atributu nastavení.

 Pokud implementujete vlastní třídu nastavení, můžete použít <xref:System.Configuration.SettingsSerializeAsAttribute> k označení nastavení pro binární nebo vlastní serializaci <xref:System.Configuration.SettingsSerializeAs> pomocí výčtu. Další informace o tom, jak vytvořit vlastní třídu nastavení v kódu, [naleznete v tématu How to: Vytvořte nastavení](how-to-create-application-settings.md)aplikace.

### <a name="settings-file-locations"></a>Umístění souborů nastavení
 Umístění `app`souborů. exe. config a *User*. config se bude lišit podle toho, jak je aplikace nainstalovaná. Aby byla aplikace založená na model Windows Forms zkopírována do místního počítače, `app`soubor. exe. config bude umístěn ve stejném adresáři jako základní adresář hlavního spustitelného souboru aplikace a *uživatel*. config bude umístěn v umístění určeném parametrem <xref:System.Windows.Forms.Application.LocalUserAppDataPath%2A?displayProperty=nameWithType> vlastnost. Pro aplikaci nainstalovanou pomocí technologie ClickOnce se oba tyto soubory nacházejí v adresáři dat ClickOnce pod%InstallRoot%\Documents a\\nastavení*uživatelské jméno*\Local.

 Umístění úložiště těchto souborů se mírně liší, pokud uživatel povolil cestovní profily, což uživateli umožňuje definovat různá nastavení systému Windows a aplikace, když používá jiné počítače v doméně. V takovém případě aplikace ClickOnce i aplikace bez ClickOnce `app`budou mít soubory. exe. config a *User*. config uložené v%InstallRoot%\Documents a nastavení\\*username*\Application Data.

 Další informace o tom, jak funkce nastavení aplikace funguje s novou technologií nasazení, naleznete v tématu [ClickOnce a nastavení aplikace](/visualstudio/deployment/clickonce-and-application-settings). Další informace o adresáři dat ClickOnce naleznete [v tématu přístup k místním a vzdáleným datům v aplikacích ClickOnce](/visualstudio/deployment/accessing-local-and-remote-data-in-clickonce-applications).

## <a name="application-settings-and-security"></a>Nastavení aplikace a zabezpečení
 Nastavení aplikace jsou navržená tak, aby fungovala v částečném vztahu důvěryhodnosti, což je omezené prostředí, které je výchozím nastavením pro model Windows Forms aplikací hostovaných po internetu nebo intranetu. K použití nastavení aplikace s výchozím zprostředkovatelem nastavení nejsou nutná žádná zvláštní oprávnění nad rámec částečné důvěryhodnosti.

 Při použití nastavení aplikace v aplikaci `user`ClickOnce je soubor. config uložen v adresáři dat ClickOnce. Velikost konfiguračního souboru aplikace `user`nemůže přesáhnout kvótu datového adresáře nastavenou ClickOnce. Další informace naleznete v tématu [ClickOnce a nastavení aplikace](/visualstudio/deployment/clickonce-and-application-settings).

## <a name="custom-settings-providers"></a>Poskytovatelé vlastních nastavení
 V architektuře nastavení aplikace existuje volné propojení mezi obálkovou třídou nastavení aplikace, odvozená od <xref:System.Configuration.ApplicationSettingsBase>a přidruženého poskytovatele nebo zprostředkovatelů nastavení odvozený od. <xref:System.Configuration.SettingsProvider> Toto přidružení je definováno pouze <xref:System.Configuration.SettingsProviderAttribute> aplikovanou na obálkovou třídu nebo její jednotlivé vlastnosti. Pokud není explicitně zadaný zprostředkovatel nastavení, použije se výchozí zprostředkovatel <xref:System.Configuration.LocalFileSettingsProvider>. V důsledku toho tato architektura podporuje vytváření a používání poskytovatelů vlastních nastavení.

 Předpokládejme například, že chcete vyvinout a použít `SqlSettingsProvider`poskytovatele, který bude ukládat všechna data nastavení do databáze Microsoft SQL Server. Vaše <xref:System.Configuration.SettingsProvider>odvozená třída obdrží tyto informace `Initialize` v metodě jako parametr typu <xref:System.Collections.Specialized.NameValueCollection?displayProperty=nameWithType>. Pak implementujete <xref:System.Configuration.SettingsProvider.GetPropertyValues%2A> metodu, která načte vaše nastavení z úložiště dat, a <xref:System.Configuration.SettingsProvider.SetPropertyValues%2A> uložte je. Váš poskytovatel může použít <xref:System.Configuration.SettingsPropertyCollection> dodaný pro <xref:System.Configuration.SettingsProvider.GetPropertyValues%2A> k určení názvu vlastnosti, typu a oboru, jakož i všech dalších atributů nastavení definovaných pro tuto vlastnost.

 Váš poskytovatel bude muset implementovat jednu vlastnost a jednu metodu, jejíž implementace nemusí být zjevné. Vlastnost je abstraktní vlastnost třídy <xref:System.Configuration.SettingsProvider>. měli byste programovat, aby vracela následující: <xref:System.Configuration.SettingsProvider.ApplicationName%2A>

 [!code-csharp[ApplicationSettings.Architecture#2](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#2)]
 [!code-vb[ApplicationSettings.Architecture#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#2)]

 Vaše odvozená třída musí také implementovat `Initialize` metodu, která nepřijímá žádné argumenty a nevrací žádnou hodnotu. Tato metoda není definována nástrojem <xref:System.Configuration.SettingsProvider>.

 Nakonec implementujete <xref:System.Configuration.IApplicationSettingsProvider> na svého poskytovatele, abyste mohli poskytovat podporu pro aktualizaci nastavení, vrácení nastavení na výchozí hodnoty a upgrade nastavení z jedné verze aplikace na jinou.

 Po implementaci a zkompilování poskytovatele je potřeba, aby vaše třída nastavení používala tohoto poskytovatele namísto výchozího. Můžete to provést prostřednictvím <xref:System.Configuration.SettingsProviderAttribute>. Při použití na celou třídu nastavení se poskytovatel používá pro každé nastavení, které třída definuje. Při použití na jednotlivá nastavení používá architektura nastavení aplikace tohoto poskytovatele pouze pro tato nastavení a používá <xref:System.Configuration.LocalFileSettingsProvider> se pro zbytek. Následující příklad kódu ukazuje, jak instruovat třídu nastavení, aby používala vlastního zprostředkovatele.

 [!code-csharp[ApplicationSettings.Architecture#1](~/samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#1)]
 [!code-vb[ApplicationSettings.Architecture#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#1)]

 Zprostředkovatele lze volat z více vláken současně, ale bude vždy zapisovat do stejného umístění úložiště; Proto architektura nastavení aplikace vždy vytvoří instanci jedné instance třídy poskytovatele.

> [!IMPORTANT]
>  Měli byste zajistit, aby byl váš poskytovatel bezpečný pro přístup z více vláken, a v jednom okamžiku umožňuje zapisovat do konfiguračních souborů.

 Váš poskytovatel nemusí podporovat všechny <xref:System.Configuration?displayProperty=nameWithType> atributy nastavení definované v oboru názvů, i když musí podporovat minimální podporu <xref:System.Configuration.ApplicationScopedSettingAttribute> a <xref:System.Configuration.UserScopedSettingAttribute>a měla by také podporovat <xref:System.Configuration.DefaultSettingValueAttribute>. U těch atributů, které nepodporuje, by váš poskytovatel měl být neúspěšný bez oznámení; neměl by vyvolat výjimku. Pokud třída nastavení používá neplatnou kombinaci atributů, jako je například použití <xref:System.Configuration.ApplicationScopedSettingAttribute> a <xref:System.Configuration.UserScopedSettingAttribute> ke stejnému nastavení – váš poskytovatel by měl vyvolat výjimku a zastavit operaci.

## <a name="see-also"></a>Viz také:

- <xref:System.Configuration.ApplicationSettingsBase>
- <xref:System.Configuration.SettingsProvider>
- <xref:System.Configuration.LocalFileSettingsProvider>
- [Přehled nastavení aplikace](application-settings-overview.md)
- [Nastavení aplikace pro vlastní ovládací prvky](application-settings-for-custom-controls.md)
- [ClickOnce a nastavení aplikace](/visualstudio/deployment/clickonce-and-application-settings)
- [Schéma nastavení aplikace](../../configure-apps/file-schema/application-settings-schema.md)
