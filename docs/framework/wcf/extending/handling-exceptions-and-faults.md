---
title: Zpracování výjimek a chyb
ms.date: 03/30/2017
ms.assetid: a64d01c6-f221-4f58-93e5-da4e87a5682e
ms.openlocfilehash: c28b4420be82562a30873b65113811da06cee761
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975479"
---
# <a name="handling-exceptions-and-faults"></a>Zpracování výjimek a chyb
Výjimky slouží ke sdělování chyb místně v rámci služby nebo implementace klienta. Na druhé straně chyby slouží k sdělování chyb napříč hranicemi služby, například ze serveru do klienta nebo naopak. Kromě chyb využívají přenosové kanály často mechanismy přenosu pro komunikaci s chybami na úrovni přenosu. Například přenos HTTP používá ke komunikaci neexistující adresy URL koncového bodu stavové kódy jako 404 (není k dispozici žádný koncový bod pro odeslání zpětné chyby). Tento dokument se skládá ze tří částí, které poskytují pokyny pro vlastní autory kanálů. První část poskytuje pokyny, kdy a jak definovat a vyvolat výjimky. Druhá část obsahuje pokyny k vytváření a využívání chyb. Třetí část vysvětluje, jak poskytnout trasovací informace pro pomoc uživateli vlastního kanálu při odstraňování potíží se spuštěnými aplikacemi.  
  
## <a name="exceptions"></a>Výjimky  
 Existují dvě věci, které je potřeba vzít v úvahu při vyvolání výjimky: nejdříve musí být typ, který umožňuje uživatelům napsat správný kód, který může reagovat odpovídajícím způsobem. Za druhé musí poskytnout dostatek informací, aby mohl uživatel pochopit, co se nepovedlo, dopad na selhání a jak ho opravit. Následující části obsahují pokyny týkající se typů výjimek a zpráv pro kanály Windows Communication Foundation (WCF). V pokynech pro návrh dokumentu výjimek jsou také k dispozici obecné pokyny týkající se výjimek v rozhraní .NET.  
  
### <a name="exception-types"></a>Typy výjimek  
 Všechny výjimky vyvolané kanály musí být buď <xref:System.TimeoutException?displayProperty=nameWithType>, <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>, nebo typ odvozený z <xref:System.ServiceModel.CommunicationException>. (Výjimky jako <xref:System.ObjectDisposedException> mohou být také vyvolány, ale pouze k označení toho, že volající kód má nepoužitý kanál. Pokud se kanál používá správně, musí vyvolávat pouze dané výjimky.) Služba WCF poskytuje sedm typů výjimek, které jsou odvozeny od <xref:System.ServiceModel.CommunicationException> a jsou určeny pro použití v kanálech. Existují další výjimky odvozené od <xref:System.ServiceModel.CommunicationException>, které jsou určeny pro použití jinými částmi systému. Tyto typy výjimek jsou:  
  
