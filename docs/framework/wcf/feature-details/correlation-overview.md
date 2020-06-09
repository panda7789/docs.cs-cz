---
title: Korelace – přehled
ms.date: 03/30/2017
ms.assetid: edcc0315-5d26-44d6-a36d-ea554c418e9f
ms.openlocfilehash: 65f87195fde0c3dbda610804260f0ebfbf599073
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84586972"
---
# <a name="correlation-overview"></a>Korelace – přehled
Korelace je mechanismus pro vzájemné navýšení zpráv služby pracovního postupu nebo stav instance aplikace, jako je například odpověď na počáteční požadavek nebo konkrétní ID objednávky do trvalého stavu pracovního postupu zpracování objednávek. V tomto tématu najdete přehled korelace. Další témata v této části poskytují další informace o jednotlivých typech korelace.  
  
## <a name="types-of-correlation"></a>Typy korelace  
 Korelace může být založená na protokolu nebo na základě obsahu. Korelace založené na protokolech používají data poskytovaná infrastrukturou doručování zpráv k poskytnutí mapování mezi zprávami. Zprávy, které jsou korelační pomocí korelace založené na protokolech, jsou vzájemně propojené pomocí objektu v paměti, jako je například <xref:System.ServiceModel.Channels.RequestContext> nebo pomocí tokenu poskytnutého transportním protokolem. Korelace na základě obsahu vzájemně procházejí zprávy pomocí dat zadaných aplikací. Zprávy, které jsou korelační pomocí korelace na základě obsahu, vzájemně souvisí s některými daty definovanými aplikací ve zprávě, jako je číslo zákazníka.  
  
 Aktivity, které se účastní korelace, využívají <xref:System.ServiceModel.Activities.CorrelationHandle> k propojení aktivit zasílání zpráv. Například, <xref:System.ServiceModel.Activities.Send> který se používá k volání služby a následného <xref:System.ServiceModel.Activities.Receive> , který se používá k získání zpětného volání ze služby, můžete sdílet stejné <xref:System.ServiceModel.Activities.CorrelationHandle> . Tento základní vzor se používá, je-li korelace založená na obsahu nebo protokolu. Korelační popisovač lze explicitně nastavit u každé aktivity nebo aktivity mohou být obsaženy v <xref:System.ServiceModel.Activities.CorrelationScope> aktivitě. Aktivity obsažené v rámci <xref:System.ServiceModel.Activities.CorrelationScope> mají své korelační popisovače spravované pomocí <xref:System.ServiceModel.Activities.CorrelationScope> a nevyžadují, aby byly <xref:System.ServiceModel.Activities.CorrelationHandle> nastaveny explicitně. <xref:System.ServiceModel.Activities.CorrelationScope>Obor poskytuje <xref:System.ServiceModel.Activities.CorrelationHandle> správu pro korelaci požadavek-odpověď a jeden další typ korelace. Služba pracovního postupu hostovaná pomocí nástroje <xref:System.ServiceModel.Activities.WorkflowServiceHost> mají stejnou výchozí správu korelace jako <xref:System.ServiceModel.Activities.CorrelationScope> aktivita. Tato výchozí Správa korelace obecně znamená, že v mnoha scénářích nevyžadují aktivity zasílání zpráv ve <xref:System.ServiceModel.Activities.CorrelationScope> službě nebo v rámci služby pracovního postupu, <xref:System.ServiceModel.Activities.CorrelationHandle> Pokud je více aktivit zasílání zpráv paralelní nebo překrývající se, například dvě <xref:System.ServiceModel.Activities.Receive> aktivity paralelně, nebo dvě <xref:System.ServiceModel.Activities.Send> aktivity, které následují dvě <xref:System.ServiceModel.Activities.Receive> aktivity. Další informace o výchozí korelaci najdete v tématech v této části, které se týkají každého konkrétního typu korelace. Další informace o aktivitách zasílání zpráv najdete v tématech aktivity zasílání [zpráv](messaging-activities.md) a [Postupy: vytvoření služby pracovního postupu pomocí aktivit zasílání zpráv](how-to-create-a-workflow-service-with-messaging-activities.md).  
  
## <a name="protocol-based-correlation"></a>Korelace na základě protokolů

Korelace založená na protokolech používá přenosový mechanismus k vzájemnému propojení zpráv a příslušné instance. Mezi korelace protokolů poskytovaných systémem patří korelace požadavku a odpovědi a korelace na základě kontextu. Korelace požadavek-odpověď se používá ke korelaci jedné dvojice aktivit zasílání zpráv za účelem vytvoření obousměrné operace, například <xref:System.ServiceModel.Activities.Send> párování s <xref:System.ServiceModel.Activities.ReceiveReply> nebo <xref:System.ServiceModel.Activities.Receive> spárovaného s <xref:System.ServiceModel.Activities.SendReply> . Sada Visual Studio Návrhář postupu provádění také poskytuje sadu šablon aktivity k rychlé implementaci tohoto modelu. Korelace založená na kontextu je založena na mechanismu výměny kontextu popsaném ve [specifikaci protokolu výměny kontextu .NET](https://docs.microsoft.com/openspecs/windows_protocols/mc-netcex/a7f26280-491f-465b-9914-c5eb5322dbb4). Chcete-li použít kontextovou korelaci, použijte kontextovou vazbu, jako <xref:System.ServiceModel.BasicHttpContextBinding> je například, <xref:System.ServiceModel.WSHttpContextBinding> nebo <xref:System.ServiceModel.NetTcpContextBinding> musí být použita na koncovém bodu.  
  
Další informace o korelaci protokolu najdete v tématu [odolný Duplex](durable-duplex-correlation.md) a [Request-Reply](request-reply-correlation.md). Další informace o používání šablon aktivity aplikace Visual Studio Návrhář postupu provádění najdete v tématu [aktivity zasílání zpráv](messaging-activities.md). Vzorový kód naleznete v ukázce [NetContextExchangeCorrelation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee662963%28v%3dvs.100%29) .  
  
## <a name="content-based-correlation"></a>Korelace na základě obsahu

Korelace na základě obsahu používá některé informace ve zprávě k jejímu přidružení ke konkrétní instanci. Na rozdíl od korelace na základě protokolu vyžaduje korelace na základě obsahu explicitní stav, kde se tato data dají najít v každé související zprávě. Aktivity, které používají korelaci na základě obsahu, určují tato data zprávy pomocí <xref:System.ServiceModel.MessageQuerySet> . Korelace na základě obsahu je užitečná při komunikaci se službami, které nepoužívají jednu z kontextových vazeb, jako je <xref:System.ServiceModel.BasicHttpContextBinding> .
  
## <a name="see-also"></a>Viz také

- [NetContextExchangeCorrelation](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee662963%28v%3dvs.100%29)
