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
ms.openlocfilehash: 84f0caace70f9877e84fdd01dc69216dc10fe485
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950576"
---
# <a name="how-to-create-a-windows-forms-control-that-shows-progress"></a>Postupy: Vytvoření ovládacího prvku Windows Forms zobrazujícího průběh
Následující příklad kódu ukazuje vlastní ovládací prvek s názvem `FlashTrackBar` , který lze použít k zobrazení úrovně nebo průběhu aplikace na úrovni uživatele. Pomocí přechodu vizuálně reprezentuje průběh.  
  
 `FlashTrackBar` Ovládací prvek znázorňuje následující koncepty:  
  
- Definování vlastních vlastností.  
  
- Definování vlastních událostí. `FlashTrackBar` (`ValueChanged` definuje událost.)  
  
- <xref:System.Windows.Forms.Control.OnPaint%2A> Přepsání metody k poskytnutí logiky pro vykreslení ovládacího prvku.  
  
- Výpočet oblasti, která je k dispozici pro vykreslení ovládacího <xref:System.Windows.Forms.Control.ClientRectangle%2A> prvku pomocí jeho vlastnosti. `FlashTrackBar`provede tuto `OptimizedInvalidate` metodu.  
  
- Implementace serializace nebo trvalosti vlastnosti při změně v Návrhář formulářů. `FlashTrackBar`Definuje metody a `ShouldSerializeEndColor` pro serializaci vlastností `EndColor` a.`StartColor` `ShouldSerializeStartColor`  
  
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
  
 V následující tabulce jsou uvedeny další členy, `FlashTrackBar:` které jsou definovány událostí změny vlastností a metoda, která událost vyvolává.  
  
|Člen|Popis|  
|------------|-----------------|  
|`ValueChanged`|Událost, která je vyvolána při `Value` změně vlastnosti panelu sledování.|  
|`OnValueChanged`|Metoda, která vyvolá `ValueChanged` událost.|  
  
> [!NOTE]
> `FlashTrackBar`používá třídu pro data události a <xref:System.EventHandler> delegáta události. <xref:System.EventArgs>  
  
 Pro zpracování odpovídajících `FlashTrackBar` událostí *EventName* přepíše následující metody, které dědí z: <xref:System.Windows.Forms.Control?displayProperty=nameWithType>  
  
- <xref:System.Windows.Forms.Control.OnPaint%2A>  
  
- <xref:System.Windows.Forms.Control.OnMouseDown%2A>  
  
- <xref:System.Windows.Forms.Control.OnMouseMove%2A>  
  
- <xref:System.Windows.Forms.Control.OnMouseUp%2A>  
  
- <xref:System.Windows.Forms.Control.OnResize%2A>  
  
 Chcete-li zpracovat odpovídající události změněné vlastností, `FlashTrackBar` potlačí následující metody, které dědí z <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:  
  
- <xref:System.Windows.Forms.Control.OnBackColorChanged%2A>  
  
- <xref:System.Windows.Forms.Control.OnBackgroundImageChanged%2A>  
  
- <xref:System.Windows.Forms.Control.OnTextChanged%2A>  
  
## <a name="example"></a>Příklad  
 Ovládací prvek definuje dva `FlashTrackBarValueEditor` editory typů uživatelského rozhraní `FlashTrackBarDarkenByEditor`a, které jsou uvedeny v následujících výpisech kódu. `FlashTrackBar` `HostApp` Třída`FlashTrackBar` používá ovládací prvek ve formuláři Windows.  
  
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
