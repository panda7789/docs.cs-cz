---
title: 'Postupy: Detekce stisknuté klávesy Enter'
description: Rozpoznat, kdy je na klávesnici v Windows Presentation Foundation vybraný klávesa ENTER Tento příklad se skládá z XAML a souboru kódu na pozadí.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Enter key [WPF], detecting
- keys [WPF], Enter
ms.assetid: a66f39d2-ef4a-43a5-b454-a4ea0fe88655
ms.openlocfilehash: a955f52ec7bf93b32c70259b27fb51747664ac2e
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87163182"
---
# <a name="how-to-detect-when-the-enter-key-pressed"></a>Postupy: Detekce stisknuté klávesy Enter
Tento příklad ukazuje, jak zjistit, kdy se <xref:System.Windows.Input.Key.Enter> klávesa stiskne na klávesnici.  
  
 Tento příklad se skládá ze [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] souboru a souboru kódu na pozadí.  
  
## <a name="example"></a>Příklad  
 Když uživatel stiskne klávesu <xref:System.Windows.Input.Key.Enter> v <xref:System.Windows.Controls.TextBox> , zobrazí se vstup v textovém poli v jiné oblasti [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] .  
  
 Následující kód XAML vytvoří uživatelské rozhraní, které se skládá z typu <xref:System.Windows.Controls.StackPanel> , a <xref:System.Windows.Controls.TextBlock> a <xref:System.Windows.Controls.TextBox> .  
  
 [!code-xaml[keydown#KeyDownUI](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml#keydownui)]  
  
 Následující kód na pozadí vytvoří <xref:System.Windows.UIElement.KeyDown> obslužnou rutinu události.  Pokud klávesa, která se stiskne <xref:System.Windows.Input.Key.Enter> , je klíč, zobrazí se zpráva v <xref:System.Windows.Controls.TextBlock> .  
  
 [!code-csharp[keydown#KeyDownSample](~/samples/snippets/csharp/VS_Snippets_Wpf/KeyDown/CSharp/Window1.xaml.cs#keydownsample)]
 [!code-vb[keydown#KeyDownSample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/KeyDown/VisualBasic/Window1.xaml.vb#keydownsample)]  
  
## <a name="see-also"></a>Viz také

- [Přehled vstupu](input-overview.md)
- [Přehled směrovaných událostí](routed-events-overview.md)
