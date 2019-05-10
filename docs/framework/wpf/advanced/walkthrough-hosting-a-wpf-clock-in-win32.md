---
title: 'Návod: Hostování hodin WPF ve Win32'
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 555e55a7-0851-4ec8-b1c6-0acba7e9b648
ms.openlocfilehash: 4001c34f6673e036bdbf731baed782c6dc0a16b0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64755906"
---
# <a name="walkthrough-hosting-a-wpf-clock-in-win32"></a>Návod: Hostování hodin WPF ve Win32

Vložit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uvnitř [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikací, použijte <xref:System.Windows.Interop.HwndSource>, poskytující HWND, který obsahuje vaše [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah. Nejprve vytvoříte <xref:System.Windows.Interop.HwndSource>, předá CreateWindow podobně jako parametry. Pak můžete zjistit <xref:System.Windows.Interop.HwndSource> o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu chcete dovnitř. Nakonec získejte HWND z celkového počtu <xref:System.Windows.Interop.HwndSource>. Tento návod ukazuje, jak vytvořit smíšenými [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uvnitř [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikaci, která reimplements operační systém **vlastnosti data a času** dialogového okna.

## <a name="prerequisites"></a>Požadavky

Zobrazit [WPF a systému Win32 vzájemná spolupráce grafického subsystému](wpf-and-win32-interoperation.md).

## <a name="how-to-use-this-tutorial"></a>Jak používat v tomto kurzu

V tomto kurzu se soustřeďuje na důležité kroky pro vytváření aplikace vzájemné spolupráce. Tento kurz je založená na výběru [ukázka vzájemná spolupráce grafického subsystému hodin Win32](https://go.microsoft.com/fwlink/?LinkID=160051), ale tato ukázka je reflektivní konečného produktu. V tomto kurzu dokumenty kroky, jako kdyby byly spuštění s existujícím [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projektu vlastní, možná již existující projekt a přidávání hostovaný [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do vaší aplikace. Můžete porovnat svůj produkt end s [ukázka vzájemná spolupráce grafického subsystému hodin Win32](https://go.microsoft.com/fwlink/?LinkID=160051).

## <a name="a-walkthrough-of-windows-presentation-framework-inside-win32-hwndsource"></a>Názorný postup Windows Presentation Framework v systému Win32 (HwndSource)

Následující obrázek znázorňuje zamýšlený konečný produkt v tomto kurzu:

![Snímek obrazovky ukazující dialogové okno Vlastnosti data a času.](./media/walkthrough-hosting-a-wpf-clock-in-win32/date-time-properties-dialog.png)

Toto dialogové okno můžete znovu vytvořit tak, že vytvoříte C++ projekt Win32 ve Visual Studiu a použití editoru dialogových oken k vytvoření následujících:

![Znovu vytvořená dialogové okno Vlastnosti data a času](./media/walkthrough-hosting-a-wpf-clock-in-win32/recreated-date-time-properties-dialog.png)

(Není potřeba použít [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] používat <xref:System.Windows.Interop.HwndSource>, a není potřeba C++ použít k zápisu [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programy, ale to je poměrně typické způsob, jak to provést a slouží také k podle jednotlivých kroků kurzu vysvětlení).

Budete muset provést pět konkrétní dílčích kroků jednotlivých aby bylo možné vložit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hodiny do dialogového okna:

1. Povolit vaše [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projekt tak, aby volání spravovaného kódu (**/CLR**) tak, že změníte nastavení projektu na [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)].

2. Vytvoření [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> v samostatné knihovně DLL.

3. Vytvořit z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> uvnitř <xref:System.Windows.Interop.HwndSource>.

4. Získat popisovačem HWND, který <xref:System.Windows.Controls.Page> pomocí <xref:System.Windows.Interop.HwndSource.Handle%2A> vlastnost.

5. Použití [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] rozhodnout, kam umístit HWND v rámci větší [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikace

## <a name="clr"></a>/ CLR

Prvním krokem je chcete-li to nespravované [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projektu do jednoho, který může volat spravovaný kód. Použijte možnost kompilátoru/CLR, který bude propojovat nezbytné knihoven DLL, která chcete použít a upravit metodu Main pro použití s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

Pokud chcete povolit použití spravovaný kód uvnitř projektu C++: Klikněte pravým tlačítkem na projekt win32clock a vyberte **vlastnosti**. Na **Obecné** stránka vlastností (výchozí), změňte Podpora Common Language Runtime `/clr`.

V dalším kroku přidejte odkazy na knihovny DLL, které jsou nezbytné pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: PresentationCore.dll, knihovně PresentationFramework.dll, System.dll, knihovně WindowsBase.dll, UIAutomationProvider.dll a UIAutomationTypes.dll. (Tyto pokyny předpokládají, že je nainstalovaný operační systém na jednotce C:.)

1. Klikněte pravým tlačítkem na projekt win32clock a vyberte **odkazy...** a v tomto dialogovém okně:

2. Klikněte pravým tlačítkem na projekt win32clock a vyberte **odkazy...** .

3. Klikněte na tlačítko **přidat nový odkaz**, klikněte na kartu Procházet, zadejte C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationCore.dll a klikněte na tlačítko OK.

4. Opakujte pro knihovně PresentationFramework.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationFramework.dll.

5. Opakujte pro knihovně WindowsBase.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\WindowsBase.dll.

6. Opakujte pro UIAutomationTypes.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationTypes.dll.

7. Opakujte pro UIAutomationProvider.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationProvider.dll.

8. Klikněte na tlačítko **přidat nový odkaz**vyberte System.dll a klikněte na tlačítko **OK**.

9. Klikněte na tlačítko **OK** ukončíte win32clock stránky vlastností pro přidání odkazů.

 Nakonec přidejte `STAThreadAttribute` k `_tWinMain` metody pro použití s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:

```cpp
[System::STAThreadAttribute]
int APIENTRY _tWinMain(HINSTANCE hInstance,
                     HINSTANCE hPrevInstance,
                     LPTSTR    lpCmdLine,
                     int       nCmdShow)
```

Tento atribut oznamuje [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] , když inicializuje [!INCLUDE[TLA#tla_com](../../../../includes/tlasharptla-com-md.md)], měla by používat model jednovláknový objekt apartment (STA), což je nezbytné pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]).

## <a name="create-a-windows-presentation-framework-page"></a>Vytvoření stránky Windows Presentation Framework

Dále vytvořte knihovnu DLL, která definuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page>. Často je nejjednodušší vytvořit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> jako samostatná aplikace a zápis a ladění [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] část tímto způsobem. Po dokončení tohoto projektu mohou být změněny na knihovnu DLL kliknutím pravým tlačítkem myši na projekt, kliknutím na **vlastnosti**, přejde na aplikaci a změna výstupní typ pro knihovny tříd Windows.

[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Projektu knihovny dll je pak možné kombinovat s [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projektu (jedno řešení, které obsahuje dva projekty) – klikněte pravým tlačítkem na řešení, vyberte **Add\Existing projektu**.

Chcete-li použít tato [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] knihovny dll z [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projektu, musíte přidat odkaz:

1. Klikněte pravým tlačítkem na projekt win32clock a vyberte **odkazy...** .

2. Klikněte na tlačítko **přidat nový odkaz**.

3. Klikněte na tlačítko **projekty** kartu. Vyberte WPFClock, klikněte na tlačítko OK.

4. Klikněte na tlačítko **OK** ukončíte win32clock stránky vlastností pro přidání odkazů.

## <a name="hwndsource"></a>HwndSource

Dále použijete <xref:System.Windows.Interop.HwndSource> provést [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> vypadat popisovačem HWND. Přidejte tento blok kódu do souboru jazyka C++:

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

 Toto je dlouhý část kódu, který by mohl použít vysvětlení. První část je různé klauzule tak, že nepotřebujete k plnému určení všech volání:

```cpp
namespace ManagedCode
{
    using namespace System;
    using namespace System::Windows;
    using namespace System::Windows::Interop;
    using namespace System::Windows::Media;
```

 Potom definujte funkci, která vytvoří [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu, vloží <xref:System.Windows.Interop.HwndSource> kolem a vrátí HWND:

```cpp
HWND GetHwnd(HWND parent, int x, int y, int width, int height) {
```

Nejprve vytvoříte <xref:System.Windows.Interop.HwndSource>, jejíž parametry jsou podobné CreateWindow:

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

Poté vytvoříte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu pomocí volání konstruktoru třídy:

```cpp
UIElement^ page = gcnew WPFClock::Clock();
```

Připojte stránky <xref:System.Windows.Interop.HwndSource>:

```cpp
source->RootVisual = page;
```

 A vraťte se na posledním řádku HWND pro <xref:System.Windows.Interop.HwndSource>:

```cpp
return (HWND) source->Handle.ToPointer();
```

## <a name="positioning-the-hwnd"></a>Umístění Hwnd

Teď, když máte HWND, který obsahuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hodiny, je potřeba přidat tento HWND uvnitř [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dialogového okna. Pokud jste zjistili, stačí kam chcete vložit HWND, by stačí pouze předat tuto velikost a umístění `GetHwnd` funkce, které jste definovali dříve. Ale používá soubor prostředků k definování dialogového okna, takže máte jistotu, že přesně, kde jsou umístěny všechny HWND. Můžete použít [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] editoru dialogových oken pro umístění [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] statické řídit, kam chcete přejít na hodiny ("Vložit formát tady") a použijte ho k umístění [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hodiny.

Pokud zpracování nezavěsíte použijete `GetDlgItem` načíst HWND pro zástupný text statické:

```cpp
HWND placeholder = GetDlgItem(hDlg, IDC_CLOCK);
```

Můžete pak vypočítá velikost a umístění tohoto zástupného symbolu STATICKÁ, tak můžete umístit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hodiny na tomto místě:

Rect – obdélník;

```cpp
GetWindowRect(placeholder, &rectangle);
int width = rectangle.right - rectangle.left;
int height = rectangle.bottom - rectangle.top;
POINT point;
point.x = rectangle.left;
point.y = rectangle.top;
result = MapWindowPoints(NULL, hDlg, &point, 1);
```

Potom skrýt zástupný symbol statické:

```cpp
ShowWindow(placeholder, SW_HIDE);
```

A vytvořit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock HWND v tomto umístění:

```cpp
HWND clock = ManagedCode::GetHwnd(hDlg, point.x, point.y, width, height);
```

To usnadňuje kurz zajímavé a vytvořit reálné [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hodiny, budete muset vytvořit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hodiny ovládacího prvku, v tomto okamžiku. To většinou v kódu, můžete provést pomocí několika málo obslužné rutiny událostí v modelu code-behind. Protože v tomto kurzu se o vzájemné spolupráci a nemusíte ovládacího prvku návrhu, dokončení kódu pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hodin je k dispozici jako blok kódu bez diskrétní pokyny, jak se vytvářejí nebo co jednotlivé části znamená, že zde. Bez obav experimentovat s tímto kódem můžete změnit vzhled a chování nebo funkce pro ovládací prvek.

Toto je zápis:

[!code-xaml[Win32Clock#AllClockXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml#allclockxaml)]

A tady je doprovodné kódu:

[!code-csharp[Win32Clock#AllClockCS](~/samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml.cs#allclockcs)]

Konečný výsledek vypadá takto:

![Konečný výsledek vlastnosti data a času dialogové okno](./media/walkthrough-hosting-a-wpf-clock-in-win32/final-result-date-time-properties-dialog.png)

Porovnejte vaše konečný výsledek kódu, který vytváří tento snímek obrazovky, naleznete v tématu [ukázka vzájemná spolupráce grafického subsystému hodin Win32](https://go.microsoft.com/fwlink/?LinkID=160051).

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Interop.HwndSource>
- [Vzájemná spolupráce grafického subsystému WPF a systému Win32](wpf-and-win32-interoperation.md)
- [Ukázka součinnosti hodin Win32](https://go.microsoft.com/fwlink/?LinkID=160051)
