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
ms.workload: dotnet
ms.openlocfilehash: db19b5188c98d157b98d65422ee38d4ed59f733a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="using-message-contracts"></a><span data-ttu-id="81980-102">Použití kontraktů zpráv</span><span class="sxs-lookup"><span data-stu-id="81980-102">Using Message Contracts</span></span>
<span data-ttu-id="81980-103">Obvykle při sestavování [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] aplikací vývojáři zaměřit se na datové struktury a serializace problémy a nemusíte sami se týkají se strukturou zpráv, ve kterých se přenášejí data.</span><span class="sxs-lookup"><span data-stu-id="81980-103">Typically when building [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] applications, developers pay close attention to the data structures and serialization issues and do not need to concern themselves with the structure of the messages in which the data is carried.</span></span> <span data-ttu-id="81980-104">Pro tyto aplikace je jednoduchá vytváření kontrakty dat pro parametry nebo návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="81980-104">For these applications, creating data contracts for the parameters or return values is straightforward.</span></span> <span data-ttu-id="81980-105">([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Zadání přenos dat v kontraktech služby](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).)</span><span class="sxs-lookup"><span data-stu-id="81980-105">([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Specifying Data Transfer in Service Contracts](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).)</span></span>  
  
 <span data-ttu-id="81980-106">Někdy úplnou kontrolu nad strukturou zprávu protokolu SOAP se ale stejně důležité jako kontrolu nad jeho obsah.</span><span class="sxs-lookup"><span data-stu-id="81980-106">However, sometimes complete control over the structure of a SOAP message is just as important as control over its contents.</span></span> <span data-ttu-id="81980-107">To platí hlavně při interoperability je důležité, nebo přímo řídit zabezpečení problémy na úrovni zprávě, nebo část zprávy.</span><span class="sxs-lookup"><span data-stu-id="81980-107">This is especially true when interoperability is important or to specifically control security issues at the level of the message or message part.</span></span> <span data-ttu-id="81980-108">V těchto případech můžete vytvořit *kontrakt zprávy* , můžete určit strukturu vyžaduje přesné protokolu SOAP zprávy.</span><span class="sxs-lookup"><span data-stu-id="81980-108">In these cases, you can create a *message contract* that enables you to specify the structure of the precise SOAP message required.</span></span>  
  
 <span data-ttu-id="81980-109">Toto téma popisuje postup vytvoření kontraktu zprávy specifické pro vaši operaci pomocí různých atributů kontrakt zprávy.</span><span class="sxs-lookup"><span data-stu-id="81980-109">This topic discusses how to use the various message contract attributes to create a specific message contract for your operation.</span></span>  
  
## <a name="using-message-contracts-in-operations"></a><span data-ttu-id="81980-110">Použití kontraktů zpráv v operacích</span><span class="sxs-lookup"><span data-stu-id="81980-110">Using Message Contracts in Operations</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="81980-111">podporuje operace vymodelován buď *vzdálených volání (procedur RPC) styl* nebo *zasílání zpráv styl*.</span><span class="sxs-lookup"><span data-stu-id="81980-111"> supports operations modeled on either the *remote procedure call (RPC) style* or the *messaging style*.</span></span> <span data-ttu-id="81980-112">V operaci stylu RPC, můžete použít jakýkoli serializovatelný typ, a máte přístup k funkcím, které jsou k dispozici pro místní volání, jako například několik parametrů a `ref` a `out` parametry.</span><span class="sxs-lookup"><span data-stu-id="81980-112">In an RPC-style operation, you can use any serializable type, and you have access to the features that are available to local calls, such as multiple parameters and `ref` and `out` parameters.</span></span> <span data-ttu-id="81980-113">V tomto stylu forma serializace vybrali řídí strukturu dat v podkladové zprávy a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] runtime vytvoří zprávy pro podporu operaci.</span><span class="sxs-lookup"><span data-stu-id="81980-113">In this style, the form of serialization chosen controls the structure of the data in the underlying messages, and the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] runtime creates the messages to support the operation.</span></span> <span data-ttu-id="81980-114">Díky tomu mohou vývojáři, kteří se s protokolu SOAP a SOAP zprávy a pokuste se rychle a snadno vytvořit a používat aplikace služby.</span><span class="sxs-lookup"><span data-stu-id="81980-114">This enables developers who are not familiar with SOAP and SOAP messages to quickly and easily create and use service applications.</span></span>  
  
 <span data-ttu-id="81980-115">Následující příklad kódu ukazuje operace služby modelován na styl RPC.</span><span class="sxs-lookup"><span data-stu-id="81980-115">The following code example shows a service operation modeled on the RPC style.</span></span>  
  
