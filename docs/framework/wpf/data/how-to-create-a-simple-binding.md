---
title: 'Postupy: Vytváření jednoduchých připojení'
ms.date: 03/30/2017
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
ms.openlocfilehash: faef59ed426059eb2d488d0584d3325c8d46d415
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73453509"
---
# <a name="how-to-create-a-simple-binding"></a>Postupy: Vytváření jednoduchých připojení
V tomto příkladu se dozvíte, jak vytvořit jednoduchý <xref:System.Windows.Data.Binding>.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu máte objekt `Person` s vlastností řetězce s názvem `PersonName`. Objekt `Person` je definován v oboru názvů s názvem `SDKSample`.  
  
 Zvýrazněný řádek, který obsahuje prvek `<src>` v následujícím příkladu vytvoří instanci objektu `Person` s hodnotou vlastnosti `PersonName` `Joe`. To se provádí v části `Resources` a přiřazená `x:Key`.  
  
 [!code-xaml[SimpleBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 Zvýrazněný řádek, který obsahuje prvek `<TextBlock>` poté sváže ovládací prvek <xref:System.Windows.Controls.TextBlock> s vlastností `PersonName`. V důsledku toho se <xref:System.Windows.Controls.TextBlock> zobrazí s hodnotou "Jana".  
  
## <a name="see-also"></a>Viz také:

- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [Témata s postupy](data-binding-how-to-topics.md)
