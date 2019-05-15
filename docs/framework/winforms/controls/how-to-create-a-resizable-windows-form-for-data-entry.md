---
title: 'Postupy: Vytvoření formuláře Windows Forms s možností změny velikosti pro zadávání dat'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms]
- layout [Windows Forms], resizing
- forms [Windows Forms], creating resizable
- Windows Forms, resizable
ms.assetid: babdf198-404c-485d-a914-ed370c6ecd99
ms.openlocfilehash: 1b27c0e67aae1935c4216654d9f3ddf557719572
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65588936"
---
# <a name="how-to-create-a-resizable-windows-form-for-data-entry"></a>Postupy: Vytvoření formuláře Windows Forms s možností změny velikosti pro zadávání dat
Dobré rozložení odpovídá změny v dimenzích jeho nadřazený formulář. Můžete použít <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku na upravte si rozložení formuláře pro změnit velikost a umístění ovládacích prvků běžely jako změnu rozměrů formuláře. <xref:System.Windows.Forms.TableLayoutPanel> Ovládací prvek je také užitečné v případě změny v obsahu své ovládací prvky příčina změny v rozložení. Proces popsané v tomto postupu můžete provést v rámci prostředí sady Visual Studio.  Viz také [názorný postup: Vytvoření formuláře Windows s možností změny velikosti pro zadávání dat](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100)).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku k vytvoření rozložení, které dobře reaguje, když uživatel změní velikost formuláře. Ukazuje také rozložení, jež odpovídá lokalizaci.  
  
 [!code-cpp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/cpp/basicdataentryform.cpp#1)]
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/CS/basicdataentryform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/VB/basicdataentryform.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení systému, System.Data, System.Drawing a System.Windows.Forms.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [Postupy: Ukotvení a podřízených ovládacích prvků v ovládacím prvku TableLayoutPanel](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [Postupy: Návrh rozložení Windows Forms, jež odpovídá lokalizaci](how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)
- [Microsoft Windows uživatelské prostředí, oficiální pokyny pro uživatelské rozhraní vývojářů a návrhářů. Redmond, WA: Microsoft Press, 1999. (USBN: 0-7356-0566-1)](https://www.microsoft.com/mspress/southpacific/books/book11588.htm)