```csharp  
[OperationContract]  
public BankingTransactionResponse PostBankingTransaction(BankingTransaction bt);  
```  
  
 <span data-ttu-id="81980-116">Za normálních okolností kontraktu dat stačí definovat schéma pro zprávy.</span><span class="sxs-lookup"><span data-stu-id="81980-116">Normally, a data contract is sufficient to define the schema for the messages.</span></span> <span data-ttu-id="81980-117">Například v předchozím příkladu je dostatečné pro většinu aplikací Pokud `BankingTransaction` a `BankingTransactionResponse` mít kontrakty dat zadat obsah základní protokolu SOAP zprávy.</span><span class="sxs-lookup"><span data-stu-id="81980-117">For instance, in the preceding example, it is sufficient for most applications if `BankingTransaction` and `BankingTransactionResponse` have data contracts to define the contents of the underlying SOAP messages.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="81980-118">kontrakty dat najdete v části [pomocí kontrakty dat](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="81980-118"> data contracts, see [Using Data Contracts](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span></span>  
  
 <span data-ttu-id="81980-119">Ale někdy je nezbytné přesně řídit, jak strukturu zprávu SOAP odeslány prostřednictvím sítě.</span><span class="sxs-lookup"><span data-stu-id="81980-119">However, occasionally it is necessary to precisely control how the structure of the SOAP message transmitted over the wire.</span></span> <span data-ttu-id="81980-120">Nejběžnější scénáře je vkládání vlastní hlavičky SOAP.</span><span class="sxs-lookup"><span data-stu-id="81980-120">The most common scenario for this is inserting custom SOAP headers.</span></span> <span data-ttu-id="81980-121">Další z typických možností je definovat vlastnosti zabezpečení pro záhlaví zprávy a text, který je, a rozhodnout, zda tyto prvky jsou digitálně podepsat a zašifrovat.</span><span class="sxs-lookup"><span data-stu-id="81980-121">Another common scenario is to define security properties for the message's headers and body, that is, to decide whether these elements are digitally signed and encrypted.</span></span> <span data-ttu-id="81980-122">Nakonec vyžadují zásobníky některých třetích stran protokolu SOAP zprávy se v určitém formátu.</span><span class="sxs-lookup"><span data-stu-id="81980-122">Finally, some third-party SOAP stacks require messages be in a specific format.</span></span> <span data-ttu-id="81980-123">Zasílání zpráv ve stylu operations zadejte tento ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="81980-123">Messaging-style operations provide this control.</span></span>  
  
 <span data-ttu-id="81980-124">Zasílání zpráv ve stylu operace obsahuje maximálně jeden parametr a jeden návratovou hodnotu kde oba typy jsou typy zpráv; To znamená že serializovat přímo do zadané struktury zprávu protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="81980-124">A messaging-style operation has at most one parameter and one return value where both types are message types; that is, they serialize directly into a specified SOAP message structure.</span></span> <span data-ttu-id="81980-125">To může být jakéhokoli typu označené jako <xref:System.ServiceModel.MessageContractAttribute> nebo <xref:System.ServiceModel.Channels.Message> typu.</span><span class="sxs-lookup"><span data-stu-id="81980-125">This may be any type marked with the <xref:System.ServiceModel.MessageContractAttribute> or the <xref:System.ServiceModel.Channels.Message> type.</span></span> <span data-ttu-id="81980-126">Následující příklad kódu ukazuje operace podobná předchozí RCP stylu, ale styl zasílání zpráv, který používá.</span><span class="sxs-lookup"><span data-stu-id="81980-126">The following code example shows an operation similar to the preceding RCP-style, but which uses the messaging style.</span></span>  
  
 <span data-ttu-id="81980-127">Například pokud `BankingTransaction` a `BankingTransactionResponse` se oba typy, které jsou kontrakty zpráv, pak kód v následující operace je platná.</span><span class="sxs-lookup"><span data-stu-id="81980-127">For example, if `BankingTransaction` and `BankingTransactionResponse` are both types that are message contracts, then the code in the following operations is valid.</span></span>  
  
```csharp  
[OperationContract]  
BankingTransactionResponse Process(BankingTransaction bt);  
[OperationContract]  
void Store(BankingTransaction bt);  
[OperationContract]  
BankingTransactionResponse GetResponse();  
```  
  
 <span data-ttu-id="81980-128">Následující kód je však neplatný.</span><span class="sxs-lookup"><span data-stu-id="81980-128">However, the following code is invalid.</span></span>  
  
```csharp  
[OperationContract]  
bool Validate(BankingTransaction bt);  
// Invalid, the return type is not a message contract.  
[OperationContract]  
void Reconcile(BankingTransaction bt1, BankingTransaction bt2);  
// Invalid, there is more than one parameter.  
```  
  
 <span data-ttu-id="81980-129">Pro žádnou operaci, která zahrnuje typ kontrakt zprávy a není, použijte jednu z platných vzorů je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="81980-129">An exception is thrown for any operation that involves a message contract type and that does not follow one of the valid patterns.</span></span> <span data-ttu-id="81980-130">Tato omezení operací, které nezahrnují typy kontraktů zpráv samozřejmě se nevztahuje.</span><span class="sxs-lookup"><span data-stu-id="81980-130">Of course, operations that do not involve message contract types are not subject to these restrictions.</span></span>  
  
 <span data-ttu-id="81980-131">Pokud typ kontrakt zprávy a kontraktu dat, jenom jeho kontrakt zprávy považuje, pokud typ se používá v operaci.</span><span class="sxs-lookup"><span data-stu-id="81980-131">If a type has both a message contract and a data contract, only its message contract is considered when the type is used in an operation.</span></span>  
  
## <a name="defining-message-contracts"></a><span data-ttu-id="81980-132">Definování kontraktů zpráv</span><span class="sxs-lookup"><span data-stu-id="81980-132">Defining Message Contracts</span></span>  
 <span data-ttu-id="81980-133">Chcete-li definovat kontrakt zprávy pro typ (to znamená, definovat mapování mezi typem a obálku protokolu SOAP), použít <xref:System.ServiceModel.MessageContractAttribute> typu.</span><span class="sxs-lookup"><span data-stu-id="81980-133">To define a message contract for a type (that is, to define the mapping between the type and a SOAP envelope), apply the <xref:System.ServiceModel.MessageContractAttribute> to the type.</span></span> <span data-ttu-id="81980-134">Následně použít <xref:System.ServiceModel.MessageHeaderAttribute> těmto členům typ, který chcete provést do záhlaví SOAP a použít <xref:System.ServiceModel.MessageBodyMemberAttribute> těmto členům chcete, aby se do části těla protokolu SOAP zprávy.</span><span class="sxs-lookup"><span data-stu-id="81980-134">Then apply the <xref:System.ServiceModel.MessageHeaderAttribute> to those members of the type you want to make into SOAP headers, and apply the <xref:System.ServiceModel.MessageBodyMemberAttribute> to those members you want to make into parts of the SOAP body of the message.</span></span>  
  
 <span data-ttu-id="81980-135">Následující kód představuje příklad použití kontrakt zprávy.</span><span class="sxs-lookup"><span data-stu-id="81980-135">The following code provides an example of using a message contract.</span></span>  
  
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
  
 <span data-ttu-id="81980-136">Při použití tohoto typu jako parametr operace, je vygenerována následující obálku protokolu SOAP:</span><span class="sxs-lookup"><span data-stu-id="81980-136">When using this type as an operation parameter, the following SOAP envelope is generated:</span></span>  
  
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
  
 <span data-ttu-id="81980-137">Všimněte si, že `operation` a `transactionDate` zobrazí jako hlavičky SOAP a těla protokolu SOAP se skládá z element obálky `BankingTransaction` obsahující `sourceAccount`,`targetAccount`, a `amount`.</span><span class="sxs-lookup"><span data-stu-id="81980-137">Notice that `operation` and `transactionDate` appear as SOAP headers and the SOAP body consists of a wrapper element `BankingTransaction` containing `sourceAccount`,`targetAccount`, and `amount`.</span></span>  
  
 <span data-ttu-id="81980-138">Můžete použít <xref:System.ServiceModel.MessageHeaderAttribute> a <xref:System.ServiceModel.MessageBodyMemberAttribute> do všech polí, vlastnosti a události, bez ohledu na to, zda jsou veřejné, privátní, chráněný nebo interní.</span><span class="sxs-lookup"><span data-stu-id="81980-138">You can apply the <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> to all fields, properties, and events, regardless of whether they are public, private, protected, or internal.</span></span>  
  
 <span data-ttu-id="81980-139"><xref:System.ServiceModel.MessageContractAttribute> Vám umožní určit WrapperName a WrapperNamespace atributy, které řídí název elementu obálku v těle protokolu SOAP zprávy.</span><span class="sxs-lookup"><span data-stu-id="81980-139">The <xref:System.ServiceModel.MessageContractAttribute> allows you to specify the WrapperName and WrapperNamespace attributes which control the name of the wrapper element in the body of the SOAP message.</span></span> <span data-ttu-id="81980-140">Ve výchozím nastavení název kontrakt zprávy typ se používá pro obálku a oboru názvů, ve kterém je definovaný kontrakt zprávy `HYPERLINK "http://tempuri.org/" http://tempuri.org/` se používá jako výchozí obor názvů.</span><span class="sxs-lookup"><span data-stu-id="81980-140">By default the name of the message contract type is used for the wrapper and the namespace in which the message contract is defined  `HYPERLINK "http://tempuri.org/" http://tempuri.org/` is used as the default namespace.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="81980-141"><xref:System.Runtime.Serialization.KnownTypeAttribute>atributy se ignorují v kontrakty zpráv.</span><span class="sxs-lookup"><span data-stu-id="81980-141"><xref:System.Runtime.Serialization.KnownTypeAttribute> attributes are ignored in message contracts.</span></span> <span data-ttu-id="81980-142">Pokud <xref:System.Runtime.Serialization.KnownTypeAttribute> je potřeba, umístěte ji na operaci, která používá kontrakt zprávy nejistá.</span><span class="sxs-lookup"><span data-stu-id="81980-142">If a <xref:System.Runtime.Serialization.KnownTypeAttribute> is required, place it on the operation that is using the message contract in question.</span></span>  
  
## <a name="controlling-header-and-body-part-names-and-namespaces"></a><span data-ttu-id="81980-143">Řízení záhlaví a názvům součástí textu a obory názvů</span><span class="sxs-lookup"><span data-stu-id="81980-143">Controlling Header and Body Part Names and Namespaces</span></span>  
 <span data-ttu-id="81980-144">V protokolu SOAP reprezentace kontrakt zprávy každou část záhlaví a text mapuje na element XML, který má název a obor názvů.</span><span class="sxs-lookup"><span data-stu-id="81980-144">In the SOAP representation of a message contract, each header and body part maps to an XML element that has a name and a namespace.</span></span>  
  
 <span data-ttu-id="81980-145">Ve výchozím nastavení, obor názvů je stejný jako obor názvů kontraktu služby, který se účastní zprávu, a název je dáno název člena, ke kterému <xref:System.ServiceModel.MessageHeaderAttribute> nebo <xref:System.ServiceModel.MessageBodyMemberAttribute> jsou použity atributy.</span><span class="sxs-lookup"><span data-stu-id="81980-145">By default, the namespace is the same as the namespace of the service contract that the message is participating in, and the name is determined by the member name to which the <xref:System.ServiceModel.MessageHeaderAttribute> or the <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes are applied.</span></span>  
  
 <span data-ttu-id="81980-146">Tato výchozí nastavení můžete změnit manipulace s <xref:System.ServiceModel.MessageContractMemberAttribute.Name%2A?displayProperty=nameWithType> a <xref:System.ServiceModel.MessageContractMemberAttribute.Namespace%2A?displayProperty=nameWithType> (na nadřazenou třídu <xref:System.ServiceModel.MessageHeaderAttribute> a <xref:System.ServiceModel.MessageBodyMemberAttribute> atributy).</span><span class="sxs-lookup"><span data-stu-id="81980-146">You can change these defaults by manipulating the <xref:System.ServiceModel.MessageContractMemberAttribute.Name%2A?displayProperty=nameWithType> and <xref:System.ServiceModel.MessageContractMemberAttribute.Namespace%2A?displayProperty=nameWithType> (on the parent class of the <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes).</span></span>  
  
 <span data-ttu-id="81980-147">Vezměte v úvahu třídy v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="81980-147">Consider the class in the following code example.</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageHeader(Namespace="http://schemas.contoso.com/auditing/2005")] public bool IsAudited;  
  [MessageBodyMember(Name="transactionData")] public BankingTransactionData theData;  
}  
```  
  
 <span data-ttu-id="81980-148">V tomto příkladu `IsAudited` záhlaví je v oboru názvů zadaný v kódu a část textu, který představuje `theData` člen je reprezentována element XML s názvem `transactionData`.</span><span class="sxs-lookup"><span data-stu-id="81980-148">In this example, the `IsAudited` header is in the namespace specified in the code, and the body part that represents the `theData` member is represented by an XML element with the name `transactionData`.</span></span> <span data-ttu-id="81980-149">Následující obrázek znázorňuje XML vygenerovat pro tento kontrakt zprávy.</span><span class="sxs-lookup"><span data-stu-id="81980-149">The following shows the XML generated for this message contract.</span></span>  
  
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
  
## <a name="controlling-whether-the-soap-body-parts-are-wrapped"></a><span data-ttu-id="81980-150">Řízení, zda jsou zabalené částí textu protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="81980-150">Controlling Whether the SOAP Body Parts Are Wrapped</span></span>  
 <span data-ttu-id="81980-151">Ve výchozím nastavení jsou do zabalené elementu serializovat částí textu protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="81980-151">By default, the SOAP body parts are serialized inside a wrapped element.</span></span> <span data-ttu-id="81980-152">Například následující kód ukazuje `HelloGreetingMessage` element obálky generované z názvu <xref:System.ServiceModel.MessageContractAttribute> typu v kontrakt zprávy pro `HelloGreetingMessage` zprávy.</span><span class="sxs-lookup"><span data-stu-id="81980-152">For example, the following code shows the `HelloGreetingMessage` wrapper element generated from the name of the <xref:System.ServiceModel.MessageContractAttribute> type in the message contract for the `HelloGreetingMessage` message.</span></span>  
  
 [!code-csharp[MessageHeaderAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/messageheaderattribute/cs/services.cs#3)]
 [!code-vb[MessageHeaderAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/messageheaderattribute/vb/services.vb#3)]  
  
 <span data-ttu-id="81980-153">Chcete-li potlačit element obálky, nastavte <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="81980-153">To suppress the wrapper element, set the <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> property to `false`.</span></span> <span data-ttu-id="81980-154">Chcete-li řídit název a obor názvů elementu obálky, použijte <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> a <xref:System.ServiceModel.MessageContractAttribute.WrapperNamespace%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="81980-154">To control the name and the namespace of the wrapper element, use the <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> and <xref:System.ServiceModel.MessageContractAttribute.WrapperNamespace%2A> properties.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="81980-155">S více než jednu část textu zprávy ve zprávy, které nejsou zabalené není kompatibilní s WS-I Basic Profile 1.1 a nedoporučuje při návrhu nové kontrakty zpráv.</span><span class="sxs-lookup"><span data-stu-id="81980-155">Having more than one message body part in messages that are not wrapped is not compliant with WS-I Basic Profile 1.1 and is not recommended when designing new message contracts.</span></span> <span data-ttu-id="81980-156">Však může být potřeba mít více než jednu část textu rozbalenou zprávy v některých scénářích konkrétní interoperability.</span><span class="sxs-lookup"><span data-stu-id="81980-156">However, it may be necessary to have more than one unwrapped message body part in certain specific interoperability scenarios.</span></span> <span data-ttu-id="81980-157">Pokud budete přenášet více než jeden prvek dat text zprávy, se doporučuje použít režim výchozí (zabalená).</span><span class="sxs-lookup"><span data-stu-id="81980-157">If you are going to transmit more than one piece of data in a message body, it is recommended to use the default (wrapped) mode.</span></span> <span data-ttu-id="81980-158">S více než jeden záhlaví zprávy ve nerozbalené zprávy je zcela přijatelné.</span><span class="sxs-lookup"><span data-stu-id="81980-158">Having more than one message header in unwrapped messages is completely acceptable.</span></span>  
  
## <a name="using-custom-types-inside-message-contracts"></a><span data-ttu-id="81980-159">Pomocí vlastních typů uvnitř kontrakty zpráv</span><span class="sxs-lookup"><span data-stu-id="81980-159">Using Custom Types Inside Message Contracts</span></span>  
 <span data-ttu-id="81980-160">Každý záhlaví jednotlivé zprávy a část textu zprávy je serializováno (převedena na XML) pomocí zvolené Serializační stroj pro kontrakt služby, které zprávy se používá.</span><span class="sxs-lookup"><span data-stu-id="81980-160">Each individual message header and message body part is serialized (turned into XML) using the chosen serialization engine for the service contract where the message is used.</span></span> <span data-ttu-id="81980-161">Výchozí serializace modul, `XmlFormatter`, může zpracovat žádný typ, který má kontraktu dat, buď explicitně (tak, že <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType>) nebo implicitně (tím se primitivní typ, které mají <xref:System.SerializableAttribute?displayProperty=nameWithType>a tak dále).</span><span class="sxs-lookup"><span data-stu-id="81980-161">The default serialization engine, the `XmlFormatter`, can handle any type that has a data contract, either explicitly (by having the <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType>) or implicitly (by being a primitive type, having the <xref:System.SerializableAttribute?displayProperty=nameWithType>, and so on).</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="81980-162">[Použití kontraktů dat](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="81980-162"> [Using Data Contracts](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span></span>  
  
 <span data-ttu-id="81980-163">V předchozím příkladu `Operation` a `BankingTransactionData` typy musí mít kontraktu dat a `transactionDate` serializovat protože <xref:System.DateTime> jednoduchého typu (a tak má kontrakt implicitní dat).</span><span class="sxs-lookup"><span data-stu-id="81980-163">In the preceding example, the `Operation` and `BankingTransactionData` types must have a data contract, and `transactionDate` is serializable because <xref:System.DateTime> is a primitive (and so has an implicit data contract).</span></span>  
  
 <span data-ttu-id="81980-164">Je však možné přepnout na jiný Serializační stroj, `XmlSerializer`.</span><span class="sxs-lookup"><span data-stu-id="81980-164">However, it is possible to switch to a different serialization engine, the `XmlSerializer`.</span></span> <span data-ttu-id="81980-165">Pokud provedete tyto přepínače, je nutné zajistit, že všechny typy používané pro záhlaví zprávy a částí textu jsou serializovatelný pomocí `XmlSerializer`.</span><span class="sxs-lookup"><span data-stu-id="81980-165">If you make such a switch, you should ensure that all of the types used for message headers and body parts are serializable using the `XmlSerializer`.</span></span>  
  
## <a name="using-arrays-inside-message-contracts"></a><span data-ttu-id="81980-166">Použití polí uvnitř kontrakty zpráv</span><span class="sxs-lookup"><span data-stu-id="81980-166">Using Arrays Inside Message Contracts</span></span>  
 <span data-ttu-id="81980-167">Můžete použít pole opakovaných elementů v kontrakty zpráv dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="81980-167">You can use arrays of repeating elements in message contracts in two ways.</span></span>  
  
 <span data-ttu-id="81980-168">První je použití <xref:System.ServiceModel.MessageHeaderAttribute> nebo <xref:System.ServiceModel.MessageBodyMemberAttribute> přímo na pole.</span><span class="sxs-lookup"><span data-stu-id="81980-168">The first is to use a <xref:System.ServiceModel.MessageHeaderAttribute> or a <xref:System.ServiceModel.MessageBodyMemberAttribute> directly on the array.</span></span> <span data-ttu-id="81980-169">V takovém případě je jako jeden element (to znamená, jeden záhlaví nebo jednu část textu) s více podřízených elementů serializováno celé pole.</span><span class="sxs-lookup"><span data-stu-id="81980-169">In this case, the entire array is serialized as one element (that is, one header or one body part) with multiple child elements.</span></span> <span data-ttu-id="81980-170">Vezměte v úvahu třídy v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="81980-170">Consider the class in the following example.</span></span>  
  
```csharp  
[MessageContract]  
public class BankingDepositLog  
{  
  [MessageHeader] public int numRecords;  
  [MessageHeader] public DepositRecord[] records;  
  [MessageHeader] public int branchID;  
}  
```  
  
 <span data-ttu-id="81980-171">Výsledkem hlavičky SOAP je podobný následujícímu.</span><span class="sxs-lookup"><span data-stu-id="81980-171">This results in SOAP headers is similar to the following.</span></span>  
  
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
  
 <span data-ttu-id="81980-172">Alternativou k tomuto je použít <xref:System.ServiceModel.MessageHeaderArrayAttribute>.</span><span class="sxs-lookup"><span data-stu-id="81980-172">An alternative to this is to use the <xref:System.ServiceModel.MessageHeaderArrayAttribute>.</span></span> <span data-ttu-id="81980-173">V takovém případě každý element pole je serializováno nezávisle a tak, že každý element pole má jedno záhlaví, podobný následujícímu.</span><span class="sxs-lookup"><span data-stu-id="81980-173">In this case, each array element is serialized independently and so that each array element has one header, similar to the following.</span></span>  
  
```xml  
<numRecords>3</numRecords>  
<records>Record1</records>  
<records>Record2</records>  
<records>Record3</records>  
<branchID>20643</branchID>  
```  
  
 <span data-ttu-id="81980-174">Výchozí název položky pole je název člena, ke kterému <xref:System.ServiceModel.MessageHeaderArrayAttribute> použít atributů.</span><span class="sxs-lookup"><span data-stu-id="81980-174">The default name for array entries is the name of the member to which the <xref:System.ServiceModel.MessageHeaderArrayAttribute> attributes is applied.</span></span>  
  
 <span data-ttu-id="81980-175"><xref:System.ServiceModel.MessageHeaderArrayAttribute> Atribut dědí z <xref:System.ServiceModel.MessageHeaderAttribute>.</span><span class="sxs-lookup"><span data-stu-id="81980-175">The <xref:System.ServiceModel.MessageHeaderArrayAttribute> attribute inherits from the <xref:System.ServiceModel.MessageHeaderAttribute>.</span></span> <span data-ttu-id="81980-176">Má stejnou sadu funkcí jako atributy mimo pole, například je možné nastavit pořadí, název a obor názvů pro pole hlavičky stejným způsobem, nastavit pro jednu hlavičky.</span><span class="sxs-lookup"><span data-stu-id="81980-176">It has the same set of features as the non-array attributes, for example, it is possible to set the order, name, and namespace for an array of headers in the same way you set it for a single header.</span></span> <span data-ttu-id="81980-177">Při použití `Order` vlastnost na pole, která se vztahuje na celé pole.</span><span class="sxs-lookup"><span data-stu-id="81980-177">When you use the `Order` property on an array, it applies to the entire array.</span></span>  
  
 <span data-ttu-id="81980-178">Můžete použít <xref:System.ServiceModel.MessageHeaderArrayAttribute> pouze na pole, není kolekcí.</span><span class="sxs-lookup"><span data-stu-id="81980-178">You can apply the <xref:System.ServiceModel.MessageHeaderArrayAttribute> only to arrays, not collections.</span></span>  
  
## <a name="using-byte-arrays-in-message-contracts"></a><span data-ttu-id="81980-179">Pomocí bajtových polí v kontrakty zpráv</span><span class="sxs-lookup"><span data-stu-id="81980-179">Using Byte Arrays in Message Contracts</span></span>  
 <span data-ttu-id="81980-180">Bajtová pole, pokud se používá s atributy mimo pole (<xref:System.ServiceModel.MessageBodyMemberAttribute> a <xref:System.ServiceModel.MessageHeaderAttribute>), nejsou považovány jako pole, ale speciální primitivní typ vyjádřený jako data ve výsledném souboru XML s kódováním Base64.</span><span class="sxs-lookup"><span data-stu-id="81980-180">Byte arrays, when used with the non-array attributes (<xref:System.ServiceModel.MessageBodyMemberAttribute> and <xref:System.ServiceModel.MessageHeaderAttribute>), are not treated as arrays but as a special primitive type represented as Base64-encoded data in the resulting XML.</span></span>  
  
 <span data-ttu-id="81980-181">Pokud používáte pole bajtů s atributem pole <xref:System.ServiceModel.MessageHeaderArrayAttribute>, výsledky závisí na serializátoru, který je používán.</span><span class="sxs-lookup"><span data-stu-id="81980-181">When you use byte arrays with the array attribute <xref:System.ServiceModel.MessageHeaderArrayAttribute>, the results depend on the serializer in use.</span></span> <span data-ttu-id="81980-182">S výchozí serializátor pole je reprezentován jako jednotlivé položky pro každý bajtů.</span><span class="sxs-lookup"><span data-stu-id="81980-182">With the default serializer, the array is represented as an individual entry for each byte.</span></span> <span data-ttu-id="81980-183">Ale když `XmlSerializer` je vybraná, (pomocí <xref:System.ServiceModel.XmlSerializerFormatAttribute> na kontrakt služby), bajtová pole jsou považovány za Base64 dat bez ohledu na to, jestli se používají atributy pole nebo jiné pole.</span><span class="sxs-lookup"><span data-stu-id="81980-183">However, when the `XmlSerializer` is selected, (using the <xref:System.ServiceModel.XmlSerializerFormatAttribute> on the service contract), byte arrays are treated as Base64 data regardless of whether the array or non-array attributes are used.</span></span>  
  
## <a name="signing-and-encrypting-parts-of-the-message"></a><span data-ttu-id="81980-184">Podepisování a šifrování částí zprávy</span><span class="sxs-lookup"><span data-stu-id="81980-184">Signing and Encrypting Parts of the Message</span></span>  
 <span data-ttu-id="81980-185">Kontrakt zprávy můžete určit, zda záhlaví nebo textu zprávy by měl být digitálně podepsat a zašifrovat.</span><span class="sxs-lookup"><span data-stu-id="81980-185">A message contract can indicate whether the headers and/or body of the message should be digitally signed and encrypted.</span></span>  
  
 <span data-ttu-id="81980-186">To se provádí nastavením <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A?displayProperty=nameWithType> vlastnost <xref:System.ServiceModel.MessageHeaderAttribute> a <xref:System.ServiceModel.MessageBodyMemberAttribute> atributy.</span><span class="sxs-lookup"><span data-stu-id="81980-186">This is done by setting the <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A?displayProperty=nameWithType> property on the <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes.</span></span> <span data-ttu-id="81980-187">Vlastnost je výčet <xref:System.Net.Security.ProtectionLevel?displayProperty=nameWithType> zadejte a může být nastaven na <xref:System.Net.Security.ProtectionLevel.None> (bez šifrování nebo podpis), <xref:System.Net.Security.ProtectionLevel.Sign> (digitální podpis pouze), nebo <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> (šifrování i digitální podpis).</span><span class="sxs-lookup"><span data-stu-id="81980-187">The property is an enumeration of the <xref:System.Net.Security.ProtectionLevel?displayProperty=nameWithType> type and can be set to <xref:System.Net.Security.ProtectionLevel.None> (no encryption or signature), <xref:System.Net.Security.ProtectionLevel.Sign> (digital signature only), or <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> (both encryption and a digital signature).</span></span> <span data-ttu-id="81980-188">Výchozí hodnota je <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span><span class="sxs-lookup"><span data-stu-id="81980-188">The default is <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span></span>  
  
 <span data-ttu-id="81980-189">Pro fungování těchto funkcí zabezpečení musí správně nakonfigurovat vazby a chování.</span><span class="sxs-lookup"><span data-stu-id="81980-189">For these security features to work, you must properly configure the binding and behaviors.</span></span> <span data-ttu-id="81980-190">Pokud používáte tyto funkce zabezpečení bez správnou konfiguraci (například pokus o přihlášení zprávu bez nutnosti zadávat svoje přihlašovací údaje), je vyvolána výjimka během ověření.</span><span class="sxs-lookup"><span data-stu-id="81980-190">If you use these security features without the proper configuration (for example, attempting to sign a message without supplying your credentials), an exception is thrown at validation time.</span></span>  
  
 <span data-ttu-id="81980-191">Zpráva hlavičky úroveň ochrany je určeno jednotlivě u každého záhlaví.</span><span class="sxs-lookup"><span data-stu-id="81980-191">For message headers, the protection level is determined individually for each header.</span></span>  
  
 <span data-ttu-id="81980-192">Pro částí textu zprávy úroveň ochrany můžete představit jako "minimální úroveň ochrany."</span><span class="sxs-lookup"><span data-stu-id="81980-192">For message body parts, the protection level can be thought of as the "minimum protection level."</span></span> <span data-ttu-id="81980-193">Text má úroveň ochrany jenom jeden, bez ohledu na počet částí textu.</span><span class="sxs-lookup"><span data-stu-id="81980-193">The body has only one protection level, regardless of the number of body parts.</span></span> <span data-ttu-id="81980-194">Úroveň ochrany obsahu, je dáno nejvyšší <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A> vlastnost na hodnotu všechny části textu.</span><span class="sxs-lookup"><span data-stu-id="81980-194">The protection level of the body is determined by the highest <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A> property setting of all the body parts.</span></span> <span data-ttu-id="81980-195">Ale byste měli nastavit skutečné ochrany minimální úroveň požadované úrovně ochrany každá část textu.</span><span class="sxs-lookup"><span data-stu-id="81980-195">However, you should set the protection level of each body part to the actual minimum protection level required.</span></span>  
  
 <span data-ttu-id="81980-196">Vezměte v úvahu třídy v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="81980-196">Consider the class in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="81980-197">V tomto příkladu `recordID` hlavičky není chráněný, `patientName` je `signed`, a `SSN` je šifrovaný a podepsaný.</span><span class="sxs-lookup"><span data-stu-id="81980-197">In this example, the `recordID` header is not protected, `patientName` is `signed`, and `SSN` is encrypted and signed.</span></span> <span data-ttu-id="81980-198">Část alespoň jeden textu `medicalHistory`, má <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> použít, a proto je obsah celé zprávy šifrovaný a podepsaný, i když komentáře a částí textu diagnostiku zadejte nižší úrovně ochrany.</span><span class="sxs-lookup"><span data-stu-id="81980-198">At least one body part, `medicalHistory`, has <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> applied, and thus the entire message body is encrypted and signed, even though the comments and diagnosis body parts specify lower protection levels.</span></span>  
  
## <a name="soap-action"></a><span data-ttu-id="81980-199">Akce protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="81980-199">SOAP Action</span></span>  
 <span data-ttu-id="81980-200">SOAP a související standardy webových služeb definovat vlastnost s názvem `Action` , může být k dispozici pro všechny protokolu SOAP zprávy určené.</span><span class="sxs-lookup"><span data-stu-id="81980-200">SOAP and related Web services standards define a property called `Action` that can be present for every SOAP message sent.</span></span> <span data-ttu-id="81980-201">Operace <xref:System.ServiceModel.OperationContractAttribute.Action%2A?displayProperty=nameWithType> a <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A?displayProperty=nameWithType> vlastnosti řídí hodnota této vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="81980-201">The operation's <xref:System.ServiceModel.OperationContractAttribute.Action%2A?displayProperty=nameWithType> and <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A?displayProperty=nameWithType> properties control the value of this property.</span></span>  
  
## <a name="soap-header-attributes"></a><span data-ttu-id="81980-202">Atributy hlavičky SOAP</span><span class="sxs-lookup"><span data-stu-id="81980-202">SOAP Header Attributes</span></span>  
 <span data-ttu-id="81980-203">Standard protokolu SOAP definuje následující atributy, které mohou existovat v záhlaví:</span><span class="sxs-lookup"><span data-stu-id="81980-203">The SOAP standard defines the following attributes that may exist on a header:</span></span>  
  
-   <span data-ttu-id="81980-204">`Actor/Role`(`Actor` v protokolu SOAP 1.1, `Role` v protokolu SOAP 1.2)</span><span class="sxs-lookup"><span data-stu-id="81980-204">`Actor/Role` (`Actor` in SOAP 1.1, `Role` in SOAP 1.2)</span></span>  
  
-   `MustUnderstand`  
  
-   `Relay`  
  
 <span data-ttu-id="81980-205">`Actor` Nebo `Role` Určuje atribut identifikátor URI (Uniform Resource) uzlu, pro kterou je určená danou hlavičku.</span><span class="sxs-lookup"><span data-stu-id="81980-205">The `Actor` or `Role` attribute specifies the Uniform Resource Identifier (URI) of the node for which a given header is intended.</span></span> <span data-ttu-id="81980-206">`MustUnderstand` Atribut určuje, zda uzel zpracování záhlaví musíte pochopit.</span><span class="sxs-lookup"><span data-stu-id="81980-206">The `MustUnderstand` attribute specifies whether the node processing the header must understand it.</span></span> <span data-ttu-id="81980-207">`Relay` Atribut určuje, zda záhlaví přenos pro podřízené uzly.</span><span class="sxs-lookup"><span data-stu-id="81980-207">The `Relay` attribute specifies whether the header is to be relayed to downstream nodes.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="81980-208">neprovede žádné zpracování těchto atributů pro příchozí zprávy, s výjimkou `MustUnderstand` atributu, jak je uvedeno v části "Správa verzí kontraktů zpráva" dál v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="81980-208"> does not perform any processing of these attributes on incoming messages, except for the `MustUnderstand` attribute, as specified in the "Message Contract Versioning" section later in this topic.</span></span> <span data-ttu-id="81980-209">Však umožňuje číst a zapisovat podle potřeby, stejně jako následující popis těchto atributů.</span><span class="sxs-lookup"><span data-stu-id="81980-209">However, it allows you to read and write these attributes as necessary, as in the following description.</span></span>  
  
 <span data-ttu-id="81980-210">Při odesílání zprávy, nejsou ve výchozím nastavení vygenerované těchto atributů.</span><span class="sxs-lookup"><span data-stu-id="81980-210">When sending a message, these attributes are not emitted by default.</span></span> <span data-ttu-id="81980-211">Toto můžete změnit dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="81980-211">You can change this in two ways.</span></span> <span data-ttu-id="81980-212">Nejprve může staticky nastavíte atributy na všechny požadované hodnoty tak, že změníte <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.MessageHeaderAttribute.MustUnderstand%2A?displayProperty=nameWithType>, a <xref:System.ServiceModel.MessageHeaderAttribute.Relay%2A?displayProperty=nameWithType> vlastnosti, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="81980-212">First, you may statically set the attributes to any desired values by changing the <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.MessageHeaderAttribute.MustUnderstand%2A?displayProperty=nameWithType>, and <xref:System.ServiceModel.MessageHeaderAttribute.Relay%2A?displayProperty=nameWithType> properties, as shown in the following code example.</span></span> <span data-ttu-id="81980-213">(Všimněte si, že je žádné `Role` vlastnost; nastavení <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A> vlastnost vysílá `Role` atribut Pokud používáte SOAP 1.2).</span><span class="sxs-lookup"><span data-stu-id="81980-213">(Note that there is no `Role` property; setting the <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A> property emits the `Role` attribute if you are using SOAP 1.2).</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader(Actor="http://auditingservice.contoso.com", MustUnderstand=true)] public bool IsAudited;  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public BankingTransactionData theData;  
}  
```  
  
 <span data-ttu-id="81980-214">Druhý způsob pro řízení těchto atributů je dynamicky prostřednictvím kódu.</span><span class="sxs-lookup"><span data-stu-id="81980-214">The second way to control these attributes is dynamically, through code.</span></span> <span data-ttu-id="81980-215">Toho lze dosáhnout pomocí zabalení typu požadované hlavičky v <xref:System.ServiceModel.MessageHeader%601> typu (ujistěte se, abyste nezaměnili tento typ s verzí neobecnou) a pomocí typu společně s <xref:System.ServiceModel.MessageHeaderAttribute>.</span><span class="sxs-lookup"><span data-stu-id="81980-215">You can achieve this by wrapping the desired header type in the <xref:System.ServiceModel.MessageHeader%601> type (be sure not to confuse this type with the non-generic version) and by using the type together with the <xref:System.ServiceModel.MessageHeaderAttribute>.</span></span> <span data-ttu-id="81980-216">Pak můžete použít vlastnosti na <xref:System.ServiceModel.MessageHeader%601> nastavit atributy protokolu SOAP, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="81980-216">Then, you can use properties on the <xref:System.ServiceModel.MessageHeader%601> to set the SOAP attributes, as shown in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="81980-217">Pokud používáte dynamické i statické kontrolní mechanismy, jsou použity jako výchozí nastavení statické ale můžete později přepsat pomocí dynamické mechanismus, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="81980-217">If you use both the dynamic and the static control mechanisms, the static settings are used as a default but can later be overridden by using the dynamic mechanism, as shown in the following code.</span></span>  
  
