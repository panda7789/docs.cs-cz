---
title: 'Postupy: Svázání vlastností dvou ovládacích prvků'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], binding properties of two controls
- binding properties of two controls [WPF]
- controls [WPF], binding properties of
ms.assetid: 06318fac-6afd-4c7d-a277-6d7ef50f47bc
ms.openlocfilehash: d38c473b8c4d3f71f1e3decd4f66be248665c57b
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73974806"
---
# <a name="how-to-bind-the-properties-of-two-controls"></a>Postupy: Svázání vlastností dvou ovládacích prvků

Tento příklad ukazuje, jak vytvořit navázání vlastnosti jednoho ovládacího prvku s vytvořeným instancemi na jiný pomocí vlastnosti <xref:System.Windows.Data.Binding.ElementName%2A>.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak vytvořit navázání vlastnosti <xref:System.Windows.Controls.Panel.Background%2A> <xref:System.Windows.Controls.Canvas> na vlastnost [SelectedItem. Content](xref:System.Windows.Controls.ContentControl.Content%2A) <xref:System.Windows.Controls.ComboBox>:

[!code-xaml[BindDptoDp#1](~/samples/snippets/csharp/VS_Snippets_Wpf/BindDPtoDP/CS/Window1.xaml#1)]

Když je tento příklad vykreslený, vypadá takto:

![Snímek obrazovky s polem se seznamem s hodnotou zelenou vybranou a zeleným čtvercem](./media/how-to-bind-the-properties-of-two-controls/data-binding-bind-background-canvas.png)

> [!NOTE]
> Vlastnost target vazby (v tomto příkladu vlastnost <xref:System.Windows.Controls.Panel.Background%2A>) musí být vlastnost závislosti. Další informace najdete v tématu [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md).

## <a name="see-also"></a>Viz také:

- [Určení zdroje vazby](how-to-specify-the-binding-source.md)
- [Témata s postupy](data-binding-how-to-topics.md)
