---
title: Svázání ovládacích prvků s komponentou BindingSource pomocí návrháře
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], binding
- BindingSource component [Windows Forms], binding controls
- data binding [Windows Forms], BindingSource component
ms.assetid: 391ae170-de5c-40f8-8233-91cb2ee4683a
ms.openlocfilehash: 35b3fb7b9884f07dd6e2aef311a01d3090c44227
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744388"
---
# <a name="how-to-bind-windows-forms-controls-with-the-bindingsource-component-using-the-designer"></a>Postupy: Vytvoření vazby ovládacích prvků Windows Forms ke komponentě BindingSource pomocí Návrháře
Po přidání ovládacích prvků do formuláře a určení uživatelského rozhraní vaší aplikace můžete navazovat ovládací prvky na zdroj dat, takže v době běhu mohou uživatelé upravovat a ukládat data související s aplikací.

 Vázání ovládacího prvku nebo řady ovládacích prvků v model Windows Forms je nejsnadnějším použitím ovládacího prvku <xref:System.Windows.Forms.BindingSource> jako mostu mezi ovládacími prvky formuláře a zdrojem dat.

 Jeden nebo více ovládacích prvků na formuláři lze svázat s daty; v následujícím postupu je ovládací prvek <xref:System.Windows.Forms.TextBox> svázán se zdrojem dat.

 K dokončení postupu se předpokládá, že budete Přivážete ke zdroji dat odvozenému z databáze. Další informace o vytváření zdrojů dat z jiných úložišť dat najdete v tématu [Přidání nových zdrojů dat](/visualstudio/data-tools/add-new-data-sources).

## <a name="to-bind-a-control-at-design-time"></a>Navázání ovládacího prvku v době návrhu

1. Přetáhněte ovládací prvek <xref:System.Windows.Forms.TextBox> do formuláře.

2. V okně **vlastnosti** :

    1. Rozbalte uzel **(datové vazby)** .

    2. Klikněte na šipku vedle vlastnosti <xref:System.Windows.Forms.TextBox.Text%2A>.

         Otevře se Editor typu uživatelského rozhraní **DataSource** .

         Pokud byl zdroj dat dříve nakonfigurován pro projekt nebo formulář, zobrazí se.

3. Kliknutím na **Přidat zdroj dat projektu** se můžete připojit k datům a vytvořit zdroj dat.

4. Na úvodní stránce **Průvodce konfigurací zdroje dat** klikněte na tlačítko **Další**.

5. Na stránce **Vybrat typ zdroje dat** vyberte možnost **databáze**.

6. Na stránce **Vyberte datové připojení** vyberte datové připojení ze seznamu dostupných připojení. Pokud vaše požadované datové připojení není k dispozici, vyberte **nové připojení** a vytvořte nové datové připojení.

7. Vyberte **Ano, uložit připojení** pro uložení připojovacího řetězce do konfiguračního souboru aplikace.

8. Vyberte databázové objekty, které chcete přenést do aplikace. V takovém případě vyberte pole v tabulce, pro které chcete zobrazit <xref:System.Windows.Forms.TextBox>.

9. Pokud chcete, nahraďte výchozí název datové sady.

10. Klikněte na **Dokončit**.

11. V okně **vlastnosti** klikněte znovu na šipku vedle vlastnosti <xref:System.Windows.Forms.TextBox.Text%2A>. V editoru typu uživatelského rozhraní **zdroje dat** vyberte název pole, ke kterému se má <xref:System.Windows.Forms.TextBox> navazovat.

     Editor typu uživatelského rozhraní **DataSource** se zavře a do formuláře se přidají datová sada, <xref:System.Windows.Forms.BindingSource> a adaptér tabulky specifický pro toto datové připojení.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.BindingNavigator>
- [Přidání nových zdrojů dat](/visualstudio/data-tools/add-new-data-sources)
- [Okno zdroje dat](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/6ckyxa83(v=vs.120))
