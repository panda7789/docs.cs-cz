---
title: 'Postupy: Otevřete dialogové okno'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- opening dialog boxes [WPF]
- dialog boxes [WPF], opening
ms.assetid: 6b1557d2-da98-4ef4-9f68-4089f04ab9ea
ms.openlocfilehash: 29fe8b0d516f20fcc742b91099a30e368dfe4548
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-open-a-dialog-box"></a>Postupy: Otevřete dialogové okno
Tento příklad ukazuje, jak otevřít dialogové okno.  
  
## <a name="example"></a>Příklad  
 Je dialogové okno, ve kterém je otevřen po vytvoření instance <xref:System.Windows.Window> a volání <xref:System.Windows.Window.ShowDialog%2A> metoda. <xref:System.Windows.Window.ShowDialog%2A> Otevře se okno a nevrací dokud dialogové okno Nový bylo ukončeno. Tento typ okna je také označován jako *modální* okně a omezuje vstup uživatele.  
  
 [!code-csharp[HOWTOWindowManagementSnippets#OpenNewDialogBoxCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#opennewdialogboxcode)]
 [!code-vb[HOWTOWindowManagementSnippets#OpenNewDialogBoxCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#opennewdialogboxcode)]  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Volání metody <xref:System.Windows.Window.ShowDialog%2A> vyžaduje oprávnění k používání všechna okna a vstupních událostech uživatele bez omezení.  
  
## <a name="see-also"></a>Viz také  
 [Vrácení výsledku dialogového okna](../../../../docs/framework/wpf/app-development/how-to-return-a-dialog-box-result.md)