```csharp  
[MessageHeader(MustUnderstand=true)] public MessageHeader<Person> documentApprover;  
// later on in the code:  
BankingTransaction bt = new BankingTransaction();  
bt.documentApprover = new MessageHeader<Person>();  
bt.documentApprover.MustUnderstand = false; // override the static default of 'true'  
```  
  
 <span data-ttu-id="81980-218">Vytvoření opakovaných záhlaví s ovládacím prvkem dynamického atributu je povoleno, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="81980-218">Creating repeated headers with dynamic attribute control is allowed, as shown in the following code.</span></span>  
  
```csharp  
[MessageHeaderArray] public MessageHeader<Person> documentApprovers[];  
```  
  
 <span data-ttu-id="81980-219">Na straně příjmu, čtení těchto atributů protokolu SOAP lze provést pouze pokud <xref:System.ServiceModel.MessageHeader%601> třída se používá pro hlavičku v typu.</span><span class="sxs-lookup"><span data-stu-id="81980-219">On the receiving side, reading these SOAP attributes can only be done if the <xref:System.ServiceModel.MessageHeader%601> class is used for the header in the type.</span></span> <span data-ttu-id="81980-220">Zkontrolujte `Actor`, `Relay`, nebo `MustUnderstand` vlastnosti záhlaví <xref:System.ServiceModel.MessageHeader%601> typ ke zjištění nastavení atributů na přijatou zprávu.</span><span class="sxs-lookup"><span data-stu-id="81980-220">Examine the `Actor`, `Relay`, or `MustUnderstand` properties of a header of the <xref:System.ServiceModel.MessageHeader%601> type to discover the attribute settings on the received message.</span></span>  
  
 <span data-ttu-id="81980-221">Když zprávu přijme a pak se odešle zpět, nastavení atributů protokolu SOAP, jdou pouze operace round-trip pro hlavičky <xref:System.ServiceModel.MessageHeader%601> typu.</span><span class="sxs-lookup"><span data-stu-id="81980-221">When a message is received and then sent back, the SOAP attribute settings only go round-trip for headers of the <xref:System.ServiceModel.MessageHeader%601> type.</span></span>  
  
