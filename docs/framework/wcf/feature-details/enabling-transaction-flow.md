---
title: Povolení toku transakcí
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF], enabling flow
ms.assetid: a03f5041-5049-43f4-897c-e0292d4718f7
ms.openlocfilehash: 180fc99195444057c5bbb4a1679e948f9ddf1830
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="enabling-transaction-flow"></a>Povolení toku transakcí
Windows Communication Foundation (WCF) poskytuje vysoce flexibilní možnosti pro řízení toku transakcí. Nastavení toku transakcí služby lze vyjádřit pomocí kombinace atributů a konfigurace.  
  
## <a name="transaction-flow-settings"></a>Nastavení toku transakcí  
 Nastavení toku transakce jsou generovány pro koncový bod služby v důsledku průnik následující tři hodnoty:  
  
-   <xref:System.ServiceModel.TransactionFlowAttribute> Atribut pro každou metodu v kontrakt služby.  
  
-   `TransactionFlow` Vlastnost Vazba konkrétní vazba.  
  
-   `TransactionFlowProtocol` Vlastnost Vazba konkrétní vazba. `TransactionFlowProtocol` Vazby vlastnosti vám umožní vybrat mezi dva protokoly jinou transakci, můžete toku transakce. Následující části popisují stručně každý z nich.  
  
### <a name="ws-atomictransaction-protocol"></a>Protokol WS-AtomicTransaction  
 Protokol WS-AtomicTransaction (WS-AT) je užitečné v případech, pokud vzájemná funkční spolupráce s zásobníky třetích stran protokol je potřeba.  
  
### <a name="oletransactions-protocol"></a>Protokol OleTransactions  
 Protokol OleTransactions je užitečné v případech, pokud vzájemná funkční spolupráce s zásobníky třetích stran protokolu není potřeba, a deployer služby zná předem, aby služba protokolu WS-AT je zakázána místně nebo nemá existující topologie sítě není upřednostnit využití WS-AT.  
  
 Následující tabulka uvádí různé typy toků transakce, které lze generovat pomocí těchto různé kombinace.  
  
|TransactionFlow<br /><br /> vazba|Vlastnost TransactionFlow vazby|Protokol vazby TransactionFlowProtocol|Typ toku transakcí|  
|---------------------------------|--------------------------------------|----------------------------------------------|------------------------------|  
|Povinné|true|WS-AT|Transakce musí být plynoucích ve formátu interoperabilní služby WS-AT.|  
|Povinné|true|OleTransactions|Transakce musí být naplněn ve formátu WCF OleTransactions.|  
|Povinné|false|Nelze použít|Není k dispozici vzhledem k tomu, že tato konfigurace je neplatná.|  
|Povoleno|true|WS-AT|Transakce může plynoucích ve formátu interoperabilní služby WS-AT.|  
|Povoleno|true|OleTransactions|Transakce může plynoucích ve formátu WCF OleTransactions.|  
|Povoleno|false|Libovolná hodnota|Transakce není plynoucích.|  
|NotAllowed|Libovolná hodnota|Libovolná hodnota|Transakce není plynoucích.|  
  
 Následující tabulka shrnuje výsledek zpracování zpráv.  
  
|Příchozí zprávy|Nastavení TransactionFlow|Záhlaví transakce|Výsledek zpracování zprávy|  
|----------------------|-----------------------------|------------------------|-------------------------------|  
|Transakce odpovídá formátu očekávanému protokolu|Povolených nebo povinné|`MustUnderstand` se rovná `true`.|Proces|  
|Transakce není ve formátu očekávanému protokolu|Povinné|`MustUnderstand` se rovná `false`.|Odmítnuta, protože je požadována transakce|  
|Transakce není ve formátu očekávanému protokolu|Povoleno|`MustUnderstand` se rovná `false`.|Odmítnuta, protože nebyl pochopen záhlaví|  
|Všechny formátu protokolu transakcí|NotAllowed|`MustUnderstand` se rovná `false`.|Odmítnuta, protože nebyl pochopen záhlaví|  
|Žádná transakce|Povinné|Není k dispozici|Odmítnuta, protože je požadována transakce|  
|Žádná transakce|Povoleno|Není k dispozici|Proces|  
|Žádná transakce|NotAllowed|Není k dispozici|Proces|  
  
 Při každé metody na kontraktu můžou mít požadavky toku jinou transakci, nastavení protokolu toku transakcí je vymezen na úrovni vazby. To znamená, že všechny metody, které sdílejí stejnou koncový bod (a proto stejnou vazbu) také sdílet stejné zásady povolit nebo nutnosti toku transakcí, jakož i stejný protokol transakcí, pokud je k dispozici.  
  
