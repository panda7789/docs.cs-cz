---
title: Vázání ovládacího prvku na objekt factory
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], binding
- factory objects [Windows Forms], binding to
- BindingSource component [Windows Forms], binding to a factory object
- BindingSource component [Windows Forms], examples
ms.assetid: 7d59af89-ff82-41d8-a48a-f1fbae788b0d
ms.openlocfilehash: 2b4d9aca3345a0cb1e7e995f66a8982dee983ca8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745092"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-factory-object"></a>Postupy: Vázání ovládacího prvku Windows Forms k objektu factory
Při sestavování ovládacích prvků, které komunikují s daty, někdy budete potřebovat navázání ovládacího prvku na objekt nebo metodu, která generuje jiné objekty. Takový objekt nebo metoda se nazývá továrna. Váš zdroj dat může být například návratovou hodnotou z volání metody, namísto objektu v paměti nebo typu. Můžete navazovat ovládací prvek na tento druh zdroje dat, pokud zdroj vrátí kolekci.  
  
 Ovládací prvek lze snadno navazovat na objekt továrny pomocí ovládacího prvku <xref:System.Windows.Forms.BindingSource>.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit vazbu ovládacího prvku <xref:System.Windows.Forms.DataGridView> s metodou objektu pro vytváření pomocí ovládacího prvku <xref:System.Windows.Forms.BindingSource>. Metoda Factory má název `GetOrdersByCustomerId`a vrátí všechny objednávky daného zákazníka v databázi Northwind.  
  
 [!code-cpp[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.BindToFactory#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení System, System. data, System. Drawing a System. Windows. Forms.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Komponenta BindingSource](bindingsource-component.md)
- [Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu](how-to-bind-a-windows-forms-control-to-a-type.md)
