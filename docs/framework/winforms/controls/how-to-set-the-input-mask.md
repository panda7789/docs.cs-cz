---
title: 'Postupy: Nastavení vstupní masky'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.MaskPropertyEditor
helpviewer_keywords:
- MaskedTextBox control [Windows Forms]
ms.assetid: 779b3a12-cd74-4e58-b46e-04983bda5b2c
ms.openlocfilehash: 6f554c239e3444db5f6ac84f7994108ac70df0a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-set-the-input-mask"></a>Postupy: Nastavení vstupní masky
Maskované textové pole je prvek pole rozšířené text, který podporuje deklarativní syntaxe pro přijetí nebo odmítnutí vstup uživatele. Nastavením vlastnosti maska můžete povolená uživatelský vstup bez nutnosti psaní veškeré logiky vlastního ověřování ve vaší aplikaci. Další informace najdete v části poznámky <xref:System.Windows.Forms.MaskedTextBox> třídy.  
  
## <a name="setting-the-mask-property-manually"></a>Nastavení vlastnosti maska ručně  
 Pokud jste obeznámeni s znaky, které podporuje vlastnost maska, můžete ji zadat ručně. Souhrn znaků, které podporuje vlastnost maska, najdete v části poznámky <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> vlastnost.  
  
#### <a name="to-set-the-mask-property-manually"></a>Chcete-li ručně nastavit vlastnost maska  
  
1.  V **návrhu** zobrazení, vyberte <xref:System.Windows.Forms.MaskedTextBox>.  
  
2.  V **vlastnosti** okno, vyhledejte <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> vlastnost.  
  
3.  Zadejte masku, který chcete. Můžete například zadat `###`.  
  
## <a name="using-the-input-mask-dialog-box"></a>Pomocí dialogového okna vstupní maska  
 Vstupní maska dialogové okno obsahuje několik předdefinovaných vstupní masky. Můžete také změnit předdefinované masek nebo zadejte vlastní masku ručně.  
  
#### <a name="to-open-the-input-mask-dialog-box"></a>Chcete-li otevřít dialogové okno Vstupní maska  
  
1.  V **návrhu** zobrazení, vyberte <xref:System.Windows.Forms.MaskedTextBox>.  
  
    1.  Klikněte na inteligentní značky otevřete **MaskedTextBox úlohy** panelu.  
  
    2.  Klikněte na tlačítko **nastavit maska**.  
  
     \- nebo –  
  
    1.  V **vlastnosti** vyberte <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> vlastnost.  
  
    2.  Klikněte na tlačítko se třemi tečkami ve sloupci Hodnota vlastnosti.  
  
     **Vstupní maska** zobrazí se dialogové okno.  
  
#### <a name="to-use-the-input-mask-dialog-box"></a>Chcete-li pomocí dialogového okna vstupní maska  
  
1.  (Volitelné) Klikněte na jednu z předdefinovaných masky v seznamu.  
  
2.  (Volitelné) Upravit předdefinované maska ve **maska** pole.  
  
3.  (Volitelné) Zadejte masku nové v **maska** pole. To znamená, že nemáte použijte jeden z předdefinovaných masky.  
  
    > [!NOTE]
    >  V poli Náhled zobrazí znaky, které uživateli se zobrazí v <xref:System.Windows.Forms.MaskedTextBox>. Tyto znaky jsou Průvodce pomoct uživateli zadat data správně.  
  
4.  Vyberte nebo zrušte **použití ValidatingType** zaškrtávací políčko. **Použití ValidatingType** políčko určuje, jestli používá datový typ ověření vstupu dat uživatelem. Další informace najdete v tématu <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> vlastnost.  
  
5.  Click **OK**.  
  
     Maska je zadána v **maska** vlastnost **vlastnosti** okno.  
  
## <a name="see-also"></a>Viz také  
 [Návod: Práce s ovládacím prvkem MaskedTextBox](../../../../docs/framework/winforms/controls/walkthrough-working-with-the-maskedtextbox-control.md)
