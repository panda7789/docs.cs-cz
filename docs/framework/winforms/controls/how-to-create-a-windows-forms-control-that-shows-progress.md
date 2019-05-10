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
ms.openlocfilehash: 877df5139fd0e626cd2242e3790bc7100f6233aa
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64599328"
---
# <a name="how-to-create-a-windows-forms-control-that-shows-progress"></a>Postupy: Vytvoření ovládacího prvku Windows Forms zobrazujícího průběh
Následující příklad kódu ukazuje vlastního ovládacího prvku volá `FlashTrackBar` , který umožňuje zobrazit uživatele, úroveň nebo průběh aplikace. Použije barevný přechod vizuálně znázornit průběh.  
  
 `FlashTrackBar` Ovládací prvek znázorňuje tyto koncepty:  
  
- Definování vlastních vlastností.  
  
- Definování vlastních událostí. (`FlashTrackBar` definuje `ValueChanged` události.)  
  
- Přepsání <xref:System.Windows.Forms.Control.OnPaint%2A> metodu k dispozici logiku pro vykreslení ovládacího prvku.  
  
- Výpočetní oblasti k dispozici pro vykreslení ovládacího prvku s použitím jeho <xref:System.Windows.Forms.Control.ClientRectangle%2A> vlastnost. `FlashTrackBar` to dělá jeho `OptimizedInvalidate` metoda.  
  
- Implementace serializace nebo trvalosti pro vlastnost, když se změní v Návrháři formulářů Windows. `FlashTrackBar` definuje `ShouldSerializeStartColor` a `ShouldSerializeEndColor` metody pro serializaci jeho `StartColor` a `EndColor` vlastnosti.  
  
 V následující tabulce jsou uvedeny vlastní vlastnosti definované `FlashTrackBar`.  
  
|Vlastnost|Popis|  
|--------------|-----------------|  
|`AllowUserEdit`|Určuje, zda uživatel může změnit hodnotu pruh sledování flash kliknutím a přetažením.|  
|`EndColor`|Určuje koncovou barvu pruh sledování.|  
|`DarkenBy`|Určuje, kolik ztmavení na pozadí s ohledem na popředí přechodu.|  
|`Max`|Určuje maximální hodnotu pruh sledování.|  
|`Min`|Určuje minimální hodnotu pruh sledování.|  
|`StartColor`|Určuje počáteční barva přechodu.|  
|`ShowPercentage`|Určuje, jestli se má zobrazit v procentech přechodu.|  
|`ShowValue`|Určuje, jestli se má zobrazit aktuální hodnotu přechodu.|  
|`ShowGradient`|Udává, zda pruh sledování by měla zobrazit barva přechodu zobrazuje aktuální hodnotu.|  
|-   `Value`|Určuje aktuální hodnotu pruh sledování.|  
  
 V následující tabulce jsou uvedeny další členy definované `FlashTrackBar:` události změny vlastnosti a metody, která vyvolává událost.  
  
|Člen|Popis|  
|------------|-----------------|  
|`ValueChanged`|Událost, která je vyvolána při `Value` vlastnost pruh sledování změn.|  
|`OnValueChanged`|Metoda, která vyvolá `ValueChanged` událostí.|  
  
> [!NOTE]
>  `FlashTrackBar` používá <xref:System.EventArgs> třídu pro data události a <xref:System.EventHandler> pro delegáta události.  
  
 Pro zpracování odpovídající *EventName* události, `FlashTrackBar` přepíše následující metody, které dědí z <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:  
  
- <xref:System.Windows.Forms.Control.OnPaint%2A>  
  
- <xref:System.Windows.Forms.Control.OnMouseDown%2A>  
  
- <xref:System.Windows.Forms.Control.OnMouseMove%2A>  
  
- <xref:System.Windows.Forms.Control.OnMouseUp%2A>  
  
- <xref:System.Windows.Forms.Control.OnResize%2A>  
  
 Pro zpracování odpovídající události změny vlastnosti `FlashTrackBar` přepíše následující metody, které dědí z <xref:System.Windows.Forms.Control?displayProperty=nameWithType>:  
  
- <xref:System.Windows.Forms.Control.OnBackColorChanged%2A>  
  
- <xref:System.Windows.Forms.Control.OnBackgroundImageChanged%2A>  
  
- <xref:System.Windows.Forms.Control.OnTextChanged%2A>  
  
## <a name="example"></a>Příklad  
 `FlashTrackBar` Ovládací prvek definuje dvě editory typů uživatelského rozhraní, `FlashTrackBarValueEditor` a `FlashTrackBarDarkenByEditor`, které jsou uvedeny v následující výpis kódu. `HostApp` Třídy používá `FlashTrackBar` ovládací prvek na formuláři Windows.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#1)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#1)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarDarkenByEditor.cs#10)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarDarkenByEditor.vb#10)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBarValueEditor.cs#20)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBarValueEditor.vb#20)]  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/HostApp.cs#30)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/HostApp.vb#30)]  
  
## <a name="see-also"></a>Viz také:

- [Rozšíření podpory během návrhu](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/37899azc(v=vs.120))
- [Základní informace o vývoji ovládacích prvků Windows Forms](windows-forms-control-development-basics.md)
