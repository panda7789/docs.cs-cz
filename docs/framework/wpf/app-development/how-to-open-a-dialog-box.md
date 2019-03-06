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
ms.openlocfilehash: 1182e22ad40b49ee13832c51986662373f36ee35
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57351980"
---
# <a name="how-to-open-a-dialog-box"></a>Postupy: Otevřete dialogové okno
Tento příklad ukazuje, jak otevřít dialogové okno.  
  
## <a name="example"></a>Příklad  
 Dialogové okno je okno, které se otevře po vytvoření instance <xref:System.Windows.Window> a volání <xref:System.Windows.Window.ShowDialog%2A> metody. <xref:System.Windows.Window.ShowDialog%2A> Otevře se okno a nevrací, dokud se nové dialogové okno se zavřelo. Tento typ okno se také označuje jako *modální* okna a omezí vstup uživatele.  
  
 [!code-csharp[HOWTOWindowManagementSnippets#OpenNewDialogBoxCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/CSharp/MainWindow.xaml.cs#opennewdialogboxcode)]
 [!code-vb[HOWTOWindowManagementSnippets#OpenNewDialogBoxCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HOWTOWindowManagementSnippets/visualbasic/mainwindow.xaml.vb#opennewdialogboxcode)]  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Volání <xref:System.Windows.Window.ShowDialog%2A> vyžaduje souhlas s používáním všechna okna a události uživatelského vstupu bez omezení.  
  
## <a name="see-also"></a>Viz také:
- [Vrácení výsledku dialogového okna](how-to-return-a-dialog-box-result.md)
