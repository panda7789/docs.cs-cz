---
title: Seskupování zpráv zařazených do fronty v relaci
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- queues [WCF]. grouping messages
ms.assetid: 63b23b36-261f-4c37-99a2-cc323cd72a1a
ms.openlocfilehash: 37f0874ea99ee928e49a54a3e6a05ea4ef06f84e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61855917"
---
# <a name="grouping-queued-messages-in-a-session"></a>Seskupování zpráv zařazených do fronty v relaci
Windows Communication Foundation (WCF) poskytuje relaci, která umožňuje seskupit sadu souvisejících zpráv pro zpracování jedné přijímající aplikace. Zprávy, které jsou součástí relace musí být součástí stejné transakce. Protože všechny zprávy jsou součástí stejné transakce, pokud se nepodaří zpracovat celou relaci jednu zprávu se vrátí zpět. Relace mají podobné chování s ohledem na fronty nedoručených zpráv a nezpracovatelných fronty. Time to Live (TTL) nastavenou na vazbu s frontou nakonfigurované pro relace se použijí pro relaci jako celek. Pokud jen některé zprávy v relaci odeslány předtím, než hodnota TTL nevyprší, je umístěn celou relaci ve frontě nedoručených zpráv. Podobně když dojde k selhání zprávy v relaci k odeslání do aplikace z fronty aplikace, celá relace nachází ve nezpracovatelných frontu (Pokud je k dispozici).  
  
## <a name="message-grouping-example"></a>Ukázková zpráva seskupení  
 Jedním z příkladů kde seskupování zpráv je užitečné, je při implementaci zpracování objednávky aplikace jako služba WCF. Například klient odešle objednávku k této aplikaci, která obsahuje celou řadu položek. Pro každou položku klient zavolá službu, která vede samostatné odeslání zprávy. Je možné, používat A na první položku a server B pro příjem druhé položky. Pokaždé, když se přidá položka zpracování této položky na serveru má vyhledat správné místo v pořadí a do něj přidat položku, což je velmi neefektivní. Stále dochází k takové nedostatečnou s pouze jedním serverem zpracování všech požadavků, protože server musí udržovat přehled o všech objednávek, které se právě zpracovává a určit, která z nich se nová položka patří. Seskupení všech požadavků na jednu objednávku výrazně zjednodušuje provádění takové aplikace. Klientská aplikace odešle všechny položky na jednu objednávku v relaci, takže když službu objednávku zpracovává, zpracuje najednou celou relaci. \  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-set-up-a-service-contract-to-use-sessions"></a>K nastavení kontraktu služby pro použití relací  
  
1. Definování kontraktu služby vyžadující relace. K tomu <xref:System.ServiceModel.OperationContractAttribute> atribut a zadáním:  
  
    ```  
    SessionMode=SessionMode.Required  
    ```  
  
2. Označte operace v kontraktu jako jednosměrná, protože tyto metody nic nevrátí. Používá se k tomu <xref:System.ServiceModel.OperationContractAttribute> atribut a zadáním:  
  
    ```  
    [OperationContract(IsOneWay = true)]  
    ```  
  
3. Implementace kontraktu služby a zadejte `InstanceContextMode` z `PerSession`. To vytvoří instanci služby pouze jednou pro každou relaci.  
  
    ```  
    [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
    ```  
  
4. Každá služba operace vyžaduje transakci. S tuto verzi uveďte <xref:System.ServiceModel.OperationBehaviorAttribute> atribut. Tato operace provede transakce nastavte také `TransactionAutoComplete` k `true`.  
  
    ```  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]   
    ```  
  
5. Konfigurace koncového bodu, který používá poskytovaných systémem `NetMsmqBinding` vazby.  
  
6. Vytvoření transakční fronty pomocí <xref:System.Messaging>. Fronty můžete vytvořit také pomocí služby Řízení front zpráv (MSMQ) nebo konzoly MMC. Pokud tak učiníte, vytvoření transakční fronty.  
  
7. Vytvoření hostitele služby pro službu pomocí <xref:System.ServiceModel.ServiceHost>.  
  
8. Otevření hostitele služby, aby tato služba k dispozici.  
  
9. Zavřete hostitele služby.  
  
#### <a name="to-set-up-a-client"></a>Nastavení klienta  
  
1. Vytvoření oboru transakce k zápisu transakční fronty.  
  
2. Vytvoření pomocí klienta WCF [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) nástroj.  
  
3. Objednávku.  
  
4. Zavřete klienta WCF.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad uvádí kód `IProcessOrder` služby a pro klienta, která využívá tuto službu. To ukazuje, jak WCF používá relace ve frontě poskytnout chování seskupení.  
  
### <a name="code-for-the-service"></a>Kód služby  
 [!code-csharp[S_Msmq_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/service.cs#1)]
 [!code-vb[S_Msmq_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/service.vb#1)]  

### <a name="code-for-the-client"></a>Kód pro klienta  
 [!code-csharp[S_Msmq_Session#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/client.cs#3)]
 [!code-vb[S_Msmq_Session#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/client.vb#3)]  

## <a name="see-also"></a>Viz také:

- [Relace a fronty](../../../../docs/framework/wcf/samples/sessions-and-queues.md)
- [Přehled front](../../../../docs/framework/wcf/feature-details/queues-overview.md)
