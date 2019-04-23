---
title: 'Postupy: Změna zprostředkovatele kryptografických služeb pro privátní klíč certifikátu X.509'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptographic provider [WCF], changing
- cryptographic provider [WCF]
ms.assetid: b4254406-272e-4774-bd61-27e39bbb6c12
ms.openlocfilehash: 9d7216b3aed89dc88737cc346386d6b03929fe60
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59295572"
---
# <a name="how-to-change-the-cryptographic-provider-for-an-x509-certificates-private-key"></a>Postupy: Změna zprostředkovatele kryptografických služeb pro privátní klíč certifikátu X.509
Toto téma ukazuje, jak změnit zprostředkovatele kryptografických služeb používají k zajištění privátní klíč certifikátu X.509 a jak integrovat zprostředkovatele do architektury zabezpečení Windows Communication Foundation (WCF). Další informace o používání certifikátů najdete v tématu [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
 Zabezpečení rozhraní WCF poskytuje způsob, jak zavést nové typy tokenů zabezpečení, jak je popsáno v [jak: Vytvoření vlastního tokenu](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md). Je také možné použít vlastní token nahradit existující typy tokenů poskytované systémem.  
  
 V tomto tématu se nahrazuje token zabezpečení poskytované systémem X.509 vlastní token X.509, který poskytuje různé implementace pro privátní klíč certifikátu. To je užitečné v situacích, kdy skutečná privátní klíč poskytuje různé zprostředkovatele kryptografických služeb než výchozí Windows zprostředkovatele kryptografických služeb. Jedním z příkladů alternativní zprostředkovatele kryptografických služeb je modul hardwarového zabezpečení, která provádí všechny privátní klíče související kryptografických operací a neukládá privátní klíče v paměti, a zlepšit zabezpečení systému.  
  
 Následující příklad je pouze pro demonstrační účely. Nenahrazuje výchozí zprostředkovatel kryptografických služeb Windows, ale ukazuje, kde může takový zprostředkovatel integrované.  
  
## <a name="procedures"></a>Procedury  
 Každý token zabezpečení, který má přiřazený bezpečnostní klíč nebo klíče, musí implementovat <xref:System.IdentityModel.Tokens.SecurityToken.SecurityKeys%2A> vlastnost, která vrátí kolekci klíčů z instance tokenu zabezpečení. Pokud je token token zabezpečení X.509, kolekce obsahuje jednu instanci <xref:System.IdentityModel.Tokens.X509AsymmetricSecurityKey> třídu, která představuje veřejného a privátního klíče přidruženého k certifikátu. Pokud chcete nahradit výchozí zprostředkovatele kryptografických služeb použitý k poskytnutí klíčů certifikátu, vytvořte novou implementaci této třídy.  
  
#### <a name="to-create-a-custom-x509-asymmetric-key"></a>Chcete-li vytvořit vlastní asymetrického klíče X.509  
  
1. Definovat nové třídy odvozené od <xref:System.IdentityModel.Tokens.X509AsymmetricSecurityKey> třídy.  
  
2. Přepsat <xref:System.IdentityModel.Tokens.SecurityKey.KeySize%2A> vlastnost jen pro čtení. Tato vlastnost vrátí skutečná velikost klíče dvojice veřejného/soukromého klíče certifikátu.  
  
3. Přepsat <xref:System.IdentityModel.Tokens.SecurityKey.DecryptKey%2A> metody. Tato metoda je volána rozhraním zabezpečení WCF k dešifrování symetrického klíče se privátní klíč certifikátu. (Klíč byla dříve zašifrována pomocí certifikátu veřejného klíče.)  
  
4. Přepsat <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey.GetAsymmetricAlgorithm%2A> metody. Tato metoda je volána rozhraním zabezpečení WCF k získání instance <xref:System.Security.Cryptography.AsymmetricAlgorithm> Třída zastupující zprostředkovatele kryptografických služeb pro buď privátního nebo veřejného klíče certifikátu, v závislosti na parametrech předaný metodě.  
  
5. Volitelné. Přepsat <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey.GetHashAlgorithmForSignature%2A> metody. Potlačí tuto metodu, pokud se na různé implementace <xref:System.Security.Cryptography.HashAlgorithm> třída je povinné.  
  
6. Přepsat <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey.GetSignatureFormatter%2A> metody. Tato metoda vrátí instanci <xref:System.Security.Cryptography.AsymmetricSignatureFormatter> třídy, který je přidružený privátní klíč certifikátu.  
  
7. Přepsat <xref:System.IdentityModel.Tokens.SecurityKey.IsSupportedAlgorithm%2A> metody. Tato metoda se používá k označení, zda konkrétní kryptografický algoritmus je podporováno implementací zabezpečení klíčů.  
  
     [!code-csharp[c_CustomX509Token#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#1)]
     [!code-vb[c_CustomX509Token#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#1)]  
  
 Následující postup ukazuje, jak integrovat vlastní X.509 asymetrického klíče implementace zabezpečení vytvořili v předchozím postupu pomocí architektury zabezpečení WCF, aby bylo možné nahradit X.509 zabezpečení poskytované systémem tokenu.  
  
#### <a name="to-replace-the-system-provided-x509-security-token-with-a-custom-x509-asymmetric-security-key-token"></a>Nahraďte vlastní X.509 asymetrického klíče token zabezpečení poskytované systémem token zabezpečení X.509  
  
1. Vytvoření vlastního tokenu zabezpečení X.509, který vrací vlastní klíč asymetrické zabezpečení X.509, místo abyste klíč zabezpečení poskytnuté systémem, jak je znázorněno v následujícím příkladu. Další informace o zabezpečení vlastních tokenů, naleznete v tématu [jak: Vytvoření vlastního tokenu](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
     [!code-csharp[c_CustomX509Token#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#2)]
     [!code-vb[c_CustomX509Token#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#2)]  
  
2. Vytvoření vlastního zprostředkovatele tokenů zabezpečení, která vrací vlastní X.509 token zabezpečení, jak je znázorněno v příkladu. Další informace o poskytovatelích vlastní bezpečnostní token, naleznete v tématu [jak: Vytvoření vlastního zprostředkovatele tokenů zabezpečení](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md).  
  
     [!code-csharp[c_CustomX509Token#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#3)]
     [!code-vb[c_CustomX509Token#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#3)]  
  
3. Pokud vlastní bezpečnostní klíč se musí použít na straně iniciátor, vytvořte vlastní klienta Správce tokenů zabezpečení a vlastních klientských přihlašovacích údajů třídy, jak je znázorněno v následujícím příkladu. Další informace o vlastních klientských přihlašovacích údajů a Správce tokenu zabezpečení klienta najdete v tématu [názorný postup: Vytvoření vlastního klienta a pověření služby](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
     [!code-csharp[c_CustomX509Token#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#4)]
     [!code-vb[c_CustomX509Token#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#4)]  
  
     [!code-csharp[c_CustomX509Token#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#6)]
     [!code-vb[c_CustomX509Token#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#6)]  
  
4. Pokud vlastní bezpečnostní klíč se musí použít na straně příjemce, vytvořte Správce tokenů zabezpečení vlastní služby a služby vlastní přihlašovací údaje, jak je znázorněno v následujícím příkladu. Další informace o pověření vlastní služby a Správce tokenu zabezpečení služby najdete v tématu [názorný postup: Vytvoření vlastního klienta a pověření služby](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
     [!code-csharp[c_CustomX509Token#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#5)]
     [!code-vb[c_CustomX509Token#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#5)]  
  
     [!code-csharp[c_CustomX509Token#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#7)]
     [!code-vb[c_CustomX509Token#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#7)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.IdentityModel.Tokens.X509AsymmetricSecurityKey>
- <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey>
- <xref:System.IdentityModel.Tokens.SecurityKey>
- <xref:System.Security.Cryptography.AsymmetricAlgorithm>
- <xref:System.Security.Cryptography.HashAlgorithm>
- <xref:System.Security.Cryptography.AsymmetricSignatureFormatter>
- [Návod: Vytvoření vlastního klienta a pověření služby](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)
- [Postupy: Vytvořit vlastní bezpečnostní ověřovací data tokenu](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)
- [Postupy: Vytvoření vlastního zprostředkovatele tokenů zabezpečení](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)
- [Postupy: Vytvoření vlastního tokenu](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)
