---
title: Útoky opakováním
ms.date: 03/30/2017
ms.assetid: 7a17e040-93cd-4432-81b9-9f62fec78c8f
ms.openlocfilehash: 6874e87ba2a50bb496c5d7bf091fd670510ab840
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626865"
---
# <a name="replay-attacks"></a>Útoky opakováním
A *přehrát útoku* nastane, pokud útočník zkopíruje datový proud zpráv mezi dvěma stranami a přehrává datový proud na jeden nebo více stran. Není-li minimalizovat, počítače v souladu s útoku zpracování datového proudu jako legitimní zprávy, což vede k celou řadu chybný důsledky, jako je například redundantní objednávky položku.  
  
## <a name="bindings-may-be-subject-to-reflection-attacks"></a>Vazby se můžou stát terčem útoků reflexe  
 *Reflexe útoky* jsou riziko zprávy zpět do odesílatele, jako kdyby pocházejí přijímač jako odpověď. Standardní *přehrání* ve Windows Communication Foundation (WCF) mechanismus nezpracovává automaticky to.  
  
 Reflexe útoky jsou ve výchozím nastavení zmírnit, protože model služby WCF přidá podepsanou zprávu ID zpráv požadavků a očekává, že podepsané `relates-to` záhlaví zprávy odpovědi. V důsledku toho nelze přehrály zprávy s požadavkem jako odpověď. Ve scénářích zabezpečené spolehlivé zprávy (SV) jsou útoky reflexe zmírnit, protože:  
  
- Vytvoření pořadí a schémata zpráv odpověď vytvoření sekvence se liší.  
  
- Vzhledem k tomu, že klient nemůže rozumět takové zprávy, nelze pro nezpracovávají pořadí přehrály zprávy sekvence, které klient odešle zpět do.  
  
- Pro duplexní pořadí dvě pořadí identifikátory musí být jedinečný. Odchozí zpráva sekvence nemůže proto znovu přehrát zpět jako příchozí zprávy sekvence (všechny hlavičky pořadí a úřadů, které jsou podepsané, příliš).  
  
 Pouze vazby, které jsou náchylné k útokům reflexe jsou bez WS-Addressing: vlastní vazby, které mají WS-Addressing zakázána a použít symetrický klíč zabezpečení. <xref:System.ServiceModel.BasicHttpBinding> Nepoužívá WS-Addressing ve výchozím nastavení, ale nepoužívá symetrický klíč zabezpečení tak, aby díky tomu bude zranitelný vůči útoku.  
  
 Zmírnění dopadů pro vlastní vazby není vytvoření kontextu zabezpečení nebo tak, aby vyžadovala záhlaví WS-Addressing.  
  
## <a name="web-farm-attacker-replays-request-to-multiple-nodes"></a>Webové farmy: Útočník riziko požadavek na víc uzlů  
 Klient používá službu, která je implementována do webové farmy. Útočník přehrává žádost byla odeslána na jeden uzel ve farmě do jiného uzlu ve farmě. Kromě toho pokud restartování služby mezipaměti opětovného přehrání vyprazdňuje, což útočníkovi umožňuje přehrát požadavku. (Mezipaměť obsahuje podpis hodnoty používané, dříve zobrazenou zprávy a brání riziko, takže tyto podpisy lze použít pouze jednou. Přehrání mezipaměti nejsou sdíleny napříč webovou farmu.)  
  
 Zmírnění rizik patří:  
  
- Režim zabezpečení zpráv pomocí tokenů kontextu zabezpečení stavové (s nebo bez zabezpečené konverzace povolené). Další informace najdete v tématu [jak: Vytvoření kontextu zabezpečení pro zabezpečenou relaci Token](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).  
  
- Konfigurace služby pro použití zabezpečení na úrovni přenosu.  
  
## <a name="see-also"></a>Viz také:

- [Důležité informace o zabezpečení](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)
- [Zpřístupnění informací](../../../../docs/framework/wcf/feature-details/information-disclosure.md)
- [Zvýšení oprávnění](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)
- [Útok DoS](../../../../docs/framework/wcf/feature-details/denial-of-service.md)
- [Falšování](../../../../docs/framework/wcf/feature-details/tampering.md)
- [Nepodporované scénáře](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
