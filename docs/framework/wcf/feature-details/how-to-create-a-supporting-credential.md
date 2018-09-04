---
title: 'Postupy: vytvoření podpůrných přihlašovacích údajů'
ms.date: 03/30/2017
ms.assetid: d0952919-8bb4-4978-926c-9cc108f89806
ms.openlocfilehash: ef4d9a406e6fc929e4ad59911d587e462c9b2b65
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43499988"
---
# <a name="how-to-create-a-supporting-credential"></a><span data-ttu-id="26af3-102">Postupy: vytvoření podpůrných přihlašovacích údajů</span><span class="sxs-lookup"><span data-stu-id="26af3-102">How to: Create a Supporting Credential</span></span>
<span data-ttu-id="26af3-103">Je možné mít vlastní bezpečnostní schéma, které vyžaduje více přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="26af3-103">It is possible to have a custom security scheme that requires more than one credential.</span></span> <span data-ttu-id="26af3-104">Například služba vyžádat od klienta nejen uživatelské jméno a heslo, ale také pověření, která prokáže vaše oprávnění klienta je víc než 18.</span><span class="sxs-lookup"><span data-stu-id="26af3-104">For example, a service may demand from the client not just a user name and password, but also a credential that proves the client is over the age of 18.</span></span> <span data-ttu-id="26af3-105">Je druhý přihlašovacích údajů *podpora přihlašovacích údajů*.</span><span class="sxs-lookup"><span data-stu-id="26af3-105">The second credential is a *supporting credential*.</span></span> <span data-ttu-id="26af3-106">Toto téma vysvětluje, jak implementovat tyto přihlašovací údaje v klientovi Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="26af3-106">This topic explains how to implement such credentials in an Windows Communication Foundation (WCF) client.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="26af3-107">Specifikace pro podporu přihlašovacích údajů je součástí specifikace WS-SecurityPolicy.</span><span class="sxs-lookup"><span data-stu-id="26af3-107">The specification for supporting credentials is part of the WS-SecurityPolicy specification.</span></span> <span data-ttu-id="26af3-108">Další informace najdete v tématu [specifikací webových služeb zabezpečení](https://go.microsoft.com/fwlink/?LinkId=88537).</span><span class="sxs-lookup"><span data-stu-id="26af3-108">For more information, see [Web Services Security Specifications](https://go.microsoft.com/fwlink/?LinkId=88537).</span></span>  
  
## <a name="supporting-tokens"></a><span data-ttu-id="26af3-109">Podpora tokenů</span><span class="sxs-lookup"><span data-stu-id="26af3-109">Supporting Tokens</span></span>  
 <span data-ttu-id="26af3-110">Stručně řečeno, při použití zabezpečení zpráv *primární pověření* vždy slouží k zabezpečení zpráv (například certifikát X.509 nebo lístek protokolu Kerberos).</span><span class="sxs-lookup"><span data-stu-id="26af3-110">In brief, when you use message security, a *primary credential* is always used to secure the message (for example, an X.509 certificate or a Kerberos ticket).</span></span>  
  
 <span data-ttu-id="26af3-111">Jak je definováno ve specifikaci vazby zabezpečení používá *tokeny* k výměně zpráv zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="26af3-111">As defined by the specification, a security binding uses *tokens* to secure the message exchange.</span></span> <span data-ttu-id="26af3-112">A *token* je reprezentace bezpečnostním pověřením.</span><span class="sxs-lookup"><span data-stu-id="26af3-112">A *token* is a representation of a security credential.</span></span>  
  
 <span data-ttu-id="26af3-113">Vazby zabezpečení používá k vytvoření podpisu primární token identifikované v zásadách zabezpečení vazby.</span><span class="sxs-lookup"><span data-stu-id="26af3-113">The security binding uses a primary token identified in the security binding policy to create a signature.</span></span> <span data-ttu-id="26af3-114">Tento podpis se označuje jako *podpis zprávy*.</span><span class="sxs-lookup"><span data-stu-id="26af3-114">This signature is referred to as the *message signature*.</span></span>  
  
 <span data-ttu-id="26af3-115">Další tokeny lze k posílení deklarací poskytovaných token spojený s podpis zprávy.</span><span class="sxs-lookup"><span data-stu-id="26af3-115">Additional tokens can be specified to augment the claims provided by the token associated with the message signature.</span></span>  
  
## <a name="endorsing-signing-and-encrypting"></a><span data-ttu-id="26af3-116">Potvrdit, podepisování a šifrování</span><span class="sxs-lookup"><span data-stu-id="26af3-116">Endorsing, Signing, and Encrypting</span></span>  
 <span data-ttu-id="26af3-117">Výsledkem podpůrného pověření *podpůrný token* přenášených uvnitř zprávy.</span><span class="sxs-lookup"><span data-stu-id="26af3-117">A supporting credential results in a *supporting token* transmitted inside the message.</span></span> <span data-ttu-id="26af3-118">Specifikace WS-SecurityPolicy definuje čtyři způsoby, jak připojit podpůrný token na zprávu, jak je popsáno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="26af3-118">The WS-SecurityPolicy specification defines four ways to attach a supporting token to the message, as described in the following table.</span></span>  
  
|<span data-ttu-id="26af3-119">Účel</span><span class="sxs-lookup"><span data-stu-id="26af3-119">Purpose</span></span>|<span data-ttu-id="26af3-120">Popis</span><span class="sxs-lookup"><span data-stu-id="26af3-120">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="26af3-121">podepsané</span><span class="sxs-lookup"><span data-stu-id="26af3-121">Signed</span></span>|<span data-ttu-id="26af3-122">Token podpory je zahrnutá v záhlaví zabezpečení a je podepsán společností podpis zprávy.</span><span class="sxs-lookup"><span data-stu-id="26af3-122">The supporting token is included in the security header and is signed by the message signature.</span></span>|  
|<span data-ttu-id="26af3-123">Potvrdit</span><span class="sxs-lookup"><span data-stu-id="26af3-123">Endorsing</span></span>|<span data-ttu-id="26af3-124">*Podporujícími token* podepíše podpis zprávy.</span><span class="sxs-lookup"><span data-stu-id="26af3-124">An *endorsing token* signs the message signature.</span></span>|  
|<span data-ttu-id="26af3-125">Podepsaný a podporujícími</span><span class="sxs-lookup"><span data-stu-id="26af3-125">Signed and Endorsing</span></span>|<span data-ttu-id="26af3-126">Podepsaná, podporujících tokeny přihlášení celý `ds:Signature` element vytvořenými podpis zprávy a jsou samotné podepsány tento podpis zprávy; to znamená, že oba tokeny (tokenu používaného k podpis zprávy a podepsaný token potvrzující) podepsat mezi sebou.</span><span class="sxs-lookup"><span data-stu-id="26af3-126">Signed, endorsing tokens sign the entire `ds:Signature` element produced from the message signature and are themselves signed by that message signature; that is, both tokens (the token used for the message signature and the signed endorsing token) sign each other.</span></span>|  
|<span data-ttu-id="26af3-127">Podepsaný a šifrování</span><span class="sxs-lookup"><span data-stu-id="26af3-127">Signed and Encrypting</span></span>|<span data-ttu-id="26af3-128">Podepsaný a šifrované podpůrných tokenů jsou podepsané podpůrnými tokeny, které se také šifrují, pokud se objeví v `wsse:SecurityHeader`.</span><span class="sxs-lookup"><span data-stu-id="26af3-128">Signed, encrypted supporting tokens are signed supporting tokens that are also encrypted when they appear in the `wsse:SecurityHeader`.</span></span>|  
  
## <a name="programming-supporting-credentials"></a><span data-ttu-id="26af3-129">Programování podporuje přihlašovací údaje</span><span class="sxs-lookup"><span data-stu-id="26af3-129">Programming Supporting Credentials</span></span>  
 <span data-ttu-id="26af3-130">Pokud chcete vytvořit službu, která používá podpůrných tokenů, musíte vytvořit [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="26af3-130">To create a service that uses supporting tokens you must create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span> <span data-ttu-id="26af3-131">(Další informace najdete v tématu [postupy: vytvoření vlastní vazby pomocí elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).)</span><span class="sxs-lookup"><span data-stu-id="26af3-131">(For more information, see [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).)</span></span>  
  
 <span data-ttu-id="26af3-132">Prvním krokem při vytváření vlastní vazby je vytvořit element vazby zabezpečení, který může být jeden ze tří typů:</span><span class="sxs-lookup"><span data-stu-id="26af3-132">The first step when creating a custom binding is to create a security binding element, which can be one of three types:</span></span>  
  
-   <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
  
-   <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
  
-   <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 <span data-ttu-id="26af3-133">Dědí všechny třídy <xref:System.ServiceModel.Channels.SecurityBindingElement>, což zahrnuje čtyři relevantní vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="26af3-133">All classes inherit from the <xref:System.ServiceModel.Channels.SecurityBindingElement>, which includes four relevant properties:</span></span>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.EndpointSupportingTokenParameters%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.OperationSupportingTokenParameters%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalEndpointSupportingTokenParameters%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalOperationSupportingTokenParameters%2A>  
  
#### <a name="scopes"></a><span data-ttu-id="26af3-134">Obory</span><span class="sxs-lookup"><span data-stu-id="26af3-134">Scopes</span></span>  
 <span data-ttu-id="26af3-135">Existují dva obory pro podporu přihlašovací údaje:</span><span class="sxs-lookup"><span data-stu-id="26af3-135">Two scopes exist for supporting credentials:</span></span>  
  
-   <span data-ttu-id="26af3-136">*Koncový bod podporující tokeny* podporují všechny operace koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="26af3-136">*Endpoint supporting tokens* support all operations of an endpoint.</span></span> <span data-ttu-id="26af3-137">To znamená přihlašovacích údajů, který představuje podpůrný token lze vždy, když jsou vyvolány žádné operace koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="26af3-137">That is, the credential that the supporting token represents can be used whenever any endpoint operations are invoked.</span></span>  
  
-   <span data-ttu-id="26af3-138">*Podpora tokenů operace* podporují jenom operace určitého koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="26af3-138">*Operation supporting tokens* support only a specific endpoint operation.</span></span>  
  
 <span data-ttu-id="26af3-139">Je určeno názvy vlastností, podpora přihlašovacích údajů může být povinné nebo volitelné.</span><span class="sxs-lookup"><span data-stu-id="26af3-139">As indicated by the property names, supporting credentials can be either required or optional.</span></span> <span data-ttu-id="26af3-140">To znamená pokud podpůrného pověření se používá, pokud je k dispozici, i když není nutné, ale pokud není k dispozici k selhání ověřování.</span><span class="sxs-lookup"><span data-stu-id="26af3-140">That is, if the supporting credential is used if it is present, although it is not necessary, but the authentication will not fail if it is not present.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="26af3-141">Procedury</span><span class="sxs-lookup"><span data-stu-id="26af3-141">Procedures</span></span>  
  
#### <a name="to-create-a-custom-binding-that-includes-supporting-credentials"></a><span data-ttu-id="26af3-142">K vytvoření vlastní vazby, která zahrnuje podporu přihlašovacích údajů</span><span class="sxs-lookup"><span data-stu-id="26af3-142">To create a custom binding that includes supporting credentials</span></span>  
  
1.  <span data-ttu-id="26af3-143">Vytvořte element vazby zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="26af3-143">Create a security binding element.</span></span> <span data-ttu-id="26af3-144">Následující příklad vytvoří <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> s `UserNameForCertificate` režim ověřování.</span><span class="sxs-lookup"><span data-stu-id="26af3-144">The example below creates a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> with the `UserNameForCertificate` authentication mode.</span></span> <span data-ttu-id="26af3-145">Použití <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="26af3-145">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> method.</span></span>  
  
2.  <span data-ttu-id="26af3-146">Přidání podpory parametru do kolekci typů odpovídající vlastnost vrátí (`Endorsing`, `Signed`, `SignedEncrypted`, nebo `SignedEndorsed`).</span><span class="sxs-lookup"><span data-stu-id="26af3-146">Add the supporting parameter to the collection of types returned by the appropriate property (`Endorsing`, `Signed`, `SignedEncrypted`, or `SignedEndorsed`).</span></span> <span data-ttu-id="26af3-147">Typy v <xref:System.ServiceModel.Security.Tokens> obor názvů patří běžně používané typy, například <xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters>.</span><span class="sxs-lookup"><span data-stu-id="26af3-147">The types in the <xref:System.ServiceModel.Security.Tokens> namespace include commonly used types, such as the <xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="26af3-148">Příklad</span><span class="sxs-lookup"><span data-stu-id="26af3-148">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="26af3-149">Popis</span><span class="sxs-lookup"><span data-stu-id="26af3-149">Description</span></span>  
 <span data-ttu-id="26af3-150">Následující příklad vytvoří instance <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> a přidá instanci <xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> třídy Endorsing vlastnosti vrácené do kolekce.</span><span class="sxs-lookup"><span data-stu-id="26af3-150">The following example creates an instance of the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and adds an instance of the <xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> class to the collection the Endorsing property returned.</span></span>  
  
### <a name="code"></a><span data-ttu-id="26af3-151">Kód</span><span class="sxs-lookup"><span data-stu-id="26af3-151">Code</span></span>  
 [!code-csharp[c_SupportingCredential#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_supportingcredential/cs/source.cs#1)]  
  
## <a name="see-also"></a><span data-ttu-id="26af3-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="26af3-152">See Also</span></span>  
 [<span data-ttu-id="26af3-153">Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="26af3-153">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
