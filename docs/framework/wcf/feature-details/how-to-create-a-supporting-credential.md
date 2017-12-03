---
title: "Postupy: vytvoření přihlašovacích údajů podpora"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d0952919-8bb4-4978-926c-9cc108f89806
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a460a3fdd48813801b18af5a896252134687816d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-create-a-supporting-credential"></a>Postupy: vytvoření přihlašovacích údajů podpora
Je možné, že schéma vlastní zabezpečení, která vyžaduje více než jedno pověření. Například služby vyžádat z klienta nejen uživatelské jméno a heslo, ale také přihlašovacích údajů, který prokáže, klient je víc než 18. Druhý přihlašovací údaje *podpora přihlašovacích údajů*. Toto téma vysvětluje, jak implementovat tyto přihlašovací údaje v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] klienta.  
  
> [!NOTE]
>  Specifikace pro podporu přihlašovací údaje je součástí specifikace WS-SecurityPolicy. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Webových služeb zabezpečení specifikace](http://go.microsoft.com/fwlink/?LinkId=88537).  
  
## <a name="supporting-tokens"></a>Podpora tokenů  
 Stručně řečeno, při použití zabezpečení zpráv *primární pověření* vždy slouží k zabezpečení zpráv (například certifikát X.509 nebo lístek protokolu Kerberos).  
  
 Podle definice specifikace, používá vazby zabezpečení *tokeny* zabezpečit zprávy exchange. A *tokenu* je reprezentace pověření zabezpečení.  
  
 Vazby zabezpečení používá primární token identifikovat v zásadách zabezpečení vazby k vytvoření podpisu. Tento podpis odkazuje jako *podpis zprávy*.  
  
 K posílení deklarace identity poskytované tokenu přidružený podpis zprávy lze zadat další tokeny.  
  
## <a name="endorsing-signing-and-encrypting"></a>Potvrzování, podepisování a šifrování  
 Výsledkem podpůrné přihlašovacích údajů *token podpory* přenášených v rámci zprávy. Specifikace WS-SecurityPolicy definuje čtyři způsoby, jak připojit token podpory na zprávu, jak je popsáno v následující tabulce.  
  
|Účel|Popis|  
|-------------|-----------------|  
|Podepsané|Token podpory je zahrnutý v záhlaví zabezpečení a je podepsána podpis zprávy.|  
|Potvrdit správnost|*Či identifikaci token* podepisuje podpis zprávy.|  
|Podepsaná a či identifikaci|Podepsaná, potvrzování tokeny přihlašovací celý `ds:Signature` element vytvořeného z podpis zprávy a jsou sami podepsána tuto podpis zprávy; to znamená, oba tokeny (tokenu používaného k podpis zprávy a podepsaný token či identifikaci) přihlásit navzájem.|  
|Podepsaná a šifrování|Podepsaný držitelem, šifrované podpůrné tokeny jsou podepsané podpora tokenů, které jsou také zašifrované, když se zobrazí v `wsse:SecurityHeader`.|  
  
## <a name="programming-supporting-credentials"></a>Programování podpora přihlašovací údaje  
 Chcete-li vytvořit službu, která používá podpůrné tokeny, musíte vytvořit [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md). ([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Postupy: vytvoření vlastní vazby pomocí elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).)  
  
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
  
-   *Koncový bod podpora tokenů* podporují všechny operace koncový bod. To znamená pověření, které představuje token podpory lze vždy, když jsou vyvolány žádné operace koncového bodu.  
  
-   *Operace podpora tokenů* podporují pouze o operaci konkrétní koncový bod.  
  
 Jak názvy vlastností, podpora pověření může být požadované nebo volitelné. To znamená pokud podpůrné přihlašovacích údajů se používá, pokud je k dispozici, i když není nutné, ale nebudou ověřování, pokud není přítomen.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="to-create-a-custom-binding-that-includes-supporting-credentials"></a>Chcete-li vytvořit vlastní vazby, která zahrnuje podporu přihlašovací údaje  
  
1.  Vytvořte element vazby a zabezpečení. Následující příklad vytvoří <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> s `UserNameForCertificate` režim ověřování. Použití <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> metoda.  
  
2.  Přidat parametr podpůrné ke kolekci typů vrácené odpovídající vlastnost (`Endorsing`, `Signed`, `SignedEncrypted`, nebo `SignedEndorsed`). Typy v <xref:System.ServiceModel.Security.Tokens> obor názvů zahrnují běžně používané typy, jako <xref:System.ServiceModel.Security.Tokens.X509SecurityTokenParameters>.  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Následující příklad vytvoří instanci <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> a přidá instanci <xref:System.ServiceModel.Security.Tokens.KerberosSecurityTokenParameters> třídy ke kolekci vlastnost Endorsing vrátila.  
  
### <a name="code"></a>Kód  
 [!code-csharp[c_SupportingCredential#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_supportingcredential/cs/source.cs#1)]  
  
## <a name="see-also"></a>Viz také  
 [Postupy: vytvoření vlastní vazby pomocí elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
