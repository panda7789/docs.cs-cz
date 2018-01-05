---
title: "Postupy: Vytvoření tlačítka s obrázkem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: Button controls [WPF], creating
ms.assetid: 607a193c-4098-4dd8-8dc0-51256cec2020
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e95f027a8e3568365fa7957c36241b6ec2c30d28
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-button-that-has-an-image"></a>Postupy: Vytvoření tlačítka s obrázkem
Tento příklad ukazuje, jak zahrnout obrázek na <xref:System.Windows.Controls.Button>.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří dvě <xref:System.Windows.Controls.Button> ovládací prvky. Jeden <xref:System.Windows.Controls.Button> obsahuje text a dalších obsahuje bitovou kopii. Obrázek je ve složce s názvem data, která je podsložkou složky projektu v příkladu. Když uživatel klikne <xref:System.Windows.Controls.Button> obsahujícím bitovou kopii, na pozadí a text dalších <xref:System.Windows.Controls.Button> změnit.  
  
 Tento příklad vytvoří <xref:System.Windows.Controls.Button> řídí pomocí značek, ale kód používá k zápisu <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obslužné rutiny událostí.  
  
 [!code-xaml[BtnColor#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml#4)]  
  
 [!code-csharp[BtnColor#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml.cs#6)]
 [!code-vb[BtnColor#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BtnColor/VisualBasic/Pane1.xaml.vb#6)]  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvky](../../../../docs/framework/wpf/controls/index.md)  
 [Knihovna ovládacích prvků](../../../../docs/framework/wpf/controls/control-library.md)
