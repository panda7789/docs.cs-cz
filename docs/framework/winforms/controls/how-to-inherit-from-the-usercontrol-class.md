---
title: 'Postupy: Dědění ze třídy UserControl'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- UserControl class [Windows Forms], inheriting from
- user controls [Windows Forms], creating
- composite controls [Windows Forms], creating
ms.assetid: 67713625-e2e4-4f6a-bce7-0855ee5043d9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 10bb807d012a130ad633b7ce06f99c5abf2cdda1
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458368"
---
# <a name="how-to-inherit-from-the-usercontrol-class"></a><span data-ttu-id="5e39c-102">Postupy: Dědění ze třídy UserControl</span><span class="sxs-lookup"><span data-stu-id="5e39c-102">How to: Inherit from the UserControl Class</span></span>

<span data-ttu-id="5e39c-103">Chcete-li kombinovat funkce jednoho nebo více model Windows Forms ovládacích prvků s vlastním kódem, můžete vytvořit *uživatelský ovládací prvek*.</span><span class="sxs-lookup"><span data-stu-id="5e39c-103">To combine the functionality of one or more Windows Forms controls with custom code, you can create a *user control*.</span></span> <span data-ttu-id="5e39c-104">Uživatelské ovládací prvky kombinují rychlý vývoj ovládacích prvků, standardní funkce řízení model Windows Forms a univerzálnost vlastních vlastností a metod.</span><span class="sxs-lookup"><span data-stu-id="5e39c-104">User controls combine rapid control development, standard Windows Forms control functionality, and the versatility of custom properties and methods.</span></span> <span data-ttu-id="5e39c-105">Po zahájení vytváření uživatelského ovládacího prvku se zobrazí viditelný Návrhář, na kterém můžete umístit standardní model Windows Forms ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="5e39c-105">When you begin creating a user control, you are presented with a visible designer, upon which you can place standard Windows Forms controls.</span></span> <span data-ttu-id="5e39c-106">Tyto ovládací prvky zachovávají veškerou svou vlastní funkčnost a také vzhled a chování (vzhled a chování) standardních ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="5e39c-106">These controls retain all of their inherent functionality, as well as the appearance and behavior (look and feel) of standard controls.</span></span> <span data-ttu-id="5e39c-107">Jakmile jsou tyto ovládací prvky integrovány do uživatelského ovládacího prvku, nejsou již k dispozici prostřednictvím kódu.</span><span class="sxs-lookup"><span data-stu-id="5e39c-107">Once these controls are built into the user control, however, they are no longer available to you through code.</span></span> <span data-ttu-id="5e39c-108">Uživatelský ovládací prvek provádí vlastní Malování a také zpracovává všechny základní funkce přidružené k ovládacím prvkům.</span><span class="sxs-lookup"><span data-stu-id="5e39c-108">The user control does its own painting and also handles all of the basic functionality associated with controls.</span></span>

## <a name="to-create-a-user-control"></a><span data-ttu-id="5e39c-109">Vytvoření uživatelského ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="5e39c-109">To create a user control</span></span>

1. <span data-ttu-id="5e39c-110">Vytvořte nový projekt **knihovny ovládacích prvků systému Windows** v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5e39c-110">Create a new **Windows Control Library** project in Visual Studio.</span></span>

   <span data-ttu-id="5e39c-111">Vytvoří se nový projekt s prázdným uživatelským ovládacím prvkem.</span><span class="sxs-lookup"><span data-stu-id="5e39c-111">A new project is created with a blank user control.</span></span>

2. <span data-ttu-id="5e39c-112">Přetáhněte ovládací prvky z karty **model Windows Forms** **panelu nástrojů** do návrháře.</span><span class="sxs-lookup"><span data-stu-id="5e39c-112">Drag controls from the **Windows Forms** tab of the **Toolbox** onto your designer.</span></span>

3. <span data-ttu-id="5e39c-113">Tyto ovládací prvky by měly být umístěny a navrženy tak, jak se mají zobrazovat v konečném uživatelském ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="5e39c-113">These controls should be positioned and designed as you want them to appear in the final user control.</span></span> <span data-ttu-id="5e39c-114">Chcete-li vývojářům dovolit přístup k ovládacím prvkům prvku, je nutné je deklarovat jako veřejné nebo selektivně vystavit vlastnosti ovládacího prvku prvku.</span><span class="sxs-lookup"><span data-stu-id="5e39c-114">If you want to allow developers to access the constituent controls, you must declare them as public, or selectively expose properties of the constituent control.</span></span> <span data-ttu-id="5e39c-115">Podrobnosti naleznete v tématu [How to: vystavování vlastností ovládacích prvků](how-to-expose-properties-of-constituent-controls.md)prvku.</span><span class="sxs-lookup"><span data-stu-id="5e39c-115">For details, see [How to: Expose Properties of Constituent Controls](how-to-expose-properties-of-constituent-controls.md).</span></span>

4. <span data-ttu-id="5e39c-116">Implementujte všechny vlastní metody nebo vlastnosti, které bude váš ovládací prvek obsahovat.</span><span class="sxs-lookup"><span data-stu-id="5e39c-116">Implement any custom methods or properties that your control will incorporate.</span></span>

5. <span data-ttu-id="5e39c-117">Stisknutím klávesy **F5** Sestavte projekt a spusťte ovládací prvek v **kontejneru testu UserControl**.</span><span class="sxs-lookup"><span data-stu-id="5e39c-117">Press **F5** to build the project and run your control in the **UserControl Test Container**.</span></span> <span data-ttu-id="5e39c-118">Další informace naleznete v tématu [How to: test runtime Behavior prvku UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="5e39c-118">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5e39c-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5e39c-119">See also</span></span>

- [<span data-ttu-id="5e39c-120">Typy vlastních ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="5e39c-120">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="5e39c-121">Postupy: Dědění ze třídy Control</span><span class="sxs-lookup"><span data-stu-id="5e39c-121">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)
- [<span data-ttu-id="5e39c-122">Postupy: Dědění ze stávajících ovládacích prvků Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5e39c-122">How to: Inherit from Existing Windows Forms Controls</span></span>](how-to-inherit-from-existing-windows-forms-controls.md)
- [<span data-ttu-id="5e39c-123">Postupy: Vytváření ovládacích prvků pro Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5e39c-123">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)
- [<span data-ttu-id="5e39c-124">Řešení potíží se zděděnými obslužnými rutinami událostí v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5e39c-124">Troubleshoot Inherited Event Handlers in Visual Basic</span></span>](~/docs/visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [<span data-ttu-id="5e39c-125">Postupy: Otestování běhového chování UserControl</span><span class="sxs-lookup"><span data-stu-id="5e39c-125">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
