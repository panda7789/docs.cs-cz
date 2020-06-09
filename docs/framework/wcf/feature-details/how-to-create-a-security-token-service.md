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
# <a name="how-to-create-a-security-token-service"></a>Postupy: Vytvoření služby tokenů zabezpečení
Služba tokenů zabezpečení implementuje protokol definovaný ve specifikaci WS-Trust. Tento protokol definuje formáty zpráv a vzory výměny zpráv pro vydávání, obnovování, rušení a ověřování tokenů zabezpečení. Daná služba tokenů zabezpečení poskytuje jednu nebo více těchto možností. Toto téma se zabývá nejběžnějším scénářem: implementace vystavování tokenu.  
  
## <a name="issuing-tokens"></a>Vydávání tokenů  
 WS-Trust definuje formáty zpráv založené na `RequestSecurityToken` elementu schématu XML Schema Definition Language (XSD) a `RequestSecurityTokenResponse` elementu schématu XSD pro vystavení tokenu. Kromě toho definuje přidružené akce identifikátory URI (Uniform Resource Identifier). Identifikátor URI akce přidružený ke `RequestSecurityToken` zprávě je `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue` . Identifikátor URI akce přidružený ke `RequestSecurityTokenResponse` zprávě je `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue` .  
  
### <a name="request-message-structure"></a>Požadovat strukturu zpráv  
 Struktura zprávy požadavku na problém se obvykle skládá z následujících položek:  
  
- Identifikátor URI typu požadavku s hodnotou `http://schemas.xmlsoap.org/ws/2005/02/trust/Issue` .
  
- Identifikátor URI typu tokenu. Pro tokeny SAML (Security Assert Markup Language) 1,1 je hodnota tohoto identifikátoru URI `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1` .  
  
- Hodnota velikosti klíče určující počet bitů v klíči, které mají být přidruženy k vydanému tokenu.  
  
- Identifikátor URI typu klíče. U symetrických klíčů je hodnota tohoto identifikátoru URI `http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey` .  
  
 Kromě toho může být k dispozici několik dalších položek:  
  
- Klíčový materiál poskytovaný klientem  
  
- Informace o oboru, které označují cílovou službu, se kterou vydaný token bude použit.  
  
 Služba tokenů zabezpečení používá informace ve zprávě s požadavkem na vydání zprávy při sestavování zprávy s odpovědí na problém.  
  
## <a name="response-message-structure"></a>Struktura zprávy odpovědi  
 Struktura zprávy odpovědi na problém se obvykle skládá z následujících položek:  
  
- Vydaný token zabezpečení, například kontrolní výraz SAML 1,1.  
  
- Token důkazu přidružený k tokenu zabezpečení. U symetrických klíčů je to často šifrovaný tvar materiálu klíče.  
  
- Odkazy na vydaný token zabezpečení Služba tokenů zabezpečení obvykle vrací odkaz, který může být použit v případě, že se vydaný token zobrazuje v následné zprávě odeslané klientem a další, které lze použít, když se token nenachází v následných zprávách.  
  
 Kromě toho může být k dispozici několik dalších položek:  
  
- Klíčový materiál poskytovaný službou tokenů zabezpečení.  
  
- Algoritmus potřebný k výpočtu sdíleného klíče.  
  
- Informace o životnosti vydaného tokenu.  
  
## <a name="processing-request-messages"></a>Zpracování zpráv s požadavky  
 Služba tokenů zabezpečení zpracovává žádost o vydání vyzkoumáním různých částí zprávy požadavku a zajištěním, že může vydat token, který požadavek splní. Služba tokenů zabezpečení musí před vytvořením tokenu, který se má vydat, určit následující:  
  
- Požadavek je skutečně požadavkem na vydání tokenu.  
  
- Služba tokenů zabezpečení podporuje požadovaný typ tokenu.  
  
- Žadatel má oprávnění k vytvoření žádosti.  
  
