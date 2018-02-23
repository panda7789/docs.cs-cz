---
title: "Postupy: Vytváření jednoduchých připojení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- simple binding [WPF], creating
- data binding [WPF], creating simple bindings
- binding data [WPF], creating
ms.assetid: 69b80f72-6259-44cb-8294-5bdcebca1e08
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a595f255b014e08b4b5b2036a7b1940e46df268f
ms.sourcegitcommit: 973a12d1e6962cd9a9c263fbfaad040ec8267fe9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/22/2018
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
