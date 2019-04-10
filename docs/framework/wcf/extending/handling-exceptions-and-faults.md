---
title: Zpracování výjimek a chyb
ms.date: 03/30/2017
ms.assetid: a64d01c6-f221-4f58-93e5-da4e87a5682e
ms.openlocfilehash: c29b3900a36d8d5c41fee49c408a2e3fdf67680b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59343425"
---
# <a name="handling-exceptions-and-faults"></a>Zpracování výjimek a chyb
Výjimky se používají k předání chyby místně v rámci služby nebo implementace klienta. Chyby, na druhé straně, se používají k předání chyby přes hranice služeb, jako například ze serveru klientovi nebo naopak. Kromě chyb přenosové kanály často používají mechanismy specifické pro přenos komunikace chyb na úrovni přenosu. Například přenos pomocí protokolu HTTP používá stavové kódy, jako je například 404 ke komunikaci neexistující adresa URL koncového bodu (neexistuje žádný koncový bod má být zaslán zpět chybu). Tento dokument se skládá z tři oddíly, které poskytují pokyny pro autory vlastního kanálu. První část obsahuje pokyny k kdy a jak definovat a vyvolávat výjimky. Druhá část obsahuje pokyny týkající se vytváření a využívání chyb. Třetí část vysvětluje, jak poskytnout informace o trasování pro řešení potíží s běžící aplikací uživatele vlastního kanálu.  
  
## <a name="exceptions"></a>Výjimky  
 Mějte na paměti při vyvolání výjimky dvě věci: Nejprve musí být typu, který umožňuje zapisovat správný kód, který může reagovat odpovídajícím způsobem na výjimku. Za druhé má poskytnout dostatek informací pro uživatele k pochopení toho, co nefunguje, dopad selhání a jak ho opravit. Následující části poskytují pokyny týkající se typy výjimek a zprávy pro kanály Windows Communication Foundation (WCF). Je také obecné pokyny k jeho výjimek v rozhraní .NET v pokyny návrhu pro výjimky dokumentu.  
  
### <a name="exception-types"></a>Typy výjimek  
 Všechny výjimky vyvolané kanály musí být buď <xref:System.TimeoutException?displayProperty=nameWithType>, <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>, nebo typ odvozený od <xref:System.ServiceModel.CommunicationException>. (Například výjimky <xref:System.ObjectDisposedException> může také být vyvolána výjimka, ale pouze pro označení, že volající kód má potenciálně nebezpečného kanál. Pokud se používá kanál, se musí pouze vyvolat dané výjimky.) WCF obsahuje sedm typy výjimek, které jsou odvozeny z <xref:System.ServiceModel.CommunicationException> a jsou navržené pro kanály. Existují jiné <xref:System.ServiceModel.CommunicationException>-odvozené výjimky, které jsou navrženy pro použití jinými částmi systému. Tyto typy výjimek jsou:  
  
