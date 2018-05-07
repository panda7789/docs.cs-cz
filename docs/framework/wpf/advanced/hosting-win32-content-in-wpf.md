---
title: Hostování obsahu Win32 v platformě WPF
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 3cc8644a-34f3-4082-9ddc-77623e4df2d8
ms.openlocfilehash: beb7d5e6e1f934b89bb7516eb7e9bbbaad696238
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="hosting-win32-content-in-wpf"></a>Hostování obsahu Win32 v platformě WPF
## <a name="prerequisites"></a>Požadavky  
 V tématu [WPF a vzájemná spolupráce Win32](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md).  
  
## <a name="a-walkthrough-of-win32-inside-windows-presentation-framework-hwndhost"></a>Návod Win32 uvnitř Windows Presentation Framework (HwndHost)  
 Znovu použít [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] obsahu uvnitř [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace, použijte <xref:System.Windows.Interop.HwndHost>, což je ovládací prvek, který umožňuje HWND vypadat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah.  Jako <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost> je jednoduchá používat: odvozena od <xref:System.Windows.Interop.HwndHost> a implementovat `BuildWindowCore` a `DestroyWindowCore` metod, vytvoří instanci vaše <xref:System.Windows.Interop.HwndHost> odvozené třídy a umístěte jej uvnitř vaší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.  
  
 Pokud vaše [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] logiku je již zabalené jako ovládací prvek, pak vaše `BuildWindowCore` implementace je trochu déle než volání `CreateWindow`.  Chcete-li například vytvořit [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ListBox – ovládací prvek v [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)]:  
  
```  
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
  
 Předpokládejme, ale [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kód není poměrně tak samostatná? Pokud ano, můžete vytvořit [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dialogové okno pole a vložit obsah do větší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.  Ukázka zobrazuje v [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] a [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)], i když je také možné provést v jiném jazyce, nebo na příkazovém řádku.  
  
 Začněte s jednoduchý dialog, který se zkompiluje do [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] projektu.  
  
 V dalším kroku zavedení dialogu do delší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace:  
  
-   Kompilace [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] jako spravovaný (`/clr`)  
  
-   Zapnout dialogu do ovládacího prvku  
  
-   Definování odvozené třídy z <xref:System.Windows.Interop.HwndHost> s `BuildWindowCore` a `DestroyWindowCore` metody  
  
-   Přepsání `TranslateAccelerator` metodu ke zpracování klíče dialogové okno  
  
-   Přepsání `TabInto` metoda pro podporu použití tabulátoru  
  
-   Přepsání `OnMnemonic` metoda pro podporu mnemonické klávesy  
  
-   Vytvoření instance <xref:System.Windows.Interop.HwndHost> podtřídami a umístí jej v rámci práva [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] – element  
  
### <a name="turn-the-dialog-into-a-control"></a>Zapnout dialogu do ovládacího prvku  
 Dialogové okno můžete upravit na podřízenou HWND pomocí ws_child – a DS_CONTROL stylů.  Přejděte do souboru prostředků (.rc), kde je definován dialogové okno a najděte začátku definici dialogového okna:  
  
```  
IDD_DIALOG1 DIALOGEX 0, 0, 303, 121  
STYLE DS_SETFONT | DS_MODALFRAME | DS_FIXEDSYS | WS_POPUP | WS_CAPTION | WS_SYSMENU  
```  
  
 Změna na druhém řádku pro:  
  
```  
STYLE DS_SETFONT | WS_CHILD | WS_BORDER | DS_CONTROL  
```  
  
 Tato akce není plně je zabalit do ovládacího prvku nezávislý; stále je třeba volat `IsDialogMessage()` tak [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] může zpracovat některé zprávy, ale poskytuje snadný způsob, jak umístění těchto ovládacích prvků uvnitř jiné HWND řízení změn.  
  
## <a name="subclass-hwndhost"></a>Podtřída HwndHost  
 Importujte následujících oborů názvů:  
  
```  
namespace ManagedCpp  
{  
    using namespace System;  
    using namespace System::Windows;  
    using namespace System::Windows::Interop;  
    using namespace System::Windows::Input;  
    using namespace System::Windows::Media;  
    using namespace System::Runtime::InteropServices;  
```  
  
 Pak vytvořte třídu odvozenou z <xref:System.Windows.Interop.HwndHost> a přepsat `BuildWindowCore` a `DestroyWindowCore` metody:  
  
```  
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
  
 Tady můžete použít `CreateDialog` vytvořit okno, které je ve skutečnosti ovládacího prvku.  Vzhledem k tomu, že toto je jedna z metod první volána v rámci [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)], je vhodné provést některé standardní [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] inicializace voláním funkce později, nadefinujete názvem `InitializeGlobals()`:  
  
```  
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
  
### <a name="override-translateaccelerator-method-to-handle-dialog-keys"></a>Potlačí metodu TranslateAccelerator za účelem zpracování klíče dialogové okno  
 Pokud jste spustili Tato ukázka nyní, které byste získali, dialogové okno Ovládací prvek, který zobrazuje, ale můžete všechny klávesnice zpracování této díky by ignorovat dialogové okno funkční dialogové okno.  Nyní by měly přepsat `TranslateAccelerator` implementace (který pochází z `IKeyboardInputSink`, rozhraní, <xref:System.Windows.Interop.HwndHost> implementuje).  Tato metoda je volána při WM_KEYDOWN a WM_SYSKEYDOWN aplikace obdrží.  
  
```  
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
  
 Toto je velké množství kódu v jednu část, takže by mohl použít některé podrobnější vysvětlení.  První, kódu pomocí [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] a [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] makra, je třeba si uvědomit, že již makro s názvem `TranslateAccelerator`, která je definována v winuser:  
  
```  
#define TranslateAccelerator  TranslateAcceleratorW  
```  
  
 Proto nezapomeňte definovat `TranslateAccelerator` metoda a ne `TranslateAcceleratorW` metoda.  
  
 Podobně je spravovaných i nespravovaných winuser MSG `Microsoft::Win32::MSG` struktura.  Můžete odstranit nejednoznačnost mezi nimi pomocí [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] `::` operátor.  
  
```  
virtual bool TranslateAccelerator(System::Windows::Interop::MSG% msg,   
    ModifierKeys modifiers) override   
{  
    ::MSG m = ConvertMessage(msg);  
```  
  
 Jak zprávy o obsahovaly stejná data, ale někdy je snazší s ním pracovat definici nespravované, v této ukázce můžete definovat zřejmé převod rutiny:  
  
```  
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
  
 Zpět na `TranslateAccelerator`.  Základní princip je volání [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] funkce `IsDialogMessage` tolik práci co možná, ale `IsDialogMessage` nemá přístup k ničemu mimo dialogové okno. Na kartě uživatele kolem tohoto dialogového okna při použití tabulátoru běží po poslední ovládacího prvku v dialogovém okně pro naše, budete muset nastavit fokus [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] část voláním `IKeyboardInputSite::OnNoMoreStops`.  
  
```  
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
  
 Nakonec volání `IsDialogMessage`.  Ale jeden z odpovědnosti `TranslateAccelerator` oznamuje, metoda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jestli zpracovávat klávesu nebo ne. Pokud jste se nepodařilo zpracovat, může tunelovat vstupní událost a bublin procházení zbývající aplikace. Zde bude vystavovat datového toku zvuku nabízí messange zpracování klávesnice a povaze vstupní architektura v [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]. Bohužel `IsDialogMessage` nevrací žádným způsobem zda zpracovává konkrétní klávesu.  I horší, bude volat `DispatchMessage()` na stisknutí kláves by nemělo vyřizovat!  Budete muset provádět zpětnou analýzu `IsDialogMessage`a pouze volání pro bude zpracovávat klíče vy víte, že:  
  
```  
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
  
### <a name="override-tabinto-method-to-support-tabbing"></a>Potlačí metodu TabInto pro podporu použití tabulátoru  
 Teď, když jste implementovali `TranslateAccelerator`, uživatel může kartě kolem uvnitř dialogové okno pole a karta mimo ho do delší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.  Ale uživatel nemůže kartě zpět do dialogových oken.  K řešení, které, přepíšete `TabInto`:  
  
```  
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
  
 `TraversalRequest` Parametr řekne, jestli je na kartě Akce kartě nebo shift.  
  
### <a name="override-onmnemonic-method-to-support-mnemonics"></a>Potlačí metodu OnMnemonic pro podporu mnemonické klávesy  
 Zpracování pomocí klávesnice je téměř dokončena, ale je jedna věc chybí – klávesové zkratky nefungují.  Pokud uživatel stiskne klávesu alt-F, fokus doe není přejít na "křestní jméno:" textové pole. Ano, můžete přepsat `OnMnemonic` metoda:  
  
```  
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
  
 Proč ne volání `IsDialogMessage` tady?  Můžete mít stejný problém jako před – je potřeba mít k informování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] code, jestli váš kód zpracovávat klávesu nebo Ne, a `IsDialogMessage` nejde udělat.  Také druhý problémem je, protože `IsDialogMessage` odmítá ke zpracování symbolické Pokud cílených HWND není uvnitř dialogové okno.  
  
### <a name="instantiate-the-hwndhost-derived-class"></a>Vytvoření instance HwndHost odvozené třídy  
 Nakonec teď, když všechny klíče a karta podporu je na místě, které můžete vložit vaše <xref:System.Windows.Interop.HwndHost> do delší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.  Pokud hlavní aplikace je napsána v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], nejjednodušší způsob, jak pro něj na správném místě je ponechat prázdnou <xref:System.Windows.Controls.Border> element, kam chcete umístit <xref:System.Windows.Interop.HwndHost>.  Zde můžete vytvořit <xref:System.Windows.Controls.Border> s názvem `insertHwndHostHere`:  
  
```  
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
  
 Pak zbývá najít vhodná v pořadí kód pro vytvoření instance <xref:System.Windows.Interop.HwndHost> a připojte ho k <xref:System.Windows.Controls.Border>.  V tomto příkladu se umístí jej do konstruktoru pro <xref:System.Windows.Window> odvozené třídy:  
  
```  
public partial class Window1 : Window {  
    public Window1() {  
    }  
  
    void Window1_Loaded(object sender, RoutedEventArgs e) {  
        HwndHost host = new ManagedCpp.MyHwndHost();  
        insertHwndHostHere.Child = host;  
    }  
}  
```  
  
 Níž získáte:  
  
 ![Snímek obrazovky aplikace WPF](../../../../docs/framework/wpf/advanced/media/interoparch09.PNG "InteropArch09")  
  
## <a name="see-also"></a>Viz také  
 [Vzájemná spolupráce grafického subsystému WPF a systému Win32](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)
