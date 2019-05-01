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
# <a name="hosting-win32-content-in-wpf"></a><span data-ttu-id="d321d-102">Hostování obsahu Win32 v platformě WPF</span><span class="sxs-lookup"><span data-stu-id="d321d-102">Hosting Win32 Content in WPF</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d321d-103">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d321d-103">Prerequisites</span></span>

<span data-ttu-id="d321d-104">Zobrazit [WPF a systému Win32 vzájemná spolupráce grafického subsystému](wpf-and-win32-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="d321d-104">See [WPF and Win32 Interoperation](wpf-and-win32-interoperation.md).</span></span>

## <a name="a-walkthrough-of-win32-inside-windows-presentation-framework-hwndhost"></a><span data-ttu-id="d321d-105">Názorný postup Win32 v rámci Windows Presentation Framework (HwndHost)</span><span class="sxs-lookup"><span data-stu-id="d321d-105">A Walkthrough of Win32 Inside Windows Presentation Framework (HwndHost)</span></span>

<span data-ttu-id="d321d-106">Pro opětovné použití [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] obsahu uvnitř [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikací, použijte <xref:System.Windows.Interop.HwndHost>, což je ovládací prvek, který umožňuje HWND vypadat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah.</span><span class="sxs-lookup"><span data-stu-id="d321d-106">To reuse [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] content inside [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications, use <xref:System.Windows.Interop.HwndHost>, which is a control that makes HWNDs look like [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content.</span></span> <span data-ttu-id="d321d-107">Jako <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost> je jednoduché použití: jsou odvozeny z <xref:System.Windows.Interop.HwndHost> a implementovat `BuildWindowCore` a `DestroyWindowCore` metody, potom vytvořte instanci vaší <xref:System.Windows.Interop.HwndHost> odvozené třídy a umístěte ji uvnitř vaší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="d321d-107">Like <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost> is straightforward to use: derive from <xref:System.Windows.Interop.HwndHost> and implement `BuildWindowCore` and `DestroyWindowCore` methods, then instantiate your <xref:System.Windows.Interop.HwndHost> derived class and place it inside your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>

<span data-ttu-id="d321d-108">Pokud vaše [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] logiky je už zabalené jako ovládací prvek, pak vaše `BuildWindowCore` implementace je poněkud složitější než volání `CreateWindow`.</span><span class="sxs-lookup"><span data-stu-id="d321d-108">If your [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] logic is already packaged as a control, then your `BuildWindowCore` implementation is little more than a call to `CreateWindow`.</span></span> <span data-ttu-id="d321d-109">Například, chcete-li vytvořit [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] ListBox – ovládací prvek v [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="d321d-109">For example, to create a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] LISTBOX control in [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)]:</span></span>

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

<span data-ttu-id="d321d-110">Předpokládejme, ale [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] kód není úplně tak samostatná?</span><span class="sxs-lookup"><span data-stu-id="d321d-110">But suppose the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] code is not quite so self-contained?</span></span> <span data-ttu-id="d321d-111">Pokud ano, můžete vytvořit [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dialogové okno pole a jeho obsah vložit do větší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="d321d-111">If so, you can create a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dialog box and embed its contents into a larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="d321d-112">Tato ukázka vysvětluje to [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] a [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)], i když je také možné provést v jiném jazyce nebo na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="d321d-112">The sample shows this in [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] and [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)], although it is also possible to do this in a different language or at the command line.</span></span>

<span data-ttu-id="d321d-113">Začněte s jednoduchou dialog, který je zkompilován [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] projektu.</span><span class="sxs-lookup"><span data-stu-id="d321d-113">Start with a simple dialog, which is compiled into a [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] project.</span></span>

<span data-ttu-id="d321d-114">V dalším kroku představovat dialogového okna na větší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace:</span><span class="sxs-lookup"><span data-stu-id="d321d-114">Next, introduce the dialog into the larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application:</span></span>

- <span data-ttu-id="d321d-115">Kompilace [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] jako spravovaný (`/clr`)</span><span class="sxs-lookup"><span data-stu-id="d321d-115">Compile the [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)] as managed (`/clr`)</span></span>

- <span data-ttu-id="d321d-116">Zapnout dialogového okna do ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="d321d-116">Turn the dialog into a control</span></span>

- <span data-ttu-id="d321d-117">Definice třídy odvozené z <xref:System.Windows.Interop.HwndHost> s `BuildWindowCore` a `DestroyWindowCore` metody</span><span class="sxs-lookup"><span data-stu-id="d321d-117">Define the derived class of <xref:System.Windows.Interop.HwndHost> with `BuildWindowCore` and `DestroyWindowCore` methods</span></span>

