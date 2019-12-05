---
title: Řízení spotřeby prostředků a zlepšení výkonu
ms.date: 03/30/2017
ms.assetid: 9a829669-5f76-4c88-80ec-92d0c62c0660
ms.openlocfilehash: 16d6f29235455ff30e115b7aff3425412bc7ba6a
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802254"
---
# <a name="controlling-resource-consumption-and-improving-performance"></a>Řízení spotřeby prostředků a zlepšení výkonu
Toto téma popisuje různé vlastnosti v různých oblastech architektury Windows Communication Foundation (WCF), které pracují na řízení spotřeby prostředků a vlivu na metriky výkonu.

## <a name="properties-that-constrain-resource-consumption-in-wcf"></a>Vlastnosti, které omezí spotřebu prostředků ve službě WCF
 Windows Communication Foundation (WCF) aplikuje omezení na určité typy procesů pro účely zabezpečení nebo výkonu. Tato omezení jsou dvě hlavní formuláře, a to buď kvóty, a omezení. *Kvóty* jsou limity, které při dosažení nebo překročení triggeru aktivují v určitém okamžiku v systému okamžitou výjimku. *Omezení* jsou omezení, která okamžitě nezpůsobí vyvolání výjimky. Místo toho, když je dosaženo limitu omezení, zpracování pokračuje, ale v rámci omezení stanovených hodnotou tohoto omezení. Toto omezené zpracování může vyvolat výjimku jinde, ale závisí na aplikaci.

 Kromě rozdílu mezi kvótami a omezeními jsou některé omezující vlastnosti umístěny na úrovni serializace, některé na úrovni přenosu a některé na úrovni aplikace. Například kvóta <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A?displayProperty=nameWithType>, která je implementována všemi systémem dodanými prvky vazby, je ve výchozím nastavení nastavena na 65 536 bajtů, aby bránila útokům škodlivých klientů na útoky DoS (Denial-of-Service) proti službě, což by způsobilo nadměrné využití paměti. (Obvykle můžete zvýšit výkon snížením této hodnoty.)

 Příkladem kvóty serializace je vlastnost <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A?displayProperty=nameWithType>, která určuje maximální počet objektů, které serializátor serializace nebo deserializace v jednom volání metody <xref:System.Runtime.Serialization.DataContractSerializer.ReadObject%2A>. Příkladem omezení na úrovni aplikace je vlastnost <xref:System.ServiceModel.Dispatcher.ServiceThrottle.MaxConcurrentSessions%2A?displayProperty=nameWithType>, která ve výchozím nastavení omezuje počet souběžných připojení kanálů relací na 10. (Na rozdíl od kvót platí, že pokud je dosažena tato hodnota omezení, aplikace pokračuje ve zpracování, ale nepřijímá žádné nové kanály relací, což znamená, že se noví klienti nebudou moci připojit, dokud nebude ukončen některý z ostatních kanálů relace.)

 Tyto ovládací prvky jsou navržené tak, aby poskytovaly předem zaměřené zmírnění určitých typů útoků nebo vylepšili metriky výkonu, jako jsou nároky na paměť, čas spuštění a tak dále. V závislosti na aplikaci ale tyto ovládací prvky můžou narušit výkon aplikace služby nebo zabránit tomu, aby aplikace fungovala vůbec. Například aplikace určená pro streamování videa může snadno překročit výchozí vlastnost <xref:System.ServiceModel.Channels.TransportBindingElement.MaxReceivedMessageSize%2A?displayProperty=nameWithType>. Toto téma obsahuje přehled různých ovládacích prvků použitých u aplikací na všech úrovních WCF. popisuje různé způsoby, jak získat další informace o tom, zda nastavení brání aplikaci, a popisuje způsoby, jak opravit různé problémy. Většina omezení a některé kvóty jsou k dispozici na úrovni aplikace, a to i v případě, že základní vlastnost je omezení serializace nebo Transport. Vlastnost <xref:System.Runtime.Serialization.DataContractSerializer.MaxItemsInObjectGraph%2A?displayProperty=nameWithType> můžete například nastavit pomocí vlastnosti <xref:System.ServiceModel.ServiceBehaviorAttribute.MaxItemsInObjectGraph%2A?displayProperty=nameWithType> třídy služby.

> [!NOTE]
> Pokud máte konkrétní problém, měli byste nejdřív přečíst příručku pro [rychlý Start řešení WCF](wcf-troubleshooting-quickstart.md) , abyste viděli, jestli je tam uvedený problém (a řešení).

 Vlastnosti, které omezují procesy serializace, jsou uvedeny v [informacích o zabezpečení pro data](./feature-details/security-considerations-for-data.md). V části [přenosové kvóty](./feature-details/transport-quotas.md)jsou uvedeny vlastnosti, které omezují spotřebu prostředků souvisejících s přenosy. Vlastnosti, které omezují spotřebu prostředků na aplikační vrstvě, jsou členy třídy <xref:System.ServiceModel.Dispatcher.ServiceThrottle>.

