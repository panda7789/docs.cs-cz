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
ms.openlocfilehash: a230611bfbb0a7f21a96de22674377887cc93c2d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527797"
---
# <a name="handling-user-input"></a>Zpracování uživatelského vstupu
Toto téma popisuje hlavní události klávesnice a myši poskytované <xref:System.Windows.Forms.Control?displayProperty=nameWithType>. Při zpracování události, by měly přepsat autoři řízení chráněného `On` *EventName* metoda místo připojení delegáta k události. Ke kontrole událostí, najdete v části [vyvolání události ze součásti](http://msdn.microsoft.com/library/9aebf605-a87d-470b-b7c8-f9abfc8360a0).  
  
> [!NOTE]
>  Pokud nejsou žádná data přidružená události instance základní třídy <xref:System.EventArgs> je předat jako argument k `On` *EventName* metoda.  
  
## <a name="keyboard-events"></a>Události klávesnice  
 Jsou běžné události klávesnice, které může zpracovat vlastního ovládacího prvku <xref:System.Windows.Forms.Control.KeyDown>, <xref:System.Windows.Forms.Control.KeyPress>, a <xref:System.Windows.Forms.Control.KeyUp>.  
  
|Název události|Metoda k přepsání|Popis události|  
|----------------|------------------------|--------------------------|  
|`KeyDown`|`void OnKeyDown(KeyEventArgs)`|Vyvolána, pouze pokud původně stisknutí klávesy.|  
|`KeyPress`|`void OnKeyPress`<br /><br /> `(KeyPressEventArgs)`|Vyvolá se pokaždé, když stisknutí klávesy. Pokud je klávesa stisknuta, <xref:System.Windows.Forms.Control.KeyPress> událost se vyvolá při opakovaném míry definované v operačním systému.|  
|`KeyUp`|`void OnKeyUp(KeyEventArgs)`|Vyvolá, když uvolnění klávesy.|  
  
> [!NOTE]
>  Zpracování vstupu klávesnice je podstatně složitější než přepsání události v předchozí tabulce a je nad rámec tohoto tématu. Další informace najdete v tématu [uživatelský vstup ve Windows Forms](../../../../docs/framework/winforms/user-input-in-windows-forms.md).  
  
## <a name="mouse-events"></a>Události myši  
 Události myši, které může zpracovat vlastního ovládacího prvku jsou <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseHover>, <xref:System.Windows.Forms.Control.MouseLeave>, <xref:System.Windows.Forms.Control.MouseMove>, a <xref:System.Windows.Forms.Control.MouseUp>.  
  
|Název události|Metoda k přepsání|Popis události|  
|----------------|------------------------|--------------------------|  
|`MouseDown`|`void OnMouseDown(MouseEventArgs)`|Vyvolána při stisknutí tlačítka myši při ukazatel myši nad ovládací prvek.|  
|`MouseEnter`|`void OnMouseEnter(EventArgs)`|Vyvolá, když ukazatel vstoupí nejprve oblast ovládacího prvku.|  
|`MouseHover`|`void OnMouseHover(EventArgs)`|Vyvolá, když ukazatelem myši ovládací prvek.|  
|`MouseLeave`|`void OnMouseLeave(EventArgs)`|Vyvolá, když ukazatel opustí oblast ovládacího prvku.|  
|`MouseMove`|`void OnMouseMove(MouseEventArgs)`|Vyvolána při umístění ukazatele v oblasti řízení.|  
|`MouseUp`|`void OnMouseUp(MouseEventArgs)`|Vyvolá, když je uvolnění tlačítka myši, když je ukazatel myši nad ovládací prvek nebo když ukazatel opustí oblast ovládacího prvku.|  
  
 Následující fragment kódu ukazuje příklad přepsání <xref:System.Windows.Forms.Control.MouseDown> událostí.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#7)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#7)]  
  
 Následující fragment kódu ukazuje příklad přepsání <xref:System.Windows.Forms.Control.MouseMove> událostí.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#8)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#8)]  
  
 Následující fragment kódu ukazuje příklad přepsání <xref:System.Windows.Forms.Control.MouseUp> událostí.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#9)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#9)]  
  
 Pro úplný zdrojový kód `FlashTrackBar` ukázkové najdete v tématu [postupy: vytvoření Windows Forms ovládací prvek, zobrazuje průběh](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
## <a name="see-also"></a>Viz také  
 [Události v ovládacích prvcích Windows Forms](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)  
 [Definování události](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)  
 [Události](../../../../docs/standard/events/index.md)  
 [Uživatelský vstup ve Windows Forms](../../../../docs/framework/winforms/user-input-in-windows-forms.md)
