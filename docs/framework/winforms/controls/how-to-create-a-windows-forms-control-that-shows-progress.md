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
ms.openlocfilehash: 1f457d6e2b0eb73da7a16dc93ea80a14ddb4b2c2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59202011"
---
# <a name="how-to-create-a-windows-forms-control-that-shows-progress"></a><span data-ttu-id="c49e9-102">Postupy: Vytvoření ovládacího prvku Windows Forms zobrazujícího průběh</span><span class="sxs-lookup"><span data-stu-id="c49e9-102">How to: Create a Windows Forms Control That Shows Progress</span></span>
<span data-ttu-id="c49e9-103">Následující příklad kódu ukazuje vlastního ovládacího prvku volá `FlashTrackBar` , který umožňuje zobrazit uživatele, úroveň nebo průběh aplikace.</span><span class="sxs-lookup"><span data-stu-id="c49e9-103">The following code example shows a custom control called `FlashTrackBar` that can be used to show the user the level or the progress of an application.</span></span> <span data-ttu-id="c49e9-104">Použije barevný přechod vizuálně znázornit průběh.</span><span class="sxs-lookup"><span data-stu-id="c49e9-104">It uses a gradient to visually represent progress.</span></span>  
  
 <span data-ttu-id="c49e9-105">`FlashTrackBar` Ovládací prvek znázorňuje tyto koncepty:</span><span class="sxs-lookup"><span data-stu-id="c49e9-105">The `FlashTrackBar` control illustrates the following concepts:</span></span>  
  
-   <span data-ttu-id="c49e9-106">Definování vlastních vlastností.</span><span class="sxs-lookup"><span data-stu-id="c49e9-106">Defining custom properties.</span></span>  
  
-   <span data-ttu-id="c49e9-107">Definování vlastních událostí.</span><span class="sxs-lookup"><span data-stu-id="c49e9-107">Defining custom events.</span></span> <span data-ttu-id="c49e9-108">(`FlashTrackBar` definuje `ValueChanged` události.)</span><span class="sxs-lookup"><span data-stu-id="c49e9-108">(`FlashTrackBar` defines the `ValueChanged` event.)</span></span>  
  
-   <span data-ttu-id="c49e9-109">Přepsání <xref:System.Windows.Forms.Control.OnPaint%2A> metodu k dispozici logiku pro vykreslení ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="c49e9-109">Overriding the <xref:System.Windows.Forms.Control.OnPaint%2A> method to provide logic to draw the control.</span></span>  
  
-   <span data-ttu-id="c49e9-110">Výpočetní oblasti k dispozici pro vykreslení ovládacího prvku s použitím jeho <xref:System.Windows.Forms.Control.ClientRectangle%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c49e9-110">Computing the area available for drawing the control by using its <xref:System.Windows.Forms.Control.ClientRectangle%2A> property.</span></span> <span data-ttu-id="c49e9-111">`FlashTrackBar` to dělá jeho `OptimizedInvalidate` metoda.</span><span class="sxs-lookup"><span data-stu-id="c49e9-111">`FlashTrackBar` does this in its `OptimizedInvalidate` method.</span></span>  
  
-   <span data-ttu-id="c49e9-112">Implementace serializace nebo trvalosti pro vlastnost, když se změní v Návrháři formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="c49e9-112">Implementing serialization or persistence for a property when it is changed in the Windows Forms Designer.</span></span> <span data-ttu-id="c49e9-113">`FlashTrackBar` definuje `ShouldSerializeStartColor` a `ShouldSerializeEndColor` metody pro serializaci jeho `StartColor` a `EndColor` vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c49e9-113">`FlashTrackBar` defines the `ShouldSerializeStartColor` and `ShouldSerializeEndColor` methods for serializing its `StartColor` and `EndColor` properties.</span></span>  
  
 <span data-ttu-id="c49e9-114">V následující tabulce jsou uvedeny vlastní vlastnosti definované `FlashTrackBar`.</span><span class="sxs-lookup"><span data-stu-id="c49e9-114">The following table shows the custom properties defined by `FlashTrackBar`.</span></span>  
  
