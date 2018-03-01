---
title: "Postupy: získání všech oken v aplikaci"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- window objects [WPF], getting
ms.assetid: f120f06e-993b-4a97-9657-af0d1986981f
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fdb1baad8b779b6ef0443a05e5f6575b552b1c19
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-get-all-windows-in-an-application"></a>Postupy: získání všech oken v aplikaci
Tento příklad ukazuje, jak získat všechny <xref:System.Windows.Window> objekty v aplikaci.  
  
## <a name="example"></a>Příklad  
 Každé instanci <xref:System.Windows.Window> objektu, zda je viditelná nebo Ne, se automaticky přidá do kolekce odkazů na okno, které spravuje <xref:System.Windows.Application>a zveřejněné z <xref:System.Windows.Application.Windows%2A>.  
  
 Můžete vytvořit výčet <xref:System.Windows.Application.Windows%2A> získat všech instancí systému windows pomocí následujícího kódu:  
  
 [!code-csharp[HOWTOWindowManagementSnippets#GetAllWindows](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/CustomWindow.xaml.cs#getallwindows)]
 [!code-vb[HOWTOWindowManagementSnippets#GetAllWindows](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/customwindow.xaml.vb#getallwindows)]
