---
title: Kompatibilita funkcí s částečnou důvěryhodností
ms.date: 03/30/2017
ms.assetid: a36a540b-1606-4e63-88e0-b7c59e0e6ab7
ms.openlocfilehash: 97a51fe29677f46f9d3053250b65b3d818ca47dc
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43864521"
---
# <a name="partial-trust-feature-compatibility"></a>Kompatibilita funkcí s částečnou důvěryhodností
Windows Communication Foundation (WCF) podporuje omezenou podmnožinou funkce při spouštění v částečně důvěryhodném prostředí. Funkce podporované v částečném vztahu důvěryhodnosti jsou navržená kolem konkrétní škálu scénářů, jak je popsáno v [Podporované scénáře nasazení](../../../../docs/framework/wcf/feature-details/supported-deployment-scenarios.md) tématu.  
  
## <a name="minimum-permission-requirements"></a>Požadavky na minimální oprávnění  
 WCF podporuje podmnožinu funkcí v aplikace spuštěné v některé z následujících sad standardní pojmenovaných oprávnění:  
  
-   Střední oprávnění důvěryhodnosti  
  
-   Oprávnění pro zónu Internetu  
  
 Pokus o použití WCF v částečně důvěryhodné aplikace s víc omezující oprávnění může vést k bezpečnostním výjimkám v době běhu.  
  
## <a name="contracts"></a>Kontrakty  
 Kontrakty se vztahují následující omezení při spouštění v částečném vztahu důvěryhodnosti:  
  
-   Třídu služby, který implementuje `[ServiceContract]` rozhraní musí být `public` a mít `public` konstruktoru. Pokud ho definuje `[OperationContract]` metod, musí být `public`. Pokud místo toho implementuje `[ServiceContract]` rozhraní, tyto implementace metody může být explicitní nebo `private`za předpokladu, že `[ServiceContract]` rozhraní je `public`.  
  
-   Při použití `[ServiceKnownType]` atribut, musí být zadaná metoda `public`.  
  
-   `[MessageContract]` třídy a jejich členy, může být `public`. Pokud `[MessageContract]` třída je definována v sestavení aplikace může být `internal` a mít `internal` členy.  
  
## <a name="system-provided-bindings"></a>Vazby poskytované systémem  
 <xref:System.ServiceModel.BasicHttpBinding> a <xref:System.ServiceModel.WebHttpBinding> jsou plně podporovány v prostředí s částečnou důvěryhodností. <xref:System.ServiceModel.WSHttpBinding> Je podporováno pouze v režimu zabezpečení přenosu.  
  
 Vazby, které používají přenosy jiné než HTTP, jako <xref:System.ServiceModel.NetTcpBinding>, <xref:System.ServiceModel.NetNamedPipeBinding>, nebo <xref:System.ServiceModel.NetMsmqBinding>, nejsou podporovány při spouštění v prostředí s částečnou důvěryhodností.  
  
## <a name="custom-bindings"></a>Vlastní vazby  
 Vlastní vazby je možné vytvořit a použít v prostředí s částečnou důvěryhodností, ale musí dodržovat omezení uvedených v této části.  
  
### <a name="transports"></a>Přenosy  
 Jediným povoleným názvem vazby přenosu prvky jsou <xref:System.ServiceModel.Channels.HttpTransportBindingElement> a <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>.  
  
### <a name="encoders"></a>Kodérů  
 Jsou povoleny následující kodéry:  
  
-   Kodér textu (<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>).  
  
-   Binárního kodéru (<xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>).  
  
-   Kodér zprávy Web (<xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>).  
  
 Kodérů zpráv přenosu optimalizace mechanismus (MTOM) nejsou podporovány.  
  
### <a name="security"></a>Zabezpečení  
 Částečně důvěryhodné aplikace můžou využívat funkce zabezpečení na úrovni přenosu WCF. pro zabezpečení komunikace. Zabezpečení na úrovni zprávy se nepodporuje. Konfigurace vazby pro použití zabezpečení na úrovni zpráv za následek výjimku za běhu.  
  
