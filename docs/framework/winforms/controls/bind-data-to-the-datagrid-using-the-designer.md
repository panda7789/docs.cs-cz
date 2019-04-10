---
title: 'Postupy: Vytvoření vazby dat k ovládacímu prvku Windows Forms DataGridView pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, binding to a data source
- data sources [Windows Forms], binding to Windows Forms controls
- DataGridView control [Windows Forms], data binding
ms.assetid: f4f46009-cec2-441b-8668-6b5af057558b
ms.openlocfilehash: 59a025535e850cf3c773a2a078511d41058bb24c
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59321845"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control-using-the-designer"></a>Postupy: Vytvoření vazby dat k ovládacímu prvku Windows Forms DataGridView pomocí Návrháře
Návrhář slouží k připojení <xref:System.Windows.Forms.DataGridView> ovládací prvek zdroje dat z několika různých typy, včetně databází, business objektů nebo webové služby. Když se navážete na zdroj dat pomocí návrháře ovládací prvek, ovládací prvek automaticky svázán s <xref:System.Windows.Forms.BindingSource> komponenta, která představuje zdroj dat. Kromě toho sloupce jsou automaticky generovány v ovládacím prvku tak, aby odpovídaly schématu na základě informací poskytnutých zdroj dat.  
  
 Po vygenerování sloupců, můžete upravit tak, aby splňovaly vaše potřeby. Například můžete odebrat nebo skrýt sloupce vás nezajímají v zobrazení, můžete změnit uspořádání sloupců nebo upravíte typy sloupců. Další informace o změnách sloupců najdete v tématech uvedených v části Viz také.  
  
 Můžete také navázat více <xref:System.Windows.Forms.DataGridView> ovládacích prvků pro tabulky v relaci k vytváření záznamů master/detail vztahů. V této konfiguraci jeden ovládací prvek zobrazí nadřazené tabulky a další ovládací prvek zobrazí pouze řádky z podřízené tabulky, které se vztahují k aktuální řádek v nadřazené tabulce. Další informace najdete v tématu [jak: Zobrazení souvisejících dat v Windows Forms aplikace](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/57tx3hhe(v=vs.120)).  
  
 Následující postup vyžaduje, **aplikace Windows** projektu, který obsahuje formulář <xref:System.Windows.Forms.DataGridView> ovládací prvek nebo pro vztah záznamů master/detail dvou ovládacích prvků. Informace o spuštění tohoto projektu naleznete v tématu [jak: Vytvoření projektu aplikace Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project) a [jak: Přidání ovládacích prvků Windows Forms](how-to-add-controls-to-windows-forms.md).  
  
> [!NOTE]
>  Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici. Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-bind-the-control-to-a-data-source"></a>K vytvoření vazby ovládacího prvku do zdroje dat.  
  
1. Klikněte na inteligentní označit piktogram (![piktogram inteligentní](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) v pravém horním rohu <xref:System.Windows.Forms.DataGridView> ovládacího prvku.  
  
2. Klikněte na šipku rozevíracího seznamu pro **zvolit zdroj dat** možnost.  
  
3. Pokud váš projekt již nemá žádné zdroje dat, klikněte na tlačítko **přidat zdroj dat projektu** a postupujte podle kroků uvedených v průvodci.  
  
     Další informace najdete v tématu [Průvodce konfigurací zdroje dat](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/w4dd7z6t(v=vs.120)). Nový zdroj dat se zobrazí v **zvolit zdroj dat** okno rozevíracího seznamu. Pokud nový zdroj dat obsahuje pouze jednoho člena, jako je například tabulka izolované databáze, ovládací prvek automaticky svázán s tohoto člena. V opačném případě pokračujte k dalšímu kroku.  
  
4. Rozbalte **jiných zdrojů dat** a **zdroje dat projektu** uzly dojde k jejich není rozbalen a pak vyberte zdroj dat pro vytvoření vazby ovládacího prvku.  
  
5. Pokud zdroj dat obsahuje více než jednoho člena, třeba když jste vytvořili <xref:System.Data.DataSet?displayProperty=nameWithType> , který obsahuje více tabulek, rozbalení zdroje dat a pak vyberte konkrétní členu, který chcete vytvořit vazbu k.  
  
6. K vytvoření vztahu záznamů master/detail v **zvolit zdroj dat** rozevírací okno pro sekundy <xref:System.Windows.Forms.DataGridView> řídit, rozbalte <xref:System.Windows.Forms.BindingSource> vytvořené pro nadřazenou tabulku a pak vyberte také související podřízené tabulky ze seznamu Zobrazit.  
  
    > [!NOTE]
    >  Pokud váš projekt již má zdroj dat, můžete také použít **zdroje dat** okno Vytvoření dat formuláře. Další informace najdete v tématu [okna zdroje dat](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/6ckyxa83(v=vs.120)).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.DataGridView.DataMember%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- [Postupy: Připojení k datům v databázi](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fxk9yw1t(v=vs.120))
- [Postupy: Přidávání a odebírání sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [Postupy: Změna pořadí sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře](change-the-order-of-columns-in-the-datagrid-using-the-designer.md)
- [Postupy: Změna typu sloupce Windows Forms DataGridView pomocí Návrháře](change-the-type-of-a-wf-datagridview-column-using-the-designer.md)
- [Postupy: Zablokování sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře](freeze-columns-in-the-datagrid-using-the-designer.md)
- [Postupy: Skrytí sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře](hide-columns-in-the-datagrid-using-the-designer.md)
- [Postupy: Převedení sloupců do režimu jen pro čtení v ovládacím prvku Windows Forms DataGridView pomocí Návrháře](make-columns-read-only-in-the-datagrid-using-the-designer.md)
- [Postupy: Vytvoření projektu aplikace Windows Forms](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Postupy: Přidávání ovládacích prvků do Windows Forms](how-to-add-controls-to-windows-forms.md)
- [Okno Zdroje dat](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/6ckyxa83(v=vs.120))
- [Postupy: Zobrazení souvisejících dat ve formulářové aplikaci Windows](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/57tx3hhe(v=vs.120))
