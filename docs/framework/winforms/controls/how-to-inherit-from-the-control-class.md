---
title: 'Postupy: Dědění ze třídy Control'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], Windows Forms custom controls
- Control class [Windows Forms], inheriting from
- custom controls [Windows Forms], inheritance
- OnPaint method [Windows Forms]
- custom controls [Windows Forms], creating
ms.assetid: 46ba0df3-5cf7-443c-a3b4-a72660172476
ms.openlocfilehash: 0cb63be6774fd82cd94a1bc59b8a1025efa47df5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966572"
---
# <a name="how-to-inherit-from-the-control-class"></a><span data-ttu-id="ebbcb-102">Postupy: Dědění ze třídy Control</span><span class="sxs-lookup"><span data-stu-id="ebbcb-102">How to: Inherit from the Control Class</span></span>
<span data-ttu-id="ebbcb-103">Chcete-li vytvořit zcela vlastní ovládací prvek pro použití ve formuláři Windows, měli byste dědit z <xref:System.Windows.Forms.Control> třídy.</span><span class="sxs-lookup"><span data-stu-id="ebbcb-103">If you want to create a completely custom control to use on a Windows Form, you should inherit from the <xref:System.Windows.Forms.Control> class.</span></span> <span data-ttu-id="ebbcb-104">Dědění od <xref:System.Windows.Forms.Control> třídy vyžaduje, abyste provedli další plánování a implementaci, ale poskytuje také největší rozsah možností.</span><span class="sxs-lookup"><span data-stu-id="ebbcb-104">While inheriting from the <xref:System.Windows.Forms.Control> class requires that you perform more planning and implementation, it also provides you with the largest range of options.</span></span> <span data-ttu-id="ebbcb-105">Při dědění z <xref:System.Windows.Forms.Control>je děděna velmi základní funkce, která ovládací prvky usnadňují práci.</span><span class="sxs-lookup"><span data-stu-id="ebbcb-105">When inheriting from <xref:System.Windows.Forms.Control>, you inherit the very basic functionality that makes controls work.</span></span> <span data-ttu-id="ebbcb-106">Funkce, které jsou <xref:System.Windows.Forms.Control> součástí třídy, zpracovává vstup uživatele prostřednictvím klávesnice a myši, definuje meze a velikost ovládacího prvku, nabízí popisovač systému Windows a poskytuje řízení a zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="ebbcb-106">The functionality inherent in the <xref:System.Windows.Forms.Control> class handles user input through the keyboard and mouse, defines the bounds and size of the control, provides a windows handle, and provides message handling and security.</span></span> <span data-ttu-id="ebbcb-107">Nezahrnuje žádné vykreslování, což je v tomto případě skutečné vykreslování grafického rozhraní ovládacího prvku, ani nezahrnuje žádné konkrétní funkce interakce s uživatelem.</span><span class="sxs-lookup"><span data-stu-id="ebbcb-107">It does not incorporate any painting, which in this case is the actual rendering of the graphical interface of the control, nor does it incorporate any specific user interaction functionality.</span></span> <span data-ttu-id="ebbcb-108">Všechny tyto aspekty je nutné poskytnout prostřednictvím vlastního kódu.</span><span class="sxs-lookup"><span data-stu-id="ebbcb-108">You must provide all of these aspects through custom code.</span></span>

## <a name="to-create-a-custom-control"></a><span data-ttu-id="ebbcb-109">Vytvoření vlastního ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="ebbcb-109">To create a custom control</span></span>

1. <span data-ttu-id="ebbcb-110">Vytvořte novou **aplikaci systému Windows** nebo projekt **knihovny ovládacích prvků systému** Windows.</span><span class="sxs-lookup"><span data-stu-id="ebbcb-110">Create a new **Windows Application** or **Windows Control Library** project.</span></span>

2. <span data-ttu-id="ebbcb-111">V nabídce **projekt** vyberte možnost **Přidat třídu**.</span><span class="sxs-lookup"><span data-stu-id="ebbcb-111">From the **Project** menu, choose **Add Class**.</span></span>

