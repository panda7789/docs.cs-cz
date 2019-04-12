---
title: 'Postupy: Provádění dotazů v asynchronní datové služby (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, asynchronous operations
- asynchronous operations [WCF Data Services]
ms.assetid: 902a2dc1-d0e9-4b00-90a8-becc4cb1f6a7
ms.openlocfilehash: f89a5004afeffe5aa9a28cb2d43374aede8a935e
ms.sourcegitcommit: 680a741667cf6859de71586a0caf6be14f4f7793
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/12/2019
ms.locfileid: "59518159"
---
# <a name="how-to-execute-asynchronous-data-service-queries-wcf-data-services"></a>Postupy: Provádění dotazů v asynchronní datové služby (WCF Data Services)
S použitím [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klientské knihovny, můžete asynchronně provádět operace klient server, jako je zpracování dotazů a ukládají se změny. Další informace najdete v tématu [asynchronních operací](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md).  
  
> [!NOTE]
>  V aplikaci, ve kterém musí být zpětné volání vyvolat na konkrétním vlákně, musí explicitně zařazování provádění <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> metody. Další informace najdete v tématu [asynchronních operací](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md).  
  
 V příkladu v tomto tématu se používá Northwind ukázková data service a automaticky vygenerovaných tříd klientské datové služby. Tuto službu a třídy dat klientů jsou vytvořeny po dokončení [rychlý start služeb WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak k provedení asynchronního dotazu pomocí volání <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> metoda dotaz spustíte. Vložený delegáta volání <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> metodu pro zobrazení výsledků dotazu.  
  
 [!code-csharp[Astoria Northwind Client#ExecuteQueryAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#executequeryasync)]
 [!code-vb[Astoria Northwind Client#ExecuteQueryAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#executequeryasync)]  
  
## <a name="see-also"></a>Viz také:

- [Klientská knihovna pro WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
