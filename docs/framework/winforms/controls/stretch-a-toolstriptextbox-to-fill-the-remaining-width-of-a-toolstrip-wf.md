---
title: 'Postupy: Roztažení prvku ToolStripTextBox k zaplnění zbývající šířky prvku ToolStrip (Windows Forms)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text boxes [Windows Forms], stretching in ToolStrip control [Windows Forms]
- ToolStrip control [Windows Forms], stretching a text box
ms.assetid: 0e610fbf-85fe-414c-900c-9704a5dd5cc6
ms.openlocfilehash: 707fd2e470a9be1d61d2878eeff845b3cad270db
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59223573"
---
# <a name="how-to-stretch-a-toolstriptextbox-to-fill-the-remaining-width-of-a-toolstrip-windows-forms"></a>Postupy: Roztažení prvku ToolStripTextBox k zaplnění zbývající šířky prvku ToolStrip (Windows Forms)
Při nastavení <xref:System.Windows.Forms.ToolStrip.Stretch%2A> vlastnost <xref:System.Windows.Forms.ToolStrip> mít pod kontrolou `true`, ovládací prvek vyplní svého kontejneru od začátku do konce a velikost přizpůsobí svou velikost svého kontejneru. V této konfiguraci, možná bude užitečné k roztahování položku v ovládacím prvku, například <xref:System.Windows.Forms.ToolStripTextBox>, aby vyplnil dostupné místo a pro změnu velikosti při změní velikost ovládacího prvku. Tato roztažení je užitečné, například, pokud chcete dosáhnout vzhled a chování podobný panelu Adresa v aplikaci Microsoft® Internet Explorer.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu obsahuje třídu odvozenou z <xref:System.Windows.Forms.ToolStripTextBox> volá `ToolStripSpringTextBox`. Tato třída přepíše <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A> metodu pro výpočet dostupná šířka nadřazené <xref:System.Windows.Forms.ToolStrip> řídit po odečtení kombinované šířku všechny ostatní položky. Tento příklad kódu také poskytuje <xref:System.Windows.Forms.Form> třídy a `Program` třídy, na které si předvedeme nové chování.  
  
 [!code-csharp[ToolStripSpringTextBox#00](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripSpringTextBox/cs/ToolStripSpringTextBox.cs#00)]
 [!code-vb[ToolStripSpringTextBox#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripSpringTextBox/vb/ToolStripSpringTextBox.vb#00)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na sestavení systému, System.Drawing a System.Windows.Forms.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStrip.Stretch%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripTextBox>
- <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A?displayProperty=nameWithType>
- [Architektura ovládacího prvku ToolStrip](toolstrip-control-architecture.md)
- [Postupy: Interaktivní používání vlastnosti Spring v prvku StatusStrip](how-to-use-the-spring-property-interactively-in-a-statusstrip.md)