|<span data-ttu-id="c49e9-115">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="c49e9-115">Property</span></span>|<span data-ttu-id="c49e9-116">Popis</span><span class="sxs-lookup"><span data-stu-id="c49e9-116">Description</span></span>|  
|--------------|-----------------|  
|`AllowUserEdit`|<span data-ttu-id="c49e9-117">Určuje, zda uživatel může změnit hodnotu pruh sledování flash kliknutím a přetažením.</span><span class="sxs-lookup"><span data-stu-id="c49e9-117">Indicates whether the user can change the value of the flash track bar by clicking and dragging it.</span></span>|  
|`EndColor`|<span data-ttu-id="c49e9-118">Určuje koncovou barvu pruh sledování.</span><span class="sxs-lookup"><span data-stu-id="c49e9-118">Specifies the ending color of the track bar.</span></span>|  
|`DarkenBy`|<span data-ttu-id="c49e9-119">Určuje, kolik ztmavení na pozadí s ohledem na popředí přechodu.</span><span class="sxs-lookup"><span data-stu-id="c49e9-119">Specifies how much to darken the background with respect to the foreground gradient.</span></span>|  
|`Max`|<span data-ttu-id="c49e9-120">Určuje maximální hodnotu pruh sledování.</span><span class="sxs-lookup"><span data-stu-id="c49e9-120">Specifies the maximum value of the track bar.</span></span>|  
|`Min`|<span data-ttu-id="c49e9-121">Určuje minimální hodnotu pruh sledování.</span><span class="sxs-lookup"><span data-stu-id="c49e9-121">Specifies the minimum value of the track bar.</span></span>|  
|`StartColor`|<span data-ttu-id="c49e9-122">Určuje počáteční barva přechodu.</span><span class="sxs-lookup"><span data-stu-id="c49e9-122">Specifies the starting color of the gradient.</span></span>|  
|`ShowPercentage`|<span data-ttu-id="c49e9-123">Určuje, jestli se má zobrazit v procentech přechodu.</span><span class="sxs-lookup"><span data-stu-id="c49e9-123">Indicates whether to display a percentage over the gradient.</span></span>|  
|`ShowValue`|<span data-ttu-id="c49e9-124">Určuje, jestli se má zobrazit aktuální hodnotu přechodu.</span><span class="sxs-lookup"><span data-stu-id="c49e9-124">Indicates whether to display the current value over the gradient.</span></span>|  
|`ShowGradient`|<span data-ttu-id="c49e9-125">Udává, zda pruh sledování by měla zobrazit barva přechodu zobrazuje aktuální hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c49e9-125">Indicates whether the track bar should display a color gradient showing the current value.</span></span>|  
|-   `Value`|<span data-ttu-id="c49e9-126">Určuje aktuální hodnotu pruh sledování.</span><span class="sxs-lookup"><span data-stu-id="c49e9-126">Specifies the current value of the track bar.</span></span>|  
  
 <span data-ttu-id="c49e9-127">V následující tabulce jsou uvedeny další členy definované `FlashTrackBar:` události změny vlastnosti a metody, která vyvolává událost.</span><span class="sxs-lookup"><span data-stu-id="c49e9-127">The following table shows additional members defined by `FlashTrackBar:` the property-changed event and the method that raises the event.</span></span>  
  
