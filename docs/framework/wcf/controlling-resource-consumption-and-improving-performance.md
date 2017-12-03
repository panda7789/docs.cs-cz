---
title: "Řízení spotřeby prostředků a zlepšení výkonu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a829669-5f76-4c88-80ec-92d0c62c0660
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8cd80805eee58db16f5865683cbd322a49c554a8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="controlling-resource-consumption-and-improving-performance"></a>Řízení spotřeby prostředků a zlepšení výkonu
Toto téma popisuje různé vlastnosti v jiné oblasti [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] architekturu, která pracují pro řízení spotřeby prostředků a ovlivnit metriky výkonu.  
  
## <a name="properties-that-constrain-resource-consumption-in-wcf"></a>Vlastnosti, které omezit spotřeby prostředků ve službě WCF  
 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)]platí omezení na určité typy procesů pro účely zabezpečení a výkonu. Tato omezení mají dvě hlavní formy, kvóty a omezení. *Kvóty* jsou limity, které při dosažena nebo překročena spuštění okamžitou výjimky v určitém okamžiku v systému. *Omezí generovaný* jsou limity, které okamžitě nezpůsobí vyvolání výjimky. Místo toho po dosažení limit omezení zpracování pokračuje ale v rámci omezení nastavuje tuto hodnotu omezení. Omezené zpracování může aktivovat jinde výjimku, ale to závisí na aplikaci.  
  
 Kromě rozdíl mezi kvóty a omezení některé omezující vlastnosti jsou umístěné na úrovni serializace, některé na úrovni přenosu a některé na úrovni aplikace. Například kvótu <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A?displayProperty=nameWithType>, které je implementované všechny prvky vazeb přenosu poskytnuté systémem, je 65 536 bajtů ve výchozím nastavení má bránit škodlivý klienti účastnit denial-of-service útoky na služby tím, že na příliš mnoho paměti Spotřeba. (Obvykle, můžete zvýšit výkon snížením tuto hodnotu.)  
  
 Příkladem kvótu serializace je <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A?displayProperty=nameWithType> vlastnosti, která určuje maximální počet objektů, které serializátoru, který serializuje a deserializuje v jediném <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A> volání metody. Je například úrovni aplikace omezení <xref:System.ServiceModel.Dispatcher.ServiceThrottle.MaxConcurrentSessions%2A?displayProperty=nameWithType> vlastností, která se ve výchozím nastavení omezuje počet souběžných kanálu relací připojení do 10. (Na rozdíl od kvóty, když je dosaženo hodnoty omezení, aplikace pokračuje ve zpracování, ale přijímá nové kanály, relacemi, což znamená, že noví klienti nelze připojit, dokud jeden z dalších relacemi kanálů je zakončeno.)  
  
 Tyto ovládací prvky jsou určeny k poskytování omezení rizik se na pole vůči určitým typům útoků nebo ke zlepšení výkonu metriky například spotřeba paměti, čas spuštění a tak dále. Ale v závislosti na aplikaci, tyto ovládací prvky mít dopad na výkon aplikace služby nebo zabránit aplikaci v práci vůbec. Například může aplikace navržené tak, aby datový proud videa snadno překročit výchozí <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A?displayProperty=nameWithType> vlastnost. Toto téma obsahuje přehled různých ovládacích prvků, které se použijí na aplikace na všech úrovních [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], popisuje různé způsoby, jak získat další informace o tom, jestli je nastavení brání aplikaci a popisuje, jak opravit různé problémy. Většina omezení a některé kvóty jsou dostupné na úrovni aplikace, i v případě, že je vlastnost základní omezení serializace nebo přenos. Například můžete nastavit <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A?displayProperty=nameWithType> vlastnost pomocí <xref:System.ServiceModel.ServiceBehaviorAttribute.MaxItemsInObjectGraph%2A?displayProperty=nameWithType> vlastnost v třídě služby.  
  
> [!NOTE]
>  Pokud máte konkrétního problému, měli byste nejprve si přečíst [rychlý start řešení potíží s WCF](../../../docs/framework/wcf/wcf-troubleshooting-quickstart.md) a zkontrolujte, zda váš problém (a řešení) uveden existuje.  
  
 Vlastnosti, které omezují procesy serializace jsou uvedeny v [důležité informace o zabezpečení pro Data](../../../docs/framework/wcf/feature-details/security-considerations-for-data.md). Vlastnosti, které omezují spotřeby materiály související s přenosy jsou uvedeny v [přenosové kvóty](../../../docs/framework/wcf/feature-details/transport-quotas.md). Vlastnosti, které omezují spotřeby prostředků na aplikační vrstvu jsou členy <xref:System.ServiceModel.Dispatcher.ServiceThrottle> třídy.  
  
