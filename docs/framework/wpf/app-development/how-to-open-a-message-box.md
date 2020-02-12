---
title: 'Postupy: otevření okna se zprávou'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message boxes [WPF], opening
- opening message boxes [WPF]
ms.assetid: acaad17f-af43-4eca-a004-f1c9e7c6f292
ms.openlocfilehash: bd2c4dce78e46163eb4628cb3aab829fc0173edf
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77123724"
---
# <a name="how-to-open-a-message-box"></a>Postupy: otevření okna se zprávou
Tento příklad ukazuje, jak otevřít okno se zprávou.  
  
## <a name="example"></a>Příklad  
 Okno se zprávou je přednastavené modální dialogové okno pro zobrazení informací uživatelům. Okno se zprávou je otevřeno voláním metody static <xref:System.Windows.MessageBox.Show%2A> třídy <xref:System.Windows.MessageBox>. Při volání <xref:System.Windows.MessageBox.Show%2A> je zpráva předána pomocí řetězcového parametru. Několik přetížení <xref:System.Windows.MessageBox.Show%2A> umožňuje nakonfigurovat, jak se zobrazí okno se zprávou (viz <xref:System.Windows.MessageBox>).  
  
 [!code-csharp[MessageBoxSnippets#MessageBoxShow1CODE](~/samples/snippets/csharp/VS_Snippets_Wpf/MessageBoxSnippets/CSharp/Show1Window.xaml.cs#messageboxshow1code)]
 [!code-vb[MessageBoxSnippets#MessageBoxShow1CODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MessageBoxSnippets/visualbasic/show1window.xaml.vb#messageboxshow1code)]  
  
## <a name="see-also"></a>Viz také

- [MessageBox – ukázka](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/MessageBox)
