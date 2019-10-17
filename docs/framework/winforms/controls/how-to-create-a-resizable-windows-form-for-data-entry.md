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
ms.openlocfilehash: aeab1b506b9ded4c3c2ab527f07a8655a44cad2b
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/16/2019
ms.locfileid: "72396029"
---
# <a name="how-to-create-a-resizable-windows-form-for-data-entry"></a>Postupy: Vytvoření formuláře Windows s možností změny velikosti pro zadávání dat
Dobré rozložení reaguje na změny v dimenzích svého nadřazeného formuláře. Pomocí ovládacího prvku <xref:System.Windows.Forms.TableLayoutPanel> můžete uspořádat rozložení formuláře tak, aby se změnila velikost a umístění ovládacích prvků konzistentním způsobem, jakým se mění rozměry formuláře. Ovládací prvek <xref:System.Windows.Forms.TableLayoutPanel> je také užitečný v případě, že změny v obsahu ovládacích prvků způsobují změny v rozložení. Proces popsaný v tomto postupu lze provést v prostředí sady Visual Studio.  Viz také [Návod: Vytvoření formuláře Windows s možností změny velikosti pro zadávání dat](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100)).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak použít ovládací prvek <xref:System.Windows.Forms.TableLayoutPanel> k sestavení rozložení, které reaguje na to, kdy uživatel změní velikost formuláře. Ukazuje také rozložení, které reaguje dobře na lokalizaci.  
  
 [!code-cpp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/cpp/basicdataentryform.cpp#1)]
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/CS/basicdataentryform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/VB/basicdataentryform.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení System, System. data, System. Drawing a System. Windows. Forms.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.FlowLayoutPanel>
- <xref:System.Windows.Forms.TableLayoutPanel>
- [Postupy: Ukotvení podřízených ovládacích prvků v ovládacím prvku TableLayoutPanel](how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)
- [Postupy: Návrh rozložení Windows Forms, jež odpovídá lokalizaci](how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)
