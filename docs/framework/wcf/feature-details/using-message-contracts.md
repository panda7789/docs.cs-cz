---
title: Použití kontraktů zpráv
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message contracts [WCF]
ms.assetid: 1e19c64a-ae84-4c2f-9155-91c54a77c249
ms.openlocfilehash: 34f1c761a127fe00612259a79dae47d1c9d5512f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54534417"
---
# <a name="using-message-contracts"></a>Použití kontraktů zpráv
Obvykle při vytváření aplikací Windows Communication Foundation (WCF), vývojáři pozornosti datových struktur a problémům se serializací a není nutné starat struktura zpráv, ve kterých se provádí s data. V případě těchto aplikací je jednoduché vytváření kontraktů dat pro parametry nebo návratové hodnoty. (Další informace najdete v tématu [zadání přenosu dat v kontraktech služeb](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).)  
  
 Ale někdy úplnou kontrolu nad strukturou zprávu protokolu SOAP je stejně důležité jako kontrolu nad jeho obsah. To platí zejména při zajištění lepší interoperability je důležité nebo konkrétně řízení zabezpečení problémy na úrovni zprávy nebo část zprávy. V těchto případech můžete vytvořit *kontraktu zprávy* , který umožňuje určit strukturu přesné zprávu protokolu SOAP vyžaduje.  
  
 Toto téma popisuje, jak použít různé atributy kontraktu zprávy k vytvoření kontraktu zprávy specifické pro vaši operaci.  
  
## <a name="using-message-contracts-in-operations"></a>Použití kontraktů zpráv v operacích  
 WCF podporuje operace vymodelován buď *vzdálené volání (procedur RPC) styl* nebo *zasílání zpráv styl*. V operaci stylu RPC, můžete použít libovolný serializovatelný typ., a budete mít přístup k funkcím, které jsou k dispozici pro místní volání, jako je například více parametrů a `ref` a `out` parametry. V tomto stylu forma serializace zvolit řídí strukturu dat v podkladové zprávy a zprávy, které mají podporovat operaci, vytvoří modul runtime WCF. To umožňuje vývojářům, kteří nejsou obeznámeni s SOAP a zpráv SOAP rychle a snadno vytvářet a používat služby aplikace.  
  
 Následující příklad kódu ukazuje operaci služby modelována ve stylu RPC.  
  