## <a name="order-of-soap-body-parts"></a><span data-ttu-id="81980-222">Pořadí částí textu protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="81980-222">Order of SOAP Body Parts</span></span>  
 <span data-ttu-id="81980-223">V některých případech můžete řídit pořadí částí textu.</span><span class="sxs-lookup"><span data-stu-id="81980-223">In some circumstances, you may need to control the order of the body parts.</span></span> <span data-ttu-id="81980-224">Je abecední ve výchozím nastavení pořadí prvků textu, ale je řízena <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="81980-224">The order of the body elements is alphabetical by default, but can be controlled by the <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="81980-225">Tato vlastnost má stejnou sémantiku jako <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A?displayProperty=nameWithType> vlastnost, s výjimkou jejich chování v dědičnosti scénáře (v kontrakty zpráv, základní typ textu, které nejsou členy seřazeny před členy textu odvozený typ).</span><span class="sxs-lookup"><span data-stu-id="81980-225">This property has the same semantics as the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A?displayProperty=nameWithType> property, except for the behavior in inheritance scenarios (in message contracts, base type body members are not sorted before the derived type body members).</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="81980-226">[Pořadí datových členů](../../../../docs/framework/wcf/feature-details/data-member-order.md).</span><span class="sxs-lookup"><span data-stu-id="81980-226"> [Data Member Order](../../../../docs/framework/wcf/feature-details/data-member-order.md).</span></span>  
  
 <span data-ttu-id="81980-227">V následujícím příkladu `amount` by za normálních okolností pocházet nejprve vzhledem k tomu, že je první podle abecedy.</span><span class="sxs-lookup"><span data-stu-id="81980-227">In the following example, `amount` would normally come first because it is first alphabetically.</span></span> <span data-ttu-id="81980-228">Ale <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A> vlastnost vloží je do třetí polohy.</span><span class="sxs-lookup"><span data-stu-id="81980-228">However, the <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A> property puts it into the third position.</span></span>  
  
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
  
