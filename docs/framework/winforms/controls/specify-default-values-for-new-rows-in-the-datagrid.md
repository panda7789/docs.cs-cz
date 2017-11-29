---
title: "Postupy: Určení výchozích hodnot pro nové řádky v ovládacím prvku Windows Forms DataGridView"
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
- data grids [Windows Forms], default values for new rows
- DataGridView control [Windows Forms], data entry
- rows [Windows Forms], specifying default values
- DataGridView control [Windows Forms], default values for new rows
ms.assetid: 8d127963-d9f8-4e4e-9f7f-beb66688f1f2
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 577d5c3bc4b4afef845cd51b62b7d48fcc9d4a7e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-default-values-for-new-rows-in-the-windows-forms-datagridview-control"></a>Postupy: Určení výchozích hodnot pro nové řádky v ovládacím prvku Windows Forms DataGridView
Vkládání dat můžete nastavit pohodlnější, když aplikace doplní ve výchozí hodnoty pro nově přidaného řádků. S <xref:System.Windows.Forms.DataGridView> třídu, můžete vyplnit ve výchozí hodnoty <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> událostí. Tato událost se vyvolá, když uživatel zadá řádek pro nové záznamy. Když váš kód zpracovává této události, může vyplnit požadované buněk s hodnotami dle vlastního výběru.  
  
 Následující příklad kódu ukazuje, jak zadat výchozí hodnoty pro nové řádky pomocí <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> událostí.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#120)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#120)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.  
  
-   A `NewCustomerId` funkce pro generování jedinečný `CustomerID` hodnoty.  
  
-   Odkazuje na <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>  
 [Vkládání dat v systému Windows Forms DataGridView – ovládací prvek](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 [Použití řádku pro nové záznamy v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
