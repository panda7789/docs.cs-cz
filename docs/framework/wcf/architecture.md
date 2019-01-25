---
title: Architektura Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], architecture
- WCF [WCF], architecture
- architecture [WCF]
ms.assetid: a3bcb0a1-56ea-4ba6-9736-d260d90dade5
ms.openlocfilehash: f152ac48c2897259d07222fafd33d17d5287a870
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745377"
---
# <a name="windows-communication-foundation-architecture"></a>Architektura Windows Communication Foundation
Následující obrázek znázorňuje hlavní vrstvy architektury Windows Communication Foundation (WCF).  
  
## <a name="wcf-architecture"></a>Architektura WCF  
 ![Architektura WCF](../../../docs/framework/wcf/media/wcf-architecture.gif "WCF_Architecture")  
  
### <a name="contracts-and-descriptions"></a>Popisy a kontrakty  
 Kontrakty definovat různé aspekty systému zprávy. Kontrakt dat popisuje každý parametr, který tvoří všechny zprávy, které můžete vytvořit nebo využívání služby. Zpráva parametry jsou definované ve schématu XML definice jazyk (XSD) dokumenty, povolení všechny systémy, které rozumí ke zpracování dokumentů XML. Kontrakt zprávy definuje části konkrétní zprávu přes protokoly protokolu SOAP a umožňuje citlivější kontrolu nad částí zprávy, když vzájemná funkční spolupráce se požadavky na takové přesnosti. Kontrakt služby určuje skutečné signatury služby a je distribuován jako rozhraní v jednom z podporovaných programovacích jazycích, jako je například Visual Basic nebo Visual C#.  
  
 Zásady a vazby stanoví podmínky potřebné ke komunikaci se službou.  Například vazby (minimálně) zadejte přenosu použít (například HTTP nebo TCP) a kódování. Zásady zahrnovat požadavky na zabezpečení a jiných podmínek, které musí být splněny pro komunikaci se službou.  
  
### <a name="service-runtime"></a>Běh služby  
 Vrstva služby modulu runtime obsahuje chování, ke kterým dochází pouze během aktuální operace služby, to znamená, chování za běhu služby. Omezení ovládacích prvků zpracování počet zpráv, které lze měnit pokud požadavky na službu zvětšuje, aby přednastavený limit. K chybě chování Určuje, co se stane při interní dojde k chybě ve službě, například kontrolou, jaké informace se předává se do klienta. (Příliš mnoho informací můžete udělit uživateli se zlými úmysly výhodu v připojení k útoku.) Řídí chování metadat jak a jestli je k dispozici zvnějšku metadat. Instance chování Určuje, kolik instancí služby, můžete spustit (například jednotlivý prvek určuje jenom jednu instanci zpracovávat všechny zprávy). Chování při transakci umožňuje vrátit zpět změny provedené operace, pokud dojde k chybě. Chování odesílání je prvek zpracování zprávy infrastruktura WCF.  
  
 Rozšiřitelnost umožňuje přizpůsobit procesy modulu runtime. Například zpráva kontroly je zařízení ke kontrole části zpráv a parametr filtrování umožňuje předvolby akcí podle filtry na záhlaví zpráv.  
  
### <a name="messaging"></a>Zasílání zpráv  
 Vrstva zasílání zpráv se skládá z *kanály*. Kanál je komponenta, která zpracovává zprávu nějakým způsobem, například pomocí ověřování zprávy. Sada kanály se taky říká *kanál zásobníku*. Kanály pracovat zprávy a záhlaví zpráv. Tím se liší od vrstva služby modulu runtime, která se týká hlavně o zpracování obsahu těla zprávy.  
  
 Existují dva typy kanálů: přenosu kanálů a kanály protokolů.  
  
 Přenosové kanály čtení a zápis zpráv v síti (nebo některých jiných bod komunikace s vnějším světem). Některé přenosy pomocí kodéru pro převod zprávy (které jsou reprezentovány ve formě XML Infosets) a z reprezentace datového proudu bajtů používanou v síti. Přenosy jsou HTTP, pojmenované kanály, TCP a služby MSMQ. Příklady kódování jsou XML a optimalizovaného binárního souboru.  
  
 Kanály protokolů implementovat protokoly zpracování zpráv, často čtením nebo zápisem další záhlaví ke zprávě. Příklady těchto protokolů: specifikace WS-Security a WS-spolehlivost.  
  
 Vrstvě zasílání zpráv znázorňuje možných formátů a vzory data systému exchange. WS-Security je implementace povolení zabezpečení ve vrstvě zpráva specifikace WS-Security. Zasílání zpráv WS-Reliable channel povolí záruky doručení zpráv. U kodérů nabízejí širokou škálu kódování, který můžete použít tak, aby vyhovoval potřebám zprávy. Kanál protokolu HTTP Určuje, že hypertextový přenosový protokol se používá pro doručení zpráv. Kanál TCP podobně Určuje protokol TCP. Kanál tok transakce se řídí počet zrušených zpracovaných zpráv vzory. Kanál s názvem umožňuje komunikaci mezi procesy. MSMQ – channel povolí interoperabilitu s aplikací služby MSMQ.  
  
### <a name="hosting-and-activation"></a>Hostování a aktivace  
 V posledním podobě služba je program. Podobně jako ostatní aplikace služba musí být spuštěna ve spustitelném souboru. Jedná se *samoobslužně* služby.  
  
 Služby mohou také být *hostované*, nebo spustit v externí agenta, například IIS nebo aktivace služby Windows (WAS) spravuje spustitelný soubor. BYLA, byla aplikací WCF umožňuje automaticky aktivovat, když jsou nasazená v počítači se systémem. Služby můžete také ručně spustit jako spustitelné soubory (soubory .exe). Služby můžete také spustit automaticky jako služba Windows. Komponenty modelu COM + je rovněž možné hostovat jako služba WCF.  
  
## <a name="see-also"></a>Viz také:
- [Co je Windows Communication Foundation](../../../docs/framework/wcf/whats-wcf.md)
- [Základní koncepty Windows Communication Foundation](../../../docs/framework/wcf/fundamental-concepts.md)
