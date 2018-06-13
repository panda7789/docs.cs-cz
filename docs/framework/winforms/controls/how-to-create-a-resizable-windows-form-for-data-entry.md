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
ms.openlocfilehash: a7768b3c6be10373e742cbeea0028d1aee0b261d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531788"
---
# <a name="how-to-create-a-resizable-windows-form-for-data-entry"></a>Postupy: Vytvoření formuláře Windows s možností změny velikosti pro zadávání dat
Dobrý rozložení odpovídá změny v dimenzích jeho nadřazeného formuláře. Můžete použít <xref:System.Windows.Forms.TableLayoutPanel> řízení uspořádat rozložení svého formuláře na velikost a umístit vaše ovládací prvky v konzistentní způsob jako změnu dimenze formuláře. <xref:System.Windows.Forms.TableLayoutPanel> Ovládací prvek je také užitečné v případě změny v obsahu pro vaše ovládací prvky příčina změny v rozložení. Proces zahrnutých v rámci tohoto postupu lze provést v prostředí Visual Studio.  Viz také [návod: vytvoření formuláře Windows s možností změny velikosti pro zadávání dat](http://msdn.microsoft.com/library/991eahec\(v=vs.110\)).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat <xref:System.Windows.Forms.TableLayoutPanel> řízení k vytvoření rozložení, který odpovídá dobře, když uživatel změní velikost formuláře. Také ukazuje rozložení, který odpovídá lokalizaci.  
  
 [!code-cpp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/cpp/basicdataentryform.cpp#1)]
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/CS/basicdataentryform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/VB/basicdataentryform.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na systém, System.Data, System.Drawing a System.Windows.Forms sestavení.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic a Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit zadáním nebo vložením kódu do nového projektu.  Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [Postupy: Ukotvení podřízených ovládacích prvků v ovládacím prvku TableLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [Postupy: Návrh rozložení Windows Forms, jež odpovídá lokalizaci](../../../../docs/framework/winforms/controls/how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)  
 [Uživatelské prostředí pro Microsoft Windows, oficiální pokyny pro uživatelské rozhraní vývojářů a návrhářů. Brno: Společnosti Microsoft Press, 1999. (USBN: 0-7356-0566-1)](http://www.microsoft.com/mspress/southpacific/books/book11588.htm)
