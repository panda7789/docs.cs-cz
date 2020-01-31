---
title: Vázání ovládacího prvku na typ
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 94faeebb-d2bc-45d6-86d7-96a42661b43d
ms.openlocfilehash: 0bc1f92ee8922990bd0e461655168f5618ba39a6
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744987"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type"></a>Postupy: Vázání ovládacího prvku Windows Forms k typu
Při vytváření ovládacích prvků, které komunikují s daty, někdy je nutné pro svázání ovládacího prvku s typem namísto objektu. Tato situace nastane hlavně v době návrhu, pokud data nemusí být k dispozici, ale ovládací prvky vázané na data stále potřebují zobrazovat informace z veřejného rozhraní typu. Například můžete navazovat ovládací prvek <xref:System.Windows.Forms.DataGridView> k objektu, který je vystavený webovou službou a chcete, aby ovládací prvek <xref:System.Windows.Forms.DataGridView> v době návrhu pokryl své sloupce s názvy členů vlastního typu.  
  
 Ovládací prvek lze snadno navazovat na typ pomocí komponenty <xref:System.Windows.Forms.BindingSource>.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak vytvořit vazbu ovládacího prvku <xref:System.Windows.Forms.DataGridView> k vlastnímu typu pomocí komponenty <xref:System.Windows.Forms.BindingSource>. Když spustíte příklad, všimnete si, že <xref:System.Windows.Forms.DataGridView> má označené sloupce, které odráží vlastnosti objektu `Customer`, před tím, než se ovládací prvek naplní daty. V příkladu je tlačítko Přidat zákazníka, které přidá data do ovládacího prvku <xref:System.Windows.Forms.DataGridView>. Po kliknutí na tlačítko se do <xref:System.Windows.Forms.BindingSource>přidá nový objekt `Customer`. Ve scénáři reálného světa může být data získána voláním webové služby nebo jiného zdroje dat.  
  
 [!code-csharp[System.Windows.Forms.DataConnector.BindingToType#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindingToType/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.BindingToType#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindingToType/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení System a System. Windows. Forms.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Komponenta BindingSource](bindingsource-component.md)
