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
ms.openlocfilehash: 19bb494d6f478c8cb7adda770f441470c4b2d19f
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/16/2018
ms.locfileid: "45677666"
---
# <a name="handling-user-input"></a>Zpracování uživatelského vstupu
Toto téma popisuje hlavní události klávesnice a myši poskytované <xref:System.Windows.Forms.Control?displayProperty=nameWithType>. Při zpracování události, ovládací prvek autoři by měly přepsat chráněnou `On` *EventName* metody spíše než připojením delegáta k události. Přehled událostí, naleznete v tématu [vyvolávání událostí z komponenty](https://msdn.microsoft.com/library/9aebf605-a87d-470b-b7c8-f9abfc8360a0).  
  
> [!NOTE]
>  Pokud neexistuje žádná data přidružená k události, instance základní třídy <xref:System.EventArgs> je předán jako argument `On` *EventName* metody.  
  
## <a name="keyboard-events"></a>Události klávesnice  
 Jsou běžné události klávesnice, které dokáže zpracovat váš ovládací prvek <xref:System.Windows.Forms.Control.KeyDown>, <xref:System.Windows.Forms.Control.KeyPress>, a <xref:System.Windows.Forms.Control.KeyUp>.  
  
|Název události|Metoda přepsání.|Popis události|  
|----------------|------------------------|--------------------------|  
|`KeyDown`|`void OnKeyDown(KeyEventArgs)`|Vyvolána, pouze když se stiskne klávesa, původně.|  
|`KeyPress`|`void OnKeyPress`<br /><br /> `(KeyPressEventArgs)`|Vyvolá se pokaždé, když se stiskne klávesa. Pokud je klávesa stisknuta, <xref:System.Windows.Forms.Control.KeyPress> událost se vyvolá při opakovaném rychlostí definované v operačním systému.|  
|`KeyUp`|`void OnKeyUp(KeyEventArgs)`|Vyvoláno, když se uvolní klávesa.|  
  
> [!NOTE]
>  Zpracování vstupu klávesnice je podstatně složitější než přepsání události v předchozí tabulce a je nad rámec tohoto tématu. Další informace najdete v tématu [uživatelský vstup ve Windows Forms](../../../../docs/framework/winforms/user-input-in-windows-forms.md).  
  
## <a name="mouse-events"></a>Události myši  
 Události myši, které dokáže zpracovat váš ovládací prvek se <xref:System.Windows.Forms.Control.MouseDown>, <xref:System.Windows.Forms.Control.MouseEnter>, <xref:System.Windows.Forms.Control.MouseHover>, <xref:System.Windows.Forms.Control.MouseLeave>, <xref:System.Windows.Forms.Control.MouseMove>, a <xref:System.Windows.Forms.Control.MouseUp>.  
  
|Název události|Metoda přepsání.|Popis události|  
|----------------|------------------------|--------------------------|  
|`MouseDown`|`void OnMouseDown(MouseEventArgs)`|Vyvoláno, když se stiskne tlačítko myši, zatímco je ukazatel nad ovládací prvek.|  
|`MouseEnter`|`void OnMouseEnter(EventArgs)`|Vyvoláno, když ukazatel poprvé vstoupí oblasti ovládacího prvku.|  
|`MouseHover`|`void OnMouseHover(EventArgs)`|Vyvoláno, když ukazatel myši setrvá na ovládacím prvku.|  
|`MouseLeave`|`void OnMouseLeave(EventArgs)`|Vyvoláno, když ukazatel opustí oblasti ovládacího prvku.|  
|`MouseMove`|`void OnMouseMove(MouseEventArgs)`|Vyvolá se při přesunutí ukazatele myši do oblasti ovládacího prvku.|  
|`MouseUp`|`void OnMouseUp(MouseEventArgs)`|Vyvoláno, když se uvolní tlačítko myši, zatímco je ukazatel myši nad ovládací prvek nebo ukazatel opustí oblasti ovládacího prvku.|  
  
 Následující fragment kódu ukazuje příklad přepsání <xref:System.Windows.Forms.Control.MouseDown> událostí.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#7)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#7)]  
  
 Následující fragment kódu ukazuje příklad přepsání <xref:System.Windows.Forms.Control.MouseMove> událostí.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#8)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#8)]  
  
 Následující fragment kódu ukazuje příklad přepsání <xref:System.Windows.Forms.Control.MouseUp> událostí.  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#9](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#9)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#9](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#9)]  
  
 Pro úplný zdrojový kód pro `FlashTrackBar` ukázkový, přečtěte si téma [postupy: vytvoření Windows Forms ovládací prvek, že zobrazuje průběh](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
## <a name="see-also"></a>Viz také  
 [Události v ovládacích prvcích Windows Forms](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)  
 [Definování události](../../../../docs/framework/winforms/controls/defining-an-event-in-windows-forms-controls.md)  
 [Události](../../../../docs/standard/events/index.md)  
 [Uživatelský vstup ve Windows Forms](../../../../docs/framework/winforms/user-input-in-windows-forms.md)
