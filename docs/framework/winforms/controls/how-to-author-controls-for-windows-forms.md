---
title: 'Postupy: vytváření ovládacích prvků'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], creating
- UserControl class [Windows Forms], Windows Forms
- custom controls [Windows Forms], creating
ms.assetid: 7570e982-545b-4c3a-a7c7-55581d313400
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 169104f51898f9bda08efa08685207e50406a7ff
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746717"
---
# <a name="how-to-author-controls-for-windows-forms"></a><span data-ttu-id="e0836-102">Postupy: vytváření ovládacích prvků pro model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e0836-102">How to: Author controls for Windows Forms</span></span>

<span data-ttu-id="e0836-103">Ovládací prvek představuje grafické propojení mezi uživatelem a programem.</span><span class="sxs-lookup"><span data-stu-id="e0836-103">A control represents a graphical link between the user and the program.</span></span> <span data-ttu-id="e0836-104">Ovládací prvek může poskytovat nebo zpracovávat data, přijímat vstup uživatele, reagovat na události nebo provádět libovolný počet dalších funkcí, které spojují uživatele a aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e0836-104">A control can provide or process data, accept user input, respond to events, or perform any number of other functions that connect the user and the application.</span></span> <span data-ttu-id="e0836-105">Vzhledem k tomu, že ovládací prvek je v podstatě komponenta s grafickým rozhraním, může obsluhovat jakoukoli funkci, kterou komponenta dělá, a poskytnout interakci s uživatelem.</span><span class="sxs-lookup"><span data-stu-id="e0836-105">Because a control is essentially a component with a graphical interface, it can serve any function that a component does, as well as provide user interaction.</span></span> <span data-ttu-id="e0836-106">Ovládací prvky jsou vytvořeny pro poskytování konkrétních účelů a ovládací prvky pro vytváření obsahu jsou pouze další úlohy programování.</span><span class="sxs-lookup"><span data-stu-id="e0836-106">Controls are created to serve specific purposes, and authoring controls is just another programming task.</span></span> <span data-ttu-id="e0836-107">V takovém případě následující kroky reprezentují přehled procesu vytváření ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="e0836-107">With that in mind, the following steps represent an overview of the control authoring process.</span></span> <span data-ttu-id="e0836-108">Odkazy poskytují další informace o jednotlivých krocích.</span><span class="sxs-lookup"><span data-stu-id="e0836-108">Links provide additional information on the individual steps.</span></span>

## <a name="to-author-a-control"></a><span data-ttu-id="e0836-109">Chcete-li vytvořit ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="e0836-109">To author a control</span></span>

1. <span data-ttu-id="e0836-110">Určete, jak chcete, aby váš ovládací prvek vyzkoušel nebo co jeho součást bude možné ve vaší aplikaci přehrát.</span><span class="sxs-lookup"><span data-stu-id="e0836-110">Determine what you want your control to accomplish, or what part it will play in your application.</span></span> <span data-ttu-id="e0836-111">Faktory, které je potřeba vzít v úvahu:</span><span class="sxs-lookup"><span data-stu-id="e0836-111">Factors to consider are:</span></span>

    - <span data-ttu-id="e0836-112">Jaký druh grafického rozhraní potřebujete?</span><span class="sxs-lookup"><span data-stu-id="e0836-112">What kind of graphical interface do you need?</span></span>

    - <span data-ttu-id="e0836-113">Jakou interakci s uživatelem tento ovládací prvek zpracuje?</span><span class="sxs-lookup"><span data-stu-id="e0836-113">What specific user interactions will this control handle?</span></span>

    - <span data-ttu-id="e0836-114">Je funkce, kterou potřebujete k dispozici u všech stávajících ovládacích prvků?</span><span class="sxs-lookup"><span data-stu-id="e0836-114">Is the functionality you need provided by any existing controls?</span></span>

    - <span data-ttu-id="e0836-115">Funkce, které potřebujete, můžete získat kombinováním několika model Windows Formsch ovládacích prvků?</span><span class="sxs-lookup"><span data-stu-id="e0836-115">Can you get the functionality you need by combining several Windows Forms controls?</span></span>

2. <span data-ttu-id="e0836-116">Pokud potřebujete objektový model pro ovládací prvek, určete, jak budou distribuovány funkce v celém objektovém modelu a rozdělte funkce mezi ovládací prvek a všechny podobjekty.</span><span class="sxs-lookup"><span data-stu-id="e0836-116">If you need an object model for your control, determine how functionality will be distributed throughout the object model, and divide up functionality between the control and any subobjects.</span></span> <span data-ttu-id="e0836-117">Objektový model může být užitečný, pokud plánujete složitý ovládací prvek nebo chcete začlenit několik funkcí.</span><span class="sxs-lookup"><span data-stu-id="e0836-117">An object model may be useful if you are planning a complex control, or want to incorporate several functionalities.</span></span>

