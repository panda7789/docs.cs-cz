---
title: 'Postupy: Vytvoření služby tokenů zabezpečení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: 98e82101-4cff-4bb8-a220-f7abed3556e5
ms.openlocfilehash: 39c54c5d91c38e43fd7d0b1205537948e84a0782
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64587533"
---
# <a name="how-to-create-a-security-token-service"></a><span data-ttu-id="532b0-102">Postupy: Vytvoření služby tokenů zabezpečení</span><span class="sxs-lookup"><span data-stu-id="532b0-102">How to: Create a Security Token Service</span></span>
<span data-ttu-id="532b0-103">Služba tokenů zabezpečení implementuje protokol definovaných ve specifikaci WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="532b0-103">A security token service implements the protocol defined in the WS-Trust specification.</span></span> <span data-ttu-id="532b0-104">Tento protokol definuje formáty zpráv a zpráv exchange vzory pro vystavování, obnovení, zrušení a ověřování tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="532b0-104">This protocol defines message formats and message exchange patterns for issuing, renewing, canceling, and validating security tokens.</span></span> <span data-ttu-id="532b0-105">Služba tokenů zabezpečení obsahuje nejméně jeden z těchto možností.</span><span class="sxs-lookup"><span data-stu-id="532b0-105">A given security token service provides one or more of these capabilities.</span></span> <span data-ttu-id="532b0-106">Toto téma vypadá nanejvýš běžný scénář: implementace vystavování tokenů.</span><span class="sxs-lookup"><span data-stu-id="532b0-106">This topic looks at the most common scenario: implementing token issuance.</span></span>  
  
## <a name="issuing-tokens"></a><span data-ttu-id="532b0-107">Vystavování tokenů</span><span class="sxs-lookup"><span data-stu-id="532b0-107">Issuing Tokens</span></span>  
 <span data-ttu-id="532b0-108">WS-Trust definuje formáty zpráv, na základě `RequestSecurityToken` element schématu XML definice jazyk (XSD) schématu, a `RequestSecurityTokenResponse` element schématu XSD pro provádění vystavování tokenů.</span><span class="sxs-lookup"><span data-stu-id="532b0-108">WS-Trust defines message formats, based on the `RequestSecurityToken` XML Schema definition language (XSD) schema element, and `RequestSecurityTokenResponse` XSD schema element for performing token issuance.</span></span> <span data-ttu-id="532b0-109">Kromě toho definuje přidružené identifikátory Uniform Resource (identifikátory URI) akce.</span><span class="sxs-lookup"><span data-stu-id="532b0-109">In addition, it defines the associated Action Uniform Resource Identifiers (URIs).</span></span> <span data-ttu-id="532b0-110">Akci přidruženou k identifikátoru URI `RequestSecurityToken` zpráva `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue`.</span><span class="sxs-lookup"><span data-stu-id="532b0-110">The action URI associated with the `RequestSecurityToken` message is `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue`.</span></span> <span data-ttu-id="532b0-111">Akci přidruženou k identifikátoru URI `RequestSecurityTokenResponse` zpráva `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue`.</span><span class="sxs-lookup"><span data-stu-id="532b0-111">The action URI associated with the `RequestSecurityTokenResponse` message is   `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue`.</span></span>  
  
### <a name="request-message-structure"></a><span data-ttu-id="532b0-112">Struktura zprávy požadavku</span><span class="sxs-lookup"><span data-stu-id="532b0-112">Request Message Structure</span></span>  
 <span data-ttu-id="532b0-113">Struktura zprávy požadavku problém se obvykle skládá z následujících položek:</span><span class="sxs-lookup"><span data-stu-id="532b0-113">The issue request message structure typically consists of the following items:</span></span>  
  
- <span data-ttu-id="532b0-114">Žádost o zadejte identifikátor URI s hodnotou `http://schemas.xmlsoap.org/ws/2005/02/trust/Issue`.</span><span class="sxs-lookup"><span data-stu-id="532b0-114">A request type URI with a value of `http://schemas.xmlsoap.org/ws/2005/02/trust/Issue`.</span></span>
  
