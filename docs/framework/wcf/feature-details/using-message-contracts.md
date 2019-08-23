---
title: Použití kontraktů zpráv
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message contracts [WCF]
ms.assetid: 1e19c64a-ae84-4c2f-9155-91c54a77c249
ms.openlocfilehash: 18d0ea97f1de40044d40fa85c9792c809fb73346
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959885"
---
# <a name="using-message-contracts"></a>Použití kontraktů zpráv
Obvykle při sestavování aplikací Windows Communication Foundation (WCF), vývojáři účtují téměř pozor na datové struktury a problémy serializace a nepotřebují se k tomu zabývat strukturou zpráv, ve kterých jsou data přenášena. Pro tyto aplikace je vytvoření kontraktů dat pro parametry nebo návratové hodnoty jednoduché. (Další informace najdete v tématu [určení přenos dat v kontraktech služby](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).)  
  
 Někdy však kompletní řízení nad strukturou zprávy SOAP je stejně důležité jako řízení obsahu. To platí hlavně v případě, že je vzájemná funkční spolupráce, nebo pro konkrétní řízení problémů zabezpečení na úrovni zprávy nebo části zprávy. V těchto případech můžete vytvořit *kontrakt zprávy* , který vám umožní určit strukturu přesné požadované zprávy SOAP.  
  
 Toto téma popisuje, jak používat různé atributy kontraktů zpráv k vytvoření konkrétního kontraktu zprávy pro vaši operaci.  
  
## <a name="using-message-contracts-in-operations"></a>Použití kontraktů zpráv v operacích  
 Služba WCF podporuje operace modelované buď ve *stylu vzdáleného volání procedur (RPC)* , nebo ve *stylu zasílání zpráv*. Ve stylu operace RPC můžete použít libovolný serializovatelný typ a máte přístup k funkcím, které jsou k dispozici pro místní volání, jako je například více parametrů a `ref` `out` parametrů. V tomto stylu je zvolena forma serializace ovládací prvky struktury dat v podkladových zprávách a modul runtime WCF vytvoří zprávy pro podporu operace. To umožňuje vývojářům, kteří nejsou obeznámeni se zprávami SOAP a SOAP, rychle a snadno vytvářet a používat aplikace služby.  
  
 Následující příklad kódu ukazuje operaci služby modelované ve stylu RPC.  
  
