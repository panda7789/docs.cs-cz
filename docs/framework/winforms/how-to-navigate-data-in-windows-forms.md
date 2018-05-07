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
ms.openlocfilehash: 9572c1234c07c77d5df0c9cd58499faafe460e4e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-navigate-data-in-windows-forms"></a>Postupy: Procházení dat v rozhraní Windows Forms
V aplikaci Windows, je nejjednodušší způsob, jak procházet záznamy ze zdroje dat pro vazbu <xref:System.Windows.Forms.BindingSource> součásti na zdroj dat a pak vazby ovládacích prvků <xref:System.Windows.Forms.BindingSource>. Pak můžete použít metodu předdefinovanou navigaci na <xref:System.Windows.Forms.BindingSource> takové <xref:System.Windows.Forms.BindingSource.MoveNext%2A>, <xref:System.Windows.Forms.BindingSource.MoveLast%2A>, <xref:System.Windows.Forms.BindingSource.MovePrevious%2A> a <xref:System.Windows.Forms.BindingSource.MoveFirst%2A>. Pomocí těchto metod se upraví <xref:System.Windows.Forms.BindingSource.Position%2A> a <xref:System.Windows.Forms.BindingSource.Current%2A> vlastnosti <xref:System.Windows.Forms.BindingSource> správně. Můžete také najít položku a nastavte jej jako aktuální položky nastavením <xref:System.Windows.Forms.BindingSource.Position%2A> vlastnost.  
  
### <a name="to-increment-the-position-in-a-data-source"></a>Chcete-li zvýšit pozice ve zdroji dat  
  
1.  Nastavte <xref:System.Windows.Forms.BindingSource.Position%2A> vlastnost <xref:System.Windows.Forms.BindingSource> vázané dat na pozici záznam přejít na. Následující příklad ilustruje, pomocí <xref:System.Windows.Forms.BindingSource.MoveNext%2A> metodu <xref:System.Windows.Forms.BindingSource> k přírůstek <xref:System.Windows.Forms.BindingSource.Position%2A> vlastnost při `nextButton` po kliknutí na. <xref:System.Windows.Forms.BindingSource> Přidružen `Customers` tabulky datové sady `Northwind`.  
  
    > [!NOTE]
    >  Nastavení <xref:System.Windows.Forms.BindingSource.Position%2A> vlastnost na hodnotu nad rámec první nebo poslední záznam nevede k chybě, jako [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] neumožní vám umožní nastavit na hodnotu mimo rozsah seznamu pozici. Pokud je důležité ve vaší aplikaci vědět, jestli jste došli po první nebo poslední záznam, zahrňte logiku k ověření, zda bude překročen počet datových element.  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.NavigatingData#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#4)]  
  
### <a name="to-check-whether-you-have-passed-the-end-or-beginning"></a>Zkontrolujte, zda předané koncové nebo počáteční  
  
1.  Vytvoření obslužné rutiny událostí <xref:System.Windows.Forms.BindingSource.PositionChanged> událostí. V obslužné rutině můžete zkontrolovat, zda hodnota navrhované pozice překročila počet element skutečná data.  
  
     Následující příklad ilustruje, jak můžete zkontrolovat, zda jste dosáhli poslední datový prvek. V příkladu, pokud jste v posledním prvkem **Další** tlačítko ve formuláři je zakázané.  
  
    > [!NOTE]
    >  Mějte na paměti, že můžete změnit v seznamu jsou navigace v kódu, měli byste znovu povolit **Další** tlačítko tak, aby uživatelé mohou procházet celou délku nového seznamu. Kromě toho mějte na paměti, výše <xref:System.Windows.Forms.BindingSource.PositionChanged> událostí pro konkrétní <xref:System.Windows.Forms.BindingSource> pracujete s musí být přidruženy k metodě jeho zpracování událostí. Tady je příklad metody pro zpracování <xref:System.Windows.Forms.BindingSource.PositionChanged> událostí:  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.NavigatingData#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#3)]  
  
### <a name="to-find-an-item-and-set-it-as-the-current-item"></a>Najít položku a nastavte jej jako s aktuální položkou.  
  
1.  Najděte záznam, který chcete nastavit jako s aktuální položkou. Můžete provést pomocí <xref:System.Windows.Forms.BindingSource.Find%2A> metodu <xref:System.Windows.Forms.BindingSource>, pokud vaše data zdroje implementuje <xref:System.ComponentModel.IBindingList>. Některé příklady datového zdroje, které implementují <xref:System.ComponentModel.IBindingList> jsou <xref:System.ComponentModel.BindingList%601> a <xref:System.Data.DataView>.  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.NavigatingData#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#2)]  
  
## <a name="see-also"></a>Viz také  
 [Zdroje dat podporované rozhraním Windows Forms](../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md)  
 [Oznámení změn v datové vazbě Windows Forms](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 [Datové vazby a Windows Forms](../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 [Windows Forms – datová vazba](../../../docs/framework/winforms/windows-forms-data-binding.md)
