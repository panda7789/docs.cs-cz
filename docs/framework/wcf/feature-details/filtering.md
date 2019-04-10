---
title: Filtrování
ms.date: 03/30/2017
ms.assetid: 4002946c-e34a-4356-8cfb-e25912a4be63
ms.openlocfilehash: 667cc1cc95208c5c653ec4088d69ae105a2f8889
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59214595"
---
# <a name="filtering"></a>Filtrování
Windows Communication Foundation (WCF) filtrování systému můžete použít filtry deklarativní podle zpráv a provozní rozhodování. Filtry můžete použít k určení, co dělat, a zobrazí se zpráva prozkoumáním část zprávy. Proces řazení do fronty, například můžete použít k dotazu XPath 1.0 ke kontrole element priority známé hlavičky. Chcete-li zjistit, jestli se má přesunout na začátek fronty zprávu.  
  
 Filtrování systému se skládá z sadu tříd, které se dají efektivně zjistit sady filtrů `true` pro konkrétní zprávy WCF.  
  
 Filtrování systému je základní součástí zasílání zpráv WCF; je navržená velmi rychlá. Každá implementace filtru optimalizovaná pro určitý typ porovnání zpráv WCF.  
  
 Filtrování systém není bezpečné pro vlákna. Aplikace musí umět zpracovat všechny sémantiku uzamčení. Podporuje ale více čtečky, jeden zapisovače.  
  
## <a name="where-filtering-fits"></a>Kde filtrování vyhovuje  
 Filtrování se provádí po přijetí zprávy a je součástí procesu odeslání zprávy do komponenty příslušná aplikace. Návrh filtrovacího systému řeší požadavky na několik dílčích WCF, včetně zasílání zpráv, směrování, zabezpečení, zpracování událostí a správa systému.  
  
## <a name="filters"></a>Filtry  
 Modul filtr má dvě primární součásti, filtry a filtru tabulky. Filtr je logická rozhodnutí o zprávy na základě zadaného uživatelem logických podmínek. Implementace filtry <xref:System.ServiceModel.Dispatcher.MessageFilter> třídy.  
  
 <xref:System.ServiceModel.Dispatcher.MessageFilter.Match%2A> Metody se používají k určení, pokud zpráva splňuje filtru. Jednou z metod testuje záhlaví zprávy, ale nejde kontrolovat obsah zprávy. Tato metoda přebírá *vyrovnávací paměť zpráv* jako vstupní parametr a můžete si prohlédnout obsah zprávy.  
  
 Filtry nejsou testovány obvykle jednotlivě, ale v rámci filtru tabulky, která je obecná třída, která <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601.CreateFilterTable%2A> metoda vytvoří.  
  
 Několik druhů filtry jednotlivých se specializují na odpovídající na konkrétní typ logickou podmínku. Po vytvoření filtru, nebudete moct změnit kritéria, která používá filtr; Upravit kritéria filtrování, můžete vytvářet nové a odstranit existující filtr.  
  
### <a name="action-filters"></a>Filtry akcí  
 <xref:System.ServiceModel.Dispatcher.ActionMessageFilter> Obsahuje seznam řetězců akce. Pokud některé z akcí v seznamu filtru odpovídá záhlaví akce ve zprávě, nebo vyrovnávací paměť zpráv `Match` vrátí metoda `true`. Pokud je seznam prázdný, filtr je považován za odpovídá shoda – to všechno filtr a zpráva nebo zpráva vyrovnávací paměti a `Match` vrátí `true`. Pokud žádná akce v seznamu filtru odpovídá záhlaví akce ve zprávě, nebo vyrovnávací paměť zpráv `Match` vrátí `false`. Pokud není nic ve zprávě a filtru seznam je prázdný, pak `Match` vrátí `false`.  
  
### <a name="endpoint-address-filters"></a>Filtry adres koncového bodu  
 <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter> Filtrů zpráv a vyrovnávací paměti zpráv na základě adresy koncového bodu, reprezentovaný ve své kolekce hlaviček. Zprávy k předání tohoto filtru musí být splněny následující podmínky:  
  
-   Tento filtr adresa identifikátoru URI (Uniform Resource) musí být stejná jako ta, ve zprávě na záhlaví.  
  
-   Každý koncový bod parametr do pole adresy ve filtru (`address.Headers` kolekce) musí najít záhlaví ve zprávě k mapování na. Dodatečné hlavičky ve zprávě, nebo vyrovnávací paměť zpráv jsou přijatelné pro porovnání zůstanou `true`.  
  
### <a name="prefix-endpoint-address-filters"></a>Předpony adres filtrech koncového bodu  
  
1.  <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> Funguje stejně jako <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter> filtrovat, s tím rozdílem, že shody může být na předponě zprávy s identifikátorem URI. Například filtr určení adresy `http://www.adatum.com` odpovídá zprávy adresované do `http://www.adatum.com/userA`.  
  
