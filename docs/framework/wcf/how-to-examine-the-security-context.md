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
ms.openlocfilehash: c6c36641463a45b79d437ae3910bbe7474d425cb
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59305101"
---
# <a name="how-to-examine-the-security-context"></a><span data-ttu-id="ebd1c-102">Postupy: Prozkoumání kontextu zabezpečení</span><span class="sxs-lookup"><span data-stu-id="ebd1c-102">How to: Examine the Security Context</span></span>
<span data-ttu-id="ebd1c-103">Při programování služby Windows Communication Foundation (WCF), kontext zabezpečení služby vám umožní určit podrobnosti o přihlašovací údaje pro klienta a deklarace identity použít k ověřování ve službě.</span><span class="sxs-lookup"><span data-stu-id="ebd1c-103">When programming Windows Communication Foundation (WCF) services, the service security context enables you to determine details about the client credentials and claims used to authenticate with the service.</span></span> <span data-ttu-id="ebd1c-104">To se provádí pomocí vlastnosti <xref:System.ServiceModel.ServiceSecurityContext> třídy.</span><span class="sxs-lookup"><span data-stu-id="ebd1c-104">This is done by using the properties of the <xref:System.ServiceModel.ServiceSecurityContext> class.</span></span>  
  
 <span data-ttu-id="ebd1c-105">Například můžete načíst identitu aktuálního klienta pomocí <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> nebo <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ebd1c-105">For example, you can retrieve the identity of the current client by using the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> or the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property.</span></span> <span data-ttu-id="ebd1c-106">Chcete-li zjistit, zda klient je anonymní, použijte <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ebd1c-106">To determine whether the client is anonymous, use the <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> property.</span></span>  
  
 <span data-ttu-id="ebd1c-107">Můžete také určit, jaké deklarace identity se provádějí jménem klienta sadu deklarací identity v rámci iterací <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ebd1c-107">You can also determine what claims are being made on behalf of the client by iterating through the collection of claims in the <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> property.</span></span>  
  
### <a name="to-get-the-current-security-context"></a><span data-ttu-id="ebd1c-108">Chcete-li získat aktuální kontext zabezpečení</span><span class="sxs-lookup"><span data-stu-id="ebd1c-108">To get the current security context</span></span>  
  
-   <span data-ttu-id="ebd1c-109">Přístup k statickou vlastnost <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> získat aktuální kontext zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="ebd1c-109">Access the static property <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> to get the current security context.</span></span> <span data-ttu-id="ebd1c-110">Prozkoumejte v kterékoliv z vlastností aktuálního kontextu z odkazu.</span><span class="sxs-lookup"><span data-stu-id="ebd1c-110">Examine any of the properties of the current context from the reference.</span></span>  
  
### <a name="to-determine-the-identity-of-the-caller"></a><span data-ttu-id="ebd1c-111">Chcete-li zjistit identitu volajícího</span><span class="sxs-lookup"><span data-stu-id="ebd1c-111">To determine the identity of the caller</span></span>  
  
1. <span data-ttu-id="ebd1c-112">Tisk hodnoty <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> a <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ebd1c-112">Print the value of the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> and <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> properties.</span></span>  
  
### <a name="to-parse-the-claims-of-a-caller"></a><span data-ttu-id="ebd1c-113">Analyzovat deklarace identity volajícího</span><span class="sxs-lookup"><span data-stu-id="ebd1c-113">To parse the claims of a caller</span></span>  
  
1. <span data-ttu-id="ebd1c-114">Vrátí aktuální <xref:System.IdentityModel.Policy.AuthorizationContext> třídy.</span><span class="sxs-lookup"><span data-stu-id="ebd1c-114">Return the current <xref:System.IdentityModel.Policy.AuthorizationContext> class.</span></span> <span data-ttu-id="ebd1c-115">Použití <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> vlastnost vrátit aktuální kontext zabezpečení služeb a pak se vraťte `AuthorizationContext` pomocí <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ebd1c-115">Use the <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> property to return the current service security context, then return the `AuthorizationContext` using the <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> property.</span></span>  
  
2. <span data-ttu-id="ebd1c-116">Analýza kolekce <xref:System.IdentityModel.Claims.ClaimSet> objektů vrácených podle <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> vlastnost <xref:System.IdentityModel.Policy.AuthorizationContext> třídy.</span><span class="sxs-lookup"><span data-stu-id="ebd1c-116">Parse the collection of <xref:System.IdentityModel.Claims.ClaimSet> objects returned by the <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> property of the <xref:System.IdentityModel.Policy.AuthorizationContext> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ebd1c-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="ebd1c-117">Example</span></span>  
 <span data-ttu-id="ebd1c-118">Následující příklad vypíše hodnoty <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> a <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> vlastnosti aktuální kontext zabezpečení a <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> vlastnosti, zdroj hodnota deklarace identity a <xref:System.IdentityModel.Claims.Claim.Right%2A> vlastnosti každé tvrzení v aktuální zabezpečení kontext.</span><span class="sxs-lookup"><span data-stu-id="ebd1c-118">The following example prints the values of the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> and <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> properties of the current security context and the <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> property, the resource value of the claim, and the <xref:System.IdentityModel.Claims.Claim.Right%2A> property of every claim in the current security context.</span></span>  
  
 [!code-csharp[c_PrincipalPermissionAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#4)]
 [!code-vb[c_PrincipalPermissionAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ebd1c-119">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="ebd1c-119">Compiling the Code</span></span>  
 <span data-ttu-id="ebd1c-120">Kód používá následující obory názvů:</span><span class="sxs-lookup"><span data-stu-id="ebd1c-120">The code uses the following namespaces:</span></span>  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.IdentityModel.Policy>  
  
-   <xref:System.IdentityModel.Claims>  
  
## <a name="see-also"></a><span data-ttu-id="ebd1c-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ebd1c-121">See also</span></span>

- [<span data-ttu-id="ebd1c-122">Zabezpečení služeb</span><span class="sxs-lookup"><span data-stu-id="ebd1c-122">Securing Services</span></span>](../../../docs/framework/wcf/securing-services.md)
- [<span data-ttu-id="ebd1c-123">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="ebd1c-123">Service Identity and Authentication</span></span>](../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
