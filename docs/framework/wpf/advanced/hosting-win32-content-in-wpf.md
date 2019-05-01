---
title: Hostování obsahu Win32 v platformě WPF
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 3cc8644a-34f3-4082-9ddc-77623e4df2d8
ms.openlocfilehash: 3c00539eb5f2a96fec974accda2fea1c0200aeec
ms.sourcegitcommit: 89fcad7e816c12eb1299128481183f01c73f2c07
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/24/2019
ms.locfileid: "63807762"
---
# <a name="hosting-win32-content-in-wpf"></a>Hostování obsahu Win32 v platformě WPF

## <a name="prerequisites"></a>Požadavky

Zobrazit [WPF a systému Win32 vzájemná spolupráce grafického subsystému](wpf-and-win32-interoperation.md).

## <a name="a-walkthrough-of-win32-inside-windows-presentation-framework-hwndhost"></a>Názorný postup Win32 v rámci Windows Presentation Framework (HwndHost)

Pro opětovné použití [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] obsahu uvnitř [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikací, použijte <xref:System.Windows.Interop.HwndHost>, což je ovládací prvek, který umožňuje HWND vypadat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah. Jako <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost> je jednoduché použití: jsou odvozeny z <xref:System.Windows.Interop.HwndHost> a implementovat `BuildWindowCore` a `DestroyWindowCore` metody, potom vytvořte instanci vaší <xref:System.Windows.Interop.HwndHost> odvozené třídy a umístěte ji uvnitř vaší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.

Pokud vaše [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] logiky je už zabalené jako ovládací prvek, pak vaše `BuildWindowCore` implementace je poněkud složitější než volání `CreateWindow`. Například, chcete-li vytvořit [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ListBox – ovládací prvek v [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)]:

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

Předpokládejme, ale [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kód není úplně tak samostatná? Pokud ano, můžete vytvořit [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dialogové okno pole a jeho obsah vložit do větší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace. Tato ukázka vysvětluje to [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] a [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)], i když je také možné provést v jiném jazyce nebo na příkazovém řádku.

Začněte s jednoduchou dialog, který je zkompilován [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] projektu.

V dalším kroku představovat dialogového okna na větší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace:

- Kompilace [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] jako spravovaný (`/clr`)

- Zapnout dialogového okna do ovládacího prvku

- Definice třídy odvozené z <xref:System.Windows.Interop.HwndHost> s `BuildWindowCore` a `DestroyWindowCore` metody

- Přepsat `TranslateAccelerator` metodu ke zpracování dialogové okno klíče

- Přepsat `TabInto` metoda k podpoře tabulátoru

- Přepsat `OnMnemonic` metody pro podporu klávesových zkratek

- Vytvoření instance <xref:System.Windows.Interop.HwndHost> podtřídy a vložte ji pod vpravo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] – element

### <a name="turn-the-dialog-into-a-control"></a>Zapnout dialogového okna do ovládacího prvku

Proměňte dialogového okna na podřízené HWND pomocí WS_CHILD a DS_CONTROL stylů. Přejděte do souboru prostředků (.rc), kde je definován dialogového okna a najít začátek definici dialogového okna:

```
IDD_DIALOG1 DIALOGEX 0, 0, 303, 121
STYLE DS_SETFONT | DS_MODALFRAME | DS_FIXEDSYS | WS_POPUP | WS_CAPTION | WS_SYSMENU
```

Změňte druhý řádek na:

```
STYLE DS_SETFONT | WS_CHILD | WS_BORDER | DS_CONTROL
```

Tato akce není balíček plně ho do samostatné ovládacího prvku; je stále potřeba volat `IsDialogMessage()` tak [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] může zpracovat některé zprávy, ale poskytuje jednoduchý způsob, jak umístění těchto ovládacích prvků uvnitř jiného HWND Změna ovládacího prvku.

## <a name="subclass-hwndhost"></a>HwndHost podtřídy

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

Vytvořte třídu odvozenou z <xref:System.Windows.Interop.HwndHost> a přepsat `BuildWindowCore` a `DestroyWindowCore` metody:

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

Zde použijete `CreateDialog` vytvořit dialogové okno, které je ve skutečnosti ovládací prvek. Protože to je jedna z prvních metod volat [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)], by měl také provést některé standardní [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] inicializace voláním funkce budou definovat později, volá `InitializeGlobals()`:

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

### <a name="override-translateaccelerator-method-to-handle-dialog-keys"></a>Potlačí metodu TranslateAccelerator za účelem zpracování dialogové okno klíče

Pokud jste spustili této ukázce nyní, získali byste ovládací prvek dialogového okna, která zobrazuje, ale ho by Přeskakovat vše klávesnice zpracování této vytvoří dialogové okno funkční dialogového okna. Teď byste měli přepsat `TranslateAccelerator` implementace (které pochází z `IKeyboardInputSink`, rozhraní, který <xref:System.Windows.Interop.HwndHost> implementuje). Tato metoda volána, když aplikace obdrží WM_KEYDOWN a WM_SYSKEYDOWN.

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

