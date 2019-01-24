---
title: Poskytování informací o usnadnění pro ovládací prvky ve formuláři Windows
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, accessibility
- controls [Windows Forms], accessibility
- accessibility [Windows Forms], Windows Forms controls
ms.assetid: 887dee6f-5059-4d57-957d-7c6fcd4acb10
ms.openlocfilehash: 976aff327a5212c181d455bab1cdc84f98d75a2a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54540910"
---
# <a name="providing-accessibility-information-for-controls-on-a-windows-form"></a><span data-ttu-id="12422-102">Poskytování informací o usnadnění pro ovládací prvky ve formuláři Windows</span><span class="sxs-lookup"><span data-stu-id="12422-102">Providing Accessibility Information for Controls on a Windows Form</span></span>
<span data-ttu-id="12422-103">Usnadnění jsou specializované programy a zařízení, která pomůže uživatelům s postižením používání počítačů efektivněji.</span><span class="sxs-lookup"><span data-stu-id="12422-103">Accessibility aids are specialized programs and devices that help people with disabilities use computers more effectively.</span></span> <span data-ttu-id="12422-104">Mezi příklady patří čtečky obrazovky pro uživatele, kteří jsou blind a způsobu vyjadřování vstupní nástroje pro uživatele, kteří poskytují slovní příkazy místo pomocí myši nebo klávesnice.</span><span class="sxs-lookup"><span data-stu-id="12422-104">Examples include screen readers for people who are blind and voice input utilities for people who provide verbal commands instead of using the mouse or keyboard.</span></span> <span data-ttu-id="12422-105">Tyto usnadnění interakci s usnadnění vlastností vystavovaných třídami ovládacích prvků Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="12422-105">These accessibility aids interact with the accessibility properties exposed by Windows Forms controls.</span></span> <span data-ttu-id="12422-106">Tyto vlastnosti jsou:</span><span class="sxs-lookup"><span data-stu-id="12422-106">These properties are:</span></span>  
  
-   <span data-ttu-id="12422-107">**AccessibilityObject**</span><span class="sxs-lookup"><span data-stu-id="12422-107">**AccessibilityObject**</span></span>  
  
-   <span data-ttu-id="12422-108">**AccessibleDefaultActionDescription**</span><span class="sxs-lookup"><span data-stu-id="12422-108">**AccessibleDefaultActionDescription**</span></span>  
  
-   <span data-ttu-id="12422-109">**AccessibleDescription**</span><span class="sxs-lookup"><span data-stu-id="12422-109">**AccessibleDescription**</span></span>  
  
-   <span data-ttu-id="12422-110">**AccessibleName**</span><span class="sxs-lookup"><span data-stu-id="12422-110">**AccessibleName**</span></span>  
  
-   <span data-ttu-id="12422-111">**AccessibleRole**</span><span class="sxs-lookup"><span data-stu-id="12422-111">**AccessibleRole**</span></span>  
  
## <a name="accessibilityobject-property"></a><span data-ttu-id="12422-112">Vlastnost AccessibilityObject</span><span class="sxs-lookup"><span data-stu-id="12422-112">AccessibilityObject Property</span></span>  
 <span data-ttu-id="12422-113">Tato vlastnost jen pro čtení obsahuje <xref:System.Windows.Forms.AccessibleObject> instance.</span><span class="sxs-lookup"><span data-stu-id="12422-113">This read-only property contains an <xref:System.Windows.Forms.AccessibleObject> instance.</span></span> <span data-ttu-id="12422-114">**Třída AccessibleObject** implementuje <xref:Accessibility.IAccessible> rozhraní, který poskytuje informace o popis ovládacího prvku, umístění na obrazovce, navigační schopnosti a hodnotu.</span><span class="sxs-lookup"><span data-stu-id="12422-114">The **AccessibleObject** implements the <xref:Accessibility.IAccessible> interface, which provides information about the control's description, screen location, navigational abilities, and value.</span></span> <span data-ttu-id="12422-115">Návrhář nastaví tuto hodnotu, pokud ovládací prvek je přidán do formuláře.</span><span class="sxs-lookup"><span data-stu-id="12422-115">The designer sets this value when the control is added to the form.</span></span>  
  
## <a name="accessibledefaultactiondescription-property"></a><span data-ttu-id="12422-116">Vlastnost AccessibleDefaultActionDescription</span><span class="sxs-lookup"><span data-stu-id="12422-116">AccessibleDefaultActionDescription Property</span></span>  
 <span data-ttu-id="12422-117">Tento řetězec popisuje akci ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="12422-117">This string describes the action of the control.</span></span> <span data-ttu-id="12422-118">V okně Vlastnosti se nezobrazí a může být nastavena pouze v kódu.</span><span class="sxs-lookup"><span data-stu-id="12422-118">It does not appear in the Properties window and may only be set in code.</span></span> <span data-ttu-id="12422-119">Následující příklad nastaví tuto vlastnost pro ovládací prvek tlačítka:</span><span class="sxs-lookup"><span data-stu-id="12422-119">The following example sets this property for a button control:</span></span>  
  
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
  
