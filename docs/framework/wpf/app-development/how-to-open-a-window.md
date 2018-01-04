---
title: "Postupy: otevření okna"
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
helpviewer_keywords:
- windows [WPF], opening
- opening windows [WPF]
ms.assetid: 6b91b2bb-fda7-491d-a72e-139dd630a5b0
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c6f3efda8257d9f7ed843438b0e9fb42e13de2c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-open-a-window"></a>Postupy: otevření okna
Tento příklad ukazuje, jak k otevření okna.  
  
## <a name="example"></a>Příklad  
 Po vytvoření instance je otevřené okno <xref:System.Windows.Window> a volání <xref:System.Windows.Window.Show%2A> metoda. <xref:System.Windows.Window.Show%2A>Otevře se okno a vrátí okamžitě bez čekání na nové okno zavřete. Tento typ okna je také označován jako *nemodální* okně a není omezit vstup uživatele.  
  
 [!code-csharp[HOWTOWindowManagementSnippets#OpenNewWindowCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#opennewwindowcode)]
 [!code-vb[HOWTOWindowManagementSnippets#OpenNewWindowCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#opennewwindowcode)]  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Vytváření instancí <xref:System.Windows.Window> vyžaduje oprávnění k volání metody unsafe nativní (viz <xref:System.Windows.Window.%23ctor%2A>).
