---
title: Použití kontraktů v pracovním postupu
ms.date: 03/30/2017
ms.assetid: 939c64e9-e7cc-4abc-b41e-27cfce1d7e50
ms.openlocfilehash: 9f967d75a8e9d24fcfac8b7376a3d4840fba52f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184277"
---
# <a name="using-contracts-in-workflow"></a>Použití kontraktů v pracovním postupu
Při implementaci služby definujete řadu smluv, které popisují službu a data, která odesílá a přijímá. Data jsou reprezentována jako kontrakty dat a zprávy; WCF a workflow služby používají data smlouvy a definice smlouvy zprávy jako součást popisů služeb. Samotná služba zveřejňuje metadata (ve formě WSDL) k popisu operací služby. V WCF služby smlouvy a provozní smlouvy definovat služby a operace, které podporuje. Ve službě pracovního postupu jsou však tyto smlouvy součástí samotného obchodního procesu. jsou vystaveny v metadatech procesem nazývaným odvození smlouvy.  
  
## <a name="contract-inference"></a>Odvození smlouvy  
 Pokud je služba pracovního <xref:System.ServiceModel.Activities.WorkflowServiceHost>postupu hostována pomocí , je zkontrolována definice pracovního postupu a smlouva je generována na základě sady aktivit zasílání zpráv nalezených v pracovním postupu. Ke generování smlouvy se používají zejména následující činnosti a vlastnosti:  
  
 <xref:System.ServiceModel.Activities.Receive>Činnosti  
  
- <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>  
  
- <xref:System.ServiceModel.Activities.Receive.OperationName%2A>
  
- <xref:System.ServiceModel.Activities.Receive.Action%2A>

 <xref:System.ServiceModel.Activities.SendReply>Činnosti  
  
- <xref:System.ServiceModel.Activities.SendReply.Action%2A>  
  
 <xref:System.ServiceModel.Activities.TransactedReceiveScope>Činnosti  
  
 Konečný výsledek odvození smlouvy je popis služby pomocí stejné datové struktury jako WCF smlouvy o službách a operacích. Tyto informace se pak používají k vystavení WSDL pro službu pracovního postupu.  
  
## <a name="see-also"></a>Viz také

- [Služby pracovních postupů](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [Aktivity zasílání zpráv](../../../../docs/framework/wcf/feature-details/messaging-activities.md)
- [Postupy: Vytvoření služby pracovního postupu pomocí aktivit zasílání zpráv](../../../../docs/framework/wcf/feature-details/how-to-create-a-workflow-service-with-messaging-activities.md)
- [Postupy: Vytvoření služby pracovního postupu, která využívá existující kontrakt služby](../../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)
