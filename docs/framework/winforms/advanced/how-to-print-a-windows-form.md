---
title: 'Postupy: Tisk formuláře Windows'
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
ms.openlocfilehash: 85fb12028687578b76e0f16061deb9b9a4de70e3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62003974"
---
# <a name="how-to-print-a-windows-form"></a>Postupy: Tisk formuláře Windows
Jako součást procesu vývoje obvykle chcete vytisknout kopii formuláře Windows. Následující příklad kódu ukazuje, jak vytisknout kopii aktuálního formuláře pomocí <xref:System.Drawing.Graphics.CopyFromScreen%2A> metody.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Drawing.Graphics.CopyFromScreen#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.Graphics.CopyFromScreen#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Graphics.CopyFromScreen/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Toto je příklad úplného kódu, který obsahuje `Main` metoda.  
  
## <a name="robust-programming"></a>Robustní programování  
 Následující podmínky mohou způsobit výjimku:  
  
- Nemáte oprávnění k přístupu k tiskárně.  
  
- Není nainstalovaná žádná tiskárna.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Chcete-li spustit tento příklad kódu, musíte mít oprávnění k přístupu k tiskárně, které používáte s počítačem.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Drawing.Printing.PrintDocument>
- [Postupy: Vykreslení obrázků pomocí GDI +](how-to-render-images-with-gdi.md)
- [Postupy: Tisk grafiky ve Windows Forms](how-to-print-graphics-in-windows-forms.md)
