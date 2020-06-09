---
title: Použití kontraktů zpráv
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message contracts [WCF]
ms.assetid: 1e19c64a-ae84-4c2f-9155-91c54a77c249
ms.openlocfilehash: 1b102b97c62df0bb8b031ded0f9165a11f8a8911
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600267"
---
# <a name="using-message-contracts"></a><span data-ttu-id="cabe1-102">Použití kontraktů zpráv</span><span class="sxs-lookup"><span data-stu-id="cabe1-102">Using Message Contracts</span></span>
<span data-ttu-id="cabe1-103">Obvykle při sestavování aplikací Windows Communication Foundation (WCF), vývojáři účtují téměř pozor na datové struktury a problémy serializace a nepotřebují se k tomu zabývat strukturou zpráv, ve kterých jsou data přenášena.</span><span class="sxs-lookup"><span data-stu-id="cabe1-103">Typically when building Windows Communication Foundation (WCF) applications, developers pay close attention to the data structures and serialization issues and do not need to concern themselves with the structure of the messages in which the data is carried.</span></span> <span data-ttu-id="cabe1-104">Pro tyto aplikace je vytvoření kontraktů dat pro parametry nebo návratové hodnoty jednoduché.</span><span class="sxs-lookup"><span data-stu-id="cabe1-104">For these applications, creating data contracts for the parameters or return values is straightforward.</span></span> <span data-ttu-id="cabe1-105">(Další informace najdete v tématu [určení přenos dat v kontraktech služby](specifying-data-transfer-in-service-contracts.md).)</span><span class="sxs-lookup"><span data-stu-id="cabe1-105">(For more information, see [Specifying Data Transfer in Service Contracts](specifying-data-transfer-in-service-contracts.md).)</span></span>  
  
 <span data-ttu-id="cabe1-106">Někdy však kompletní řízení nad strukturou zprávy SOAP je stejně důležité jako řízení obsahu.</span><span class="sxs-lookup"><span data-stu-id="cabe1-106">However, sometimes complete control over the structure of a SOAP message is just as important as control over its contents.</span></span> <span data-ttu-id="cabe1-107">To platí hlavně v případě, že je vzájemná funkční spolupráce, nebo pro konkrétní řízení problémů zabezpečení na úrovni zprávy nebo části zprávy.</span><span class="sxs-lookup"><span data-stu-id="cabe1-107">This is especially true when interoperability is important or to specifically control security issues at the level of the message or message part.</span></span> <span data-ttu-id="cabe1-108">V těchto případech můžete vytvořit *kontrakt zprávy* , který vám umožní určit strukturu přesné požadované zprávy SOAP.</span><span class="sxs-lookup"><span data-stu-id="cabe1-108">In these cases, you can create a *message contract* that enables you to specify the structure of the precise SOAP message required.</span></span>  
  
 <span data-ttu-id="cabe1-109">Toto téma popisuje, jak používat různé atributy kontraktů zpráv k vytvoření konkrétního kontraktu zprávy pro vaši operaci.</span><span class="sxs-lookup"><span data-stu-id="cabe1-109">This topic discusses how to use the various message contract attributes to create a specific message contract for your operation.</span></span>  
  
## <a name="using-message-contracts-in-operations"></a><span data-ttu-id="cabe1-110">Použití kontraktů zpráv v operacích</span><span class="sxs-lookup"><span data-stu-id="cabe1-110">Using Message Contracts in Operations</span></span>  
 <span data-ttu-id="cabe1-111">Služba WCF podporuje operace modelované buď ve *stylu vzdáleného volání procedur (RPC)* , nebo ve *stylu zasílání zpráv*.</span><span class="sxs-lookup"><span data-stu-id="cabe1-111">WCF supports operations modeled on either the *remote procedure call (RPC) style* or the *messaging style*.</span></span> <span data-ttu-id="cabe1-112">Ve stylu operace RPC můžete použít libovolný serializovatelný typ a máte přístup k funkcím, které jsou k dispozici pro místní volání, jako je například více parametrů a `ref` `out` parametrů.</span><span class="sxs-lookup"><span data-stu-id="cabe1-112">In an RPC-style operation, you can use any serializable type, and you have access to the features that are available to local calls, such as multiple parameters and `ref` and `out` parameters.</span></span> <span data-ttu-id="cabe1-113">V tomto stylu je zvolena forma serializace ovládací prvky struktury dat v podkladových zprávách a modul runtime WCF vytvoří zprávy pro podporu operace.</span><span class="sxs-lookup"><span data-stu-id="cabe1-113">In this style, the form of serialization chosen controls the structure of the data in the underlying messages, and the WCF runtime creates the messages to support the operation.</span></span> <span data-ttu-id="cabe1-114">To umožňuje vývojářům, kteří nejsou obeznámeni se zprávami SOAP a SOAP, rychle a snadno vytvářet a používat aplikace služby.</span><span class="sxs-lookup"><span data-stu-id="cabe1-114">This enables developers who are not familiar with SOAP and SOAP messages to quickly and easily create and use service applications.</span></span>  
  
 <span data-ttu-id="cabe1-115">Následující příklad kódu ukazuje operaci služby modelované ve stylu RPC.</span><span class="sxs-lookup"><span data-stu-id="cabe1-115">The following code example shows a service operation modeled on the RPC style.</span></span>  
  
