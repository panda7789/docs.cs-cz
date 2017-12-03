---
title: "Použití kontraktů zpráv"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: message contracts [WCF]
ms.assetid: 1e19c64a-ae84-4c2f-9155-91c54a77c249
caps.latest.revision: "46"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 14020e62e936ae6a9acad25c6c24d937feb150af
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="using-message-contracts"></a>Použití kontraktů zpráv
Obvykle při sestavování [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplikací vývojáři zaměřit se na datové struktury a serializace problémy a nemusíte sami se týkají se strukturou zpráv, ve kterých se přenášejí data. Pro tyto aplikace je jednoduchá vytváření kontrakty dat pro parametry nebo návratové hodnoty. ([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Zadání přenos dat v kontraktech služby](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).)  
  
 Někdy úplnou kontrolu nad strukturou zprávu protokolu SOAP se ale stejně důležité jako kontrolu nad jeho obsah. To platí hlavně při interoperability je důležité, nebo přímo řídit zabezpečení problémy na úrovni zprávě, nebo část zprávy. V těchto případech můžete vytvořit *kontrakt zprávy* , můžete určit strukturu vyžaduje přesné protokolu SOAP zprávy.  
  
 Toto téma popisuje postup vytvoření kontraktu zprávy specifické pro vaši operaci pomocí různých atributů kontrakt zprávy.  
  
## <a name="using-message-contracts-in-operations"></a>Použití kontraktů zpráv v operacích  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]podporuje operace vymodelován buď *vzdálených volání (procedur RPC) styl* nebo *zasílání zpráv styl*. V operaci stylu RPC, můžete použít jakýkoli serializovatelný typ, a máte přístup k funkcím, které jsou k dispozici pro místní volání, jako například několik parametrů a `ref` a `out` parametry. V tomto stylu forma serializace vybrali řídí strukturu dat v podkladové zprávy a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] runtime vytvoří zprávy pro podporu operaci. Díky tomu mohou vývojáři, kteří se s protokolu SOAP a SOAP zprávy a pokuste se rychle a snadno vytvořit a používat aplikace služby.  
  
 Následující příklad kódu ukazuje operace služby modelován na styl RPC.  
  
```csharp  
[OperationContract]  
public BankingTransactionResponse PostBankingTransaction(BankingTransaction bt);  
```  
  
 Za normálních okolností kontraktu dat stačí definovat schéma pro zprávy. Například v předchozím příkladu je dostatečné pro většinu aplikací Pokud `BankingTransaction` a `BankingTransactionResponse` mít kontrakty dat zadat obsah základní protokolu SOAP zprávy. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]kontrakty dat najdete v části [pomocí kontrakty dat](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
 Ale někdy je nezbytné přesně řídit, jak strukturu zprávu SOAP odeslány prostřednictvím sítě. Nejběžnější scénáře je vkládání vlastní hlavičky SOAP. Další z typických možností je definovat vlastnosti zabezpečení pro záhlaví zprávy a text, který je, a rozhodnout, zda tyto prvky jsou digitálně podepsat a zašifrovat. Nakonec vyžadují zásobníky některých třetích stran protokolu SOAP zprávy se v určitém formátu. Zasílání zpráv ve stylu operations zadejte tento ovládací prvek.  
  
 Zasílání zpráv ve stylu operace obsahuje maximálně jeden parametr a jeden návratovou hodnotu kde oba typy jsou typy zpráv; To znamená že serializovat přímo do zadané struktury zprávu protokolu SOAP. To může být jakéhokoli typu označené jako <xref:System.ServiceModel.MessageContractAttribute> nebo <xref:System.ServiceModel.Channels.Message> typu. Následující příklad kódu ukazuje operace podobná předchozí RCP stylu, ale styl zasílání zpráv, který používá.  
  
 Například pokud `BankingTransaction` a `BankingTransactionResponse` se oba typy, které jsou kontrakty zpráv, pak kód v následující operace je platná.  
  
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
  
 Pro žádnou operaci, která zahrnuje typ kontrakt zprávy a není, použijte jednu z platných vzorů je vyvolána výjimka. Tato omezení operací, které nezahrnují typy kontraktů zpráv samozřejmě se nevztahuje.  
  
 Pokud typ kontrakt zprávy a kontraktu dat, jenom jeho kontrakt zprávy považuje, pokud typ se používá v operaci.  
  
## <a name="defining-message-contracts"></a>Definování kontraktů zpráv  
 Chcete-li definovat kontrakt zprávy pro typ (to znamená, definovat mapování mezi typem a obálku protokolu SOAP), použít <xref:System.ServiceModel.MessageContractAttribute> typu. Následně použít <xref:System.ServiceModel.MessageHeaderAttribute> těmto členům typ, který chcete provést do záhlaví SOAP a použít <xref:System.ServiceModel.MessageBodyMemberAttribute> těmto členům chcete, aby se do části těla protokolu SOAP zprávy.  
  
 Následující kód představuje příklad použití kontrakt zprávy.  
  
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
  
 Při použití tohoto typu jako parametr operace, je vygenerována následující obálku protokolu SOAP:  
  
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
  
 Všimněte si, že `operation` a `transactionDate` zobrazí jako hlavičky SOAP a těla protokolu SOAP se skládá z element obálky `BankingTransaction` obsahující `sourceAccount`,`targetAccount`, a `amount`.  
  
 Můžete použít <xref:System.ServiceModel.MessageHeaderAttribute> a <xref:System.ServiceModel.MessageBodyMemberAttribute> do všech polí, vlastnosti a události, bez ohledu na to, zda jsou veřejné, privátní, chráněný nebo interní.  
  
 <xref:System.ServiceModel.MessageContractAttribute> Vám umožní určit WrapperName a WrapperNamespace atributy, které řídí název elementu obálku v těle protokolu SOAP zprávy. Ve výchozím nastavení název kontrakt zprávy typ se používá pro obálku a oboru názvů, ve kterém je definovaný kontrakt zprávy `HYPERLINK "http://tempuri.org/" http://tempuri.org/` se používá jako výchozí obor názvů.  
  
> [!NOTE]
>  <xref:System.Runtime.Serialization.KnownTypeAttribute>atributy se ignorují v kontrakty zpráv. Pokud <xref:System.Runtime.Serialization.KnownTypeAttribute> je potřeba, umístěte ji na operaci, která používá kontrakt zprávy nejistá.  
  
## <a name="controlling-header-and-body-part-names-and-namespaces"></a>Řízení záhlaví a názvům součástí textu a obory názvů  
 V protokolu SOAP reprezentace kontrakt zprávy každou část záhlaví a text mapuje na element XML, který má název a obor názvů.  
  
 Ve výchozím nastavení, obor názvů je stejný jako obor názvů kontraktu služby, který se účastní zprávu, a název je dáno název člena, ke kterému <xref:System.ServiceModel.MessageHeaderAttribute> nebo <xref:System.ServiceModel.MessageBodyMemberAttribute> jsou použity atributy.  
  
 Tato výchozí nastavení můžete změnit manipulace s <xref:System.ServiceModel.MessageContractMemberAttribute.Name%2A?displayProperty=nameWithType> a <xref:System.ServiceModel.MessageContractMemberAttribute.Namespace%2A?displayProperty=nameWithType> (na nadřazenou třídu <xref:System.ServiceModel.MessageHeaderAttribute> a <xref:System.ServiceModel.MessageBodyMemberAttribute> atributy).  
  
 Vezměte v úvahu třídy v následujícím příkladu kódu.  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageHeader(Namespace="http://schemas.contoso.com/auditing/2005")] public bool IsAudited;  
  [MessageBodyMember(Name="transactionData")] public BankingTransactionData theData;  
}  
```  
  
 V tomto příkladu `IsAudited` záhlaví je v oboru názvů zadaný v kódu a část textu, který představuje `theData` člen je reprezentována element XML s názvem `transactionData`. Následující obrázek znázorňuje XML vygenerovat pro tento kontrakt zprávy.  
  
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
  
## <a name="controlling-whether-the-soap-body-parts-are-wrapped"></a>Řízení, zda jsou zabalené částí textu protokolu SOAP  
 Ve výchozím nastavení jsou do zabalené elementu serializovat částí textu protokolu SOAP. Například následující kód ukazuje `HelloGreetingMessage` element obálky generované z názvu <xref:System.ServiceModel.MessageContractAttribute> typu v kontrakt zprávy pro `HelloGreetingMessage` zprávy.  
  
 [!code-csharp[MessageHeaderAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/messageheaderattribute/cs/services.cs#3)]
 [!code-vb[MessageHeaderAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/messageheaderattribute/vb/services.vb#3)]  
  
 Chcete-li potlačit element obálky, nastavte <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> vlastnost `false`. Chcete-li řídit název a obor názvů elementu obálky, použijte <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> a <xref:System.ServiceModel.MessageContractAttribute.WrapperNamespace%2A> vlastnosti.  
  
> [!NOTE]
>  S více než jednu část textu zprávy ve zprávy, které nejsou zabalené není kompatibilní s WS-I Basic Profile 1.1 a nedoporučuje při návrhu nové kontrakty zpráv. Však může být potřeba mít více než jednu část textu rozbalenou zprávy v některých scénářích konkrétní interoperability. Pokud budete přenášet více než jeden prvek dat text zprávy, se doporučuje použít režim výchozí (zabalená). S více než jeden záhlaví zprávy ve nerozbalené zprávy je zcela přijatelné.  
  
## <a name="using-custom-types-inside-message-contracts"></a>Pomocí vlastních typů uvnitř kontrakty zpráv  
 Každý záhlaví jednotlivé zprávy a část textu zprávy je serializováno (převedena na XML) pomocí zvolené Serializační stroj pro kontrakt služby, které zprávy se používá. Výchozí serializace modul, `XmlFormatter`, může zpracovat žádný typ, který má kontraktu dat, buď explicitně (tak, že <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType>) nebo implicitně (tím se primitivní typ, které mají <xref:System.SerializableAttribute?displayProperty=nameWithType>a tak dále). [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Použití kontraktů dat](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
 V předchozím příkladu `Operation` a `BankingTransactionData` typy musí mít kontraktu dat a `transactionDate` serializovat protože <xref:System.DateTime> jednoduchého typu (a tak má kontrakt implicitní dat).  
  
 Je však možné přepnout na jiný Serializační stroj, `XmlSerializer`. Pokud provedete tyto přepínače, je nutné zajistit, že všechny typy používané pro záhlaví zprávy a částí textu jsou serializovatelný pomocí `XmlSerializer`.  
  
## <a name="using-arrays-inside-message-contracts"></a>Použití polí uvnitř kontrakty zpráv  
 Můžete použít pole opakovaných elementů v kontrakty zpráv dvěma způsoby.  
  
 První je použití <xref:System.ServiceModel.MessageHeaderAttribute> nebo <xref:System.ServiceModel.MessageBodyMemberAttribute> přímo na pole. V takovém případě je jako jeden element (to znamená, jeden záhlaví nebo jednu část textu) s více podřízených elementů serializováno celé pole. Vezměte v úvahu třídy v následujícím příkladu.  
  
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
  
 Alternativou k tomuto je použít <xref:System.ServiceModel.MessageHeaderArrayAttribute>. V takovém případě každý element pole je serializováno nezávisle a tak, že každý element pole má jedno záhlaví, podobný následujícímu.  
  
```xml  
<numRecords>3</numRecords>  
<records>Record1</records>  
<records>Record2</records>  
<records>Record3</records>  
<branchID>20643</branchID>  
```  
  
 Výchozí název položky pole je název člena, ke kterému <xref:System.ServiceModel.MessageHeaderArrayAttribute> použít atributů.  
  
 <xref:System.ServiceModel.MessageHeaderArrayAttribute> Atribut dědí z <xref:System.ServiceModel.MessageHeaderAttribute>. Má stejnou sadu funkcí jako atributy mimo pole, například je možné nastavit pořadí, název a obor názvů pro pole hlavičky stejným způsobem, nastavit pro jednu hlavičky. Při použití `Order` vlastnost na pole, která se vztahuje na celé pole.  
  
 Můžete použít <xref:System.ServiceModel.MessageHeaderArrayAttribute> pouze na pole, není kolekcí.  
  
## <a name="using-byte-arrays-in-message-contracts"></a>Pomocí bajtových polí v kontrakty zpráv  
 Bajtová pole, pokud se používá s atributy mimo pole (<xref:System.ServiceModel.MessageBodyMemberAttribute> a <xref:System.ServiceModel.MessageHeaderAttribute>), nejsou považovány jako pole, ale speciální primitivní typ vyjádřený jako data ve výsledném souboru XML s kódováním Base64.  
  
 Pokud používáte pole bajtů s atributem pole <xref:System.ServiceModel.MessageHeaderArrayAttribute>, výsledky závisí na serializátoru, který je používán. S výchozí serializátor pole je reprezentován jako jednotlivé položky pro každý bajtů. Ale když `XmlSerializer` je vybraná, (pomocí <xref:System.ServiceModel.XmlSerializerFormatAttribute> na kontrakt služby), bajtová pole jsou považovány za Base64 dat bez ohledu na to, jestli se používají atributy pole nebo jiné pole.  
  
## <a name="signing-and-encrypting-parts-of-the-message"></a>Podepisování a šifrování částí zprávy  
 Kontrakt zprávy můžete určit, zda záhlaví nebo textu zprávy by měl být digitálně podepsat a zašifrovat.  
  
 To se provádí nastavením <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A?displayProperty=nameWithType> vlastnost <xref:System.ServiceModel.MessageHeaderAttribute> a <xref:System.ServiceModel.MessageBodyMemberAttribute> atributy. Vlastnost je výčet <xref:System.Net.Security.ProtectionLevel?displayProperty=nameWithType> zadejte a může být nastaven na <xref:System.Net.Security.ProtectionLevel.None> (bez šifrování nebo podpis), <xref:System.Net.Security.ProtectionLevel.Sign> (digitální podpis pouze), nebo <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> (šifrování i digitální podpis). Výchozí hodnota je <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.  
  
 Pro fungování těchto funkcí zabezpečení musí správně nakonfigurovat vazby a chování. Pokud používáte tyto funkce zabezpečení bez správnou konfiguraci (například pokus o přihlášení zprávu bez nutnosti zadávat svoje přihlašovací údaje), je vyvolána výjimka během ověření.  
  
 Zpráva hlavičky úroveň ochrany je určeno jednotlivě u každého záhlaví.  
  
 Pro částí textu zprávy úroveň ochrany můžete představit jako "minimální úroveň ochrany." Text má úroveň ochrany jenom jeden, bez ohledu na počet částí textu. Úroveň ochrany obsahu, je dáno nejvyšší <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A> vlastnost na hodnotu všechny části textu. Ale byste měli nastavit skutečné ochrany minimální úroveň požadované úrovně ochrany každá část textu.  
  
 Vezměte v úvahu třídy v následujícím příkladu kódu.  
  
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
  
 V tomto příkladu `recordID` hlavičky není chráněný, `patientName` je `signed`, a `SSN` je šifrovaný a podepsaný. Část alespoň jeden textu `medicalHistory`, má <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> použít, a proto je obsah celé zprávy šifrovaný a podepsaný, i když komentáře a částí textu diagnostiku zadejte nižší úrovně ochrany.  
  
## <a name="soap-action"></a>Akce protokolu SOAP  
 SOAP a související standardy webových služeb definovat vlastnost s názvem `Action` , může být k dispozici pro všechny protokolu SOAP zprávy určené. Operace <xref:System.ServiceModel.OperationContractAttribute.Action%2A?displayProperty=nameWithType> a <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A?displayProperty=nameWithType> vlastnosti řídí hodnota této vlastnosti.  
  
## <a name="soap-header-attributes"></a>Atributy hlavičky SOAP  
 Standard protokolu SOAP definuje následující atributy, které mohou existovat v záhlaví:  
  
-   `Actor/Role`(`Actor` v protokolu SOAP 1.1, `Role` v protokolu SOAP 1.2)  
  
-   `MustUnderstand`  
  
-   `Relay`  
  
 `Actor` Nebo `Role` Určuje atribut identifikátor URI (Uniform Resource) uzlu, pro kterou je určená danou hlavičku. `MustUnderstand` Atribut určuje, zda uzel zpracování záhlaví musíte pochopit. `Relay` Atribut určuje, zda záhlaví přenos pro podřízené uzly. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]neprovede žádné zpracování těchto atributů pro příchozí zprávy, s výjimkou `MustUnderstand` atributu, jak je uvedeno v části "Správa verzí kontraktů zpráva" dál v tomto tématu. Však umožňuje číst a zapisovat podle potřeby, stejně jako následující popis těchto atributů.  
  
 Při odesílání zprávy, nejsou ve výchozím nastavení vygenerované těchto atributů. Toto můžete změnit dvěma způsoby. Nejprve může staticky nastavíte atributy na všechny požadované hodnoty tak, že změníte <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.MessageHeaderAttribute.MustUnderstand%2A?displayProperty=nameWithType>, a <xref:System.ServiceModel.MessageHeaderAttribute.Relay%2A?displayProperty=nameWithType> vlastnosti, jak je znázorněno v následujícím příkladu kódu. (Všimněte si, že je žádné `Role` vlastnost; nastavení <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A> vlastnost vysílá `Role` atribut Pokud používáte SOAP 1.2).  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader(Actor="http://auditingservice.contoso.com", MustUnderstand=true)] public bool IsAudited;  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public BankingTransactionData theData;  
}  
```  
  
 Druhý způsob pro řízení těchto atributů je dynamicky prostřednictvím kódu. Toho lze dosáhnout pomocí zabalení typu požadované hlavičky v <xref:System.ServiceModel.MessageHeader%601> typu (ujistěte se, abyste nezaměnili tento typ s verzí neobecnou) a pomocí typu společně s <xref:System.ServiceModel.MessageHeaderAttribute>. Pak můžete použít vlastnosti na <xref:System.ServiceModel.MessageHeader%601> nastavit atributy protokolu SOAP, jak je znázorněno v následujícím příkladu kódu.  
  
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
  
 Pokud používáte dynamické i statické kontrolní mechanismy, jsou použity jako výchozí nastavení statické ale můžete později přepsat pomocí dynamické mechanismus, jak je znázorněno v následujícím kódu.  
  
