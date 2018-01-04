---
title: "Postupy: Vytváření přístupových klíčů pomocí ovládacích prvků Windows Forms Label"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], access keys
- dialog box controls [Windows Forms], mnemonics
- access keys [Windows Forms], creating for controls
- Label control [Windows Forms], creating access keys
- mnemonics [Windows Forms], adding to dialog box controls
- mnemonics
- Windows Forms controls, access keys
- UseMnemonic property [Windows Forms], Label control
- keyboard shortcuts [Windows Forms], creating for controls
- access keys [Windows Forms], Windows Forms
ms.assetid: 5ee8f823-80be-4a4f-96a4-412671e2e306
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6a856090a76f484c21c1d9982d67e9fdf21e8451
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-access-keys-with-windows-forms-label-controls"></a>Postupy: Vytváření přístupových klíčů pomocí ovládacích prvků Windows Forms Label
Windows Forms <xref:System.Windows.Forms.Label> ovládací prvky můžete použít k definování přístupové klíče pro další ovládací prvky. Když definujete přístupový klíč v ovládacím prvku popisek, může uživatel stisknout klávesy ALT a znak, který určíte přesunout fokus na ovládací prvek, který následuje v pořadí. Protože popisky nemůže přijmout fokus, automaticky aktivuje na další ovládací prvek v pořadí. Tento postup slouží k přiřazení přístupových klíčů k textová pole, pole se seznamem, seznamy a datové mřížky.  
  
### <a name="to-assign-an-access-key-to-a-control-with-a-label"></a>Přiřadit přístupový klíč do ovládacího prvku s popiskem  
  
1.  Nejprve kreslení štítek a potom kreslení další ovládací prvek.  
  
     -nebo-  
  
     Vykreslení ovládacích prvků v libovolném pořadí a nastavte <xref:System.Windows.Forms.Control.TabIndex%2A> vlastnost popisku k jednomu menší než ostatní ovládací prvek.  
  
2.  Nastavte jeho <xref:System.Windows.Forms.Label.UseMnemonic%2A> vlastnost `true`.  
  
3.  Použít znak ampersand (&) v atributu label <xref:System.Windows.Forms.Label.Text%2A> vlastnost přiřadit přístupový klíč pro popisek. Další informace najdete v tématu [vytváření přístup klíčů pro Windows Forms – ovládací prvky](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md).  
  
    > [!NOTE]
    >  Můžete do zobrazení ampersandy v ovládacím prvku popisek, nikoli je použít k vytvoření přístupové klíče. To může dojít, pokud vytvoření vazby ovládací prvek popisek na pole v sadě záznamů, kde data obsahují tyto znaky. Chcete-li zobrazit tyto znaky v ovládacím prvku popisek, nastavte <xref:System.Windows.Forms.Label.UseMnemonic%2A> vlastnost `false`. Pokud chcete zobrazit tyto znaky a také mít přístupový klíč, nastavte <xref:System.Windows.Forms.Label.UseMnemonic%2A> vlastnost, která má `true` a uvést přístupového klíče s jeden ampersand (&) a ampersand zobrazíte s dva tyto znaky.  
  
    ```vb  
    Label1.UseMnemonic = True  
    Label1.Text = "&Print"  
    Label2.UseMnemonic = True  
    Label2.Text = "&Copy && Paste"  
    ```  
  
    ```csharp  
    label1.UseMnemonic = true;  
    label1.Text = "&Print";  
    label2.UseMnemonic = true;  
    label2.Text = "&Copy && Paste";  
    ```  
  
    ```cpp  
    label1->UseMnemonic = true;  
    label1->Text = "&Print";  
    label2->UseMnemonic = true;  
    label2->Text = "&Copy && Paste";  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Určení velikosti ovládacího prvku Windows Forms Label k zobrazení jeho obsahu](../../../../docs/framework/winforms/controls/how-to-size-a-windows-forms-label-control-to-fit-its-contents.md)  
 [Přehled ovládacího prvku Label](../../../../docs/framework/winforms/controls/label-control-overview-windows-forms.md)  
 [Ovládací prvek Label](../../../../docs/framework/winforms/controls/label-control-windows-forms.md)