## <a name="message-contract-versioning"></a><span data-ttu-id="81980-229">Správa verzí kontraktů zpráv</span><span class="sxs-lookup"><span data-stu-id="81980-229">Message Contract Versioning</span></span>  
 <span data-ttu-id="81980-230">V některých případech může muset změnit kontrakty zpráv.</span><span class="sxs-lookup"><span data-stu-id="81980-230">Occasionally, you may need to change message contracts.</span></span> <span data-ttu-id="81980-231">Nová verze aplikace může například přidat hlavičku navíc na zprávy.</span><span class="sxs-lookup"><span data-stu-id="81980-231">For example, a new version of your application may add an extra header to a message.</span></span> <span data-ttu-id="81980-232">Potom při odesílání z nové verze starý, systém musí řešit navíc záhlaví, jakož i chybí záhlaví při přechodu opačným směrem.</span><span class="sxs-lookup"><span data-stu-id="81980-232">Then, when sending from the new version to the old, the system must deal with an extra header, as well as a missing header when going in the other direction.</span></span>  
  
 <span data-ttu-id="81980-233">Správa verzí hlaviček, platí následující pravidla:</span><span class="sxs-lookup"><span data-stu-id="81980-233">The following rules apply for versioning headers:</span></span>  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="81980-234">proti hlavičkách chybí – odpovídající členové jsou ponechány na jejich výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="81980-234"> does not object to the missing headers—the corresponding members are left at their default values.</span></span>  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="81980-235">také ignoruje neočekávané další hlavičky.</span><span class="sxs-lookup"><span data-stu-id="81980-235"> also ignores unexpected extra headers.</span></span> <span data-ttu-id="81980-236">Jedinou výjimkou tohoto pravidla je, pokud má navíc záhlaví `MustUnderstand` atribut nastaven na `true` v příchozí zprávu SOAP – v takovém případě je vyvolána výjimka, protože hlavičku, která je třeba chápat nelze zpracovat.</span><span class="sxs-lookup"><span data-stu-id="81980-236">The one exception to this rule is if the extra header has a `MustUnderstand` attribute set to `true` in the incoming SOAP message—in this case, an exception is thrown because a header that must be understood cannot be processed.</span></span>  
  
 <span data-ttu-id="81980-237">Zpráva subjekty mají podobné pravidla Správa verzí – chybí a dalších částí textu zprávy jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="81980-237">Message bodies have similar versioning rules—both missing and additional message body parts are ignored.</span></span>  
  
