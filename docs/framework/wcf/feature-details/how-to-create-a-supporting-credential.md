---
title: 'Postupy: vytvoření přihlašovacích údajů podpora'
ms.date: 03/30/2017
ms.assetid: d0952919-8bb4-4978-926c-9cc108f89806
ms.openlocfilehash: 6ec7412d1de2bca349c7cfbf4a37c98ca60cc78d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33495883"
---
# <a name="how-to-create-a-supporting-credential"></a><span data-ttu-id="bc89d-102">Postupy: vytvoření přihlašovacích údajů podpora</span><span class="sxs-lookup"><span data-stu-id="bc89d-102">How to: Create a Supporting Credential</span></span>
<span data-ttu-id="bc89d-103">Je možné, že schéma vlastní zabezpečení, která vyžaduje více než jedno pověření.</span><span class="sxs-lookup"><span data-stu-id="bc89d-103">It is possible to have a custom security scheme that requires more than one credential.</span></span> <span data-ttu-id="bc89d-104">Například služby vyžádat z klienta nejen uživatelské jméno a heslo, ale také přihlašovacích údajů, který prokáže, klient je víc než 18.</span><span class="sxs-lookup"><span data-stu-id="bc89d-104">For example, a service may demand from the client not just a user name and password, but also a credential that proves the client is over the age of 18.</span></span> <span data-ttu-id="bc89d-105">Druhý přihlašovací údaje *podpora přihlašovacích údajů*.</span><span class="sxs-lookup"><span data-stu-id="bc89d-105">The second credential is a *supporting credential*.</span></span> <span data-ttu-id="bc89d-106">Toto téma vysvětluje, jak implementovat tyto přihlašovací údaje v klientovi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="bc89d-106">This topic explains how to implement such credentials in an Windows Communication Foundation (WCF) client.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bc89d-107">Specifikace pro podporu přihlašovací údaje je součástí specifikace WS-SecurityPolicy.</span><span class="sxs-lookup"><span data-stu-id="bc89d-107">The specification for supporting credentials is part of the WS-SecurityPolicy specification.</span></span> <span data-ttu-id="bc89d-108">Další informace najdete v tématu [specifikací zabezpečení webových služeb](http://go.microsoft.com/fwlink/?LinkId=88537).</span><span class="sxs-lookup"><span data-stu-id="bc89d-108">For more information, see [Web Services Security Specifications](http://go.microsoft.com/fwlink/?LinkId=88537).</span></span>  
  
## <a name="supporting-tokens"></a><span data-ttu-id="bc89d-109">Podpora tokenů</span><span class="sxs-lookup"><span data-stu-id="bc89d-109">Supporting Tokens</span></span>  
 <span data-ttu-id="bc89d-110">Stručně řečeno, při použití zabezpečení zpráv *primární pověření* vždy slouží k zabezpečení zpráv (například certifikát X.509 nebo lístek protokolu Kerberos).</span><span class="sxs-lookup"><span data-stu-id="bc89d-110">In brief, when you use message security, a *primary credential* is always used to secure the message (for example, an X.509 certificate or a Kerberos ticket).</span></span>  
  
 <span data-ttu-id="bc89d-111">Podle definice specifikace, používá vazby zabezpečení *tokeny* zabezpečit zprávy exchange.</span><span class="sxs-lookup"><span data-stu-id="bc89d-111">As defined by the specification, a security binding uses *tokens* to secure the message exchange.</span></span> <span data-ttu-id="bc89d-112">A *tokenu* je reprezentace pověření zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="bc89d-112">A *token* is a representation of a security credential.</span></span>  
  
 <span data-ttu-id="bc89d-113">Vazby zabezpečení používá primární token identifikovat v zásadách zabezpečení vazby k vytvoření podpisu.</span><span class="sxs-lookup"><span data-stu-id="bc89d-113">The security binding uses a primary token identified in the security binding policy to create a signature.</span></span> <span data-ttu-id="bc89d-114">Tento podpis odkazuje jako *podpis zprávy*.</span><span class="sxs-lookup"><span data-stu-id="bc89d-114">This signature is referred to as the *message signature*.</span></span>  
  
 <span data-ttu-id="bc89d-115">K posílení deklarace identity poskytované tokenu přidružený podpis zprávy lze zadat další tokeny.</span><span class="sxs-lookup"><span data-stu-id="bc89d-115">Additional tokens can be specified to augment the claims provided by the token associated with the message signature.</span></span>  
  
