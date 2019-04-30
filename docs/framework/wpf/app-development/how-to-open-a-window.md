---
title: 'Postupy: Otevření okna'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- windows [WPF], opening
- opening windows [WPF]
ms.assetid: 6b91b2bb-fda7-491d-a72e-139dd630a5b0
ms.openlocfilehash: 9ce7ffb3f46dd869fda7893745b531bd02d18ee1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61947677"
---
# <a name="how-to-open-a-window"></a>Postupy: Otevření okna
Tento příklad ukazuje, jak otevřít okno.  
  
## <a name="example"></a>Příklad  
 Po vytvoření instance je otevřené okno <xref:System.Windows.Window> a volání <xref:System.Windows.Window.Show%2A> metody. <xref:System.Windows.Window.Show%2A> Otevře se okno a vrátí hodnotu okamžitě bez čekání na nové okno zavřete. Tento typ okno se také označuje jako *nemodální* okna a nijak neomezuje vstup uživatele.  
  
 [!code-csharp[HOWTOWindowManagementSnippets#OpenNewWindowCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#opennewwindowcode)]
 [!code-vb[HOWTOWindowManagementSnippets#OpenNewWindowCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#opennewwindowcode)]  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Vytvoření instance <xref:System.Windows.Window> vyžaduje oprávnění k volání nebezpečné nativní metody (viz <xref:System.Windows.Window.%23ctor%2A>).
