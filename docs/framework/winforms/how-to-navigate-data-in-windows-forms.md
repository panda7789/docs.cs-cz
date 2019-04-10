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
ms.openlocfilehash: 2ba33f9ecb3a12a62c41af17d3f9ad6f6e3f8a5d
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59344998"
---
# <a name="how-to-navigate-data-in-windows-forms"></a>Postupy: Procházení dat v rozhraní Windows Forms
V aplikaci Windows, je nejjednodušší způsob, jak procházet záznamy ve zdroji dat pro vazbu <xref:System.Windows.Forms.BindingSource> zdroj dat a vazby ovládacích prvků pro komponentu <xref:System.Windows.Forms.BindingSource>. Pak můžete použít metodu předdefinovanou navigaci na <xref:System.Windows.Forms.BindingSource> takové <xref:System.Windows.Forms.BindingSource.MoveNext%2A>, <xref:System.Windows.Forms.BindingSource.MoveLast%2A>, <xref:System.Windows.Forms.BindingSource.MovePrevious%2A> a <xref:System.Windows.Forms.BindingSource.MoveFirst%2A>. Použití těchto metod se upraví <xref:System.Windows.Forms.BindingSource.Position%2A> a <xref:System.Windows.Forms.BindingSource.Current%2A> vlastnosti <xref:System.Windows.Forms.BindingSource> odpovídajícím způsobem. Můžete také najít položku a nastavte ji jako aktuální položky tak, že nastavíte <xref:System.Windows.Forms.BindingSource.Position%2A> vlastnost.  
  
### <a name="to-increment-the-position-in-a-data-source"></a>Pro zvýšení pozice ve zdroji dat.  
  
1. Nastavte <xref:System.Windows.Forms.BindingSource.Position%2A> vlastnost <xref:System.Windows.Forms.BindingSource> pro vaše data vázaná na pozici záznam přejdete na. Následující příklad ukazuje použití <xref:System.Windows.Forms.BindingSource.MoveNext%2A> metodu <xref:System.Windows.Forms.BindingSource> vyšší <xref:System.Windows.Forms.BindingSource.Position%2A> vlastnost při `nextButton` dojde ke kliknutí na. <xref:System.Windows.Forms.BindingSource> Je přidružený `Customers` tabulku z datové sady `Northwind`.  
  
    > [!NOTE]
    >  Nastavení <xref:System.Windows.Forms.BindingSource.Position%2A> vlastnost na hodnotu za první nebo poslední záznam nemá za následek chybu, jako [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] nedovolí vám umožní nastavit pozice na hodnotu mimo rozsah seznamu. Pokud je to důležité ve vaší aplikaci vědět, jestli jste došli za první nebo poslední záznam, obsahují logiku pro ověření, zda překročí počet prvků data.  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.NavigatingData#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#4)]  
  
### <a name="to-check-whether-you-have-passed-the-end-or-beginning"></a>Chcete-li zkontrolovat, jestli jste předali koncové nebo počáteční  
  
1. Vytvořte obslužnou rutinu události pro <xref:System.Windows.Forms.BindingSource.PositionChanged> událostí. V obslužné rutině můžete zkontrolovat, jestli hodnota navrhované umístění překročil počet prvků skutečná data.  
  
     Následující příklad ukazuje, jak můžete zkontrolovat, jestli jste dosáhli poslední datový element. V příkladu, pokud jste v poslední prvek **Další** tlačítko ve formuláři je zakázané.  
  
    > [!NOTE]
    >  Mějte na paměti, že můžete změnit v seznamu jsou navigace v kódu, měli byste znovu povolit **Další** tlačítko, takže uživatelé můžou procházet celou délku nového seznamu. Kromě toho mějte na paměti, která výše <xref:System.Windows.Forms.BindingSource.PositionChanged> události pro konkrétní <xref:System.Windows.Forms.BindingSource> pracujete se musí přiřadit pomocí jeho metody zpracování událostí. Následuje příklad metody pro zpracování <xref:System.Windows.Forms.BindingSource.PositionChanged> události:  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.NavigatingData#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#3)]  
  
### <a name="to-find-an-item-and-set-it-as-the-current-item"></a>K vyhledání položky a nastavte ji jako aktuální položky  
  
1. Najděte záznam, který chcete nastavit jako aktuální položku. Můžete provést pomocí <xref:System.Windows.Forms.BindingSource.Find%2A> metodu <xref:System.Windows.Forms.BindingSource>, pokud zdroj dat implementuje <xref:System.ComponentModel.IBindingList>. Některé příklady datového zdroje, které implementují <xref:System.ComponentModel.IBindingList> jsou <xref:System.ComponentModel.BindingList%601> a <xref:System.Data.DataView>.  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.NavigatingData#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#2)]  
  
## <a name="see-also"></a>Viz také:

- [Zdroje dat podporované rozhraním Windows Forms](data-sources-supported-by-windows-forms.md)
- [Oznámení změn v datové vazbě rozhraní Windows Forms](change-notification-in-windows-forms-data-binding.md)
- [Datové vazby a rozhraní Windows Forms](data-binding-and-windows-forms.md)
- [Windows Forms – datová vazba](windows-forms-data-binding.md)
