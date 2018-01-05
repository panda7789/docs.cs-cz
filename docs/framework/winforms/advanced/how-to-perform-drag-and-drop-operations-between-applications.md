---
title: "Postupy: Provádění operací přetažení mezi aplikacemi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: drag and drop [Windows Forms], between applications
ms.assetid: fa347436-2b12-4dd6-8507-59d7241f6a06
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 514c283575ca54e74d23ae31d3590979be2c3ef0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-perform-drag-and-drop-operations-between-applications"></a>Postupy: Provádění operací přetažení mezi aplikacemi
Provádění operací přetažení myší mezi aplikacemi se nejsou jiné než povolíte tuto akci v aplikaci, tak dlouho, dokud obě aplikace související se situací chovat podle "smlouva" navázat mezi <xref:System.Windows.Forms.DragEventArgs.AllowedEffect%2A> a <xref:System.Windows.Forms.DragEventArgs.Effect%2A> Vlastnosti.  
  
 V následujícím postupu budete používat aplikace pro systém Windows, které vytvoříte a WordPad textový editor, která je součástí operačního systému Windows k provádění operací přetažení myší mezi aplikacemi. WordPad má určitou sadu povolených důsledky pro text se přetáhnout; aplikace pro systém Windows, které budete psát kód pro bude fungovat s těchto důsledcích tak, aby operací přetažení myší může úspěšně dokončena.  
  
### <a name="to-perform-a-drag-and-drop-procedure-between-applications"></a>Postup a přetažení mezi aplikacemi  
  
1.  Vytvořte novou aplikaci Windows Forms.  
  
2.  Přidat <xref:System.Windows.Forms.TextBox> ovládacího prvku do svého formuláře.  
  
3.  Konfigurace <xref:System.Windows.Forms.TextBox> řízení přijímat vynechaných data.  
  
     Další informace najdete v tématu [návod: provádění operace přetažení myší ve Windows Forms](../../../../docs/framework/winforms/advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md).  
  
4.  Spusťte aplikaci systému Windows a když aplikace běží, spusťte WordPad.  
  
     WordPad je textový editor, nainstalovaná v systému Windows, který umožňuje operací přetažení myší. Je dostupné po stisknutí **spustit** tlačítko výběru **spustit**a zadáním `WordPad` do textového pole **spustit** dialogové okno a kliknutím na tlačítko **OK**.  
  
5.  Jakmile WordPad je otevřený, zadejte řetězec textu do ní.  
  
6.  Pomocí myši, vyberte text a poté přetáhněte vybraný text přes k <xref:System.Windows.Forms.TextBox> ovládací prvek v aplikaci systému Windows.  
  
     Všimněte při umístění ukazatele myši <xref:System.Windows.Forms.TextBox> ovládací prvek (a v důsledku toho vyvolat <xref:System.Windows.Forms.Control.DragEnter> událostí), změní a mohou vyřadit vybraný text do <xref:System.Windows.Forms.TextBox> ovládacího prvku.  
  
     Kromě toho můžete nakonfigurovat vaše <xref:System.Windows.Forms.TextBox> řízení umožňující textové řetězce do přetahování do WordPad. Další informace najdete v tématu [návod: provádění operace přetažení myší ve Windows Forms](../../../../docs/framework/winforms/advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md).  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Přidání dat do schránky](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)  
 [Postupy: Načtení dat ze schránky](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)  
 [Operace přetažení a podpora schránky](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)