|Typ výjimky|Význam|Obsah vnitřní výjimky|Strategie obnovení|  
|--------------------|-------------|-----------------------------|-----------------------|  
|<xref:System.ServiceModel.AddressAlreadyInUseException>|Adresa koncového bodu určená pro naslouchání se již používá.|Pokud je k dispozici, poskytuje další podrobnosti o chybě přenosu, která způsobila tuto výjimku. Například. <xref:System.IO.PipeException>, <xref:System.Net.HttpListenerException>nebo <xref:System.Net.Sockets.SocketException>.|Zkuste jinou adresu.|  
|<xref:System.ServiceModel.AddressAccessDeniedException>|Proces není povolený přístup k adrese koncového bodu zadané pro naslouchání.|Pokud je k dispozici, poskytuje další podrobnosti o chybě přenosu, která způsobila tuto výjimku. Například <xref:System.IO.PipeException>nebo <xref:System.Net.HttpListenerException>.|Zkuste použít jiné přihlašovací údaje.|  
|<xref:System.ServiceModel.CommunicationObjectFaultedException>|Použitý <xref:System.ServiceModel.ICommunicationObject> je v chybovém stavu (Další informace najdete v tématu [porozumění změnám stavu](understanding-state-changes.md)). Všimněte si, že pokud objekt s více nevyřízenými voláními přechází do chybového stavu, vyvolá pouze jedno volání výjimku, která souvisí s chybou a zbytek volání vyvolá <xref:System.ServiceModel.CommunicationObjectFaultedException>. Tato výjimka je obvykle vyvolána, protože aplikace vyhledává určitou výjimku a pokouší se použít již chybný objekt, pravděpodobně na jiném vlákně, než je ten, který zachytil původní výjimku.|Pokud je k dispozici, zobrazí se podrobnosti o vnitřní výjimce.|Vytvoří nový objekt. Všimněte si, že v závislosti na tom, co způsobilo selhání <xref:System.ServiceModel.ICommunicationObject> v prvním místě, se může stát, že bude nutné obnovit další práci.|  
|<xref:System.ServiceModel.CommunicationObjectAbortedException>|Použitá <xref:System.ServiceModel.ICommunicationObject> byla přerušena (Další informace naleznete v tématu [porozumění změnám stavu](understanding-state-changes.md)). Podobně jako <xref:System.ServiceModel.CommunicationObjectFaultedException>, jeho výjimka označuje, že aplikace volala <xref:System.ServiceModel.ICommunicationObject.Abort%2A> na objektu, případně z jiného vlákna, a objekt již z tohoto důvodu není použitelný.|Pokud je k dispozici, zobrazí se podrobnosti o vnitřní výjimce.|Vytvoří nový objekt. Všimněte si, že v závislosti na tom, co způsobilo přerušování <xref:System.ServiceModel.ICommunicationObject> v prvním místě, může být nutné provést další práci, kterou je potřeba obnovit.|  
|<xref:System.ServiceModel.EndpointNotFoundException>|Cílový vzdálený koncový bod nenaslouchá. To může vést k tomu, že všechny části adresy koncového bodu jsou nesprávné, nevyřešitelná nebo koncový bod. Mezi příklady patří Chyba služby DNS, správce front není dostupný a služba není spuštěná.|Vnitřní výjimka poskytuje podrobnosti, obvykle z podkladového přenosu.|Zkuste jinou adresu. Případně může odesílatel chvíli počkat a zkusit to znovu, pokud služba byla vypnutá.|  
|<xref:System.ServiceModel.ProtocolException>|Komunikační protokoly, jak je popsáno v zásadách koncového bodu, se neshodují mezi koncovými body. Například byl překročen počet neshody typů obsahu rámců nebo maximální velikost zprávy.|Pokud je k dispozici, zobrazí se další informace o chybě konkrétního protokolu. Například <xref:System.ServiceModel.QuotaExceededException> je vnitřní výjimka, když příčina chyby překročí třídu MaxReceivedMessageSize.|Obnovení: Ujistěte se, že se nastavení odesílatele a přijatého protokolu shodují. To lze provést tak, že znovu naimportujete metadata koncového bodu služby (zásady) a pomocí vygenerované vazby znovu vytvoříte kanál.|  
|<xref:System.ServiceModel.ServerTooBusyException>|Vzdálený koncový bod naslouchá, ale není připraven ke zpracování zpráv.|Je-li k dispozici, vnitřní výjimka poskytuje chyby protokolu SOAP nebo podrobnosti o chybě na úrovni přenosu.|Obnovení: Počkejte a opakujte operaci později.|  
|<xref:System.TimeoutException>|Operaci se nepovedlo dokončit v časovém limitu.|Může poskytnout podrobnosti o vypršení časového limitu.|Počkejte a opakujte operaci později.|  
  
 Definujte nový typ výjimky pouze v případě, že tento typ odpovídá konkrétní strategii obnovení, která se liší od všech stávajících typů výjimek. Pokud definujete nový typ výjimky, musí odvozovat z <xref:System.ServiceModel.CommunicationException> nebo jedné z jeho odvozených tříd.  
  
