---
title: 'Postupy: Vyberte položku v ovládacím prvku Windows Forms ListView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lists [Windows Forms], selecting items
- ListView control [Windows Forms], selecting items
- selection [Windows Forms], in list views
- list views [Windows Forms], selecting items
ms.assetid: ddea918e-1ddf-47f4-bd09-1e9b4c9d0c39
ms.openlocfilehash: 09ec0b60e5d591f4cc66cf5ed454576203afa473
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57707025"
---
# <a name="how-to-select-an-item-in-the-windows-forms-listview-control"></a>Postupy: Vyberte položku v ovládacím prvku Windows Forms ListView
Tento příklad ukazuje, jak prostřednictvím kódu programu vyberte položku ve Windows Forms <xref:System.Windows.Forms.ListView> ovládacího prvku. Výběr položky pomocí programu nezmění automaticky fokus <xref:System.Windows.Forms.ListView> ovládacího prvku. Z tohoto důvodu se obvykle také chcete nastavit položku jako fokus při výběru položky.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.ListView.Misc#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Misc#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Misc/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   A <xref:System.Windows.Forms.ListView> ovládací prvek s názvem `listView1` , který obsahuje alespoň jednu položku.  
  
-   Odkazy <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> obory názvů.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.ListView>
- <xref:System.Windows.Forms.ListViewItem.Selected%2A?displayProperty=nameWithType>
