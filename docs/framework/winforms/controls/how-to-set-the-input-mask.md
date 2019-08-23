---
title: 'Postupy: Nastavení vstupní masky'
ms.date: 03/30/2017
f1_keywords:
- net.ComponentModel.MaskPropertyEditor
helpviewer_keywords:
- MaskedTextBox control [Windows Forms]
ms.assetid: 779b3a12-cd74-4e58-b46e-04983bda5b2c
ms.openlocfilehash: 06dee48765653ac7a659246cc3dfe865c795ca21
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949138"
---
# <a name="how-to-set-the-input-mask"></a>Postupy: Nastavení vstupní masky
Ovládací prvek maskovaná textová pole je vylepšený ovládací prvek textového pole, který podporuje deklarativní syntaxi pro přijetí nebo odmítnutí vstupu uživatele. Nastavením vlastnosti maska můžete zadat povolený vstup uživatele bez psaní jakékoli vlastní ověřovací logiky v aplikaci. Další informace naleznete v oddílu <xref:System.Windows.Forms.MaskedTextBox> poznámky třídy.  
  
## <a name="setting-the-mask-property-manually"></a>Ruční nastavení vlastnosti masky  
 Pokud jste obeznámeni se znaky, které vlastnost Mask podporuje, můžete ji zadat ručně. Souhrn znaků, které vlastnost Mask podporuje, naleznete v části <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> poznámky v této vlastnosti.  
  
### <a name="to-set-the-mask-property-manually"></a>Ruční nastavení vlastnosti masky  
  
1. V zobrazení **Návrh** vyberte <xref:System.Windows.Forms.MaskedTextBox>.  
  
2. V okně **vlastnosti** vyhledejte <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> vlastnost.  
  
3. Zadejte masku, kterou chcete. Zadejte například příkaz `###`.  
  
## <a name="using-the-input-mask-dialog-box"></a>Použití dialogového okna vstupní maska  
 Dialogové okno vstupní maska poskytuje některé předdefinované vstupní masky. Můžete také změnit předdefinované masky nebo zadat vlastní masku ručně.  
  
### <a name="to-open-the-input-mask-dialog-box"></a>Otevření dialogového okna vstupní maska  
  
1. V zobrazení **Návrh** vyberte <xref:System.Windows.Forms.MaskedTextBox>.  
  
    1. Kliknutím na inteligentní značku otevřete panel **úlohy ovládacím MaskedTextBox** .  
  
    2. Klikněte na **nastavit masku**.  
  
     \- nebo –  
  
    1. V okně **vlastnosti** vyberte <xref:System.Windows.Forms.MaskedTextBox.Mask%2A> vlastnost.  
  
    2. Klikněte na tlačítko se třemi tečkami ve sloupci Hodnota vlastnosti.  
  
     Zobrazí se dialogové okno **vstupní maska** .  
  
### <a name="to-use-the-input-mask-dialog-box"></a>Použití dialogového okna vstupní maska  
  
1. Volitelné V seznamu klikněte na jednu z předdefinovaných masek.  
  
2. Volitelné Upravte předdefinovanou masku v poli **Maska** .  
  
3. Volitelné Do pole **Maska** zadejte novou masku. To znamená, že nemusíte používat jednu z předdefinovaných masek.  
  
    > [!NOTE]
    > V poli Náhled se zobrazí znaky, které uživatel vidí v <xref:System.Windows.Forms.MaskedTextBox>. Tyto znaky jsou vodítkem, který uživatelům pomůže správně zadat data.  
  
4. Zaškrtněte nebo zrušte zaškrtnutí políčka **Use ValidatingType** . Zaškrtávací políčko **použít ValidatingType** určuje, zda datový typ slouží k ověření datového vstupu uživatelem. Další informace najdete v tématu <xref:System.Windows.Forms.MaskedTextBox.ValidatingType%2A> vlastnost.  
  
5. Klikněte na **OK**.  
  
     Maska se zadává do vlastnosti **Maska** v okně **vlastnosti** .  
  
## <a name="see-also"></a>Viz také:

- [Návod: Práce s ovládacím prvkem ovládacím MaskedTextBox](walkthrough-working-with-the-maskedtextbox-control.md)