```csharp  
[OperationContract]  
public BankingTransactionResponse PostBankingTransaction(BankingTransaction bt);  
```  
  
 <span data-ttu-id="cabe1-116">Obvykle je kontrakt dat dostačující k definování schématu pro zprávy.</span><span class="sxs-lookup"><span data-stu-id="cabe1-116">Normally, a data contract is sufficient to define the schema for the messages.</span></span> <span data-ttu-id="cabe1-117">Například v předchozím příkladu je dostačující pro většinu aplikací, pokud `BankingTransaction` a `BankingTransactionResponse` mají kontrakty dat k definování obsahu podkladových zpráv SOAP.</span><span class="sxs-lookup"><span data-stu-id="cabe1-117">For instance, in the preceding example, it is sufficient for most applications if `BankingTransaction` and `BankingTransactionResponse` have data contracts to define the contents of the underlying SOAP messages.</span></span> <span data-ttu-id="cabe1-118">Další informace o kontraktech dat najdete v tématu [Použití kontraktů dat](using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="cabe1-118">For more information about data contracts, see [Using Data Contracts](using-data-contracts.md).</span></span>  
  
 <span data-ttu-id="cabe1-119">Občas ale je nutné přesně určit, jak se struktura zprávy protokolu SOAP přenáší přes síťový kabel.</span><span class="sxs-lookup"><span data-stu-id="cabe1-119">However, occasionally it is necessary to precisely control how the structure of the SOAP message transmitted over the wire.</span></span> <span data-ttu-id="cabe1-120">Nejběžnější scénář pro toto je vložení vlastních hlaviček SOAP.</span><span class="sxs-lookup"><span data-stu-id="cabe1-120">The most common scenario for this is inserting custom SOAP headers.</span></span> <span data-ttu-id="cabe1-121">Dalším běžným scénářem je definování vlastností zabezpečení pro záhlaví a text zprávy, to znamená, abyste se rozhodli, jestli jsou tyto prvky digitálně podepsané a šifrované.</span><span class="sxs-lookup"><span data-stu-id="cabe1-121">Another common scenario is to define security properties for the message's headers and body, that is, to decide whether these elements are digitally signed and encrypted.</span></span> <span data-ttu-id="cabe1-122">Nakonec některé zásobníky SOAP jiných výrobců vyžadují, aby zprávy byly v konkrétním formátu.</span><span class="sxs-lookup"><span data-stu-id="cabe1-122">Finally, some third-party SOAP stacks require messages be in a specific format.</span></span> <span data-ttu-id="cabe1-123">Tento ovládací prvek poskytuje operace stylu zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="cabe1-123">Messaging-style operations provide this control.</span></span>  
  
 <span data-ttu-id="cabe1-124">Operace ve stylu zasílání zpráv má maximálně jeden parametr a jednu návratovou hodnotu, kde jsou oba typy zprávy. To znamená, že jsou serializovány přímo do zadané struktury zpráv SOAP.</span><span class="sxs-lookup"><span data-stu-id="cabe1-124">A messaging-style operation has at most one parameter and one return value where both types are message types; that is, they serialize directly into a specified SOAP message structure.</span></span> <span data-ttu-id="cabe1-125">Může to být libovolný typ označený jako <xref:System.ServiceModel.MessageContractAttribute> <xref:System.ServiceModel.Channels.Message> typ nebo.</span><span class="sxs-lookup"><span data-stu-id="cabe1-125">This may be any type marked with the <xref:System.ServiceModel.MessageContractAttribute> or the <xref:System.ServiceModel.Channels.Message> type.</span></span> <span data-ttu-id="cabe1-126">Následující příklad kódu ukazuje operaci podobnou předchozímu stylu RCP, ale používá styl zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="cabe1-126">The following code example shows an operation similar to the preceding RCP-style, but which uses the messaging style.</span></span>  
  
 <span data-ttu-id="cabe1-127">Například pokud `BankingTransaction` a `BankingTransactionResponse` jsou oba typy, které jsou kontrakty zpráv, je kód v následujících operacích platný.</span><span class="sxs-lookup"><span data-stu-id="cabe1-127">For example, if `BankingTransaction` and `BankingTransactionResponse` are both types that are message contracts, then the code in the following operations is valid.</span></span>  
  
```csharp  
[OperationContract]  
BankingTransactionResponse Process(BankingTransaction bt);  
[OperationContract]  
void Store(BankingTransaction bt);  
[OperationContract]  
BankingTransactionResponse GetResponse();  
```  
  
 <span data-ttu-id="cabe1-128">Následující kód však není platný.</span><span class="sxs-lookup"><span data-stu-id="cabe1-128">However, the following code is invalid.</span></span>  
  
```csharp  
[OperationContract]  
bool Validate(BankingTransaction bt);  
// Invalid, the return type is not a message contract.  
[OperationContract]  
void Reconcile(BankingTransaction bt1, BankingTransaction bt2);  
// Invalid, there is more than one parameter.  
```  
  
 <span data-ttu-id="cabe1-129">Výjimka je vyvolána pro všechny operace, které zahrnují typ kontraktu zprávy a které nenásledují po jednom z platných vzorů.</span><span class="sxs-lookup"><span data-stu-id="cabe1-129">An exception is thrown for any operation that involves a message contract type and that does not follow one of the valid patterns.</span></span> <span data-ttu-id="cabe1-130">Samozřejmě operací, které nezahrnují typy kontraktů zpráv, se tyto omezení nevztahují.</span><span class="sxs-lookup"><span data-stu-id="cabe1-130">Of course, operations that do not involve message contract types are not subject to these restrictions.</span></span>  
  
 <span data-ttu-id="cabe1-131">Pokud typ obsahuje kontrakt zprávy i kontrakt dat, je při použití daného typu v rámci operace zvážen pouze jeho kontrakt zprávy.</span><span class="sxs-lookup"><span data-stu-id="cabe1-131">If a type has both a message contract and a data contract, only its message contract is considered when the type is used in an operation.</span></span>  
  
## <a name="defining-message-contracts"></a><span data-ttu-id="cabe1-132">Definování kontraktů zpráv</span><span class="sxs-lookup"><span data-stu-id="cabe1-132">Defining Message Contracts</span></span>  
 <span data-ttu-id="cabe1-133">Chcete-li definovat kontrakt zprávy pro typ (tj. pro definování mapování mezi typem a obálkou protokolu SOAP), použijte <xref:System.ServiceModel.MessageContractAttribute> pro typ.</span><span class="sxs-lookup"><span data-stu-id="cabe1-133">To define a message contract for a type (that is, to define the mapping between the type and a SOAP envelope), apply the <xref:System.ServiceModel.MessageContractAttribute> to the type.</span></span> <span data-ttu-id="cabe1-134">Pak použijte u <xref:System.ServiceModel.MessageHeaderAttribute> těch členů typu, který chcete vytvořit v hlavičkách SOAP, a použijte u <xref:System.ServiceModel.MessageBodyMemberAttribute> těch členů, které chcete vytvořit do částí těla protokolu SOAP zprávy.</span><span class="sxs-lookup"><span data-stu-id="cabe1-134">Then apply the <xref:System.ServiceModel.MessageHeaderAttribute> to those members of the type you want to make into SOAP headers, and apply the <xref:System.ServiceModel.MessageBodyMemberAttribute> to those members you want to make into parts of the SOAP body of the message.</span></span>  
  
 <span data-ttu-id="cabe1-135">Následující kód poskytuje příklad použití kontraktu zprávy.</span><span class="sxs-lookup"><span data-stu-id="cabe1-135">The following code provides an example of using a message contract.</span></span>  
  
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
  
 <span data-ttu-id="cabe1-136">Při použití tohoto typu jako parametru operace je vygenerována následující obálka protokolu SOAP:</span><span class="sxs-lookup"><span data-stu-id="cabe1-136">When using this type as an operation parameter, the following SOAP envelope is generated:</span></span>  
  
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
  
 <span data-ttu-id="cabe1-137">Všimněte si, že `operation` a `transactionDate` jak se zobrazí jako hlavičky SOAP a tělo SOAP se skládá z prvku obálky `BankingTransaction` obsahujícího `sourceAccount` , `targetAccount` a `amount` .</span><span class="sxs-lookup"><span data-stu-id="cabe1-137">Notice that `operation` and `transactionDate` appear as SOAP headers and the SOAP body consists of a wrapper element `BankingTransaction` containing `sourceAccount`,`targetAccount`, and `amount`.</span></span>  
  
 <span data-ttu-id="cabe1-138">Můžete použít <xref:System.ServiceModel.MessageHeaderAttribute> a <xref:System.ServiceModel.MessageBodyMemberAttribute> pro všechna pole, vlastnosti a události bez ohledu na to, zda jsou veřejné, privátní, chráněné nebo interní.</span><span class="sxs-lookup"><span data-stu-id="cabe1-138">You can apply the <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> to all fields, properties, and events, regardless of whether they are public, private, protected, or internal.</span></span>  
  
 <span data-ttu-id="cabe1-139"><xref:System.ServiceModel.MessageContractAttribute>Umožňuje určit atributy wrapper a WrapperNamespace, které řídí název prvku obálky v těle zprávy protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="cabe1-139">The <xref:System.ServiceModel.MessageContractAttribute> allows you to specify the WrapperName and WrapperNamespace attributes which control the name of the wrapper element in the body of the SOAP message.</span></span> <span data-ttu-id="cabe1-140">Ve výchozím nastavení se pro obálku používá název typu kontraktu zprávy a obor názvů, ve kterém je kontrakt zprávy definovaný, `http://tempuri.org/` se používá jako výchozí obor názvů.</span><span class="sxs-lookup"><span data-stu-id="cabe1-140">By default the name of the message contract type is used for the wrapper and the namespace in which the message contract is defined `http://tempuri.org/` is used as the default namespace.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cabe1-141"><xref:System.Runtime.Serialization.KnownTypeAttribute>atributy se v kontraktech zpráv ignorují.</span><span class="sxs-lookup"><span data-stu-id="cabe1-141"><xref:System.Runtime.Serialization.KnownTypeAttribute> attributes are ignored in message contracts.</span></span> <span data-ttu-id="cabe1-142">Pokud <xref:System.Runtime.Serialization.KnownTypeAttribute> se vyžaduje, umístěte ho na operaci, která používá daný kontrakt zprávy.</span><span class="sxs-lookup"><span data-stu-id="cabe1-142">If a <xref:System.Runtime.Serialization.KnownTypeAttribute> is required, place it on the operation that is using the message contract in question.</span></span>  
  
## <a name="controlling-header-and-body-part-names-and-namespaces"></a><span data-ttu-id="cabe1-143">Řízení záhlaví a názvů částí těla a oborů názvů</span><span class="sxs-lookup"><span data-stu-id="cabe1-143">Controlling Header and Body Part Names and Namespaces</span></span>  
 <span data-ttu-id="cabe1-144">V prohlášení protokolu SOAP u kontraktu zprávy se každé záhlaví a část těla mapuje na element XML, který má název a obor názvů.</span><span class="sxs-lookup"><span data-stu-id="cabe1-144">In the SOAP representation of a message contract, each header and body part maps to an XML element that has a name and a namespace.</span></span>  
  
 <span data-ttu-id="cabe1-145">Ve výchozím nastavení je obor názvů stejný jako obor názvů kontraktu služby, ve kterém se zpráva účastní, a název je určen názvem člena, na který <xref:System.ServiceModel.MessageHeaderAttribute> <xref:System.ServiceModel.MessageBodyMemberAttribute> jsou atributy aplikovány.</span><span class="sxs-lookup"><span data-stu-id="cabe1-145">By default, the namespace is the same as the namespace of the service contract that the message is participating in, and the name is determined by the member name to which the <xref:System.ServiceModel.MessageHeaderAttribute> or the <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes are applied.</span></span>  
  
 <span data-ttu-id="cabe1-146">Tato výchozí nastavení můžete změnit pomocí manipulace s <xref:System.ServiceModel.MessageContractMemberAttribute.Name%2A?displayProperty=nameWithType> a <xref:System.ServiceModel.MessageContractMemberAttribute.Namespace%2A?displayProperty=nameWithType> (v nadřazené třídě <xref:System.ServiceModel.MessageHeaderAttribute> <xref:System.ServiceModel.MessageBodyMemberAttribute> atributů a).</span><span class="sxs-lookup"><span data-stu-id="cabe1-146">You can change these defaults by manipulating the <xref:System.ServiceModel.MessageContractMemberAttribute.Name%2A?displayProperty=nameWithType> and <xref:System.ServiceModel.MessageContractMemberAttribute.Namespace%2A?displayProperty=nameWithType> (on the parent class of the <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes).</span></span>  
  
 <span data-ttu-id="cabe1-147">Zvažte třídu v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="cabe1-147">Consider the class in the following code example.</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageHeader(Namespace="http://schemas.contoso.com/auditing/2005")] public bool IsAudited;  
  [MessageBodyMember(Name="transactionData")] public BankingTransactionData theData;  
}  
```  
  
 <span data-ttu-id="cabe1-148">V tomto příkladu `IsAudited` je hlavička v oboru názvů zadaném v kódu a část těla, která představuje `theData` člen, je reprezentována elementem XML s názvem `transactionData` .</span><span class="sxs-lookup"><span data-stu-id="cabe1-148">In this example, the `IsAudited` header is in the namespace specified in the code, and the body part that represents the `theData` member is represented by an XML element with the name `transactionData`.</span></span> <span data-ttu-id="cabe1-149">Následující příklad ukazuje generovaný kód XML pro tento kontrakt zprávy.</span><span class="sxs-lookup"><span data-stu-id="cabe1-149">The following shows the XML generated for this message contract.</span></span>  
  
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
  
## <a name="controlling-whether-the-soap-body-parts-are-wrapped"></a><span data-ttu-id="cabe1-150">Řízení, zda jsou části těla protokolu SOAP zabaleny</span><span class="sxs-lookup"><span data-stu-id="cabe1-150">Controlling Whether the SOAP Body Parts Are Wrapped</span></span>  
 <span data-ttu-id="cabe1-151">Ve výchozím nastavení jsou části těla protokolu SOAP serializovány uvnitř zabaleného prvku.</span><span class="sxs-lookup"><span data-stu-id="cabe1-151">By default, the SOAP body parts are serialized inside a wrapped element.</span></span> <span data-ttu-id="cabe1-152">Například následující kód ukazuje `HelloGreetingMessage` Obálkový prvek vygenerovaný z názvu <xref:System.ServiceModel.MessageContractAttribute> typu v kontraktu zprávy pro `HelloGreetingMessage` zprávu.</span><span class="sxs-lookup"><span data-stu-id="cabe1-152">For example, the following code shows the `HelloGreetingMessage` wrapper element generated from the name of the <xref:System.ServiceModel.MessageContractAttribute> type in the message contract for the `HelloGreetingMessage` message.</span></span>  
  
[!code-csharp[MessageHeaderAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/messageheaderattribute/cs/services.cs#3)]
[!code-vb[MessageHeaderAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/messageheaderattribute/vb/services.vb#3)]  
  
 <span data-ttu-id="cabe1-153">Chcete-li potlačit prvek obálky, nastavte <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> vlastnost na hodnotu `false` .</span><span class="sxs-lookup"><span data-stu-id="cabe1-153">To suppress the wrapper element, set the <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> property to `false`.</span></span> <span data-ttu-id="cabe1-154">Chcete-li řídit název a obor názvů prvku obálky, použijte <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> <xref:System.ServiceModel.MessageContractAttribute.WrapperNamespace%2A> vlastnosti a.</span><span class="sxs-lookup"><span data-stu-id="cabe1-154">To control the name and the namespace of the wrapper element, use the <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> and <xref:System.ServiceModel.MessageContractAttribute.WrapperNamespace%2A> properties.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cabe1-155">Pokud máte více než jednu část těla zprávy ve zprávách, které nejsou zabaleny, není kompatibilní s profilem WS-I Basic Profile 1,1 a při navrhování nových kontraktů zpráv se nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="cabe1-155">Having more than one message body part in messages that are not wrapped is not compliant with WS-I Basic Profile 1.1 and is not recommended when designing new message contracts.</span></span> <span data-ttu-id="cabe1-156">Může být ale nutné mít více než jeden nezabalený tělo zprávy v některých specifických scénářích interoperability.</span><span class="sxs-lookup"><span data-stu-id="cabe1-156">However, it may be necessary to have more than one unwrapped message body part in certain specific interoperability scenarios.</span></span> <span data-ttu-id="cabe1-157">Pokud budete přenášet více než jednu část dat v těle zprávy, doporučuje se použít výchozí (zabalený) režim.</span><span class="sxs-lookup"><span data-stu-id="cabe1-157">If you are going to transmit more than one piece of data in a message body, it is recommended to use the default (wrapped) mode.</span></span> <span data-ttu-id="cabe1-158">Používání více než jednoho záhlaví zprávy v nezabalených zprávách je zcela přijatelné.</span><span class="sxs-lookup"><span data-stu-id="cabe1-158">Having more than one message header in unwrapped messages is completely acceptable.</span></span>  
  
## <a name="using-custom-types-inside-message-contracts"></a><span data-ttu-id="cabe1-159">Použití vlastních typů uvnitř kontraktů zpráv</span><span class="sxs-lookup"><span data-stu-id="cabe1-159">Using Custom Types Inside Message Contracts</span></span>  
 <span data-ttu-id="cabe1-160">Každá jednotlivá Hlavička zprávy a část těla zprávy je serializovaná (převedená do XML) s použitím vybraného serializačního modulu pro kontrakt služby, kde se zpráva používá.</span><span class="sxs-lookup"><span data-stu-id="cabe1-160">Each individual message header and message body part is serialized (turned into XML) using the chosen serialization engine for the service contract where the message is used.</span></span> <span data-ttu-id="cabe1-161">Výchozí Serializační modul, `XmlFormatter` , může zpracovat jakýkoli typ, který má kontrakt dat, buď explicitně (pomocí <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType> ), nebo implicitně (pomocí primitivního typu, který má <xref:System.SerializableAttribute?displayProperty=nameWithType> a tak dále).</span><span class="sxs-lookup"><span data-stu-id="cabe1-161">The default serialization engine, the `XmlFormatter`, can handle any type that has a data contract, either explicitly (by having the <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType>) or implicitly (by being a primitive type, having the <xref:System.SerializableAttribute?displayProperty=nameWithType>, and so on).</span></span> <span data-ttu-id="cabe1-162">Další informace najdete v tématu [Použití kontraktů dat](using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="cabe1-162">For more information, see [Using Data Contracts](using-data-contracts.md).</span></span>  
  
 <span data-ttu-id="cabe1-163">V předchozím příkladu `Operation` `BankingTransactionData` musí mít typy a typ kontraktu dat, který `transactionDate` je serializovatelný, protože <xref:System.DateTime> je primitivní (a má tedy implicitní kontrakt dat).</span><span class="sxs-lookup"><span data-stu-id="cabe1-163">In the preceding example, the `Operation` and `BankingTransactionData` types must have a data contract, and `transactionDate` is serializable because <xref:System.DateTime> is a primitive (and so has an implicit data contract).</span></span>  
  
 <span data-ttu-id="cabe1-164">Je však možné přepnout na jiný Serializační modul, `XmlSerializer` .</span><span class="sxs-lookup"><span data-stu-id="cabe1-164">However, it is possible to switch to a different serialization engine, the `XmlSerializer`.</span></span> <span data-ttu-id="cabe1-165">Pokud tento přepínač provedete, měli byste zajistit, aby všechny typy používané pro záhlaví zpráv a části těla textu byly serializovatelný pomocí `XmlSerializer` .</span><span class="sxs-lookup"><span data-stu-id="cabe1-165">If you make such a switch, you should ensure that all of the types used for message headers and body parts are serializable using the `XmlSerializer`.</span></span>  
  
## <a name="using-arrays-inside-message-contracts"></a><span data-ttu-id="cabe1-166">Použití polí uvnitř kontraktů zpráv</span><span class="sxs-lookup"><span data-stu-id="cabe1-166">Using Arrays Inside Message Contracts</span></span>  
 <span data-ttu-id="cabe1-167">Pole opakujících se prvků v kontraktech zpráv můžete použít dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="cabe1-167">You can use arrays of repeating elements in message contracts in two ways.</span></span>  
  
 <span data-ttu-id="cabe1-168">První je použití <xref:System.ServiceModel.MessageHeaderAttribute> nebo <xref:System.ServiceModel.MessageBodyMemberAttribute> přímo v poli.</span><span class="sxs-lookup"><span data-stu-id="cabe1-168">The first is to use a <xref:System.ServiceModel.MessageHeaderAttribute> or a <xref:System.ServiceModel.MessageBodyMemberAttribute> directly on the array.</span></span> <span data-ttu-id="cabe1-169">V tomto případě je celé pole serializováno jako jeden prvek (tj. jedna hlavička nebo jedna část těla) s více podřízenými prvky.</span><span class="sxs-lookup"><span data-stu-id="cabe1-169">In this case, the entire array is serialized as one element (that is, one header or one body part) with multiple child elements.</span></span> <span data-ttu-id="cabe1-170">V následujícím příkladu zvažte třídu.</span><span class="sxs-lookup"><span data-stu-id="cabe1-170">Consider the class in the following example.</span></span>  
  
```csharp  
[MessageContract]  
public class BankingDepositLog  
{  
  [MessageHeader] public int numRecords;  
  [MessageHeader] public DepositRecord[] records;  
  [MessageHeader] public int branchID;  
}  
```  
  
 <span data-ttu-id="cabe1-171">Výsledkem je, že hlavičky SOAP jsou podobné následujícímu.</span><span class="sxs-lookup"><span data-stu-id="cabe1-171">This results in SOAP headers is similar to the following.</span></span>  
  
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
  
 <span data-ttu-id="cabe1-172">Alternativou k tomu je použití <xref:System.ServiceModel.MessageHeaderArrayAttribute> .</span><span class="sxs-lookup"><span data-stu-id="cabe1-172">An alternative to this is to use the <xref:System.ServiceModel.MessageHeaderArrayAttribute>.</span></span> <span data-ttu-id="cabe1-173">V tomto případě jsou jednotlivé prvky pole serializovány nezávisle, takže každý prvek pole má jednu hlavičku, podobně jako následující.</span><span class="sxs-lookup"><span data-stu-id="cabe1-173">In this case, each array element is serialized independently and so that each array element has one header, similar to the following.</span></span>  
  
```xml  
<numRecords>3</numRecords>  
<records>Record1</records>  
<records>Record2</records>  
<records>Record3</records>  
<branchID>20643</branchID>  
```  
  
 <span data-ttu-id="cabe1-174">Výchozí název pro položky pole je název člena, na který jsou <xref:System.ServiceModel.MessageHeaderArrayAttribute> atributy aplikovány.</span><span class="sxs-lookup"><span data-stu-id="cabe1-174">The default name for array entries is the name of the member to which the <xref:System.ServiceModel.MessageHeaderArrayAttribute> attributes is applied.</span></span>  
  
 <span data-ttu-id="cabe1-175"><xref:System.ServiceModel.MessageHeaderArrayAttribute>Atribut dědí z <xref:System.ServiceModel.MessageHeaderAttribute> .</span><span class="sxs-lookup"><span data-stu-id="cabe1-175">The <xref:System.ServiceModel.MessageHeaderArrayAttribute> attribute inherits from the <xref:System.ServiceModel.MessageHeaderAttribute>.</span></span> <span data-ttu-id="cabe1-176">Má stejnou sadu funkcí jako atributy mimo pole, například je možné nastavit pořadí, název a obor názvů pro pole hlaviček stejným způsobem jako pro jednu hlavičku.</span><span class="sxs-lookup"><span data-stu-id="cabe1-176">It has the same set of features as the non-array attributes, for example, it is possible to set the order, name, and namespace for an array of headers in the same way you set it for a single header.</span></span> <span data-ttu-id="cabe1-177">Použijete-li `Order` vlastnost v poli, platí pro celé pole.</span><span class="sxs-lookup"><span data-stu-id="cabe1-177">When you use the `Order` property on an array, it applies to the entire array.</span></span>  
  
 <span data-ttu-id="cabe1-178">Můžete použít <xref:System.ServiceModel.MessageHeaderArrayAttribute> jenom pro pole, ne pro kolekce.</span><span class="sxs-lookup"><span data-stu-id="cabe1-178">You can apply the <xref:System.ServiceModel.MessageHeaderArrayAttribute> only to arrays, not collections.</span></span>  
  
## <a name="using-byte-arrays-in-message-contracts"></a><span data-ttu-id="cabe1-179">Použití polí bajtů v kontraktech zpráv</span><span class="sxs-lookup"><span data-stu-id="cabe1-179">Using Byte Arrays in Message Contracts</span></span>  
 <span data-ttu-id="cabe1-180">Pole bajtů, pokud se používají s atributy mimo pole ( <xref:System.ServiceModel.MessageBodyMemberAttribute> a <xref:System.ServiceModel.MessageHeaderAttribute> ), nejsou považována za pole, ale jako speciální primitivní typ reprezentovaný ve VÝSLEDNÉM souboru XML jako data zakódovaná ve formátu base64.</span><span class="sxs-lookup"><span data-stu-id="cabe1-180">Byte arrays, when used with the non-array attributes (<xref:System.ServiceModel.MessageBodyMemberAttribute> and <xref:System.ServiceModel.MessageHeaderAttribute>), are not treated as arrays but as a special primitive type represented as Base64-encoded data in the resulting XML.</span></span>  
  
 <span data-ttu-id="cabe1-181">Použijete-li pole bajtů s atributem array <xref:System.ServiceModel.MessageHeaderArrayAttribute> , výsledky budou záviset na použitém serializátoru.</span><span class="sxs-lookup"><span data-stu-id="cabe1-181">When you use byte arrays with the array attribute <xref:System.ServiceModel.MessageHeaderArrayAttribute>, the results depend on the serializer in use.</span></span> <span data-ttu-id="cabe1-182">U výchozího serializátoru je pole vyjádřeno jako jednotlivé položky pro každý bajt.</span><span class="sxs-lookup"><span data-stu-id="cabe1-182">With the default serializer, the array is represented as an individual entry for each byte.</span></span> <span data-ttu-id="cabe1-183">Pokud `XmlSerializer` je však vybrána možnost (pomocí <xref:System.ServiceModel.XmlSerializerFormatAttribute> kontraktu služby), pole bajtů jsou považována za data typu Base64 bez ohledu na to, zda jsou použity atributy Array a Array.</span><span class="sxs-lookup"><span data-stu-id="cabe1-183">However, when the `XmlSerializer` is selected, (using the <xref:System.ServiceModel.XmlSerializerFormatAttribute> on the service contract), byte arrays are treated as Base64 data regardless of whether the array or non-array attributes are used.</span></span>  
  
## <a name="signing-and-encrypting-parts-of-the-message"></a><span data-ttu-id="cabe1-184">Podepisování a šifrování částí zprávy</span><span class="sxs-lookup"><span data-stu-id="cabe1-184">Signing and Encrypting Parts of the Message</span></span>  
 <span data-ttu-id="cabe1-185">Kontrakt zprávy může označovat, zda mají být záhlaví a/nebo text zprávy digitálně podepsány a zašifrovány.</span><span class="sxs-lookup"><span data-stu-id="cabe1-185">A message contract can indicate whether the headers and/or body of the message should be digitally signed and encrypted.</span></span>  
  
 <span data-ttu-id="cabe1-186">To se provádí nastavením <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A?displayProperty=nameWithType> vlastnosti v <xref:System.ServiceModel.MessageHeaderAttribute> <xref:System.ServiceModel.MessageBodyMemberAttribute> atributech a.</span><span class="sxs-lookup"><span data-stu-id="cabe1-186">This is done by setting the <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A?displayProperty=nameWithType> property on the <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes.</span></span> <span data-ttu-id="cabe1-187">Vlastnost je výčet <xref:System.Net.Security.ProtectionLevel?displayProperty=nameWithType> typu a může být nastaven na <xref:System.Net.Security.ProtectionLevel.None> (bez šifrování, podpis), <xref:System.Net.Security.ProtectionLevel.Sign> (pouze digitální podpis), nebo <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> (šifrování i digitální podpis).</span><span class="sxs-lookup"><span data-stu-id="cabe1-187">The property is an enumeration of the <xref:System.Net.Security.ProtectionLevel?displayProperty=nameWithType> type and can be set to <xref:System.Net.Security.ProtectionLevel.None> (no encryption or signature), <xref:System.Net.Security.ProtectionLevel.Sign> (digital signature only), or <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> (both encryption and a digital signature).</span></span> <span data-ttu-id="cabe1-188">Výchozí formát je <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span><span class="sxs-lookup"><span data-stu-id="cabe1-188">The default is <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span></span>  
  
 <span data-ttu-id="cabe1-189">Aby tyto funkce zabezpečení fungovaly, musíte správně nakonfigurovat vazbu a chování.</span><span class="sxs-lookup"><span data-stu-id="cabe1-189">For these security features to work, you must properly configure the binding and behaviors.</span></span> <span data-ttu-id="cabe1-190">Použijete-li tyto funkce zabezpečení bez správné konfigurace (například při pokusu o podepsání zprávy bez zadání přihlašovacích údajů), je vyvolána výjimka v době ověřování.</span><span class="sxs-lookup"><span data-stu-id="cabe1-190">If you use these security features without the proper configuration (for example, attempting to sign a message without supplying your credentials), an exception is thrown at validation time.</span></span>  
  
 <span data-ttu-id="cabe1-191">Pro záhlaví zpráv je úroveň ochrany určena individuálně pro každé záhlaví.</span><span class="sxs-lookup"><span data-stu-id="cabe1-191">For message headers, the protection level is determined individually for each header.</span></span>  
  
 <span data-ttu-id="cabe1-192">V části těla zprávy se úroveň ochrany dá představit jako minimální úroveň ochrany.</span><span class="sxs-lookup"><span data-stu-id="cabe1-192">For message body parts, the protection level can be thought of as the "minimum protection level."</span></span> <span data-ttu-id="cabe1-193">Tělo má pouze jednu úroveň ochrany bez ohledu na počet částí těla.</span><span class="sxs-lookup"><span data-stu-id="cabe1-193">The body has only one protection level, regardless of the number of body parts.</span></span> <span data-ttu-id="cabe1-194">Úroveň ochrany těla je určena nastavením nejvyšší <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A> vlastnosti všech částí těla.</span><span class="sxs-lookup"><span data-stu-id="cabe1-194">The protection level of the body is determined by the highest <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A> property setting of all the body parts.</span></span> <span data-ttu-id="cabe1-195">Měli byste ale nastavit úroveň ochrany každé části těla na skutečnou minimální požadovanou úroveň ochrany.</span><span class="sxs-lookup"><span data-stu-id="cabe1-195">However, you should set the protection level of each body part to the actual minimum protection level required.</span></span>  
  
 <span data-ttu-id="cabe1-196">Zvažte třídu v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="cabe1-196">Consider the class in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="cabe1-197">V tomto příkladu není `recordID` Hlavička chráněná, `patientName` je `signed` a `SSN` je šifrovaná a podepsaná.</span><span class="sxs-lookup"><span data-stu-id="cabe1-197">In this example, the `recordID` header is not protected, `patientName` is `signed`, and `SSN` is encrypted and signed.</span></span> <span data-ttu-id="cabe1-198">Alespoň jedna část těla, `medicalHistory` , která se <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> používá, a proto je celý text zprávy zašifrovaný a podepsaný, i když části těla komentářů a diagnostiky určují nižší úrovně ochrany.</span><span class="sxs-lookup"><span data-stu-id="cabe1-198">At least one body part, `medicalHistory`, has <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> applied, and thus the entire message body is encrypted and signed, even though the comments and diagnosis body parts specify lower protection levels.</span></span>  
  
## <a name="soap-action"></a><span data-ttu-id="cabe1-199">Akce SOAP</span><span class="sxs-lookup"><span data-stu-id="cabe1-199">SOAP Action</span></span>  
 <span data-ttu-id="cabe1-200">Standardy SOAP a související webové služby definují vlastnost s názvem `Action` , která může být k dispozici pro každou odeslanou zprávu SOAP.</span><span class="sxs-lookup"><span data-stu-id="cabe1-200">SOAP and related Web services standards define a property called `Action` that can be present for every SOAP message sent.</span></span> <span data-ttu-id="cabe1-201"><xref:System.ServiceModel.OperationContractAttribute.Action%2A?displayProperty=nameWithType> <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A?displayProperty=nameWithType> Vlastnost a vlastnosti určují hodnotu této vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="cabe1-201">The operation's <xref:System.ServiceModel.OperationContractAttribute.Action%2A?displayProperty=nameWithType> and <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A?displayProperty=nameWithType> properties control the value of this property.</span></span>  
  
## <a name="soap-header-attributes"></a><span data-ttu-id="cabe1-202">Atributy záhlaví SOAP</span><span class="sxs-lookup"><span data-stu-id="cabe1-202">SOAP Header Attributes</span></span>  
 <span data-ttu-id="cabe1-203">Standard SOAP definuje následující atributy, které mohou existovat v záhlaví:</span><span class="sxs-lookup"><span data-stu-id="cabe1-203">The SOAP standard defines the following attributes that may exist on a header:</span></span>  
  
- <span data-ttu-id="cabe1-204">`Actor/Role`( `Actor` v soap 1,1, `Role` v SOAP 1,2)</span><span class="sxs-lookup"><span data-stu-id="cabe1-204">`Actor/Role` (`Actor` in SOAP 1.1, `Role` in SOAP 1.2)</span></span>  
  
- `MustUnderstand`  
  
- `Relay`  
  
 <span data-ttu-id="cabe1-205">`Actor`Atribut or `Role` Určuje identifikátor URI (Uniform Resource Identifier) uzlu, pro který je daná hlavička určena.</span><span class="sxs-lookup"><span data-stu-id="cabe1-205">The `Actor` or `Role` attribute specifies the Uniform Resource Identifier (URI) of the node for which a given header is intended.</span></span> <span data-ttu-id="cabe1-206">`MustUnderstand`Atribut určuje, zda musí uzel zpracovat hlavičku.</span><span class="sxs-lookup"><span data-stu-id="cabe1-206">The `MustUnderstand` attribute specifies whether the node processing the header must understand it.</span></span> <span data-ttu-id="cabe1-207">`Relay`Atribut určuje, zda má být záhlaví přeneseno do podřízených uzlů.</span><span class="sxs-lookup"><span data-stu-id="cabe1-207">The `Relay` attribute specifies whether the header is to be relayed to downstream nodes.</span></span> <span data-ttu-id="cabe1-208">Technologie WCF neprovádí žádné zpracování těchto atributů u příchozích zpráv s výjimkou `MustUnderstand` atributu, jak je uvedeno v části Správa verzí kontraktu zpráv dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="cabe1-208">WCF does not perform any processing of these attributes on incoming messages, except for the `MustUnderstand` attribute, as specified in the "Message Contract Versioning" section later in this topic.</span></span> <span data-ttu-id="cabe1-209">To však umožňuje číst a zapisovat tyto atributy podle potřeby, jako v následujícím popisu.</span><span class="sxs-lookup"><span data-stu-id="cabe1-209">However, it allows you to read and write these attributes as necessary, as in the following description.</span></span>  
  
 <span data-ttu-id="cabe1-210">Při odesílání zprávy nejsou ve výchozím nastavení vygenerovány tyto atributy.</span><span class="sxs-lookup"><span data-stu-id="cabe1-210">When sending a message, these attributes are not emitted by default.</span></span> <span data-ttu-id="cabe1-211">Můžete to změnit dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="cabe1-211">You can change this in two ways.</span></span> <span data-ttu-id="cabe1-212">Nejprve můžete staticky nastavit atributy na požadované hodnoty změnou <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A?displayProperty=nameWithType> <xref:System.ServiceModel.MessageHeaderAttribute.MustUnderstand%2A?displayProperty=nameWithType> vlastností, a <xref:System.ServiceModel.MessageHeaderAttribute.Relay%2A?displayProperty=nameWithType> , jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="cabe1-212">First, you may statically set the attributes to any desired values by changing the <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.MessageHeaderAttribute.MustUnderstand%2A?displayProperty=nameWithType>, and <xref:System.ServiceModel.MessageHeaderAttribute.Relay%2A?displayProperty=nameWithType> properties, as shown in the following code example.</span></span> <span data-ttu-id="cabe1-213">(Všimněte si, že vlastnost není k dispozici `Role` ; nastavení <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A> vlastnosti emituje `Role` atribut, pokud používáte SOAP 1,2).</span><span class="sxs-lookup"><span data-stu-id="cabe1-213">(Note that there is no `Role` property; setting the <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A> property emits the `Role` attribute if you are using SOAP 1.2).</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader(Actor="http://auditingservice.contoso.com", MustUnderstand=true)] public bool IsAudited;  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public BankingTransactionData theData;  
}  
```  
  
 <span data-ttu-id="cabe1-214">Druhý způsob, jak tyto atributy řídit, je prostřednictvím kódu dynamicky.</span><span class="sxs-lookup"><span data-stu-id="cabe1-214">The second way to control these attributes is dynamically, through code.</span></span> <span data-ttu-id="cabe1-215">Toho lze dosáhnout zabalením požadovaného typu hlavičky v <xref:System.ServiceModel.MessageHeader%601> typu (Nezapomeňte, že nepleťete tento typ s neobecnou verzí) a pomocí typu společně s <xref:System.ServiceModel.MessageHeaderAttribute> .</span><span class="sxs-lookup"><span data-stu-id="cabe1-215">You can achieve this by wrapping the desired header type in the <xref:System.ServiceModel.MessageHeader%601> type (be sure not to confuse this type with the non-generic version) and by using the type together with the <xref:System.ServiceModel.MessageHeaderAttribute>.</span></span> <span data-ttu-id="cabe1-216">Pak můžete použít vlastnosti v <xref:System.ServiceModel.MessageHeader%601> pro nastavení atributů SOAP, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="cabe1-216">Then, you can use properties on the <xref:System.ServiceModel.MessageHeader%601> to set the SOAP attributes, as shown in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="cabe1-217">Použijete-li jak dynamický, tak i statický mechanismus řízení, bude statické nastavení použito jako výchozí, ale lze jej později přepsat pomocí dynamického mechanismu, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="cabe1-217">If you use both the dynamic and the static control mechanisms, the static settings are used as a default but can later be overridden by using the dynamic mechanism, as shown in the following code.</span></span>  
  