## <a name="endorsing-signing-and-encrypting"></a><span data-ttu-id="bc89d-116">Potvrzování, podepisování a šifrování</span><span class="sxs-lookup"><span data-stu-id="bc89d-116">Endorsing, Signing, and Encrypting</span></span>  
 <span data-ttu-id="bc89d-117">Výsledkem podpůrné přihlašovacích údajů *token podpory* přenášených v rámci zprávy.</span><span class="sxs-lookup"><span data-stu-id="bc89d-117">A supporting credential results in a *supporting token* transmitted inside the message.</span></span> <span data-ttu-id="bc89d-118">Specifikace WS-SecurityPolicy definuje čtyři způsoby, jak připojit token podpory na zprávu, jak je popsáno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="bc89d-118">The WS-SecurityPolicy specification defines four ways to attach a supporting token to the message, as described in the following table.</span></span>  
  
|<span data-ttu-id="bc89d-119">Účel</span><span class="sxs-lookup"><span data-stu-id="bc89d-119">Purpose</span></span>|<span data-ttu-id="bc89d-120">Popis</span><span class="sxs-lookup"><span data-stu-id="bc89d-120">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bc89d-121">Podepsané</span><span class="sxs-lookup"><span data-stu-id="bc89d-121">Signed</span></span>|<span data-ttu-id="bc89d-122">Token podpory je zahrnutý v záhlaví zabezpečení a je podepsána podpis zprávy.</span><span class="sxs-lookup"><span data-stu-id="bc89d-122">The supporting token is included in the security header and is signed by the message signature.</span></span>|  
|<span data-ttu-id="bc89d-123">Potvrdit správnost</span><span class="sxs-lookup"><span data-stu-id="bc89d-123">Endorsing</span></span>|<span data-ttu-id="bc89d-124">*Či identifikaci token* podepisuje podpis zprávy.</span><span class="sxs-lookup"><span data-stu-id="bc89d-124">An *endorsing token* signs the message signature.</span></span>|  
|<span data-ttu-id="bc89d-125">Podepsaná a či identifikaci</span><span class="sxs-lookup"><span data-stu-id="bc89d-125">Signed and Endorsing</span></span>|<span data-ttu-id="bc89d-126">Podepsaná, potvrzování tokeny přihlašovací celý `ds:Signature` element vytvořeného z podpis zprávy a jsou sami podepsána tuto podpis zprávy; to znamená, oba tokeny (tokenu používaného k podpis zprávy a podepsaný token či identifikaci) přihlásit navzájem.</span><span class="sxs-lookup"><span data-stu-id="bc89d-126">Signed, endorsing tokens sign the entire `ds:Signature` element produced from the message signature and are themselves signed by that message signature; that is, both tokens (the token used for the message signature and the signed endorsing token) sign each other.</span></span>|  
|<span data-ttu-id="bc89d-127">Podepsaná a šifrování</span><span class="sxs-lookup"><span data-stu-id="bc89d-127">Signed and Encrypting</span></span>|<span data-ttu-id="bc89d-128">Podepsaný držitelem, šifrované podpůrné tokeny jsou podepsané podpora tokenů, které jsou také zašifrované, když se zobrazí v `wsse:SecurityHeader`.</span><span class="sxs-lookup"><span data-stu-id="bc89d-128">Signed, encrypted supporting tokens are signed supporting tokens that are also encrypted when they appear in the `wsse:SecurityHeader`.</span></span>|  
  
