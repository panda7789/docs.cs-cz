---
title: Postup přidání úvodní obrazovky
description: Zjistěte, jak přidat spouštěcí okno nebo úvodní obrazovku do aplikace Windows Presentation Foundation (WPF).
ms.date: 08/18/2018
helpviewer_keywords:
- WPF [WPF], splash screen
- startup window [WPF]
- SplashScreen class [WPF]
- splash screen [WPF]
ms.assetid: d70a25c4-5fb9-4c27-b01d-b1b8ef39b3fd
ms.openlocfilehash: 0d0cf2e2a550320650c3b4a0c257071a0403c32b
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85617957"
---
# <a name="how-to-add-a-splash-screen-to-a-wpf-application"></a><span data-ttu-id="5e4f0-103">Postupy: Přidání úvodní obrazovky do aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="5e4f0-103">How to: Add a Splash Screen to a WPF Application</span></span>

<span data-ttu-id="5e4f0-104">Toto téma ukazuje, jak přidat spouštěcí okno nebo *úvodní obrazovku*do aplikace Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="5e4f0-104">This topic shows how to add a startup window, or *splash screen*, to a Windows Presentation Foundation (WPF) application.</span></span>

## <a name="to-add-an-existing-image-as-a-splash-screen"></a><span data-ttu-id="5e4f0-105">Přidání existujícího obrázku jako úvodní obrazovky</span><span class="sxs-lookup"><span data-stu-id="5e4f0-105">To add an existing image as a splash screen</span></span>

1. <span data-ttu-id="5e4f0-106">Vytvořte nebo najděte obrázek, který chcete použít pro úvodní obrazovku.</span><span class="sxs-lookup"><span data-stu-id="5e4f0-106">Create or find an image that you want to use for the splash screen.</span></span> <span data-ttu-id="5e4f0-107">Můžete použít libovolný formát obrázku, který podporuje součást WIC (Windows Imaging Component).</span><span class="sxs-lookup"><span data-stu-id="5e4f0-107">You can use any image format that is supported by the Windows Imaging Component (WIC).</span></span> <span data-ttu-id="5e4f0-108">Můžete například použít formát BMP, GIF, JPEG, PNG nebo TIFF.</span><span class="sxs-lookup"><span data-stu-id="5e4f0-108">For example, you can use the BMP, GIF, JPEG, PNG, or TIFF format.</span></span>

2. <span data-ttu-id="5e4f0-109">Přidejte soubor obrázku do projektu aplikace WPF.</span><span class="sxs-lookup"><span data-stu-id="5e4f0-109">Add the image file to the WPF Application project.</span></span>

3. <span data-ttu-id="5e4f0-110">V **Průzkumník řešení**vyberte bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="5e4f0-110">In **Solution Explorer**, select the image.</span></span>

4. <span data-ttu-id="5e4f0-111">V okno Vlastnosti klikněte na šipku rozevíracího seznamu vlastnosti **Akce sestavení** .</span><span class="sxs-lookup"><span data-stu-id="5e4f0-111">In the Properties window, click the drop-down arrow for the **Build Action** property.</span></span>

5. <span data-ttu-id="5e4f0-112">V rozevíracím seznamu vyberte **třídy SplashScreen** .</span><span class="sxs-lookup"><span data-stu-id="5e4f0-112">Select **SplashScreen** from the drop-down list.</span></span>

6. <span data-ttu-id="5e4f0-113">Stisknutím klávesy **F5** Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="5e4f0-113">Press **F5** to build and run the application.</span></span>

     <span data-ttu-id="5e4f0-114">Obrázek úvodní obrazovky se zobrazí uprostřed obrazovky a po zobrazení okna hlavní aplikace zmizí.</span><span class="sxs-lookup"><span data-stu-id="5e4f0-114">The splash screen image appears in the center of the screen, and then fades when the main application window appears.</span></span>

## <a name="to-exclude-the-splash-screen-from-build"></a><span data-ttu-id="5e4f0-115">Vyloučení úvodní obrazovky ze sestavení</span><span class="sxs-lookup"><span data-stu-id="5e4f0-115">To exclude the splash screen from build</span></span>

1. <span data-ttu-id="5e4f0-116">V **Průzkumník řešení**vyberte obrázek úvodní obrazovky.</span><span class="sxs-lookup"><span data-stu-id="5e4f0-116">In **Solution Explorer**, select the splash screen image.</span></span>

2. <span data-ttu-id="5e4f0-117">V okně **vlastnosti** nastavte **akci sestavení** na **žádná**.</span><span class="sxs-lookup"><span data-stu-id="5e4f0-117">In the **Properties** window, set the **Build Action** to **None**.</span></span>

## <a name="to-remove-the-splash-screen-from-an-application"></a><span data-ttu-id="5e4f0-118">Odebrání úvodní obrazovky z aplikace</span><span class="sxs-lookup"><span data-stu-id="5e4f0-118">To remove the splash screen from an application</span></span>

<span data-ttu-id="5e4f0-119">V **Průzkumník řešení**odstraňte obrázek úvodní obrazovky.</span><span class="sxs-lookup"><span data-stu-id="5e4f0-119">In **Solution Explorer**, delete the splash screen image.</span></span>

## <a name="see-also"></a><span data-ttu-id="5e4f0-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5e4f0-120">See also</span></span>

- <xref:System.Windows.SplashScreen>
- <span data-ttu-id="5e4f0-121">[Postupy: Přidání existujících položek do projektu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="5e4f0-121">[How to: Add Existing Items to a Project](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))</span></span>
