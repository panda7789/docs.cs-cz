---
title: Zpracování výjimek a chyb
ms.date: 03/30/2017
ms.assetid: a64d01c6-f221-4f58-93e5-da4e87a5682e
ms.openlocfilehash: bca77b575be65513f9a792352e14e3f9bd7b4904
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185630"
---
# <a name="handling-exceptions-and-faults"></a>Zpracování výjimek a chyb
Výjimky se používají ke komunikaci chyb místně v rámci služby nebo implementace klienta. Chyby, na druhé straně se používají ke komunikaci chyb přes hranice služby, například ze serveru klientovi nebo naopak. Kromě chyb dopravní kanály často používají mechanismy specifické pro přenos ke komunikaci chyb na úrovni přenosu. Například přenos HTTP používá stavové kódy, jako je například 404 ke komunikaci neexistující adresu URL koncového bodu (neexistuje žádný koncový bod pro odeslání chyby zpět). Tento dokument se skládá ze tří částí, které poskytují pokyny pro vlastní autory kanálů. První část obsahuje pokyny, kdy a jak definovat a vyvolat výjimky. Druhá část obsahuje pokyny týkající se generování a spotřebovávání chyb. Třetí část vysvětluje, jak poskytnout informace o trasování, které pomohou uživateli vlastního kanálu při odstraňování potíží se spuštěných aplikací.  
  
## <a name="exceptions"></a>Výjimky  
 Existují dvě věci, které je třeba mít na paměti při vyvolání výjimky: Nejprve musí být typu, který umožňuje uživatelům psát správný kód, který může odpovídajícím způsobem reagovat na výjimku. Za druhé, musí poskytnout dostatek informací pro uživatele pochopit, co se pokazilo, dopad selhání a jak to opravit. V následujících částech jsou uvedeny pokyny týkající se typů výjimek a zpráv pro kanály WCF (Windows Communication Foundation). V dokumentu Pokyny pro návrh výjimek naleznete také obecné pokyny týkající se výjimek v rozhraní .NET.  
  
### <a name="exception-types"></a>Typy výjimek  
 Všechny výjimky vyváděné <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>kanály musí být <xref:System.ServiceModel.CommunicationException>buď <xref:System.TimeoutException?displayProperty=nameWithType>, nebo typ odvozený od . (Výjimky, <xref:System.ObjectDisposedException> jako může být také vyvolána, ale pouze k označení, že volající kód zneužil kanál. Pokud kanál se používá správně, musí vyvolat pouze dané výjimky.) WCF poskytuje sedm typů <xref:System.ServiceModel.CommunicationException> výjimek, které jsou odvozeny z a jsou určeny pro použití kanály. Existují další <xref:System.ServiceModel.CommunicationException>odvozené výjimky, které jsou určeny pro použití jinými částmi systému. Tyto typy výjimek jsou:  
  
