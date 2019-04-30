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
ms.openlocfilehash: 1d4964cf0379b35c4955bf45d8a7c0fd40477c9f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61787670"
---
# <a name="how-to-create-a-security-token-service"></a>Postupy: Vytvoření služby tokenů zabezpečení
Služba tokenů zabezpečení implementuje protokol definovaných ve specifikaci WS-Trust. Tento protokol definuje formáty zpráv a zpráv exchange vzory pro vystavování, obnovení, zrušení a ověřování tokenů zabezpečení. Služba tokenů zabezpečení obsahuje nejméně jeden z těchto možností. Toto téma vypadá nanejvýš běžný scénář: implementace vystavování tokenů.  
  
## <a name="issuing-tokens"></a>Vystavování tokenů  
 WS-Trust definuje formáty zpráv, na základě `RequestSecurityToken` element schématu XML definice jazyk (XSD) schématu, a `RequestSecurityTokenResponse` element schématu XSD pro provádění vystavování tokenů. Kromě toho definuje přidružené identifikátory Uniform Resource (identifikátory URI) akce. Akci přidruženou k identifikátoru URI `RequestSecurityToken` zpráva `http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue`. Akci přidruženou k identifikátoru URI `RequestSecurityTokenResponse` zpráva `http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue`.  
  
### <a name="request-message-structure"></a>Struktura zprávy požadavku  
 Struktura zprávy požadavku problém se obvykle skládá z následujících položek:  
  
- Žádost o zadejte identifikátor URI s hodnotou `http://schemas.xmlsoap.org/ws/2005/02/trust/Issue`.
  
- Token typu identifikátoru URI. Pro tokeny zabezpečení kontrolní výrazy SAML (Markup Language) 1.1, hodnota tohoto identifikátoru URI je `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1`.  
  
- Velikost klíče hodnota, která určuje počet bitů v klíči, který se má přidružit vydaný token.  
  
- Klíče typu identifikátoru URI. Pro symetrické klíče, hodnota tohoto identifikátoru URI je `http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey`.  
  
 Kromě toho několik dalších položek, může být k dispozici:  
  
- Materiál klíče, který klient poskytl.  
  
- Informace o oboru, která určuje, který se použije vydaný token s cílovou službu.  
  
 Služba tokenů zabezpečení používá informace ve zprávě požadavku problém při vytvoří zprávu odpovědi problém.  
  
## <a name="response-message-structure"></a>Struktura zpráva odpovědi  
 Struktura zprávu odpovědi problém se obvykle skládá z následujících položek;  
  
- Token vydaný zabezpečení, třeba kontrolní výraz SAML 1.1.  
  
- Token důkazu přidružené k tokenu zabezpečení. Pro symetrické klíče je to často zašifrované materiál klíče.  
  
- Odkazy na token vydaný zabezpečení. Služba tokenů zabezpečení obvykle vrací odkaz, který se dá použít při vydaný token se zobrazí následující zprávy odeslané klienta a další, který se dá použít při token není k dispozici v dalších zpráv.  
  
 Kromě toho několik dalších položek, může být k dispozici:  
  
- Materiál klíče poskytovaných službou tokenu zabezpečení.  
  
- Algoritmus potřebných pro výpočet sdílený klíč.  
  
- Informace o životnosti pro vydaný token.  
  
## <a name="processing-request-messages"></a>Zpracování zpráv požadavků  
 Služba tokenů zabezpečení zpracuje žádost o problém zkoumání různých součástí zprávy s požadavkem a zajistit, aby mohla vystavovat token, který splňuje požadavek. Služba tokenů zabezpečení musí určit následující předtím, než vytvoří token, který má být vydaný:  
  
- Požadavek ve skutečnosti je žádost o token vystavování.  
  
- Služba tokenů zabezpečení podporuje požadovaný typ tokenu.  
  
- Žadatel je autorizovaný k odeslání požadavku.  
  
