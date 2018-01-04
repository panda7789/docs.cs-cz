---
title: "Postupy: Implementace rozhraní ITypedList"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ITypedList interface
- BindingList(Of T) class
- data binding [Windows Forms], implementing
- IBindingList interface
ms.assetid: 834cc15c-50bc-4a8b-a610-313d6a217357
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 09eb28e865fb020dae9a8b6ffc3f05a52e6eec4a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-the-itypedlist-interface"></a>Postupy: Implementace rozhraní ITypedList
Implementace <xref:System.ComponentModel.ITypedList> rozhraní chcete zapnout zjišťování schéma pro vazbu seznamu.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak implementovat <xref:System.ComponentModel.ITypedList> rozhraní. Obecný typ s názvem `SortableBindingList` je odvozena z <xref:System.ComponentModel.BindingList%601> třídy a implementuje <xref:System.ComponentModel.ITypedList> rozhraní. Jednoduché třídy s názvem `Customer` poskytuje data, která je vázána na záhlaví <xref:System.Windows.Forms.DataGridView> ovládacího prvku.  
  
 [!code-csharp[System.ComponentModel.ITypedList#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.ITypedList/CS/SortableBindingList.cs#1)]
 [!code-vb[System.ComponentModel.ITypedList#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.ITypedList/VB/SortableBindingList.vb#1)]  
  
 [!code-csharp[System.ComponentModel.ITypedList#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.ITypedList/CS/Customer.cs#10)]
 [!code-vb[System.ComponentModel.ITypedList#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.ITypedList/VB/Customer.vb#10)]  
  
 [!code-csharp[System.ComponentModel.ITypedList#100](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.ITypedList/CS/Form1.cs#100)]
 [!code-vb[System.ComponentModel.ITypedList#100](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.ITypedList/VB/Form1.vb#100)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkazy na sestavení System.Drawing a System.Windows.Forms.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ComponentModel.ITypedList>  
 <xref:System.ComponentModel.BindingList%601>  
 <xref:System.ComponentModel.IBindingList>  
 [Datové vazby a Windows Forms](../../../docs/framework/winforms/data-binding-and-windows-forms.md)
