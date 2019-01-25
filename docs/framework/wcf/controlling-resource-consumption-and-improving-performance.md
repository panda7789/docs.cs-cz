---
title: Řízení spotřeby prostředků a zlepšení výkonu
ms.date: 03/30/2017
ms.assetid: 9a829669-5f76-4c88-80ec-92d0c62c0660
ms.openlocfilehash: 11d1333ed0ae8b46f8f87fa6f4643d4b31fac3ff
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54664158"
---
# <a name="controlling-resource-consumption-and-improving-performance"></a>Řízení spotřeby prostředků a zlepšení výkonu
Toto téma popisuje různé vlastnosti v různých oblastech Architektura Windows Communication Foundation (WCF), které fungují při řízení spotřeby prostředků a ovlivňují metrik výkonu.

## <a name="properties-that-constrain-resource-consumption-in-wcf"></a>Vlastnosti, které se omezila využití prostředků ve službě WCF
 Windows Communication Foundation (WCF) platí omezení na určitých typech procesy pro účely zabezpečení ani výkon. Tato omezení se dělí na dvě hlavní formulář, kvóty a omezení. *Kvóty* jsou omezení, která při dosáhlo nebo došlo k překročení spuštění okamžité výjimky v určitém okamžiku v systému. *Omezí* jsou omezení, která okamžitě nevyvolá výjimku, která je vyvolána. Místo toho při dosažení limitu omezení zpracování bude pokračovat, ale v rámci omezení nastavit hodnotu tohoto omezení. Tato omezená zpracování může aktivovat výjimku jinde, ale to závisí na aplikaci.

 Kromě rozdílu mezi kvóty a omezení některé omezující vlastnosti jsou umístěné na úrovni serializace, některé na úrovni přenosu a některé na úrovni aplikace. Například kvóty <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A?displayProperty=nameWithType>, které je implementované všechny elementy vazby přenosu poskytnuté systémem, je 65 536 bajtů ve výchozím nastavení brání škodlivým klientů ze smluvních denial-of-service útoků, které služba způsobením využívala příliš mnoho paměti Spotřeba. (Obvykle můžete zvýšit výkon snížením tuto hodnotu.)

 Příklad kvótu serializace je <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A?displayProperty=nameWithType> vlastnost, která určuje maximální počet objektů, které serializátoru, který serializuje a deserializuje v jediném <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A> volání metody. Je například omezení úrovni aplikace <xref:System.ServiceModel.Dispatcher.ServiceThrottle.MaxConcurrentSessions%2A?displayProperty=nameWithType> vlastnosti, která je ve výchozím nastavení omezuje počet souběžných kanál s relacemi připojení k 10. (Na rozdíl od kvóty, při dosažení této hodnoty omezení aplikace pokračuje ve zpracování, ale přijímá žádné nové duplexních kanálů s relacemi, což znamená, že noví klienti nemůžou připojit, dokud jeden z jiných kanálů s relacemi je zakončeno.)

 Tyto ovládací prvky jsou určeny omezení rizik out-of-the-box s určitým typům útoků nebo ke zlepšení výkonu metriky, jako je paměť, čas spuštění a tak dále. Ale v závislosti na aplikaci, tyto ovládací prvky bránit výkonu aplikací služby nebo zabránit aplikaci v pracovní době. Například aplikace navržené tak, aby datový proud videa může snadno překročit výchozí <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A?displayProperty=nameWithType> vlastnost. Toto téma obsahuje přehled různých ovládacích prvků použijí na aplikace na všech úrovních služby WCF, popisuje různé způsoby, jak získat další informace o tom, jestli je nastavení omezování aplikace a způsoby, jak opravit různé problémy. Většinu omezení a některé kvóty jsou k dispozici na úrovni aplikace i v případě, že je vlastnost základní omezení serializace nebo přenos. Například můžete nastavit <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A?displayProperty=nameWithType> pomocí vlastnosti <xref:System.ServiceModel.ServiceBehaviorAttribute.MaxItemsInObjectGraph%2A?displayProperty=nameWithType> vlastnost ve třídě služby.

> [!NOTE]
> Pokud máte konkrétního problému, byste si měli nejdřív přečíst [rychlý start řešení potíží s WCF](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md) chcete zobrazit, zda je zde uvedeny váš problém (a řešení).

 Vlastnosti, které omezují procesů serializace jsou uvedeny v [aspekty zabezpečení pro Data](../../../docs/framework/wcf/feature-details/security-considerations-for-data.md). Vlastnosti, které omezují spotřebu prostředků související s přenosy jsou uvedeny v [přenosové kvóty](../../../docs/framework/wcf/feature-details/transport-quotas.md). Jako objekty její členové jsou vlastnosti, které omezují spotřebu prostředků v aplikační vrstvě <xref:System.ServiceModel.Dispatcher.ServiceThrottle> třídy.

