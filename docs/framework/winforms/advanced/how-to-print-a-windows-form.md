---
title: "Postupy: Tisk formuláře Windows Form"
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
- Windows Forms, printing
- printing [Windows Forms]
- printing a form
- printing [Windows Forms], printing a form
ms.assetid: c8dff5f8-f56a-4c07-ae31-64643b31f8fc
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8c50b1f47d207334160ed12674ee8efb1390fb84
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-print-a-windows-form"></a>Postupy: Tisk formuláře Windows Form
Jako součást procesu vývoje obvykle můžete vytisknout kopii svého formuláře systému Windows. Následující příklad kódu ukazuje, jak chcete vytisknout kopii aktuálního formuláře pomocí <xref:System.Drawing.Graphics.CopyFromScreen%2A> metoda.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Drawing.Graphics.CopyFromScreen#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Graphics.CopyFromScreen#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Toto je příklad dokončení kódu, který obsahuje `Main` metoda.  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
-   Nemáte oprávnění k přístupu k tiskárně.  
  
-   Neexistuje žádné nainstalovanou tiskárnu.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Chcete-li spustit tento příklad kódu, musí mít oprávnění k přístupu k tiskárně, které používáte pro váš počítač.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Drawing.Printing.PrintDocument>  
 [Postupy: Vykreslení obrázků pomocí GDI+](../../../../docs/framework/winforms/advanced/how-to-render-images-with-gdi.md)  
 [Postupy: Tisk grafiky v modelu Windows Forms](../../../../docs/framework/winforms/advanced/how-to-print-graphics-in-windows-forms.md)
