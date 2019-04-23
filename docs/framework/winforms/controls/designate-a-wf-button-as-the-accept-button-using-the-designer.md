---
title: 'Postupy: Určení tlačítka Windows Forms pro funkci tlačítka Přijmout pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- buttons [Windows Forms], default on Windows Forms
- Accept button on Windows Forms
- Button control [Windows Forms], designating as default
- Windows Forms controls, default button on form
ms.assetid: a1da0590-755f-49f2-aca7-609fac6351bf
ms.openlocfilehash: e0eaa90c8450888ea325470db5d4adae555f8d82
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59304165"
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button-using-the-designer"></a>Postupy: Určení tlačítka Windows Forms pro funkci tlačítka Přijmout pomocí Návrháře
Na formuláři Windows, můžete určit <xref:System.Windows.Forms.Button> ovládacího prvku tlačítko Přijmout, označované také jako výchozího tlačítka. Pokaždé, když uživatel stiskne klávesu ENTER, výchozí je stisknuto tlačítko bez ohledu na to, který má jiný ovládací prvek ve formuláři fokus. Výjimky jsou při ovládací prvek fokus je jiný tlačítko – v takovém případě bude kliknutí na tlačítko s fokusem – nebo víceřádkovém textovém poli, nebo vlastní ovládací prvek, který zachycuje klávesu ENTER.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-designate-the-accept-button"></a>Chcete-li určit tlačítka přijmout  
  
1. Vyberte formulář, na kterém je umístěn tlačítku.  
  
2. V **vlastnosti** okno, nastavte formuláře <xref:System.Windows.Forms.Form.AcceptButton%2A> vlastnost <xref:System.Windows.Forms.Button> název ovládacího prvku.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Form.AcceptButton%2A>
- [Přehled ovládacího prvku Button](button-control-overview-windows-forms.md)
- [Metody výběru ovládacího prvku Windows Forms Button](ways-to-select-a-windows-forms-button-control.md)
- [Postupy: Reakce na kliknutí na tlačítko Windows Forms](how-to-respond-to-windows-forms-button-clicks.md)
- [Postupy: Určení tlačítka Windows Forms pro funkci tlačítka Storno pomocí návrháře](designate-a-wf-button-as-the-cancel-button-using-the-designer.md)
- [Ovládací prvek Button](button-control-windows-forms.md)
