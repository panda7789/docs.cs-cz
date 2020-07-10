---
title: 'Postupy: Tisk formuláře Windows Form'
description: Naučte se programově tisknout kopii aktuálního formuláře Windows pomocí metody CopyFromScreen.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, printing
- printing [Windows Forms]
- printing a form
- printing [Windows Forms], printing a form
ms.assetid: c8dff5f8-f56a-4c07-ae31-64643b31f8fc
ms.openlocfilehash: b59ea4b5347903b36a166c4f8ac0d8d7db18635e
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174689"
---
# <a name="how-to-print-a-windows-form"></a>Postupy: Tisk formuláře Windows Form
V rámci procesu vývoje obvykle budete chtít vytisknout kopii formuláře Windows. Následující příklad kódu ukazuje, jak vytisknout kopii aktuálního formuláře pomocí <xref:System.Drawing.Graphics.CopyFromScreen%2A> metody.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Drawing.Graphics.CopyFromScreen#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Graphics.CopyFromScreen#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/VB/Form1.vb#1)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
- Nemáte oprávnění pro přístup k tiskárně.  
  
- Není nainstalovaná žádná tiskárna.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Aby bylo možné spustit tento příklad kódu, musíte mít oprávnění pro přístup k tiskárně, kterou používáte s vaším počítačem.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Drawing.Printing.PrintDocument>
- [Postupy: Vykreslení obrázků pomocí GDI+](how-to-render-images-with-gdi.md)
- [Postupy: Tisk grafiky v modelu Windows Forms](how-to-print-graphics-in-windows-forms.md)
