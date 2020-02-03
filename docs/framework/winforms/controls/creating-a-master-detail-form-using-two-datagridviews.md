---
title: 'Návod: Vytvoření hlavního a podrobného formuláře pomocí dvou ovládacích prvků DataGridView'
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
ms.openlocfilehash: bb3da36430c7493b941f3711cb584b4517d5bd54
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740580"
---
# <a name="walkthrough-creating-a-masterdetail-form-using-two-windows-forms-datagridview-controls"></a>Návod: Vytvoření hlavního/podrobného formuláře pomocí dvou ovládacích prvků Windows Forms DataGridView

Jedním z nejběžnějších scénářů použití ovládacího prvku <xref:System.Windows.Forms.DataGridView> je hlavní formulář *a formulář podrobností* , ve kterém je zobrazený vztah nadřazenosti/podřízenosti mezi dvěma databázovými tabulkami. Výběrem řádků v hlavní tabulce dojde k aktualizaci tabulky podrobností s odpovídajícími podřízenými daty.

Implementace hlavního a podrobného formuláře pomocí interakce mezi ovládacím prvkem <xref:System.Windows.Forms.DataGridView> a <xref:System.Windows.Forms.BindingSource> komponentou je snadná. V tomto návodu vytvoříte formulář pomocí dvou ovládacích prvků <xref:System.Windows.Forms.DataGridView> a dvou <xref:System.Windows.Forms.BindingSource>ch komponent. Ve formuláři se zobrazí dvě související tabulky v ukázkové databázi Northwind SQL Server: `Customers` a `Orders`. Až budete hotovi, budete mít formulář, který zobrazí všechny zákazníky v databázi v hlavní <xref:System.Windows.Forms.DataGridView> a všechny objednávky pro vybraného zákazníka v <xref:System.Windows.Forms.DataGridView>podrobností.

Chcete-li zkopírovat kód v tomto tématu jako jeden výpis, přečtěte si téma [Postup: Vytvoření hlavního a podrobného formuláře pomocí dvou ovládacích prvků model Windows Forms DataGridView](create-a-master-detail-form-using-two-datagridviews.md).

## <a name="prerequisites"></a>Předpoklady

Aby bylo možné dokončit tento návod, budete potřebovat:

- Přístup k serveru, který má ukázkovou databázi Northwind SQL Server.

## <a name="creating-the-form"></a>Vytvoření formuláře

#### <a name="to-create-a-masterdetail-form"></a>Vytvoření hlavního a podrobného formuláře

1. Vytvořte třídu, která je odvozena z <xref:System.Windows.Forms.Form> a obsahuje dva ovládací prvky <xref:System.Windows.Forms.DataGridView> a dvě <xref:System.Windows.Forms.BindingSource> komponenty. Následující kód poskytuje základní inicializaci formuláře a zahrnuje metodu `Main`. Použijete-li k vytvoření formuláře Návrhář aplikace Visual Studio, můžete použít kód vygenerovaný návrhářem namísto tohoto kódu, ale nezapomeňte použít názvy zobrazené v deklaracích proměnných zde.

    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#01](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#01)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#01](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#01)]
    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#02](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#02](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#02)]

2. Implementujte metodu v definici třídy formuláře pro zpracování podrobností o připojení k databázi. Tento příklad používá metodu `GetData`, která naplňuje objekt <xref:System.Data.DataSet>, přidá objekt <xref:System.Data.DataRelation> do sady dat a vytvoří vazby <xref:System.Windows.Forms.BindingSource> komponent. Nezapomeňte nastavit `connectionString` proměnnou na hodnotu, která je vhodná pro vaši databázi.

    > [!IMPORTANT]
    > Ukládání citlivých informací, jako je například heslo, v rámci připojovacího řetězce může ovlivnit zabezpečení aplikace. Bezpečnější způsob, jak řídit přístup k databázi, je ověřování systému Windows (označované také jako integrované zabezpečení). Další informace najdete v tématu [ochrana informací o připojení](../../data/adonet/protecting-connection-information.md).

    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#20)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#20)]

3. Implementujte obslužnou rutinu pro událost <xref:System.Windows.Forms.Form.Load> formuláře, která sváže ovládací prvky <xref:System.Windows.Forms.DataGridView> s <xref:System.Windows.Forms.BindingSource> komponentami a volá metodu `GetData`. Následující příklad obsahuje kód, který změní velikost <xref:System.Windows.Forms.DataGridView> sloupce tak, aby odpovídala zobrazeným datům.

    [!code-csharp[System.Windows.Forms.DataGridViewMasterDetails#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/CS/masterdetails.cs#10)]
    [!code-vb[System.Windows.Forms.DataGridViewMasterDetails#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMasterDetails/VB/masterdetails.vb#10)]

## <a name="testing-the-application"></a>Testování aplikace

Nyní můžete testovat formulář, abyste se ujistili, že se chová podle očekávání.

#### <a name="to-test-the-form"></a>Testování formuláře

- Zkompilujte a spusťte aplikaci.

  Zobrazí se dva <xref:System.Windows.Forms.DataGridView> ovládací prvky, jednu nad druhou. Nahoře jsou zákazníci z tabulky `Customers` Northwind a v dolní části `Orders` odpovídající vybranému zákazníkovi. Když vyberete jiné řádky v horním <xref:System.Windows.Forms.DataGridView>, obsah nižší <xref:System.Windows.Forms.DataGridView> odpovídajícím způsobem se změní.

## <a name="next-steps"></a>Další kroky

Tato aplikace vám poskytne základní informace o možnostech ovládacího prvku <xref:System.Windows.Forms.DataGridView>. Vzhled a chování ovládacího prvku <xref:System.Windows.Forms.DataGridView> můžete přizpůsobit několika způsoby:

- Změnit styly ohraničení a záhlaví. Další informace najdete v tématu [Postup: Změna stylů ohraničení a mřížky v ovládacím prvku DataGridView model Windows Forms](change-the-border-and-gridline-styles-in-the-datagrid.md).

- Povolí nebo zakáže vstup uživatele do ovládacího prvku <xref:System.Windows.Forms.DataGridView>. Další informace naleznete v tématu [How to: zabránění přidání a odstranění řádku v ovládacím prvku datagridview model Windows Forms](prevent-row-addition-and-deletion-datagridview.md)a [Postupy: vytvoření sloupců jen pro čtení v ovládacím prvku model Windows Forms DataGridView](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).

- Ověří vstup uživatele do ovládacího prvku <xref:System.Windows.Forms.DataGridView>. Další informace naleznete v tématu [Návod: ověřování dat v ovládacím prvku DataGridView model Windows Forms](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).

- Zpracování velmi velkých datových sad pomocí virtuálního režimu. Další informace naleznete v tématu [Návod: implementace virtuálního režimu v ovládacím prvku DataGridView model Windows Forms](implementing-virtual-mode-wf-datagridview-control.md).

- Přizpůsobení vzhledu buněk Další informace naleznete v tématu [Postupy: přizpůsobení vzhledu buněk v ovládacím prvku model Windows Forms DataGridView](customize-the-appearance-of-cells-in-the-datagrid.md) a [Postup: nastavení výchozích stylů buňky pro ovládací prvek DataGridView model Windows Forms](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Zobrazení dat v ovládacím prvku Windows Forms DataGridView](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Postupy: Vytvoření hlavního/podrobného formuláře pomocí dvou ovládacích prvků Windows Forms DataGridView](create-a-master-detail-form-using-two-datagridviews.md)
- [Ochrana informací o připojení](../../data/adonet/protecting-connection-information.md)