- <span data-ttu-id="532b0-115">Token typu identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="532b0-115">A token type URI.</span></span> <span data-ttu-id="532b0-116">Pro tokeny zabezpečení kontrolní výrazy SAML (Markup Language) 1.1, hodnota tohoto identifikátoru URI je `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1`.</span><span class="sxs-lookup"><span data-stu-id="532b0-116">For Security Assertions Markup Language (SAML) 1.1 tokens, the value of this URI is `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1`.</span></span>  
  
- <span data-ttu-id="532b0-117">Velikost klíče hodnota, která určuje počet bitů v klíči, který se má přidružit vydaný token.</span><span class="sxs-lookup"><span data-stu-id="532b0-117">A key size value that indicates the number of bits in the key to be associated with the issued token.</span></span>  
  
- <span data-ttu-id="532b0-118">Klíče typu identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="532b0-118">A key type URI.</span></span> <span data-ttu-id="532b0-119">Pro symetrické klíče, hodnota tohoto identifikátoru URI je `http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey`.</span><span class="sxs-lookup"><span data-stu-id="532b0-119">For symmetric keys, the value of this URI is `http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey`.</span></span>  
  
 <span data-ttu-id="532b0-120">Kromě toho několik dalších položek, může být k dispozici:</span><span class="sxs-lookup"><span data-stu-id="532b0-120">In addition, a couple of other items might be present:</span></span>  
  
- <span data-ttu-id="532b0-121">Materiál klíče, který klient poskytl.</span><span class="sxs-lookup"><span data-stu-id="532b0-121">Key material provided by the client.</span></span>  
  
- <span data-ttu-id="532b0-122">Informace o oboru, která určuje, který se použije vydaný token s cílovou službu.</span><span class="sxs-lookup"><span data-stu-id="532b0-122">Scope information that indicates the target service that the issued token will be used with.</span></span>  
  
 <span data-ttu-id="532b0-123">Služba tokenů zabezpečení používá informace ve zprávě požadavku problém při vytvoří zprávu odpovědi problém.</span><span class="sxs-lookup"><span data-stu-id="532b0-123">The security token service uses the information in the issue request message when it constructs the Issue Response message.</span></span>  
  
## <a name="response-message-structure"></a><span data-ttu-id="532b0-124">Struktura zpráva odpovědi</span><span class="sxs-lookup"><span data-stu-id="532b0-124">Response Message Structure</span></span>  
 <span data-ttu-id="532b0-125">Struktura zprávu odpovědi problém se obvykle skládá z následujících položek;</span><span class="sxs-lookup"><span data-stu-id="532b0-125">The issue response message structure typically consists of the following items;</span></span>  
  
- <span data-ttu-id="532b0-126">Token vydaný zabezpečení, třeba kontrolní výraz SAML 1.1.</span><span class="sxs-lookup"><span data-stu-id="532b0-126">The issued security token, for example, a SAML 1.1 assertion.</span></span>  
  
- <span data-ttu-id="532b0-127">Token důkazu přidružené k tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="532b0-127">A proof token associated with the security token.</span></span> <span data-ttu-id="532b0-128">Pro symetrické klíče je to často zašifrované materiál klíče.</span><span class="sxs-lookup"><span data-stu-id="532b0-128">For symmetric keys, this is often an encrypted form of the key material.</span></span>  
  
