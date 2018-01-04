---
title: "Přehled ovládacího prvku Tlačítko (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Button
helpviewer_keywords:
- Button control [Windows Forms], about Button control
- buttons [Windows Forms], about buttons
ms.assetid: 255b291b-51a9-4a92-a1a4-2400cd82443f
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e04b99c9d85ae92ad4d013abc01c5b16914fe1c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="button-control-overview-windows-forms"></a>Přehled ovládacího prvku Tlačítko (Windows Forms)
Windows Forms <xref:System.Windows.Forms.Button> řízení umožňuje uživateli klikněte na něj k provedení akce. Při kliknutí na tlačítko efekt stisknuté a vydání. Vždy, když uživatel klikne tlačítko <xref:System.Windows.Forms.Control.Click> je volána obslužná rutina události. Umístit kód <xref:System.Windows.Forms.Control.Click> obslužné rutiny události provádět veškeré akce, které zvolíte.  
  
 Text zobrazovaný na tlačítko se nachází v <xref:System.Windows.Forms.Control.Text%2A> vlastnost. Pokud text přesahuje šířku tlačítko, budou zahrnovat na další řádek. Však bude oříznut Pokud ovládací prvek neumožňuje celkové výšku. Další informace najdete v tématu [postupy: nastavení zobrazí Text pomocí ovládacího prvku Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md). <xref:System.Windows.Forms.Control.Text%2A> Vlastnost může obsahovat přístupový klíč, který umožňuje uživateli "Kliknutím" ovládacího prvku stisknutím klávesy ALT přístupovým klíčem. Podrobnosti najdete v tématu [postupy: vytvoření přístup klíčů pro Windows Forms – ovládací prvky](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md). Řídí vzhled text <xref:System.Windows.Forms.Control.Font%2A> vlastnost a <xref:System.Windows.Forms.ButtonBase.TextAlign%2A> vlastnost.  
  
 <xref:System.Windows.Forms.Button> Řízení lze také zobrazit obrázky pomocí <xref:System.Windows.Forms.ButtonBase.Image%2A> a <xref:System.Windows.Forms.ButtonBase.ImageList%2A> vlastnosti. Další informace najdete v tématu [postupy: nastavení obrázek zobrazit pomocí ovládacího prvku Windows Forms](../../../../docs/framework/winforms/controls/how-to-set-the-image-displayed-by-a-windows-forms-control.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Button>  
 [Postupy: Reakce na kliknutí na tlačítko Windows Forms](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [Metody výběru ovládacího prvku Windows Forms Button](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [Postupy: Určení tlačítka Windows Forms pro funkci tlačítka Přijmout pomocí Návrháře](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-accept-button-using-the-designer.md)  
 [Postupy: Určení tlačítka Windows Forms pro funkci tlačítka Zrušit pomocí Návrháře](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-cancel-button-using-the-designer.md)  
 [Ovládací prvek Button](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
