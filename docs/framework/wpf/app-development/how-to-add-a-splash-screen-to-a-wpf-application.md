---
title: Postup přidání úvodní obrazovky
ms.date: 08/18/2018
helpviewer_keywords:
- WPF [WPF], splash screen
- startup window [WPF]
- SplashScreen class [WPF]
- splash screen [WPF]
ms.assetid: d70a25c4-5fb9-4c27-b01d-b1b8ef39b3fd
ms.openlocfilehash: 39f53e21c40f036c65894b4f275cd5fb414999be
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740448"
---
# <a name="how-to-add-a-splash-screen-to-a-wpf-application"></a><span data-ttu-id="8ff51-102">Postupy: Přidání úvodní obrazovky do aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="8ff51-102">How to: Add a Splash Screen to a WPF Application</span></span>

<span data-ttu-id="8ff51-103">Toto téma ukazuje, jak přidat spouštěcí okno nebo *úvodní obrazovku*do aplikace Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="8ff51-103">This topic shows how to add a startup window, or *splash screen*, to a Windows Presentation Foundation (WPF) application.</span></span>

## <a name="to-add-an-existing-image-as-a-splash-screen"></a><span data-ttu-id="8ff51-104">Přidání existujícího obrázku jako úvodní obrazovky</span><span class="sxs-lookup"><span data-stu-id="8ff51-104">To add an existing image as a splash screen</span></span>

1. <span data-ttu-id="8ff51-105">Vytvořte nebo najděte obrázek, který chcete použít pro úvodní obrazovku.</span><span class="sxs-lookup"><span data-stu-id="8ff51-105">Create or find an image that you want to use for the splash screen.</span></span> <span data-ttu-id="8ff51-106">Můžete použít libovolný formát obrázku, který podporuje součást WIC (Windows Imaging Component).</span><span class="sxs-lookup"><span data-stu-id="8ff51-106">You can use any image format that is supported by the Windows Imaging Component (WIC).</span></span> <span data-ttu-id="8ff51-107">Můžete například použít formát BMP, GIF, JPEG, PNG nebo TIFF.</span><span class="sxs-lookup"><span data-stu-id="8ff51-107">For example, you can use the BMP, GIF, JPEG, PNG, or TIFF format.</span></span>

2. <span data-ttu-id="8ff51-108">Přidejte soubor obrázku do projektu aplikace WPF.</span><span class="sxs-lookup"><span data-stu-id="8ff51-108">Add the image file to the WPF Application project.</span></span>

3. <span data-ttu-id="8ff51-109">V **Průzkumník řešení**vyberte bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="8ff51-109">In **Solution Explorer**, select the image.</span></span>

4. <span data-ttu-id="8ff51-110">V okno Vlastnosti klikněte na šipku rozevíracího seznamu vlastnosti **Akce sestavení** .</span><span class="sxs-lookup"><span data-stu-id="8ff51-110">In the Properties window, click the drop-down arrow for the **Build Action** property.</span></span>

5. <span data-ttu-id="8ff51-111">V rozevíracím seznamu vyberte **třídy SplashScreen** .</span><span class="sxs-lookup"><span data-stu-id="8ff51-111">Select **SplashScreen** from the drop-down list.</span></span>

6. <span data-ttu-id="8ff51-112">Stisknutím klávesy **F5** Sestavte a spusťte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8ff51-112">Press **F5** to build and run the application.</span></span>

     <span data-ttu-id="8ff51-113">Obrázek úvodní obrazovky se zobrazí uprostřed obrazovky a po zobrazení okna hlavní aplikace zmizí.</span><span class="sxs-lookup"><span data-stu-id="8ff51-113">The splash screen image appears in the center of the screen, and then fades when the main application window appears.</span></span>

## <a name="to-exclude-the-splash-screen-from-build"></a><span data-ttu-id="8ff51-114">Vyloučení úvodní obrazovky ze sestavení</span><span class="sxs-lookup"><span data-stu-id="8ff51-114">To exclude the splash screen from build</span></span>

1. <span data-ttu-id="8ff51-115">V **Průzkumník řešení**vyberte obrázek úvodní obrazovky.</span><span class="sxs-lookup"><span data-stu-id="8ff51-115">In **Solution Explorer**, select the splash screen image.</span></span>

2. <span data-ttu-id="8ff51-116">V okně **vlastnosti** nastavte **akci sestavení** na **žádná**.</span><span class="sxs-lookup"><span data-stu-id="8ff51-116">In the **Properties** window, set the **Build Action** to **None**.</span></span>

## <a name="to-remove-the-splash-screen-from-an-application"></a><span data-ttu-id="8ff51-117">Odebrání úvodní obrazovky z aplikace</span><span class="sxs-lookup"><span data-stu-id="8ff51-117">To remove the splash screen from an application</span></span>

<span data-ttu-id="8ff51-118">V **Průzkumník řešení**odstraňte obrázek úvodní obrazovky.</span><span class="sxs-lookup"><span data-stu-id="8ff51-118">In **Solution Explorer**, delete the splash screen image.</span></span>

## <a name="see-also"></a><span data-ttu-id="8ff51-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8ff51-119">See also</span></span>

- <xref:System.Windows.SplashScreen>
- <span data-ttu-id="8ff51-120">[Postupy: Přidání existujících položek do projektu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8ff51-120">[How to: Add Existing Items to a Project](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))</span></span>