To je velké množství kódu v jednu část, protože může využívat některé podrobnější vysvětlení. První, kód s využitím [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] a [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] makra; co potřebujete vědět, že už existuje s názvem makra `TranslateAccelerator`, který je definován v winuser:

```cpp
#define TranslateAccelerator  TranslateAcceleratorW
```

Tak definovat `TranslateAccelerator` – metoda a ne `TranslateAcceleratorW` metoda.

Podobně je spravované i nespravované winuser MSG `Microsoft::Win32::MSG` struktury. Můžete odstranit nejednoznačnost mezi nimi pomocí [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] `::` operátor.

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

Zpět na `TranslateAccelerator`. Základním principem je volání [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] funkce `IsDialogMessage` tolik práci nejvíce, ale `IsDialogMessage` nemá přístup k ničemu mimo dialogového okna. Na kartě uživatele kolem dialogové okno, při procházení tabulátorem běží za poslední ovládací prvek v našich dialogového okna, je potřeba nastavit fokus na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] část voláním `IKeyboardInputSite::OnNoMoreStops`.

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

Nakonec proveďte volání `IsDialogMessage`. Jeden odpovědnosti `TranslateAccelerator` sděluje metoda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Určuje, zda stisknutí kláves zpracována či nikoli. Pokud jste se nepodařilo zpracovat, můžete tunelového propojení událost vstupu a bubliny procházení zbývající části aplikace. Tady bude vystavovat datového toku zvuku nabízí messange zpracování klávesnice a povaze architektura vstupu v [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]. Bohužel `IsDialogMessage` nevrací žádným způsobem, zda zpracovává konkrétní stisk klávesy. Ještě hůř, bude volat `DispatchMessage()` na stisknutí kláves by nemělo vyřizovat!  Proto budete muset provést zpětnou analýzu `IsDialogMessage`a pouze volání pro klíče, můžete ji znát zpracuje:

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

### <a name="override-tabinto-method-to-support-tabbing"></a>Potlačí metodu TabInto pro podporu tabulátor

Teď, když jste implementovali `TranslateAccelerator`, uživatel může kartě kolem v dialogovém okně pole a karty z ní do větší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace. Ale uživatel nemůže kartě zpět do dialogového okna. Chcete-li to vyřešit, přepište `TabInto`:

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

`TraversalRequest` Parametr zjistíte, jestli akce karta je karta nebo shift tab.

### <a name="override-onmnemonic-method-to-support-mnemonics"></a>Potlačí metodu OnMnemonic za účelem podpory klávesových zkratek

Zpracování pomocí klávesnice je skoro hotová, ale je jedna věc, kterou chybí – klávesových zkratek, nebudou fungovat. Pokud uživatel stiskne klávesu alt-F, doe fokus není přejít "křestní jméno:" upravit pole. Přepíšete tak, `OnMnemonic` metody:

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

Případně proč bezpečná není volání `IsDialogMessage` tady?  Budete mít stejný problém před – potřebujete mít možnost informovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kódu, jestli váš kód zpracovává stisk klávesy nebo Ne, a `IsDialogMessage` nemůžete udělat. Existuje problém také druhý, protože `IsDialogMessage` odmítne zpracovat symbol, pokud není cílené HWND v dialogovém okně.

### <a name="instantiate-the-hwndhost-derived-class"></a>Vytvoření instance HwndHost odvozené třídy

A konečně, teď, když všechny klíče a kartu podporu na místě, můžete umístit vaše <xref:System.Windows.Interop.HwndHost> do větší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace. Pokud je hlavní aplikace napsané v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], nejjednodušší způsob, jak vložit na správném místě je ponechat prázdnou <xref:System.Windows.Controls.Border> elementu, kam chcete umístit <xref:System.Windows.Interop.HwndHost>. Zde můžete vytvořit <xref:System.Windows.Controls.Border> s názvem `insertHwndHostHere`:

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

Pak už jen zbývá k vyhledání vhodné místo v pořadí kód k vytvoření instance <xref:System.Windows.Interop.HwndHost> a propojte jej s <xref:System.Windows.Controls.Border>. V tomto příkladu je zařadí ho uvnitř konstruktoru pro <xref:System.Windows.Window> odvozené třídy:

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

– Umožňuje:

![Snímek obrazovky spuštěné aplikace WPF.](./media/hosting-win32-content-in-wpf/windows-presentation-foundation-application.png)

## <a name="see-also"></a>Viz také:

- [Vzájemná spolupráce grafického subsystému WPF a systému Win32](wpf-and-win32-interoperation.md)
