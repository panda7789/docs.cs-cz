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
ms.openlocfilehash: 1cfcca524e5dd2b0c1560eb7600795766e2db1d6
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598954"
---
# <a name="how-to-create-a-security-token-service"></a><span data-ttu-id="8fedc-102">Postupy: Vytvoření služby tokenů zabezpečení</span><span class="sxs-lookup"><span data-stu-id="8fedc-102">How to: Create a Security Token Service</span></span>
<span data-ttu-id="8fedc-103">Služba tokenů zabezpečení implementuje protokol definovaný ve specifikaci WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="8fedc-103">A security token service implements the protocol defined in the WS-Trust specification.</span></span> <span data-ttu-id="8fedc-104">Tento protokol definuje formáty zpráv a vzory výměny zpráv pro vydávání, obnovování, rušení a ověřování tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="8fedc-104">This protocol defines message formats and message exchange patterns for issuing, renewing, canceling, and validating security tokens.</span></span> <span data-ttu-id="8fedc-105">Daná služba tokenů zabezpečení poskytuje jednu nebo více těchto možností.</span><span class="sxs-lookup"><span data-stu-id="8fedc-105">A given security token service provides one or more of these capabilities.</span></span> <span data-ttu-id="8fedc-106">Toto téma se zabývá nejběžnějším scénářem: implementace vystavování tokenu.</span><span class="sxs-lookup"><span data-stu-id="8fedc-106">This topic looks at the most common scenario: implementing token issuance.</span></span>  
  
## <a name="issuing-tokens"></a><span data-ttu-id="8fedc-107">Vydávání tokenů</span><span class="sxs-lookup"><span data-stu-id="8fedc-107">Issuing Tokens</span></span>  
 <span data-ttu-id="8fedc-108">WS-Trust definuje formáty zpráv založené na `RequestSecurityToken` elementu schématu XML Schema Definition Language (XSD) a `RequestSecurityTokenResponse` elementu schématu XSD pro vystavení tokenu.</span><span class="sxs-lookup"><span data-stu-id="8fedc-108">WS-Trust defines message formats, based on the `RequestSecurityToken` XML Schema definition language (XSD) schema element, and `RequestSecurityTokenResponse` XSD schema element for performing token issuance.</span></span> <span data-ttu-id="8fedc-109">Kromě toho definuje přidružené akce identifikátory URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="8fedc-109">In addition, it defines the associated Action Uniform Resource Identifiers (URIs).</span></span> <span data-ttu-id="8fedc-110">Identifikátor URI akce přidružený ke `RequestSecurityToken` zprávě je `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue` .</span><span class="sxs-lookup"><span data-stu-id="8fedc-110">The action URI associated with the `RequestSecurityToken` message is `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue`.</span></span> <span data-ttu-id="8fedc-111">Identifikátor URI akce přidružený ke `RequestSecurityTokenResponse` zprávě je `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue` .</span><span class="sxs-lookup"><span data-stu-id="8fedc-111">The action URI associated with the `RequestSecurityTokenResponse` message is   `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue`.</span></span>  
  
### <a name="request-message-structure"></a><span data-ttu-id="8fedc-112">Požadovat strukturu zpráv</span><span class="sxs-lookup"><span data-stu-id="8fedc-112">Request Message Structure</span></span>  
 <span data-ttu-id="8fedc-113">Struktura zprávy požadavku na problém se obvykle skládá z následujících položek:</span><span class="sxs-lookup"><span data-stu-id="8fedc-113">The issue request message structure typically consists of the following items:</span></span>  
  
- <span data-ttu-id="8fedc-114">Identifikátor URI typu požadavku s hodnotou `http://schemas.xmlsoap.org/ws/2005/02/trust/Issue` .</span><span class="sxs-lookup"><span data-stu-id="8fedc-114">A request type URI with a value of `http://schemas.xmlsoap.org/ws/2005/02/trust/Issue`.</span></span>
  