|Typ výjimky|Význam|Vnitřní obsah výjimky|Strategie obnovení|  
|--------------------|-------------|-----------------------------|-----------------------|  
|<xref:System.ServiceModel.AddressAlreadyInUseException>|Adresa koncového bodu zadaná pro naslouchání je již používána.|Pokud je k dispozici, poskytuje další podrobnosti o chybě přenosu, která způsobila tuto výjimku. Například. <xref:System.IO.PipeException>, <xref:System.Net.HttpListenerException>, <xref:System.Net.Sockets.SocketException>nebo .|Zkuste jinou adresu.|  
|<xref:System.ServiceModel.AddressAccessDeniedException>|Proces není povolen přístup k adrese koncového bodu určené pro naslouchání.|Pokud je k dispozici, poskytuje další podrobnosti o chybě přenosu, která způsobila tuto výjimku. Například <xref:System.IO.PipeException>, <xref:System.Net.HttpListenerException>nebo .|Zkuste s různými přihlašovacími údaji.|  
|<xref:System.ServiceModel.CommunicationObjectFaultedException>|Používaná <xref:System.ServiceModel.ICommunicationObject> položky jsou ve stavu Chybovaný (další informace naleznete v [tématu Principy změn stavu](understanding-state-changes.md)). Všimněte si, že když objekt s více čekající volání přechody do chybovaného stavu, pouze jedno volání <xref:System.ServiceModel.CommunicationObjectFaultedException>vyvolá výjimku, která souvisí s selhání a zbytek volání vyvolat . Tato výjimka je obvykle vyvolána, protože aplikace přehlíží některé výjimky a pokusí se použít již vadný objekt, případně ve vlákně než ten, který zachytil původní výjimku.|Pokud je k dispozici poskytuje podrobnosti o vnitřní výjimku.|Vytvořte nový objekt. Všimněte si, že <xref:System.ServiceModel.ICommunicationObject> v závislosti na tom, co způsobilo chybu na prvním místě, může být další práce potřebné k obnovení.|  
|<xref:System.ServiceModel.CommunicationObjectAbortedException>|Používaná <xref:System.ServiceModel.ICommunicationObject> informace byla přerušena (další informace naleznete v [tématu Principy změn stavu](understanding-state-changes.md)). Podobně <xref:System.ServiceModel.CommunicationObjectFaultedException>jako , jeho výjimka <xref:System.ServiceModel.ICommunicationObject.Abort%2A> označuje, že aplikace volá objekt, případně z jiného vlákna, a objekt již není použitelný z tohoto důvodu.|Pokud je k dispozici poskytuje podrobnosti o vnitřní výjimku.|Vytvořte nový objekt. Všimněte si, že <xref:System.ServiceModel.ICommunicationObject> v závislosti na co způsobilo přerušení na prvním místě, může být další práce potřebné k obnovení.|  
|<xref:System.ServiceModel.EndpointNotFoundException>|Cílový vzdálený koncový bod nenaslouchá. To může vyplývat z jakékoli části koncového bodu adresy je nesprávné, neřešitelné nebo koncový bod je dolů. Příklady zahrnují chybu DNS, Správce front není k dispozici a služba není spuštěna.|Vnitřní výjimka obsahuje podrobnosti, obvykle z podkladového přenosu.|Zkuste jinou adresu. Odesílatel může také chvíli počkat a zkusit to znovu v případě, že služba neklesla.|  
|<xref:System.ServiceModel.ProtocolException>|Komunikační protokoly, jak je popsáno v zásadách koncového bodu, jsou neodpovídající mezi koncovými body. Například neshoda typu obsahu nebo maximální velikost zprávy byla překročena.|Pokud je k dispozici poskytuje další informace o konkrétní chybě protokolu. Například <xref:System.ServiceModel.QuotaExceededException> je vnitřní výjimka, když příčina chyby je vyšší MaxReceivedMessageSize.|Obnovení: Ujistěte se, že odesílatel a přijaté nastavení protokolu odpovídají. Jedním ze způsobů, jak to provést, je znovu importovat metadata (zásady) koncového bodu služby a použít vygenerovanou vazbu k opětovnému vytvoření kanálu.|  
|<xref:System.ServiceModel.ServerTooBusyException>|Vzdálený koncový bod naslouchá, ale není připraven ke zpracování zpráv.|Pokud je k dispozici, vnitřní Exception poskytuje podrobnosti o chybě SOAP nebo na úrovni přenosu.|Obnovení: Počkejte a opakujte operaci později.|  
|<xref:System.TimeoutException>|Operaci se nepodařilo dokončit v časovém rámci.|Může poskytnout podrobnosti o časovém odnož.|Počkejte a opakujte operaci později.|  
  
 Nový typ výjimky definujte pouze v případě, že tento typ odpovídá konkrétní strategii obnovení, která se liší od všech existujících typů výjimek. Pokud definujete nový typ výjimky, <xref:System.ServiceModel.CommunicationException> musí být odvozen z nebo z jedné z jeho odvozených tříd.  
  
