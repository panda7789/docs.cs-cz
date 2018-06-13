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
ms.locfileid: "33547352"
---
# <a name="hosting-win32-content-in-wpf"></a><span data-ttu-id="94d09-102">Hostování obsahu Win32 v platformě WPF</span><span class="sxs-lookup"><span data-stu-id="94d09-102">Hosting Win32 Content in WPF</span></span>
## <a name="prerequisites"></a><span data-ttu-id="94d09-103">Požadavky</span><span class="sxs-lookup"><span data-stu-id="94d09-103">Prerequisites</span></span>  
 <span data-ttu-id="94d09-104">V tématu [WPF a vzájemná spolupráce Win32](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="94d09-104">See [WPF and Win32 Interoperation](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md).</span></span>  
  
## <a name="a-walkthrough-of-win32-inside-windows-presentation-framework-hwndhost"></a><span data-ttu-id="94d09-105">Návod Win32 uvnitř Windows Presentation Framework (HwndHost)</span><span class="sxs-lookup"><span data-stu-id="94d09-105">A Walkthrough of Win32 Inside Windows Presentation Framework (HwndHost)</span></span>  
 <span data-ttu-id="94d09-106">Znovu použít [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] obsahu uvnitř [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace, použijte <xref:System.Windows.Interop.HwndHost>, což je ovládací prvek, který umožňuje HWND vypadat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah.</span><span class="sxs-lookup"><span data-stu-id="94d09-106">To reuse [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] content inside [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications, use <xref:System.Windows.Interop.HwndHost>, which is a control that makes HWNDs look like [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content.</span></span>  <span data-ttu-id="94d09-107">Jako <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost> je jednoduchá používat: odvozena od <xref:System.Windows.Interop.HwndHost> a implementovat `BuildWindowCore` a `DestroyWindowCore` metod, vytvoří instanci vaše <xref:System.Windows.Interop.HwndHost> odvozené třídy a umístěte jej uvnitř vaší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="94d09-107">Like <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost> is straightforward to use: derive from <xref:System.Windows.Interop.HwndHost> and implement `BuildWindowCore` and `DestroyWindowCore` methods, then instantiate your <xref:System.Windows.Interop.HwndHost> derived class and place it inside your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>  
  
 <span data-ttu-id="94d09-108">Pokud vaše [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] logiku je již zabalené jako ovládací prvek, pak vaše `BuildWindowCore` implementace je trochu déle než volání `CreateWindow`.</span><span class="sxs-lookup"><span data-stu-id="94d09-108">If your [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] logic is already packaged as a control, then your `BuildWindowCore` implementation is little more than a call to `CreateWindow`.</span></span>  <span data-ttu-id="94d09-109">Chcete-li například vytvořit [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ListBox – ovládací prvek v [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="94d09-109">For example, to create a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] LISTBOX control in [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)]:</span></span>  
  
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
  
 <span data-ttu-id="94d09-110">Předpokládejme, ale [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kód není poměrně tak samostatná?</span><span class="sxs-lookup"><span data-stu-id="94d09-110">But suppose the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] code is not quite so self-contained?</span></span> <span data-ttu-id="94d09-111">Pokud ano, můžete vytvořit [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dialogové okno pole a vložit obsah do větší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="94d09-111">If so, you can create a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dialog box and embed its contents into a larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>  <span data-ttu-id="94d09-112">Ukázka zobrazuje v [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] a [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)], i když je také možné provést v jiném jazyce, nebo na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="94d09-112">The sample shows this in [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] and [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)], although it is also possible to do this in a different language or at the command line.</span></span>  
  
 <span data-ttu-id="94d09-113">Začněte s jednoduchý dialog, který se zkompiluje do [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] projektu.</span><span class="sxs-lookup"><span data-stu-id="94d09-113">Start with a simple dialog, which is compiled into a [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] project.</span></span>  
  
 <span data-ttu-id="94d09-114">V dalším kroku zavedení dialogu do delší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace:</span><span class="sxs-lookup"><span data-stu-id="94d09-114">Next, introduce the dialog into the larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application:</span></span>  
  
-   <span data-ttu-id="94d09-115">Kompilace [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] jako spravovaný (`/clr`)</span><span class="sxs-lookup"><span data-stu-id="94d09-115">Compile the [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] as managed (`/clr`)</span></span>  
  
-   <span data-ttu-id="94d09-116">Zapnout dialogu do ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="94d09-116">Turn the dialog into a control</span></span>  
  
-   <span data-ttu-id="94d09-117">Definování odvozené třídy z <xref:System.Windows.Interop.HwndHost> s `BuildWindowCore` a `DestroyWindowCore` metody</span><span class="sxs-lookup"><span data-stu-id="94d09-117">Define the derived class of <xref:System.Windows.Interop.HwndHost> with `BuildWindowCore` and `DestroyWindowCore` methods</span></span>  
  
-   <span data-ttu-id="94d09-118">Přepsání `TranslateAccelerator` metodu ke zpracování klíče dialogové okno</span><span class="sxs-lookup"><span data-stu-id="94d09-118">Override `TranslateAccelerator` method to handle dialog keys</span></span>  
  
-   <span data-ttu-id="94d09-119">Přepsání `TabInto` metoda pro podporu použití tabulátoru</span><span class="sxs-lookup"><span data-stu-id="94d09-119">Override `TabInto` method to support tabbing</span></span>  
  
-   <span data-ttu-id="94d09-120">Přepsání `OnMnemonic` metoda pro podporu mnemonické klávesy</span><span class="sxs-lookup"><span data-stu-id="94d09-120">Override `OnMnemonic` method to support mnemonics</span></span>  
  
-   <span data-ttu-id="94d09-121">Vytvoření instance <xref:System.Windows.Interop.HwndHost> podtřídami a umístí jej v rámci práva [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] – element</span><span class="sxs-lookup"><span data-stu-id="94d09-121">Instantiate the <xref:System.Windows.Interop.HwndHost> subclass and put it under the right [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element</span></span>  
  
### <a name="turn-the-dialog-into-a-control"></a><span data-ttu-id="94d09-122">Zapnout dialogu do ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="94d09-122">Turn the Dialog into a Control</span></span>  
 <span data-ttu-id="94d09-123">Dialogové okno můžete upravit na podřízenou HWND pomocí ws_child – a DS_CONTROL stylů.</span><span class="sxs-lookup"><span data-stu-id="94d09-123">You can turn a dialog box into a child HWND using the WS_CHILD and DS_CONTROL styles.</span></span>  <span data-ttu-id="94d09-124">Přejděte do souboru prostředků (.rc), kde je definován dialogové okno a najděte začátku definici dialogového okna:</span><span class="sxs-lookup"><span data-stu-id="94d09-124">Go into the resource file (.rc) where the dialog is defined, and find the beginning of the definition of the dialog:</span></span>  
  
```  
IDD_DIALOG1 DIALOGEX 0, 0, 303, 121  
STYLE DS_SETFONT | DS_MODALFRAME | DS_FIXEDSYS | WS_POPUP | WS_CAPTION | WS_SYSMENU  
```  
  
 <span data-ttu-id="94d09-125">Změna na druhém řádku pro:</span><span class="sxs-lookup"><span data-stu-id="94d09-125">Change the second line to:</span></span>  
  
```  
STYLE DS_SETFONT | WS_CHILD | WS_BORDER | DS_CONTROL  
```  
  
 <span data-ttu-id="94d09-126">Tato akce není plně je zabalit do ovládacího prvku nezávislý; stále je třeba volat `IsDialogMessage()` tak [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] může zpracovat některé zprávy, ale poskytuje snadný způsob, jak umístění těchto ovládacích prvků uvnitř jiné HWND řízení změn.</span><span class="sxs-lookup"><span data-stu-id="94d09-126">This action does not fully package it into a self-contained control; you still need to call `IsDialogMessage()` so [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] can process certain messages, but the control change does provide a straightforward way of putting those controls inside another HWND.</span></span>  
  
## <a name="subclass-hwndhost"></a><span data-ttu-id="94d09-127">Podtřída HwndHost</span><span class="sxs-lookup"><span data-stu-id="94d09-127">Subclass HwndHost</span></span>  
 <span data-ttu-id="94d09-128">Importujte následujících oborů názvů:</span><span class="sxs-lookup"><span data-stu-id="94d09-128">Import the following namespaces:</span></span>  
  
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
  
 <span data-ttu-id="94d09-129">Pak vytvořte třídu odvozenou z <xref:System.Windows.Interop.HwndHost> a přepsat `BuildWindowCore` a `DestroyWindowCore` metody:</span><span class="sxs-lookup"><span data-stu-id="94d09-129">Then create a derived class of <xref:System.Windows.Interop.HwndHost> and override the `BuildWindowCore` and `DestroyWindowCore` methods:</span></span>  
  
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
  
 <span data-ttu-id="94d09-130">Tady můžete použít `CreateDialog` vytvořit okno, které je ve skutečnosti ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="94d09-130">Here you use the `CreateDialog` to create the dialog box that is really a control.</span></span>  <span data-ttu-id="94d09-131">Vzhledem k tomu, že toto je jedna z metod první volána v rámci [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)], je vhodné provést některé standardní [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] inicializace voláním funkce později, nadefinujete názvem `InitializeGlobals()`:</span><span class="sxs-lookup"><span data-stu-id="94d09-131">Since this is one of the first methods called inside the [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)], you should also do some standard [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] initialization by calling a function you will define later, called `InitializeGlobals()`:</span></span>  
  
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
  
### <a name="override-translateaccelerator-method-to-handle-dialog-keys"></a><span data-ttu-id="94d09-132">Potlačí metodu TranslateAccelerator za účelem zpracování klíče dialogové okno</span><span class="sxs-lookup"><span data-stu-id="94d09-132">Override TranslateAccelerator Method to Handle Dialog Keys</span></span>  
 <span data-ttu-id="94d09-133">Pokud jste spustili Tato ukázka nyní, které byste získali, dialogové okno Ovládací prvek, který zobrazuje, ale můžete všechny klávesnice zpracování této díky by ignorovat dialogové okno funkční dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="94d09-133">If you ran this sample now, you would get a dialog control that displays, but it would ignore all of the keyboard processing that makes a dialog box a functional dialog box.</span></span>  <span data-ttu-id="94d09-134">Nyní by měly přepsat `TranslateAccelerator` implementace (který pochází z `IKeyboardInputSink`, rozhraní, <xref:System.Windows.Interop.HwndHost> implementuje).</span><span class="sxs-lookup"><span data-stu-id="94d09-134">You should now override the `TranslateAccelerator` implementation (which comes from `IKeyboardInputSink`, an interface that <xref:System.Windows.Interop.HwndHost> implements).</span></span>  <span data-ttu-id="94d09-135">Tato metoda je volána při WM_KEYDOWN a WM_SYSKEYDOWN aplikace obdrží.</span><span class="sxs-lookup"><span data-stu-id="94d09-135">This method gets called when the application receives WM_KEYDOWN and WM_SYSKEYDOWN.</span></span>  
  
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
  
 <span data-ttu-id="94d09-136">Toto je velké množství kódu v jednu část, takže by mohl použít některé podrobnější vysvětlení.</span><span class="sxs-lookup"><span data-stu-id="94d09-136">This is a lot of code in one piece, so it could use some more detailed explanations.</span></span>  <span data-ttu-id="94d09-137">První, kódu pomocí [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] a [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] makra, je třeba si uvědomit, že již makro s názvem `TranslateAccelerator`, která je definována v winuser:</span><span class="sxs-lookup"><span data-stu-id="94d09-137">First, the code using [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] and [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] macros; you need to be aware that there is already a macro named `TranslateAccelerator`, which is defined in winuser.h:</span></span>  
  
```  
#define TranslateAccelerator  TranslateAcceleratorW  
```  
  
 <span data-ttu-id="94d09-138">Proto nezapomeňte definovat `TranslateAccelerator` metoda a ne `TranslateAcceleratorW` metoda.</span><span class="sxs-lookup"><span data-stu-id="94d09-138">So make sure to define a `TranslateAccelerator` method and not a `TranslateAcceleratorW` method.</span></span>  
  
 <span data-ttu-id="94d09-139">Podobně je spravovaných i nespravovaných winuser MSG `Microsoft::Win32::MSG` struktura.</span><span class="sxs-lookup"><span data-stu-id="94d09-139">Similarly, there is both the unmanaged winuser.h MSG and the managed `Microsoft::Win32::MSG` struct.</span></span>  <span data-ttu-id="94d09-140">Můžete odstranit nejednoznačnost mezi nimi pomocí [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] `::` operátor.</span><span class="sxs-lookup"><span data-stu-id="94d09-140">You can disambiguate between the two using the [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] `::` operator.</span></span>  
  
```  
virtual bool TranslateAccelerator(System::Windows::Interop::MSG% msg,   
    ModifierKeys modifiers) override   
{  
    ::MSG m = ConvertMessage(msg);  
```  
  
 <span data-ttu-id="94d09-141">Jak zprávy o obsahovaly stejná data, ale někdy je snazší s ním pracovat definici nespravované, v této ukázce můžete definovat zřejmé převod rutiny:</span><span class="sxs-lookup"><span data-stu-id="94d09-141">Both MSGs have the same data, but sometimes it is easier to work with the unmanaged definition, so in this sample you can define the obvious conversion routine:</span></span>  
  
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
  
 <span data-ttu-id="94d09-142">Zpět na `TranslateAccelerator`.</span><span class="sxs-lookup"><span data-stu-id="94d09-142">Back to `TranslateAccelerator`.</span></span>  <span data-ttu-id="94d09-143">Základní princip je volání [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] funkce `IsDialogMessage` tolik práci co možná, ale `IsDialogMessage` nemá přístup k ničemu mimo dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="94d09-143">The basic principle is to call the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] function `IsDialogMessage` to do as much work as possible, but `IsDialogMessage` does not have access to anything outside the dialog.</span></span> <span data-ttu-id="94d09-144">Na kartě uživatele kolem tohoto dialogového okna při použití tabulátoru běží po poslední ovládacího prvku v dialogovém okně pro naše, budete muset nastavit fokus [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] část voláním `IKeyboardInputSite::OnNoMoreStops`.</span><span class="sxs-lookup"><span data-stu-id="94d09-144">As a user tab around the dialog, when tabbing runs past the last control in our dialog, you need to set focus to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] portion by calling `IKeyboardInputSite::OnNoMoreStops`.</span></span>  
  
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
  
 <span data-ttu-id="94d09-145">Nakonec volání `IsDialogMessage`.</span><span class="sxs-lookup"><span data-stu-id="94d09-145">Finally, call `IsDialogMessage`.</span></span>  <span data-ttu-id="94d09-146">Ale jeden z odpovědnosti `TranslateAccelerator` oznamuje, metoda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] jestli zpracovávat klávesu nebo ne.</span><span class="sxs-lookup"><span data-stu-id="94d09-146">But one of the responsibilities of a `TranslateAccelerator` method is telling [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] whether you handled the keystroke or not.</span></span> <span data-ttu-id="94d09-147">Pokud jste se nepodařilo zpracovat, může tunelovat vstupní událost a bublin procházení zbývající aplikace.</span><span class="sxs-lookup"><span data-stu-id="94d09-147">If you did not handle it, the input event can tunnel and bubble through the rest of the application.</span></span> <span data-ttu-id="94d09-148">Zde bude vystavovat datového toku zvuku nabízí messange zpracování klávesnice a povaze vstupní architektura v [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].</span><span class="sxs-lookup"><span data-stu-id="94d09-148">Here, you will expose a quirk of keyboard messange handling and the nature of the input architecture in [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].</span></span> <span data-ttu-id="94d09-149">Bohužel `IsDialogMessage` nevrací žádným způsobem zda zpracovává konkrétní klávesu.</span><span class="sxs-lookup"><span data-stu-id="94d09-149">Unfortunately, `IsDialogMessage` does not return in any way whether it handles a particular keystroke.</span></span>  <span data-ttu-id="94d09-150">I horší, bude volat `DispatchMessage()` na stisknutí kláves by nemělo vyřizovat!</span><span class="sxs-lookup"><span data-stu-id="94d09-150">Even worse, it will call `DispatchMessage()` on keystrokes it should not handle!</span></span>  <span data-ttu-id="94d09-151">Budete muset provádět zpětnou analýzu `IsDialogMessage`a pouze volání pro bude zpracovávat klíče vy víte, že:</span><span class="sxs-lookup"><span data-stu-id="94d09-151">So you will have to reverse-engineer `IsDialogMessage`, and only call it for the keys you know it will handle:</span></span>  
  
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
  