- <span data-ttu-id="8fedc-115">Identifikátor URI typu tokenu.</span><span class="sxs-lookup"><span data-stu-id="8fedc-115">A token type URI.</span></span> <span data-ttu-id="8fedc-116">Pro tokeny SAML (Security Assert Markup Language) 1,1 je hodnota tohoto identifikátoru URI `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1` .</span><span class="sxs-lookup"><span data-stu-id="8fedc-116">For Security Assertions Markup Language (SAML) 1.1 tokens, the value of this URI is `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1`.</span></span>  
  
- <span data-ttu-id="8fedc-117">Hodnota velikosti klíče určující počet bitů v klíči, které mají být přidruženy k vydanému tokenu.</span><span class="sxs-lookup"><span data-stu-id="8fedc-117">A key size value that indicates the number of bits in the key to be associated with the issued token.</span></span>  
  
- <span data-ttu-id="8fedc-118">Identifikátor URI typu klíče.</span><span class="sxs-lookup"><span data-stu-id="8fedc-118">A key type URI.</span></span> <span data-ttu-id="8fedc-119">U symetrických klíčů je hodnota tohoto identifikátoru URI `http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey` .</span><span class="sxs-lookup"><span data-stu-id="8fedc-119">For symmetric keys, the value of this URI is `http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey`.</span></span>  
  
 <span data-ttu-id="8fedc-120">Kromě toho může být k dispozici několik dalších položek:</span><span class="sxs-lookup"><span data-stu-id="8fedc-120">In addition, a couple of other items might be present:</span></span>  
  
- <span data-ttu-id="8fedc-121">Klíčový materiál poskytovaný klientem</span><span class="sxs-lookup"><span data-stu-id="8fedc-121">Key material provided by the client.</span></span>  
  
- <span data-ttu-id="8fedc-122">Informace o oboru, které označují cílovou službu, se kterou vydaný token bude použit.</span><span class="sxs-lookup"><span data-stu-id="8fedc-122">Scope information that indicates the target service that the issued token will be used with.</span></span>  
  
 <span data-ttu-id="8fedc-123">Služba tokenů zabezpečení používá informace ve zprávě s požadavkem na vydání zprávy při sestavování zprávy s odpovědí na problém.</span><span class="sxs-lookup"><span data-stu-id="8fedc-123">The security token service uses the information in the issue request message when it constructs the Issue Response message.</span></span>  
  
## <a name="response-message-structure"></a><span data-ttu-id="8fedc-124">Struktura zprávy odpovědi</span><span class="sxs-lookup"><span data-stu-id="8fedc-124">Response Message Structure</span></span>  
 <span data-ttu-id="8fedc-125">Struktura zprávy odpovědi na problém se obvykle skládá z následujících položek:</span><span class="sxs-lookup"><span data-stu-id="8fedc-125">The issue response message structure typically consists of the following items;</span></span>  
  
- <span data-ttu-id="8fedc-126">Vydaný token zabezpečení, například kontrolní výraz SAML 1,1.</span><span class="sxs-lookup"><span data-stu-id="8fedc-126">The issued security token, for example, a SAML 1.1 assertion.</span></span>  
  
- <span data-ttu-id="8fedc-127">Token důkazu přidružený k tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="8fedc-127">A proof token associated with the security token.</span></span> <span data-ttu-id="8fedc-128">U symetrických klíčů je to často šifrovaný tvar materiálu klíče.</span><span class="sxs-lookup"><span data-stu-id="8fedc-128">For symmetric keys, this is often an encrypted form of the key material.</span></span>  
  
- <span data-ttu-id="8fedc-129">Odkazy na vydaný token zabezpečení</span><span class="sxs-lookup"><span data-stu-id="8fedc-129">References to the issued security token.</span></span> <span data-ttu-id="8fedc-130">Služba tokenů zabezpečení obvykle vrací odkaz, který může být použit v případě, že se vydaný token zobrazuje v následné zprávě odeslané klientem a další, které lze použít, když se token nenachází v následných zprávách.</span><span class="sxs-lookup"><span data-stu-id="8fedc-130">Typically, the security token service returns a reference that can be used when the issued token appears in a subsequent message sent by the client and another that can be used when the token is not present in subsequent messages.</span></span>  
  
 <span data-ttu-id="8fedc-131">Kromě toho může být k dispozici několik dalších položek:</span><span class="sxs-lookup"><span data-stu-id="8fedc-131">In addition, a couple of other items might be present:</span></span>  
  
