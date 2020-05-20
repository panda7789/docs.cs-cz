---
title: Migrace Windows 10
description: Hluboká podrobně v funkcích Windows 10, jako je například balení a kódování na ostrovech XAML.
ms.date: 09/16/2019
ms.openlocfilehash: cd17088b086a32fd3bb37e617d3a1047acedde0e
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83423206"
---
# <a name="windows-10-migration"></a>Migrace Windows 10

Vezměte v úvahu následující situaci: máte pracovní desktopovou aplikaci, která byla vyvinuta v systému Windows 7 dnů. Používá technologii WPF dostupnou v daném čase a funguje správně, ale má zastaralé uživatelské rozhraní a chování při spuštění ve Windows 10. Vypadá to jako při sledování Futuristic filmu jako matice a vidíte Neo pomocí zařízení Nokia 8110. Film funguje Skvělé po 20 letech, ale místo toho by měla těžit z modernizace zařízení.

S vydáním Windows 10 Společnost Microsoft představila mnoho inovací pro podporu scénářů, jako jsou tablety a dotyková zařízení, a poskytuje tak nejlepší možnosti pro uživatele v operačním systému Microsoftu. Můžete například provést následující věci:

- Přihlaste se s využitím svého obličeje pomocí Windows Hello.
- Použijte pero k nakreslení nebo ručnímu psaní textu, který se automaticky rozpozná a digitálně.
- Spouštějte místně přizpůsobené modely AI založené na cloudu pomocí WinML.

Všechny tyto funkce jsou povolené pro vývojáře v systému Windows prostřednictvím knihoven prostředí Windows Runtime (WinRT). Tyto funkce můžete využít ve stávajících aplikacích klasické pracovní plochy, protože knihovny jsou zpřístupněny i pro .NET Framework i .NET Core. Můžete dokonce modernizovat své uživatelské rozhraní pomocí jazyka XAML a zlepšit vizuály a chování vašich aplikací podle času.

Jednou z důležitých věcí, které je třeba poznamenat, je, že nemusíte opustit .NET Framework technologie, abyste mohli postupovat podle této cesty k modernizaci. V této části můžete bezpečně zůstat a mít všechny výhody Windows 10 bez přítlaku na migraci do .NET Core. Získáte tedy i flexibilitu a možnost zvolit si cestu k modernizaci.

## <a name="winrt-apis"></a>Rozhraní API WinRT

Rozhraní API WinRT jsou objektově orientované a strukturované aplikační programovací rozhraní (API), které vývojářům Windows 10 poskytují přístup ke všemu, co nabízí operační systém. Prostřednictvím rozhraní API WinRT můžete integrovat funkce, jako jsou nabízená oznámení, rozhraní API pro zařízení, Microsoft Ink a WinML, a to mimo jiné na vaše desktopové aplikace.

Obecně platí, že rozhraní API WinRT je možné volat z klasické desktopové aplikace. Existují však dvě hlavní oblasti s výjimkou pro toto pravidlo:

* Rozhraní API, která vyžadují identitu balíčku.
* Rozhraní API, která vyžadují vizualizaci, jako je XAML nebo složení.

### <a name="universal-windows-platform-uwp-packages"></a>Balíčky Univerzální platforma Windows (UWP)

#### <a name="application-package-identity"></a>Identita balíčku aplikace

Aplikace pro UWP mají systém nasazení, ve kterém operační systém spravuje instalaci a odinstalaci aplikace. To vyžaduje deklarativní instalaci, což znamená, že během instalace není proveden žádný uživatelský kód. Místo toho je v manifestu aplikace deklarována vše, co aplikace chce integrovat se systémem, jako jsou protokoly, typy souborů a rozšíření. V době nasazení nakonfiguruje kanál nasazení tyto integrační body. Jediným způsobem, jak operační systém spravovat všechny tyto funkce a sledovat, je pro každý balíček, aby měl identitu, jedinečný identifikátor pro aplikaci.

