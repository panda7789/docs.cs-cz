---
title: 'Postupy: Vytvoření služby tokenů zabezpečení'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 98e82101-4cff-4bb8-a220-f7abed3556e5
caps.latest.revision: 12
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: e043b9b9a3b09bec0d7484fb732e33571b5aaf0c
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="how-to-create-a-security-token-service"></a><span data-ttu-id="67223-102">Postupy: Vytvoření služby tokenů zabezpečení</span><span class="sxs-lookup"><span data-stu-id="67223-102">How to: Create a Security Token Service</span></span>
<span data-ttu-id="67223-103">Služby tokenů zabezpečení implementuje protokol definovaný ve specifikaci WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="67223-103">A security token service implements the protocol defined in the WS-Trust specification.</span></span> <span data-ttu-id="67223-104">Tento protokol definuje formáty zpráv a vzory exchange zprávu pro vystavování, obnovení, zrušení a ověřování tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="67223-104">This protocol defines message formats and message exchange patterns for issuing, renewing, canceling, and validating security tokens.</span></span> <span data-ttu-id="67223-105">Služba tokenů zabezpečení poskytuje jeden nebo více z těchto funkcí.</span><span class="sxs-lookup"><span data-stu-id="67223-105">A given security token service provides one or more of these capabilities.</span></span> <span data-ttu-id="67223-106">Toto téma vypadá nejvíce běžný scénář: implementace vystavování tokenů.</span><span class="sxs-lookup"><span data-stu-id="67223-106">This topic looks at the most common scenario: implementing token issuance.</span></span>  
  
## <a name="issuing-tokens"></a><span data-ttu-id="67223-107">Vydávání tokenů</span><span class="sxs-lookup"><span data-stu-id="67223-107">Issuing Tokens</span></span>  
 <span data-ttu-id="67223-108">WS-Trust definuje formáty zpráv, na základě `RequestSecurityToken` schématu XML definition language (XSD) schématu elementu, a `RequestSecurityTokenResponse` element schématu XSD pro provádění vystavování tokenů.</span><span class="sxs-lookup"><span data-stu-id="67223-108">WS-Trust defines message formats, based on the `RequestSecurityToken` XML Schema definition language (XSD) schema element, and `RequestSecurityTokenResponse` XSD schema element for performing token issuance.</span></span> <span data-ttu-id="67223-109">Kromě toho definuje přidružené akce identifikátory Uniform Resource (Identifier).</span><span class="sxs-lookup"><span data-stu-id="67223-109">In addition, it defines the associated Action Uniform Resource Identifiers (URIs).</span></span> <span data-ttu-id="67223-110">Akce přidružené k identifikátoru URI `RequestSecurityToken` zpráva http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue.</span><span class="sxs-lookup"><span data-stu-id="67223-110">The action URI associated with the `RequestSecurityToken` message is http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue.</span></span> <span data-ttu-id="67223-111">Akce přidružené k identifikátoru URI `RequestSecurityTokenResponse` zpráva http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue.</span><span class="sxs-lookup"><span data-stu-id="67223-111">The action URI associated with the `RequestSecurityTokenResponse` message is   http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue.</span></span>  
  
### <a name="request-message-structure"></a><span data-ttu-id="67223-112">Struktura zprávy požadavku</span><span class="sxs-lookup"><span data-stu-id="67223-112">Request Message Structure</span></span>  
 <span data-ttu-id="67223-113">Struktura zprávy požadavku problém se obvykle skládá z následujících položek:</span><span class="sxs-lookup"><span data-stu-id="67223-113">The issue request message structure typically consists of the following items:</span></span>  
  
-   <span data-ttu-id="67223-114">Žádost o zadejte identifikátor URI s hodnotou http://schemas.xmlsoap.org/ws/2005/02/trust/Issue.</span><span class="sxs-lookup"><span data-stu-id="67223-114">A request type URI with a value of    http://schemas.xmlsoap.org/ws/2005/02/trust/Issue.</span></span>  
  
-   <span data-ttu-id="67223-115">Token typ identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="67223-115">A token type URI.</span></span> <span data-ttu-id="67223-116">Pro tokeny zabezpečení kontrolní výrazy Markup Language (SAML) 1.1, hodnota tento identifikátor URI je http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1.</span><span class="sxs-lookup"><span data-stu-id="67223-116">For Security Assertions Markup Language (SAML) 1.1 tokens, the value of this URI is http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1.</span></span>  
  
-   <span data-ttu-id="67223-117">Velikost klíče hodnotu, která určuje počet bitů klíč, který chcete přidružit vydaný token.</span><span class="sxs-lookup"><span data-stu-id="67223-117">A key size value that indicates the number of bits in the key to be associated with the issued token.</span></span>  
  
