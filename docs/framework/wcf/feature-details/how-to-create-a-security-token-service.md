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
ms.openlocfilehash: 827fef90a6277387ceac1c8f1d6df00a69a5d612
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-create-a-security-token-service"></a>Postupy: Vytvoření služby tokenů zabezpečení
Služby tokenů zabezpečení implementuje protokol definovaný ve specifikaci WS-Trust. Tento protokol definuje formáty zpráv a vzory exchange zprávu pro vystavování, obnovení, zrušení a ověřování tokenů zabezpečení. Služba tokenů zabezpečení poskytuje jeden nebo více z těchto funkcí. Toto téma vypadá nejvíce běžný scénář: implementace vystavování tokenů.  
  
## <a name="issuing-tokens"></a>Vydávání tokenů  
 WS-Trust definuje formáty zpráv, na základě `RequestSecurityToken` schématu XML definition language (XSD) schématu elementu, a `RequestSecurityTokenResponse` element schématu XSD pro provádění vystavování tokenů. Kromě toho definuje přidružené akce identifikátory Uniform Resource (Identifier). Akce přidružené k identifikátoru URI `RequestSecurityToken` zpráva http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue. Akce přidružené k identifikátoru URI `RequestSecurityTokenResponse` zpráva http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue.  
  
### <a name="request-message-structure"></a>Struktura zprávy požadavku  
 Struktura zprávy požadavku problém se obvykle skládá z následujících položek:  
  
-   Žádost o zadejte identifikátor URI s hodnotou http://schemas.xmlsoap.org/ws/2005/02/trust/Issue.  
  
-   Token typ identifikátoru URI. Pro tokeny zabezpečení kontrolní výrazy Markup Language (SAML) 1.1, hodnota tento identifikátor URI je http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1.  
  
-   Velikost klíče hodnotu, která určuje počet bitů klíč, který chcete přidružit vydaný token.  
  
-   Klíče typu identifikátor URI. Symetrické klíče, je hodnota tento identifikátor URI http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey.  
  
 Kromě toho může být několik další položky k dispozici:  
  
-   Materiál klíče zadaných klientem.  
  
-   Obor informace, které určuje cílovou službu, která se použije vystavený token.  
  
 Služby tokenů zabezpečení používá informace ve zprávě požadavku problém, když se vytvoří zprávu odpovědi problém.  
  
## <a name="response-message-structure"></a>Struktura zprávu odpovědi  
 Struktura zprávu odpovědi problém se obvykle skládá z následujících položek;  
  
-   Token zabezpečení vydané, například SAML 1.1 kontrolní výraz.  
  
-   Doklad token přidružené k tokenu zabezpečení. Pro symetrické klíče je to často šifrovaném formátu materiál klíče.  
  
-   Odkazy na token vydaných zabezpečení. Obvykle služby tokenů zabezpečení vrátí odkaz, který lze použít při následné zprávy poslal klienta a druhou, která lze použít, pokud token není k dispozici v dalších zpráv se zobrazí vydaný token.  
  
 Kromě toho může být několik další položky k dispozici:  
  
-   Materiál klíče poskytované služby tokenů zabezpečení.  
  
-   Algoritmus potřebné k výpočtu sdílený klíč.  
  
-   Doba platnosti informace pro vydané token.  
  
## <a name="processing-request-messages"></a>Zpracování zpráv požadavků  
 Služby tokenů zabezpečení zpracuje požadavek problém zkoumání jednotlivých částí zprávy požadavku a zajištění, aby mohla vystavovat token, který splňuje požadavek. Předtím, než se vytvoří token, který má být vydaný, musíte určit služby tokenů zabezpečení následující:  
  
-   Žádost je opravdu žádost o token pro vystavování.  
  
-   Služby tokenů zabezpečení podporuje požadovaný typ tokenu.  
  
-   Žadatel je oprávnění k vytvoření žádosti.  
  
