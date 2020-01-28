---
title: Svázání ovládacích prvků s hodnotami databáze DBNull
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BindingSource component [Windows Forms], binding to DBNull values
- examples [Windows Forms], BindingSource component
- controls [Windows Forms], binding to DBNull values
ms.assetid: 96494e6f-5f40-4f83-af97-bbd7192c2af8
ms.openlocfilehash: 175d7f5aee2540916480e2c55a485af1f9d16653
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746663"
---
# <a name="how-to-bind-windows-forms-controls-to-dbnull-database-values"></a>Postupy: Připojení ovládacích prvků Windows Forms k hodnotám databáze DBNull
Když svážete model Windows Forms ovládací prvky ke zdroji dat a zdroj dat vrátí hodnotu <xref:System.DBNull>, můžete nahradit příslušnou hodnotu bez zpracování, formátování nebo analýzy událostí. Vlastnost <xref:System.Windows.Forms.Binding.NullValue%2A> bude při formátování nebo analýze hodnot zdrojů dat převedena <xref:System.DBNull> na zadaný objekt.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit vazby <xref:System.DBNull> hodnoty ve dvou různých situacích. První ukazuje, jak nastavit <xref:System.Windows.Forms.Binding.NullValue%2A> pro řetězcovou vlastnost; druhý ukazuje, jak nastavit <xref:System.Windows.Forms.Binding.NullValue%2A> pro vlastnost obrázku.  
  
 [!code-csharp[System.Windows.Forms.BindingDBNull#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingDBNull#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/VB/form1.vb#1)]  
  
 Typy vázaných vlastností a vlastností <xref:System.Windows.Forms.Binding.NullValue%2A> musí být stejné, nebo dojde k chybě a nebudou zpracovány žádné další <xref:System.Windows.Forms.Binding.NullValue%2A> hodnoty. V takové situaci nebude vyvolána výjimka.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení System, System. data, System. Drawing a System. Windows. Forms.  
  
## <a name="see-also"></a>Viz také:

- [Komponenta BindingSource](bindingsource-component.md)
- [Postupy: Zpracování chyb a výjimek, k nimž došlo v souvislosti s datovou vazbou](how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)
- [Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu](how-to-bind-a-windows-forms-control-to-a-type.md)