Některá rozhraní WinRT API vyžadují, aby tato identita balíčku fungovala podle očekávání. Klasické desktopové aplikace, jako jsou nativní aplikace C++ nebo .NET, ale používají různé systémy nasazení, které nevyžadují identitu balíčku. Pokud chcete tato rozhraní API WinRT použít v desktopové aplikaci, musíte jim poskytnout identitu balíčku.

Jedním ze způsobů, jak pokračovat, je sestavit další balící projekt. V rámci balícího projektu odkazujete na původní projekt zdrojového kódu a určíte informace o identitě, kterou chcete poskytnout.Pokud balíček nainstalujete a spustíte nainstalovanou aplikaci, automaticky se získá identifikace umožňující vašemu kódu volat všechna rozhraní API WinRT vyžadující identitu.

```xml
<?xml version="1.0" encoding="utf-8"?>
<Package xmlns="http://schemas.microsoft.com/appx/manifest/foundation/windows10"
         xmlns:uap="http://schemas.microsoft.com/appx/manifest/uap/windows10">
    <Identity Name="YOUR-APP-GUID "
              Publisher="CN=YOUR COMPANY"
              Version="1.x.x.x" />
</Package>
```

Pomocí kontroly, jestli je typ obsahující rozhraní API označený atributem [DualApiPartition](xref:Windows.Foundation.Metadata.DualApiPartitionAttribute) , můžete zkontrolovat, která rozhraní API potřebují zabalené identity aplikace.Pokud je, můžete zavolat, pokud z nebalené tradiční desktopové aplikace. V opačném případě je nutné převést klasickou desktopovou aplikaci na UWP pomocí balícího projektu.

<https://docs.microsoft.com/windows/desktop/apiindex/uwp-apis-callable-from-a-classic-desktop-app>

#### <a name="benefits-of-packaging"></a>Výhody balení

Kromě udělení přístupu k těmto rozhraním API získáte další výhody vytvořením balíčku aplikace pro Windows pro vaši desktopovou aplikaci, včetně:

* **Zjednodušené nasazení**. Aplikace mají Skvělé prostředí pro nasazení, které zajišťuje, aby si uživatelé mohli bez obav nainstalovat aplikaci a aktualizovat ji. Pokud se uživatel rozhodne aplikaci odinstalovat, je zcela odebrána bez trasování, které brání problému s Windows hnilobou.

* **Automatické aktualizace a licencování**. Vaše aplikace se může účastnit integrovaných funkcí licencování a automatických aktualizací Microsoft Store. Automatická aktualizace je vysoce spolehlivý a efektivní mechanismus, protože se stáhnou jenom změněné části souborů.

* **Zvýšení dosahu a zjednodušení finanční zhodnocení** Možná se nejedná o váš případ, ale pokud se rozhodnete distribuovat aplikaci prostřednictvím Microsoft Store dostanete miliony uživatelů s Windows 10.

* **Přidejte funkce UWP**. Do balíčku vaší aplikace můžete přidat funkce UWP vaším vlastním tempem.

#### <a name="prepare-for-packaging"></a>Příprava na balení

Než budete pokračovat v zabalení aplikace klasické pracovní plochy, je nutné před zahájením procesu vyřešit několik bodů. Vaše aplikace musí respektovat všechna pravidla Microsoft Store a zásady a spouštět je v aplikačním modelu UWP. Například musí běžet na .NET Framework 4.6.2 nebo novějším a zapisuje se do `HKEY_CURRENT_USER` podregistru a složky s tímto rozhraním budou virtualizované na místní umístění aplikace specifické pro uživatele.

Cílem pro sbalení je oddělit stav aplikace od stavu systému a současně zachovat kompatibilitu s jinými aplikacemi. Windows 10 tento cíl dosahuje umístěním aplikace do balíčku UWP. Detekuje a přesměruje některé změny v systému souborů a v registru za běhu, aby splnily příslib důvěryhodného a čistého chování instalace a odinstalace aplikace poskytované balíčkem.

