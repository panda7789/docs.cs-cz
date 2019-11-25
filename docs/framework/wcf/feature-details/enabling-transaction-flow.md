---
title: Povolení toku transakcí
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF], enabling flow
ms.assetid: a03f5041-5049-43f4-897c-e0292d4718f7
ms.openlocfilehash: 8aff6afb09c97d7d01f5e7b7f1b92ae24bb99fb7
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141764"
---
# <a name="enabling-transaction-flow"></a>Povolení toku transakcí
Windows Communication Foundation (WCF) poskytuje vysoce flexibilní možnosti pro řízení toku transakce. Nastavení toku transakce služby lze vyjádřit pomocí kombinace atributů a konfigurací.  
  
## <a name="transaction-flow-settings"></a>Nastavení toku transakce  
 Nastavení toku transakce jsou generována pro koncový bod služby v důsledku průniku následujících tří hodnot:  
  
- Atribut <xref:System.ServiceModel.TransactionFlowAttribute> zadaný pro každou metodu v kontraktu služby.  
  
- Vlastnost vazby `TransactionFlow` v konkrétní vazbě.  
  
- Vlastnost vazby `TransactionFlowProtocol` v konkrétní vazbě. Vlastnost vazby `TransactionFlowProtocol` umožňuje zvolit mezi dvěma různými transakčními protokoly, které lze použít k flowování transakce. Následující části stručně popisují každou z nich.  
  
### <a name="ws-atomictransaction-protocol"></a>Protokol WS-AtomicTransaction  
 Protokol WS-AtomicTransaction (WS-AT) je užitečný pro scénáře, kdy je potřeba vzájemná funkční spolupráce se zásobníky protokolů třetích stran.  
  
### <a name="oletransactions-protocol"></a>Protokol OleTransactions  
 Protokol OleTransactions je vhodný pro scénáře, kdy se nepodporuje interoperabilita se zásobníky protokolů jiných výrobců, a nasazování služby ví předem, že je služba protokolu WS-AT zakázaná místně, nebo že existující topologie sítě. Nepoužívejte upřednostnění použití WS-AT.  
  
 V následující tabulce jsou uvedeny různé typy toků transakcí, které lze vygenerovat pomocí těchto různých kombinací.  
  
|TransactionFlow<br /><br /> vazba|Vlastnost vazby TransactionFlow|Protokol vazby TransactionFlowProtocol|Typ toku transakce|  
|---------------------------------|--------------------------------------|----------------------------------------------|------------------------------|  
|Povinné|true|WS-AT|Transakce musí být převedena do interoperabilního formátu WS-AT.|  
|Povinné|true|OleTransactions|Transakce musí být předávána ve formátu OleTransactions WCF.|  
|Povinné|false|Nelze použít|Nelze použít, protože se jedná o neplatnou konfiguraci.|  
|Povolené|true|WS-AT|Transakce může být převedena do interoperabilního formátu WS-AT.|  
|Povolené|true|OleTransactions|Transakce se může přesměrovat ve formátu WCF OleTransactions.|  
|Povolené|false|Libovolná hodnota|Transakce není přesměrovaná.|  
|NotAllowed|Libovolná hodnota|Libovolná hodnota|Transakce není přesměrovaná.|  
  
 Následující tabulka shrnuje výsledek zpracování zprávy.  
  
|Příchozí zpráva|Nastavení TransactionFlow|Hlavička transakce|Výsledek zpracování zprávy|  
|----------------------|-----------------------------|------------------------|-------------------------------|  
|Formát očekávaného protokolu shody transakcí|Povoleno nebo povinný|`MustUnderstand` se rovná `true`.|Přihlášení|  
|Transakce neodpovídá očekávanému formátu protokolu.|Povinné|`MustUnderstand` se rovná `false`.|Odmítnuto, protože transakce je povinná|  
|Transakce neodpovídá očekávanému formátu protokolu.|Povolené|`MustUnderstand` se rovná `false`.|Odmítnuto, protože hlavička není srozumitelná|  
|Transakce pomocí libovolného formátu protokolu|NotAllowed|`MustUnderstand` se rovná `false`.|Odmítnuto, protože hlavička není srozumitelná|  
|Žádná transakce|Povinné|Není k dispozici|Odmítnuto, protože transakce je povinná|  
|Žádná transakce|Povolené|Není k dispozici|Přihlášení|  
|Žádná transakce|NotAllowed|Není k dispozici|Přihlášení|  
  
 Zatímco každá metoda ve kontraktu může mít různé požadavky na tok transakce, nastavení protokolu toku transakce je vymezeno na úrovni vazby. To znamená, že všechny metody, které sdílejí stejný koncový bod (a tudíž stejnou vazbu), sdílejí také stejné zásady, které umožňují nebo vyžadují tok transakce a také stejný transakční protokol, pokud je to možné.  
  
