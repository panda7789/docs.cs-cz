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
# <a name="using-message-contracts"></a><span data-ttu-id="8d61a-102">Použití kontraktů zpráv</span><span class="sxs-lookup"><span data-stu-id="8d61a-102">Using Message Contracts</span></span>
<span data-ttu-id="8d61a-103">Obvykle při vytváření aplikací Windows Communication Foundation (WCF), vývojáři pozornosti datových struktur a problémům se serializací a není nutné starat struktura zpráv, ve kterých se provádí s data.</span><span class="sxs-lookup"><span data-stu-id="8d61a-103">Typically when building Windows Communication Foundation (WCF) applications, developers pay close attention to the data structures and serialization issues and do not need to concern themselves with the structure of the messages in which the data is carried.</span></span> <span data-ttu-id="8d61a-104">V případě těchto aplikací je jednoduché vytváření kontraktů dat pro parametry nebo návratové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="8d61a-104">For these applications, creating data contracts for the parameters or return values is straightforward.</span></span> <span data-ttu-id="8d61a-105">(Další informace najdete v tématu [zadání přenosu dat v kontraktech služeb](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).)</span><span class="sxs-lookup"><span data-stu-id="8d61a-105">(For more information, see [Specifying Data Transfer in Service Contracts](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md).)</span></span>  
  
 <span data-ttu-id="8d61a-106">Ale někdy úplnou kontrolu nad strukturou zprávu protokolu SOAP je stejně důležité jako kontrolu nad jeho obsah.</span><span class="sxs-lookup"><span data-stu-id="8d61a-106">However, sometimes complete control over the structure of a SOAP message is just as important as control over its contents.</span></span> <span data-ttu-id="8d61a-107">To platí zejména při zajištění lepší interoperability je důležité nebo konkrétně řízení zabezpečení problémy na úrovni zprávy nebo část zprávy.</span><span class="sxs-lookup"><span data-stu-id="8d61a-107">This is especially true when interoperability is important or to specifically control security issues at the level of the message or message part.</span></span> <span data-ttu-id="8d61a-108">V těchto případech můžete vytvořit *kontraktu zprávy* , který umožňuje určit strukturu přesné zprávu protokolu SOAP vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="8d61a-108">In these cases, you can create a *message contract* that enables you to specify the structure of the precise SOAP message required.</span></span>  
  
 <span data-ttu-id="8d61a-109">Toto téma popisuje, jak použít různé atributy kontraktu zprávy k vytvoření kontraktu zprávy specifické pro vaši operaci.</span><span class="sxs-lookup"><span data-stu-id="8d61a-109">This topic discusses how to use the various message contract attributes to create a specific message contract for your operation.</span></span>  
  
## <a name="using-message-contracts-in-operations"></a><span data-ttu-id="8d61a-110">Použití kontraktů zpráv v operacích</span><span class="sxs-lookup"><span data-stu-id="8d61a-110">Using Message Contracts in Operations</span></span>  
 <span data-ttu-id="8d61a-111">WCF podporuje operace vymodelován buď *vzdálené volání (procedur RPC) styl* nebo *zasílání zpráv styl*.</span><span class="sxs-lookup"><span data-stu-id="8d61a-111">WCF supports operations modeled on either the *remote procedure call (RPC) style* or the *messaging style*.</span></span> <span data-ttu-id="8d61a-112">V operaci stylu RPC, můžete použít libovolný serializovatelný typ., a budete mít přístup k funkcím, které jsou k dispozici pro místní volání, jako je například více parametrů a `ref` a `out` parametry.</span><span class="sxs-lookup"><span data-stu-id="8d61a-112">In an RPC-style operation, you can use any serializable type, and you have access to the features that are available to local calls, such as multiple parameters and `ref` and `out` parameters.</span></span> <span data-ttu-id="8d61a-113">V tomto stylu forma serializace zvolit řídí strukturu dat v podkladové zprávy a zprávy, které mají podporovat operaci, vytvoří modul runtime WCF.</span><span class="sxs-lookup"><span data-stu-id="8d61a-113">In this style, the form of serialization chosen controls the structure of the data in the underlying messages, and the WCF runtime creates the messages to support the operation.</span></span> <span data-ttu-id="8d61a-114">To umožňuje vývojářům, kteří nejsou obeznámeni s SOAP a zpráv SOAP rychle a snadno vytvářet a používat služby aplikace.</span><span class="sxs-lookup"><span data-stu-id="8d61a-114">This enables developers who are not familiar with SOAP and SOAP messages to quickly and easily create and use service applications.</span></span>  
  
 <span data-ttu-id="8d61a-115">Následující příklad kódu ukazuje operaci služby modelována ve stylu RPC.</span><span class="sxs-lookup"><span data-stu-id="8d61a-115">The following code example shows a service operation modeled on the RPC style.</span></span>  
  
