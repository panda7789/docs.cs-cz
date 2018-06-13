---
title: 'Postupy: Vytvoření ovládacího prvku Windows Forms zobrazujícího průběh'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], progress tracking
- controls [Windows Forms], creating
- progress [Windows Forms], reporting [Windows Forms]
- FlashTrackBar custom control
ms.assetid: 24c5a2e3-058c-4b8d-a217-c06e6a130c2f
ms.openlocfilehash: 5773181b8883f0f94ff451808c8c97ce3407970e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531427"
---
# <a name="how-to-create-a-windows-forms-control-that-shows-progress"></a><span data-ttu-id="48504-102">Postupy: Vytvoření ovládacího prvku Windows Forms zobrazujícího průběh</span><span class="sxs-lookup"><span data-stu-id="48504-102">How to: Create a Windows Forms Control That Shows Progress</span></span>
<span data-ttu-id="48504-103">Následující příklad kódu ukazuje vlastního ovládacího prvku názvem `FlashTrackBar` který lze použít na úroveň nebo průběh aplikace se uživateli zobrazí.</span><span class="sxs-lookup"><span data-stu-id="48504-103">The following code example shows a custom control called `FlashTrackBar` that can be used to show the user the level or the progress of an application.</span></span> <span data-ttu-id="48504-104">Přechod na základě vizuálně představují průběh.</span><span class="sxs-lookup"><span data-stu-id="48504-104">It uses a gradient to visually represent progress.</span></span>  
  
 <span data-ttu-id="48504-105">`FlashTrackBar` Řízení znázorňuje následující koncepty:</span><span class="sxs-lookup"><span data-stu-id="48504-105">The `FlashTrackBar` control illustrates the following concepts:</span></span>  
  
-   <span data-ttu-id="48504-106">Definování vlastní vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="48504-106">Defining custom properties.</span></span>  
  
-   <span data-ttu-id="48504-107">Definování vlastních událostí.</span><span class="sxs-lookup"><span data-stu-id="48504-107">Defining custom events.</span></span> <span data-ttu-id="48504-108">(`FlashTrackBar` definuje `ValueChanged` události.)</span><span class="sxs-lookup"><span data-stu-id="48504-108">(`FlashTrackBar` defines the `ValueChanged` event.)</span></span>  
  
-   <span data-ttu-id="48504-109">Přepsání <xref:System.Windows.Forms.Control.OnPaint%2A> metody můžete zajistit logiku k vykreslení ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="48504-109">Overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method to provide logic to draw the control.</span></span>  
  
-   <span data-ttu-id="48504-110">Computing oblasti k dispozici pro vykreslení ovládacího prvku pomocí jeho <xref:System.Windows.Forms.Control.ClientRectangle%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="48504-110">Computing the area available for drawing the control by using its <xref:System.Windows.Forms.Control.ClientRectangle%2A> property.</span></span> <span data-ttu-id="48504-111">`FlashTrackBar` k tomu jeho `OptimizedInvalidate` metoda.</span><span class="sxs-lookup"><span data-stu-id="48504-111">`FlashTrackBar` does this in its `OptimizedInvalidate` method.</span></span>  
  
-   <span data-ttu-id="48504-112">Implementace serializace nebo stálosti pro vlastnost, když se změní v Návrháři formulářů.</span><span class="sxs-lookup"><span data-stu-id="48504-112">Implementing serialization or persistence for a property when it is changed in the Windows Forms Designer.</span></span> <span data-ttu-id="48504-113">`FlashTrackBar` definuje `ShouldSerializeStartColor` a `ShouldSerializeEndColor` metody pro serializaci jeho `StartColor` a `EndColor` vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="48504-113">`FlashTrackBar` defines the `ShouldSerializeStartColor` and `ShouldSerializeEndColor` methods for serializing its `StartColor` and `EndColor` properties.</span></span>  
  
 <span data-ttu-id="48504-114">V následující tabulce jsou uvedeny vlastní vlastnosti definované `FlashTrackBar`.</span><span class="sxs-lookup"><span data-stu-id="48504-114">The following table shows the custom properties defined by `FlashTrackBar`.</span></span>  
  
|<span data-ttu-id="48504-115">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="48504-115">Property</span></span>|<span data-ttu-id="48504-116">Popis</span><span class="sxs-lookup"><span data-stu-id="48504-116">Description</span></span>|  
|--------------|-----------------|  
|`AllowUserEdit`|<span data-ttu-id="48504-117">Určuje, jestli uživatel může změnit hodnotu panelu flash sledovat kliknutím a přetažením.</span><span class="sxs-lookup"><span data-stu-id="48504-117">Indicates whether the user can change the value of the flash track bar by clicking and dragging it.</span></span>|  
|`EndColor`|<span data-ttu-id="48504-118">Určuje koncovou barvu panelu sledovat.</span><span class="sxs-lookup"><span data-stu-id="48504-118">Specifies the ending color of the track bar.</span></span>|  
|`DarkenBy`|<span data-ttu-id="48504-119">Určuje, kolik ztmavení pozadí s ohledem na popředí přechodu.</span><span class="sxs-lookup"><span data-stu-id="48504-119">Specifies how much to darken the background with respect to the foreground gradient.</span></span>|  
|`Max`|<span data-ttu-id="48504-120">Určuje maximální hodnotu panelu sledovat.</span><span class="sxs-lookup"><span data-stu-id="48504-120">Specifies the maximum value of the track bar.</span></span>|  
|`Min`|<span data-ttu-id="48504-121">Určuje minimální hodnotu panelu sledovat.</span><span class="sxs-lookup"><span data-stu-id="48504-121">Specifies the minimum value of the track bar.</span></span>|  
|`StartColor`|<span data-ttu-id="48504-122">Určuje počáteční barvu barevného přechodu.</span><span class="sxs-lookup"><span data-stu-id="48504-122">Specifies the starting color of the gradient.</span></span>|  
|`ShowPercentage`|<span data-ttu-id="48504-123">Označuje, zda se má zobrazit procento přechodu.</span><span class="sxs-lookup"><span data-stu-id="48504-123">Indicates whether to display a percentage over the gradient.</span></span>|  
|`ShowValue`|<span data-ttu-id="48504-124">Označuje, zda se má zobrazit aktuální hodnota přechodu.</span><span class="sxs-lookup"><span data-stu-id="48504-124">Indicates whether to display the current value over the gradient.</span></span>|  
|`ShowGradient`|<span data-ttu-id="48504-125">Udává, zda panelu sledování by měla zobrazit přechod barev, zobrazuje aktuální hodnotu.</span><span class="sxs-lookup"><span data-stu-id="48504-125">Indicates whether the track bar should display a color gradient showing the current value.</span></span>|  
|-   `Value`|<span data-ttu-id="48504-126">Určuje aktuální hodnota panelu sledovat.</span><span class="sxs-lookup"><span data-stu-id="48504-126">Specifies the current value of the track bar.</span></span>|  
  
 <span data-ttu-id="48504-127">V následující tabulce jsou uvedeny další členy, které jsou definované `FlashTrackBar:` událost změny vlastnosti a metody, která vyvolává událost.</span><span class="sxs-lookup"><span data-stu-id="48504-127">The following table shows additional members defined by `FlashTrackBar:` the property-changed event and the method that raises the event.</span></span>  
  
