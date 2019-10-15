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
ms.openlocfilehash: 328d47a583a4f047fd54589a82d339de2cb1a16f
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320994"
---
# <a name="how-to-examine-the-security-context"></a>Postupy: Prozkoumání kontextu zabezpečení
Při programování Windows Communication Foundation (WCF) se v kontextu zabezpečení služby dá určit podrobnosti o přihlašovacích údajích klienta a deklaracích identity používaných k ověřování pomocí služby. To se provádí pomocí vlastností třídy <xref:System.ServiceModel.ServiceSecurityContext>.  
  
 Identitu aktuálního klienta můžete například načíst pomocí vlastnosti <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> nebo <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A>. Pokud chcete zjistit, jestli je klient anonymní, použijte vlastnost <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A>.  
  
 Pomocí iterace kolekce deklarací ve vlastnosti <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> můžete také určit, které deklarace identity se přidávají jménem klienta.  
  
### <a name="to-get-the-current-security-context"></a>Získání aktuálního kontextu zabezpečení  
  
- Přístup ke statické vlastnosti <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> pro získání aktuálního kontextu zabezpečení. Prověřte všechny vlastnosti aktuálního kontextu z reference.  
  
### <a name="to-determine-the-identity-of-the-caller"></a>Určení identity volajícího  
  
1. Vytiskněte hodnotu vlastností <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> a <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A>.  
  
### <a name="to-parse-the-claims-of-a-caller"></a>Postup analýzy deklarací volajícího  
  
1. Vrátí aktuální třídu <xref:System.IdentityModel.Policy.AuthorizationContext>. Pomocí vlastnosti <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> vraťte aktuální kontext zabezpečení služby a pak pomocí vlastnosti <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> vraťte `AuthorizationContext`.  
  
2. Analyzuje kolekci objektů <xref:System.IdentityModel.Claims.ClaimSet> vrácených vlastností <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> třídy <xref:System.IdentityModel.Policy.AuthorizationContext>.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytiskne hodnoty vlastností <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> a <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> aktuálního kontextu zabezpečení a vlastnost <xref:System.IdentityModel.Claims.Claim.ClaimType%2A>, hodnotu prostředku deklarace identity a vlastnost <xref:System.IdentityModel.Claims.Claim.Right%2A> každé deklarace identity v aktuálním kontextu zabezpečení.  
  
 [!code-csharp[c_PrincipalPermissionAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#4)]
 [!code-vb[c_PrincipalPermissionAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#4)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Kód používá následující obory názvů:  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.IdentityModel.Policy>  
  
- <xref:System.IdentityModel.Claims>  
  
## <a name="see-also"></a>Viz také:

- [Zabezpečení služeb](securing-services.md)
- [Identita a ověřování služby](./feature-details/service-identity-and-authentication.md)