### <a name="override-tabinto-method-to-support-tabbing"></a><span data-ttu-id="94d09-152">Potlačí metodu TabInto pro podporu použití tabulátoru</span><span class="sxs-lookup"><span data-stu-id="94d09-152">Override TabInto Method to Support Tabbing</span></span>  
 <span data-ttu-id="94d09-153">Teď, když jste implementovali `TranslateAccelerator`, uživatel může kartě kolem uvnitř dialogové okno pole a karta mimo ho do delší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="94d09-153">Now that you have implemented `TranslateAccelerator`, a user can tab around inside the dialog box and tab out of it into the greater [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>  <span data-ttu-id="94d09-154">Ale uživatel nemůže kartě zpět do dialogových oken.</span><span class="sxs-lookup"><span data-stu-id="94d09-154">But a user cannot tab back into the dialog box.</span></span>  <span data-ttu-id="94d09-155">K řešení, které, přepíšete `TabInto`:</span><span class="sxs-lookup"><span data-stu-id="94d09-155">To solve that, you override `TabInto`:</span></span>  
  
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
  
 <span data-ttu-id="94d09-156">`TraversalRequest` Parametr řekne, jestli je na kartě Akce kartě nebo shift.</span><span class="sxs-lookup"><span data-stu-id="94d09-156">The `TraversalRequest` parameter tells you whether the tab action is a tab or shift tab.</span></span>  
  
### <a name="override-onmnemonic-method-to-support-mnemonics"></a><span data-ttu-id="94d09-157">Potlačí metodu OnMnemonic pro podporu mnemonické klávesy</span><span class="sxs-lookup"><span data-stu-id="94d09-157">Override OnMnemonic Method to Support Mnemonics</span></span>  
 <span data-ttu-id="94d09-158">Zpracování pomocí klávesnice je téměř dokončena, ale je jedna věc chybí – klávesové zkratky nefungují.</span><span class="sxs-lookup"><span data-stu-id="94d09-158">Keyboard handling is almost complete, but there is one thing missing – mnemonics do not work.</span></span>  <span data-ttu-id="94d09-159">Pokud uživatel stiskne klávesu alt-F, fokus doe není přejít na "křestní jméno:" textové pole.</span><span class="sxs-lookup"><span data-stu-id="94d09-159">If a user presses alt-F, focus doe not jump to the "First name:" edit box.</span></span> <span data-ttu-id="94d09-160">Ano, můžete přepsat `OnMnemonic` metoda:</span><span class="sxs-lookup"><span data-stu-id="94d09-160">So, you override the `OnMnemonic` method:</span></span>  
  
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
  
 <span data-ttu-id="94d09-161">Proč ne volání `IsDialogMessage` tady?</span><span class="sxs-lookup"><span data-stu-id="94d09-161">Why not call `IsDialogMessage` here?</span></span>  <span data-ttu-id="94d09-162">Můžete mít stejný problém jako před – je potřeba mít k informování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] code, jestli váš kód zpracovávat klávesu nebo Ne, a `IsDialogMessage` nejde udělat.</span><span class="sxs-lookup"><span data-stu-id="94d09-162">You have the same issue as before--you need to be able to inform [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] code whether your code handled the keystroke or not, and `IsDialogMessage` cannot do that.</span></span>  <span data-ttu-id="94d09-163">Také druhý problémem je, protože `IsDialogMessage` odmítá ke zpracování symbolické Pokud cílených HWND není uvnitř dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="94d09-163">There is also a second issue, because `IsDialogMessage` refuses to process the mnemonic if the focused HWND is not inside the dialog box.</span></span>  
  
