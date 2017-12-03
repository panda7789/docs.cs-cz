---
title: "Postupy: vytvoření aplikace asynchronní Windows Presentation Framework (služby WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: WCF Data Services, asynchronous operations
ms.assetid: 834614df-1427-4839-b0be-90f68e5afffd
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 52e952abc6f1b47d9caf7a5583bb591c51a70dde
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
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