3. <span data-ttu-id="ebbcb-112">V dialogovém okně **Přidat novou položku** klikněte na **vlastní ovládací prvek**.</span><span class="sxs-lookup"><span data-stu-id="ebbcb-112">In the **Add New Item** dialog box, click **Custom Control**.</span></span>

     <span data-ttu-id="ebbcb-113">Do projektu se přidá nový vlastní ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="ebbcb-113">A new custom control is added to your project.</span></span>

4. <span data-ttu-id="ebbcb-114">Stisknutím klávesy F7 otevřete **Editor kódu** vlastního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ebbcb-114">Press F7 to open the **Code Editor** for your custom control.</span></span>

5. <span data-ttu-id="ebbcb-115">Vyhledejte metodu, která bude prázdná s výjimkou volání <xref:System.Windows.Forms.Control.OnPaint%2A> metody základní třídy. <xref:System.Windows.Forms.Control.OnPaint%2A></span><span class="sxs-lookup"><span data-stu-id="ebbcb-115">Locate the <xref:System.Windows.Forms.Control.OnPaint%2A> method, which will be empty except for a call to the <xref:System.Windows.Forms.Control.OnPaint%2A> method of the base class.</span></span>

6. <span data-ttu-id="ebbcb-116">Upravte kód tak, aby zahrnoval jakékoli vlastní vykreslení, které chcete pro svůj ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="ebbcb-116">Modify the code to incorporate any custom painting you want for your control.</span></span>

     <span data-ttu-id="ebbcb-117">Informace o psaní kódu pro vykreslení grafiky ovládacích prvků naleznete v tématu [vlastní ovládací prvky Malování a vykreslování](custom-control-painting-and-rendering.md).</span><span class="sxs-lookup"><span data-stu-id="ebbcb-117">For information about writing code to render graphics for controls, see [Custom Control Painting and Rendering](custom-control-painting-and-rendering.md).</span></span>

7. <span data-ttu-id="ebbcb-118">Implementujte jakékoli vlastní metody, vlastnosti nebo události, které bude váš ovládací prvek obsahovat.</span><span class="sxs-lookup"><span data-stu-id="ebbcb-118">Implement any custom methods, properties, or events that your control will incorporate.</span></span>

8. <span data-ttu-id="ebbcb-119">Uložte a otestujte svůj ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="ebbcb-119">Save and test your control.</span></span>

## <a name="see-also"></a><span data-ttu-id="ebbcb-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ebbcb-120">See also</span></span>

- [<span data-ttu-id="ebbcb-121">Typy vlastních ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="ebbcb-121">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)
- [<span data-ttu-id="ebbcb-122">Postupy: Zdědit z třídy UserControl</span><span class="sxs-lookup"><span data-stu-id="ebbcb-122">How to: Inherit from the UserControl Class</span></span>](how-to-inherit-from-the-usercontrol-class.md)
- [<span data-ttu-id="ebbcb-123">Postupy: Zdědit z existujících ovládacích prvků model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ebbcb-123">How to: Inherit from Existing Windows Forms Controls</span></span>](how-to-inherit-from-existing-windows-forms-controls.md)
- [<span data-ttu-id="ebbcb-124">Postupy: Vytváření ovládacích prvků pro model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ebbcb-124">How to: Author Controls for Windows Forms</span></span>](how-to-author-controls-for-windows-forms.md)
- [<span data-ttu-id="ebbcb-125">Řešení potíží se zděděnými obslužnými rutinami událostí v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ebbcb-125">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)
- [<span data-ttu-id="ebbcb-126">Vývoj ovládacích prvků Windows Forms v době návrhu</span><span class="sxs-lookup"><span data-stu-id="ebbcb-126">Developing Windows Forms Controls at Design Time</span></span>](developing-windows-forms-controls-at-design-time.md)