```csharp  
[MessageHeader(MustUnderstand=true)] public MessageHeader<Person> documentApprover;  
// later on in the code:  
BankingTransaction bt = new BankingTransaction();  
bt.documentApprover = new MessageHeader<Person>();  
bt.documentApprover.MustUnderstand = false; // override the static default of 'true'  
```  
  
 <span data-ttu-id="cabe1-218">Vytváření opakujících se hlaviček s dynamickým ovládacím prvkem atributu je povoleno, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="cabe1-218">Creating repeated headers with dynamic attribute control is allowed, as shown in the following code.</span></span>  
  
```csharp  
[MessageHeaderArray] public MessageHeader<Person> documentApprovers[];  
```  
  
 <span data-ttu-id="cabe1-219">Na straně příjmu lze číst tyto atributy SOAP pouze v případě, že <xref:System.ServiceModel.MessageHeader%601> je třída použita pro hlavičku v typu.</span><span class="sxs-lookup"><span data-stu-id="cabe1-219">On the receiving side, reading these SOAP attributes can only be done if the <xref:System.ServiceModel.MessageHeader%601> class is used for the header in the type.</span></span> <span data-ttu-id="cabe1-220">Prohlédněte `Actor` si `Relay` vlastnosti, nebo `MustUnderstand` záhlaví <xref:System.ServiceModel.MessageHeader%601> typu, abyste zjistili nastavení atributu v přijaté zprávě.</span><span class="sxs-lookup"><span data-stu-id="cabe1-220">Examine the `Actor`, `Relay`, or `MustUnderstand` properties of a header of the <xref:System.ServiceModel.MessageHeader%601> type to discover the attribute settings on the received message.</span></span>  
  
 <span data-ttu-id="cabe1-221">Když se přijme zpráva a pak se pošle zpátky, nastavení atributu SOAP se v hlavičce tohoto typu dostanou jenom na zpáteční cestu <xref:System.ServiceModel.MessageHeader%601> .</span><span class="sxs-lookup"><span data-stu-id="cabe1-221">When a message is received and then sent back, the SOAP attribute settings only go round-trip for headers of the <xref:System.ServiceModel.MessageHeader%601> type.</span></span>  
  