## <a name="inheritance-considerations"></a><span data-ttu-id="81980-238">Důležité informace o dědičnosti</span><span class="sxs-lookup"><span data-stu-id="81980-238">Inheritance Considerations</span></span>  
 <span data-ttu-id="81980-239">Typ kontrakt zprávy může dědit vlastnosti z jiného typu, dokud základní typ také obsahuje kontrakt zprávy.</span><span class="sxs-lookup"><span data-stu-id="81980-239">A message contract type can inherit from another type, as long as the base type also has a message contract.</span></span>  
  
 <span data-ttu-id="81980-240">Při vytváření nebo přístup k zprávy pomocí typ zprávy kontrakt, který dědí z jiné typy kontraktů zpráv, platí následující pravidla:</span><span class="sxs-lookup"><span data-stu-id="81980-240">When creating or accessing a message using a message contract type that inherits from other message contract types, the following rules apply:</span></span>  
  
-   <span data-ttu-id="81980-241">Všechny hlavičky zpráv v hierarchii dědičnosti se shromažďují společně tvoří úplnou sadu hlaviček pro zprávu.</span><span class="sxs-lookup"><span data-stu-id="81980-241">All of the message headers in the inheritance hierarchy are collected together to form the full set of headers for the message.</span></span>  
  
-   <span data-ttu-id="81980-242">Všechny části textu zprávy v hierarchii dědičnosti se shromažďují společně tvoří obsah úplné zprávy.</span><span class="sxs-lookup"><span data-stu-id="81980-242">All of the message body parts in the inheritance hierarchy are collected together to form the full message body.</span></span> <span data-ttu-id="81980-243">Částí textu jsou seřazené podle obvyklé řazení pravidel (podle <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> vlastnost a potom abecední), s nemá význam pro jejich místo v hierarchii dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="81980-243">The body parts are ordered according to the usual ordering rules (by <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> property and then alphabetical), with no relevance to their place in the inheritance hierarchy.</span></span> <span data-ttu-id="81980-244">Použití dědičnosti kontrakt zprávy, kde částí textu zprávy probíhat na více úrovních stromu dědičnosti se důrazně nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="81980-244">Using message contract inheritance where message body parts occur at multiple levels of the inheritance tree is strongly discouraged.</span></span> <span data-ttu-id="81980-245">Pokud základní a odvozené třídě definovat hlavičku nebo část textu se stejným názvem, člena z většinu základní třída slouží k uložení hodnotu příslušné části Hlavička nebo text.</span><span class="sxs-lookup"><span data-stu-id="81980-245">If a base class and a derived class define a header or a body part with the same name, the member from the base-most class is used to store the value of that header or body part.</span></span>  
  
 <span data-ttu-id="81980-246">Vezměte v úvahu třídy v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="81980-246">Consider the classes in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="81980-247">`PatientRecord` Třída popisuje zprávu s názvem jedno záhlaví `ID`.</span><span class="sxs-lookup"><span data-stu-id="81980-247">The `PatientRecord` class describes a message with one header called `ID`.</span></span> <span data-ttu-id="81980-248">Záhlaví odpovídá `personID` a ne `patientID` člena, protože většina základní člen je zvolen.</span><span class="sxs-lookup"><span data-stu-id="81980-248">The header corresponds to the `personID` and not the `patientID` member, because the base-most member is chosen.</span></span> <span data-ttu-id="81980-249">Proto `patientID` pole v tomto případě je zbytečné.</span><span class="sxs-lookup"><span data-stu-id="81980-249">Thus, the `patientID` field is useless in this case.</span></span> <span data-ttu-id="81980-250">Tělo zprávy obsahuje `diagnosis` element, za nímž následuje `patientName` elementu, protože se jedná o abecedním pořadí.</span><span class="sxs-lookup"><span data-stu-id="81980-250">The body of the message contains the `diagnosis` element followed by the `patientName` element, because that is the alphabetical order.</span></span> <span data-ttu-id="81980-251">Všimněte si, že tento příklad ukazuje vzor, který se důrazně nedoporučuje: základní i odvozené zpráva kontrakty mají částí textu zprávy.</span><span class="sxs-lookup"><span data-stu-id="81980-251">Notice that the example shows a pattern that is strongly discouraged: both the base and the derived message contracts have message body parts.</span></span>  
  
