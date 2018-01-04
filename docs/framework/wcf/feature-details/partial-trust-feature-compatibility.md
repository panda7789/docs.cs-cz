---
title: "Kompatibilita funkcí s částečnou důvěryhodností"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a36a540b-1606-4e63-88e0-b7c59e0e6ab7
caps.latest.revision: "75"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1950a0c4015658affb0b9fa0d7c87a062865144b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="partial-trust-feature-compatibility"></a>Kompatibilita funkcí s částečnou důvěryhodností
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]podporuje omezenou podmnožinou funkce při spuštění v prostředí s částečně důvěryhodné. Funkce podporované v částečné důvěryhodnosti jsou uspořádaná kolem konkrétní sadu scénářů, jak je popsáno v [Podporované scénáře nasazení](../../../../docs/framework/wcf/feature-details/supported-deployment-scenarios.md) tématu.  
  
## <a name="minimum-permission-requirements"></a>Požadavky na minimální oprávnění  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]podporuje podmnožinu funkcí v aplikacích spuštěných v některé z následujících sad standardní pojmenované oprávnění:  
  
-   Střední oprávnění vztahu důvěryhodnosti  
  
-   Oprávnění pro zónu Internetu  
  
 Pokus o použití [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] v částečně důvěryhodné aplikace s víc omezující oprávnění, které může vést k bezpečnostním výjimkám za běhu.  
  
## <a name="contracts"></a>Kontrakty  
 Kontrakty se vztahují následující omezení při spuštění v částečné důvěryhodnosti:  
  
-   Třída služby, který implementuje `[ServiceContract]` rozhraní musí být `public` a mít `public` konstruktor. Pokud ho definuje `[OperationContract]` metod, musí mít `public`. Pokud místo toho implementuje `[ServiceContract]` rozhraní, tato metoda implementace může být explicitní nebo `private`, za předpokladu, že `[ServiceContract]` rozhraní je `public`.  
  
-   Při použití `[ServiceKnownType]` atribut, musí být určená metoda `public`.  
  
-   `[MessageContract]`třídy a jejich členové může být `public`. Pokud `[MessageContract]` třída je definována v sestavení aplikace může být `internal` a mít `internal` členy.  
  
## <a name="system-provided-bindings"></a>Vazby poskytované systémem  
 <xref:System.ServiceModel.BasicHttpBinding> a <xref:System.ServiceModel.WebHttpBinding> jsou plně podporovaný v prostředí s částečnou důvěryhodností. <xref:System.ServiceModel.WSHttpBinding> Je podporovaná jenom na režim zabezpečení přenosu.  
  
 Vazby, které používají přenosy než HTTP, například <xref:System.ServiceModel.NetTcpBinding>, <xref:System.ServiceModel.NetNamedPipeBinding>, nebo <xref:System.ServiceModel.NetMsmqBinding>, nejsou podporovány při spuštění v prostředí s částečnou důvěryhodností.  
  
## <a name="custom-bindings"></a>Vlastní vazby  
 Vlastní vazby lze vytvořit a použít v prostředí s částečnou důvěryhodností, ale musí následovat omezení zadané v této části.  
  
### <a name="transports"></a>Přenosy  
 Jediným povoleny vazby přenosu prvky jsou <xref:System.ServiceModel.Channels.HttpTransportBindingElement> a <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>.  
  
### <a name="encoders"></a>Kódovací moduly  
 Jsou povoleny následující kodéry:  
  
-   Kodér textu (<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>).  
  
-   Binární kodéru (<xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>).  
  
-   Kodér zpráv webové (<xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>).  
  
 Kodéry zpráva přenosu optimalizace mechanismus (MTOM) nejsou podporovány.  
  
### <a name="security"></a>Zabezpečení  
 Částečně důvěryhodné aplikace můžou používat [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]na úrovni přenosu funkce zabezpečení pro zabezpečení komunikace. Zabezpečení na úrovni zpráva není podporováno. Konfigurace vazeb pro použití zprávy úroveň zabezpečení za následek výjimku za běhu.  
  