3. <span data-ttu-id="e0836-118">Určete typ ovládacího prvku (například uživatelský ovládací prvek, vlastní ovládací prvek, zděděný model Windows Forms ovládací prvek), který potřebujete.</span><span class="sxs-lookup"><span data-stu-id="e0836-118">Determine the type of control (for example, user control, custom control, inherited Windows Forms control) you need.</span></span> <span data-ttu-id="e0836-119">Podrobnosti naleznete v tématu [doporučení typu ovládacího prvku](control-type-recommendations.md) a [odrůdy vlastních ovládacích prvků](varieties-of-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="e0836-119">For details, see [Control Type Recommendations](control-type-recommendations.md) and [Varieties of Custom Controls](varieties-of-custom-controls.md).</span></span>

4. <span data-ttu-id="e0836-120">Rychlé funkce jako vlastnosti, metody a události ovládacího prvku a jeho podřízených objektů nebo poboček a přiřadí příslušné úrovně přístupu (například Public, Protected atd.).</span><span class="sxs-lookup"><span data-stu-id="e0836-120">Express functionality as properties, methods, and events of the control and its subobjects or subsidiary structures, and assign appropriate access levels (for example, public, protected, and so on).</span></span>

5. <span data-ttu-id="e0836-121">Pokud pro svůj ovládací prvek potřebujete vlastní malování, přidejte pro něj kód.</span><span class="sxs-lookup"><span data-stu-id="e0836-121">If you need custom painting for your control, add code for it.</span></span> <span data-ttu-id="e0836-122">Podrobnosti najdete v tématu [Malování a vykreslování vlastního ovládacího prvku](custom-control-painting-and-rendering.md).</span><span class="sxs-lookup"><span data-stu-id="e0836-122">For details, see [Custom Control Painting and Rendering](custom-control-painting-and-rendering.md).</span></span>

6. <span data-ttu-id="e0836-123">Pokud váš ovládací prvek dědí z <xref:System.Windows.Forms.UserControl>, můžete otestovat jeho chování za běhu sestavením projektu ovládacího prvku a jeho spuštěním v **kontejneru testu UserControl**.</span><span class="sxs-lookup"><span data-stu-id="e0836-123">If your control inherits from <xref:System.Windows.Forms.UserControl>, you can test its runtime behavior by building the control project and running it in the **UserControl Test Container**.</span></span> <span data-ttu-id="e0836-124">Další informace naleznete v tématu [How to: test runtime Behavior prvku UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span><span class="sxs-lookup"><span data-stu-id="e0836-124">For more information, see [How to: Test the Run-Time Behavior of a UserControl](how-to-test-the-run-time-behavior-of-a-usercontrol.md).</span></span>

7. <span data-ttu-id="e0836-125">Můžete také otestovat a ladit ovládací prvek vytvořením nového projektu, jako je například aplikace systému Windows, a umístěním do kontejneru.</span><span class="sxs-lookup"><span data-stu-id="e0836-125">You can also test and debug your control by creating a new project, such as a Windows Application, and placing it into a container.</span></span> <span data-ttu-id="e0836-126">Tento proces je znázorněn jako součást [návodu: vytváření složeného ovládacího prvku](walkthrough-authoring-a-composite-control-with-visual-csharp.md).</span><span class="sxs-lookup"><span data-stu-id="e0836-126">This process is demonstrated as part of [Walkthrough: Authoring a Composite Control](walkthrough-authoring-a-composite-control-with-visual-csharp.md).</span></span>

8. <span data-ttu-id="e0836-127">Když přidáte jednotlivé funkce, přidejte do projektu testů funkce pro uplatnění nových funkcí.</span><span class="sxs-lookup"><span data-stu-id="e0836-127">As you add each feature, add features to your test project to exercise the new functionality.</span></span>

9. <span data-ttu-id="e0836-128">Opakujte návrh návrhu.</span><span class="sxs-lookup"><span data-stu-id="e0836-128">Repeat, refining the design.</span></span>

10. <span data-ttu-id="e0836-129">Zabalení a nasazení ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="e0836-129">Package and deploy your control.</span></span> <span data-ttu-id="e0836-130">Podrobnosti najdete v tématu [první pohled na nasazení v aplikaci Visual Studio](/visualstudio/deployment/deploying-applications-services-and-components).</span><span class="sxs-lookup"><span data-stu-id="e0836-130">For details, see [First look at deployment in Visual Studio](/visualstudio/deployment/deploying-applications-services-and-components).</span></span>

## <a name="see-also"></a><span data-ttu-id="e0836-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="e0836-131">See also</span></span>

- [<span data-ttu-id="e0836-132">Postupy: Dědění ze třídy UserControl</span><span class="sxs-lookup"><span data-stu-id="e0836-132">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)
- [<span data-ttu-id="e0836-133">Postupy: Dědění ze třídy Control</span><span class="sxs-lookup"><span data-stu-id="e0836-133">How to: Inherit from the Control Class</span></span>](how-to-inherit-from-the-control-class.md)
- [<span data-ttu-id="e0836-134">Postupy: Dědění ze stávajících ovládacích prvků Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e0836-134">How to: Inherit from Existing Windows Forms Controls</span></span>](how-to-inherit-from-existing-windows-forms-controls.md)
- [<span data-ttu-id="e0836-135">Postupy: Otestování běhového chování UserControl</span><span class="sxs-lookup"><span data-stu-id="e0836-135">How to: Test the Run-Time Behavior of a UserControl</span></span>](how-to-test-the-run-time-behavior-of-a-usercontrol.md)
- [<span data-ttu-id="e0836-136">Typy vlastních ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="e0836-136">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