### <a name="instantiate-the-hwndhost-derived-class"></a><span data-ttu-id="94d09-164">Vytvoření instance HwndHost odvozené třídy</span><span class="sxs-lookup"><span data-stu-id="94d09-164">Instantiate the HwndHost Derived Class</span></span>  
 <span data-ttu-id="94d09-165">Nakonec teď, když všechny klíče a karta podporu je na místě, které můžete vložit vaše <xref:System.Windows.Interop.HwndHost> do delší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="94d09-165">Finally, now that all the key and tab support is in place, you can put your <xref:System.Windows.Interop.HwndHost> into the larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>  <span data-ttu-id="94d09-166">Pokud hlavní aplikace je napsána v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], nejjednodušší způsob, jak pro něj na správném místě je ponechat prázdnou <xref:System.Windows.Controls.Border> element, kam chcete umístit <xref:System.Windows.Interop.HwndHost>.</span><span class="sxs-lookup"><span data-stu-id="94d09-166">If the main application is written in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], the easiest way to put it in the right place is to leave an empty <xref:System.Windows.Controls.Border> element where you want to put the <xref:System.Windows.Interop.HwndHost>.</span></span>  <span data-ttu-id="94d09-167">Zde můžete vytvořit <xref:System.Windows.Controls.Border> s názvem `insertHwndHostHere`:</span><span class="sxs-lookup"><span data-stu-id="94d09-167">Here you create a <xref:System.Windows.Controls.Border> named `insertHwndHostHere`:</span></span>  
  
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
  
 <span data-ttu-id="94d09-168">Pak zbývá najít vhodná v pořadí kód pro vytvoření instance <xref:System.Windows.Interop.HwndHost> a připojte ho k <xref:System.Windows.Controls.Border>.</span><span class="sxs-lookup"><span data-stu-id="94d09-168">Then all that remains is to find a good place in code sequence to instantiate the <xref:System.Windows.Interop.HwndHost> and connect it to the <xref:System.Windows.Controls.Border>.</span></span>  <span data-ttu-id="94d09-169">V tomto příkladu se umístí jej do konstruktoru pro <xref:System.Windows.Window> odvozené třídy:</span><span class="sxs-lookup"><span data-stu-id="94d09-169">In this example, you will put it inside the constructor for the <xref:System.Windows.Window> derived class:</span></span>  
  
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
  
 <span data-ttu-id="94d09-170">Níž získáte:</span><span class="sxs-lookup"><span data-stu-id="94d09-170">Which gives you:</span></span>  
  
 <span data-ttu-id="94d09-171">![Snímek obrazovky aplikace WPF](../../../../docs/framework/wpf/advanced/media/interoparch09.PNG "InteropArch09")</span><span class="sxs-lookup"><span data-stu-id="94d09-171">![WPF application screen shot](../../../../docs/framework/wpf/advanced/media/interoparch09.PNG "InteropArch09")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94d09-172">Viz také</span><span class="sxs-lookup"><span data-stu-id="94d09-172">See Also</span></span>  
 [<span data-ttu-id="94d09-173">Vzájemná spolupráce grafického subsystému WPF a systému Win32</span><span class="sxs-lookup"><span data-stu-id="94d09-173">WPF and Win32 Interoperation</span></span>](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)
