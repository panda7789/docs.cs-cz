---
title: 'Návod: Hostování hodin WPF v systému Win32'
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 555e55a7-0851-4ec8-b1c6-0acba7e9b648
ms.openlocfilehash: 8d1f376a2c5b3f31407af0100d9a4417f7cff34e
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740248"
---
# <a name="walkthrough-hosting-a-wpf-clock-in-win32"></a>Návod: Hostování hodin WPF v systému Win32

Chcete-li umístit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do aplikací Win32, použijte <xref:System.Windows.Interop.HwndSource>, která poskytuje HWND, který obsahuje váš [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah. Nejdřív vytvoříte <xref:System.Windows.Interop.HwndSource>, takže parametry pro něj budou podobné funkci CreateWindow. Pak <xref:System.Windows.Interop.HwndSource> informace o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]m obsahu, který v něm potřebujete. Nakonec obdržíte HWND z <xref:System.Windows.Interop.HwndSource>. Tento návod ukazuje, jak vytvořit smíšený [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] v rámci aplikace Win32, která znovu implementuje dialog **vlastností data a času** operačního systému.

## <a name="prerequisites"></a>Požadavky

Viz [spolupráce WPF a Win32](wpf-and-win32-interoperation.md).

## <a name="how-to-use-this-tutorial"></a>Jak používat tento kurz

Tento kurz se zaměřuje na důležité kroky k vytvoření meziprovozního aplikace. Tento kurz je zálohovaný ukázkou, [Ukázka mezioperace v prostředí Win32](https://go.microsoft.com/fwlink/?LinkID=160051), ale tato ukázka se odráží u koncového produktu. V tomto kurzu se dokončí postup, jak jste se rozhodli, že jste začali s existujícím projektem Win32 vlastní, možná již existující projekt a přidáváte do aplikace hostovaný [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Můžete porovnat svůj koncový produkt s [ukázkou meziprovozu pro hodiny Win32](https://go.microsoft.com/fwlink/?LinkID=160051).

## <a name="a-walkthrough-of-windows-presentation-framework-inside-win32-hwndsource"></a>Návod pro Windows Presentation Framework uvnitř Win32 (HwndSource)

Následující obrázek znázorňuje zamýšlený koncový produkt tohoto kurzu:

![Snímek obrazovky, který zobrazuje dialogové okno Vlastnosti data a času.](./media/walkthrough-hosting-a-wpf-clock-in-win32/date-time-properties-dialog.png)

Tento dialog můžete znovu vytvořit tak, že vytvoříte C++ projekt Win32 v aplikaci Visual Studio a pomocí editoru dialogového okna vytvoříte následující:

![Dialogové okno znovu vytvořit vlastnosti data a času](./media/walkthrough-hosting-a-wpf-clock-in-win32/recreated-date-time-properties-dialog.png)

(Nemusíte používat Visual Studio k použití <xref:System.Windows.Interop.HwndSource>a nemusíte používat C++ k psaní programů Win32, ale jedná se o poměrně typický způsob, jak to provést, a stejně tak se dobře hodí k vysvětlení kurzu stupňovaný).

Chcete-li vložit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hodiny do dialogového okna, je nutné provést pět jednotlivých podkroků:

1. Umožněte Vašemu projektu Win32 volat spravovaný kód ( **/CLR**) změnou nastavení projektu v aplikaci Visual Studio.

2. Vytvoří [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> v samostatné knihovně DLL.

3. Vložení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> dovnitř <xref:System.Windows.Interop.HwndSource>.

4. Získat HWND pro tento <xref:System.Windows.Controls.Page> pomocí vlastnosti <xref:System.Windows.Interop.HwndSource.Handle%2A>.

5. Použití Win32 k rozhodnutí, kam umístit HWND v rámci větší aplikace Win32

## <a name="clr"></a>možností

Prvním krokem je zapnutí tohoto nespravovaného projektu Win32 na jeden, který může volat spravovaný kód. Použijete možnost kompilátoru/CLR, která se připojí k potřebným knihovnám DLL, které chcete použít, a upravte metodu Main pro použití s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].

Povolení použití spravovaného kódu v rámci C++ projektu: klikněte pravým tlačítkem na projekt win32clock a vyberte **vlastnosti**. Na stránce **Obecné** vlastnosti (výchozí) změňte podporu modulu Common Language Runtime na `/clr`.

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

 Nakonec přidejte `STAThreadAttribute` do metody `_tWinMain` pro použití s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:

```cpp
[System::STAThreadAttribute]
int APIENTRY _tWinMain(HINSTANCE hInstance,
                     HINSTANCE hPrevInstance,
                     LPTSTR    lpCmdLine,
                     int       nCmdShow)
```

Tento atribut oznamuje modulu CLR (Common Language Runtime), že při inicializaci modelu COM (Component Object Model) by měl používat jeden model Apartment (STA), který je nezbytný pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]).