```csharp  
[MessageHeader(MustUnderstand=true)] public MessageHeader<Person> documentApprover;  
// later on in the code:  
BankingTransaction bt = new BankingTransaction();  
bt.documentApprover = new MessageHeader<Person>();  
bt.documentApprover.MustUnderstand = false; // override the static default of 'true'  
```  
  
 Vytvoření opakovaných záhlaví s ovládacím prvkem dynamického atributu je povoleno, jak je znázorněno v následujícím kódu.  
  
```csharp  
[MessageHeaderArray] public MessageHeader<Person> documentApprovers[];  
```  
  
 Na straně příjmu, čtení těchto atributů protokolu SOAP lze provést pouze pokud <xref:System.ServiceModel.MessageHeader%601> třída se používá pro hlavičku v typu. Zkontrolujte `Actor`, `Relay`, nebo `MustUnderstand` vlastnosti záhlaví <xref:System.ServiceModel.MessageHeader%601> typ ke zjištění nastavení atributů na přijatou zprávu.  
  
 Když zprávu přijme a pak se odešle zpět, nastavení atributů protokolu SOAP, jdou pouze operace round-trip pro hlavičky <xref:System.ServiceModel.MessageHeader%601> typu.  
  
## <a name="order-of-soap-body-parts"></a>Pořadí částí textu protokolu SOAP  
 V některých případech můžete řídit pořadí částí textu. Je abecední ve výchozím nastavení pořadí prvků textu, ale je řízena <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> vlastnost. Tato vlastnost má stejnou sémantiku jako <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A?displayProperty=nameWithType> vlastnost, s výjimkou jejich chování v dědičnosti scénáře (v kontrakty zpráv, základní typ textu, které nejsou členy seřazeny před členy textu odvozený typ). [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Pořadí datových členů](../../../../docs/framework/wcf/feature-details/data-member-order.md).  
  
 V následujícím příkladu `amount` by za normálních okolností pocházet nejprve vzhledem k tomu, že je první podle abecedy. Ale <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A> vlastnost vloží je do třetí polohy.  
  
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
 V některých případech může muset změnit kontrakty zpráv. Nová verze aplikace může například přidat hlavičku navíc na zprávy. Potom při odesílání z nové verze starý, systém musí řešit navíc záhlaví, jakož i chybí záhlaví při přechodu opačným směrem.  
  
 Správa verzí hlaviček, platí následující pravidla:  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]proti hlavičkách chybí – odpovídající členové jsou ponechány na jejich výchozí hodnoty.  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]také ignoruje neočekávané další hlavičky. Jedinou výjimkou tohoto pravidla je, pokud má navíc záhlaví `MustUnderstand` atribut nastaven na `true` v příchozí zprávu SOAP – v takovém případě je vyvolána výjimka, protože hlavičku, která je třeba chápat nelze zpracovat.  
  
 Zpráva subjekty mají podobné pravidla Správa verzí – chybí a dalších částí textu zprávy jsou ignorovány.  
  