Balíčky, které vytvoříte pro desktopovou aplikaci, jsou aplikace s plnou důvěryhodností, které nejsou v izolovaném prostoru (sandbox), i když je v aplikaci odlehčená virtualizace, která se používá pro zápisy do `HKCU` a `AppData` . Tato virtualizace umožňuje interakci s ostatními aplikacemi stejným způsobem jako klasické aplikace klasické pracovní plochy.

##### <a name="installation"></a>Instalace

Balíčky aplikací jsou nainstalovány ve složce *% ProgramFiles% \\ WindowsApps \\ package_name*s názvem souboru  `app_name.exe` . Každá složka balíčku obsahuje manifest (pojmenovaný `AppxManifest.xml` ), který obsahuje speciální obor názvů XML pro zabalené aplikace. Uvnitř tohoto souboru manifestu je  `<EntryPoint>`   prvek, který odkazuje na aplikaci s úplným vztahem důvěryhodnosti. Při spuštění aplikace se nespustí v kontejneru aplikace, ale místo toho se spustí jako uživatel normálně.

Po nasazení jsou soubory balíčku označené jen pro čtení a silně uzamčeny operačním systémem. Systém Windows zabraňuje spuštění aplikací, pokud jsou tyto soubory úmyslně poškozeny.

##### <a name="file-system"></a>Systém souborů

OPERAČNÍ systém podporuje různé úrovně operací se systémem souborů pro zabalené desktopové aplikace v závislosti na umístění složky.

Když se pokusíte o přístup ke *složce s* uživatelskými rozhraními, systém vytvoří pro jednotlivé aplikace na pozadí privátní umístění jednotlivých uživatelů. Tím se vytvoří iluze, kterou zabalená aplikace upravuje v *reálném čase* , když je skutečně upravována soukromá kopie. Změnou přesměrování tímto způsobem může systém sledovat všechny změny souborů provedené aplikací. Pak může vyčistit všechny tyto soubory při odinstalaci systému snižovat "hnilobu" a zajistit tak lepší prostředí pro odebrání aplikací pro uživatele.

##### <a name="registry"></a>Registr

Balíčky aplikací obsahují soubor Registry. dat, který slouží jako logický ekvivalent  `HKLM\Software`   v reálném registru. V době běhu tento virtuální registr sloučí obsah tohoto podregistru do nativního systémového podregistru, aby poskytoval jednotné zobrazení v rámci obou.

Všechna zápisy se uchovávají během upgradu balíčku a odstraňují se jenom při odinstalaci aplikace.

##### <a name="uninstallation"></a>Odinstalace

Když uživatel odinstaluje balíček, odeberou se všechny soubory a složky  `C:\Program Files\WindowsApps\package_name` , které jsou umístěné v části, i všechny přesměrované zápisy na data nebo Registry zaznamenané během procesu.

Podrobnosti o tom, jak zabalená aplikace zpracovává instalaci, přístup k souborům, registr a odinstalaci, najdete v tématu <https://docs.microsoft.com/windows/msix/desktop/desktop-to-uwp-behind-the-scenes> .

Můžete získat úplný seznam věcí, které byste měli kontrolovat <https://docs.microsoft.com/windows/msix/desktop/desktop-to-uwp-prepare> .

## <a name="how-to-add-winrt-apis-to-your-desktop-project"></a>Postup přidání rozhraní API WinRT do desktopového projektu

V této části najdete návod, jak integrovat informační oznámení do existující aplikace WPF. I když je v perspektivě kódu jednoduché, pomůže ilustrovat celý proces. Oznámení jsou jedním z dostupných dostupných rozhraní API WinRT, která můžete použít v aplikaci .NET. V takovém případě rozhraní API vyžaduje identitu balíčku. Tento proces je složitější, pokud rozhraní API nevyžadují identitu balíčku.