### <a name="exception-messages"></a>Zprávy výjimek  
 Zprávy o výjimkách jsou zaměřeny na uživatele, který není programem, takže by měli poskytnout dostatečné informace, které uživateli pomohou pochopit a vyřešit problém. Mezi tři podstatné části dobré zprávy o výjimce patří:  
  
 Co se přihodilo. Zadejte jasný popis problému s použitím podmínek, které se vztahují k uživatelskému prostředí. Zpráva o špatné výjimce by mohla být například "neplatný konfigurační oddíl". Tím se uživateli zajímá, který konfigurační oddíl je nesprávný a proč není správný. Vylepšená zpráva bude "neplatný konfigurační oddíl \<customBinding >". Ještě lepší zpráva by byla "nelze přidat Transport s názvem myTransport do vazby s názvem myBinding, protože vazba již má Transport s názvem myTransport". Toto je velmi specifická zpráva s použitím podmínek a názvů, které může uživatel snadno identifikovat v konfiguračním souboru aplikace. Stále však chybí několik klíčových součástí.  
  
 Význam chyby. Pokud se zpráva nezřetelně nejedná o chybu, uživatel bude pravděpodobně zajímat, zda se jedná o závažnou chybu, nebo zda může být ignorována. Obecně by zprávy měly vést s významem nebo významem chyby. Aby bylo možné vylepšit předchozí příklad, zpráva může být "hostitel ServiceHost se nepodařilo otevřít z důvodu chyby v konfiguraci: nelze přidat Transport s názvem myTransport do vazby s názvem myBinding, protože vazba již má přenos s názvem myTransport".  
  
 Jak by měl uživatel problém vyřešit. Nejdůležitější část zprávy pomáhá uživateli problém vyřešit. Zpráva by měla obsahovat některé doprovodné materiály nebo doporučení týkající se toho, co je třeba opravit nebo opravit, aby problém mohl vyřešit. Například "hostitel ServiceHost se nepodařilo otevřít z důvodu chyby v konfiguraci: do vazby s názvem myBinding nelze přidat přenos s názvem myTransport, protože vazba již má přenos s názvem myTransport. Ujistěte se prosím, že vazba obsahuje jenom jeden přenos.  
  
## <a name="communicating-faults"></a>Komunikace s chybami  
 SOAP 1,1 a SOAP 1,2 definují specifickou strukturu pro chyby. Existují některé rozdíly mezi těmito dvěma specifikacemi, ale obecně jsou typy zpráva a parametr MessageFault použity k vytváření a zpracování chyb.  
  
 ![Zpracování výjimek a chyb](./media/wcfc-soap1-1andsoap1-2faultcomparisonc.gif "wcfc_SOAP1 – 1AndSOAP1 – 2FaultComparisonc")  