## <a name="detecting-application-and-performance-issues-related-to-quota-settings"></a>Detekce aplikací a problémy výkonu týkající se nastavení kvót
 Výchozí hodnoty předchozí hodnoty zvolili k dosažení funkce základní aplikaci v rámci široký rozsah typů aplikací poskytuje základní ochranu proti běžné problémy se zabezpečením. Návrhy různé aplikace však může překročit minimálně jedno nastavení omezení, i když je zabezpečená jinak aplikace a bude fungovat tak, jak navrženo. V těchto případech je nutné určit, které hodnoty omezení jsou překročení a na co úrovně a rozhodnout o vhodných opatření pro zvýšení propustnosti aplikace.

 Obvykle při psaní aplikace a její ladění, nastavení <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> vlastnost `true` v konfiguračním souboru nebo prostřednictvím kódu programu. Toto dá pokyn WCF se vraťte do klientské aplikace pro zobrazení trasování zásobníku výjimky služby. Tato funkce sestav většina výjimek úrovni aplikace v takovým způsobem, zobrazit nastavení kvóty, které může být zahrnut, pokud je to problém.

 Některé výjimky nastávají v době spuštění pod viditelnost aplikační vrstvu a nejsou vráceny za použití tohoto mechanismu a nemusí být zpracovány vlastní <xref:System.ServiceModel.Dispatcher.IErrorHandler?displayProperty=nameWithType> implementace. Pokud jste ve vývojovém prostředí, jako je Microsoft Visual Studio, zobrazí se automaticky většinu těchto výjimek. Nicméně některé výjimky můžete maskovaná nastavení prostředí vývoje, jako [pouze můj kód](/visualstudio/debugger/just-my-code) sady Visual Studio.

 Bez ohledu na funkce vývojového prostředí můžete použít možnosti WCF trasování a protokolování zpráv všechny výjimky ladění a optimalizace výkonu vaší aplikace. Další informace najdete v tématu [pomocí trasování pro řešení potíží s aplikace](../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).

## <a name="performance-issues-and-xmlserializer"></a>Problémy s výkonem a XmlSerializer
 Služby a klientské aplikace, které používají datové typy, které jsou serializovatelné pomocí <xref:System.Xml.Serialization.XmlSerializer> generování a kompilaci Serializační kód pro tyto datové typy v době běhu, což může vést k pomalé spouštění výkonu.

> [!NOTE]
> Serializace předem generovaného kódu lze použít pouze v klientských aplikacích a ne v služeb.

 [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) výkon lze zvýšit objem požadovaný při spuštění pro tyto aplikace generování kódu serializace nezbytné ze zkompilovaných sestavení pro aplikaci. Další informace najdete v tématu [jak: Vylepšení spuštění čas z klientských aplikací WCF pomocí třídy XmlSerializer](../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md).

## <a name="performance-issues-when-hosting-wcf-services-under-aspnet"></a>Problémy s výkonem při hostování služby WCF v ASP.NET
 Když je služba WCF hostované na IIS a ASP.NET, nastavení konfigurace služby IIS a ASP.NET může ovlivnit nároky na propustnost a paměti služby WCF.  Další informace o výkonu technologie ASP.NET, naleznete v tématu [zlepšení výkonu technologie ASP.NET](https://go.microsoft.com/fwlink/?LinkId=186462).  Jedno nastavení, která může mít nežádoucí důsledky je <xref:System.Web.Configuration.ProcessModelSection.MinWorkerThreads%2A>, což je vlastnost <xref:System.Web.Configuration.ProcessModelSection>. Pokud vaše aplikace má pevný nebo malý počet klientů, nastavení <xref:System.Web.Configuration.ProcessModelSection.MinWorkerThreads%2A> 2 může poskytnout zvýšení propustnosti na počítači s více procesory, který má využití procesoru téměř 100 %. Toto zvýšení výkonu se dodává s náklady: také způsobí zvýšení využití paměti, což může omezit škálovatelnost.

## <a name="see-also"></a>Viz také:

- [Správa a diagnostika](../../../docs/framework/wcf/diagnostics/index.md)
- [Objemná data a streamování](../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)