## <a name="enabling-transaction-flow-at-the-method-level"></a>Povolení toku transakce na úrovni metody  
 Požadavky na tok transakce nejsou vždy stejné pro všechny metody v kontraktu služby. Proto WCF také poskytuje mechanismus založený na atributech, aby bylo možné vyjádřit předvolby toku transakce jednotlivých metod. Toho dosáhnete <xref:System.ServiceModel.TransactionFlowAttribute>, která určuje úroveň, ve které operace služby akceptuje hlavičku transakce. Metody kontraktu služby byste měli označit pomocí tohoto atributu, pokud chcete povolit tok transakce. Tento atribut přebírá jednu z hodnot <xref:System.ServiceModel.TransactionFlowOption> výčtu, ve kterém je výchozí hodnota <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>. Pokud je zadána jakákoli hodnota kromě <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>, musí být metoda jednosměrná. Vývojář může pomocí tohoto atributu zadat požadavky nebo omezení toku transakce na úrovni metody v době návrhu.  
  
## <a name="enabling-transaction-flow-at-the-endpoint-level"></a>Povolení toku transakce na úrovni koncového bodu  
 Kromě <xref:System.ServiceModel.TransactionFlowAttribute> nastavení toku transakce na úrovni metody poskytuje služba WCF nastavení pro tok transakce v rámci koncového bodu a umožňuje správcům řídit tok transakcí na vyšší úrovni.  
  
 To je dosaženo <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>, který umožňuje povolit nebo zakázat tok příchozích transakcí v nastaveních vazby koncového bodu a také pro určení požadovaného formátu transakčního protokolu pro příchozí transakce.  
  
 Pokud vazba zakázala tok transakce, ale jedna z operací v kontraktu služby vyžaduje příchozí transakci, pak je vyvolána výjimka ověření při spuštění služby.  
  
 Většina ze stálých vazeb WCF poskytuje atributy `transactionFlow` a `transactionProtocol`, které vám umožní nakonfigurovat konkrétní vazbu pro příjem příchozích transakcí. Další informace o nastavení elementů konfigurace naleznete v tématu [\<binding >](../../configure-apps/file-schema/wcf/bindings.md).  
  
 Správce nebo nástroj pro nasazení může použít tok transakce na úrovni koncového bodu ke konfiguraci požadavků a omezení toku transakce v době nasazení pomocí konfiguračního souboru.  
  
## <a name="security"></a>Zabezpečení  
 Chcete-li zajistit zabezpečení a integritu systému, je nutné zabezpečit výměnu zpráv při toku transakcí mezi aplikacemi. Do žádné aplikace, která nemá nárok na účast ve stejné transakci, byste neměli přesměrovat ani zveřejňovat podrobnosti transakce.  
  
 Při generování klientů WCF pro neznámé nebo nedůvěryhodné webové služby prostřednictvím použití výměny metadat musí volání operací na těchto webových službách potlačit aktuální transakci, pokud je to možné. Následující příklad demonstruje, jak to udělat.  
  
```csharp
//client code which has an ambient transaction  
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Suppress))  
{  
    // No transaction will flow to this operation  
    untrustedProxy.Operation1(...);  
    scope.Complete();  
}  
//remainder of client code  
```  
  
 Služby je navíc potřeba nakonfigurovat tak, aby přijímaly příchozí transakce jenom od klientů, které ověřil a schválili. Příchozí transakce by měly být přijaty pouze v případě, že pocházejí z vysoce důvěryhodných klientů.  
  
## <a name="policy-assertions"></a>Kontrolní výrazy zásad  
 WCF používá kontrolní výrazy zásad pro řízení toku transakce. Kontrolní výrazy zásad lze nalézt v dokumentu zásad služby, který je generován agregací smluv, konfigurací a atributů. Klient může získat dokument zásad služby pomocí požadavku HTTP GET nebo WS-MetadataExchange Request-Reply. Klienti pak mohou zpracovat dokument zásad a určit, které operace v kontraktu služby mohou podporovat nebo vyžadovat tok transakce.  
  
 Kontrolní výrazy zásad toku transakce ovlivňují tok transakce určením hlaviček SOAP, které by měl klient odeslat službě, aby představovala transakci. Všechna záhlaví transakcí musí být označena jako `MustUnderstand` rovna `true`. Jakákoli zpráva s záhlavím označeným jinak je odmítnuta s chybou protokolu SOAP.  
  
 V rámci jedné operace může být k dispozici pouze jeden kontrolní výraz zásad souvisejících s transakcí. Dokumenty zásad s více než jedním kontrolním výrazem transakce u operace jsou považovány za neplatné a WCF je odmítne. Kromě toho může být v každém typu portu přítomen pouze jeden transakční protokol. Dokumenty zásad s operacemi odkazujícími na více než jeden transakční protokol v rámci jednoho typu portu jsou považovány za neplatné a jsou odmítnuty nástrojem pro nástroj pro dodávání [metadat (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Dokumenty zásad s kontrolními výrazy transakce, které jsou k dispozici pro výstupní zprávy nebo jednosměrné vstupní zprávy, jsou také považovány za neplatné.
