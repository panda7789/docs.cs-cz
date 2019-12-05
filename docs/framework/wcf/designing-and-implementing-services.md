---
title: Navrhování a implementace služeb
ms.date: 03/30/2017
helpviewer_keywords:
- defining service contracts [WCF]
ms.assetid: 036fae20-7c55-4002-b71d-ac4466e167a3
ms.openlocfilehash: 9ddb3fe637cd0402f0ce850bc523ae8cb0c5dc37
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74801972"
---
# <a name="designing-and-implementing-services"></a>Navrhování a implementace služeb
V této části se dozvíte, jak definovat a implementovat kontrakty WCF. Kontrakt služby určuje, co koncový bod komunikuje s vnějším světem. Na přesnější úrovni je to prohlášení o sadě konkrétních zpráv uspořádaných do základních vzorů výměny zpráv (MEPs), jako je například požadavek/odpověď, jednosměrné a duplexní využití. Je-li kontrakt služby logicky spojenou sadou výměn zpráv, je operace služby jediným výměnou zpráv. Například operace `Hello` musí zjevně akceptovat jednu zprávu (takže volající může oznámení pozdravu) a může nebo nemusí vracet zprávu (v závislosti na povýšení operace).  
  
 Další informace o smlouvách a dalších konceptech služby Core Windows Communication Foundation (WCF) najdete v tématu [základní koncepty Windows Communication Foundation](fundamental-concepts.md). Toto téma se zaměřuje na porozumění kontraktům služby. Další informace o tom, jak vytvořit klienty, kteří používají kontrakty služeb pro připojení ke službám, najdete v tématu [Přehled klientů WCF](wcf-client-overview.md).  
  
## <a name="overview"></a>Přehled  
 Toto téma obsahuje koncepční koncepční orientaci pro návrh a implementaci služeb WCF. Dílčí témata poskytují podrobnější informace o konkrétních návrhech a implementacich. Před návrhem a implementací aplikace WCF doporučujeme:  
  
- Seznamte se s principem kontraktu služby, jak funguje a jak ho vytvořit.  
  
- Seznamte se s minimálními požadavky na stav kontraktů, které konfigurace modulu runtime nebo hostitelské prostředí nemusí podporovat.  
  
## <a name="service-contracts"></a>Kontrakty služeb  
 Kontrakt služby určuje následující:  
  
- Operace, které kontrakt zveřejňuje.  
  
- Signatura operací v podobě vyměňovaných zpráv.  
  
- Datové typy těchto zpráv.  
  
- Umístění operací.  
  
- Konkrétní protokoly a formáty serializace, které se používají k podpoře úspěšné komunikace se službou.  
  
 Například kontrakt nákupní objednávky může mít operaci `CreateOrder`, která přijímá vstupní typy informací o objednávkách a vrací informace o úspěchu nebo neúspěchu včetně identifikátoru objednávky. Může mít také operaci `GetOrderStatus`, která přijímá identifikátor objednávky a vrací informace o stavu objednávky. Kontrakt služby tohoto řazení by určoval:  
  
1. Tato smlouva o nákupu se skládá z `CreateOrder` a `GetOrderStatus`ch operací.  
  
2. Že operace mají zadané vstupní zprávy a výstupní zprávy.  
  
3. Data, která tyto zprávy mohou přenášet.  
  