### <a name="xpath-message-filters"></a>Filtry zpráv XPath  
 <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> Výraz XPath používá k určení, jestli dokument XML obsahuje konkrétní prvky, atributy, text nebo jiné XML syntaktické konstrukce. Tento filtr je optimalizována pro být velice efektivní pro striktní podmnožinou XPath. Jazyk XML Path je popsána v [W3C XML Path Language 1.0 – specifikace](https://go.microsoft.com/fwlink/?LinkId=94779).  
  
 Obvykle se používá aplikace <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> na koncový bod k dotazu na obsah zprávy protokolu SOAP a potom přijímá příslušnou akci na základě výsledků z dotazu. Proces řazení do fronty, například může použít dotaz XPath ke kontrole element priority známé hlavičky se rozhodnout, jestli se má přesunout na začátek fronty zprávu.  
  
## <a name="filter-tables"></a>Filtr tabulky  
 Filtr tabulky se používají k ukládání páry klíč hodnota, kde filtr je klíč a některé související data se hodnota. Filtrování dat slouží k označení jaká opatření je třeba provést v případě, že zpráva odpovídá filtru a typu dat filtru je obecný parametr pro tabulkovou třídu filtru. Filtrování dat můžou obsahovat pravidla směrování, zabezpečení stavu relace, moduly pro naslouchání na kanálu a tak dále. Kde je nezbytné řízení toku dat je možné data.  
  
 Filtr tabulky implementovat obecné rozhraní <xref:System.ServiceModel.Dispatcher.IMessageFilterTable%601>.  
  
 Filtr tabulky použít několik metod, které odpovídají zprávu pro všechny filtry v tabulce a vrátí kolekci Neseřazený odpovídající filtry nebo data. Některé metody shoda se více hodí a vrátí všechny odpovídající položky. Ostatní jsou jedním shoda, vrátí pouze jednu položku a výjimku <xref:System.ServiceModel.Dispatcher.MultipleFilterMatchesException> Pokud odpovídá více než jeden filtr.  
  
### <a name="message-filter-table"></a>Tabulka Filtr zpráv  
 <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> Je nejobecnější provádění <xref:System.ServiceModel.Dispatcher.IMessageFilterTable%601>. V tabulce můžete uložit filtry všech typů.  
  
 Číselné priority můžete přiřadit filtry, kde je nejvyšší prioritou označeny nejvyšší číslo. Více typů filtrů můžete mají stejnou prioritu. Konkrétní typ filtru se může zobrazit ve více než jednu úroveň priority.  
  
 Porovnávání se provádí jednou shodu filtry a spouští se s nejvyšší prioritou se nacházejí s uvedenou prioritou, jsou zkoumány žádné filtry s nižší prioritou. Proto pokud jste pomocí filtru jedním shodovat s metodou, více než jeden filtr hledá shodu ve zprávě, ale každý odpovídající filtr má jinou prioritu, není vyvolána žádná výjimka a vrátil filtr s nejvyšší prioritou. Podobně filtr více odpovídají metoda vrátí pouze odpovídající filtrům s nejvyšší prioritou.  
  
### <a name="xpath-message-filter-table"></a>Tabulka filtr XPath zpráv  
 <xref:System.ServiceModel.Dispatcher.XPathMessageFilterTable%601> Je optimalizovaná pro deklarativní filtrů XPath, je klíče tabulky <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.  
  
 <xref:System.ServiceModel.Dispatcher.XPathMessageFilterTable%601> Třídy optimalizuje odpovídající pro podmnožinu XPath, které zabírá většinu scénářů zasílání zpráv a také podporuje úplné gramatiky XPath 1.0. Optimalizovala algoritmy pro efektivní paralelní párování.  
  
 Tato tabulka obsahuje několik specializovaných `Match` metody, které se spustí <xref:System.Xml.XPath.XPathNavigator> a <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator>. A <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator> rozšiřuje <xref:System.Xml.XPath.XPathNavigator> třídy tak, že přidáte <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator.CurrentPosition%2A> vlastnost. Tato vlastnost umožňuje pozice v rámci dokument XML k uložení a načtení rychle bez nutnosti klonovat Navigátor náročné přidělení paměti, která <xref:System.Xml.XPath.XPathNavigator> vyžaduje pro tyto operace. Modul WCF XPath musí často zaznamenat pozici kurzoru v průběhu provádění dotazů v dokumentech XML, takže <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator> poskytuje důležité aktualizace pro zpracování zpráv.  
  
## <a name="customer-scenarios"></a>Situace zákazníka  
 Můžete použít filtrování kdykoli chcete odeslat zprávu do jiné zpracování moduly v závislosti na data obsažená ve zprávě. Dva typické scénáře jsou směrování zprávy na základě svých akcí kódu a zrušení multiplexing datový proud zpráv na základě adresy koncového bodu zpráv.  
  
### <a name="routing"></a>Směrování  
 Naslouchací proces koncového bodu čeká na zprávy, které mají jednu nebo více akcí kódy v hlavičce protokolu SOAP zprávy. Tato implementace tak, že vytvoříte <xref:System.ServiceModel.Dispatcher.ActionMessageFilter> předáním pole, která obsahuje kódy akce konstruktoru. Tento filtr používá k registraci ve službě `ListenerFactory`, takže pouze zprávy, jejichž akce odpovídá některé z nich ve filtru do tohoto konkrétního koncového bodu.  
  
### <a name="de-multiplexing"></a>Multiplexingu rušit  
 Když více koncových bodů škálovatelnou ze stejné `ServiceListener` vypnutí přenosu, je jediný způsob, jak zrušit multiplexovaný zprávy a vědět, jestli patří do určité adresa koncového bodu, použít <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter>s, která je vybrat zprávy směrem k registrované koncové body podle provádění vyhledávání na informace uložené v záhlaví. Tyto filtry mají pouze zprávy, které předávají všechny potřebné hlavičky, které odpovídají jak:  
  
-   V identifikátoru URI `EndpointAddress`.  
  
-   Zbytek parametrů koncový bod v `EndpointAddress` podle <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter>.  
  
## <a name="see-also"></a>Viz také:

- [Přenos a serializace dat](../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)
