---
title: 'Návod: Hostování hodin WPF ve Win32'
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 555e55a7-0851-4ec8-b1c6-0acba7e9b648
ms.openlocfilehash: 27e1a2e88beeacf8c2cd98f61b11542ee2341e8f
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68433978"
---
# <a name="walkthrough-hosting-a-wpf-clock-in-win32"></a>Návod: Hostování hodin WPF ve Win32

Pro vložení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Interop.HwndSource>do aplikací použijte, který poskytuje HWND, který obsahuje váš [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah. [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] Nejdřív vytvoříte <xref:System.Windows.Interop.HwndSource>a dáte parametrům, které se budou podobat funkci CreateWindow. Pak se <xref:System.Windows.Interop.HwndSource> dozvíte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] o obsahu, který v něm chcete. Nakonec obdržíte HWND z <xref:System.Windows.Interop.HwndSource>. Tento návod ukazuje, jak vytvořit smíšený [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] program v rámci [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikace, který znovu implementuje dialogové okno **vlastností data a času** operačního systému.

## <a name="prerequisites"></a>Požadavky

Viz [spolupráce WPF a Win32](wpf-and-win32-interoperation.md).

## <a name="how-to-use-this-tutorial"></a>Jak používat tento kurz

Tento kurz se zaměřuje na důležité kroky k vytvoření meziprovozního aplikace. Tento kurz je zálohovaný ukázkou, [Ukázka mezioperace v prostředí Win32](https://go.microsoft.com/fwlink/?LinkID=160051), ale tato ukázka se odráží u koncového produktu. V tomto kurzu se dokončí postup, jak jste se rozhodli, [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] že jste začali s existujícím projektem, který je třeba již existujícím projektem, a přidali [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jste hostovaný do vaší aplikace. Můžete porovnat svůj koncový produkt s [ukázkou meziprovozu pro hodiny Win32](https://go.microsoft.com/fwlink/?LinkID=160051).

## <a name="a-walkthrough-of-windows-presentation-framework-inside-win32-hwndsource"></a>Návod pro Windows Presentation Framework uvnitř Win32 (HwndSource)

Následující obrázek znázorňuje zamýšlený koncový produkt tohoto kurzu:

![Snímek obrazovky, který zobrazuje dialogové okno Vlastnosti data a času.](./media/walkthrough-hosting-a-wpf-clock-in-win32/date-time-properties-dialog.png)

Tento dialog můžete znovu vytvořit tak, že vytvoříte C++ projekt Win32 v aplikaci Visual Studio a pomocí editoru dialogového okna vytvoříte následující:

![Dialogové okno znovu vytvořit vlastnosti data a času](./media/walkthrough-hosting-a-wpf-clock-in-win32/recreated-date-time-properties-dialog.png)

(Nemusíte [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] používat <xref:System.Windows.Interop.HwndSource>, abyste mohli používat, a nemusíte používat C++ k psaní [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programů, ale jedná se o poměrně typický způsob, jak to udělat, tak se dobře hodí k vysvětlení kurzu stupňovaný).

Chcete-li vložit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hodiny do dialogového okna, je třeba provést pět jednotlivých podkroků:

1. Povolit vašemu [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projektu volání spravovaného kódu ( **/CLR**) změnou nastavení projektu v [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)].

2. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Vytvořte<xref:System.Windows.Controls.Page> v samostatné knihovně DLL.

3. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Umístěte dovnitř.<xref:System.Windows.Controls.Page> <xref:System.Windows.Interop.HwndSource>

4. Získejte HWND pro, který <xref:System.Windows.Controls.Page> <xref:System.Windows.Interop.HwndSource.Handle%2A> používá vlastnost.

5. Použijte [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] k rozhodnutí, kam umístit HWND v rámci větší [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikace

## <a name="clr"></a>možností

Prvním krokem je zapínání tohoto nespravovaného [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projektu na jeden, který může volat spravovaný kód. Použijete možnost kompilátoru/CLR, která se připojí k potřebným knihovnám DLL, které chcete použít, a upravte metodu Main pro použití s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

Povolení použití spravovaného kódu v rámci C++ projektu: Klikněte pravým tlačítkem na projekt win32clock a vyberte **vlastnosti**. Na stránce **Obecné** vlastnosti (výchozí) změňte podporu modulu Common Language Runtime na `/clr`.

Dále přidejte odkazy na knihovny DLL nutné pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: PresentationCore. dll, PresentationFramework. dll, System. dll, WindowsBase. dll, UIAutomationProvider. dll a UIAutomationTypes. dll. (V následujících pokynech se předpokládá, že je operační systém nainstalovaný na jednotce C:.)

1. Klikněte pravým tlačítkem na projekt win32clock a vyberte **odkazy...** a v tomto dialogovém okně:

2. Klikněte pravým tlačítkem na projekt win32clock a vyberte **odkazy...** .

3. Klikněte na tlačítko **Přidat nový odkaz**, klikněte na tlačítko Procházet, zadejte C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationCore.dll a klikněte na tlačítko OK.

4. Opakovat pro PresentationFramework. dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationFramework.dll.

5. Opakovat pro WindowsBase. dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\WindowsBase.dll.

6. Opakovat pro UIAutomationTypes. dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationTypes.dll.

7. Opakovat pro UIAutomationProvider. dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationProvider.dll.

8. Klikněte na tlačítko **Přidat nový odkaz**, vyberte položku System. dll a klikněte na tlačítko **OK**.

9. Kliknutím na tlačítko **OK** zavřete stránky vlastností win32clock pro přidání odkazů.

 Nakonec přidejte `STAThreadAttribute` `_tWinMain` do metody pro použití s: [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]

```cpp
[System::STAThreadAttribute]
int APIENTRY _tWinMain(HINSTANCE hInstance,
                     HINSTANCE hPrevInstance,
                     LPTSTR    lpCmdLine,
                     int       nCmdShow)
```

Tento atribut oznamuje modulu CLR (Common Language Runtime), že při inicializaci modelu COM (Component Object Model) by měl používat jeden model Apartment (STA), který je nezbytný pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]).

## <a name="create-a-windows-presentation-framework-page"></a>Vytvoření stránky Windows Presentation Framework

V dalším kroku vytvoříte knihovnu DLL, která definuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. <xref:System.Windows.Controls.Page> Často je nejjednodušší vytvořit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> jako samostatnou aplikaci a napsat a ladit tak, jak je [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] . Po dokončení lze tento projekt přepínat na knihovnu DLL tak, že kliknete pravým tlačítkem myši na projekt, kliknete na **vlastnosti**, přejdete do aplikace a změníte typ výstupu na knihovnu tříd systému Windows.

Projekt knihovny DLL lze následně kombinovat [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] s projektem (jedno řešení, které obsahuje dva projekty) – klikněte pravým tlačítkem na řešení, vyberte **projekt Add\Existing**. [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]

Chcete-li [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] použít tuto knihovnu [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dll z projektu, je nutné přidat odkaz:

1. Klikněte pravým tlačítkem na projekt win32clock a vyberte **odkazy...** .

2. Klikněte na tlačítko **Přidat nový odkaz**.

3. Klikněte na kartu **projekty** . Vyberte WPFClock, klikněte na OK.

4. Kliknutím na tlačítko **OK** zavřete stránky vlastností win32clock pro přidání odkazů.

## <a name="hwndsource"></a>HwndSource

V <xref:System.Windows.Interop.HwndSource> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dalším kroku použijete k vytvoření vzhledu jako HWND. <xref:System.Windows.Controls.Page> Tento blok kódu přidáte do C++ souboru:

```cpp
namespace ManagedCode
{
    using namespace System;
    using namespace System::Windows;
    using namespace System::Windows::Interop;
    using namespace System::Windows::Media;

    HWND GetHwnd(HWND parent, int x, int y, int width, int height) {
        HwndSource^ source = gcnew HwndSource(
            0, // class style
            WS_VISIBLE | WS_CHILD, // style
            0, // exstyle
            x, y, width, height,
            "hi", // NAME
            IntPtr(parent)        // parent window
            );

        UIElement^ page = gcnew WPFClock::Clock();
        source->RootVisual = page;
        return (HWND) source->Handle.ToPointer();
    }
}
}
```

 Toto je dlouhý kód, který může používat určité vysvětlení. První část je různé klauzule, takže nemusíte plně kvalifikovat všechna volání:

```cpp
namespace ManagedCode
{
    using namespace System;
    using namespace System::Windows;
    using namespace System::Windows::Interop;
    using namespace System::Windows::Media;
```

 Pak definujte funkci, která vytvoří [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah, <xref:System.Windows.Interop.HwndSource> vloží kolem něj a vrátí HWND:

```cpp
HWND GetHwnd(HWND parent, int x, int y, int width, int height) {
```

Nejdřív vytvoříte <xref:System.Windows.Interop.HwndSource>, jejichž parametry jsou podobné funkci CreateWindow:

```cpp
HwndSource^ source = gcnew HwndSource(
    0, // class style
    WS_VISIBLE | WS_CHILD, // style
    0, // exstyle
    x, y, width, height,
    "hi", // NAME
    IntPtr(parent) // parent window
);
```

Pak vytvoříte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] třídu obsahu voláním jejího konstruktoru:

```cpp
UIElement^ page = gcnew WPFClock::Clock();
```

Pak se stránka připojí k <xref:System.Windows.Interop.HwndSource>:

```cpp
source->RootVisual = page;
```

 A v posledním řádku vrátí HWND pro <xref:System.Windows.Interop.HwndSource>:

```cpp
return (HWND) source->Handle.ToPointer();
```

## <a name="positioning-the-hwnd"></a>Umístění HWND

Teď, když máte HWND, který obsahuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hodiny, je nutné vložit HWND [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] do dialogového okna. Pokud jste věděli, kam chcete umístit HWND, stačí pouze předat tuto velikost a umístění do `GetHwnd` dříve definované funkce. Ale použili jste soubor prostředků k definování dialogu, takže nejste přesně jisti, kde jsou umístěny všechny HWND. Editor [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] dialogového okna můžete použít k [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] vložení statického ovládacího prvku, kam chcete hodiny přidat ("vložit hodiny sem"), a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] použít ho k umístění hodin.

Kde WM_INITDIALOG zpracováváte, použijete `GetDlgItem` k načtení HWND pro statický zástupný symbol:

```cpp
HWND placeholder = GetDlgItem(hDlg, IDC_CLOCK);
```

Pak můžete vypočítat velikost a umístění zástupného symbolu, aby bylo možné vložit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hodiny do tohoto umístění:

Obdélník RECT;

```cpp
GetWindowRect(placeholder, &rectangle);
int width = rectangle.right - rectangle.left;
int height = rectangle.bottom - rectangle.top;
POINT point;
point.x = rectangle.left;
point.y = rectangle.top;
result = MapWindowPoints(NULL, hDlg, &point, 1);
```

Pak skryjete zástupný symbol STATIC:

```cpp
ShowWindow(placeholder, SW_HIDE);
```

A v tomto [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] umístění vytvořte časové HWND:

```cpp
HWND clock = ManagedCode::GetHwnd(hDlg, point.x, point.y, width, height);
```

Chcete-li vytvořit kurz zajímavé a vytvořit reálné [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hodiny, budete v tomto okamžiku muset [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vytvořit ovládací prvek hodin. To lze provést hlavně v označení, a to s několika obslužnými rutinami událostí v kódu na pozadí. Vzhledem k tomu, že tento kurz se týká vzájemného provozu a nikoli o návrhu řízení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , je zde k dispozici kompletní kód pro hodiny, a to bez diskrétních instrukcí pro sestavování a toho, co jednotlivé části znamenají. Nebojte se s tímto kódem pro změnu vzhledu a chování ovládacího prvku.

Zde je značka:

[!code-xaml[Win32Clock#AllClockXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml#allclockxaml)]

A zde je doprovodný kód na pozadí:

[!code-csharp[Win32Clock#AllClockCS](~/samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml.cs#allclockcs)]

Konečný výsledek vypadá takto:

![Dialogové okno Vlastnosti data a času finálního výsledku](./media/walkthrough-hosting-a-wpf-clock-in-win32/final-result-date-time-properties-dialog.png)

K porovnání konečného výsledku s kódem, který vytvořil tento snímek obrazovky, si přečtěte část [Ukázka mezioperačního zpracování hodin Win32](https://go.microsoft.com/fwlink/?LinkID=160051).

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Interop.HwndSource>
- [Vzájemná spolupráce grafického subsystému WPF a systému Win32](wpf-and-win32-interoperation.md)
- [Ukázka mezi operacemi hodin Win32](https://go.microsoft.com/fwlink/?LinkID=160051)
