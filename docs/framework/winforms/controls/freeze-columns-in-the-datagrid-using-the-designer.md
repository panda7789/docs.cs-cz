---
title: 'Postupy: Ukotvit sloupce v ovládacím prvku Windows Forms DataGridView pomocí návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, columns
- columns [Windows Forms], freezing
- DataGridView control [Windows Forms], column freezing
- data [Windows Forms], displaying
ms.assetid: 87412dd2-478f-4751-af87-dafc591fc215
ms.openlocfilehash: e3581390a56e2dfd19ed0d760a618993ec124bfb
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57716840"
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control-using-the-designer"></a>Postupy: Ukotvit sloupce v ovládacím prvku Windows Forms DataGridView pomocí návrháře
Když uživatelé zobrazit data zobrazená ve Windows Forms <xref:System.Windows.Forms.DataGridView> ovládacího prvku, někdy potřebují často odkazovat na jeden sloupec nebo sadu sloupců. Například při zobrazení informací o zákaznících, který obsahuje mnoho sloupců tabulky je užitečný pro zobrazované jméno zákazníka po celou dobu při povolení další sloupce mimo viditelná oblast.  
  
 K dosažení tohoto chování, lze ukotvit sloupce v ovládacím prvku. Po ukotvení sloupce jsou zmražená i všechny sloupce na levé straně (nebo vpravo v skripty jazyka zprava doleva). Zmrazené sloupce zůstanou na místě, zatímco všechny ostatní sloupce můžete posouvat. Pokud je zapnutá změnu pořadí sloupců, zmrazené sloupce jsou považovány za skupiny, která se liší od nezmrazeném sloupci. Uživatelům můžete přemístit sloupce v jedné skupině, ale sloupce z jedné skupiny nemůže přesunout do jiné.  
  
 Následující postup vyžaduje, **aplikace Windows** projektu s formulář obsahující <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Informace o nastavení takový projekt, naleznete v tématu [jak: Vytvoření projektu aplikace Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) a [jak: Přidání ovládacích prvků Windows Forms](how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-freeze-a-column-using-the-designer"></a>Chcete-li ukotvit sloupce pomocí návrháře  
  
1.  Klikněte na inteligentní označit piktogram (![piktogram inteligentní](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) v pravém horním rohu <xref:System.Windows.Forms.DataGridView> ovládací prvek a potom vyberte **upravit sloupce**.  
  
2.  Vyberte sloupec **vybrané sloupce** seznamu.  
  
3.  V **vlastnosti sloupce** mřížky, nastavte <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> vlastnost `true`.  
  
    > [!NOTE]
    >  Můžete také ukotvit sloupec při přidávání tak, že vyberete **Frozen** pole **přidat sloupec** dialogové okno.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>
- [Postupy: Přidávání a odebírání sloupců v ovládacím prvku Windows Forms DataGridView pomocí návrháře](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [Postupy: Povolení změny pořadí sloupců v ovládacím prvku Windows Forms DataGridView pomocí návrháře](enable-column-reordering-in-the-datagrid-using-the-designer.md)
- [Postupy: Zobrazení textu zprava doleva v modelu Windows Forms pro globalizaci](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/7d3337xw(v=vs.100))
- [Postupy: Vytvoření projektu aplikace Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Postupy: Přidání ovládacích prvků do formulářů Windows](how-to-add-controls-to-windows-forms.md)
