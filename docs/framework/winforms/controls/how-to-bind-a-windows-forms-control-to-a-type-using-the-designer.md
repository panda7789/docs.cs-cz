---
title: 'Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 5ab984b5-c2d0-4638-a572-1c84013e8746
ms.openlocfilehash: 5069d7d3b5ef4c5b05159dac521d32f5be8abdd1
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046044"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type-using-the-designer"></a>Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu pomocí Návrháře

Při vytváření ovládacích prvků, které komunikují s daty, někdy je nutné vytvořit navázání ovládacího prvku na typ místo objektu. Obvykle je nutné svázat ovládací prvek s typem v době návrhu, pokud data nemusí být k dispozici, ale přesto chcete, aby ovládací prvky vázané na data zobrazovaly data z veřejného rozhraní typu. Následující postupy ukazují, jak vytvořit nový <xref:System.Windows.Forms.BindingSource> , který je vázán na typ a potom jak svázat jednu z vlastností typu <xref:System.Windows.Forms.TextBox.Text%2A> s vlastností <xref:System.Windows.Forms.TextBox>.

### <a name="to-bind-the-bindingsource-to-a-type"></a>Navázání objektu BindingSource na typ

1. Vytvoření projektu model Windows Forms (**soubor** > **nového** > **projektu** > **Visual C#**  nebo**klasický Desktop**VisualBasic >  >   **Model Windows Forms aplikace**).

2. V **návrhovém** zobrazení přetáhněte <xref:System.Windows.Forms.BindingSource> komponentu do formuláře.

3. V okně **vlastnosti** klikněte na šipku u <xref:System.Windows.Forms.BindingSource.DataSource%2A> vlastnosti.

4. V **editoru typu uživatelského rozhraní DataSource**klikněte na **Přidat zdroj dat projektu**.

5. Na stránce **Zvolte typ zdroje dat** vyberte **objekt** a klikněte na **Další**.

6. Vyberte typ, na který se má vytvořit vazba:

    - Pokud je typ, ke kterému chcete vytvořit vazby, v aktuálním projektu nebo sestavení, které obsahuje typ, je již přidáno jako odkaz, rozbalte uzly a Najděte požadovaný typ a pak ho vyberte.

      \-ani

    - Pokud je typ, ke kterému chcete vytvořit vazby, v jiném sestavení, nikoli v seznamu odkazů, klikněte na tlačítko **Přidat odkaz**a poté klikněte na kartu **projekty** . Vyberte projekt, který obsahuje požadovaný obchodní objekt, a klikněte na **OK**. Tento projekt se zobrazí v seznamu sestavení, takže můžete rozbalit uzly a najít požadovaný typ a pak ho vybrat.

      > [!NOTE]
      > Pokud chcete vytvořit vazby na typ v rozhraní nebo sestavení společnosti Microsoft, zrušte zaškrtnutí políčka **Skrýt sestavení, která začínají na Microsoft nebo System** .

7. Klikněte na **Další**a potom na **Dokončit**.

### <a name="to-bind-the-control-to-the-bindingsource"></a>Navázání ovládacího prvku na objekt BindingSource

1. <xref:System.Windows.Forms.TextBox> Přidejte do formuláře.

2. V okně **vlastnosti** rozbalte uzel **(datové vazby)** .

3. Klikněte na šipku vedle <xref:System.Windows.Forms.TextBox.Text%2A> vlastnosti.

4. V **editoru typu uživatelského rozhraní DataSource**rozbalte uzel pro <xref:System.Windows.Forms.BindingSource> přidané položky a vyberte vlastnost vázaného typu, který chcete svázat s <xref:System.Windows.Forms.TextBox.Text%2A> vlastností objektu <xref:System.Windows.Forms.TextBox>.

## <a name="see-also"></a>Viz také:

- [Komponenta BindingSource](bindingsource-component.md)
- [Postupy: Svázání ovládacího prvku model Windows Forms s typem](how-to-bind-a-windows-forms-control-to-a-type.md)
- [Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