## <a name="detecting-application-and-performance-issues-related-to-quota-settings"></a>Zjišťování problémů s aplikací a výkonem souvisejících s nastavením kvót
 V rámci široké škály typů aplikací byly při poskytování základní ochrany před běžnými problémy se zabezpečením zvoleny výchozí hodnoty předchozích hodnot. Různé návrhy aplikací však mohou překročit jedno nebo více nastavení omezení, i když je aplikace zabezpečená a funguje tak, jak je navržena. V těchto případech je nutné zjistit, které hodnoty omezení jsou překročeny a na jakou úroveň, a rozhodnout o vhodném postupu pro zvýšení propustnosti aplikace.

 Obvykle při psaní aplikace a jejím ladění nastavíte vlastnost <xref:System.ServiceModel.Description.ServiceDebugBehavior.IncludeExceptionDetailInFaults%2A?displayProperty=nameWithType> na `true` v konfiguračním souboru nebo programově. Tím služba WCF vydá pokyn, aby vracela trasování zásobníku výjimky služby klientovi pro zobrazení. Tato funkce hlásí většinu výjimek na úrovni aplikace tak, aby zobrazovala, která nastavení kvót mohou být zahrnuta, pokud se jedná o problém.

 K některým výjimkám dochází za běhu pod viditelností vrstvy aplikace a nejsou vraceny pomocí tohoto mechanismu a nemusí být zpracovány vlastní <xref:System.ServiceModel.Dispatcher.IErrorHandler?displayProperty=nameWithType> implementace. Pokud jste ve vývojovém prostředí, například Microsoft Visual Studio, většina těchto výjimek se zobrazí automaticky. Některé výjimky však lze maskovat pomocí nastavení vývojového prostředí, jako je [pouze můj kód](/visualstudio/debugger/just-my-code) Visual Studio.

 Bez ohledu na možnosti vašeho vývojového prostředí můžete využít možnosti trasování WCF a protokolování zpráv pro ladění všech výjimek a ladění výkonu aplikací. Další informace najdete v tématu [použití trasování k řešení potíží s aplikací](./diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md).

## <a name="performance-issues-and-xmlserializer"></a>Problémy s výkonem a XmlSerializer
 Služby a klientské aplikace, které používají datové typy, které jsou serializovatelný pomocí <xref:System.Xml.Serialization.XmlSerializer> generovat a kompilovat serializaci kódu pro tyto datové typy za běhu, což může vést k pomalému spuštění výkonu.

> [!NOTE]
> Předem generovaný kód serializace lze použít pouze v klientských aplikacích, nikoli v službách.

 Nástroj pro měření [metadat třídy (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) může zlepšit výkon spuštění těchto aplikací vygenerováním potřebného kódu serializace z kompilovaných sestavení pro aplikaci. Další informace naleznete v tématu [How to: vylepšení doby spouštění klientských aplikací WCF pomocí objektu XmlSerializer](./feature-details/startup-time-of-wcf-client-applications-using-the-xmlserializer.md).

## <a name="performance-issues-when-hosting-wcf-services-under-aspnet"></a>Problémy s výkonem při hostování služeb WCF pod ASP.NET

Když je služba WCF hostovaná v rámci služby IIS a ASP.NET, nastavení konfigurace služby IIS a ASP.NET může ovlivnit propustnost a paměť služby WCF.  Další informace o výkonu ASP.NET najdete v tématu [zlepšení výkonu ASP.NET](https://docs.microsoft.com/previous-versions/msp-n-p/ff647787(v=pandp.10)). Jedno nastavení, které může mít nezamýšlené důsledky, je <xref:System.Web.Configuration.ProcessModelSection.MinWorkerThreads%2A>, což je vlastnost <xref:System.Web.Configuration.ProcessModelSection>. Pokud má vaše aplikace pevný nebo malý počet klientů, nastavení <xref:System.Web.Configuration.ProcessModelSection.MinWorkerThreads%2A> na 2 může poskytovat zvýšení propustnosti na počítači s více procesory, který má využití CPU blízko až 100%. Toto zvýšení výkonu přináší náklady: zvýší se taky využití paměti, což může snížit škálovatelnost.

## <a name="see-also"></a>Viz také:

- [Správa a diagnostika](./diagnostics/index.md)
- [Objemná data a streamování](./feature-details/large-data-and-streaming.md)