## <a name="inheritance-considerations"></a>Důležité informace o dědičnosti  
 Typ kontrakt zprávy může dědit vlastnosti z jiného typu, dokud základní typ také obsahuje kontrakt zprávy.  
  
 Při vytváření nebo přístup k zprávy pomocí typ zprávy kontrakt, který dědí z jiné typy kontraktů zpráv, platí následující pravidla:  
  
-   Všechny hlavičky zpráv v hierarchii dědičnosti se shromažďují společně tvoří úplnou sadu hlaviček pro zprávu.  
  
-   Všechny části textu zprávy v hierarchii dědičnosti se shromažďují společně tvoří obsah úplné zprávy. Částí textu jsou seřazené podle obvyklé řazení pravidel (podle <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> vlastnost a potom abecední), s nemá význam pro jejich místo v hierarchii dědičnosti. Použití dědičnosti kontrakt zprávy, kde částí textu zprávy probíhat na více úrovních stromu dědičnosti se důrazně nedoporučuje. Pokud základní a odvozené třídě definovat hlavičku nebo část textu se stejným názvem, člena z většinu základní třída slouží k uložení hodnotu příslušné části Hlavička nebo text.  
  
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
  
 `PatientRecord` Třída popisuje zprávu s názvem jedno záhlaví `ID`. Záhlaví odpovídá `personID` a ne `patientID` člena, protože většina základní člen je zvolen. Proto `patientID` pole v tomto případě je zbytečné. Tělo zprávy obsahuje `diagnosis` element, za nímž následuje `patientName` elementu, protože se jedná o abecedním pořadí. Všimněte si, že tento příklad ukazuje vzor, který se důrazně nedoporučuje: základní i odvozené zpráva kontrakty mají částí textu zprávy.  
  