|<span data-ttu-id="c49e9-128">Člen</span><span class="sxs-lookup"><span data-stu-id="c49e9-128">Member</span></span>|<span data-ttu-id="c49e9-129">Popis</span><span class="sxs-lookup"><span data-stu-id="c49e9-129">Description</span></span>|  
|------------|-----------------|  
|`ValueChanged`|<span data-ttu-id="c49e9-130">Událost, která je vyvolána při `Value` vlastnost pruh sledování změn.</span><span class="sxs-lookup"><span data-stu-id="c49e9-130">The event that is raised when the `Value` property of the track bar changes.</span></span>|  
|`OnValueChanged`|<span data-ttu-id="c49e9-131">Metoda, která vyvolá `ValueChanged` událostí.</span><span class="sxs-lookup"><span data-stu-id="c49e9-131">The method that raises the `ValueChanged` event.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="c49e9-132">`FlashTrackBar` používá <xref:System.EventArgs> třídu pro data události a <xref:System.EventHandler> pro delegáta události.</span><span class="sxs-lookup"><span data-stu-id="c49e9-132">`FlashTrackBar` uses the <xref:System.EventArgs> class for event data and <xref:System.EventHandler> for the event delegate.</span></span>  
  
 <span data-ttu-id="c49e9-133">Pro zpracování odpovídající *EventName* události, `FlashTrackBar` přepíše následující metody, které dědí z <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="c49e9-133">To handle the corresponding *EventName* events, `FlashTrackBar` overrides the following methods that it inherits from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:</span></span>  
  
-   <xref:System.Windows.Forms.Control.OnPaint%2A>  
  
-   <xref:System.Windows.Forms.Control.OnMouseDown%2A>  
  
-   <xref:System.Windows.Forms.Control.OnMouseMove%2A>  
  
-   <xref:System.Windows.Forms.Control.OnMouseUp%2A>  
  
-   <xref:System.Windows.Forms.Control.OnResize%2A>  
  
 <span data-ttu-id="c49e9-134">Pro zpracování odpovídající události změny vlastnosti `FlashTrackBar` přepíše následující metody, které dědí z <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="c49e9-134">To handle the corresponding property-changed events, `FlashTrackBar` overrides the following methods that it inherits from <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:</span></span>  
  
-   <xref:System.Windows.Forms.Control.OnBackColorChanged%2A>  
  
-   <xref:System.Windows.Forms.Control.OnBackgroundImageChanged%2A>  
  
-   <xref:System.Windows.Forms.Control.OnTextChanged%2A>  
  
## <a name="example"></a><span data-ttu-id="c49e9-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="c49e9-135">Example</span></span>  
 <span data-ttu-id="c49e9-136">`FlashTrackBar` Ovládací prvek definuje dvě editory typů uživatelského rozhraní, `FlashTrackBarValueEditor` a `FlashTrackBarDarkenByEditor`, které jsou uvedeny v následující výpis kódu.</span><span class="sxs-lookup"><span data-stu-id="c49e9-136">The `FlashTrackBar` control defines two UI type editors, `FlashTrackBarValueEditor` and `FlashTrackBarDarkenByEditor`, which are shown in the following code listings.</span></span> <span data-ttu-id="c49e9-137">`HostApp` Třídy používá `FlashTrackBar` ovládací prvek na formuláři Windows.</span><span class="sxs-lookup"><span data-stu-id="c49e9-137">The `HostApp` class uses the `FlashTrackBar` control on a Windows Form.</span></span>  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#1)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#1)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarDarkenByEditor.cs#10)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarDarkenByEditor.vb#10)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarValueEditor.cs#20)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarValueEditor.vb#20)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/HostApp.cs#30)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/HostApp.vb#30)]  
  
## <a name="see-also"></a><span data-ttu-id="c49e9-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c49e9-138">See also</span></span>

- <span data-ttu-id="c49e9-139">[Rozšíření podpory během návrhu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span><span class="sxs-lookup"><span data-stu-id="c49e9-139">[Extending Design-Time Support](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))</span></span>
- [<span data-ttu-id="c49e9-140">Základní informace o vývoji ovládacích prvků Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c49e9-140">Windows Forms Control Development Basics</span></span>](windows-forms-control-development-basics.md)
