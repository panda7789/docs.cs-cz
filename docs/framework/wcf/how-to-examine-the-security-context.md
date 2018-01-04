---
title: "Postupy: Prozkoumání kontextu zabezpečení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ServiceSecurityContext class
- WCF, security
- Claimset class
ms.assetid: 389b5a57-4175-4bc0-ada0-fc750d51149f
caps.latest.revision: "13"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 4d6852a3162b3a8666c711d455e72517a91c4477
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-examine-the-security-context"></a>Postupy: Prozkoumání kontextu zabezpečení
Při programování [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] služby, kontext zabezpečení služby vám umožní určit podrobnosti o pověření klienta a deklarace identity, které slouží k ověření u služby. To se provádí pomocí vlastnosti <xref:System.ServiceModel.ServiceSecurityContext> třídy.  
  
 Například můžete načíst identitu aktuálního klienta pomocí <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> nebo <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> vlastnost. Chcete-li zjistit, zda klient je anonymní, použijte <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> vlastnost.  
  
 Můžete také určit, jaké deklarace identity jsou určené jménem klienta pomocí iterace kolekce deklarací identity v <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> vlastnost.  
  
### <a name="to-get-the-current-security-context"></a>Chcete-li získat aktuální kontext zabezpečení  
  
-   Přístup k statickou vlastnost <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> získat aktuální kontext zabezpečení. Prozkoumejte v kterékoliv vlastnosti aktuální kontext z odkazu.  
  
### <a name="to-determine-the-identity-of-the-caller"></a>Chcete-li zjistit identitu volajícího  
  
1.  Tisk – hodnota <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> a <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> vlastnosti.  
  
### <a name="to-parse-the-claims-of-a-caller"></a>Analyzovat deklarace identity volající  
  
1.  Vrátí aktuální <xref:System.IdentityModel.Policy.AuthorizationContext> třídy. Použití <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> vlastnost, která má vrátit aktuální kontext zabezpečení služby a pak se vraťte `AuthorizationContext` pomocí <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> vlastnost.  
  
2.  Analyzovat kolekce <xref:System.IdentityModel.Claims.ClaimSet> objektů vrácený <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> vlastnost <xref:System.IdentityModel.Policy.AuthorizationContext> třídy.  
  
## <a name="example"></a>Příklad  
 Následující příklad vypíše hodnoty <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> a <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> vlastnosti aktuální kontext zabezpečení a <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> vlastnost, prostředků hodnota deklarace identity a <xref:System.IdentityModel.Claims.Claim.Right%2A> vlastnost každých deklarace v aktuální zabezpečení kontext.  
  
 [!code-csharp[c_PrincipalPermissionAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#4)]
 [!code-vb[c_PrincipalPermissionAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#4)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Kód používá následujících oborů názvů:  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.IdentityModel.Policy>  
  
-   <xref:System.IdentityModel.Claims>  
  
## <a name="see-also"></a>Viz také  
 [Zabezpečení služeb](../../../docs/framework/wcf/securing-services.md)  
 [Identita a ověřování služby](../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