-   <span data-ttu-id="67223-118">Klíče typu identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="67223-118">A key type URI.</span></span> <span data-ttu-id="67223-119">Symetrické klíče, je hodnota tento identifikátor URI http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey.</span><span class="sxs-lookup"><span data-stu-id="67223-119">For symmetric keys, the value of this URI is http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey.</span></span>  
  
 <span data-ttu-id="67223-120">Kromě toho může být několik další položky k dispozici:</span><span class="sxs-lookup"><span data-stu-id="67223-120">In addition, a couple of other items might be present:</span></span>  
  
-   <span data-ttu-id="67223-121">Materiál klíče zadaných klientem.</span><span class="sxs-lookup"><span data-stu-id="67223-121">Key material provided by the client.</span></span>  
  
-   <span data-ttu-id="67223-122">Obor informace, které určuje cílovou službu, která se použije vystavený token.</span><span class="sxs-lookup"><span data-stu-id="67223-122">Scope information that indicates the target service that the issued token will be used with.</span></span>  
  
 <span data-ttu-id="67223-123">Služby tokenů zabezpečení používá informace ve zprávě požadavku problém, když se vytvoří zprávu odpovědi problém.</span><span class="sxs-lookup"><span data-stu-id="67223-123">The security token service uses the information in the issue request message when it constructs the Issue Response message.</span></span>  
  
## <a name="response-message-structure"></a><span data-ttu-id="67223-124">Struktura zprávu odpovědi</span><span class="sxs-lookup"><span data-stu-id="67223-124">Response Message Structure</span></span>  
 <span data-ttu-id="67223-125">Struktura zprávu odpovědi problém se obvykle skládá z následujících položek;</span><span class="sxs-lookup"><span data-stu-id="67223-125">The issue response message structure typically consists of the following items;</span></span>  
  
-   <span data-ttu-id="67223-126">Token zabezpečení vydané, například SAML 1.1 kontrolní výraz.</span><span class="sxs-lookup"><span data-stu-id="67223-126">The issued security token, for example, a SAML 1.1 assertion.</span></span>  
  
-   <span data-ttu-id="67223-127">Doklad token přidružené k tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="67223-127">A proof token associated with the security token.</span></span> <span data-ttu-id="67223-128">Pro symetrické klíče je to často šifrovaném formátu materiál klíče.</span><span class="sxs-lookup"><span data-stu-id="67223-128">For symmetric keys, this is often an encrypted form of the key material.</span></span>  
  
-   <span data-ttu-id="67223-129">Odkazy na token vydaných zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="67223-129">References to the issued security token.</span></span> <span data-ttu-id="67223-130">Obvykle služby tokenů zabezpečení vrátí odkaz, který lze použít při následné zprávy poslal klienta a druhou, která lze použít, pokud token není k dispozici v dalších zpráv se zobrazí vydaný token.</span><span class="sxs-lookup"><span data-stu-id="67223-130">Typically, the security token service returns a reference that can be used when the issued token appears in a subsequent message sent by the client and another that can be used when the token is not present in subsequent messages.</span></span>  
  
 <span data-ttu-id="67223-131">Kromě toho může být několik další položky k dispozici:</span><span class="sxs-lookup"><span data-stu-id="67223-131">In addition, a couple of other items might be present:</span></span>  
  
-   <span data-ttu-id="67223-132">Materiál klíče poskytované služby tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="67223-132">Key material provided by the security token service.</span></span>  
  
-   <span data-ttu-id="67223-133">Algoritmus potřebné k výpočtu sdílený klíč.</span><span class="sxs-lookup"><span data-stu-id="67223-133">The algorithm needed to compute the shared key.</span></span>  
  
-   <span data-ttu-id="67223-134">Doba platnosti informace pro vydané token.</span><span class="sxs-lookup"><span data-stu-id="67223-134">Lifetime information for the issued token.</span></span>  
  
## <a name="processing-request-messages"></a><span data-ttu-id="67223-135">Zpracování zpráv požadavků</span><span class="sxs-lookup"><span data-stu-id="67223-135">Processing Request Messages</span></span>  
 <span data-ttu-id="67223-136">Služby tokenů zabezpečení zpracuje požadavek problém zkoumání jednotlivých částí zprávy požadavku a zajištění, aby mohla vystavovat token, který splňuje požadavek.</span><span class="sxs-lookup"><span data-stu-id="67223-136">The security token service processes the issue request by examining the various pieces of the request message and ensuring that it can issue a token that satisfies the request.</span></span> <span data-ttu-id="67223-137">Předtím, než se vytvoří token, který má být vydaný, musíte určit služby tokenů zabezpečení následující:</span><span class="sxs-lookup"><span data-stu-id="67223-137">The security token service must determine the following before it constructs the token to be issued:</span></span>  
  
