---
title: Omezení distribuce zpráv
ms.date: 03/30/2017
ms.assetid: 8b5ec4b8-1ce9-45ef-bb90-2c840456bcc1
ms.openlocfilehash: 188d7bd365caad7d4cd438744c78ae8e7cd95e7e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84586309"
---
# <a name="limiting-message-distribution"></a>Omezení distribuce zpráv

Rovnocenným kanálem je návrh sítě pro všesměrové vysílání. Základní model zahlcení zahrnuje distribuci každé zprávy odeslané jakýmkoli členem sítě do všech ostatních členů této sítě. To je ideální v situacích, kdy každá zpráva generovaná členem je relevantní a užitečná pro všechny ostatní členy (například chatovací místnosti). Mnohé aplikace ale mají příležitostnou nutnost omezit distribuci zpráv. Například pokud se nový člen připojí k síti a chce načíst poslední zprávu odeslanou prostřednictvím sítě, nemusí být tento požadavek zahlcený každým členem sítě. Požadavek může být omezen na okolí sousedů nebo mohou být vyfiltrovány místně generované zprávy. Zprávy je také možné odeslat do samostatného uzlu na síti. Toto téma popisuje použití čítače směrování, filtru šíření zpráv, místního filtru nebo přímého připojení k řízení toho, jak se zprávy předávají v celé síti, a poskytuje obecné pokyny pro výběr přístupu.

## <a name="hop-counts"></a>Počty segmentů

Koncept `PeerHopCount` je podobný hodnotě TTL (Time-to-Live), která se používá v protokolu IP. Hodnota `PeerHopCount` je svázána s instancí zprávy a určuje počet, kolikrát se má zpráva před vyřazením přesměrovat. Pokaždé, když klient rovnocenného kanálu obdrží zprávu, klient zprávu ověří a zjistí, jestli `PeerHopCount` je zadaná. Pokud je zadaný, pak klient sníží hodnotu počet směrování o jednu před předáním zprávy do sousedních uzlů. Když klient obdrží zprávu s hodnotou čítače směrování nula, klient zprávu zpracuje, ale nepředá zprávu sousedním sousedům.

Počet segmentů směrování lze přidat do zprávy přidáním `PeerHopCount` atributu do příslušné vlastnosti nebo pole v implementaci třídy zprávy. Před odesláním zprávy do sítě můžete nastavit konkrétní hodnotu. Tímto způsobem můžete použít počet segmentů k omezení distribuce zpráv v rámci sítě v případě potřeby, což může zabránit zbytečnému duplikaci zprávy. To je užitečné v případech, kdy síť obsahuje vysoké množství redundantních dat, nebo pro posílání zpráv bezprostředním sousedům nebo pro sousední sítě v několika segmentech směrování.

- Fragmenty kódu a související informace naleznete v tématu [atribut PeerHopCount: řízení distribuce zprávy](https://docs.microsoft.com/archive/blogs/peerchan/the-peerhopcount-attribute-controlling-message-distribution) na blogu rovnocenného kanálu.

## <a name="message-propagation-filter"></a>Filtr šíření zpráv

`MessagePropagationFilter`lze ji použít pro přizpůsobenou kontrolu zaplavování zpráv, zejména v případě, že obsah zprávy nebo jiné konkrétní scénáře určují šíření. Filtr provádí rozhodování o šíření každé zprávy, která projde uzlem. To platí pro zprávy, které pocházejí jinde v síti, kterou váš uzel přijal, i zprávy vytvořené vaší aplikací. Filtr má přístup ke zprávě i k jejímu původci, takže rozhodnutí o přeposílání nebo vyřazení zprávy můžou být založená na úplných dostupných informacích.

<xref:System.ServiceModel.PeerMessagePropagationFilter>je základní abstraktní třída s jednou funkcí, <xref:System.ServiceModel.PeerMessagePropagationFilter.ShouldMessagePropagate%2A> . První argument volání metody předává úplnou kopii zprávy. Jakékoli změny provedené ve zprávě nemají vliv na skutečnou zprávu. Poslední argument volání metody identifikuje původ zprávy ( `PeerMessageOrigination.Local` nebo `PeerMessageOrigination.Remote` ). Konkrétní implementace této metody musí vracet konstantu z <xref:System.ServiceModel.PeerMessagePropagation> výčtu, což značí, že zpráva má být předána do místní aplikace ( `Local` ), předaná vzdáleným klientům (), `Remote` (), `LocalAndRemote` nebo ani ani ( `None` ). Tento filtr lze použít přístupem k odpovídajícímu `PeerNode` objektu a určením instance třídy odvozeného filtru šíření ve `PeerNode.MessagePropagationFilter` Vlastnosti. Před otevřením rovnocenného kanálu zajistěte, aby byl filtr šíření připojen.

- Fragmenty kódu a související informace najdete na blogu s rovnocenným [kanálem a na MessagePropagationFilter](https://docs.microsoft.com/archive/blogs/peerchan/peer-channel-and-messagepropagationfilter) příspěvku na blogu s rovnocenným kanálem.

## <a name="contacting-an-individual-node-in-the-mesh"></a>Kontaktování jednotlivého uzlu v síti

Jednotlivé uzly v síti je možné kontaktovat nastavením místního filtru nebo nastavením přímého připojení.

Pokud mají uzly v síti jednotlivá ID, může být v implementaci vaší zprávy zadáno ID cíle. Místní filtr se dá nastavit tak, že v kontraktu zprávy napíšete funkci, která zobrazí zprávu jenom na aktuálním uzlu, pokud jeho ID odpovídá cílovému ID, které jste zadali. Síť přemění zprávu, takže režijní náklady na nastavení nového připojení nemusí být účtovány. Nicméně dojde ke ztrátě efektivity, protože zpráva je v celé síti posílána mnohokrát. To je vhodné pro posílání zpráv jednotlivým členům sítě, pokud zprávy nejsou příliš velké ani příliš časté.

Pro dlouhodobá připojení s vysokou šířkou pásma jsou vhodnější přímá připojení. Můžete odesílat informace o připojení přes síť a pak nastavit přímé připojení k vašemu výběru pro odesílání a příjem zpráv.

## <a name="choosing-an-approach-for-limiting-message-distribution"></a>Výběr přístupu k omezení distribuce zpráv

Když zjistíte situaci, kdy potřebujete omezit distribuci zpráv, položte si následující otázky:

- **Kdo** potřebuje zprávu přijmout? Jenom jeden sousední uzel? Uzel někam jinde v síti? Polovinu sítě?

- **Jak často** bude tato zpráva odeslána?

- Jaký druh **šířky pásma** bude tato zpráva používat?

Odpovědi na tyto otázky vám pomůžou určit, jestli se má použít počet segmentů směrování, filtr šíření zpráv, místní filtr nebo přímé připojení. Vezměte v úvahu následující obecné pokyny:

- **Kdo**

  - *Jednotlivý uzel*: místní filtr nebo přímé připojení.

  - *Okolí v rámci určitého okolí*: PeerHopCount.

  - *Složitá podmnožina sítě*: MessagePropagationFilter.

- **Jak často**

  - *Velmi časté*: přímé připojení, PeerHopCount, MessagePropagationFilter.

  - *Příležitostné*: místní filtr.

- **Využití šířky pásma**

  - *Vysoká*: přímé připojení, méně vhodné pro použití MessagePropagationFilter nebo místního filtru.

  - *Nízká*: jakékoli přímé připojení pravděpodobně není potřeba.

## <a name="see-also"></a>Viz také

- [Vytvoření aplikace protokolu Peer Channel](building-a-peer-channel-application.md)
