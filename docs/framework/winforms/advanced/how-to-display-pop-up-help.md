---
title: 'Postupy: Zobrazení místní nápovědy'
ms.date: 03/30/2017
helpviewer_keywords:
- pop-up Help
- Help [Windows Forms], pop-up Help
- Windows Forms, displaying Help
- forms [Windows Forms], displaying Help
- modal dialog boxes [Windows Forms], pop-up Help
- F1 Help [Windows Forms], in dialog boxes
- HelpProvider component [Windows Forms]
- Help [Windows Forms], adding to dialog boxes
ms.assetid: 218aa81e-e87e-4d67-af05-11627bbdce3b
ms.openlocfilehash: f6b6fa0c111783dcdad0387aed7d40fb54fa7b26
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59078366"
---
# <a name="how-to-display-pop-up-help"></a>Postupy: Zobrazení místní nápovědy
Jedním ze způsobů pro zobrazení nápovědy v modelu Windows Forms je prostřednictvím **pomáhají** tlačítko, se nachází na pravé straně záhlaví, přístupné prostřednictvím <xref:System.Windows.Forms.Form.HelpButton%2A> vlastnost. Tento typ zobrazení nápovědy je velmi vhodná pro použití s dialogových oknech. Dialogová okna zobrazen modálně (s <xref:System.Windows.Forms.Form.ShowDialog%2A> metoda), nedaří spustit až externí Nápověda systémy, protože modálních dialogových oken muset zřejmě zavřít před fokus můžete přesunout do jiného okna. Kromě toho používání **pomáhají** tlačítko vyžaduje, aby existovala žádné **minimalizovat** tlačítko nebo **Maximalizovat** tlačítka zobrazen v záhlaví. Jedná se o standardní dialogové konvenci, zatímco formuláře mají obvykle **minimalizovat** a **Maximalizovat** tlačítka.  
  
 Mějte na paměti, že můžete použít také <xref:System.Windows.Forms.HelpProvider> komponenty propojení ovládacích prvků do souborů v systému nápovědy, i v případě, že jste implementovali místní nápovědy. Další informace najdete v tématu [poskytnutí nápovědy v aplikaci Windows](how-to-provide-help-in-a-windows-application.md).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-display-pop-up-help"></a>K zobrazení místní nápovědy  
  
1.  Přetáhněte [HelpProvider](../controls/helpprovider-component-windows-forms.md) komponentu z panelu nástrojů do formuláře.  
  
     Se nacházejí na hlavním panelu v dolní části Návrháře formulářů Windows.  
  
2.  V okně Vlastnosti nastavte <xref:System.Windows.Forms.Form.HelpButton%2A> vlastnost `true`. Bude se zobrazovat tlačítko s otazníkem ho na pravé straně záhlaví formuláře.  
  
3.  Aby <xref:System.Windows.Forms.Form.HelpButton%2A> k zobrazení formuláře <xref:System.Windows.Forms.Form.MinimizeBox%2A> a <xref:System.Windows.Forms.Form.MaximizeBox%2A> vlastnosti musí být nastavena na `false`, <xref:System.Windows.Forms.Form.ControlBox%2A> vlastnost nastavena na `true`a <xref:System.Windows.Forms.Form.FormBorderStyle%2A> vlastnost na jednu z následujících hodnot: <xref:System.Windows.Forms.FormBorderStyle.FixedSingle> , <xref:System.Windows.Forms.FormBorderStyle.Fixed3D>, <xref:System.Windows.Forms.FormBorderStyle.FixedDialog> nebo <xref:System.Windows.Forms.FormBorderStyle.Sizable>.  
  
4.  Vyberte ovládací prvek, pro kterou chcete zobrazit nápovědu na formuláři a nastavit text nápovědy v okně Vlastnosti. Jedná se o řetězec textu, který se zobrazí v okně podobně jako [popisek](../controls/tooltip-component-windows-forms.md).  
  
5.  Stisknutím klávesy **F5**.  
  
6.  Stisknutím klávesy **pomáhají** tlačítko v záhlaví okna a klepněte na ovládací prvek, na kterém můžete nastavit text nápovědy.  
  
## <a name="see-also"></a>Viz také:

- [Nápověda ovládacího prvku pomocí ToolTips](control-help-using-tooltips.md)
- [Integrace uživatelské nápovědy do formulářů Windows](integrating-user-help-in-windows-forms.md)
- [Windows Forms](../index.md)
