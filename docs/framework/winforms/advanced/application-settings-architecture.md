---
title: "Architektura nastavení aplikace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: application settings [Windows Forms], architecture
ms.assetid: c8eb2ad0-fac6-4ea2-9140-675a4a44d562
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9c437f305b847ff7922c98b4917e86ebd39ee100
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="application-settings-architecture"></a>Architektura nastavení aplikace
Toto téma popisuje, jak funguje architektura nastavení aplikace a jsou zde popsány pokročilé funkce architektury, jako jsou seskupené nastavení a nastavení klíče.  
  
 Architektura nastavení aplikace podporuje definující silného typu nastavení s aplikací nebo oboru uživatele a uložením nastavení mezi relacemi aplikace. Architektura poskytuje výchozí trvalost modul pro ukládání nastavení a jejich načtení z místního systému souborů. Architektura také definuje rozhraní pro zadávání vlastního modulu.  
  
 Rozhraní jsou k dispozici, které umožňují vlastní součásti se zachovat jejich vlastní nastavení, když jsou hostované v aplikaci. Pomocí nastavení klíčů součásti můžete oddělit nastavení pro více instancí součásti.  
  
## <a name="defining-settings"></a>Definování nastavení  
 Architektura nastavení aplikace se používá v rámci obě [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] a Windows Forms a obsahuje počet základní třídy, které se sdílí v obou prostředích. Nejdůležitější je <xref:System.Configuration.SettingsBase>, který poskytuje přístup k nastavení v kolekci a poskytuje metody, nízké úrovně pro načítání a ukládá se nastavení. Každé prostředí implementuje vlastní třídy odvozené od <xref:System.Configuration.SettingsBase> nabízí funkce další nastavení pro prostředí. V aplikaci na základě formulářů Windows, musí být definovaný všechna nastavení aplikace pro třídy odvozené od <xref:System.Configuration.ApplicationSettingsBase> třída, která přidá následující funkce základní třídy:  
  
-   Načítání vyšší úrovně a ukládání operace  
  
-   Podpora pro nastavení rozsahu uživatele  
  
-   Vrácení nastavení uživatele na předdefinované výchozí hodnoty  
  
-   Upgrade nastavení z předchozí verze aplikace  
  