-   <span data-ttu-id="67223-138">Žádost je opravdu žádost o token pro vystavování.</span><span class="sxs-lookup"><span data-stu-id="67223-138">The request really is a request for a token to be issued.</span></span>  
  
-   <span data-ttu-id="67223-139">Služby tokenů zabezpečení podporuje požadovaný typ tokenu.</span><span class="sxs-lookup"><span data-stu-id="67223-139">The security token service supports the requested token type.</span></span>  
  
-   <span data-ttu-id="67223-140">Žadatel je oprávnění k vytvoření žádosti.</span><span class="sxs-lookup"><span data-stu-id="67223-140">The requester is authorized to make the request.</span></span>  
  
-   <span data-ttu-id="67223-141">Služby tokenů zabezpečení můžete splnit očekávání žadatele s ohledem na materiál klíče.</span><span class="sxs-lookup"><span data-stu-id="67223-141">The security token service can meet the requester's expectations with respect to key material.</span></span>  
  
 <span data-ttu-id="67223-142">Jaké k podepsání token s a jaké klíč k šifrování se sdílený klíč s určování dvě důležité části vytváření token.</span><span class="sxs-lookup"><span data-stu-id="67223-142">Two vital parts of constructing a token are determining what key to sign the token with and what key to encrypt the shared key with.</span></span> <span data-ttu-id="67223-143">Token musí být podepsané tak, aby při klienta uvede token, který má cílovou službu, můžete určit služby, který byl token vydán službu tokenů zabezpečení, která důvěřuje.</span><span class="sxs-lookup"><span data-stu-id="67223-143">The token needs to be signed so that when the client presents the token to the target service, that service can determine that the token was issued by a security token service that it trusts.</span></span> <span data-ttu-id="67223-144">Materiál klíče musí být šifrované tak, že cílová služba může dešifrovat tento materiál klíče.</span><span class="sxs-lookup"><span data-stu-id="67223-144">The key material needs to be encrypted in such a way that the target service can decrypt that key material.</span></span>  
  
 <span data-ttu-id="67223-145">Podepisování kontrolního výrazu SAML zahrnuje vytvoření <xref:System.IdentityModel.Tokens.SigningCredentials> instance.</span><span class="sxs-lookup"><span data-stu-id="67223-145">Signing a SAML assertion involves creating a <xref:System.IdentityModel.Tokens.SigningCredentials> instance.</span></span> <span data-ttu-id="67223-146">V konstruktoru pro tuto třídu přijímá následující:</span><span class="sxs-lookup"><span data-stu-id="67223-146">The constructor for this class takes the following:</span></span>  
  
-   <span data-ttu-id="67223-147">A <xref:System.IdentityModel.Tokens.SecurityKey> pro klíč sloužící k podepisování kontrolního výrazu SAML.</span><span class="sxs-lookup"><span data-stu-id="67223-147">A <xref:System.IdentityModel.Tokens.SecurityKey> for the key to use to sign the SAML assertion.</span></span>  
  
-   <span data-ttu-id="67223-148">Řetězec, který určuje algoritmus podpisu používat.</span><span class="sxs-lookup"><span data-stu-id="67223-148">A string identifying the signature algorithm to use.</span></span>  
  
-   <span data-ttu-id="67223-149">Řetězec, který určuje algoritmus digest používat.</span><span class="sxs-lookup"><span data-stu-id="67223-149">A string identifying the digest algorithm to use.</span></span>  
  