```csharp  
[OperationContract]  
public BankingTransactionResponse PostBankingTransaction(BankingTransaction bt);  
```  
  
 Za normálních okolností kontraktu dat. stačí definovat schéma pro zprávy. Například v předchozím příkladu je dostatečné pro většinu aplikací Pokud `BankingTransaction` a `BankingTransactionResponse` mít kontraktů dat zadat obsah základní zprávy protokolu SOAP. Další informace o kontraktech dat najdete v tématu [kontraktů dat pomocí](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
 Ale čas od času je potřeba přesně řídit, jak přenést struktura zprávu protokolu SOAP přenosu. Nejběžnější scénář je vložení vlastní hlavičky SOAP. Další z typických možností je, který je definování zabezpečení vlastností záhlaví a text zprávy, se rozhodnout, jestli tyto prvky jsou digitálně podepsané a šifrovaná. A konečně některé balíčky třetích stran SOAP vyžadují zpráv v určitém formátu. Operace zasílání zpráv ve stylu poskytují tohoto ovládacího prvku.  
  
 Operace zasílání zpráv ve stylu má maximálně jeden parametr a návratové hodnoty jednoho kde oba typy jsou typy zpráv; To znamená že serializovat přímo do struktury zadané zprávy protokolu SOAP. To může být libovolný typ označené <xref:System.ServiceModel.MessageContractAttribute> nebo <xref:System.ServiceModel.Channels.Message> typu. Následující příklad kódu ukazuje operaci podobně jako v předchozím stylu RCP, ale zasílání zpráv styl, který používá.  
  
 Například pokud `BankingTransaction` a `BankingTransactionResponse` se oba typy kontraktů zpráv, pak kód v následující operace je platná.  
  
```csharp  
[OperationContract]  
BankingTransactionResponse Process(BankingTransaction bt);  
[OperationContract]  
void Store(BankingTransaction bt);  
[OperationContract]  
BankingTransactionResponse GetResponse();  
```  
  
 Následující kód je však neplatný.  
  
```csharp  
[OperationContract]  
bool Validate(BankingTransaction bt);  
// Invalid, the return type is not a message contract.  
[OperationContract]  
void Reconcile(BankingTransaction bt1, BankingTransaction bt2);  
// Invalid, there is more than one parameter.  
```  
  
 Pro jakoukoli operaci, která zahrnuje typ kontraktu zprávy a není, proveďte jeden z platných vzorů je vyvolána výjimka. Samozřejmě operace, které nezahrnují typy kontraktů zpráv se nevztahují tato omezení.  
  
 Pokud je typ kontraktu zprávy a kontraktem dat, pouze jeho kontraktu zprávy se považuje za při použití typu v rámci operace.  
  
## <a name="defining-message-contracts"></a>Definování kontraktů zpráv  
 K definování kontraktu zprávy pro typ (to znamená, chcete-li definovat mapování mezi typem a obálku protokolu SOAP), použít <xref:System.ServiceModel.MessageContractAttribute> typu. Následně použít <xref:System.ServiceModel.MessageHeaderAttribute> na tyto členy typu, které chcete vytvořit jako záhlaví SOAP a použít <xref:System.ServiceModel.MessageBodyMemberAttribute> těmto členům chcete přejít do části těla protokolu SOAP zprávy.  
  
 Následující kód obsahuje příklad pomocí kontraktu zprávy.  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageHeader] public DateTime transactionDate;  
  [MessageBodyMember] private Account sourceAccount;  
  [MessageBodyMember] private Account targetAccount;  
  [MessageBodyMember] public int amount;  
}  
```  
  
 Při použití tohoto typu jako parametr operace, je vygenerována následující obálky protokolu SOAP:  
  
```xml  
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
  <s:Header>  
    <h:operation xmlns:h="http://tempuri.org/" xmlns="http://tempuri.org/">Deposit</h:operation>  
    <h:transactionDate xmlns:h="http://tempuri.org/" xmlns="http://tempuri.org/">2012-02-16T16:10:00</h:transactionDate>  
  </s:Header>  
  <s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
    <BankingTransaction xmlns="http://tempuri.org/">  
      <amount>0</amount>  
      <sourceAccount xsi:nil="true"/>  
      <targetAccount xsi:nil="true"/>  
    </BankingTransaction>  
  </s:Body>  
</s:Envelope>  
```  
  
 Všimněte si, že `operation` a `transactionDate` zobrazují jako záhlaví SOAP a SOAP body se skládá z prvku obálky `BankingTransaction` obsahující `sourceAccount`,`targetAccount`, a `amount`.  
  
 Můžete použít <xref:System.ServiceModel.MessageHeaderAttribute> a <xref:System.ServiceModel.MessageBodyMemberAttribute> pro všechna pole, vlastnosti a události, bez ohledu na to, zda jsou veřejné, privátní, chráněné nebo interní.  
  
 <xref:System.ServiceModel.MessageContractAttribute> Vám umožní určit WrapperName a WrapperNamespace atributy, které řídí název prvku obálky v těle zprávy protokolu SOAP. Ve výchozím nastavení název kontraktu zprávy typ se používá pro obálku a obor názvů, ve kterém je definována kontraktu zprávy `http://tempuri.org/` slouží jako výchozí obor názvů.  
  
> [!NOTE]
>  <xref:System.Runtime.Serialization.KnownTypeAttribute> atributy se ignorují v kontraktů zpráv. Pokud <xref:System.Runtime.Serialization.KnownTypeAttribute> je potřeba, umístěte ho na operaci, která používá kontrakt zprávy dotyčný.  
  