-   Služby tokenů zabezpečení můžete splnit očekávání žadatele s ohledem na materiál klíče.  
  
 Jaké k podepsání token s a jaké klíč k šifrování se sdílený klíč s určování dvě důležité části vytváření token. Token musí být podepsané tak, aby při klienta uvede token, který má cílovou službu, můžete určit služby, který byl token vydán službu tokenů zabezpečení, která důvěřuje. Materiál klíče musí být šifrované tak, že cílová služba může dešifrovat tento materiál klíče.  
  
 Podepisování kontrolního výrazu SAML zahrnuje vytvoření <xref:System.IdentityModel.Tokens.SigningCredentials> instance. V konstruktoru pro tuto třídu přijímá následující:  
  
-   A <xref:System.IdentityModel.Tokens.SecurityKey> pro klíč sloužící k podepisování kontrolního výrazu SAML.  
  
-   Řetězec, který určuje algoritmus podpisu používat.  
  
-   Řetězec, který určuje algoritmus digest používat.  
  
-   Volitelně můžete <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> identifikující klíč sloužící k podepisování kontrolní výraz.  
  
 [!code-csharp[c_CreateSTS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#1)]
 [!code-vb[c_CreateSTS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#1)]  
  
 Šifrování se sdílený klíč zahrnuje trvá materiál klíče a šifrování pomocí klíče, Cílová služba můžete použít k dešifrování sdílený klíč. Obvykle se používá veřejný klíč z cílových služeb.  
  
 [!code-csharp[c_CreateSTS#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#2)]
 [!code-vb[c_CreateSTS#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#2)]  
  
 Kromě toho <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> pro šifrovaný klíč je potřeba.  
  
 [!code-csharp[c_CreateSTS#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#3)]
 [!code-vb[c_CreateSTS#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#3)]  
  
 To <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> se pak použije k vytvoření `SamlSubject` jako součást `SamlToken`.  
  
 [!code-csharp[c_CreateSTS#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#4)]
 [!code-vb[c_CreateSTS#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#4)]  
  
 Další informace najdete v tématu [ukázka federace](../../../../docs/framework/wcf/samples/federation-sample.md).  
  
## <a name="creating-response-messages"></a>Vytváření odpovědí na zprávy  
 Jakmile služby tokenů zabezpečení zpracuje žádost o problému a vytvoří token, který má být vydaný společně s doklad klíčem, zprávu odpovědi musí zkonstruovat, včetně alespoň požadovaný token, doklad token a odkazy na vydaných tokenů. Vystavený token je obvykle <xref:System.IdentityModel.Tokens.SamlSecurityToken> vytvořené z <xref:System.IdentityModel.Tokens.SamlAssertion>, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[c_CreateSTS#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#5)]
 [!code-vb[c_CreateSTS#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#5)]  
  
 V případě, kdy služby tokenů zabezpečení poskytuje sdílené materiál klíče, doklad token je vytvořený tak, že vytvoříte <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>.  
  
 [!code-csharp[c_CreateSTS#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#6)]
 [!code-vb[c_CreateSTS#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#6)]  
  
 Další informace o tom, jak vytvořit doklad token, když klienta a služby tokenů zabezpečení poskytují materiál klíče pro sdílený klíč najdete v tématu [ukázka federace](../../../../docs/framework/wcf/samples/federation-sample.md).  
  
 Vystavený token odkazy se vytvářejí pomocí instancí <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause> třídy.  
  
 [!code-csharp[c_CreateSTS#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#7)]
 [!code-vb[c_CreateSTS#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#7)]  
  
 Tyto různé hodnoty jsou pak serializovat do zprávu odpovědi vrácen do klienta.  
  
## <a name="example"></a>Příklad  
 Úplný kód pro službu tokenů zabezpečení, najdete v části [ukázka federace](../../../../docs/framework/wcf/samples/federation-sample.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IdentityModel.Tokens.SigningCredentials>  
 <xref:System.IdentityModel.Tokens.SecurityKey>  
 <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier>  
 <xref:System.IdentityModel.Tokens.SamlSecurityToken>  
 <xref:System.IdentityModel.Tokens.SamlAssertion>  
 <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>  
 <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause>  
 [Ukázka federace](../../../../docs/framework/wcf/samples/federation-sample.md)