```csharp  
[OperationContract]  
public BankingTransactionResponse PostBankingTransaction(BankingTransaction bt);  
```  
  
 Obvykle je kontrakt dat dostačující k definování schématu pro zprávy. Například v předchozím příkladu je dostačující pro většinu aplikací, pokud `BankingTransaction` a `BankingTransactionResponse` mají kontrakty dat k definování obsahu podkladových zpráv SOAP. Další informace o kontraktech dat najdete v tématu [Použití kontraktů dat](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
 Občas ale je nutné přesně určit, jak se struktura zprávy protokolu SOAP přenáší přes síťový kabel. Nejběžnější scénář pro toto je vložení vlastních hlaviček SOAP. Dalším běžným scénářem je definování vlastností zabezpečení pro záhlaví a text zprávy, to znamená, abyste se rozhodli, jestli jsou tyto prvky digitálně podepsané a šifrované. Nakonec některé zásobníky SOAP jiných výrobců vyžadují, aby zprávy byly v konkrétním formátu. Tento ovládací prvek poskytuje operace stylu zasílání zpráv.  
  
 Operace ve stylu zasílání zpráv má maximálně jeden parametr a jednu návratovou hodnotu, kde jsou oba typy zprávy. To znamená, že jsou serializovány přímo do zadané struktury zpráv SOAP. Může to být libovolný typ označený <xref:System.ServiceModel.MessageContractAttribute> jako <xref:System.ServiceModel.Channels.Message> typ nebo. Následující příklad kódu ukazuje operaci podobnou předchozímu stylu RCP, ale používá styl zasílání zpráv.  
  
 Například pokud `BankingTransaction` a `BankingTransactionResponse` jsou oba typy, které jsou kontrakty zpráv, je kód v následujících operacích platný.  
  
```csharp  
[OperationContract]  
BankingTransactionResponse Process(BankingTransaction bt);  
[OperationContract]  
void Store(BankingTransaction bt);  
[OperationContract]  
BankingTransactionResponse GetResponse();  
```  
  
 Následující kód však není platný.  
  
```csharp  
[OperationContract]  
bool Validate(BankingTransaction bt);  
// Invalid, the return type is not a message contract.  
[OperationContract]  
void Reconcile(BankingTransaction bt1, BankingTransaction bt2);  
// Invalid, there is more than one parameter.  
```  
  
 Výjimka je vyvolána pro všechny operace, které zahrnují typ kontraktu zprávy a které nenásledují po jednom z platných vzorů. Samozřejmě operací, které nezahrnují typy kontraktů zpráv, se tyto omezení nevztahují.  
  
 Pokud typ obsahuje kontrakt zprávy i kontrakt dat, je při použití daného typu v rámci operace zvážen pouze jeho kontrakt zprávy.  
  
## <a name="defining-message-contracts"></a>Definování kontraktů zpráv  
 Chcete-li definovat kontrakt zprávy pro typ (tj. pro definování mapování mezi typem a obálkou protokolu SOAP), použijte <xref:System.ServiceModel.MessageContractAttribute> pro typ. Pak použijte <xref:System.ServiceModel.MessageHeaderAttribute> u těch členů typu, který chcete vytvořit v hlavičkách SOAP, a <xref:System.ServiceModel.MessageBodyMemberAttribute> použijte u těch členů, které chcete vytvořit do částí těla protokolu SOAP zprávy.  
  
 Následující kód poskytuje příklad použití kontraktu zprávy.  
  
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
  
 Při použití tohoto typu jako parametru operace je vygenerována následující obálka protokolu SOAP:  
  
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
  
 Všimněte si `operation` , `transactionDate` že a jak se zobrazí jako hlavičky SOAP a tělo SOAP se skládá `BankingTransaction` z `sourceAccount`prvku`targetAccount`obálky obsahujícího, a `amount`.  
  
 Můžete použít <xref:System.ServiceModel.MessageHeaderAttribute> a <xref:System.ServiceModel.MessageBodyMemberAttribute> pro všechna pole, vlastnosti a události bez ohledu na to, zda jsou veřejné, privátní, chráněné nebo interní.  
  
 <xref:System.ServiceModel.MessageContractAttribute> Umožňuje určit atributy wrapper a WrapperNamespace, které řídí název prvku obálky v těle zprávy protokolu SOAP. Ve výchozím nastavení se pro obálku používá název typu kontraktu zprávy a obor názvů, ve kterém je kontrakt zprávy definovaný `http://tempuri.org/` , se používá jako výchozí obor názvů.  
  
> [!NOTE]
> <xref:System.Runtime.Serialization.KnownTypeAttribute>atributy se v kontraktech zpráv ignorují. <xref:System.Runtime.Serialization.KnownTypeAttribute> Pokud se vyžaduje, umístěte ho na operaci, která používá daný kontrakt zprávy.  
  
## <a name="controlling-header-and-body-part-names-and-namespaces"></a>Řízení záhlaví a názvů částí těla a oborů názvů  
 V prohlášení protokolu SOAP u kontraktu zprávy se každé záhlaví a část těla mapuje na element XML, který má název a obor názvů.  
  
 Ve výchozím nastavení je obor názvů stejný jako obor názvů kontraktu služby, ve kterém se zpráva účastní, a název je určen názvem člena, na který <xref:System.ServiceModel.MessageHeaderAttribute> <xref:System.ServiceModel.MessageBodyMemberAttribute> jsou atributy aplikovány.  
  
 Tato výchozí nastavení můžete <xref:System.ServiceModel.MessageContractMemberAttribute.Name%2A?displayProperty=nameWithType> změnit pomocí manipulace s a <xref:System.ServiceModel.MessageContractMemberAttribute.Namespace%2A?displayProperty=nameWithType> (v nadřazené třídě <xref:System.ServiceModel.MessageHeaderAttribute> atributů a <xref:System.ServiceModel.MessageBodyMemberAttribute> ).  
  
 Zvažte třídu v následujícím příkladu kódu.  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageHeader(Namespace="http://schemas.contoso.com/auditing/2005")] public bool IsAudited;  
  [MessageBodyMember(Name="transactionData")] public BankingTransactionData theData;  
}  
```  
  
 V tomto příkladu `IsAudited` je hlavička v oboru názvů zadaném v kódu a část těla, která `theData` představuje člen, je reprezentována elementem XML s názvem `transactionData`. Následující příklad ukazuje generovaný kód XML pro tento kontrakt zprávy.  
  
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
  
## <a name="controlling-whether-the-soap-body-parts-are-wrapped"></a>Řízení, zda jsou části těla protokolu SOAP zabaleny  
 Ve výchozím nastavení jsou části těla protokolu SOAP serializovány uvnitř zabaleného prvku. Například následující kód ukazuje `HelloGreetingMessage` Obálkový prvek vygenerovaný z názvu <xref:System.ServiceModel.MessageContractAttribute> typu v kontraktu zprávy pro `HelloGreetingMessage` zprávu.  
  
[!code-csharp[MessageHeaderAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/messageheaderattribute/cs/services.cs#3)]
[!code-vb[MessageHeaderAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/messageheaderattribute/vb/services.vb#3)]  
  
 Chcete-li potlačit prvek obálky, <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> nastavte vlastnost `false`na hodnotu. Chcete-li řídit název a obor názvů prvku obálky, použijte <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> vlastnosti a. <xref:System.ServiceModel.MessageContractAttribute.WrapperNamespace%2A>  
  
> [!NOTE]
> Pokud máte více než jednu část těla zprávy ve zprávách, které nejsou zabaleny, není kompatibilní s profilem WS-I Basic Profile 1,1 a při navrhování nových kontraktů zpráv se nedoporučuje. Může být ale nutné mít více než jeden nezabalený tělo zprávy v některých specifických scénářích interoperability. Pokud budete přenášet více než jednu část dat v těle zprávy, doporučuje se použít výchozí (zabalený) režim. Používání více než jednoho záhlaví zprávy v nezabalených zprávách je zcela přijatelné.  
  
## <a name="using-custom-types-inside-message-contracts"></a>Použití vlastních typů uvnitř kontraktů zpráv  
 Každá jednotlivá Hlavička zprávy a část těla zprávy je serializovaná (převedená do XML) s použitím vybraného serializačního modulu pro kontrakt služby, kde se zpráva používá. Výchozí Serializační modul, `XmlFormatter`, může zpracovat jakýkoli typ, který má kontrakt dat, buď explicitně (pomocí <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType>), nebo implicitně (pomocí <xref:System.SerializableAttribute?displayProperty=nameWithType>primitivního typu, který má a tak dále). Další informace najdete v tématu [Použití kontraktů dat](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
 V předchozím příkladu `Operation` musí mít typy a `BankingTransactionData` typ kontraktu dat, který `transactionDate` je serializovatelný, protože <xref:System.DateTime> je primitivní (a má tedy implicitní kontrakt dat).  
  
 Je však možné přepnout na jiný Serializační modul, `XmlSerializer`. Pokud tento přepínač provedete, měli byste zajistit, aby všechny typy používané pro záhlaví zpráv a části těla textu byly serializovatelný pomocí `XmlSerializer`.  
  
## <a name="using-arrays-inside-message-contracts"></a>Použití polí uvnitř kontraktů zpráv  
 Pole opakujících se prvků v kontraktech zpráv můžete použít dvěma způsoby.  
  
 První je použití <xref:System.ServiceModel.MessageHeaderAttribute> <xref:System.ServiceModel.MessageBodyMemberAttribute> nebo přímo v poli. V tomto případě je celé pole serializováno jako jeden prvek (tj. jedna hlavička nebo jedna část těla) s více podřízenými prvky. V následujícím příkladu zvažte třídu.  
  
```csharp  
[MessageContract]  
public class BankingDepositLog  
{  
  [MessageHeader] public int numRecords;  
  [MessageHeader] public DepositRecord[] records;  
  [MessageHeader] public int branchID;  
}  
```  
  
 Výsledkem je, že hlavičky SOAP jsou podobné následujícímu.  
  
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
  
 Alternativou k tomu je použití <xref:System.ServiceModel.MessageHeaderArrayAttribute>. V tomto případě jsou jednotlivé prvky pole serializovány nezávisle, takže každý prvek pole má jednu hlavičku, podobně jako následující.  
  
```xml  
<numRecords>3</numRecords>  
<records>Record1</records>  
<records>Record2</records>  
<records>Record3</records>  
<branchID>20643</branchID>  
```  
  
 Výchozí název pro položky pole je název člena, na který <xref:System.ServiceModel.MessageHeaderArrayAttribute> jsou atributy aplikovány.  
  
 <xref:System.ServiceModel.MessageHeaderArrayAttribute> Atribut dědí <xref:System.ServiceModel.MessageHeaderAttribute>z. Má stejnou sadu funkcí jako atributy mimo pole, například je možné nastavit pořadí, název a obor názvů pro pole hlaviček stejným způsobem jako pro jednu hlavičku. Použijete-li vlastnost v poli, platí pro celé pole. `Order`  
  
 Můžete použít <xref:System.ServiceModel.MessageHeaderArrayAttribute> jenom pro pole, ne pro kolekce.  
  
## <a name="using-byte-arrays-in-message-contracts"></a>Použití polí bajtů v kontraktech zpráv  
 Pole bajtů, pokud se používají s atributy mimo pole (<xref:System.ServiceModel.MessageBodyMemberAttribute> a <xref:System.ServiceModel.MessageHeaderAttribute>), nejsou považována za pole, ale jako speciální primitivní typ reprezentovaný ve výsledném souboru XML jako data zakódovaná ve formátu base64.  
  
 Použijete-li pole bajtů s atributem <xref:System.ServiceModel.MessageHeaderArrayAttribute>Array, výsledky budou záviset na použitém serializátoru. U výchozího serializátoru je pole vyjádřeno jako jednotlivé položky pro každý bajt. Pokud `XmlSerializer` je však vybrána možnost ( <xref:System.ServiceModel.XmlSerializerFormatAttribute> pomocí kontraktu služby), pole bajtů jsou považována za data typu Base64 bez ohledu na to, zda jsou použity atributy Array a Array.  
  
## <a name="signing-and-encrypting-parts-of-the-message"></a>Podepisování a šifrování částí zprávy  
 Kontrakt zprávy může označovat, zda mají být záhlaví a/nebo text zprávy digitálně podepsány a zašifrovány.  
  
 To se provádí nastavením <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A?displayProperty=nameWithType> vlastnosti <xref:System.ServiceModel.MessageHeaderAttribute> v atributech a <xref:System.ServiceModel.MessageBodyMemberAttribute> . Vlastnost je výčet <xref:System.Net.Security.ProtectionLevel?displayProperty=nameWithType> typu a může být nastaven na <xref:System.Net.Security.ProtectionLevel.None> (bez šifrování, podpis), <xref:System.Net.Security.ProtectionLevel.Sign> (pouze digitální podpis), nebo <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> (šifrování i digitální podpis). Výchozí hodnota je <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.  
  
 Aby tyto funkce zabezpečení fungovaly, musíte správně nakonfigurovat vazbu a chování. Použijete-li tyto funkce zabezpečení bez správné konfigurace (například při pokusu o podepsání zprávy bez zadání přihlašovacích údajů), je vyvolána výjimka v době ověřování.  
  
 Pro záhlaví zpráv je úroveň ochrany určena individuálně pro každé záhlaví.  
  
 V části těla zprávy se úroveň ochrany dá představit jako minimální úroveň ochrany. Tělo má pouze jednu úroveň ochrany bez ohledu na počet částí těla. Úroveň ochrany těla je určena nastavením nejvyšší <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A> vlastnosti všech částí těla. Měli byste ale nastavit úroveň ochrany každé části těla na skutečnou minimální požadovanou úroveň ochrany.  
  
 Zvažte třídu v následujícím příkladu kódu.  
  
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
  
 V tomto příkladu `recordID` není hlavička chráněná, `patientName` je `signed`a `SSN` je šifrovaná a podepsaná. Alespoň jedna část těla, `medicalHistory`, která <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> se používá, a proto je celý text zprávy zašifrovaný a podepsaný, i když části těla komentářů a diagnostiky určují nižší úrovně ochrany.  
  
## <a name="soap-action"></a>Akce SOAP  
 Standardy SOAP a související webové služby definují vlastnost s názvem `Action` , která může být k dispozici pro každou odeslanou zprávu SOAP. <xref:System.ServiceModel.OperationContractAttribute.Action%2A?displayProperty=nameWithType> Vlastnost a <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A?displayProperty=nameWithType> vlastnosti určují hodnotu této vlastnosti.  
  
## <a name="soap-header-attributes"></a>Atributy záhlaví SOAP  
 Standard SOAP definuje následující atributy, které mohou existovat v záhlaví:  
  
- `Actor/Role`(`Actor` v SOAP 1,1, `Role` v SOAP 1,2)  
  
- `MustUnderstand`  
  
- `Relay`  
  
 Atribut `Actor` OR`Role` Určuje identifikátor URI (Uniform Resource Identifier) uzlu, pro který je daná hlavička určena. `MustUnderstand` Atribut určuje, zda musí uzel zpracovat hlavičku. `Relay` Atribut určuje, zda má být záhlaví přeneseno do podřízených uzlů. Technologie WCF neprovádí žádné zpracování těchto atributů u příchozích zpráv s výjimkou atributu, `MustUnderstand` jak je uvedeno v části Správa verzí kontraktu zpráv dále v tomto tématu. To však umožňuje číst a zapisovat tyto atributy podle potřeby, jako v následujícím popisu.  
  
 Při odesílání zprávy nejsou ve výchozím nastavení vygenerovány tyto atributy. Můžete to změnit dvěma způsoby. Nejprve můžete staticky nastavit atributy na požadované hodnoty změnou <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A?displayProperty=nameWithType>vlastností, <xref:System.ServiceModel.MessageHeaderAttribute.MustUnderstand%2A?displayProperty=nameWithType>a <xref:System.ServiceModel.MessageHeaderAttribute.Relay%2A?displayProperty=nameWithType> , jak je znázorněno v následujícím příkladu kódu. (Všimněte si, že vlastnost `Role` není k dispozici <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A> ; nastavení vlastnosti emituje `Role` atribut, pokud používáte SOAP 1,2).  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader(Actor="http://auditingservice.contoso.com", MustUnderstand=true)] public bool IsAudited;  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public BankingTransactionData theData;  
}  
```  
  
 Druhý způsob, jak tyto atributy řídit, je prostřednictvím kódu dynamicky. Toho lze dosáhnout zabalením požadovaného typu hlavičky v <xref:System.ServiceModel.MessageHeader%601> typu (Nezapomeňte, že nepleťete tento typ s neobecnou verzí) a pomocí typu společně <xref:System.ServiceModel.MessageHeaderAttribute>s. Pak můžete použít vlastnosti v <xref:System.ServiceModel.MessageHeader%601> pro nastavení atributů SOAP, jak je znázorněno v následujícím příkladu kódu.  
  
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
  
 Použijete-li jak dynamický, tak i statický mechanismus řízení, bude statické nastavení použito jako výchozí, ale lze jej později přepsat pomocí dynamického mechanismu, jak je znázorněno v následujícím kódu.  
  
