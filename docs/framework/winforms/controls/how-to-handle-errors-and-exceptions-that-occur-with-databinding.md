---
title: 'Postupy: Zpracování chyb a výjimek, k nimž došlo v souvislosti s datovou vazbou'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- error handling [Windows Forms], examples
- data binding [Windows Forms], examples
- examples [Windows Forms], error handling
- error handling [Windows Forms], data binding
- data binding [Windows Forms], error handling
- BindingSource component [Windows Forms], handling errors and exceptions
ms.assetid: eddc5bad-9513-47df-ab28-f02d8dff7892
ms.openlocfilehash: 14326d793be3ee71022a7a1e7398b9af469aab10
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592447"
---
# <a name="how-to-handle-errors-and-exceptions-that-occur-with-databinding"></a>Postupy: Zpracování chyb a výjimek, k nimž došlo v souvislosti s datovou vazbou
Často výjimky a chyby dojde u podkladových objektů obchodní svázat s ovládacími prvky. Můžete zachytit tyto chyby a výjimky a potom obnovit nebo předat informace o chybě pro uživatele pomocí manipulace <xref:System.Windows.Forms.Binding.BindingComplete> události pro konkrétní <xref:System.Windows.Forms.Binding>, <xref:System.Windows.Forms.BindingSource>, nebo <xref:System.Windows.Forms.CurrencyManager> komponenty.  
  
## <a name="example"></a>Příklad  
 Tento příklad kódu ukazuje, jak zpracování chyb a výjimek, ke kterým dochází při operaci datové vazby. Ukazuje, jak zachytávat chyby pomocí manipulace <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> událost <xref:System.Windows.Forms.Binding> objekty. Pokud chcete zachytávat chyby a výjimky ve zpracování této události, je nutné povolit formátování pro vazbu. Můžete povolit formátování, pokud vazba je vytvořen nebo přidat do kolekce vazby nebo nastavením <xref:System.Windows.Forms.Binding.FormattingEnabled%2A> vlastnost `true`.  
  
 [!code-cpp[System.Windows.Forms.DataConnectorBindingComplete#3](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/CPP/form1.cpp#3)]
 [!code-csharp[System.Windows.Forms.DataConnectorBindingComplete#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/CS/form1.cs#3)]
 [!code-vb[System.Windows.Forms.DataConnectorBindingComplete#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/VB/form1.vb#3)]  
  
 Když je kód spuštěn a prázdný řetězec je zadána pro název součásti nebo hodnotu nižší než 100 je zadána pro výrobní číslo se zobrazí okno se zprávou. To je výsledkem zpracování <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> událost pro tyto vazby textové pole.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení systému, System.Drawing a System.Windows.Forms.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType>
- <xref:System.Windows.Forms.BindingSource.BindingComplete?displayProperty=nameWithType>
- [Komponenta BindingSource](bindingsource-component.md)
