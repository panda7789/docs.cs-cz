---
title: Klientské aplikace střední vrstvy
ms.date: 03/30/2017
ms.assetid: f9714a64-d0ae-4a98-bca0-5d370fdbd631
ms.openlocfilehash: c50223a55765f211dae710f96bffa7716ce36b32
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598811"
---
# <a name="middle-tier-client-applications"></a>Klientské aplikace střední vrstvy
Toto téma popisuje různé problémy, které jsou specifické pro klientské aplikace střední vrstvy, které používají Windows Communication Foundation (WCF).  
  
## <a name="increasing-middle-tier-client-performance"></a>Zvýšení výkonu klientů střední vrstvy  
 V porovnání s předchozími komunikačními technologiemi, jako jsou webové služby využívající ASP.NET, vytvoření instance klienta služby WCF může být složitější, protože sada funkcí WCF s bohatou funkcí je složitá. Například když <xref:System.ServiceModel.ChannelFactory%601> je objekt otevřen, může vytvořit zabezpečenou relaci se službou, což je postup, který zvyšuje čas spuštění instance klienta. Tyto dodatečné funkce obvykle neovlivňují klientské aplikace významně, protože klient WCF provede několik volání a pak se ukončí.  
  
 Klientské aplikace střední vrstvy ale můžou rychle vytvořit mnoho objektů klienta WCF a v důsledku toho se zvýší požadavky na inicializaci. Existují dva hlavní přístupy ke zvýšení výkonu aplikací střední vrstvy při volání služeb:  
  
- Umožňuje uložit objekt klienta WCF do mezipaměti a znovu ho použít pro následné volání.  
  
- Vytvořte <xref:System.ServiceModel.ChannelFactory%601> objekt a poté pomocí tohoto objektu vytvořte nové objekty kanálu klienta WCF pro každé volání.  
  
 Mezi problémy, které je potřeba zvážit při použití těchto přístupů, patří:  
  
- Pokud služba udržuje stav specifický pro konkrétního klienta pomocí relace, nemůžete znovu použít klienta WCF prostřední vrstvy s požadavky na vrstvu na více klientů, protože stav služby je svázán s klientem střední vrstvy.  
  
- Pokud je nutné, aby služba prováděla ověřování pro každého klienta, je nutné vytvořit nového klienta pro každý příchozí požadavek na střední úrovni místo opětovného použití klienta WCF střední vrstvy (nebo objektu kanálu klienta WCF), protože po vytvoření klienta služby WCF (nebo) nelze změnit pověření klienta <xref:System.ServiceModel.ChannelFactory%601> .  
  
- I když kanály a klienti vytvořené kanály jsou bezpečné pro přístup z více vláken, nemusí podporovat současně zápis více než jedné zprávy na daný přenos. Pokud posíláte velké zprávy, zejména pokud streamování, může operace odeslání blokovat čekání na dokončení jiného odeslání. To způsobuje dvě druhy problémů: nedostatek souběžnosti a možnost zablokování, pokud se tok ovládacího prvku vrátí ke službě, který kanál znovu používá (to znamená, že sdílený klient volá službu, jejíž cesta kódu má za následek zpětné volání do sdíleného klienta). To platí bez ohledu na typ klienta služby WCF, který znovu použijete.  
  
- Je potřeba zpracovat chybové kanály bez ohledu na to, jestli kanál sdílíte. Když se kanály znovu použijí, může kanál chyb zabrat víc než jednu nevyřízenou žádost nebo odeslat.  
  
 Příklad, který ukazuje osvědčené postupy pro opakované použití klienta pro více požadavků, najdete v tématu [datové vazby v klientovi ASP.NET](../samples/data-binding-in-an-aspnet-client.md).  
  
 Kromě toho můžete zvýšit výkon při spuštění pro tyto klienty, kteří používají datové typy, které jsou serializovatelný pomocí <xref:System.Xml.Serialization.XmlSerializer> generování a kompilování serializace kódu pro tyto datové typy za běhu, což může vést k pomalému spuštění výkonu. Nástroj pro měření [metadat třídy (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) může zlepšit výkon spuštění těchto aplikací vygenerováním potřebného kódu serializace z kompilovaných sestavení pro aplikaci. Další informace naleznete v tématu [How to: vylepšení doby spouštění klientských aplikací WCF pomocí objektu XmlSerializer](startup-time-of-wcf-client-applications-using-the-xmlserializer.md).  
  
## <a name="see-also"></a>Viz také

- [Přístup ke službám pomocí klienta WCF](accessing-services-using-a-client.md)