- <span data-ttu-id="532b0-129">Odkazy na token vydaný zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="532b0-129">References to the issued security token.</span></span> <span data-ttu-id="532b0-130">Služba tokenů zabezpečení obvykle vrací odkaz, který se dá použít při vydaný token se zobrazí následující zprávy odeslané klienta a další, který se dá použít při token není k dispozici v dalších zpráv.</span><span class="sxs-lookup"><span data-stu-id="532b0-130">Typically, the security token service returns a reference that can be used when the issued token appears in a subsequent message sent by the client and another that can be used when the token is not present in subsequent messages.</span></span>  
  
 <span data-ttu-id="532b0-131">Kromě toho několik dalších položek, může být k dispozici:</span><span class="sxs-lookup"><span data-stu-id="532b0-131">In addition, a couple of other items might be present:</span></span>  
  
- <span data-ttu-id="532b0-132">Materiál klíče poskytovaných službou tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="532b0-132">Key material provided by the security token service.</span></span>  
  
- <span data-ttu-id="532b0-133">Algoritmus potřebných pro výpočet sdílený klíč.</span><span class="sxs-lookup"><span data-stu-id="532b0-133">The algorithm needed to compute the shared key.</span></span>  
  
- <span data-ttu-id="532b0-134">Informace o životnosti pro vydaný token.</span><span class="sxs-lookup"><span data-stu-id="532b0-134">Lifetime information for the issued token.</span></span>  
  
## <a name="processing-request-messages"></a><span data-ttu-id="532b0-135">Zpracování zpráv požadavků</span><span class="sxs-lookup"><span data-stu-id="532b0-135">Processing Request Messages</span></span>  
 <span data-ttu-id="532b0-136">Služba tokenů zabezpečení zpracuje žádost o problém zkoumání různých součástí zprávy s požadavkem a zajistit, aby mohla vystavovat token, který splňuje požadavek.</span><span class="sxs-lookup"><span data-stu-id="532b0-136">The security token service processes the issue request by examining the various pieces of the request message and ensuring that it can issue a token that satisfies the request.</span></span> <span data-ttu-id="532b0-137">Služba tokenů zabezpečení musí určit následující předtím, než vytvoří token, který má být vydaný:</span><span class="sxs-lookup"><span data-stu-id="532b0-137">The security token service must determine the following before it constructs the token to be issued:</span></span>  
  
- <span data-ttu-id="532b0-138">Požadavek ve skutečnosti je žádost o token vystavování.</span><span class="sxs-lookup"><span data-stu-id="532b0-138">The request really is a request for a token to be issued.</span></span>  
  
- <span data-ttu-id="532b0-139">Služba tokenů zabezpečení podporuje požadovaný typ tokenu.</span><span class="sxs-lookup"><span data-stu-id="532b0-139">The security token service supports the requested token type.</span></span>  
  
- <span data-ttu-id="532b0-140">Žadatel je autorizovaný k odeslání požadavku.</span><span class="sxs-lookup"><span data-stu-id="532b0-140">The requester is authorized to make the request.</span></span>  
  
- <span data-ttu-id="532b0-141">Služba tokenů zabezpečení můžete očekávání žadatele s ohledem na materiál klíče.</span><span class="sxs-lookup"><span data-stu-id="532b0-141">The security token service can meet the requester's expectations with respect to key material.</span></span>  
  
 <span data-ttu-id="532b0-142">Dvě důležité části vytváření token určování jaké klíč k podepsání token s a jaké klíč k šifrování pomocí sdíleného klíče.</span><span class="sxs-lookup"><span data-stu-id="532b0-142">Two vital parts of constructing a token are determining what key to sign the token with and what key to encrypt the shared key with.</span></span> <span data-ttu-id="532b0-143">Token musí být podepsané tak, že když klient poskytne token, který má cílová služba service můžete určit, který byl token vydán službou tokenu zabezpečení, který důvěřuje.</span><span class="sxs-lookup"><span data-stu-id="532b0-143">The token needs to be signed so that when the client presents the token to the target service, that service can determine that the token was issued by a security token service that it trusts.</span></span> <span data-ttu-id="532b0-144">Materiál klíče je potřeba šifrovat tak, že cílová služba mohly dešifrovat tohoto klíče.</span><span class="sxs-lookup"><span data-stu-id="532b0-144">The key material needs to be encrypted in such a way that the target service can decrypt that key material.</span></span>  
  
 <span data-ttu-id="532b0-145">Podepisování kontrolní výraz SAML zahrnuje vytvoření <xref:System.IdentityModel.Tokens.SigningCredentials> instance.</span><span class="sxs-lookup"><span data-stu-id="532b0-145">Signing a SAML assertion involves creating a <xref:System.IdentityModel.Tokens.SigningCredentials> instance.</span></span> <span data-ttu-id="532b0-146">Konstruktor pro tuto třídu používá následující:</span><span class="sxs-lookup"><span data-stu-id="532b0-146">The constructor for this class takes the following:</span></span>  
  
