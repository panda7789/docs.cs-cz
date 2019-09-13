---
title: Seskupování zpráv zařazených do fronty v relaci
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- queues [WCF]. grouping messages
ms.assetid: 63b23b36-261f-4c37-99a2-cc323cd72a1a
ms.openlocfilehash: 995697e618ff5d56a719efc5d69b97583733d980
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70892735"
---
# <a name="grouping-queued-messages-in-a-session"></a>Seskupování zpráv zařazených do fronty v relaci
Windows Communication Foundation (WCF) poskytuje relaci, která umožňuje seskupit sadu souvisejících zpráv pro zpracování v rámci jedné přijímající aplikace. Zprávy, které jsou součástí relace, musí být součástí stejné transakce. Vzhledem k tomu, že všechny zprávy jsou součástí stejné transakce, v případě, že se jedna zpráva nedokáže zpracovat, vrátí se celá relace zpátky. Relace mají podobné chování s ohledem na fronty nedoručených zpráv a poškozené fronty. Vlastnost Time to Live (TTL) nastavená u vazby ve frontě konfigurovaná pro relace je použita pro relaci jako celek. Pokud se do vypršení hodnoty TTL odešlou jenom některé zprávy v relaci, bude celá relace umístěná ve frontě nedoručených zpráv. Podobně platí, že když se zprávy v relaci neodesílají do aplikace z fronty aplikace, celá relace se umístí do fronty poškození (Pokud je dostupná).  
  
## <a name="message-grouping-example"></a>Příklad seskupování zpráv  
 Jeden příklad, kde je seskupování zpráv užitečné, je při implementaci aplikace pro zpracování objednávek jako služby WCF. Například klient odešle objednávku do této aplikace, která obsahuje několik položek. Pro každou položku klient provede volání služby, což vede k odeslání samostatné zprávy. Je možné, aby mohl získat první položku a server B přijmout druhou položku. Pokaždé, když se přidá položka, Server zpracovává tuto položku, aby vyhledal příslušné pořadí a přidal do něj položku, která je vysoce neefektivní. Pořád se to netýká pouze jednoho serveru, který zpracovává všechny požadavky, protože server musí sledovat všechny aktuálně zpracovávané objednávky a určit, do které z nich patří nová položka. Seskupení všech požadavků pro jednu objednávku značně zjednodušuje implementaci takové aplikace. Klientská aplikace pošle všechny položky v relaci jediným pořadím, takže když služba zpracuje objednávku, zpracuje celou relaci najednou. \  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-set-up-a-service-contract-to-use-sessions"></a>Nastavení kontraktu služby pro použití relací  
  
1. Definujte kontrakt služby, který vyžaduje relaci. Provedete to <xref:System.ServiceModel.ServiceContractAttribute> pomocí atributu zadáním:  
  
    ```csharp
    SessionMode=SessionMode.Required  
    ```  
  
2. Označte operace v kontraktu jako jednosměrné, protože tyto metody nevrátí žádnou hodnotu. To se provádí s <xref:System.ServiceModel.OperationContractAttribute> atributem zadáním:  
  
    ```csharp  
    [OperationContract(IsOneWay = true)]  
    ```  
  
3. Implementujte kontrakt služby a zadejte <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode>. <xref:System.ServiceModel.InstanceContextMode.PerSession?displayProperty=nameWithType> Tato služba vytvoří instanci služby pouze jednou pro každou relaci.  
  
    ```csharp  
    [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
    ```  
  
4. Každá operace služby vyžaduje transakci. Tuto <xref:System.ServiceModel.OperationBehaviorAttribute> vlastnost zadejte s atributem. Operace, která dokončí transakci, by měla <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete> být `true`také nastavena na.  
  
    ```csharp  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]   
    ```  
  
5. Nakonfigurujte koncový bod, který používá vazbu poskytovanou `NetMsmqBinding` systémem.  
  
6. Vytvořte transakční frontu pomocí <xref:System.Messaging>. Frontu můžete vytvořit také pomocí služby Řízení front zpráv (MSMQ) nebo konzoly MMC. Pokud tak učiníte, vytvořte transakční frontu.  
  
7. Vytvořte hostitele služby pro službu pomocí nástroje <xref:System.ServiceModel.ServiceHost>.  
  
8. Otevřete hostitele služby, aby služba byla dostupná.  
  
9. Zavřete hostitele služby.  
  
#### <a name="to-set-up-a-client"></a>Nastavení klienta  
  
1. Vytvořte obor transakce pro zápis do transakční fronty.  
  
2. Vytvořte klienta WCF pomocí nástroje [Svcutil. exe (Nástroj pro metadata ServiceModel)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) .  
  
3. Umístěte objednávku.  
  
4. Zavřete klienta WCF.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad poskytuje kód pro `IProcessOrder` službu a pro klienta, který používá tuto službu. Ukazuje, jak WCF používá relace ve frontě k zajištění chování seskupení.  
  
### <a name="code-for-the-service"></a>Kód pro službu  
 [!code-csharp[S_Msmq_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/service.cs#1)]
 [!code-vb[S_Msmq_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/service.vb#1)]  

### <a name="code-for-the-client"></a>Kód pro klienta  
 [!code-csharp[S_Msmq_Session#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/client.cs#3)]
 [!code-vb[S_Msmq_Session#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/client.vb#3)]  

## <a name="see-also"></a>Viz také:

- [Relace a fronty](../../../../docs/framework/wcf/samples/sessions-and-queues.md)
- [Přehled front](../../../../docs/framework/wcf/feature-details/queues-overview.md)
