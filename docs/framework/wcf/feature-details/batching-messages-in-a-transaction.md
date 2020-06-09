---
title: Dávkování zpráv v transakci
ms.date: 03/30/2017
helpviewer_keywords:
- batching messages [WCF]
ms.assetid: 53305392-e82e-4e89-aedc-3efb6ebcd28c
ms.openlocfilehash: 3b35d1de76587ce750bf73189eb37658c3d87a90
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593617"
---
# <a name="batching-messages-in-a-transaction"></a>Dávkování zpráv v transakci
Aplikace zařazené do fronty používají transakce k zajištění správnosti a spolehlivého doručování zpráv. Transakce jsou ale náročné na operace a můžou významně snižovat propustnost zpráv. Jedním ze způsobů, jak zvýšit propustnost zpráv, je mít aplikace čtení a zpracování více zpráv v rámci jedné transakce. Kompromis mezi výkonem a obnovením: při zvyšování počtu zpráv v dávce dojde v důsledku toho k tomu, že množství práce obnovení vyžadované v případě vrácení transakcí zpět. Je důležité poznamenat rozdíl mezi dávkovými zprávami v transakci a relacích. *Relace* je seskupení souvisejících zpráv, které jsou zpracovávány jedinou aplikací a potvrzené jako jedna jednotka. Relace se obecně používají v případě, že je třeba zpracovat skupinu souvisejících zpráv. Příkladem je online nákupní web. *Dávky* se používají ke zpracování několika nesouvisejících zpráv způsobem, který zvyšuje propustnost zprávy. Další informace o relacích najdete v tématu [seskupování zpráv zařazených do fronty v relaci](grouping-queued-messages-in-a-session.md). Zprávy v dávce jsou také zpracovávány pomocí jedné aplikace a potvrzeny jako jediná jednotka, ale mezi zprávami v dávce nemusí existovat žádný vztah. Dávkování zpráv v transakci je optimalizace, která nemění způsob, jakým se aplikace spouští.  
  
## <a name="entering-batching-mode"></a>Vstup do režimu dávkování  
 <xref:System.ServiceModel.Description.TransactedBatchingBehavior>Chování koncového bodu řídí dávkování. Přidání tohoto chování koncového bodu do koncového bodu služby instruuje Windows Communication Foundation (WCF) k dávkám zpráv v transakci. Ne všechny zprávy vyžadují transakci, takže pouze zprávy, které vyžadují transakci, se umístí do dávky a `TransactionScopeRequired`  =  `true` `TransactionAutoComplete`  =  `true` pro dávku se považují pouze zprávy odeslané z operací s označením a. Pokud jsou všechny operace v kontraktu služby označeny `TransactionScopeRequired`  =  `false` a `TransactionAutoComplete`  =  `false` , pak se režim dávkování nikdy nezadá.  
  
## <a name="committing-a-transaction"></a>Potvrzení transakce  
 Dávkovaná transakce je potvrzena podle následujících pokynů:  
  
- `MaxBatchSize`. Vlastnost <xref:System.ServiceModel.Description.TransactedBatchingBehavior> chování. Tato vlastnost určuje maximální počet zpráv, které jsou umístěny do dávky. Po dosažení tohoto čísla se dávka potvrdí. Toto je hodnota nestriktního limitu, je možné před přijetím tohoto počtu zpráv potvrdit dávku.  
  
- `Transaction Timeout`. Po uplynutí 80 procent časového limitu transakce se dávka potvrdí a vytvoří se nová dávka. To znamená, že v případě, že je v případě, že je transakce dokončena, zbývá 20% nebo méně času, dávka bude potvrzena.  
  
- `TransactionScopeRequired`. Při zpracování dávky zpráv, pokud WCF nalezne jednu z nich `TransactionScopeRequired`  =  `false` , potvrdí dávku a znovu otevře novou dávku při přijetí první zprávy s `TransactionScopeRequired`  =  `true` a `TransactionAutoComplete`  =  `true` .  
  
- Pokud ve frontě neexistují žádné další zprávy, bude aktuální dávka potvrzena i v případě, že nebyla `MaxBatchSize` dosažena nebo 80% časového limitu transakce neuplynula.  
  
