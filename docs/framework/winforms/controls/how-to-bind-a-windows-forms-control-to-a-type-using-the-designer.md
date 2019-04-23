---
title: 'Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu pomocí Návrháře'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 5ab984b5-c2d0-4638-a572-1c84013e8746
ms.openlocfilehash: b298efb0494994659673f9bf9893b667f7eb0f8c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59304205"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type-using-the-designer"></a>Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu pomocí Návrháře
Při vytváření ovládacích prvků, které pracují s daty, někdy potřebujete k vytvoření vazby ovládacího prvku typu, nikoli objekt. Obvykle budete muset vytvoření vazby ovládacího prvku na typ v době návrhu, když dat nemusí být k dispozici, ale stále chcete své ovládací prvky vázané na data pro zobrazení dat z veřejného rozhraní typu. Následující postupy ukazují, jak vytvořit nový <xref:System.Windows.Forms.BindingSource> , který je s vazbou na typ a pak jednu z vlastností typu vazba <xref:System.Windows.Forms.TextBox.Text%2A> vlastnost <xref:System.Windows.Forms.TextBox>.  
  
### <a name="to-bind-the-bindingsource-to-a-type"></a>Pro vazbu na typ objektu BindingSource  
  
1. Vytvoření projektu Windows Forms (**souboru** > **nový** > **projektu** > **Visual C#** nebo **Jazyka Visual Basic** > **klasický desktopový** > **aplikaci Windows Forms**).  
  
2. V **návrhu** zobrazení, přetáhněte <xref:System.Windows.Forms.BindingSource> komponentu do formuláře.  
  
3. V **vlastnosti** okna, klikněte na šipku u <xref:System.Windows.Forms.BindingSource.DataSource%2A> vlastnost.  
  
4. V **editoru typů uživatelského rozhraní DataSource**, klikněte na tlačítko **přidat zdroj dat projektu**.  
  
5. Na **zvolte typ zdroje dat** stránce **objekt** a klikněte na tlačítko **Další**.  
  
6. Vyberte typ, který chcete vytvořit vazbu na:  
  
    -   Pokud je typ, který chcete vytvořit vazbu k v aktuálním projektu nebo sestavení obsahující typ je již přidána jako odkaz, rozbalte uzly najít požadovaný typ a pak ho vyberte.  
  
         -nebo-  
  
    -   Pokud chcete vytvořit vazbu na typ je v jiném sestavení, není aktuálně v seznamu odkazů, klikněte na tlačítko **přidat odkaz**a potom klikněte na tlačítko **projekty** kartu. Vyberte projekt, který obsahuje obchodní objekt a klikněte na tlačítko **OK**. Tento projekt se objeví v seznamu sestavení, tak lze rozbalit uzly se najít typ můžete a pak vyberte ho.  
  
        > [!NOTE]
        >  Pokud chcete vytvořit vazbu na typ v rámci nebo sestavení Microsoft, zrušte zaškrtnutí políčka **skrýt sestavení, které začínají s Microsoftem nebo systém** zaškrtávací políčko.  
  
7. Klikněte na tlačítko **Další**a potom klikněte na tlačítko **Dokončit**.  
  
### <a name="to-bind-the-control-to-the-bindingsource"></a>K vytvoření vazby ovládacího prvku BindingSource  
  
1. Přidat <xref:System.Windows.Forms.TextBox> do formuláře.  
  
2. V **vlastnosti** okna, rozbalte **(DataBindings)** uzlu.  
  
3. Klikněte na šipku vedle položky <xref:System.Windows.Forms.TextBox.Text%2A> vlastnost.  
  
4. V **editoru typů uživatelského rozhraní DataSource**, rozbalte uzel pro <xref:System.Windows.Forms.BindingSource> přidali dříve a vyberte vlastnost vázaný typ, který chcete vytvořit vazbu k <xref:System.Windows.Forms.TextBox.Text%2A> vlastnost <xref:System.Windows.Forms.TextBox>.  
  
## <a name="see-also"></a>Viz také:

- [Komponenta BindingSource](bindingsource-component.md)
- [Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu](how-to-bind-a-windows-forms-control-to-a-type.md)
- [Vytvoření vazby ovládacích prvků k datům v sadě Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
