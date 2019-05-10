---
title: Povolení toku transakcí
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF], enabling flow
ms.assetid: a03f5041-5049-43f4-897c-e0292d4718f7
ms.openlocfilehash: 560b03b8e2788c88e6c92c64834bf36c750575ea
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626947"
---
# <a name="enabling-transaction-flow"></a>Povolení toku transakcí
Windows Communication Foundation (WCF) poskytuje vysoce flexibilní možnosti pro řízení toku transakce. Nastavení toku transakce služby lze vyjádřit pomocí kombinace atributů a konfigurace.  
  
## <a name="transaction-flow-settings"></a>Nastavení toku transakcí  
 Nastavení toku transakce jsou generovány pro koncový bod služby v důsledku je určena průsečíkem následujících tří hodnot:  
  
- <xref:System.ServiceModel.TransactionFlowAttribute> Atribut zadaný pro každé metodě v kontraktu služby.  
  
- `TransactionFlow` Vazby vlastností v konkrétní vazby.  
  
- `TransactionFlowProtocol` Vazby vlastností v konkrétní vazby. `TransactionFlowProtocol` Vazby vlastností můžete zvolit mezi dva různé transakční protokoly, že vám pomůže transakce. Následující části stručně popisují každou z nich.  
  
### <a name="ws-atomictransaction-protocol"></a>Protokol WS-AtomicTransaction  
 Protokol WS-AtomicTransaction (WS-AT) je užitečná v případech, pokud je nutné použít vzájemná funkční spolupráce s sad protokolů třetích stran.  
  
### <a name="oletransactions-protocol"></a>Protokolu OleTransactions  
 Protokolu OleTransactions je užitečné pro scénáře, když vzájemná funkční spolupráce s sad protokolů třetí strany se nevyžaduje a deployer služby ví předem, že služba protokol WS-AT zakázána místně nebo neodpovídá existující topologie sítě upřednostnit není využití WS-AT.  
  
 V následující tabulce jsou uvedeny různé typy toků transakce, které můžete vygenerovat pomocí těchto různých kombinací.  
  
|TransactionFlow<br /><br /> vazba|Vlastnost binding TransactionFlow|Protokol vazby TransactionFlowProtocol|Typ toku transakcí|  
|---------------------------------|--------------------------------------|----------------------------------------------|------------------------------|  
|Povinné|true|WS-AT|Transakce musí být předávány v interoperabilním formátu WS-AT.|  
|Povinné|true|OleTransactions|Transakce musí být předávány ve formátu WCF OleTransactions.|  
|Povinné|false|Nelze použít|Nedá se použít kvůli tato konfigurace je neplatná.|  
|Povoleno|true|WS-AT|Transakce mohou být předávány v interoperabilním formátu WS-AT.|  
|Povoleno|true|OleTransactions|Transakce mohou být předávány ve formátu WCF OleTransactions.|  
|Povoleno|false|Libovolná hodnota|Transakce není naplněn.|  
|Hodnotu NotAllowed|Libovolná hodnota|Libovolná hodnota|Transakce není naplněn.|  
  
 Následující tabulka shrnuje výsledek zpracování zprávy.  
  
|Příchozí zpráva|Nastavení TransactionFlow|Záhlaví transakce|Výsledek zpracování zprávy|  
|----------------------|-----------------------------|------------------------|-------------------------------|  
|Transakce odpovídá očekávanému protokol formátu|Povolené nebo povinné|`MustUnderstand` se rovná `true`.|Proces|  
|Transakce neodpovídá očekávanému protokol formátu|Povinné|`MustUnderstand` se rovná `false`.|Odmítnout, protože je požadována transakce|  
|Transakce neodpovídá očekávanému protokol formátu|Povoleno|`MustUnderstand` se rovná `false`.|Odmítnout, protože nebylo porozuměno záhlaví|  
|Transakci pomocí libovolný formát protokolu|Hodnotu NotAllowed|`MustUnderstand` se rovná `false`.|Odmítnout, protože nebylo porozuměno záhlaví|  
|Žádná transakce|Povinné|Není k dispozici|Odmítnout, protože je požadována transakce|  
|Žádná transakce|Povoleno|Není k dispozici|Proces|  
|Žádná transakce|Hodnotu NotAllowed|Není k dispozici|Proces|  
  
 Zatímco jednotlivé metody na smlouvy může mít jinou transakcí toku požadavky, nastavení protokolu toku transakce je vymezen na úrovni vazby. To znamená, že všechny metody, které sdílejí stejný koncový bod (a tedy stejnou vazbu) také sdílet stejné zásady, povolení nebo vyžadování tok transakcí, stejně jako stejný protokol transakce, pokud je k dispozici.  
  
