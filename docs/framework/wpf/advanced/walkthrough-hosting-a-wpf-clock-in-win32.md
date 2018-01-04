---
title: "Návod: Hostování hodin WPF v systému Win32"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- interoperability [WPF], tutorials
- Win32 code [WPF], WPF interoperation
- interoperability [WPF], Win32
ms.assetid: 555e55a7-0851-4ec8-b1c6-0acba7e9b648
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: caf652f8a80da8e927a74ffc012d09b2389b1b09
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-hosting-a-wpf-clock-in-win32"></a><span data-ttu-id="5b247-102">Návod: Hostování hodin WPF v systému Win32</span><span class="sxs-lookup"><span data-stu-id="5b247-102">Walkthrough: Hosting a WPF Clock in Win32</span></span>
<span data-ttu-id="5b247-103">Uvést [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uvnitř [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikace, použijte <xref:System.Windows.Interop.HwndSource>, který poskytuje HWND, která obsahuje vaše [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsah.</span><span class="sxs-lookup"><span data-stu-id="5b247-103">To put [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inside [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] applications, use <xref:System.Windows.Interop.HwndSource>, which provides the HWND that contains your [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content.</span></span> <span data-ttu-id="5b247-104">Nejdřív vytvoříte <xref:System.Windows.Interop.HwndSource>, předá podobná CreateWindow parametry.</span><span class="sxs-lookup"><span data-stu-id="5b247-104">First you create the <xref:System.Windows.Interop.HwndSource>, giving it parameters similar to CreateWindow.</span></span>  <span data-ttu-id="5b247-105">Pak můžete zjistit <xref:System.Windows.Interop.HwndSource> o [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu chcete uvnitř ho.</span><span class="sxs-lookup"><span data-stu-id="5b247-105">Then you tell the <xref:System.Windows.Interop.HwndSource> about the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content you want inside it.</span></span>  <span data-ttu-id="5b247-106">Nakonec můžete získat HWND mimo <xref:System.Windows.Interop.HwndSource>.</span><span class="sxs-lookup"><span data-stu-id="5b247-106">Finally, you get the HWND out of the <xref:System.Windows.Interop.HwndSource>.</span></span> <span data-ttu-id="5b247-107">Tento návod ukazuje, jak vytvořit smíšený [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uvnitř [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikace, která reimplements operačního systému **vlastnosti data a času** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="5b247-107">This walkthrough illustrates how to create a mixed [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] inside [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] application that reimplements the operating system **Date and Time Properties** dialog.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="5b247-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5b247-108">Prerequisites</span></span>  
 <span data-ttu-id="5b247-109">V tématu [WPF a vzájemná spolupráce Win32](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md).</span><span class="sxs-lookup"><span data-stu-id="5b247-109">See [WPF and Win32 Interoperation](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md).</span></span>  
  
## <a name="how-to-use-this-tutorial"></a><span data-ttu-id="5b247-110">Jak používat v tomto kurzu</span><span class="sxs-lookup"><span data-stu-id="5b247-110">How to Use This Tutorial</span></span>  
 <span data-ttu-id="5b247-111">V tomto kurzu soustřeďuje na důležité kroky k vytvoření aplikace součinnosti.</span><span class="sxs-lookup"><span data-stu-id="5b247-111">This tutorial concentrates on the important steps of producing an interoperation application.</span></span> <span data-ttu-id="5b247-112">Tento kurz je zálohovaný díky ukázku, [ukázka vzájemná spolupráce hodin Win32](http://go.microsoft.com/fwlink/?LinkID=160051), ale tato ukázka je neodpovídajícím end produktu.</span><span class="sxs-lookup"><span data-stu-id="5b247-112">The tutorial is backed by a sample, [Win32 Clock Interoperation Sample](http://go.microsoft.com/fwlink/?LinkID=160051), but that sample is reflective of the end product.</span></span> <span data-ttu-id="5b247-113">V tomto kurzu dokumenty kroky, jako kdyby byly počínaje existující [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projektu vlastní, možná již existující projekt a byly přidání hostovaný [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] do vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="5b247-113">This tutorial documents the steps as if you were starting with an existing [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project of your own, perhaps a pre-existing project, and you were adding a hosted [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] to your application.</span></span> <span data-ttu-id="5b247-114">Můžete porovnat svůj produkt end s [ukázka vzájemná spolupráce hodin Win32](http://go.microsoft.com/fwlink/?LinkID=160051).</span><span class="sxs-lookup"><span data-stu-id="5b247-114">You can compare your end product with [Win32 Clock Interoperation Sample](http://go.microsoft.com/fwlink/?LinkID=160051).</span></span>  
  
## <a name="a-walkthrough-of-windows-presentation-framework-inside-win32-hwndsource"></a><span data-ttu-id="5b247-115">Návod Windows Presentation Framework uvnitř Win32 (HwndSource)</span><span class="sxs-lookup"><span data-stu-id="5b247-115">A Walkthrough of Windows Presentation Framework Inside Win32 (HwndSource)</span></span>  
 <span data-ttu-id="5b247-116">Následující obrázek ukazuje zamýšlené koncovým produkt v tomto kurzu:</span><span class="sxs-lookup"><span data-stu-id="5b247-116">The following graphic shows the intended end product of this tutorial:</span></span>  
  
 <span data-ttu-id="5b247-117">![Dialogové okno Vlastnosti data a času](../../../../docs/framework/wpf/advanced/media/interoparch06.PNG "InteropArch06")</span><span class="sxs-lookup"><span data-stu-id="5b247-117">![Date and Time Properties dialog box](../../../../docs/framework/wpf/advanced/media/interoparch06.PNG "InteropArch06")</span></span>  
  
 <span data-ttu-id="5b247-118">Tento dialog můžete znovu vytvořit tak, že vytvoříte C++ [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projektu v [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)]a použití editoru dialogových oken k vytvoření následující:</span><span class="sxs-lookup"><span data-stu-id="5b247-118">You can recreate this dialog by creating C++ [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project in [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], and using the dialog editor to create the following:</span></span>  
  
 <span data-ttu-id="5b247-119">![Dialogové okno Vlastnosti data a času](../../../../docs/framework/wpf/advanced/media/interoparch07.PNG "InteropArch07")</span><span class="sxs-lookup"><span data-stu-id="5b247-119">![Date and Time Properties dialog box](../../../../docs/framework/wpf/advanced/media/interoparch07.PNG "InteropArch07")</span></span>  
  
 <span data-ttu-id="5b247-120">(Není potřeba použít [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] používat <xref:System.Windows.Interop.HwndSource>, a není potřeba použít C++ k zápisu [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programy, ale to je celkem obvyklý způsob, jak to provést a různě dobře stupňový kurz vysvětlení).</span><span class="sxs-lookup"><span data-stu-id="5b247-120">(You do not need to use [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] to use <xref:System.Windows.Interop.HwndSource>, and you do not need to use C++ to write [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] programs, but this is a fairly typical way to do it, and lends itself well to a stepwise tutorial explanation).</span></span>  
  
 <span data-ttu-id="5b247-121">Je třeba provést pět konkrétní dílčích kroků, aby bylo možné umístit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hodiny do dialogu:</span><span class="sxs-lookup"><span data-stu-id="5b247-121">You need to accomplish five particular substeps in order to put a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock into the dialog:</span></span>  
  
1.  <span data-ttu-id="5b247-122">Povolit vaše [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projektu volat spravovaného kódu (**/CLR**) změnou nastavení projektu v [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5b247-122">Enable your [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project to call managed code (**/clr**) by changing project settings in [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)].</span></span>  
  
2.  <span data-ttu-id="5b247-123">Vytvoření [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> v samostatné knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="5b247-123">Create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> in a separate DLL.</span></span>  
  
3.  <span data-ttu-id="5b247-124">Uveďte, která [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> uvnitř <xref:System.Windows.Interop.HwndSource>.</span><span class="sxs-lookup"><span data-stu-id="5b247-124">Put that [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> inside an <xref:System.Windows.Interop.HwndSource>.</span></span>  
  
4.  <span data-ttu-id="5b247-125">Získat popisovačem HWND pro tento <xref:System.Windows.Controls.Page> pomocí <xref:System.Windows.Interop.HwndSource.Handle%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="5b247-125">Get an HWND for that <xref:System.Windows.Controls.Page> using the <xref:System.Windows.Interop.HwndSource.Handle%2A> property.</span></span>  
  
5.  <span data-ttu-id="5b247-126">Použití [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] rozhoduje, kam umístit HWND v rámci delší [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] aplikace</span><span class="sxs-lookup"><span data-stu-id="5b247-126">Use [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] to decide where to place the HWND within the larger [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] application</span></span>  
  
## <a name="clr"></a><span data-ttu-id="5b247-127">/ CLR</span><span class="sxs-lookup"><span data-stu-id="5b247-127">/clr</span></span>  
 <span data-ttu-id="5b247-128">Prvním krokem je chcete-li to nespravované [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projektu do jednoho, které můžete volat spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="5b247-128">The first step is to turn this unmanaged [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project into one that can call managed code.</span></span>  <span data-ttu-id="5b247-129">Použít / CLR – možnost kompilátoru, která bude propojit potřebné knihovny DLL, kterou chcete použít a upravit metodu Main pro použití s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="5b247-129">You use the /clr compiler option, which will link to the necessary DLLs you want to use, and adjust the Main method for use with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].</span></span>  
  
 <span data-ttu-id="5b247-130">Povolit používání spravovaného kódu v projektu C++: klikněte pravým tlačítkem na projekt win32clock a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="5b247-130">To enable the use of managed code inside the C++ project: Right-click on win32clock project and select **Properties**.</span></span>  <span data-ttu-id="5b247-131">Na **Obecné** stránka vlastností (výchozí), změnit modul Common Language Runtime podporu, aby `/clr`.</span><span class="sxs-lookup"><span data-stu-id="5b247-131">On the **General** property page (the default), change Common Language Runtime support to `/clr`.</span></span>  
  
 <span data-ttu-id="5b247-132">Dál přidejte odkazy na knihovny DLL, které jsou nezbytné pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: knihovně PresentationCore.dll, knihovně PresentationFramework.dll, System.dll, knihovně WindowsBase.dll, UIAutomationProvider.dll a UIAutomationTypes.dll.</span><span class="sxs-lookup"><span data-stu-id="5b247-132">Next, add references to DLLs necessary for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]: PresentationCore.dll, PresentationFramework.dll, System.dll, WindowsBase.dll, UIAutomationProvider.dll, and UIAutomationTypes.dll.</span></span> <span data-ttu-id="5b247-133">(Tyto pokyny předpokládají, že je nainstalovaný operační systém na jednotce C:.)</span><span class="sxs-lookup"><span data-stu-id="5b247-133">(Following instructions assume the operating system is installed on C: drive.)</span></span>  
  
1.  <span data-ttu-id="5b247-134">Klikněte pravým tlačítkem na projekt win32clock a vyberte **odkazy...** a v tomto dialogovém okně:</span><span class="sxs-lookup"><span data-stu-id="5b247-134">Right-click win32clock project and select **References...**, and inside that dialog:</span></span>  
  
2.  <span data-ttu-id="5b247-135">Klikněte pravým tlačítkem na projekt win32clock a vyberte **odkazy...** .</span><span class="sxs-lookup"><span data-stu-id="5b247-135">Right-click win32clock project and select **References...**.</span></span>  
  
3.  <span data-ttu-id="5b247-136">Klikněte na tlačítko **přidat nový odkaz**, klikněte na kartu Procházet, zadejte C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationCore.dll a klikněte na tlačítko OK.</span><span class="sxs-lookup"><span data-stu-id="5b247-136">Click **Add New Reference**, click Browse tab, enter C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationCore.dll, and click OK.</span></span>  
  
4.  <span data-ttu-id="5b247-137">Opakujte pro knihovně PresentationFramework.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationFramework.dll.</span><span class="sxs-lookup"><span data-stu-id="5b247-137">Repeat for PresentationFramework.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationFramework.dll.</span></span>  
  
5.  <span data-ttu-id="5b247-138">Opakujte pro knihovně WindowsBase.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\WindowsBase.dll.</span><span class="sxs-lookup"><span data-stu-id="5b247-138">Repeat for WindowsBase.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\WindowsBase.dll.</span></span>  
  
6.  <span data-ttu-id="5b247-139">Opakujte pro UIAutomationTypes.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationTypes.dll.</span><span class="sxs-lookup"><span data-stu-id="5b247-139">Repeat for UIAutomationTypes.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationTypes.dll.</span></span>  
  
7.  <span data-ttu-id="5b247-140">Opakujte pro UIAutomationProvider.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationProvider.dll.</span><span class="sxs-lookup"><span data-stu-id="5b247-140">Repeat for UIAutomationProvider.dll: C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\UIAutomationProvider.dll.</span></span>  
  
8.  <span data-ttu-id="5b247-141">Klikněte na tlačítko **přidat nový odkaz**vyberte System.dll a klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="5b247-141">Click **Add New Reference**, select System.dll, and click **OK**.</span></span>  
  
9. <span data-ttu-id="5b247-142">Klikněte na tlačítko **OK** ukončíte win32clock stránek vlastností pro přidání odkazů.</span><span class="sxs-lookup"><span data-stu-id="5b247-142">Click **OK** to exit the win32clock Property Pages for adding references.</span></span>  
  
 <span data-ttu-id="5b247-143">Nakonec přidejte `STAThreadAttribute` k `_tWinMain` metoda pro použití s [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:</span><span class="sxs-lookup"><span data-stu-id="5b247-143">Finally, add the `STAThreadAttribute` to the `_tWinMain` method for use with [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]:</span></span>  
  
```  
[System::STAThreadAttribute]  
int APIENTRY _tWinMain(HINSTANCE hInstance,  
                     HINSTANCE hPrevInstance,  
                     LPTSTR    lpCmdLine,  
                     int       nCmdShow)  
```  
  
 <span data-ttu-id="5b247-144">Tento atribut informuje [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] , když inicializuje [!INCLUDE[TLA#tla_com](../../../../includes/tlasharptla-com-md.md)], měla by používat model jeden model typu apartment (STA), který je potřebný pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]).</span><span class="sxs-lookup"><span data-stu-id="5b247-144">This attribute tells the [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] that when it initializes [!INCLUDE[TLA#tla_com](../../../../includes/tlasharptla-com-md.md)], it should use a single threaded apartment model (STA), which is necessary for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] (and [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]).</span></span>  
  
## <a name="create-a-windows-presentation-framework-page"></a><span data-ttu-id="5b247-145">Vytvoření stránky Windows Presentation Framework</span><span class="sxs-lookup"><span data-stu-id="5b247-145">Create a Windows Presentation Framework Page</span></span>  
 <span data-ttu-id="5b247-146">Dále vytvořte knihovnu DLL, kterou definuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page>.</span><span class="sxs-lookup"><span data-stu-id="5b247-146">Next, you create a DLL that defines a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page>.</span></span> <span data-ttu-id="5b247-147">Často je nejjednodušší vytvořit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> jako samostatná aplikace a zápis a ladění [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] část tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="5b247-147">It’s often easiest to create the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> as a standalone application, and write and debug the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] portion that way.</span></span>  <span data-ttu-id="5b247-148">Po dokončení tohoto projektu, mohou být změněny na knihovnu DLL kliknete pravým tlačítkem projekt kliknete na **vlastnosti**, přejdete na stránku aplikace a změna výstupní typ pro knihovny tříd systému Windows.</span><span class="sxs-lookup"><span data-stu-id="5b247-148">Once done, that project can be turned into a DLL by right-clicking the project, clicking on **Properties**, going to the Application, and changing Output type to Windows Class Library.</span></span>  
  
 <span data-ttu-id="5b247-149">[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Je pak možné kombinovat projektu knihovny dll s [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projektu (jedno řešení, které obsahuje dva projekty) – klikněte pravým tlačítkem na řešení, vyberte **Add\Existing projektu**.</span><span class="sxs-lookup"><span data-stu-id="5b247-149">The [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll project can then be combined with the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project (one solution that contains two projects) – right-click on the solution, select **Add\Existing Project**.</span></span>  
  
 <span data-ttu-id="5b247-150">Použít [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] knihovny dll z [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] projektu, budete muset přidat odkaz:</span><span class="sxs-lookup"><span data-stu-id="5b247-150">To use that [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dll from the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] project, you need to add a reference:</span></span>  
  
1.  <span data-ttu-id="5b247-151">Klikněte pravým tlačítkem na projekt win32clock a vyberte **odkazy...** .</span><span class="sxs-lookup"><span data-stu-id="5b247-151">Right-click win32clock project and select **References...**.</span></span>  
  
2.  <span data-ttu-id="5b247-152">Klikněte na tlačítko **přidat nový odkaz**.</span><span class="sxs-lookup"><span data-stu-id="5b247-152">Click **Add New Reference**.</span></span>  
  
3.  <span data-ttu-id="5b247-153">Klikněte **projekty** kartě.  Vyberte WPFClock, klikněte na tlačítko OK.</span><span class="sxs-lookup"><span data-stu-id="5b247-153">Click the **Projects** tab.  Select WPFClock, click OK.</span></span>  
  
4.  <span data-ttu-id="5b247-154">Klikněte na tlačítko **OK** ukončíte win32clock stránek vlastností pro přidání odkazů.</span><span class="sxs-lookup"><span data-stu-id="5b247-154">Click **OK** to exit the win32clock Property Pages for adding references.</span></span>  
  
## <a name="hwndsource"></a><span data-ttu-id="5b247-155">HwndSource</span><span class="sxs-lookup"><span data-stu-id="5b247-155">HwndSource</span></span>  
 <span data-ttu-id="5b247-156">V dalším kroku použijete <xref:System.Windows.Interop.HwndSource> aby [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Page> vypadat popisovačem HWND.</span><span class="sxs-lookup"><span data-stu-id="5b247-156">Next, you use <xref:System.Windows.Interop.HwndSource> to make the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<xref:System.Windows.Controls.Page> look like an HWND.</span></span>  <span data-ttu-id="5b247-157">Tento blok kódu přidáte do souboru C++:</span><span class="sxs-lookup"><span data-stu-id="5b247-157">You add this block of code to a C++ file:</span></span>  
  
```  
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
  
 <span data-ttu-id="5b247-158">Toto je dlouhý úsek kódu, který může použít vysvětlení.</span><span class="sxs-lookup"><span data-stu-id="5b247-158">This is a long piece of code that could use some explanation.</span></span>  <span data-ttu-id="5b247-159">První část je různé klauzule, takže není nutné k plnému určení všechna volání:</span><span class="sxs-lookup"><span data-stu-id="5b247-159">The first part is various clauses so that you do not need to fully qualify all the calls:</span></span>  
  
```  
namespace ManagedCode  
{  
    using namespace System;  
    using namespace System::Windows;  
    using namespace System::Windows::Interop;  
    using namespace System::Windows::Media;  
```  
  
 <span data-ttu-id="5b247-160">Potom můžete definovat funkci, která vytvoří [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu, PUT <xref:System.Windows.Interop.HwndSource> kolem a vrátí HWND:</span><span class="sxs-lookup"><span data-stu-id="5b247-160">Then you define a function that creates the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content, puts an <xref:System.Windows.Interop.HwndSource> around it, and returns the HWND:</span></span>  
  
```  
HWND GetHwnd(HWND parent, int x, int y, int width, int height) {  
```  
  
 <span data-ttu-id="5b247-161">Nejdřív vytvoříte <xref:System.Windows.Interop.HwndSource>, jejíž parametry jsou podobné CreateWindow:</span><span class="sxs-lookup"><span data-stu-id="5b247-161">First you create an <xref:System.Windows.Interop.HwndSource>, whose parameters are similar to CreateWindow:</span></span>  
  
```  
HwndSource^ source = gcnew HwndSource(  
    0, // class style  
    WS_VISIBLE | WS_CHILD, // style  
    0, // exstyle  
    x, y, width, height,  
    "hi", // NAME  
    IntPtr(parent) // parent window   
    );  
```  
  
 <span data-ttu-id="5b247-162">Potom můžete vytvořit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahu voláním jeho konstruktoru třídy:</span><span class="sxs-lookup"><span data-stu-id="5b247-162">Then you create the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] content class by calling its constructor:</span></span>  
  
```  
UIElement^ page = gcnew WPFClock::Clock();  
```  
  
 <span data-ttu-id="5b247-163">Potom připojíte stránku a <xref:System.Windows.Interop.HwndSource>:</span><span class="sxs-lookup"><span data-stu-id="5b247-163">You then connect the page to the <xref:System.Windows.Interop.HwndSource>:</span></span>  
  
```  
source->RootVisual = page;  
```  
  
 <span data-ttu-id="5b247-164">A na posledním řádku vrátí HWND pro <xref:System.Windows.Interop.HwndSource>:</span><span class="sxs-lookup"><span data-stu-id="5b247-164">And in the final line, return the HWND for the <xref:System.Windows.Interop.HwndSource>:</span></span>  
  
```  
return (HWND) source->Handle.ToPointer();  
```  
  
## <a name="positioning-the-hwnd"></a><span data-ttu-id="5b247-165">Umístění Hwnd</span><span class="sxs-lookup"><span data-stu-id="5b247-165">Positioning the Hwnd</span></span>  
 <span data-ttu-id="5b247-166">Teď, když máte popisovačem HWND, který obsahuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hodiny, které potřebujete k odeslání tohoto HWND uvnitř [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="5b247-166">Now that you have an HWND that contains the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock, you need to put that HWND inside the [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] dialog.</span></span>  <span data-ttu-id="5b247-167">Pokud budete vědět, právě umístění HWND, by stačí předat tento velikost a umístění `GetHwnd` funkce definovaného dříve.</span><span class="sxs-lookup"><span data-stu-id="5b247-167">If you knew just where to put the HWND, you would just pass that size and location to the `GetHwnd` function you defined earlier.</span></span>  <span data-ttu-id="5b247-168">Ale používá zdrojového souboru k definování dialogovém okně, takže jste si jisti, přesně, kde jsou umístěny žádné HWND.</span><span class="sxs-lookup"><span data-stu-id="5b247-168">But you used a resource file to define the dialog, so you are not exactly sure where any of the HWNDs are positioned.</span></span>  <span data-ttu-id="5b247-169">Můžete použít [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] editoru dialogového okna se umístí [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] statické řídit, kam chcete hodiny přejdete ("Insert hodiny zde") a použít jej k umístění [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hodiny.</span><span class="sxs-lookup"><span data-stu-id="5b247-169">You can use the [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] dialog editor to put a [!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)] STATIC control where you want the clock to go ("Insert clock here"), and use that to position the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock.</span></span>  
  
 <span data-ttu-id="5b247-170">Kde zpracováváte WM_INITDIALOG, použijete `GetDlgItem` načtení HWND pro zástupný symbol statické:</span><span class="sxs-lookup"><span data-stu-id="5b247-170">Where you handle WM_INITDIALOG, you use `GetDlgItem` to retrieve the HWND for the placeholder STATIC:</span></span>  
  
```  
HWND placeholder = GetDlgItem(hDlg, IDC_CLOCK);  
```  
  
 <span data-ttu-id="5b247-171">Můžete pak vypočítat velikost a umístění tento zástupný symbol STATIC, tak můžete umístit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] taktovací na tomto místě:</span><span class="sxs-lookup"><span data-stu-id="5b247-171">You then calculate the size and position of that placeholder STATIC, so you can put the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock in that place:</span></span>  
  
 <span data-ttu-id="5b247-172">Rect – obdélníku;</span><span class="sxs-lookup"><span data-stu-id="5b247-172">RECT rectangle;</span></span>  
  
```  
GetWindowRect(placeholder, &rectangle);  
int width = rectangle.right - rectangle.left;  
int height = rectangle.bottom - rectangle.top;  
POINT point;  
point.x = rectangle.left;  
point.y = rectangle.top;  
result = MapWindowPoints(NULL, hDlg, &point, 1);  
```  
  
 <span data-ttu-id="5b247-173">Potom můžete skrýt zástupný symbol statické:</span><span class="sxs-lookup"><span data-stu-id="5b247-173">Then you hide the placeholder STATIC:</span></span>  
  
```  
ShowWindow(placeholder, SW_HIDE);  
```  
  
 <span data-ttu-id="5b247-174">A vytvořte [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] taktovací HWND v tomto umístění:</span><span class="sxs-lookup"><span data-stu-id="5b247-174">And create the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock HWND in that location:</span></span>  
  
```  
HWND clock = ManagedCode::GetHwnd(hDlg, point.x, point.y, width, height);  
```  
  
 <span data-ttu-id="5b247-175">Chcete-li kurz zajímavé a k vytvoření reálné [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hodiny, budete muset vytvořit [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] taktovací ovládací prvek v tomto okamžiku.</span><span class="sxs-lookup"><span data-stu-id="5b247-175">To make the tutorial interesting, and to produce a real [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock, you will need to create a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock control at this point.</span></span> <span data-ttu-id="5b247-176">Můžete provést tak nejčastěji v značek, s několika obslužné rutiny událostí v kódu.</span><span class="sxs-lookup"><span data-stu-id="5b247-176">You can do so mostly in markup, with just a few event handlers in code-behind.</span></span> <span data-ttu-id="5b247-177">Vzhledem k tomu, že v tomto kurzu je o vzájemné spolupráci a nikoli o ovládací prvek návrhu, kód pro dokončení [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hodiny je k dispozici zde jako blok kódu bez diskrétní pokyny pro vytváření nebo co znamená každou část.</span><span class="sxs-lookup"><span data-stu-id="5b247-177">Since this tutorial is about interoperation and not about control design, complete code for the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] clock is provided here as a code block, without discrete instructions for building it up or what each part means.</span></span> <span data-ttu-id="5b247-178">Nebojte se, že experimentovat s tímto kódem změnit vzhled a chování nebo funkce ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="5b247-178">Feel free to experiment with this code to change the look and feel or functionality of the control.</span></span>  
  
 <span data-ttu-id="5b247-179">Zde je kód:</span><span class="sxs-lookup"><span data-stu-id="5b247-179">Here is the markup:</span></span>  
  
 [!code-xaml[Win32Clock#AllClockXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml#allclockxaml)]  
  
 <span data-ttu-id="5b247-180">A tady je doprovodné kódu:</span><span class="sxs-lookup"><span data-stu-id="5b247-180">And here is the accompanying code-behind:</span></span>  
  
 [!code-csharp[Win32Clock#AllClockCS](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Win32Clock/CS/Clock.xaml.cs#allclockcs)]  
  
 <span data-ttu-id="5b247-181">Konečný výsledek bude vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="5b247-181">The final result looks like:</span></span>  
  
 <span data-ttu-id="5b247-182">![Dialogové okno Vlastnosti data a času](../../../../docs/framework/wpf/advanced/media/interoparch08.PNG "InteropArch08")</span><span class="sxs-lookup"><span data-stu-id="5b247-182">![Date and Time Properties dialog box](../../../../docs/framework/wpf/advanced/media/interoparch08.PNG "InteropArch08")</span></span>  
  
 <span data-ttu-id="5b247-183">K porovnání vaší konečný výsledek na kód, který vytvořil tento snímek obrazovky, najdete v části [ukázka vzájemná spolupráce hodin Win32](http://go.microsoft.com/fwlink/?LinkID=160051).</span><span class="sxs-lookup"><span data-stu-id="5b247-183">To compare your end result to the code that produced this screenshot, see [Win32 Clock Interoperation Sample](http://go.microsoft.com/fwlink/?LinkID=160051).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b247-184">Viz také</span><span class="sxs-lookup"><span data-stu-id="5b247-184">See Also</span></span>  
 <xref:System.Windows.Interop.HwndSource>  
 [<span data-ttu-id="5b247-185">Vzájemná spolupráce grafického subsystému WPF a systému Win32</span><span class="sxs-lookup"><span data-stu-id="5b247-185">WPF and Win32 Interoperation</span></span>](../../../../docs/framework/wpf/advanced/wpf-and-win32-interoperation.md)  
 [<span data-ttu-id="5b247-186">Ukázka součinnosti hodin Win32</span><span class="sxs-lookup"><span data-stu-id="5b247-186">Win32 Clock Interoperation Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160051)
