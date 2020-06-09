---
title: 'Postupy: Vytvoření podpůrných přihlašovacích údajů'
ms.date: 03/30/2017
ms.assetid: d0952919-8bb4-4978-926c-9cc108f89806
ms.openlocfilehash: b8e7ddcd6118c77e14e090a0b1fa8d65aeb8e3df
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597147"
---
# <a name="how-to-create-a-supporting-credential"></a>Postupy: Vytvoření podpůrných přihlašovacích údajů
Je možné mít vlastní schéma zabezpečení, které vyžaduje více než jedno přihlašovací údaje. Například služba může vyžadovat od klienta nejen uživatelské jméno a heslo, ale také přihlašovací údaje, které klienta prokáže za stáří 18. Druhá přihlašovací údaje jsou *podpůrná pověření*. Toto téma vysvětluje, jak implementovat takové přihlašovací údaje v klientovi Windows Communication Foundation (WCF).  
  
> [!NOTE]
> Specifikace pro podpůrná pověření je součástí specifikace WS-SecurityPolicy. Další informace najdete v článku [specifikace specifikace Web Services Security](https://docs.microsoft.com/previous-versions/dotnet/articles/ms951273(v=msdn.10)).  
  
## <a name="supporting-tokens"></a>Podpora tokenů  
 V krátké době se při použití zabezpečení zprávy *primární přihlašovací údaj* vždycky používá k zabezpečení zprávy (například certifikát X. 509 nebo lístek Kerberos).  
  
 Jak je definováno specifikací, vazba zabezpečení používá *tokeny* k zabezpečení výměny zpráv. *Token* je reprezentace bezpečnostního pověření.  
  
 Vazba zabezpečení používá primární token identifikovaný v zásadách vazby zabezpečení k vytvoření podpisu. Tento podpis je označován jako *podpis zprávy*.  
  
 Další tokeny lze zadat pro rozšíření deklarací poskytovaných tokenem, který je přidružen k podpisu zprávy.  
  
## <a name="endorsing-signing-and-encrypting"></a>Registrace, podepisování a šifrování  
 Výsledkem doprovodného pověření je *podpůrná token* , který se v rámci zprávy přenáší. Specifikace WS-SecurityPolicy definuje čtyři způsoby připojení podpůrného tokenu ke zprávě, jak je popsáno v následující tabulce.  
  
|Účel|Popis|  
|-------------|-----------------|  
|Podpisy|Token podpory je obsažen v záhlaví zabezpečení a je podepsán podpisem zprávy.|  
|Potvrzující|*Token* , který podepisuje, podepíše podpis zprávy.|  
|Podepsaná a schválená|Podepsané a registrační tokeny podepisují celý `ds:Signature` prvek vytvořený z podpisu zprávy a jsou podepsaný podpisem zprávy; to znamená, že obě tokeny (token použitý pro podpis zprávy a podepsaný registrační token) jsou navzájem podepsané.|  
|Podepsané a šifrované|Podepsané, šifrované podpůrné tokeny jsou podepsané podpůrnými tokeny, které jsou také zašifrovány, když se objeví v `wsse:SecurityHeader` .|  
  
## <a name="programming-supporting-credentials"></a>Programování podporující přihlašovací údaje  
 Chcete-li vytvořit službu, která používá podpůrné tokeny, musíte vytvořit [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) . (Další informace najdete v tématu [Postup: Vytvoření vlastní vazby pomocí SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).)  
  
 Prvním krokem při vytváření vlastní vazby je vytvoření elementu vazby zabezpečení, který může být jeden ze tří typů:  
  
- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
  
- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
  
- <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>  
  
 Všechny třídy dědí z <xref:System.ServiceModel.Channels.SecurityBindingElement> , který obsahuje čtyři relevantní vlastnosti:  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.EndpointSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OperationSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalEndpointSupportingTokenParameters%2A>  
  
- <xref:System.ServiceModel.Channels.SecurityBindingElement.OptionalOperationSupportingTokenParameters%2A>  
  
#### <a name="scopes"></a>Obory  
 Pro podpůrná pověření existují dva obory:  
  
- *Tokeny podporující koncové body* podporují všechny operace koncového bodu. To znamená, že přihlašovací údaje, které podpůrný token představuje, lze použít při každém vyvolání všech operací koncového bodu.  
  
- *Operace podporující tokeny* podporují pouze konkrétní operaci koncového bodu.  
  
 Jak je uvedeno v názvech vlastností, mohou být podpůrná pověření buď povinná, nebo volitelná. To znamená, že pokud je podpůrná pověření použita, je-li k dispozici, ale není nutné, ověřování nebude úspěšné, pokud není k dispozici.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-create-a-custom-binding-that-includes-supporting-credentials"></a>Vytvoření vlastní vazby, která zahrnuje podpůrná pověření  
  
1. Vytvořte prvek vazby zabezpečení. Následující příklad vytvoří <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> s `UserNameForCertificate` režimem ověřování. Použijte metodu <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A>.  
  
2. Přidejte podpůrný parametr do kolekce typů vrácených příslušnou vlastností ( `Endorsing` , `Signed` , `SignedEncrypted` nebo `SignedEndorsed` ). Typy v <xref:System.ServiceModel.Security.Tokens> oboru názvů obsahují běžně používané typy, jako je například <xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters> .  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad vytvoří instanci <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> třídy a přidá <xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> do kolekce instanci třídy, kterou vrátila vlastnost potvrdit.  
  
### <a name="code"></a>Kód  
 [!code-csharp[c_SupportingCredential#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_supportingcredential/cs/source.cs#1)]  
  
## <a name="see-also"></a>Viz také

- [Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md)
