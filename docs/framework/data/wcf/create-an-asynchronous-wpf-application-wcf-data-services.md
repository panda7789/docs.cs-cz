---
title: 'Postupy: vytvoření aplikace asynchronní Windows Presentation Framework (služby WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, asynchronous operations
ms.assetid: 834614df-1427-4839-b0be-90f68e5afffd
ms.openlocfilehash: d6acf3cbbfce491ebf98513b116d76ef9feb6d08
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33357631"
---
# <a name="how-to-create-an-asynchronous-windows-presentation-framework-application-wcf-data-services"></a>Postupy: vytvoření aplikace asynchronní Windows Presentation Framework (služby WCF Data Services)
S [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], lze vázat data získaná z datové služby element uživatelského rozhraní aplikace Windows Presentation Framework (WPF). Další informace najdete v tématu [vazby dat k ovládacím prvkům](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md). Operace u služby data můžete také spustit v asynchronním režimu, který umožňuje aplikaci dál odpovídat při čekání na odpověď na žádost o službu data. Aplikace pro Silverlight vyžadovaných pro přístup ke službě data asynchronně. Další informace najdete v tématu [asynchronních operací](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md).  
  
 Toto téma ukazuje, jak asynchronně přístup ke službě data a k prvkům v aplikaci WPF vytvořte vazbu výsledky. Příklady v tomto tématu službu Northwind ukázková data a data klienta automaticky vygenerovanou služby třídy. Tato služba a datové třídy klienta se vytvoří při dokončení [rychlého startu služby WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Příklad  
 Následující XAML definuje okno aplikace WPF.  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingAsyncXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerordersasync.xaml#wpfdatabindingasyncxaml)]  
  
## <a name="example"></a>Příklad  
 Následující kódu stránky XAML souboru provede asynchronní dotaz pomocí dat služby a sváže výsledky prvků v okně WPF.  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBindingAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerordersasync.xaml.cs#wpfdatabindingasync)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerordersasync.xaml.vb#wpfdatabindingasync)]  
  
## <a name="see-also"></a>Viz také  
 [Klientská knihovna pro WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
