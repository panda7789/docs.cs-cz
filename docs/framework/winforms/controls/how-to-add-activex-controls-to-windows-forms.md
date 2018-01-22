---
title: "Postupy: Přidávání ovládacích prvků ActiveX do formulářů Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms controls, ActiveX controls
- forms [Windows Forms], adding ActiveX controls
- ActiveX controls [Windows Forms], adding
ms.assetid: 54a61e5b-555e-4887-b41e-6244fed271eb
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 940dd21fc48c23ce623280aab2c487db5810057c
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-add-activex-controls-to-windows-forms"></a><span data-ttu-id="27e5f-102">Postupy: Přidávání ovládacích prvků ActiveX do formulářů Windows</span><span class="sxs-lookup"><span data-stu-id="27e5f-102">How to: Add ActiveX Controls to Windows Forms</span></span>
<span data-ttu-id="27e5f-103">Zatímco Návrhář formulářů Windows je optimalizovaná tak, aby hostitelské ovládací prvky Windows Forms, můžete taky v rozhraní Windows Forms – ovládací prvky ActiveX.</span><span class="sxs-lookup"><span data-stu-id="27e5f-103">While the Windows Forms Designer is optimized to host Windows Forms controls, you can also put ActiveX controls on Windows Forms.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="27e5f-104">Existují omezení výkonu pro Windows Forms, když jsou do nich přidány ovládací prvky ActiveX.</span><span class="sxs-lookup"><span data-stu-id="27e5f-104">There are performance limitations for Windows Forms when ActiveX controls are added to them.</span></span>  
  
 <span data-ttu-id="27e5f-105">Než přidáte do svého formuláře ovládací prvky ActiveX, musíte je přidat do sady nástrojů.</span><span class="sxs-lookup"><span data-stu-id="27e5f-105">Before you add ActiveX controls to your form, you must add them to the Toolbox.</span></span> <span data-ttu-id="27e5f-106">Další informace najdete v tématu [komponenty modelu COM, dialogové okno přizpůsobení sady nástrojů](http://msdn.microsoft.com/library/171333f3-f207-4e02-bbdc-17862556212c).</span><span class="sxs-lookup"><span data-stu-id="27e5f-106">For more information, see [COM Components, Customize Toolbox Dialog Box](http://msdn.microsoft.com/library/171333f3-f207-4e02-bbdc-17862556212c).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="27e5f-107">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="27e5f-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="27e5f-108">Chcete-li změnit nastavení, klikněte na tlačítko **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="27e5f-108">To change your settings, click **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="27e5f-109">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="27e5f-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-an-activex-control-to-your-windows-form"></a><span data-ttu-id="27e5f-110">Přidání ovládacího prvku ActiveX do svého formuláře Windows</span><span class="sxs-lookup"><span data-stu-id="27e5f-110">To add an ActiveX control to your Windows Form</span></span>  
  
-   <span data-ttu-id="27e5f-111">Dvakrát klikněte na ovládací prvek v panelu nástrojů.</span><span class="sxs-lookup"><span data-stu-id="27e5f-111">Double-click the control on the Toolbox.</span></span>  
  
     [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]<span data-ttu-id="27e5f-112">Přidá všechny odkazy na ovládací prvek v projektu.</span><span class="sxs-lookup"><span data-stu-id="27e5f-112"> adds all references to the control in your project.</span></span> <span data-ttu-id="27e5f-113">Další informace o aspektech, které při použití na Windows Forms – ovládací prvky ActiveX mějte na paměti najdete v tématu [aspekty hostování ovládacího prvku ActiveX ve formuláři Windows](../../../../docs/framework/winforms/controls/considerations-when-hosting-an-activex-control-on-a-windows-form.md).</span><span class="sxs-lookup"><span data-stu-id="27e5f-113">For more information about things to keep in mind when using ActiveX controls on Windows Forms, see [Considerations When Hosting an ActiveX Control on a Windows Form](../../../../docs/framework/winforms/controls/considerations-when-hosting-an-activex-control-on-a-windows-form.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="27e5f-114">Systému Windows Forms ActiveX – Importér ovládacích prvků (AxImp.exe) vytvoří argumenty událostí jiného typu než se čekalo na Import ActiveX dynamické knihovny.</span><span class="sxs-lookup"><span data-stu-id="27e5f-114">The Windows Forms ActiveX Control Importer (AxImp.exe) creates event arguments of a different type than expected upon importation of ActiveX dynamic link libraries.</span></span> <span data-ttu-id="27e5f-115">Argumenty vytvořené AxImp.exe jsou podobné následujícím: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, když `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` se očekává.</span><span class="sxs-lookup"><span data-stu-id="27e5f-115">The arguments created by AxImp.exe are similar to the following: `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEvent e)`, when `Invoke(object sender, DWebBrowserEvents2_ProgressChangeEventArgs e)` is expected.</span></span> <span data-ttu-id="27e5f-116">Upozorňujeme, že tato nesrovnalost nezabrání kód fungovat normálně.</span><span class="sxs-lookup"><span data-stu-id="27e5f-116">Be aware that this irregularity does not prevent code from functioning normally.</span></span> <span data-ttu-id="27e5f-117">Podrobnosti najdete v tématu [Windows Forms ActiveX – Importér ovládacích prvků (Aximp.exe)](../../../../docs/framework/tools/aximp-exe-windows-forms-activex-control-importer.md).</span><span class="sxs-lookup"><span data-stu-id="27e5f-117">For details, see [Windows Forms ActiveX Control Importer (Aximp.exe)](../../../../docs/framework/tools/aximp-exe-windows-forms-activex-control-importer.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27e5f-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="27e5f-118">See Also</span></span>  
 [<span data-ttu-id="27e5f-119">Windows Forms – ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="27e5f-119">Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/index.md)  
 [<span data-ttu-id="27e5f-120">Ovládací prvky a programovatelný objekty porovnání v různých jazycích a knihovny</span><span class="sxs-lookup"><span data-stu-id="27e5f-120">Controls and Programmable Objects Compared in Various Languages and Libraries</span></span>](http://msdn.microsoft.com/library/021f2a1b-8247-4348-a5ad-e1d9ab23004b)  
 [<span data-ttu-id="27e5f-121">Postupy: Přidávání ovládacích prvků do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="27e5f-121">How to: Add Controls to Windows Forms</span></span>](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md)  
 [<span data-ttu-id="27e5f-122">Uspořádávání ovládacích prvků ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="27e5f-122">Arranging Controls on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [<span data-ttu-id="27e5f-123">Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky</span><span class="sxs-lookup"><span data-stu-id="27e5f-123">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [<span data-ttu-id="27e5f-124">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="27e5f-124">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [<span data-ttu-id="27e5f-125">Ovládací prvky Windows Forms podle funkce</span><span class="sxs-lookup"><span data-stu-id="27e5f-125">Windows Forms Controls by Function</span></span>](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)