4. Kategorií příkazy týkající se komunikační infrastruktury potřebné k úspěšnému zpracování zpráv. Mezi tyto podrobnosti patří například to, jestli a jaké jsou požadavky na zabezpečení, aby bylo možné navázat úspěšnou komunikaci.  
  
 Aby bylo možné tyto informace předat jiným aplikacím na mnoha platformách (včetně platforem jiných výrobců než Microsoftu), smlouvy služby XML jsou veřejně vyjádřeny ve standardních formátech XML, jako je například [Web Services Description Language](https://www.w3.org/TR/2001/NOTE-wsdl-20010315) (WSDL) a [schématu XML](https://www.w3.org/XML/Schema) (XSD), mimo jiné. Vývojáři pro mnoho platforem můžou tyto informace o veřejné smlouvě využít k vytváření aplikací, které můžou komunikovat se službou, protože rozumí jazyk specifikace a protože tyto jazyky jsou navržené tak, aby umožňovaly vzájemnou operaci. popisem veřejných formulářů, formátů a protokolů, které služba podporuje. Další informace o tom, jak WCF zpracovává tento druh informací, najdete v tématu [metadata](./feature-details/metadata.md).  
  
 Kontrakty můžou být vyjádřené mnoha způsoby a i když jsou jazyky WSDL a XSD vynikajícími jazyky pro usnadnění přístupu ke službám, jsou obtížné použít přímo a jsou jenom popisy služby, nikoli implementace servisních smluv. Proto aplikace WCF používají spravované atributy, rozhraní a třídy pro definování struktury služby a její implementaci.  
  
 Výsledný kontrakt definovaný ve spravovaných typech lze *exportovat* jako metadata – WSDL a XSD – v případě potřeby klienty nebo jiné implementátory služby. Výsledkem je přímočarý programovací model, který může být popsán (pomocí veřejných metadat) k libovolné klientské aplikaci. Podrobnosti o podkladových zprávách protokolu SOAP, informace o dopravě a zabezpečení atd., mohou být ponechány na WCF, který provádí nezbytné převody na systém typů servisních smluv a do systému typů XML automaticky.  
  
 Další informace o návrhu smluv najdete v tématu [Navrhování kontraktů služeb](designing-service-contracts.md). Další informace o implementaci smluv najdete v tématu [implementace kontraktů služeb](implementing-service-contracts.md).  
  
### <a name="messages-up-front-and-center"></a>Zprávy před a na střed  
 Použití spravovaných rozhraní, tříd a metod modelování operací služby je jednoduché, pokud používáte signatury metod se vzdáleným voláním procedur (RPC), ve kterých jsou předány parametry do metody a příjem návratových hodnot je normální forma vyžádání funkcí z objektu nebo jiného typu kódu. Například programátoři používající spravované jazyky, jako je Visual Basic a com C++ , mohou použít své znalosti přístupu ve stylu RPC (ať už používajících objekty nebo rozhraní) k vytváření kontraktů služby WCF, aniž by se setkaly s problémy, které jsou v systémech distribuovaných objektů ve stylu RPC. Orientace služby přináší výhody volně vázaných a uživatelsky orientovaných programování a přitom zachovává snadné a známé prostředí pro programování RPC.  
  
 Mnoho programátorů je pohodlnější při používání programovacích rozhraní aplikace orientovaných na zprávy, jako jsou například fronty zpráv, jako je Microsoft MSMQ, <xref:System.Messaging> obory názvů v .NET Framework nebo posílání nestrukturovaných XML v požadavcích HTTP, a to na několik názvů. Další informace o programování na úrovni zpráv najdete v tématech [používání kontraktů zpráv](./feature-details/using-message-contracts.md), [programování na úrovni kanálu služby](./extending/service-channel-level-programming.md)a [interoperability s aplikacemi POX](./feature-details/interoperability-with-pox-applications.md).  
  
### <a name="understanding-the-hierarchy-of-requirements"></a>Porozumění hierarchii požadavků  
 Servisní smlouva seskupuje operace. Určuje vzor výměny zpráv, typy zpráv a typy dat, které tyto zprávy obsahují. a označuje kategorie chování modulu runtime, které musí implementace vyžadovat pro podporu kontraktu (například může vyžadovat, aby zprávy byly šifrované a podepsané). Samotný kontrakt služby nespecifikuje přesně to, jak jsou tyto požadavky splněné, jenom to, že musí být. Typ šifrování nebo způsob, jakým je zpráva podepsána, je až do implementace a konfigurace kompatibilní služby.  
  
 Všimněte si, že smlouva vyžaduje určité věci implementace kontraktu služby a konfiguraci modulu runtime pro přidání chování. Sada požadavků, které je nutné splnit k vystavení služby pro použití sestavení na předchozí sadě požadavků. Pokud kontrakt provede požadavky na implementaci, implementace může vyžadovat ještě více konfigurací a vazeb, které umožňují spuštění služby. Nakonec musí hostitelská aplikace podporovat také všechny požadavky, které konfigurace služby a vazby přidávají.  
  
 Tento proces požadavku na doplňkovou látku je důležitý při navrhování, implementaci, konfiguraci a hostování aplikace služby Windows Communication Foundation (WCF). Kontrakt může například určit, že musí podporovat relaci. Pokud ano, musíte nakonfigurovat vazbu na podporu tohoto smluvního požadavku, jinak nebude implementace služby fungovat. Nebo pokud vaše služba vyžaduje integrované ověřování Windows a je hostovaná ve službě Internetová informační služba (IIS), musí mít webová aplikace, ve které se služba nachází, zapnuté integrované ověřování systému Windows a vypnout anonymní podporu. Další informace o funkcích a vlivu různých typů hostitelských aplikací služby najdete v tématu [hostingové služby](hosting-services.md).  
  
## <a name="see-also"></a>Viz také:

- [Navrhování kontraktů služby](designing-service-contracts.md)
- [Implementace kontraktů služeb](implementing-service-contracts.md)
