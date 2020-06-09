---
title: Útoky opakováním
ms.date: 03/30/2017
ms.assetid: 7a17e040-93cd-4432-81b9-9f62fec78c8f
ms.openlocfilehash: 47a4726859605415b4e3e1b4d523f2f8059a3989
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84586296"
---
# <a name="replay-attacks"></a>Útoky opakováním
K *útoku opakovaného přehrání* dojde, když útočník zkopíruje datový proud zpráv mezi dvěma stranami a přehraje datový proud na jednu nebo více stran. Pokud to snižuje riziko, počítače, na které se útok vztahuje, zpracovávají datový proud jako legitimní zprávy, což vede k celé řadě špatných důsledků, jako je například redundantní objednávka položky.  
  
## <a name="bindings-may-be-subject-to-reflection-attacks"></a>Vazby můžou být vystavené útokům reflexe.  
 *Útoky na reflexi* přehrávají zprávy zpátky odesílateli, jako by byly získány z přijímače jako odpověď. Standardní zjišťování opětovného *přehrání* v mechanismu Windows Communication Foundation (WCF) ho automaticky nezpracovává.  
  
 Útoky na reflexi jsou ve výchozím nastavení omezeny, protože model služby WCF přidá ID podepsané zprávy pro vyžádání zprávy a očekává u `relates-to` zpráv s odpovědí podepsané záhlaví. V důsledku toho nelze zprávu požadavku přehrát jako odpověď. V zabezpečených scénářích spolehlivé zprávy (RM) jsou útoky na reflexi zmírňované z těchto důvodů:  
  
- Schémata zpráv odpovědi vytvořit sekvenci a vytvořit sekvenci se liší.  
  
- V případě simplexních sekvencí se zprávy sekvence, na které se klient pošle, nedá znovu přehrát, protože klient tyto zprávy nedokáže pochopit.  
  
- Pro duplexní sekvence musí být ID těchto dvou sekvencí jedinečné. Proto se zpráva o odchozí sekvenci nedá znovu přehrát jako příchozí zpráva sekvence (jsou také podepsané všechny hlavičky a texty sekvence).  
  
 Jediné vazby, které jsou náchylné k útokům na reflexi, jsou ty bez WS-Addressing: vlastní vazby, které mají zakázané WS-Addressing a používají zabezpečení založené na symetrických klíčích. <xref:System.ServiceModel.BasicHttpBinding>Nepoužívá výchozí adresování WS-Addressing, ale nepoužívá symetrické zabezpečení založené na klíčích tak, aby bylo možné ho pro tento útok zneužít.  
  
 Zmírnění pro vlastní vazby není vytvoření kontextu zabezpečení nebo vyžadování hlaviček WS-Addressing.  
  
## <a name="web-farm-attacker-replays-request-to-multiple-nodes"></a>Webová farma: útočník přehrává požadavek na více uzlů.  
 Klient používá službu, která je implementována ve webové farmě. Útočník znovu nahraje požadavek, který byl odeslán do jednoho uzlu ve farmě do jiného uzlu ve farmě. Navíc platí, že pokud se služba restartuje, mezipaměť pro přehrání se vyprázdní a umožní útočníkovi přehrání žádosti. (Mezipaměť obsahuje použité, dříve zobrazené hodnoty podpisu zprávy a brání opakovanému přehrání, aby se tyto podpisy mohly použít jenom jednou. Opakované přehrávání mezipamětí není v rámci webové farmy sdíleno.)  
  
 Zmírnění rizik zahrnuje:  
  
- Použijte zabezpečení režimu zpráv s tokeny kontextového kontextu zabezpečení (s povolenou nebo bez zabezpečené konverzace). Další informace najdete v tématu [Postup: vytvoření tokenu kontextu zabezpečení pro zabezpečenou relaci](how-to-create-a-security-context-token-for-a-secure-session.md).  
  
- Nakonfigurujte službu tak, aby používala zabezpečení na úrovni přenosu.  
  
## <a name="see-also"></a>Viz také

- [Otázky zabezpečení](security-considerations-in-wcf.md)
- [Zpřístupnění informací](information-disclosure.md)
- [Zvýšení oprávnění](elevation-of-privilege.md)
- [Útok DoS](denial-of-service.md)
- [Falšování](tampering.md)
- [Nepodporované scénáře](unsupported-scenarios.md)