## <a name="detecting-application-and-performance-issues-related-to-quota-settings"></a>Zjišťování aplikace a související s nastavení kvót problémy s výkonem  
 Výchozí hodnoty na předchozí hodnoty rozhodli povolit funkce základní aplikace v rámci řadu různých typů aplikací při současném poskytování základní ochranu před běžné problémy se zabezpečením. Návrhy jinou aplikaci však můžete překročit jeden nebo více nastavení omezení, i když je aplikace, jinak zabezpečené a bude fungovat jako navržená tak. V těchto případech je potřeba určit, které hodnoty omezení jsou právě překročeno na co úrovně a rozhodnout na vhodných opatření, pokud chcete zvýšit propustnost aplikace.  
  
 Obvykle se při psaní aplikace a ladění, nastavení <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> vlastnost `true` v konfiguračním souboru nebo prostřednictvím kódu programu. Tím se nastaví [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] vrátit trasování zásobníku výjimky služby do klientské aplikace pro zobrazení. Tato funkce hlásí většina výjimky na úrovni aplikace v tak, aby zobrazení nastavení kvóty, které může být zahrnut, pokud je problém.  
  
 Některé výjimky nastávají v době spuštění pod viditelnost aplikační vrstvu a nebudou zobrazeny pomocí tento mechanismus a nemusí být zpracována vlastní <xref:System.ServiceModel.Dispatcher.IErrorHandler?displayProperty=nameWithType> implementace. Pokud jste ve vývojovém prostředí, jako je Microsoft Visual Studio, většinu těchto výjimek se zobrazí automaticky. Ale některé výjimky můžete zamaskovat nastavení prostředí pro vývoj, jako [pouze můj kód](http://go.microsoft.com/fwlink/?LinkId=82174) nastavení v sadě Visual Studio 2005.  
  
 Bez ohledu na to funkce vývojového prostředí, můžete použít možnosti [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] trasování a protokolování zpráv ladit všechny výjimky a vylaďte výkon vaší aplikace. Další informace najdete v tématu [pomocí trasování pro řešení potíží s vaše aplikace](../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).  
  
## <a name="performance-issues-and-xmlserializer"></a>Problémy s výkonem a třídy XmlSerializer  
 Služby a klientské aplikace používající typy dat, které jsou serializovatelný pomocí <xref:System.Xml.Serialization.XmlSerializer> generování a kompilace kódu serializace pro tyto typy dat za běhu, což může vést k pomalé spuštění výkonu.  
  
> [!NOTE]
>  Předem vygenerovaná serializace kódu je možné pouze v klientských aplikacích a není v služby.  
  
 [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) lze vylepšit výkon spuštění pro tyto aplikace generování kódu nezbytné serializace z kompilované sestavení pro aplikaci. Další informace najdete v tématu [postupy: zlepšení spuštění čas klientských aplikací WCF pomocí třídy XmlSerializer](../../../docs/framework/wcf/feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md).  
  
## <a name="performance-issues-when-hosting-wcf-services-under-aspnet"></a>Problémy s výkonem při hostování služby WCF v rámci technologie ASP.NET  
 Když je služba WCF hostované na IIS a ASP.NET, nastavení konfigurace služby IIS a ASP.NET může ovlivnit nároky na propustnost a paměti služby WCF.  [!INCLUDE[crabout](../../../includes/crabout-md.md)]Výkonu technologie ASP.NET, najdete v části [zlepšení výkonu technologie ASP.NET](http://go.microsoft.com/fwlink/?LinkId=186462).  Jedno nastavení, která může mít nežádoucích důsledků je <xref:System.Web.Configuration.ProcessModelSection.MinWorkerThreads%2A>, což je vlastnost <xref:System.Web.Configuration.ProcessModelSection>. Pokud vaše aplikace má pevnou nebo malý počet klientů, nastavení <xref:System.Web.Configuration.ProcessModelSection.MinWorkerThreads%2A> 2 může poskytovat nárůst propustnosti na počítači s více procesory, který má využití procesoru blíží 100 %. Toto zvýšení výkonu dodává se s náklady: také způsobí nárůst využití paměti, které by mohly snížit škálovatelnost.  
  
## <a name="see-also"></a>Viz také  
 [Správa a Diagnostika](../../../docs/framework/wcf/diagnostics/index.md)  
 [Velkého množství dat a vysílání datového proudu](../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)
