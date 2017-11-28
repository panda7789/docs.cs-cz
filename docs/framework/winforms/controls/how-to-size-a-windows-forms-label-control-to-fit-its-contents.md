---
title: "Postupy: Určení velikosti ovládacího prvku popisku Windows Forms k zobrazení jeho obsahu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- captions [Windows Forms], sizing
- sizing controls
- size [Windows Forms], controls
- labels [Windows Forms], sizing to fit contents
- Label control [Windows Forms], sizing to fit contents
ms.assetid: 99648964-63b2-438c-980e-d24103ad602b
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bd89d72264e5837d2c41fcb0ab024a7b16f4205b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-size-a-windows-forms-label-control-to-fit-its-contents"></a>Postupy: Určení velikosti ovládacího prvku popisku Windows Forms k zobrazení jeho obsahu
Windows Forms <xref:System.Windows.Forms.Label> ovládací prvek může být v jednom nebo více řádky, a může být buď pevnou velikost nebo můžete automaticky měnit velikost pro umístění titulek. <xref:System.Windows.Forms.Label.AutoSize%2A> Vlastnost umožňuje ovládacích prvků k přizpůsobení titulků větší nebo menší velikost, která je zvlášť užitečné, pokud titulek se změní za běhu.  
  
### <a name="to-make-a-label-control-resize-dynamically-to-fit-its-contents"></a>Chcete-li ovládací prvek popisek dynamicky Změna velikosti podle obsahu  
  
1.  Nastavte její <xref:System.Windows.Forms.Label.AutoSize%2A> vlastnost `true`.  
  
 Pokud <xref:System.Windows.Forms.Label.AutoSize%2A> je nastaven na `false`, slova zadaný v <xref:System.Windows.Forms.Label.Text%2A> vlastnost budou zahrnovat na další řádek Pokud je to možné, ale ovládací prvek nebude zvětšovat.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: vytváření přístupových klíčů pomocí ovládacích prvků Windows Forms Label](../../../../docs/framework/winforms/controls/how-to-create-access-keys-with-windows-forms-label-controls.md)  
 [Přehled ovládacího prvku popisek](../../../../docs/framework/winforms/controls/label-control-overview-windows-forms.md)  
 [Popisek – ovládací prvek](../../../../docs/framework/winforms/controls/label-control-windows-forms.md)