```csharp  
[OperationContract]  
public BankingTransactionResponse PostBankingTransaction(BankingTransaction bt);  
```  
  
 <span data-ttu-id="8d61a-116">Za normálních okolností kontraktu dat. stačí definovat schéma pro zprávy.</span><span class="sxs-lookup"><span data-stu-id="8d61a-116">Normally, a data contract is sufficient to define the schema for the messages.</span></span> <span data-ttu-id="8d61a-117">Například v předchozím příkladu je dostatečné pro většinu aplikací Pokud `BankingTransaction` a `BankingTransactionResponse` mít kontraktů dat zadat obsah základní zprávy protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="8d61a-117">For instance, in the preceding example, it is sufficient for most applications if `BankingTransaction` and `BankingTransactionResponse` have data contracts to define the contents of the underlying SOAP messages.</span></span> <span data-ttu-id="8d61a-118">Další informace o kontraktech dat najdete v tématu [kontraktů dat pomocí](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="8d61a-118">For more information about data contracts, see [Using Data Contracts](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span></span>  
  
 <span data-ttu-id="8d61a-119">Ale čas od času je potřeba přesně řídit, jak přenést struktura zprávu protokolu SOAP přenosu.</span><span class="sxs-lookup"><span data-stu-id="8d61a-119">However, occasionally it is necessary to precisely control how the structure of the SOAP message transmitted over the wire.</span></span> <span data-ttu-id="8d61a-120">Nejběžnější scénář je vložení vlastní hlavičky SOAP.</span><span class="sxs-lookup"><span data-stu-id="8d61a-120">The most common scenario for this is inserting custom SOAP headers.</span></span> <span data-ttu-id="8d61a-121">Další z typických možností je, který je definování zabezpečení vlastností záhlaví a text zprávy, se rozhodnout, jestli tyto prvky jsou digitálně podepsané a šifrovaná.</span><span class="sxs-lookup"><span data-stu-id="8d61a-121">Another common scenario is to define security properties for the message's headers and body, that is, to decide whether these elements are digitally signed and encrypted.</span></span> <span data-ttu-id="8d61a-122">A konečně některé balíčky třetích stran SOAP vyžadují zpráv v určitém formátu.</span><span class="sxs-lookup"><span data-stu-id="8d61a-122">Finally, some third-party SOAP stacks require messages be in a specific format.</span></span> <span data-ttu-id="8d61a-123">Operace zasílání zpráv ve stylu poskytují tohoto ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="8d61a-123">Messaging-style operations provide this control.</span></span>  
  
 <span data-ttu-id="8d61a-124">Operace zasílání zpráv ve stylu má maximálně jeden parametr a návratové hodnoty jednoho kde oba typy jsou typy zpráv; To znamená že serializovat přímo do struktury zadané zprávy protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="8d61a-124">A messaging-style operation has at most one parameter and one return value where both types are message types; that is, they serialize directly into a specified SOAP message structure.</span></span> <span data-ttu-id="8d61a-125">To může být libovolný typ označené <xref:System.ServiceModel.MessageContractAttribute> nebo <xref:System.ServiceModel.Channels.Message> typu.</span><span class="sxs-lookup"><span data-stu-id="8d61a-125">This may be any type marked with the <xref:System.ServiceModel.MessageContractAttribute> or the <xref:System.ServiceModel.Channels.Message> type.</span></span> <span data-ttu-id="8d61a-126">Následující příklad kódu ukazuje operaci podobně jako v předchozím stylu RCP, ale zasílání zpráv styl, který používá.</span><span class="sxs-lookup"><span data-stu-id="8d61a-126">The following code example shows an operation similar to the preceding RCP-style, but which uses the messaging style.</span></span>  
  
 <span data-ttu-id="8d61a-127">Například pokud `BankingTransaction` a `BankingTransactionResponse` se oba typy kontraktů zpráv, pak kód v následující operace je platná.</span><span class="sxs-lookup"><span data-stu-id="8d61a-127">For example, if `BankingTransaction` and `BankingTransactionResponse` are both types that are message contracts, then the code in the following operations is valid.</span></span>  
  
```csharp  
[OperationContract]  
BankingTransactionResponse Process(BankingTransaction bt);  
[OperationContract]  
void Store(BankingTransaction bt);  
[OperationContract]  
BankingTransactionResponse GetResponse();  
```  
  
 <span data-ttu-id="8d61a-128">Následující kód je však neplatný.</span><span class="sxs-lookup"><span data-stu-id="8d61a-128">However, the following code is invalid.</span></span>  
  
```csharp  
[OperationContract]  
bool Validate(BankingTransaction bt);  
// Invalid, the return type is not a message contract.  
[OperationContract]  
void Reconcile(BankingTransaction bt1, BankingTransaction bt2);  
// Invalid, there is more than one parameter.  
```  
  
 <span data-ttu-id="8d61a-129">Pro jakoukoli operaci, která zahrnuje typ kontraktu zprávy a není, proveďte jeden z platných vzorů je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="8d61a-129">An exception is thrown for any operation that involves a message contract type and that does not follow one of the valid patterns.</span></span> <span data-ttu-id="8d61a-130">Samozřejmě operace, které nezahrnují typy kontraktů zpráv se nevztahují tato omezení.</span><span class="sxs-lookup"><span data-stu-id="8d61a-130">Of course, operations that do not involve message contract types are not subject to these restrictions.</span></span>  
  
 <span data-ttu-id="8d61a-131">Pokud je typ kontraktu zprávy a kontraktem dat, pouze jeho kontraktu zprávy se považuje za při použití typu v rámci operace.</span><span class="sxs-lookup"><span data-stu-id="8d61a-131">If a type has both a message contract and a data contract, only its message contract is considered when the type is used in an operation.</span></span>  
  
## <a name="defining-message-contracts"></a><span data-ttu-id="8d61a-132">Definování kontraktů zpráv</span><span class="sxs-lookup"><span data-stu-id="8d61a-132">Defining Message Contracts</span></span>  
 <span data-ttu-id="8d61a-133">K definování kontraktu zprávy pro typ (to znamená, chcete-li definovat mapování mezi typem a obálku protokolu SOAP), použít <xref:System.ServiceModel.MessageContractAttribute> typu.</span><span class="sxs-lookup"><span data-stu-id="8d61a-133">To define a message contract for a type (that is, to define the mapping between the type and a SOAP envelope), apply the <xref:System.ServiceModel.MessageContractAttribute> to the type.</span></span> <span data-ttu-id="8d61a-134">Následně použít <xref:System.ServiceModel.MessageHeaderAttribute> na tyto členy typu, které chcete vytvořit jako záhlaví SOAP a použít <xref:System.ServiceModel.MessageBodyMemberAttribute> těmto členům chcete přejít do části těla protokolu SOAP zprávy.</span><span class="sxs-lookup"><span data-stu-id="8d61a-134">Then apply the <xref:System.ServiceModel.MessageHeaderAttribute> to those members of the type you want to make into SOAP headers, and apply the <xref:System.ServiceModel.MessageBodyMemberAttribute> to those members you want to make into parts of the SOAP body of the message.</span></span>  
  
 <span data-ttu-id="8d61a-135">Následující kód obsahuje příklad pomocí kontraktu zprávy.</span><span class="sxs-lookup"><span data-stu-id="8d61a-135">The following code provides an example of using a message contract.</span></span>  
  
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
  
 <span data-ttu-id="8d61a-136">Při použití tohoto typu jako parametr operace, je vygenerována následující obálky protokolu SOAP:</span><span class="sxs-lookup"><span data-stu-id="8d61a-136">When using this type as an operation parameter, the following SOAP envelope is generated:</span></span>  
  
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
  
 <span data-ttu-id="8d61a-137">Všimněte si, že `operation` a `transactionDate` zobrazují jako záhlaví SOAP a SOAP body se skládá z prvku obálky `BankingTransaction` obsahující `sourceAccount`,`targetAccount`, a `amount`.</span><span class="sxs-lookup"><span data-stu-id="8d61a-137">Notice that `operation` and `transactionDate` appear as SOAP headers and the SOAP body consists of a wrapper element `BankingTransaction` containing `sourceAccount`,`targetAccount`, and `amount`.</span></span>  
  
 <span data-ttu-id="8d61a-138">Můžete použít <xref:System.ServiceModel.MessageHeaderAttribute> a <xref:System.ServiceModel.MessageBodyMemberAttribute> pro všechna pole, vlastnosti a události, bez ohledu na to, zda jsou veřejné, privátní, chráněné nebo interní.</span><span class="sxs-lookup"><span data-stu-id="8d61a-138">You can apply the <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> to all fields, properties, and events, regardless of whether they are public, private, protected, or internal.</span></span>  
  
 <span data-ttu-id="8d61a-139"><xref:System.ServiceModel.MessageContractAttribute> Vám umožní určit WrapperName a WrapperNamespace atributy, které řídí název prvku obálky v těle zprávy protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="8d61a-139">The <xref:System.ServiceModel.MessageContractAttribute> allows you to specify the WrapperName and WrapperNamespace attributes which control the name of the wrapper element in the body of the SOAP message.</span></span> <span data-ttu-id="8d61a-140">Ve výchozím nastavení název kontraktu zprávy typ se používá pro obálku a obor názvů, ve kterém je definována kontraktu zprávy `http://tempuri.org/` slouží jako výchozí obor názvů.</span><span class="sxs-lookup"><span data-stu-id="8d61a-140">By default the name of the message contract type is used for the wrapper and the namespace in which the message contract is defined `http://tempuri.org/` is used as the default namespace.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8d61a-141"><xref:System.Runtime.Serialization.KnownTypeAttribute> atributy se ignorují v kontraktů zpráv.</span><span class="sxs-lookup"><span data-stu-id="8d61a-141"><xref:System.Runtime.Serialization.KnownTypeAttribute> attributes are ignored in message contracts.</span></span> <span data-ttu-id="8d61a-142">Pokud <xref:System.Runtime.Serialization.KnownTypeAttribute> je potřeba, umístěte ho na operaci, která používá kontrakt zprávy dotyčný.</span><span class="sxs-lookup"><span data-stu-id="8d61a-142">If a <xref:System.Runtime.Serialization.KnownTypeAttribute> is required, place it on the operation that is using the message contract in question.</span></span>  
  
## <a name="controlling-header-and-body-part-names-and-namespaces"></a><span data-ttu-id="8d61a-143">Řízení hlavička a tělo část názvy a obory názvů</span><span class="sxs-lookup"><span data-stu-id="8d61a-143">Controlling Header and Body Part Names and Namespaces</span></span>  
 <span data-ttu-id="8d61a-144">V reprezentaci kontraktu zprávy protokolu SOAP každá část hlavička a tělo zprávy mapuje na element XML, který má název a obor názvů.</span><span class="sxs-lookup"><span data-stu-id="8d61a-144">In the SOAP representation of a message contract, each header and body part maps to an XML element that has a name and a namespace.</span></span>  
  
 <span data-ttu-id="8d61a-145">Ve výchozím nastavení, stejně jako obor názvů kontraktu služby, který je součástí zprávy a název je určen název členu, ke které je obor názvů <xref:System.ServiceModel.MessageHeaderAttribute> nebo <xref:System.ServiceModel.MessageBodyMemberAttribute> atributy jsou použity.</span><span class="sxs-lookup"><span data-stu-id="8d61a-145">By default, the namespace is the same as the namespace of the service contract that the message is participating in, and the name is determined by the member name to which the <xref:System.ServiceModel.MessageHeaderAttribute> or the <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes are applied.</span></span>  
  
 <span data-ttu-id="8d61a-146">Tato výchozí nastavení můžete změnit pomocí manipulace s <xref:System.ServiceModel.MessageContractMemberAttribute.Name%2A?displayProperty=nameWithType> a <xref:System.ServiceModel.MessageContractMemberAttribute.Namespace%2A?displayProperty=nameWithType> (na nadřazené třídu <xref:System.ServiceModel.MessageHeaderAttribute> a <xref:System.ServiceModel.MessageBodyMemberAttribute> atributy).</span><span class="sxs-lookup"><span data-stu-id="8d61a-146">You can change these defaults by manipulating the <xref:System.ServiceModel.MessageContractMemberAttribute.Name%2A?displayProperty=nameWithType> and <xref:System.ServiceModel.MessageContractMemberAttribute.Namespace%2A?displayProperty=nameWithType> (on the parent class of the <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes).</span></span>  
  
 <span data-ttu-id="8d61a-147">Vezměte v úvahu třídu v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="8d61a-147">Consider the class in the following code example.</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader] public Operation operation;  
  [MessageHeader(Namespace="http://schemas.contoso.com/auditing/2005")] public bool IsAudited;  
  [MessageBodyMember(Name="transactionData")] public BankingTransactionData theData;  
}  
```  
  
 <span data-ttu-id="8d61a-148">V tomto příkladu `IsAudited` záhlaví je v oboru názvů určenému v kódu a část textu, který představuje `theData` člen je reprezentována element XML s názvem `transactionData`.</span><span class="sxs-lookup"><span data-stu-id="8d61a-148">In this example, the `IsAudited` header is in the namespace specified in the code, and the body part that represents the `theData` member is represented by an XML element with the name `transactionData`.</span></span> <span data-ttu-id="8d61a-149">Následuje ukázka kódem XML vygenerovaným pro tento kontrakt zprávy.</span><span class="sxs-lookup"><span data-stu-id="8d61a-149">The following shows the XML generated for this message contract.</span></span>  
  
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
  
## <a name="controlling-whether-the-soap-body-parts-are-wrapped"></a><span data-ttu-id="8d61a-150">Řízení, zda jsou zabaleny částí textu protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="8d61a-150">Controlling Whether the SOAP Body Parts Are Wrapped</span></span>  
 <span data-ttu-id="8d61a-151">Ve výchozím nastavení částí textu SOAP serializují uvnitř zabalené elementu.</span><span class="sxs-lookup"><span data-stu-id="8d61a-151">By default, the SOAP body parts are serialized inside a wrapped element.</span></span> <span data-ttu-id="8d61a-152">Například následující kód ukazuje `HelloGreetingMessage` element obálky, které jsou generovány z názvu <xref:System.ServiceModel.MessageContractAttribute> typ v kontraktu zprávy pro `HelloGreetingMessage` zprávy.</span><span class="sxs-lookup"><span data-stu-id="8d61a-152">For example, the following code shows the `HelloGreetingMessage` wrapper element generated from the name of the <xref:System.ServiceModel.MessageContractAttribute> type in the message contract for the `HelloGreetingMessage` message.</span></span>  
  
[!code-csharp[MessageHeaderAttribute#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/messageheaderattribute/cs/services.cs#3)]
[!code-vb[MessageHeaderAttribute#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/messageheaderattribute/vb/services.vb#3)]  
  
 <span data-ttu-id="8d61a-153">Chcete-li potlačit element obálky, nastavte <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="8d61a-153">To suppress the wrapper element, set the <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> property to `false`.</span></span> <span data-ttu-id="8d61a-154">Pokud chcete nastavit název a obor názvů element obálky, použijte <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> a <xref:System.ServiceModel.MessageContractAttribute.WrapperNamespace%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="8d61a-154">To control the name and the namespace of the wrapper element, use the <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> and <xref:System.ServiceModel.MessageContractAttribute.WrapperNamespace%2A> properties.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8d61a-155">S více než jednu část textu zprávy ve zprávách, které nejsou zabaleny není kompatibilní s WS-I Basic Profile 1.1 a nedoporučuje se při navrhování nových kontraktů zpráv.</span><span class="sxs-lookup"><span data-stu-id="8d61a-155">Having more than one message body part in messages that are not wrapped is not compliant with WS-I Basic Profile 1.1 and is not recommended when designing new message contracts.</span></span> <span data-ttu-id="8d61a-156">Však může být potřeba mít více než jednu část textu nerozbalené zprávy v některých scénářích konkrétní vzájemná funkční spolupráce.</span><span class="sxs-lookup"><span data-stu-id="8d61a-156">However, it may be necessary to have more than one unwrapped message body part in certain specific interoperability scenarios.</span></span> <span data-ttu-id="8d61a-157">Pokud budete přenášet víc než jednu část dat v textu zprávy, se doporučuje použít režim výchozí (zabalená).</span><span class="sxs-lookup"><span data-stu-id="8d61a-157">If you are going to transmit more than one piece of data in a message body, it is recommended to use the default (wrapped) mode.</span></span> <span data-ttu-id="8d61a-158">Nerozbalené zprávy s více než jedno záhlaví zprávy je zcela přijatelné.</span><span class="sxs-lookup"><span data-stu-id="8d61a-158">Having more than one message header in unwrapped messages is completely acceptable.</span></span>  
  
## <a name="using-custom-types-inside-message-contracts"></a><span data-ttu-id="8d61a-159">Použití vlastních typů uvnitř kontraktů zpráv</span><span class="sxs-lookup"><span data-stu-id="8d61a-159">Using Custom Types Inside Message Contracts</span></span>  
 <span data-ttu-id="8d61a-160">Každá hlavička jednotlivých zpráv a část textu zprávy serializován (převedena na XML) pomocí zvolené Serializační stroj pro servisní smlouvy použití zprávy.</span><span class="sxs-lookup"><span data-stu-id="8d61a-160">Each individual message header and message body part is serialized (turned into XML) using the chosen serialization engine for the service contract where the message is used.</span></span> <span data-ttu-id="8d61a-161">Modul výchozí serializace `XmlFormatter`, zvládne libovolný typ, který má kontraktu dat, buď explicitně (tím, že <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType>) nebo implicitně (tím je primitivního typu, které mají <xref:System.SerializableAttribute?displayProperty=nameWithType>, a tak dále).</span><span class="sxs-lookup"><span data-stu-id="8d61a-161">The default serialization engine, the `XmlFormatter`, can handle any type that has a data contract, either explicitly (by having the <xref:System.Runtime.Serialization.DataContractAttribute?displayProperty=nameWithType>) or implicitly (by being a primitive type, having the <xref:System.SerializableAttribute?displayProperty=nameWithType>, and so on).</span></span> <span data-ttu-id="8d61a-162">Další informace najdete v tématu [kontraktů dat pomocí](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="8d61a-162">For more information, see [Using Data Contracts](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).</span></span>  
  
 <span data-ttu-id="8d61a-163">V předchozím příkladu `Operation` a `BankingTransactionData` typy musí mít kontraktu dat, a `transactionDate` serializovat protože <xref:System.DateTime> je jednoduchého typu (a tedy má implicitní data).</span><span class="sxs-lookup"><span data-stu-id="8d61a-163">In the preceding example, the `Operation` and `BankingTransactionData` types must have a data contract, and `transactionDate` is serializable because <xref:System.DateTime> is a primitive (and so has an implicit data contract).</span></span>  
  
 <span data-ttu-id="8d61a-164">Je však možné přepnout na jinou Serializační stroj, `XmlSerializer`.</span><span class="sxs-lookup"><span data-stu-id="8d61a-164">However, it is possible to switch to a different serialization engine, the `XmlSerializer`.</span></span> <span data-ttu-id="8d61a-165">Pokud provedete tyto přepínače, měli byste zajistit, že všechny typy použité pro záhlaví zpráv a částí textu jsou serializovatelné pomocí `XmlSerializer`.</span><span class="sxs-lookup"><span data-stu-id="8d61a-165">If you make such a switch, you should ensure that all of the types used for message headers and body parts are serializable using the `XmlSerializer`.</span></span>  
  
## <a name="using-arrays-inside-message-contracts"></a><span data-ttu-id="8d61a-166">Použití polí uvnitř kontraktů zpráv</span><span class="sxs-lookup"><span data-stu-id="8d61a-166">Using Arrays Inside Message Contracts</span></span>  
 <span data-ttu-id="8d61a-167">Můžete použít pole opakující se elementy v kontraktů zpráv dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="8d61a-167">You can use arrays of repeating elements in message contracts in two ways.</span></span>  
  
 <span data-ttu-id="8d61a-168">První je použití <xref:System.ServiceModel.MessageHeaderAttribute> nebo <xref:System.ServiceModel.MessageBodyMemberAttribute> přímo na pole.</span><span class="sxs-lookup"><span data-stu-id="8d61a-168">The first is to use a <xref:System.ServiceModel.MessageHeaderAttribute> or a <xref:System.ServiceModel.MessageBodyMemberAttribute> directly on the array.</span></span> <span data-ttu-id="8d61a-169">V takovém případě celého pole je serializován jako jeden prvek (to znamená, že jedno záhlaví nebo jednu část textu) s více podřízenými prvky.</span><span class="sxs-lookup"><span data-stu-id="8d61a-169">In this case, the entire array is serialized as one element (that is, one header or one body part) with multiple child elements.</span></span> <span data-ttu-id="8d61a-170">Vezměte v úvahu třídu v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="8d61a-170">Consider the class in the following example.</span></span>  
  
```csharp  
[MessageContract]  
public class BankingDepositLog  
{  
  [MessageHeader] public int numRecords;  
  [MessageHeader] public DepositRecord[] records;  
  [MessageHeader] public int branchID;  
}  
```  
  
 <span data-ttu-id="8d61a-171">Výsledkem hlavičky SOAP je podobný následujícímu.</span><span class="sxs-lookup"><span data-stu-id="8d61a-171">This results in SOAP headers is similar to the following.</span></span>  
  
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
  
 <span data-ttu-id="8d61a-172">Alternativa k tomuto je použít <xref:System.ServiceModel.MessageHeaderArrayAttribute>.</span><span class="sxs-lookup"><span data-stu-id="8d61a-172">An alternative to this is to use the <xref:System.ServiceModel.MessageHeaderArrayAttribute>.</span></span> <span data-ttu-id="8d61a-173">V tomto případě nezávisle na sobě serializován každý prvek pole a tak pole, které každý prvek má jedno záhlaví, podobný následujícímu.</span><span class="sxs-lookup"><span data-stu-id="8d61a-173">In this case, each array element is serialized independently and so that each array element has one header, similar to the following.</span></span>  
  
```xml  
<numRecords>3</numRecords>  
<records>Record1</records>  
<records>Record2</records>  
<records>Record3</records>  
<branchID>20643</branchID>  
```  
  
 <span data-ttu-id="8d61a-174">Název členu, ke kterému je výchozí název položky pole <xref:System.ServiceModel.MessageHeaderArrayAttribute> použít atributy.</span><span class="sxs-lookup"><span data-stu-id="8d61a-174">The default name for array entries is the name of the member to which the <xref:System.ServiceModel.MessageHeaderArrayAttribute> attributes is applied.</span></span>  
  
 <span data-ttu-id="8d61a-175"><xref:System.ServiceModel.MessageHeaderArrayAttribute> Atributu inherits z <xref:System.ServiceModel.MessageHeaderAttribute>.</span><span class="sxs-lookup"><span data-stu-id="8d61a-175">The <xref:System.ServiceModel.MessageHeaderArrayAttribute> attribute inherits from the <xref:System.ServiceModel.MessageHeaderAttribute>.</span></span> <span data-ttu-id="8d61a-176">Má stejnou sadu funkcí jako atributy mimo pole, například je možné nastavit pořadí, název a obor názvů pro pole hlavičky stejným způsobem, který jste nastavili pro jednu hlavičku.</span><span class="sxs-lookup"><span data-stu-id="8d61a-176">It has the same set of features as the non-array attributes, for example, it is possible to set the order, name, and namespace for an array of headers in the same way you set it for a single header.</span></span> <span data-ttu-id="8d61a-177">Při použití `Order` vlastnost na pole, která se vztahuje na celý pole.</span><span class="sxs-lookup"><span data-stu-id="8d61a-177">When you use the `Order` property on an array, it applies to the entire array.</span></span>  
  
 <span data-ttu-id="8d61a-178">Můžete použít <xref:System.ServiceModel.MessageHeaderArrayAttribute> pouze na pole, nikoli kolekce.</span><span class="sxs-lookup"><span data-stu-id="8d61a-178">You can apply the <xref:System.ServiceModel.MessageHeaderArrayAttribute> only to arrays, not collections.</span></span>  
  
## <a name="using-byte-arrays-in-message-contracts"></a><span data-ttu-id="8d61a-179">Pomocí polí bajtů v kontraktů zpráv</span><span class="sxs-lookup"><span data-stu-id="8d61a-179">Using Byte Arrays in Message Contracts</span></span>  
 <span data-ttu-id="8d61a-180">Bajtová pole, při použití s atributy mimo pole (<xref:System.ServiceModel.MessageBodyMemberAttribute> a <xref:System.ServiceModel.MessageHeaderAttribute>), nemají být považována jako pole, ale jako speciální primitivní typ reprezentovaný jako data v výsledného kódu XML s kódováním Base64.</span><span class="sxs-lookup"><span data-stu-id="8d61a-180">Byte arrays, when used with the non-array attributes (<xref:System.ServiceModel.MessageBodyMemberAttribute> and <xref:System.ServiceModel.MessageHeaderAttribute>), are not treated as arrays but as a special primitive type represented as Base64-encoded data in the resulting XML.</span></span>  
  
 <span data-ttu-id="8d61a-181">Při použití pole bajtů s atributem pole <xref:System.ServiceModel.MessageHeaderArrayAttribute>, výsledek závisí na serializátoru, který je používán.</span><span class="sxs-lookup"><span data-stu-id="8d61a-181">When you use byte arrays with the array attribute <xref:System.ServiceModel.MessageHeaderArrayAttribute>, the results depend on the serializer in use.</span></span> <span data-ttu-id="8d61a-182">S výchozí serializátor pole je vyjádřena jako jednotlivé položky pro každý bajt.</span><span class="sxs-lookup"><span data-stu-id="8d61a-182">With the default serializer, the array is represented as an individual entry for each byte.</span></span> <span data-ttu-id="8d61a-183">Ale, když `XmlSerializer` je vybrána, (pomocí <xref:System.ServiceModel.XmlSerializerFormatAttribute> u kontraktu služby), bajtová pole jsou považovány za data ve formátu Base64, bez ohledu na to, zda pole nebo mimo pole atributy se používají.</span><span class="sxs-lookup"><span data-stu-id="8d61a-183">However, when the `XmlSerializer` is selected, (using the <xref:System.ServiceModel.XmlSerializerFormatAttribute> on the service contract), byte arrays are treated as Base64 data regardless of whether the array or non-array attributes are used.</span></span>  
  
## <a name="signing-and-encrypting-parts-of-the-message"></a><span data-ttu-id="8d61a-184">Podepisování a šifrování částí zprávy</span><span class="sxs-lookup"><span data-stu-id="8d61a-184">Signing and Encrypting Parts of the Message</span></span>  
 <span data-ttu-id="8d61a-185">Kontrakt zprávy můžete určit, zda záhlaví a text zprávy by měl být digitálně podepsat a zašifrovat.</span><span class="sxs-lookup"><span data-stu-id="8d61a-185">A message contract can indicate whether the headers and/or body of the message should be digitally signed and encrypted.</span></span>  
  
 <span data-ttu-id="8d61a-186">To se provádí tak, že nastavíte <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A?displayProperty=nameWithType> vlastnost <xref:System.ServiceModel.MessageHeaderAttribute> a <xref:System.ServiceModel.MessageBodyMemberAttribute> atributy.</span><span class="sxs-lookup"><span data-stu-id="8d61a-186">This is done by setting the <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A?displayProperty=nameWithType> property on the <xref:System.ServiceModel.MessageHeaderAttribute> and <xref:System.ServiceModel.MessageBodyMemberAttribute> attributes.</span></span> <span data-ttu-id="8d61a-187">Vlastnost je výčet <xref:System.Net.Security.ProtectionLevel?displayProperty=nameWithType> zadejte a může být nastaven na <xref:System.Net.Security.ProtectionLevel.None> (žádné šifrování nebo podpis), <xref:System.Net.Security.ProtectionLevel.Sign> (digitální podpis pouze), nebo <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> (šifrování a digitálním podpisem).</span><span class="sxs-lookup"><span data-stu-id="8d61a-187">The property is an enumeration of the <xref:System.Net.Security.ProtectionLevel?displayProperty=nameWithType> type and can be set to <xref:System.Net.Security.ProtectionLevel.None> (no encryption or signature), <xref:System.Net.Security.ProtectionLevel.Sign> (digital signature only), or <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> (both encryption and a digital signature).</span></span> <span data-ttu-id="8d61a-188">Výchozí hodnota je <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span><span class="sxs-lookup"><span data-stu-id="8d61a-188">The default is <xref:System.Net.Security.ProtectionLevel.EncryptAndSign>.</span></span>  
  
 <span data-ttu-id="8d61a-189">Pro fungování těchto funkcí zabezpečení musíte správně nakonfigurovat vazby a chování.</span><span class="sxs-lookup"><span data-stu-id="8d61a-189">For these security features to work, you must properly configure the binding and behaviors.</span></span> <span data-ttu-id="8d61a-190">Pokud používáte tyto funkce zabezpečení bez správnou konfiguraci (například pokus o přihlášení zprávu bez nutnosti zadávat svoje přihlašovací údaje), je vyvolána výjimka během ověřování.</span><span class="sxs-lookup"><span data-stu-id="8d61a-190">If you use these security features without the proper configuration (for example, attempting to sign a message without supplying your credentials), an exception is thrown at validation time.</span></span>  
  
 <span data-ttu-id="8d61a-191">Záhlaví zpráv úroveň ochrany je určeno jednotlivě pro každého záhlaví.</span><span class="sxs-lookup"><span data-stu-id="8d61a-191">For message headers, the protection level is determined individually for each header.</span></span>  
  
 <span data-ttu-id="8d61a-192">Pro zprávu částí textu aby úroveň ochrany můžete představit jako "minimální úroveň ochrany."</span><span class="sxs-lookup"><span data-stu-id="8d61a-192">For message body parts, the protection level can be thought of as the "minimum protection level."</span></span> <span data-ttu-id="8d61a-193">Text má pouze jeden ochranu úroveň, bez ohledu na počet částí textu.</span><span class="sxs-lookup"><span data-stu-id="8d61a-193">The body has only one protection level, regardless of the number of body parts.</span></span> <span data-ttu-id="8d61a-194">Úroveň ochrany obsahu je určeno nejvyšší <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A> nastavení vlastnosti všechny části textu.</span><span class="sxs-lookup"><span data-stu-id="8d61a-194">The protection level of the body is determined by the highest <xref:System.ServiceModel.MessageContractMemberAttribute.ProtectionLevel%2A> property setting of all the body parts.</span></span> <span data-ttu-id="8d61a-195">Nicméně byste měli nastavit úroveň ochrany každá část textu skutečné ochrany minimální úroveň požadovaných.</span><span class="sxs-lookup"><span data-stu-id="8d61a-195">However, you should set the protection level of each body part to the actual minimum protection level required.</span></span>  
  
 <span data-ttu-id="8d61a-196">Vezměte v úvahu třídu v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="8d61a-196">Consider the class in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="8d61a-197">V tomto příkladu `recordID` záhlaví není chráněný, `patientName` je `signed`, a `SSN` je šifrovaný a podepsaný.</span><span class="sxs-lookup"><span data-stu-id="8d61a-197">In this example, the `recordID` header is not protected, `patientName` is `signed`, and `SSN` is encrypted and signed.</span></span> <span data-ttu-id="8d61a-198">Část alespoň jeden textu `medicalHistory`, má <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> použít, a proto je obsah celé zprávy zašifrovaná a podepsaná, i když komentáře a částí textu diagnostiku zadejte nižší úrovně ochrany.</span><span class="sxs-lookup"><span data-stu-id="8d61a-198">At least one body part, `medicalHistory`, has <xref:System.Net.Security.ProtectionLevel.EncryptAndSign> applied, and thus the entire message body is encrypted and signed, even though the comments and diagnosis body parts specify lower protection levels.</span></span>  
  
## <a name="soap-action"></a><span data-ttu-id="8d61a-199">Akce SOAP</span><span class="sxs-lookup"><span data-stu-id="8d61a-199">SOAP Action</span></span>  
 <span data-ttu-id="8d61a-200">SOAP a související standardy webových služeb definovat vlastnost s názvem `Action` , může být k dispozici pro všechny zprávy protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="8d61a-200">SOAP and related Web services standards define a property called `Action` that can be present for every SOAP message sent.</span></span> <span data-ttu-id="8d61a-201">Operace <xref:System.ServiceModel.OperationContractAttribute.Action%2A?displayProperty=nameWithType> a <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A?displayProperty=nameWithType> vlastnosti řídí hodnota této vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="8d61a-201">The operation's <xref:System.ServiceModel.OperationContractAttribute.Action%2A?displayProperty=nameWithType> and <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A?displayProperty=nameWithType> properties control the value of this property.</span></span>  
  
## <a name="soap-header-attributes"></a><span data-ttu-id="8d61a-202">Atributy záhlaví SOAP</span><span class="sxs-lookup"><span data-stu-id="8d61a-202">SOAP Header Attributes</span></span>  
 <span data-ttu-id="8d61a-203">SOAP standard definuje následující atributy, které mohou existovat v hlavičce:</span><span class="sxs-lookup"><span data-stu-id="8d61a-203">The SOAP standard defines the following attributes that may exist on a header:</span></span>  
  
-   <span data-ttu-id="8d61a-204">`Actor/Role` (`Actor` v protokolu SOAP 1.1, `Role` v protokolu SOAP 1.2)</span><span class="sxs-lookup"><span data-stu-id="8d61a-204">`Actor/Role` (`Actor` in SOAP 1.1, `Role` in SOAP 1.2)</span></span>  
  
-   `MustUnderstand`  
  
-   `Relay`  
  
 <span data-ttu-id="8d61a-205">`Actor` Nebo `Role` Určuje atribut identifikátor URI (Uniform Resource) z uzlu, pro který je určený danou hlavičku.</span><span class="sxs-lookup"><span data-stu-id="8d61a-205">The `Actor` or `Role` attribute specifies the Uniform Resource Identifier (URI) of the node for which a given header is intended.</span></span> <span data-ttu-id="8d61a-206">`MustUnderstand` Atribut určuje, zda uzel zpracování záhlaví musí pochopit.</span><span class="sxs-lookup"><span data-stu-id="8d61a-206">The `MustUnderstand` attribute specifies whether the node processing the header must understand it.</span></span> <span data-ttu-id="8d61a-207">`Relay` Atribut určuje, zda záhlaví je možné předat do podřízené uzly.</span><span class="sxs-lookup"><span data-stu-id="8d61a-207">The `Relay` attribute specifies whether the header is to be relayed to downstream nodes.</span></span> <span data-ttu-id="8d61a-208">WCF neprovádí zpracování těchto atributů na příchozí zprávy, s výjimkou `MustUnderstand` atributu, jak je uvedeno v části "Správa verzí kontraktů zpráv" dále v tomto tématu.</span><span class="sxs-lookup"><span data-stu-id="8d61a-208">WCF does not perform any processing of these attributes on incoming messages, except for the `MustUnderstand` attribute, as specified in the "Message Contract Versioning" section later in this topic.</span></span> <span data-ttu-id="8d61a-209">Však umožňuje číst a zapisovat podle potřeby, stejně jako v následujícím popis těchto atributů.</span><span class="sxs-lookup"><span data-stu-id="8d61a-209">However, it allows you to read and write these attributes as necessary, as in the following description.</span></span>  
  
 <span data-ttu-id="8d61a-210">Při odesílání zprávy, nejsou ve výchozím nastavení zaznamenávány těchto atributů.</span><span class="sxs-lookup"><span data-stu-id="8d61a-210">When sending a message, these attributes are not emitted by default.</span></span> <span data-ttu-id="8d61a-211">Toto můžete změnit dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="8d61a-211">You can change this in two ways.</span></span> <span data-ttu-id="8d61a-212">Nejdřív, může staticky nastavíte atributy na všechny požadované hodnoty tak, že změníte <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.MessageHeaderAttribute.MustUnderstand%2A?displayProperty=nameWithType>, a <xref:System.ServiceModel.MessageHeaderAttribute.Relay%2A?displayProperty=nameWithType> vlastnosti, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="8d61a-212">First, you may statically set the attributes to any desired values by changing the <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A?displayProperty=nameWithType>, <xref:System.ServiceModel.MessageHeaderAttribute.MustUnderstand%2A?displayProperty=nameWithType>, and <xref:System.ServiceModel.MessageHeaderAttribute.Relay%2A?displayProperty=nameWithType> properties, as shown in the following code example.</span></span> <span data-ttu-id="8d61a-213">(Všimněte si, že neexistuje žádné `Role` vlastnost; nastavení <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A> vysílá vlastnost `Role` atribut, pokud používáte protokol SOAP 1.2).</span><span class="sxs-lookup"><span data-stu-id="8d61a-213">(Note that there is no `Role` property; setting the <xref:System.ServiceModel.MessageHeaderAttribute.Actor%2A> property emits the `Role` attribute if you are using SOAP 1.2).</span></span>  
  
```csharp  
[MessageContract]  
public class BankingTransaction  
{  
  [MessageHeader(Actor="http://auditingservice.contoso.com", MustUnderstand=true)] public bool IsAudited;  
  [MessageHeader] public Operation operation;  
  [MessageBodyMember] public BankingTransactionData theData;  
}  
```  
  
 <span data-ttu-id="8d61a-214">Druhý způsob, jak řídit tyto atributy se dynamicky prostřednictvím kódu.</span><span class="sxs-lookup"><span data-stu-id="8d61a-214">The second way to control these attributes is dynamically, through code.</span></span> <span data-ttu-id="8d61a-215">Lze toho dosáhnout obalením typ požadovaného záhlaví v <xref:System.ServiceModel.MessageHeader%601> typ (ujistěte se, abyste nezaměnili tohoto typu v obecné verzi) a s použitím typu spolu s <xref:System.ServiceModel.MessageHeaderAttribute>.</span><span class="sxs-lookup"><span data-stu-id="8d61a-215">You can achieve this by wrapping the desired header type in the <xref:System.ServiceModel.MessageHeader%601> type (be sure not to confuse this type with the non-generic version) and by using the type together with the <xref:System.ServiceModel.MessageHeaderAttribute>.</span></span> <span data-ttu-id="8d61a-216">Potom můžete použít vlastnosti na <xref:System.ServiceModel.MessageHeader%601> nastavení atributů protokolu SOAP, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="8d61a-216">Then, you can use properties on the <xref:System.ServiceModel.MessageHeader%601> to set the SOAP attributes, as shown in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="8d61a-217">Pokud používáte dynamické i statické kontrolní mechanismy, statické nastavení jsou použita jako výchozí, ale později se dá přepsat pomocí dynamické mechanismus, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="8d61a-217">If you use both the dynamic and the static control mechanisms, the static settings are used as a default but can later be overridden by using the dynamic mechanism, as shown in the following code.</span></span>  
  
```csharp  
[MessageHeader(MustUnderstand=true)] public MessageHeader<Person> documentApprover;  
// later on in the code:  
BankingTransaction bt = new BankingTransaction();  
bt.documentApprover = new MessageHeader<Person>();  
bt.documentApprover.MustUnderstand = false; // override the static default of 'true'  
```  
  
 <span data-ttu-id="8d61a-218">Vytvoření opakovaně záhlaví s ovládacím prvkem dynamického atributu je povoleno, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="8d61a-218">Creating repeated headers with dynamic attribute control is allowed, as shown in the following code.</span></span>  
  
```csharp  
[MessageHeaderArray] public MessageHeader<Person> documentApprovers[];  
```  
  
 <span data-ttu-id="8d61a-219">Na straně příjmu čtení těchto atributů protokolu SOAP lze pouze v případě, <xref:System.ServiceModel.MessageHeader%601> třída se používá pro záhlaví v typu.</span><span class="sxs-lookup"><span data-stu-id="8d61a-219">On the receiving side, reading these SOAP attributes can only be done if the <xref:System.ServiceModel.MessageHeader%601> class is used for the header in the type.</span></span> <span data-ttu-id="8d61a-220">Zkontrolujte `Actor`, `Relay`, nebo `MustUnderstand` vlastnosti s hlavičkou <xref:System.ServiceModel.MessageHeader%601> typu ke zjištění nastavení atributů na přijatou zprávu.</span><span class="sxs-lookup"><span data-stu-id="8d61a-220">Examine the `Actor`, `Relay`, or `MustUnderstand` properties of a header of the <xref:System.ServiceModel.MessageHeader%601> type to discover the attribute settings on the received message.</span></span>  
  
 <span data-ttu-id="8d61a-221">Pokud zprávu přijme a potom odeslány zpět, nastavení atributů protokolu SOAP, jdou pouze operace round-trip pro záhlaví <xref:System.ServiceModel.MessageHeader%601> typu.</span><span class="sxs-lookup"><span data-stu-id="8d61a-221">When a message is received and then sent back, the SOAP attribute settings only go round-trip for headers of the <xref:System.ServiceModel.MessageHeader%601> type.</span></span>  
  
## <a name="order-of-soap-body-parts"></a><span data-ttu-id="8d61a-222">Pořadí částí textu zprávy protokolu SOAP</span><span class="sxs-lookup"><span data-stu-id="8d61a-222">Order of SOAP Body Parts</span></span>  
 <span data-ttu-id="8d61a-223">V některých případech budete muset určit pořadí částí textu.</span><span class="sxs-lookup"><span data-stu-id="8d61a-223">In some circumstances, you may need to control the order of the body parts.</span></span> <span data-ttu-id="8d61a-224">Pořadí prvků textu je abecední ve výchozím nastavení, ale mohou být řízena <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="8d61a-224">The order of the body elements is alphabetical by default, but can be controlled by the <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="8d61a-225">Tato vlastnost má stejnou sémantiku jako <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A?displayProperty=nameWithType> vlastnost, s výjimkou chování ve scénářích dědičnosti (v kontraktů zpráv, základní typ těla členy nejsou seřazené před tělo členy odvozeného typu).</span><span class="sxs-lookup"><span data-stu-id="8d61a-225">This property has the same semantics as the <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A?displayProperty=nameWithType> property, except for the behavior in inheritance scenarios (in message contracts, base type body members are not sorted before the derived type body members).</span></span> <span data-ttu-id="8d61a-226">Další informace najdete v tématu [pořadí datových členů](../../../../docs/framework/wcf/feature-details/data-member-order.md).</span><span class="sxs-lookup"><span data-stu-id="8d61a-226">For more information, see [Data Member Order](../../../../docs/framework/wcf/feature-details/data-member-order.md).</span></span>  
  
 <span data-ttu-id="8d61a-227">V následujícím příkladu `amount` by obvykle pocházejí nejprve vzhledem k tomu, že je první podle abecedy.</span><span class="sxs-lookup"><span data-stu-id="8d61a-227">In the following example, `amount` would normally come first because it is first alphabetically.</span></span> <span data-ttu-id="8d61a-228">Ale <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A> vlastnost vloží je do třetí pozici.</span><span class="sxs-lookup"><span data-stu-id="8d61a-228">However, the <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A> property puts it into the third position.</span></span>  
  
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
  
## <a name="message-contract-versioning"></a><span data-ttu-id="8d61a-229">Správa verzí kontraktů zpráv</span><span class="sxs-lookup"><span data-stu-id="8d61a-229">Message Contract Versioning</span></span>  
 <span data-ttu-id="8d61a-230">V některých případech budete muset změnit kontraktů zpráv.</span><span class="sxs-lookup"><span data-stu-id="8d61a-230">Occasionally, you may need to change message contracts.</span></span> <span data-ttu-id="8d61a-231">Novou verzi vaší aplikace může například přidat další záhlaví zprávy.</span><span class="sxs-lookup"><span data-stu-id="8d61a-231">For example, a new version of your application may add an extra header to a message.</span></span> <span data-ttu-id="8d61a-232">Pak při odesílání z nové verze původní, systém musí zabývat dodatečné hlavičky, jakož i chybí hlavička při přechodu v opačném směru.</span><span class="sxs-lookup"><span data-stu-id="8d61a-232">Then, when sending from the new version to the old, the system must deal with an extra header, as well as a missing header when going in the other direction.</span></span>  
  
 <span data-ttu-id="8d61a-233">Pro správu verzí hlavičky platí následující pravidla:</span><span class="sxs-lookup"><span data-stu-id="8d61a-233">The following rules apply for versioning headers:</span></span>  
  
-   <span data-ttu-id="8d61a-234">WCF není objekt pro chybějící záhlaví – odpovídající členů jsou ponechány na výchozích hodnotách.</span><span class="sxs-lookup"><span data-stu-id="8d61a-234">WCF does not object to the missing headers—the corresponding members are left at their default values.</span></span>  
  
-   <span data-ttu-id="8d61a-235">WCF rovněž ignoruje neočekávané dodatečné hlavičky.</span><span class="sxs-lookup"><span data-stu-id="8d61a-235">WCF also ignores unexpected extra headers.</span></span> <span data-ttu-id="8d61a-236">Jedinou výjimkou tohoto pravidla je, pokud má navíc záhlaví `MustUnderstand` atribut nastaven na `true` v příchozí zprávě SOAP – v takovém případě je vyvolána výjimka, protože nelze zpracovat hlavičku, která musí být srozumitelný.</span><span class="sxs-lookup"><span data-stu-id="8d61a-236">The one exception to this rule is if the extra header has a `MustUnderstand` attribute set to `true` in the incoming SOAP message—in this case, an exception is thrown because a header that must be understood cannot be processed.</span></span>  
  
 <span data-ttu-id="8d61a-237">Zpráva úřadů, které mají podobné pravidla správy verzí – chybí a dalších částí textu zprávy jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="8d61a-237">Message bodies have similar versioning rules—both missing and additional message body parts are ignored.</span></span>  
  
## <a name="inheritance-considerations"></a><span data-ttu-id="8d61a-238">Důležité informace o dědičnosti</span><span class="sxs-lookup"><span data-stu-id="8d61a-238">Inheritance Considerations</span></span>  
 <span data-ttu-id="8d61a-239">Typ kontraktu zprávy může dědit z jiného typu, jako základní typ také obsahuje kontrakt zprávy.</span><span class="sxs-lookup"><span data-stu-id="8d61a-239">A message contract type can inherit from another type, as long as the base type also has a message contract.</span></span>  
  
 <span data-ttu-id="8d61a-240">Při vytváření nebo přístup k zprávu pomocí typ kontraktu zprávy, která dědí z jiných typů kontraktu zprávy, platí následující pravidla:</span><span class="sxs-lookup"><span data-stu-id="8d61a-240">When creating or accessing a message using a message contract type that inherits from other message contract types, the following rules apply:</span></span>  
  
-   <span data-ttu-id="8d61a-241">Všechny hlavičky zprávy v hierarchii dědičnosti shromažďují společně tvoří úplnou sadu záhlaví zprávy.</span><span class="sxs-lookup"><span data-stu-id="8d61a-241">All of the message headers in the inheritance hierarchy are collected together to form the full set of headers for the message.</span></span>  
  
-   <span data-ttu-id="8d61a-242">Všechny části textu zprávy v hierarchii dědičnosti shromažďují společně tvoří obsah celé zprávy.</span><span class="sxs-lookup"><span data-stu-id="8d61a-242">All of the message body parts in the inheritance hierarchy are collected together to form the full message body.</span></span> <span data-ttu-id="8d61a-243">Částí textu jsou řazeny podle obvyklých pravidel řazení (podle <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> vlastnost a potom abecedy), s žádný vztah k jejich místo v hierarchii dědičnosti.</span><span class="sxs-lookup"><span data-stu-id="8d61a-243">The body parts are ordered according to the usual ordering rules (by <xref:System.ServiceModel.MessageBodyMemberAttribute.Order%2A?displayProperty=nameWithType> property and then alphabetical), with no relevance to their place in the inheritance hierarchy.</span></span> <span data-ttu-id="8d61a-244">Pomocí dědičnosti kontraktu zprávy, pokud dojde k částí textu zprávy na více úrovních strom dědičnosti se důrazně nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="8d61a-244">Using message contract inheritance where message body parts occur at multiple levels of the inheritance tree is strongly discouraged.</span></span> <span data-ttu-id="8d61a-245">Pokud základní třída a odvozené třídy definují záhlaví nebo část textu se stejným názvem, člen ze třídy base většinu se používá pro ukládání hodnoty horní části Hlavička nebo text.</span><span class="sxs-lookup"><span data-stu-id="8d61a-245">If a base class and a derived class define a header or a body part with the same name, the member from the base-most class is used to store the value of that header or body part.</span></span>  
  
 <span data-ttu-id="8d61a-246">Vezměte v úvahu třídy v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="8d61a-246">Consider the classes in the following code example.</span></span>  
  
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
  
 <span data-ttu-id="8d61a-247">`PatientRecord` Třída popisuje zprávy jednu hlavičku s názvem `ID`.</span><span class="sxs-lookup"><span data-stu-id="8d61a-247">The `PatientRecord` class describes a message with one header called `ID`.</span></span> <span data-ttu-id="8d61a-248">Odpovídá záhlaví `personID` a ne `patientID` člena, protože většina základní člen je vybrán.</span><span class="sxs-lookup"><span data-stu-id="8d61a-248">The header corresponds to the `personID` and not the `patientID` member, because the base-most member is chosen.</span></span> <span data-ttu-id="8d61a-249">To znamená `patientID` pole v tomto případě je zbytečné.</span><span class="sxs-lookup"><span data-stu-id="8d61a-249">Thus, the `patientID` field is useless in this case.</span></span> <span data-ttu-id="8d61a-250">Tělo zprávy obsahuje `diagnosis` element, za nímž následuje `patientName` element, protože, který je v abecedním pořadí.</span><span class="sxs-lookup"><span data-stu-id="8d61a-250">The body of the message contains the `diagnosis` element followed by the `patientName` element, because that is the alphabetical order.</span></span> <span data-ttu-id="8d61a-251">Všimněte si, že v příkladu ukazuje vzor, který se důrazně nedoporučuje: základních a odvozených zpráv kontrakty mají částí textu zprávy.</span><span class="sxs-lookup"><span data-stu-id="8d61a-251">Notice that the example shows a pattern that is strongly discouraged: both the base and the derived message contracts have message body parts.</span></span>  
  
## <a name="wsdl-considerations"></a><span data-ttu-id="8d61a-252">Důležité informace o WSDL</span><span class="sxs-lookup"><span data-stu-id="8d61a-252">WSDL Considerations</span></span>  
 <span data-ttu-id="8d61a-253">Při generování kontraktu webové služby WSDL (Description Language) ze služby, která používá zprávy smlouvy, je dobré si uvědomit, že ne všechny funkce kontraktu zprávy, se projeví v výsledný WSDL.</span><span class="sxs-lookup"><span data-stu-id="8d61a-253">When generating a Web Services Description Language (WSDL) contract from a service that uses message contracts, it is important to remember that not all message contract features are reflected in the resulting WSDL.</span></span> <span data-ttu-id="8d61a-254">Vezměte v úvahu následující body:</span><span class="sxs-lookup"><span data-stu-id="8d61a-254">Consider the following points:</span></span>  
  
-   <span data-ttu-id="8d61a-255">WSDL nelze vyjádřit pojem pole záhlaví.</span><span class="sxs-lookup"><span data-stu-id="8d61a-255">WSDL cannot express the concept of an array of headers.</span></span> <span data-ttu-id="8d61a-256">Při vytváření zprávy s pole záhlaví pomocí <xref:System.ServiceModel.MessageHeaderArrayAttribute>, pouze jedno záhlaví místo pole odráží výsledný WSDL.</span><span class="sxs-lookup"><span data-stu-id="8d61a-256">When creating messages with an array of headers using the <xref:System.ServiceModel.MessageHeaderArrayAttribute>, the resulting WSDL reflects only one header instead of the array.</span></span>  
  
-   <span data-ttu-id="8d61a-257">Výsledné dokument WSDL nemusí odrážet některé informace úroveň ochrany.</span><span class="sxs-lookup"><span data-stu-id="8d61a-257">The resulting WSDL document may not reflect some protection-level information.</span></span>  
  
-   <span data-ttu-id="8d61a-258">Typ zprávy generované ve schématu WSDL má stejný název jako název třídy typu kontraktu zprávy.</span><span class="sxs-lookup"><span data-stu-id="8d61a-258">The message type generated in the WSDL has the same name as the class name of the message contract type.</span></span>  
  
-   <span data-ttu-id="8d61a-259">Při použití stejné zprávy smlouvy ve více operací, více typy zpráv jsou generovány v dokumentu WSDL.</span><span class="sxs-lookup"><span data-stu-id="8d61a-259">When using the same message contract in multiple operations, multiple message types are generated in the WSDL document.</span></span> <span data-ttu-id="8d61a-260">Přidáním čísel "2", "3" a tak dále, pro následující účely, jsou provedeny jedinečné názvy.</span><span class="sxs-lookup"><span data-stu-id="8d61a-260">The names are made unique by adding the numbers "2", "3", and so on, for subsequent uses.</span></span> <span data-ttu-id="8d61a-261">Když importujete zpět WSDL, více typy kontraktů zpráv jsou vytvořeny a jsou stejné s výjimkou jejich názvy.</span><span class="sxs-lookup"><span data-stu-id="8d61a-261">When importing back the WSDL, multiple message contract types are created and are identical except for their names.</span></span>  
  
## <a name="soap-encoding-considerations"></a><span data-ttu-id="8d61a-262">Důležité informace o kódování SOAP</span><span class="sxs-lookup"><span data-stu-id="8d61a-262">SOAP Encoding Considerations</span></span>  
 <span data-ttu-id="8d61a-263">WCF umožňuje použít starší verzi protokolu SOAP kódování styl XML, ale jeho použití nedoporučuje.</span><span class="sxs-lookup"><span data-stu-id="8d61a-263">WCF allows you to use the legacy SOAP encoding style of XML, however, its use is not recommended.</span></span> <span data-ttu-id="8d61a-264">Při použití tohoto stylu (nastavením `Use` vlastnost `Encoded` na <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType> u kontraktu služby), platí následující další aspekty:</span><span class="sxs-lookup"><span data-stu-id="8d61a-264">When using this style (by setting the `Use` property to `Encoded` on the <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType> applied to the service contract), the following additional considerations apply:</span></span>  
  
-   <span data-ttu-id="8d61a-265">Záhlaví zpráv nejsou podporovány. To znamená, že atribut <xref:System.ServiceModel.MessageHeaderAttribute> a atribut pole <xref:System.ServiceModel.MessageHeaderArrayAttribute> nejsou kompatibilní s kódováním SOAP.</span><span class="sxs-lookup"><span data-stu-id="8d61a-265">The message headers are not supported; this means that the attribute <xref:System.ServiceModel.MessageHeaderAttribute> and the array attribute <xref:System.ServiceModel.MessageHeaderArrayAttribute> are incompatible with SOAP encoding.</span></span>  
  
-   <span data-ttu-id="8d61a-266">Pokud kontrakt zprávy není zabalena, to znamená, pokud vlastnost <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> je nastavena na `false`, kontrakt zprávy může mít část textu pouze jeden.</span><span class="sxs-lookup"><span data-stu-id="8d61a-266">If the message contract is not wrapped, that is, if the property <xref:System.ServiceModel.MessageContractAttribute.IsWrapped%2A> is set to `false`, the message contract can have only one body part.</span></span>  
  
-   <span data-ttu-id="8d61a-267">Název prvku obálky pro kontrakt zprávy požadavku musí odpovídat názvu operace.</span><span class="sxs-lookup"><span data-stu-id="8d61a-267">The name of the wrapper element for the request message contract must match the operation name.</span></span> <span data-ttu-id="8d61a-268">Použití `WrapperName` kontraktu zprávy pro tuto vlastnost.</span><span class="sxs-lookup"><span data-stu-id="8d61a-268">Use the `WrapperName` property of the message contract for this.</span></span>  
  
-   <span data-ttu-id="8d61a-269">Název prvku obálky pro kontrakt zprávy odpovědi musí být stejný jako název operace příponou podle "Odpověď".</span><span class="sxs-lookup"><span data-stu-id="8d61a-269">The name of the wrapper element for the response message contract must be the same as the name of the operation suffixed by 'Response'.</span></span> <span data-ttu-id="8d61a-270">Použití <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> kontraktu zprávy pro tuto vlastnost.</span><span class="sxs-lookup"><span data-stu-id="8d61a-270">Use the <xref:System.ServiceModel.MessageContractAttribute.WrapperName%2A> property of the message contract for this.</span></span>  
  
-   <span data-ttu-id="8d61a-271">Kódování SOAP zachová odkazy na objekty.</span><span class="sxs-lookup"><span data-stu-id="8d61a-271">SOAP encoding preserves object references.</span></span> <span data-ttu-id="8d61a-272">Zvažte například následující kód.</span><span class="sxs-lookup"><span data-stu-id="8d61a-272">For example, consider the following code.</span></span>  
  
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
  
 <span data-ttu-id="8d61a-273">Po serializaci zprávy s kódováním SOAP `changedFrom` a `changedTo` neobsahují své vlastní kopie `p`, ale místo toho přejděte na kopírování uvnitř `changedBy` elementu.</span><span class="sxs-lookup"><span data-stu-id="8d61a-273">After serializing the message using SOAP encoding, `changedFrom` and `changedTo` do not contain their own copies of `p`, but instead point to the copy inside the `changedBy` element.</span></span>  
  
## <a name="performance-considerations"></a><span data-ttu-id="8d61a-274">Faktory ovlivňující výkon</span><span class="sxs-lookup"><span data-stu-id="8d61a-274">Performance Considerations</span></span>  
 <span data-ttu-id="8d61a-275">Každý záhlaví zprávy a část textu zprávy serializován nezávisle na ostatních.</span><span class="sxs-lookup"><span data-stu-id="8d61a-275">Every message header and message body part is serialized independently of the others.</span></span> <span data-ttu-id="8d61a-276">Proto stejné obory názvů mohou být deklarovány opakujte pro každou část textu a záhlaví.</span><span class="sxs-lookup"><span data-stu-id="8d61a-276">Therefore, the same namespaces can be declared again for each header and body part.</span></span> <span data-ttu-id="8d61a-277">Kvůli zvýšení výkonu, zejména z hlediska velikosti zpráv na lince, konsolidovat více záhlaví a částí textu do jedné části Hlavička nebo text.</span><span class="sxs-lookup"><span data-stu-id="8d61a-277">To improve performance, especially in terms of the size of the message on the wire, consolidate multiple headers and body parts into a single header or body part.</span></span> <span data-ttu-id="8d61a-278">Například místo následující kód:</span><span class="sxs-lookup"><span data-stu-id="8d61a-278">For example, instead of the following code:</span></span>  
  
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
  
 <span data-ttu-id="8d61a-279">Pomocí tohoto kódu.</span><span class="sxs-lookup"><span data-stu-id="8d61a-279">Use this code.</span></span>  
  
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
  
### <a name="event-based-asynchronous-and-message-contracts"></a><span data-ttu-id="8d61a-280">Založený na událostech asynchronní a kontrakty zprávy</span><span class="sxs-lookup"><span data-stu-id="8d61a-280">Event-based Asynchronous and Message Contracts</span></span>  
 <span data-ttu-id="8d61a-281">Pokyny návrhu pro asynchronní model založený na událostech stát, že pokud se vrátí více než jednu hodnotu, se vrátí jednu hodnotu jako `Result` vlastnosti a ostatní jsou vrácena jako vlastnosti na <xref:System.EventArgs> objektu.</span><span class="sxs-lookup"><span data-stu-id="8d61a-281">The design guidelines for the event-based asynchronous model state that if more than one value is returned, one value is returned as the `Result` property and the others are returned as properties on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="8d61a-282">Jeden výsledek tohoto je, že pokud klient naimportuje metadata pomocí možnosti založené na událostech asynchronního příkazu a operace vrátí více než jednu hodnotu, výchozí <xref:System.EventArgs> objekt vrátí jednu hodnotu jako `Result` vlastnost a zbývající jsou vlastnosti <xref:System.EventArgs> objektu.</span><span class="sxs-lookup"><span data-stu-id="8d61a-282">One result of this is that if a client imports metadata using the event-based asynchronous command options and the operation returns more than one value, the default <xref:System.EventArgs> object returns one value as the `Result` property and the remainder are properties of the <xref:System.EventArgs> object.</span></span>  
  
 <span data-ttu-id="8d61a-283">Pokud chcete přijímat zprávy objektu jako `Result` vlastnost a vrácené hodnoty jako vlastnosti objektu, použijte `/messageContract` možnost příkazu.</span><span class="sxs-lookup"><span data-stu-id="8d61a-283">If you want to receive the message object as the `Result` property and have the returned values as properties on that object, use the `/messageContract` command option.</span></span> <span data-ttu-id="8d61a-284">Tím se vygeneruje podpis, který vrací zprávy s odpovědí jako `Result` vlastnost <xref:System.EventArgs> objektu.</span><span class="sxs-lookup"><span data-stu-id="8d61a-284">This generates a signature that returns the response message as the `Result` property on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="8d61a-285">Všechny interní vrácené hodnoty jsou pak vlastnosti objektu zprávu odpovědi.</span><span class="sxs-lookup"><span data-stu-id="8d61a-285">All internal return values are then properties of the response message object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d61a-286">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8d61a-286">See also</span></span>
- [<span data-ttu-id="8d61a-287">Použití kontraktů dat</span><span class="sxs-lookup"><span data-stu-id="8d61a-287">Using Data Contracts</span></span>](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [<span data-ttu-id="8d61a-288">Navrhování a implementace služeb</span><span class="sxs-lookup"><span data-stu-id="8d61a-288">Designing and Implementing Services</span></span>](../../../../docs/framework/wcf/designing-and-implementing-services.md)
