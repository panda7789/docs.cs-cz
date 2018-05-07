---
title: 'Postupy: Výměna zpráv zařazených do fronty pomocí koncových bodů WCF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 938e7825-f63a-4c3d-b603-63772fabfdb3
ms.openlocfilehash: ab6ca46fad8ee1ededef5cc14a9654b79b2e6a8e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-exchange-queued-messages-with-wcf-endpoints"></a>Postupy: Výměna zpráv zařazených do fronty pomocí koncových bodů WCF
Fronty zajistit spolehlivé zasílání zpráv můžete mezi klientem a služby Windows Communication Foundation (WCF), i když služba není k dispozici v době komunikace. Následující postupy ukazují, jak zajistit trvanlivý komunikace mezi klientem a služby pomocí standardní zařazených do fronty závazný při implementaci služby WCF.  
  
 Tato část vysvětluje, jak používat <xref:System.ServiceModel.NetMsmqBinding> pro komunikaci mezi klienta WCF a služby WCF ve frontě.  
  
### <a name="to-use-queuing-in-a-wcf-service"></a>Použití služby Řízení front služby WCF  
  
1.  Definování kontraktu služby pomocí rozhraní označené jako <xref:System.ServiceModel.ServiceContractAttribute>. Označit operace v rozhraní, které jsou součástí na kontrakt služby s <xref:System.ServiceModel.OperationContractAttribute> a zadejte je jako jednosměrný, protože je vrácena žádná odezva na metodu. Následující kód obsahuje kontrakt služby příklad a jeho definice operace.  
  
     [!code-csharp[S_Msmq_Transacted#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#1)]
     [!code-vb[S_Msmq_Transacted#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#1)]  
  
2.  Když je kontrakt služby úspěšné uživatelem definované typy, je nutné zadat kontrakty dat pro tyto typy. Následující kód ukazuje dva datové kontrakty, `PurchaseOrder` a `PurchaseOrderLineItem`. Tyto dva typy zadat data, která je odeslána do služby. (Všimněte si, že třídy, které definují tento kontrakt dat také definovat několik metod. Tyto metody nejsou považovány za součást kontrakt dat. Pouze členové, které jsou deklarovány s `DataMember` atribut jsou součástí kontrakt dat.)  
  
     [!code-csharp[S_Msmq_Transacted#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#2)]
     [!code-vb[S_Msmq_Transacted#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#2)]  
  
3.  Implementace metody kontraktu služby, které jsou definované v rozhraní v třídě.  
  
     [!code-csharp[S_Msmq_Transacted#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#3)]
     [!code-vb[S_Msmq_Transacted#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#3)]  
  
     Upozornění <xref:System.ServiceModel.OperationBehaviorAttribute> umístit na `SubmitPurchaseOrder` metoda. Toto nastavení určuje, že tato operace je nutné volat v transakci a transakce automaticky dokončí při dokončení metody.  
  
4.  Vytvoření transakční fronty pomocí <xref:System.Messaging>. Můžete vytvořit frontu, místo toho použít Microsoft služby Řízení front zpráv (MSMQ) Microsoft Management Console (MMC). Pokud ano, ujistěte se, že vytvoříte transakční fronty.  
  
     [!code-csharp[S_Msmq_Transacted#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#4)]
     [!code-vb[S_Msmq_Transacted#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#4)]  
  
5.  Definování <xref:System.ServiceModel.Description.ServiceEndpoint> v konfiguraci, kterou určuje adresu služby a používá standardní <xref:System.ServiceModel.NetMsmqBinding> vazby. Další informace o používání konfigurace WCF najdete v tématu [konfigurace Windows Communication Foundation aplikací](http://msdn.microsoft.com/library/13cb368e-88d4-4c61-8eed-2af0361c6d7a).  
  
  
  
6.  Vytvořte pro hostitele, který `OrderProcessing` služby pomocí <xref:System.ServiceModel.ServiceHost> která čte zprávy z fronty a zpracovává je. Otevření hostitele služby chcete zpřístupnit službu. Zobrazí zprávu, která uživateli říká, aby stisknutím libovolné klávesy ukončit službu. Volání `ReadLine` čekat pro klíč stisknout a pak zavřete službu.  
  
     [!code-csharp[S_Msmq_Transacted#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#6)]
     [!code-vb[S_Msmq_Transacted#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#6)]  
  
### <a name="to-create-a-client-for-the-queued-service"></a>Vytvoření klienta pro službu ve frontě  
  
1.  Následující příklad ukazuje, jak spouštět hostitelskou aplikaci a používat nástroje Svcutil.exe pro vytvoření klienta WCF.  
  
    ```  
    svcutil http://localhost:8000/ServiceModelSamples/service  
    ```  
  
2.  Definování <xref:System.ServiceModel.Description.ServiceEndpoint> v konfiguraci, kterou určuje adresu a používá standardní <xref:System.ServiceModel.NetMsmqBinding> vazby, jak je znázorněno v následujícím příkladu.  
  
  
  
3.  Vytvoření oboru transakce k zápisu do transakční fronty, volání `SubmitPurchaseOrder` operace a zavřít klienta WCF, jak je znázorněno v následujícím příkladu.  
  
     [!code-csharp[S_Msmq_Transacted#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#8)]
     [!code-vb[S_Msmq_Transacted#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#8)]  
  
## <a name="example"></a>Příklad  
 Následující příklady ukazují kódu služby, hostování aplikace, soubor App.config a kód klienta, které jsou zahrnuté v tomto příkladu.  
  
 [!code-csharp[S_Msmq_Transacted#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#9)]
 [!code-vb[S_Msmq_Transacted#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#9)]  
  
 [!code-csharp[S_Msmq_Transacted#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#10)]
 [!code-vb[S_Msmq_Transacted#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#10)]  
  
  
  
 [!code-csharp[S_Msmq_Transacted#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#12)]
 [!code-vb[S_Msmq_Transacted#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#12)]  
  
  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.NetMsmqBinding>  
 [Zpracované vazby služby MSMQ](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)  
 [Zařazování do front ve WCF](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [Postupy: Výměna zpráv s koncovými body WCF a aplikací pro řazení zpráv do front](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 [Z Windows Communication Foundation do služby Řízení front zpráv](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)  
 [Instalace služby Řízení front zpráv (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)  
 [Ukázky vazby integrace služby Řízení front zpráv](http://msdn.microsoft.com/library/997d11cb-f2c5-4ba0-9209-92843d4d0e1a)  
 [Ze služby Řízení front zpráv do Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)  
 [Zabezpečení zprávy pomocí služby Řízení front zpráv](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
