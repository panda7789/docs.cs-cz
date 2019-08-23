---
title: Kompatibilita funkcí s částečnou důvěryhodností
ms.date: 03/30/2017
ms.assetid: a36a540b-1606-4e63-88e0-b7c59e0e6ab7
ms.openlocfilehash: adeef7a8fa12751c53e2096ae6bf844f091a5545
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965318"
---
# <a name="partial-trust-feature-compatibility"></a>Kompatibilita funkcí s částečnou důvěryhodností
Windows Communication Foundation (WCF) podporuje při spuštění v částečně důvěryhodném prostředí omezené podmnožinu funkcí. Funkce podporované v částečném vztahu důvěryhodnosti jsou navržené kolem konkrétní sady scénářů, jak je popsáno v tématu [podporované scénáře nasazení](../../../../docs/framework/wcf/feature-details/supported-deployment-scenarios.md) .  
  
## <a name="minimum-permission-requirements"></a>Minimální požadavky na oprávnění  
 WCF podporuje podmnožinu funkcí v aplikacích spuštěných v jedné z následujících standardních pojmenovaných sad oprávnění:  
  
- Oprávnění střední důvěryhodnosti  
  
- Oprávnění pro internetovou zónu  
  
 Pokus o použití WCF v částečně důvěryhodných aplikacích s více omezujícími oprávněními může za běhu způsobit výjimky zabezpečení.  
  
## <a name="contracts"></a>Kontrakty  
 U kontraktů se při spuštění s částečnou důvěryhodností řídí následující omezení:  
  
- Třída služby, která implementuje `[ServiceContract]` rozhraní, musí mít `public` `public` konstruktor. Pokud definuje `[OperationContract]` metody, musí být `public`. `[ServiceContract]` Pokud místo toho implementuje rozhraní, implementace těchto metod mohou být explicitní nebo `private`, za předpokladu, `[ServiceContract]` že rozhraní `public`je.  
  
- Při použití `[ServiceKnownType]` atributu musí být `public`zadaná metoda.  
  
- `[MessageContract]`třídy a jejich členové mohou být `public`. `internal` `internal` Pokud je `[MessageContract]` třída definovaná v sestavení aplikace, může být a mít členy.  
  
## <a name="system-provided-bindings"></a>Vazby poskytované systémem  
 <xref:System.ServiceModel.BasicHttpBinding> A<xref:System.ServiceModel.WebHttpBinding> jsou plně podporovány v prostředí s částečným vztahem důvěryhodnosti. Podpora <xref:System.ServiceModel.WSHttpBinding> je podporována pouze pro režim zabezpečení přenosu.  
  
 Vazby, které používají jiné přenosy než HTTP, jako <xref:System.ServiceModel.NetTcpBinding>například <xref:System.ServiceModel.NetNamedPipeBinding>, nebo <xref:System.ServiceModel.NetMsmqBinding>, nejsou podporovány při spuštění v prostředí s částečným vztahem důvěryhodnosti.  
  
## <a name="custom-bindings"></a>Vlastní vazby  
 Vlastní vazby lze vytvořit a použít v prostředí s částečným vztahem důvěryhodnosti, ale musí splňovat omezení uvedená v této části.  
  
### <a name="transports"></a>Přenosy  
 Jediné povolené prvky vazby přenosu jsou <xref:System.ServiceModel.Channels.HttpTransportBindingElement> a. <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
### <a name="encoders"></a>Kodérů  
 Jsou povoleny následující kodéry:  
  
- Kodér textu (<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>).  
  
- Binární kodér (<xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>).  
  
- Kodér webové zprávy (<xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>).  
  
 Kodéry mechanismu optimalizace přenosu zpráv (MTOM) nejsou podporovány.  
  
### <a name="security"></a>Zabezpečení  
 Částečně důvěryhodné aplikace mohou používat funkce zabezpečení služby WCF na úrovni přenosu pro zabezpečení jejich komunikace. Zabezpečení na úrovni zpráv se nepodporuje. Konfigurace vazby na použití zabezpečení na úrovni zprávy vede k výjimce za běhu.  
  
