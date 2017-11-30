---
title: "Zpracování výjimek a chyb"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a64d01c6-f221-4f58-93e5-da4e87a5682e
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: cf621ce53b1e0aa5fd95adbd9de01bdbd97392bb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="handling-exceptions-and-faults"></a>Zpracování výjimek a chyb
Výjimky se používají ke komunikaci chyby místně v rámci služby nebo implementace klienta. Chyb, na druhé straně, se použijí ke komunikaci chyby napříč hranicemi služby, například ze serveru do klienta a naopak. Kromě chyb používají přenosové kanály mechanismy specifické pro přenos často ke komunikaci chyb na úrovni přenosu. Například přenos HTTP používá stavové kódy, jako je například 404 ke komunikaci neexistující adresu URL koncového bodu (neexistuje žádný koncový bod, který má být zaslán zpět chybu). Tento dokument se skládá ze tří oddílů, které poskytují pokyny k vlastním kanálu autoři. První část obsahuje pokyny k kdy a jak definovat a generování výjimek. Druhá část obsahuje pokyny ohledně generování a využívání chyb. Třetí část vysvětluje, jak poskytnout informace o trasování a řešení potíží s běžící aplikací usnadňuje uživateli vlastní kanál.  
  
## <a name="exceptions"></a>Výjimky  
 Mějte na paměti při vyvolání k výjimce dvě věci: nejprve musí být typu, který umožňuje uživatelům správně napsat správný kód, který může reagovat na výjimku. Druhý je poskytnout dostatek informací pro porozumět, co došlo k chybě, dopad selhání a jeho řešení. Následující části poskytují pokyny ohledně typy výjimek a zprávy pro [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] kanály. Je také obecné pokyny ohledně výjimky v rozhraní .NET obecných zásad návrhu pro dokument výjimky.  
  
### <a name="exception-types"></a>Typy výjimek  
 Všechny výjimky vyvolané kanály musí být buď <xref:System.TimeoutException?displayProperty=nameWithType>, <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>, nebo z odvozený typ. <xref:System.ServiceModel.CommunicationException>. (Výjimky jako <xref:System.ObjectDisposedException> může být rovněž vyvolána, ale pouze pro označení volající kód má došlo ke zneužití kanál. Pokud se používá kanál, se musí pouze throw dané výjimky.) [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] poskytuje sedm typy výjimek, které jsou odvozeny od <xref:System.ServiceModel.CommunicationException> a jsou určeny k použití podle kanály. Existují jiné <xref:System.ServiceModel.CommunicationException>-odvozené výjimky, které jsou určeny k použití podle dalších částí systému. Tyto typy výjimek jsou:  
  