|Typ výjimky|Význam|Obsah v popisu vnitřní výjimky|Strategie zotavení|  
|--------------------|-------------|-----------------------------|-----------------------|  
|<xref:System.ServiceModel.AddressAlreadyInUseException>|Zadaná adresa koncového bodu pro naslouchání je již používán.|Pokud jsou k dispozici, poskytuje další podrobnosti o chybě přenosu, která způsobila tuto výjimku. Např. <xref:System.IO.PipeException>, <xref:System.Net.HttpListenerException>, nebo <xref:System.Net.Sockets.SocketException>.|Zkuste jinou adresu.|  
|<xref:System.ServiceModel.AddressAccessDeniedException>|Proces není povolený přístup k adresu koncového bodu, který je zadán pro naslouchání.|Pokud jsou k dispozici, poskytuje další podrobnosti o chybě přenosu, která způsobila tuto výjimku. Například <xref:System.IO.PipeException>, nebo <xref:System.Net.HttpListenerException>.|Zkuste s jinými přihlašovacími údaji.|  
|<xref:System.ServiceModel.CommunicationObjectFaultedException>|<xref:System.ServiceModel.ICommunicationObject> Používá je v chybovém stavu (Další informace najdete v tématu [změny stavu Principy](../../../../docs/framework/wcf/extending/understanding-state-changes.md)). Všimněte si, že když objekt s více čekající volání přejde do stavu chyba pouze jedno volání, vyvolá výjimku, týkající se selhání a zbytek throw volání <xref:System.ServiceModel.CommunicationObjectFaultedException>. Tato výjimka je obvykle vyvolána, protože aplikace overlooks některé výjimky a pokusí se použít objekt již chybnou pravděpodobně ve vlákně, než která byla zachycena výjimka původní.|Pokud jsou k dispozici obsahuje podrobné informace o vnitřní výjimce.|Vytvořte nový objekt. Všimněte si, že v závislosti na tom, co způsobilo <xref:System.ServiceModel.ICommunicationObject> k selhání na prvním místě, může být jiné práce potřebné k obnovení.|  
|<xref:System.ServiceModel.CommunicationObjectAbortedException>|<xref:System.ServiceModel.ICommunicationObject> Používá byla přerušena. (Další informace najdete v tématu [změny stavu Principy](../../../../docs/framework/wcf/extending/understanding-state-changes.md)). Podobně jako <xref:System.ServiceModel.CommunicationObjectFaultedException>, jeho výjimka označuje, že aplikace volala <xref:System.ServiceModel.ICommunicationObject.Abort%2A> na objekt, případně z jiného vlákna, a objekt již není použitelné z tohoto důvodu.|Pokud jsou k dispozici obsahuje podrobné informace o vnitřní výjimce.|Vytvořte nový objekt. Všimněte si, že v závislosti na tom, co způsobilo <xref:System.ServiceModel.ICommunicationObject> přerušit na prvním místě, může být jiné práce potřebné k obnovení.|  
|<xref:System.ServiceModel.EndpointNotFoundException>|Vzdálený koncový bod cíl nenaslouchá. To může být následek libovolné části adresu koncového bodu je nesprávná, nevyřešitelná nebo koncový bod se dolů. Mezi příklady patří chybu DNS, správce fronty není k dispozici a služba není spuštěná.|Vnitřní výjimka obsahuje podrobné informace, typicky ze základní přenos.|Zkuste jinou adresu. Alternativně může odesílatel chvíli počkejte a zkuste to znovu v případě, že služba se dolů|  
|<xref:System.ServiceModel.ProtocolException>|Komunikační protokoly, jak je popsáno v zásad koncového bodu se neshoda mezi koncovými body. Například rámců Neshoda typu obsahu nebo překročila se maximální počet zpráv velikost.|Pokud jsou k dispozici poskytuje další informace o chybě určitý protokol. Například <xref:System.ServiceModel.QuotaExceededException> je vnitřní výjimka, pokud příčina chyby je vyšší než MaxReceivedMessageSize.|Obnovení: Zajištění odesílatele a přijaté protokolu, které odpovídají nastavení. Jedním ze způsobů, provedete to tak je znovu importovat metadata koncový bod služby (zásady) a znovu vytvořit kanál pomocí generovaného vazby.|  
|<xref:System.ServiceModel.ServerTooBusyException>|Vzdálený koncový bod naslouchá, ale není připravená pro zpracování zpráv.|Pokud jsou k dispozici, poskytuje vnitřní výjimka nastala chyba protokolu SOAP nebo podrobnosti o chybě na úrovni přenosu.|Obnovení: Počkejte a zkuste operaci zopakovat později.|  
|<xref:System.TimeoutException>|Operaci se nepodařilo dokončit v časovém limitu.|Může poskytnout podrobnosti o časový limit.|Počkejte a zkuste operaci zopakovat později.|  
  
 Definujte nový typ výjimky, pouze v případě, že tento typ odpovídá strategii pro konkrétní zotavení odlišné od všech existujících typů výjimek. Pokud definujete nový typ výjimky, musí být odvozen od <xref:System.ServiceModel.CommunicationException> nebo jeden z jeho odvozených tříd.  
  
