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
ms.openlocfilehash: 64e566fb8d0cfadc2a46d0a335ddb2799739f9f9
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50187777"
---
# <a name="how-to-examine-the-security-context"></a><span data-ttu-id="89475-102">Postupy: Prozkoumání kontextu zabezpečení</span><span class="sxs-lookup"><span data-stu-id="89475-102">How to: Examine the Security Context</span></span>
<span data-ttu-id="89475-103">Při programování služby Windows Communication Foundation (WCF), kontext zabezpečení služby vám umožní určit podrobnosti o přihlašovací údaje pro klienta a deklarace identity použít k ověřování ve službě.</span><span class="sxs-lookup"><span data-stu-id="89475-103">When programming Windows Communication Foundation (WCF) services, the service security context enables you to determine details about the client credentials and claims used to authenticate with the service.</span></span> <span data-ttu-id="89475-104">To se provádí pomocí vlastnosti <xref:System.ServiceModel.ServiceSecurityContext> třídy.</span><span class="sxs-lookup"><span data-stu-id="89475-104">This is done by using the properties of the <xref:System.ServiceModel.ServiceSecurityContext> class.</span></span>  
  
 <span data-ttu-id="89475-105">Například můžete načíst identitu aktuálního klienta pomocí <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> nebo <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="89475-105">For example, you can retrieve the identity of the current client by using the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> or the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property.</span></span> <span data-ttu-id="89475-106">Chcete-li zjistit, zda klient je anonymní, použijte <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="89475-106">To determine whether the client is anonymous, use the <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> property.</span></span>  
  
 <span data-ttu-id="89475-107">Můžete také určit, jaké deklarace identity se provádějí jménem klienta sadu deklarací identity v rámci iterací <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="89475-107">You can also determine what claims are being made on behalf of the client by iterating through the collection of claims in the <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> property.</span></span>  
  
### <a name="to-get-the-current-security-context"></a><span data-ttu-id="89475-108">Chcete-li získat aktuální kontext zabezpečení</span><span class="sxs-lookup"><span data-stu-id="89475-108">To get the current security context</span></span>  
  
-   <span data-ttu-id="89475-109">Přístup k statickou vlastnost <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> získat aktuální kontext zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="89475-109">Access the static property <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> to get the current security context.</span></span> <span data-ttu-id="89475-110">Prozkoumejte v kterékoliv z vlastností aktuálního kontextu z odkazu.</span><span class="sxs-lookup"><span data-stu-id="89475-110">Examine any of the properties of the current context from the reference.</span></span>  
  
### <a name="to-determine-the-identity-of-the-caller"></a><span data-ttu-id="89475-111">Chcete-li zjistit identitu volajícího</span><span class="sxs-lookup"><span data-stu-id="89475-111">To determine the identity of the caller</span></span>  
  
1.  <span data-ttu-id="89475-112">Tisk hodnoty <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> a <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="89475-112">Print the value of the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> and <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> properties.</span></span>  
  
### <a name="to-parse-the-claims-of-a-caller"></a><span data-ttu-id="89475-113">Analyzovat deklarace identity volajícího</span><span class="sxs-lookup"><span data-stu-id="89475-113">To parse the claims of a caller</span></span>  
  
1.  <span data-ttu-id="89475-114">Vrátí aktuální <xref:System.IdentityModel.Policy.AuthorizationContext> třídy.</span><span class="sxs-lookup"><span data-stu-id="89475-114">Return the current <xref:System.IdentityModel.Policy.AuthorizationContext> class.</span></span> <span data-ttu-id="89475-115">Použití <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> vlastnost vrátit aktuální kontext zabezpečení služeb a pak se vraťte `AuthorizationContext` pomocí <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="89475-115">Use the <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> property to return the current service security context, then return the `AuthorizationContext` using the <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> property.</span></span>  
  
2.  <span data-ttu-id="89475-116">Analýza kolekce <xref:System.IdentityModel.Claims.ClaimSet> objektů vrácených podle <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> vlastnost <xref:System.IdentityModel.Policy.AuthorizationContext> třídy.</span><span class="sxs-lookup"><span data-stu-id="89475-116">Parse the collection of <xref:System.IdentityModel.Claims.ClaimSet> objects returned by the <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> property of the <xref:System.IdentityModel.Policy.AuthorizationContext> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="89475-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="89475-117">Example</span></span>  
 <span data-ttu-id="89475-118">Následující příklad vypíše hodnoty <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> a <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> vlastnosti aktuální kontext zabezpečení a <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> vlastnosti, zdroj hodnota deklarace identity a <xref:System.IdentityModel.Claims.Claim.Right%2A> vlastnosti každé tvrzení v aktuální zabezpečení kontext.</span><span class="sxs-lookup"><span data-stu-id="89475-118">The following example prints the values of the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> and <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> properties of the current security context and the <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> property, the resource value of the claim, and the <xref:System.IdentityModel.Claims.Claim.Right%2A> property of every claim in the current security context.</span></span>  
  
 [!code-csharp[c_PrincipalPermissionAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#4)]
 [!code-vb[c_PrincipalPermissionAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="89475-119">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="89475-119">Compiling the Code</span></span>  
 <span data-ttu-id="89475-120">Kód používá následující obory názvů:</span><span class="sxs-lookup"><span data-stu-id="89475-120">The code uses the following namespaces:</span></span>  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.IdentityModel.Policy>  
  
-   <xref:System.IdentityModel.Claims>  
  
## <a name="see-also"></a><span data-ttu-id="89475-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="89475-121">See Also</span></span>  
 [<span data-ttu-id="89475-122">Zabezpečení služeb</span><span class="sxs-lookup"><span data-stu-id="89475-122">Securing Services</span></span>](../../../docs/framework/wcf/securing-services.md)  
 [<span data-ttu-id="89475-123">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="89475-123">Service Identity and Authentication</span></span>](../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
