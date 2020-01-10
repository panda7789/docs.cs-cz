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
# <a name="hosting-win32-content-in-wpf"></a><span data-ttu-id="9668a-102">Hostování obsahu Win32 v platformě WPF</span><span class="sxs-lookup"><span data-stu-id="9668a-102">Hosting Win32 Content in WPF</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9668a-103">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9668a-103">Prerequisites</span></span>

<span data-ttu-id="9668a-104">Viz [spolupráce WPF a Win32](wpf-and-win32-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="9668a-104">See [WPF and Win32 Interoperation](wpf-and-win32-interoperation.md).</span></span>

## <a name="a-walkthrough-of-win32-inside-windows-presentation-framework-hwndhost"></a><span data-ttu-id="9668a-105">Návod k Win32 v rámci Windows Presentation Framework (HwndHost)</span><span class="sxs-lookup"><span data-stu-id="9668a-105">A Walkthrough of Win32 Inside Windows Presentation Framework (HwndHost)</span></span>

<span data-ttu-id="9668a-106">Chcete-li znovu použít obsah Win32 v aplikacích [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikací, použijte <xref:System.Windows.Interop.HwndHost>, což je ovládací prvek, který umožňuje, aby HWND vypadaly jako [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah.</span><span class="sxs-lookup"><span data-stu-id="9668a-106">To reuse Win32 content inside [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications, use <xref:System.Windows.Interop.HwndHost>, which is a control that makes HWNDs look like [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content.</span></span> <span data-ttu-id="9668a-107">Podobně jako <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost> je jednoduché použití: odvozovat z <xref:System.Windows.Interop.HwndHost> a implementovat metody `BuildWindowCore` a `DestroyWindowCore` a pak vytvořit instanci vaší <xref:System.Windows.Interop.HwndHost> odvozené třídy a umístit ji do vaší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="9668a-107">Like <xref:System.Windows.Interop.HwndSource>, <xref:System.Windows.Interop.HwndHost> is straightforward to use: derive from <xref:System.Windows.Interop.HwndHost> and implement `BuildWindowCore` and `DestroyWindowCore` methods, then instantiate your <xref:System.Windows.Interop.HwndHost> derived class and place it inside your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span>

<span data-ttu-id="9668a-108">Pokud je vaše logika Win32 již zabalena jako ovládací prvek, je vaše implementace `BuildWindowCore` menší než volání `CreateWindow`.</span><span class="sxs-lookup"><span data-stu-id="9668a-108">If your Win32 logic is already packaged as a control, then your `BuildWindowCore` implementation is little more than a call to `CreateWindow`.</span></span> <span data-ttu-id="9668a-109">Například pro vytvoření ovládacího prvku seznamu Win32 v C++:</span><span class="sxs-lookup"><span data-stu-id="9668a-109">For example, to create a Win32 LISTBOX control in C++:</span></span>

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

<span data-ttu-id="9668a-110">Ale představte si, že kód Win32 není poměrně tak, jak je součástí sebe?</span><span class="sxs-lookup"><span data-stu-id="9668a-110">But suppose the Win32 code is not quite so self-contained?</span></span> <span data-ttu-id="9668a-111">Pokud ano, můžete vytvořit dialogové okno Win32 a vložit jeho obsah do větší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="9668a-111">If so, you can create a Win32 dialog box and embed its contents into a larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="9668a-112">Ukázka ukazuje tuto možnost v aplikaci Visual Studio C++a, i když je to možné, i v jiném jazyce nebo na příkazovém řádku.</span><span class="sxs-lookup"><span data-stu-id="9668a-112">The sample shows this in Visual Studio and C++, although it is also possible to do this in a different language or at the command line.</span></span>

<span data-ttu-id="9668a-113">Začněte jednoduchým dialogem, který se zkompiluje do projektu C++ knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="9668a-113">Start with a simple dialog, which is compiled into a C++ DLL project.</span></span>

<span data-ttu-id="9668a-114">Dále zaveďte dialog do větší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace:</span><span class="sxs-lookup"><span data-stu-id="9668a-114">Next, introduce the dialog into the larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application:</span></span>

- <span data-ttu-id="9668a-115">Zkompilovat knihovnu DLL jako spravovanou (`/clr`)</span><span class="sxs-lookup"><span data-stu-id="9668a-115">Compile the DLL as managed (`/clr`)</span></span>

- <span data-ttu-id="9668a-116">Přepněte dialog do ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="9668a-116">Turn the dialog into a control</span></span>

- <span data-ttu-id="9668a-117">Definovat odvozenou třídu <xref:System.Windows.Interop.HwndHost> s metodami `BuildWindowCore` a `DestroyWindowCore`</span><span class="sxs-lookup"><span data-stu-id="9668a-117">Define the derived class of <xref:System.Windows.Interop.HwndHost> with `BuildWindowCore` and `DestroyWindowCore` methods</span></span>

- <span data-ttu-id="9668a-118">Přepsat metodu `TranslateAccelerator` pro zpracování klíčů dialogových oken</span><span class="sxs-lookup"><span data-stu-id="9668a-118">Override `TranslateAccelerator` method to handle dialog keys</span></span>

- <span data-ttu-id="9668a-119">Přepsat metodu `TabInto` pro podporu tabulátorů</span><span class="sxs-lookup"><span data-stu-id="9668a-119">Override `TabInto` method to support tabbing</span></span>

- <span data-ttu-id="9668a-120">Přepsat metodu `OnMnemonic` pro podporu symbolických instrukcí</span><span class="sxs-lookup"><span data-stu-id="9668a-120">Override `OnMnemonic` method to support mnemonics</span></span>

- <span data-ttu-id="9668a-121">Vytvoření instance <xref:System.Windows.Interop.HwndHost> podtřídy a její umístění pod správným [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prvkem</span><span class="sxs-lookup"><span data-stu-id="9668a-121">Instantiate the <xref:System.Windows.Interop.HwndHost> subclass and put it under the right [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] element</span></span>

### <a name="turn-the-dialog-into-a-control"></a><span data-ttu-id="9668a-122">Přepněte dialog do ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="9668a-122">Turn the Dialog into a Control</span></span>

<span data-ttu-id="9668a-123">Můžete změnit dialogové okno na podřízeného HWND pomocí stylů WS_CHILD a DS_CONTROL.</span><span class="sxs-lookup"><span data-stu-id="9668a-123">You can turn a dialog box into a child HWND using the WS_CHILD and DS_CONTROL styles.</span></span> <span data-ttu-id="9668a-124">Přejít do souboru prostředků (. RC), kde je dialogové okno definováno, a najít začátek definice dialogového okna:</span><span class="sxs-lookup"><span data-stu-id="9668a-124">Go into the resource file (.rc) where the dialog is defined, and find the beginning of the definition of the dialog:</span></span>

```text
IDD_DIALOG1 DIALOGEX 0, 0, 303, 121
STYLE DS_SETFONT | DS_MODALFRAME | DS_FIXEDSYS | WS_POPUP | WS_CAPTION | WS_SYSMENU
```

<span data-ttu-id="9668a-125">Změňte druhý řádek na:</span><span class="sxs-lookup"><span data-stu-id="9668a-125">Change the second line to:</span></span>

```text
STYLE DS_SETFONT | WS_CHILD | WS_BORDER | DS_CONTROL
```

<span data-ttu-id="9668a-126">Tato akce zcela nebalí do samostatného ovládacího prvku. stále musíte volat `IsDialogMessage()`, aby Win32 mohl zpracovat určité zprávy, ale změna ovládacího prvku poskytuje jednoduchý způsob, jak umístit tyto ovládací prvky do jiného HWND.</span><span class="sxs-lookup"><span data-stu-id="9668a-126">This action does not fully package it into a self-contained control; you still need to call `IsDialogMessage()` so Win32 can process certain messages, but the control change does provide a straightforward way of putting those controls inside another HWND.</span></span>

## <a name="subclass-hwndhost"></a><span data-ttu-id="9668a-127">HwndHost podtříd</span><span class="sxs-lookup"><span data-stu-id="9668a-127">Subclass HwndHost</span></span>

<span data-ttu-id="9668a-128">Importujte následující obory názvů:</span><span class="sxs-lookup"><span data-stu-id="9668a-128">Import the following namespaces:</span></span>

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

<span data-ttu-id="9668a-129">Pak vytvořte odvozenou třídu <xref:System.Windows.Interop.HwndHost> a přepište metody `BuildWindowCore` a `DestroyWindowCore`:</span><span class="sxs-lookup"><span data-stu-id="9668a-129">Then create a derived class of <xref:System.Windows.Interop.HwndHost> and override the `BuildWindowCore` and `DestroyWindowCore` methods:</span></span>

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

<span data-ttu-id="9668a-130">Zde můžete použít `CreateDialog` k vytvoření dialogového okna, které je skutečně ovládacím prvkem.</span><span class="sxs-lookup"><span data-stu-id="9668a-130">Here you use the `CreateDialog` to create the dialog box that is really a control.</span></span> <span data-ttu-id="9668a-131">Vzhledem k tomu, že se jedná o jednu z prvních metod, které jsou volány uvnitř knihovny DLL, měli byste také provést několik standardních inicializací Win32 voláním funkce, kterou definujete později s názvem `InitializeGlobals()`:</span><span class="sxs-lookup"><span data-stu-id="9668a-131">Since this is one of the first methods called inside the DLL, you should also do some standard Win32 initialization by calling a function you will define later, called `InitializeGlobals()`:</span></span>

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

### <a name="override-translateaccelerator-method-to-handle-dialog-keys"></a><span data-ttu-id="9668a-132">Přepsat metodu TranslateAccelerator pro zpracování klíčů dialogových oken</span><span class="sxs-lookup"><span data-stu-id="9668a-132">Override TranslateAccelerator Method to Handle Dialog Keys</span></span>

<span data-ttu-id="9668a-133">Pokud jste teď spustili tuto ukázku, měli byste obdržet ovládací prvek dialog, který se zobrazí, ale bude ignorovat všechny funkce pro zpracování klávesnice, které vytvoří dialogové okno s funkčním seznamem.</span><span class="sxs-lookup"><span data-stu-id="9668a-133">If you ran this sample now, you would get a dialog control that displays, but it would ignore all of the keyboard processing that makes a dialog box a functional dialog box.</span></span> <span data-ttu-id="9668a-134">Nyní byste měli přepsat `TranslateAccelerator` implementaci (která pochází z `IKeyboardInputSink`rozhraní, které <xref:System.Windows.Interop.HwndHost> implementuje).</span><span class="sxs-lookup"><span data-stu-id="9668a-134">You should now override the `TranslateAccelerator` implementation (which comes from `IKeyboardInputSink`, an interface that <xref:System.Windows.Interop.HwndHost> implements).</span></span> <span data-ttu-id="9668a-135">Tato metoda se volá, když aplikace získá WM_KEYDOWN a WM_SYSKEYDOWN.</span><span class="sxs-lookup"><span data-stu-id="9668a-135">This method gets called when the application receives WM_KEYDOWN and WM_SYSKEYDOWN.</span></span>

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

<span data-ttu-id="9668a-136">Toto je spousta kódu v jednom kusu, takže by mohla používat podrobnější vysvětlení.</span><span class="sxs-lookup"><span data-stu-id="9668a-136">This is a lot of code in one piece, so it could use some more detailed explanations.</span></span> <span data-ttu-id="9668a-137">Nejprve kód pomocí C++ a C++ makra; je nutné si uvědomit, že již existuje makro s názvem `TranslateAccelerator`, které je definováno v Winuser. h:</span><span class="sxs-lookup"><span data-stu-id="9668a-137">First, the code using C++ and C++ macros; you need to be aware that there is already a macro named `TranslateAccelerator`, which is defined in winuser.h:</span></span>

```cpp
#define TranslateAccelerator  TranslateAcceleratorW
```

<span data-ttu-id="9668a-138">Proto se ujistěte, že definujete metodu `TranslateAccelerator`, a ne metodu `TranslateAcceleratorW`.</span><span class="sxs-lookup"><span data-stu-id="9668a-138">So make sure to define a `TranslateAccelerator` method and not a `TranslateAcceleratorW` method.</span></span>

<span data-ttu-id="9668a-139">Podobně je k dispozici nespravovaná Winuser. h MSG a spravovaná struktura `Microsoft::Win32::MSG`.</span><span class="sxs-lookup"><span data-stu-id="9668a-139">Similarly, there is both the unmanaged winuser.h MSG and the managed `Microsoft::Win32::MSG` struct.</span></span> <span data-ttu-id="9668a-140">Pomocí operátoru C++ `::` lze odstranit mezi dvěma.</span><span class="sxs-lookup"><span data-stu-id="9668a-140">You can disambiguate between the two using the C++ `::` operator.</span></span>

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

<span data-ttu-id="9668a-141">Zpět na `TranslateAccelerator`.</span><span class="sxs-lookup"><span data-stu-id="9668a-141">Back to `TranslateAccelerator`.</span></span> <span data-ttu-id="9668a-142">Základní princip je volání funkce Win32 `IsDialogMessage` k tomu, aby co nejvíce fungovalo, ale `IsDialogMessage` nemá přístup k cokoli mimo dialog.</span><span class="sxs-lookup"><span data-stu-id="9668a-142">The basic principle is to call the Win32 function `IsDialogMessage` to do as much work as possible, but `IsDialogMessage` does not have access to anything outside the dialog.</span></span> <span data-ttu-id="9668a-143">Jako karta uživatele kolem dialogu, když se na kartách spouští poslední ovládací prvek v našem dialogu, musíte nastavit fokus na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ou část voláním `IKeyboardInputSite::OnNoMoreStops`.</span><span class="sxs-lookup"><span data-stu-id="9668a-143">As a user tab around the dialog, when tabbing runs past the last control in our dialog, you need to set focus to the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] portion by calling `IKeyboardInputSite::OnNoMoreStops`.</span></span>

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

<span data-ttu-id="9668a-144">Nakonec zavolejte `IsDialogMessage`.</span><span class="sxs-lookup"><span data-stu-id="9668a-144">Finally, call `IsDialogMessage`.</span></span> <span data-ttu-id="9668a-145">Jedna z odpovědností `TranslateAccelerator` metody ale oznamuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], jestli jste vypustili klávesovou zkratku nebo ne.</span><span class="sxs-lookup"><span data-stu-id="9668a-145">But one of the responsibilities of a `TranslateAccelerator` method is telling [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] whether you handled the keystroke or not.</span></span> <span data-ttu-id="9668a-146">Pokud jste ho nezpracovali, vstupní událost může být tunelem a bublinou prostřednictvím zbytku aplikace.</span><span class="sxs-lookup"><span data-stu-id="9668a-146">If you did not handle it, the input event can tunnel and bubble through the rest of the application.</span></span> <span data-ttu-id="9668a-147">Tady vystavíte Quirk ovládání messange klávesnice a povahu vstupní architektury v prostředí Win32.</span><span class="sxs-lookup"><span data-stu-id="9668a-147">Here, you will expose a quirk of keyboard messange handling and the nature of the input architecture in Win32.</span></span> <span data-ttu-id="9668a-148">Bohužel se `IsDialogMessage` nevrátí žádným způsobem, ať už zpracovává konkrétní klávesovou zkratku.</span><span class="sxs-lookup"><span data-stu-id="9668a-148">Unfortunately, `IsDialogMessage` does not return in any way whether it handles a particular keystroke.</span></span> <span data-ttu-id="9668a-149">I horší, bude volat `DispatchMessage()` na úhozech, které by neměly být zpracovány!</span><span class="sxs-lookup"><span data-stu-id="9668a-149">Even worse, it will call `DispatchMessage()` on keystrokes it should not handle!</span></span>  <span data-ttu-id="9668a-150">Proto budete muset provádět zpětnou analýzu `IsDialogMessage`a volat ji jenom pro ty, které víte, že se budou zpracovávat:</span><span class="sxs-lookup"><span data-stu-id="9668a-150">So you will have to reverse-engineer `IsDialogMessage`, and only call it for the keys you know it will handle:</span></span>

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

### <a name="override-tabinto-method-to-support-tabbing"></a><span data-ttu-id="9668a-151">Přepsat metodu TabInto pro podporu tabulátorů</span><span class="sxs-lookup"><span data-stu-id="9668a-151">Override TabInto Method to Support Tabbing</span></span>

<span data-ttu-id="9668a-152">Teď, když jste nasadili `TranslateAccelerator`, uživatel může kolem dialogového okna a kartu z něj v rámci větší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace vyhledat kartu.</span><span class="sxs-lookup"><span data-stu-id="9668a-152">Now that you have implemented `TranslateAccelerator`, a user can tab around inside the dialog box and tab out of it into the greater [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="9668a-153">Uživatel ale nemůže kartu zpátky do dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="9668a-153">But a user cannot tab back into the dialog box.</span></span> <span data-ttu-id="9668a-154">Chcete-li tento problém vyřešit, přepíšete `TabInto`:</span><span class="sxs-lookup"><span data-stu-id="9668a-154">To solve that, you override `TabInto`:</span></span>

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

<span data-ttu-id="9668a-155">Parametr `TraversalRequest` určuje, zda je akce karty karta nebo klávesa SHIFT.</span><span class="sxs-lookup"><span data-stu-id="9668a-155">The `TraversalRequest` parameter tells you whether the tab action is a tab or shift tab.</span></span>

### <a name="override-onmnemonic-method-to-support-mnemonics"></a><span data-ttu-id="9668a-156">Přepsat metodu s podporou symbolických instrukcí</span><span class="sxs-lookup"><span data-stu-id="9668a-156">Override OnMnemonic Method to Support Mnemonics</span></span>

<span data-ttu-id="9668a-157">Zpracování klávesnice je skoro hotové, ale chybí jedna věc – symbolické symboly nefungují.</span><span class="sxs-lookup"><span data-stu-id="9668a-157">Keyboard handling is almost complete, but there is one thing missing – mnemonics do not work.</span></span> <span data-ttu-id="9668a-158">Pokud uživatel stiskne ALT-F, fokus fokusu neskočí do textového pole "first name:".</span><span class="sxs-lookup"><span data-stu-id="9668a-158">If a user presses alt-F, focus doe not jump to the "First name:" edit box.</span></span> <span data-ttu-id="9668a-159">Proto přepíšete metodu `OnMnemonic`:</span><span class="sxs-lookup"><span data-stu-id="9668a-159">So, you override the `OnMnemonic` method:</span></span>

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

<span data-ttu-id="9668a-160">Proč zde nevolat `IsDialogMessage`?</span><span class="sxs-lookup"><span data-stu-id="9668a-160">Why not call `IsDialogMessage` here?</span></span>  <span data-ttu-id="9668a-161">Máte stejný problém jako předtím – musíte být schopni informovat [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] kód, zda kód zpracoval klávesovou zkratku nebo ne, a `IsDialogMessage` jej nelze provést.</span><span class="sxs-lookup"><span data-stu-id="9668a-161">You have the same issue as before--you need to be able to inform [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] code whether your code handled the keystroke or not, and `IsDialogMessage` cannot do that.</span></span> <span data-ttu-id="9668a-162">Existuje také druhý problém, protože `IsDialogMessage` zamítnout zpracování instrukcí, pokud fokus HWND není uvnitř dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="9668a-162">There is also a second issue, because `IsDialogMessage` refuses to process the mnemonic if the focused HWND is not inside the dialog box.</span></span>

### <a name="instantiate-the-hwndhost-derived-class"></a><span data-ttu-id="9668a-163">Vytvoření instance odvozené třídy HwndHost</span><span class="sxs-lookup"><span data-stu-id="9668a-163">Instantiate the HwndHost Derived Class</span></span>

<span data-ttu-id="9668a-164">Nakonec, když je teď všechna podpora klíčů a karet, můžete <xref:System.Windows.Interop.HwndHost> umístit do větší [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikace.</span><span class="sxs-lookup"><span data-stu-id="9668a-164">Finally, now that all the key and tab support is in place, you can put your <xref:System.Windows.Interop.HwndHost> into the larger [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application.</span></span> <span data-ttu-id="9668a-165">Je-li hlavní aplikace napsána v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], nejjednodušší způsob, jak ji umístit do správného místa, je opustit prázdný <xref:System.Windows.Controls.Border> prvek, kam chcete umístit <xref:System.Windows.Interop.HwndHost>.</span><span class="sxs-lookup"><span data-stu-id="9668a-165">If the main application is written in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], the easiest way to put it in the right place is to leave an empty <xref:System.Windows.Controls.Border> element where you want to put the <xref:System.Windows.Interop.HwndHost>.</span></span> <span data-ttu-id="9668a-166">Zde vytvoříte <xref:System.Windows.Controls.Border> s názvem `insertHwndHostHere`:</span><span class="sxs-lookup"><span data-stu-id="9668a-166">Here you create a <xref:System.Windows.Controls.Border> named `insertHwndHostHere`:</span></span>

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

<span data-ttu-id="9668a-167">Pak vše, co zbývá, je najít dobré místo v sekvenci kódu pro vytvoření instance <xref:System.Windows.Interop.HwndHost> a jeho připojení k <xref:System.Windows.Controls.Border>.</span><span class="sxs-lookup"><span data-stu-id="9668a-167">Then all that remains is to find a good place in code sequence to instantiate the <xref:System.Windows.Interop.HwndHost> and connect it to the <xref:System.Windows.Controls.Border>.</span></span> <span data-ttu-id="9668a-168">V tomto příkladu se umístí do konstruktoru pro <xref:System.Windows.Window> odvozenou třídu:</span><span class="sxs-lookup"><span data-stu-id="9668a-168">In this example, you will put it inside the constructor for the <xref:System.Windows.Window> derived class:</span></span>

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

<span data-ttu-id="9668a-169">Díky tomu máte následující:</span><span class="sxs-lookup"><span data-stu-id="9668a-169">Which gives you:</span></span>

![Snímek obrazovky aplikace WPF spuštěné.](./media/hosting-win32-content-in-wpf/windows-presentation-foundation-application.png)

## <a name="see-also"></a><span data-ttu-id="9668a-171">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9668a-171">See also</span></span>

- [<span data-ttu-id="9668a-172">Vzájemná spolupráce grafického subsystému WPF a systému Win32</span><span class="sxs-lookup"><span data-stu-id="9668a-172">WPF and Win32 Interoperation</span></span>](wpf-and-win32-interoperation.md)
