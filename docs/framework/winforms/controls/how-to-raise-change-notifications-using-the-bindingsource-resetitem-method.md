---
title: 'Postupy: Vytváření oznámení o změnách pomocí metody BindingSource ResetItem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- change notifications [Windows Forms], raising
- data binding [Windows Forms], change notifications
- BindingSource component [Windows Forms], raising change notifications with
- data sources [Windows Forms], detecting changes
- change notifications
ms.assetid: ab8b4096-37ff-4e30-aabc-de79a2f2e972
ms.openlocfilehash: 39beb5c7162fb01a51360330216687c158ff433c
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65583708"
---
# <a name="how-to-raise-change-notifications-using-the-bindingsource-resetitem-method"></a>Postupy: Vytváření oznámení o změnách pomocí metody BindingSource ResetItem
Některé zdroje dat pro ovládací prvky nevyvolávejte oznámení o změnách při změně, přidání nebo odstranění položek. S <xref:System.Windows.Forms.BindingSource> součásti, můžete vytvořit vazbu k takovým zdrojům dat a vyvolání oznámení o změně v kódu.  
  
## <a name="example"></a>Příklad  
 Tento formulář ukazuje použití <xref:System.Windows.Forms.BindingSource> součásti pro vytvoření vazby seznam <xref:System.Windows.Forms.DataGridView> ovládacího prvku. V seznamu nevyvolává oznámení o změnách, proto <xref:System.Windows.Forms.BindingSource.ResetItem%2A> metodu na <xref:System.Windows.Forms.BindingSource> se volá při změně položky v seznamu. .  
  
 [!code-cpp[System.Windows.Forms.DataConnector.ResetItem#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetItem/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.ResetItem#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetItem/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.ResetItem#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetItem/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení systému, System.Data, System.Drawing a System.Windows.Forms.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Komponenta BindingSource](bindingsource-component.md)
- [Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu](how-to-bind-a-windows-forms-control-to-a-type.md)