## <a name="wsdl-considerations"></a>Aspekty WSDL  
 Při generování z službu, která používá kontrakty zpráv kontraktu služby popis jazyka WSDL (Web), je důležité si pamatovat, že ne všechny funkce kontrakt zprávy se projeví ve výsledné schématu WSDL. Mějte na paměti následující body:  
  
-   WSDL nelze express koncept pole hlavičky. Při vytváření zpráv pomocí pole hlavičky pomocí <xref:System.ServiceModel.MessageHeaderArrayAttribute>, výsledná WSDL odráží pouze jedno záhlaví místo pole.  
  
-   Výsledný dokument WSDL nemusí odrážet některé informace úroveň ochrany.  
  
-   Typ zprávy generované ve schématu WSDL má stejný název jako název třídy typ kontrakt zprávy.  
  
-   Při použití stejné zprávy sbalit ve více operací, několik typů zpráv vytvoří v souboru WSDL. Přidáním čísla "2", "3" a tak dále, pro následné používá, jsou vytvářeny jedinečné názvy. Při importu zpět schématu WSDL, vytvoří se více typy kontraktů zpráv a jsou identické s výjimkou jejich názvy.  
  
## <a name="soap-encoding-considerations"></a>Kódování důležité informace o protokolu SOAP  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]umožňuje používat starší verze protokolu SOAP kódování styl XML, ale jeho použití se nedoporučuje. Při použití této styl (nastavením `Use` vlastnost `Encoded` na <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType> u kontrakt služby), platí následující další aspekty:  
  
