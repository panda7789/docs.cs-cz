---
title: Poskytování informací o usnadnění pro ovládací prvky ve formuláři Windows
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, accessibility
- controls [Windows Forms], accessibility
- accessibility [Windows Forms], Windows Forms controls
ms.assetid: 887dee6f-5059-4d57-957d-7c6fcd4acb10
ms.openlocfilehash: ffeecc1dfe52f1703fc201ef196644afbcc4708c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33536833"
---
# <a name="providing-accessibility-information-for-controls-on-a-windows-form"></a><span data-ttu-id="10821-102">Poskytování informací o usnadnění pro ovládací prvky ve formuláři Windows</span><span class="sxs-lookup"><span data-stu-id="10821-102">Providing Accessibility Information for Controls on a Windows Form</span></span>
<span data-ttu-id="10821-103">Usnadnění jsou specializované programy a zařízení, které pomáhají osoby s postižením efektivněji využívat počítače.</span><span class="sxs-lookup"><span data-stu-id="10821-103">Accessibility aids are specialized programs and devices that help people with disabilities use computers more effectively.</span></span> <span data-ttu-id="10821-104">Mezi příklady patří čtečky obrazovky pro uživatele, kteří jsou blind a hlasové vstupní nástrojů pro uživatele, kteří poskytují ústní příkazy místo pomocí myši a klávesnice.</span><span class="sxs-lookup"><span data-stu-id="10821-104">Examples include screen readers for people who are blind and voice input utilities for people who provide verbal commands instead of using the mouse or keyboard.</span></span> <span data-ttu-id="10821-105">Tyto usnadnění komunikovat s vlastnostmi usnadnění vystavené ovládací prvky Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="10821-105">These accessibility aids interact with the accessibility properties exposed by Windows Forms controls.</span></span> <span data-ttu-id="10821-106">Tyto vlastnosti jsou:</span><span class="sxs-lookup"><span data-stu-id="10821-106">These properties are:</span></span>  
  
-   <span data-ttu-id="10821-107">**AccessibilityObject**</span><span class="sxs-lookup"><span data-stu-id="10821-107">**AccessibilityObject**</span></span>  
  
-   <span data-ttu-id="10821-108">**AccessibleDefaultActionDescription**</span><span class="sxs-lookup"><span data-stu-id="10821-108">**AccessibleDefaultActionDescription**</span></span>  
  
-   <span data-ttu-id="10821-109">**AccessibleDescription**</span><span class="sxs-lookup"><span data-stu-id="10821-109">**AccessibleDescription**</span></span>  
  
-   <span data-ttu-id="10821-110">**AccessibleName**</span><span class="sxs-lookup"><span data-stu-id="10821-110">**AccessibleName**</span></span>  
  
-   <span data-ttu-id="10821-111">**AccessibleRole**</span><span class="sxs-lookup"><span data-stu-id="10821-111">**AccessibleRole**</span></span>  
  
## <a name="accessibilityobject-property"></a><span data-ttu-id="10821-112">Vlastnost AccessibilityObject</span><span class="sxs-lookup"><span data-stu-id="10821-112">AccessibilityObject Property</span></span>  
 <span data-ttu-id="10821-113">Tato vlastnost jen pro čtení obsahuje <xref:System.Windows.Forms.AccessibleObject> instance.</span><span class="sxs-lookup"><span data-stu-id="10821-113">This read-only property contains an <xref:System.Windows.Forms.AccessibleObject> instance.</span></span> <span data-ttu-id="10821-114">**Třída AccessibleObject** implementuje <xref:Accessibility.IAccessible> rozhraní, která poskytuje informace o popis ovládacího prvku, umístění na obrazovce, navigační dalo a hodnoty.</span><span class="sxs-lookup"><span data-stu-id="10821-114">The **AccessibleObject** implements the <xref:Accessibility.IAccessible> interface, which provides information about the control's description, screen location, navigational abilities, and value.</span></span> <span data-ttu-id="10821-115">Návrháře nastavuje tuto hodnotu, když je ovládací prvek přidán do formuláře.</span><span class="sxs-lookup"><span data-stu-id="10821-115">The designer sets this value when the control is added to the form.</span></span>  
  
## <a name="accessibledefaultactiondescription-property"></a><span data-ttu-id="10821-116">Vlastnost AccessibleDefaultActionDescription</span><span class="sxs-lookup"><span data-stu-id="10821-116">AccessibleDefaultActionDescription Property</span></span>  
 <span data-ttu-id="10821-117">Tento řetězec popisuje akci ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="10821-117">This string describes the action of the control.</span></span> <span data-ttu-id="10821-118">Se nezobrazí v okně vlastností a lze nastavit pouze v kódu.</span><span class="sxs-lookup"><span data-stu-id="10821-118">It does not appear in the Properties window and may only be set in code.</span></span> <span data-ttu-id="10821-119">Tato vlastnost pro ovládací prvek tlačítko nastaví v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="10821-119">The following example sets this property for a button control:</span></span>  
  
