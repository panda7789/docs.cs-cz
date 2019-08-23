---
title: 'Postupy: Pohyb v prvku DataSet pomocí ovládacího prvku Windows Forms BindingNavigator'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- datasets [Windows Forms], moving through
- BindingNavigator control [Windows Forms], moving through datasets
- examples [Windows Forms], BindingNavigator control
ms.assetid: 146d97be-3d97-400e-accb-860bbf47729d
ms.openlocfilehash: d33cad4d0a60aa29d8c9f5e2217532963e8358c4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952698"
---
# <a name="how-to-move-through-a-dataset-with-the-windows-forms-bindingnavigator-control"></a>Postupy: Pohyb v prvku DataSet pomocí ovládacího prvku Windows Forms BindingNavigator
Při sestavování aplikací založených na datech budete často potřebovat zobrazit kolekce dat pro uživatele. Ovládací prvek, ve spojení <xref:System.Windows.Forms.BindingSource> s komponentou, poskytuje pohodlné a rozšiřitelné řešení pro přesun v kolekci a zobrazení položek postupně. <xref:System.Windows.Forms.BindingNavigator>  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak použít <xref:System.Windows.Forms.BindingNavigator> ovládací prvek k přesunu dat. Sada je obsažena v <xref:System.Data.DataView>, která je svázána <xref:System.Windows.Forms.TextBox> s ovládacím prvkem s <xref:System.Windows.Forms.BindingSource> komponentou.  
  
> [!NOTE]
> Ukládání citlivých informací, jako je například heslo, v rámci připojovacího řetězce může ovlivnit zabezpečení aplikace. Bezpečnější způsob, jak řídit přístup k databázi, je ověřování systému Windows (označované také jako integrované zabezpečení). Další informace najdete v tématu [ochrana informací o připojení](../../data/adonet/protecting-connection-information.md).  
  
 [!code-csharp[System.Windows.Forms.DataNavigator#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataNavigator#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení System, System. data, System. Drawing, System. Windows. Forms a System. XML.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [Ovládací prvek BindingNavigator](bindingnavigator-control-windows-forms.md)
- [Komponenta BindingSource](bindingsource-component.md)
- [Postupy: Svázání ovládacího prvku model Windows Forms s typem](how-to-bind-a-windows-forms-control-to-a-type.md)