- <span data-ttu-id="d321d-118">Přepsat `TranslateAccelerator` metodu ke zpracování dialogové okno klíče</span><span class="sxs-lookup"><span data-stu-id="d321d-118">Override `TranslateAccelerator` method to handle dialog keys</span></span>

- <span data-ttu-id="d321d-119">Přepsat `TabInto` metoda k podpoře tabulátoru</span><span class="sxs-lookup"><span data-stu-id="d321d-119">Override `TabInto` method to support tabbing</span></span>

- <span data-ttu-id="d321d-120">Přepsat `OnMnemonic` metody pro podporu klávesových zkratek</span><span class="sxs-lookup"><span data-stu-id="d321d-120">Override `OnMnemonic` method to support mnemonics</span></span>

- <span data-ttu-id="d321d-121">Vytvoření instance <xref:System.Windows.Interop.HwndHost> podtřídy a vložte ji pod vpravo [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] – element</span><span class="sxs-lookup"><span data-stu-id="d321d-121">Instantiate the <xref:System.Windows.Interop.HwndHost> subclass and put it under the right [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element</span></span>

### <a name="turn-the-dialog-into-a-control"></a><span data-ttu-id="d321d-122">Zapnout dialogového okna do ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="d321d-122">Turn the Dialog into a Control</span></span>

<span data-ttu-id="d321d-123">Proměňte dialogového okna na podřízené HWND pomocí WS_CHILD a DS_CONTROL stylů.</span><span class="sxs-lookup"><span data-stu-id="d321d-123">You can turn a dialog box into a child HWND using the WS_CHILD and DS_CONTROL styles.</span></span> <span data-ttu-id="d321d-124">Přejděte do souboru prostředků (.rc), kde je definován dialogového okna a najít začátek definici dialogového okna:</span><span class="sxs-lookup"><span data-stu-id="d321d-124">Go into the resource file (.rc) where the dialog is defined, and find the beginning of the definition of the dialog:</span></span>

```
IDD_DIALOG1 DIALOGEX 0, 0, 303, 121
STYLE DS_SETFONT | DS_MODALFRAME | DS_FIXEDSYS | WS_POPUP | WS_CAPTION | WS_SYSMENU
```

<span data-ttu-id="d321d-125">Změňte druhý řádek na:</span><span class="sxs-lookup"><span data-stu-id="d321d-125">Change the second line to:</span></span>

```
STYLE DS_SETFONT | WS_CHILD | WS_BORDER | DS_CONTROL
```

<span data-ttu-id="d321d-126">Tato akce není balíček plně ho do samostatné ovládacího prvku; je stále potřeba volat `IsDialogMessage()` tak [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] může zpracovat některé zprávy, ale poskytuje jednoduchý způsob, jak umístění těchto ovládacích prvků uvnitř jiného HWND Změna ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="d321d-126">This action does not fully package it into a self-contained control; you still need to call `IsDialogMessage()` so [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] can process certain messages, but the control change does provide a straightforward way of putting those controls inside another HWND.</span></span>

## <a name="subclass-hwndhost"></a><span data-ttu-id="d321d-127">HwndHost podtřídy</span><span class="sxs-lookup"><span data-stu-id="d321d-127">Subclass HwndHost</span></span>

<span data-ttu-id="d321d-128">Importujte následující obory názvů:</span><span class="sxs-lookup"><span data-stu-id="d321d-128">Import the following namespaces:</span></span>

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

<span data-ttu-id="d321d-129">Vytvořte třídu odvozenou z <xref:System.Windows.Interop.HwndHost> a přepsat `BuildWindowCore` a `DestroyWindowCore` metody:</span><span class="sxs-lookup"><span data-stu-id="d321d-129">Then create a derived class of <xref:System.Windows.Interop.HwndHost> and override the `BuildWindowCore` and `DestroyWindowCore` methods:</span></span>

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

<span data-ttu-id="d321d-130">Zde použijete `CreateDialog` vytvořit dialogové okno, které je ve skutečnosti ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="d321d-130">Here you use the `CreateDialog` to create the dialog box that is really a control.</span></span> <span data-ttu-id="d321d-131">Protože to je jedna z prvních metod volat [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)], by měl také provést některé standardní [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] inicializace voláním funkce budou definovat později, volá `InitializeGlobals()`:</span><span class="sxs-lookup"><span data-stu-id="d321d-131">Since this is one of the first methods called inside the [!INCLUDE[TLA2#tla_dll](../../../../includes/tla2sharptla-dll-md.md)], you should also do some standard [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] initialization by calling a function you will define later, called `InitializeGlobals()`:</span></span>

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

### <a name="override-translateaccelerator-method-to-handle-dialog-keys"></a><span data-ttu-id="d321d-132">Potlačí metodu TranslateAccelerator za účelem zpracování dialogové okno klíče</span><span class="sxs-lookup"><span data-stu-id="d321d-132">Override TranslateAccelerator Method to Handle Dialog Keys</span></span>

<span data-ttu-id="d321d-133">Pokud jste spustili této ukázce nyní, získali byste ovládací prvek dialogového okna, která zobrazuje, ale ho by Přeskakovat vše klávesnice zpracování této vytvoří dialogové okno funkční dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="d321d-133">If you ran this sample now, you would get a dialog control that displays, but it would ignore all of the keyboard processing that makes a dialog box a functional dialog box.</span></span> <span data-ttu-id="d321d-134">Teď byste měli přepsat `TranslateAccelerator` implementace (které pochází z `IKeyboardInputSink`, rozhraní, který <xref:System.Windows.Interop.HwndHost> implementuje).</span><span class="sxs-lookup"><span data-stu-id="d321d-134">You should now override the `TranslateAccelerator` implementation (which comes from `IKeyboardInputSink`, an interface that <xref:System.Windows.Interop.HwndHost> implements).</span></span> <span data-ttu-id="d321d-135">Tato metoda volána, když aplikace obdrží WM_KEYDOWN a WM_SYSKEYDOWN.</span><span class="sxs-lookup"><span data-stu-id="d321d-135">This method gets called when the application receives WM_KEYDOWN and WM_SYSKEYDOWN.</span></span>

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

<span data-ttu-id="d321d-136">To je velké množství kódu v jednu část, protože může využívat některé podrobnější vysvětlení.</span><span class="sxs-lookup"><span data-stu-id="d321d-136">This is a lot of code in one piece, so it could use some more detailed explanations.</span></span> <span data-ttu-id="d321d-137">První, kód s využitím [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] a [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] makra; co potřebujete vědět, že už existuje s názvem makra `TranslateAccelerator`, který je definován v winuser:</span><span class="sxs-lookup"><span data-stu-id="d321d-137">First, the code using [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] and [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] macros; you need to be aware that there is already a macro named `TranslateAccelerator`, which is defined in winuser.h:</span></span>

```cpp
#define TranslateAccelerator  TranslateAcceleratorW
```

<span data-ttu-id="d321d-138">Tak definovat `TranslateAccelerator` – metoda a ne `TranslateAcceleratorW` metoda.</span><span class="sxs-lookup"><span data-stu-id="d321d-138">So make sure to define a `TranslateAccelerator` method and not a `TranslateAcceleratorW` method.</span></span>

<span data-ttu-id="d321d-139">Podobně je spravované i nespravované winuser MSG `Microsoft::Win32::MSG` struktury.</span><span class="sxs-lookup"><span data-stu-id="d321d-139">Similarly, there is both the unmanaged winuser.h MSG and the managed `Microsoft::Win32::MSG` struct.</span></span> <span data-ttu-id="d321d-140">Můžete odstranit nejednoznačnost mezi nimi pomocí [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] `::` operátor.</span><span class="sxs-lookup"><span data-stu-id="d321d-140">You can disambiguate between the two using the [!INCLUDE[TLA#tla_cpp](../../../../includes/tlasharptla-cpp-md.md)] `::` operator.</span></span>

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

<span data-ttu-id="d321d-141">Zpět na `TranslateAccelerator`.</span><span class="sxs-lookup"><span data-stu-id="d321d-141">Back to `TranslateAccelerator`.</span></span> <span data-ttu-id="d321d-142">Základním principem je volání [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] funkce `IsDialogMessage` tolik práci nejvíce, ale `IsDialogMessage` nemá přístup k ničemu mimo dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="d321d-142">The basic principle is to call the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] function `IsDialogMessage` to do as much work as possible, but `IsDialogMessage` does not have access to anything outside the dialog.</span></span> <span data-ttu-id="d321d-143">Na kartě uživatele kolem dialogové okno, při procházení tabulátorem běží za poslední ovládací prvek v našich dialogového okna, je potřeba nastavit fokus na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] část voláním `IKeyboardInputSite::OnNoMoreStops`.</span><span class="sxs-lookup"><span data-stu-id="d321d-143">As a user tab around the dialog, when tabbing runs past the last control in our dialog, you need to set focus to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] portion by calling `IKeyboardInputSite::OnNoMoreStops`.</span></span>

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

<span data-ttu-id="d321d-144">Nakonec proveďte volání `IsDialogMessage`.</span><span class="sxs-lookup"><span data-stu-id="d321d-144">Finally, call `IsDialogMessage`.</span></span> <span data-ttu-id="d321d-145">Jeden odpovědnosti `TranslateAccelerator` sděluje metoda [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Určuje, zda stisknutí kláves zpracována či nikoli.</span><span class="sxs-lookup"><span data-stu-id="d321d-145">But one of the responsibilities of a `TranslateAccelerator` method is telling [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] whether you handled the keystroke or not.</span></span> <span data-ttu-id="d321d-146">Pokud jste se nepodařilo zpracovat, můžete tunelového propojení událost vstupu a bubliny procházení zbývající části aplikace.</span><span class="sxs-lookup"><span data-stu-id="d321d-146">If you did not handle it, the input event can tunnel and bubble through the rest of the application.</span></span> <span data-ttu-id="d321d-147">Tady bude vystavovat datového toku zvuku nabízí messange zpracování klávesnice a povaze architektura vstupu v [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d321d-147">Here, you will expose a quirk of keyboard messange handling and the nature of the input architecture in [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)].</span></span> <span data-ttu-id="d321d-148">Bohužel `IsDialogMessage` nevrací žádným způsobem, zda zpracovává konkrétní stisk klávesy.</span><span class="sxs-lookup"><span data-stu-id="d321d-148">Unfortunately, `IsDialogMessage` does not return in any way whether it handles a particular keystroke.</span></span> <span data-ttu-id="d321d-149">Ještě hůř, bude volat `DispatchMessage()` na stisknutí kláves by nemělo vyřizovat!</span><span class="sxs-lookup"><span data-stu-id="d321d-149">Even worse, it will call `DispatchMessage()` on keystrokes it should not handle!</span></span>  <span data-ttu-id="d321d-150">Proto budete muset provést zpětnou analýzu `IsDialogMessage`a pouze volání pro klíče, můžete ji znát zpracuje:</span><span class="sxs-lookup"><span data-stu-id="d321d-150">So you will have to reverse-engineer `IsDialogMessage`, and only call it for the keys you know it will handle:</span></span>

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

### <a name="override-tabinto-method-to-support-tabbing"></a><span data-ttu-id="d321d-151">Potlačí metodu TabInto pro podporu tabulátor</span><span class="sxs-lookup"><span data-stu-id="d321d-151">Override TabInto Method to Support Tabbing</span></span>

<span data-ttu-id="d321d-152">Teď, když jste implementovali `TranslateAccelerator`, uživatel může kartě kolem v dialogovém okně pole a karty z ní do větší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="d321d-152">Now that you have implemented `TranslateAccelerator`, a user can tab around inside the dialog box and tab out of it into the greater [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="d321d-153">Ale uživatel nemůže kartě zpět do dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="d321d-153">But a user cannot tab back into the dialog box.</span></span> <span data-ttu-id="d321d-154">Chcete-li to vyřešit, přepište `TabInto`:</span><span class="sxs-lookup"><span data-stu-id="d321d-154">To solve that, you override `TabInto`:</span></span>

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

<span data-ttu-id="d321d-155">`TraversalRequest` Parametr zjistíte, jestli akce karta je karta nebo shift tab.</span><span class="sxs-lookup"><span data-stu-id="d321d-155">The `TraversalRequest` parameter tells you whether the tab action is a tab or shift tab.</span></span>

### <a name="override-onmnemonic-method-to-support-mnemonics"></a><span data-ttu-id="d321d-156">Potlačí metodu OnMnemonic za účelem podpory klávesových zkratek</span><span class="sxs-lookup"><span data-stu-id="d321d-156">Override OnMnemonic Method to Support Mnemonics</span></span>

<span data-ttu-id="d321d-157">Zpracování pomocí klávesnice je skoro hotová, ale je jedna věc, kterou chybí – klávesových zkratek, nebudou fungovat.</span><span class="sxs-lookup"><span data-stu-id="d321d-157">Keyboard handling is almost complete, but there is one thing missing – mnemonics do not work.</span></span> <span data-ttu-id="d321d-158">Pokud uživatel stiskne klávesu alt-F, doe fokus není přejít "křestní jméno:" upravit pole.</span><span class="sxs-lookup"><span data-stu-id="d321d-158">If a user presses alt-F, focus doe not jump to the "First name:" edit box.</span></span> <span data-ttu-id="d321d-159">Přepíšete tak, `OnMnemonic` metody:</span><span class="sxs-lookup"><span data-stu-id="d321d-159">So, you override the `OnMnemonic` method:</span></span>

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

<span data-ttu-id="d321d-160">Případně proč bezpečná není volání `IsDialogMessage` tady?</span><span class="sxs-lookup"><span data-stu-id="d321d-160">Why not call `IsDialogMessage` here?</span></span>  <span data-ttu-id="d321d-161">Budete mít stejný problém před – potřebujete mít možnost informovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kódu, jestli váš kód zpracovává stisk klávesy nebo Ne, a `IsDialogMessage` nemůžete udělat.</span><span class="sxs-lookup"><span data-stu-id="d321d-161">You have the same issue as before--you need to be able to inform [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] code whether your code handled the keystroke or not, and `IsDialogMessage` cannot do that.</span></span> <span data-ttu-id="d321d-162">Existuje problém také druhý, protože `IsDialogMessage` odmítne zpracovat symbol, pokud není cílené HWND v dialogovém okně.</span><span class="sxs-lookup"><span data-stu-id="d321d-162">There is also a second issue, because `IsDialogMessage` refuses to process the mnemonic if the focused HWND is not inside the dialog box.</span></span>

### <a name="instantiate-the-hwndhost-derived-class"></a><span data-ttu-id="d321d-163">Vytvoření instance HwndHost odvozené třídy</span><span class="sxs-lookup"><span data-stu-id="d321d-163">Instantiate the HwndHost Derived Class</span></span>

<span data-ttu-id="d321d-164">A konečně, teď, když všechny klíče a kartu podporu na místě, můžete umístit vaše <xref:System.Windows.Interop.HwndHost> do větší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="d321d-164">Finally, now that all the key and tab support is in place, you can put your <xref:System.Windows.Interop.HwndHost> into the larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="d321d-165">Pokud je hlavní aplikace napsané v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], nejjednodušší způsob, jak vložit na správném místě je ponechat prázdnou <xref:System.Windows.Controls.Border> elementu, kam chcete umístit <xref:System.Windows.Interop.HwndHost>.</span><span class="sxs-lookup"><span data-stu-id="d321d-165">If the main application is written in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], the easiest way to put it in the right place is to leave an empty <xref:System.Windows.Controls.Border> element where you want to put the <xref:System.Windows.Interop.HwndHost>.</span></span> <span data-ttu-id="d321d-166">Zde můžete vytvořit <xref:System.Windows.Controls.Border> s názvem `insertHwndHostHere`:</span><span class="sxs-lookup"><span data-stu-id="d321d-166">Here you create a <xref:System.Windows.Controls.Border> named `insertHwndHostHere`:</span></span>

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

<span data-ttu-id="d321d-167">Pak už jen zbývá k vyhledání vhodné místo v pořadí kód k vytvoření instance <xref:System.Windows.Interop.HwndHost> a propojte jej s <xref:System.Windows.Controls.Border>.</span><span class="sxs-lookup"><span data-stu-id="d321d-167">Then all that remains is to find a good place in code sequence to instantiate the <xref:System.Windows.Interop.HwndHost> and connect it to the <xref:System.Windows.Controls.Border>.</span></span> <span data-ttu-id="d321d-168">V tomto příkladu je zařadí ho uvnitř konstruktoru pro <xref:System.Windows.Window> odvozené třídy:</span><span class="sxs-lookup"><span data-stu-id="d321d-168">In this example, you will put it inside the constructor for the <xref:System.Windows.Window> derived class:</span></span>

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

<span data-ttu-id="d321d-169">– Umožňuje:</span><span class="sxs-lookup"><span data-stu-id="d321d-169">Which gives you:</span></span>

![Snímek obrazovky spuštěné aplikace WPF.](./media/hosting-win32-content-in-wpf/windows-presentation-foundation-application.png)

## <a name="see-also"></a><span data-ttu-id="d321d-171">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d321d-171">See also</span></span>

- [<span data-ttu-id="d321d-172">Vzájemná spolupráce grafického subsystému WPF a systému Win32</span><span class="sxs-lookup"><span data-stu-id="d321d-172">WPF and Win32 Interoperation</span></span>](wpf-and-win32-interoperation.md)
