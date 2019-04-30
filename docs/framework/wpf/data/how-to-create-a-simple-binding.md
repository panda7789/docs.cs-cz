---
title: 'Postupy: Vytvoření jednoduché vazby'
ms.date: 03/30/2017
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
ms.openlocfilehash: d617c8b97aa679398ed2d061a652f5164f1e499b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61931560"
---
# <a name="how-to-create-a-simple-binding"></a>Postupy: Vytvoření jednoduché vazby
Tento příklad ukazuje, jak vytvořit jednoduchou <xref:System.Windows.Data.Binding>.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu je nutné `Person` objekt s řetězcovou vlastnost s názvem `PersonName`. `Person` Objekt je definovaný v oboru názvů volá `SDKSample`.  
  
 Zvýrazněný řádek, který obsahuje `<src>` element v následujícím příkladu vytvoří instanci `Person` objektu `PersonName` hodnotou vlastnosti `Joe`. To se provádí v `Resources` části a přiřazené `x:Key`.  
  
 [!code-xaml[SimpleBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 Zvýrazněný řádek, který obsahuje `<TextBlock>` prvek pak vytvoří vazbu <xref:System.Windows.Controls.TextBlock> ovládací prvek `PersonName` vlastnost. V důsledku toho <xref:System.Windows.Controls.TextBlock> se zobrazí s hodnotou "Jan".  
  
## <a name="see-also"></a>Viz také:

- [Přehled datových vazeb](data-binding-overview.md)
- [Témata s postupy](data-binding-how-to-topics.md)
