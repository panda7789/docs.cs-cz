---
title: 'Postupy: Vytváření jednoduchých připojení'
ms.date: 03/30/2017
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
ms.openlocfilehash: 8910dd3ec6c9f72f9d8fb64cd33912f0d4318e5f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-simple-binding"></a>Postupy: Vytváření jednoduchých připojení
Tento příklad ukazuje, jak vytvořit jednoduchou <xref:System.Windows.Data.Binding>.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu jsou k dispozici `Person` objekt s řetězec vlastnost s názvem `PersonName`. `Person` Objekt je definován v oboru názvů názvem `SDKSample`.  
  
 Zvýrazněný řádek, který obsahuje `<src>` element v následujícím příkladu se vytvoří instance `Person` objektu s `PersonName` hodnota vlastnosti `Joe`. To se provádí v `Resources` části a přiřazené `x:Key`.  
  
 [!code-xaml[SimpleBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 Zvýrazněný řádek, který obsahuje `<TextBlock>` element pak váže <xref:System.Windows.Controls.TextBlock> řídit k `PersonName` vlastnost. V důsledku toho <xref:System.Windows.Controls.TextBlock> se zobrazí s hodnotou "Jan".  
  
## <a name="see-also"></a>Viz také  
 [Přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Témata s postupy](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