### <a name="exception-messages"></a>Zprávy o výjimky  
 Zprávy o výjimce jsou zaměřeny na uživatele, nikoli na program, takže by měly poskytnout dostatečné informace, které uživateli pomohou pochopit a vyřešit problém. Tři základní části zprávy o dobré výjimce jsou:  
  
 Co se stalo. Poskytněte jasný popis problému pomocí termínů, které se vztahují k uživatelskému prostředí. Chybná zpráva o výjimce by například byla "Neplatná konfigurační část". To ponechává uživateli přemýšlel, která část konfigurace je nesprávná a proč je nesprávná. Vylepšená zpráva by "Neplatná konfigurační sekce \<customBinding>". Ještě lepší zpráva by "Nelze přidat přenos s názvem myTransport do vazby s názvem myBinding, protože vazba již má přenos s názvem myTransport". Jedná se o velmi specifickou zprávu pomocí termínů a názvů, které může uživatel snadno identifikovat v konfiguračním souboru aplikace. Stále však chybí několik klíčových součástí.  
  
 Význam chyby. Pokud zpráva jasně neuvádí, co chyba znamená, uživatel se pravděpodobně bude ptát, zda se jedná o závažnou chybu nebo zda ji lze ignorovat. Obecně zprávy by měly vést s významem nebo významem chyby. Chcete-li zlepšit předchozí příklad, zpráva může být "ServiceHost se nepodařilo otevřít z důvodu chyby konfigurace: Nelze přidat přenos s názvem myTransport na vazbu s názvem myBinding, protože vazba již má přenos s názvem myTransport".  
  
 Jak by měl uživatel problém opravit. Nejdůležitější částí zprávy je pomoc uživateli vyřešit problém. Zpráva by měla obsahovat některé pokyny nebo rady o tom, co zkontrolovat nebo opravit k vyřešení problému. Například "ServiceHost se nepodařilo otevřít z důvodu chyby konfigurace: Nelze přidat přenos s názvem myTransport do vazby s názvem myBinding, protože vazba již má přenos s názvem myTransport. Ujistěte se, že ve vazbě je pouze jedna přeprava".  
  
## <a name="communicating-faults"></a>Komunikace s chybami  
 SOAP 1.1 a SOAP 1.2 oba definují specifickou strukturu pro chyby. Existují určité rozdíly mezi dvěma specifikacemi, ale obecně Message a MessageFault typy se používají k vytvoření a využití chyb.  
  
 ![Zpracování výjimek a závad](./media/wcfc-soap1-1andsoap1-2faultcomparisonc.gif "wcfc_SOAP1-1AndSOAP1-2Porovnání chyb")  
SOAP 1.2 Porucha (vlevo) a CHYBA SOAP 1.1 (vpravo). Všimněte si, že v SOAP 1.1 pouze Fault element je obor názvů kvalifikovaný.  
  
 SOAP definuje zprávu o chybě jako zprávu, která obsahuje pouze `<env:Fault>`prvek poruchy (prvek, jehož název je ) jako podřízený . `<env:Body>` Obsah zlomového prvku se mírně liší mezi SOAP 1.1 a SOAP 1.2, jak je znázorněno na obrázku 1. Třída však <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType> normalizuje tyto rozdíly do jednoho objektového modelu:  
  
