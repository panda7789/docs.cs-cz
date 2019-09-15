---
title: Poskytování informací o usnadnění pro ovládací prvky ve formuláři Windows
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, accessibility
- controls [Windows Forms], accessibility
- accessibility [Windows Forms], Windows Forms controls
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 887dee6f-5059-4d57-957d-7c6fcd4acb10
ms.openlocfilehash: 791944bd9e8f5520a571e6fb415d69022aa0bead
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991716"
---
# <a name="providing-accessibility-information-for-controls-on-a-windows-form"></a><span data-ttu-id="faf3f-102">Poskytování informací o usnadnění pro ovládací prvky ve formuláři Windows</span><span class="sxs-lookup"><span data-stu-id="faf3f-102">Providing Accessibility Information for Controls on a Windows Form</span></span>
<span data-ttu-id="faf3f-103">Pomůcky pro usnadnění přístupu jsou specializované programy a zařízení, které lidem s postižením můžou efektivněji používat počítače.</span><span class="sxs-lookup"><span data-stu-id="faf3f-103">Accessibility aids are specialized programs and devices that help people with disabilities use computers more effectively.</span></span> <span data-ttu-id="faf3f-104">Mezi příklady patří čtečky obrazovky pro lidi, kteří jsou nevidomí a nástroje pro zadávání hlasu pro lidi, kteří poskytují ústní příkazy namísto použití myši nebo klávesnice.</span><span class="sxs-lookup"><span data-stu-id="faf3f-104">Examples include screen readers for people who are blind and voice input utilities for people who provide verbal commands instead of using the mouse or keyboard.</span></span> <span data-ttu-id="faf3f-105">Tato pomůcka pro usnadnění práce spolupracuje s vlastnostmi přístupnosti vystavenými ovládacími prvky model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="faf3f-105">These accessibility aids interact with the accessibility properties exposed by Windows Forms controls.</span></span> <span data-ttu-id="faf3f-106">Tyto vlastnosti jsou:</span><span class="sxs-lookup"><span data-stu-id="faf3f-106">These properties are:</span></span>  
  
- <span data-ttu-id="faf3f-107">**AccessibilityObject**</span><span class="sxs-lookup"><span data-stu-id="faf3f-107">**AccessibilityObject**</span></span>  
  
- <span data-ttu-id="faf3f-108">**AccessibleDefaultActionDescription**</span><span class="sxs-lookup"><span data-stu-id="faf3f-108">**AccessibleDefaultActionDescription**</span></span>  
  
- <span data-ttu-id="faf3f-109">**AccessibleDescription**</span><span class="sxs-lookup"><span data-stu-id="faf3f-109">**AccessibleDescription**</span></span>  
  
- <span data-ttu-id="faf3f-110">**Přístupný**</span><span class="sxs-lookup"><span data-stu-id="faf3f-110">**AccessibleName**</span></span>  
  
- <span data-ttu-id="faf3f-111">**AccessibleRole**</span><span class="sxs-lookup"><span data-stu-id="faf3f-111">**AccessibleRole**</span></span>  
  
## <a name="accessibilityobject-property"></a><span data-ttu-id="faf3f-112">Vlastnost AccessibilityObject</span><span class="sxs-lookup"><span data-stu-id="faf3f-112">AccessibilityObject Property</span></span>  
 <span data-ttu-id="faf3f-113">Tato vlastnost jen pro čtení obsahuje <xref:System.Windows.Forms.AccessibleObject> instanci.</span><span class="sxs-lookup"><span data-stu-id="faf3f-113">This read-only property contains an <xref:System.Windows.Forms.AccessibleObject> instance.</span></span> <span data-ttu-id="faf3f-114">**Třída AccessibleObject** implementuje <xref:Accessibility.IAccessible> rozhraní, které poskytuje informace o popisu ovládacího prvku, umístění obrazovky, navigačních schopnostech a hodnotě.</span><span class="sxs-lookup"><span data-stu-id="faf3f-114">The **AccessibleObject** implements the <xref:Accessibility.IAccessible> interface, which provides information about the control's description, screen location, navigational abilities, and value.</span></span> <span data-ttu-id="faf3f-115">Návrhář tuto hodnotu nastaví při přidání ovládacího prvku do formuláře.</span><span class="sxs-lookup"><span data-stu-id="faf3f-115">The designer sets this value when the control is added to the form.</span></span>  
  
## <a name="accessibledefaultactiondescription-property"></a><span data-ttu-id="faf3f-116">Vlastnost AccessibleDefaultActionDescription</span><span class="sxs-lookup"><span data-stu-id="faf3f-116">AccessibleDefaultActionDescription Property</span></span>  
 <span data-ttu-id="faf3f-117">Tento řetězec popisuje akci ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="faf3f-117">This string describes the action of the control.</span></span> <span data-ttu-id="faf3f-118">Nezobrazuje se v okno Vlastnosti a lze ji nastavit pouze v kódu.</span><span class="sxs-lookup"><span data-stu-id="faf3f-118">It does not appear in the Properties window and may only be set in code.</span></span> <span data-ttu-id="faf3f-119">Následující příklad nastaví tuto vlastnost pro ovládací prvek tlačítko:</span><span class="sxs-lookup"><span data-stu-id="faf3f-119">The following example sets this property for a button control:</span></span>  
  