## <a name="order-of-soap-body-parts"></a><span data-ttu-id="cabe1-222">Pořadí částí těla protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="cabe1-222">Order of SOAP Body Parts</span></span>  
 <span data-ttu-id="cabe1-223">V některých případech může být nutné řídit pořadí částí těla.</span><span class="sxs-lookup"><span data-stu-id="cabe1-223">In some circumstances, you may need to control the order of the body parts.</span></span> <span data-ttu-id="cabe1-224">Pořadí prvků textu je ve výchozím nastavení abecední, ale lze je ovládat pomocí <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="cabe1-224">The order of the body elements is alphabetical by default, but can be controlled by the <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="cabe1-225">Tato vlastnost má stejnou sémantiku jako <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A?displayProperty=nameWithType> vlastnost, s výjimkou chování ve scénářích dědičnosti (v kontraktech zprávy, členy základního typu základního typu nejsou řazeny před členy těla odvozeného typu).</span><span class="sxs-lookup"><span data-stu-id="cabe1-225">This property has the same semantics as the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A?displayProperty=nameWithType> property, except for the behavior in inheritance scenarios (in message contracts, base type body members are not sorted before the derived type body members).</span></span> <span data-ttu-id="cabe1-226">Další informace najdete v tématu [pořadí datových členů](data-member-order.md).</span><span class="sxs-lookup"><span data-stu-id="cabe1-226">For more information, see [Data Member Order](data-member-order.md).</span></span>  
  
 <span data-ttu-id="cabe1-227">V následujícím příkladu by se `amount` normálně nacházela jako první, protože je první abecedně.</span><span class="sxs-lookup"><span data-stu-id="cabe1-227">In the following example, `amount` would normally come first because it is first alphabetically.</span></span> <span data-ttu-id="cabe1-228"><xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A>Vlastnost však vloží do třetí pozice.</span><span class="sxs-lookup"><span data-stu-id="cabe1-228">However, the <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A> property puts it into the third position.</span></span>  
  
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
  
