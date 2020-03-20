---
title: Seskupování zpráv zařazených do fronty v relaci
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- queues [WCF]. grouping messages
ms.assetid: 63b23b36-261f-4c37-99a2-cc323cd72a1a
ms.openlocfilehash: 231310e5c427f507141e3c144cb02b8e848d4fbf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185161"
---
# <a name="grouping-queued-messages-in-a-session"></a>Seskupování zpráv zařazených do fronty v relaci
Windows Communication Foundation (WCF) poskytuje relaci, která umožňuje seskupit sadu souvisejících zpráv společně pro zpracování pomocí jedné přijímající aplikace. Zprávy, které jsou součástí relace, musí být součástí stejné transakce. Vzhledem k tomu, že všechny zprávy jsou součástí stejné transakce, pokud jedna zpráva se nezdaří zpracovat celou relaci je vrácena zpět. Relace mají podobné chování s ohledem na fronty nedoručených zpráv a fronty jed. Vlastnost Time to Live (TTL) nastavená na vazbě ve frontě nakonfigurované pro relace se použije pro relaci jako celek. Pokud jsou odeslány pouze některé zprávy v relaci před vypršením platnosti ttl, celá relace je umístěn a fronty nedoručených zpráv. Podobně při zprávy v relaci nezdaří odeslat do aplikace z fronty aplikace, celá relace je umístěn a fronty poison (pokud je k dispozici).  
  
## <a name="message-grouping-example"></a>Příklad seskupení zpráv  
 Jedním z příkladů, kde je užitečné seskupování zpráv je při implementaci aplikace zpracování objednávek jako služby WCF. Například klient odešle objednávku do této aplikace, která obsahuje řadu položek. Pro každou položku klient provede volání služby, což má za následek odeslání samostatné zprávy. Je možné sloužit A přijímat první položku a server B přijímat druhou položku. Při každém přidání položky musí server zpracovávající tuto položku najít příslušnou objednávku a přidat do ní položku, což je vysoce neefektivní. Stále narazíte na tyto neefektivnosti pouze s jedním serverem, který zpracovává všechny požadavky, protože server musí sledovat všechny aktuálně zpracovávané objednávky a určit, ke které z nich nová položka patří. Seskupení všech požadavků na jednu objednávku značně zjednodušuje implementaci takové aplikace. Klientská aplikace odešle všechny položky pro jednu objednávku v relaci, takže když služba zpracuje objednávku, zpracuje celou relaci najednou. \  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-set-up-a-service-contract-to-use-sessions"></a>Nastavení servisní smlouvy pro použití relací  
  
1. Definujte servisní smlouvu, která vyžaduje relaci. Proveďte to <xref:System.ServiceModel.ServiceContractAttribute> s atributem zadáním:  
  
    ```csharp
    SessionMode=SessionMode.Required  
    ```  
  
2. Označte operace ve smlouvě jako jednosměrné, protože tyto metody nic nevrátí. To se provádí <xref:System.ServiceModel.OperationContractAttribute> s atributem zadáním:  
  
    ```csharp  
    [OperationContract(IsOneWay = true)]  
    ```  
  
3. Implementujte servisní smlouvu <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode> <xref:System.ServiceModel.InstanceContextMode.PerSession?displayProperty=nameWithType>a zadejte . Tím se služba konkretizovat pouze jednou pro každou relaci.  
  
    ```csharp  
    [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
    ```  
  
4. Každá operace služby vyžaduje transakci. Zadejte to <xref:System.ServiceModel.OperationBehaviorAttribute> s atributem. Operace, která dokončí transakci by <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete> `true`měla být také nastavena na .  
  
    ```csharp  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]
    ```  
  
5. Nakonfigurujte koncový bod, `NetMsmqBinding` který používá vazby poskytované systémem.  
  
6. Vytvořte transakční frontu pomocí <xref:System.Messaging>aplikace . Frontu můžete také vytvořit pomocí služby Řízení front zpráv (MSMQ) nebo mmc. Pokud tak učiníte, vytvořte transakční frontu.  
  
7. Vytvořte hostitele služby pro <xref:System.ServiceModel.ServiceHost>službu pomocí .  
  
8. Chcete-li službu zpřístupnit, otevřete hostitele služby.  
  
9. Zavřete hostitele služby.  
  
#### <a name="to-set-up-a-client"></a>Nastavení klienta  
  
1. Vytvořte obor transakce pro zápis do transakční fronty.  
  
2. Vytvořte klienta WCF pomocí nástroje [ServiceModel Metadata Utility Tool (Svcutil.exe).](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)  
  
3. Objednejte si.  
  
4. Zavřete klienta WCF.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad obsahuje kód `IProcessOrder` pro službu a pro klienta, který používá tuto službu. Ukazuje, jak WCF používá relace ve frontě k poskytnutí chování seskupení.  
  
### <a name="code-for-the-service"></a>Kód pro službu  
 [!code-csharp[S_Msmq_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/service.cs#1)]
 [!code-vb[S_Msmq_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/service.vb#1)]  

### <a name="code-for-the-client"></a>Kód pro klienta  
 [!code-csharp[S_Msmq_Session#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/client.cs#3)]
 [!code-vb[S_Msmq_Session#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/client.vb#3)]  

## <a name="see-also"></a>Viz také

- [Relace a fronty](../../../../docs/framework/wcf/samples/sessions-and-queues.md)
- [Přehled front](../../../../docs/framework/wcf/feature-details/queues-overview.md)