```csharp  
[MessageHeader(MustUnderstand=true)] public MessageHeader<Person> documentApprover;  
// later on in the code:  
BankingTransaction bt = new BankingTransaction();  
bt.documentApprover = new MessageHeader<Person>();  
bt.documentApprover.MustUnderstand = false; // override the static default of 'true'  
```  
  
 Vytváření opakujících se hlaviček s dynamickým ovládacím prvkem atributu je povoleno, jak je znázorněno v následujícím kódu.  
  
```csharp  
[MessageHeaderArray] public MessageHeader<Person> documentApprovers[];  
```  
  
 Na straně příjmu lze číst tyto atributy SOAP pouze v případě, že <xref:System.ServiceModel.MessageHeader%601> je třída použita pro hlavičku v typu. Prohlédněte si `Relay`vlastnosti `MustUnderstand` , nebo záhlaví <xref:System.ServiceModel.MessageHeader%601> typu, abyste zjistili nastavení atributu v přijaté zprávě. `Actor`  
  
 Když se přijme zpráva a pak se pošle zpátky, nastavení atributu SOAP se v hlavičce tohoto <xref:System.ServiceModel.MessageHeader%601> typu dostanou jenom na zpáteční cestu.  
  
## <a name="order-of-soap-body-parts"></a>Pořadí částí těla protokolu SOAP  
 V některých případech může být nutné řídit pořadí částí těla. Pořadí prvků textu je ve výchozím nastavení abecední, ale lze je ovládat pomocí <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> vlastnosti. Tato vlastnost má stejnou sémantiku jako <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A?displayProperty=nameWithType> vlastnost, s výjimkou chování ve scénářích dědičnosti (v kontraktech zprávy, členy základního typu základního typu nejsou řazeny před členy těla odvozeného typu). Další informace najdete v tématu [pořadí datových členů](../../../../docs/framework/wcf/feature-details/data-member-order.md).  
  
 V následujícím příkladu by se `amount` normálně nacházela jako první, protože je první abecedně. <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A> Vlastnost však vloží do třetí pozice.  
  
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
 V některých případech může být nutné změnit kontrakty zpráv. Například nová verze vaší aplikace může do zprávy přidat další záhlaví. Když pak při posílání z nové verze do starého, systém musí při přechodu na druhý směr zabývat se další hlavičkou a chybějící hlavičkou.  
  
 Pro hlavičky verzí platí následující pravidla:  
  
