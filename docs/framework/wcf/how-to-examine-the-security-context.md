---
title: 'Postupy: Prozkoumání kontextu zabezpečení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ServiceSecurityContext class
- WCF, security
- Claimset class
ms.assetid: 389b5a57-4175-4bc0-ada0-fc750d51149f
ms.openlocfilehash: e67ac9c452337b6f490d99ea4430ec2a02b952a1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625805"
---
# <a name="how-to-examine-the-security-context"></a>Postupy: Prozkoumání kontextu zabezpečení
Při programování služby Windows Communication Foundation (WCF), kontext zabezpečení služby vám umožní určit podrobnosti o přihlašovací údaje pro klienta a deklarace identity použít k ověřování ve službě. To se provádí pomocí vlastnosti <xref:System.ServiceModel.ServiceSecurityContext> třídy.  
  
 Například můžete načíst identitu aktuálního klienta pomocí <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> nebo <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> vlastnost. Chcete-li zjistit, zda klient je anonymní, použijte <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> vlastnost.  
  
 Můžete také určit, jaké deklarace identity se provádějí jménem klienta sadu deklarací identity v rámci iterací <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> vlastnost.  
  
### <a name="to-get-the-current-security-context"></a>Chcete-li získat aktuální kontext zabezpečení  
  
- Přístup k statickou vlastnost <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> získat aktuální kontext zabezpečení. Prozkoumejte v kterékoliv z vlastností aktuálního kontextu z odkazu.  
  
### <a name="to-determine-the-identity-of-the-caller"></a>Chcete-li zjistit identitu volajícího  
  
1. Tisk hodnoty <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> a <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> vlastnosti.  
  
### <a name="to-parse-the-claims-of-a-caller"></a>Analyzovat deklarace identity volajícího  
  
1. Vrátí aktuální <xref:System.IdentityModel.Policy.AuthorizationContext> třídy. Použití <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> vlastnost vrátit aktuální kontext zabezpečení služeb a pak se vraťte `AuthorizationContext` pomocí <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> vlastnost.  
  
2. Analýza kolekce <xref:System.IdentityModel.Claims.ClaimSet> objektů vrácených podle <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> vlastnost <xref:System.IdentityModel.Policy.AuthorizationContext> třídy.  
  
## <a name="example"></a>Příklad  
 Následující příklad vypíše hodnoty <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> a <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> vlastnosti aktuální kontext zabezpečení a <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> vlastnosti, zdroj hodnota deklarace identity a <xref:System.IdentityModel.Claims.Claim.Right%2A> vlastnosti každé tvrzení v aktuální zabezpečení kontext.  
  
 [!code-csharp[c_PrincipalPermissionAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#4)]
 [!code-vb[c_PrincipalPermissionAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#4)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Kód používá následující obory názvů:  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.IdentityModel.Policy>  
  
- <xref:System.IdentityModel.Claims>  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení služeb](../../../docs/framework/wcf/securing-services.md)
- [Identita a ověřování služby](../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
