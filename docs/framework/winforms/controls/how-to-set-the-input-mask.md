---
title: 'Postupy: Nastavení vstupní masky'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.MaskPropertyEditor
helpviewer_keywords:
- MaskedTextBox control [Windows Forms]
ms.assetid: 779b3a12-cd74-4e58-b46e-04983bda5b2c
ms.openlocfilehash: 06eaf68fef167d63e6f8404dd5049f5445881d24
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61912870"
---
# <a name="how-to-set-the-input-mask"></a>Postupy: Nastavení vstupní masky
Maskované textové pole je vylepšené textový ovládací prvek, který podporuje deklarativní syntaxe pro přijetí nebo odmítnutí vstup uživatele. Tím, že nastavíte vlastnost maska, můžete zadat povolenou uživatelský vstup bez nutnosti jakékoli vlastní ověřovací logiky ve vaší aplikaci. Další informace najdete v části poznámky <xref:System.Windows.Forms.MaskedTextBox> třídy.  
  
## <a name="setting-the-mask-property-manually"></a>Vlastnost maska nastavení ručně  
 Pokud jste se seznámili se znaky, které podporuje vlastnost maska, můžete ji zadat ručně. Přehled znaky, které podporuje vlastnost maska, naleznete v části poznámky <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> vlastnost.  
  
#### <a name="to-set-the-mask-property-manually"></a>Chcete-li nastavit vlastnost maska ručně  
  
1. V **návrhu** zobrazení, vyberte <xref:System.Windows.Forms.MaskedTextBox>.  
  
2. V **vlastnosti** okna, vyhledejte <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> vlastnost.  
  
3. Zadejte masku, který chcete. Zadejte například příkaz `###`.  
  
## <a name="using-the-input-mask-dialog-box"></a>Pomocí dialogového okna vstupní maska  
 Vstupní maska dialogové okno obsahuje některé předdefinované vstupní masky. Můžete také změnit předdefinované masky nebo ručně zadejte vlastní masku.  
  
#### <a name="to-open-the-input-mask-dialog-box"></a>Chcete-li otevřít dialogové okno Vstupní maska  
  
1. V **návrhu** zobrazení, vyberte <xref:System.Windows.Forms.MaskedTextBox>.  
  
    1. Kliknutím na inteligentní značku otevřete **MaskedTextBox úlohy** panelu.  
  
    2. Klikněte na tlačítko **nastavení masky**.  
  
     \- nebo –  
  
    1. V **vlastnosti** okna, vyberte <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> vlastnost.  
  
    2. Klikněte na tlačítko se třemi tečkami v sloupec hodnoty vlastnosti.  
  
     **Vstupní maska** zobrazí se dialogové okno.  
  
#### <a name="to-use-the-input-mask-dialog-box"></a>Chcete-li pomocí dialogového okna vstupní maska  
  
1. (Volitelné) Klikněte na jednu z předdefinovaných masky v seznamu.  
  
2. (Volitelné) Upravit předdefinované masky v **maska** pole.  
  
3. (Volitelné) Zadejte nový masku **maska** pole. To znamená, že nemáte použijte jednu z předdefinovaných masky.  
  
    > [!NOTE]
    >  Zobrazí znaky, které uživateli se zobrazí v náhledu <xref:System.Windows.Forms.MaskedTextBox>. Tyto znaky se tento průvodce pomůže uživateli zadat data správně.  
  
4. Zaškrtněte nebo zrušte zaškrtnutí **použít vlastnost ValidatingType** zaškrtávací políčko. **Použít vlastnost ValidatingType** zaškrtávací políčko určuje, zda datový typ se používá k ověření vstupu dat uživatelem. Další informace najdete v tématu <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> vlastnost.  
  
5. Klikněte na **OK**.  
  
     Maska je zadána v **maska** vlastnost **vlastnosti** okna.  
  
## <a name="see-also"></a>Viz také:

- [Návod: Práce s ovládacím prvkem MaskedTextBox](walkthrough-working-with-the-maskedtextbox-control.md)