## <a name="controlling-header-and-body-part-names-and-namespaces"></a>Řízení hlavička a tělo část názvy a obory názvů  
 V reprezentaci kontraktu zprávy protokolu SOAP každá část hlavička a tělo zprávy mapuje na element XML, který má název a obor názvů.  
  
 Ve výchozím nastavení, stejně jako obor názvů kontraktu služby, který je součástí zprávy a název je určen název členu, ke které je obor názvů <xref:System.ServiceModel.MessageHeaderAttribute> nebo <xref:System.ServiceModel.MessageBodyMemberAttribute> atributy jsou použity.  
  
 Tato výchozí nastavení můžete změnit pomocí manipulace s <xref:System.ServiceModel.MessageContractMemberAttribute.Name%2A?displayProperty=nameWithType> a <xref:System.ServiceModel.MessageContractMemberAttribute.Namespace%2A?displayProperty=nameWithType> (na nadřazené třídu <xref:System.ServiceModel.MessageHeaderAttribute> a <xref:System.ServiceModel.MessageBodyMemberAttribute> atributy).  
  
 Vezměte v úvahu třídu v následujícím příkladu kódu.  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageHeader(Namespace="http://schemas.contoso.com/auditing/2005")] public bool IsAudited;  
  [MessageBodyMember(Name="transactionData")] public BankingTransactionData theData;  
}  
```  
  
 V tomto příkladu `IsAudited` záhlaví je v oboru názvů určenému v kódu a část textu, který představuje `theData` člen je reprezentována element XML s názvem `transactionData`. Následuje ukázka kódem XML vygenerovaným pro tento kontrakt zprávy.  
  
```xml  
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">  
  <s:Header>  
    <h:IsAudited xmlns:h="http://schemas.contoso.com/auditing/2005" xmlns="http://schemas.contoso.com/auditing/2005">false</h:IsAudited>  
    <h:operation xmlns:h="http://tempuri.org/" xmlns="http://tempuri.org/">Deposit</h:operation>  
  </s:Header>  
  <s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
    <AuditedBankingTransaction xmlns="http://tempuri.org/">  
      <transactionData/>  
    </AuditedBankingTransaction>  
  </s:Body>  
</s:Envelope>  
```  
  
## <a name="controlling-whether-the-soap-body-parts-are-wrapped"></a>Řízení, zda jsou zabaleny částí textu protokolu SOAP  
 Ve výchozím nastavení částí textu SOAP serializují uvnitř zabalené elementu. Například následující kód ukazuje `HelloGreetingMessage` element obálky, které jsou generovány z názvu <xref:System.ServiceModel.MessageContractAttribute> typ v kontraktu zprávy pro `HelloGreetingMessage` zprávy.  
  
[!code-csharp[MessageHeaderAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/messageheaderattribute/cs/services.cs#3)]
[!code-vb[MessageHeaderAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/messageheaderattribute/vb/services.vb#3)]  
  
 Chcete-li potlačit element obálky, nastavte <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> vlastnost `false`. Pokud chcete nastavit název a obor názvů element obálky, použijte <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> a <xref:System.ServiceModel.MessageContractAttribute.WrapperNamespace%2A> vlastnosti.  
  
> [!NOTE]
>  S více než jednu část textu zprávy ve zprávách, které nejsou zabaleny není kompatibilní s WS-I Basic Profile 1.1 a nedoporučuje se při navrhování nových kontraktů zpráv. Však může být potřeba mít více než jednu část textu nerozbalené zprávy v některých scénářích konkrétní vzájemná funkční spolupráce. Pokud budete přenášet víc než jednu část dat v textu zprávy, se doporučuje použít režim výchozí (zabalená). Nerozbalené zprávy s více než jedno záhlaví zprávy je zcela přijatelné.  
  
## <a name="using-custom-types-inside-message-contracts"></a>Použití vlastních typů uvnitř kontraktů zpráv  
 Každá hlavička jednotlivých zpráv a část textu zprávy serializován (převedena na XML) pomocí zvolené Serializační stroj pro servisní smlouvy použití zprávy. Modul výchozí serializace `XmlFormatter`, zvládne libovolný typ, který má kontraktu dat, buď explicitně (tím, že <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType>) nebo implicitně (tím je primitivního typu, které mají <xref:System.SerializableAttribute?displayProperty=nameWithType>, a tak dále). Další informace najdete v tématu [kontraktů dat pomocí](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
 V předchozím příkladu `Operation` a `BankingTransactionData` typy musí mít kontraktu dat, a `transactionDate` serializovat protože <xref:System.DateTime> je jednoduchého typu (a tedy má implicitní data).  
  
 Je však možné přepnout na jinou Serializační stroj, `XmlSerializer`. Pokud provedete tyto přepínače, měli byste zajistit, že všechny typy použité pro záhlaví zpráv a částí textu jsou serializovatelné pomocí `XmlSerializer`.  
  
## <a name="using-arrays-inside-message-contracts"></a>Použití polí uvnitř kontraktů zpráv  
 Můžete použít pole opakující se elementy v kontraktů zpráv dvěma způsoby.  
  
 První je použití <xref:System.ServiceModel.MessageHeaderAttribute> nebo <xref:System.ServiceModel.MessageBodyMemberAttribute> přímo na pole. V takovém případě celého pole je serializován jako jeden prvek (to znamená, že jedno záhlaví nebo jednu část textu) s více podřízenými prvky. Vezměte v úvahu třídu v následujícím příkladu.  
  
```csharp  
[MessageContract]  
public class BankingDepositLog  
{  
  [MessageHeader] public int numRecords;  
  [MessageHeader] public DepositRecord[] records;  
  [MessageHeader] public int branchID;  
}  
```  
  
 Výsledkem hlavičky SOAP je podobný následujícímu.  
  
```xml  
<BankingDepositLog>  
<numRecords>3</numRecords>  
<records>  
  <DepositRecord>Record1</DepositRecord>  
  <DepositRecord>Record2</DepositRecord>  
  <DepositRecord>Record3</DepositRecord>  
