---
title: "Postupy: Procházení dat v rozhraní Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7c754bba18e93f63306701381f66af04b593c473
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-navigate-data-in-windows-forms"></a><span data-ttu-id="bff6d-102">Postupy: Procházení dat v rozhraní Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bff6d-102">How to: Navigate Data in Windows Forms</span></span>
<span data-ttu-id="bff6d-103">V aplikaci Windows, je nejjednodušší způsob, jak procházet záznamy ze zdroje dat pro vazbu <xref:System.Windows.Forms.BindingSource> součásti na zdroj dat a pak vazby ovládacích prvků <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="bff6d-103">In a Windows application, the easiest way to navigate through records in a data source is to bind a <xref:System.Windows.Forms.BindingSource> component to the data source and then bind controls to the <xref:System.Windows.Forms.BindingSource>.</span></span> <span data-ttu-id="bff6d-104">Pak můžete použít metodu předdefinovanou navigaci na <xref:System.Windows.Forms.BindingSource> takové <xref:System.Windows.Forms.BindingSource.MoveNext%2A>, <xref:System.Windows.Forms.BindingSource.MoveLast%2A>, <xref:System.Windows.Forms.BindingSource.MovePrevious%2A> a <xref:System.Windows.Forms.BindingSource.MoveFirst%2A>.</span><span class="sxs-lookup"><span data-stu-id="bff6d-104">You can then use the built-in navigation method on the <xref:System.Windows.Forms.BindingSource> such a <xref:System.Windows.Forms.BindingSource.MoveNext%2A>, <xref:System.Windows.Forms.BindingSource.MoveLast%2A>, <xref:System.Windows.Forms.BindingSource.MovePrevious%2A> and <xref:System.Windows.Forms.BindingSource.MoveFirst%2A>.</span></span> <span data-ttu-id="bff6d-105">Pomocí těchto metod se upraví <xref:System.Windows.Forms.BindingSource.Position%2A> a <xref:System.Windows.Forms.BindingSource.Current%2A> vlastnosti <xref:System.Windows.Forms.BindingSource> správně.</span><span class="sxs-lookup"><span data-stu-id="bff6d-105">Using these methods will adjust the <xref:System.Windows.Forms.BindingSource.Position%2A> and <xref:System.Windows.Forms.BindingSource.Current%2A> properties of the <xref:System.Windows.Forms.BindingSource> appropriately.</span></span> <span data-ttu-id="bff6d-106">Můžete také najít položku a nastavte jej jako aktuální položky nastavením <xref:System.Windows.Forms.BindingSource.Position%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="bff6d-106">You can also find an item and set it as the current item by setting the <xref:System.Windows.Forms.BindingSource.Position%2A> property.</span></span>  
  
### <a name="to-increment-the-position-in-a-data-source"></a><span data-ttu-id="bff6d-107">Chcete-li zvýšit pozice ve zdroji dat</span><span class="sxs-lookup"><span data-stu-id="bff6d-107">To increment the position in a data source</span></span>  
  
1.  <span data-ttu-id="bff6d-108">Nastavte <xref:System.Windows.Forms.BindingSource.Position%2A> vlastnost <xref:System.Windows.Forms.BindingSource> vázané dat na pozici záznam přejít na.</span><span class="sxs-lookup"><span data-stu-id="bff6d-108">Set the <xref:System.Windows.Forms.BindingSource.Position%2A> property of the <xref:System.Windows.Forms.BindingSource> for your bound data to the record position to go to.</span></span> <span data-ttu-id="bff6d-109">Následující příklad ilustruje, pomocí <xref:System.Windows.Forms.BindingSource.MoveNext%2A> metodu <xref:System.Windows.Forms.BindingSource> k přírůstek <xref:System.Windows.Forms.BindingSource.Position%2A> vlastnost při `nextButton` po kliknutí na.</span><span class="sxs-lookup"><span data-stu-id="bff6d-109">The following example illustrates using the <xref:System.Windows.Forms.BindingSource.MoveNext%2A> method of the <xref:System.Windows.Forms.BindingSource> to increment the <xref:System.Windows.Forms.BindingSource.Position%2A> property when the `nextButton` is clicked.</span></span> <span data-ttu-id="bff6d-110"><xref:System.Windows.Forms.BindingSource> Přidružen `Customers` tabulky datové sady `Northwind`.</span><span class="sxs-lookup"><span data-stu-id="bff6d-110">The <xref:System.Windows.Forms.BindingSource> is associated with the `Customers` table of a dataset `Northwind`.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bff6d-111">Nastavení <xref:System.Windows.Forms.BindingSource.Position%2A> vlastnost na hodnotu nad rámec první nebo poslední záznam nevede k chybě, jako [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] neumožní vám umožní nastavit na hodnotu mimo rozsah seznamu pozici.</span><span class="sxs-lookup"><span data-stu-id="bff6d-111">Setting the <xref:System.Windows.Forms.BindingSource.Position%2A> property to a value beyond the first or last record does not result in an error, as the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] will not allow you to set the position to a value outside the bounds of the list.</span></span> <span data-ttu-id="bff6d-112">Pokud je důležité ve vaší aplikaci vědět, jestli jste došli po první nebo poslední záznam, zahrňte logiku k ověření, zda bude překročen počet datových element.</span><span class="sxs-lookup"><span data-stu-id="bff6d-112">If it is important in your application to know whether you have gone past the first or last record, include logic to test whether you will exceed the data element count.</span></span>  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.NavigatingData#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#4)]  
  
