---
title: "Postupy: Seskupování ovládacích prvků pomocí ovládacího prvku Windows Forms GroupBox"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [Windows Forms], grouping
- GroupBox control [Windows Forms], grouping controls
- Windows Forms controls, grouping
ms.assetid: 0bda316d-bd2a-43aa-ac73-342453303169
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 50d29de04b4e221105bb02e58de01344f13af69f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-group-controls-with-the-windows-forms-groupbox-control"></a>Postupy: Seskupování ovládacích prvků pomocí ovládacího prvku Windows Forms GroupBox
Windows Forms <xref:System.Windows.Forms.GroupBox> ovládací prvky slouží k seskupení další ovládací prvky. Existují tři důvodů, proč seskupování ovládacích prvků:  
  
-   Chcete-li vytvořit visual seskupení prvků související formuláře pro zrušte uživatelské rozhraní.  
  
-   Chcete-li vytvořit programový seskupení (přepínačů, např.).  
  
-   Pro přesun ovládací prvky jako jednotku v době návrhu.  
  
### <a name="to-create-a-group-of-controls"></a>Chcete-li vytvořit skupinu ovládacích prvků  
  
1.  Kreslení <xref:System.Windows.Forms.GroupBox> prvek na formuláři.  
  
2.  Přidání dalších ovládacích prvků do pole skupiny kreslení každý uvnitř pole skupiny.  
  
     Pokud máte stávající ovládací prvky, které chcete uzavřete ve skupinovém rámečku, můžete vybrat všechny ovládací prvky, je vyjmout data do schránky, vyberte <xref:System.Windows.Forms.GroupBox> řízení a pak je vložte do pole skupiny. Můžete je také přetáhnout do pole skupiny.  
  
3.  Nastavte <xref:System.Windows.Forms.GroupBox.Text%2A> vlastnost pole skupiny do příslušné titulek.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.GroupBox>  
 [Groupbox – ovládací prvek](../../../../docs/framework/winforms/controls/groupbox-control-windows-forms.md)