Chyba protokolu SOAP 1,2 (Left) a chyby SOAP 1,1 (vpravo). Všimněte si, že v SOAP 1,1 pouze element fault je kvalifikovaný obor názvů.  
  
 SOAP definuje zprávu o chybě jako zprávu, která obsahuje pouze element Fault (element, jehož název je `<env:Fault>`) jako podřízený objekt `<env:Body>`. Obsah chybného prvku se mírně liší mezi SOAP 1,1 a SOAP 1,2, jak je znázorněno na obrázku 1. Nicméně třída <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType> normalizuje tyto rozdíly do jednoho objektového modelu:  
  
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
  
 Vlastnost `Code` odpovídá `env:Code` (nebo `faultCode` v protokolu SOAP 1,1) a identifikuje typ chyby. Protokol SOAP 1,2 definuje pět přípustných hodnot pro `faultCode` (například sender a přijímač) a definuje `Subcode` element, který může obsahovat libovolnou hodnotu podkódu. (Viz [specifikace protokolu SOAP 1,2](https://go.microsoft.com/fwlink/?LinkId=95176) pro seznam povolených kódů chyb a jejich význam) Protokol SOAP 1,1 má mírně odlišný mechanismus: definuje čtyři `faultCode` hodnoty (například klient a Server), které se dají rozšířit tak, že se nadefinují zcela nové nebo pomocí zápisu teček vytvoří konkrétnější `faultCodes`, například Client. Authentication.  
  
 Použijete-li parametr MessageFault k programovým chybám, FaultCode.Name a FaultCode. Namespace se mapují na název a obor názvů `env:Code` protokolu SOAP 1,2 nebo `faultCode`SOAP 1,1. FaultCode. Subcode mapuje na `env:Subcode` pro SOAP 1,2 a pro SOAP 1,1 je null.  
  
 Měli byste vytvořit nové podkódy chyb (nebo nové kódy chyb, pokud používáte protokol SOAP 1,1), pokud je to zajímavé pro programové odlišení chyby. To je podobné jako vytvoření nového typu výjimky. Nepoužívejte zápis tečky s kódy chyb SOAP 1,1. ( [Základní profil WS-I](https://go.microsoft.com/fwlink/?LinkId=95177) také nedoporučuje použití zápisu teček v kódu chyby.)  
  
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
  
 Vlastnost `Reason` odpovídá `env:Reason` (nebo `faultString` v protokolu SOAP 1,1) s popisem chybového stavu, který se podobá zprávě výjimky, uživatelsky čitelný. Třída `FaultReason` (a SOAP `env:Reason/faultString`) obsahuje integrovanou podporu pro více překladů v zájmu globalizace.  
  
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
  
 Obsah podrobností o chybě se zveřejňuje na parametr MessageFault pomocí různých metod, včetně `GetDetail`\<T > a `GetReaderAtDetailContents`(). Podrobnosti o chybě je neprůhledný prvek pro další podrobnosti o chybě. To je užitečné v případě, že existuje několik libovolných strukturovaných podrobností, které chcete s chybou přenášet.  
  
### <a name="generating-faults"></a>Generují se chyby.  
 Tato část vysvětluje proces generování chyby v reakci na chybový stav zjištěný v kanálu nebo ve vlastnosti zprávy vytvořené kanálem. Typický příklad posílá zpět chybu v reakci na zprávu požadavku, která obsahuje neplatná data.  
  
 Při generování chyby by vlastní kanál neměl přímo odeslat chybu, místo toho by měla vyvolat výjimku a nechat vrstvu výše rozhodnout, zda má být tato výjimka převedena na chybu a jak ji odeslat. Pro pomoc v tomto převodu by měl kanál poskytovat `FaultConverter` implementaci, která může převést výjimku vyvolanou vlastním kanálem na příslušnou chybu. `FaultConverter` je definován jako:  
  
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
  
 Každý kanál, který generuje vlastní chyby, musí implementovat `FaultConverter` a vracet ho ze volání `GetProperty<FaultConverter>`. Vlastní implementace `OnTryCreateFaultMessage` musí buď převést výjimku na chybu, nebo delegovat na `FaultConverter`vnitřního kanálu. Pokud je kanálem přenos, musí buď převést výjimku nebo delegáta na `FaultConverter` kodéru, nebo výchozí `FaultConverter` poskytovaný v rámci WCF. Výchozí `FaultConverter` převádí chyby odpovídající chybovým zprávám určeným protokolem WS-Addressing a SOAP. Tady je příklad implementace `OnTryCreateFaultMessage`.  
  
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
  
 Nenásobení tohoto vzoru je, že výjimky vyvolané mezi vrstvami pro chybové stavy, které vyžadují chyby, musí obsahovat dostatek informací pro odpovídající generátor chyb pro vytvoření správné chyby. Jako autor vlastního kanálu můžete definovat typy výjimek, které odpovídají různým chybám, pokud takové výjimky ještě neexistují. Všimněte si, že vrstvy přesměrované kanály by měly sdělit chybový stav, nikoli neprůhledná data chyby.  
  
### <a name="fault-categories"></a>Kategorie chyb  
 Existují všeobecně tři kategorie chyb:  
  
1. Chyby, které se Pervasive v celém zásobníku. K těmto chybám může dojít v libovolné vrstvě v zásobníku kanálů, například InvalidCardinalityAddressingException.  
  
2. Chyby, které mohou být zjištěny kdekoli nad určitou vrstvou v zásobníku, například některé chyby, které se týkají toku transakce nebo rolí zabezpečení.  
  
3. Chyby směrované na jednu vrstvu v zásobníku, například chyby, jako je číslo sekvence WS-RM, chyba.  
  
 Kategorie 1. Chyby jsou obecně WS-Addressing a SOAP chyby. Základní `FaultConverter` třída poskytovaná službou WCF převádí chyby odpovídající chybovým zprávám určeným protokolem WS-Addressing a SOAP, takže nemusíte tyto výjimky zpracovávat sami.  
  
 Kategorie 2. K chybám dochází, když vrstva přidá vlastnost do zprávy, která zcela nespotřebovává informace zprávy, které se vztahují k této vrstvě. Chyby mohou být zjištěny později, pokud vyšší vrstva požádá o vlastnost zprávy o zpracování informací o zprávách. Tyto kanály by měly implementovat `GetProperty` zadanou dříve, aby vyšší vrstva mohla odeslat zpět správnou chybu. Příkladem je TransactionMessageProperty. Tato vlastnost se přidá do zprávy bez úplného ověřování všech dat v hlavičce (v takovém případě může zahrnovat kontaktování služby DTC (Distributed Transaction Coordinator).  
  
 Kategorie 3. Chyby jsou generovány a odesílány pouze jednou vrstvou v procesoru. Všechny výjimky jsou proto obsaženy v rámci vrstvy. Aby bylo možné zvýšit konzistenci mezi kanály a snadnou údržbou, váš vlastní kanál by měl pomocí výše uvedeného vzoru vygenerovat chybové zprávy, a to i u interních chyb.  
  
### <a name="interpreting-received-faults"></a>Interpretují se přijaté chyby.  
 V této části najdete pokyny k vygenerování vhodné výjimky při příjmu chybové zprávy. Rozhodovací strom pro zpracování zprávy v každé vrstvě v zásobníku je následující:  
  
1. Pokud vrstva považuje zprávu za neplatnou, měla by tato vrstva provádět zpracování "neplatné zprávy". Toto zpracování je specifické pro vrstvu, ale může zahrnovat vyřazení zprávy, trasování nebo vyvolání výjimky, která je převedena na chybu. Příkladem může být zabezpečení přijímání zprávy, která není správně zabezpečena nebo správce prostředků obdržel zprávu s chybným pořadovým číslem.  
  
2. V opačném případě, pokud se jedná o zprávu o chybě, která se vztahuje konkrétně na vrstvu, a zpráva není smysluplná mimo interakci vrstvy, měla by vrstva zpracovat chybový stav. Příkladem je, že sekvence RM odmítla chybu, která nemá smysl na vrstvy nad kanálem RM a který implikuje chybu kanálu RM a vyvolává se z nevyřízených operací.  
  
3. V opačném případě by měla být zpráva vrácena z Request () nebo Receive (). To zahrnuje případy, kdy vrstva rozpoznala chybu, ale chyba právě indikuje, že žádost selhala a neznamená chybu kanálu a vyvolání z nevyřízených operací. Pro zlepšení použitelnosti v takovém případě by měla vrstva implementovat `GetProperty<FaultConverter>` a vracet `FaultConverter` odvozenou třídu, která může chybu převést na výjimku přepsáním `OnTryCreateException`.  
  
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
  
 Vrstva kanálu může implementovat `GetProperty<FaultConverter>` pro podporu převodu chybových zpráv na výjimky. Provedete to tak, že přepíšete `OnTryCreateException` a zkontrolujete zprávu o chybě. Je-li rozpoznán, proveďte převod, jinak požádejte o převod na vnitřní kanál. Přenosové kanály by měly `FaultConverter.GetDefaultFaultConverter`, aby se získal výchozí protokol SOAP/WS-Addressing FaultConverter.  
  
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
  
 Pro konkrétní chybové stavy, které mají odlišné scénáře obnovení, zvažte definování odvozené třídy `ProtocolException`.  
  
### <a name="mustunderstand-processing"></a>Zpracování MustUnderstand  
 Protokol SOAP definuje obecnou chybu pro signalizaci, že příjemce nerozuměl požadované záhlaví. Tato chyba je známá jako chyba `mustUnderstand`. Ve službě WCF nikdy negenerují vlastní kanály `mustUnderstand` chyby. Místo toho služba WCF Dispatcher, která je umístěna v horní části komunikačního zásobníku WCF, zkontroluje, zda je v podkladovém zásobníku porozuměla všechna záhlaví označená jako MustUnderstand = true. Pokud některý z nich nebyl pochopen, vygeneruje se v tomto okamžiku `mustUnderstand`á chyba. (Uživatel se může rozhodnout vypnout toto `mustUnderstand` zpracování a aplikace obdrží všechna záhlaví zpráv. V takovém případě je aplikace zodpovědná za provádění `mustUnderstand`ho zpracování.) Vygenerovaná chyba zahrnuje hlavičku NotUnderstood, která obsahuje názvy všech hlaviček s MustUnderstand = true, které se nerozuměly.  
  
 Pokud kanál protokolu odešle vlastní hlavičku s MustUnderstand = true a obdrží chybu `mustUnderstand`, musí zjistit, jestli je tato chyba způsobená hlavičkou, kterou odeslala. Existují dva členy `MessageFault` třídy, které jsou užitečné pro tuto třídu:  
  
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
  
 `IsMustUnderstandFault` vrátí `true`, pokud se jedná o chybu `mustUnderstand`. `WasHeaderNotUnderstood` vrátí `true`, pokud je hlavička se zadaným názvem a oborem názvů obsažena v chybě jako hlavička NotUnderstood.  V opačném případě vrátí `false`.  
  
 Pokud kanál vygeneruje hlavičku, která je označena jako MustUnderstand = true, pak by tato vrstva měla také implementovat vzor rozhraní API generování výjimek a měla by převést `mustUnderstand` chyby způsobené touto hlavičkou na užitečnější výjimku, jak je popsáno výše.  
  
## <a name="tracing"></a>Trasování  
 .NET Framework poskytuje mechanismus pro trasování spuštění programu jako způsob, jak pomoci diagnostikovat produkčních aplikací nebo občasné problémy, kde není možné pouze připojit ladicí program a krokovat kód. Základní komponenty tohoto mechanismu jsou v oboru názvů <xref:System.Diagnostics?displayProperty=nameWithType> a skládají se z:  
  
- <xref:System.Diagnostics.TraceSource?displayProperty=nameWithType>, což je zdroj trasovacích informací, které mají být zapsány, <xref:System.Diagnostics.TraceListener?displayProperty=nameWithType>, což je abstraktní základní třída pro konkrétní naslouchací procesy, které obdrží informace, které mají být trasovány z <xref:System.Diagnostics.TraceSource> a jejich výstup do cíle specifického pro naslouchací proces. Například <xref:System.Diagnostics.XmlWriterTraceListener> výstupy trasovacích informací do souboru XML. Nakonec <xref:System.Diagnostics.TraceSwitch?displayProperty=nameWithType>, která umožňuje uživatelskému ovládacímu prvku aplikace sledovat podrobnosti trasování a je obvykle zadáno v konfiguraci.  
  
- Kromě základních komponent můžete použít [Nástroj pro prohlížeč trasování služby (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) k zobrazení a hledání trasování WCF. Nástroj je navržen speciálně pro trasovací soubory vygenerované službou WCF a zapisují se pomocí <xref:System.Diagnostics.XmlWriterTraceListener>. Následující obrázek znázorňuje různé komponenty, které jsou součástí trasování.  
  
 ![Zpracování výjimek a chyb](./media/wcfc-tracinginchannelsc.gif "wcfc_TracingInChannelsc")  
  
### <a name="tracing-from-a-custom-channel"></a>Trasování z vlastního kanálu  
 Vlastní kanály by měly vypsat zprávy trasování, které vám pomůžou diagnostikovat problémy, když není možné připojit ladicí program ke spuštěné aplikaci. To zahrnuje dva úlohy na nejvyšší úrovni: vytvoření instance <xref:System.Diagnostics.TraceSource> a volání jeho metod pro zápis trasování.  
  
 Při vytváření instance <xref:System.Diagnostics.TraceSource>se řetězec, který zadáte, bude název tohoto zdroje. Tento název se používá ke konfiguraci (povolení nebo zakázání/nastavení úrovně trasování) zdroje trasování. Také se zobrazí ve výstupu trasování. Vlastní kanály by měly používat jedinečný název zdroje, aby usnadnili čtenářům výstup trasování pochopit, odkud informace o trasování pocházejí. Použití názvu sestavení, které zapisuje informace jako název zdroje trasování, je běžný postup. Například WCF používá jako zdroj trasování System. ServiceModel pro informace napsané ze sestavení System. ServiceModel.  
  
 Jakmile budete mít zdroj trasování, zavolejte jeho <xref:System.Diagnostics.TraceSource.TraceData%2A>, <xref:System.Diagnostics.TraceSource.TraceEvent%2A>nebo <xref:System.Diagnostics.TraceSource.TraceInformation%2A> metody pro zápis trasovacích položek do posluchačů trasování. Pro každý záznam trasování, který zapisujete, je třeba klasifikovat typ události jako jeden z typů událostí definovaných v <xref:System.Diagnostics.TraceEventType>. Tato klasifikace a nastavení úrovně trasování v konfiguraci určují, zda je záznam trasování výstupem naslouchacího procesu. Například nastavení úrovně trasování v konfiguraci na `Warning` povoluje zápis `Warning`, `Error` a `Critical` záznamů trasování, ale blokuje informace a podrobné položky. Tady je příklad vytvoření instance zdroje trasování a zápis položky na úrovni informací:  
  
```csharp
using System.Diagnostics;  
//...  
TraceSource udpSource = new TraceSource("Microsoft.Samples.Udp");  
//...  
udpsource.TraceInformation("UdpInputChannel received a message");  
```  
  
> [!IMPORTANT]
> Důrazně doporučujeme zadat název zdroje trasování, který je jedinečný pro váš vlastní kanál, aby bylo možné sledovat čtecí zařízení pro výstup a pochopit, odkud výstup pochází.  
  
#### <a name="integrating-with-the-trace-viewer"></a>Integrace s prohlížečem trasování  
 Trasování generovaná vaším kanálem může být výstupem ve formátu čitelném [nástrojem pro prohlížení služby Service Trace (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) pomocí <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> jako naslouchací proces trasování. Nejedná se o něco, co je třeba pro vývojáře kanálu. Místo toho je uživatel aplikace (nebo osoba, která řešení potíží s aplikací), která vyžaduje konfiguraci tohoto naslouchacího procesu trasování v konfiguračním souboru aplikace. Následující konfigurace například vypíše informace o trasování z <xref:System.ServiceModel?displayProperty=nameWithType> a `Microsoft.Samples.Udp` do souboru s názvem `TraceEventsFile.e2e`:  
  
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
 <xref:System.Diagnostics.TraceSource?displayProperty=nameWithType> má <xref:System.Diagnostics.TraceSource.TraceData%2A> metodu, která přebírá jeden nebo více objektů, které mají být zahrnuty do položky trasování. Obecně je metoda <xref:System.Object.ToString%2A?displayProperty=nameWithType> volána pro každý objekt a výsledný řetězec je zapsán jako součást položky trasování. Při použití <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> pro výstup trasování můžete předat <xref:System.Xml.XPath.IXPathNavigable?displayProperty=nameWithType> jako datový objekt <xref:System.Diagnostics.TraceSource.TraceData%2A>. Výsledná položka trasování obsahuje XML od <xref:System.Xml.XPath.XPathNavigator?displayProperty=nameWithType>. Tady je příklad položky s daty aplikace XML:  
  
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
  
 Prohlížeč trasování WCF rozumí schématu `TraceRecord`ho prvku, který jste předtím ukázali, extrahuje data z jejích podřízených prvků a zobrazí je v tabulkovém formátu. Kanál by měl používat toto schéma při trasování strukturovaných dat aplikace, aby uživatelé SvcTraceViewer. exe mohli data číst.