|Typ výjimky|Význam|Vnitřní výjimka obsahu|Strategie obnovení|  
|--------------------|-------------|-----------------------------|-----------------------|  
|<xref:System.ServiceModel.AddressAlreadyInUseException>|Zadaná adresa koncového bodu pro naslouchání se už používá.|Pokud existuje, obsahuje další podrobnosti o této chybě přenosu, který způsobil výjimku. Například. <xref:System.IO.PipeException>, <xref:System.Net.HttpListenerException>, nebo <xref:System.Net.Sockets.SocketException>.|Zkuste jinou adresu.|  
|<xref:System.ServiceModel.AddressAccessDeniedException>|Proces není povolen přístup k zadaná adresa koncového bodu pro naslouchání.|Pokud existuje, obsahuje další podrobnosti o této chybě přenosu, který způsobil výjimku. Například <xref:System.IO.PipeException>, nebo <xref:System.Net.HttpListenerException>.|Opakujte s jinými přihlašovacími údaji.|  
|<xref:System.ServiceModel.CommunicationObjectFaultedException>|<xref:System.ServiceModel.ICommunicationObject> Používá je v chybném stavu (Další informace najdete v tématu [změny stavu Principy](../../../../docs/framework/wcf/extending/understanding-state-changes.md)). Všimněte si, že při aktualizaci objektu s více čekající na vyřízení přechody volání chybném stavu pouze jedno volání vyvolá výjimku, která souvisí s chybou a zbytek throw volání <xref:System.ServiceModel.CommunicationObjectFaultedException>. Tato výjimka je obvykle vyvolána, protože aplikace overlooks některé výjimky a pokusí se použít objekt již chybný, pravděpodobně na vlákno než ten, který vyvolal výjimku původní.|Pokud je k dispozici poskytuje podrobnosti o informacích o vnitřní výjimce.|Vytvořte nový objekt. Všimněte si, že v závislosti na tom, co způsobilo <xref:System.ServiceModel.ICommunicationObject> k poruch na prvním místě, může být jiné práce potřebné k obnovení.|  
|<xref:System.ServiceModel.CommunicationObjectAbortedException>|<xref:System.ServiceModel.ICommunicationObject> Používá byla přerušena (Další informace najdete v tématu [změny stavu Principy](../../../../docs/framework/wcf/extending/understanding-state-changes.md)). Podobně jako <xref:System.ServiceModel.CommunicationObjectFaultedException>, jeho výjimka označuje aplikace volal <xref:System.ServiceModel.ICommunicationObject.Abort%2A> na objekt, případně z jiného vlákna, a objekt již není použitelné z tohoto důvodu.|Pokud je k dispozici poskytuje podrobnosti o informacích o vnitřní výjimce.|Vytvořte nový objekt. Všimněte si, že v závislosti na tom, co způsobilo <xref:System.ServiceModel.ICommunicationObject> k přerušení na prvním místě, může být jiné práce potřebné k obnovení.|  
|<xref:System.ServiceModel.EndpointNotFoundException>|Vzdálený koncový bod cílové nenaslouchá. Může to být důsledkem libovolná součást adresa koncového bodu je nesprávná, irresolvable nebo koncový bod se dolů. Mezi příklady patří chyby DNS, správce front není k dispozici a služba není spuštěna.|V popisu vnitřní výjimky poskytuje podrobnosti, obvykle ze základní přenos.|Zkuste jinou adresu. Alternativně může odesílatel chvíli počkejte a zkuste to znovu, v případě, že byla služba dolů|  
|<xref:System.ServiceModel.ProtocolException>|Komunikační protokoly, jak je popsáno pomocí zásad pro koncový bod, se neshoda mezi koncovými body. Například počet rámců Neshoda typu obsahu nebo zprávy maximální velikost překročena.|Pokud je k dispozici poskytuje další informace o chybě určitý protokol. Například <xref:System.ServiceModel.QuotaExceededException> při příčina chyby je vyšší než MaxReceivedMessageSize je v popisu vnitřní výjimky.|Obnovení: Zkontrolujte odesílatele a přijaté protokolu, které odpovídají nastavení. Jedním ze způsobů k tomu je znovu importovat metadata koncový bod služby (zásady) a znovu vytvořit kanál pomocí generovaného vazby.|  
|<xref:System.ServiceModel.ServerTooBusyException>|Vzdálený koncový bod naslouchá, ale není připravený ke zpracování zpráv.|Pokud je k dispozici, v popisu vnitřní výjimky poskytuje chybu protokolu SOAP nebo podrobnosti o chybě transportní vrstvy.|Obnovení: Počkejte a opakujte operaci později.|  
|<xref:System.TimeoutException>|Operaci se nepodařilo dokončit během časového limitu.|Poskytnout informace o časový limit.|Počkejte a opakujte operaci později.|  
  
 Definujte nový typ výjimky, pouze v případě, že tento typ odpovídá konkrétní obnovení strategie, který se liší od všechny existující typy výjimek. Pokud definujete nový typ výjimky, musí být odvozeny od <xref:System.ServiceModel.CommunicationException> nebo jeden z jejich odvozené třídy.  
  
