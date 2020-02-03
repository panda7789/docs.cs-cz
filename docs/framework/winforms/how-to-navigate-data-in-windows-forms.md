---
title: 'Postupy: navigace v datech'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cursors [Windows Forms], data sources
- data sources [Windows Forms], Windows Forms
- Windows Forms, navigating
- CurrencyManager class [Windows Forms], navigating Windows Forms data
- data [Windows Forms], navigating
ms.assetid: 97360f7b-b181-4084-966a-4c62518f735b
ms.openlocfilehash: 2dd900b652b0ff21ea0eb0dbc5463b22c869ec7c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739398"
---
# <a name="how-to-navigate-data-in-windows-forms"></a>Postupy: Procházení dat v rozhraní Windows Forms
V aplikaci pro Windows nejjednodušší způsob, jak procházet záznamy ve zdroji dat, je vytvořit navázání <xref:System.Windows.Forms.BindingSource> komponenty ke zdroji dat a potom navazovat ovládací prvky na <xref:System.Windows.Forms.BindingSource>. Pak můžete použít integrovanou navigační metodu na <xref:System.Windows.Forms.BindingSource> jako <xref:System.Windows.Forms.BindingSource.MoveNext%2A>, <xref:System.Windows.Forms.BindingSource.MoveLast%2A>, <xref:System.Windows.Forms.BindingSource.MovePrevious%2A> a <xref:System.Windows.Forms.BindingSource.MoveFirst%2A>. Pomocí těchto metod se odpovídajícím způsobem upraví <xref:System.Windows.Forms.BindingSource.Position%2A> a vlastnosti <xref:System.Windows.Forms.BindingSource.Current%2A> <xref:System.Windows.Forms.BindingSource>. Můžete také najít položku a nastavit ji jako aktuální položku nastavením vlastnosti <xref:System.Windows.Forms.BindingSource.Position%2A>.  
  
### <a name="to-increment-the-position-in-a-data-source"></a>Zvýšení pozice ve zdroji dat  
  
1. Nastavte vlastnost <xref:System.Windows.Forms.BindingSource.Position%2A> <xref:System.Windows.Forms.BindingSource> pro vázaná data na umístění záznamu, na který chcete přejít. Následující příklad ukazuje použití metody <xref:System.Windows.Forms.BindingSource.MoveNext%2A> <xref:System.Windows.Forms.BindingSource> k zvýšení vlastnosti <xref:System.Windows.Forms.BindingSource.Position%2A> při kliknutí na `nextButton`. <xref:System.Windows.Forms.BindingSource> je přidružená k `Customers` tabulce datové sady `Northwind`.  
  
    > [!NOTE]
    > Nastavení vlastnosti <xref:System.Windows.Forms.BindingSource.Position%2A> na hodnotu mimo první nebo poslední záznam nevede k chybě, protože .NET Framework nedovolí nastavit pozici na hodnotu mimo hranice seznamu. Pokud je důležité ve vaší aplikaci zjistit, zda jste prošli za prvním nebo posledním záznamem, zahrňte logiku pro otestování, zda budete přesáhnout počet datových prvků.  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.NavigatingData#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#4)]  
  
### <a name="to-check-whether-you-have-passed-the-end-or-beginning"></a>Chcete-li ověřit, zda jste prošli koncem nebo začátkem  
  
1. Vytvořte obslužnou rutinu události pro událost <xref:System.Windows.Forms.BindingSource.PositionChanged>. V obslužné rutině můžete testovat, zda hodnota navrhované pozice překročila skutečný počet datových elementů.  
  
     Následující příklad ukazuje, jak můžete testovat, zda jste dosáhli posledního datového prvku. V příkladu, pokud jste na posledním prvku, je tlačítko **Další** ve formuláři zakázané.  
  
    > [!NOTE]
    > Pamatujte na to, že pokud změníte seznam, který v kódu procházíte, měli byste znovu povolit tlačítko **Další** , aby uživatelé mohli procházet celou délku nového seznamu. Kromě toho mějte na paměti, že výše uvedená událost <xref:System.Windows.Forms.BindingSource.PositionChanged> pro konkrétní <xref:System.Windows.Forms.BindingSource>, se kterou pracujete, musí být přidružená ke své metodě zpracování událostí. Následuje příklad metody pro zpracování <xref:System.Windows.Forms.BindingSource.PositionChanged> události:  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.NavigatingData#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#3)]  
  
### <a name="to-find-an-item-and-set-it-as-the-current-item"></a>Vyhledání položky a její nastavení jako aktuální položky  
  
1. Vyhledejte záznam, který chcete nastavit jako aktuální položku. To lze provést pomocí metody <xref:System.Windows.Forms.BindingSource.Find%2A> <xref:System.Windows.Forms.BindingSource>, pokud zdroj dat implementuje <xref:System.ComponentModel.IBindingList>. Některé příklady zdrojů dat, které implementují <xref:System.ComponentModel.IBindingList>, jsou <xref:System.ComponentModel.BindingList%601> a <xref:System.Data.DataView>.  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.NavigatingData#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#2)]  
  
## <a name="see-also"></a>Viz také

- [Zdroje dat podporované rozhraním Windows Forms](data-sources-supported-by-windows-forms.md)
- [Oznámení změn v datové vazbě Windows Forms](change-notification-in-windows-forms-data-binding.md)
- [Datové vazby a Windows Forms](data-binding-and-windows-forms.md)
- [Windows Forms – datová vazba](windows-forms-data-binding.md)
