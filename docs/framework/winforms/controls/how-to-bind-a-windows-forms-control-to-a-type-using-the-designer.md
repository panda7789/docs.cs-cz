---
title: Svázání ovládacího prvku s typem pomocí návrháře
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 5ab984b5-c2d0-4638-a572-1c84013e8746
ms.openlocfilehash: 2257489e123ceeea819ad3538952db51b726c7e5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742029"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type-using-the-designer"></a>Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu pomocí Návrháře

Při vytváření ovládacích prvků, které komunikují s daty, někdy je nutné vytvořit navázání ovládacího prvku na typ místo objektu. Obvykle je nutné svázat ovládací prvek s typem v době návrhu, pokud data nemusí být k dispozici, ale přesto chcete, aby ovládací prvky vázané na data zobrazovaly data z veřejného rozhraní typu. Následující postupy ukazují, jak vytvořit nový <xref:System.Windows.Forms.BindingSource> vázaný na typ a následně jak svázat jednu z vlastností typu s vlastností <xref:System.Windows.Forms.TextBox.Text%2A> <xref:System.Windows.Forms.TextBox>.

### <a name="to-bind-the-bindingsource-to-a-type"></a>Navázání objektu BindingSource na typ

1. Vytvořte projekt model Windows Forms (**soubor** > **Nový** > **projektu** > **vizuálu C#**  nebo **Visual Basic** > **klasické plochy** > **model Windows Forms aplikaci**).

2. V **návrhovém** zobrazení přetáhněte komponentu <xref:System.Windows.Forms.BindingSource> do formuláře.

3. V okně **vlastnosti** klikněte na šipku u vlastnosti <xref:System.Windows.Forms.BindingSource.DataSource%2A>.

4. V **editoru typu uživatelského rozhraní DataSource**klikněte na **Přidat zdroj dat projektu**.

5. Na stránce **Zvolte typ zdroje dat** vyberte **objekt** a klikněte na **Další**.

6. Vyberte typ, na který se má vytvořit vazba:

    - Pokud je typ, ke kterému chcete vytvořit vazby, v aktuálním projektu nebo sestavení, které obsahuje typ, je již přidáno jako odkaz, rozbalte uzly a Najděte požadovaný typ a pak ho vyberte.

      \-nebo-

    - Pokud je typ, ke kterému chcete vytvořit vazby, v jiném sestavení, které není aktuálně v seznamu odkazů, klikněte na tlačítko **Přidat odkaz**a poté klikněte na kartu **projekty** . Vyberte projekt obsahující požadovaný obchodní objekt a klikněte na tlačítko **OK**. Tento projekt se zobrazí v seznamu sestavení, takže můžete rozbalit uzly a najít požadovaný typ a pak ho vybrat.

      > [!NOTE]
      > Pokud chcete vytvořit vazby na typ v rozhraní nebo sestavení společnosti Microsoft, zrušte zaškrtnutí políčka **Skrýt sestavení, která začínají na Microsoft nebo System** .

7. Klikněte na **Další**a potom na **Dokončit**.

### <a name="to-bind-the-control-to-the-bindingsource"></a>Navázání ovládacího prvku na objekt BindingSource

1. Přidejte <xref:System.Windows.Forms.TextBox> do formuláře.

2. V okně **vlastnosti** rozbalte uzel **(datové vazby)** .

3. Klikněte na šipku vedle vlastnosti <xref:System.Windows.Forms.TextBox.Text%2A>.

4. V **editoru typu uživatelského rozhraní DataSource**rozbalte uzel pro <xref:System.Windows.Forms.BindingSource> přidané dříve a vyberte vlastnost vázaného typu, který chcete svázat s vlastností <xref:System.Windows.Forms.TextBox.Text%2A> <xref:System.Windows.Forms.TextBox>.

## <a name="see-also"></a>Viz také:

- [Komponenta BindingSource](bindingsource-component.md)
- [Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu](how-to-bind-a-windows-forms-control-to-a-type.md)
- [Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
