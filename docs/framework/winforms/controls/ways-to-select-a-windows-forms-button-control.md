---
title: "Metody výběru ovládacího prvku Windows Forms Button"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Button control [Windows Forms], selecting
ms.assetid: fe2fc058-5118-4f70-b264-6147d64a7a8d
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0b6fa31b89b8fbe50077933cf04aa3c17db86438
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ways-to-select-a-windows-forms-button-control"></a>Metody výběru ovládacího prvku Windows Forms Button
Tlačítko Windows Forms lze vybrat následujícími způsoby:  
  
-   Klikněte na tlačítko pomocí myši.  
  
-   Vyvolání na tlačítko <xref:System.Windows.Forms.Control.Click> událostí v kódu.  
  
-   Přesun zaměření pro tlačítko stisknutím klávesy TAB a pak zvolte tlačítko stisknutím klávesy MEZERNÍK nebo ENTER.  
  
-   Stisknutím klávesy přístup (ALT + podtržené písmeno) pro tlačítko. Další informace o přístupových klíčů najdete v tématu [postupy: vytvoření přístup klíčů pro Windows Forms – ovládací prvky](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md).  
  
-   Je-li na tlačítko "přijmout" tlačítko ve formuláři, stisknutím klávesy ENTER rozhodne na tlačítko i v případě, že další ovládací prvek fokus – s výjimkou je-li tuto další kontrolu jiné tlačítko, Víceřádkový textového pole nebo vlastní ovládací prvek, který traps klávesu enter.  
  
-   Je-li na tlačítko tlačítko "zrušit" formuláře, stisknutím klávesy ESC zvolí tlačítko, i v případě, že další ovládací prvek fokus.  
  
-   Volání <xref:System.Windows.Forms.Button.PerformClick%2A> metoda vyberte tlačítko prostřednictvím kódu programu.  
  
## <a name="see-also"></a>Viz také  
 [Přehled ovládacího prvku Button](../../../../docs/framework/winforms/controls/button-control-overview-windows-forms.md)  
 [Postupy: Reakce na kliknutí na tlačítko Windows Forms](../../../../docs/framework/winforms/controls/how-to-respond-to-windows-forms-button-clicks.md)  
 [Ovládací prvek Button](../../../../docs/framework/winforms/controls/button-control-windows-forms.md)
