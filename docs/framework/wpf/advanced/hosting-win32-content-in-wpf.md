---
title: Hostování obsahu Win32 v platformě WPF
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 3cc8644a-34f3-4082-9ddc-77623e4df2d8
ms.openlocfilehash: a9d9de1f35375e48981f895d096e46fd501ef8ec
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740374"
---
# <a name="hosting-win32-content-in-wpf"></a>Hostování obsahu Win32 v platformě WPF

## <a name="prerequisites"></a>Požadavky

Viz [spolupráce WPF a Win32](wpf-and-win32-interoperation.md).

## <a name="a-walkthrough-of-win32-inside-windows-presentation-framework-hwndhost"></a>Návod k Win32 v rámci Windows Presentation Framework (HwndHost)

Chcete-li znovu použít obsah Win32 v aplikacích [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikací, použijte <xref:System.Windows.Interop.HwndHost>, což je ovládací prvek, který umožňuje, aby HWND vypadaly jako [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah. Podobně jako <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost> je jednoduché použití: odvozovat z <xref:System.Windows.Interop.HwndHost> a implementovat metody `BuildWindowCore` a `DestroyWindowCore` a pak vytvořit instanci vaší <xref:System.Windows.Interop.HwndHost> odvozené třídy a umístit ji do vaší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.

Pokud je vaše logika Win32 již zabalena jako ovládací prvek, je vaše implementace `BuildWindowCore` menší než volání `CreateWindow`. Například pro vytvoření ovládacího prvku seznamu Win32 v C++:

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

Ale představte si, že kód Win32 není poměrně tak, jak je součástí sebe? Pokud ano, můžete vytvořit dialogové okno Win32 a vložit jeho obsah do větší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace. Ukázka ukazuje tuto možnost v aplikaci Visual Studio C++a, i když je to možné, i v jiném jazyce nebo na příkazovém řádku.

Začněte jednoduchým dialogem, který se zkompiluje do projektu C++ knihovny DLL.

Dále zaveďte dialog do větší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace:

- Zkompilovat knihovnu DLL jako spravovanou (`/clr`)

- Přepněte dialog do ovládacího prvku.

- Definovat odvozenou třídu <xref:System.Windows.Interop.HwndHost> s metodami `BuildWindowCore` a `DestroyWindowCore`

- Přepsat metodu `TranslateAccelerator` pro zpracování klíčů dialogových oken

- Přepsat metodu `TabInto` pro podporu tabulátorů

- Přepsat metodu `OnMnemonic` pro podporu symbolických instrukcí

- Vytvoření instance <xref:System.Windows.Interop.HwndHost> podtřídy a její umístění pod správným [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prvkem

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

Tato akce zcela nebalí do samostatného ovládacího prvku. stále musíte volat `IsDialogMessage()`, aby Win32 mohl zpracovat určité zprávy, ale změna ovládacího prvku poskytuje jednoduchý způsob, jak umístit tyto ovládací prvky do jiného HWND.

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

Pak vytvořte odvozenou třídu <xref:System.Windows.Interop.HwndHost> a přepište metody `BuildWindowCore` a `DestroyWindowCore`:

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

Zde můžete použít `CreateDialog` k vytvoření dialogového okna, které je skutečně ovládacím prvkem. Vzhledem k tomu, že se jedná o jednu z prvních metod, které jsou volány uvnitř knihovny DLL, měli byste také provést několik standardních inicializací Win32 voláním funkce, kterou definujete později s názvem `InitializeGlobals()`:

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

Proto se ujistěte, že definujete metodu `TranslateAccelerator`, a ne metodu `TranslateAcceleratorW`.

Podobně je k dispozici nespravovaná Winuser. h MSG a spravovaná struktura `Microsoft::Win32::MSG`. Pomocí operátoru C++ `::` lze odstranit mezi dvěma.

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

Zpět na `TranslateAccelerator`. Základní princip je volání funkce Win32 `IsDialogMessage` k tomu, aby co nejvíce fungovalo, ale `IsDialogMessage` nemá přístup k cokoli mimo dialog. Jako karta uživatele kolem dialogu, když se na kartách spouští poslední ovládací prvek v našem dialogu, musíte nastavit fokus na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ou část voláním `IKeyboardInputSite::OnNoMoreStops`.

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

Nakonec zavolejte `IsDialogMessage`. Jedna z odpovědností `TranslateAccelerator` metody ale oznamuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], jestli jste vypustili klávesovou zkratku nebo ne. Pokud jste ho nezpracovali, vstupní událost může být tunelem a bublinou prostřednictvím zbytku aplikace. Tady vystavíte Quirk ovládání messange klávesnice a povahu vstupní architektury v prostředí Win32. Bohužel se `IsDialogMessage` nevrátí žádným způsobem, ať už zpracovává konkrétní klávesovou zkratku. I horší, bude volat `DispatchMessage()` na úhozech, které by neměly být zpracovány!  Proto budete muset provádět zpětnou analýzu `IsDialogMessage`a volat ji jenom pro ty, které víte, že se budou zpracovávat:

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

Teď, když jste nasadili `TranslateAccelerator`, uživatel může kolem dialogového okna a kartu z něj v rámci větší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace vyhledat kartu. Uživatel ale nemůže kartu zpátky do dialogového okna. Chcete-li tento problém vyřešit, přepíšete `TabInto`:

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

Parametr `TraversalRequest` určuje, zda je akce karty karta nebo klávesa SHIFT.

### <a name="override-onmnemonic-method-to-support-mnemonics"></a>Přepsat metodu s podporou symbolických instrukcí

Zpracování klávesnice je skoro hotové, ale chybí jedna věc – symbolické symboly nefungují. Pokud uživatel stiskne ALT-F, fokus fokusu neskočí do textového pole "first name:". Proto přepíšete metodu `OnMnemonic`:

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

Proč zde nevolat `IsDialogMessage`?  Máte stejný problém jako předtím – musíte být schopni informovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kód, zda kód zpracoval klávesovou zkratku nebo ne, a `IsDialogMessage` jej nelze provést. Existuje také druhý problém, protože `IsDialogMessage` zamítnout zpracování instrukcí, pokud fokus HWND není uvnitř dialogového okna.

### <a name="instantiate-the-hwndhost-derived-class"></a>Vytvoření instance odvozené třídy HwndHost

Nakonec, když je teď všechna podpora klíčů a karet, můžete <xref:System.Windows.Interop.HwndHost> umístit do větší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace. Je-li hlavní aplikace napsána v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], nejjednodušší způsob, jak ji umístit do správného místa, je opustit prázdný <xref:System.Windows.Controls.Border> prvek, kam chcete umístit <xref:System.Windows.Interop.HwndHost>. Zde vytvoříte <xref:System.Windows.Controls.Border> s názvem `insertHwndHostHere`:

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

Pak vše, co zbývá, je najít dobré místo v sekvenci kódu pro vytvoření instance <xref:System.Windows.Interop.HwndHost> a jeho připojení k <xref:System.Windows.Controls.Border>. V tomto příkladu se umístí do konstruktoru pro <xref:System.Windows.Window> odvozenou třídu:

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