- Služba tokenů zabezpečení může splňovat očekávání žadatele s ohledem na klíčový materiál.  
  
 Dvě důležité části konstrukce tokenu určují, který klíč k podepsání tokenu má a jaký klíč k šifrování sdíleného klíče má. Token musí být podepsán, aby když klient prezentuje token cílové službě, může zjistit, že token byl vydán službou tokenu zabezpečení, kterou důvěřuje. Klíčový materiál musí být zašifrovaný takovým způsobem, že cílová služba může tento klíčový materiál dešifrovat.  
  
 Podepisování kontrolního výrazu SAML zahrnuje vytvoření <xref:System.IdentityModel.Tokens.SigningCredentials> instance. Konstruktor pro tuto třídu používá následující:  
  
- Klíč, který se <xref:System.IdentityModel.Tokens.SecurityKey> má použít k podepsání kontrolního výrazu SAML.  
  
- Řetězec identifikující algoritmus podpisu, který se má použít.  
  
- Řetězec identifikující algoritmus Digest, který má být použit.  
  
- Volitelně, <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> který identifikuje klíč, který se má použít k podepsání kontrolního výrazu.  
  
 [!code-csharp[c_CreateSTS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#1)]
 [!code-vb[c_CreateSTS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#1)]  
  
 Šifrování sdíleného klíče zahrnuje pořízení materiálu klíče a jeho šifrování pomocí klíče, který může cílová služba použít k dešifrování sdíleného klíče. Obvykle se používá veřejný klíč cílové služby.  
  
 [!code-csharp[c_CreateSTS#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#2)]
 [!code-vb[c_CreateSTS#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#2)]  
  
 <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier>Pro šifrovaný klíč je navíc potřeba.  
  
 [!code-csharp[c_CreateSTS#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#3)]
 [!code-vb[c_CreateSTS#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#3)]  
  
 <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier>Pak se použije k vytvoření `SamlSubject` jako součást `SamlToken` .  
  
 [!code-csharp[c_CreateSTS#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#4)]
 [!code-vb[c_CreateSTS#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#4)]  
  
 Další informace najdete v tématu [federace – ukázka](../samples/federation-sample.md).  
  
## <a name="creating-response-messages"></a>Vytváření zpráv odpovědí  
 Jakmile služba tokenů zabezpečení zpracuje požadavek na problém a sestaví token, který se má vystavit spolu s klíčem ověření, musí být vytvořena zpráva odpovědi, včetně alespoň požadovaného tokenu, tokenu důkazu a odkazů na vydané tokeny. Vydaný token je obvykle <xref:System.IdentityModel.Tokens.SamlSecurityToken> vytvořen z rozhraní <xref:System.IdentityModel.Tokens.SamlAssertion> , jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[c_CreateSTS#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#5)]
 [!code-vb[c_CreateSTS#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#5)]  
  
 V případě, že služba tokenů zabezpečení poskytuje materiál sdíleného klíče, je token důkazu vytvořen vytvořením <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken> .  
  
 [!code-csharp[c_CreateSTS#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#6)]
 [!code-vb[c_CreateSTS#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#6)]  
  
 Další informace o tom, jak vytvořit token důkazu v případě, že klient a služba tokenů zabezpečení poskytují materiál klíče pro sdílený klíč, najdete v tématu [federace – ukázka](../samples/federation-sample.md).  
  
 Odkazy na vydané tokeny jsou vytvořené vytvořením instancí <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause> třídy.  
  
 [!code-csharp[c_CreateSTS#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#7)]
 [!code-vb[c_CreateSTS#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#7)]  
  
 Tyto různé hodnoty jsou poté serializovány do zprávy odpovědi vrácené klientovi.  
  
## <a name="example"></a>Příklad  
 Úplný kód pro službu tokenu zabezpečení najdete v tématu [federace – ukázka](../samples/federation-sample.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.IdentityModel.Tokens.SigningCredentials>
- <xref:System.IdentityModel.Tokens.SecurityKey>
- <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier>
- <xref:System.IdentityModel.Tokens.SamlSecurityToken>
- <xref:System.IdentityModel.Tokens.SamlAssertion>
- <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>
- <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause>
- [Ukázka federace](../samples/federation-sample.md)
