---
title: 'Postupy: Vytvoření jednoduše vázaného ovládacího prvku na formuláři Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [Windows Forms], simple data binding
- Windows Forms controls, data binding
ms.assetid: 3bcaded8-0f1a-4cc0-8830-f59be253bf4e
ms.openlocfilehash: ed1d0e423a3cdf77a242ec3214720f1466f65897
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039509"
---
# <a name="how-to-create-a-simple-bound-control-on-a-windows-form"></a>Postupy: Vytvoření jednoduše vázaného ovládacího prvku na formuláři Windows Forms

S *jednoduchou vazbou*můžete v ovládacím prvku zobrazit jeden datový prvek, jako je například hodnota sloupce z tabulky DataSet. Můžete vytvořit jednoduchou datovou vlastnost ovládacího prvku s datovou hodnotou.

### <a name="to-simple-bind-a-control"></a>Jednoduché vázání ovládacího prvku

1. Připojte se ke zdroji dat. Další informace najdete v tématu [připojení ke zdroji dat](../data/adonet/connecting-to-a-data-source.md).

2. Ve formuláři vyberte ovládací prvek a zobrazte okno **vlastnosti** .

3. Rozbalte vlastnost **(DataBindings)** .

     Vlastnosti nejčastěji vázaných jsou zobrazeny pod vlastností **(DataBindings)** . Ve většině ovládacích prvků je například vlastnost **text** nejčastěji svázána.

4. Pokud vlastnost, kterou chcete svázat, není jednou z běžně vázaných vlastností, klikněte na tlačítko se **třemi tečkami** ![(na tlačítko se třemi tečkami (...) v okno vlastnosti](./media/how-to-create-a-simple-bound-control-on-a-windows-form/visual-studio-ellipsis-button.png)sady Visual Studio.) v poli **(rozšířeném)** zobrazte  **Dialogové okno formátování a rozšířené vazby** s úplným seznamem vlastností pro tento ovládací prvek.

5. Vyberte vlastnost, kterou chcete svázat, a klikněte na šipku rozevíracího seznamu u položky **vazba**.

     Zobrazí se seznam dostupných zdrojů dat.

6. Rozbalte zdroj dat, ke kterému chcete vytvořit vazby, dokud nenajdete jeden datový prvek, který chcete. Pokud například vytváříte vazbu k hodnotě sloupce v tabulce datové sady, rozbalíte název datové sady a potom rozbalíte název tabulky pro zobrazení názvů sloupců.

7. Klikněte na název elementu, na který se má vytvořit vazba.

8. Pokud jste pracovali v dialogovém okně **formátování a rozšířené vazby** , kliknutím na tlačítko **OK** se vraťte do okna **vlastnosti** .

9. Pokud chcete navazovat další vlastnosti ovládacího prvku, opakujte kroky 3 až 7.

    > [!NOTE]
    > Vzhledem k tomu, že jednoduché ovládací prvky jsou zobrazeny pouze s jedním datovým prvkem, je velmi typický zahrnout navigační logiku do formuláře Windows pomocí jednoduchých vázaných ovládacích prvků.

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Binding>
- [Windows Forms – datová vazba](windows-forms-data-binding.md)
- [Datové vazby a Windows Forms](data-binding-and-windows-forms.md)
