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
# <a name="how-to-create-a-windows-forms-control-that-shows-progress"></a>Postupy: Vytvoření ovládacího prvku Windows Forms zobrazujícího průběh
Následující příklad kódu ukazuje vlastní ovládací prvek s názvem `FlashTrackBar`, který lze použít k zobrazení úrovně nebo průběhu aplikace na úrovni uživatele. Pomocí přechodu vizuálně reprezentuje průběh.  
  
 Ovládací prvek `FlashTrackBar` ilustruje následující koncepty:  
  
- Definování vlastních vlastností.  
  
- Definování vlastních událostí. (`FlashTrackBar` definuje událost `ValueChanged`.)  
  
- Přepsání metody <xref:System.Windows.Forms.Control.OnPaint%2A> k poskytnutí logiky pro vykreslení ovládacího prvku.  
  
- Výpočet oblasti, která je k dispozici pro vykreslení ovládacího prvku pomocí vlastnosti <xref:System.Windows.Forms.Control.ClientRectangle%2A>. `FlashTrackBar` to dělá v metodě `OptimizedInvalidate`.  
  
- Implementace serializace nebo trvalosti vlastnosti při změně v Návrhář formulářů. `FlashTrackBar` definuje metody `ShouldSerializeStartColor` a `ShouldSerializeEndColor` pro serializaci vlastností `StartColor` a `EndColor`.  
  
 V následující tabulce jsou uvedeny vlastní vlastnosti definované `FlashTrackBar`.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|`AllowUserEdit`|Určuje, zda uživatel může změnit hodnotu panelu sledování blesku kliknutím a přetažením.|  
|`EndColor`|Určuje koncovou barvu panelu sledování.|  
|`DarkenBy`|Určuje, kolik se má ztmavit pozadí vzhledem k přechodu na popředí.|  
|`Max`|Určuje maximální hodnotu panelu sledování.|  
|`Min`|Určuje minimální hodnotu panelu sledování.|  
|`StartColor`|Určuje počáteční barvu přechodu.|  
|`ShowPercentage`|Označuje, zda se má zobrazit procento nad přechodem.|  
|`ShowValue`|Označuje, zda se má zobrazit aktuální hodnota nad přechodem.|  
|`ShowGradient`|Určuje, zda se má na panelu sledování zobrazit barevný přechod znázorňující aktuální hodnotu.|  
|-   `Value`|Určuje aktuální hodnotu panelu sledování.|  
  
 Následující tabulka ukazuje další členy definované `FlashTrackBar:` události změněné vlastností a metody, která událost vyvolá.  
  
|Člen|Popis|  
|------------|-----------------|  
|`ValueChanged`|Událost, která je vyvolána při změně vlastnosti `Value` panelu sledování.|  
|`OnValueChanged`|Metoda, která vyvolá událost `ValueChanged`.|  
  
> [!NOTE]
> `FlashTrackBar` používá <xref:System.EventArgs> třídu pro data události a <xref:System.EventHandler> pro delegáta události.  
  
 Pro zpracování odpovídajících událostí *EventName* `FlashTrackBar` Přepisuje následující metody, které dědí z <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:  
  
- <xref:System.Windows.Forms.Control.OnPaint%2A>  
  
- <xref:System.Windows.Forms.Control.OnMouseDown%2A>  
  
- <xref:System.Windows.Forms.Control.OnMouseMove%2A>  
  
- <xref:System.Windows.Forms.Control.OnMouseUp%2A>  
  
- <xref:System.Windows.Forms.Control.OnResize%2A>  
  
 Pro zpracování odpovídajících událostí změněných vlastností `FlashTrackBar` Přepisuje následující metody, které dědí z <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:  
  
- <xref:System.Windows.Forms.Control.OnBackColorChanged%2A>  
  
- <xref:System.Windows.Forms.Control.OnBackgroundImageChanged%2A>  
  
- <xref:System.Windows.Forms.Control.OnTextChanged%2A>  
  
## <a name="example"></a>Příklad  
 Ovládací prvek `FlashTrackBar` definuje dva editory typů uživatelského rozhraní, `FlashTrackBarValueEditor` a `FlashTrackBarDarkenByEditor`, které jsou uvedeny v následujících výpisech kódu. Třída `HostApp` používá ovládací prvek `FlashTrackBar` ve formuláři Windows.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#1)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#1)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarDarkenByEditor.cs#10)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarDarkenByEditor.vb#10)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarValueEditor.cs#20)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarValueEditor.vb#20)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/HostApp.cs#30)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/HostApp.vb#30)]  
  
## <a name="see-also"></a>Viz také:

- [Rozšíření podpory pro dobu návrhu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))
- [Základní informace o vývoji ovládacích prvků Windows Forms](windows-forms-control-development-basics.md)