Pojďme si nechat existující ukázkovou aplikaci WPF, která načte soubory a zobrazí její obsah na obrazovce. Cílem je zobrazit informační zprávy při spuštění aplikace.

![Snímek obrazovky se spuštěnou ukázkovou aplikací](./media/windows-migration/sample-application.png)

Nejdřív byste měli vrátit následující odkaz na to, jestli rozhraní Windows 10 API, které budete používat, vyžaduje identitu balíčku:

<https://docs.microsoft.com/windows/apps/desktop/modernize/desktop-to-uwp-supported-api>

Naše ukázka bude používat <xref:Windows.UI.Notifications.Notification?displayProperty=nameWithType> rozhraní API, které vyžaduje zabalenou identitu:

![Třída oznámení v dokumentaci Microsoftu](./media/windows-migration/notification-class-documentation.png)

Pokud chcete získat přístup k rozhraní API WinRT, přidejte odkaz na `Microsoft.Windows.SDK.Contracts`   balíček NuGet a tento balíček provede Magic na pozadí (viz podrobnosti na adrese <https://blogs.windows.com/windowsdeveloper/2019/04/30/calling-windows-10-apis-from-a-desktop-application-just-got-easier/> ).

Teď jste připraveni začít přidávat nějaký kód.

Vytvořte `ShowToastNotification` metodu, která bude volána při spuštění aplikace. Pouze vytvoří informační zprávu ze vzoru XML:

```csharp
private void ShowNotification(string title, string content, string image)
{
    string xmlString = $@"<toast><visual><binding template = 'ToastGeneric'><text>{title}</text><text>{content}</text><image src=>'{image}'</image></binding></visual></toast>";
    XmlDocument toastXml = new XmlDocument();
    toastXml.LoadXml(xmlString);
    ToastNotification toast = new ToastNotification(toastXml);
    ToastNotificationManager.CreateToastNotifier().Show(toast);
}
```

I když je projekt sestaven, dochází k chybám, protože rozhraní API oznámení vyžaduje identitu balíčku a neposkytli jste ji. Při přidání projektového balíčku Windows do řešení se problém vyřeší:

![Snímek obrazovky dialogového okna Přidat nový projekt v aplikaci Visual Studio](./media/windows-migration/add-packaging-project.png)

Vyberte minimální verzi Windows, kterou chcete podporovat, a verzi, na kterou cílíte. Všechna rozhraní API WinRT nejsou podporovaná ve všech verzích Windows 10. Každá aktualizace Windows 10 přidává nová rozhraní API, která jsou dostupná jenom z této verze. Podpora nižší úrovně není k dispozici.

![Výběr minimální verze Windows](./media/windows-migration/select-versions.png)

Dalším krokem je přidání aplikace WPF do projektového balíčku Windows přidáním odkazu na projekt:

![Přidání aplikace WPF do balícího projektu Windows](./media/windows-migration/add-application.png)

![Správce odkazů](./media/windows-migration/reference-manager.png)

Projekt balíčku Windows může zabalit několik aplikací, takže byste měli nastavit, který z nich je vstupním bodem:

![Nastavení vstupního bodu](./media/windows-migration/set-entry-point.png)

Dalším krokem je nastavení projektu WPF jako spouštěného projektu v konfiguraci řešení. Stiskem klávesy F5 můžete kompilovat a sestavovat a zobrazovat výsledky.

![Ukázková aplikace běží a zobrazuje výsledky.](./media/windows-migration/sample-app-result.png)

Pojďme vygenerovat balíček, abyste mohli nainstalovat aplikaci. Klikněte pravým tlačítkem na **úložiště**  >  **vytvořit balíčky aplikací**.

![Dialogové okno vytvořit balíčky aplikací](./media/windows-migration/create-app-packages.png)

Vyberte možnost zkušební načtení pro nasazení aplikace z počítače:

![Výběr možnosti pro zkušební načtení](./media/windows-migration/select-sideloading-option.png)

Vyberte architekturu aplikace vaší aplikace:

![Výběr architektury aplikace](./media/windows-migration/select-app-architecture.png)

Nakonec vytvořte balíček kliknutím na **vytvořit**.

## <a name="xaml-islands"></a>XAML – ostrovy

XAML – ostrovy jsou sada komponent, které vývojářům pro stolní počítače s Windows umožňují používat ovládací prvky UWP v jazyce XAML na svých stávajících aplikacích Win32, včetně model Windows Forms a WPF.

![Struktura na ostrovech XAML](./media/windows-migration/xaml-islands.png)

Pomocí standardních ovládacích prvků a mezi nimi můžete image aplikace Win32, která obsahuje ovládací prvky z moderního světa, a mezi nimi i "ostrov". Koncept je podobný jako při zobrazení prvku iFrame uvnitř webové stránky, která zobrazuje obsah z`different page.`

Kromě přidávání funkcí z rozhraní API pro Windows 10 můžete do své aplikace přidat části prostředí UWP XAML pomocí ostrovů v jazyce XAML.

Windows 10 1903 Update zavádí sadu rozhraní API, která umožňuje hostování obsahu UWP ve Windows v systému Win32. Pro aplikace, které běží na Windows 10 1903, můžou používat i jazyky XAML.

### <a name="the-road-to-xaml-islands"></a>Silnice na ostrovy XAML

Cesta na ostrovy XAML začala v 2012, když společnost Microsoft představila rozhraní API WinRT jako rozhraní pro modernizovat aplikací Win32 (model Windows Forms, WPF a nativní aplikace Win32). Nové ovládací prvky uživatelského rozhraní v WinRT byly ale k dispozici pro nové aplikace, ale ne pro stávající.

V 2015, společně s Windows 10, se nenarodila UWP. UWP umožňují vytvářet aplikace, které fungují na zařízeních s Windows, jako je XBox, Mobile a Desktop. Po jednom roce později Microsoft oznámil stolní most (dříve označovaný jako projekt Centennial). Desktopový most je sada nástrojů, které vývojářům umožňují přenést své stávající aplikace Win32 do Microsoft Store. V 2017 byly přidány další možnosti, které vývojářům umožňují vylepšit aplikace Win32 s využitím některých nových rozhraní API Windows 10, jako jsou živé dlaždice a oznámení v centru akcí. Ale pořád žádné nové ovládací prvky uživatelského rozhraní.

V buildu 2018 Microsoft oznámil vývojářům možnost používat nové ovládací prvky Windows 10 XAML ve svých aktuálních aplikacích Win32, aniž by museli plně migrovat své aplikace na UWP. Byla označena jako ostrovy UWP v jazyce XAML.

### <a name="how-it-works"></a>Jak to funguje

Aktualizace pro Windows 10 1903 zavádí několik rozhraní API pro hostování XAML. Dva z nich jsou `WindowsXamlManager`   a  `DesktopWindowXamlSource` .

 `WindowsXamlManager`   Třída zpracovává rozhraní XAML pro UWP. Jeho `InitializeForCurrentThread` Metoda načte architekturu UWP v rámci aktuálního vlákna aplikace Win32.

 `DesktopWindowXamlSource`   Je instancí vašeho obsahu v jazyce XAML. Má `Content` vlastnost, kterou zodpovídáte za vytváření instancí a nastavení. `DesktopWindowXamlSource`   Vykreslí a získá jeho vstup z HWND. Oddělení IT musí znát, ke kterému druhému HWND bude připojovat prvek XAML a Vy zodpovídáte za jeho určení velikosti a umístění jeho nadřazeného prvku HWND.

WPF nebo model Windows Forms vývojáři obvykle nepracují s HWND uvnitř kódu, takže může být obtížné pochopit a zpracovávat ukazatele HWND a základní kabeláži pro komunikaci Win32 a UWP světů.

#### <a name="the-xaml-islands-net-wrappers"></a>Obálky XAML na ostrovech

Sada nástrojů Community Toolkit pro Windows má nastavovat obálky XAML pro WPF nebo model Windows Forms, které usnadňují použití na ostrovech XAML. Tyto obálky spravují HWND, správu fokusu mimo jiné. Vývojáři model Windows Forms a WPF by měli používat tyto obálky.

Sada nástrojů Windows Community Toolkit nabízí dva typy ovládacích prvků: zabalené ovládací prvky a hostitelské ovládací prvky.

##### <a name="wrapped-controls"></a>Zabalené ovládací prvky

Tyto zabalené ovládací prvky zabalí některé ovládací prvky UWP do ovládacích prvků model Windows Forms nebo WPF, které těmto vývojářům skrývají koncepty UWP. Jsou to tyto ovládací prvky:

* WebView a WebViewCompatible
* InkCanvas a InkToolbar
* MediaPlayerElement
* MapControl

Přidejte `Microsoft.Toolkit.Wpf.UI.Controls` balíček do projektu, zahrňte odkaz na obor názvů a začněte ho používat.

```xml
<Window
        ...
        xmlns:uwpControls="clr-namespace:Microsoft.Toolkit.Wpf.UI.Controls;assembly=Microsoft.Toolkit.Wpf.UI.Controls">
<Grid>
    <Grid.RowDefinitions>
        <RowDefinition Height="Auto"/>
        <RowDefinition Height="\*"/>
    </Grid.RowDefinitions>
    <uwpControls:InkToolbar TargetInkCanvas="{x:Reference Name=inkCanvas}"/>
    <uwpControls:InkCanvas Grid.Row="1" x:Name="inkCanvas" />
</Grid>
```

##### <a name="hosting-controls"></a>Hostování ovládacích prvků

Výkon ostrovů v jazyce XAML rozšiřuje na většinu ovládacích prvků první strany, ovládací prvky třetích stran a vlastní ovládací prvky vyvinuté pro UWP, které je možné integrovat do model Windows Forms a WPF jako "ostrovy" s plně funkčním uživatelským rozhraním. `WindowsXamlHost`To umožňuje ovládací prvek pro WPF a model Windows Forms.

Chcete-li například použít `WindowsXamlHost` ovládací prvek v WPF, přidejte odkaz na `Microsoft.Toolkit.Wpf.UI.XamlHost` balíček poskytovaný sadu nástrojů Windows Community Toolkit.

Po umístění `WindowsXamlHost` do kódu uživatelského rozhraní určete, který typ UWP chcete načíst. Můžete zvolit, že se má používat zabalený ovládací prvek jako nebo složitější a `Button` tvořený několika různými ovládacími prvky, které jsou vlastním ovládacím prvkem UWP.

Následující příklad ukazuje, jak přidat UWP `Button` :

```xml
<Window
        ...
        xmlns:xamlhost="clr-namespace:Microsoft.Toolkit.Wpf.UI.XamlHost;assembly=Microsoft.Toolkit.Wpf.UI.XamlHost">

<xamlhost:WindowsXamlHost x:Name="myUwpButton"
                          InitialTypeName="Windows.UI.Xaml.Controls.Button" />
```

Existuje jasné doporučení k tomuto přístupu a je lepší mít jeden a větší jazyk XAML, který obsahuje vlastní složený ovládací prvek, než má několik ostrovů s jedním ovládacím prvkem.

Jedna z klíčových funkcí jazyka XAML je vazba a funguje mezi kódem Win32 a ostrovem. To znamená, že můžete vytvořit instanci Win32 `Textbox` pomocí UWP `Textbox` . Jedním z důležitých věcí, které je třeba zvážit, je, že tyto vazby jsou jednosměrné vazby, od UWP po Win32, takže pokud aktualizujete `Textbox` uvnitř ostrova XAML, bude textové pole Win32 aktualizováno, ale nikoli jiným způsobem.

Návod, jak používat ostrovy XAML, najdete v těchto tématech:

<https://docs.microsoft.com/windows/apps/desktop/modernize/host-standard-control-with-xaml-islands>

#### <a name="adding-uwp-xaml-custom-controls"></a>Přidávání vlastních ovládacích prvků XAML pro UWP

Vlastní ovládací prvek XAML je ovládací prvek (nebo uživatelský ovládací prvek), který jste vytvořili vy nebo třetí strany (včetně ovládacích prvků WinUI 2. x). Chcete-li hostovat vlastní ovládací prvek UWP v aplikaci model Windows Forms nebo WPF, budete potřebovat:

- Použití `WindowsXamlHost` ovládacího prvku UWP v aplikaci .NET Core 3. x.
- Chcete-li vytvořit projekt aplikace UWP definující `XamlApplication` objekt.

Váš projekt WPF nebo model Windows Forms musí mít přístup k instanci `Microsoft.Toolkit.Win32.UI.XamlHost.XamlApplication` třídy poskytované sadu nástrojů Windows Community Toolkit. Tento objekt funguje jako zprostředkovatel kořenových metadat pro načítání metadat pro vlastní typy jazyka XAML UWP v sestaveních v aktuálním adresáři aplikace. Doporučeným způsobem je přidat prázdný projekt aplikace (univerzální pro Windows) do stejného řešení jako vaše WPF nebo model Windows Forms projekt a revidovat výchozí třídu aplikace v tomto projektu.

Vlastní ovládací prvek XAML pro UWP může být součástí této aplikace pro UWP nebo v nezávislém projektu knihovny tříd UWP, na který odkazujete ve stejném řešení jako vaše WPF nebo model Windows Forms projekt.

Podrobný popis procesu najdete v těchto krocích:

<https://docs.microsoft.com/windows/apps/desktop/modernize/host-custom-control-with-xaml-islands>

#### <a name="the-windows-ui-library-winui-2"></a>Knihovna uživatelského rozhraní systému Windows (WinUI 2)

Kromě ovládacích prvků Doručená pošta systému Windows 10, které jsou součástí operačního systému, je stejný tým pro UWP XAML také poskytovat další ovládací prvky v knihovně uživatelského rozhraní systému Windows (**WinUI 2**). WinUI 2 poskytuje oficiální nativní ovládací prvky a funkce uživatelského rozhraní Microsoft pro aplikace pro Windows UWP a tyto ovládací prvky je možné použít uvnitř na ostrovech XAML.

WinUI 2 je open source a informace najdete na adrese <https://github.com/microsoft/microsoft-ui-xaml> .

Následující článek ukazuje, jak hostovat ovládací prvek jazyka XAML UWP z knihovny WinUI 2:<https://docs.microsoft.com/windows/apps/desktop/modernize/host-custom-control-with-xaml-islands>

### <a name="do-you-need-xaml-islands"></a>Potřebujete ostrovy XAML

Ostrovy XAML jsou určené pro existující aplikace Win32, které chtějí zlepšit uživatelské prostředí tím, že využívají nové ovládací prvky a chování UWP bez úplného přepsání aplikace. Mohli jste už [využít rozhraní API Windows 10](/windows/uwp/porting/desktop-to-uwp-enhance), ale až do kódování XAML, ale jenom pro rozhraní API, které nesouvisí s UŽIVATELSKÝm rozhraním.

Pokud vyvíjíte novou aplikaci pro Windows, je pravděpodobně to správný přístup k [aplikaci pro UWP](/windows/uwp/get-started/universal-application-platform-guide)   .

### <a name="the-road-ahead-xaml-islands-winui-30"></a>Silniční a XAML – ostrovy WinUI 3,0

Vzhledem k tomu, že systém Windows 8, platforma uživatelského rozhraní systému Windows, včetně rozhraní XAML UI, vizuálního složení a vstupního zpracování, byla dodávána jako nedílnou součást systému Windows. To znamená, že pokud chcete využít nejnovější vylepšení technologií uživatelského rozhraní, musíte upgradovat na nejnovější verzi uživatelského rozhraní a zpomalit tempo inovací při vývoji aplikací. Aby bylo možné oddělit tyto dva cykly vývoje a podpořit inovace, společnost Microsoft aktivně pracuje na projektu WinUI.

Od WinUI 2 v 2018 se společnost Microsoft začala dodávat některé nové ovládací prvky a funkce uživatelského rozhraní XAML jako samostatné balíčky NuGet, které sestavují na základě sady SDK pro UWP.

![Struktura WinUI 2,0](./media/windows-migration/winui2.png)

WinUI 3 je pod aktivním vývojem a výrazně rozšiřuje rozsah WinUI tak, aby zahrnoval celou platformu uživatelského rozhraní, která bude plně oddělená od sady SDK pro UWP:

![Struktura WinUI 3,0](./media/windows-migration/winui3.png)

Rozhraní XAML Framework bude nyní vyvíjeno na GitHubu a dodáváno mimo IP síť jako balíčky [NuGet](/nuget/what-is-nuget)   .

Existující funkce rozhraní API pro UWP, dodávané jako součást operačního systému, již nebudou dostávat nové aktualizace funkcí. Budou dál dostávat aktualizace zabezpečení a kritické opravy v souladu s životním cyklem podpory Windows 10.

Univerzální platforma Windows obsahuje více než pouze rozhraní XAML Framework (například model aplikace a zabezpečení, kanál médií, integrace prostředí Xbox a Windows 10, Rozsáhlá podpora zařízení) a bude nadále vyvíjet. Všechny nové funkce XAML se budou vyvíjet a místo toho budou dodávat jako součást WinUI.

#### <a name="winui-3-in-desktop-app-and-winui-xaml-islands"></a>WinUI 3 v desktopové aplikaci a na ostrovech WinUI XAML

Jak vidíte, WinUI 3 je vývoj pro UWP XAML a přirozeně funguje v rámci modelu aplikace UWP a všech jeho požadavků (MSIX zabaleného ID, izolovaného prostoru, CoreWindow atd.). Chcete-li použít pouze WinUI 3 v modelu aplikace Win32, měl by být obsah WinUI hostovaný jiným rozhraním uživatelského rozhraní (model Windows Forms, WPF a tak dále) pomocí **WinUIch ostrovů jazyka XAML**. Jedná se o správnou cestu, pokud chcete vyvíjet aplikace a míchat technologie. Pokud ale chcete nahradit celé staré uživatelské rozhraní pro WinUI, vaše aplikace by by neměla načíst architektury uživatelského rozhraní pro jenom hostování WinUI.

WinUI 3 bude tuto kritickou zpětnou vazbu přidávat **v desktopových aplikacích WinUI**. To umožní, aby aplikace Win32 používaly jako samostatné rozhraní WinUI 3. není nutné načítat model Windows Forms ani WPF.

WinUI 3 v rámci této agregace umožní vývojářům snadno kombinovat a porovnat pravou kombinaci:

* Aplikační model: UWP, Win32
* Platforma: .NET Core nebo nativní
* Jazyk: .NET (C \# , Visual Basic), Standard C++
* Balení: MSIX, AppX pro Microsoft Store, unpackageed
* Spolupráce: použijte WinUI 3 pro rozšiřování existujících aplikací WPF, WinForms a MFC pomocí WinUIových ostrovů.

Pokud chcete získat další informace, Microsoft tento plán sdílí v nástroji <https://github.com/microsoft/microsoft-ui-xaml/blob/master/docs/roadmap.md> .

>[!div class="step-by-step"]
>[Předchozí](migrate-modern-applications.md) 
> [Další](example-migration-core.md)