- Služba tokenů zabezpečení můžete očekávání žadatele s ohledem na materiál klíče.  
  
 Dvě důležité části vytváření token určování jaké klíč k podepsání token s a jaké klíč k šifrování pomocí sdíleného klíče. Token musí být podepsané tak, že když klient poskytne token, který má cílová služba service můžete určit, který byl token vydán službou tokenu zabezpečení, který důvěřuje. Materiál klíče je potřeba šifrovat tak, že cílová služba mohly dešifrovat tohoto klíče.  
  
 Podepisování kontrolní výraz SAML zahrnuje vytvoření <xref:System.IdentityModel.Tokens.SigningCredentials> instance. Konstruktor pro tuto třídu používá následující:  
  
- A <xref:System.IdentityModel.Tokens.SecurityKey> pro klíč k podepsání kontrolního výrazu SAML.  
  
- Řetězec, který určuje použití algoritmu podpisu.  
  
- Řetězec, který určuje použití algoritmu digest.  
  
- Volitelně můžete <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> , který určuje klíč k podepsání kontrolního výrazu.  
  
 [!code-csharp[c_CreateSTS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#1)]
 [!code-vb[c_CreateSTS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#1)]  
  
 Sdílený klíč šifrování zahrnuje pořizování materiál klíče a šifrování pomocí klíče k dešifrování sdílený klíč můžete použít cílovou službu. Obvykle se používá veřejný klíč cílovou službu.  
  
 [!code-csharp[c_CreateSTS#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#2)]
 [!code-vb[c_CreateSTS#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#2)]  
  
 Kromě toho <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> pro šifrovaný klíč je potřeba.  
  
 [!code-csharp[c_CreateSTS#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#3)]
 [!code-vb[c_CreateSTS#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#3)]  
  
 To <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> se pak použije k vytvoření `SamlSubject` jako součást `SamlToken`.  
  
 [!code-csharp[c_CreateSTS#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#4)]
 [!code-vb[c_CreateSTS#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#4)]  
  
 Další informace najdete v tématu [ukázka federace](../../../../docs/framework/wcf/samples/federation-sample.md).  
  
## <a name="creating-response-messages"></a>Vytváření zprávy odpovědi  
 Po služby tokenů zabezpečení zpracuje žádost o problému a vytvoří token, který má být vydána spolu s klíč důkazu, zprávy s odpovědí musí být vytvořen, včetně alespoň nedokáže token důkazu a vystavený token odkazy. Vydaný token je obvykle <xref:System.IdentityModel.Tokens.SamlSecurityToken> vytvořené z <xref:System.IdentityModel.Tokens.SamlAssertion>, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[c_CreateSTS#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#5)]
 [!code-vb[c_CreateSTS#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#5)]  
  
 V případě, kdy služba tokenů zabezpečení poskytuje materiál sdíleného klíče, je token důkazu vytvořená tak, že vytvoříte <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>.  
  
 [!code-csharp[c_CreateSTS#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#6)]
 [!code-vb[c_CreateSTS#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#6)]  
  
 Další informace o tom, jak vytvořit token důkazu, když klient a služba tokenů zabezpečení poskytují materiál klíče pro sdílený klíč najdete v tématu [ukázka federace](../../../../docs/framework/wcf/samples/federation-sample.md).  
  
 Vydaný token odkazy jsou vytvořeny ve vytváření instancí <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause> třídy.  
  
 [!code-csharp[c_CreateSTS#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#7)]
 [!code-vb[c_CreateSTS#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#7)]  
  
 Tyto různé hodnoty jsou pak serializován do zprávy s odpovědí vrácen do klienta.  
  
## <a name="example"></a>Příklad  
 Úplný kód pro službu tokenů zabezpečení, najdete v části [ukázka federace](../../../../docs/framework/wcf/samples/federation-sample.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IdentityModel.Tokens.SigningCredentials>
- <xref:System.IdentityModel.Tokens.SecurityKey>
- <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier>
- <xref:System.IdentityModel.Tokens.SamlSecurityToken>
- <xref:System.IdentityModel.Tokens.SamlAssertion>
- <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>
- <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause>
- [Ukázka federace](../../../../docs/framework/wcf/samples/federation-sample.md)
