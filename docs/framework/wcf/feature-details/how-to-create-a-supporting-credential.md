---
title: 'Postupy: Vytvoření podpůrného pověření'
ms.date: 03/30/2017
ms.assetid: d0952919-8bb4-4978-926c-9cc108f89806
ms.openlocfilehash: 1f95748235aa5238193b8869f8330f0a7fc650d9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968902"
---
# <a name="how-to-create-a-supporting-credential"></a><span data-ttu-id="edf41-102">Postupy: Vytvoření podpůrného pověření</span><span class="sxs-lookup"><span data-stu-id="edf41-102">How to: Create a Supporting Credential</span></span>
<span data-ttu-id="edf41-103">Je možné mít vlastní schéma zabezpečení, které vyžaduje více než jedno přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="edf41-103">It is possible to have a custom security scheme that requires more than one credential.</span></span> <span data-ttu-id="edf41-104">Například služba může vyžadovat od klienta nejen uživatelské jméno a heslo, ale také přihlašovací údaje, které klienta prokáže za stáří 18.</span><span class="sxs-lookup"><span data-stu-id="edf41-104">For example, a service may demand from the client not just a user name and password, but also a credential that proves the client is over the age of 18.</span></span> <span data-ttu-id="edf41-105">Druhá přihlašovací údaje jsou *podpůrná pověření*.</span><span class="sxs-lookup"><span data-stu-id="edf41-105">The second credential is a *supporting credential*.</span></span> <span data-ttu-id="edf41-106">Toto téma vysvětluje, jak implementovat takové přihlašovací údaje v klientovi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="edf41-106">This topic explains how to implement such credentials in an Windows Communication Foundation (WCF) client.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="edf41-107">Specifikace pro podpůrná pověření je součástí specifikace WS-SecurityPolicy.</span><span class="sxs-lookup"><span data-stu-id="edf41-107">The specification for supporting credentials is part of the WS-SecurityPolicy specification.</span></span> <span data-ttu-id="edf41-108">Další informace najdete v článku [specifikace specifikace Web Services Security](https://go.microsoft.com/fwlink/?LinkId=88537).</span><span class="sxs-lookup"><span data-stu-id="edf41-108">For more information, see [Web Services Security Specifications](https://go.microsoft.com/fwlink/?LinkId=88537).</span></span>  
  
## <a name="supporting-tokens"></a><span data-ttu-id="edf41-109">Podpora tokenů</span><span class="sxs-lookup"><span data-stu-id="edf41-109">Supporting Tokens</span></span>  
 <span data-ttu-id="edf41-110">V krátké době se při použití zabezpečení zprávy *primární přihlašovací údaj* vždycky používá k zabezpečení zprávy (například certifikát X. 509 nebo lístek Kerberos).</span><span class="sxs-lookup"><span data-stu-id="edf41-110">In brief, when you use message security, a *primary credential* is always used to secure the message (for example, an X.509 certificate or a Kerberos ticket).</span></span>  
  
 <span data-ttu-id="edf41-111">Jak je definováno specifikací, vazba zabezpečení používá tokeny k zabezpečení výměny zpráv.</span><span class="sxs-lookup"><span data-stu-id="edf41-111">As defined by the specification, a security binding uses *tokens* to secure the message exchange.</span></span> <span data-ttu-id="edf41-112">*Token* je reprezentace bezpečnostního pověření.</span><span class="sxs-lookup"><span data-stu-id="edf41-112">A *token* is a representation of a security credential.</span></span>  
  
 <span data-ttu-id="edf41-113">Vazba zabezpečení používá primární token identifikovaný v zásadách vazby zabezpečení k vytvoření podpisu.</span><span class="sxs-lookup"><span data-stu-id="edf41-113">The security binding uses a primary token identified in the security binding policy to create a signature.</span></span> <span data-ttu-id="edf41-114">Tento podpis je označován jako *podpis zprávy*.</span><span class="sxs-lookup"><span data-stu-id="edf41-114">This signature is referred to as the *message signature*.</span></span>  
  
 <span data-ttu-id="edf41-115">Další tokeny lze zadat pro rozšíření deklarací poskytovaných tokenem, který je přidružen k podpisu zprávy.</span><span class="sxs-lookup"><span data-stu-id="edf41-115">Additional tokens can be specified to augment the claims provided by the token associated with the message signature.</span></span>  
  
## <a name="endorsing-signing-and-encrypting"></a><span data-ttu-id="edf41-116">Registrace, podepisování a šifrování</span><span class="sxs-lookup"><span data-stu-id="edf41-116">Endorsing, Signing, and Encrypting</span></span>  
 <span data-ttu-id="edf41-117">Výsledkem doprovodného pověření je *podpůrná token* , který se v rámci zprávy přenáší.</span><span class="sxs-lookup"><span data-stu-id="edf41-117">A supporting credential results in a *supporting token* transmitted inside the message.</span></span> <span data-ttu-id="edf41-118">Specifikace WS-SecurityPolicy definuje čtyři způsoby připojení podpůrného tokenu ke zprávě, jak je popsáno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="edf41-118">The WS-SecurityPolicy specification defines four ways to attach a supporting token to the message, as described in the following table.</span></span>  
  
|<span data-ttu-id="edf41-119">Účel</span><span class="sxs-lookup"><span data-stu-id="edf41-119">Purpose</span></span>|<span data-ttu-id="edf41-120">Popis</span><span class="sxs-lookup"><span data-stu-id="edf41-120">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="edf41-121">Podpisy</span><span class="sxs-lookup"><span data-stu-id="edf41-121">Signed</span></span>|<span data-ttu-id="edf41-122">Token podpory je obsažen v záhlaví zabezpečení a je podepsán podpisem zprávy.</span><span class="sxs-lookup"><span data-stu-id="edf41-122">The supporting token is included in the security header and is signed by the message signature.</span></span>|  
|<span data-ttu-id="edf41-123">Potvrzující</span><span class="sxs-lookup"><span data-stu-id="edf41-123">Endorsing</span></span>|<span data-ttu-id="edf41-124">*Token* , který podepisuje, podepíše podpis zprávy.</span><span class="sxs-lookup"><span data-stu-id="edf41-124">An *endorsing token* signs the message signature.</span></span>|  
|<span data-ttu-id="edf41-125">Podepsaná a schválená</span><span class="sxs-lookup"><span data-stu-id="edf41-125">Signed and Endorsing</span></span>|<span data-ttu-id="edf41-126">Podepsané a registrační tokeny podepisují celý `ds:Signature` prvek vytvořený z podpisu zprávy a jsou podepsaný podpisem zprávy; to znamená, že obě tokeny (token použitý pro podpis zprávy a podepsaný registrační token) jsou navzájem podepsané.</span><span class="sxs-lookup"><span data-stu-id="edf41-126">Signed, endorsing tokens sign the entire `ds:Signature` element produced from the message signature and are themselves signed by that message signature; that is, both tokens (the token used for the message signature and the signed endorsing token) sign each other.</span></span>|  
|<span data-ttu-id="edf41-127">Podepsané a šifrované</span><span class="sxs-lookup"><span data-stu-id="edf41-127">Signed and Encrypting</span></span>|<span data-ttu-id="edf41-128">Podepsané, šifrované podpůrné tokeny jsou podepsané podpůrnými tokeny, které jsou také zašifrovány, když se objeví v `wsse:SecurityHeader`.</span><span class="sxs-lookup"><span data-stu-id="edf41-128">Signed, encrypted supporting tokens are signed supporting tokens that are also encrypted when they appear in the `wsse:SecurityHeader`.</span></span>|  
  
## <a name="programming-supporting-credentials"></a><span data-ttu-id="edf41-129">Programování podporující přihlašovací údaje</span><span class="sxs-lookup"><span data-stu-id="edf41-129">Programming Supporting Credentials</span></span>  
 <span data-ttu-id="edf41-130">Pokud chcete vytvořit službu, která používá podpůrné tokeny, musíte vytvořit [ \<CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="edf41-130">To create a service that uses supporting tokens you must create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span> <span data-ttu-id="edf41-131">(Další informace najdete v tématu [postup: Vytvoření vlastní vazby pomocí SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).)</span><span class="sxs-lookup"><span data-stu-id="edf41-131">(For more information, see [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).)</span></span>  
  
 <span data-ttu-id="edf41-132">Prvním krokem při vytváření vlastní vazby je vytvoření elementu vazby zabezpečení, který může být jeden ze tří typů:</span><span class="sxs-lookup"><span data-stu-id="edf41-132">The first step when creating a custom binding is to create a security binding element, which can be one of three types:</span></span>  
  
- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
  
- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
  
- <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 <span data-ttu-id="edf41-133">Všechny třídy dědí z <xref:System.ServiceModel.Channels.SecurityBindingElement>, který obsahuje čtyři relevantní vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="edf41-133">All classes inherit from the <xref:System.ServiceModel.Channels.SecurityBindingElement>, which includes four relevant properties:</span></span>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.EndpointSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OperationSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalEndpointSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalOperationSupportingTokenParameters%2A>  
  
#### <a name="scopes"></a><span data-ttu-id="edf41-134">Oboru</span><span class="sxs-lookup"><span data-stu-id="edf41-134">Scopes</span></span>  
 <span data-ttu-id="edf41-135">Pro podpůrná pověření existují dva obory:</span><span class="sxs-lookup"><span data-stu-id="edf41-135">Two scopes exist for supporting credentials:</span></span>  
  
- <span data-ttu-id="edf41-136">*Tokeny podporující koncové body* podporují všechny operace koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="edf41-136">*Endpoint supporting tokens* support all operations of an endpoint.</span></span> <span data-ttu-id="edf41-137">To znamená, že přihlašovací údaje, které podpůrný token představuje, lze použít při každém vyvolání všech operací koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="edf41-137">That is, the credential that the supporting token represents can be used whenever any endpoint operations are invoked.</span></span>  
  
- <span data-ttu-id="edf41-138">*Operace podporující tokeny* podporují pouze konkrétní operaci koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="edf41-138">*Operation supporting tokens* support only a specific endpoint operation.</span></span>  
  
 <span data-ttu-id="edf41-139">Jak je uvedeno v názvech vlastností, mohou být podpůrná pověření buď povinná, nebo volitelná.</span><span class="sxs-lookup"><span data-stu-id="edf41-139">As indicated by the property names, supporting credentials can be either required or optional.</span></span> <span data-ttu-id="edf41-140">To znamená, že pokud je podpůrná pověření použita, je-li k dispozici, ale není nutné, ověřování nebude úspěšné, pokud není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="edf41-140">That is, if the supporting credential is used if it is present, although it is not necessary, but the authentication will not fail if it is not present.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="edf41-141">Procedury</span><span class="sxs-lookup"><span data-stu-id="edf41-141">Procedures</span></span>  
  
#### <a name="to-create-a-custom-binding-that-includes-supporting-credentials"></a><span data-ttu-id="edf41-142">Vytvoření vlastní vazby, která zahrnuje podpůrná pověření</span><span class="sxs-lookup"><span data-stu-id="edf41-142">To create a custom binding that includes supporting credentials</span></span>  
  
1. <span data-ttu-id="edf41-143">Vytvořte prvek vazby zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="edf41-143">Create a security binding element.</span></span> <span data-ttu-id="edf41-144">Následující příklad vytvoří <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> `UserNameForCertificate` s režimem ověřování.</span><span class="sxs-lookup"><span data-stu-id="edf41-144">The example below creates a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> with the `UserNameForCertificate` authentication mode.</span></span> <span data-ttu-id="edf41-145"><xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> Použijte metodu.</span><span class="sxs-lookup"><span data-stu-id="edf41-145">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> method.</span></span>  
  
2. <span data-ttu-id="edf41-146">Přidejte podpůrný parametr do kolekce typů vrácených příslušnou vlastností`Endorsing`(, `Signed`, `SignedEncrypted`nebo `SignedEndorsed`).</span><span class="sxs-lookup"><span data-stu-id="edf41-146">Add the supporting parameter to the collection of types returned by the appropriate property (`Endorsing`, `Signed`, `SignedEncrypted`, or `SignedEndorsed`).</span></span> <span data-ttu-id="edf41-147">Typy v <xref:System.ServiceModel.Security.Tokens> oboru názvů obsahují běžně používané typy, jako je <xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters>například.</span><span class="sxs-lookup"><span data-stu-id="edf41-147">The types in the <xref:System.ServiceModel.Security.Tokens> namespace include commonly used types, such as the <xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="edf41-148">Příklad</span><span class="sxs-lookup"><span data-stu-id="edf41-148">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="edf41-149">Popis</span><span class="sxs-lookup"><span data-stu-id="edf41-149">Description</span></span>  
 <span data-ttu-id="edf41-150">Následující příklad vytvoří instanci <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> <xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> třídy a přidá do kolekce instanci třídy, kterou vrátila vlastnost potvrdit.</span><span class="sxs-lookup"><span data-stu-id="edf41-150">The following example creates an instance of the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and adds an instance of the <xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> class to the collection the Endorsing property returned.</span></span>  
  
### <a name="code"></a><span data-ttu-id="edf41-151">Kód</span><span class="sxs-lookup"><span data-stu-id="edf41-151">Code</span></span>  
 [!code-csharp[c_SupportingCredential#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_supportingcredential/cs/source.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="edf41-152">Viz také:</span><span class="sxs-lookup"><span data-stu-id="edf41-152">See also</span></span>

- [<span data-ttu-id="edf41-153">Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="edf41-153">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
