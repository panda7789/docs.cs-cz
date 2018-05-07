---
title: 'Postupy: Zajistěte, aby více ovládacích prvků vázaných ke stejnému zdroji dat zůstalo synchronizovaných'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], binding multiple
- controls [Windows Forms], synchronizing with data source
ms.assetid: c2f0ecc6-11e6-4c2c-a1ca-0759630c451e
ms.openlocfilehash: 5ab7eebd4f4087502f8709e17dde3f3de448c9aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-ensure-multiple-controls-bound-to-the-same-data-source-remain-synchronized"></a>Postupy: Zajistěte, aby více ovládacích prvků vázaných ke stejnému zdroji dat zůstalo synchronizovaných
Často při práci s datové vazby v systému Windows Forms, jsou svázané více ovládacích prvků na stejném datovém zdroji. V některých případech může být nutné provést další kroky k zajištění, aby zůstaly synchronizované s sebe navzájem a zdroj dat vázané vlastnosti ovládacích prvků. Tyto kroky jsou nutné ve dvou situacích:  
  
-   Pokud zdroj dat neimplementuje <xref:System.ComponentModel.IBindingList>a proto generování <xref:System.ComponentModel.IBindingList.ListChanged> události typu <xref:System.ComponentModel.ListChangedType.ItemChanged>.  
  
-   Pokud zdroj dat implementuje <xref:System.ComponentModel.IEditableObject>.  
  
 V prvním případě můžete použít <xref:System.Windows.Forms.BindingSource> svázat zdroj dat pro ovládací prvky. V takovém případě použijete <xref:System.Windows.Forms.BindingSource> a zpracovat <xref:System.Windows.Forms.BindingSource.BindingComplete> událostí a volání <xref:System.Windows.Forms.BindingManagerBase.EndCurrentEdit%2A> na přidruženého <xref:System.Windows.Forms.BindingManagerBase>.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak k vytvoření vazby ovládacích prvků tři – dvou ovládacích prvků textového pole a <xref:System.Windows.Forms.DataGridView> ovládací prvek – na stejný sloupec v <xref:System.Data.DataSet> pomocí <xref:System.Windows.Forms.BindingSource> součásti. Tento příklad ukazuje, jak bude zpracováván <xref:System.Windows.Forms.BindingSource.BindingComplete> událostí a ověřte, že při změně textové hodnoty jednoho textového pole, další textového pole a <xref:System.Windows.Forms.DataGridView> řízení jsou aktualizovány pomocí správnou hodnotu.  
  
 V příkladu se používá <xref:System.Windows.Forms.BindingSource> k vytvoření vazby zdroje dat a ovládací prvky. Alternativně můžete vytvoření vazby ovládacích prvků přímo ke zdroji dat a načtení <xref:System.Windows.Forms.BindingManagerBase> pro vazbu z formuláře <xref:System.Windows.Forms.Control.BindingContext%2A> a pak zpracovat <xref:System.Windows.Forms.BindingManagerBase.BindingComplete> událost pro <xref:System.Windows.Forms.BindingManagerBase>. Příklad toho, jak to provést naleznete na stránce nápovědy <xref:System.Windows.Forms.BindingManagerBase.BindingComplete> události <xref:System.Windows.Forms.BindingManagerBase>.  
  
 [!code-csharp[System.Windows.Forms.BindingSourceMultipleControls#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleControls/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingSourceMultipleControls#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleControls/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Tento příklad kódu vyžaduje  
  
-   Odkazuje na <xref:System>, <xref:System.Windows.Forms>, a <xref:System.Drawing> sestavení.  
  
-   Formulář s <xref:System.Windows.Forms.Form.Load> zpracovává události a volání `InitializeControlsAndDataSource` metoda v příkladu z formuláře <xref:System.Windows.Forms.Form.Load> obslužné rutiny události.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Sdílení vázaných dat mezi formuláři pomocí komponenty BindingSource](../../../docs/framework/winforms/controls/how-to-share-bound-data-across-forms-using-the-bindingsource-component.md)  
 [Oznámení změn v datové vazbě Windows Forms](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 [Rozhraní související s datovou vazbou](../../../docs/framework/winforms/interfaces-related-to-data-binding.md)  
 [Windows Forms – datová vazba](../../../docs/framework/winforms/windows-forms-data-binding.md)
