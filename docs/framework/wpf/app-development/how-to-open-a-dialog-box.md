---
title: 'Postupy: Otevření dialogového okna'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- opening dialog boxes [WPF]
- dialog boxes [WPF], opening
ms.assetid: 6b1557d2-da98-4ef4-9f68-4089f04ab9ea
ms.openlocfilehash: 70ac31285dd22244b4bd6ad0d188d182eb6e6264
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59084964"
---
# <a name="how-to-open-a-dialog-box"></a>Postupy: Otevření dialogového okna
Tento příklad ukazuje, jak otevřít dialogové okno.  
  
## <a name="example"></a>Příklad  
 Dialogové okno je okno, které se otevře po vytvoření instance <xref:System.Windows.Window> a volání <xref:System.Windows.Window.ShowDialog%2A> metody. <xref:System.Windows.Window.ShowDialog%2A> Otevře se okno a nevrací, dokud se nové dialogové okno se zavřelo. Tento typ okno se také označuje jako *modální* okna a omezí vstup uživatele.  
  
 [!code-csharp[HOWTOWindowManagementSnippets#OpenNewDialogBoxCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#opennewdialogboxcode)]
 [!code-vb[HOWTOWindowManagementSnippets#OpenNewDialogBoxCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#opennewdialogboxcode)]  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Volání <xref:System.Windows.Window.ShowDialog%2A> vyžaduje souhlas s používáním všechna okna a události uživatelského vstupu bez omezení.  
  
## <a name="see-also"></a>Viz také:

- [Vrácení výsledku dialogového okna](how-to-return-a-dialog-box-result.md)
