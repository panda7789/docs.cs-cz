---
title: Omezení distribuce zpráv
ms.date: 03/30/2017
ms.assetid: 8b5ec4b8-1ce9-45ef-bb90-2c840456bcc1
ms.openlocfilehash: d09a2be4a59a08a4bddbb1e0f4d038cd2c5ff3e2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59130218"
---
# <a name="limiting-message-distribution"></a>Omezení distribuce zpráv
Rovnocenný kanál chování je záměrné všesměrového vysílání sítě. Svůj základní flooding model zahrnuje distribuce odeslaná službou členem sítě u všech členů této sítě. To je ideální v situacích, kde každé zprávy vygenerované metodou člen je důležité a užitečné pro všechny ostatní členy (například chatovací místnosti). Mnoho aplikací však mít občasné potřebu omezení distribuce zpráv. Například pokud se nový člen připojí sítě a chce, aby se k načtení poslední zprávou odeslanou přes síť, tento požadavek nemusí být zahlcenou pro každého člena síť. Požadavek může být omezena na téměř okolí nebo můžete místně vygenerovanou zprávy odfiltrovány. Zprávy mohou rovněž odeslány do jednotlivých uzlů na síť. Toto téma popisuje použití počet směrování, filtr šíření zpráv, filtr místní nebo přímé připojení k řízení, jak se předávají zprávy v průběhu síť a obsahuje obecné pokyny pro výběr přístupu.  
  
## <a name="hop-counts"></a>Počet segmentů směrování  
 Koncept `PeerHopCount` je podobný TTL (Time-To-Live) používá v protokolu IP. Hodnota `PeerHopCount` se váže na instanci zprávy a určuje, kolikrát se mají předávat zprávy před probíhá vyřazování. Pokaždé, když je přijata zpráva rovnocenným kanálem klientem, klient zkontroluje zprávy a zjistěte, jestli `PeerHopCount` je zadán. Pokud je zadán, pak dekrementuje klienta ke směrování hodnota počtu jednou před předávání zpráv do sousedních uzlů. Když klient obdrží zprávu s nulovou hodnotu počet segmentů směrování, klient se zpracovává zprávy, ale okolí nepředává zprávy.  
  
 Počet segmentů směrování může přidat do zprávy tak, že přidáte `PeerHopCount` jako atribut, který má použít vlastnost nebo pole v implementaci třídy zpráv. To můžete nastavit na určitou hodnotu před odesláním zprávy na síť. Tímto způsobem můžete použít segmenty směrování pro omezení distribuce zpráv v rámci sítě, pokud je to nezbytné, potenciálně vyhnout duplikaci nepotřebné zprávy. To je užitečné v případech, kde síť obsahuje vysoké množství redundantních dat nebo pro posílání zprávy k okamžité okolí, protokolu BGP nebo Sousedé v rámci několik segmentů směrování.  
  