### <a name="to-check-whether-you-have-passed-the-end-or-beginning"></a><span data-ttu-id="bff6d-113">Zkontrolujte, zda předané koncové nebo počáteční</span><span class="sxs-lookup"><span data-stu-id="bff6d-113">To check whether you have passed the end or beginning</span></span>  
  
1.  <span data-ttu-id="bff6d-114">Vytvoření obslužné rutiny událostí <xref:System.Windows.Forms.BindingSource.PositionChanged> událostí.</span><span class="sxs-lookup"><span data-stu-id="bff6d-114">Create an event handler for the <xref:System.Windows.Forms.BindingSource.PositionChanged> event.</span></span> <span data-ttu-id="bff6d-115">V obslužné rutině můžete zkontrolovat, zda hodnota navrhované pozice překročila počet element skutečná data.</span><span class="sxs-lookup"><span data-stu-id="bff6d-115">In the handler, you can test whether the proposed position value has exceeded the actual data element count.</span></span>  
  
     <span data-ttu-id="bff6d-116">Následující příklad ilustruje, jak můžete zkontrolovat, zda jste dosáhli poslední datový prvek.</span><span class="sxs-lookup"><span data-stu-id="bff6d-116">The following example illustrates how you can test whether you have reached the last data element.</span></span> <span data-ttu-id="bff6d-117">V příkladu, pokud jste v posledním prvkem **Další** tlačítko ve formuláři je zakázané.</span><span class="sxs-lookup"><span data-stu-id="bff6d-117">In the example, if you are at the last element, the **Next** button on the form is disabled.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bff6d-118">Mějte na paměti, že můžete změnit v seznamu jsou navigace v kódu, měli byste znovu povolit **Další** tlačítko tak, aby uživatelé mohou procházet celou délku nového seznamu.</span><span class="sxs-lookup"><span data-stu-id="bff6d-118">Be aware that, should you change the list you are navigating in code, you should re-enable the **Next** button, so that users may browse the entire length of the new list.</span></span> <span data-ttu-id="bff6d-119">Kromě toho mějte na paměti, výše <xref:System.Windows.Forms.BindingSource.PositionChanged> událostí pro konkrétní <xref:System.Windows.Forms.BindingSource> pracujete s musí být přidruženy k metodě jeho zpracování událostí.</span><span class="sxs-lookup"><span data-stu-id="bff6d-119">Additionally, be aware that the above <xref:System.Windows.Forms.BindingSource.PositionChanged> event for the specific <xref:System.Windows.Forms.BindingSource> you are working with needs to be associated with its event-handling method.</span></span> <span data-ttu-id="bff6d-120">Tady je příklad metody pro zpracování <xref:System.Windows.Forms.BindingSource.PositionChanged> událostí:</span><span class="sxs-lookup"><span data-stu-id="bff6d-120">The following is an example of a method for handling the <xref:System.Windows.Forms.BindingSource.PositionChanged> event:</span></span>  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.NavigatingData#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#3)]  
  
### <a name="to-find-an-item-and-set-it-as-the-current-item"></a><span data-ttu-id="bff6d-121">Najít položku a nastavte jej jako s aktuální položkou.</span><span class="sxs-lookup"><span data-stu-id="bff6d-121">To find an item and set it as the current item</span></span>  
  
1.  <span data-ttu-id="bff6d-122">Najděte záznam, který chcete nastavit jako s aktuální položkou.</span><span class="sxs-lookup"><span data-stu-id="bff6d-122">Find the record you wish to set as the current item.</span></span> <span data-ttu-id="bff6d-123">Můžete provést pomocí <xref:System.Windows.Forms.BindingSource.Find%2A> metodu <xref:System.Windows.Forms.BindingSource>, pokud vaše data zdroje implementuje <xref:System.ComponentModel.IBindingList>.</span><span class="sxs-lookup"><span data-stu-id="bff6d-123">You can do this using the <xref:System.Windows.Forms.BindingSource.Find%2A> method of the <xref:System.Windows.Forms.BindingSource>, if your data source implements <xref:System.ComponentModel.IBindingList>.</span></span> <span data-ttu-id="bff6d-124">Některé příklady datového zdroje, které implementují <xref:System.ComponentModel.IBindingList> jsou <xref:System.ComponentModel.BindingList%601> a <xref:System.Data.DataView>.</span><span class="sxs-lookup"><span data-stu-id="bff6d-124">Some examples of data sources that implement <xref:System.ComponentModel.IBindingList> are <xref:System.ComponentModel.BindingList%601> and <xref:System.Data.DataView>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.NavigatingData#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.NavigatingData#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.NavigatingData/VB/Form1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="bff6d-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="bff6d-125">See Also</span></span>  
 [<span data-ttu-id="bff6d-126">Zdroje dat podporované rozhraním Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bff6d-126">Data Sources Supported by Windows Forms</span></span>](../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md)  
 [<span data-ttu-id="bff6d-127">Oznámení změn v systému Windows Forms datové vazby</span><span class="sxs-lookup"><span data-stu-id="bff6d-127">Change Notification in Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/change-notification-in-windows-forms-data-binding.md)  
 [<span data-ttu-id="bff6d-128">Datová vazba a systém Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bff6d-128">Data Binding and Windows Forms</span></span>](../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 [<span data-ttu-id="bff6d-129">Windows Forms – datová vazba</span><span class="sxs-lookup"><span data-stu-id="bff6d-129">Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/windows-forms-data-binding.md)
