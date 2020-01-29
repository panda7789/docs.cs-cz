---
title: Uzamčení ovládacích prvků
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, locking
- controls [Windows Forms], locking
ms.assetid: 94efe0d2-c14e-4d14-b903-63ea9b07e290
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 16eb151dc435614e1edc82bf9f0acf3974f36690
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736235"
---
# <a name="how-to-lock-controls-to-windows-forms"></a><span data-ttu-id="b8601-102">Postupy: uzamknutí ovládacích prvků na model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b8601-102">How to: Lock controls to Windows Forms</span></span>

<span data-ttu-id="b8601-103">Při návrhu uživatelského rozhraní (UI) aplikace systému Windows můžete ovládací prvky uzamknout, jakmile jsou umístěny správně, takže při nastavování dalších vlastností je neúmyslně přesunovat ani měnit jejich velikost.</span><span class="sxs-lookup"><span data-stu-id="b8601-103">When you design the user interface (UI) of your Windows application, you can lock the controls once they are positioned correctly, so that you do not inadvertently move or resize them when setting other properties.</span></span>

<span data-ttu-id="b8601-104">Kromě toho můžete uzamknout a odemknout všechny ovládací prvky ve formuláři najednou, což je užitečné pro formuláře s mnoha ovládacími prvky, nebo můžete odemknout jednotlivé ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="b8601-104">Additionally, you can lock and unlock all the controls on the form at once, which is helpful for forms with many controls, or you can unlock individual controls.</span></span> <span data-ttu-id="b8601-105">Po umístění všech ovládacích prvků tam, kde je chcete umístit do formuláře, je všechny zablokované, aby nedocházelo k chybnému přesunu.</span><span class="sxs-lookup"><span data-stu-id="b8601-105">Once you have placed all the controls where you want them on the form, lock them all in place to prevent erroneous movement.</span></span>

## <a name="to-lock-a-control"></a><span data-ttu-id="b8601-106">Uzamčení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="b8601-106">To lock a control</span></span>

<span data-ttu-id="b8601-107">V okně **vlastnosti** sady Visual Studio vyberte vlastnost **Uzamčeno** a pak vyberte **hodnotu true**.</span><span class="sxs-lookup"><span data-stu-id="b8601-107">In the **Properties** window of Visual Studio, select the **Locked** property and then select **true**.</span></span> <span data-ttu-id="b8601-108">(Dvojitým kliknutím na název přepínáte nastavení vlastnosti.)</span><span class="sxs-lookup"><span data-stu-id="b8601-108">(Double-clicking the name toggles the property setting.)</span></span>

<span data-ttu-id="b8601-109">Případně klikněte pravým tlačítkem myši na ovládací prvek a vyberte **Zamknout ovládací prvky**.</span><span class="sxs-lookup"><span data-stu-id="b8601-109">Alternatively, right-click the control and choose **Lock Controls**.</span></span>

> [!NOTE]
> <span data-ttu-id="b8601-110">Blokovací ovládací prvky zabraňují jejich přetažení na novou velikost nebo umístění na návrhové ploše.</span><span class="sxs-lookup"><span data-stu-id="b8601-110">Locking controls prevents them from being dragged to a new size or location on the design surface.</span></span> <span data-ttu-id="b8601-111">Můžete však i nadále měnit velikost nebo umístění ovládacích prvků pomocí okna **vlastnosti** nebo v kódu.</span><span class="sxs-lookup"><span data-stu-id="b8601-111">However, you can still change the size or location of controls by means of the **Properties** window or in code.</span></span>

## <a name="to-lock-all-the-controls-on-a-form"></a><span data-ttu-id="b8601-112">Uzamčení všech ovládacích prvků ve formuláři</span><span class="sxs-lookup"><span data-stu-id="b8601-112">To lock all the controls on a form</span></span>

<span data-ttu-id="b8601-113">V nabídce **Formát** vyberte možnost **Zamknout ovládací prvky**.</span><span class="sxs-lookup"><span data-stu-id="b8601-113">From the **Format** menu, choose **Lock Controls**.</span></span>

> [!NOTE]
> <span data-ttu-id="b8601-114">Tento příkaz zamkne i velikost formuláře, protože formulář je ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="b8601-114">This command locks the form's size as well, because a form is a control.</span></span>

## <a name="to-unlock-all-locked-controls-on-a-form"></a><span data-ttu-id="b8601-115">Odemčení všech uzamčených ovládacích prvků na formuláři</span><span class="sxs-lookup"><span data-stu-id="b8601-115">To unlock all locked controls on a form</span></span>

<span data-ttu-id="b8601-116">V nabídce **Formát** vyberte možnost **Zamknout ovládací prvky**.</span><span class="sxs-lookup"><span data-stu-id="b8601-116">From the **Format** menu, choose **Lock Controls**.</span></span>

<span data-ttu-id="b8601-117">Všechny dříve uzamčené ovládací prvky ve formuláři jsou nyní odemčeny.</span><span class="sxs-lookup"><span data-stu-id="b8601-117">All previously locked controls on the form are now unlocked.</span></span>

## <a name="to-unlock-locked-controls-individually"></a><span data-ttu-id="b8601-118">Chcete-li odemknout uzamčené ovládací prvky individuálně</span><span class="sxs-lookup"><span data-stu-id="b8601-118">To unlock locked controls individually</span></span>

<span data-ttu-id="b8601-119">V okně **vlastnosti** vyberte vlastnost **Uzamčeno** a pak vyberte **hodnotu false**.</span><span class="sxs-lookup"><span data-stu-id="b8601-119">In the **Properties** window, select the **Locked** property and then select **false**.</span></span> <span data-ttu-id="b8601-120">(Dvojitým kliknutím na název přepínáte nastavení vlastnosti.)</span><span class="sxs-lookup"><span data-stu-id="b8601-120">(Double-clicking the name toggles the property setting.)</span></span>

## <a name="see-also"></a><span data-ttu-id="b8601-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b8601-121">See also</span></span>

- [<span data-ttu-id="b8601-122">Windows Forms – ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="b8601-122">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="b8601-123">Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky</span><span class="sxs-lookup"><span data-stu-id="b8601-123">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="b8601-124">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b8601-124">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="b8601-125">Ovládací prvky Windows Forms podle funkce</span><span class="sxs-lookup"><span data-stu-id="b8601-125">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)