-   Záhlaví zprávy nejsou podporovány; To znamená, že atribut <xref:System.ServiceModel.MessageHeaderAttribute> a pole atributu <xref:System.ServiceModel.MessageHeaderArrayAttribute> nejsou kompatibilní s kódováním protokolu SOAP.  
  
-   Pokud kontrakt zprávy není zabalená, to znamená, pokud vlastnost <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> je nastaven na `false`, kontrakt zprávy může mít část pouze jeden textu.  
  
-   Název elementu obálku pro kontrakt zprávy požadavku musí odpovídat názvu operaci. Použití `WrapperName` kontrakt zprávy pro tuto vlastnost.  
  
-   Název elementu obálku pro kontrakt zprávy odpovědi musí být stejný jako název operace na konci podle "Odpověď". Použití <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> kontrakt zprávy pro tuto vlastnost.  
  
-   Kódování SOAP zachovává odkazy na objekty. Zvažte například následující kód.  
  
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
  
 Po serializaci zprávu pomocí protokolu SOAP kódování, `changedFrom` a `changedTo` neobsahují své vlastní kopie `p`, ale místo toho přejděte na kopírování uvnitř `changedBy` elementu.  
  
## <a name="performance-considerations"></a>Faktory ovlivňující výkon  
 Každý záhlaví zprávy a část textu zprávy je serializováno nezávisle na ostatních. Proto lze stejné obory názvů deklarovat opakujte pro každou záhlaví a část textu. Pro zlepšení výkonu, zejména z hlediska velikost zprávy v drátové síti, konsolidovat více hlavičky a částí textu do jedné součásti Hlavička nebo text. Například místo následující kód:  
  
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
  
