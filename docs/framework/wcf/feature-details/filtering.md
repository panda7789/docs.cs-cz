---
title: "Filtrování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4002946c-e34a-4356-8cfb-e25912a4be63
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4a5b2c78ef7e675a656caf00e9d0ba0c9eb0630b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="filtering"></a>Filtrování
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Filtrování systému pomocí deklarativní filtrů odpovídající zprávy a provozní rozhodnutí. Filtry můžete použít k určení toho, co dělat s zpráva prověřením část zprávy. Proces řazení do fronty, například můžete použít dotaz XPath 1.0 Zkontrolujte priority element známé hlavičky k určení, zda chcete zprávu přesunout na začátek fronty.  
  
 Filtrování systém se skládá z sadu tříd, které můžete efektivně určete, které sady filtrů jsou `true` pro konkrétní [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zprávy.  
  
 Filtrování systém je základní součástí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zasílání zpráv; je navržen pro fungoval velmi rychle. Každá implementace filtru optimalizovaná pro určitý typ porovnání [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zprávy.  
  
 Filtrování systém není bezpečné pro přístup z více vláken. Aplikace musí zpracovat žádné uzamčení sémantiku. Podporuje však více čtečky, jeden zapisovače.  
  
## <a name="where-filtering-fits"></a>Kde vyhovuje filtrování  
 Filtrování se provádí po zprávu přijme a je součástí procesu odeslání zprávy do součásti příslušná aplikace. Návrh filtrování systému řeší požadavky na několik [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] subsystémy, včetně zasílání zpráv, směrování, zabezpečení, zpracování událostí a správa systému.  
  
## <a name="filters"></a>Filtry  
 Modul filtr má dvě primární součásti, filtrů a filtru tabulky. Filtr Boolean rozhoduje o zprávu na základě zadaného uživatelem logických podmínek. Filtry implementovat <xref:System.ServiceModel.Dispatcher.MessageFilter> třídy.  
  
 <xref:System.ServiceModel.Dispatcher.MessageFilter.Match%2A> Metody se používají k určení, pokud zpráva splňuje filtru. Jednu z metod testy záhlaví zprávy, ale nemůže zkontrolovat obsah zprávy. Jiná metoda má *vyrovnávací paměti zpráv* jako vstupní parametr a můžete zkontrolovat obsah zprávy.  
  
 Filtry nejsou testovány obvykle jednotlivě, ale v rámci filtru tabulky, který je obecný třídy, která <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601.CreateFilterTable%2A> metoda vytvoří.  
  
 Několik druhů filtry každý se specializují na odpovídající na konkrétní typ Boolean podmínku. Jakmile vytvoříte filtr, nelze změnit kritéria, která používá filtr; Chcete-li upravit kritéria filtrování, vytvořit nový a odstranit existující filtru.  
  
### <a name="action-filters"></a>Filtry akcí  
 <xref:System.ServiceModel.Dispatcher.ActionMessageFilter> Obsahuje seznam řetězců akce. Pokud některou z akcí v seznamu filtru odpovídá hlavičku akce ve zprávě, nebo vyrovnávací paměti zpráv, `Match` metoda vrátí `true`. Pokud je seznam prázdný, filtr považuje za odpovídá všechny shody filtru a všechny zpráva nebo zpráva vyrovnávací paměť a `Match` vrátí `true`. Pokud žádná akce v seznamu filtru odpovídá záhlaví akce v zpráva nebo zpráva vyrovnávací paměť, `Match` vrátí `false`. Pokud není žádná akce ve zprávě a jeho seznam je prázdný, pak `Match` vrátí `false`.  
  
### <a name="endpoint-address-filters"></a>Filtry adres koncový bod  
 <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter> Filtry zpráv a vyrovnávacích pamětí zpráv podle adresy koncového bodu, reprezentovaný v jejich kolekci hlaviček. Zprávy k předání takové filtru musí být splněny následující podmínky:  
  
-   Adresa se filtr identifikátor URI (Uniform Resource) musí být stejná jako v zprávu, která se záhlaví.  
  
-   Každý koncový bod parametr v adrese filtru (`address.Headers` kolekce) ve zprávě k mapování na musí najít hlavičku. Další hlavičky ve zprávě, nebo vyrovnávací paměti zpráv jsou přijatelné pro shodu zůstat `true`.  
  
### <a name="prefix-endpoint-address-filters"></a>Předpony filtry adres koncový bod  
  
1.  <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> Funguje stejně jako <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter> filtrovat, s tím rozdílem, že shody může být na předponě zprávy identifikátor URI. Například filtr zadání http://www.adatum.com adresa odpovídá zprávy adresované do http://www.adatum.com/userA.  
  
### <a name="xpath-message-filters"></a>Filtry zpráv XPath  
 <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> Používá k určení, zda dokument XML obsahuje konkrétní prvky, atributy, text nebo jiné XML syntaktické konstrukce výraz XPath. Filtr je optimalizovaná tak, aby se velmi efektivní pro podmnožinu XPath strict. XML Path Language je podrobněji popsaná [W3C XML Path Language 1.0 – specifikace](http://go.microsoft.com/fwlink/?LinkId=94779).  
  
 Obvykle se aplikace používá <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> v dotazu na obsah a zprávu protokolu SOAP a trvá koncového bodu příslušné akce na základě výsledků tohoto dotazu. Proces řazení do fronty, například může použít dotaz XPath kontrola element s prioritou známé hlavičky můžete rozhodnout, jestli chcete zprávu přesunout na začátek fronty.  
  
## <a name="filter-tables"></a>Filtr tabulky  
 Filtr tabulky se používají k ukládání páry klíč hodnota, kde filtr je klíč a některé přidružená data je hodnota. Filtrování dat slouží k akcí mají přijmout v případě zprávu odpovídá filtru a typu dat filtru je obecný parametr pro třídu filtru tabulky. Filtrování dat může skládat z pravidel směrování, zabezpečení stav relace, moduly pro naslouchání na kanál a tak dále. Data lze použít, pokud řízení toku dat je nezbytné.  
  
 Filtr tabulky implementovat obecné rozhraní <xref:System.ServiceModel.Dispatcher.IMessageFilterTable%601>.  
  
 Filtr tabulky obsahovat několik metod, které odpovídají zprávy všechny filtry, které jsou v tabulce a vrátí kolekci neuspořádaný odpovídající filtry nebo data. Některé metody shoda se několika match a vrátí všechny odpovídající položky. Ostatní jsou jedním match, vrácení pouze jedinou položku a výjimku <xref:System.ServiceModel.Dispatcher.MultipleFilterMatchesException> Pokud odpovídá více než jeden filtr.  
  
### <a name="message-filter-table"></a>Tabulku filtru zpráv  
 <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601> Je nejobecnější implementace <xref:System.ServiceModel.Dispatcher.IMessageFilterTable%601>. V tabulce můžete uložit filtry všechny typy.  
  
 Číselné priority lze přiřadit filtry, které jsou označeny nejvyšší prioritou číslem nejvyšší číslo. Více typů filtrů, může mít stejnou prioritu. Konkrétní typ filtru se může zobrazit ve více než jednu úroveň priority.  
  
 Odpovídající Probíhá spuštění s nejvyšší prioritou a jednou odpovídající filtrům nebyly nalezeny s uvedenou prioritou, se zkontrolují žádné filtry s nižší prioritou. Proto pokud jste pomocí filtru jedním shodovat s metodou, odpovídá více než jeden filtr zprávu, ale každý odpovídající filtr má jinou prioritu, nedojde k výjimce a je vrácen filtr s nejvyšší prioritou. Podobně filtrem více odpovídat metoda vrátí pouze ty odpovídající filtrům s nejvyšší prioritou.  
  
### <a name="xpath-message-filter-table"></a>Tabulky filtr XPath zpráv  
 <xref:System.ServiceModel.Dispatcher.XPathMessageFilterTable%601> Je optimalizovaná pro deklarativní XPath filtry, takže je klíč tabulky <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>.  
  
 <xref:System.ServiceModel.Dispatcher.XPathMessageFilterTable%601> Třída optimalizuje odpovídající pro podmnožinu XPath, který obsahuje většinu scénáře zasílání zpráv a také podporuje úplné gramatika XPath 1.0. Ho optimalizovala algoritmy pro efektivní paralelní párování.  
  
 Tato tabulka obsahuje některé speciální `Match` metody, které provozují přes <xref:System.Xml.XPath.XPathNavigator> a <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator>. A <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator> rozšiřuje <xref:System.Xml.XPath.XPathNavigator> třída přidáním <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator.CurrentPosition%2A> vlastnost. Tato vlastnost umožňuje pozice v dokumentu XML, který má uložit a načíst rychle bez nutnosti klonovat navigátoru přidělení nákladné paměti, <xref:System.Xml.XPath.XPathNavigator> vyžaduje pro takovou operaci. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] XPath modul musí často záznam pozice kurzoru v průběhu zpracování dotazů na dokumenty XML, proto <xref:System.ServiceModel.Dispatcher.SeekableXPathNavigator> poskytuje důležité optimalizace pro zpracování zprávy.  
  
## <a name="customer-scenarios"></a>Scénáře zákazníka  
 Pomocí filtrování kdykoli chcete odeslat zprávu do různých zpracování moduly v závislosti na data obsažená ve zprávě. Dva typické scénáře jsou směrování zpráv na základě jeho akce kódu a zrušte multiplexní datového proudu zpráv na základě zprávy na koncový bod adresy.  
  
### <a name="routing"></a>Směrování  
 Naslouchací proces koncový bod čeká na zprávy, které mají jeden nebo více kódů akce v hlavičce protokolu SOAP zprávy. Tato implementace vytvořením <xref:System.ServiceModel.Dispatcher.ActionMessageFilter> předáním pole, které obsahuje kódy akce jeho konstruktoru. Pro registraci se použije tento filtr `ListenerFactory`, proto pouze zprávy, jejichž akce odpovídá jednomu z těch, které ve filtru do daného koncového bodu.  
  
### <a name="de-multiplexing"></a>Zrušte multiplexní  
 Když se víc koncových bodů ventilátor ze stejné `ServiceListener` vypnout sítě, je jediným způsobem, jak zrušte multiplexovaný zprávy a vědět, jestli patří do určité adresa koncového bodu, použít <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter>s, který vyberte zprávy směrem k registrované koncové body pomocí provádění vyhledávání na informace uložené v hlavičkách chybí. Tyto filtry pouze zprávy, které předávají mít všechny potřebné hlavičky, které odpovídají na obě:  
  
-   Identifikátor URI v `EndpointAddress`.  
  
-   Zbytek parametrů koncového bodu v `EndpointAddress` uvedené v <xref:System.ServiceModel.Dispatcher.EndpointAddressMessageFilter>.  
  
## <a name="see-also"></a>Viz také  
 [Přenos a serializace dat](../../../../docs/framework/wcf/feature-details/data-transfer-and-serialization.md)