## <a name="wsdl-considerations"></a><span data-ttu-id="81980-252">Aspekty WSDL</span><span class="sxs-lookup"><span data-stu-id="81980-252">WSDL Considerations</span></span>  
 <span data-ttu-id="81980-253">Při generování z službu, která používá kontrakty zpráv kontraktu služby popis jazyka WSDL (Web), je důležité si pamatovat, že ne všechny funkce kontrakt zprávy se projeví ve výsledné schématu WSDL.</span><span class="sxs-lookup"><span data-stu-id="81980-253">When generating a Web Services Description Language (WSDL) contract from a service that uses message contracts, it is important to remember that not all message contract features are reflected in the resulting WSDL.</span></span> <span data-ttu-id="81980-254">Mějte na paměti následující body:</span><span class="sxs-lookup"><span data-stu-id="81980-254">Consider the following points:</span></span>  
  
-   <span data-ttu-id="81980-255">WSDL nelze express koncept pole hlavičky.</span><span class="sxs-lookup"><span data-stu-id="81980-255">WSDL cannot express the concept of an array of headers.</span></span> <span data-ttu-id="81980-256">Při vytváření zpráv pomocí pole hlavičky pomocí <xref:System.ServiceModel.MessageHeaderArrayAttribute>, výsledná WSDL odráží pouze jedno záhlaví místo pole.</span><span class="sxs-lookup"><span data-stu-id="81980-256">When creating messages with an array of headers using the <xref:System.ServiceModel.MessageHeaderArrayAttribute>, the resulting WSDL reflects only one header instead of the array.</span></span>  
  
-   <span data-ttu-id="81980-257">Výsledný dokument WSDL nemusí odrážet některé informace úroveň ochrany.</span><span class="sxs-lookup"><span data-stu-id="81980-257">The resulting WSDL document may not reflect some protection-level information.</span></span>  
  
-   <span data-ttu-id="81980-258">Typ zprávy generované ve schématu WSDL má stejný název jako název třídy typ kontrakt zprávy.</span><span class="sxs-lookup"><span data-stu-id="81980-258">The message type generated in the WSDL has the same name as the class name of the message contract type.</span></span>  
  
-   <span data-ttu-id="81980-259">Při použití stejné zprávy sbalit ve více operací, několik typů zpráv vytvoří v souboru WSDL.</span><span class="sxs-lookup"><span data-stu-id="81980-259">When using the same message contract in multiple operations, multiple message types are generated in the WSDL document.</span></span> <span data-ttu-id="81980-260">Přidáním čísla "2", "3" a tak dále, pro následné používá, jsou vytvářeny jedinečné názvy.</span><span class="sxs-lookup"><span data-stu-id="81980-260">The names are made unique by adding the numbers "2", "3", and so on, for subsequent uses.</span></span> <span data-ttu-id="81980-261">Při importu zpět schématu WSDL, vytvoří se více typy kontraktů zpráv a jsou identické s výjimkou jejich názvy.</span><span class="sxs-lookup"><span data-stu-id="81980-261">When importing back the WSDL, multiple message contract types are created and are identical except for their names.</span></span>  
  