</records>  
<branchID>20643</branchID>  
</BankingDepositLog>  
```  
  
 Alternativa k tomuto je použít <xref:System.ServiceModel.MessageHeaderArrayAttribute>. V tomto případě nezávisle na sobě serializován každý prvek pole a tak pole, které každý prvek má jedno záhlaví, podobný následujícímu.  
  
```xml  
<numRecords>3</numRecords>  
<records>Record1</records>  
<records>Record2</records>  
<records>Record3</records>  
<branchID>20643</branchID>  
```  
  
 Název členu, ke kterému je výchozí název položky pole <xref:System.ServiceModel.MessageHeaderArrayAttribute> použít atributy.  
  
 <xref:System.ServiceModel.MessageHeaderArrayAttribute> Atributu inherits z <xref:System.ServiceModel.MessageHeaderAttribute>. Má stejnou sadu funkcí jako atributy mimo pole, například je možné nastavit pořadí, název a obor názvů pro pole hlavičky stejným způsobem, který jste nastavili pro jednu hlavičku. Při použití `Order` vlastnost na pole, která se vztahuje na celý pole.  
  
 Můžete použít <xref:System.ServiceModel.MessageHeaderArrayAttribute> pouze na pole, nikoli kolekce.  
  
## <a name="using-byte-arrays-in-message-contracts"></a>Pomocí polí bajtů v kontraktů zpráv  
 Bajtová pole, při použití s atributy mimo pole (<xref:System.ServiceModel.MessageBodyMemberAttribute> a <xref:System.ServiceModel.MessageHeaderAttribute>), nemají být považována jako pole, ale jako speciální primitivní typ reprezentovaný jako data v výsledného kódu XML s kódováním Base64.  
  
 Při použití pole bajtů s atributem pole <xref:System.ServiceModel.MessageHeaderArrayAttribute>, výsledek závisí na serializátoru, který je používán. S výchozí serializátor pole je vyjádřena jako jednotlivé položky pro každý bajt. Ale, když `XmlSerializer` je vybrána, (pomocí <xref:System.ServiceModel.XmlSerializerFormatAttribute> u kontraktu služby), bajtová pole jsou považovány za data ve formátu Base64, bez ohledu na to, zda pole nebo mimo pole atributy se používají.  
  
## <a name="signing-and-encrypting-parts-of-the-message"></a>Podepisování a šifrování částí zprávy  
 Kontrakt zprávy můžete určit, zda záhlaví a text zprávy by měl být digitálně podepsat a zašifrovat.  
  
 To se provádí tak, že nastavíte <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A?displayProperty=nameWithType> vlastnost <xref:System.ServiceModel.MessageHeaderAttribute> a <xref:System.ServiceModel.MessageBodyMemberAttribute> atributy. Vlastnost je výčet <xref:System.Net.Security.ProtectionLevel?displayProperty=nameWithType> zadejte a může být nastaven na <xref:System.Net.Security.ProtectionLevel.None> (žádné šifrování nebo podpis), <xref:System.Net.Security.ProtectionLevel.Sign> (digitální podpis pouze), nebo <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> (šifrování a digitálním podpisem). Výchozí hodnota je <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.  
  
 Pro fungování těchto funkcí zabezpečení musíte správně nakonfigurovat vazby a chování. Pokud používáte tyto funkce zabezpečení bez správnou konfiguraci (například pokus o přihlášení zprávu bez nutnosti zadávat svoje přihlašovací údaje), je vyvolána výjimka během ověřování.  
  
 Záhlaví zpráv úroveň ochrany je určeno jednotlivě pro každého záhlaví.  
  
 Pro zprávu částí textu aby úroveň ochrany můžete představit jako "minimální úroveň ochrany." Text má pouze jeden ochranu úroveň, bez ohledu na počet částí textu. Úroveň ochrany obsahu je určeno nejvyšší <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A> nastavení vlastnosti všechny části textu. Nicméně byste měli nastavit úroveň ochrany každá část textu skutečné ochrany minimální úroveň požadovaných.  
  
 Vezměte v úvahu třídu v následujícím příkladu kódu.  
  
```csharp  
[MessageContract]  
public class PatientRecord  
{  
   [MessageHeader(ProtectionLevel=None)] public int recordID;  
   [MessageHeader(ProtectionLevel=Sign)] public string patientName;  
   [MessageHeader(ProtectionLevel=EncryptAndSign)] public string SSN;  
   [MessageBodyMember(ProtectionLevel=None)] public string comments;  
   [MessageBodyMember(ProtectionLevel=Sign)] public string diagnosis;  
   [MessageBodyMember(ProtectionLevel=EncryptAndSign)] public string medicalHistory;  
}  
```  
  
 V tomto příkladu `recordID` záhlaví není chráněný, `patientName` je `signed`, a `SSN` je šifrovaný a podepsaný. Část alespoň jeden textu `medicalHistory`, má <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> použít, a proto je obsah celé zprávy zašifrovaná a podepsaná, i když komentáře a částí textu diagnostiku zadejte nižší úrovně ochrany.  
  
## <a name="soap-action"></a>Akce SOAP  
 SOAP a související standardy webových služeb definovat vlastnost s názvem `Action` , může být k dispozici pro všechny zprávy protokolu SOAP. Operace <xref:System.ServiceModel.OperationContractAttribute.Action%2A?displayProperty=nameWithType> a <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A?displayProperty=nameWithType> vlastnosti řídí hodnota této vlastnosti.  
  
## <a name="soap-header-attributes"></a>Atributy záhlaví SOAP  
 SOAP standard definuje následující atributy, které mohou existovat v hlavičce:  
  
-   `Actor/Role` (`Actor` v protokolu SOAP 1.1, `Role` v protokolu SOAP 1.2)  
  
-   `MustUnderstand`  
  
-   `Relay`  
  
 `Actor` Nebo `Role` Určuje atribut identifikátor URI (Uniform Resource) z uzlu, pro který je určený danou hlavičku. `MustUnderstand` Atribut určuje, zda uzel zpracování záhlaví musí pochopit. `Relay` Atribut určuje, zda záhlaví je možné předat do podřízené uzly. WCF neprovádí zpracování těchto atributů na příchozí zprávy, s výjimkou `MustUnderstand` atributu, jak je uvedeno v části "Správa verzí kontraktů zpráv" dále v tomto tématu. Však umožňuje číst a zapisovat podle potřeby, stejně jako v následujícím popis těchto atributů.  
  
 Při odesílání zprávy, nejsou ve výchozím nastavení zaznamenávány těchto atributů. Toto můžete změnit dvěma způsoby. Nejdřív, může staticky nastavíte atributy na všechny požadované hodnoty tak, že změníte <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.MessageHeaderAttribute.MustUnderstand%2A?displayProperty=nameWithType>, a <xref:System.ServiceModel.MessageHeaderAttribute.Relay%2A?displayProperty=nameWithType> vlastnosti, jak je znázorněno v následujícím příkladu kódu. (Všimněte si, že neexistuje žádné `Role` vlastnost; nastavení <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A> vysílá vlastnost `Role` atribut, pokud používáte protokol SOAP 1.2).  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader(Actor="http://auditingservice.contoso.com", MustUnderstand=true)] public bool IsAudited;  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public BankingTransactionData theData;  
}  
```  
  
 Druhý způsob, jak řídit tyto atributy se dynamicky prostřednictvím kódu. Lze toho dosáhnout obalením typ požadovaného záhlaví v <xref:System.ServiceModel.MessageHeader%601> typ (ujistěte se, abyste nezaměnili tohoto typu v obecné verzi) a s použitím typu spolu s <xref:System.ServiceModel.MessageHeaderAttribute>. Potom můžete použít vlastnosti na <xref:System.ServiceModel.MessageHeader%601> nastavení atributů protokolu SOAP, jak je znázorněno v následujícím příkladu kódu.  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public MessageHeader<bool> IsAudited;  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public BankingTransactionData theData;  
}  
// application code:  
BankingTransaction bt = new BankingTransaction();  
bt.IsAudited = new MessageHeader<bool>();  
bt.IsAudited.Content = false; // Set IsAudited header value to "false"  
bt.IsAudited.Actor="http://auditingservice.contoso.com";  
bt.IsAudited.MustUnderstand=true;  
```  
  
 Pokud používáte dynamické i statické kontrolní mechanismy, statické nastavení jsou použita jako výchozí, ale později se dá přepsat pomocí dynamické mechanismus, jak je znázorněno v následujícím kódu.  
  
```csharp  
[MessageHeader(MustUnderstand=true)] public MessageHeader<Person> documentApprover;  
// later on in the code:  
BankingTransaction bt = new BankingTransaction();  
bt.documentApprover = new MessageHeader<Person>();  
bt.documentApprover.MustUnderstand = false; // override the static default of 'true'  
```  
  
 Vytvoření opakovaně záhlaví s ovládacím prvkem dynamického atributu je povoleno, jak je znázorněno v následujícím kódu.  
  
```csharp  
[MessageHeaderArray] public MessageHeader<Person> documentApprovers[];  
```  
  
 Na straně příjmu čtení těchto atributů protokolu SOAP lze pouze v případě, <xref:System.ServiceModel.MessageHeader%601> třída se používá pro záhlaví v typu. Zkontrolujte `Actor`, `Relay`, nebo `MustUnderstand` vlastnosti s hlavičkou <xref:System.ServiceModel.MessageHeader%601> typu ke zjištění nastavení atributů na přijatou zprávu.  
  
 Pokud zprávu přijme a potom odeslány zpět, nastavení atributů protokolu SOAP, jdou pouze operace round-trip pro záhlaví <xref:System.ServiceModel.MessageHeader%601> typu.  
  
## <a name="order-of-soap-body-parts"></a>Pořadí částí textu zprávy protokolu SOAP  
 V některých případech budete muset určit pořadí částí textu. Pořadí prvků textu je abecední ve výchozím nastavení, ale mohou být řízena <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> vlastnost. Tato vlastnost má stejnou sémantiku jako <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A?displayProperty=nameWithType> vlastnost, s výjimkou chování ve scénářích dědičnosti (v kontraktů zpráv, základní typ těla členy nejsou seřazené před tělo členy odvozeného typu). Další informace najdete v tématu [pořadí datových členů](../../../../docs/framework/wcf/feature-details/data-member-order.md).  
  
 V následujícím příkladu `amount` by obvykle pocházejí nejprve vzhledem k tomu, že je první podle abecedy. Ale <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A> vlastnost vloží je do třetí pozici.  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember(Order=1)] public Account sourceAccount;  
  [MessageBodyMember(Order=2)] public Account targetAccount;  
  [MessageBodyMember(Order=3)] public int amount;  
}  
```  
  
