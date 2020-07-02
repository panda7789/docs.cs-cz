---
title: 'Postupy: Vytváření jednoduchých připojení'
description: Pomocí tohoto postupu v Windows Presentation Foundation (WPF) vytvořte jednoduchou vazbu pro vaše aplikace.
ms.date: 03/30/2017
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
ms.openlocfilehash: 63dc44b442bb4658382bf12faf57b51c8e0698bb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618698"
---
# <a name="how-to-create-a-simple-binding"></a>Postupy: Vytváření jednoduchých připojení
V tomto příkladu se dozvíte, jak vytvořit jednoduchou <xref:System.Windows.Data.Binding> .  
  
## <a name="example"></a>Příklad  
 V tomto příkladu máte `Person` objekt s vlastností řetězce s názvem `PersonName` . `Person`Objekt je definován v oboru názvů s názvem `SDKSample` .  
  
 Zvýrazněný řádek, který obsahuje `<src>` prvek v následujícím příkladu, vytvoří instanci `Person` objektu s `PersonName` hodnotou vlastnosti `Joe` . To se provádí v `Resources` oddílu a přiřazeno `x:Key` .  
  
 [!code-xaml[SimpleBinding](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 Zvýrazněný řádek, který obsahuje `<TextBlock>` prvek, potom sváže <xref:System.Windows.Controls.TextBlock> ovládací prvek s `PersonName` vlastností. Výsledkem je, že <xref:System.Windows.Controls.TextBlock> se zobrazí hodnota "Jana".  
  
## <a name="see-also"></a>Viz také:

- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [– postupy](data-binding-how-to-topics.md)