### <a name="unsupported-bindings"></a>Nepodporované vazby  
 Vazby, které používají spolehlivé zasílání zpráv, transakce nebo zabezpečení na úrovni zpráv nejsou podporovány.  
  
## <a name="serialization"></a>Serializace  
 Jak <xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Xml.Serialization.XmlSerializer> jsou podporovány v prostředí s částečnou důvěryhodností. Však použít <xref:System.Runtime.Serialization.DataContractSerializer> se vztahují následující podmínky:  
  
-   Všechny serializovatelný `[DataContract]` typy musí být `public`.  
  
-   Všechny serializovatelný `[DataMember]` polí a vlastností v `[DataContract]` typ musí být veřejné a pro čtení a zápis. Serializace a deserializace [jen pro čtení](http://go.microsoft.com/fwlink/?LinkID=98854) polí není podporováno při spuštění [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] v aplikaci částečně důvěryhodné.  
  
-   `[Serializable]` /ISerializable programovací model není podporována v prostředí s částečnou důvěryhodností.  
  
-   Známé typy je třeba zadat v konfiguraci úrovně počítače (machine.config) nebo kódu. Známé typy nelze zadat v konfiguraci na úrovni aplikace z bezpečnostních důvodů.  
  
-   Typy, které implementují <xref:System.Runtime.Serialization.IObjectReference> výjimku v prostředí částečně důvěryhodné.  
  
 Najdete v části serializace v [částečné důvěryhodnosti osvědčené postupy](../../../../docs/framework/wcf/feature-details/partial-trust-best-practices.md) Další informace o zabezpečení při použití <xref:System.Runtime.Serialization.DataContractSerializer> bezpečně v aplikaci částečně důvěryhodné.  
  
### <a name="collection-types"></a>Typy kolekcí  
 Některé typy kolekcí obě implementovat <xref:System.Collections.Generic.IEnumerable%601> a <xref:System.Collections.IEnumerable>. Příklady typů, které implementují <xref:System.Collections.Generic.ICollection%601>. Můžete implementovat tyto typy `public` implementace `GetEnumerator()`a explicitní implementaci `GetEnumerator()`. V takovém případě <xref:System.Runtime.Serialization.DataContractSerializer> vyvolá `public` implementace `GetEnumerator()`a ne explicitní implementace `GetEnumerator()`. Pokud žádná z `GetEnumerator()` implementace jsou `public` a všechny explicitní implementace, jsou pak <xref:System.Runtime.Serialization.DataContractSerializer> vyvolá `IEnumerable.GetEnumerator()`.  
  
 Pro kolekci typů při [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] běží v prostředí s částečnou důvěryhodností, pokud žádná z `GetEnumerator()` implementace jsou `public`, nebo žádná z nich jsou explicitní implementace rozhraní a pak je vyvolána výjimka zabezpečení.  
  
### <a name="netdatacontractserializer"></a>NetDataContractSerializer  
 Mnoho typů kolekce rozhraní .NET Framework jako <xref:System.Collections.Generic.List%601>, <xref:System.Collections.ArrayList>, <xref:System.Collections.Generic.Dictionary%602> a <xref:System.Collections.Hashtable> nejsou podporovány <xref:System.Runtime.Serialization.NetDataContractSerializer> v částečné důvěryhodnosti. Tyto typy mají `[Serializable]` atribut nastaven, a jak jsme uvedli dříve v části serializace, tento atribut není podporován v částečné důvěryhodnosti. <xref:System.Runtime.Serialization.DataContractSerializer> Zpracovává kolekce zvláštním způsobem a je proto nemůže získat kolem tohoto omezení, ale <xref:System.Runtime.Serialization.NetDataContractSerializer> nemá žádný takový mechanismus pro toto omezení obejít.  
  
 <xref:System.DateTimeOffset> Typ není podporován <xref:System.Runtime.Serialization.NetDataContractSerializer> v částečné důvěryhodnosti.  
  
 Náhradní nelze použít s <xref:System.Runtime.Serialization.NetDataContractSerializer> (pomocí <xref:System.Runtime.Serialization.SurrogateSelector> mechanismus) při spuštění v částečné důvěryhodnosti. Všimněte si, že toto omezení platí pro použití náhradní, ne na jeho serializace.  
  
## <a name="enabling-common-behaviors-to-run"></a>Povolení společné chování ke spuštění  
 Služba nebo koncový bod chování neoznačené <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atribut (APTCA), které jsou přidány do [ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) oddílu konfiguračního souboru se nespustí, pokud je aplikace spuštěná v částečné důvěryhodnosti v takovém případě je vyvolána prostředí a žádná výjimka. Chcete-li vynutit spuštění společné chování, musíte udělat jednu z následujících možností:  
  
-   Označit chování vaší běžné s <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atribut, aby se může spustit při nasazení jako aplikace s částečnou důvěryhodností. Všimněte si, že položka registru lze nastavit v počítači aby označena APTCA sestavení spuštění. .  
  
-   Zajistěte, aby pokud je aplikace nasazená jako plně důvěryhodné aplikace, uživatelé nemohou upravovat nastavení zabezpečení přístupu kódu ke spuštění aplikace v prostředí s částečnou důvěryhodností. Pokud se zachovají, chování nespustí a nedojde k výjimce. Aby, najdete v článku **levelfinal** možnost pomocí [Caspol.exe (nástroj zásad zabezpečení přístupu kódu)](../../../../docs/framework/tools/caspol-exe-code-access-security-policy-tool.md).  
  
 [!INCLUDE[crexample](../../../../includes/crexample-md.md)]společné chování najdete v části [postup: uzamčení mimo provoz koncovými body v podnikové síti](../../../../docs/framework/wcf/extending/how-to-lock-down-endpoints-in-the-enterprise.md).  
  
## <a name="configuration"></a>Konfigurace  
 S jednou výjimkou mohou načíst pouze částečně důvěryhodného kódu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] konfigurační oddíly funkce v místní `app.config` souboru. Načíst [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] konfigurace částech tento odkaz [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ConfigurationPermission(Unrestricted) vyžaduje oddílů v souboru machine.config nebo v kořenovém souboru web.config. Bez tohoto oprávnění, odkazuje na [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] konfigurační oddíly (chování, vazby) mimo místní konfigurační soubor výsledky v výjimku při načtení konfigurace.  
  
 Jedinou výjimkou je konfigurace známé typ pro serializaci, jak je popsáno v části serializace v tomto tématu.  
  
> [!IMPORTANT]
>  Konfigurace rozšíření jsou podporovány pouze při spuštění v úplný vztah důvěryhodnosti.  
  
## <a name="diagnostics"></a>Diagnostika  
  
### <a name="event-logging"></a>Protokolování událostí  
 Protokolování událostí omezená je podporována v částečné důvěryhodnosti. Pouze služby Aktivace chyb a selhání protokolování trasování/zprávy se zaznamenávají do protokolu událostí. Maximální počet událostí, které mohou být protokolovány procesem je 5, aby se zabránilo nadměrnému zprávy zápis do protokolu událostí.  
  
### <a name="message-logging"></a>Protokolování zpráv  
 Zpráva protokolování nelze použít v případě [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] běží v prostředí s částečnou důvěryhodností. Pokud je povoleno v částečné důvěryhodnosti, neselže aktivace služby, ale je zaznamenána žádná zpráva.  
  
### <a name="tracing"></a>Trasování  
 Funkce s omezeným přístupem trasování je k dispozici při spuštění v prostředí s částečnou důvěryhodností. V <`listeners`> elementu v konfiguračním souboru, jsou pouze typy, které můžete přidat <xref:System.Diagnostics.TextWriterTraceListener> a nové <xref:System.Diagnostics.EventSchemaTraceListener>. Použijte standardní <xref:System.Diagnostics.XmlWriterTraceListener> může mít za následek protokoly neúplné nebo není správný.  
  
 Podporované trasování zdroje jsou:  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.Runtime.Serialization>  
  
-   <xref:System.IdentityModel.Claims>, <xref:System.IdentityModel.Policy>, <xref:System.IdentityModel.Selectors>, a <xref:System.IdentityModel.Tokens>.  
  
 Následující zdroje trasování nejsou podporovány:  
  
-   CardSpace  
  
-   <xref:System.IO.Log>  

-   [System.ServiceModel.Internal.TransactionBridge](https://msdn.microsoft.com/library/system.servicemodel.internal.transactionbridge.aspx)]
  
 Následující členy <xref:System.Diagnostics.TraceOptions> výčtu by neměl být určen:  
  
-   <xref:System.Diagnostics.TraceOptions.Callstack?displayProperty=nameWithType>  
  
-   <xref:System.Diagnostics.TraceOptions.ProcessId?displayProperty=nameWithType>  
  
 Při použití trasování v prostředí s částečnou důvěryhodností, ujistěte se, že aplikace má dostatečná oprávnění k uložení výstup naslouchací proces trasování. Například při použití <xref:System.Diagnostics.TextWriterTraceListener> k zápisu výstupu trasování do textového souboru, zkontrolujte, zda má aplikace potřebné FileIOPermission potřeba úspěšně zapisovat do souboru trasování.  
  
> [!NOTE]
>  Aby nedošlo k zaplavení trasovací soubory s duplicitní chybami [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zakáže trasování prostředku nebo akce po prvním selhání zabezpečení. Prvním je proveden pokus o přístup k prostředku nebo provedení akce není jeden trasování výjimky pro přístup každý prostředek, který selhal.  
  
## <a name="wcf-service-host"></a>Hostitel služby WCF  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Hostitel služby nepodporuje částečnou důvěryhodností. Pokud chcete použít [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby v částečné důvěryhodnosti, nepoužívejte [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] šablona projektu knihovny služby v [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] k vytvoření služby. Místo toho vytvořte nový web v [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] výběrem [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] webu šablony služby, která může hostovat službu na webovém serveru, na kterém [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] částečné důvěryhodnosti je podporována.  
  
## <a name="other-limitations"></a>Další omezení  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]je obecně omezený na aspekty zabezpečení při jeho způsobené hostitelskou aplikaci. Například pokud [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] je hostován v aplikace prohlížeče XAML (XBAP), je předmětem XBAP omezení, jak je popsáno v [zabezpečení systému Windows Presentation Foundation částečné důvěryhodnosti](http://go.microsoft.com/fwlink/?LinkId=89138).  
  
 Při spuštění indigo2 v prostředí s částečnou důvěryhodností nejsou povoleny tyto další funkce:  
  
-   Windows Management Instrumentation (WMI)  
  
-   Protokolování událostí je povolená jen částečně (viz popis v **diagnostiky** části).  
  
-   Čítače výkonu  
  
 Použití [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] funkce, které nejsou podporované v prostředí s částečnou důvěryhodností může mít za následek výjimky za běhu.  
  
## <a name="unlisted-features"></a>Neuvedené funkce  
 Nejlepší způsob, jak zjistit, že je část informace nebo akce není dostupná, když je nainstalován v prostředí s částečnou důvěryhodností k pokusu o přístup k prostředku nebo provádět akce uvnitř `try` blok a potom `catch` selhání. Aby nedošlo k zaplavení trasovací soubory s duplicitní chybami [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zakáže trasování prostředku nebo akce po prvním selhání zabezpečení. Prvním je proveden pokus o přístup k prostředku nebo provedení akce není jeden trasování výjimky pro přístup každý prostředek, který selhal.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>  
 [Podporované scénáře nasazení](../../../../docs/framework/wcf/feature-details/supported-deployment-scenarios.md)  
 [Osvědčené postupy pro částečnou důvěryhodnost](../../../../docs/framework/wcf/feature-details/partial-trust-best-practices.md)