## <a name="message-contract-versioning"></a>Správa verzí kontraktů zpráv  
 V některých případech budete muset změnit kontraktů zpráv. Novou verzi vaší aplikace může například přidat další záhlaví zprávy. Pak při odesílání z nové verze původní, systém musí zabývat dodatečné hlavičky, jakož i chybí hlavička při přechodu v opačném směru.  
  
 Pro správu verzí hlavičky platí následující pravidla:  
  
-   WCF není objekt pro chybějící záhlaví – odpovídající členů jsou ponechány na výchozích hodnotách.  
  
-   WCF rovněž ignoruje neočekávané dodatečné hlavičky. Jedinou výjimkou tohoto pravidla je, pokud má navíc záhlaví `MustUnderstand` atribut nastaven na `true` v příchozí zprávě SOAP – v takovém případě je vyvolána výjimka, protože nelze zpracovat hlavičku, která musí být srozumitelný.  
  
 Zpráva úřadů, které mají podobné pravidla správy verzí – chybí a dalších částí textu zprávy jsou ignorovány.  
  
## <a name="inheritance-considerations"></a>Důležité informace o dědičnosti  
 Typ kontraktu zprávy může dědit z jiného typu, jako základní typ také obsahuje kontrakt zprávy.  
  
 Při vytváření nebo přístup k zprávu pomocí typ kontraktu zprávy, která dědí z jiných typů kontraktu zprávy, platí následující pravidla:  
  
