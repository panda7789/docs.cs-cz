---
title: 'Postupy: Uzamykání ovládacích prvků ve Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, locking
- controls [Windows Forms], locking
ms.assetid: 94efe0d2-c14e-4d14-b903-63ea9b07e290
ms.openlocfilehash: ac5fbf33564ed2dd1a030132a35b36164f777519
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59301695"
---
# <a name="how-to-lock-controls-to-windows-forms"></a><span data-ttu-id="d9832-102">Postupy: Uzamykání ovládacích prvků ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d9832-102">How to: Lock Controls to Windows Forms</span></span>
<span data-ttu-id="d9832-103">Při návrhu uživatelského rozhraní (UI) aplikace Windows můžete uzamknout ovládací prvky, jakmile náleží správně, tak, aby nikoli neúmyslně přesunout nebo změnit jejich velikost, při nastavení dalších vlastností.</span><span class="sxs-lookup"><span data-stu-id="d9832-103">When you design the user interface (UI) of your Windows application, you can lock the controls once they are positioned correctly, so that you do not inadvertently move or resize them when setting other properties.</span></span>  
  
 <span data-ttu-id="d9832-104">Kromě toho můžete zamknutí a odemknutí všech ovládacích prvků na formuláři najednou, který je užitečný pro formuláře s mnoho ovládacích prvků, nebo můžete odemknout jednotlivých ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="d9832-104">Additionally, you can lock and unlock all the controls on the form at once, which is helpful for forms with many controls, or you can unlock individual controls.</span></span> <span data-ttu-id="d9832-105">Jakmile všechny ovládací prvky mají umístit kamkoli chcete ve formuláři, uzamknout je vše na místo, kde můžete zabránit přesunu chybné.</span><span class="sxs-lookup"><span data-stu-id="d9832-105">Once you have placed all the controls where you want them on the form, lock them all in place to prevent erroneous movement.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d9832-106">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="d9832-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="d9832-107">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="d9832-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="d9832-108">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="d9832-108">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-lock-a-control"></a><span data-ttu-id="d9832-109">Uzamknout ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="d9832-109">To lock a control</span></span>  
  
1. <span data-ttu-id="d9832-110">V **vlastnosti** okna, klikněte na tlačítko **uzamčené** vlastnosti a vyberte `true`.</span><span class="sxs-lookup"><span data-stu-id="d9832-110">In the **Properties** window, click the **Locked** property and select `true`.</span></span> <span data-ttu-id="d9832-111">(Poklepete na název přepíná nastavení vlastnosti.)</span><span class="sxs-lookup"><span data-stu-id="d9832-111">(Double-clicking the name toggles the property setting.)</span></span>  
  
     <span data-ttu-id="d9832-112">Alternativně klikněte pravým tlačítkem na ovládací prvek a vyberte **uzamknout ovládací prvky**.</span><span class="sxs-lookup"><span data-stu-id="d9832-112">Alternatively, right-click the control and choose **Lock Controls**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d9832-113">Uzamykání ovládacích prvků jim to brání přetažen novou velikost nebo umístění na návrhové ploše.</span><span class="sxs-lookup"><span data-stu-id="d9832-113">Locking controls prevents them from being dragged to a new size or location on the design surface.</span></span> <span data-ttu-id="d9832-114">Ale můžete pořád změnit velikost nebo umístění ovládacích prvků prostřednictvím **vlastnosti** okna nebo v kódu.</span><span class="sxs-lookup"><span data-stu-id="d9832-114">However, you can still change the size or location of controls by means of the **Properties** window or in code.</span></span>  
  
### <a name="to-lock-all-the-controls-on-a-form"></a><span data-ttu-id="d9832-115">Uzamknout ovládací prvky ve formuláři</span><span class="sxs-lookup"><span data-stu-id="d9832-115">To lock all the controls on a form</span></span>  
  
1. <span data-ttu-id="d9832-116">Z **formátu** nabídce zvolte **uzamknout ovládací prvky**.</span><span class="sxs-lookup"><span data-stu-id="d9832-116">From the **Format** menu, choose **Lock Controls**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d9832-117">Tento příkaz uzamkne velikost formuláře, protože formulář je ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="d9832-117">This command locks the form's size as well, because a form is a control.</span></span>  
  
### <a name="to-unlock-all-locked-controls-on-a-form"></a><span data-ttu-id="d9832-118">K odemknutí všechny uzamčené ovládací prvky ve formuláři</span><span class="sxs-lookup"><span data-stu-id="d9832-118">To unlock all locked controls on a form</span></span>  
  
1. <span data-ttu-id="d9832-119">Z **formátu** nabídce zvolte **uzamknout ovládací prvky**.</span><span class="sxs-lookup"><span data-stu-id="d9832-119">From the **Format** menu, choose **Lock Controls**.</span></span>  
  
     <span data-ttu-id="d9832-120">Všechny předtím zamčenými ovládací prvky ve formuláři jsou teď odemknout.</span><span class="sxs-lookup"><span data-stu-id="d9832-120">All previously locked controls on the form are now unlocked.</span></span>  
  
### <a name="to-unlock-locked-controls-individually"></a><span data-ttu-id="d9832-121">Odemknout uzamčení jednotlivě ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="d9832-121">To unlock locked controls individually</span></span>  
  
1. <span data-ttu-id="d9832-122">V **vlastnosti** okna, klikněte na tlačítko **uzamčené** vlastnosti a vyberte `false`.</span><span class="sxs-lookup"><span data-stu-id="d9832-122">In the **Properties** window, click the **Locked** property and select `false`.</span></span> <span data-ttu-id="d9832-123">(Poklepete na název přepíná nastavení vlastnosti.)</span><span class="sxs-lookup"><span data-stu-id="d9832-123">(Double-clicking the name toggles the property setting.)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9832-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d9832-124">See also</span></span>

- [<span data-ttu-id="d9832-125">Windows Forms – ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="d9832-125">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="d9832-126">Uspořádávání ovládacích prvků ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d9832-126">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="d9832-127">Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky</span><span class="sxs-lookup"><span data-stu-id="d9832-127">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="d9832-128">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d9832-128">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="d9832-129">Ovládací prvky Windows Forms podle funkce</span><span class="sxs-lookup"><span data-stu-id="d9832-129">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
