---
title: Hostování obsahu Win32 v platformě WPF
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 3cc8644a-34f3-4082-9ddc-77623e4df2d8
ms.openlocfilehash: b598b55c72096daac2487e4c52584abf9735f257
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991461"
---
# <a name="hosting-win32-content-in-wpf"></a>Hostování obsahu Win32 v platformě WPF

## <a name="prerequisites"></a>Požadavky

Viz [spolupráce WPF a Win32](wpf-and-win32-interoperation.md).

## <a name="a-walkthrough-of-win32-inside-windows-presentation-framework-hwndhost"></a>Návod k Win32 v rámci Windows Presentation Framework (HwndHost)

Chcete- [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] li znovu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] použít obsah v <xref:System.Windows.Interop.HwndHost>aplikacích, použijte, což je ovládací prvek, který umožňuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , aby HWND vypadaly jako obsah. <xref:System.Windows.Interop.HwndSource> <xref:System.Windows.Interop.HwndHost> `BuildWindowCore` `DestroyWindowCore` [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Podobně jako <xref:System.Windows.Interop.HwndHost> je jednoduché použití: odvození z a implementace a metod, vytvoření instance odvozené třídy a její umístění uvnitř <xref:System.Windows.Interop.HwndHost> použití.

Pokud je [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] vaše logika již zabalena jako ovládací prvek, je `BuildWindowCore` vaše implementace menší než volání `CreateWindow`. Například pro vytvoření [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ovládacího prvku ListBox v: C++

```cpp
virtual HandleRef BuildWindowCore(HandleRef hwndParent) override {
    HWND handle = CreateWindowEx(0, L"LISTBOX",
    L"this is a Win32 listbox",
    WS_CHILD | WS_VISIBLE | LBS_NOTIFY
    | WS_VSCROLL | WS_BORDER,
    0, 0, // x, y
    30, 70, // height, width
    (HWND) hwndParent.Handle.ToPointer(), // parent hwnd
    0, // hmenu
    0, // hinstance
    0); // lparam

    return HandleRef(this, IntPtr(handle));
}

virtual void DestroyWindowCore(HandleRef hwnd) override {
    // HwndHost will dispose the hwnd for us
}
```

Ale představte si, že [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kód není poměrně tak nezávislý? Pokud ano, můžete vytvořit [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dialogové okno a vložit jeho obsah do větší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace. Ukázka ukazuje tuto možnost v [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] a C++, i když je to možné, i v jiném jazyce nebo na příkazovém řádku.

Začněte jednoduchým dialogem, který se zkompiluje do projektu C++ knihovny DLL.

Dále zaveďte dialog do větší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace:

- Zkompilovat knihovnu DLL jako spravovanou (`/clr`)

- Přepněte dialog do ovládacího prvku.

- Definování odvozené třídy <xref:System.Windows.Interop.HwndHost> s `BuildWindowCore` metodami a `DestroyWindowCore`

- Přepsat `TranslateAccelerator` metodu pro zpracování klíčů dialogových oken

- Přepsat `TabInto` metodu pro podporu tabulátorů

- Přepsat `OnMnemonic` metodu pro podporu symbolických instrukcí

- Vytvoření instance podtřídy a její umístění pod pravým [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]prvkem <xref:System.Windows.Interop.HwndHost>

### <a name="turn-the-dialog-into-a-control"></a>Přepněte dialog do ovládacího prvku.

Můžete změnit dialogové okno na podřízeného HWND pomocí stylů WS_CHILD a DS_CONTROL. Přejít do souboru prostředků (. RC), kde je dialogové okno definováno, a najít začátek definice dialogového okna:

```text
IDD_DIALOG1 DIALOGEX 0, 0, 303, 121
STYLE DS_SETFONT | DS_MODALFRAME | DS_FIXEDSYS | WS_POPUP | WS_CAPTION | WS_SYSMENU
```

Změňte druhý řádek na:

```text
STYLE DS_SETFONT | WS_CHILD | WS_BORDER | DS_CONTROL
```

Tato akce zcela nebalí do samostatného ovládacího prvku. Přesto je nutné volat `IsDialogMessage()` , aby bylo [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] možné zpracovat určité zprávy, ale změna ovládacího prvku poskytuje jednoduchý způsob, jak umístit tyto ovládací prvky do jiného prvku HWND.

## <a name="subclass-hwndhost"></a>HwndHost podtříd

Importujte následující obory názvů:

```cpp
namespace ManagedCpp
{
    using namespace System;
    using namespace System::Windows;
    using namespace System::Windows::Interop;
    using namespace System::Windows::Input;
    using namespace System::Windows::Media;
    using namespace System::Runtime::InteropServices;
```

Pak vytvořte odvozenou třídu třídy <xref:System.Windows.Interop.HwndHost> a `BuildWindowCore` přepište metody `DestroyWindowCore` a:

```cpp
public ref class MyHwndHost : public HwndHost, IKeyboardInputSink {
    private:
        HWND dialog;

    protected:
        virtual HandleRef BuildWindowCore(HandleRef hwndParent) override {
            InitializeGlobals();
            dialog = CreateDialog(hInstance,
                MAKEINTRESOURCE(IDD_DIALOG1),
                (HWND) hwndParent.Handle.ToPointer(),
                (DLGPROC) About);
            return HandleRef(this, IntPtr(dialog));
        }

        virtual void DestroyWindowCore(HandleRef hwnd) override {
            // hwnd will be disposed for us
        }
```

Zde můžete použít `CreateDialog` k vytvoření dialogového okna, které je skutečně ovládacím prvkem. Vzhledem k tomu, že se jedná o jednu z prvních metod, které jsou volány uvnitř knihovny [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] DLL, měli byste také provést několik standardních inicializací voláním funkce, kterou definujete později, která se nazývá: `InitializeGlobals()`

```cpp
bool initialized = false;
    void InitializeGlobals() {
        if (initialized) return;
        initialized = true;

        // TODO: Place code here.
        MSG msg;
        HACCEL hAccelTable;

        // Initialize global strings
        LoadString(hInstance, IDS_APP_TITLE, szTitle, MAX_LOADSTRING);
        LoadString(hInstance, IDC_TYPICALWIN32DIALOG, szWindowClass, MAX_LOADSTRING);
        MyRegisterClass(hInstance);
```

### <a name="override-translateaccelerator-method-to-handle-dialog-keys"></a>Přepsat metodu TranslateAccelerator pro zpracování klíčů dialogových oken

Pokud jste teď spustili tuto ukázku, měli byste obdržet ovládací prvek dialog, který se zobrazí, ale bude ignorovat všechny funkce pro zpracování klávesnice, které vytvoří dialogové okno s funkčním seznamem. Nyní byste měli přepsat `TranslateAccelerator` implementaci (která pochází z `IKeyboardInputSink`rozhraní, které <xref:System.Windows.Interop.HwndHost> implementuje). Tato metoda se volá, když aplikace získá WM_KEYDOWN a WM_SYSKEYDOWN.

```cpp
#undef TranslateAccelerator
        virtual bool TranslateAccelerator(System::Windows::Interop::MSG% msg,
            ModifierKeys modifiers) override
        {
            ::MSG m = ConvertMessage(msg);

            // Win32's IsDialogMessage() will handle most of our tabbing, but doesn't know
            // what to do when it reaches the last tab stop
            if (m.message == WM_KEYDOWN && m.wParam == VK_TAB) {
                HWND firstTabStop = GetDlgItem(dialog, IDC_EDIT1);
                HWND lastTabStop = GetDlgItem(dialog, IDCANCEL);
                TraversalRequest^ request = nullptr;

                if (GetKeyState(VK_SHIFT) && GetFocus() == firstTabStop) {
                    // this code should work, but there’s a bug with interop shift-tab in current builds
                    request = gcnew TraversalRequest(FocusNavigationDirection::Last);
                }
                else if (!GetKeyState(VK_SHIFT) && GetFocus() == lastTabStop) {
                    request = gcnew TraversalRequest(FocusNavigationDirection::Next);
                }

                if (request != nullptr)
                    return ((IKeyboardInputSink^) this)->KeyboardInputSite->OnNoMoreTabStops(request);

            }

            // Only call IsDialogMessage for keys it will do something with.
            if (msg.message == WM_SYSKEYDOWN || msg.message == WM_KEYDOWN) {
                switch (m.wParam) {
                    case VK_TAB:
                    case VK_LEFT:
                    case VK_UP:
                    case VK_RIGHT:
                    case VK_DOWN:
                    case VK_EXECUTE:
                    case VK_RETURN:
                    case VK_ESCAPE:
                    case VK_CANCEL:
                        IsDialogMessage(dialog, &m);
                        // IsDialogMessage should be called ProcessDialogMessage --
                        // it processes messages without ever really telling you
                        // if it handled a specific message or not
                        return true;
                }
            }

            return false; // not a key we handled
        }
```

Toto je spousta kódu v jednom kusu, takže by mohla používat podrobnější vysvětlení. Nejprve kód pomocí C++ a C++ makra; je nutné si uvědomit, že již existuje makro s názvem `TranslateAccelerator`, které je definováno v Winuser. h:

```cpp
#define TranslateAccelerator  TranslateAcceleratorW
```

Proto je nutné definovat `TranslateAccelerator` metodu a `TranslateAcceleratorW` nikoli metodu.

Podobně platí, že se jedná o nespravovanou Winuser. h MSG a `Microsoft::Win32::MSG` spravovanou strukturu. C++ Pomocí`::` operátoru můžete odstranit nejednoznačnost mezi dvěma.

```cpp
virtual bool TranslateAccelerator(System::Windows::Interop::MSG% msg,
    ModifierKeys modifiers) override
{
    ::MSG m = ConvertMessage(msg);
}

Both MSGs have the same data, but sometimes it is easier to work with the unmanaged definition, so in this sample you can define the obvious conversion routine:

```cpp
::MSG ConvertMessage(System::Windows::Interop::MSG% msg) {
    ::MSG m;
    m.hwnd = (HWND) msg.hwnd.ToPointer();
    m.lParam = (LPARAM) msg.lParam.ToPointer();
    m.message = msg.message;
    m.wParam = (WPARAM) msg.wParam.ToPointer();

    m.time = msg.time;

    POINT pt;
    pt.x = msg.pt_x;
    pt.y = msg.pt_y;
    m.pt = pt;

    return m;
}
```

Zpět na `TranslateAccelerator`. Základní princip je zavolat [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] funkci `IsDialogMessage` , aby co nejvíce fungovala, ale `IsDialogMessage` nemá přístup k cokoli mimo dialog. Jako karta uživatele kolem dialogu, když se na kartách spouští poslední ovládací prvek v našem dialogu, musíte nastavit fokus na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] část voláním. `IKeyboardInputSite::OnNoMoreStops`

```cpp
// Win32's IsDialogMessage() will handle most of the tabbing, but doesn't know
// what to do when it reaches the last tab stop
if (m.message == WM_KEYDOWN && m.wParam == VK_TAB) {
    HWND firstTabStop = GetDlgItem(dialog, IDC_EDIT1);
    HWND lastTabStop = GetDlgItem(dialog, IDCANCEL);
    TraversalRequest^ request = nullptr;

    if (GetKeyState(VK_SHIFT) && GetFocus() == firstTabStop) {
        request = gcnew TraversalRequest(FocusNavigationDirection::Last);
    }
    else if (!GetKeyState(VK_SHIFT) && GetFocus() ==  lastTabStop) { {
        request = gcnew TraversalRequest(FocusNavigationDirection::Next);
    }

    if (request != nullptr)
        return ((IKeyboardInputSink^) this)->KeyboardInputSite->OnNoMoreTabStops(request);
}
```

Nakonec zavolejte `IsDialogMessage`. Jedna z odpovědností `TranslateAccelerator` metody ale oznamuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] , zda jste vypustili klávesovou zkratku nebo ne. Pokud jste ho nezpracovali, vstupní událost může být tunelem a bublinou prostřednictvím zbytku aplikace. Tady vystavíte quirki zpracování messange klávesnice a povahu vstupní architektury v [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]. `IsDialogMessage` Bohužel nevrátí žádný způsob, zda zpracuje konkrétní klávesovou zkratku. Ještě horší voláním `DispatchMessage()` na stisknutí kláves by nemělo být zpracováno!  Proto budete muset provést zpětnou analýzu `IsDialogMessage`a volat ji jenom pro klíče, které víte, že budou pracovat:

```cpp
// Only call IsDialogMessage for keys it will do something with.
if (msg.message == WM_SYSKEYDOWN || msg.message == WM_KEYDOWN) {
    switch (m.wParam) {
        case VK_TAB:
        case VK_LEFT:
        case VK_UP:
        case VK_RIGHT:
        case VK_DOWN:
        case VK_EXECUTE:
        case VK_RETURN:
        case VK_ESCAPE:
        case VK_CANCEL:
            IsDialogMessage(dialog, &m);
            // IsDialogMessage should be called ProcessDialogMessage --
            // it processes messages without ever really telling you
            // if it handled a specific message or not
            return true;
    }
```

### <a name="override-tabinto-method-to-support-tabbing"></a>Přepsat metodu TabInto pro podporu tabulátorů

Teď, když jste nasadili `TranslateAccelerator`, uživatel může kolem dialogového okna a tabulátoru být v rámci větší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace tabulátor. Uživatel ale nemůže kartu zpátky do dialogového okna. Chcete-li tento problém vyřešit `TabInto`, přepíšete:

```cpp
public:
    virtual bool TabInto(TraversalRequest^ request) override {
        if (request->FocusNavigationDirection == FocusNavigationDirection::Last) {
            HWND lastTabStop = GetDlgItem(dialog, IDCANCEL);
            SetFocus(lastTabStop);
        }
        else {
            HWND firstTabStop = GetDlgItem(dialog, IDC_EDIT1);
            SetFocus(firstTabStop);
        }
        return true;
    }
```

`TraversalRequest` Parametr oznamuje, zda je akce karty karta nebo klávesa SHIFT.

### <a name="override-onmnemonic-method-to-support-mnemonics"></a>Přepsat metodu s podporou symbolických instrukcí

Zpracování klávesnice je skoro hotové, ale chybí jedna věc – symbolické symboly nefungují. Pokud uživatel stiskne ALT-F, fokus fokusu neskočí do textového pole "first name:". Proto přepíšete `OnMnemonic` metodu:

```cpp
virtual bool OnMnemonic(System::Windows::Interop::MSG% msg, ModifierKeys modifiers) override {
    ::MSG m = ConvertMessage(msg);

    // If it's one of our mnemonics, set focus to the appropriate hwnd
    if (msg.message == WM_SYSCHAR && GetKeyState(VK_MENU /*alt*/)) {
        int dialogitem = 9999;
        switch (m.wParam) {
            case 's': dialogitem = IDOK; break;
            case 'c': dialogitem = IDCANCEL; break;
            case 'f': dialogitem = IDC_EDIT1; break;
            case 'l': dialogitem = IDC_EDIT2; break;
            case 'p': dialogitem = IDC_EDIT3; break;
            case 'a': dialogitem = IDC_EDIT4; break;
            case 'i': dialogitem = IDC_EDIT5; break;
            case 't': dialogitem = IDC_EDIT6; break;
            case 'z': dialogitem = IDC_EDIT7; break;
        }
        if (dialogitem != 9999) {
            HWND hwnd = GetDlgItem(dialog, dialogitem);
            SetFocus(hwnd);
            return true;
        }
    }
    return false; // key unhandled
};
```

Proč se sem `IsDialogMessage` nevolá?  Máte stejný problém jako předtím – musíte být schopni informovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kód o tom, jestli kód zpracoval klávesovou zkratku, a `IsDialogMessage` nemůže to udělat. Dojde také k druhému problému, protože `IsDialogMessage` odmítnutí zpracování instrukcí, pokud fokus HWND není uvnitř dialogového okna.

### <a name="instantiate-the-hwndhost-derived-class"></a>Vytvoření instance odvozené třídy HwndHost

Nakonec, když je teď všechna podpora klíče a karty, můžete do větší <xref:System.Windows.Interop.HwndHost> [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace umístit své místo. Je-li hlavní aplikace napsána v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]nástroji, nejjednodušší způsob, jak ji umístit do správného místa, je opustit prázdný <xref:System.Windows.Controls.Border> prvek, kam chcete vložit <xref:System.Windows.Interop.HwndHost>. Tady vytvoříte <xref:System.Windows.Controls.Border> název `insertHwndHostHere`:

```xaml
<Window x:Class="WPFApplication1.Window1"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    Title="Windows Presentation Framework Application"
    Loaded="Window1_Loaded"
    >
    <StackPanel>
        <Button Content="WPF button"/>
        <Border Name="insertHwndHostHere" Height="200" Width="500"/>
        <Button Content="WPF button"/>
    </StackPanel>
</Window>
```

Pak vše zůstává k nalezení vhodného místa v sekvenci kódu pro vytvoření instance <xref:System.Windows.Interop.HwndHost> a připojení <xref:System.Windows.Controls.Border>k. V tomto příkladu se umístí do konstruktoru pro <xref:System.Windows.Window> odvozenou třídu:

```csharp
public partial class Window1 : Window {
    public Window1() {
    }

    void Window1_Loaded(object sender, RoutedEventArgs e) {
        HwndHost host = new ManagedCpp.MyHwndHost();
        insertHwndHostHere.Child = host;
    }
}
```

Díky tomu máte následující:

![Snímek obrazovky aplikace WPF spuštěné.](./media/hosting-win32-content-in-wpf/windows-presentation-foundation-application.png)

## <a name="see-also"></a>Viz také:

- [Vzájemná spolupráce grafického subsystému WPF a systému Win32](wpf-and-win32-interoperation.md)