### <a name="unsupported-bindings"></a>Nepodporované vazby  
 Vazby, které používají spolehlivé zasílání zpráv, transakce nebo zabezpečení na úrovni zpráv nejsou podporovány.  
  
## <a name="serialization"></a>Serializace  
 Jak <xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Xml.Serialization.XmlSerializer> jsou podporovány v prostředí s částečnou důvěryhodností. Nicméně použití <xref:System.Runtime.Serialization.DataContractSerializer> podléhá následující podmínky:  
  
-   Všechny serializovatelný `[DataContract]` typy musí být `public`.  
  
-   Všechny serializovatelný `[DataMember]` pole nebo vlastnosti v `[DataContract]` typ musí být veřejný a čtení a zápisu. Serializace a deserializace [jen pro čtení](https://go.microsoft.com/fwlink/?LinkID=98854) polí není podporováno při spouštění v částečně důvěryhodné aplikaci WCF.  
  
-   `[Serializable]` /ISerializable programovacího modelu není podporován v částečném vztahu důvěryhodnosti prostředí.  
  
-   Známé typy je třeba zadat v kódu nebo konfigurace na úrovni počítače (machine.config). Známé typy nelze zadat v konfigurace na úrovni aplikace z bezpečnostních důvodů.  
  
-   Typy, které implementují <xref:System.Runtime.Serialization.IObjectReference> vyvolat výjimku v částečně důvěryhodném prostředí.  
  
 V části serializace v [částečné důvěryhodnosti osvědčené postupy](../../../../docs/framework/wcf/feature-details/partial-trust-best-practices.md) Další informace o zabezpečení při použití <xref:System.Runtime.Serialization.DataContractSerializer> bezpečně v částečně důvěryhodné aplikaci.  
  
### <a name="collection-types"></a>Typy kolekcí  
 Některé typy kolekcí implementovat oba <xref:System.Collections.Generic.IEnumerable%601> a <xref:System.Collections.IEnumerable>. Mezi příklady patří typy, které implementují <xref:System.Collections.Generic.ICollection%601>. Tyto typy můžou implementovat `public` provádění `GetEnumerator()`a explicitní implementaci `GetEnumerator()`. V takovém případě <xref:System.Runtime.Serialization.DataContractSerializer> vyvolá `public` provádění `GetEnumerator()`a ne explicitní implementaci `GetEnumerator()`. Pokud žádná z `GetEnumerator()` implementace jsou `public` a jsou všechny explicitní implementací, pak <xref:System.Runtime.Serialization.DataContractSerializer> vyvolá `IEnumerable.GetEnumerator()`.  
  
 U typů kolekce při WCF běží v částečném vztahu důvěryhodnosti prostředí, pokud žádná z `GetEnumerator()` implementace jsou `public`, nebo žádná z nich jsou implementace explicitního rozhraní a pak je vyvolána výjimka zabezpečení.  
  
### <a name="netdatacontractserializer"></a>NetDataContractSerializer  
 Mnoho typů kolekce rozhraní .NET Framework, jako <xref:System.Collections.Generic.List%601>, <xref:System.Collections.ArrayList>, <xref:System.Collections.Generic.Dictionary%602> a <xref:System.Collections.Hashtable> nejsou podporovány <xref:System.Runtime.Serialization.NetDataContractSerializer> v částečném vztahu důvěryhodnosti. Tyto typy mají `[Serializable]` nastaven atribut a jak bylo uvedeno dříve v části serializace, tento atribut není podporován v částečném vztahu důvěryhodnosti. <xref:System.Runtime.Serialization.DataContractSerializer> Zpracovává kolekce zvláštním způsobem a je tedy možné jsme toto omezení, ale <xref:System.Runtime.Serialization.NetDataContractSerializer> nemá žádný takový mechanismus pro toto omezení obejít.  
  
 <xref:System.DateTimeOffset> Typ není podporován <xref:System.Runtime.Serialization.NetDataContractSerializer> v částečném vztahu důvěryhodnosti.  
  
 Náhradní nelze použít s <xref:System.Runtime.Serialization.NetDataContractSerializer> (pomocí <xref:System.Runtime.Serialization.SurrogateSelector> mechanismus) při spouštění v částečném vztahu důvěryhodnosti. Všimněte si, že toto omezení platí pro použití náhradní, ne k jeho serializace.  
  
## <a name="enabling-common-behaviors-to-run"></a>Povolení společné chování pro spuštění  
 Chování služby nebo koncového bodu není označené <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atribut (APTCA), které jsou přidány do [ \<commonBehaviors >](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) oddílu konfiguračního souboru se nespustí, když aplikace běží v částečném vztahu důvěryhodnosti Pokud k tomu dojde, je vyvolána prostředí a žádná výjimka. Pokud chcete vynutit spuštění společné chování, musíte udělat jednu z následujících možností:  
  
-   Označit vaše běžné chování s <xref:System.Security.AllowPartiallyTrustedCallersAttribute> atribut tak, aby ji můžete spustit po nasazení jako aplikace s částečnou důvěryhodností. Všimněte si, že položka registru můžete nastavit v počítači zabránit sestavení APTCA označené spouštění. .  
  
-   Ujistěte se, že pokud je aplikace nasazená jako plně důvěryhodné aplikace, uživatelé nemohou upravovat nastavení zabezpečení přístupu kódu a spusťte aplikaci v prostředí s částečnou důvěryhodností. Pokud můžete, chování se nespustí a není vyvolána žádná výjimka. Aby se zajistilo to, najdete v článku **levelfinal** možnost použití [Caspol.exe (nástroj zásad zabezpečení přístupu kódu)](../../../../docs/framework/tools/caspol-exe-code-access-security-policy-tool.md).  
  
 Příklad běžné chování najdete v tématu [jak: zámek dolů koncových bodů v podniku](../../../../docs/framework/wcf/extending/how-to-lock-down-endpoints-in-the-enterprise.md).  
  
## <a name="configuration"></a>Konfigurace  
 S jednou výjimkou může částečně důvěryhodným kódem načíst jenom WCF konfigurační oddíly funkce v místním `app.config` souboru. Načíst WCF konfigurační oddíly funkce, které odkazují na části WCF v souboru machine.config nebo kořenového souboru web.config vyžaduje ConfigurationPermission(Unrestricted). Bez tohoto oprávnění odkazy na WCF konfigurační oddíly (chování, vazby) mimo místní konfigurační soubor výsledkem výjimku při načtení konfigurace.  
  
 Jedinou výjimkou je známý typ konfigurace pro serializaci, jak je popsáno v části serializace v tomto tématu.  
  
> [!IMPORTANT]
>  Konfigurace rozšíření jsou podporovány pouze při spuštění v plné důvěryhodnosti.  
  
## <a name="diagnostics"></a>Diagnostika  
  
### <a name="event-logging"></a>Protokolování událostí  
 Omezené události protokolování je podporován v částečném vztahu důvěryhodnosti. Pouze služba Aktivace chyb a selhání protokolování trasování/zpráv jsou protokolovány do protokolu událostí. Maximální počet událostí, které můžete protokolovat procesem je 5, aby se zabránilo nadměrnému zprávy zápisu do protokolu událostí.  
  
### <a name="message-logging"></a>Protokolování zpráv  
 Protokolování zpráv nefunguje při spuštění WCF v prostředí s částečnou důvěryhodností. Pokud je povoleno v částečném vztahu důvěryhodnosti, neselže pro aktivaci služeb, ale je zaznamenána žádná zpráva.  
  
### <a name="tracing"></a>Trasování  
 Omezené trasování funkce je k dispozici při spuštění v prostředí s částečnou důvěryhodností. V <`listeners`> element v konfiguračním souboru, jsou pouze typy, které můžete přidat <xref:System.Diagnostics.TextWriterTraceListener> a nové <xref:System.Diagnostics.EventSchemaTraceListener>. Použití standardu <xref:System.Diagnostics.XmlWriterTraceListener> může způsobit nesprávné nebo neúplné protokoly.  
  
 Podporované trasování zdroje jsou:  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.Runtime.Serialization>  
  
-   <xref:System.IdentityModel.Claims>, <xref:System.IdentityModel.Policy>, <xref:System.IdentityModel.Selectors>, a <xref:System.IdentityModel.Tokens>.  
  
 Nejsou podporovány následující zdroje trasování:  
  
-   CardSpace  
  
-   <xref:System.IO.Log>  

-   [System.ServiceModel.Internal.TransactionBridge](https://msdn.microsoft.com/library/system.servicemodel.internal.transactionbridge.aspx)]
  
 Následující členové <xref:System.Diagnostics.TraceOptions> by neměl být zadaný výčet:  
  
-   <xref:System.Diagnostics.TraceOptions.Callstack?displayProperty=nameWithType>  
  
-   <xref:System.Diagnostics.TraceOptions.ProcessId?displayProperty=nameWithType>  
  
 Při použití trasování v částečně důvěryhodném prostředí, ujistěte se, že aplikace má dostatečná oprávnění k uložení výstupu naslouchací služby stopy. Například při použití <xref:System.Diagnostics.TextWriterTraceListener> zapisovat výstup trasování do textového souboru, ujistěte se, že aplikace má potřebné FileIOPermission vyžadovaných k zápisu úspěšně pro trasovacího souboru.  
  
> [!NOTE]
>  Aby nedošlo k zaplavení trasovací soubory s duplicitní chyby, zakáže WCF sledování prostředku nebo akce po prvním selhání zabezpečení. Existuje jedna výjimka trasování pro každý přístup k problémovému prostředku poprvé, který je proveden pokus o přístup k prostředku nebo provedení akce.  
  
## <a name="wcf-service-host"></a>Hostitel služby WCF  
 Hostitel služby WCF nepodporuje částečným vztahem důvěryhodnosti. Pokud chcete použít službu WCF v částečném vztahu důvěryhodnosti, nepoužívejte šablony projektu Knihovna služby WCF v sadě Visual Studio k vytvoření vaší služby. Místo toho vytvořte nový web v sadě Visual Studio výběrem šablony webu služby WCF, která může hostovat službu na webovém serveru, na kterém se podporuje částečné důvěryhodnosti WCF.  
  
## <a name="other-limitations"></a>Další omezení  
 WCF je obvykle omezená na aspekty zabezpečení podle ní stanovené hostitelské aplikace. Například pokud WCF je hostitelem v aplikace prohlížeče XAML (XBAP), je v souladu s omezeními XBAP, jak je popsáno v [Windows Presentation Foundation částečné důvěryhodnosti zabezpečení](https://go.microsoft.com/fwlink/?LinkId=89138).  
  
 Tyhle další funkce nejsou povoleny při spuštění indigo2 v prostředí s částečným vztahem důvěryhodnosti:  
  
-   Windows Management Instrumentation (WMI)  
  
-   Protokolování událostí je povolená jen částečně (viz diskuze v **diagnostiky** části).  
  
-   Čítače výkonu  
  
 Využívání funkce WCF, které nejsou podporovány v prostředí s částečnou důvěryhodností může vést k výjimkám v době běhu.  
  
## <a name="unlisted-features"></a>Neuvedené v seznamu funkcí  
 Nejlepší způsob, jak zjistit, že část informací nebo akce není k dispozici při spuštění v prostředí s částečnou důvěryhodností pro pokus o přístup k prostředku nebo provedení akce uvnitř `try` bloku a potom `catch` selhání. Aby nedošlo k zaplavení trasovací soubory s duplicitní chyby, zakáže WCF sledování prostředku nebo akce po prvním selhání zabezpečení. Existuje jedna výjimka trasování pro každý přístup k problémovému prostředku poprvé, který je proveden pokus o přístup k prostředku nebo provedení akce.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
 <xref:System.ServiceModel.Channels.WebMessageEncodingBindingElement>  
 [Podporované scénáře nasazení](../../../../docs/framework/wcf/feature-details/supported-deployment-scenarios.md)  
 [Osvědčené postupy pro částečnou důvěryhodnost](../../../../docs/framework/wcf/feature-details/partial-trust-best-practices.md)