-   <span data-ttu-id="67223-150">Volitelně můžete <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> identifikující klíč sloužící k podepisování kontrolní výraz.</span><span class="sxs-lookup"><span data-stu-id="67223-150">Optionally, a <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> that identifies the key to use to sign the assertion.</span></span>  
  
 [!code-csharp[c_CreateSTS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#1)]
 [!code-vb[c_CreateSTS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#1)]  
  
 <span data-ttu-id="67223-151">Šifrování se sdílený klíč zahrnuje trvá materiál klíče a šifrování pomocí klíče, Cílová služba můžete použít k dešifrování sdílený klíč.</span><span class="sxs-lookup"><span data-stu-id="67223-151">Encrypting the shared key involves taking the key material and encrypting it with a key that the target service can use to decrypt the shared key.</span></span> <span data-ttu-id="67223-152">Obvykle se používá veřejný klíč z cílových služeb.</span><span class="sxs-lookup"><span data-stu-id="67223-152">Typically, the public key of the target service is used.</span></span>  
  
 [!code-csharp[c_CreateSTS#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#2)]
 [!code-vb[c_CreateSTS#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#2)]  
  
 <span data-ttu-id="67223-153">Kromě toho <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> pro šifrovaný klíč je potřeba.</span><span class="sxs-lookup"><span data-stu-id="67223-153">In addition, a <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> for the encrypted key is needed.</span></span>  
  
 [!code-csharp[c_CreateSTS#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#3)]
 [!code-vb[c_CreateSTS#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#3)]  
  
 <span data-ttu-id="67223-154">To <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> se pak použije k vytvoření `SamlSubject` jako součást `SamlToken`.</span><span class="sxs-lookup"><span data-stu-id="67223-154">This <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> is then used to create a `SamlSubject` as part of the `SamlToken`.</span></span>  
  
 [!code-csharp[c_CreateSTS#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#4)]
 [!code-vb[c_CreateSTS#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#4)]  
  
 <span data-ttu-id="67223-155">Další informace najdete v tématu [ukázka federace](../../../../docs/framework/wcf/samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="67223-155">For more information, see [Federation Sample](../../../../docs/framework/wcf/samples/federation-sample.md).</span></span>  
  
## <a name="creating-response-messages"></a><span data-ttu-id="67223-156">Vytváření odpovědí na zprávy</span><span class="sxs-lookup"><span data-stu-id="67223-156">Creating Response Messages</span></span>  
 <span data-ttu-id="67223-157">Jakmile služby tokenů zabezpečení zpracuje žádost o problému a vytvoří token, který má být vydaný společně s doklad klíčem, zprávu odpovědi musí zkonstruovat, včetně alespoň požadovaný token, doklad token a odkazy na vydaných tokenů.</span><span class="sxs-lookup"><span data-stu-id="67223-157">Once the security token service processes the issue request and constructs the token to be issued along with the proof key, the response message needs to be constructed, including at least the requested token, the proof token, and the issued token references.</span></span> <span data-ttu-id="67223-158">Vystavený token je obvykle <xref:System.IdentityModel.Tokens.SamlSecurityToken> vytvořené z <xref:System.IdentityModel.Tokens.SamlAssertion>, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="67223-158">The issued token is typically a <xref:System.IdentityModel.Tokens.SamlSecurityToken> created from the <xref:System.IdentityModel.Tokens.SamlAssertion>, as shown in the following example.</span></span>  
  
 [!code-csharp[c_CreateSTS#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#5)]
 [!code-vb[c_CreateSTS#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#5)]  
  
 <span data-ttu-id="67223-159">V případě, kdy služby tokenů zabezpečení poskytuje sdílené materiál klíče, doklad token je vytvořený tak, že vytvoříte <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>.</span><span class="sxs-lookup"><span data-stu-id="67223-159">In the case where the security token service provides the shared key material, the proof token is constructed by creating a <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>.</span></span>  
  
 [!code-csharp[c_CreateSTS#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#6)]
 [!code-vb[c_CreateSTS#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#6)]  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="67223-160"> Postup vytvoření doklad token, pokud obě služby klienta a token zabezpečení poskytne klíče pro sdílený klíč, najdete v části [ukázka federace](../../../../docs/framework/wcf/samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="67223-160"> how to construct the proof token when the client and the security token service both provide key material for the shared key, see [Federation Sample](../../../../docs/framework/wcf/samples/federation-sample.md).</span></span>  
  
 <span data-ttu-id="67223-161">Vystavený token odkazy se vytvářejí pomocí instancí <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause> třídy.</span><span class="sxs-lookup"><span data-stu-id="67223-161">The issued token references are constructed by creating instances of the <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause> class.</span></span>  
  
 [!code-csharp[c_CreateSTS#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#7)]
 [!code-vb[c_CreateSTS#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#7)]  
  
 <span data-ttu-id="67223-162">Tyto různé hodnoty jsou pak serializovat do zprávu odpovědi vrácen do klienta.</span><span class="sxs-lookup"><span data-stu-id="67223-162">These various values are then serialized into the response message returned to the client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67223-163">Příklad</span><span class="sxs-lookup"><span data-stu-id="67223-163">Example</span></span>  
 <span data-ttu-id="67223-164">Úplný kód pro službu tokenů zabezpečení, najdete v části [ukázka federace](../../../../docs/framework/wcf/samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="67223-164">For full code for a security token service, see [Federation Sample](../../../../docs/framework/wcf/samples/federation-sample.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67223-165">Viz také</span><span class="sxs-lookup"><span data-stu-id="67223-165">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.SigningCredentials>  
 <xref:System.IdentityModel.Tokens.SecurityKey>  
 <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier>  
 <xref:System.IdentityModel.Tokens.SamlSecurityToken>  
 <xref:System.IdentityModel.Tokens.SamlAssertion>  
 <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>  
 <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause>  
 [<span data-ttu-id="67223-166">Ukázka federace</span><span class="sxs-lookup"><span data-stu-id="67223-166">Federation Sample</span></span>](../../../../docs/framework/wcf/samples/federation-sample.md)