## <a name="create-a-windows-presentation-framework-page"></a>Vytvoření stránky Windows Presentation Framework

V dalším kroku vytvoříte knihovnu DLL, která definuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page>. Často je nejjednodušší vytvořit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> jako samostatnou aplikaci a napsat a ladit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ou část. Po dokončení lze tento projekt přepínat na knihovnu DLL tak, že kliknete pravým tlačítkem myši na projekt, kliknete na **vlastnosti**, přejdete do aplikace a změníte typ výstupu na knihovnu tříd systému Windows.

Projekt [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] DLL lze následně kombinovat s projektem Win32 (jedno řešení, které obsahuje dva projekty) – klikněte pravým tlačítkem na řešení, vyberte **projekt Add\Existing**.

Chcete-li použít tuto [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll z projektu Win32, je nutné přidat odkaz:

1. Klikněte pravým tlačítkem na projekt win32clock a vyberte **odkazy...** .

2. Klikněte na tlačítko **Přidat nový odkaz**.

3. Klikněte na kartu **projekty** . Vyberte WPFClock, klikněte na OK.

4. Kliknutím na tlačítko **OK** zavřete stránky vlastností win32clock pro přidání odkazů.

## <a name="hwndsource"></a>HwndSource

V dalším kroku použijete <xref:System.Windows.Interop.HwndSource>, aby [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> vypadal jako HWND. Tento blok kódu přidáte do C++ souboru:

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

 Pak definujte funkci, která vytvoří obsah [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], vloží <xref:System.Windows.Interop.HwndSource> kolem něj a vrátí HWND:

```cpp
HWND GetHwnd(HWND parent, int x, int y, int width, int height) {
```

Nejprve vytvoříte <xref:System.Windows.Interop.HwndSource>, jejichž parametry jsou podobné funkci CreateWindow:

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

Pak vytvoříte třídu obsahu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] voláním jejího konstruktoru:

```cpp
UIElement^ page = gcnew WPFClock::Clock();
```

Pak stránku připojíte k <xref:System.Windows.Interop.HwndSource>:

```cpp
source->RootVisual = page;
```

 A v posledním řádku vrátí HWND pro <xref:System.Windows.Interop.HwndSource>:

```cpp
return (HWND) source->Handle.ToPointer();
```

## <a name="positioning-the-hwnd"></a>Umístění HWND

Teď, když máte HWND, který obsahuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hodin, je nutné vložit HWND do dialogového okna Win32. Pokud jste věděli, kam chcete přidat HWND, stačí pouze předat tuto velikost a umístění do funkce `GetHwnd`, kterou jste definovali dříve. Ale použili jste soubor prostředků k definování dialogu, takže nejste přesně jisti, kde jsou umístěny všechny HWND. Editor dialogového okna sady Visual Studio můžete použít k vložení STATICKÉho ovládacího prvku systému Win32, kde chcete, aby se hodiny posunuly ("vložit hodiny sem"), a použít k umístění [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ch hodin.

Kde WM_INITDIALOG zpracováváte, použijete `GetDlgItem` k načtení HWND pro statický zástupný symbol:

```cpp
HWND placeholder = GetDlgItem(hDlg, IDC_CLOCK);
```

Pak můžete vypočítat velikost a umístění zástupného symbolu, aby bylo možné umístit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hodiny na toto místo:

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

A vytvořte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hodinového HWND v tomto umístění:

```cpp
HWND clock = ManagedCode::GetHwnd(hDlg, point.x, point.y, width, height);
```

Aby se kurz zajímavý a vytvořil reálné [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]é hodiny, budete v tomto okamžiku muset vytvořit ovládací prvek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hodin. To lze provést hlavně v označení, a to s několika obslužnými rutinami událostí v kódu na pozadí. Vzhledem k tomu, že tento kurz se týká vzájemného provozu a nikoli o návrhu ovládacích prvků, je zde k dispozici kompletní kód pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hodiny, a to bez diskrétních instrukcí pro sestavování a toho, co jednotlivé části znamenají. Nebojte se s tímto kódem pro změnu vzhledu a chování ovládacího prvku.

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
