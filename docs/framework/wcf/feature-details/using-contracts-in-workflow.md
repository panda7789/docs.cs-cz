---
title: Použití kontraktů v pracovním postupu
ms.date: 03/30/2017
ms.assetid: 939c64e9-e7cc-4abc-b41e-27cfce1d7e50
ms.openlocfilehash: 1772c61147bb8a96f3f78b4226a1d341df3eb9d9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="using-contracts-in-workflow"></a>Použití kontraktů v pracovním postupu
Při implementaci služby, definujete číslo smlouvy, které popisují služby a data, která se odesílá a přijímá. Data je reprezentována jako kontrakty dat a kontrakty zpráv; služby WCF a pracovní postup použít jako součást popis služby definice kontraktu dat kontrakt a zprávy. Službu samotnou zveřejňuje metadata (ve formě WSDL) Chcete-li popsali, jak službu. Ve službě WCF definování kontraktů služby a operace kontraktů služby a operace, které podporuje. Ale ve službě pracovního postupu, tyto smlouvy jsou součástí obchodní proces, sama o sobě; pomocí procesu nazývaného kontrakt odvození jsou vystaveny v metadatech.  
  
## <a name="contract-inference"></a>Odvození kontraktu  
 Když je pracovní postup služby hostované pomocí <xref:System.ServiceModel.Activities.WorkflowServiceHost>, je zkontrolován definice pracovního postupu a kontraktu se vygeneruje na základě sady zasílání zpráv aktivity nalezen v pracovním postupu. Zejména následující aktivity a vlastnosti jsou použita pro vytvoření kontraktu:  
  
 <xref:System.ServiceModel.Activities.Receive> Aktivity  
  
-   <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>  
  
-   <xref:System.ServiceModel.Activities.Receive.OperationName%2A>
  
-   <xref:System.ServiceModel.Activities.Receive.Action%2A>   
 
 <xref:System.ServiceModel.Activities.SendReply> Aktivity  
  
-   <xref:System.ServiceModel.Activities.SendReply.Action%2A>  
  
 <xref:System.ServiceModel.Activities.TransactedReceiveScope> Aktivity  
  
 Konečný výsledek kontrakt odvození je popis služby pomocí stejné datové struktury jako kontraktů služby a operace WCF. Tyto informace se pak používá ke zveřejnění WSDL pro služby pracovního postupu.  
  
## <a name="see-also"></a>Viz také  
 [Služby pracovních postupů](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Aktivity zasílání zpráv](../../../../docs/framework/wcf/feature-details/messaging-activities.md)  
 [Postupy: Vytvoření služby pracovního postupu pomocí aktivit zasílání zpráv](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)  
 [Postupy: Vytvoření služby pracovního postupu, která využívá existující kontrakt služby](../../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)
