---
title: Vytvoří ovládací prvek, který zobrazuje průběh.
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
ms.openlocfilehash: 9d2cf353ba2309380221bb51733baaca1b81a5d5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731187"
---
# <a name="how-to-create-a-windows-forms-control-that-shows-progress"></a><span data-ttu-id="2f303-102">Postupy: Vytvoření ovládacího prvku Windows Forms zobrazujícího průběh</span><span class="sxs-lookup"><span data-stu-id="2f303-102">How to: Create a Windows Forms Control That Shows Progress</span></span>
<span data-ttu-id="2f303-103">Následující příklad kódu ukazuje vlastní ovládací prvek s názvem `FlashTrackBar`, který lze použít k zobrazení úrovně nebo průběhu aplikace na úrovni uživatele.</span><span class="sxs-lookup"><span data-stu-id="2f303-103">The following code example shows a custom control called `FlashTrackBar` that can be used to show the user the level or the progress of an application.</span></span> <span data-ttu-id="2f303-104">Pomocí přechodu vizuálně reprezentuje průběh.</span><span class="sxs-lookup"><span data-stu-id="2f303-104">It uses a gradient to visually represent progress.</span></span>  
  
 <span data-ttu-id="2f303-105">Ovládací prvek `FlashTrackBar` ilustruje následující koncepty:</span><span class="sxs-lookup"><span data-stu-id="2f303-105">The `FlashTrackBar` control illustrates the following concepts:</span></span>  
  
- <span data-ttu-id="2f303-106">Definování vlastních vlastností.</span><span class="sxs-lookup"><span data-stu-id="2f303-106">Defining custom properties.</span></span>  
  
- <span data-ttu-id="2f303-107">Definování vlastních událostí.</span><span class="sxs-lookup"><span data-stu-id="2f303-107">Defining custom events.</span></span> <span data-ttu-id="2f303-108">(`FlashTrackBar` definuje událost `ValueChanged`.)</span><span class="sxs-lookup"><span data-stu-id="2f303-108">(`FlashTrackBar` defines the `ValueChanged` event.)</span></span>  
  
- <span data-ttu-id="2f303-109">Přepsání metody <xref:System.Windows.Forms.Control.OnPaint%2A> k poskytnutí logiky pro vykreslení ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="2f303-109">Overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method to provide logic to draw the control.</span></span>  
  
- <span data-ttu-id="2f303-110">Výpočet oblasti, která je k dispozici pro vykreslení ovládacího prvku pomocí vlastnosti <xref:System.Windows.Forms.Control.ClientRectangle%2A>.</span><span class="sxs-lookup"><span data-stu-id="2f303-110">Computing the area available for drawing the control by using its <xref:System.Windows.Forms.Control.ClientRectangle%2A> property.</span></span> <span data-ttu-id="2f303-111">`FlashTrackBar` to dělá v metodě `OptimizedInvalidate`.</span><span class="sxs-lookup"><span data-stu-id="2f303-111">`FlashTrackBar` does this in its `OptimizedInvalidate` method.</span></span>  
  
- <span data-ttu-id="2f303-112">Implementace serializace nebo trvalosti vlastnosti při změně v Návrhář formulářů.</span><span class="sxs-lookup"><span data-stu-id="2f303-112">Implementing serialization or persistence for a property when it is changed in the Windows Forms Designer.</span></span> <span data-ttu-id="2f303-113">`FlashTrackBar` definuje metody `ShouldSerializeStartColor` a `ShouldSerializeEndColor` pro serializaci vlastností `StartColor` a `EndColor`.</span><span class="sxs-lookup"><span data-stu-id="2f303-113">`FlashTrackBar` defines the `ShouldSerializeStartColor` and `ShouldSerializeEndColor` methods for serializing its `StartColor` and `EndColor` properties.</span></span>  
  
 <span data-ttu-id="2f303-114">V následující tabulce jsou uvedeny vlastní vlastnosti definované `FlashTrackBar`.</span><span class="sxs-lookup"><span data-stu-id="2f303-114">The following table shows the custom properties defined by `FlashTrackBar`.</span></span>  
  