## <a name="enabling-transaction-flow-at-the-method-level"></a>Povolení toku transakcí na úrovni – metoda  
 Požadavky na toku transakce nejsou vždy stejný pro všechny metody v kontraktu služby. Proto WCF také poskytuje mechanismus založený na atributu umožňující každá metoda transakce toku předvolby vyjádřeno. Toho se dosáhne <xref:System.ServiceModel.TransactionFlowAttribute> , určuje úroveň, ve kterém přijímá operace služby hlavičku transakce. Pokud chcete povolit toku transakcí byste měli označit vaše metody kontrakt služby s tímto atributem. Tento atribut má jednu z hodnot <xref:System.ServiceModel.TransactionFlowOption> výčtu, ve kterém se výchozí hodnota je <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>. Pokud je některá hodnota s výjimkou <xref:System.ServiceModel.TransactionFlowOption.NotAllowed> je zadána, je potřeba metodu nesmí být jednosměrná. Vývojář může použít tento atribut určete úrovni metody transakce toku požadavky nebo omezení v době návrhu.  
  
## <a name="enabling-transaction-flow-at-the-endpoint-level"></a>Povolení toku transakcí na úrovni koncového bodu  
 Kromě nastavení tok metoda úroveň transakce <xref:System.ServiceModel.TransactionFlowAttribute> poskytuje atribut, WCF poskytuje nastavení úrovni koncového bodu pro tok transakcí do umožňují správcům řídit tok transakcí na vyšší úrovni.  
  
 Toho se dosáhne <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>, což umožňuje povolit nebo zakázat příchozí tok transakcí v koncový bod nastavení také vazby, zadejte požadované transakce formát protokolu pro příchozí transakce.  
  
 Pokud vazba zakázal toku transakcí, ale některé z operací na kontraktu služby vyžaduje příchozí transakce, je vyvolána výjimka ověření při spuštění služby.  
  
 Většina stojící vazby WCF poskytuje obsahovat `transactionFlow` a `transactionProtocol` atributů, které vám umožní nakonfigurovat konkrétní vazby tak, aby přijímal příchozí transakce. Další informace o nastavení konfigurační prvky najdete v tématu [ \<vazby >](../../../../docs/framework/misc/binding.md).  
  
 Správce nebo nástroje pro nasazení slouží ke konfiguraci transakce toku požadavky nebo omezení v době nasazení pomocí konfiguračního souboru toku transakcí úrovni koncového bodu.  
  
## <a name="security"></a>Zabezpečení  
 Aby systém zabezpečení a integrity, musíte zabezpečit výměny zpráv při průchodu transakce mezi aplikacemi. Byste neměli toku ani zveřejnit podrobnosti transakce pro každou aplikaci, která nemá oprávnění k účasti ve stejné transakci.  
  
 Při generování klienti WCF na neznámý nebo nedůvěryhodný webových služeb prostřednictvím metadata exchange, volání operací na tyto webové služby-li to možné potlačit aktuální transakci. Následující příklad demonstruje, jak to udělat.  
  
```  
//client code which has an ambient transaction  
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Suppress))  
{  
    // No transaction will flow to this operation  
    untrustedProxy.Operation1(...);  
    scope.Complete();  
}  
//remainder of client code  
```  
  
 Kromě toho služby by měl být nastaven na přijímání příchozích transakcí pouze od klientů, kteří budou mít ověří a autorizuje. Příchozí transakce by měla pouze přípustné, které pocházejí z vysoce důvěryhodné klienty.  
  
## <a name="policy-assertions"></a>Kontrolní výrazy zásad  
 WCF používá k řízení toku transakcí výrazy zásad. Kontrolních výrazů zásad najdete v dokumentu zásady služby, který je generován totožný kontrakty, konfiguraci a atributy. Klient může získat dokument zásad služby pomocí HTTP GET nebo WS-MetadataExchange požadavek odpověď. Klienti potom může zpracovat zásady dokumentu a zjistěte, které operace na kontraktu služby může podporovat nebo vyžadovat toku transakcí.  
  
 Výrazy zásad toku transakcí ovlivnit tok transakcí zadáním hlavičky SOAP, klient by měl poslat služby představují transakce. Všechny hlavičky transakce musí být označené jako `MustUnderstand` rovna `true`. Všechny zprávy s hlavičku označena jinak se odmítne kvůli chybě protokolu SOAP.  
  
 Pouze jeden výraz související transakci zásad může být v rámci jedné operace. Zásady dokumenty s více než jeden výraz transakce na operace jsou považovány za neplatné a odmítne WCF. Kromě toho může být pouze protokol jedné transakci nachází uvnitř každý typ portu. Dokumenty zásad s operacemi odkazující na více než jeden protokol transakcí uvnitř typu jediný port, jsou považovány za neplatné a odmítne [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Dokumenty zásad pomocí kontrolních výrazů transakce k dispozici výstupní zprávy nebo jednosměrný vstupní zprávy jsou také považovány za neplatné.