### <a name="exception-messages"></a>Zprávy o výjimkách  
 Zprávy o výjimkách, které jsou zaměřeny na uživatele není program, se musí poskytovat dostatečné informace umožňující uživateli pochopit a vyřešit problém. Jsou tři základní části zprávy dobré výjimka:  
  
 Co se přihodilo. Zadejte jasný popis problému pomocí termínů, které se týkají prostředí uživatele. Například by zpráva chybná výjimky "Neplatný konfigurační oddíl". Kvůli tomu uživatele zajímá vás, jaké konfiguračního oddílu je nesprávný a proč je nesprávný. Vylepšené zprávy by "Neplatný konfigurační oddíl \<customBinding >". Zpráva ještě lepší by bylo "nelze přidat přenosu s názvem myTransport pro vazbu s názvem myBinding, protože vazba již přenosu s názvem myTransport". To je velmi konkrétní zprávu pomocí podmínek a názvy, které uživatele, snadno zjistíte v konfiguračním souboru aplikace. Existují však ještě několik klíčových komponent chybí.  
  
 Význam chybu. Pokud zpráva s oznámením jasně znamená chybu, uživatel by mohla zajímat, jestli se o závažnou chybu nebo pokud se to dá ignorovat. Obecně platí by měl vést zprávy s význam nebo závažnosti chyby. Aby se zvýšil z předchozího příkladu, může být zpráva "hostitel služby se nepodařilo otevřít kvůli chybě v konfiguraci: Nelze přidat přenosu s názvem myTransport pro vazbu s názvem myBinding, protože vazba již přenosu s názvem myTransport ".  
  
 Jak uživatel má problém. Nejdůležitější část zprávy pomáhá uživatele vyřešit problém. Zpráva by měl obsahovat některé pokyny nebo nápovědu, jak zkontrolovat nebo opravit a odstranění problému. Například "hostitel služby se nepodařilo otevřít kvůli chybě v konfiguraci: Nelze přidat přenosu s názvem myTransport pro vazbu s názvem myBinding, protože vazba již přenosu s názvem myTransport. Ujistěte se, že existuje pouze jeden přenosu ve vazbě".  
  
## <a name="communicating-faults"></a>Komunikaci chyb  
 Protokol SOAP 1.1 a SOAP 1.2 definovat strukturu specifické pro chyby. Existuje několik rozdílů mezi dvěma specifikace, ale obecně typy zpráv a objekt MessageFault se používají k vytváření a využívání chyb.  
  
 ![Zpracování výjimek a chyb](../../../../docs/framework/wcf/extending/media/wcfc-soap1-1andsoap1-2faultcomparisonc.gif "wcfc_SOAP1. 1AndSOAP1 2FaultComparisonc")  
Ze SOAP 1.2 selhání (vlevo) a Chyba protokolu SOAP 1.1 (vpravo). Upozorňujeme, že v protokolu SOAP 1.1 pouze element selhání oboru názvů.  
  
 SOAP definuje zprávu o chybě jako zprávu, která obsahuje jenom chyby element (element, jehož název je `<env:Fault>`) jako podřízený objekt `<env:Body>`. Obsah elementu selhání mírně mezi SOAP 1.1 a SOAP 1.2, jak je znázorněno na obrázku 1. Ale <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType> normalizuje tyto rozdíly do modelu jeden objekt třídy:  
  