|<span data-ttu-id="2f303-115">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="2f303-115">Property</span></span>|<span data-ttu-id="2f303-116">Popis</span><span class="sxs-lookup"><span data-stu-id="2f303-116">Description</span></span>|  
|--------------|-----------------|  
|`AllowUserEdit`|<span data-ttu-id="2f303-117">Určuje, zda uživatel může změnit hodnotu panelu sledování blesku kliknutím a přetažením.</span><span class="sxs-lookup"><span data-stu-id="2f303-117">Indicates whether the user can change the value of the flash track bar by clicking and dragging it.</span></span>|  
|`EndColor`|<span data-ttu-id="2f303-118">Určuje koncovou barvu panelu sledování.</span><span class="sxs-lookup"><span data-stu-id="2f303-118">Specifies the ending color of the track bar.</span></span>|  
|`DarkenBy`|<span data-ttu-id="2f303-119">Určuje, kolik se má ztmavit pozadí vzhledem k přechodu na popředí.</span><span class="sxs-lookup"><span data-stu-id="2f303-119">Specifies how much to darken the background with respect to the foreground gradient.</span></span>|  
|`Max`|<span data-ttu-id="2f303-120">Určuje maximální hodnotu panelu sledování.</span><span class="sxs-lookup"><span data-stu-id="2f303-120">Specifies the maximum value of the track bar.</span></span>|  
|`Min`|<span data-ttu-id="2f303-121">Určuje minimální hodnotu panelu sledování.</span><span class="sxs-lookup"><span data-stu-id="2f303-121">Specifies the minimum value of the track bar.</span></span>|  
|`StartColor`|<span data-ttu-id="2f303-122">Určuje počáteční barvu přechodu.</span><span class="sxs-lookup"><span data-stu-id="2f303-122">Specifies the starting color of the gradient.</span></span>|  
|`ShowPercentage`|<span data-ttu-id="2f303-123">Označuje, zda se má zobrazit procento nad přechodem.</span><span class="sxs-lookup"><span data-stu-id="2f303-123">Indicates whether to display a percentage over the gradient.</span></span>|  
|`ShowValue`|<span data-ttu-id="2f303-124">Označuje, zda se má zobrazit aktuální hodnota nad přechodem.</span><span class="sxs-lookup"><span data-stu-id="2f303-124">Indicates whether to display the current value over the gradient.</span></span>|  
|`ShowGradient`|<span data-ttu-id="2f303-125">Určuje, zda se má na panelu sledování zobrazit barevný přechod znázorňující aktuální hodnotu.</span><span class="sxs-lookup"><span data-stu-id="2f303-125">Indicates whether the track bar should display a color gradient showing the current value.</span></span>|  
|-   `Value`|<span data-ttu-id="2f303-126">Určuje aktuální hodnotu panelu sledování.</span><span class="sxs-lookup"><span data-stu-id="2f303-126">Specifies the current value of the track bar.</span></span>|  
  
 <span data-ttu-id="2f303-127">Následující tabulka ukazuje další členy definované `FlashTrackBar:` události změněné vlastností a metody, která událost vyvolá.</span><span class="sxs-lookup"><span data-stu-id="2f303-127">The following table shows additional members defined by `FlashTrackBar:` the property-changed event and the method that raises the event.</span></span>  
  
|<span data-ttu-id="2f303-128">Člen</span><span class="sxs-lookup"><span data-stu-id="2f303-128">Member</span></span>|<span data-ttu-id="2f303-129">Popis</span><span class="sxs-lookup"><span data-stu-id="2f303-129">Description</span></span>|  
|------------|-----------------|  
|`ValueChanged`|<span data-ttu-id="2f303-130">Událost, která je vyvolána při změně vlastnosti `Value` panelu sledování.</span><span class="sxs-lookup"><span data-stu-id="2f303-130">The event that is raised when the `Value` property of the track bar changes.</span></span>|  
|`OnValueChanged`|<span data-ttu-id="2f303-131">Metoda, která vyvolá událost `ValueChanged`.</span><span class="sxs-lookup"><span data-stu-id="2f303-131">The method that raises the `ValueChanged` event.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="2f303-132">`FlashTrackBar` používá <xref:System.EventArgs> třídu pro data události a <xref:System.EventHandler> pro delegáta události.</span><span class="sxs-lookup"><span data-stu-id="2f303-132">`FlashTrackBar` uses the <xref:System.EventArgs> class for event data and <xref:System.EventHandler> for the event delegate.</span></span>  
  
 <span data-ttu-id="2f303-133">Pro zpracování odpovídajících událostí *EventName* `FlashTrackBar` Přepisuje následující metody, které dědí z <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="2f303-133">To handle the corresponding *EventName* events, `FlashTrackBar` overrides the following methods that it inherits from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:</span></span>  
  
- <xref:System.Windows.Forms.Control.OnPaint%2A>  
  
- <xref:System.Windows.Forms.Control.OnMouseDown%2A>  
  
- <xref:System.Windows.Forms.Control.OnMouseMove%2A>  
  
- <xref:System.Windows.Forms.Control.OnMouseUp%2A>  
  
- <xref:System.Windows.Forms.Control.OnResize%2A>  
  
 <span data-ttu-id="2f303-134">Pro zpracování odpovídajících událostí změněných vlastností `FlashTrackBar` Přepisuje následující metody, které dědí z <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="2f303-134">To handle the corresponding property-changed events, `FlashTrackBar` overrides the following methods that it inherits from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:</span></span>  
  
- <xref:System.Windows.Forms.Control.OnBackColorChanged%2A>  
  
- <xref:System.Windows.Forms.Control.OnBackgroundImageChanged%2A>  
  
- <xref:System.Windows.Forms.Control.OnTextChanged%2A>  
  
## <a name="example"></a><span data-ttu-id="2f303-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="2f303-135">Example</span></span>  
 <span data-ttu-id="2f303-136">Ovládací prvek `FlashTrackBar` definuje dva editory typů uživatelského rozhraní, `FlashTrackBarValueEditor` a `FlashTrackBarDarkenByEditor`, které jsou uvedeny v následujících výpisech kódu.</span><span class="sxs-lookup"><span data-stu-id="2f303-136">The `FlashTrackBar` control defines two UI type editors, `FlashTrackBarValueEditor` and `FlashTrackBarDarkenByEditor`, which are shown in the following code listings.</span></span> <span data-ttu-id="2f303-137">Třída `HostApp` používá ovládací prvek `FlashTrackBar` ve formuláři Windows.</span><span class="sxs-lookup"><span data-stu-id="2f303-137">The `HostApp` class uses the `FlashTrackBar` control on a Windows Form.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#1)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#1)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarDarkenByEditor.cs#10)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarDarkenByEditor.vb#10)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarValueEditor.cs#20)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarValueEditor.vb#20)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/HostApp.cs#30)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/HostApp.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="2f303-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2f303-138">See also</span></span>

- <span data-ttu-id="2f303-139">[Rozšíření podpory pro dobu návrhu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="2f303-139">[Extending Design-Time Support](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span></span>
- [<span data-ttu-id="2f303-140">Základní informace o vývoji ovládacích prvků Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2f303-140">Windows Forms Control Development Basics</span></span>](windows-forms-control-development-basics.md)
