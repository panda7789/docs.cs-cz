---
title: 'Postupy: Povolení změny pořadí sloupců v ovládacím prvku Windows Forms DataGridView pomocí návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], column order
- Windows Forms, columns
- columns [Windows Forms], reordering
- data [Windows Forms], displaying
ms.assetid: d82bd69c-6799-4439-a32c-91139c5901d1
ms.openlocfilehash: a08c15e4fea76d8f6e97db6d463c4141b7d13b4b
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57718828"
---
# <a name="how-to-enable-column-reordering-in-the-windows-forms-datagridview-control-using-the-designer"></a>Postupy: Povolení změny pořadí sloupců v ovládacím prvku Windows Forms DataGridView pomocí návrháře
Při prohlížení dat zobrazovat ve formuláři Windows <xref:System.Windows.Forms.DataGridView> ovládacího prvku, uživatelé někdy chtějí porovnat hodnoty v určité sloupce. To může být vhodná, pokud sloupce, které jsou daleko od v ovládacím prvku, zejména v případě, že uživatelům musí vzájemně vodorovné posouvání, chcete-li zobrazit všechny sloupce, které je zajímají. Můžete vytvořit úkol porovnávání hodnot sloupců jednodušší tím, že umožňuje uživatelům změnit uspořádání sloupců. Když povolíte změnu pořadí sloupců, mohou uživatelé přesouvat sloupec na nové pozici přetažením záhlaví sloupce myší.  
  
 Následující postup vyžaduje, **aplikace Windows** projektu s formulář obsahující <xref:System.Windows.Forms.DataGridView> ovládacího prvku. Informace o nastavení takový projekt, naleznete v tématu [jak: Vytvoření projektu aplikace Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) a [jak: Přidání ovládacích prvků Windows Forms](how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-enable-column-reordering"></a>Povolit změnu pořadí sloupců  
  
-   Klikněte na inteligentní označit piktogram (![piktogram inteligentní](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) v pravém horním rohu <xref:System.Windows.Forms.DataGridView> ovládací prvek a potom vyberte **povolit změnu pořadí sloupců**.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType>
- [Postupy: Ukotvit sloupce v ovládacím prvku Windows Forms DataGridView pomocí návrháře](freeze-columns-in-the-datagrid-using-the-designer.md)
- [Postupy: Vytvoření projektu aplikace Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Postupy: Přidání ovládacích prvků do formulářů Windows](how-to-add-controls-to-windows-forms.md)