### <a name="exception-messages"></a>Zprávy o výjimkách  
 Zprávy o výjimkách jsou zaměřeny na uživatele není program, se musí poskytovat dostatečné informace pomoct pochopit a vyřešit problém s uživateli. Jsou tři základní části zpráva dobrý výjimky:  
  
 Co se přihodilo. Zadejte výstižný popis problému pomocí termínů, které se vztahují k možnosti pro uživatele. Například by zpráva chybná výjimky "Neplatný konfigurační oddíl". Zůstane uživatele vás zajímá, které konfigurační oddíl jsou nesprávné a proč je nesprávný. Vylepšené zprávy by "Neplatný konfigurační oddíl \<customBinding >". By být ještě lepší zpráva "nelze přidat přenosu s názvem myTransport pro vazbu s názvem myBinding, protože vazba již přenos s názvem myTransport". Toto je velmi konkrétní zprávu pomocí podmínek a názvy, které může uživatel snadno identifikovat v konfiguračním souboru aplikace. Existují však stále několik klíčové komponenty chybí.  
  
 Násobek chyba. Pokud zpráva jasně neurčí, co znamená chybu, uživatel bude pravděpodobně zajímat, zda se jedná o závažné chybě nebo pokud můžete ignorovat. Obecně platí by měla vést zprávy s význam nebo násobek chyby. Ke zlepšení předchozí příklad, může být zpráva "hostitel služby se nezdařilo otevřít z důvodu chyby konfigurace: nelze přidat přenosu s názvem myTransport pro vazbu s názvem myBinding, protože vazba již přenos s názvem myTransport".  
  
 Jak uživatel by měl problém opravit. Nejdůležitější část zprávy pomáhá uživatele opravu problému. Zpráva by měla obsahovat některé pokyny nebo pomocné parametry o tom, jak zkontrolovat nebo opravte problém odstraněn. Například "hostitel služby se nezdařilo otevřít z důvodu chyby konfigurace: nelze přidat přenosu s názvem myTransport pro vazbu s názvem myBinding, protože vazba již přenos s názvem myTransport. Ujistěte se, že je vazba pouze jeden přenos".  
  
## <a name="communicating-faults"></a>Komunikaci chyb  
 SOAP 1.1 a SOAP 1.2 definovat konkrétní strukturu pro chyb. Existují určité rozdíly mezi dvěma specifikace, ale obecně platí, zprávu a MessageFault typy slouží k vytvoření a využívat chyb.  
  
 ![Zpracování výjimek a chyb](../../../../docs/framework/wcf/extending/media/wcfc-soap1-1andsoap1-2faultcomparisonc.gif "wcfc_SOAP1. 1AndSOAP1 2FaultComparisonc")  
