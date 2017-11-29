---
title: "Postupy: Roztažení prvku ToolStripTextBox k vyplnění zbývající šířky prvku ToolStrip (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text boxes [Windows Forms], stretching in ToolStrip control [Windows Forms]
- ToolStrip control [Windows Forms], stretching a text box
ms.assetid: 0e610fbf-85fe-414c-900c-9704a5dd5cc6
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 213929e52f08fff19eb7641092789501c31648e0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-stretch-a-toolstriptextbox-to-fill-the-remaining-width-of-a-toolstrip-windows-forms"></a>Postupy: Roztažení prvku ToolStripTextBox k vyplnění zbývající šířky prvku ToolStrip (Windows Forms)
Když nastavíte <xref:System.Windows.Forms.ToolStrip.Stretch%2A> vlastnost <xref:System.Windows.Forms.ToolStrip> řídit k `true`, ovládacího prvku vyplní celé jeho kontejneru a provést tak kompletní a změní, když se změní jeho kontejneru. V této konfiguraci může být užitečné k roztahování položky v ovládacím prvku, například <xref:System.Windows.Forms.ToolStripTextBox>, vyplňování dostupného místa a velikost, pokud se změní velikost ovládacího prvku. Tato roztažení je užitečné, například, pokud chcete dosáhnout vzhled a chování podobná panelu Adresa v aplikaci Microsoft® Internet Explorer.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu poskytuje třídy odvozené od <xref:System.Windows.Forms.ToolStripTextBox> názvem `ToolStripSpringTextBox`. Tato třída přepsání <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A> metodu pro výpočet dostupná šířka nadřazené <xref:System.Windows.Forms.ToolStrip> řízení po odečtení kombinované šířku všechny ostatní položky. Také poskytuje tento příklad kódu <xref:System.Windows.Forms.Form> třídy a `Program` třída k předvedení nové chování.  
  
 [!code-csharp[ToolStripSpringTextBox#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripSpringTextBox/cs/ToolStripSpringTextBox.cs#00)]
 [!code-vb[ToolStripSpringTextBox#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripSpringTextBox/vb/ToolStripSpringTextBox.vb#00)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na systém, System.Drawing a System.Windows.Forms sestavení.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStrip.Stretch%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripTextBox>  
 <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A?displayProperty=nameWithType>  
 [Architektura ovládacího prvku ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [Postupy: interaktivní používání vlastnosti Spring v prvku StatusStrip](../../../../docs/framework/winforms/controls/how-to-use-the-spring-property-interactively-in-a-statusstrip.md)