- WCF neobjektí do chybějících hlaviček – odpovídající členové jsou ponecháni na jejich výchozích hodnotách.  
  
- WCF také ignoruje neočekávané nadbytečné hlavičky. Jedinou výjimkou z tohoto pravidla je, že pokud má `MustUnderstand` navíc záhlaví vlastnost nastavenou na `true` příchozí zprávu SOAP – v tomto případě je vyvolána výjimka, protože záhlaví, které je nutné chápat, nelze zpracovat.  
  
 Tělo zprávy mají podobná pravidla správy verzí – chybějící a další části těla zprávy jsou ignorovány.  
  
## <a name="inheritance-considerations"></a>Otázky dědičnosti  
 Typ kontraktu zprávy může dědit z jiného typu, pokud základní typ má také kontrakt zprávy.  
  
 Při vytváření nebo přístupu ke zprávě pomocí typu kontraktu zprávy, který dědí z jiných typů kontraktů zpráv, platí následující pravidla:  
  
- Všechna záhlaví zpráv v hierarchii dědičnosti jsou shromažďována dohromady, aby bylo možné vytvořit úplnou sadu hlaviček pro zprávu.  
  
- Všechny části těla zprávy v hierarchii dědičnosti jsou shromažďovány dohromady, aby bylo možné vytvořit úplný text zprávy. Části těla jsou seřazené podle obvyklých pravidel řazení (podle <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> vlastnosti a pak podle abecedy), a to bez relevance na jejich místě v hierarchii dědičnosti. Použití dědičnosti kontraktu zprávy, kde se části těla zprávy vyskytují na více úrovních stromu dědičnosti, se důrazně nedoporučuje. Pokud základní třída a odvozená třída definuje záhlaví nebo část těla se stejným názvem, člen z třídy Base-nejvíc se použije k uložení hodnoty této hlavičky nebo části těla.  
  
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
  
 Třída popisuje zprávu s názvem `ID`s jednou hlavičkou. `PatientRecord` Hlavička odpovídá `personID` `patientID` členu a nikoli členovi, protože je vybrán člen nejvíce Base. Proto je pole v tomto případě nepoužitelné. `patientID` Tělo zprávy obsahuje `diagnosis` element následovaný `patientName` elementem, protože to je abecední pořadí. Všimněte si, že příklad ukazuje vzor, který se důrazně nedoporučuje: základem i odvozených kontraktů zpráv jsou části těla zprávy.  
  
