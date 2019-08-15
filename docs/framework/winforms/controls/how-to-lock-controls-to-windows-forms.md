---
title: 'Postupy: Uzamykání ovládacích prvků ve Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, locking
- controls [Windows Forms], locking
ms.assetid: 94efe0d2-c14e-4d14-b903-63ea9b07e290
ms.openlocfilehash: cbf82f1481ee9779cec5cfbf3fb057b7ea399a1c
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039907"
---
# <a name="how-to-lock-controls-to-windows-forms"></a><span data-ttu-id="11e3a-102">Postupy: Uzamykání ovládacích prvků ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="11e3a-102">How to: Lock Controls to Windows Forms</span></span>
<span data-ttu-id="11e3a-103">Při návrhu uživatelského rozhraní (UI) aplikace systému Windows můžete ovládací prvky uzamknout, jakmile jsou umístěny správně, takže při nastavování dalších vlastností je neúmyslně přesunovat ani měnit jejich velikost.</span><span class="sxs-lookup"><span data-stu-id="11e3a-103">When you design the user interface (UI) of your Windows application, you can lock the controls once they are positioned correctly, so that you do not inadvertently move or resize them when setting other properties.</span></span>

 <span data-ttu-id="11e3a-104">Kromě toho můžete uzamknout a odemknout všechny ovládací prvky ve formuláři najednou, což je užitečné pro formuláře s mnoha ovládacími prvky, nebo můžete odemknout jednotlivé ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="11e3a-104">Additionally, you can lock and unlock all the controls on the form at once, which is helpful for forms with many controls, or you can unlock individual controls.</span></span> <span data-ttu-id="11e3a-105">Po umístění všech ovládacích prvků tam, kde je chcete umístit do formuláře, je všechny zablokované, aby nedocházelo k chybnému přesunu.</span><span class="sxs-lookup"><span data-stu-id="11e3a-105">Once you have placed all the controls where you want them on the form, lock them all in place to prevent erroneous movement.</span></span>

## <a name="to-lock-a-control"></a><span data-ttu-id="11e3a-106">Uzamčení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="11e3a-106">To lock a control</span></span>

1. <span data-ttu-id="11e3a-107">V okně **vlastnosti** klikněte na vlastnost **Uzamčeno** a vyberte `true`.</span><span class="sxs-lookup"><span data-stu-id="11e3a-107">In the **Properties** window, click the **Locked** property and select `true`.</span></span> <span data-ttu-id="11e3a-108">(Dvojitým kliknutím na název přepínáte nastavení vlastnosti.)</span><span class="sxs-lookup"><span data-stu-id="11e3a-108">(Double-clicking the name toggles the property setting.)</span></span>

     <span data-ttu-id="11e3a-109">Případně klikněte pravým tlačítkem myši na ovládací prvek a vyberte **Zamknout ovládací prvky**.</span><span class="sxs-lookup"><span data-stu-id="11e3a-109">Alternatively, right-click the control and choose **Lock Controls**.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="11e3a-110">Blokovací ovládací prvky zabraňují jejich přetažení na novou velikost nebo umístění na návrhové ploše.</span><span class="sxs-lookup"><span data-stu-id="11e3a-110">Locking controls prevents them from being dragged to a new size or location on the design surface.</span></span> <span data-ttu-id="11e3a-111">Můžete však i nadále měnit velikost nebo umístění ovládacích prvků pomocí okna **vlastnosti** nebo v kódu.</span><span class="sxs-lookup"><span data-stu-id="11e3a-111">However, you can still change the size or location of controls by means of the **Properties** window or in code.</span></span>

## <a name="to-lock-all-the-controls-on-a-form"></a><span data-ttu-id="11e3a-112">Uzamčení všech ovládacích prvků ve formuláři</span><span class="sxs-lookup"><span data-stu-id="11e3a-112">To lock all the controls on a form</span></span>

1. <span data-ttu-id="11e3a-113">V nabídce **Formát** vyberte možnost **Zamknout ovládací prvky**.</span><span class="sxs-lookup"><span data-stu-id="11e3a-113">From the **Format** menu, choose **Lock Controls**.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="11e3a-114">Tento příkaz zamkne i velikost formuláře, protože formulář je ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="11e3a-114">This command locks the form's size as well, because a form is a control.</span></span>

## <a name="to-unlock-all-locked-controls-on-a-form"></a><span data-ttu-id="11e3a-115">Odemčení všech uzamčených ovládacích prvků na formuláři</span><span class="sxs-lookup"><span data-stu-id="11e3a-115">To unlock all locked controls on a form</span></span>

1. <span data-ttu-id="11e3a-116">V nabídce **Formát** vyberte možnost **Zamknout ovládací prvky**.</span><span class="sxs-lookup"><span data-stu-id="11e3a-116">From the **Format** menu, choose **Lock Controls**.</span></span>

     <span data-ttu-id="11e3a-117">Všechny dříve uzamčené ovládací prvky ve formuláři jsou nyní odemčeny.</span><span class="sxs-lookup"><span data-stu-id="11e3a-117">All previously locked controls on the form are now unlocked.</span></span>

## <a name="to-unlock-locked-controls-individually"></a><span data-ttu-id="11e3a-118">Chcete-li odemknout uzamčené ovládací prvky individuálně</span><span class="sxs-lookup"><span data-stu-id="11e3a-118">To unlock locked controls individually</span></span>

1. <span data-ttu-id="11e3a-119">V okně **vlastnosti** klikněte na vlastnost **Uzamčeno** a vyberte `false`.</span><span class="sxs-lookup"><span data-stu-id="11e3a-119">In the **Properties** window, click the **Locked** property and select `false`.</span></span> <span data-ttu-id="11e3a-120">(Dvojitým kliknutím na název přepínáte nastavení vlastnosti.)</span><span class="sxs-lookup"><span data-stu-id="11e3a-120">(Double-clicking the name toggles the property setting.)</span></span>

## <a name="see-also"></a><span data-ttu-id="11e3a-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="11e3a-121">See also</span></span>

- [<span data-ttu-id="11e3a-122">Windows Forms – ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="11e3a-122">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="11e3a-123">Uspořádávání ovládacích prvků ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="11e3a-123">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="11e3a-124">Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky</span><span class="sxs-lookup"><span data-stu-id="11e3a-124">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="11e3a-125">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="11e3a-125">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="11e3a-126">Ovládací prvky Windows Forms podle funkce</span><span class="sxs-lookup"><span data-stu-id="11e3a-126">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