- <span data-ttu-id="8fedc-132">Klíčový materiál poskytovaný službou tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="8fedc-132">Key material provided by the security token service.</span></span>  
  
- <span data-ttu-id="8fedc-133">Algoritmus potřebný k výpočtu sdíleného klíče.</span><span class="sxs-lookup"><span data-stu-id="8fedc-133">The algorithm needed to compute the shared key.</span></span>  
  
- <span data-ttu-id="8fedc-134">Informace o životnosti vydaného tokenu.</span><span class="sxs-lookup"><span data-stu-id="8fedc-134">Lifetime information for the issued token.</span></span>  
  
## <a name="processing-request-messages"></a><span data-ttu-id="8fedc-135">Zpracování zpráv s požadavky</span><span class="sxs-lookup"><span data-stu-id="8fedc-135">Processing Request Messages</span></span>  
 <span data-ttu-id="8fedc-136">Služba tokenů zabezpečení zpracovává žádost o vydání vyzkoumáním různých částí zprávy požadavku a zajištěním, že může vydat token, který požadavek splní.</span><span class="sxs-lookup"><span data-stu-id="8fedc-136">The security token service processes the issue request by examining the various pieces of the request message and ensuring that it can issue a token that satisfies the request.</span></span> <span data-ttu-id="8fedc-137">Služba tokenů zabezpečení musí před vytvořením tokenu, který se má vydat, určit následující:</span><span class="sxs-lookup"><span data-stu-id="8fedc-137">The security token service must determine the following before it constructs the token to be issued:</span></span>  
  
- <span data-ttu-id="8fedc-138">Požadavek je skutečně požadavkem na vydání tokenu.</span><span class="sxs-lookup"><span data-stu-id="8fedc-138">The request really is a request for a token to be issued.</span></span>  
  
- <span data-ttu-id="8fedc-139">Služba tokenů zabezpečení podporuje požadovaný typ tokenu.</span><span class="sxs-lookup"><span data-stu-id="8fedc-139">The security token service supports the requested token type.</span></span>  
  
- <span data-ttu-id="8fedc-140">Žadatel má oprávnění k vytvoření žádosti.</span><span class="sxs-lookup"><span data-stu-id="8fedc-140">The requester is authorized to make the request.</span></span>  
  
- <span data-ttu-id="8fedc-141">Služba tokenů zabezpečení může splňovat očekávání žadatele s ohledem na klíčový materiál.</span><span class="sxs-lookup"><span data-stu-id="8fedc-141">The security token service can meet the requester's expectations with respect to key material.</span></span>  
  
 <span data-ttu-id="8fedc-142">Dvě důležité části konstrukce tokenu určují, který klíč k podepsání tokenu má a jaký klíč k šifrování sdíleného klíče má.</span><span class="sxs-lookup"><span data-stu-id="8fedc-142">Two vital parts of constructing a token are determining what key to sign the token with and what key to encrypt the shared key with.</span></span> <span data-ttu-id="8fedc-143">Token musí být podepsán, aby když klient prezentuje token cílové službě, může zjistit, že token byl vydán službou tokenu zabezpečení, kterou důvěřuje.</span><span class="sxs-lookup"><span data-stu-id="8fedc-143">The token needs to be signed so that when the client presents the token to the target service, that service can determine that the token was issued by a security token service that it trusts.</span></span> <span data-ttu-id="8fedc-144">Klíčový materiál musí být zašifrovaný takovým způsobem, že cílová služba může tento klíčový materiál dešifrovat.</span><span class="sxs-lookup"><span data-stu-id="8fedc-144">The key material needs to be encrypted in such a way that the target service can decrypt that key material.</span></span>  
  
 <span data-ttu-id="8fedc-145">Podepisování kontrolního výrazu SAML zahrnuje vytvoření <xref:System.IdentityModel.Tokens.SigningCredentials> instance.</span><span class="sxs-lookup"><span data-stu-id="8fedc-145">Signing a SAML assertion involves creating a <xref:System.IdentityModel.Tokens.SigningCredentials> instance.</span></span> <span data-ttu-id="8fedc-146">Konstruktor pro tuto třídu používá následující:</span><span class="sxs-lookup"><span data-stu-id="8fedc-146">The constructor for this class takes the following:</span></span>  
  
