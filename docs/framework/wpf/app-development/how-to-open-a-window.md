---
title: 'Postupy: otevření okna'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- windows [WPF], opening
- opening windows [WPF]
ms.assetid: 6b91b2bb-fda7-491d-a72e-139dd630a5b0
ms.openlocfilehash: 23dc74666d8f47a0fb735d96ad22ed56c96bdbc5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545461"
---
# <a name="how-to-open-a-window"></a>Postupy: otevření okna
Tento příklad ukazuje, jak k otevření okna.  
  
## <a name="example"></a>Příklad  
 Po vytvoření instance je otevřené okno <xref:System.Windows.Window> a volání <xref:System.Windows.Window.Show%2A> metoda. <xref:System.Windows.Window.Show%2A> Otevře se okno a vrátí okamžitě bez čekání na nové okno zavřete. Tento typ okna je také označován jako *nemodální* okně a není omezit vstup uživatele.  
  
 [!code-csharp[HOWTOWindowManagementSnippets#OpenNewWindowCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#opennewwindowcode)]
 [!code-vb[HOWTOWindowManagementSnippets#OpenNewWindowCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#opennewwindowcode)]  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Vytváření instancí <xref:System.Windows.Window> vyžaduje oprávnění k volání metody unsafe nativní (viz <xref:System.Windows.Window.%23ctor%2A>).