```  
public abstract class MessageFault  
{  
    protected MessageFault();  
  
    public virtual string Actor { get; }  
    public virtual string Node { get; }  
    public static string DefaultAction { get; }  
    public abstract FaultCode Code { get; }  
    public abstract bool HasDetail { get; }  
    public abstract FaultReason Reason { get; }  
  
    public T GetDetail<T>();  
    public T GetDetail<T>( XmlObjectSerializer serializer);  
    public System.Xml.XmlDictionaryReader GetReaderAtDetailContents();  
  
    // other methods omitted  
}  
```  
  
 `Code` Odpovídá vlastnosti `env:Code` (nebo `faultCode` v protokolu SOAP 1.1) a identifikuje typ chyby. Protokol SOAP 1.2 definuje pět povolené hodnoty pro `faultCode` (například odesílatel a příjemce) a definuje `Subcode` element, který může obsahovat libovolnou hodnotu podřízeného. (Viz [specifikace SOAP 1.2](https://go.microsoft.com/fwlink/?LinkId=95176) seznam povolených chybových kódů a jejich význam.) Protokol SOAP 1.1 má mírně odlišné mechanismus: Definuje čtyři `faultCode` hodnoty (například klient a Server), které můžete rozšířit definováním zcela nové značky nebo vytvořte konkrétnější pomocí zápisu s tečkou `faultCodes`, například Client.Authentication.  
  
 Když použijete objekt MessageFault na chyby programu, FaultCode.Name a FaultCode.Namespace mapuje na název a obor názvů SOAP 1.2 `env:Code` nebo SOAP 1.1 `faultCode`. Mapuje FaultCode.SubCode `env:Subcode` pro SOAP 1.2 a má hodnotu null. pro protokol SOAP 1.1.  
  
 Měli byste vytvořit nový dílčí kódy chyb (nebo nové kódy chyb při použití protokolu SOAP 1.1) Pokud je zajímavé programově rozlišit chybu. Toto je analogická k vytvoření nového typu výjimky. Neměli byste pomocí zápisu s tečkou s kódy chyb protokolu SOAP 1.1. ( [WS-I Basic Profile](https://go.microsoft.com/fwlink/?LinkId=95177) také odrazuje od pomocí zápisu s tečkou kód chyby.)  
  
```  
public class FaultCode  
{  
    public FaultCode(string name);  
    public FaultCode(string name, FaultCode subCode);  
    public FaultCode(string name, string ns);  
    public FaultCode(string name, string ns, FaultCode subCode);  
  
    public bool IsPredefinedFault { get; }  
    public bool IsReceiverFault { get; }  
    public bool IsSenderFault { get; }  
    public string Name { get; }  
    public string Namespace { get; }  
    public FaultCode SubCode { get; }  
  
//  methods omitted  
  
}  
```  
  
 `Reason` Odpovídá vlastnosti `env:Reason` (nebo `faultString` v protokolu SOAP 1.1) čitelný popis podobná zpráva výjimce chybový stav. `FaultReason` Třídu (a SOAP `env:Reason/faultString`) obsahuje integrovanou podporu s více překlady větší globalizace.  
  
```  
public class FaultReason  
{  
    public FaultReason(FaultReasonText translation);  
    public FaultReason(IEnumerable<FaultReasonText> translations);  
    public FaultReason(string text);  
  
    public SynchronizedReadOnlyCollection<FaultReasonText> Translations   
    {   
       get;   
    }  
  
 }  
```  
  
 Obsah podrobnosti o selhání jsou zveřejněné na objekt MessageFault pomocí různých metod, včetně `GetDetail` \<T > a `GetReaderAtDetailContents`(). Detail chyby se element neprůhledné pro další podrobnosti o chybu provádění. To je užitečné, pokud je některé libovolného strukturovaných podrobností, které chcete provést s chyby.  
  
### <a name="generating-faults"></a>Generování chyb  
 Tato část vysvětluje proces generuje chybu v reakci na chybový stav zjištění v kanálu nebo do zprávy vlastnost vytvořený kanál. Typickým příkladem je odesílá zpět chybu v reakci na zprávu požadavku, která obsahuje neplatná data.  
  
 Při generování chybu, vlastním kanálu by neměl přímo odeslat chyby, místo toho by měla vyvolat výjimku a nechat vrstvu nad rozhodnout, jestli se má převést tuto výjimku na chybu a jak ji odeslat. Pro tento převod, by měly poskytnout kanál `FaultConverter` implementace, která můžete převést výjimku vyvolanou ve vlastním kanálu pro příslušné chyby. `FaultConverter` je definována takto:  
  
```  
public class FaultConverter  
{  
    public static FaultConverter GetDefaultFaultConverter(  
                                   MessageVersion version);  
    protected abstract bool OnTryCreateFaultMessage(  
                                   Exception exception,   
                                   out Message message);  
    public bool TryCreateFaultMessage(  
                                   Exception exception,   
                                   out Message message);  
}  
```  
  
 Každý kanál, který generuje vlastní chyby musí implementovat `FaultConverter` a vrátit ji z volání `GetProperty<FaultConverter>`. Vlastní `OnTryCreateFaultMessage` implementace musí převést do srozumitelného chybu nebo delegovat do vnitřního kanálu `FaultConverter`. Pokud je kanál přenosu musí, buď ji převést do srozumitelného nebo delegovat kodér `FaultConverter` nebo výchozí hodnotu `FaultConverter` součástí WCF. Výchozí hodnota `FaultConverter` převede chyby odpovídající chybové zprávy určené WS-Addressing a SOAP. Tady je příklad `OnTryCreateFaultMessage` implementace.  
  
```  
public override bool OnTryCreateFaultMessage(Exception exception,   
                                             out Message message)  
{  
    if (exception is ...)  
    {  
        message = ...;  
        return true;  
    }  
  
#if IMPLEMENTING_TRANSPORT_CHANNEL  
    FaultConverter encoderConverter =   
                    this.encoder.GetProperty<FaultConverter>();  
    if ((encoderConverter != null) &&               
        (encoderConverter.TryCreateFaultMessage(  
         exception, out message)))  
    {  
        return true;  
    }  
  
    FaultConverter defaultConverter =   
                   FaultConverter.GetDefaultFaultConverter(  
                   this.channel.messageVersion);  
    return defaultConverter.TryCreateFaultMessage(  
                   exception,   
                   out message);  
#else  
    FaultConverter inner =   
                   this.innerChannel.GetProperty<FaultConverter>();  
    if (inner != null)  
    {  
        return inner.TryCreateFaultMessage(exception, out message);  
    }  
    else  
    {  
        message = null;  
        return false;  
    }  
#endif  
}  
```  
  
 Důsledkem tohoto modelu je, že výjimky vyvolané mezi vrstvami pro chybové podmínky, které vyžadují chyby musí obsahovat dostatek informací pro odpovídající generátor selhání vytvoření správné chyby. Jako vlastní kanál Autor můžete definovat typy výjimek, které odpovídají různých chybových podmínek, je-li tyto výjimky již neexistují. Všimněte si, že byste neprůhledné odolnost dat. chybová podmínka spíše než komunikovat výjimky procházení vrstvám kanálu.  
  
### <a name="fault-categories"></a>Kategorie chyby  
 Existují obecně tři kategorie chyb:  
  
1. Chyby, které se objevují v rámci celý zásobník. Tyto chyby by mohlo dojít v libovolné vrstvě v zásobníku kanál, třeba InvalidCardinalityAddressingException.  
  
2. Chyby, které mohou být došlo k kdekoli nad určitým vrstvou v zásobníku například některé chyby, které se týkají sdružení transakcí nebo k rolím zabezpečení.  
  
3. Chyby, které jsou směrované na jedné vrstvy v zásobníku, například chyby, jako je číslo chyby WS-RM pořadí.  
  
 Kategorie 1. Chyby jsou obvykle WS-Addressing a chyb SOAP. Základní `FaultConverter` třídy poskytované službou WCF chyby převede odpovídající chybové zprávy specifikované WS-Addressing a SOAP, není nutné ke zpracování převodu těchto výjimek sami.  
  
 Kategorie 2. K chybám dochází při vrstvy přidá vlastnost na zprávu, která úplně nespotřebovává zpráva informace, které se vztahují k této vrstvě. Chyby může později zjistit, když vyšší vrstvu zeptá vlastnost zprávy zpracovávat další informace o zprávě. Tyto kanály by měly implementovat `GetProperty` zadaný dříve umožňuje vyšší vrstvě má být zaslán zpět správné chyby. Příkladem je TransactionMessageProperty. Tato vlastnost se přidá do zprávy bez plně ověřování všechna data v hlavičce (díky tomu může zahrnovat kontaktování koordinátor distribuovaných transakcí (DTC).  
  
 Kategorie 3. Chyby jsou pouze vygenerovat a odeslat pomocí jedné vrstvy v procesoru. Proto všechny výjimky jsou obsaženy v rámci vrstvy. Vylepšit konzistenci mezi kanály a snadné údržby, měli by používat vlastní kanál vzoru určenému dříve generovat selhání i pro interní chyby.  
  
### <a name="interpreting-received-faults"></a>Interpretace přijatých chyb  
 Tato část obsahuje pokyny pro generování vhodná výjimka při přijímání zprávu o chybě. Rozhodovací strom pro zpracování zprávy v každé vrstvě v zásobníku je následujícím způsobem:  
  
1. Pokud zpráva není platný za vrstvu, vrstvy proveďte jeho zpracování "Neplatná zpráva". Toto zpracování je specifická pro vrstvy, ale mohou obsahovat vyřazením zprávy trasování, nebo došlo k výjimce, která získá převedeny na chybu. Mezi příklady patří zabezpečení, které přijímají zprávy, která nejsou řádně zabezpečená nebo RM přijetí zprávy s chybné pořadové číslo.  
  
2. Jinak Pokud zpráva je chybová zpráva, která se vztahuje konkrétně k vrstvě a zpráva není smysluplné mimo interakce vrstvy, vrstvě by měl zpracovat chybový stav. Příkladem je selhání bylo odmítnuto pořadí RM, který nemá význam do vrstvy nad RM kanálu a to znamená neposlat RM a vyvolání z čekající operace.  
  
3. V opačném případě by měl být vrácená zpráva z Request() nebo Receive(). To zahrnuje případy, kdy vrstvě rozpozná chybu, ale chyby pouze označuje, že žádost se nezdařilo a neznamená přerušením kanálu a vyvolání z čekající operace. Použitelnosti v takovém případě by měly implementovat vrstvě `GetProperty<FaultConverter>` a vraťte se `FaultConverter` odvozenou třídu, která můžete převést chyby výjimky tak, že přepíšete `OnTryCreateException`.  
  
 Následující objektový model podporuje převod zprávy výjimky:  
  
```  
public class FaultConverter  
{  
    public static FaultConverter GetDefaultFaultConverter(  
                                  MessageVersion version);  
    protected abstract bool OnTryCreateException(  
                                 Message message,   
                                 MessageFault fault,   
                                 out Exception exception);  
    public bool TryCreateException(  
                                 Message message,   
                                 MessageFault fault,   
                                 out Exception exception);  
}  
```  
  
 Kanál vrstvu můžete implementovat `GetProperty<FaultConverter>` pro podporu převodu chybové zprávy k výjimkám. Uděláte to tak, přepsat `OnTryCreateException` a zkontrolujte chybová zpráva. Je-li rozpoznán, provést převod, jinak požádejte vnitřního kanálu ho převést. Přenosové kanály by měly delegovat do `FaultConverter.GetDefaultFaultConverter` aby se získal výchozí FaultConverter SOAP, WS-Addressing.  
  
 Obvyklá implementace vypadá takto:  
  
```  
public override bool OnTryCreateException(  
                            Message message,   
                            MessageFault fault,   
                            out Exception exception)  
{  
    if (message.Action == "...")  
    {  
        exception = ...;  
        return true;  
    }  
    // OR  
    if ((fault.Code.Name == "...") && (fault.Code.Namespace == "..."))  
    {  
        exception = ...;  
        return true;  
    }  
  
    if (fault.IsMustUnderstand)  
    {  
        if (fault.WasHeaderNotUnderstood(  
                   message.Headers, "...", "..."))  
        {  
            exception = new ProtocolException(...);  
            return true;  
        }  
    }  
  
#if IMPLEMENTING_TRANSPORT_CHANNEL  
    FaultConverter encoderConverter =   
              this.encoder.GetProperty<FaultConverter>();  
    if ((encoderConverter != null) &&   
        (encoderConverter.TryCreateException(  
                              message, fault, out exception)))  
    {  
        return true;  
    }  
  
    FaultConverter defaultConverter =  
             FaultConverter.GetDefaultFaultConverter(  
                             this.channel.messageVersion);  
    return defaultConverter.TryCreateException(  
                             message, fault, out exception);  
#else  
    FaultConverter inner =   
                    this.innerChannel.GetProperty<FaultConverter>();  
    if (inner != null)  
    {  
        return inner.TryCreateException(message, fault, out exception);  
    }  
    else  
    {  
        exception = null;  
        return false;  
    }  
#endif  
}  
```  
  
 Pro konkrétní chyby podmínky, které mají odlišné obnovení scénáře, vezměte v úvahu definování odvozenou třídu `ProtocolException`.  
  
### <a name="mustunderstand-processing"></a>Zpracování MustUnderstand  
 SOAP definuje obecné chyby pro signalizaci, že požadovaná hlavička nebyla srozumitelné pro příjemce. Tato porucha se označuje jako `mustUnderstand` selhání. Ve službě WCF, vlastních kanálů nikdy nevygeneruje `mustUnderstand` chyb. Místo toho dispečer WCF, která se nachází v horní části zásobníku komunikace WCF, zkontroluje, který všechny hlavičky, které byly označeny jako MustUndestand = true byly srozumitelné pro základní zásobníku. Pokud některý se nerozpoznaly, `mustUnderstand` selhání je vygenerována v daném okamžiku. (Uživatel může rozhodnout pro vypnutí to `mustUnderstand` zpracování a je aplikace přijímat všechny hlavičky zprávy. In that Case aplikace zodpovídá za `mustUnderstand` zpracování.) Vygenerovaný selhání obsahuje hlavičku NotUnderstood, který obsahuje názvy všech záhlaví s MustUnderstand = true, který se nerozpoznaly.  
  
 Pokud váš kanál protokolu odesílá vlastní hlavičku s MustUnderstand = true a přijímá `mustUnderstand` selhání, se musí zjistit, zda je záhlaví je odeslat z důvodu tohoto selhání. Existují dva členy na `MessageFault` třídu, která jsou užitečné pro toto:  
  
```  
public class MessageFault  
{  
    ...  
    public bool IsMustUnderstandFault { get; }  
    public static bool WasHeaderNotUnderstood(MessageHeaders headers,   
        string name, string ns) { }  
    ...  
  
}  
```  
  
 `IsMustUnderstandFault` Vrátí `true` Pokud se jedná `mustUnderstand` selhání. `WasHeaderNotUnderstood` Vrátí `true` Pokud hlavička se zadaným názvem a oborem názvů je součástí selhání jako NotUnderstood záhlaví.  V opačném případě vrátí `false`.  
  
 Pokud kanál vysílá hlavičku, která je označena MustUnderstand = true, pak tuto vrstvu by měly také implementovat vzor rozhraní API pro generování výjimek a měli převést `mustUnderstand` chyby způsobené této hlavičky užitečnější výjimku, jak je popsáno výše.  
  
## <a name="tracing"></a>Trasování  
 Rozhraní .NET Framework poskytuje mechanismus pro trasování spuštění programu jako způsob, jak vám pomůže diagnostiku produkčních aplikací nebo přerušované problémy, kde není možné jenom připojení ladicího programu a krokovat kód. Základní součásti tohoto mechanismu jsou v <xref:System.Diagnostics?displayProperty=nameWithType> obor názvů a obsahovat:  
  
-   <xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>, což je zdroj informací trasování mají být zapsány, <xref:System.Diagnostics.TraceListener?displayProperty=nameWithType>, což je abstraktní základní třída pro konkrétní naslouchacích procesů, které zobrazí informace, které mají být vyvolány z <xref:System.Diagnostics.TraceSource> a vytvořit jeho výstup do cíle specifické pro naslouchací proces. Například <xref:System.Diagnostics.XmlWriterTraceListener> výstupy trasovací informace do souboru XML. Nakonec <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType>, která umožňuje řídit úroveň podrobností trasování uživatelů aplikace a je obvykle zadaný v konfiguraci.  
  
-   Kromě základních komponent, můžete použít [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) k zobrazení a prohledávání WCF trasování. Nástroj je určený speciálně pro trasovací soubory vygenerován pomocí WCF a zapsat pomocí <xref:System.Diagnostics.XmlWriterTraceListener>. Následující obrázek znázorňuje různé součásti účastnící se trasování.  
  
 ![Zpracování výjimek a chyb](../../../../docs/framework/wcf/extending/media/wcfc-tracinginchannelsc.gif "wcfc_TracingInChannelsc")  
  
### <a name="tracing-from-a-custom-channel"></a>Trasování z vlastního kanálu  
 Vlastní kanály by měly vypsat zprávy trasování, které pomáhají při diagnostikování problémů, když není možné se připojit ladicí program k běžící aplikaci. To zahrnuje dvě základní úlohy: Vytvoření instance <xref:System.Diagnostics.TraceSource> a volání metody zapsat trasování.  
  
 Při vytváření instance <xref:System.Diagnostics.TraceSource>, řetězec zadáte se stane název tohoto zdroje. Tento název se používá ke konfiguraci (úroveň trasování povolit/zakázat/set) zdroje trasování. Objevuje se taky ve výstupu samotné trasování. Vlastní kanály používali název jedinečný zdroj k pomáhají čtenářům výstup trasování pochopit, odkud pochází informace o trasování. Pomocí názvu sestavení, který zapisuje informace jako název zdroje trasování je běžný postup. WCF například používá informace ze sestavení System.ServiceModel zapisovat System.ServiceModel jako zdroj trasování.  
  
 Jakmile budete mít zdroj trasování, můžete volat jeho <xref:System.Diagnostics.TraceSource.TraceData%2A>, <xref:System.Diagnostics.TraceSource.TraceEvent%2A>, nebo <xref:System.Diagnostics.TraceSource.TraceInformation%2A> metody zapsat trasování položky pro posluchače trasování. Pro každou položku trasování zápisu, budete muset klasifikovat typ události jako jeden z typů událostí definovaných v <xref:System.Diagnostics.TraceEventType>. Tato klasifikace a nastavení úrovně trasování v konfiguraci zjistit, zda je položka sledování výstupu k naslouchacímu procesu. Například v konfiguraci k nastavení úrovně trasování `Warning` umožňuje `Warning`, `Error` a `Critical` položky k zapsání ale bloky informace a podrobné záznamy sledování. Tady je příklad vytvoření instance zdroje trasování a zápis položky na úrovni informace:  
  
```  
using System.Diagnostics;  
//...  
TraceSource udpSource=new TraceSource("Microsoft.Samples.Udp");  
//...  
udpsource.TraceInformation("UdpInputChannel received a message");  
```  
  
> [!IMPORTANT]
>  Důrazně doporučujeme, že zadáte název zdroje trasování, který je jedinečný pro váš vlastní kanál pomáhají čtenářům výstup trasování pochopit výstup, odkud.  
  
#### <a name="integrating-with-the-trace-viewer"></a>Integrace s prohlížečem trasování  
 Trasování vygenerovaná kanálu může být výstup ve formátu, který dokáže přečíst [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) pomocí <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> jako naslouchací proces trasování. To není něco, jako vývojář kanálu, musíte udělat. Místo toho je uživatel aplikace (nebo osoby, řešení potíží s aplikace), který by měl nakonfigurovat tento naslouchací proces trasování v konfiguračním souboru aplikace. Například následující konfigurace poskytuje trasovací informace z obou <xref:System.ServiceModel?displayProperty=nameWithType> a `Microsoft.Samples.Udp` do souboru s názvem `TraceEventsFile.e2e`:  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <!-- configure System.ServiceModel trace source -->  
      <source name="System.ServiceModel" switchValue="Verbose"   
              propagateActivity="true">  
        <listeners>  
          <add name="e2e" />  
        </listeners>  
      </source>  
      <!-- configure Microsoft.Samples.Udp trace source -->  
      <source name="Microsoft.Samples.Udp" switchValue="Verbose" >  
        <listeners>  
          <add name="e2e" />  
        </listeners>  
      </source>  
    </sources>  
    <!--   
    Define a shared trace listener that outputs to TraceFile.e2e  
    The listener name is e2e   
    -->  
    <sharedListeners>  
      <add name="e2e" type="System.Diagnostics.XmlWriterTraceListener"  
        initializeData=".\TraceFile.e2e"/>  
    </sharedListeners>  
    <trace autoflush="true" />  
  </system.diagnostics>  
</configuration>  
```  
  
#### <a name="tracing-structured-data"></a>Trasování strukturovaných dat  
 <xref:System.Diagnostics.TraceSource?displayProperty=nameWithType> má <xref:System.Diagnostics.TraceSource.TraceData%2A> metodu, která přebírá jeden nebo více objektů, které mají být zahrnuty v položce trasování. Obecně platí <xref:System.Object.ToString%2A?displayProperty=nameWithType> metoda je volána na každý objekt a výsledný řetězec je zapsán jako součást položku trasování. Při použití <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> do výstupu trasování, můžete předat <xref:System.Xml.XPath.IXPathNavigable?displayProperty=nameWithType> jako datový objekt k <xref:System.Diagnostics.TraceSource.TraceData%2A>. Výsledný záznam trasování zahrnuje kód XML poskytnutý podle <xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>. Tady je příklad položky s daty XML aplikace:  
  
```xml  
<E2ETraceEvent xmlns="http://schemas.microsoft.com/2004/06/E2ETraceEvent">  
  <System xmlns="...">  
    <EventID>12</EventID>  
    <Type>3</Type>  
    <SubType Name="Information">0</SubType>  
    <Level>8</Level>  
    <TimeCreated SystemTime="2006-01-13T22:58:03.0654832Z" />  
    <Source Name="Microsoft.ServiceModel.Samples.Udp" />  
    <Correlation ActivityID="{00000000-0000-0000-0000-000000000000}" />  
    <Execution  ProcessName="UdpTestConsole"   
                ProcessID="3348" ThreadID="4" />  
    <Channel />  
    <Computer>COMPUTER-LT01</Computer>  
  </System>  
<!-- XML application data -->  
  <ApplicationData>  
  <TraceData>  
   <DataItem>  
   <TraceRecord   
     Severity="Information"  
     xmlns="…">  
        <TraceIdentifier>some trace id</TraceIdentifier>  
        <Description>EndReceive called</Description>  
        <AppDomain>UdpTestConsole.exe</AppDomain>  
        <Source>UdpInputChannel</Source>  
      </TraceRecord>  
    </DataItem>  
  </TraceData>  
  </ApplicationData>  
</E2ETraceEvent>  
```  
  
 Prohlížeč trasování WCF rozumí schématu `TraceRecord` element uvedenému výše a extrahuje data z jeho podřízené prvky a zobrazí jej ve formátu tabulky. Váš kanál používejte pro toto schéma aplikace strukturovaná data trasování, k poskytování pomoci uživatelům Svctraceviewer.exe číst data.
