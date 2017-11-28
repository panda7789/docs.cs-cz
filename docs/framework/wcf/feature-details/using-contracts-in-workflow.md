---
title: "Použití kontraktů v pracovním postupu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 939c64e9-e7cc-4abc-b41e-27cfce1d7e50
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1c84483b2ca18d63f20e64a62bb757e244db9b24
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="using-contracts-in-workflow"></a>Použití kontraktů v pracovním postupu
Při implementaci služby, definujete číslo smlouvy, které popisují služby a data, která se odesílá a přijímá. Data je reprezentována jako kontrakty dat a kontrakty zpráv; obě [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] a služby, pracovní postup definice kontraktu dat kontrakt a zprávy v rámci popis služby. Službu samotnou zveřejňuje metadata (ve formě WSDL) Chcete-li popsali, jak službu. V [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], služba kontraktů a kontraktů operaci definovat služby a činnosti podporuje. Ale ve službě pracovního postupu, tyto smlouvy jsou součástí obchodní proces, sama o sobě; pomocí procesu nazývaného kontrakt odvození jsou vystaveny v metadatech.  
  
## <a name="contract-inference"></a>Odvození kontraktu  
 Když je pracovní postup služby hostované pomocí <xref:System.ServiceModel.Activities.WorkflowServiceHost>, je zkontrolován definice pracovního postupu a kontraktu se vygeneruje na základě sady zasílání zpráv aktivity nalezen v pracovním postupu. Zejména následující aktivity a vlastnosti jsou použita pro vytvoření kontraktu:  
  
 <xref:System.ServiceModel.Activities.Receive>Aktivity  
  
-   <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>  
  
-   <!--zz <xref:System.ServiceModel.Activities.Receive.OperationContractName%2A>  --> `System.ServiceModel.Activities.Receive.OperationContractName`
  
-   <xref:System.ServiceModel.Activities.Receive.Action%2A>  
  
-   <!--zz <xref:System.ServiceModel.Activities.Receive.ValueType%2A> --> `System.ServiceModel.Activities.Receive.ValueType`
  
 <xref:System.ServiceModel.Activities.SendReply>Aktivity  
  
-   <xref:System.ServiceModel.Activities.SendReply.Action%2A>  
  
-   <!--zz <xref:System.ServiceModel.Activities.SendReply.ValueType%2A>-->  `System.ServiceModel.Activities.SendReply.ValueType`
  
 <xref:System.ServiceModel.Activities.TransactedReceiveScope>Aktivity  
  
 Konečný výsledek kontrakt odvození je popis služby pomocí stejné datové struktury jako kontraktů služby a operace WCF. Tyto informace se pak používá ke zveřejnění WSDL pro služby pracovního postupu.  
  
## <a name="see-also"></a>Viz také  
 [Služby pracovních postupů](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Aktivity zasílání zpráv](../../../../docs/framework/wcf/feature-details/messaging-activities.md)  
 [Postupy: vytvoření služby pracovního postupu se aktivity zasílání zpráv](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)  
 [Postupy: vytvoření služby pracovního postupu, který využívá existující smlouvy služby](../../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)