|<span data-ttu-id="48504-128">Člen</span><span class="sxs-lookup"><span data-stu-id="48504-128">Member</span></span>|<span data-ttu-id="48504-129">Popis</span><span class="sxs-lookup"><span data-stu-id="48504-129">Description</span></span>|  
|------------|-----------------|  
|`ValueChanged`|<span data-ttu-id="48504-130">Událost, která se vyvolá, když `Value` vlastnost sledování změn panelu.</span><span class="sxs-lookup"><span data-stu-id="48504-130">The event that is raised when the `Value` property of the track bar changes.</span></span>|  
|`OnValueChanged`|<span data-ttu-id="48504-131">Metoda, která vyvolává `ValueChanged` událostí.</span><span class="sxs-lookup"><span data-stu-id="48504-131">The method that raises the `ValueChanged` event.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="48504-132">`FlashTrackBar` používá <xref:System.EventArgs> třídu pro data události a <xref:System.EventHandler> pro delegát události.</span><span class="sxs-lookup"><span data-stu-id="48504-132">`FlashTrackBar` uses the <xref:System.EventArgs> class for event data and <xref:System.EventHandler> for the event delegate.</span></span>  
  
 <span data-ttu-id="48504-133">Pro zpracování odpovídající *EventName* události, `FlashTrackBar` přepíše následující metody, které dědí z <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="48504-133">To handle the corresponding *EventName* events, `FlashTrackBar` overrides the following methods that it inherits from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:</span></span>  
  
-   <xref:System.Windows.Forms.Control.OnPaint%2A>  
  
-   <xref:System.Windows.Forms.Control.OnMouseDown%2A>  
  
-   <xref:System.Windows.Forms.Control.OnMouseMove%2A>  
  
-   <xref:System.Windows.Forms.Control.OnMouseUp%2A>  
  
-   <xref:System.Windows.Forms.Control.OnResize%2A>  
  
 <span data-ttu-id="48504-134">Zpracování událostí odpovídající vlastnost změnit `FlashTrackBar` přepíše následující metody, které dědí z <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="48504-134">To handle the corresponding property-changed events, `FlashTrackBar` overrides the following methods that it inherits from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:</span></span>  
  
-   <xref:System.Windows.Forms.Control.OnBackColorChanged%2A>  
  
-   <xref:System.Windows.Forms.Control.OnBackgroundImageChanged%2A>  
  
-   <xref:System.Windows.Forms.Control.OnTextChanged%2A>  
  
## <a name="example"></a><span data-ttu-id="48504-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="48504-135">Example</span></span>  
 <span data-ttu-id="48504-136">`FlashTrackBar` Řízení definuje dvě editory typ uživatelského rozhraní, `FlashTrackBarValueEditor` a `FlashTrackBarDarkenByEditor`, které jsou uvedené v následující příklady kódu.</span><span class="sxs-lookup"><span data-stu-id="48504-136">The `FlashTrackBar` control defines two UI type editors, `FlashTrackBarValueEditor` and `FlashTrackBarDarkenByEditor`, which are shown in the following code listings.</span></span> <span data-ttu-id="48504-137">`HostApp` Třídy používá `FlashTrackBar` ovládacího prvku ve formuláři Windows.</span><span class="sxs-lookup"><span data-stu-id="48504-137">The `HostApp` class uses the `FlashTrackBar` control on a Windows Form.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#1)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#1)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarDarkenByEditor.cs#10)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarDarkenByEditor.vb#10)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarValueEditor.cs#20)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarValueEditor.vb#20)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/HostApp.cs#30)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/HostApp.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="48504-138">Viz také</span><span class="sxs-lookup"><span data-stu-id="48504-138">See Also</span></span>  
 [<span data-ttu-id="48504-139">Rozšíření podpory návrhu</span><span class="sxs-lookup"><span data-stu-id="48504-139">Extending Design-Time Support</span></span>](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)  
 [<span data-ttu-id="48504-140">Základní informace o vývoji ovládacích prvků Windows Forms</span><span class="sxs-lookup"><span data-stu-id="48504-140">Windows Forms Control Development Basics</span></span>](../../../../docs/framework/winforms/controls/windows-forms-control-development-basics.md)
