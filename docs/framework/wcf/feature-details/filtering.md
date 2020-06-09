---
title: Filtrování
ms.date: 03/30/2017
ms.assetid: 4002946c-e34a-4356-8cfb-e25912a4be63
ms.openlocfilehash: d04141e4720320784bc92c332a3f0b96a7b1ac92
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595463"
---
# <a name="filtering"></a>Filtrování
Systém pro filtrování Windows Communication Foundation (WCF) může použít deklarativní filtry k porovnávání zpráv a provádění provozních rozhodnutí. Filtry můžete použít k určení toho, co se má udělat se zprávou, a to zkoumáním části zprávy. Proces řazení do fronty může například použít dotaz XPath 1,0 ke kontrole prvku priority známé hlavičky k určení, zda má být zpráva přesunuta do před frontou.  
  
 Systém filtrování se skládá ze sady tříd, které mohou efektivně určit, která sada filtrů je určena `true` pro konkrétní zprávu WCF.  
  
 Systém filtrování je základní součástí zasílání zpráv WCF; je navržený tak, aby byl velmi rychlý. Každá implementace filtru je optimalizovaná pro konkrétní druh porovnání se zprávami WCF.  
  
 Systém filtrování není bezpečný pro přístup z více vláken. Aplikace musí zpracovat jakoukoli sémantiku uzamykání. Podporuje ale více čtenářů, jeden zapisovač.  
  
## <a name="where-filtering-fits"></a>Kam se vejde filtrování  
 Filtrování je provedeno po přijetí zprávy a je součástí procesu odeslání zprávy do správné součásti aplikace. Návrh systému filtrování řeší požadavky několika subsystémů WCF, včetně zasílání zpráv, směrování, zabezpečení, zpracování událostí a správu systému.  
  
## <a name="filters"></a>Filtry  
 Modul filtru má dvě primární komponenty, filtry a tabulky filtru. Filtr provádí logická rozhodnutí týkající se zprávy na základě logických podmínek zadaných uživatelem. Filtry implementují <xref:System.ServiceModel.Dispatcher.MessageFilter> třídu.  
  
 <xref:System.ServiceModel.Dispatcher.MessageFilter.Match%2A>Metody slouží k určení, zda zpráva splňuje filtr. Jedna z metod testuje hlavičku zprávy, ale nemůže zkontrolovat tělo zprávy. Druhá metoda přebírá *vyrovnávací paměť zpráv* jako vstupní parametr a může kontrolovat tělo zprávy.  
  
 Filtry nejsou obvykle testovány jednotlivě, ale jako součást tabulky filtru, což je obecná třída, kterou <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601.CreateFilterTable%2A> Metoda vytvoří.  
  
 Několik druhů filtrů každý specializuje v porovnání s konkrétním druhem logické podmínky. Po vytvoření filtru nemůžete změnit kritéria, která filtr používá; Chcete-li upravit kritéria filtru, vytvořte nové a odstraňte existující filtr.  
  
### <a name="action-filters"></a>Filtry akcí  
 <xref:System.ServiceModel.Dispatcher.ActionMessageFilter>Obsahuje seznam řetězců akcí. Pokud některá z akcí v seznamu filtru odpovídá záhlaví akce ve zprávě nebo ve vyrovnávací paměti zpráv, `Match` metoda se vrátí `true` . Pokud je seznam prázdný, filtr se považuje za odpovídající filtr a všechny zprávy nebo vyrovnávací paměti zpráv a `Match` vrátí hodnotu `true` . Pokud žádná z akcí v seznamu filtru nesouhlasí s hlavičkou akce ve zprávě nebo ve vyrovnávací paměti zpráv, `Match` vrátí `false` . Pokud zpráva neobsahuje žádnou akci a seznam filtru není prázdný, `Match` vrátí `false` .  
  
### <a name="endpoint-address-filters"></a>Filtry adresy koncového bodu  
 <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter>Filtruje zprávy a vyrovnávací paměti zpráv na základě adresy koncového bodu, jak je znázorněno v kolekci hlaviček. Aby zpráva vyhověla takovému filtru, musí být splněny následující podmínky:  
  
- Adresa filtru identifikátor URI (Uniform Resource Identifier) musí být stejná jako ta ve zprávě pro záhlaví.  
  
- Každý parametr koncového bodu v adrese filtru ( `address.Headers` kolekce) musí ve zprávě, která má být namapována, najít hlavičku. Další hlavičky ve zprávě nebo vyrovnávací paměti zpráv jsou přijatelné pro zachování shody `true` .  
  
### <a name="prefix-endpoint-address-filters"></a>Prefixovat filtry adresy koncových bodů  
  
1. <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter>Funguje stejně jako <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter> filtr, s tím rozdílem, že shoda může být na PŘEDPONu identifikátoru URI zprávy. Například filtr určující adresu `http://www.adatum.com` odpovídá zprávám, které jsou adresovány `http://www.adatum.com/userA` .  
  
