---
title: Architektura Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], architecture
- WCF [WCF], architecture
- architecture [WCF]
ms.assetid: a3bcb0a1-56ea-4ba6-9736-d260d90dade5
ms.openlocfilehash: 1514010ca573be364e54a53ae047a2ff49cdad82
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="windows-communication-foundation-architecture"></a>Architektura Windows Communication Foundation
Následující obrázek znázorňuje hlavní vrstvy architektury Windows Communication Foundation (WCF).  
  
## <a name="wcf-architecture"></a>Architektura WCF  
 ![Architektura WCF](../../../docs/framework/wcf/media/wcf-architecture.gif "WCF_Architecture")  
  
### <a name="contracts-and-descriptions"></a>Kontrakty a popisy  
 Kontrakty definovat různé aspekty systému zpráva. Kontrakt dat popisuje každý parametr, který tvoří každou zprávu, která můžete vytvořit nebo využívat službu. Parametry zprávy jsou definovány schématu XML definice jazyka (XSD) dokumenty, povolení všechny systémy, které jste srozuměni s tím ke zpracování dokumentů XML. Kontrakt zprávy definuje části konkrétní zprávu pomocí protokolu SOAP protokolů a umožňuje citlivější kontrolu nad částí zprávy, když interoperabilita požaduje takové přesnost. Kontrakt služby určuje skutečné metoda podpisy služby a je distribuován jako rozhraní v jednom z podporované programovací jazyky, jako je například jazyka Visual Basic a Visual C#.  
  
 Zásady a vazeb stanovení podmínky vyžadované pro komunikaci se službou.  Například vazby (minimálně) zadejte přenos používá (například HTTP nebo TCP) a kódování. Zásady obsahují požadavky na zabezpečení a jiných podmínek, které musí být splněny, aby komunikaci se službou.  
  
### <a name="service-runtime"></a>Běh služby  
 Služby modulu runtime vrstva obsahuje chování, které dojde jenom během aktuální operace služby, to znamená, že modul runtime chování služby. Omezení ovládacích prvků zpracování kolik zpráv, které lze měnit pokud vyžádání pro službu zvětšuje, aby přednastavené limit. K chybě chování Určuje, co se stane, když interní dojde k chybě ve službě, například kontrolou, jaké informace se předávají klienta. (Příliš velkého množství informací mohou poskytnout uživatel se zlými úmysly výhodu v připojení k útoku.) Chování metadata řídí, zda je k dispozici k vnějším světem metadat. Instance chování Určuje, kolik instancí služby lze spustit (například jednotlivý prvek určuje jenom jeden výskyt zpracovat všechny zprávy). Chování transakce umožňuje vrácení zpět zpracovaných operací, pokud dojde k chybě. Chování odesílání je řízení zpracování zprávy infrastruktura WCF.  
  
 Rozšiřitelnost umožňuje přizpůsobení runtime procesů. Například zpráva kontroly je zařízení ke kontrole části zpráv a parametr filtrování umožňuje přednastavené akcí podle filtry funguje na záhlaví zprávy.  
  
### <a name="messaging"></a>Zasílání zpráv  
 Vrstva zasílání zpráv se skládá z *kanály*. Kanál je komponenta, která zpracuje zprávu nějakým způsobem, například tak, že zprávu. Je také označován jako sadu kanálů *kanál zásobníku*. Kanály pracovat zpráv a hlavičky zpráv. To se liší z vrstvy služby modulu runtime, která se týká hlavně o zpracování obsah těla zprávy.  
  
 Existují dva typy kanálů: přenosu kanálů a kanály protokolů.  
  
 Přenosové kanály čtení a zápis zpráv ze sítě (nebo jinému bodu komunikace s vnějším světem). Některé přenosy použít kodér převést zprávy (které jsou reprezentovány jako XML Infosets) do a z reprezentace datového proudu bajtů používané sítí. Přenosy jsou protokolu HTTP, pojmenované kanály, TCP a služby MSMQ. Příkladem kódování jsou XML a optimalizované binární.  
  
 Kanály protokolů implementovat protokoly zpracování zpráv, často ve čtení nebo zápis další záhlaví ke zprávě. Příklady těchto protokolů: WS-zabezpečení a spolehlivost WS.  
  
 Vrstva zasílání zpráv znázorňuje možné formáty a vzorce dat systému exchange. WS-Security je implementace specifikace WS-zabezpečení povolení zabezpečení ve vrstvě zprávy. Kanál WS-spolehlivé zasílání zpráv umožňuje záruky doručení zpráv. Do různých kódování, které je možné podle potřeb zprávy k dispozici kodérů. Kanál protokolu HTTP Určuje, že tohoto protokolu se používá pro doručování zpráv. Kanál TCP podobně Určuje protokol TCP. Tok transakcí kanál řídí vzory zpracovaných zpráv. Kanál s názvem kanálu umožňuje komunikaci mezi procesy. Kanál služby MSMQ umožňuje vzájemná spolupráce pomocí aplikacím služby MSMQ.  
  
### <a name="hosting-and-activation"></a>Hostování a aktivace  
 V konečné podobě se služba je program. Podobně jako ostatní aplikace služby musí být spuštěn v spustitelný soubor. To se označuje jako *hostovanou na vlastním* služby.  
  
 Služby mohou být také *hostované*, nebo spustit ve spustitelném souboru spravuje externí agenta, například služby IIS nebo aktivace služby WAS (Windows). BYLA, byla aplikace WCF umožňuje automaticky aktivovaná, při nasazení v počítači se systémem. Služby můžete také ručně spustit jako spustitelné soubory (soubory .exe). Službu můžete také spustit automaticky jako služby systému Windows. Komponenty modelu COM + může být hostovaný také jako služby WCF.  
  
## <a name="see-also"></a>Viz také  
 [Co je Windows Communication Foundation](../../../docs/framework/wcf/whats-wcf.md)  
 [Základní koncepty Windows Communication Foundation](../../../docs/framework/wcf/fundamental-concepts.md)