-   Fragmenty kódu a související informace najdete v tématu [rovnocenného kanálu blogu](https://go.microsoft.com/fwlink/?LinkID=114531).  
  
## <a name="message-propagation-filter"></a>Filtr šíření zpráv  
 `MessagePropagationFilter` můžete použít pro vlastní ovládací prvek zaplavení zprávy, zejména v případě, že obsah zprávy nebo jiných konkrétních scénářů určit šíření. Lze díky filtru šíření rozhodnutí, která pro každou zprávu, která prochází uzlu. To platí pro zprávy, které pochází jinde v mřížce, že váš uzel byl přijat a zprávy vytvořené v aplikaci. Filtr má přístup k zprávu a jeho vzniku tak rozhodnutí o předávání nebo vyřazuje zprávy může být založen na úplné informace, které jsou k dispozici.  
  
 <xref:System.ServiceModel.PeerMessagePropagationFilter> je abstraktní základní třída s jedinou funkci <xref:System.ServiceModel.PeerMessagePropagationFilter.ShouldMessagePropagate%2A>. Prvním argumentem funkce volání metody předá úplnou kopii zprávy. Všechny změny provedené zprávy nemají vliv na skutečné zprávy. Poslední argument volání metody, které identifikuje původní zprávu (`PeerMessageOrigination.Local` nebo `PeerMessageOrigination.Remote`). Konkrétní implementace této metody musí vracet konstantu z <xref:System.ServiceModel.PeerMessagePropagation> výčet označující, že je zpráva předávány na místní aplikaci (`Local`), předané ke vzdáleným klientům (`Remote`), obě (`LocalAndRemote`), nebo ani jedna (`None`). Tento filtr lze použít díky přístupu do odpovídajícího `PeerNode` objektů a určení instance odvozené šíření třída v filter `PeerNode.MessagePropagationFilter` vlastnost. Zkontrolujte, zda je před otevřením protokolu Peer Channel připojen šíření filtru.  
  
-   Fragmenty kódu a související informace najdete v tématu [rovnocenného kanálu blogu](https://go.microsoft.com/fwlink/?LinkID=114532).  
  
## <a name="contacting-an-individual-node-in-the-mesh"></a>Kontaktování jednotlivých uzlů v síť  
 Jednotlivých uzlů v sítě lze kontaktovat, nastavením místní filtr nebo nastavením přímé připojení.  
  
 Pokud uzly v síti každý jednotlivých ID, a cílové ID můžete zadanou v implementaci zprávy. Místní filtr můžete nastavit pomocí funkce váš kontraktu zprávy, které budou zobrazovat jenom zprávy pro aktuální uzel pokud jeho ID odpovídá vámi zadané ID cílové. Síť přenáší zprávy, tak nároky na nastavení nového připojení nemusí být účtovány poplatky. Však dojde ke ztrátě účinnosti vzhledem k tomu, že je zpráva odeslána v mnoha případech v rámci síť. Tento postup funguje dobře pro odesílání zpráv do jednotlivých členů sítě, za předpokladu, zprávy jsou příliš velké objemy ani moc často.  
  
 U dlouhodobých a velkou šířkou pásma připojení je vhodnější přímé připojení. Můžete odeslat informace o připojení přes síť a pak nastavit přímé připojení podle vašeho výběru pro odesílání a příjem zpráv.  
  
## <a name="choosing-an-approach-for-limiting-message-distribution"></a>Výběr přístupu pro omezení distribuce zpráv  
 Po zjištění scénář, ve které budete potřebovat k omezení distribuce zpráv, položte si následující otázky:  
  
-   **Kdo** potřebuje zpráva? Sousední pouze jeden uzel? Uzel někde jinde v síť? Poloviční síť?  
  
-   **Jak často** tato zpráva přijde?  
  
-   Jaký typ z **šířky pásma** použije tuto zprávu?  
  
 Odpovědi na tyto otázky vám umožňují určit, jestli se má použít počet směrování, filtr šíření zpráv, filtr místní nebo přímé připojení. Vezměte v úvahu následující obecné pokyny:  
  
-   **Kdo**  
  
    -   *Jednotlivých uzlů*:  Filtr místní nebo přímé připojení.  
  
    -   *Sousední v rámci určité okolí*:  PeerHopCount.  
  
    -   *Komplexní podmnožinou síť*:  MessagePropagationFilter.  
  
-   **Jak často**  
  
    -   *Velmi často*:  Direct connection, PeerHopCount, MessagePropagationFilter.  
  
    -   *Příležitostné*:  Místní filtr.  
  
-   **Využití šířky pásma**  
  
    -   *Vysoká*:  Přímé připojení, méně vhodné použít Třída MessagePropagationFilter nebo místní filtr.  
  
    -   *Nízká*:  Pravděpodobně nejsou potřeba žádné, přímé připojení.  
  
## <a name="see-also"></a>Viz také:

- [Vytvoření aplikace rovnocenného kanálu](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