### <a name="xpath-message-filters"></a>Filtry zpráv XPath  
 <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>Pomocí výrazu XPath určíte, zda dokument XML obsahuje konkrétní prvky, atributy, text nebo jiné syntaktické konstruktory XML. Filtr je optimalizován tak, aby byl extrémně efektivní pro striktní podmnožinu XPath. Jazyk XML Path je popsaný ve [specifikaci W3C XML Path jazyka 1,0](https://www.w3.org/TR/xpath/all/).  
  
 Aplikace obvykle používá u <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> koncového bodu dotaz na obsah zprávy SOAP a provede příslušnou akci na základě výsledků tohoto dotazu. Proces řazení do fronty může například použít dotaz XPath ke kontrole prvku priority známé hlavičky k rozhodnutí, zda má být zpráva přesunuta na frontu.  
  
## <a name="filter-tables"></a>Filtrovat tabulky  
 Tabulky filtrů se používají k uložení párů klíč-hodnota, kde filtr je klíč a některá přidružená data jsou hodnota. Data filtru lze použít k určení akcí, které mají být použity, pokud zpráva odpovídá filtru a typ dat filtru je obecný parametr pro třídu Table Filter. Data filtru se můžou skládat z pravidel směrování, stavu zabezpečení relace, naslouchacího procesu na kanálu atd. Data se dají použít tam, kde je potřeba řízení toku dat.  
  
 Filtry tabulky implementují obecné rozhraní <xref:System.ServiceModel.Dispatcher.IMessageFilterTable%601> .  
  
 Tabulky filtrů mají několik metod, které odpovídají zprávě proti všem filtrům v tabulce a vracejí neuspořádanou kolekci odpovídajících filtrů nebo dat. Některé metody shody jsou vícenásobné a vracejí všechny odpovídající položky. Jiné se shodují s jednou shodou, vrací jenom jednu položku a vyvolají, <xref:System.ServiceModel.Dispatcher.MultipleFilterMatchesException> Pokud se shoduje více než jeden filtr.  
  
### <a name="message-filter-table"></a>Tabulka filtru zpráv  
 <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601>Je nejobecnější implementace <xref:System.ServiceModel.Dispatcher.IMessageFilterTable%601> . Můžete ukládat filtry všech typů v tabulce.  
  
 Můžete přiřadit číselné priority filtrům, u kterých je nejvyšší priorita vynásobena nejvyšším číslem. U více typů filtrů může být stejná priorita. Určitý typ filtru se může objevit ve více než jedné úrovni priority.  
  
 Porovnání je provedeno od nejvyšší priority a jakmile budou nalezeny vyhovující filtry s danou prioritou, nebudou zkontrolovány žádné filtry s nižšími prioritami. Proto pokud používáte metodu shody s jedním filtrem a více než jeden filtr odpovídá zprávě, ale každý odpovídající filtr má jinou prioritu, pak není vyvolána žádná výjimka a bude vrácen filtr s nejvyšší prioritou. Podobně metoda shody s vícenásobným filtrováním vrátí pouze ty odpovídající filtry s nejvyšší prioritou.  
  
### <a name="xpath-message-filter-table"></a>Tabulka filtru zpráv XPath  
 <xref:System.ServiceModel.Dispatcher.XPathMessageFilterTable%601>Je optimalizován pro deklarativní filtry XPath, takže klíč tabulky je <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> .  
  
 <xref:System.ServiceModel.Dispatcher.XPathMessageFilterTable%601>Třída optimalizuje porovnání pro podmnožinu XPath, která pokrývá většinu scénářů zasílání zpráv a také podporuje úplnou gramatiku xpath 1,0. Má optimalizované algoritmy pro efektivní paralelní porovnání.  
  
 Tato tabulka obsahuje několik specializovaných `Match` metod, které pracují s <xref:System.Xml.XPath.XPathNavigator> a <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator> . <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator>Rozšiřuje <xref:System.Xml.XPath.XPathNavigator> třídu přidáním <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator.CurrentPosition%2A> Vlastnosti. Tato vlastnost umožňuje, aby byly pozice v rámci dokumentu XML uloženy a načítány rychle bez nutnosti klonování navigátoru, což je náročné přidělení paměti, které <xref:System.Xml.XPath.XPathNavigator> vyžaduje taková operace. Modul XPath WCF musí často zaznamenávat pozici kurzoru v průběhu provádění dotazů na dokumentech XML, takže <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator> poskytuje důležitou optimalizaci pro zpracování zpráv.  
  
## <a name="customer-scenarios"></a>Scénáře zákazníků  
 Filtrování můžete použít kdykoli, když chcete poslat zprávu do různých modulů zpracování v závislosti na datech obsažených ve zprávě. Dvěma typickými scénáři je směrování zprávy na základě kódu akce a demultiplexování datového proudu zpráv na základě adresy koncového bodu zprávy.  
  
### <a name="routing"></a>Směrování  
 Naslouchací proces koncového bodu naslouchá zprávám, které mají jeden nebo více kódů akcí v hlavičce protokolu SOAP zprávy. Implementujete to vytvořením <xref:System.ServiceModel.Dispatcher.ActionMessageFilter> pole, které obsahuje kódy akcí pro svůj konstruktor. Používá tento filtr k registraci v `ListenerFactory` , takže pouze zprávy, jejichž akce odpovídá jednomu z těch, které jsou ve filtru, získají do tohoto konkrétního koncového bodu.  
  
### <a name="de-multiplexing"></a>Zrušení multiplexování  
 Když se více koncových bodů dostanou od stejného typu `ServiceListener` , jediným způsobem pro zprávy o tom, že patří do určité adresy koncového bodu, je použití <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter> s, které vybere zprávy do registrovaných koncových bodů pomocí vyhledávání informací uložených v hlavičkách. V těchto filtrech obsahují pouze ty zprávy, které přecházejí z nezbytných hlaviček, které odpovídají oběma:  
  
- Identifikátor URI v `EndpointAddress` .  
  
- Zbytek parametrů koncového bodu v, `EndpointAddress` jak je uvedeno v <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter> .  
  
## <a name="see-also"></a>Viz také

- [Přenos a serializace dat](data-transfer-and-serialization.md)