-   Všechny hlavičky zprávy v hierarchii dědičnosti shromažďují společně tvoří úplnou sadu záhlaví zprávy.  
  
-   Všechny části textu zprávy v hierarchii dědičnosti shromažďují společně tvoří obsah celé zprávy. Částí textu jsou řazeny podle obvyklých pravidel řazení (podle <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> vlastnost a potom abecedy), s žádný vztah k jejich místo v hierarchii dědičnosti. Pomocí dědičnosti kontraktu zprávy, pokud dojde k částí textu zprávy na více úrovních strom dědičnosti se důrazně nedoporučuje. Pokud základní třída a odvozené třídy definují záhlaví nebo část textu se stejným názvem, člen ze třídy base většinu se používá pro ukládání hodnoty horní části Hlavička nebo text.  
  
 Vezměte v úvahu třídy v následujícím příkladu kódu.  
  
```csharp  
[MessageContract]  
public class PersonRecord  
{  
  [MessageHeader(Name="ID")] public int personID;  
  [MessageBodyMember] public string patientName;  
}  
  
[MessageContract]  
public class PatientRecord : PersonRecord  
{  
  [MessageHeader(Name="ID")] public int patientID;  
  [MessageBodyMember] public string diagnosis;  
}  
```  
  
 `PatientRecord` Třída popisuje zprávy jednu hlavičku s názvem `ID`. Odpovídá záhlaví `personID` a ne `patientID` člena, protože většina základní člen je vybrán. To znamená `patientID` pole v tomto případě je zbytečné. Tělo zprávy obsahuje `diagnosis` element, za nímž následuje `patientName` element, protože, který je v abecedním pořadí. Všimněte si, že v příkladu ukazuje vzor, který se důrazně nedoporučuje: základních a odvozených zpráv kontrakty mají částí textu zprávy.  
  