## <a name="wsdl-considerations"></a>WSDL – požadavky  
 Při generování kontraktu jazyka WSDL (Web Services Description Language) ze služby, která používá kontrakty zpráv, je důležité si uvědomit, že ne všechny funkce kontraktu zprávy se odrazí ve výsledném WSDL. Vezměte v úvahu následující body:  
  
- WSDL nemůže vyjádřit koncept pole hlaviček. Při vytváření zpráv s polem hlaviček pomocí <xref:System.ServiceModel.MessageHeaderArrayAttribute>, výsledné WSDL odráží pouze jedno záhlaví místo pole.  
  
- Výsledný dokument WSDL nemusí odrážet některé informace na úrovni ochrany.  
  
- Typ zprávy generovaný v jazyce WSDL má stejný název jako název třídy typu kontraktu zprávy.  
  
- Při použití stejné kontraktu zprávy ve více operacích se v dokumentu WSDL generuje více typů zpráv. Názvy jsou jedinečné přidáním čísel "2", "3" atd. "pro následné použití. Při importu zpět WSDL se vytvoří více typů kontraktů zpráv a jsou identické, s výjimkou jejich názvů.  
  
## <a name="soap-encoding-considerations"></a>Požadavky na kódování SOAP  
 WCF vám umožňuje používat starší styly kódování protokolu SOAP XML, ale jeho použití se nedoporučuje. Při použití tohoto stylu ( `Use` nastavením vlastnosti na `Encoded` hodnotu v případě <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType> použití pro kontrakt služby) platí následující další požadavky:  
  
