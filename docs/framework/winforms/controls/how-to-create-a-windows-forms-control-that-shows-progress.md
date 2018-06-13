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
# <a name="how-to-create-a-windows-forms-control-that-shows-progress"></a>Postupy: Vytvoření ovládacího prvku Windows Forms zobrazujícího průběh
Následující příklad kódu ukazuje vlastního ovládacího prvku názvem `FlashTrackBar` který lze použít na úroveň nebo průběh aplikace se uživateli zobrazí. Přechod na základě vizuálně představují průběh.  
  
 `FlashTrackBar` Řízení znázorňuje následující koncepty:  
  
-   Definování vlastní vlastnosti.  
  
-   Definování vlastních událostí. (`FlashTrackBar` definuje `ValueChanged` události.)  
  
-   Přepsání <xref:System.Windows.Forms.Control.OnPaint%2A> metody můžete zajistit logiku k vykreslení ovládacího prvku.  
  
-   Computing oblasti k dispozici pro vykreslení ovládacího prvku pomocí jeho <xref:System.Windows.Forms.Control.ClientRectangle%2A> vlastnost. `FlashTrackBar` k tomu jeho `OptimizedInvalidate` metoda.  
  
-   Implementace serializace nebo stálosti pro vlastnost, když se změní v Návrháři formulářů. `FlashTrackBar` definuje `ShouldSerializeStartColor` a `ShouldSerializeEndColor` metody pro serializaci jeho `StartColor` a `EndColor` vlastnosti.  
  
 V následující tabulce jsou uvedeny vlastní vlastnosti definované `FlashTrackBar`.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|`AllowUserEdit`|Určuje, jestli uživatel může změnit hodnotu panelu flash sledovat kliknutím a přetažením.|  
|`EndColor`|Určuje koncovou barvu panelu sledovat.|  
|`DarkenBy`|Určuje, kolik ztmavení pozadí s ohledem na popředí přechodu.|  
|`Max`|Určuje maximální hodnotu panelu sledovat.|  
|`Min`|Určuje minimální hodnotu panelu sledovat.|  
|`StartColor`|Určuje počáteční barvu barevného přechodu.|  
|`ShowPercentage`|Označuje, zda se má zobrazit procento přechodu.|  
|`ShowValue`|Označuje, zda se má zobrazit aktuální hodnota přechodu.|  
|`ShowGradient`|Udává, zda panelu sledování by měla zobrazit přechod barev, zobrazuje aktuální hodnotu.|  
|-   `Value`|Určuje aktuální hodnota panelu sledovat.|  
  
 V následující tabulce jsou uvedeny další členy, které jsou definované `FlashTrackBar:` událost změny vlastnosti a metody, která vyvolává událost.  
  
|Člen|Popis|  
|------------|-----------------|  
|`ValueChanged`|Událost, která se vyvolá, když `Value` vlastnost sledování změn panelu.|  
|`OnValueChanged`|Metoda, která vyvolává `ValueChanged` událostí.|  
  
> [!NOTE]
>  `FlashTrackBar` používá <xref:System.EventArgs> třídu pro data události a <xref:System.EventHandler> pro delegát události.  
  
 Pro zpracování odpovídající *EventName* události, `FlashTrackBar` přepíše následující metody, které dědí z <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:  
  
-   <xref:System.Windows.Forms.Control.OnPaint%2A>  
  
-   <xref:System.Windows.Forms.Control.OnMouseDown%2A>  
  
-   <xref:System.Windows.Forms.Control.OnMouseMove%2A>  
  
-   <xref:System.Windows.Forms.Control.OnMouseUp%2A>  
  
-   <xref:System.Windows.Forms.Control.OnResize%2A>  
  
 Zpracování událostí odpovídající vlastnost změnit `FlashTrackBar` přepíše následující metody, které dědí z <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:  
  
-   <xref:System.Windows.Forms.Control.OnBackColorChanged%2A>  
  
-   <xref:System.Windows.Forms.Control.OnBackgroundImageChanged%2A>  
  
-   <xref:System.Windows.Forms.Control.OnTextChanged%2A>  
  
## <a name="example"></a>Příklad  
 `FlashTrackBar` Řízení definuje dvě editory typ uživatelského rozhraní, `FlashTrackBarValueEditor` a `FlashTrackBarDarkenByEditor`, které jsou uvedené v následující příklady kódu. `HostApp` Třídy používá `FlashTrackBar` ovládacího prvku ve formuláři Windows.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#1)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#1)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarDarkenByEditor.cs#10)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarDarkenByEditor.vb#10)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarValueEditor.cs#20)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarValueEditor.vb#20)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/HostApp.cs#30)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/HostApp.vb#30)]  
  
## <a name="see-also"></a>Viz také  
 [Rozšíření podpory návrhu](http://msdn.microsoft.com/library/d6ac8a6a-42fd-4bc8-bf33-b212811297e2)  
 [Základní informace o vývoji ovládacích prvků Windows Forms](../../../../docs/framework/winforms/controls/windows-forms-control-development-basics.md)
