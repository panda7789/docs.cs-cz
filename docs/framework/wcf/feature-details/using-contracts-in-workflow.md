---
title: Použití kontraktů v pracovním postupu
ms.date: 03/30/2017
ms.assetid: 939c64e9-e7cc-4abc-b41e-27cfce1d7e50
ms.openlocfilehash: dd35766011c412acc937eed75d523a0574f6b9cb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59150056"
---
# <a name="using-contracts-in-workflow"></a>Použití kontraktů v pracovním postupu
Při implementaci služby definovat několik smluv, které popisují služby a data, která odesílá a přijímá. Data je vyjádřena jako data kontraktů a kontraktů zpráv; služby WCF a pracovního postupu pomocí definice kontraktu dat kontrakt a zprávy jako součást služby popisy. Samotné služby zveřejňuje metadata (ve formě WSDL) aby bylo možné popisují operace služby. Ve službě WCF definování kontraktů služby a operace kontraktů služby a operace, které podporuje. Ale ve službě pracovního postupu, těchto smluv jsou součástí samotným obchodního procesu pomocí procesu nazývaného smlouvy odvození jsou vystaveny v metadatech.  
  
## <a name="contract-inference"></a>Odvození kontraktu  
 Když je hostované služby pracovních postupů, pomocí <xref:System.ServiceModel.Activities.WorkflowServiceHost>, definice pracovního postupu je zkontrolován a kontrakt je generován a základě sadu zasílání zpráv aktivity v pracovním postupu nalezen. Zejména následující aktivity a vlastnosti slouží ke generování kontraktu:  
  
 <xref:System.ServiceModel.Activities.Receive> Aktivita  
  
-   <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>  
  
-   <xref:System.ServiceModel.Activities.Receive.OperationName%2A>
  
-   <xref:System.ServiceModel.Activities.Receive.Action%2A>   
 
 <xref:System.ServiceModel.Activities.SendReply> Aktivita  
  
-   <xref:System.ServiceModel.Activities.SendReply.Action%2A>  
  
 <xref:System.ServiceModel.Activities.TransactedReceiveScope> Aktivita  
  
 Konečný výsledek odvození smlouvy je popis služby pomocí stejné datové struktury jako smlouvy WCF služby a operace. Potom tyto informace slouží k vystavení WSDL pro službu pracovního postupu.  
  
## <a name="see-also"></a>Viz také:

- [Služby pracovních postupů](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Aktivity zasílání zpráv](../../../../docs/framework/wcf/feature-details/messaging-activities.md)
- [Postupy: Vytvoření služby pracovního postupu pomocí činnosti související se zprávami](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)
- [Postupy: Vytvoření služby pracovního postupu, která využívá existující kontrakt služby](../../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)
