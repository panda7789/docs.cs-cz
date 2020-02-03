---
title: 'Postupy: Roztažení prvku ToolStripTextBox k zaplnění zbývající šířky prvku ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text boxes [Windows Forms], stretching in ToolStrip control [Windows Forms]
- ToolStrip control [Windows Forms], stretching a text box
ms.assetid: 0e610fbf-85fe-414c-900c-9704a5dd5cc6
ms.openlocfilehash: c60cc2a377f08a73159f25b2ab5f2812d41f0c10
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742839"
---
# <a name="how-to-stretch-a-toolstriptextbox-to-fill-the-remaining-width-of-a-toolstrip-windows-forms"></a>Postupy: Roztažení prvku ToolStripTextBox k vyplnění zbývající šířky prvku ToolStrip (Windows Forms)
Když nastavíte vlastnost <xref:System.Windows.Forms.ToolStrip.Stretch%2A> ovládacího prvku <xref:System.Windows.Forms.ToolStrip> na `true`, ovládací prvek vyplní svůj kontejner od konce až do konce a změní velikost kontejneru při změně velikosti kontejneru. V této konfiguraci může být užitečné roztáhnout položku v ovládacím prvku, jako je například <xref:System.Windows.Forms.ToolStripTextBox>, vyplnit dostupný prostor a změnit velikost ovládacího prvku. Toto roztažení je užitečné, například pokud chcete dosáhnout vzhledu a chování podobného adresnímu řádku v aplikaci Microsoft® Internet Explorer.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu poskytuje třídu odvozenou z <xref:System.Windows.Forms.ToolStripTextBox> s názvem `ToolStripSpringTextBox`. Tato třída přepisuje metodu <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A> pro výpočet dostupné šířky nadřazeného ovládacího prvku <xref:System.Windows.Forms.ToolStrip> poté, co byla odečtena kombinovaná šířka všech ostatních položek. Tento příklad kódu poskytuje také třídu <xref:System.Windows.Forms.Form> a třídu `Program`, která demonstruje nové chování.  
  
 [!code-csharp[ToolStripSpringTextBox#00](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripSpringTextBox/cs/ToolStripSpringTextBox.cs#00)]
 [!code-vb[ToolStripSpringTextBox#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripSpringTextBox/vb/ToolStripSpringTextBox.vb#00)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení System, System. Drawing a System. Windows. Forms.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStrip.Stretch%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripTextBox>
- <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A?displayProperty=nameWithType>
- [Architektura ovládacího prvku ToolStrip](toolstrip-control-architecture.md)
- [Postupy: Interaktivní používání vlastnosti Spring v prvku StatusStrip](how-to-use-the-spring-property-interactively-in-a-statusstrip.md)