```csharp
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
  
 Vlastnost `Code` odpovídá `env:Code` (nebo `faultCode` v SOAP 1.1) a identifikuje typ poruchy. SOAP 1.2 definuje pět povolených hodnot pro `faultCode` (například Odesílatel a `Subcode` Příjemce) a definuje prvek, který může obsahovat libovolnou hodnotu podkódu. (Seznam povolených chybových kódů a jejich význam naleznete ve [specifikaci SOAP 1.2.)](https://www.w3.org/TR/soap12-part1/#tabsoapfaultcodes) SOAP 1.1 má mírně odlišný mechanismus: `faultCode` Definuje čtyři hodnoty (například Klient a Server), které lze rozšířit buď definováním zcela nových, `faultCodes`nebo pomocí notace tečky k vytvoření konkrétnější , například Client.Authentication.  
  
 Při použití MessageFault k programování chyb, FaultCode.Name a FaultCode.Namespace mapuje na název `env:Code` a obor názvů `faultCode`SOAP 1.2 nebo SOAP 1.1 . FaultCode.SubCode mapuje `env:Subcode` pro SOAP 1.2 a je null pro SOAP 1.1.  
  
 Pokud používáte soap 1.1, měli byste vytvořit nové dílčí kódy poruch (nebo nové chybové kódy), pokud je zajímavé programově rozlišit chybu. To je analogické k vytvoření nového typu výjimky. Měli byste se vyhnout použití tečky zápisu s SOAP 1.1 chybové kódy. (Základní [profil WS-I](http://www.ws-i.org/Profiles/BasicProfile-1.1-2004-08-24.html#SOAP_Custom_Fault_Codes) také odrazuje od použití zápisu tečky chybového kódu.)  
  
```csharp
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
  
 Vlastnost `Reason` odpovídá `env:Reason` (nebo `faultString` v SOAP 1.1) lidsky čitelný popis chybového stavu analogicky k zprávě výjimky. Třída `FaultReason` (a `env:Reason/faultString`SOAP) má vestavěnou podporu pro více překladů v zájmu globalizace.  
  
```csharp
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
  
 Obsah podrobností o chybě jsou vystaveny na `GetDetail` \<MessageFault `GetReaderAtDetailContents`pomocí různých metod, včetně T> a (). Detail poruchy je neprůhledný prvek pro přenášení dalších podrobností o poruše. To je užitečné, pokud existuje nějaký libovolný strukturovaný detail, který chcete provést s chybou.  
  
### <a name="generating-faults"></a>Generování chyb  
 Tato část vysvětluje proces generování chyby v reakci na chybový stav zjištěný v kanálu nebo ve vlastnosti zprávy vytvořené kanálem. Typickým příkladem je odeslání chyby v odpovědi na zprávu požadavku, která obsahuje neplatná data.  
  
 Při generování chyby by vlastní kanál neměl odesílat chybu přímo, spíše by měl vyvolat výjimku a nechat výše uvedenou vrstvu rozhodnout, zda převést tuto výjimku na chybu a jak ji odeslat. Chcete-li pomoci v tomto převodu, kanál by měl poskytnout `FaultConverter` implementaci, která může převést výjimku vyváděnou vlastní kanál na příslušnou chybu. `FaultConverter`je definována jako:  
  
```csharp
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
  
 Každý kanál, který generuje vlastní `FaultConverter` chyby, musí `GetProperty<FaultConverter>`implementovat a vrátit z volání do . Vlastní `OnTryCreateFaultMessage` implementace musí buď převést výjimku na chybu nebo `FaultConverter`delegovat na vnitřní kanál . Pokud kanál je přenos musí převést výjimku nebo delegovat `FaultConverter` na `FaultConverter` kodéru nebo výchozí k dispozici v WCF . Výchozí `FaultConverter` převede chyby odpovídající chybové zprávy určené WS-Adresování a SOAP. Zde je `OnTryCreateFaultMessage` příklad implementace.  
  