## <a name="soap-encoding-considerations"></a><span data-ttu-id="81980-262">Kódování důležité informace o protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="81980-262">SOAP Encoding Considerations</span></span>  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="81980-263">umožňuje používat starší verze protokolu SOAP kódování styl XML, ale jeho použití se nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="81980-263"> allows you to use the legacy SOAP encoding style of XML, however, its use is not recommended.</span></span> <span data-ttu-id="81980-264">Při použití této styl (nastavením `Use` vlastnost `Encoded` na <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType> u kontrakt služby), platí následující další aspekty:</span><span class="sxs-lookup"><span data-stu-id="81980-264">When using this style (by setting the `Use` property to `Encoded` on the <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType> applied to the service contract), the following additional considerations apply:</span></span>  
  
-   <span data-ttu-id="81980-265">Záhlaví zprávy nejsou podporovány; To znamená, že atribut <xref:System.ServiceModel.MessageHeaderAttribute> a pole atributu <xref:System.ServiceModel.MessageHeaderArrayAttribute> nejsou kompatibilní s kódováním protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="81980-265">The message headers are not supported; this means that the attribute <xref:System.ServiceModel.MessageHeaderAttribute> and the array attribute <xref:System.ServiceModel.MessageHeaderArrayAttribute> are incompatible with SOAP encoding.</span></span>  
  
-   <span data-ttu-id="81980-266">Pokud kontrakt zprávy není zabalená, to znamená, pokud vlastnost <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> je nastaven na `false`, kontrakt zprávy může mít část pouze jeden textu.</span><span class="sxs-lookup"><span data-stu-id="81980-266">If the message contract is not wrapped, that is, if the property <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> is set to `false`, the message contract can have only one body part.</span></span>  
  
-   <span data-ttu-id="81980-267">Název elementu obálku pro kontrakt zprávy požadavku musí odpovídat názvu operaci.</span><span class="sxs-lookup"><span data-stu-id="81980-267">The name of the wrapper element for the request message contract must match the operation name.</span></span> <span data-ttu-id="81980-268">Použití `WrapperName` kontrakt zprávy pro tuto vlastnost.</span><span class="sxs-lookup"><span data-stu-id="81980-268">Use the `WrapperName` property of the message contract for this.</span></span>  
  
-   <span data-ttu-id="81980-269">Název elementu obálku pro kontrakt zprávy odpovědi musí být stejný jako název operace na konci podle "Odpověď".</span><span class="sxs-lookup"><span data-stu-id="81980-269">The name of the wrapper element for the response message contract must be the same as the name of the operation suffixed by 'Response'.</span></span> <span data-ttu-id="81980-270">Použití <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> kontrakt zprávy pro tuto vlastnost.</span><span class="sxs-lookup"><span data-stu-id="81980-270">Use the <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> property of the message contract for this.</span></span>  
  
-   <span data-ttu-id="81980-271">Kódování SOAP zachovává odkazy na objekty.</span><span class="sxs-lookup"><span data-stu-id="81980-271">SOAP encoding preserves object references.</span></span> <span data-ttu-id="81980-272">Zvažte například následující kód.</span><span class="sxs-lookup"><span data-stu-id="81980-272">For example, consider the following code.</span></span>  
  
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
  
 <span data-ttu-id="81980-273">Po serializaci zprávu pomocí protokolu SOAP kódování, `changedFrom` a `changedTo` neobsahují své vlastní kopie `p`, ale místo toho přejděte na kopírování uvnitř `changedBy` elementu.</span><span class="sxs-lookup"><span data-stu-id="81980-273">After serializing the message using SOAP encoding, `changedFrom` and `changedTo` do not contain their own copies of `p`, but instead point to the copy inside the `changedBy` element.</span></span>  
  
## <a name="performance-considerations"></a><span data-ttu-id="81980-274">Faktory ovlivňující výkon</span><span class="sxs-lookup"><span data-stu-id="81980-274">Performance Considerations</span></span>  
 <span data-ttu-id="81980-275">Každý záhlaví zprávy a část textu zprávy je serializováno nezávisle na ostatních.</span><span class="sxs-lookup"><span data-stu-id="81980-275">Every message header and message body part is serialized independently of the others.</span></span> <span data-ttu-id="81980-276">Proto lze stejné obory názvů deklarovat opakujte pro každou záhlaví a část textu.</span><span class="sxs-lookup"><span data-stu-id="81980-276">Therefore, the same namespaces can be declared again for each header and body part.</span></span> <span data-ttu-id="81980-277">Pro zlepšení výkonu, zejména z hlediska velikost zprávy v drátové síti, konsolidovat více hlavičky a částí textu do jedné součásti Hlavička nebo text.</span><span class="sxs-lookup"><span data-stu-id="81980-277">To improve performance, especially in terms of the size of the message on the wire, consolidate multiple headers and body parts into a single header or body part.</span></span> <span data-ttu-id="81980-278">Například místo následující kód:</span><span class="sxs-lookup"><span data-stu-id="81980-278">For example, instead of the following code:</span></span>  
  
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
  
 <span data-ttu-id="81980-279">Pomocí tohoto kódu.</span><span class="sxs-lookup"><span data-stu-id="81980-279">Use this code.</span></span>  
  
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
  
### <a name="event-based-asynchronous-and-message-contracts"></a><span data-ttu-id="81980-280">Na základě událostí asynchronní a kontrakty zpráv</span><span class="sxs-lookup"><span data-stu-id="81980-280">Event-based Asynchronous and Message Contracts</span></span>  
 <span data-ttu-id="81980-281">Podle pokynů návrhu pro asynchronní model na základě událostí stavu, že pokud je vrácen více než jednu hodnotu, se vrátí jednu hodnotu jako `Result` vlastnost a jiné jsou vrácena jako vlastnosti na <xref:System.EventArgs> objektu.</span><span class="sxs-lookup"><span data-stu-id="81980-281">The design guidelines for the event-based asynchronous model state that if more than one value is returned, one value is returned as the `Result` property and the others are returned as properties on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="81980-282">Jeden výsledek tohoto objektu je, že pokud klient naimportuje metadata pomocí možností na základě událostí asynchronní příkaz a operaci vrátí více než jednu hodnotu, výchozí <xref:System.EventArgs> objekt vrátí jednu hodnotu jako `Result` vlastnost a zbývající jsou vlastnosti <xref:System.EventArgs> objektu.</span><span class="sxs-lookup"><span data-stu-id="81980-282">One result of this is that if a client imports metadata using the event-based asynchronous command options and the operation returns more than one value, the default <xref:System.EventArgs> object returns one value as the `Result` property and the remainder are properties of the <xref:System.EventArgs> object.</span></span>  
  
 <span data-ttu-id="81980-283">Pokud chcete dostávat zprávy objektu jako `Result` vlastnost a mít vrácené hodnoty jako vlastnosti tohoto objektu, použijte `/messageContract` příkaz možnost.</span><span class="sxs-lookup"><span data-stu-id="81980-283">If you want to receive the message object as the `Result` property and have the returned values as properties on that object, use the `/messageContract` command option.</span></span> <span data-ttu-id="81980-284">Tím se vygeneruje podpisu, který vrátí zprávu odpovědi jako `Result` vlastnost <xref:System.EventArgs> objektu.</span><span class="sxs-lookup"><span data-stu-id="81980-284">This generates a signature that returns the response message as the `Result` property on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="81980-285">Všechny interní návratové hodnoty jsou pak vlastnosti objektu zprávu odpovědi.</span><span class="sxs-lookup"><span data-stu-id="81980-285">All internal return values are then properties of the response message object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81980-286">Viz také</span><span class="sxs-lookup"><span data-stu-id="81980-286">See Also</span></span>  
 [<span data-ttu-id="81980-287">Použití kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="81980-287">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [<span data-ttu-id="81980-288">Navrhování a implementace služeb</span><span class="sxs-lookup"><span data-stu-id="81980-288">Designing and Implementing Services</span></span>](../../../../docs/framework/wcf/designing-and-implementing-services.md)
