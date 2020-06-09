---
title: Použití kontraktů v pracovním postupu
ms.date: 03/30/2017
ms.assetid: 939c64e9-e7cc-4abc-b41e-27cfce1d7e50
ms.openlocfilehash: def100f9483ea9ac8bf1aa3285d76edccffb030a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595008"
---
# <a name="using-contracts-in-workflow"></a>Použití kontraktů v pracovním postupu
Při implementaci služby definujete řadu kontraktů, které popisují službu a data, která odesílá a přijímá. Data jsou reprezentována jako kontrakty dat a kontrakty zpráv. WCF i služba pracovních postupů používají jako součást popisů služeb kontrakt dat a definice kontraktů zpráv. Služba sama zveřejňuje metadata (ve formě WSDL), aby bylo možné popsání operací služby. V rámci WCF, kontrakty služeb a kontrakty operací definují službu a operace, které podporuje. Ve službě pracovního postupu ale tyto smlouvy jsou součástí samotného obchodního procesu; jsou zpřístupněny v metadatech pomocí procesu nazývaného odvození kontraktu.  
  
## <a name="contract-inference"></a>Odvození kontraktu  
 Je-li služba pracovního postupu hostována pomocí nástroje <xref:System.ServiceModel.Activities.WorkflowServiceHost> , je prověřena definice pracovního postupu a na základě sady aktivit zasílání zpráv, které jsou v pracovním postupu nalezeny, je vygenerován kontrakt. Konkrétně se k vygenerování kontraktu použijí tyto aktivity a vlastnosti:  
  
 <xref:System.ServiceModel.Activities.Receive>Akce  
  
- <xref:System.ServiceModel.Activities.Receive.ServiceContractName%2A>  
  
- <xref:System.ServiceModel.Activities.Receive.OperationName%2A>
  
- <xref:System.ServiceModel.Activities.Receive.Action%2A>

 <xref:System.ServiceModel.Activities.SendReply>Akce  
  
- <xref:System.ServiceModel.Activities.SendReply.Action%2A>  
  
 <xref:System.ServiceModel.Activities.TransactedReceiveScope>Akce  
  
 Konečný výsledek odvození smlouvy je popis služby, která používá stejné datové struktury jako služby WCF a kontrakty operací. Tyto informace se pak použijí k vystavení WSDL pro službu pracovního postupu.  
  
## <a name="see-also"></a>Viz také

- [Služby pracovních postupů](workflow-services.md)
- [Aktivity zasílání zpráv](messaging-activities.md)
- [Postupy: Vytvoření služby pracovního postupu pomocí aktivit zasílání zpráv](how-to-create-a-workflow-service-with-messaging-activities.md)
- [Postupy: Vytvoření služby pracovního postupu, která využívá existující kontrakt služby](../../windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md)