## <a name="leaving-batching-mode"></a>Opustit režim dávkování  
 Pokud zpráva v dávce způsobí přerušení transakce, dojde k následujícím krokům:  
  
1. Celá dávka zpráv se vrátí zpět.  
  
2. Zprávy jsou čteny po jednom, dokud počet přečtených zpráv nepřekračuje maximální velikost dávky.  
  
3. Dávkový režim je znovu zadán.  
  
## <a name="choosing-the-batch-size"></a>Výběr velikosti dávky  
 Velikost dávky je závislá na aplikaci. Empirická metoda je nejlepší způsob, jak dosáhnout optimální velikosti dávky pro aplikaci. Je důležité si uvědomit, že při výběru velikosti dávky se má zvolit velikost podle skutečného modelu nasazení vaší aplikace. Například při nasazení aplikace, pokud potřebujete SQL Server na vzdáleném počítači a transakci, která zahrnuje frontu a SQL Server, pak je velikost dávky nejlépe určena spuštěním této přesné konfigurace.  
  
## <a name="concurrency-and-batching"></a>Souběžnost a dávkování  
 Pokud chcete zvýšit propustnost, můžete mít také souběžně spuštěnou spoustu dávek. Nastavením `ConcurrencyMode.Multiple` v `ServiceBehaviorAttribute` můžete povolit souběžnou dávkování.  
  
 *Omezování služby* je chování služby, které slouží k určení, kolik maximálních souběžných volání může být ve službě provedeno. Při použití s dávkou pro dávkové zpracování je tato funkce interpretována jako počet souběžných dávek, které lze spustit. Pokud není omezení služby nastaveno, služba WCF nastaví maximální počet souběžných volání na 16. Proto, pokud bylo chování dávkování přidáno ve výchozím nastavení, může být aktivní maximálně 16 dávek. Nejlepší je vyladit omezení služby a dávkování na základě vaší kapacity. Pokud má například fronta zprávy 100 a dávka 20 je požadovaná, maximální počet souběžných volání nastavených na 16 není užitečný, protože v závislosti na propustnosti může být 16 transakcí aktivní, podobně jako při nezapnutém dávkování. Proto při vyladění výkonu buď nemají souběžnou dávkování, nebo nemají souběžnou dávkování se správnou velikostí omezení služby.  
  
## <a name="batching-and-multiple-endpoints"></a>Dávkování a více koncových bodů  
 Koncový bod se skládá z adresy a kontraktu. Může existovat několik koncových bodů, které sdílejí stejnou vazbu. Je možné, aby dva koncové body sdílely stejnou vazbu a naslouchaly identifikátoru URI (Uniform Resource Identifier) nebo adresy front. Pokud se ze stejné fronty čtou dva koncové body a do obou koncových bodů se přidají transakční chování dávkování, může dojít ke konfliktu ve specifikovaných velikostech dávek. To je vyřešeno implementací dávkového zpracování s použitím minimální velikosti dávky zadané mezi dvěma transakčními chováními v dávce. V tomto scénáři, pokud jeden z koncových bodů nespecifikuje transakční dávkování, pak oba koncové body nepoužívají dávkování.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak zadat `TransactedBatchingBehavior` v konfiguračním souboru.  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="TransactedBatchingBehavior"
              maxBatchSize="100" />
  </endpointBehaviors>
</behaviors>
```  
  
 Následující příklad ukazuje, jak zadat <xref:System.ServiceModel.Description.TransactedBatchingBehavior> kód v kódu.  
  
```csharp
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService)))
{
     ServiceEndpoint sep = ServiceHost.AddServiceEndpoint(typeof(IOrderProcessor), new NetMsmqBinding(), "net.msmq://localhost/private/ServiceModelSamplesTransacted");
     sep.Behaviors.Add(new TransactedBatchingBehavior(100));

     // Open the ServiceHost to create listeners and start listening for messages.
    serviceHost.Open();
  
    // The service can now be accessed.
    Console.WriteLine("The service is ready.");
    Console.WriteLine("Press <ENTER> to terminate service.");
    Console.WriteLine();
    Console.ReadLine();
  
    // Close the ServiceHostB to shut down the service.
    serviceHost.Close();
}  
```  
  
## <a name="see-also"></a>Viz také

- [Přehled front](queues-overview.md)
- [Fronty ve WCF](queuing-in-wcf.md)