- <span data-ttu-id="8fedc-147">Klíč, který se <xref:System.IdentityModel.Tokens.SecurityKey> má použít k podepsání kontrolního výrazu SAML.</span><span class="sxs-lookup"><span data-stu-id="8fedc-147">A <xref:System.IdentityModel.Tokens.SecurityKey> for the key to use to sign the SAML assertion.</span></span>  
  
- <span data-ttu-id="8fedc-148">Řetězec identifikující algoritmus podpisu, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="8fedc-148">A string identifying the signature algorithm to use.</span></span>  
  
- <span data-ttu-id="8fedc-149">Řetězec identifikující algoritmus Digest, který má být použit.</span><span class="sxs-lookup"><span data-stu-id="8fedc-149">A string identifying the digest algorithm to use.</span></span>  
  
- <span data-ttu-id="8fedc-150">Volitelně, <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> který identifikuje klíč, který se má použít k podepsání kontrolního výrazu.</span><span class="sxs-lookup"><span data-stu-id="8fedc-150">Optionally, a <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> that identifies the key to use to sign the assertion.</span></span>  
  
 [!code-csharp[c_CreateSTS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#1)]
 [!code-vb[c_CreateSTS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#1)]  
  
 <span data-ttu-id="8fedc-151">Šifrování sdíleného klíče zahrnuje pořízení materiálu klíče a jeho šifrování pomocí klíče, který může cílová služba použít k dešifrování sdíleného klíče.</span><span class="sxs-lookup"><span data-stu-id="8fedc-151">Encrypting the shared key involves taking the key material and encrypting it with a key that the target service can use to decrypt the shared key.</span></span> <span data-ttu-id="8fedc-152">Obvykle se používá veřejný klíč cílové služby.</span><span class="sxs-lookup"><span data-stu-id="8fedc-152">Typically, the public key of the target service is used.</span></span>  
  
 [!code-csharp[c_CreateSTS#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#2)]
 [!code-vb[c_CreateSTS#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#2)]  
  
 <span data-ttu-id="8fedc-153"><xref:System.IdentityModel.Tokens.SecurityKeyIdentifier>Pro šifrovaný klíč je navíc potřeba.</span><span class="sxs-lookup"><span data-stu-id="8fedc-153">In addition, a <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> for the encrypted key is needed.</span></span>  
  
 [!code-csharp[c_CreateSTS#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#3)]
 [!code-vb[c_CreateSTS#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#3)]  
  
 <span data-ttu-id="8fedc-154"><xref:System.IdentityModel.Tokens.SecurityKeyIdentifier>Pak se použije k vytvoření `SamlSubject` jako součást `SamlToken` .</span><span class="sxs-lookup"><span data-stu-id="8fedc-154">This <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> is then used to create a `SamlSubject` as part of the `SamlToken`.</span></span>  
  
 [!code-csharp[c_CreateSTS#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#4)]
 [!code-vb[c_CreateSTS#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#4)]  
  
 <span data-ttu-id="8fedc-155">Další informace najdete v tématu [federace – ukázka](../samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="8fedc-155">For more information, see [Federation Sample](../samples/federation-sample.md).</span></span>  
  
## <a name="creating-response-messages"></a><span data-ttu-id="8fedc-156">Vytváření zpráv odpovědí</span><span class="sxs-lookup"><span data-stu-id="8fedc-156">Creating Response Messages</span></span>  
 <span data-ttu-id="8fedc-157">Jakmile služba tokenů zabezpečení zpracuje požadavek na problém a sestaví token, který se má vystavit spolu s klíčem ověření, musí být vytvořena zpráva odpovědi, včetně alespoň požadovaného tokenu, tokenu důkazu a odkazů na vydané tokeny.</span><span class="sxs-lookup"><span data-stu-id="8fedc-157">Once the security token service processes the issue request and constructs the token to be issued along with the proof key, the response message needs to be constructed, including at least the requested token, the proof token, and the issued token references.</span></span> <span data-ttu-id="8fedc-158">Vydaný token je obvykle <xref:System.IdentityModel.Tokens.SamlSecurityToken> vytvořen z rozhraní <xref:System.IdentityModel.Tokens.SamlAssertion> , jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="8fedc-158">The issued token is typically a <xref:System.IdentityModel.Tokens.SamlSecurityToken> created from the <xref:System.IdentityModel.Tokens.SamlAssertion>, as shown in the following example.</span></span>  
  
 [!code-csharp[c_CreateSTS#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#5)]
 [!code-vb[c_CreateSTS#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#5)]  
  
 <span data-ttu-id="8fedc-159">V případě, že služba tokenů zabezpečení poskytuje materiál sdíleného klíče, je token důkazu vytvořen vytvořením <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken> .</span><span class="sxs-lookup"><span data-stu-id="8fedc-159">In the case where the security token service provides the shared key material, the proof token is constructed by creating a <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>.</span></span>  
  
 [!code-csharp[c_CreateSTS#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#6)]
 [!code-vb[c_CreateSTS#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#6)]  
  
 <span data-ttu-id="8fedc-160">Další informace o tom, jak vytvořit token důkazu v případě, že klient a služba tokenů zabezpečení poskytují materiál klíče pro sdílený klíč, najdete v tématu [federace – ukázka](../samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="8fedc-160">For more information about how to construct the proof token when the client and the security token service both provide key material for the shared key, see [Federation Sample](../samples/federation-sample.md).</span></span>  
  
 <span data-ttu-id="8fedc-161">Odkazy na vydané tokeny jsou vytvořené vytvořením instancí <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause> třídy.</span><span class="sxs-lookup"><span data-stu-id="8fedc-161">The issued token references are constructed by creating instances of the <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause> class.</span></span>  
  
 [!code-csharp[c_CreateSTS#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#7)]
 [!code-vb[c_CreateSTS#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#7)]  
  
 <span data-ttu-id="8fedc-162">Tyto různé hodnoty jsou poté serializovány do zprávy odpovědi vrácené klientovi.</span><span class="sxs-lookup"><span data-stu-id="8fedc-162">These various values are then serialized into the response message returned to the client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8fedc-163">Příklad</span><span class="sxs-lookup"><span data-stu-id="8fedc-163">Example</span></span>  
 <span data-ttu-id="8fedc-164">Úplný kód pro službu tokenu zabezpečení najdete v tématu [federace – ukázka](../samples/federation-sample.md).</span><span class="sxs-lookup"><span data-stu-id="8fedc-164">For full code for a security token service, see [Federation Sample](../samples/federation-sample.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fedc-165">Viz také</span><span class="sxs-lookup"><span data-stu-id="8fedc-165">See also</span></span>

- <xref:System.IdentityModel.Tokens.SigningCredentials>
- <xref:System.IdentityModel.Tokens.SecurityKey>
- <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier>
- <xref:System.IdentityModel.Tokens.SamlSecurityToken>
- <xref:System.IdentityModel.Tokens.SamlAssertion>
- <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>
- <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause>
- [<span data-ttu-id="8fedc-166">Ukázka federace</span><span class="sxs-lookup"><span data-stu-id="8fedc-166">Federation Sample</span></span>](../samples/federation-sample.md)
