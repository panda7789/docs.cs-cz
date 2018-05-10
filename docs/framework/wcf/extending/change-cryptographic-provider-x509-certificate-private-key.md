---
title: 'Postupy: Změna zprostředkovatele kryptografických služeb pro certifikát X.509&#39;s privátním klíčem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptographic provider [WCF], changing
- cryptographic provider [WCF]
ms.assetid: b4254406-272e-4774-bd61-27e39bbb6c12
ms.openlocfilehash: 633e87bca302adc0963e1bf52d2470c9dbae81a5
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-change-the-cryptographic-provider-for-an-x509-certificate39s-private-key"></a>Postupy: Změna zprostředkovatele kryptografických služeb pro certifikát X.509&#39;s privátním klíčem
Toto téma ukazuje, jak změnit zprostředkovatele kryptografických služeb používá k zajištění privátní klíč certifikátu X.509 a jak integrovat zprostředkovatele do zabezpečení systému Windows Communication Foundation (WCF). Další informace o používání certifikátů najdete v tématu [práce s certifikáty](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
 Zabezpečení rozhraní WCF poskytuje způsob, jak zavést nové typy tokenů zabezpečení, jak je popsáno v [postupy: vytvoření vlastního tokenu](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md). Je také možné použít vlastní token k nahrazení stávající poskytované systémem typy tokenů.  
  
 V tomto tématu se token zabezpečení poskytované systémem X.509 nahrazuje token vlastní X.509, který poskytuje jinou implementaci pro privátní klíč certifikátu. To je užitečné v situacích, kdy skutečná privátní klíč poskytuje různé zprostředkovatele kryptografických služeb než výchozí Windows zprostředkovatele kryptografických služeb. Příkladem alternativního zprostředkovatele kryptografických služeb je modul hardwarového zabezpečení, který provede všechny privátní klíče související kryptografických operací a privátní klíče nejsou uložené v paměti, a zlepšit zabezpečení systému.  
  
 V následujícím příkladu je pouze pro demonstrační účely. Nenahrazuje výchozí zprostředkovatel kryptografických služeb systému Windows, ale ukazuje, kde může integrovat takové zprostředkovatele.  
  
## <a name="procedures"></a>Procedury  
 Každý token zabezpečení, který má přiřazený bezpečnostní klíč nebo klíče musí implementovat <xref:System.IdentityModel.Tokens.SecurityToken.SecurityKeys%2A> vlastnosti, která vrátí kolekci klíčů z instance tokenu zabezpečení. Pokud je token token zabezpečení X.509, kolekce obsahuje jednu instanci <xref:System.IdentityModel.Tokens.X509AsymmetricSecurityKey> třídu, která představuje veřejné a soukromé klíče přidruženého k certifikátu. Chcete-li nahradit výchozí zprostředkovatele kryptografických služeb použitý k poskytnutí klíčů certifikátu, vytvořte novou implementací této třídy.  
  
#### <a name="to-create-a-custom-x509-asymmetric-key"></a>Chcete-li vytvořit vlastní asymetrický klíč X.509  
  
1.  Definovat nové třídy odvozené od <xref:System.IdentityModel.Tokens.X509AsymmetricSecurityKey> třídy.  
  
2.  Přepsání <xref:System.IdentityModel.Tokens.SecurityKey.KeySize%2A> vlastnost určenou jen pro čtení. Tato vlastnost vrátí skutečná velikost klíče certifikátu pár veřejného a privátního klíče.  
  
3.  Přepsání <xref:System.IdentityModel.Tokens.SecurityKey.DecryptKey%2A> metoda. Tato metoda je volána rámcem zabezpečení WCF k dešifrování symetrického klíče s privátním klíčem certifikátu. (Klíč byl dříve zašifrován pomocí veřejného klíče certifikátu.)  
  
4.  Přepsání <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey.GetAsymmetricAlgorithm%2A> metoda. Tato metoda je volána rámcem zabezpečení WCF získat instanci <xref:System.Security.Cryptography.AsymmetricAlgorithm> třídu, která představuje zprostředkovatele kryptografických služeb pro buď privátního nebo veřejného klíče certifikátu, v závislosti na parametrech předaný metodě.  
  
5.  Volitelné. Přepsání <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey.GetHashAlgorithmForSignature%2A> metoda. Potlačí tuto metodu, pokud na různé implementace <xref:System.Security.Cryptography.HashAlgorithm> je vyžadován.  
  
6.  Přepsání <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey.GetSignatureFormatter%2A> metoda. Tato metoda vrací instanci třídy <xref:System.Security.Cryptography.AsymmetricSignatureFormatter> třídy, který je přidružený privátní klíč certifikátu.  
  
7.  Přepsání <xref:System.IdentityModel.Tokens.SecurityKey.IsSupportedAlgorithm%2A> metoda. Tato metoda se používá k označení, zda je podporováno konkrétní kryptografický algoritmus klíče implementace zabezpečení.  
  
     [!code-csharp[c_CustomX509Token#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#1)]
     [!code-vb[c_CustomX509Token#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#1)]  
  
 Následující postup ukazuje, jak integrovat vlastní X.509 zabezpečení asymetrického klíče implementace vytvořen v předchozím postupu s framework zabezpečení WCF, chcete-li nahradit X.509 zabezpečení poskytované systémem tokenu.  
  
#### <a name="to-replace-the-system-provided-x509-security-token-with-a-custom-x509-asymmetric-security-key-token"></a>Nahradit token zabezpečení poskytované systémem X.509 vlastní X.509 asymetrického klíče token zabezpečení  
  
1.  Vytvoření vlastního tokenu zabezpečení X.509, který vrací vlastní klíč asymetrické zabezpečení X.509 místo klíč zabezpečení poskytované systémem, jak je znázorněno v následujícím příkladu. Další informace o tokeny vlastní zabezpečení najdete v tématu [postupy: vytvoření vlastního tokenu](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
     [!code-csharp[c_CustomX509Token#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#2)]
     [!code-vb[c_CustomX509Token#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#2)]  
  
2.  Vytvořte vlastní zabezpečovací zprostředkovatele tokenů, který vrátí token zabezpečení vlastní X.509, jak je znázorněno v příkladu. Další informace o poskytovatele tokenů vlastní zabezpečení najdete v tématu [postupy: vytvoření vlastního poskytovatele tokenu zabezpečení](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md).  
  
     [!code-csharp[c_CustomX509Token#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#3)]
     [!code-vb[c_CustomX509Token#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#3)]  
  
3.  Pokud klíč vlastní zabezpečení se musí použít na straně iniciátor, vytvořte vlastní klienta Správce tokenů zabezpečení a vlastních klientských třídy přihlašovací údaje, jak je znázorněno v následujícím příkladu. Další informace o pověření vlastního klienta a správci tokenu zabezpečení klienta najdete v tématu [návod: vytvoření vlastního klienta a pověření služby](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
     [!code-csharp[c_CustomX509Token#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#4)]
     [!code-vb[c_CustomX509Token#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#4)]  
  
     [!code-csharp[c_CustomX509Token#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#6)]
     [!code-vb[c_CustomX509Token#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#6)]  
  
4.  Pokud klíč vlastní zabezpečení se musí použít na straně příjemce, vytvořte Správce tokenů zabezpečení vlastní služby a přihlašovací údaje vlastní služby, jak je znázorněno v následujícím příkladu. Další informace o pověření vlastní služby a služby jako správci tokenu zabezpečení najdete v tématu [návod: vytvoření vlastního klienta a pověření služby](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md).  
  
     [!code-csharp[c_CustomX509Token#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#5)]
     [!code-vb[c_CustomX509Token#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#5)]  
  
     [!code-csharp[c_CustomX509Token#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_customx509token/cs/source.cs#7)]
     [!code-vb[c_CustomX509Token#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_customx509token/vb/source.vb#7)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.IdentityModel.Tokens.X509AsymmetricSecurityKey>  
 <xref:System.IdentityModel.Tokens.AsymmetricSecurityKey>  
 <xref:System.IdentityModel.Tokens.SecurityKey>  
 <xref:System.Security.Cryptography.AsymmetricAlgorithm>  
 <xref:System.Security.Cryptography.HashAlgorithm>  
 <xref:System.Security.Cryptography.AsymmetricSignatureFormatter>  
 [Návod: Vytvoření vlastních přihlašovacích údajů klienta a služby](../../../../docs/framework/wcf/extending/walkthrough-creating-custom-client-and-service-credentials.md)  
 [Postupy: Vytvoření vlastních ověřovacích dat tokenu zabezpečení](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-authenticator.md)  
 [Postupy: Vytvoření vlastního zprostředkovatele tokenů zabezpečení](../../../../docs/framework/wcf/extending/how-to-create-a-custom-security-token-provider.md)  
 [Postupy: Vytvoření vlastního tokenu](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)  
 [Architektura zabezpečení](http://msdn.microsoft.com/library/16593476-d36a-408d-808c-ae6fd483e28f)