- <span data-ttu-id="532b0-147">A <xref:System.IdentityModel.Tokens.SecurityKey> pro klíč k podepsání kontrolního výrazu SAML.</span><span class="sxs-lookup"><span data-stu-id="532b0-147">A <xref:System.IdentityModel.Tokens.SecurityKey> for the key to use to sign the SAML assertion.</span></span>  
  
- <span data-ttu-id="532b0-148">Řetězec, který určuje použití algoritmu podpisu.</span><span class="sxs-lookup"><span data-stu-id="532b0-148">A string identifying the signature algorithm to use.</span></span>  
  
- <span data-ttu-id="532b0-149">Řetězec, který určuje použití algoritmu digest.</span><span class="sxs-lookup"><span data-stu-id="532b0-149">A string identifying the digest algorithm to use.</span></span>  
  
- <span data-ttu-id="532b0-150">Volitelně můžete <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> , který určuje klíč k podepsání kontrolního výrazu.</span><span class="sxs-lookup"><span data-stu-id="532b0-150">Optionally, a <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> that identifies the key to use to sign the assertion.</span></span>  
  
 [!code-csharp[c_CreateSTS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#1)]
 [!code-vb[c_CreateSTS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#1)]  
  
 <span data-ttu-id="532b0-151">Sdílený klíč šifrování zahrnuje pořizování materiál klíče a šifrování pomocí klíče k dešifrování sdílený klíč můžete použít cílovou službu.</span><span class="sxs-lookup"><span data-stu-id="532b0-151">Encrypting the shared key involves taking the key material and encrypting it with a key that the target service can use to decrypt the shared key.</span></span> <span data-ttu-id="532b0-152">Obvykle se používá veřejný klíč cílovou službu.</span><span class="sxs-lookup"><span data-stu-id="532b0-152">Typically, the public key of the target service is used.</span></span>  
  
 [!code-csharp[c_CreateSTS#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#2)]
 [!code-vb[c_CreateSTS#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#2)]  
  
 <span data-ttu-id="532b0-153">Kromě toho <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> pro šifrovaný klíč je potřeba.</span><span class="sxs-lookup"><span data-stu-id="532b0-153">In addition, a <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> for the encrypted key is needed.</span></span>  
  
 [!code-csharp[c_CreateSTS#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#3)]
 [!code-vb[c_CreateSTS#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#3)]  
  
 <span data-ttu-id="532b0-154">To <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> se pak použije k vytvoření `SamlSubject` jako součást `SamlToken`.</span><span class="sxs-lookup"><span data-stu-id="532b0-154">This <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> is then used to create a `SamlSubject` as part of the `SamlToken`.</span></span>  
  
 [!code-csharp[c_CreateSTS#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#4)]
 [!code-vb[c_CreateSTS#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#4)]  
  
 <span data-ttu-id="532b0-155">Další informace najdete v tématu [ukázka federace](../../../../docs/framework/wcf/samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="532b0-155">For more information, see [Federation Sample](../../../../docs/framework/wcf/samples/federation-sample.md).</span></span>  
  
## <a name="creating-response-messages"></a><span data-ttu-id="532b0-156">Vytváření zprávy odpovědi</span><span class="sxs-lookup"><span data-stu-id="532b0-156">Creating Response Messages</span></span>  
 <span data-ttu-id="532b0-157">Po služby tokenů zabezpečení zpracuje žádost o problému a vytvoří token, který má být vydána spolu s klíč důkazu, zprávy s odpovědí musí být vytvořen, včetně alespoň nedokáže token důkazu a vystavený token odkazy.</span><span class="sxs-lookup"><span data-stu-id="532b0-157">Once the security token service processes the issue request and constructs the token to be issued along with the proof key, the response message needs to be constructed, including at least the requested token, the proof token, and the issued token references.</span></span> <span data-ttu-id="532b0-158">Vydaný token je obvykle <xref:System.IdentityModel.Tokens.SamlSecurityToken> vytvořené z <xref:System.IdentityModel.Tokens.SamlAssertion>, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="532b0-158">The issued token is typically a <xref:System.IdentityModel.Tokens.SamlSecurityToken> created from the <xref:System.IdentityModel.Tokens.SamlAssertion>, as shown in the following example.</span></span>  
  
 [!code-csharp[c_CreateSTS#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#5)]
 [!code-vb[c_CreateSTS#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#5)]  
  
 <span data-ttu-id="532b0-159">V případě, kdy služba tokenů zabezpečení poskytuje materiál sdíleného klíče, je token důkazu vytvořená tak, že vytvoříte <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>.</span><span class="sxs-lookup"><span data-stu-id="532b0-159">In the case where the security token service provides the shared key material, the proof token is constructed by creating a <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>.</span></span>  
  
 [!code-csharp[c_CreateSTS#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#6)]
 [!code-vb[c_CreateSTS#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#6)]  
  
 <span data-ttu-id="532b0-160">Další informace o tom, jak vytvořit token důkazu, když klient a služba tokenů zabezpečení poskytují materiál klíče pro sdílený klíč najdete v tématu [ukázka federace](../../../../docs/framework/wcf/samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="532b0-160">For more information about how to construct the proof token when the client and the security token service both provide key material for the shared key, see [Federation Sample](../../../../docs/framework/wcf/samples/federation-sample.md).</span></span>  
  
 <span data-ttu-id="532b0-161">Vydaný token odkazy jsou vytvořeny ve vytváření instancí <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause> třídy.</span><span class="sxs-lookup"><span data-stu-id="532b0-161">The issued token references are constructed by creating instances of the <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause> class.</span></span>  
  
 [!code-csharp[c_CreateSTS#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#7)]
 [!code-vb[c_CreateSTS#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#7)]  
  
 <span data-ttu-id="532b0-162">Tyto různé hodnoty jsou pak serializován do zprávy s odpovědí vrácen do klienta.</span><span class="sxs-lookup"><span data-stu-id="532b0-162">These various values are then serialized into the response message returned to the client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="532b0-163">Příklad</span><span class="sxs-lookup"><span data-stu-id="532b0-163">Example</span></span>  
 <span data-ttu-id="532b0-164">Úplný kód pro službu tokenů zabezpečení, najdete v části [ukázka federace](../../../../docs/framework/wcf/samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="532b0-164">For full code for a security token service, see [Federation Sample](../../../../docs/framework/wcf/samples/federation-sample.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="532b0-165">Viz také:</span><span class="sxs-lookup"><span data-stu-id="532b0-165">See also</span></span>

- <xref:System.IdentityModel.Tokens.SigningCredentials>
- <xref:System.IdentityModel.Tokens.SecurityKey>
- <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier>
- <xref:System.IdentityModel.Tokens.SamlSecurityToken>
- <xref:System.IdentityModel.Tokens.SamlAssertion>
- <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>
- <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause>
- [<span data-ttu-id="532b0-166">Ukázka federace</span><span class="sxs-lookup"><span data-stu-id="532b0-166">Federation Sample</span></span>](../../../../docs/framework/wcf/samples/federation-sample.md)