## <a name="accessibledescription-property"></a><span data-ttu-id="12422-120">Vlastnost AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="12422-120">AccessibleDescription Property</span></span>  
 <span data-ttu-id="12422-121">Tento řetězec popisuje ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="12422-121">This string describes the control.</span></span> <span data-ttu-id="12422-122">To může být nastavena v okně Vlastnosti, nebo v kódu následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="12422-122">It may be set in the Properties window, or in code as follows:</span></span>  
  
```  
' Visual Basic  
Button1.AccessibleDescription = "A button with text 'Exit'."  
  
// C#  
Button1.AccessibleDescription = "A button with text 'Exit'";  
  
// C++  
button1->AccessibleDescription = "A button with text 'Exit'";  
```  
  
## <a name="accessiblename-property"></a><span data-ttu-id="12422-123">Vlastnost AccessibleName</span><span class="sxs-lookup"><span data-stu-id="12422-123">AccessibleName Property</span></span>  
 <span data-ttu-id="12422-124">Toto je název ovládacího prvku ohlášených pro usnadnění.</span><span class="sxs-lookup"><span data-stu-id="12422-124">This is the name of a control reported to accessibility aids.</span></span> <span data-ttu-id="12422-125">To může být nastavena v okně Vlastnosti, nebo v kódu následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="12422-125">It may be set in the Properties window, or in code as follows:</span></span>  
  
```  
' Visual Basic  
Button1.AccessibleName = "Order"  
  
// C#  
Button1.AccessibleName = "Order";  
  
// C++  
button1->AccessibleName = "Order";  
```  
  
## <a name="accessiblerole-property"></a><span data-ttu-id="12422-126">Vlastnost AccessibleRole</span><span class="sxs-lookup"><span data-stu-id="12422-126">AccessibleRole Property</span></span>  
 <span data-ttu-id="12422-127">Tuto vlastnost, která obsahuje <xref:System.Windows.Forms.AccessibleRole> výčet, popisuje role uživatele rozhraní ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="12422-127">This property, which contains an <xref:System.Windows.Forms.AccessibleRole> enumeration, describes the user interface role of the control.</span></span> <span data-ttu-id="12422-128">Nový ovládací prvek je nastavena hodnota `Default`.</span><span class="sxs-lookup"><span data-stu-id="12422-128">A new control has the value set to `Default`.</span></span> <span data-ttu-id="12422-129">To znamená, že ve výchozím nastavení, **tlačítko** ovládací prvek funguje jako **tlačítko**.</span><span class="sxs-lookup"><span data-stu-id="12422-129">This would mean that by default, a **Button** control acts as a **Button**.</span></span> <span data-ttu-id="12422-130">Chcete resetovat tuto vlastnost, pokud ovládací prvek obsahuje jiné role.</span><span class="sxs-lookup"><span data-stu-id="12422-130">You may want to reset this property if a control has another role.</span></span> <span data-ttu-id="12422-131">Například využíváte **PictureBox** ovládací prvek jako **grafu**, a může být vhodné usnadnění hlášení role jako **grafu**, ne jako **ovládací prvek PictureBox** .</span><span class="sxs-lookup"><span data-stu-id="12422-131">For example, you may be using a **PictureBox** control as a **Chart**, and you may want accessibility aids to report the role as a **Chart**, not as a **PictureBox**.</span></span> <span data-ttu-id="12422-132">Můžete také určit tuto vlastnost u vlastních ovládacích prvků, které jste vytvořili.</span><span class="sxs-lookup"><span data-stu-id="12422-132">You may also want to specify this property for custom controls you have developed.</span></span> <span data-ttu-id="12422-133">Tato vlastnost může být nastavena v okně Vlastnosti, nebo v kódu následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="12422-133">This property may be set in the Properties window, or in code as follows:</span></span>  
  
```  
' Visual Basic  
PictureBox1.AccessibleRole = AccessibleRole.Chart  
  
// C#  
PictureBox1.AccessibleRole = AccessibleRole.Chart;  
  
// C++  
pictureBox1->AccessibleRole = AccessibleRole::Chart;  
```  
  
## <a name="see-also"></a><span data-ttu-id="12422-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="12422-134">See also</span></span>
- <xref:System.Windows.Forms.AccessibleObject>
- <xref:System.Windows.Forms.Control.AccessibilityObject%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleDefaultActionDescription%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleDescription%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleName%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleRole%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.AccessibleRole>
