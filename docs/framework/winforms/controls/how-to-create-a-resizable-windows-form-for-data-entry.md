---
title: 'Postupy: Vytvoření formuláře Windows s možností změny velikosti pro zadávání dat'
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
ms.openlocfilehash: a319fba43c6735cd5552dd71d1fb614a6192da97
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/15/2018
ms.locfileid: "45645707"
---
# <a name="how-to-create-a-resizable-windows-form-for-data-entry"></a>Postupy: Vytvoření formuláře Windows s možností změny velikosti pro zadávání dat
Dobré rozložení odpovídá změny v dimenzích jeho nadřazený formulář. Můžete použít <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku na upravte si rozložení formuláře pro změnit velikost a umístění ovládacích prvků běžely jako změnu rozměrů formuláře. <xref:System.Windows.Forms.TableLayoutPanel> Ovládací prvek je také užitečné v případě změny v obsahu své ovládací prvky příčina změny v rozložení. Proces popsané v tomto postupu můžete provést v rámci prostředí sady Visual Studio.  Viz také [návod: vytvoření formuláře Windows umožňující změnu velikosti pro zadávání dat](https://msdn.microsoft.com/library/991eahec\(v=vs.110\)).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku k vytvoření rozložení, které dobře reaguje, když uživatel změní velikost formuláře. Ukazuje také rozložení, jež odpovídá lokalizaci.  
  
 [!code-cpp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/cpp/basicdataentryform.cpp#1)]
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/CS/basicdataentryform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/VB/basicdataentryform.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na sestavení systému, System.Data, System.Drawing a System.Windows.Forms.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.  Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [Postupy: Ukotvení podřízených ovládacích prvků v ovládacím prvku TableLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [Postupy: Návrh rozložení Windows Forms, jež odpovídá lokalizaci](../../../../docs/framework/winforms/controls/how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)  
 [Microsoft Windows uživatelské prostředí, oficiální pokyny pro uživatelské rozhraní vývojářů a návrhářů. Redmond, WA: Microsoft Press, 1999. (USBN: 0-7356-0566-1)](https://www.microsoft.com/mspress/southpacific/books/book11588.htm)