```  
' Visual Basic  
Button1.AccessibleDefaultActionDescription = _  
   "Closes the application."  
  
// C#  
Button1.AccessibleDefaultActionDescription =   
   "Closes the application.";  
  
// C++  
button1->AccessibleDefaultActionDescription =  
   "Closes the application.";  
```  
  
## <a name="accessibledescription-property"></a><span data-ttu-id="10821-120">Vlastnost AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="10821-120">AccessibleDescription Property</span></span>  
 <span data-ttu-id="10821-121">Tento řetězec popisuje ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="10821-121">This string describes the control.</span></span> <span data-ttu-id="10821-122">Může být nastaveno v okně Vlastnosti, nebo v kódu následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="10821-122">It may be set in the Properties window, or in code as follows:</span></span>  
  
```  
' Visual Basic  
Button1.AccessibleDescription = "A button with text 'Exit'."  
  
// C#  
Button1.AccessibleDescription = "A button with text 'Exit'";  
  
// C++  
button1->AccessibleDescription = "A button with text 'Exit'";  
```  
  
## <a name="accessiblename-property"></a><span data-ttu-id="10821-123">Vlastnost AccessibleName</span><span class="sxs-lookup"><span data-stu-id="10821-123">AccessibleName Property</span></span>  
 <span data-ttu-id="10821-124">Toto je název ovládacího prvku oznamovány usnadnění.</span><span class="sxs-lookup"><span data-stu-id="10821-124">This is the name of a control reported to accessibility aids.</span></span> <span data-ttu-id="10821-125">Může být nastaveno v okně Vlastnosti, nebo v kódu následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="10821-125">It may be set in the Properties window, or in code as follows:</span></span>  
  
```  
' Visual Basic  
Button1.AccessibleName = "Order"  
  
// C#  
Button1.AccessibleName = "Order";  
  
// C++  
button1->AccessibleName = "Order";  
```  
  
## <a name="accessiblerole-property"></a><span data-ttu-id="10821-126">Vlastnost AccessibleRole</span><span class="sxs-lookup"><span data-stu-id="10821-126">AccessibleRole Property</span></span>  
 <span data-ttu-id="10821-127">Tato vlastnost, která obsahuje <xref:System.Windows.Forms.AccessibleRole> výčtu, popisuje roli uživatele rozhraní ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="10821-127">This property, which contains an <xref:System.Windows.Forms.AccessibleRole> enumeration, describes the user interface role of the control.</span></span> <span data-ttu-id="10821-128">Nový ovládací prvek je nastavena hodnota `Default`.</span><span class="sxs-lookup"><span data-stu-id="10821-128">A new control has the value set to `Default`.</span></span> <span data-ttu-id="10821-129">To by znamenají, že ve výchozím nastavení, **tlačítko** řízení funguje jako **tlačítko**.</span><span class="sxs-lookup"><span data-stu-id="10821-129">This would mean that by default, a **Button** control acts as a **Button**.</span></span> <span data-ttu-id="10821-130">Chcete resetovat tuto vlastnost, pokud se ovládací prvek obsahuje jiné role.</span><span class="sxs-lookup"><span data-stu-id="10821-130">You may want to reset this property if a control has another role.</span></span> <span data-ttu-id="10821-131">Například je možné, že používáte **PictureBox** řízení jako **grafu**, a může být vhodné usnadnění nahlásit roli jako **grafu**, ne jako **PictureBox** .</span><span class="sxs-lookup"><span data-stu-id="10821-131">For example, you may be using a **PictureBox** control as a **Chart**, and you may want accessibility aids to report the role as a **Chart**, not as a **PictureBox**.</span></span> <span data-ttu-id="10821-132">Můžete také zadat tato vlastnost pro vlastní ovládací prvky, kterou jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="10821-132">You may also want to specify this property for custom controls you have developed.</span></span> <span data-ttu-id="10821-133">Tuto vlastnost lze nastavit v okně Vlastnosti, nebo v kódu následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="10821-133">This property may be set in the Properties window, or in code as follows:</span></span>  
  
```  
' Visual Basic  
PictureBox1.AccessibleRole = AccessibleRole.Chart  
  
// C#  
PictureBox1.AccessibleRole = AccessibleRole.Chart;  
  
// C++  
pictureBox1->AccessibleRole = AccessibleRole::Chart;  
```  
  
## <a name="see-also"></a><span data-ttu-id="10821-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="10821-134">See Also</span></span>  
 <xref:System.Windows.Forms.AccessibleObject>  
 <xref:System.Windows.Forms.Control.AccessibilityObject%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.AccessibleDefaultActionDescription%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.AccessibleDescription%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.AccessibleName%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.AccessibleRole%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.AccessibleRole>
