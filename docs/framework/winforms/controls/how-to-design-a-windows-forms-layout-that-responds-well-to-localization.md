---
title: 'Postupy: Návrh rozložení Windows Forms, jež odpovídá lokalizaci'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms]
- application design [Windows Forms], localization
- Windows Forms, localization
- localization [Windows Forms], Windows Forms layout
ms.assetid: d13eff2d-701c-4b6e-8838-3885cbfb7223
ms.openlocfilehash: 131dc688d2a742fa7a0d99ec7858d4e280c9882f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59310756"
---
# <a name="how-to-design-a-windows-forms-layout-that-responds-well-to-localization"></a>Postupy: Návrh rozložení Windows Forms, jež odpovídá lokalizaci
Vytvoření formulářů, které jsou připravené k odeslání lokalizovaných výrazně rychlosti vývoje pro mezinárodní trhy. Můžete použít <xref:System.Windows.Forms.TableLayoutPanel> ovládacího prvku k implementaci rozložení, která reagovat bez výpadku, jak změnit velikost ovládacích prvků z důvodu změn v jejich <xref:System.Windows.Forms.Control.Text%2A> hodnot vlastností.  
  
## <a name="example"></a>Příklad  
 Tento formulář ukazuje, jak vytvořit rozložení, která se přizpůsobí proporcionálně při překlad zobrazené řetězcové hodnoty do jiných jazyků. Tento proces překladu se nazývá *lokalizace*. Další informace najdete v tématu [lokalizace](../../../standard/globalization-localization/localization.md).  
  
 Není k dispozici rozsáhlou podporu pro tuto úlohu v sadě Visual Studio.  Viz také [názorný postup: Vytvoření rozložení, jež upravuje proporce pro lokalizaci](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100)).  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/CS/localizableform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/VB/localizableform.vb#1)]  
  
## <a name="additional-resources"></a>Další zdroje
1. [Postupy: Zarovnání a roztažení ovládacího prvku v ovládacím prvku TableLayoutPanel](how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control.md)  
  
2. [Návod: Uspořádání ovládacích prvků na formuláři Windows s použitím ovládacího prvku FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  

3. [Postupy: Rozpětí řádků a sloupců v ovládacím prvku TableLayoutPanel](how-to-span-rows-and-columns-in-a-tablelayoutpanel-control.md)  
  
4. [Postupy: Upravování sloupců a řádků v ovládacím prvku TableLayoutPanel](how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control.md)  
  
5. [Návod: Provádění obecných úloh pomocí inteligentních značek na Windows Forms ovládací prvky](performing-common-tasks-using-smart-tags-on-wf-controls.md)  
  
6. [Návod: Uspořádání ovládacích prvků na formuláři Windows s použitím ovládacího prvku TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  

7. [Návod: Vytváření rozložení Windows Forms ovládací prvky s odsazením, okraji a s vlastností AutoSize](windows-forms-controls-padding-autosize.md)  
  
8. [Postupy: Podpora lokalizace ve formulářích Windows pomocí AutoSize a TableLayoutPanel – ovládací prvek](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/1zkt8b33(v=vs.100))  
  
9. [Návod: Vytvoření formuláře Windows s možností změny velikosti pro zadávání dat](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na sestavení systému, System.Data, System.Drawing a System.Windows.Forms.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
- [Lokalizace](../../../standard/globalization-localization/localization.md)
