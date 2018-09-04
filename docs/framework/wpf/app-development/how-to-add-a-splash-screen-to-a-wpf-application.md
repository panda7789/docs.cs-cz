---
title: 'Postupy: Přidání úvodní obrazovky do aplikace WPF'
ms.date: 08/18/2018
helpviewer_keywords:
- WPF [WPF], splash screen
- startup window [WPF]
- SplashScreen class [WPF]
- splash screen [WPF]
ms.assetid: d70a25c4-5fb9-4c27-b01d-b1b8ef39b3fd
ms.openlocfilehash: 46efa041736870c5c0f08baa321ef0dc53cacc0d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43502751"
---
# <a name="how-to-add-a-splash-screen-to-a-wpf-application"></a><span data-ttu-id="7ae26-102">Postupy: Přidání úvodní obrazovky do aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="7ae26-102">How to: Add a Splash Screen to a WPF Application</span></span>

<span data-ttu-id="7ae26-103">Toto téma ukazuje, jak přidat časové období při spuštění nebo *úvodní obrazovka*, k aplikaci Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="7ae26-103">This topic shows how to add a startup window, or *splash screen*, to a Windows Presentation Foundation (WPF) application.</span></span>

## <a name="to-add-an-existing-image-as-a-splash-screen"></a><span data-ttu-id="7ae26-104">Chcete-li přidat existující image jako úvodní obrazovka</span><span class="sxs-lookup"><span data-stu-id="7ae26-104">To add an existing image as a splash screen</span></span>

1.  <span data-ttu-id="7ae26-105">Vytvořit nebo vyhledat bitovou kopii, kterou chcete použít pro úvodní obrazovku.</span><span class="sxs-lookup"><span data-stu-id="7ae26-105">Create or find an image that you want to use for the splash screen.</span></span> <span data-ttu-id="7ae26-106">Můžete použít libovolný formát obrázku, který je podporovaný službou Windows Imaging Component (WIC).</span><span class="sxs-lookup"><span data-stu-id="7ae26-106">You can use any image format that is supported by the Windows Imaging Component (WIC).</span></span> <span data-ttu-id="7ae26-107">Například můžete pomocí formátu BMP, GIF, JPEG, PNG nebo ve formátu TIFF.</span><span class="sxs-lookup"><span data-stu-id="7ae26-107">For example, you can use the BMP, GIF, JPEG, PNG, or TIFF format.</span></span>

2.  <span data-ttu-id="7ae26-108">Přidání souboru obrázku do projektu aplikace WPF.</span><span class="sxs-lookup"><span data-stu-id="7ae26-108">Add the image file to the WPF Application project.</span></span>

3.  <span data-ttu-id="7ae26-109">V **Průzkumníka řešení**, vyberte bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="7ae26-109">In **Solution Explorer**, select the image.</span></span>

4.  <span data-ttu-id="7ae26-110">V okně Vlastnosti klikněte na šipku rozevíracího seznamu pro **akce sestavení** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7ae26-110">In the Properties window, click the drop-down arrow for the **Build Action** property.</span></span>

5.  <span data-ttu-id="7ae26-111">Vyberte **SplashScreen** z rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="7ae26-111">Select **SplashScreen** from the drop-down list.</span></span>

6.  <span data-ttu-id="7ae26-112">Stisknutím klávesy **F5** sestavíte a spustíte aplikaci.</span><span class="sxs-lookup"><span data-stu-id="7ae26-112">Press **F5** to build and run the application.</span></span>

     <span data-ttu-id="7ae26-113">Na úvodní obrazovce je zobrazena ve středu obrazovky a pak sníží (zesvětlí) až se zobrazí hlavního okna aplikace.</span><span class="sxs-lookup"><span data-stu-id="7ae26-113">The splash screen image appears in the center of the screen, and then fades when the main application window appears.</span></span>

## <a name="to-exclude-the-splash-screen-from-build"></a><span data-ttu-id="7ae26-114">Na úvodní obrazovce vyloučit ze sestavení</span><span class="sxs-lookup"><span data-stu-id="7ae26-114">To exclude the splash screen from build</span></span>

1.  <span data-ttu-id="7ae26-115">V **Průzkumníka řešení**, vyberte obrázek úvodní obrazovky.</span><span class="sxs-lookup"><span data-stu-id="7ae26-115">In **Solution Explorer**, select the splash screen image.</span></span>

2.  <span data-ttu-id="7ae26-116">V **vlastnosti** okno, nastaveno **akce sestavení** k **žádný**.</span><span class="sxs-lookup"><span data-stu-id="7ae26-116">In the **Properties** window, set the **Build Action** to **None**.</span></span>

## <a name="to-remove-the-splash-screen-from-an-application"></a><span data-ttu-id="7ae26-117">Chcete-li odebrat úvodní obrazovky z aplikace</span><span class="sxs-lookup"><span data-stu-id="7ae26-117">To remove the splash screen from an application</span></span>

<span data-ttu-id="7ae26-118">V **Průzkumníka řešení**, odstraňte na úvodní obrazovce.</span><span class="sxs-lookup"><span data-stu-id="7ae26-118">In **Solution Explorer**, delete the splash screen image.</span></span>

## <a name="see-also"></a><span data-ttu-id="7ae26-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="7ae26-119">See Also</span></span>

- <xref:System.Windows.SplashScreen>
- <span data-ttu-id="7ae26-120">[Postupy: Přidání existující položky do projektu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7ae26-120">[How to: Add Existing Items to a Project](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))</span></span>
