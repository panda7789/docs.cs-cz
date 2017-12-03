---
title: "Útoky opakováním"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a17e040-93cd-4432-81b9-9f62fec78c8f
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cd96404adea7fb8e7d59dcea322b2d3832f2bfe4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="replay-attacks"></a>Útoky opakováním
A *přehráním útoku* nastane, když útočník zkopíruje datového proudu zpráv mezi dvěma účastníky a replays datový proud na jeden nebo více stran. Pokud omezeny, počítače podřízené útoku zpracovat datového proudu jako legitimní zprávy, což vede k řadu chybný důsledky, jako je například redundantní objednávky položky.  
  
## <a name="bindings-may-be-subject-to-reflection-attacks"></a>Vazby může být vystavené útokům s reflexe  
 *Reflexe útoky* jsou opětovná přehrání zprávy zpět do odesílatele, jako kdyby jejich pochází přijímač jako odpověď. Standardní *zjišťování opakování* v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] mechanismus nezpracovává automaticky to.  
  
 Reflexe útoky jsou omezeny ve výchozím nastavení, protože [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] model služby přidá ID podepsanou zprávu do zprávy žádosti a očekává přihlášeni `relates-to` hlavičky v odpovědi na zprávy. Zpráva žádosti v důsledku toho nelze přehrány jako odpověď. Ve scénářích zabezpečenou zprávu spolehlivé (RM) jsou omezeny reflexe útoky protože:  
  
-   Vytvoření pořadí a vytvořit pořadí odpovědi zpráva schémat se liší.  
  
-   Protože klient nemůže porozumět takové zprávy, nelze pro nezpracovávají pořadí přehrány pořadí zprávy, které klient odesílá zpět do.  
  
-   Duplexní pořadí dvě pořadí ID musí být jedinečný. Odchozí zprávy pořadí nelze proto přehrány zpět jako příchozí zprávy pořadí (všechna pořadí záhlaví a texty jsou podepsané, příliš).  
  
 Jenom vazby, které jsou náchylné k útokům reflexe jsou bez WS-Addressing: vlastní vazby, které mají WS adresování zakázat a použít symetrický zabezpečení na základě klíčů. <xref:System.ServiceModel.BasicHttpBinding> Nepoužívá WS-Addressing ve výchozím nastavení, ale nepoužívá symetrický zabezpečení na základě klíčů způsobem, který mohou být zranitelné v důsledku tento útok.  
  
 Je toto řešení pro vlastní vazby není vytvoření kontextu zabezpečení nebo tak, aby vyžadovala WS-Addressing hlavičky.  
  
## <a name="web-farm-attacker-replays-request-to-multiple-nodes"></a>Webové farmy: Útočník opětovná přehrání požadavek na víc uzlů  
 Klient používá službu, která se implementuje na webové farmy. Útočník replays žádost byla odeslána do jednoho uzlu ve farmě do jiného uzlu ve farmě. Kromě toho pokud restartování služby mezipaměti opětovného přehrání vyprazdňuje, což útočníkovi o přehrání žádosti. (Mezipaměť obsahuje podpis hodnoty používané, dříve zobrazenou zpráv a zabraňuje přehrání, takže tyto podpisy lze použít pouze jednou. Přehrání mezipaměti nejsou sdílená mezi webové farmy.)  
  
 Způsoby zmírnění patří:  
  
-   Režim zabezpečení zpráv pomocí tokenů kontextu stavová zabezpečení (s nebo bez zabezpečené konverzaci povoleno). [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Postupy: Vytvoření kontextu zabezpečení tokenu pro zabezpečenou relaci](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).  
  
-   Nakonfigurujte službu, která používá zabezpečení na úrovni přenosu.  
  
## <a name="see-also"></a>Viz také  
 [Aspekty zabezpečení](../../../../docs/framework/wcf/feature-details/security-considerations-in-wcf.md)  
 [Zpřístupnění informací](../../../../docs/framework/wcf/feature-details/information-disclosure.md)  
 [Zvýšení úrovně oprávnění](../../../../docs/framework/wcf/feature-details/elevation-of-privilege.md)  
 [Odmítnutí služby](../../../../docs/framework/wcf/feature-details/denial-of-service.md)  
 [Manipulaci](../../../../docs/framework/wcf/feature-details/tampering.md)  
 [Nepodporované scénáře](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)
