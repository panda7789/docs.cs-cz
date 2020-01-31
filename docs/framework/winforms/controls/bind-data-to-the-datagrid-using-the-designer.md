---
title: Svázání dat s ovládacím prvkem DataGridView pomocí návrháře
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, binding to a data source
- data sources [Windows Forms], binding to Windows Forms controls
- DataGridView control [Windows Forms], data binding
ms.assetid: f4f46009-cec2-441b-8668-6b5af057558b
ms.openlocfilehash: d5fab6acc53e5b8be247e958bdba78f0d3647fdc
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744112"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control-using-the-designer"></a>Postupy: Vytvoření vazby dat k ovládacímu prvku Windows Forms DataGridView pomocí Návrháře
Pomocí návrháře můžete propojit ovládací prvek <xref:System.Windows.Forms.DataGridView> se zdroji dat několika různých odrůd, včetně databází, obchodních objektů a webových služeb. Při navázání ovládacího prvku na zdroj dat pomocí návrháře je ovládací prvek automaticky svázán s <xref:System.Windows.Forms.BindingSource> komponentou, která představuje zdroj dat. Kromě toho se sloupce automaticky generují v ovládacím prvku tak, aby odpovídaly informacím schématu poskytnutým zdrojem dat.

 Po vygenerování sloupců je můžete upravit tak, aby vyhovovaly vašim potřebám. Můžete například odebrat nebo skrýt sloupce, které se nezobrazují, můžete změnit uspořádání sloupců nebo můžete upravit typy sloupců. Další informace o úpravách sloupců najdete v tématech uvedených v části Viz také.

 Můžete také vytvořit propojení více <xref:System.Windows.Forms.DataGridView>ch ovládacích prvků se souvisejícími tabulkami a vytvořit tak relace hlavní/podrobnosti. V této konfiguraci jeden ovládací prvek zobrazí nadřazenou tabulku a jiný ovládací prvek zobrazí pouze řádky z podřízené tabulky, které souvisejí s aktuálním řádkem v nadřazené tabulce. Další informace najdete v tématu [Postup: zobrazení souvisejících dat v aplikaci model Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/57tx3hhe(v=vs.120)).

 Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje ovládací prvek <xref:System.Windows.Forms.DataGridView> nebo dva ovládací prvky pro relaci hlavní/podrobnosti. Informace o spuštění takového projektu naleznete v tématu [How to: Create a model Windows Forms Application Project](/visualstudio/ide/step-1-create-a-windows-forms-application-project) a [How to: Add a controls to model Windows Forms](how-to-add-controls-to-windows-forms.md).

## <a name="to-bind-the-control-to-a-data-source"></a>Svázání ovládacího prvku se zdrojem dat

1. V pravém horním rohu ovládacího prvku <xref:System.Windows.Forms.DataGridView> klikněte na glyf inteligentních značek (![glyf inteligentních značek](./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")).

2. Klikněte na šipku rozevíracího seznamu u možnosti **Zvolit zdroj dat** .

3. Pokud projekt ještě nemá zdroj dat, klikněte na **Přidat zdroj dat projektu** a postupujte podle kroků uvedených v průvodci.

     Další informace najdete v tématu [Průvodce konfigurací zdroje dat](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/w4dd7z6t(v=vs.120)). Nový zdroj dat se zobrazí v rozevíracím okně **Zvolit zdroj dat** . Pokud nový zdroj dat obsahuje pouze jednoho člena, například jedinou databázovou tabulku, bude ovládací prvek automaticky svázán s tímto členem. V opačném případě pokračujte k dalšímu kroku.

4. Rozbalte **Další uzly zdroje dat** a **zdroje dat projektu** , pokud ještě nejsou rozbalené, a pak vyberte zdroj dat, ke kterému chcete ovládací prvek navazovat.

5. Pokud zdroj dat obsahuje více než jednoho člena, například pokud jste vytvořili <xref:System.Data.DataSet?displayProperty=nameWithType>, který obsahuje více tabulek, rozbalte zdroj dat a pak vyberte konkrétního člena, ke kterému se má vytvořit vazba.

6. Chcete-li vytvořit relaci hlavního a podrobností, v rozevíracím okně **Zvolit zdroj dat** pro druhý ovládací prvek <xref:System.Windows.Forms.DataGridView> rozbalte <xref:System.Windows.Forms.BindingSource> vytvořenou pro nadřazenou tabulku a pak v zobrazeném seznamu vyberte související podřízenou tabulku.

    > [!NOTE]
    > Pokud projekt již obsahuje zdroj dat, můžete také použít okno **zdroje dat** k vytvoření datového formuláře. Další informace naleznete v tématu [okno zdroje dat](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/6ckyxa83(v=vs.120)).

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.DataGridView.DataMember%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- [Postupy: připojení k datům v databázi](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fxk9yw1t(v=vs.120))
- [Postupy: Přidávání a odebírání sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [Postupy: Změna pořadí sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře](change-the-order-of-columns-in-the-datagrid-using-the-designer.md)
- [Postupy: Změna typu sloupce Windows Forms DataGridView pomocí Návrháře](change-the-type-of-a-wf-datagridview-column-using-the-designer.md)
- [Postupy: Zablokování sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře](freeze-columns-in-the-datagrid-using-the-designer.md)
- [Postupy: Skrytí sloupců v ovládacím prvku Windows Forms DataGridView pomocí Návrháře](hide-columns-in-the-datagrid-using-the-designer.md)
- [Postupy: Převedení sloupců do režimu jen pro čtení v ovládacím prvku Windows Forms DataGridView pomocí Návrháře](make-columns-read-only-in-the-datagrid-using-the-designer.md)
- [Postupy: vytvoření projektu model Windows Forms aplikace](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Postupy: Přidávání ovládacích prvků do Windows Forms](how-to-add-controls-to-windows-forms.md)
- [Okno zdroje dat](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/6ckyxa83(v=vs.120))
- [Postupy: zobrazení souvisejících dat v aplikaci model Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/57tx3hhe(v=vs.120))
