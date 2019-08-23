---
title: 'Postupy: Vytváření přístupových klíčů pomocí ovládacích prvků Windows Forms Label'
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
ms.openlocfilehash: dd7f238f8c20ba990158f23344e36376d3b1cb7a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950536"
---
# <a name="how-to-create-access-keys-with-windows-forms-label-controls"></a>Postupy: Vytváření přístupových klíčů pomocí ovládacích prvků Windows Forms Label
Ovládací <xref:System.Windows.Forms.Label> prvky model Windows Forms lze použít k definování přístupových klíčů pro jiné ovládací prvky. Při definování přístupového klíče v ovládacím prvku popisek může uživatel stisknout klávesu ALT a znak, který určíte, chcete-li přesunout fokus na ovládací prvek, který následuje v pořadí prvků. Vzhledem k tomu, že popisky nemohou získat fokus, fokus se automaticky přesune na další ovládací prvek v pořadí prvků. Tento postup slouží k přiřazení přístupových kláves k textovým polím, polím se seznamem, seznamům a datovým mřížkám.  
  
### <a name="to-assign-an-access-key-to-a-control-with-a-label"></a>Přiřazení přístupového klíče k ovládacímu prvku s popiskem  
  
1. Nejprve nakreslete popisek a potom nakreslete druhý ovládací prvek.  
  
     -nebo-  
  
     Nakreslete ovládací prvky v libovolném pořadí a nastavte <xref:System.Windows.Forms.Control.TabIndex%2A> vlastnost popisku na hodnotu menší, než je ten jiný ovládací prvek.  
  
2. Nastavte <xref:System.Windows.Forms.Label.UseMnemonic%2A> vlastnost popisku na `true`.  
  
3. Pomocí ampersandu (&) ve <xref:System.Windows.Forms.Label.Text%2A> vlastnosti Label přiřaďte přístupový klíč pro popisek. Další informace najdete v tématu [vytváření přístupových klíčů pro ovládací prvky model Windows Forms](how-to-create-access-keys-for-windows-forms-controls.md).  
  
    > [!NOTE]
    > V ovládacím prvku popisek možná budete chtít zobrazit ampersandy namísto použití pro vytváření přístupových klíčů. K této chybě může dojít, Pokud svážete ovládací prvek popisek s polem v sadě záznamů, kde data obsahují ampersandy. Chcete-li v ovládacím prvku popisek zobrazit ampersandy <xref:System.Windows.Forms.Label.UseMnemonic%2A> , nastavte `false`vlastnost na hodnotu. Pokud chcete zobrazit ampersandy a také mít přístupový klíč, nastavte <xref:System.Windows.Forms.Label.UseMnemonic%2A> vlastnost na `true` a označte přístupový klíč jedním ampersandem (&) a ampersand pro zobrazení dvěma ampersandy.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Postupy: Velikost ovládacího prvku popisku model Windows Forms podle jeho obsahu](how-to-size-a-windows-forms-label-control-to-fit-its-contents.md)
- [Přehled ovládacího prvku Label](label-control-overview-windows-forms.md)
- [Ovládací prvek Label](label-control-windows-forms.md)