```csharp
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
  
 Důsledkem tohoto vzoru je, že výjimky vyzvané mezi vrstvami pro chybové stavy, které vyžadují chyby, musí obsahovat dostatek informací pro odpovídající generátor chyb k vytvoření správné chyby. Jako vlastní autor kanálu můžete definovat typy výjimek, které odpovídají různým poruchovým podmínkám, pokud takové výjimky ještě neexistují. Všimněte si, že výjimky procházející vrstvy kanálu by měly komunikovat chybový stav spíše než neprůhledná data poruchy.  
  
### <a name="fault-categories"></a>Kategorie poruch  
 Obecně existují tři kategorie závad:  
  
1. Chyby, které jsou všudypřítomné v celém zásobníku. Tyto chyby může dojít v libovolné vrstvě v zásobníku kanálu, například InvalidCardinalityAddressingException.  
  
2. Chyby, které lze narazit kdekoli nad určitou vrstvu v zásobníku například některé chyby, které se týkající se toku transakce nebo role zabezpečení.  
  
3. Chyby, které jsou směrovány na jednu vrstvu v zásobníku, například chyby, jako jsou chyby pořadového čísla WS-RM.  
  
 Kategorie 1. Chyby jsou obecně WS adresování a SOAP chyby. Základní `FaultConverter` třída poskytovaná WCF převádí chyby odpovídající chybové zprávy určené WS-Adresování a SOAP, takže není třeba zpracovat převod těchto výjimek sami.  
  
 Kategorie 2. Chyby dojít, když vrstva přidá vlastnost zprávy, která není zcela využívat informace o zprávě, která se týká této vrstvy. Chyby mohou být zjištěny později, když vyšší vrstva požádá vlastnost zprávy o další zpracování informací o zprávě. Tyto kanály `GetProperty` by měly implementovat zadané dříve povolit vyšší vrstvy odeslat zpět správnou chybu. Příkladem je TransactionMessageProperty. Tato vlastnost je přidána do zprávy bez úplného ověření všech dat v záhlaví (to může zahrnovat kontaktování koordinátora distribuovaných transakcí (DTC).  
  
 Kategorie 3. Chyby jsou generovány a odesílány pouze jednou vrstvou v procesoru. Proto jsou všechny výjimky obsaženy ve vrstvě. Chcete-li zlepšit konzistenci mezi kanály a usnadnit údržbu, vlastní kanál by měl použít vzor zadaný dříve generovat chybové zprávy i pro vnitřní chyby.  
  
### <a name="interpreting-received-faults"></a>Interpretace přijatých chyb  
 Tato část obsahuje pokyny pro generování příslušné výjimky při přijímání chybové zprávy. Rozhodovací strom pro zpracování zprávy v každé vrstvě v zásobníku je následující:  
  
1. Pokud vrstva považuje zprávu za neplatnou, měla by provést zpracování "neplatné zprávy". Takové zpracování je specifické pro vrstvu, ale může zahrnovat uvolnění zprávy, trasování nebo vyvolání výjimky, která získá převedena na chybu. Mezi příklady patří zabezpečení přijímající zprávu, která není správně zabezpečena, nebo rm přijímající zprávu se špatným pořadovým číslem.  
  
2. V opačném případě pokud zpráva je zpráva, která se vztahuje konkrétně na vrstvu a zpráva není smysluplné mimo interakci vrstvy, vrstva by měla zpracovat chybový stav. Příkladem je chyba ODMÍTNUTÁ RM, která nemá smysl pro vrstvy nad kanálem RM a znamená chybovat kanál RM a vyvolávat z čekajících operací.  
  
3. V opačném případě by měla být vrácena zpráva z Request() nebo Receive(). To zahrnuje případy, kdy vrstva rozpozná chybu, ale chyba pouze označuje, že požadavek se nezdařil a neznamená chybování kanálu a vyvolání z čekajících operací. Chcete-li zlepšit použitelnost v takovém případě `GetProperty<FaultConverter>` by `FaultConverter` měla vrstva implementovat a vrátit odvozenou `OnTryCreateException`třídu, která může převést chybu na výjimku přepsáním .  
  
 Následující objektový model podporuje převod zpráv na výjimky:  
  
```csharp
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
  
 Vrstva kanálu `GetProperty<FaultConverter>` můžete implementovat pro podporu převodu chybové zprávy na výjimky. Chcete-li tak `OnTryCreateException` učinit, přepsat a zkontrolujte zprávu o chybě. Pokud je rozpoznán, proveďte převod, jinak požádejte vnitřní kanál, aby jej převedl. Kanály přenosu `FaultConverter.GetDefaultFaultConverter` by měldelegovat získat výchozí SOAP/WS adresování FaultConverter.  
  
 Typická implementace vypadá takto:  
  