- Hlavičky zpráv nejsou podporovány. To znamená, že atribut <xref:System.ServiceModel.MessageHeaderAttribute> a atribut <xref:System.ServiceModel.MessageHeaderArrayAttribute> Array jsou nekompatibilní s kódováním SOAP.  
  
- Pokud není kontrakt zprávy zabalený, to znamená, že pokud je vlastnost <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> nastavená na `false`hodnotu, kontrakt zprávy může mít jenom jednu část těla.  
  
- Název prvku obálky pro kontrakt zprávy požadavku musí odpovídat názvu operace. Pro tuto zprávu použijte vlastnostkontraktuzprávy.`WrapperName`  
  
- Název prvku obálky pro kontrakt zprávy odpovědi musí být stejný jako název operace s příponou Response. Pro tuto zprávu použijte vlastnostkontraktuzprávy.<xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A>  
  
- Kódování SOAP zachovává odkazy na objekty. Zvažte například následující kód.  
  
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
  
 Po `changedFrom` serializaci zprávy pomocí kódování SOAP a `changedTo` `p`neobsahují své vlastní kopie, `changedBy` ale místo toho, aby odkazovala na kopii uvnitř elementu.  
  
## <a name="performance-considerations"></a>Faktory ovlivňující výkon  
 Každé záhlaví zprávy a část těla zprávy jsou serializovány nezávisle na ostatních. Proto je možné stejné obory názvů deklarovat znovu pro každou hlavičku a část těla. Chcete-li zvýšit výkon, zejména v souvislosti s velikostí zprávy na lince, konsolidovat více částí záhlaví a částí těla do jedné hlavičky nebo části těla. Například namísto následujícího kódu:  
  
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
  
 Použijte tento kód.  
  
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
  
