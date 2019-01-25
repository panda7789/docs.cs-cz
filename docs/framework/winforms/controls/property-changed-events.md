---
title: Události změny vlastnosti
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- custom controls [Windows Forms], property changes (using code)
- properties [Windows Forms], changes
ms.assetid: 268039ec-5aaa-4d76-b902-acccb036c850
ms.openlocfilehash: d02c6f6f3b5a3add7d78f6c3813a36d08b2b9cb3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54584854"
---
# <a name="property-changed-events"></a>Události změny vlastnosti
Pokud chcete, aby ovládací prvek k odesílání oznámení, když vlastnost s názvem *PropertyName* změny, definovat událost s názvem *PropertyName* `Changed` a metodu s názvem `On` *PropertyName* `Changed` , která vyvolává událost. Zásady vytváření názvů v modelu Windows Forms je připojit slovo *změněné* k názvu vlastnosti. Typ delegáta přidružené události pro události změny vlastnosti je <xref:System.EventHandler>, a datový typ události je <xref:System.EventArgs>. Základní třída <xref:System.Windows.Forms.Control> definuje mnoho události změny vlastnosti, jako například <xref:System.Windows.Forms.Control.BackColorChanged>, <xref:System.Windows.Forms.Control.BackgroundImageChanged>, <xref:System.Windows.Forms.Control.FontChanged>, <xref:System.Windows.Forms.Control.LocationChanged>a další. Základní informace o událostech, naleznete v tématu [události](../../../../docs/standard/events/index.md) a [události v ovládacích prvcích Windows Forms](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md).  
  
 Události změny vlastnosti jsou užitečné, protože umožňují uživatelům ovládací prvek připojte obslužné rutiny událostí, které reagují na změnu. Pokud váš ovládací prvek reagovat na události změny vlastnosti, která vyvolá, přepište odpovídající `On` *PropertyName* `Changed` metoda místo připojením delegáta k události. Ovládací prvek je obvykle reakce na událost změny vlastnosti, aktualizují se ostatní vlastnosti nebo překreslování některé nebo všechny jeho návrhovém povrchu.  
  
 Následující příklad ukazuje způsob, jakým `FlashTrackBar` vlastní ovládací prvek reagovat na některé události změny vlastnosti, které dědí z <xref:System.Windows.Forms.Control>. Úplnou ukázku najdete v tématu [jak: Vytvoření ovládacího prvku Windows Forms zobrazujícího průběh](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md).  
  
 [!code-csharp[System.Windows.Forms.FlashTrackBar#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/CS/FlashTrackBar.cs#2)]
 [!code-vb[System.Windows.Forms.FlashTrackBar#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.FlashTrackBar/VB/FlashTrackBar.vb#2)]  
  
## <a name="see-also"></a>Viz také:
- [Události](../../../../docs/standard/events/index.md)
- [Události v ovládacích prvcích Windows Forms](../../../../docs/framework/winforms/controls/events-in-windows-forms-controls.md)
- [Vlastnosti v ovládacích prvcích Windows Forms](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)