```csharp
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
  
 Pro konkrétní chybové podmínky, které mají odlišné scénáře `ProtocolException`obnovení, zvažte definování odvozené třídy .  
  
### <a name="mustunderstand-processing"></a>Zpracování musí pochopit  
 SOAP definuje obecnou chybu pro signalizaci, že příjemce nepochopil požadovanou hlavičku. Tato chyba se `mustUnderstand` označuje jako chyba. V WCF vlastní kanály nikdy generovat `mustUnderstand` chyby. Místo toho WCF Dispatcher, který je umístěn v horní části zásobníku komunikace WCF, zkontroluje, zda všechny hlavičky, které byly označeny jako MustUnderstand =true byly pochopeny základní zásobníku. Pokud některé nebyly pochopeny, `mustUnderstand` chyba je generována v tomto okamžiku. (Uživatel se může rozhodnout `mustUnderstand` toto zpracování vypnout a aplikaci přijímat všechna záhlaví zpráv. V takovém případě je aplikace `mustUnderstand` zodpovědná za zpracování.) Vygenerovaná chyba obsahuje hlavičku NotUnderstood, která obsahuje názvy všech záhlaví s MustUnderstand=true, které nebyly pochopeny.  
  
 Pokud váš kanál protokolu odešle vlastní záhlaví s `mustUnderstand` MustUnderstand=true a obdrží chybu, musí zjistit, zda je tato chyba způsobena hlavičkou, kterou odeslal. Ve `MessageFault` třídě jsou dva členy, které jsou užitečné pro toto:  
  
```csharp
public class MessageFault  
{  
    ...  
    public bool IsMustUnderstandFault { get; }  
    public static bool WasHeaderNotUnderstood(MessageHeaders headers,
        string name, string ns) { }  
    ...  
  
}  
```  
  
 `IsMustUnderstandFault`pokud `true` se závada `mustUnderstand` nachází v závadě. `WasHeaderNotUnderstood`vrátí, `true` pokud je záhlaví se zadaným názvem a oborem názvů zahrnuto do chyby jako hlavička NotUnderstood.  V opačném `false`případě vrátí .  
  
 Pokud kanál vyzařuje záhlaví, které je označeno MustUnderstand = true, pak by tato `mustUnderstand` vrstva měla také implementovat vzor rozhraní API pro generování výjimek a měla by převést chyby způsobené tímto záhlavím na užitečnější výjimku, jak je popsáno výše.  
  
## <a name="tracing"></a>Trasování  
 Rozhraní .NET Framework poskytuje mechanismus pro sledování spuštění programu jako způsob, jak pomoci diagnostikovat produkční aplikace nebo občasné problémy, kde není možné pouze připojit ladicí program a krokovat kód. Základní součásti tohoto mechanismu jsou <xref:System.Diagnostics?displayProperty=nameWithType> v oboru názvů a skládají se z:  
  
- <xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>, což je zdroj trasovací informace, které mají být zapsány , <xref:System.Diagnostics.TraceListener?displayProperty=nameWithType>, což je abstraktní <xref:System.Diagnostics.TraceSource> základní třída pro konkrétní posluchače, které přijímají informace, které mají být vysledovány z a výstup do cíle specifické pro posluchače. Například <xref:System.Diagnostics.XmlWriterTraceListener> výstupy trasování informace do souboru XML. Nakonec <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType>, který umožňuje uživateli aplikace řídit podrobnosti o trasování a je obvykle zadán v konfiguraci.  
  
- Kromě základních součástí můžete k zobrazení a prohledání trasování WCF použít [nástroj prohlížeč trasování služby (SvcTraceViewer.exe).](../service-trace-viewer-tool-svctraceviewer-exe.md) Nástroj je navržen speciálně pro trasovací soubory generované <xref:System.Diagnostics.XmlWriterTraceListener>WCF a psaný pomocí . Následující obrázek znázorňuje různé součásti, které se podílejí na trasování.  
  
 ![Zpracování výjimek a závad](./media/wcfc-tracinginchannelsc.gif "wcfc_TracingInChannelsc")  
  
### <a name="tracing-from-a-custom-channel"></a>Trasování z vlastního kanálu  
 Vlastní kanály by měly zapisovat trasovací zprávy, které by pomohly při diagnostice problémů, když není možné připojit ladicí program ke spuštěné aplikaci. To zahrnuje dva úkoly na vysoké <xref:System.Diagnostics.TraceSource> úrovni: Vytváření instancí a volání jeho metody pro zápis trasování.  
  
 Při vytváření instancí <xref:System.Diagnostics.TraceSource>a se zadaný řetězec stane názvem tohoto zdroje. Tento název se používá ke konfiguraci (povolit/zakázat/nastavit úroveň trasování) zdroj trasování. Zobrazí se také v samotném výstupu trasování. Vlastní kanály by měly používat jedinečný zdrojový název, který čtenářům výstupu trasování pomůže pochopit, odkud pocházejí informace o trasování. Použití názvu sestavení, které zapisuje informace jako název zdroje trasování je běžnou praxí. Například WCF používá System.ServiceModel jako zdroj trasování pro informace napsané ze sestavení System.ServiceModel.  
  
 Jakmile máte zdroj trasování, <xref:System.Diagnostics.TraceSource.TraceData%2A>zavoláte jeho , <xref:System.Diagnostics.TraceSource.TraceEvent%2A>nebo <xref:System.Diagnostics.TraceSource.TraceInformation%2A> metody pro zápis trasovacích položek do posluchačů trasování. Pro každou položku trasování, kterou zapíšete, je třeba klasifikovat typ události jako jeden z typů událostí definovaných v . <xref:System.Diagnostics.TraceEventType> Tato klasifikace a nastavení úrovně trasování v konfiguraci určují, zda je položka trasování výstupem na schytavku. Například nastavení úrovně trasování `Warning` v `Warning` `Error` konfiguraci umožňuje a `Critical` trasování položky, které mají být zapsány, ale blokuje informace a podrobné položky. Zde je příklad vytvoření instance zdroje trasování a zápisu položky na úrovni informace:  
  
```csharp
using System.Diagnostics;  
//...  
TraceSource udpSource = new TraceSource("Microsoft.Samples.Udp");  
//...  
udpsource.TraceInformation("UdpInputChannel received a message");  
```  
  
> [!IMPORTANT]
> Důrazně doporučujeme zadat název zdroje trasování, který je jedinečný pro váš vlastní kanál, který pomůže sledovat výstupní čtečky pochopit, odkud výstup pochází.  
  
#### <a name="integrating-with-the-trace-viewer"></a>Integrace s prohlížečem trasování  
 Trasování generované kanálem může být výstup ve formátu čitelné [masce služby (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) pomocí <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> jako naslouchací proces trasování. To není něco, co musíte jako vývojář kanálu udělat. Spíše je uživatel aplikace (nebo osoba řešení potíží s aplikací), který potřebuje nakonfigurovat tento naslouchací proces trasování v konfiguračním souboru aplikace. Například následující konfigurace výstupy trasování <xref:System.ServiceModel?displayProperty=nameWithType> `Microsoft.Samples.Udp` informace z `TraceEventsFile.e2e`obou a do souboru s názvem :  
  
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
 <xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>má <xref:System.Diagnostics.TraceSource.TraceData%2A> metodu, která trvá jeden nebo více objektů, které mají být zahrnuty do položky trasování. Obecně platí, <xref:System.Object.ToString%2A?displayProperty=nameWithType> že metoda je volána na každý objekt a výsledný řetězec je zapsán jako součást položky trasování. Při <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> použití k výstupu trasování, <xref:System.Xml.XPath.IXPathNavigable?displayProperty=nameWithType> můžete předat <xref:System.Diagnostics.TraceSource.TraceData%2A>jako datový objekt . Výsledná položka trasování zahrnuje xml <xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>poskytované . Zde je ukázková položka s daty aplikace XML:  
  
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
  
 Prohlížeč trasování WCF rozumí schématu `TraceRecord` dříve zobrazeného prvku a extrahuje data z podřízených prvků a zobrazí je v tabulkovém formátu. Váš kanál by měl používat toto schéma při trasování strukturovaných dat aplikace pomoci Uživatelům Svctraceviewer.exe číst data.
