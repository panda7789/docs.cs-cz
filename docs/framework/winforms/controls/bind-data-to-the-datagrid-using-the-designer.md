---
title: 'Postupy: Vytvoření vazby dat k ovládacímu prvku Windows Forms DataGridView pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms controls, binding to a data source
- data sources [Windows Forms], binding to Windows Forms controls
- DataGridView control [Windows Forms], data binding
ms.assetid: f4f46009-cec2-441b-8668-6b5af057558b
ms.openlocfilehash: 609878416be26786ce865168c996c78e18b1897f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917878"
---
# <a name="how-to-bind-data-to-the-windows-forms-datagridview-control-using-the-designer"></a>Postupy: Vytvoření vazby dat k ovládacímu prvku Windows Forms DataGridView pomocí Návrháře
Pomocí návrháře můžete propojit <xref:System.Windows.Forms.DataGridView> ovládací prvek se zdroji dat několika různých odrůd, včetně databází, obchodních objektů a webových služeb. Při svázání ovládacího prvku se zdrojem dat pomocí návrháře je ovládací prvek automaticky svázán <xref:System.Windows.Forms.BindingSource> s komponentou, která představuje zdroj dat. Kromě toho se sloupce automaticky generují v ovládacím prvku tak, aby odpovídaly informacím schématu poskytnutým zdrojem dat.

 Po vygenerování sloupců je můžete upravit tak, aby vyhovovaly vašim potřebám. Můžete například odebrat nebo skrýt sloupce, které se nezobrazují, můžete změnit uspořádání sloupců nebo můžete upravit typy sloupců. Další informace o úpravách sloupců najdete v tématech uvedených v části Viz také.

 Můžete také vytvořit propojení více <xref:System.Windows.Forms.DataGridView> ovládacích prvků se souvisejícími tabulkami a vytvořit tak relace hlavní/podrobnosti. V této konfiguraci jeden ovládací prvek zobrazí nadřazenou tabulku a jiný ovládací prvek zobrazí pouze řádky z podřízené tabulky, které souvisejí s aktuálním řádkem v nadřazené tabulce. Další informace najdete v tématu [jak: Zobrazení souvisejících dat v aplikaci](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/57tx3hhe(v=vs.120))model Windows Forms.

 Následující postup vyžaduje projekt **aplikace systému Windows** s formulářem, který obsahuje <xref:System.Windows.Forms.DataGridView> ovládací prvek nebo dva ovládací prvky pro relaci hlavní/podrobnosti. Informace o spuštění takového projektu naleznete v tématu [How to: Vytvořte projekt](/visualstudio/ide/step-1-create-a-windows-forms-application-project) aplikace model Windows Forms a [postupujte takto: Přidejte ovládací prvky do](how-to-add-controls-to-windows-forms.md)model Windows Forms.

## <a name="to-bind-the-control-to-a-data-source"></a>Svázání ovládacího prvku se zdrojem dat

1. V pravém horním <xref:System.Windows.Forms.DataGridView> rohu ovládacího prvku klikněte na glyf inteligentních značek ((./media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")![glyf inteligentních značek]).

2. Klikněte na šipku rozevíracího seznamu u možnosti **Zvolit zdroj dat** .

3. Pokud projekt ještě nemá zdroj dat, klikněte na **Přidat zdroj dat projektu** a postupujte podle kroků uvedených v průvodci.

     Další informace najdete v tématu [Průvodce konfigurací zdroje dat](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/w4dd7z6t(v=vs.120)). Nový zdroj dat se zobrazí v rozevíracím okně **Zvolit zdroj dat** . Pokud nový zdroj dat obsahuje pouze jednoho člena, například jedinou databázovou tabulku, bude ovládací prvek automaticky svázán s tímto členem. V opačném případě pokračujte k dalšímu kroku.

4. Rozbalte **Další uzly zdroje dat** a **zdroje dat projektu** , pokud ještě nejsou rozbalené, a pak vyberte zdroj dat, ke kterému chcete ovládací prvek navazovat.

5. Pokud zdroj dat obsahuje více než jednoho člena, například pokud jste vytvořili <xref:System.Data.DataSet?displayProperty=nameWithType> , který obsahuje více tabulek, rozbalte zdroj dat a pak vyberte konkrétního člena, ke kterému se má vytvořit vazba.

6. Chcete-li vytvořit relaci hlavního a podrobností v rozevíracím okně **Zvolit zdroj dat** pro druhý <xref:System.Windows.Forms.DataGridView> <xref:System.Windows.Forms.BindingSource> ovládací prvek, rozbalte položku Vytvořeno pro nadřazenou tabulku a pak v zobrazeném seznamu vyberte související podřízenou tabulku.

    > [!NOTE]
    > Pokud projekt již obsahuje zdroj dat, můžete také použít okno **zdroje dat** k vytvoření datového formuláře. Další informace naleznete v tématu [okno zdroje dat](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/6ckyxa83(v=vs.120)).

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.DataGridView.DataMember%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>
- [Postupy: Připojení k datům v databázi](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/fxk9yw1t(v=vs.120))
- [Postupy: Přidání a odebrání sloupců v ovládacím prvku DataGridView model Windows Forms pomocí návrháře](add-and-remove-columns-in-the-datagrid-using-the-designer.md)
- [Postupy: Změna pořadí sloupců v ovládacím prvku DataGridView model Windows Forms pomocí návrháře](change-the-order-of-columns-in-the-datagrid-using-the-designer.md)
- [Postupy: Změna typu sloupce model Windows Forms DataGridView pomocí návrháře](change-the-type-of-a-wf-datagridview-column-using-the-designer.md)
- [Postupy: Ukotvit sloupce v ovládacím prvku DataGridView model Windows Forms pomocí návrháře](freeze-columns-in-the-datagrid-using-the-designer.md)
- [Postupy: Skrýt sloupce v ovládacím prvku DataGridView model Windows Forms pomocí návrháře](hide-columns-in-the-datagrid-using-the-designer.md)
- [Postupy: Nastavit sloupce jen pro čtení v ovládacím prvku DataGridView model Windows Forms pomocí návrháře](make-columns-read-only-in-the-datagrid-using-the-designer.md)
- [Postupy: Vytvoření projektu model Windows Forms aplikace](/visualstudio/ide/step-1-create-a-windows-forms-application-project)
- [Postupy: Přidat ovládací prvky do model Windows Forms](how-to-add-controls-to-windows-forms.md)
- [Okno zdroje dat](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/6ckyxa83(v=vs.120))
- [Postupy: Zobrazení souvisejících dat v aplikaci model Windows Forms](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/57tx3hhe(v=vs.120))
