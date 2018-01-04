---
title: "Postupy: Určení tlačítka Windows Forms pro funkci tlačítka Přijmout pomocí Návrháře"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- buttons [Windows Forms], default on Windows Forms
- Accept button on Windows Forms
- Button control [Windows Forms], designating as default
- Windows Forms controls, default button on form
ms.assetid: a1da0590-755f-49f2-aca7-609fac6351bf
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ba7b6f8ff44763c19de1eac6d4be98bca75ff9f7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-designate-a-windows-forms-button-as-the-accept-button-using-the-designer"></a>Postupy: Určení tlačítka Windows Forms pro funkci tlačítka Přijmout pomocí Návrháře
Na všechny formuláře Windows, můžete určit <xref:System.Windows.Forms.Button> ovládacího prvku tlačítko Přijmout, také známé jako výchozího tlačítka. Vždy, když uživatel stiskne klávesu ENTER, výchozí je stisknuto tlačítko bez ohledu na to, které další ovládací prvek na formuláři fokus. Výjimky pro tento jsou jiné tlačítko po ovládací prvek fokus – v takovém případě bude kliknutí na tlačítko s fokusem – nebo víceřádkové textové pole, nebo vlastní ovládací prvek, který traps klávesu ENTER.  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-designate-the-accept-button"></a>K určení přijmout  
  
1.  Vyberte formuláře, na kterém se nachází na tlačítko.  
  
2.  V **vlastnosti** nastavte formuláře <xref:System.Windows.Forms.Form.AcceptButton%2A> vlastnost, která má <xref:System.Windows.Forms.Button> název ovládacího prvku.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Form.AcceptButton%2A>  
 [Přehled ovládacího prvku Button](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [Metody výběru ovládacího prvku Windows Forms Button](../../../../docs/framework/winforms/controls/ways-to-select-a-windows-forms-button-control.md)  
 [Postupy: Reakce na kliknutí na tlačítko Windows Forms](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [Postupy: Určení tlačítka Windows Forms pro funkci tlačítka Zrušit pomocí Návrháře](../../../../docs/framework/winforms/controls/designate-a-wf-button-as-the-cancel-button-using-the-designer.md)  
 [Ovládací prvek Button](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