### <a name="unsupported-bindings"></a>Nepodporované vazby  
 Vazby, které používají spolehlivé zasílání zpráv, transakce nebo zabezpečení na úrovni zpráv, nejsou podporovány.  
  
## <a name="serialization"></a>Serializace  
 <xref:System.Runtime.Serialization.DataContractSerializer> Ajsoupodporoványvprostředísčástečným<xref:System.Xml.Serialization.XmlSerializer> vztahem důvěryhodnosti. Použití <xref:System.Runtime.Serialization.DataContractSerializer> nástroje však podléhá následujícím podmínkám:  
  
- Všechny serializovatelné `[DataContract]` typy musí `public`být.  
  
- Všechna serializovatelný `[DataMember]` pole nebo vlastnosti `[DataContract]` v typu musí být veřejná a musí mít oprávnění ke čtení a zápisu. Serializace a deserializace polí [jen pro čtení](https://go.microsoft.com/fwlink/?LinkID=98854) není podporována při spuštění WCF v částečně důvěryhodné aplikaci.  
  
- Programovací `[Serializable]`model/ISerializable není podporován v prostředí s částečným vztahem důvěryhodnosti.  
  
- V kódu nebo konfiguraci na úrovni počítače (Machine. config) musí být zadané známé typy. Známé typy nelze v konfiguraci na úrovni aplikace zadat z bezpečnostních důvodů.  
  
- Typy, které <xref:System.Runtime.Serialization.IObjectReference> implementují výjimku, v částečně důvěryhodném prostředí.  
  
 Další informace o zabezpečení při bezpečném použití <xref:System.Runtime.Serialization.DataContractSerializer> v částečně důvěryhodné aplikaci najdete v části serializace v tématu osvědčené [postupy důvěryhodnosti](../../../../docs/framework/wcf/feature-details/partial-trust-best-practices.md) .  
  
### <a name="collection-types"></a>Typy kolekcí  
 Některé typy kolekcí implementují <xref:System.Collections.Generic.IEnumerable%601> i <xref:System.Collections.IEnumerable>. Příklady zahrnují typy, které <xref:System.Collections.Generic.ICollection%601>implementují. Tyto typy mohou implementovat `public` `GetEnumerator()`implementaci `GetEnumerator()`a explicitní implementaci. V tomto případě <xref:System.Runtime.Serialization.DataContractSerializer> vyvolá `public` implementaci `GetEnumerator()`a nikoli explicitní implementaci `GetEnumerator()`. Pokud `GetEnumerator()` žádná z `public` implementací není a všechny jsou explicitní `IEnumerable.GetEnumerator()`implementace, potom <xref:System.Runtime.Serialization.DataContractSerializer> vyvolá.  
  
 Pro typy kolekce, pokud je WCF spuštěno v prostředí s částečným vztahem důvěryhodnosti `GetEnumerator()` , pokud `public`žádná implementace není nebo žádná z nich není explicitní implementací rozhraní, je vyvolána výjimka zabezpečení.  
  
### <a name="netdatacontractserializer"></a>NetDataContractSerializer  
 <xref:System.Collections.Generic.List%601>Mnoho typů kolekcí .NET Framework <xref:System.Collections.Hashtable> <xref:System.Collections.ArrayList> <xref:System.Runtime.Serialization.NetDataContractSerializer> , jako jsou, a,nejsoupodporoványvčástečnémvztahudůvěryhodnosti.<xref:System.Collections.Generic.Dictionary%602> Tyto typy mají `[Serializable]` atribut nastaven a jak je uvedeno dříve v sekci serializace, tento atribut není podporován v částečném vztahu důvěryhodnosti. Zpracovává kolekce zvláštním způsobem a je tak schopné toto omezení obejít, <xref:System.Runtime.Serialization.NetDataContractSerializer> ale nemá žádný takový mechanismus pro obcházení tohoto omezení. <xref:System.Runtime.Serialization.DataContractSerializer>  
  
 Typ není podporován <xref:System.Runtime.Serialization.NetDataContractSerializer> v částečném vztahu důvěryhodnosti. <xref:System.DateTimeOffset>  
  
 Náhradu nelze použít s <xref:System.Runtime.Serialization.NetDataContractSerializer> ( <xref:System.Runtime.Serialization.SurrogateSelector> pomocí mechanismu) při spuštění v částečném vztahu důvěryhodnosti. Všimněte si, že toto omezení platí pro použití náhradního, nikoli jeho serializace.  
  
## <a name="enabling-common-behaviors-to-run"></a>Povolení spouštění běžných chování  
 Chování služby nebo koncového bodu není označené <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atributem (APTCA), který se přidá [ \<do oddílu CommonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) konfiguračního souboru, se nespustí, když se aplikace spustí v prostředí s částečným vztahem důvěryhodnosti a ne. Pokud k tomu dojde, je vyvolána výjimka. Aby se vynutilo spouštění běžných chování, musíte udělat jednu z následujících možností:  
  
- Označte běžné chování <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atributem tak, aby mohl běžet při nasazení jako aplikace s částečnou důvěryhodností. Všimněte si, že položku registru lze nastavit na počítači, aby bylo možné zabránit spuštění sestavení označených APTCA. .  
  
- Zajistěte, aby byla aplikace nasazena jako plně důvěryhodná aplikace, kterou uživatelé nemohou měnit nastavení zabezpečení přístupu kódu pro spuštění aplikace v prostředí s částečným vztahem důvěryhodnosti. Pokud to tak mohou učinit, chování nebude spuštěno a není vyvolána žádná výjimka. Pro zajištění této možnosti si přečtěte možnost **LevelFinal** pomocí [nástroje Caspol. exe (nástroj Code Access Security Policy Tool)](../../../../docs/framework/tools/caspol-exe-code-access-security-policy-tool.md).  
  
 Příklad běžného chování naleznete v tématu [How to: Zamčení koncových bodů v](../../../../docs/framework/wcf/extending/how-to-lock-down-endpoints-in-the-enterprise.md)podniku.  
  
## <a name="configuration"></a>Konfiguraci  
 V případě jedné výjimky může částečně důvěryhodný kód načíst pouze konfigurační oddíly WCF v místním `app.config` souboru. Aby bylo možné načíst konfigurační oddíly WCF, které odkazují na oddíly WCF v souboru Machine. config nebo v kořenovém souboru Web. config, je nutné ConfigurationPermission (bez omezení). Bez tohoto oprávnění, odkazy na konfigurační oddíly WCF (chování, vazby) mimo místní konfigurační soubor způsobí výjimku při načtení konfigurace.  
  
 Jedinou výjimkou je konfigurace známého typu pro serializaci, jak je popsáno v části serializace v tomto tématu.  
  
> [!IMPORTANT]
> Rozšíření konfigurace jsou podporována pouze v případě, že je spuštěna s úplným vztahem důvěryhodnosti.  
  
## <a name="diagnostics"></a>Diagnostika  
  
### <a name="event-logging"></a>Protokolování událostí  
 Omezené protokolování událostí je podporováno v rámci částečné důvěryhodnosti. Do protokolu událostí se zaznamenávají jenom chyby aktivace služby a trasování nebo selhání protokolování zpráv. Maximální počet událostí, které mohou být protokolovány procesem, je 5, aby nedocházelo k nadměrnému zapisování zpráv do protokolu událostí.  
  
### <a name="message-logging"></a>Protokolování zpráv  
 Protokolování zpráv nefunguje, když je WCF spuštěné v prostředí s částečným vztahem důvěryhodnosti. Pokud je tato možnost povolená v rámci částečné důvěryhodnosti, aktivace služby se nezdaří, ale nezaprotokoluje se žádná zpráva.  
  
### <a name="tracing"></a>Trasování  
 Funkce omezeného trasování je k dispozici při spuštění v prostředí s částečným vztahem důvěryhodnosti. V elementu <`listeners`> v konfiguračním souboru jsou <xref:System.Diagnostics.TextWriterTraceListener> jediné typy, které lze přidat, a nové <xref:System.Diagnostics.EventSchemaTraceListener>. Použití standardu <xref:System.Diagnostics.XmlWriterTraceListener> může mít za následek neúplné nebo nesprávné protokoly.  
  
 Podporované zdroje trasování:  
  
- <xref:System.ServiceModel>  
  
- <xref:System.Runtime.Serialization>  
  
- <xref:System.IdentityModel.Claims>, <xref:System.IdentityModel.Policy>, <xref:System.IdentityModel.Selectors>a .<xref:System.IdentityModel.Tokens>  
  
 Následující zdroje trasování nejsou podporovány:  
  
- CardSpace  
  
- <xref:System.IO.Log>  

- [System.ServiceModel.Internal.TransactionBridge](https://docs.microsoft.com/previous-versions/aa346556(v=vs.110))]
  
 Následující členy <xref:System.Diagnostics.TraceOptions> výčtu by neměly být zadány:  
  
- <xref:System.Diagnostics.TraceOptions.Callstack?displayProperty=nameWithType>  
  
- <xref:System.Diagnostics.TraceOptions.ProcessId?displayProperty=nameWithType>  
  
 Při použití trasování v prostředí s částečným vztahem důvěryhodnosti se ujistěte, že má aplikace dostatečná oprávnění k uložení výstupu naslouchacího procesu trasování. Například při použití <xref:System.Diagnostics.TextWriterTraceListener> pro zápis výstupu trasování do textového souboru, zajistěte, aby aplikace měla potřebné FileIOPermission potřebné k úspěšnému zápisu do trasovacího souboru.  
  
> [!NOTE]
> Aby nedošlo k zaplavování trasovacích souborů s duplicitními chybami, WCF zakáže trasování prostředku nebo akce po prvním selhání zabezpečení. K dispozici je jedno trasování výjimek pro každý neúspěšný přístup k prostředkům, při prvním pokusu o přístup k prostředku nebo provedení akce.  
  
## <a name="wcf-service-host"></a>Hostitel služby WCF  
 Hostitel služby WCF nepodporuje částečnou důvěryhodnost. Pokud chcete používat službu WCF v částečném vztahu důvěryhodnosti, nepoužívejte k sestavení vaší služby šablonu projektu knihovny služby WCF v aplikaci Visual Studio. Místo toho vytvořte nový web v aplikaci Visual Studio tak, že vyberete šablonu webu služby WCF, která může hostovat službu na webovém serveru, na kterém je podporována částečná důvěryhodnost WCF.  
  
## <a name="other-limitations"></a>Další omezení  
 Služba WCF je obecně omezená na požadavky na zabezpečení, které na ně ukládají hostitelské aplikace. Pokud je například WCF hostováno v aplikaci prohlížeče XAML (XBAP), vztahuje se na ně omezení pro XBAP, jak je popsáno v [Windows Presentation Foundation zabezpečení částečně důvěryhodného vztahu důvěryhodnosti](https://go.microsoft.com/fwlink/?LinkId=89138).  
  
 Následující další funkce nejsou při spuštění Indigo2 v prostředí s částečným vztahem důvěryhodnosti povolené:  
  
- Rozhraní WMI (Windows Management Instrumentation) (WMI)  
  
- Protokolování událostí je povoleno pouze částečně (viz část diskuze v části **Diagnostika** ).  
  
- Čítače výkonu  
  
 Použití funkcí WCF, které nejsou podporované v prostředí s částečným vztahem důvěryhodnosti, může za běhu způsobit výjimky.  
  
## <a name="unlisted-features"></a>Funkce, které nejsou v seznamu  
 Nejlepším způsobem, jak zjistit, že část informací nebo akce není k dispozici při spuštění v prostředí s částečným vztahem důvěryhodnosti, je pokusit se o přístup k prostředku nebo `try` provést akci uvnitř bloku `catch` a pak chybu. Aby nedošlo k zaplavování trasovacích souborů s duplicitními chybami, WCF zakáže trasování prostředku nebo akce po prvním selhání zabezpečení. K dispozici je jedno trasování výjimek pro každý neúspěšný přístup k prostředkům, při prvním pokusu o přístup k prostředku nebo provedení akce.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>
- <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>
- [Podporované scénáře nasazení](../../../../docs/framework/wcf/feature-details/supported-deployment-scenarios.md)
- [Osvědčené postupy pro částečnou důvěryhodnost](../../../../docs/framework/wcf/feature-details/partial-trust-best-practices.md)