SOAP 1.2 selhání (vlevo) a chybu protokolu SOAP 1.1 (vpravo). Všimněte si, že v protokolu SOAP 1.1 pouze element selhání je obor názvů kvalifikovaný.  
  
 SOAP definuje zprávu o chybě jako zprávu, která obsahuje jenom chyby element (element, jehož název je `<env:Fault>`) jako podřízený `<env:Body>`. Obsah elementu selhání mírně mezi SOAP 1.1 a SOAP 1.2, jak je znázorněno na obrázku 1. Ale <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType> třída normalizuje tyto rozdíly do jednoho objektu modelu:  
  
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
  
 `Code` Vlastnost odpovídá `env:Code` (nebo `faultCode` v SOAP 1.1) a typ poruchy. SOAP 1.2 definuje pět povolených hodnot pro `faultCode` (například odesílatele a příjemce) a definuje `Subcode` element, který může obsahovat libovolnou hodnotu dílčí. (Najdete v článku [SOAP 1.2 specifikace](http://go.microsoft.com/fwlink/?LinkId=95176) seznam povolených chybových kódů a jejich významu.) SOAP 1.1 má mechanismus mírně odlišný: definuje čtyři `faultCode` hodnoty (například klient a Server), které lze rozšířit tak, že definujete zcela nové nebo pomocí zápisu s tečkou k vytvoření konkrétnější `faultCodes`, například Client.Authentication.  
  
 Když pomocí MessageFault program chyb, FaultCode.Name a FaultCode.Namespace mapování název a obor názvů SOAP 1.2 `env:Code` nebo SOAP 1.1 `faultCode`. Se mapuje FaultCode.SubCode `env:Subcode` pro SOAP 1.2 a má hodnotu null pro SOAP 1.1.  
  
 Měli byste vytvořit nový dílčí kódy chyb (nebo nové kódy chyb při použití protokolu SOAP 1.1) Pokud je zajímavé prostřednictvím kódu programu rozlišit chybu. To se podobá je vytvoření nového typu výjimka. Neměli byste pomocí zápisu s tečkou s kódy chyb SOAP 1.1. ( [WS-I Basic Profile](http://go.microsoft.com/fwlink/?LinkId=95177) také nedoporučuje použití tečkami selhání kódu.)  
  
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
  
 `Reason` Vlastnost odpovídá `env:Reason` (nebo `faultString` v SOAP 1.1) čitelná pro člověka popis podobá zprávy výjimky chybový stav. `FaultReason` – Třída (a SOAP `env:Reason/faultString`) má integrovanou podporu pro s více překlady v zájmu globalizace.  
  
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
  
 Obsah podrobnosti chyby, které jsou zveřejněné na MessageFault pomocí různých metod, včetně `GetDetail` \<T > a `GetReaderAtDetailContents`(). Podrobnosti o selhání je element neprůhledné pro provedení další podrobnosti o poruchy. To je užitečné, pokud je některé libovolný strukturovaných podrobností, která chcete provádění se chyby.  
  
### <a name="generating-faults"></a>Generování chyb  
 Tato část vysvětluje proces generování chybu v reakci na chybový stav zjištění v kanálu nebo ve vlastnosti zprávy vytvořený kanál. Typickým příkladem je odesílání zpět chybu v reakci na žádost o zprávu, která obsahuje neplatná data.  
  
 Při generování chybu, vlastní kanál vůbec Neposílat přímo odolnost, místo toho by měla vyvolat výjimku a nechat vrstvu nad rozhodněte, jestli se má převést této výjimky na chybu a postupy pro odesílání. Pro usnadnění tohoto převodu, by měl poskytovat kanál `FaultConverter` implementace, která můžete převést výjimky ve vlastním kanálu pro příslušné selhání. `FaultConverter`je definován jako:  
  
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
  
 Každý kanál, který generuje vlastní chyby musí implementovat `FaultConverter` a obnoví v něm volání `GetProperty<FaultConverter>`. Vlastní `OnTryCreateFaultMessage` implementace musí buď převést výjimka chybu nebo delegovat na vnitřní kanál `FaultConverter`. Pokud je kanál přenos musí převést výjimku nebo delegovat na kodér `FaultConverter` nebo výchozí `FaultConverter` součástí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] . Výchozí hodnota `FaultConverter` převede chyby odpovídající určeného adresování WS a protokolu SOAP zprávy selhání. Tady je příklad `OnTryCreateFaultMessage` implementace.  
  
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
  
 Vyplývá tohoto vzoru je, že výjimky vydané mezi vrstvami pro chybové podmínky, které vyžadují chyb musí obsahovat dostatek informací pro odpovídající generátor selhání vytvoření správné selhání. Jako autor vlastní kanál může definovat typy výjimek, které odpovídají podmínky jiné chyby, pokud takové výjimky již neexistují. Všimněte si, výjimky procházení vrstvy kanálu by měl komunikovat chybový stav nikoli neprůhledného selhání data.  
  
### <a name="fault-categories"></a>Kategorie chyby  
 Existují obecně tři kategorie chyb:  
  
1.  Chyb, které jsou v rámci celý zásobník velkého rozšíření. Tyto chyby by mohlo dojít v všechny vrstvy v zásobníku kanál, například InvalidCardinalityAddressingException.  
  
2.  Chyb, které může být došlo kdekoli výše určité vrstvy v zásobníku například některé chyby, které se týkají sdružení transakcí nebo role zabezpečení.  
  
3.  Chyb, které jsou směrované na jedné vrstvy v zásobníku, například chyby jako WS-RM pořadí číslo chyby.  
  
 Kategorie 1. Chyby jsou obvykle adresování WS a chyb protokolu SOAP. Základní `FaultConverter` třída poskytované [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] převede chyby odpovídající selhání zprávy určeného adresování WS a SOAP, není nutné ke zpracování převodu tyto výjimky sami.  
  
 Kategorie 2. Chybám dochází, pokud vrstva přidá vlastnost zprávu, která není zcela využívat zpráva informace, které se vztahují na tuto vrstvu. Chyb je možné zjistit později při vyšší vrstvě požádá vlastnost zprávu zpracovat další informace o zprávě. Tyto kanály by měla implementovat `GetProperty` zadaný dříve umožňující vyšší vrstvě má být zaslán zpět správné selhání. Příkladem je TransactionMessageProperty. Tato vlastnost je přidána ke zprávě bez plně ověření všechna data v hlavičce (Pokud tak učiníte, může zahrnovat kontaktování koordinátor distribuovaných transakcí (DTC).  
  
 Kategorie 3. Chyby jsou pouze generované a odeslat pomocí jedné vrstvy v nastavení procesoru. Proto všechny výjimky jsou obsažena ve vrstvě. Vylepšit konzistenci mezi kanály a usnadnění údržby, měli použít vlastní kanál vzoru dříve určeného ke generování zprávy selhání i pro interní chyby.  
  
### <a name="interpreting-received-faults"></a>Interpretace přijatých chyb  
 Tato část obsahuje pokyny pro generování příslušné výjimky při přijímání zprávu o chybě. Rozhodovací strom pro zpracování na zprávu na všechny vrstvy v zásobníku vypadá takto:  
  
1.  Pokud je zpráva Neplatná za vrstvy, vrstvě měli udělat jeho zpracování "Neplatná zpráva". Toto zpracování je specifická pro vrstvy, ale mohou obsahovat vyřazení se zpráva trasování, nebo došlo k výjimce, který získá převést na chybu. Mezi příklady patří zabezpečení přijímání zprávy, které nejsou řádně zabezpečená, nebo RM přijímání zprávy s chybné pořadové číslo.  
  
2.  Pokud zpráva je zprávu o chybě, která se vztahuje konkrétně na vrstvu a zpráva není smysluplný mimo interakce vrstvy, by měla řídit vrstvy, jinak hodnota chybový stav. Příkladem je selhání RM pořadí odmítl smysl na vrstvy výše RM kanál a který znamená přerušením RM kanálu a byla vrácena z čekající operace.  
  
3.  Zpráva, jinak hodnota má být vrácen z Request() nebo Receive(). To zahrnuje případech, kdy vrstvě rozpozná chybu, ale poruchy právě označuje, že žádost se nezdařila a neznamená přerušením kanálu a byla vrácena z čekající operace. Pokud chcete zlepšit použitelnost v takovém případě, by měla implementovat vrstvě `GetProperty<FaultConverter>` a vrátit `FaultConverter` odvozené třídy, které můžete převést selhání výjimku přepsáním `OnTryCreateException`.  
  
 Následující objektový model podporuje převod zprávy k výjimkám:  
  
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
  
 Můžete implementovat vrstvy kanálu `GetProperty<FaultConverter>` pro podporu převodu chybové zprávy k výjimkám. Chcete-li to provést, přepište `OnTryCreateException` a zkontrolovat zprávu chyby. Pokud rozpoznána, provést převod, jinak požádejte vnitřní kanál ji převést. Přenosové kanály by měly delegovat do `FaultConverter.GetDefaultFaultConverter` získat výchozí SOAP, WS-Addressing FaultConverter.  
  
 Typická implementace vypadá takto:  
  
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
  
 Pro konkrétní chyby podmínky, které mají odlišné obnovení scénáře, zvažte možnost definice odvozených tříd z `ProtocolException`.  
  
### <a name="mustunderstand-processing"></a>Atribut MustUnderstand zpracování  
 SOAP definuje k obecné chybě signalizace, že požadovaná hlavička nebyla rozpoznaná příjemce. Toto selhání se označuje jako `mustUnderstand` selhání. V [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], nikdy generovat vlastní kanály `mustUnderstand` chyb. Místo toho [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] dispečera, která se nachází v horní části [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] komunikačního balíku, zkontroluje, který všechny hlavičky, které byly označeny jako MustUndestand = true se rozumí základní zásobníku. Pokud žádné nebyly porozuměl jsem jim `mustUnderstand` se v tomto bodě vygeneruje chyby. (Můžete vybrat uživatel pro tento vypnout `mustUnderstand` zpracování a aplikace přijímat všechny hlavičky zpráv. In that Case aplikace zodpovídá za provádění `mustUnderstand` zpracování.) Vygenerovaný selhání obsahuje hlavičku NotUnderstood, která obsahuje názvy všech záhlaví s MustUnderstand = true, které nebyly rozumí.  
  
 Pokud protokol kanál odešle vlastní hlavičku s MustUnderstand = true a přijímá `mustUnderstand` selhání, se musí zjistit, jestli je kvůli hlavička ho odeslaná této chyby. Existují dva členy na `MessageFault` třídu, která jsou užitečné pro toto:  
  
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
  
 `IsMustUnderstandFault`Vrátí `true` Pokud je odolnost `mustUnderstand` selhání. `WasHeaderNotUnderstood`Vrátí `true` Pokud hlavička se zadaným názvem a oborem názvů je součástí selhání jako hlavičku NotUnderstood.  Funkce `false`.  
  
 Pokud je kanál, který vysílá hlavičku, která je označena MustUnderstand = true, pak tuto vrstvu by také implementovat vzor rozhraní API pro generování výjimek a měli převést `mustUnderstand` chyby způsobené této hlavičky užitečnější výjimce, jak je popsáno výše.  
  
## <a name="tracing"></a>Trasování  
 Rozhraní .NET Framework poskytuje mechanismus pro trasování spuštění programu jako způsob, jak Diagnostika produkční žádosti o podporu nebo přerušované problémy, které není možné právě připojit ladicí program a krokovat kód. Základní součásti služby tento mechanismus jsou v <xref:System.Diagnostics?displayProperty=nameWithType> obor názvů a obsahovat:  
  
-   <xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>, což je zdroj informací trasování, které má být zapsán <xref:System.Diagnostics.TraceListener?displayProperty=nameWithType>, což je abstraktní základní třídu pro konkrétní naslouchací procesy, které přijímají informace k trasování z <xref:System.Diagnostics.TraceSource> a výstup do cílového umístění, specifické pro naslouchací proces. Například <xref:System.Diagnostics.XmlWriterTraceListener> výstupy trasování informace do souboru XML. Nakonec <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType>, který umožňuje řídit podrobností trasování uživatelů aplikace a je obvykle zadaný v konfiguraci.  
  
-   Kromě základních komponent, můžete použít [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) k zobrazení a hledání [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] trasování. Nástroj je určený speciálně pro trasovací soubory generované [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] a zapsány pomocí <xref:System.Diagnostics.XmlWriterTraceListener>. Následující obrázek ukazuje různé součásti účastnící se trasování.  
  
 ![Zpracování výjimek a chyb](../../../../docs/framework/wcf/extending/media/wcfc-tracinginchannelsc.gif "wcfc_TracingInChannelsc")  
  
### <a name="tracing-from-a-custom-channel"></a>Trasování z vlastního kanálu  
 Vlastní kanály měli zapsat trasování zprávy jako pomůcku při diagnostikování problémů, když není možné připojit ladicí program pro běžící aplikaci. To zahrnuje dvě úlohy nejvyšších úrovní: vytváření instancí <xref:System.Diagnostics.TraceSource> a volání její metody k zápisu trasování.  
  
 Při vytváření instance <xref:System.Diagnostics.TraceSource>, zadáte řetězec stane název tohoto zdroje. Tento název slouží ke konfiguraci zdroj trasování (povolit nebo zakázat nebo nastavení trasování úroveň). Zobrazuje se taky v samotné výstup trasování. Vlastní kanály by měl použít název jedinečný zdroj pomohou čtečky výstup trasování pochopit, kde informace trasování pocházejí z. Pomocí názvu sestavení, který zapisuje informace jako název zdroje trasování je běžnou praxí. Například [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] System.ServiceModel se používá jako zdroj trasování pro zapsaných informací z System.ServiceModel sestavení.  
  
 Až budete mít zdroj trasování, zavoláte jeho <xref:System.Diagnostics.TraceSource.TraceData%2A>, <xref:System.Diagnostics.TraceSource.TraceEvent%2A>, nebo <xref:System.Diagnostics.TraceSource.TraceInformation%2A> metody k zápisu trasování položek pro naslouchací procesy trasování. Pro každou položku trasování napíšete, budete muset klasifikovat jako jeden z typů událostí, které jsou definované v typu události <xref:System.Diagnostics.TraceEventType>. Tato klasifikace a nastavení úrovně trasování v konfiguraci určit, zda je položka sledování výstup do naslouchací proces. Například v konfiguraci k nastavení úrovně trasování `Warning` umožňuje `Warning`, `Error` a `Critical` trasování položky k zapsání ale bloky informace a podrobné záznamy. Tady je příklad vytvoření instance zdroj trasování a zápis na položku na úrovni informace:  
  
```  
using System.Diagnostics;  
//...  
TraceSource udpSource=new TraceSource("Microsoft.Samples.Udp");  
//...  
udpsource.TraceInformation("UdpInputChannel received a message");  
```  
  
> [!IMPORTANT]
>  Důrazně doporučujeme, že zadáváte název zdroje trasování, které jsou jedinečné pro vaše vlastní kanál pomohou čtenářům výstup trasování pochopit, odkud pochází výstup.  
  
#### <a name="integrating-with-the-trace-viewer"></a>Integrace s prohlížeče trasování  
 Trasování generované kanál může být výstup ve formátu přečíst [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) pomocí <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> jako naslouchací proces trasování. Toto není něco, jako vývojář kanál, musíte udělat. Místo toho je uživatel aplikace (nebo osoby, řešení potíží s aplikace), které je konfigurace této naslouchací proces trasování v konfiguračním souboru aplikace. Například následující konfigurace výstupy trasování informace z obou <xref:System.ServiceModel?displayProperty=nameWithType> a `Microsoft.Samples.Udp` do souboru s názvem `TraceEventsFile.e2e`:  
  
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
 <xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>má <xref:System.Diagnostics.TraceSource.TraceData%2A> metody, která přijímá jeden nebo více objektů, které mají být zahrnuty v položce trasování. Obecně <xref:System.Object.ToString%2A?displayProperty=nameWithType> metoda je volána na každém objektu a výsledný řetězec je zapsán v rámci položky trasování. Při použití <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> výstup trasování, můžete předat <xref:System.Xml.XPath.IXPathNavigable?displayProperty=nameWithType> jako datový objekt k <xref:System.Diagnostics.TraceSource.TraceData%2A>. Výsledná položka trasování obsahuje XML poskytované <xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>. Tady je příklad položku s XML data aplikací:  
  
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
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Prohlížeče trasování rozumí schéma `TraceRecord` element uvedený výše a extrahuje data z její podřízené elementy a zobrazí v tabulkovém formátu. Kanál používejte toto schéma při trasování data strukturovaných aplikací pomoci uživatelům Svctraceviewer.exe číst data.
