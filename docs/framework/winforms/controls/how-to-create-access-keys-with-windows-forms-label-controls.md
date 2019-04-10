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
ms.openlocfilehash: ffe4bf6fb29e82b04938e2ba9a2d9d21e5eabcde
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59314305"
---
# <a name="how-to-create-access-keys-with-windows-forms-label-controls"></a>Postupy: Vytváření přístupových klíčů pomocí ovládacích prvků Windows Forms Label
Windows Forms <xref:System.Windows.Forms.Label> ovládací prvky lze použít k definování přístupové klíče pro ostatní ovládací prvky. Při definování přístupový klíč v ovládacím prvku popisek, může uživatel stisknout klávesy ALT a znak, který určíte přesunout fokus na ovládací prvek, který následuje v pořadí. Protože popisků nemůže být vybrán, automaticky aktivuje další ovládací prvek v pořadí karet. Tento postup použijte k přiřazení přístupových klíčů a textová pole, pole se seznamem, pole se seznamem datových mřížkách.  
  
### <a name="to-assign-an-access-key-to-a-control-with-a-label"></a>K přiřazení přístupový klíč k ovládacímu prvku s popiskem  
  
1. Nejprve vykreslení popisku a nakreslete jiný ovládací prvek.  
  
     -nebo-  
  
     Vykreslení ovládacích prvků v libovolném pořadí a nastavit <xref:System.Windows.Forms.Control.TabIndex%2A> popisku na jeden menší než druhý ovládací prvek.  
  
2. Nastavte jeho <xref:System.Windows.Forms.Label.UseMnemonic%2A> vlastnost `true`.  
  
3. Použít znak ampersand (&) v popisku <xref:System.Windows.Forms.Label.Text%2A> vlastnost má být přiřazena přístupový klíč pro popisek. Další informace najdete v tématu [vytváření klíčů pro Windows Forms řízení přístupu](how-to-create-access-keys-for-windows-forms-controls.md).  
  
    > [!NOTE]
    >  Můžete chtít zobrazit tyto znaky v ovládacím prvku popisek, nikoli jejich používání při vytváření přístupových klíčů. To může dojít, pokud vytvoření vazby ovládacího prvku popisku na pole v sadě záznamů, pokud data obsahují tyto znaky. Chcete-li tyto znaky zobrazit v ovládacím prvku popisek, nastavte <xref:System.Windows.Forms.Label.UseMnemonic%2A> vlastnost `false`. Pokud si chcete zobrazit tyto znaky a mít taky přístupový kód, nastavte <xref:System.Windows.Forms.Label.UseMnemonic%2A> vlastnost `true` a přístupový klíč se jeden znak ampersand (&) a ampersand k zobrazení mají tyto dva znaky.  
  
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

- [Postupy: Určení velikosti ovládacího prvku Windows Forms Label k zobrazení jeho obsahu](how-to-size-a-windows-forms-label-control-to-fit-its-contents.md)
- [Přehled ovládacího prvku Label](label-control-overview-windows-forms.md)
- [Ovládací prvek Label](label-control-windows-forms.md)