## <a name="message-contract-versioning"></a><span data-ttu-id="cabe1-229">Správa verzí kontraktů zpráv</span><span class="sxs-lookup"><span data-stu-id="cabe1-229">Message Contract Versioning</span></span>  
 <span data-ttu-id="cabe1-230">V některých případech může být nutné změnit kontrakty zpráv.</span><span class="sxs-lookup"><span data-stu-id="cabe1-230">Occasionally, you may need to change message contracts.</span></span> <span data-ttu-id="cabe1-231">Například nová verze vaší aplikace může do zprávy přidat další záhlaví.</span><span class="sxs-lookup"><span data-stu-id="cabe1-231">For example, a new version of your application may add an extra header to a message.</span></span> <span data-ttu-id="cabe1-232">Když pak při posílání z nové verze do starého, systém musí při přechodu na druhý směr zabývat se další hlavičkou a chybějící hlavičkou.</span><span class="sxs-lookup"><span data-stu-id="cabe1-232">Then, when sending from the new version to the old, the system must deal with an extra header, as well as a missing header when going in the other direction.</span></span>  
  
 <span data-ttu-id="cabe1-233">Pro hlavičky verzí platí následující pravidla:</span><span class="sxs-lookup"><span data-stu-id="cabe1-233">The following rules apply for versioning headers:</span></span>  
  