## <a name="enabling-transaction-flow-at-the-method-level"></a>Povolení toku transakcí na úrovni – metoda  
 Požadavky na tok transakce nejsou vždy stejný pro všechny metody v kontraktu služby. Proto WCF také poskytuje mechanismus založených na atributech umožňující předvolby toku transakce každá metoda vyjádřit. To se provádí <xref:System.ServiceModel.TransactionFlowAttribute> , který určuje úroveň, ve kterém přijímá operace služby záhlaví transakce. Pokud chcete povolit tok transakcí, byste měli označit vaše metody kontraktu služby se tento atribut. Tento atribut má jednu z hodnot <xref:System.ServiceModel.TransactionFlowOption> výčtu, ve kterém se výchozí hodnota je <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>. Pokud je některá hodnota s výjimkou <xref:System.ServiceModel.TransactionFlowOption.NotAllowed> není zadána, je potřeba metodu nesmí být jednosměrná. Vývojář můžete použít tento atribut k určení požadavků na úrovni metod transakce toku nebo omezení v době návrhu.  
  
## <a name="enabling-transaction-flow-at-the-endpoint-level"></a>Povolení toku transakcí na úrovni koncového bodu  
 Kromě nastavení toku transakcí na úrovni metod <xref:System.ServiceModel.TransactionFlowAttribute> obsahuje atribut WCF obsahuje nastavení úrovni koncového bodu pro tok transakcí a umožňuje správcům řídit tok transakcí na vyšší úrovni.  
  
 To se provádí <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>, což vám umožní povolit nebo zakázat příchozí tok transakcí v koncovém bodu vazby nastavení také k určení formátu protokolu požadované transakce pro příchozí transakce.  
  
 Pokud vazba zakázal tok transakcí, ale jedna operace v kontraktu služby vyžaduje příchozí transakce, je vyvolána výjimka ověření při spuštění služby.  
  
 Většina stálého vazeb WCF poskytuje, obsahují `transactionFlow` a `transactionProtocol` atributy, které vám umožní nakonfigurovat konkrétní vazbu tak, aby přijímal příchozí transakce. Další informace o nastavení konfigurační prvky, naleznete v tématu [ \<vazby >](../../../../docs/framework/misc/binding.md).  
  
 Správce nebo nástroje pro nasazení můžete použít tok transakcí úrovni koncového bodu konfigurace požadavků na tok transakce nebo omezení v době nasazení je používán konfigurační soubor.  
  
## <a name="security"></a>Zabezpečení  
 Aby bylo zajištěno zabezpečení systému a integrita standardu, musíte zabezpečit výměny zpráv proudění transakcí mezi aplikacemi. Neměli tok nebo poskytovat podrobnosti o transakci pro každou aplikaci, která nemá nárok na účast v rámci jedné transakce.  
  
 Při generování klientů WCF na neznámý nebo nedůvěryhodný webové služby prostřednictvím výměny metadat, volání operací na těchto webových službách Pokud je to možné potlačit aktuální transakce. Následující příklad demonstruje, jak to udělat.  
  
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
  
 Kromě toho služby musí být nakonfigurovaný tak, aby přijímal příchozí transakce pouze od klientů, kteří mají ověřený a autorizovaný. Příchozí transakce by měl přijmout, pouze pokud pocházejí z vysoce důvěryhodné klienty.  
  
## <a name="policy-assertions"></a>Kontrolní výrazy zásad  
 Kontrolní výrazy zásad WCF používá k řízení toku transakcí. Kontrolní výrazy zásad najdete v dokumentu zásad služby, který je generován agregovat kontrakty, konfigurace a atributy. Klienta můžete získat dokument zásad služby pomocí HTTP GET nebo WS-MetadataExchange požadavek odpověď. Klienti mohou následně zpracovat dokument zásad k určení, které operace v kontraktu služby může podporovalo nebo vyžadovalo tok transakcí.  
  
 Kontrolní výrazy zásad toku transakce ovlivnit tok transakcí zadáním hlavičky SOAP, že klient má odeslat do služby představují transakce. Všechna záhlaví transakce musí být označeny pomocí `MustUnderstand` rovna `true`. Všechny zprávy s hlavičkou označen jinak se odmítne kvůli nastala chyba protokolu SOAP.  
  
 Pouze jeden výraz související transakce zásad může být k dispozici v rámci jedné operace. Zásady dokumenty s více než jeden výraz transakce u určité operace jsou považovány za neplatné a odmítne WCF. Kromě toho může být pouze jedné transakční protokol k dispozici uvnitř každý typ portu. Dokumenty zásad s operacemi odkazuje více než jeden protokol transakce uvnitř jednoho portu typu jsou považovány za neplatné a odmítne [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md). Dokumenty zásad pomocí kontrolních výrazů transakce prezentují na výstupní zprávy nebo jednosměrné zprávy o zadávání jsou také považovány za neplatné.
