---
title: Zpracování uživatelského vstupu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], user input using code
- custom controls [Windows Forms], keyboard events using code
- custom controls [Windows Forms], mouse events using code
ms.assetid: d9b12787-86f6-4022-8e0f-e12d312c4af2
ms.openlocfilehash: f92b742c3f6feec72e5b3150204d7d984636281d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934096"
---
# <a name="handling-user-input"></a>Zpracování uživatelského vstupu
Toto téma popisuje hlavní události klávesnice a myši, které <xref:System.Windows.Forms.Control?displayProperty=nameWithType>poskytuje. Při zpracování události by autoři ovládacího prvku měli přepsat chráněnou `On`metodu *EventName* místo připojení delegáta události. Informace o revizi událostí naleznete v tématu [vyvolání událostí ze součásti](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/sh2e3k5z(v=vs.120)).  
  
> [!NOTE]
> Pokud nejsou k události přidružena žádná data, instance základní třídy <xref:System.EventArgs> je předána jako argument `On`metodě *EventName* .  
  
## <a name="keyboard-events"></a>Události klávesnice  
 Běžné události klávesnice, které může váš ovládací prvek zpracovávat <xref:System.Windows.Forms.Control.KeyDown>, <xref:System.Windows.Forms.Control.KeyPress>jsou, <xref:System.Windows.Forms.Control.KeyUp>a.  
  
|Název události|Metoda, která se má přepsat|Popis události|  
|----------------|------------------------|--------------------------|  
|`KeyDown`|`void OnKeyDown(KeyEventArgs)`|Vyvolá se pouze při počátečním stisknutí klávesy.|  
|`KeyPress`|`void OnKeyPress`<br /><br /> `(KeyPressEventArgs)`|Vyvolá se při každém stisknutí klávesy. Pokud je klíč podržený, <xref:System.Windows.Forms.Control.KeyPress> vyvolá se událost na základě rychlosti opakování definované operačním systémem.|  
|`KeyUp`|`void OnKeyUp(KeyEventArgs)`|Vyvolá se při uvolnění klávesy.|  
  
> [!NOTE]
> Zpracování vstupu z klávesnice je podstatně složitější než přepsání událostí v předchozí tabulce a je nad rámec tohoto tématu. Další informace najdete v tématu [vstup uživatele v model Windows Forms](../user-input-in-windows-forms.md).  
  
## <a name="mouse-events"></a>Události myši  
 Události myši, které ovládací prvek může zpracovat, <xref:System.Windows.Forms.Control.MouseDown> <xref:System.Windows.Forms.Control.MouseEnter>jsou, <xref:System.Windows.Forms.Control.MouseHover>, <xref:System.Windows.Forms.Control.MouseLeave>, <xref:System.Windows.Forms.Control.MouseMove>, a <xref:System.Windows.Forms.Control.MouseUp>.  
  
|Název události|Metoda, která se má přepsat|Popis události|  
|----------------|------------------------|--------------------------|  
|`MouseDown`|`void OnMouseDown(MouseEventArgs)`|Je aktivována při stisknutí tlačítka myši, zatímco je ukazatel nad ovládacím prvkem.|  
|`MouseEnter`|`void OnMouseEnter(EventArgs)`|Je aktivována, když ukazatel poprvé vstoupí do oblasti ovládacího prvku.|  
|`MouseHover`|`void OnMouseHover(EventArgs)`|Je aktivována, když ukazatel myši najede myší na ovládací prvek.|  
|`MouseLeave`|`void OnMouseLeave(EventArgs)`|Je aktivována, když ukazatel opustí oblast ovládacího prvku.|  
|`MouseMove`|`void OnMouseMove(MouseEventArgs)`|Je aktivována, když se ukazatel pohybuje v oblasti ovládacího prvku.|  
|`MouseUp`|`void OnMouseUp(MouseEventArgs)`|Je aktivována při uvolnění tlačítka myši, když je ukazatel nad ovládacím prvkem, nebo když ukazatel opustí oblast ovládacího prvku.|  
  
 Následující fragment kódu ukazuje příklad přepsání <xref:System.Windows.Forms.Control.MouseDown> události.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#7)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#7)]  
  
 Následující fragment kódu ukazuje příklad přepsání <xref:System.Windows.Forms.Control.MouseMove> události.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#8)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#8)]  
  
 Následující fragment kódu ukazuje příklad přepsání <xref:System.Windows.Forms.Control.MouseUp> události.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#9)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#9)]  
  
 Úplný zdrojový kód pro `FlashTrackBar` ukázku naleznete v tématu [How to: Vytvoří ovládací prvek model Windows Forms, který zobrazuje](how-to-create-a-windows-forms-control-that-shows-progress.md)průběh.  
  
## <a name="see-also"></a>Viz také:

- [Události v ovládacích prvcích Windows Forms](events-in-windows-forms-controls.md)
- [Definování události](defining-an-event-in-windows-forms-controls.md)
- [Události](../../../standard/events/index.md)
- [Uživatelský vstup ve Windows Forms](../user-input-in-windows-forms.md)
