---
title: 'Postupy: Výměna zpráv zařazených do fronty pomocí koncových bodů WCF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 938e7825-f63a-4c3d-b603-63772fabfdb3
ms.openlocfilehash: ea052a2dd843205a8108ea48f17ea84577817215
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2019
ms.locfileid: "58411028"
---
# <a name="how-to-exchange-queued-messages-with-wcf-endpoints"></a>Postupy: Výměna zpráv zařazených do fronty pomocí koncových bodů WCF
Fronty Ujistěte se, že může dojít spolehlivé zasílání zpráv, mezi klientem a službou Windows Communication Foundation (WCF), i v případě, že služba není k dispozici v době komunikace. Následující postupy ukazují, jak zajistit ve frontě trvalý komunikace mezi klientem a službou pomocí standardní připojení, při implementaci služby WCF.  
  
 Tato část vysvětluje, jak používat <xref:System.ServiceModel.NetMsmqBinding> pro komunikaci mezi klienta WCF a služby WCF ve frontě.  
  
### <a name="to-use-queuing-in-a-wcf-service"></a>Použití služby Řízení front ve službě WCF  
  
1.  Definování kontraktu služby pomocí rozhraní označené <xref:System.ServiceModel.ServiceContractAttribute>. Označit operace v rozhraní, které jsou součástí kontraktu služby se <xref:System.ServiceModel.OperationContractAttribute> a zadejte jako jednosměrná, protože není vrácena žádná odpověď na metodu. Následující kód obsahuje kontrakt služby příklad a jeho definice operace.  
  
     [!code-csharp[S_Msmq_Transacted#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#1)]
     [!code-vb[S_Msmq_Transacted#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#1)]  
  
2.  Když je kontrakt služby úspěšné uživatelem definovaných typů, je nutné definovat kontraktů dat pro tyto typy. Následující kód ukazuje dva kontrakty dat `PurchaseOrder` a `PurchaseOrderLineItem`. Tyto dva typy definují data, která se odesílají do služby. (Všimněte si, že třídy, které definují tento kontrakt dat také definovat několik metod. Tyto metody nejsou považované za součást kontraktu dat. Pouze ty členy, které jsou deklarovány pomocí <xref:System.Runtime.Serialization.DataMemberAttribute> atribut jsou součástí kontraktu dat.)  
  
     [!code-csharp[S_Msmq_Transacted#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#2)]
     [!code-vb[S_Msmq_Transacted#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#2)]  
  
3.  Implementace metod definovaných v rozhraní ve třídě kontrakt služby.  
  
     [!code-csharp[S_Msmq_Transacted#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#3)]
     [!code-vb[S_Msmq_Transacted#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#3)]  
  
     Všimněte si, že <xref:System.ServiceModel.OperationBehaviorAttribute> umístit `SubmitPurchaseOrder` metody. Toto nastavení určuje, že tuto operaci musí být volána v rámci transakce a transakce automaticky dokončí při dokončení metody.  
  
4.  Vytvoření transakční fronty pomocí <xref:System.Messaging>. Můžete vytvořit frontu, místo toho použít Microsoft Message Queuing (MSMQ) Microsoft Management Console (MMC). Pokud ano, ujistěte se, že vytvoříte transakční frontu.  
  
     [!code-csharp[S_Msmq_Transacted#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#4)]
     [!code-vb[S_Msmq_Transacted#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#4)]  
  
5.  Definování <xref:System.ServiceModel.Description.ServiceEndpoint> v konfiguraci, která určuje adresu služby a využívá standardní <xref:System.ServiceModel.NetMsmqBinding> vazby. Další informace o použití konfigurace WCF najdete v tématu [konfigurace WCF services](../configuring-services.md).  
  
  
  
6.  Vytvoření hostitele pro `OrderProcessing` služby pomocí <xref:System.ServiceModel.ServiceHost> , která čte zprávy z fronty a zpracovává je. Otevření hostitele služby, aby tato služba k dispozici. Zobrazte zprávu, která uživateli říká, aby stisknutím libovolné klávesy ukončete službu. Volání `ReadLine` čekání na klávesu se aktivovala a potom zavřete okno služby.  
  
     [!code-csharp[S_Msmq_Transacted#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#6)]
     [!code-vb[S_Msmq_Transacted#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#6)]  
  
### <a name="to-create-a-client-for-the-queued-service"></a>K vytvoření klienta pro službu ve frontě  
  
1.  Následující příklad ukazuje způsob použití nástroje Svcutil.exe k vytvoření klienta WCF a spouštění hostitelské aplikace.  
  
    ```  
    svcutil http://localhost:8000/ServiceModelSamples/service  
    ```  
  
2.  Definování <xref:System.ServiceModel.Description.ServiceEndpoint> v konfiguraci, která určuje adresu a používá standardní <xref:System.ServiceModel.NetMsmqBinding> vazbu, jak je znázorněno v následujícím příkladu.  
  
  
  
3.  Vytvoření oboru transakce k zápisu transakční fronty, volání `SubmitPurchaseOrder` operace a zavřít klienta WCF, jak je znázorněno v následujícím příkladu.  
  
     [!code-csharp[S_Msmq_Transacted#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#8)]
     [!code-vb[S_Msmq_Transacted#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#8)]  
  
## <a name="example"></a>Příklad  
 Následující příklady ukazují kód služby, hostitelské aplikace, soubor App.config a kód klienta, které jsou zahrnuté v tomto příkladu.  
  
 [!code-csharp[S_Msmq_Transacted#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#9)]
 [!code-vb[S_Msmq_Transacted#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#9)]  
  
 [!code-csharp[S_Msmq_Transacted#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#10)]
 [!code-vb[S_Msmq_Transacted#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#10)]  
  
  
  
 [!code-csharp[S_Msmq_Transacted#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#12)]
 [!code-vb[S_Msmq_Transacted#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#12)]  
  
  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.NetMsmqBinding>
- [Zpracované vazby služby MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)
- [Zařazování do front ve WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
- [Postupy: Výměna zpráv pomocí koncových bodů WCF a aplikací služby Řízení front zpráv](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)
- [Z Windows Communication Foundation do služby Řízení front zpráv](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)
- [Instalace služby Řízení front zpráv (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)
- [Ze služby Řízení front zpráv do Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)
- [Zabezpečení zprávy pomocí služby Řízení front zpráv](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