- <span data-ttu-id="cabe1-234">WCF neobjektí do chybějících hlaviček – odpovídající členové jsou ponecháni na jejich výchozích hodnotách.</span><span class="sxs-lookup"><span data-stu-id="cabe1-234">WCF does not object to the missing headers—the corresponding members are left at their default values.</span></span>  
  
- <span data-ttu-id="cabe1-235">WCF také ignoruje neočekávané nadbytečné hlavičky.</span><span class="sxs-lookup"><span data-stu-id="cabe1-235">WCF also ignores unexpected extra headers.</span></span> <span data-ttu-id="cabe1-236">Jedinou výjimkou z tohoto pravidla je, že pokud má navíc záhlaví `MustUnderstand` vlastnost nastavenou na `true` příchozí zprávu SOAP – v tomto případě je vyvolána výjimka, protože záhlaví, které je nutné chápat, nelze zpracovat.</span><span class="sxs-lookup"><span data-stu-id="cabe1-236">The one exception to this rule is if the extra header has a `MustUnderstand` attribute set to `true` in the incoming SOAP message—in this case, an exception is thrown because a header that must be understood cannot be processed.</span></span>  
  
 <span data-ttu-id="cabe1-237">Tělo zprávy mají podobná pravidla správy verzí – chybějící a další části těla zprávy jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="cabe1-237">Message bodies have similar versioning rules—both missing and additional message body parts are ignored.</span></span>  
  
