---
title: 'Postupy: Vytvoření podpůrného pověření'
ms.date: 03/30/2017
ms.assetid: d0952919-8bb4-4978-926c-9cc108f89806
ms.openlocfilehash: 3ae2b59abf59b0256741ef4e908305d9f4350b4a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59093706"
---
# <a name="how-to-create-a-supporting-credential"></a>Postupy: Vytvoření podpůrného pověření
Je možné mít vlastní bezpečnostní schéma, které vyžaduje více přihlašovacích údajů. Například služba vyžádat od klienta nejen uživatelské jméno a heslo, ale také pověření, která prokáže vaše oprávnění klienta je víc než 18. Je druhý přihlašovacích údajů *podpora přihlašovacích údajů*. Toto téma vysvětluje, jak implementovat tyto přihlašovací údaje v klientovi Windows Communication Foundation (WCF).  
  
> [!NOTE]
>  Specifikace pro podporu přihlašovacích údajů je součástí specifikace WS-SecurityPolicy. Další informace najdete v tématu [specifikací webových služeb zabezpečení](https://go.microsoft.com/fwlink/?LinkId=88537).  
  
## <a name="supporting-tokens"></a>Podpora tokenů  
 Stručně řečeno, při použití zabezpečení zpráv *primární pověření* vždy slouží k zabezpečení zpráv (například certifikát X.509 nebo lístek protokolu Kerberos).  
  
 Jak je definováno ve specifikaci vazby zabezpečení používá *tokeny* k výměně zpráv zabezpečení. A *token* je reprezentace bezpečnostním pověřením.  
  
 Vazby zabezpečení používá k vytvoření podpisu primární token identifikované v zásadách zabezpečení vazby. Tento podpis se označuje jako *podpis zprávy*.  
  
 Další tokeny lze k posílení deklarací poskytovaných token spojený s podpis zprávy.  
  
## <a name="endorsing-signing-and-encrypting"></a>Potvrdit, podepisování a šifrování  
 Výsledkem podpůrného pověření *podpůrný token* přenášených uvnitř zprávy. Specifikace WS-SecurityPolicy definuje čtyři způsoby, jak připojit podpůrný token na zprávu, jak je popsáno v následující tabulce.  
  
|Účel|Popis|  
|-------------|-----------------|  
|podepsané|Token podpory je zahrnutá v záhlaví zabezpečení a je podepsán společností podpis zprávy.|  
|Potvrdit|*Podporujícími token* podepíše podpis zprávy.|  
|Podepsaný a podporujícími|Podepsaná, podporujících tokeny přihlášení celý `ds:Signature` element vytvořenými podpis zprávy a jsou samotné podepsány tento podpis zprávy; to znamená, že oba tokeny (tokenu používaného k podpis zprávy a podepsaný token potvrzující) podepsat mezi sebou.|  
|Podepsaný a šifrování|Podepsaný a šifrované podpůrných tokenů jsou podepsané podpůrnými tokeny, které se také šifrují, pokud se objeví v `wsse:SecurityHeader`.|  
  
## <a name="programming-supporting-credentials"></a>Programování podporuje přihlašovací údaje  
 Pokud chcete vytvořit službu, která používá podpůrných tokenů, musíte vytvořit [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md). (Další informace najdete v tématu [jak: Vytvoření vlastní vazby pomocí elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).)  
  
 Prvním krokem při vytváření vlastní vazby je vytvořit element vazby zabezpečení, který může být jeden ze tří typů:  
  
-   <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
  
-   <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
  
-   <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 Dědí všechny třídy <xref:System.ServiceModel.Channels.SecurityBindingElement>, což zahrnuje čtyři relevantní vlastnosti:  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.EndpointSupportingTokenParameters%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.OperationSupportingTokenParameters%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalEndpointSupportingTokenParameters%2A>  
  
-   <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalOperationSupportingTokenParameters%2A>  
  
#### <a name="scopes"></a>Obory  
 Existují dva obory pro podporu přihlašovací údaje:  
  
-   *Koncový bod podporující tokeny* podporují všechny operace koncového bodu. To znamená přihlašovacích údajů, který představuje podpůrný token lze vždy, když jsou vyvolány žádné operace koncového bodu.  
  
-   *Podpora tokenů operace* podporují jenom operace určitého koncového bodu.  
  
 Je určeno názvy vlastností, podpora přihlašovacích údajů může být povinné nebo volitelné. To znamená pokud podpůrného pověření se používá, pokud je k dispozici, i když není nutné, ale pokud není k dispozici k selhání ověřování.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-create-a-custom-binding-that-includes-supporting-credentials"></a>K vytvoření vlastní vazby, která zahrnuje podporu přihlašovacích údajů  
  
1.  Vytvořte element vazby zabezpečení. Následující příklad vytvoří <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> s `UserNameForCertificate` režim ověřování. Použití <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> metody.  
  
2.  Přidání podpory parametru do kolekci typů odpovídající vlastnost vrátí (`Endorsing`, `Signed`, `SignedEncrypted`, nebo `SignedEndorsed`). Typy v <xref:System.ServiceModel.Security.Tokens> obor názvů patří běžně používané typy, například <xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters>.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad vytvoří instance <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> a přidá instanci <xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> třídy Endorsing vlastnosti vrácené do kolekce.  
  
### <a name="code"></a>Kód  
 [!code-csharp[c_SupportingCredential#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_supportingcredential/cs/source.cs#1)]  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Vytvoření vlastní vazby pomocí elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
