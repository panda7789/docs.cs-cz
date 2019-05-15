---
title: 'Postupy: Vytvoření vazby ovládacích prvků Windows Forms k hodnotám databáze DBNull'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BindingSource component [Windows Forms], binding to DBNull values
- examples [Windows Forms], BindingSource component
- controls [Windows Forms], binding to DBNull values
ms.assetid: 96494e6f-5f40-4f83-af97-bbd7192c2af8
ms.openlocfilehash: 8abce5d69a7cece6528e0c9d8728de0e0acd9305
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591425"
---
# <a name="how-to-bind-windows-forms-controls-to-dbnull-database-values"></a>Postupy: Vytvoření vazby ovládacích prvků Windows Forms k hodnotám databáze DBNull
Při připojení ovládacích prvků Windows Forms ke zdroji dat a zdroj dat vrátí <xref:System.DBNull> hodnotu, můžete nahradit odpovídající hodnotu bez zpracování, formátování a analýzu událostí. <xref:System.Windows.Forms.Binding.NullValue%2A> Vlastnost převede <xref:System.DBNull> zadanému objektu při formátování nebo analýzy dat zdrojové hodnoty.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit vazbu <xref:System.DBNull> hodnoty ve dvou různých situacích. První ukazuje, jak nastavit <xref:System.Windows.Forms.Binding.NullValue%2A> pro vlastnosti typu string, druhý ukazuje, jak nastavit <xref:System.Windows.Forms.Binding.NullValue%2A> vlastnosti bitové kopie.  
  
 [!code-csharp[System.Windows.Forms.BindingDBNull#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingDBNull#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingDBNull/VB/form1.vb#1)]  
  
 Typy vázané vlastnosti a <xref:System.Windows.Forms.Binding.NullValue%2A> vlastnost musí být stejná nebo dojde k chybě a žádné další <xref:System.Windows.Forms.Binding.NullValue%2A> hodnoty bude zpracována. V takovém případě nebude vyvolána výjimka.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení systému, System.Data, System.Drawing a System.Windows.Forms.  
  
## <a name="see-also"></a>Viz také:

- [Komponenta BindingSource](bindingsource-component.md)
- [Postupy: Zpracování chyb a výjimek, ke kterým dochází s datovou vazbou](how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)
- [Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu](how-to-bind-a-windows-forms-control-to-a-type.md)