## <a name="inheritance-considerations"></a><span data-ttu-id="cabe1-238">Otázky dědičnosti</span><span class="sxs-lookup"><span data-stu-id="cabe1-238">Inheritance Considerations</span></span>  
 <span data-ttu-id="cabe1-239">Typ kontraktu zprávy může dědit z jiného typu, pokud základní typ má také kontrakt zprávy.</span><span class="sxs-lookup"><span data-stu-id="cabe1-239">A message contract type can inherit from another type, as long as the base type also has a message contract.</span></span>  
  
 <span data-ttu-id="cabe1-240">Při vytváření nebo přístupu ke zprávě pomocí typu kontraktu zprávy, který dědí z jiných typů kontraktů zpráv, platí následující pravidla:</span><span class="sxs-lookup"><span data-stu-id="cabe1-240">When creating or accessing a message using a message contract type that inherits from other message contract types, the following rules apply:</span></span>  
  
- <span data-ttu-id="cabe1-241">Všechna záhlaví zpráv v hierarchii dědičnosti jsou shromažďována dohromady, aby bylo možné vytvořit úplnou sadu hlaviček pro zprávu.</span><span class="sxs-lookup"><span data-stu-id="cabe1-241">All of the message headers in the inheritance hierarchy are collected together to form the full set of headers for the message.</span></span>  
  
- <span data-ttu-id="cabe1-242">Všechny části těla zprávy v hierarchii dědičnosti jsou shromažďovány dohromady, aby bylo možné vytvořit úplný text zprávy.</span><span class="sxs-lookup"><span data-stu-id="cabe1-242">All of the message body parts in the inheritance hierarchy are collected together to form the full message body.</span></span> <span data-ttu-id="cabe1-243">Části těla jsou seřazené podle obvyklých pravidel řazení (podle <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> vlastnosti a pak podle abecedy), a to bez relevance na jejich místě v hierarchii dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="cabe1-243">The body parts are ordered according to the usual ordering rules (by <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> property and then alphabetical), with no relevance to their place in the inheritance hierarchy.</span></span> <span data-ttu-id="cabe1-244">Použití dědičnosti kontraktu zprávy, kde se části těla zprávy vyskytují na více úrovních stromu dědičnosti, se důrazně nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="cabe1-244">Using message contract inheritance where message body parts occur at multiple levels of the inheritance tree is strongly discouraged.</span></span> <span data-ttu-id="cabe1-245">Pokud základní třída a odvozená třída definuje záhlaví nebo část těla se stejným názvem, člen z třídy Base-nejvíc se použije k uložení hodnoty této hlavičky nebo části těla.</span><span class="sxs-lookup"><span data-stu-id="cabe1-245">If a base class and a derived class define a header or a body part with the same name, the member from the base-most class is used to store the value of that header or body part.</span></span>  
  
 <span data-ttu-id="cabe1-246">Vezměte v úvahu třídy v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="cabe1-246">Consider the classes in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="cabe1-247">`PatientRecord`Třída popisuje zprávu s názvem s jednou hlavičkou `ID` .</span><span class="sxs-lookup"><span data-stu-id="cabe1-247">The `PatientRecord` class describes a message with one header called `ID`.</span></span> <span data-ttu-id="cabe1-248">Hlavička odpovídá `personID` `patientID` členu a nikoli členovi, protože je vybrán člen nejvíce Base.</span><span class="sxs-lookup"><span data-stu-id="cabe1-248">The header corresponds to the `personID` and not the `patientID` member, because the base-most member is chosen.</span></span> <span data-ttu-id="cabe1-249">Proto `patientID` je pole v tomto případě nepoužitelné.</span><span class="sxs-lookup"><span data-stu-id="cabe1-249">Thus, the `patientID` field is useless in this case.</span></span> <span data-ttu-id="cabe1-250">Tělo zprávy obsahuje `diagnosis` element následovaný `patientName` elementem, protože to je abecední pořadí.</span><span class="sxs-lookup"><span data-stu-id="cabe1-250">The body of the message contains the `diagnosis` element followed by the `patientName` element, because that is the alphabetical order.</span></span> <span data-ttu-id="cabe1-251">Všimněte si, že příklad ukazuje vzor, který se důrazně nedoporučuje: základem i odvozených kontraktů zpráv jsou části těla zprávy.</span><span class="sxs-lookup"><span data-stu-id="cabe1-251">Notice that the example shows a pattern that is strongly discouraged: both the base and the derived message contracts have message body parts.</span></span>  
  
## <a name="wsdl-considerations"></a><span data-ttu-id="cabe1-252">WSDL – požadavky</span><span class="sxs-lookup"><span data-stu-id="cabe1-252">WSDL Considerations</span></span>  
 <span data-ttu-id="cabe1-253">Při generování kontraktu jazyka WSDL (Web Services Description Language) ze služby, která používá kontrakty zpráv, je důležité si uvědomit, že ne všechny funkce kontraktu zprávy se odrazí ve výsledném WSDL.</span><span class="sxs-lookup"><span data-stu-id="cabe1-253">When generating a Web Services Description Language (WSDL) contract from a service that uses message contracts, it is important to remember that not all message contract features are reflected in the resulting WSDL.</span></span> <span data-ttu-id="cabe1-254">Vezměte v úvahu následující body:</span><span class="sxs-lookup"><span data-stu-id="cabe1-254">Consider the following points:</span></span>  
  
- <span data-ttu-id="cabe1-255">WSDL nemůže vyjádřit koncept pole hlaviček.</span><span class="sxs-lookup"><span data-stu-id="cabe1-255">WSDL cannot express the concept of an array of headers.</span></span> <span data-ttu-id="cabe1-256">Při vytváření zpráv s polem hlaviček pomocí <xref:System.ServiceModel.MessageHeaderArrayAttribute> , výsledné WSDL odráží pouze jedno záhlaví místo pole.</span><span class="sxs-lookup"><span data-stu-id="cabe1-256">When creating messages with an array of headers using the <xref:System.ServiceModel.MessageHeaderArrayAttribute>, the resulting WSDL reflects only one header instead of the array.</span></span>  
  
- <span data-ttu-id="cabe1-257">Výsledný dokument WSDL nemusí odrážet některé informace na úrovni ochrany.</span><span class="sxs-lookup"><span data-stu-id="cabe1-257">The resulting WSDL document may not reflect some protection-level information.</span></span>  
  
- <span data-ttu-id="cabe1-258">Typ zprávy generovaný v jazyce WSDL má stejný název jako název třídy typu kontraktu zprávy.</span><span class="sxs-lookup"><span data-stu-id="cabe1-258">The message type generated in the WSDL has the same name as the class name of the message contract type.</span></span>  
  
- <span data-ttu-id="cabe1-259">Při použití stejné kontraktu zprávy ve více operacích se v dokumentu WSDL generuje více typů zpráv.</span><span class="sxs-lookup"><span data-stu-id="cabe1-259">When using the same message contract in multiple operations, multiple message types are generated in the WSDL document.</span></span> <span data-ttu-id="cabe1-260">Názvy jsou jedinečné přidáním čísel "2", "3" atd. "pro následné použití.</span><span class="sxs-lookup"><span data-stu-id="cabe1-260">The names are made unique by adding the numbers "2", "3", and so on, for subsequent uses.</span></span> <span data-ttu-id="cabe1-261">Při importu zpět WSDL se vytvoří více typů kontraktů zpráv a jsou identické, s výjimkou jejich názvů.</span><span class="sxs-lookup"><span data-stu-id="cabe1-261">When importing back the WSDL, multiple message contract types are created and are identical except for their names.</span></span>  
  
