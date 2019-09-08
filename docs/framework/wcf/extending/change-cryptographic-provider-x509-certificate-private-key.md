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
ms.openlocfilehash: 8101c0d1214eed2c6ea42a4faab774207aab3a79
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797275"
---
# <a name="how-to-change-the-cryptographic-provider-for-an-x509-certificates-private-key"></a>Postupy: Změna zprostředkovatele kryptografických služeb pro privátní klíč certifikátu X.509
V tomto tématu se dozvíte, jak změnit zprostředkovatele kryptografických služeb, který poskytuje privátní klíč certifikátu X. 509 a jak se dá poskytovatel integrovat do architektury zabezpečení služby Windows Communication Foundation (WCF). Další informace o používání certifikátů najdete v tématu [práce s certifikáty](../feature-details/working-with-certificates.md).  
  
 Rozhraní WCF Security Framework poskytuje způsob, jak zavést nové typy tokenů zabezpečení, jak [je popsáno v tématu Postupy: Vytvoření vlastního tokenu](how-to-create-a-custom-token.md) Pomocí vlastního tokenu je také možné nahradit existující typy tokenů poskytnutých systémem.  
  
 V tomto tématu se systémem poskytnutý token zabezpečení X. 509 nahrazuje vlastním tokenem X. 509, který poskytuje odlišnou implementaci privátního klíče certifikátu. To je užitečné ve scénářích, kdy je skutečný privátní klíč poskytovaný jiným zprostředkovatelem kryptografických služeb než s výchozím zprostředkovatelem kryptografických služeb systému Windows. Jedním z příkladů alternativního zprostředkovatele kryptografických služeb je modul hardwarového zabezpečení, který provádí všechny kryptografické operace spojené s privátním klíčem a neukládá privátní klíče do paměti. tím se zvyšuje zabezpečení systému.  
  
 Následující příklad slouží pouze k demonstračním účelům. Nenahrazuje výchozího zprostředkovatele kryptografických služeb systému Windows, ale zobrazuje, kde může být takový poskytovatel integrovaný.  
  
## <a name="procedures"></a>Procedury  
 Každý token zabezpečení, který má přidružený klíč zabezpečení nebo klíče, musí implementovat <xref:System.IdentityModel.Tokens.SecurityToken.SecurityKeys%2A> vlastnost, která vrací kolekci klíčů z instance tokenu zabezpečení. Pokud je tokenem token zabezpečení X. 509, kolekce obsahuje jednu instanci <xref:System.IdentityModel.Tokens.X509AsymmetricSecurityKey> třídy, která představuje veřejné i privátní klíče přidružené k certifikátu. Pokud chcete nahradit výchozího zprostředkovatele kryptografických služeb, který se používá k zadání klíčů certifikátu, vytvořte novou implementaci této třídy.  
  
#### <a name="to-create-a-custom-x509-asymmetric-key"></a>Vytvoření vlastního asymetrického klíče X. 509  
  
1. Definujte novou třídu odvozenou z <xref:System.IdentityModel.Tokens.X509AsymmetricSecurityKey> třídy.  
  
2. Přepsat vlastnost <xref:System.IdentityModel.Tokens.SecurityKey.KeySize%2A> , která je jen pro čtení. Tato vlastnost vrací skutečnou velikost páru veřejného a privátního klíče certifikátu.  
  
3. Přepsat <xref:System.IdentityModel.Tokens.SecurityKey.DecryptKey%2A> metody. Tato metoda je volána rozhraním Security Framework pro WCF k dešifrování symetrického klíče pomocí privátního klíče certifikátu. (Klíč byl předtím zašifrovaný pomocí veřejného klíče certifikátu.)  
  
4. Přepsat <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey.GetAsymmetricAlgorithm%2A> metody. Tato metoda je volána rozhraním zabezpečení WCF pro získání instance <xref:System.Security.Cryptography.AsymmetricAlgorithm> třídy, která představuje zprostředkovatele kryptografických služeb buď privátního nebo veřejného klíče certifikátu, v závislosti na parametrech předaných metodě.  
  