-   Ověření nastavení, než jsou změněna nebo před jsou uloženy  
  
 Nastavení lze popsat pomocí několik atributů, které jsou definované v rámci <xref:System.Configuration> obor názvů; tyto možnosti jsou popsány v [atributy nastavení aplikace](../../../../docs/framework/winforms/advanced/application-settings-attributes.md). Při definování nastavení, musíte ho použít s buď <xref:System.Configuration.ApplicationScopedSettingAttribute> nebo <xref:System.Configuration.UserScopedSettingAttribute>, který popisuje, zda nastavení platí v celé aplikaci nebo jenom pro aktuálního uživatele.  
  
 Následující příklad kódu definuje třídu vlastní nastavení s jedním nastavením `BackgroundColor`.  
  
 [!code-csharp[ApplicationSettings.Create#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Create/CS/MyAppSettings.cs#1)]
 [!code-vb[ApplicationSettings.Create#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Create/VB/MyAppSettings.vb#1)]  
  
## <a name="settings-persistence"></a>Trvalost nastavení  
 <xref:System.Configuration.ApplicationSettingsBase> Třída není samotné zachovat nebo načíst nastavení; tato úloha se k nastavení poskytovatele, třída odvozená z <xref:System.Configuration.SettingsProvider>. Pokud odvozené třídy z <xref:System.Configuration.ApplicationSettingsBase> neurčuje nastavení zprostředkovatele prostřednictvím <xref:System.Configuration.SettingsProviderAttribute>, pak výchozího zprostředkovatele, <xref:System.Configuration.LocalFileSettingsProvider>, se používá.  
  
 Konfigurace systému, původně vydaná s [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] podporuje poskytuje data konfigurace statických aplikace pomocí souboru machine.config v místním počítači nebo v `app.`exe.config souboru, který nasazujete s vaše aplikace. <xref:System.Configuration.LocalFileSettingsProvider> Třída rozšíří tato nativní podpora následujícími způsoby:  
  
-   Nastavení rozsahu aplikace se dá uložit buď souboru machine.config nebo `app.`exe.config soubory. Souboru Machine.config je vždy jen pro čtení, při `app`. exe.config je omezené na základě aspekty zabezpečení jen pro čtení pro většinu aplikací.  
  
-   Nastavení rozsahu uživatele mohou být uloženy ve `app`. exe.config souborů, v takovém případě jsou považovány za statickou výchozí hodnoty.  
  
-   Jiné než výchozí nastavení uživatele nastavení ukládají do nového souboru *uživatele*.config, kde *uživatele* je uživatelské jméno osoby, které jsou aktuálně spuštěné aplikace. Můžete zadat výchozí hodnoty pro nastavení rozsahu uživatele s <xref:System.Configuration.DefaultSettingValueAttribute>. Protože uživatelských nastavení při spuštění aplikace, často mění `user`.config je vždy pro čtení a zápis.  
  
 Všechny tři konfigurační soubory uložit nastavení ve formátu XML. Element XML nejvyšší úrovně pro nastavení rozsahu aplikace je `<appSettings>`, zatímco `<userSettings>` se používá pro nastavení rozsahu uživatele. `app`. Exe.config soubor, který obsahuje nastavení pro obor aplikace a výchozí hodnoty pro nastavení rozsahu uživatele bude vypadat takto:  
  
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
  
 Definice elementů v rámci část konfiguračního souboru pro nastavení aplikace, najdete v části [aplikace – schéma nastavení](../../../../docs/framework/configure-apps/file-schema/application-settings-schema.md).  
  
### <a name="settings-bindings"></a>Nastavení vazby  
 Nastavení aplikace používá architektuře Windows Forms datové vazby k poskytnutí obousměrné komunikace aktualizace nastavení mezi objekt nastavení a součásti. Pokud používáte Visual Studio k vytvoření nastavení aplikace a přiřadit k vlastnosti součásti, jsou automaticky generovány těchto vazeb.  
  
 Nastavení aplikace můžete vázat jen na komponenty, která podporuje <xref:System.Windows.Forms.IBindableComponent> rozhraní. Navíc musí implementovat událost změny pro konkrétní vázaný vlastnost komponentu, nebo oznámit nastavení aplikace, která má vlastnost změnit prostřednictvím <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní. Pokud komponentu neimplementuje <xref:System.Windows.Forms.IBindableComponent> a vytváříte vazbu pomocí sady Visual Studio, nastaví se poprvé vázané vlastnosti, ale nebude aktualizovat. Pokud komponentu implementuje <xref:System.Windows.Forms.IBindableComponent> , ale nemá vlastnost podpora upozornění na změnu, vazba nebude aktualizovat v souboru nastavení při změně vlastnosti.  
  
 Některé součásti Windows Forms, jako například <xref:System.Windows.Forms.ToolStripItem>, nepodporují nastavení vazby.  
  
### <a name="settings-serialization"></a>Nastavení serializace  
 Když <xref:System.Configuration.LocalFileSettingsProvider> nastavení musíte uložit na disk, provede následující akce:  
  
1.  Zkontrolujte všechna vlastnosti definované na pomocí reflexe vaše <xref:System.Configuration.ApplicationSettingsBase> odvozené třídy, ty, které se použijí s buď hledání <xref:System.Configuration.ApplicationScopedSettingAttribute> nebo <xref:System.Configuration.UserScopedSettingAttribute>.  
  
2.  Serializuje vlastnost na disk. Nejprve pokusí zavolat <xref:System.ComponentModel.TypeConverter.ConvertToString%2A> nebo <xref:System.ComponentModel.TypeConverter.ConvertFromString%2A> na typ přidruženému <xref:System.ComponentModel.TypeConverter>. Pokud to nebude úspěšná, používá serializace XML místo.  
  
3.  Určuje nastavení, které v které soubory, přejděte na základě atributu název nastavení.  
  
 Pokud budete implementovat vlastní třída nastavení, můžete použít <xref:System.Configuration.SettingsSerializeAsAttribute> označit nastavení buď pomocí binary nebo vlastní serializace <xref:System.Configuration.SettingsSerializeAs> výčtu. Další informace o vytvoření vlastní třídy nastavení v kódu najdete v tématu [postupy: vytvoření nastavení aplikace](../../../../docs/framework/winforms/advanced/how-to-create-application-settings.md).  
  
### <a name="settings-file-locations"></a>Nastavení umístění souborů  
 Umístění `app`. exe.config a *uživatele*soubory .config se liší podle toho, jak je aplikace nainstalována. Pro aplikaci na základě formulářů Windows zkopírovali do místního počítače `app`. exe.config se bude nacházet ve stejném adresáři jako základního adresáře aplikace hlavní spustitelný soubor, a *uživatele*.config se bude nacházet v umístění, které <xref:System.Windows.Forms.Application.LocalUserAppDataPath%2A?displayProperty=nameWithType> vlastnost. Pro aplikaci nainstalovat prostřednictvím [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)], oba tyto soubory se bude nacházet v [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] adresář dat pod %InstallRoot%\Documents a nastavení\\*uživatelské jméno*\Local nastavení.  
  
 Umístění úložiště těchto souborů se mírně liší, pokud uživatel aktivoval cestovní profily, díky čemuž by uživatelé k definování různých Windows a nastavení aplikace, když uživatel používá jiné počítače v rámci domény. V takovém případě obě [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] aplikace a jiných-[!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] aplikace bude mít jejich `app`. exe.config a *uživatele*.config soubory uložené v části Nastavení a %InstallRoot%\Documents\\ *uživatelské jméno*\Application Data.  
  
 Další informace o fungování funkce nastavení aplikace s novou technologií nasazení najdete v tématu [ClickOnce a nastavení aplikace](/visualstudio/deployment/clickonce-and-application-settings). Další informace o [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] adresář dat najdete v části [přístup k místním a vzdáleným datům v aplikacích ClickOnce](/visualstudio/deployment/accessing-local-and-remote-data-in-clickonce-applications).  
  
## <a name="application-settings-and-security"></a>Nastavení aplikace a zabezpečení  
 Nastavení aplikace jsou navrženy pro práci v částečné důvěryhodnosti, prostředí s omezeným přístupem, které je výchozí nastavení pro aplikace Windows Forms hostované prostřednictvím Internetu nebo intranetu. Žádná zvláštní oprávnění nad rámec částečné důvěryhodnosti jsou potřeba k použití nastavení aplikace pomocí výchozího nastavení zprostředkovatele.  
  
 Při použití nastavení aplikace v [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] aplikace, `user`.config soubor je uložen v [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] datový adresář. Velikost aplikace `user`souboru .config nesmí překročit kvótu directory data, která nastavuje [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)]. Další informace najdete v tématu [ClickOnce a nastavení aplikace](/visualstudio/deployment/clickonce-and-application-settings).  
  
## <a name="custom-settings-providers"></a>Vlastní nastavení zprostředkovatele  
 V architektuře nastavení aplikace je volné párování mezi nastavení aplikací obálkovou třídu, odvozené od <xref:System.Configuration.ApplicationSettingsBase>, a související nastavení poskytovatele nebo poskytovatelů, odvozené z <xref:System.Configuration.SettingsProvider>. Toto přidružení je definována pouze pomocí <xref:System.Configuration.SettingsProviderAttribute> použít pro třídu obálky nebo jeho jednotlivé vlastnosti. Pokud zadaný zprostředkovatel není explicitně nastavení, výchozího zprostředkovatele, <xref:System.Configuration.LocalFileSettingsProvider>, se používá. V důsledku toho tato architektura podporuje vytváření a používání zprostředkovatelů vlastní nastavení.  
  
 Předpokládejme například, že chcete pro vývoj a použít `SqlSettingsProvider`, zprostředkovatele, který se uloží všechna nastavení data v databázi Microsoft SQL Server. Vaše <xref:System.Configuration.SettingsProvider>-odvozené třídy by se zobrazit tyto informace v jeho `Initialize` metoda jako parametr typu <xref:System.Collections.Specialized.NameValueCollection?displayProperty=nameWithType>. Potom by implementovat <xref:System.Configuration.SettingsProvider.GetPropertyValues%2A> metoda pro načtení nastavení z úložiště dat a <xref:System.Configuration.SettingsProvider.SetPropertyValues%2A> o jejich uložení. Můžete použít poskytovatele <xref:System.Configuration.SettingsPropertyCollection> zadané <xref:System.Configuration.SettingsProvider.GetPropertyValues%2A> k určení názvu vlastnosti, typ a oboru, stejně jako všechny ostatní atributy nastavení definované pro tuto vlastnost.  
  
 Poskytovatel bude nutné implementovat jednu vlastnost a jedna metoda, jejíž implementace nemusí být samozřejmé. <xref:System.Configuration.SettingsProvider.ApplicationName%2A> Vlastnost je abstraktní vlastnosti <xref:System.Configuration.SettingsProvider>; by ho vrátit následující program:  
  
 [!code-csharp[ApplicationSettings.Architecture#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#2)]
 [!code-vb[ApplicationSettings.Architecture#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#2)]  
  
 Odvozené třídy musí také implementovat `Initialize` metodu, která nezadávaly žádné argumenty a nevrací žádnou hodnotu. Tato metoda není definované <xref:System.Configuration.SettingsProvider>.  
  
 Nakonec implementovat <xref:System.Configuration.IApplicationSettingsProvider> na svého poskytovatele kvůli zajištění podpory pro aktualizaci nastavení vrácení nastavení na výchozí nastavení a nastavení upgrade z verze jednu aplikaci do jiného.  
  
 Po implementovat a zkompilovat svého poskytovatele, budete muset pokyn třídu pro tohoto zprostředkovatele použijte místo výchozího nastavení. Můžete dosáhnout pomocí <xref:System.Configuration.SettingsProviderAttribute>. Pokud pro celou třídu nastavení, je pro každé nastavení, která definuje třídu; používá zprostředkovatele Pokud pro jednotlivá nastavení, architektura nastavení aplikace používá tohoto zprostředkovatele pro taková nastavení pouze a <xref:System.Configuration.LocalFileSettingsProvider> pro zbytek. Následující příklad kódu ukazuje, jak se udělit pokyny třídu nastavení vlastního zprostředkovatele.  
  
 [!code-csharp[ApplicationSettings.Architecture#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ApplicationSettings.Architecture/CS/DummyClass.cs#1)]
 [!code-vb[ApplicationSettings.Architecture#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ApplicationSettings.Architecture/VB/DummyProviderClass.vb#1)]  
  
 Zprostředkovatel může být volána z více vláken současně, ale bude vždy zapisovat do stejného umístění úložiště; Architektura nastavení aplikace vytvoří instanci proto vždy jen jednu instanci třídě zprostředkovatele.  
  
> [!IMPORTANT]
>  Můžete by měl zkontrolujte, zda poskytovatel je bezpečné pro přístup z více vláken a umožňuje pouze jedno vlákno současně zapisovat do konfigurační soubory.  
  
 Poskytovatel nemusí podporovat všechny atributy definované v nastavení <xref:System.Configuration?displayProperty=nameWithType> obor názvů, i když se musí nacházet na minimální podporu <xref:System.Configuration.ApplicationScopedSettingAttribute> a <xref:System.Configuration.UserScopedSettingAttribute>a musí taky podporovat <xref:System.Configuration.DefaultSettingValueAttribute>. Pro tyto atributy, které nejsou podporovány má poskytovatel právě selhat bez oznámení; nesmí se vyvolat výjimku. Pokud třída nastavení používá neplatnou kombinaci atributů, ale – například použití <xref:System.Configuration.ApplicationScopedSettingAttribute> a <xref:System.Configuration.UserScopedSettingAttribute> na stejnou hodnotu nastavení – poskytovatel by měla vyvolat výjimku a ukončení provádění operace.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Configuration.ApplicationSettingsBase>  
 <xref:System.Configuration.SettingsProvider>  
 <xref:System.Configuration.LocalFileSettingsProvider>  
 [Přehled nastavení aplikace](../../../../docs/framework/winforms/advanced/application-settings-overview.md)  
 [Nastavení aplikace pro vlastní ovládací prvky](../../../../docs/framework/winforms/advanced/application-settings-for-custom-controls.md)  
 [ClickOnce a nastavení aplikace](/visualstudio/deployment/clickonce-and-application-settings)  
 [Schéma nastavení aplikace](../../../../docs/framework/configure-apps/file-schema/application-settings-schema.md)
