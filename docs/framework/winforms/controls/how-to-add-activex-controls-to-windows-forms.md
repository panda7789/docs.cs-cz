---
title: 'Postupy: Přidávání ovládacích prvků ActiveX do Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- forms [Windows Forms], adding ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 54a61e5b-555e-4887-b41e-6244fed271eb
ms.openlocfilehash: 780411949c543a2178de5e7c531bd2202703f27a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59166046"
---
# <a name="how-to-add-activex-controls-to-windows-forms"></a><span data-ttu-id="0aa42-102">Postupy: Přidávání ovládacích prvků ActiveX do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0aa42-102">How to: Add ActiveX Controls to Windows Forms</span></span>
<span data-ttu-id="0aa42-103">Zatímco Návrhář formulářů Windows je optimalizována pro hostitelské ovládací prvky Windows Forms, lze také umístit ovládací prvky ActiveX v modelu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="0aa42-103">While the Windows Forms Designer is optimized to host Windows Forms controls, you can also put ActiveX controls on Windows Forms.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="0aa42-104">Existují omezení výkonu pro Windows Forms, kdy ovládací prvky ActiveX jsou k nim přidány.</span><span class="sxs-lookup"><span data-stu-id="0aa42-104">There are performance limitations for Windows Forms when ActiveX controls are added to them.</span></span>  
  
 <span data-ttu-id="0aa42-105">Předtím, než přidáte do svého formuláře ovládací prvky ActiveX, musíte je přidat do panelu nástrojů.</span><span class="sxs-lookup"><span data-stu-id="0aa42-105">Before you add ActiveX controls to your form, you must add them to the Toolbox.</span></span> <span data-ttu-id="0aa42-106">Další informace najdete v tématu [komponenty modelu COM, dialogové okno přizpůsobení panelu nástrojů](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/cby6tzh5(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="0aa42-106">For more information, see [COM Components, Customize Toolbox Dialog Box](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/cby6tzh5(v=vs.100)).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0aa42-107">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="0aa42-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="0aa42-108">Chcete-li změnit nastavení, klikněte na tlačítko **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="0aa42-108">To change your settings, click **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="0aa42-109">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="0aa42-109">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-add-an-activex-control-to-your-windows-form"></a><span data-ttu-id="0aa42-110">Chcete-li přidat ovládací prvek ActiveX do formuláře Windows</span><span class="sxs-lookup"><span data-stu-id="0aa42-110">To add an ActiveX control to your Windows Form</span></span>  
  
-   <span data-ttu-id="0aa42-111">Poklepejte na ovládací prvek na panelu nástrojů.</span><span class="sxs-lookup"><span data-stu-id="0aa42-111">Double-click the control on the Toolbox.</span></span>  
  
     <span data-ttu-id="0aa42-112">Visual Studio přidá všechny odkazy na ovládací prvek ve vašem projektu.</span><span class="sxs-lookup"><span data-stu-id="0aa42-112">Visual Studio adds all references to the control in your project.</span></span> <span data-ttu-id="0aa42-113">Další informace o co je potřeba vzít v úvahu při použití ovládacích prvků ActiveX do formulářů Windows, naleznete v tématu [aspekty hostování ovládacího prvku ActiveX ve formuláři Windows](considerations-when-hosting-an-activex-control-on-a-windows-form.md).</span><span class="sxs-lookup"><span data-stu-id="0aa42-113">For more information about things to keep in mind when using ActiveX controls on Windows Forms, see [Considerations When Hosting an ActiveX Control on a Windows Form](considerations-when-hosting-an-activex-control-on-a-windows-form.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="0aa42-114">Importér ovládacích prvků ActiveX Windows Forms (AxImp.exe) vytvoří argumenty událostí jiného typu než se čekalo na Import knihoven DLL ActiveX.</span><span class="sxs-lookup"><span data-stu-id="0aa42-114">The Windows Forms ActiveX Control Importer (AxImp.exe) creates event arguments of a different type than expected upon importation of ActiveX dynamic link libraries.</span></span> <span data-ttu-id="0aa42-115">Argumenty vytvořené AxImp.exe se nějak takto: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, když `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` se očekává.</span><span class="sxs-lookup"><span data-stu-id="0aa42-115">The arguments created by AxImp.exe are similar to the following: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, when `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` is expected.</span></span> <span data-ttu-id="0aa42-116">Mějte na paměti, že tato nesrovnalost nebrání kód funguje normálně.</span><span class="sxs-lookup"><span data-stu-id="0aa42-116">Be aware that this irregularity does not prevent code from functioning normally.</span></span> <span data-ttu-id="0aa42-117">Podrobnosti najdete v tématu [Importér ovládacích prvků Windows Forms ActiveX (Aximp.exe)](../../tools/aximp-exe-windows-forms-activex-control-importer.md).</span><span class="sxs-lookup"><span data-stu-id="0aa42-117">For details, see [Windows Forms ActiveX Control Importer (Aximp.exe)](../../tools/aximp-exe-windows-forms-activex-control-importer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0aa42-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0aa42-118">See also</span></span>

- [<span data-ttu-id="0aa42-119">Ovládací prvky Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0aa42-119">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="0aa42-120">Porovnání ovládacích prvků a programovatelných objektů v různých jazycích a knihovnách</span><span class="sxs-lookup"><span data-stu-id="0aa42-120">Controls and Programmable Objects Compared in Various Languages and Libraries</span></span>](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/0061wezk(v=vs.100))
- [<span data-ttu-id="0aa42-121">Postupy: Přidávání ovládacích prvků do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0aa42-121">How to: Add Controls to Windows Forms</span></span>](how-to-add-controls-to-windows-forms.md)
- [<span data-ttu-id="0aa42-122">Uspořádávání ovládacích prvků ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0aa42-122">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="0aa42-123">Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky</span><span class="sxs-lookup"><span data-stu-id="0aa42-123">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="0aa42-124">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0aa42-124">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="0aa42-125">Ovládací prvky Windows Forms podle funkce</span><span class="sxs-lookup"><span data-stu-id="0aa42-125">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