## <a name="wsdl-considerations"></a>Důležité informace o WSDL  
 Při generování kontraktu webové služby WSDL (Description Language) ze služby, která používá zprávy smlouvy, je dobré si uvědomit, že ne všechny funkce kontraktu zprávy, se projeví v výsledný WSDL. Vezměte v úvahu následující body:  
  
-   WSDL nelze vyjádřit pojem pole záhlaví. Při vytváření zprávy s pole záhlaví pomocí <xref:System.ServiceModel.MessageHeaderArrayAttribute>, pouze jedno záhlaví místo pole odráží výsledný WSDL.  
  
-   Výsledné dokument WSDL nemusí odrážet některé informace úroveň ochrany.  
  
-   Typ zprávy generované ve schématu WSDL má stejný název jako název třídy typu kontraktu zprávy.  
  
-   Při použití stejné zprávy smlouvy ve více operací, více typy zpráv jsou generovány v dokumentu WSDL. Přidáním čísel "2", "3" a tak dále, pro následující účely, jsou provedeny jedinečné názvy. Když importujete zpět WSDL, více typy kontraktů zpráv jsou vytvořeny a jsou stejné s výjimkou jejich názvy.  
  
## <a name="soap-encoding-considerations"></a>Důležité informace o kódování SOAP  
 WCF umožňuje použít starší verzi protokolu SOAP kódování styl XML, ale jeho použití nedoporučuje. Při použití tohoto stylu (nastavením `Use` vlastnost `Encoded` na <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType> u kontraktu služby), platí následující další aspekty:  
  
