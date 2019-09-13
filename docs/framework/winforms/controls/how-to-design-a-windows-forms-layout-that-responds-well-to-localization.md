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
ms.openlocfilehash: c1aa62413e1c9cc29507b7b0ed5cbf1c5fcea26a
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70928559"
---
# <a name="how-to-design-a-windows-forms-layout-that-responds-well-to-localization"></a>Postupy: Návrh rozložení Windows Forms, jež odpovídá lokalizaci
Vytváření formulářů, které jsou připravené k lokalizaci, významně zrychluje vývoj pro mezinárodní trhy. <xref:System.Windows.Forms.TableLayoutPanel> Ovládací prvek můžete použít k implementaci rozložení, která budou reagovat řádným způsobem při změně velikosti ovládacích prvků <xref:System.Windows.Forms.Control.Text%2A> v důsledku změn hodnot vlastností.  
  
## <a name="example"></a>Příklad  
 Tento formulář ukazuje, jak vytvořit rozložení, které se přizpůsobí při převodu zobrazených řetězcových hodnot do jiných jazyků. Tento proces překladu se nazývá *lokalizace*. Další informace najdete v tématu [lokalizace](../../../standard/globalization-localization/localization.md).  
  
 Existuje Rozsáhlá podpora pro tento úkol v aplikaci Visual Studio.  Viz také [Návod: Vytvoření rozložení, které přizpůsobí proporce pro lokalizaci](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7k9fa71y(v=vs.100)).  
  
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/CS/localizableform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.LocalizableForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.LocalizableForm/VB/localizableform.vb#1)]  
  
## <a name="additional-resources"></a>Další zdroje

1. [Postupy: Zarovnání a roztažení ovládacího prvku v ovládacím prvku TableLayoutPanel](how-to-align-and-stretch-a-control-in-a-tablelayoutpanel-control.md)  
  
2. [Návod: Uspořádání ovládacích prvků na model Windows Forms pomocí FlowLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  

3. [Postupy: Rozpětí řádků a sloupců v ovládacím prvku TableLayoutPanel](how-to-span-rows-and-columns-in-a-tablelayoutpanel-control.md)  
  
4. [Postupy: Úprava sloupců a řádků v ovládacím prvku TableLayoutPanel](how-to-edit-columns-and-rows-in-a-tablelayoutpanel-control.md)  
  
5. [Návod: Provádění běžných úloh pomocí inteligentních značek v ovládacích prvcích model Windows Forms](performing-common-tasks-using-smart-tags-on-wf-controls.md)  
  
6. [Návod: Uspořádání ovládacích prvků na model Windows Forms pomocí kontejneru TableLayoutPanel](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  

7. [Návod: Rozložení model Windows Forms ovládacích prvků s odsazením, okraji a vlastností AutoSize](windows-forms-controls-padding-autosize.md)  
  
8. [Postupy: Podpora lokalizace na model Windows Forms pomocí AutoSize a ovládacího prvku TableLayoutPanel](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/1zkt8b33(v=vs.100))  
  
9. [Návod: Vytvoření formuláře Windows s možností změny velikosti pro zadávání dat](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/991eahec(v=vs.100))  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení System, System. data, System. Drawing a System. Windows. Forms.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.TableLayoutPanel>
- <xref:System.Windows.Forms.FlowLayoutPanel>
- [Lokalizace](../../../standard/globalization-localization/localization.md)
