---
title: Architektura Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], architecture
- WCF [WCF], architecture
- architecture [WCF]
ms.assetid: a3bcb0a1-56ea-4ba6-9736-d260d90dade5
ms.openlocfilehash: f34a05a436dd021f0d1fcc05f3a12a058123acdc
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320837"
---
# <a name="windows-communication-foundation-architecture"></a>Architektura Windows Communication Foundation
Následující obrázek znázorňuje hlavní vrstvy architektury Windows Communication Foundation (WCF).  
  
## <a name="wcf-architecture"></a>Architektura WCF  
 (./media/wcf-architecture.gif "WCF_Architecture") ![architektury WCF]  
  
### <a name="contracts-and-descriptions"></a>Smlouvy a popisy  
 Smlouvy definují různé aspekty systému zpráv. Kontrakt dat popisuje všechny parametry, které tvoří každou zprávu, kterou může služba vytvořit nebo spotřebovat. Parametry zprávy jsou definovány dokumenty XSD (XML Schema Definition Language) a umožňují jakýmkoli systémům, které porozuměl XML ke zpracování dokumentů. Kontrakt zprávy definuje konkrétní části zprávy pomocí protokolů SOAP a umožňuje lepší kontrolu nad částmi zprávy, pokud interoperabilita takovou přesnost vyžaduje. Kontrakt služby určuje vlastní signatury metody služby a distribuuje se jako rozhraní v jednom z podporovaných programovacích jazyků, jako je Visual Basic nebo vizuál C#.  
  
 Zásady a vazby stanoví podmínky, které jsou nutné ke komunikaci se službou.  Vazba například musí (minimálně) určovat použitý přenos (například HTTP nebo TCP) a kódování. Zásady zahrnují požadavky na zabezpečení a další podmínky, které musí být splněny ke komunikaci se službou.  
  
### <a name="service-runtime"></a>Modul runtime služby  
 Vrstva runtime služby obsahuje chování, ke kterým dochází pouze během skutečné operace služby, tedy chování za běhu služby. Omezování řídí počet zpracovaných zpráv, což může být proměnlivé, pokud se poptávka po službě zvětší na přednastavený limit. Chování při chybě určuje, co se stane, když dojde k vnitřní chybě služby, například tím, že určíte, které informace se mají sdělit klientovi. (Příliš mnoho informací může uživateli se zlými úmysly poskytnout výhodu při připojení útoku.) Chování metadat určuje, jak a zda jsou metadata k dispozici vnějšímu světě. Chování instance Určuje, kolik instancí služby lze spustit (například typ singleton určuje pouze jednu instanci pro zpracování všech zpráv). Chování transakce umožňuje vrácení operací s podporou transakcí, pokud dojde k selhání. Chování při odeslání je ovládací prvek toho, jak je zpráva zpracována infrastrukturou WCF.  
  
 Rozšiřitelnost umožňuje přizpůsobení procesů modulu runtime. Například kontrola zprávy je zařízení pro kontrolu částí zprávy a filtrování parametrů umožňuje, aby probíhají přednastavené akce založené na filtrech pracujících v záhlavích zpráv.  
  
### <a name="messaging"></a>Messaging  
 Vrstva zasílání zpráv se skládá z *kanálů*. Kanál je komponenta, která zpracovává zprávu nějakým způsobem, například ověřením zprávy. Sada kanálů je také známá jako *zásobník kanálů*. Kanály pracují se zprávami a záhlavími zpráv. To se liší od vrstvy runtime služby, která se primárně zabývá zpracováním obsahu těla zprávy.  
  
 Existují dva typy kanálů: přenosové kanály a kanály protokolu.  
  
 Přenosové kanály čtou a zapisují zprávy ze sítě (nebo jiného komunikačního bodu s vnějším světem). Některé přenosy používají kodér k převodu zpráv (které jsou reprezentovány jako XML Infosets) do a z reprezentace bajtového datového proudu používaného sítí. Mezi kanály přenosů patří HTTP, Named Pipes, TCP a MSMQ. Příklady kódování jsou XML a optimalizované binární soubory.  
  
 Kanály protokolu implementují protokoly zpracování zpráv, často čtou nebo zapisují další záhlaví do zprávy. Mezi příklady takových protokolů patří WS-Security a WS-spolehlivost.  
  
 Vrstva zasílání zpráv znázorňuje možné formáty a způsoby výměny dat. WS-Security je implementace specifikace WS-Security, která umožňuje zabezpečení ve vrstvě zpráv. Kanál pro zasílání zpráv WS-Reliable umožňuje záruku doručování zpráv. Kodéry prezentují různá kódování, která se dají použít k potřebě zprávy. Kanál HTTP určuje, že se HyperTextový přenosový protokol používá pro doručování zpráv. Kanál TCP podobně určuje protokol TCP. Kanál toku transakce určuje vzory transakčních zpráv. Kanál pojmenovaného kanálu umožňuje komunikaci mezi procesy. Kanál služby MSMQ umožňuje práci s aplikacemi služby MSMQ.  
  
### <a name="hosting-and-activation"></a>Hostování a aktivace  
 V konečné podobě je služba programem. Podobně jako jiné programy musí být služba spuštěná ve spustitelném souboru. Tato služba se označuje jako *samoobslužná* služba.  
  
 Služby je také možné *hostovat*nebo spouštět ve spustitelném souboru spravovaném externím agentem, jako je služba IIS nebo aktivační služba systému Windows (WAS). BYLO povoleno automatické aktivace aplikací WCF při nasazení v počítači se systémem. Služby je také možné spustit ručně jako spustitelné soubory (soubory. exe). Službu lze také spustit automaticky jako službu systému Windows. Komponenty modelu COM+ je také možné hostovat jako služby WCF.  
  
## <a name="see-also"></a>Viz také:

- [Co je Windows Communication Foundation](whats-wcf.md)
- [Základní koncepty Windows Communication Foundation](fundamental-concepts.md)