### <a name="event-based-asynchronous-and-message-contracts"></a>Asynchronní události a kontrakty zpráv založené na událostech  
 Pokyny pro návrh pro stav asynchronního modelu založeného na událostech, pokud je vrácena více než jedna hodnota, jako `Result` vlastnost se vrátí jedna hodnota a ostatní jsou vráceny jako vlastnosti <xref:System.EventArgs> objektu. Jedním z těchto výsledků je, že pokud klient Importuje metadata pomocí parametrů asynchronního příkazu založeného na událostech a operace vrátí více než jednu hodnotu, výchozí <xref:System.EventArgs> objekt vrátí jednu hodnotu `Result` jako vlastnost a zbytek je <xref:System.EventArgs> vlastnosti objektu  
  
 Pokud chcete jako `Result` vlastnost přijmout objekt zprávy a vracet hodnoty jako vlastnosti tohoto objektu, `/messageContract` použijte možnost Command. Tím se vygeneruje podpis, který vrátí zprávu odpovědi jako `Result` vlastnost <xref:System.EventArgs> objektu. Všechny interní návratové hodnoty jsou potom vlastnostmi objektu zprávy odpovědi.  
  
## <a name="see-also"></a>Viz také:

- [Použití kontraktů dat](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [Navrhování a implementace služeb](../../../../docs/framework/wcf/designing-and-implementing-services.md)