-   Záhlaví zpráv nejsou podporovány. To znamená, že atribut <xref:System.ServiceModel.MessageHeaderAttribute> a atribut pole <xref:System.ServiceModel.MessageHeaderArrayAttribute> nejsou kompatibilní s kódováním SOAP.  
  
-   Pokud kontrakt zprávy není zabalena, to znamená, pokud vlastnost <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> je nastavena na `false`, kontrakt zprávy může mít část textu pouze jeden.  
  
-   Název prvku obálky pro kontrakt zprávy požadavku musí odpovídat názvu operace. Použití `WrapperName` kontraktu zprávy pro tuto vlastnost.  
  
-   Název prvku obálky pro kontrakt zprávy odpovědi musí být stejný jako název operace příponou podle "Odpověď". Použití <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> kontraktu zprávy pro tuto vlastnost.  
  
-   Kódování SOAP zachová odkazy na objekty. Zvažte například následující kód.  
  
    ```csharp  
    [MessageContract(WrapperName="updateChangeRecord")]  
    public class ChangeRecordRequest  
    {  
      [MessageBodyMember] Person changedBy;  
      [MessageBodyMember] Person changedFrom;  
      [MessageBodyMember] Person changedTo;  
    }  
  
    [MessageContract(WrapperName="updateChangeRecordResponse")]  
    public class ChangeRecordResponse  
    {  
      [MessageBodyMember] Person changedBy;  
      [MessageBodyMember] Person changedFrom;  
      [MessageBodyMember] Person changedTo;  
    }  
  
    // application code:  
    ChangeRecordRequest cr = new ChangeRecordRequest();  
    Person p = new Person("John Doe");  
    cr.changedBy=p;  
    cr.changedFrom=p;  
    cr.changedTo=p;  
    ```  
  
 Po serializaci zprávy s kódováním SOAP `changedFrom` a `changedTo` neobsahují své vlastní kopie `p`, ale místo toho přejděte na kopírování uvnitř `changedBy` elementu.  
  
## <a name="performance-considerations"></a>Faktory ovlivňující výkon  
 Každý záhlaví zprávy a část textu zprávy serializován nezávisle na ostatních. Proto stejné obory názvů mohou být deklarovány opakujte pro každou část textu a záhlaví. Kvůli zvýšení výkonu, zejména z hlediska velikosti zpráv na lince, konsolidovat více záhlaví a částí textu do jedné části Hlavička nebo text. Například místo následující kód:  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public Account sourceAccount;  
  [MessageBodyMember] public Account targetAccount;  
  [MessageBodyMember] public int amount;  
}  
```  
  
 Pomocí tohoto kódu.  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public OperationDetails details;  
}  
  
[DataContract]  
public class OperationDetails  
{  
  [DataMember] public Account sourceAccount;  
  [DataMember] public Account targetAccount;  
  [DataMember] public int amount;  
}  
```  
  
### <a name="event-based-asynchronous-and-message-contracts"></a>Založený na událostech asynchronní a kontrakty zprávy  
 Pokyny návrhu pro asynchronní model založený na událostech stát, že pokud se vrátí více než jednu hodnotu, se vrátí jednu hodnotu jako `Result` vlastnosti a ostatní jsou vrácena jako vlastnosti na <xref:System.EventArgs> objektu. Jeden výsledek tohoto je, že pokud klient naimportuje metadata pomocí možnosti založené na událostech asynchronního příkazu a operace vrátí více než jednu hodnotu, výchozí <xref:System.EventArgs> objekt vrátí jednu hodnotu jako `Result` vlastnost a zbývající jsou vlastnosti <xref:System.EventArgs> objektu.  
  
 Pokud chcete přijímat zprávy objektu jako `Result` vlastnost a vrácené hodnoty jako vlastnosti objektu, použijte `/messageContract` možnost příkazu. Tím se vygeneruje podpis, který vrací zprávy s odpovědí jako `Result` vlastnost <xref:System.EventArgs> objektu. Všechny interní vrácené hodnoty jsou pak vlastnosti objektu zprávu odpovědi.  
  
## <a name="see-also"></a>Viz také:
- [Použití kontraktů dat](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [Navrhování a implementace služeb](../../../../docs/framework/wcf/designing-and-implementing-services.md)
