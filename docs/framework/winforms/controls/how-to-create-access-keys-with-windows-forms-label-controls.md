---
title: Vytváření přístupových klíčů pomocí ovládacích prvků popisek
ms.date: 03/30/2017
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
ms.openlocfilehash: 800afc03e71435e2721456b93bb9704af01f714a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731047"
---
# <a name="how-to-create-access-keys-with-windows-forms-label-controls"></a>Postupy: Vytváření přístupových klíčů pomocí ovládacích prvků Windows Forms Label
Ovládací prvky model Windows Forms <xref:System.Windows.Forms.Label> lze použít k definování přístupových klíčů pro jiné ovládací prvky. Při definování přístupového klíče v ovládacím prvku popisek může uživatel stisknout klávesu ALT a znak, který určíte, chcete-li přesunout fokus na ovládací prvek, který následuje v pořadí prvků. Vzhledem k tomu, že popisky nemohou získat fokus, fokus se automaticky přesune na další ovládací prvek v pořadí prvků. Tento postup slouží k přiřazení přístupových kláves k textovým polím, polím se seznamem, seznamům a datovým mřížkám.  
  
### <a name="to-assign-an-access-key-to-a-control-with-a-label"></a>Přiřazení přístupového klíče k ovládacímu prvku s popiskem  
  
1. Nejprve nakreslete popisek a potom nakreslete druhý ovládací prvek.  
  
     -nebo-  
  
     Nakreslete ovládací prvky v libovolném pořadí a nastavte vlastnost <xref:System.Windows.Forms.Control.TabIndex%2A> popisku na hodnotu menší, než je ten jiný ovládací prvek.  
  
2. Nastavte vlastnost <xref:System.Windows.Forms.Label.UseMnemonic%2A> popisku na hodnotu `true`.  
  
3. Pomocí ampersandu (&) ve vlastnosti <xref:System.Windows.Forms.Label.Text%2A> popisku přiřaďte přístupový klíč pro popisek. Další informace najdete v tématu [vytváření přístupových klíčů pro ovládací prvky model Windows Forms](how-to-create-access-keys-for-windows-forms-controls.md).  
  
    > [!NOTE]
    > V ovládacím prvku popisek možná budete chtít zobrazit ampersandy namísto použití pro vytváření přístupových klíčů. K této chybě může dojít, Pokud svážete ovládací prvek popisek s polem v sadě záznamů, kde data obsahují ampersandy. Chcete-li v ovládacím prvku popisek zobrazit ampersandy, nastavte vlastnost <xref:System.Windows.Forms.Label.UseMnemonic%2A> na hodnotu `false`. Pokud chcete zobrazit ampersandy a také přístupový klíč, nastavte vlastnost <xref:System.Windows.Forms.Label.UseMnemonic%2A> na `true` a označte přístupový klíč jedním ampersandem (&) a ampersandem, který se má zobrazit dvěma ampersandy.  
  
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

- [Postupy: Určení velikosti ovládacího prvku Windows Forms Label k zobrazení jeho obsahu](how-to-size-a-windows-forms-label-control-to-fit-its-contents.md)
- [Přehled ovládacího prvku Label](label-control-overview-windows-forms.md)
- [Ovládací prvek Label](label-control-windows-forms.md)