## <a name="soap-encoding-considerations"></a><span data-ttu-id="cabe1-262">Požadavky na kódování SOAP</span><span class="sxs-lookup"><span data-stu-id="cabe1-262">SOAP Encoding Considerations</span></span>  
 <span data-ttu-id="cabe1-263">WCF vám umožňuje používat starší styly kódování protokolu SOAP XML, ale jeho použití se nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="cabe1-263">WCF allows you to use the legacy SOAP encoding style of XML, however, its use is not recommended.</span></span> <span data-ttu-id="cabe1-264">Při použití tohoto stylu (nastavením `Use` vlastnosti na hodnotu `Encoded` v případě <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType> použití pro kontrakt služby) platí následující další požadavky:</span><span class="sxs-lookup"><span data-stu-id="cabe1-264">When using this style (by setting the `Use` property to `Encoded` on the <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType> applied to the service contract), the following additional considerations apply:</span></span>  
  
- <span data-ttu-id="cabe1-265">Hlavičky zpráv nejsou podporovány. To znamená, že atribut <xref:System.ServiceModel.MessageHeaderAttribute> a atribut array <xref:System.ServiceModel.MessageHeaderArrayAttribute> jsou nekompatibilní s kódováním SOAP.</span><span class="sxs-lookup"><span data-stu-id="cabe1-265">The message headers are not supported; this means that the attribute <xref:System.ServiceModel.MessageHeaderAttribute> and the array attribute <xref:System.ServiceModel.MessageHeaderArrayAttribute> are incompatible with SOAP encoding.</span></span>  
  
- <span data-ttu-id="cabe1-266">Pokud není kontrakt zprávy zabalený, to znamená, že pokud je vlastnost <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> nastavená na hodnotu `false` , kontrakt zprávy může mít jenom jednu část těla.</span><span class="sxs-lookup"><span data-stu-id="cabe1-266">If the message contract is not wrapped, that is, if the property <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> is set to `false`, the message contract can have only one body part.</span></span>  
  
- <span data-ttu-id="cabe1-267">Název prvku obálky pro kontrakt zprávy požadavku musí odpovídat názvu operace.</span><span class="sxs-lookup"><span data-stu-id="cabe1-267">The name of the wrapper element for the request message contract must match the operation name.</span></span> <span data-ttu-id="cabe1-268">`WrapperName`Pro tuto zprávu použijte vlastnost kontraktu zprávy.</span><span class="sxs-lookup"><span data-stu-id="cabe1-268">Use the `WrapperName` property of the message contract for this.</span></span>  
  
- <span data-ttu-id="cabe1-269">Název prvku obálky pro kontrakt zprávy odpovědi musí být stejný jako název operace s příponou Response.</span><span class="sxs-lookup"><span data-stu-id="cabe1-269">The name of the wrapper element for the response message contract must be the same as the name of the operation suffixed by 'Response'.</span></span> <span data-ttu-id="cabe1-270"><xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A>Pro tuto zprávu použijte vlastnost kontraktu zprávy.</span><span class="sxs-lookup"><span data-stu-id="cabe1-270">Use the <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> property of the message contract for this.</span></span>  
  
- <span data-ttu-id="cabe1-271">Kódování SOAP zachovává odkazy na objekty.</span><span class="sxs-lookup"><span data-stu-id="cabe1-271">SOAP encoding preserves object references.</span></span> <span data-ttu-id="cabe1-272">Zvažte například následující kód.</span><span class="sxs-lookup"><span data-stu-id="cabe1-272">For example, consider the following code.</span></span>  
  
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
  
 <span data-ttu-id="cabe1-273">Po serializaci zprávy pomocí kódování SOAP `changedFrom` a `changedTo` neobsahují své vlastní kopie `p` , ale místo toho, aby odkazovala na kopii uvnitř `changedBy` elementu.</span><span class="sxs-lookup"><span data-stu-id="cabe1-273">After serializing the message using SOAP encoding, `changedFrom` and `changedTo` do not contain their own copies of `p`, but instead point to the copy inside the `changedBy` element.</span></span>  
  
## <a name="performance-considerations"></a><span data-ttu-id="cabe1-274">Faktory ovlivňující výkon</span><span class="sxs-lookup"><span data-stu-id="cabe1-274">Performance Considerations</span></span>  
 <span data-ttu-id="cabe1-275">Každé záhlaví zprávy a část těla zprávy jsou serializovány nezávisle na ostatních.</span><span class="sxs-lookup"><span data-stu-id="cabe1-275">Every message header and message body part is serialized independently of the others.</span></span> <span data-ttu-id="cabe1-276">Proto je možné stejné obory názvů deklarovat znovu pro každou hlavičku a část těla.</span><span class="sxs-lookup"><span data-stu-id="cabe1-276">Therefore, the same namespaces can be declared again for each header and body part.</span></span> <span data-ttu-id="cabe1-277">Chcete-li zvýšit výkon, zejména v souvislosti s velikostí zprávy na lince, konsolidovat více částí záhlaví a částí těla do jedné hlavičky nebo části těla.</span><span class="sxs-lookup"><span data-stu-id="cabe1-277">To improve performance, especially in terms of the size of the message on the wire, consolidate multiple headers and body parts into a single header or body part.</span></span> <span data-ttu-id="cabe1-278">Například namísto následujícího kódu:</span><span class="sxs-lookup"><span data-stu-id="cabe1-278">For example, instead of the following code:</span></span>  
  
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
  
 <span data-ttu-id="cabe1-279">Použijte tento kód.</span><span class="sxs-lookup"><span data-stu-id="cabe1-279">Use this code.</span></span>  
  
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
  
### <a name="event-based-asynchronous-and-message-contracts"></a><span data-ttu-id="cabe1-280">Asynchronní události a kontrakty zpráv založené na událostech</span><span class="sxs-lookup"><span data-stu-id="cabe1-280">Event-based Asynchronous and Message Contracts</span></span>  
 <span data-ttu-id="cabe1-281">Pokyny pro návrh pro stav asynchronního modelu založeného na událostech, pokud je vrácena více než jedna hodnota, jako vlastnost se vrátí jedna hodnota `Result` a ostatní jsou vráceny jako vlastnosti <xref:System.EventArgs> objektu.</span><span class="sxs-lookup"><span data-stu-id="cabe1-281">The design guidelines for the event-based asynchronous model state that if more than one value is returned, one value is returned as the `Result` property and the others are returned as properties on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="cabe1-282">Jedním z těchto výsledků je, že pokud klient Importuje metadata pomocí parametrů asynchronního příkazu založeného na událostech a operace vrátí více než jednu hodnotu, výchozí <xref:System.EventArgs> objekt vrátí jednu hodnotu jako `Result` vlastnost a zbytek je vlastnosti <xref:System.EventArgs> objektu.</span><span class="sxs-lookup"><span data-stu-id="cabe1-282">One result of this is that if a client imports metadata using the event-based asynchronous command options and the operation returns more than one value, the default <xref:System.EventArgs> object returns one value as the `Result` property and the remainder are properties of the <xref:System.EventArgs> object.</span></span>  
  
 <span data-ttu-id="cabe1-283">Pokud chcete jako vlastnost přijmout objekt zprávy `Result` a vracet hodnoty jako vlastnosti tohoto objektu, použijte `/messageContract` možnost Command.</span><span class="sxs-lookup"><span data-stu-id="cabe1-283">If you want to receive the message object as the `Result` property and have the returned values as properties on that object, use the `/messageContract` command option.</span></span> <span data-ttu-id="cabe1-284">Tím se vygeneruje podpis, který vrátí zprávu odpovědi jako `Result` vlastnost <xref:System.EventArgs> objektu.</span><span class="sxs-lookup"><span data-stu-id="cabe1-284">This generates a signature that returns the response message as the `Result` property on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="cabe1-285">Všechny interní návratové hodnoty jsou potom vlastnostmi objektu zprávy odpovědi.</span><span class="sxs-lookup"><span data-stu-id="cabe1-285">All internal return values are then properties of the response message object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cabe1-286">Viz také</span><span class="sxs-lookup"><span data-stu-id="cabe1-286">See also</span></span>

- [<span data-ttu-id="cabe1-287">Použití kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="cabe1-287">Using Data Contracts</span></span>](using-data-contracts.md)
- [<span data-ttu-id="cabe1-288">Navrhování a implementace služeb</span><span class="sxs-lookup"><span data-stu-id="cabe1-288">Designing and Implementing Services</span></span>](../designing-and-implementing-services.md)