## <a name="programming-supporting-credentials"></a><span data-ttu-id="bc89d-129">Programování podpora přihlašovací údaje</span><span class="sxs-lookup"><span data-stu-id="bc89d-129">Programming Supporting Credentials</span></span>  
 <span data-ttu-id="bc89d-130">Chcete-li vytvořit službu, která používá podpůrné tokeny, musíte vytvořit [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="bc89d-130">To create a service that uses supporting tokens you must create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span> <span data-ttu-id="bc89d-131">(Další informace najdete v tématu [postupy: vytvoření vlastní vazby pomocí elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).)</span><span class="sxs-lookup"><span data-stu-id="bc89d-131">(For more information, see [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).)</span></span>  
  
 <span data-ttu-id="bc89d-132">Prvním krokem při vytváření vlastní vazby je vytvořit element vazby zabezpečení, který může být jeden ze tří typů:</span><span class="sxs-lookup"><span data-stu-id="bc89d-132">The first step when creating a custom binding is to create a security binding element, which can be one of three types:</span></span>  
  
-   <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
  
-   <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
  
-   <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 <span data-ttu-id="bc89d-133">Dědí všechny třídy <xref:System.ServiceModel.Channels.SecurityBindingElement>, což zahrnuje čtyři relevantní vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="bc89d-133">All classes inherit from the <xref:System.ServiceModel.Channels.SecurityBindingElement>, which includes four relevant properties:</span></span>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.EndpointSupportingTokenParameters%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.OperationSupportingTokenParameters%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalEndpointSupportingTokenParameters%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalOperationSupportingTokenParameters%2A>  
  
#### <a name="scopes"></a><span data-ttu-id="bc89d-134">Obory</span><span class="sxs-lookup"><span data-stu-id="bc89d-134">Scopes</span></span>  
 <span data-ttu-id="bc89d-135">Existují dva obory pro podporu přihlašovací údaje:</span><span class="sxs-lookup"><span data-stu-id="bc89d-135">Two scopes exist for supporting credentials:</span></span>  
  
-   <span data-ttu-id="bc89d-136">*Koncový bod podpora tokenů* podporují všechny operace koncový bod.</span><span class="sxs-lookup"><span data-stu-id="bc89d-136">*Endpoint supporting tokens* support all operations of an endpoint.</span></span> <span data-ttu-id="bc89d-137">To znamená pověření, které představuje token podpory lze vždy, když jsou vyvolány žádné operace koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="bc89d-137">That is, the credential that the supporting token represents can be used whenever any endpoint operations are invoked.</span></span>  
  
-   <span data-ttu-id="bc89d-138">*Operace podpora tokenů* podporují pouze o operaci konkrétní koncový bod.</span><span class="sxs-lookup"><span data-stu-id="bc89d-138">*Operation supporting tokens* support only a specific endpoint operation.</span></span>  
  
 <span data-ttu-id="bc89d-139">Jak názvy vlastností, podpora pověření může být požadované nebo volitelné.</span><span class="sxs-lookup"><span data-stu-id="bc89d-139">As indicated by the property names, supporting credentials can be either required or optional.</span></span> <span data-ttu-id="bc89d-140">To znamená pokud podpůrné přihlašovacích údajů se používá, pokud je k dispozici, i když není nutné, ale nebudou ověřování, pokud není přítomen.</span><span class="sxs-lookup"><span data-stu-id="bc89d-140">That is, if the supporting credential is used if it is present, although it is not necessary, but the authentication will not fail if it is not present.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="bc89d-141">Procedury</span><span class="sxs-lookup"><span data-stu-id="bc89d-141">Procedures</span></span>  
  
#### <a name="to-create-a-custom-binding-that-includes-supporting-credentials"></a><span data-ttu-id="bc89d-142">Chcete-li vytvořit vlastní vazby, která zahrnuje podporu přihlašovací údaje</span><span class="sxs-lookup"><span data-stu-id="bc89d-142">To create a custom binding that includes supporting credentials</span></span>  
  
1.  <span data-ttu-id="bc89d-143">Vytvořte element vazby a zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="bc89d-143">Create a security binding element.</span></span> <span data-ttu-id="bc89d-144">Následující příklad vytvoří <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> s `UserNameForCertificate` režim ověřování.</span><span class="sxs-lookup"><span data-stu-id="bc89d-144">The example below creates a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> with the `UserNameForCertificate` authentication mode.</span></span> <span data-ttu-id="bc89d-145">Použití <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="bc89d-145">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> method.</span></span>  
  
2.  <span data-ttu-id="bc89d-146">Přidat parametr podpůrné ke kolekci typů vrácené odpovídající vlastnost (`Endorsing`, `Signed`, `SignedEncrypted`, nebo `SignedEndorsed`).</span><span class="sxs-lookup"><span data-stu-id="bc89d-146">Add the supporting parameter to the collection of types returned by the appropriate property (`Endorsing`, `Signed`, `SignedEncrypted`, or `SignedEndorsed`).</span></span> <span data-ttu-id="bc89d-147">Typy v <xref:System.ServiceModel.Security.Tokens> obor názvů zahrnují běžně používané typy, jako <xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters>.</span><span class="sxs-lookup"><span data-stu-id="bc89d-147">The types in the <xref:System.ServiceModel.Security.Tokens> namespace include commonly used types, such as the <xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc89d-148">Příklad</span><span class="sxs-lookup"><span data-stu-id="bc89d-148">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="bc89d-149">Popis</span><span class="sxs-lookup"><span data-stu-id="bc89d-149">Description</span></span>  
 <span data-ttu-id="bc89d-150">Následující příklad vytvoří instanci <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> a přidá instanci <xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> třídy ke kolekci vlastnost Endorsing vrátila.</span><span class="sxs-lookup"><span data-stu-id="bc89d-150">The following example creates an instance of the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and adds an instance of the <xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> class to the collection the Endorsing property returned.</span></span>  
  
### <a name="code"></a><span data-ttu-id="bc89d-151">Kód</span><span class="sxs-lookup"><span data-stu-id="bc89d-151">Code</span></span>  
 [!code-csharp[c_SupportingCredential#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_supportingcredential/cs/source.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="bc89d-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="bc89d-152">See Also</span></span>  
 [<span data-ttu-id="bc89d-153">Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="bc89d-153">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