### <a name="event-based-asynchronous-and-message-contracts"></a>Na základě událostí asynchronní a kontrakty zpráv  
 Podle pokynů návrhu pro asynchronní model na základě událostí stavu, že pokud je vrácen více než jednu hodnotu, se vrátí jednu hodnotu jako `Result` vlastnost a jiné jsou vrácena jako vlastnosti na <xref:System.EventArgs> objektu. Jeden výsledek tohoto objektu je, že pokud klient naimportuje metadata pomocí možností na základě událostí asynchronní příkaz a operaci vrátí více než jednu hodnotu, výchozí <xref:System.EventArgs> objekt vrátí jednu hodnotu jako `Result` vlastnost a zbývající jsou vlastnosti <xref:System.EventArgs> objektu.  
  
 Pokud chcete dostávat zprávy objektu jako `Result` vlastnost a mít vrácené hodnoty jako vlastnosti tohoto objektu, použijte `/messageContract` příkaz možnost. Tím se vygeneruje podpisu, který vrátí zprávu odpovědi jako `Result` vlastnost <xref:System.EventArgs> objektu. Všechny interní návratové hodnoty jsou pak vlastnosti objektu zprávu odpovědi.  
  
## <a name="see-also"></a>Viz také  
 [Použití kontraktů dat](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [Navrhování a implementace služeb](../../../../docs/framework/wcf/designing-and-implementing-services.md)
