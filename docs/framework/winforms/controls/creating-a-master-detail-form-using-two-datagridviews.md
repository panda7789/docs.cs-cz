---
title: 'Návod: Vytvoření hlavního formuláře s podrobnostmi pomocí dvou ovládacích prvků model Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], master/detail form
- parent-child tables [Windows Forms], displaying on Windows Forms
- master-details lists [Windows Forms], displaying on Windows Forms
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: c5fa29e8-47f7-4691-829b-0e697a691f36
ms.openlocfilehash: 4212c7223aca6a5e7de3189d5f6b2757453cc438
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046099"
---
# <a name="walkthrough-creating-a-masterdetail-form-using-two-windows-forms-datagridview-controls"></a>Návod: Vytvoření hlavního/podrobného formuláře pomocí dvou ovládacích prvků Windows Forms DataGridView

Jedním z nejběžnějších scénářů použití <xref:System.Windows.Forms.DataGridView> ovládacího prvku je hlavní formulář *a formulář podrobností* , ve kterém je zobrazený vztah nadřazenosti/podřízenosti mezi dvěma databázovými tabulkami. Výběrem řádků v hlavní tabulce dojde k aktualizaci tabulky podrobností s odpovídajícími podřízenými daty.

Implementace hlavního nebo podrobného formuláře se snadno používá v interakci mezi <xref:System.Windows.Forms.DataGridView> ovládacím prvkem <xref:System.Windows.Forms.BindingSource> a komponentou. V tomto návodu vytvoříte formulář pomocí dvou <xref:System.Windows.Forms.DataGridView> ovládacích prvků a dvou <xref:System.Windows.Forms.BindingSource> součástí. Ve formuláři se zobrazí dvě související tabulky v ukázkové databázi Northwind SQL Server: `Customers` a. `Orders` Až budete hotovi, budete mít formulář, který zobrazí všechny zákazníky v databázi v hlavní <xref:System.Windows.Forms.DataGridView> databázi a všechny objednávky vybraného zákazníka v podrobnostech. <xref:System.Windows.Forms.DataGridView>

Postup kopírování kódu v tomto tématu jako jediného výpisu naleznete v [tématu How to: Vytvoření hlavního a podrobného formuláře pomocí dvou ovládacích prvků](create-a-master-detail-form-using-two-datagridviews.md)model Windows Forms DataGridView.

## <a name="prerequisites"></a>Požadavky

Aby bylo možné dokončit tento návod, budete potřebovat:

- Přístup k serveru, který má ukázkovou databázi Northwind SQL Server.

## <a name="creating-the-form"></a>Vytvoření formuláře

#### <a name="to-create-a-masterdetail-form"></a>Vytvoření hlavního a podrobného formuláře

1. Vytvořte třídu, která je odvozena <xref:System.Windows.Forms.Form> z a obsahuje <xref:System.Windows.Forms.DataGridView> dva ovládací prvky <xref:System.Windows.Forms.BindingSource> a dvě součásti. Následující kód poskytuje základní inicializaci formuláře a zahrnuje `Main` metodu. Použijete-li k vytvoření formuláře Návrhář aplikace Visual Studio, můžete použít kód vygenerovaný návrhářem namísto tohoto kódu, ale nezapomeňte použít názvy zobrazené v deklaracích proměnných zde.

    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#01)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#01)]
    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#02)]

2. Implementujte metodu v definici třídy formuláře pro zpracování podrobností o připojení k databázi. V tomto příkladu se `GetData` používá metoda, která naplňuje <xref:System.Data.DataSet> objekt, přidá <xref:System.Data.DataRelation> objekt do datové sady a váže <xref:System.Windows.Forms.BindingSource> komponenty. Nezapomeňte nastavit `connectionString` proměnnou na hodnotu, která je vhodná pro vaši databázi.

    > [!IMPORTANT]
    > Ukládání citlivých informací, jako je například heslo, v rámci připojovacího řetězce může ovlivnit zabezpečení aplikace. Bezpečnější způsob, jak řídit přístup k databázi, je ověřování systému Windows (označované také jako integrované zabezpečení). Další informace najdete v tématu [ochrana informací o připojení](../../data/adonet/protecting-connection-information.md).

    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#20)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#20)]

3. Implementujte <xref:System.Windows.Forms.Form.Load> obslužnou rutinu pro událost formuláře, která sváže <xref:System.Windows.Forms.DataGridView> ovládací prvky s <xref:System.Windows.Forms.BindingSource> komponentami a volá `GetData` metodu. Následující příklad obsahuje kód, který změní velikost <xref:System.Windows.Forms.DataGridView> sloupců tak, aby odpovídala zobrazeným datům.

    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#10)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#10)]

## <a name="testing-the-application"></a>Testování aplikace

Nyní můžete testovat formulář, abyste se ujistili, že se chová podle očekávání.

#### <a name="to-test-the-form"></a>Testování formuláře

- Zkompilujte a spusťte aplikaci.

  Zobrazí se dva <xref:System.Windows.Forms.DataGridView> ovládací prvky, jednu nad druhou. Nahoře jsou zákazníci z tabulky Northwind `Customers` a v dolní části `Orders` jsou odpovídající vybranému zákazníkovi. Když vyberete jiné řádky v horní <xref:System.Windows.Forms.DataGridView>části, obsah příslušné dolní <xref:System.Windows.Forms.DataGridView> změny se odpovídajícím způsobem změní.

## <a name="next-steps"></a>Další kroky

Tato aplikace vám poskytne základní informace o <xref:System.Windows.Forms.DataGridView> schopnostech ovládacího prvku. Vzhled a chování <xref:System.Windows.Forms.DataGridView> ovládacího prvku můžete přizpůsobit několika způsoby:

- Změnit styly ohraničení a záhlaví. Další informace najdete v tématu [jak: Změňte styly ohraničení a mřížky v ovládacím prvku](change-the-border-and-gridline-styles-in-the-datagrid.md)DataGridView model Windows Forms.

- Povolí nebo zakáže vstup uživatele k <xref:System.Windows.Forms.DataGridView> ovládacímu prvku. Další informace najdete v tématu [jak: Zabraňte přidávání a odstraňování řádků v ovládacím prvku](prevent-row-addition-and-deletion-datagridview.md)DataGridView model Windows Forms a [postupy: Zpřístupněte sloupce jen pro čtení v ovládacím prvku](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)DataGridView model Windows Forms.

- Ověřte vstup uživatele k <xref:System.Windows.Forms.DataGridView> ovládacímu prvku. Další informace najdete v tématu [Návod: Ověřování dat v ovládacím prvku](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)DataGridView model Windows Forms.

- Zpracování velmi velkých datových sad pomocí virtuálního režimu. Další informace najdete v tématu [Návod: Implementace virtuálního režimu v ovládacím prvku](implementing-virtual-mode-wf-datagridview-control.md)DataGridView model Windows Forms.

- Přizpůsobení vzhledu buněk Další informace najdete v tématu [jak: Přizpůsobení vzhledu buněk v ovládacím prvku](customize-the-appearance-of-cells-in-the-datagrid.md) model Windows Forms DataGridView a [postup: Nastavte výchozí styly buňky pro ovládací prvek](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)DataGridView model Windows Forms.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Zobrazení dat v ovládacím prvku Windows Forms DataGridView](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Postupy: Vytvoření hlavního a podrobného formuláře pomocí dvou ovládacích prvků model Windows Forms DataGridView](create-a-master-detail-form-using-two-datagridviews.md)
- [Ochrana informací o připojení](../../data/adonet/protecting-connection-information.md)
