---
title: 'Návod: hostování hodin WPF v systému Win32'
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 555e55a7-0851-4ec8-b1c6-0acba7e9b648
ms.openlocfilehash: 0aecde96d182e12ab72b1a6cba129ab1d8a28391
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77123776"
---
# <a name="walkthrough-host-a-wpf-clock-in-win32"></a><span data-ttu-id="64b90-102">Návod: hostování hodin WPF v systému Win32</span><span class="sxs-lookup"><span data-stu-id="64b90-102">Walkthrough: Host a WPF Clock in Win32</span></span>

<span data-ttu-id="64b90-103">Chcete-li umístit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do aplikací Win32, použijte <xref:System.Windows.Interop.HwndSource>, která poskytuje HWND, který obsahuje váš [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah.</span><span class="sxs-lookup"><span data-stu-id="64b90-103">To put [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inside Win32 applications, use <xref:System.Windows.Interop.HwndSource>, which provides the HWND that contains your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content.</span></span> <span data-ttu-id="64b90-104">Nejdřív vytvoříte <xref:System.Windows.Interop.HwndSource>, takže parametry pro něj budou podobné funkci CreateWindow.</span><span class="sxs-lookup"><span data-stu-id="64b90-104">First you create the <xref:System.Windows.Interop.HwndSource>, giving it parameters similar to CreateWindow.</span></span> <span data-ttu-id="64b90-105">Pak <xref:System.Windows.Interop.HwndSource> informace o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]m obsahu, který v něm potřebujete.</span><span class="sxs-lookup"><span data-stu-id="64b90-105">Then you tell the <xref:System.Windows.Interop.HwndSource> about the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content you want inside it.</span></span> <span data-ttu-id="64b90-106">Nakonec obdržíte HWND z <xref:System.Windows.Interop.HwndSource>.</span><span class="sxs-lookup"><span data-stu-id="64b90-106">Finally, you get the HWND out of the <xref:System.Windows.Interop.HwndSource>.</span></span> <span data-ttu-id="64b90-107">Tento návod ukazuje, jak vytvořit smíšený [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] v rámci aplikace Win32, která znovu implementuje dialog **vlastností data a času** operačního systému.</span><span class="sxs-lookup"><span data-stu-id="64b90-107">This walkthrough illustrates how to create a mixed [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inside Win32 application that reimplements the operating system **Date and Time Properties** dialog.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="64b90-108">Předpoklady</span><span class="sxs-lookup"><span data-stu-id="64b90-108">Prerequisites</span></span>

<span data-ttu-id="64b90-109">Viz [spolupráce WPF a Win32](wpf-and-win32-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="64b90-109">See [WPF and Win32 Interoperation](wpf-and-win32-interoperation.md).</span></span>

## <a name="how-to-use-this-tutorial"></a><span data-ttu-id="64b90-110">Jak používat tento kurz</span><span class="sxs-lookup"><span data-stu-id="64b90-110">How to Use This Tutorial</span></span>

<span data-ttu-id="64b90-111">Tento kurz se zaměřuje na důležité kroky k vytvoření meziprovozního aplikace.</span><span class="sxs-lookup"><span data-stu-id="64b90-111">This tutorial concentrates on the important steps of producing an interoperation application.</span></span> <span data-ttu-id="64b90-112">Tento kurz je zálohovaný ukázkou, [Ukázka mezioperace v prostředí Win32](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/Win32Clock), ale tato ukázka se odráží u koncového produktu.</span><span class="sxs-lookup"><span data-stu-id="64b90-112">The tutorial is backed by a sample, [Win32 Clock Interoperation Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/Win32Clock), but that sample is reflective of the end product.</span></span> <span data-ttu-id="64b90-113">V tomto kurzu se dokončí postup, jak jste se rozhodli, že jste začali s existujícím projektem Win32 vlastní, možná již existující projekt a přidáváte do aplikace hostovaný [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="64b90-113">This tutorial documents the steps as if you were starting with an existing Win32 project of your own, perhaps a pre-existing project, and you were adding a hosted [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] to your application.</span></span> <span data-ttu-id="64b90-114">Můžete porovnat svůj koncový produkt s [ukázkou meziprovozu pro hodiny Win32](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/Win32Clock).</span><span class="sxs-lookup"><span data-stu-id="64b90-114">You can compare your end product with [Win32 Clock Interoperation Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/Win32Clock).</span></span>

## <a name="a-walkthrough-of-windows-presentation-framework-inside-win32-hwndsource"></a><span data-ttu-id="64b90-115">Návod pro Windows Presentation Framework uvnitř Win32 (HwndSource)</span><span class="sxs-lookup"><span data-stu-id="64b90-115">A Walkthrough of Windows Presentation Framework Inside Win32 (HwndSource)</span></span>

<span data-ttu-id="64b90-116">Následující obrázek znázorňuje zamýšlený koncový produkt tohoto kurzu:</span><span class="sxs-lookup"><span data-stu-id="64b90-116">The following graphic shows the intended end product of this tutorial:</span></span>

![Snímek obrazovky, který zobrazuje dialogové okno Vlastnosti data a času.](./media/walkthrough-hosting-a-wpf-clock-in-win32/date-time-properties-dialog.png)

<span data-ttu-id="64b90-118">Tento dialog můžete znovu vytvořit tak, že vytvoříte C++ projekt Win32 v aplikaci Visual Studio a pomocí editoru dialogového okna vytvoříte následující:</span><span class="sxs-lookup"><span data-stu-id="64b90-118">You can recreate this dialog by creating a C++ Win32 project in Visual Studio, and using the dialog editor to create the following:</span></span>

![Dialogové okno znovu vytvořit vlastnosti data a času](./media/walkthrough-hosting-a-wpf-clock-in-win32/recreated-date-time-properties-dialog.png)

<span data-ttu-id="64b90-120">(Nemusíte používat Visual Studio k použití <xref:System.Windows.Interop.HwndSource>a nemusíte používat C++ k psaní programů Win32, ale jedná se o poměrně typický způsob, jak to provést, a stejně tak se dobře hodí k vysvětlení kurzu stupňovaný).</span><span class="sxs-lookup"><span data-stu-id="64b90-120">(You do not need to use Visual Studio to use <xref:System.Windows.Interop.HwndSource>, and you do not need to use C++ to write Win32 programs, but this is a fairly typical way to do it, and lends itself well to a stepwise tutorial explanation).</span></span>

<span data-ttu-id="64b90-121">Chcete-li vložit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hodiny do dialogového okna, je nutné provést pět jednotlivých podkroků:</span><span class="sxs-lookup"><span data-stu-id="64b90-121">You need to accomplish five particular substeps in order to put a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock into the dialog:</span></span>

1. <span data-ttu-id="64b90-122">Umožněte Vašemu projektu Win32 volat spravovaný kód ( **/CLR**) změnou nastavení projektu v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="64b90-122">Enable your Win32 project to call managed code (**/clr**) by changing project settings in Visual Studio.</span></span>

2. <span data-ttu-id="64b90-123">Vytvoří [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> v samostatné knihovně DLL.</span><span class="sxs-lookup"><span data-stu-id="64b90-123">Create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> in a separate DLL.</span></span>

3. <span data-ttu-id="64b90-124">Vložení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> dovnitř <xref:System.Windows.Interop.HwndSource>.</span><span class="sxs-lookup"><span data-stu-id="64b90-124">Put that [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> inside an <xref:System.Windows.Interop.HwndSource>.</span></span>

4. <span data-ttu-id="64b90-125">Získat HWND pro tento <xref:System.Windows.Controls.Page> pomocí vlastnosti <xref:System.Windows.Interop.HwndSource.Handle%2A>.</span><span class="sxs-lookup"><span data-stu-id="64b90-125">Get an HWND for that <xref:System.Windows.Controls.Page> using the <xref:System.Windows.Interop.HwndSource.Handle%2A> property.</span></span>

5. <span data-ttu-id="64b90-126">Použití Win32 k rozhodnutí, kam umístit HWND v rámci větší aplikace Win32</span><span class="sxs-lookup"><span data-stu-id="64b90-126">Use Win32 to decide where to place the HWND within the larger Win32 application</span></span>

## <a name="clr"></a><span data-ttu-id="64b90-127">možností</span><span class="sxs-lookup"><span data-stu-id="64b90-127">/clr</span></span>

<span data-ttu-id="64b90-128">Prvním krokem je zapnutí tohoto nespravovaného projektu Win32 na jeden, který může volat spravovaný kód.</span><span class="sxs-lookup"><span data-stu-id="64b90-128">The first step is to turn this unmanaged Win32 project into one that can call managed code.</span></span> <span data-ttu-id="64b90-129">Použijete možnost kompilátoru/CLR, která se připojí k potřebným knihovnám DLL, které chcete použít, a upravte metodu Main pro použití s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="64b90-129">You use the /clr compiler option, which will link to the necessary DLLs you want to use, and adjust the Main method for use with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span>

<span data-ttu-id="64b90-130">Povolení použití spravovaného kódu v rámci C++ projektu: klikněte pravým tlačítkem na projekt win32clock a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="64b90-130">To enable the use of managed code inside the C++ project: Right-click on win32clock project and select **Properties**.</span></span> <span data-ttu-id="64b90-131">Na stránce **Obecné** vlastnosti (výchozí) změňte podporu modulu Common Language Runtime na `/clr`.</span><span class="sxs-lookup"><span data-stu-id="64b90-131">On the **General** property page (the default), change Common Language Runtime support to `/clr`.</span></span>

<span data-ttu-id="64b90-132">Dále přidejte odkazy na knihovny DLL nutné pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: PresentationCore. dll, PresentationFramework. dll, System. dll, WindowsBase. dll, UIAutomationProvider. dll a UIAutomationTypes. dll.</span><span class="sxs-lookup"><span data-stu-id="64b90-132">Next, add references to DLLs necessary for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: PresentationCore.dll, PresentationFramework.dll, System.dll, WindowsBase.dll, UIAutomationProvider.dll, and UIAutomationTypes.dll.</span></span> <span data-ttu-id="64b90-133">(V následujících pokynech se předpokládá, že je operační systém nainstalovaný na jednotce C:.)</span><span class="sxs-lookup"><span data-stu-id="64b90-133">(Following instructions assume the operating system is installed on C: drive.)</span></span>

1. <span data-ttu-id="64b90-134">Klikněte pravým tlačítkem na projekt win32clock a vyberte **odkazy...** a v tomto dialogovém okně:</span><span class="sxs-lookup"><span data-stu-id="64b90-134">Right-click win32clock project and select **References...**, and inside that dialog:</span></span>

2. <span data-ttu-id="64b90-135">Klikněte pravým tlačítkem na projekt win32clock a vyberte **odkazy...** .</span><span class="sxs-lookup"><span data-stu-id="64b90-135">Right-click win32clock project and select **References...**.</span></span>

3. <span data-ttu-id="64b90-136">Klikněte na tlačítko **Přidat nový odkaz**, klikněte na tlačítko Procházet, zadejte C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationCore.dll a klikněte na tlačítko OK.</span><span class="sxs-lookup"><span data-stu-id="64b90-136">Click **Add New Reference**, click Browse tab, enter C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationCore.dll, and click OK.</span></span>

4. <span data-ttu-id="64b90-137">Opakovat pro PresentationFramework. dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationFramework.dll.</span><span class="sxs-lookup"><span data-stu-id="64b90-137">Repeat for PresentationFramework.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationFramework.dll.</span></span>

5. <span data-ttu-id="64b90-138">Opakovat pro WindowsBase. dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\WindowsBase.dll.</span><span class="sxs-lookup"><span data-stu-id="64b90-138">Repeat for WindowsBase.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\WindowsBase.dll.</span></span>

6. <span data-ttu-id="64b90-139">Opakovat pro UIAutomationTypes. dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationTypes.dll.</span><span class="sxs-lookup"><span data-stu-id="64b90-139">Repeat for UIAutomationTypes.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationTypes.dll.</span></span>

7. <span data-ttu-id="64b90-140">Opakovat pro UIAutomationProvider. dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationProvider.dll.</span><span class="sxs-lookup"><span data-stu-id="64b90-140">Repeat for UIAutomationProvider.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationProvider.dll.</span></span>

8. <span data-ttu-id="64b90-141">Klikněte na tlačítko **Přidat nový odkaz**, vyberte položku System. dll a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="64b90-141">Click **Add New Reference**, select System.dll, and click **OK**.</span></span>

9. <span data-ttu-id="64b90-142">Kliknutím na tlačítko **OK** zavřete stránky vlastností win32clock pro přidání odkazů.</span><span class="sxs-lookup"><span data-stu-id="64b90-142">Click **OK** to exit the win32clock Property Pages for adding references.</span></span>

 <span data-ttu-id="64b90-143">Nakonec přidejte `STAThreadAttribute` do metody `_tWinMain` pro použití s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="64b90-143">Finally, add the `STAThreadAttribute` to the `_tWinMain` method for use with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:</span></span>

```cpp
[System::STAThreadAttribute]
int APIENTRY _tWinMain(HINSTANCE hInstance,
                     HINSTANCE hPrevInstance,
                     LPTSTR    lpCmdLine,
                     int       nCmdShow)
```

<span data-ttu-id="64b90-144">Tento atribut oznamuje modulu CLR (Common Language Runtime), že při inicializaci modelu COM (Component Object Model) by měl používat jeden model Apartment (STA), který je nezbytný pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (a model Windows Forms).</span><span class="sxs-lookup"><span data-stu-id="64b90-144">This attribute tells the common language runtime (CLR) that when it initializes Component Object Model (COM), it should use a single threaded apartment model (STA), which is necessary for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (and Windows Forms).</span></span>

## <a name="create-a-windows-presentation-framework-page"></a><span data-ttu-id="64b90-145">Vytvoření stránky Windows Presentation Framework</span><span class="sxs-lookup"><span data-stu-id="64b90-145">Create a Windows Presentation Framework Page</span></span>

<span data-ttu-id="64b90-146">V dalším kroku vytvoříte knihovnu DLL, která definuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page>.</span><span class="sxs-lookup"><span data-stu-id="64b90-146">Next, you create a DLL that defines a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page>.</span></span> <span data-ttu-id="64b90-147">Často je nejjednodušší vytvořit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> jako samostatnou aplikaci a napsat a ladit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ou část.</span><span class="sxs-lookup"><span data-stu-id="64b90-147">It’s often easiest to create the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> as a standalone application, and write and debug the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] portion that way.</span></span> <span data-ttu-id="64b90-148">Po dokončení lze tento projekt přepínat na knihovnu DLL tak, že kliknete pravým tlačítkem myši na projekt, kliknete na **vlastnosti**, přejdete do aplikace a změníte typ výstupu na knihovnu tříd systému Windows.</span><span class="sxs-lookup"><span data-stu-id="64b90-148">Once done, that project can be turned into a DLL by right-clicking the project, clicking on **Properties**, going to the Application, and changing Output type to Windows Class Library.</span></span>

<span data-ttu-id="64b90-149">Projekt [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] DLL lze následně kombinovat s projektem Win32 (jedno řešení, které obsahuje dva projekty) – klikněte pravým tlačítkem na řešení, vyberte **projekt Add\Existing**.</span><span class="sxs-lookup"><span data-stu-id="64b90-149">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll project can then be combined with the Win32 project (one solution that contains two projects) – right-click on the solution, select **Add\Existing Project**.</span></span>

<span data-ttu-id="64b90-150">Chcete-li použít tuto [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll z projektu Win32, je nutné přidat odkaz:</span><span class="sxs-lookup"><span data-stu-id="64b90-150">To use that [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll from the Win32 project, you need to add a reference:</span></span>

1. <span data-ttu-id="64b90-151">Klikněte pravým tlačítkem na projekt win32clock a vyberte **odkazy...** .</span><span class="sxs-lookup"><span data-stu-id="64b90-151">Right-click win32clock project and select **References...**.</span></span>

2. <span data-ttu-id="64b90-152">Klikněte na tlačítko **Přidat nový odkaz**.</span><span class="sxs-lookup"><span data-stu-id="64b90-152">Click **Add New Reference**.</span></span>

3. <span data-ttu-id="64b90-153">Klikněte na kartu **projekty** . Vyberte WPFClock, klikněte na OK.</span><span class="sxs-lookup"><span data-stu-id="64b90-153">Click the **Projects** tab. Select WPFClock, click OK.</span></span>

4. <span data-ttu-id="64b90-154">Kliknutím na tlačítko **OK** zavřete stránky vlastností win32clock pro přidání odkazů.</span><span class="sxs-lookup"><span data-stu-id="64b90-154">Click **OK** to exit the win32clock Property Pages for adding references.</span></span>

## <a name="hwndsource"></a><span data-ttu-id="64b90-155">HwndSource</span><span class="sxs-lookup"><span data-stu-id="64b90-155">HwndSource</span></span>

<span data-ttu-id="64b90-156">V dalším kroku použijete <xref:System.Windows.Interop.HwndSource>, aby [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> vypadal jako HWND.</span><span class="sxs-lookup"><span data-stu-id="64b90-156">Next, you use <xref:System.Windows.Interop.HwndSource> to make the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> look like an HWND.</span></span> <span data-ttu-id="64b90-157">Tento blok kódu přidáte do C++ souboru:</span><span class="sxs-lookup"><span data-stu-id="64b90-157">You add this block of code to a C++ file:</span></span>

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

 <span data-ttu-id="64b90-158">Toto je dlouhý kód, který může používat určité vysvětlení.</span><span class="sxs-lookup"><span data-stu-id="64b90-158">This is a long piece of code that could use some explanation.</span></span> <span data-ttu-id="64b90-159">První část je různé klauzule, takže nemusíte plně kvalifikovat všechna volání:</span><span class="sxs-lookup"><span data-stu-id="64b90-159">The first part is various clauses so that you do not need to fully qualify all the calls:</span></span>

```cpp
namespace ManagedCode
{
    using namespace System;
    using namespace System::Windows;
    using namespace System::Windows::Interop;
    using namespace System::Windows::Media;
```

 <span data-ttu-id="64b90-160">Pak definujte funkci, která vytvoří obsah [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], vloží <xref:System.Windows.Interop.HwndSource> kolem něj a vrátí HWND:</span><span class="sxs-lookup"><span data-stu-id="64b90-160">Then you define a function that creates the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content, puts an <xref:System.Windows.Interop.HwndSource> around it, and returns the HWND:</span></span>

```cpp
HWND GetHwnd(HWND parent, int x, int y, int width, int height) {
```

<span data-ttu-id="64b90-161">Nejprve vytvoříte <xref:System.Windows.Interop.HwndSource>, jejichž parametry jsou podobné funkci CreateWindow:</span><span class="sxs-lookup"><span data-stu-id="64b90-161">First you create an <xref:System.Windows.Interop.HwndSource>, whose parameters are similar to CreateWindow:</span></span>

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

<span data-ttu-id="64b90-162">Pak vytvoříte třídu obsahu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] voláním jejího konstruktoru:</span><span class="sxs-lookup"><span data-stu-id="64b90-162">Then you create the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content class by calling its constructor:</span></span>

```cpp
UIElement^ page = gcnew WPFClock::Clock();
```

<span data-ttu-id="64b90-163">Pak stránku připojíte k <xref:System.Windows.Interop.HwndSource>:</span><span class="sxs-lookup"><span data-stu-id="64b90-163">You then connect the page to the <xref:System.Windows.Interop.HwndSource>:</span></span>

```cpp
source->RootVisual = page;
```

 <span data-ttu-id="64b90-164">A v posledním řádku vrátí HWND pro <xref:System.Windows.Interop.HwndSource>:</span><span class="sxs-lookup"><span data-stu-id="64b90-164">And in the final line, return the HWND for the <xref:System.Windows.Interop.HwndSource>:</span></span>

```cpp
return (HWND) source->Handle.ToPointer();
```

## <a name="positioning-the-hwnd"></a><span data-ttu-id="64b90-165">Umístění HWND</span><span class="sxs-lookup"><span data-stu-id="64b90-165">Positioning the Hwnd</span></span>

<span data-ttu-id="64b90-166">Teď, když máte HWND, který obsahuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hodin, je nutné vložit HWND do dialogového okna Win32.</span><span class="sxs-lookup"><span data-stu-id="64b90-166">Now that you have an HWND that contains the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock, you need to put that HWND inside the Win32 dialog.</span></span> <span data-ttu-id="64b90-167">Pokud jste věděli, kam chcete přidat HWND, stačí pouze předat tuto velikost a umístění do funkce `GetHwnd`, kterou jste definovali dříve.</span><span class="sxs-lookup"><span data-stu-id="64b90-167">If you knew just where to put the HWND, you would just pass that size and location to the `GetHwnd` function you defined earlier.</span></span> <span data-ttu-id="64b90-168">Ale použili jste soubor prostředků k definování dialogu, takže nejste přesně jisti, kde jsou umístěny všechny HWND.</span><span class="sxs-lookup"><span data-stu-id="64b90-168">But you used a resource file to define the dialog, so you are not exactly sure where any of the HWNDs are positioned.</span></span> <span data-ttu-id="64b90-169">Editor dialogového okna sady Visual Studio můžete použít k vložení STATICKÉho ovládacího prvku systému Win32, kde chcete, aby se hodiny posunuly ("vložit hodiny sem"), a použít k umístění [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ch hodin.</span><span class="sxs-lookup"><span data-stu-id="64b90-169">You can use the Visual Studio dialog editor to put a Win32 STATIC control where you want the clock to go ("Insert clock here"), and use that to position the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock.</span></span>

<span data-ttu-id="64b90-170">Kde WM_INITDIALOG zpracováváte, použijete `GetDlgItem` k načtení HWND pro statický zástupný symbol:</span><span class="sxs-lookup"><span data-stu-id="64b90-170">Where you handle WM_INITDIALOG, you use `GetDlgItem` to retrieve the HWND for the placeholder STATIC:</span></span>

```cpp
HWND placeholder = GetDlgItem(hDlg, IDC_CLOCK);
```

<span data-ttu-id="64b90-171">Pak můžete vypočítat velikost a umístění zástupného symbolu, aby bylo možné umístit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hodiny na toto místo:</span><span class="sxs-lookup"><span data-stu-id="64b90-171">You then calculate the size and position of that placeholder STATIC, so you can put the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock in that place:</span></span>

<span data-ttu-id="64b90-172">Obdélník RECT;</span><span class="sxs-lookup"><span data-stu-id="64b90-172">RECT rectangle;</span></span>

```cpp
GetWindowRect(placeholder, &rectangle);
int width = rectangle.right - rectangle.left;
int height = rectangle.bottom - rectangle.top;
POINT point;
point.x = rectangle.left;
point.y = rectangle.top;
result = MapWindowPoints(NULL, hDlg, &point, 1);
```

<span data-ttu-id="64b90-173">Pak skryjete zástupný symbol STATIC:</span><span class="sxs-lookup"><span data-stu-id="64b90-173">Then you hide the placeholder STATIC:</span></span>

```cpp
ShowWindow(placeholder, SW_HIDE);
```

<span data-ttu-id="64b90-174">A vytvořte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hodinového HWND v tomto umístění:</span><span class="sxs-lookup"><span data-stu-id="64b90-174">And create the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock HWND in that location:</span></span>

```cpp
HWND clock = ManagedCode::GetHwnd(hDlg, point.x, point.y, width, height);
```

<span data-ttu-id="64b90-175">Aby se kurz zajímavý a vytvořil reálné [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]é hodiny, budete v tomto okamžiku muset vytvořit ovládací prvek [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hodin.</span><span class="sxs-lookup"><span data-stu-id="64b90-175">To make the tutorial interesting, and to produce a real [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock, you will need to create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock control at this point.</span></span> <span data-ttu-id="64b90-176">To lze provést hlavně v označení, a to s několika obslužnými rutinami událostí v kódu na pozadí.</span><span class="sxs-lookup"><span data-stu-id="64b90-176">You can do so mostly in markup, with just a few event handlers in code-behind.</span></span> <span data-ttu-id="64b90-177">Vzhledem k tomu, že tento kurz se týká vzájemného provozu a nikoli o návrhu ovládacích prvků, je zde k dispozici kompletní kód pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hodiny, a to bez diskrétních instrukcí pro sestavování a toho, co jednotlivé části znamenají.</span><span class="sxs-lookup"><span data-stu-id="64b90-177">Since this tutorial is about interoperation and not about control design, complete code for the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock is provided here as a code block, without discrete instructions for building it up or what each part means.</span></span> <span data-ttu-id="64b90-178">Nebojte se s tímto kódem pro změnu vzhledu a chování ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="64b90-178">Feel free to experiment with this code to change the look and feel or functionality of the control.</span></span>

<span data-ttu-id="64b90-179">Zde je značka:</span><span class="sxs-lookup"><span data-stu-id="64b90-179">Here is the markup:</span></span>

[!code-xaml[Win32Clock#AllClockXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml#allclockxaml)]

<span data-ttu-id="64b90-180">A zde je doprovodný kód na pozadí:</span><span class="sxs-lookup"><span data-stu-id="64b90-180">And here is the accompanying code-behind:</span></span>

[!code-csharp[Win32Clock#AllClockCS](~/samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml.cs#allclockcs)]

<span data-ttu-id="64b90-181">Konečný výsledek vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="64b90-181">The final result looks like:</span></span>

![Dialogové okno Vlastnosti data a času finálního výsledku](./media/walkthrough-hosting-a-wpf-clock-in-win32/final-result-date-time-properties-dialog.png)

<span data-ttu-id="64b90-183">K porovnání konečného výsledku s kódem, který vytvořil tento snímek obrazovky, si přečtěte část [Ukázka mezioperačního zpracování hodin Win32](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/Win32Clock).</span><span class="sxs-lookup"><span data-stu-id="64b90-183">To compare your end result to the code that produced this screenshot, see [Win32 Clock Interoperation Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/Win32Clock).</span></span>

## <a name="see-also"></a><span data-ttu-id="64b90-184">Viz také</span><span class="sxs-lookup"><span data-stu-id="64b90-184">See also</span></span>

- <xref:System.Windows.Interop.HwndSource>
- [<span data-ttu-id="64b90-185">Vzájemná spolupráce grafického subsystému WPF a systému Win32</span><span class="sxs-lookup"><span data-stu-id="64b90-185">WPF and Win32 Interoperation</span></span>](wpf-and-win32-interoperation.md)
- [<span data-ttu-id="64b90-186">Ukázka mezi operacemi hodin Win32</span><span class="sxs-lookup"><span data-stu-id="64b90-186">Win32 Clock Interoperation Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Migration%20and%20Interoperability/Win32Clock)
