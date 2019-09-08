---
title: 'Postupy: Vytvoření asynchronní aplikace Windows Presentation Framework (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, asynchronous operations
ms.assetid: 834614df-1427-4839-b0be-90f68e5afffd
ms.openlocfilehash: 820cb4aa39b49d63cf1acc31e6eb5aa56fd1ba03
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790989"
---
# <a name="how-to-create-an-asynchronous-windows-presentation-framework-application-wcf-data-services"></a>Postupy: Vytvoření asynchronní aplikace Windows Presentation Framework (WCF Data Services)
Pomocí [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]nástroje můžete navazovat data získaná z datové služby na prvek uživatelského rozhraní aplikace WPF (Windows Presentation Framework). Další informace najdete v tématu [vázání dat na ovládací prvky](binding-data-to-controls-wcf-data-services.md). V asynchronním způsobu můžete také provádět operace s datovou službou. to umožňuje, aby aplikace při čekání na odpověď na požadavek datové služby pokračovala v reakci. K asynchronnímu přístupu k datové službě se vyžadují aplikace pro Silverlight. Další informace najdete v tématu [asynchronní operace](asynchronous-operations-wcf-data-services.md).  
  
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