```vb  
Button1.AccessibleDefaultActionDescription = _  
   "Closes the application."  
``` 

```csharp  
Button1.AccessibleDefaultActionDescription =   
   "Closes the application.";  
```

```cpp  
button1->AccessibleDefaultActionDescription =  
   "Closes the application.";  
```  
  
## <a name="accessibledescription-property"></a><span data-ttu-id="faf3f-120">Vlastnost AccessibleDescription</span><span class="sxs-lookup"><span data-stu-id="faf3f-120">AccessibleDescription Property</span></span>  
 <span data-ttu-id="faf3f-121">Tento řetězec popisuje ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="faf3f-121">This string describes the control.</span></span> <span data-ttu-id="faf3f-122">Může být nastavena v okno Vlastnosti nebo v kódu následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="faf3f-122">It may be set in the Properties window, or in code as follows:</span></span>  
  
```vb  
Button1.AccessibleDescription = "A button with text 'Exit'."  
```

```csharp  
Button1.AccessibleDescription = "A button with text 'Exit'";  
```

```cpp  
button1->AccessibleDescription = "A button with text 'Exit'";  
```  
  
## <a name="accessiblename-property"></a><span data-ttu-id="faf3f-123">Vlastnost s usnadněním</span><span class="sxs-lookup"><span data-stu-id="faf3f-123">AccessibleName Property</span></span>  
 <span data-ttu-id="faf3f-124">Toto je název ovládacího prvku nahlášený pro pomůcky přístupnosti.</span><span class="sxs-lookup"><span data-stu-id="faf3f-124">This is the name of a control reported to accessibility aids.</span></span> <span data-ttu-id="faf3f-125">Může být nastavena v okno Vlastnosti nebo v kódu následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="faf3f-125">It may be set in the Properties window, or in code as follows:</span></span>  
  
```vb  
Button1.AccessibleName = "Order"  
```

```csharp  
Button1.AccessibleName = "Order";  
```

```cpp  
button1->AccessibleName = "Order";  
```  
  
## <a name="accessiblerole-property"></a><span data-ttu-id="faf3f-126">Vlastnost AccessibleRole</span><span class="sxs-lookup"><span data-stu-id="faf3f-126">AccessibleRole Property</span></span>  
 <span data-ttu-id="faf3f-127">Tato vlastnost, která obsahuje <xref:System.Windows.Forms.AccessibleRole> výčet, popisuje roli uživatelského rozhraní ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="faf3f-127">This property, which contains an <xref:System.Windows.Forms.AccessibleRole> enumeration, describes the user interface role of the control.</span></span> <span data-ttu-id="faf3f-128">Nový ovládací prvek má hodnotu nastavenou na `Default`.</span><span class="sxs-lookup"><span data-stu-id="faf3f-128">A new control has the value set to `Default`.</span></span> <span data-ttu-id="faf3f-129">To by znamenalo, že ve výchozím nastavení se ovládací prvek **tlačítko** chová jako **tlačítko**.</span><span class="sxs-lookup"><span data-stu-id="faf3f-129">This would mean that by default, a **Button** control acts as a **Button**.</span></span> <span data-ttu-id="faf3f-130">Tuto vlastnost můžete chtít resetovat, pokud má ovládací prvek jinou roli.</span><span class="sxs-lookup"><span data-stu-id="faf3f-130">You may want to reset this property if a control has another role.</span></span> <span data-ttu-id="faf3f-131">Například můžete použít ovládací prvek **PictureBox** jako **graf**a můžete chtít, aby pomůcky usnadnění nahlásily roli jako **graf**, nikoli jako **PictureBox**.</span><span class="sxs-lookup"><span data-stu-id="faf3f-131">For example, you may be using a **PictureBox** control as a **Chart**, and you may want accessibility aids to report the role as a **Chart**, not as a **PictureBox**.</span></span> <span data-ttu-id="faf3f-132">Tuto vlastnost můžete také použít pro vlastní ovládací prvky, které jste vyvinuli.</span><span class="sxs-lookup"><span data-stu-id="faf3f-132">You may also want to specify this property for custom controls you have developed.</span></span> <span data-ttu-id="faf3f-133">Tato vlastnost může být nastavena v okno Vlastnosti nebo v kódu následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="faf3f-133">This property may be set in the Properties window, or in code as follows:</span></span>  
  
```vb 
PictureBox1.AccessibleRole = AccessibleRole.Chart  
```

```csharp  
PictureBox1.AccessibleRole = AccessibleRole.Chart;  
```

```cpp  
pictureBox1->AccessibleRole = AccessibleRole::Chart;  
```  
  
## <a name="see-also"></a><span data-ttu-id="faf3f-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="faf3f-134">See also</span></span>

- <xref:System.Windows.Forms.AccessibleObject>
- <xref:System.Windows.Forms.Control.AccessibilityObject%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleDefaultActionDescription%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleDescription%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleName%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.AccessibleRole%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.AccessibleRole>
