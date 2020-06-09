---
title: 'Postupy: Výměna zpráv zařazených do fronty pomocí koncových bodů WCF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 938e7825-f63a-4c3d-b603-63772fabfdb3
ms.openlocfilehash: 7da7ba1b680bae2b29eeff8fe669e097ea8eda32
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595372"
---
# <a name="how-to-exchange-queued-messages-with-wcf-endpoints"></a>Postupy: Výměna zpráv zařazených do fronty pomocí koncových bodů WCF
Fronty zajišťují, že spolehlivé zasílání zpráv může nastat mezi klientem a službou Windows Communication Foundation (WCF), a to i v případě, že služba není k dispozici v době komunikace. Následující postupy ukazují, jak zajistit trvalou komunikaci mezi klientem a službou pomocí standardní vazby ve frontě při implementaci služby WCF.  
  
 V této části se dozvíte, jak použít <xref:System.ServiceModel.NetMsmqBinding> pro komunikaci ve frontě mezi klientem WCF a službou WCF.  
  
### <a name="to-use-queuing-in-a-wcf-service"></a>Používání služby Řízení front zpráv ve službě WCF  
  
1. Definujte kontrakt služby pomocí rozhraní označeného <xref:System.ServiceModel.ServiceContractAttribute> . Označte operace v rozhraní, které jsou součástí kontraktu služby, <xref:System.ServiceModel.OperationContractAttribute> a zadejte je jako jednosměrné, protože se nevrátí žádná odpověď na metodu. Následující kód poskytuje příklad kontraktu služby a jeho definice operace.  
  
     [!code-csharp[S_Msmq_Transacted#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#1)]
     [!code-vb[S_Msmq_Transacted#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#1)]  
  
2. Pokud kontrakt služby předává uživatelsky definované typy, je nutné pro tyto typy definovat kontrakty dat. Následující kód ukazuje dvě kontrakty dat, `PurchaseOrder` a `PurchaseOrderLineItem` . Tyto dva typy definují data, která jsou odeslána do služby. (Všimněte si, že třídy, které definují tento datový kontrakt, definují také počet metod. Tyto metody nejsou považovány za součást kontraktu dat. Pouze členové, kteří jsou deklarováni s <xref:System.Runtime.Serialization.DataMemberAttribute> atributem, jsou součástí kontraktu dat.)  
  
     [!code-csharp[S_Msmq_Transacted#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#2)]
     [!code-vb[S_Msmq_Transacted#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#2)]  
  
3. Implementujte metody kontraktu služby definovaného v rozhraní třídy.  
  
     [!code-csharp[S_Msmq_Transacted#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#3)]
     [!code-vb[S_Msmq_Transacted#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#3)]  
  
     Všimněte si, že se <xref:System.ServiceModel.OperationBehaviorAttribute> nachází na `SubmitPurchaseOrder` metodě. To určuje, že tuto operaci je nutné volat v rámci transakce a že transakce se automaticky dokončí po dokončení metody.  
  
4. Vytvořte transakční frontu pomocí <xref:System.Messaging> . Místo toho můžete vytvořit frontu pomocí konzoly Microsoft Management Console (MSMQ) společnosti Microsoft (MMC). Pokud ano, ujistěte se, že jste vytvořili transakční frontu.  
  
     [!code-csharp[S_Msmq_Transacted#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#4)]
     [!code-vb[S_Msmq_Transacted#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#4)]  
  
5. Definujte <xref:System.ServiceModel.Description.ServiceEndpoint> v konfiguraci, která určuje adresu služby a používá standardní <xref:System.ServiceModel.NetMsmqBinding> vazbu. Další informace o použití konfigurace WCF najdete v tématu [Konfigurace služeb WCF](../configuring-services.md).  

6. Vytvořte hostitele pro `OrderProcessing` službu pomocí nástroje <xref:System.ServiceModel.ServiceHost> , který načte zprávy z fronty a zpracuje je. Otevřete hostitele služby, aby služba byla dostupná. Zobrazí zprávu s oznámením, že uživatel stiskne libovolnou klávesu a ukončí službu. Zavolejte `ReadLine` na čekání na stisknutí klávesy a potom službu zavřete.  
  
     [!code-csharp[S_Msmq_Transacted#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#6)]
     [!code-vb[S_Msmq_Transacted#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#6)]  
  
### <a name="to-create-a-client-for-the-queued-service"></a>Vytvoření klienta pro službu ve frontě  
  
1. Následující příklad ukazuje, jak spustit hostitelskou aplikaci a použít nástroj Svcutil. exe k vytvoření klienta WCF.  
  
    ```console
    svcutil http://localhost:8000/ServiceModelSamples/service  
    ```  
  
2. Definujte <xref:System.ServiceModel.Description.ServiceEndpoint> v konfiguraci, která určuje adresu a používá standardní <xref:System.ServiceModel.NetMsmqBinding> vazbu, jak je znázorněno v následujícím příkladu.  

3. Vytvořte obor transakce pro zápis do transakční fronty, zavolejte `SubmitPurchaseOrder` operaci a zavřete klienta služby WCF, jak je znázorněno v následujícím příkladu.  
  
     [!code-csharp[S_Msmq_Transacted#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#8)]
     [!code-vb[S_Msmq_Transacted#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#8)]  
  
## <a name="example"></a>Příklad  
 Následující příklady znázorňují kód služby, hostující aplikaci, soubor App. config a klientský kód, který je součástí tohoto příkladu.  
  
 [!code-csharp[S_Msmq_Transacted#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#9)]
 [!code-vb[S_Msmq_Transacted#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#9)]  
  
 [!code-csharp[S_Msmq_Transacted#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#10)]
 [!code-vb[S_Msmq_Transacted#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#10)]  

 [!code-csharp[S_Msmq_Transacted#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#12)]
 [!code-vb[S_Msmq_Transacted#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#12)]  

## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.NetMsmqBinding>
- [Zpracované vazby služby MSMQ](../samples/transacted-msmq-binding.md)
- [Fronty ve WCF](queuing-in-wcf.md)
- [Postupy: Výměna zpráv s koncovými body WCF a aplikací pro řazení zpráv do front](how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)
- [Z WCF do Řízení front zpráv](../samples/wcf-to-message-queuing.md)
- [Instalace služby Řízení front zpráv (MSMQ)](../samples/installing-message-queuing-msmq.md)
- [Řízení front zpráv do WCF](../samples/message-queuing-to-wcf.md)
- [Zabezpečení zprávy pomocí služby Řízení front zpráv](../samples/message-security-over-message-queuing.md)
