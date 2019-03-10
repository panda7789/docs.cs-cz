---
title: 'Postupy: Zajištění více ovládacích prvků vázaných ke stejnému zdroji dat zůstalo synchronizovaných'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], binding multiple
- controls [Windows Forms], synchronizing with data source
ms.assetid: c2f0ecc6-11e6-4c2c-a1ca-0759630c451e
ms.openlocfilehash: 01cec80c85beb64975648b2250c914fe04d3ac95
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57721382"
---
# <a name="how-to-ensure-multiple-controls-bound-to-the-same-data-source-remain-synchronized"></a>Postupy: Zajištění více ovládacích prvků vázaných ke stejnému zdroji dat zůstalo synchronizovaných
Často při práci s datovou vazbu v modelu Windows Forms, více ovládacích prvků jsou vázány na stejného datového zdroje. V některých případech může být potřeba provést další kroky a ujistěte se, že budou synchronizovány s mezi sebou a zdrojem dat vázané vlastnosti ovládacích prvků. Tyto kroky jsou nezbytné ve dvou situacích:  
  
-   Pokud zdroj dat neimplementuje <xref:System.ComponentModel.IBindingList>a proto generovat <xref:System.ComponentModel.IBindingList.ListChanged> události typu <xref:System.ComponentModel.ListChangedType.ItemChanged>.  
  
-   Pokud zdroj dat implementuje <xref:System.ComponentModel.IEditableObject>.  
  
 V prvním případě můžete použít <xref:System.Windows.Forms.BindingSource> svázat zdroj dat k ovládacím prvkům. V takovém případě použijete <xref:System.Windows.Forms.BindingSource> a zpracovat <xref:System.Windows.Forms.BindingSource.BindingComplete> událostí a volání <xref:System.Windows.Forms.BindingManagerBase.EndCurrentEdit%2A> přidruženého <xref:System.Windows.Forms.BindingManagerBase>.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak vytvořit vazbu tři ovládací prvky – dvou ovládacích prvků textového pole a <xref:System.Windows.Forms.DataGridView> ovládacího prvku – stejný sloupec v <xref:System.Data.DataSet> pomocí <xref:System.Windows.Forms.BindingSource> komponenty. Tento příklad ukazuje, jak zpracovat <xref:System.Windows.Forms.BindingSource.BindingComplete> událostí a ujistěte se, že při změně hodnoty text jednoho textového pole, další textové pole a <xref:System.Windows.Forms.DataGridView> ovládací prvek, se aktualizují správnou hodnotu.  
  
 V příkladu se používá <xref:System.Windows.Forms.BindingSource> k vytvoření vazby zdroje dat a ovládací prvky. Alternativně můžete svázat ovládací prvky přímo ke zdroji dat a načíst <xref:System.Windows.Forms.BindingManagerBase> vazby ve formuláři <xref:System.Windows.Forms.Control.BindingContext%2A> a následně zpracovat <xref:System.Windows.Forms.BindingManagerBase.BindingComplete> událost pro <xref:System.Windows.Forms.BindingManagerBase>. Příklad toho, jak to provést, naleznete na stránce nápovědy <xref:System.Windows.Forms.BindingManagerBase.BindingComplete> událost <xref:System.Windows.Forms.BindingManagerBase>.  
  
 [!code-csharp[System.Windows.Forms.BindingSourceMultipleControls#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleControls/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingSourceMultipleControls#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleControls/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Tento příklad kódu vyžaduje  
  
-   Odkazy <xref:System>, <xref:System.Windows.Forms>, a <xref:System.Drawing> sestavení.  
  
-   Formulář s <xref:System.Windows.Forms.Form.Load> zpracovává události a volání `InitializeControlsAndDataSource` metoda v příkladu ve formuláři <xref:System.Windows.Forms.Form.Load> obslužné rutiny události.  
  
## <a name="see-also"></a>Viz také:
- [Postupy: Sdílení vázaných dat mezi formuláři pomocí komponenty BindingSource](./controls/how-to-share-bound-data-across-forms-using-the-bindingsource-component.md)
- [Oznámení změn v datové vazbě Windows Forms](change-notification-in-windows-forms-data-binding.md)
- [Rozhraní související s datovou vazbou](interfaces-related-to-data-binding.md)
- [Windows Forms – datová vazba](windows-forms-data-binding.md)
