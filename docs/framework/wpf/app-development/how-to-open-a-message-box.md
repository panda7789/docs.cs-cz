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
ms.openlocfilehash: f05190030ed6324917348fa1926abd5385e30f7e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43425809"
---
# <a name="how-to-open-a-message-box"></a>Postupy: otevření okna se zprávou
Tento příklad ukazuje, jak otevřít okno se zprávou.  
  
## <a name="example"></a>Příklad  
 Okno se zprávou je prefabrikované modální dialogové okno pro zobrazení informací o uživateli. Zavoláním statické se otevře okno se zprávou <xref:System.Windows.MessageBox.Show%2A> metodu <xref:System.Windows.MessageBox> třídy. Když <xref:System.Windows.MessageBox.Show%2A> je volána, předávání zpráv pomocí parametru řetězce. Několik přetížení <xref:System.Windows.MessageBox.Show%2A> umožňují konfigurovat, jak se zobrazí okno se zprávou (viz <xref:System.Windows.MessageBox>).  
  
 [!code-csharp[MessageBoxSnippets#MessageBoxShow1CODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MessageBoxSnippets/CSharp/Show1Window.xaml.cs#messageboxshow1code)]
 [!code-vb[MessageBoxSnippets#MessageBoxShow1CODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MessageBoxSnippets/visualbasic/show1window.xaml.vb#messageboxshow1code)]  
  
## <a name="see-also"></a>Viz také  
 [Ukázka MessageBox](https://go.microsoft.com/fwlink/?LinkID=160023)
