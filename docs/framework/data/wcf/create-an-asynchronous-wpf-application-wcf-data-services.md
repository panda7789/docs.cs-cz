---
title: 'Postupy: vytvoření asynchronní aplikace Windows Presentation Framework (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, asynchronous operations
ms.assetid: 834614df-1427-4839-b0be-90f68e5afffd
ms.openlocfilehash: 9bc1cef1f76e6e55e9cd5ed318741f8913abbaab
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569268"
---
# <a name="how-to-create-an-asynchronous-windows-presentation-framework-application-wcf-data-services"></a>Postupy: vytvoření asynchronní aplikace Windows Presentation Framework (WCF Data Services)
Pomocí WCF Data Services můžete navazovat data získaná z datové služby na prvek uživatelského rozhraní aplikace WPF (Windows Presentation Framework). Další informace najdete v tématu [vázání dat na ovládací prvky](binding-data-to-controls-wcf-data-services.md). V asynchronním způsobu můžete také provádět operace s datovou službou. to umožňuje, aby aplikace při čekání na odpověď na požadavek datové služby pokračovala v reakci. K asynchronnímu přístupu k datové službě se vyžadují aplikace pro Silverlight. Další informace najdete v tématu [asynchronní operace](asynchronous-operations-wcf-data-services.md).  
  
 Toto téma ukazuje, jak přistupovat k datové službě asynchronně a navazovat výsledky na prvky aplikace WPF. Příklady v tomto tématu používají ukázkovou datovou službu Northwind a automaticky vygenerované třídy klientské datové služby. Tato služba a klientské datové třídy se vytvoří po dokončení [WCF Data Services rychlý Start](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Příklad  
 Následující kód XAML definuje okno aplikace WPF.  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingAsyncXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerordersasync.xaml#wpfdatabindingasyncxaml)]  
  
## <a name="example"></a>Příklad  
 Následující stránka s kódem na pozadí pro soubor XAML spustí asynchronní dotaz pomocí datové služby a vytvoří vazby výsledků na prvky v okně WPF.  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBindingAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerordersasync.xaml.cs#wpfdatabindingasync)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerordersasync.xaml.vb#wpfdatabindingasync)]  
  
## <a name="see-also"></a>Viz také:

- [Klientská knihovna pro WCF Data Services](wcf-data-services-client-library.md)
