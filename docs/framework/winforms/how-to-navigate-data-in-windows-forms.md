---
title: 'Postupy: Procházení dat v rozhraní Windows Forms'
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
ms.openlocfilehash: eb973497f51592b5d34c22e62da77612aec23c35
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964280"
---
# <a name="how-to-navigate-data-in-windows-forms"></a>Postupy: Procházení dat v rozhraní Windows Forms
V aplikaci pro Windows nejjednodušší způsob, jak procházet záznamy ve zdroji dat, je vytvořit vazby <xref:System.Windows.Forms.BindingSource> komponenty ke zdroji dat a potom navazovat ovládací prvky <xref:System.Windows.Forms.BindingSource>na. Pak můžete použít integrovanou navigační metodu <xref:System.Windows.Forms.BindingSource> pro <xref:System.Windows.Forms.BindingSource.MoveNext%2A>tyto metody, <xref:System.Windows.Forms.BindingSource.MoveLast%2A> <xref:System.Windows.Forms.BindingSource.MovePrevious%2A> a <xref:System.Windows.Forms.BindingSource.MoveFirst%2A>. Pomocí těchto metod se upraví <xref:System.Windows.Forms.BindingSource.Position%2A> vlastnosti <xref:System.Windows.Forms.BindingSource.Current%2A> <xref:System.Windows.Forms.BindingSource> a odpovídajícím způsobem. Můžete také najít položku a nastavit ji jako aktuální položku <xref:System.Windows.Forms.BindingSource.Position%2A> nastavením vlastnosti.  
  
### <a name="to-increment-the-position-in-a-data-source"></a>Zvýšení pozice ve zdroji dat  
  
1. <xref:System.Windows.Forms.BindingSource.Position%2A> Nastavte vlastnost <xref:System.Windows.Forms.BindingSource> pro vázaná data na umístění záznamu, na který chcete přejít. Následující příklad ukazuje <xref:System.Windows.Forms.BindingSource.MoveNext%2A> použití metody <xref:System.Windows.Forms.BindingSource> pro <xref:System.Windows.Forms.BindingSource.Position%2A> zvýšení vlastnosti při kliknutí. `nextButton` Je spojen s tabulkou datové sady `Northwind`. `Customers` <xref:System.Windows.Forms.BindingSource>  
  
    > [!NOTE]
    > <xref:System.Windows.Forms.BindingSource.Position%2A> Nastavení vlastnosti na hodnotu mimo první nebo poslední záznam nevede k chybě, protože .NET Framework neumožní nastavit pozici na hodnotu mimo hranice seznamu. Pokud je důležité ve vaší aplikaci zjistit, zda jste prošli za prvním nebo posledním záznamem, zahrňte logiku pro otestování, zda budete přesáhnout počet datových prvků.  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.NavigatingData#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#4)]  
  
### <a name="to-check-whether-you-have-passed-the-end-or-beginning"></a>Chcete-li ověřit, zda jste prošli koncem nebo začátkem  
  
1. Vytvořte obslužnou rutinu události pro <xref:System.Windows.Forms.BindingSource.PositionChanged> událost. V obslužné rutině můžete testovat, zda hodnota navrhované pozice překročila skutečný počet datových elementů.  
  
     Následující příklad ukazuje, jak můžete testovat, zda jste dosáhli posledního datového prvku. V příkladu, pokud jste na posledním prvku, je tlačítko **Další** ve formuláři zakázané.  
  
    > [!NOTE]
    > Pamatujte na to, že pokud změníte seznam, který v kódu procházíte, měli byste znovu povolit tlačítko **Další** , aby uživatelé mohli procházet celou délku nového seznamu. Kromě toho mějte na paměti, že <xref:System.Windows.Forms.BindingSource.PositionChanged> výše uvedená událost pro <xref:System.Windows.Forms.BindingSource> konkrétní, se kterou pracujete, musí být přidružená ke své metodě zpracování událostí. Následuje příklad metody pro zpracování <xref:System.Windows.Forms.BindingSource.PositionChanged> události:  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.NavigatingData#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#3)]  
  
### <a name="to-find-an-item-and-set-it-as-the-current-item"></a>Vyhledání položky a její nastavení jako aktuální položky  
  
1. Vyhledejte záznam, který chcete nastavit jako aktuální položku. To lze provést pomocí <xref:System.Windows.Forms.BindingSource.Find%2A> metody <xref:System.Windows.Forms.BindingSource>, pokud váš zdroj dat implementuje <xref:System.ComponentModel.IBindingList>. Některé příklady zdrojů dat, které implementují <xref:System.ComponentModel.IBindingList> , <xref:System.Data.DataView>jsou <xref:System.ComponentModel.BindingList%601> a.  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.NavigatingData#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#2)]  
  
## <a name="see-also"></a>Viz také:

- [Zdroje dat podporované rozhraním Windows Forms](data-sources-supported-by-windows-forms.md)
- [Oznámení změn v datové vazbě Windows Forms](change-notification-in-windows-forms-data-binding.md)
- [Datové vazby a Windows Forms](data-binding-and-windows-forms.md)
- [Windows Forms – datová vazba](windows-forms-data-binding.md)