5. Volitelný parametr. Přepsat <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey.GetHashAlgorithmForSignature%2A> metody. Tuto metodu přepište, pokud je vyžadována jiná <xref:System.Security.Cryptography.HashAlgorithm> implementace třídy.  
  
6. Přepsat <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey.GetSignatureFormatter%2A> metody. Tato metoda vrátí instanci <xref:System.Security.Cryptography.AsymmetricSignatureFormatter> třídy, která je přidružena k privátnímu klíči certifikátu.  
  
7. Přepsat <xref:System.IdentityModel.Tokens.SecurityKey.IsSupportedAlgorithm%2A> metody. Tato metoda slouží k označení, zda je konkrétní kryptografický algoritmus podporován implementací klíče zabezpečení.  
  
     [!code-csharp[c_CustomX509Token#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#1)]
     [!code-vb[c_CustomX509Token#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#1)]  
  
 Následující postup ukazuje, jak integrovat vlastní implementaci klíče zabezpečení X. 509, kterou jste vytvořili v předchozím postupu s rozhraním Security Framework pro WCF, aby nahradilo systémem poskytnutý token zabezpečení X. 509.  
  
#### <a name="to-replace-the-system-provided-x509-security-token-with-a-custom-x509-asymmetric-security-key-token"></a>Nahrazení tokenu zabezpečení X. 509 poskytovaného systémem pomocí vlastního tokenu asymetrického bezpečnostního klíče X. 509  
  
1. Vytvořte vlastní token zabezpečení X. 509, který vrátí vlastní klíč zabezpečení X. 509, a ne klíč zabezpečení poskytnutý systémem, jak je znázorněno v následujícím příkladu. Další informace o vlastních tokenech zabezpečení naleznete v [tématu How to: Vytvoření vlastního tokenu](how-to-create-a-custom-token.md)  
  
     [!code-csharp[c_CustomX509Token#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#2)]
     [!code-vb[c_CustomX509Token#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#2)]  
  
2. Vytvořte vlastního poskytovatele tokenu zabezpečení, který vrátí vlastní token zabezpečení X. 509, jak je znázorněno v příkladu. Další informace o vlastních poskytovatelích tokenů zabezpečení naleznete [v tématu How to: Vytvořte vlastního poskytovatele](how-to-create-a-custom-security-token-provider.md)tokenů zabezpečení.  
  
     [!code-csharp[c_CustomX509Token#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#3)]
     [!code-vb[c_CustomX509Token#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#3)]  
  
3. Pokud je třeba vlastní klíč zabezpečení použít na straně iniciátoru, vytvořte vlastní třídy klientského tokenu zabezpečení klienta a vlastní třídy přihlašovacích údajů klienta, jak je znázorněno v následujícím příkladu. Další informace o vlastních pověřeních klienta a správcích tokenů zabezpečení klienta [najdete v článku Návod: Vytváření vlastních přihlašovacích údajů](walkthrough-creating-custom-client-and-service-credentials.md)klienta a služby.  
  
     [!code-csharp[c_CustomX509Token#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#4)]
     [!code-vb[c_CustomX509Token#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#4)]  
  
     [!code-csharp[c_CustomX509Token#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#6)]
     [!code-vb[c_CustomX509Token#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#6)]  
  
4. Pokud je třeba vlastní klíč zabezpečení použít na straně příjemce, vytvořte vlastního správce tokenů zabezpečení služby a vlastní přihlašovací údaje služby, jak je znázorněno v následujícím příkladu. Další informace o vlastních pověřeních služby a vedoucích tokenů zabezpečení služby [najdete v článku Návod: Vytváření vlastních přihlašovacích údajů](walkthrough-creating-custom-client-and-service-credentials.md)klienta a služby.  
  
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
- [Návod: Vytváření vlastních přihlašovacích údajů klienta a služby](walkthrough-creating-custom-client-and-service-credentials.md)
- [Postupy: Vytvořit vlastní ověřovací data tokenu zabezpečení](how-to-create-a-custom-security-token-authenticator.md)
- [Postupy: Vytvoření vlastního zprostředkovatele tokenů zabezpečení](how-to-create-a-custom-security-token-provider.md)
- [Postupy: Vytvoření vlastního tokenu](how-to-create-a-custom-token.md)
