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
ms.openlocfilehash: 73ed25406aa398aa35c275b20da1deee48b119ab
ms.sourcegitcommit: f28752eab00d2bd97e971542c0f49ce63cfbc239
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2018
---
# <a name="how-to-create-a-simple-binding"></a>Postupy: Vytváření jednoduchých připojení
Tento příklad ukazuje, jak vytvořit jednoduchou <xref:System.Windows.Data.Binding>.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu jsou k dispozici `Person` objekt s řetězec vlastnost s názvem `PersonName`. `Person` Objekt je definován v oboru názvů názvem `SDKSample`.  
  
 Následující příklad vytvoří `Person` objektu s `PersonName` hodnota vlastnosti `Joe`. To se provádí v `Resources` části a přiřazené `x:Key`.  
  
 [!code-xaml[SimpleBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml)]  
  
 K vytvoření vazby `PersonName` vlastnost by postupujte takto:  
  
 [!code-xaml[SimpleBinding#BDO1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#bdo1)]  
  
 V důsledku toho <xref:System.Windows.Controls.TextBlock> se zobrazí s hodnotou "Jan".  
  
## <a name="see-also"></a>Viz také  
 [Přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Témata s postupy](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
