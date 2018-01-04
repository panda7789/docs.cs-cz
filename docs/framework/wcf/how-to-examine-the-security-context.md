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
# <a name="how-to-examine-the-security-context"></a><span data-ttu-id="dd54f-102">Postupy: Prozkoumání kontextu zabezpečení</span><span class="sxs-lookup"><span data-stu-id="dd54f-102">How to: Examine the Security Context</span></span>
<span data-ttu-id="dd54f-103">Při programování [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] služby, kontext zabezpečení služby vám umožní určit podrobnosti o pověření klienta a deklarace identity, které slouží k ověření u služby.</span><span class="sxs-lookup"><span data-stu-id="dd54f-103">When programming [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] services, the service security context enables you to determine details about the client credentials and claims used to authenticate with the service.</span></span> <span data-ttu-id="dd54f-104">To se provádí pomocí vlastnosti <xref:System.ServiceModel.ServiceSecurityContext> třídy.</span><span class="sxs-lookup"><span data-stu-id="dd54f-104">This is done by using the properties of the <xref:System.ServiceModel.ServiceSecurityContext> class.</span></span>  
  
 <span data-ttu-id="dd54f-105">Například můžete načíst identitu aktuálního klienta pomocí <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> nebo <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="dd54f-105">For example, you can retrieve the identity of the current client by using the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> or the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property.</span></span> <span data-ttu-id="dd54f-106">Chcete-li zjistit, zda klient je anonymní, použijte <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="dd54f-106">To determine whether the client is anonymous, use the <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> property.</span></span>  
  
 <span data-ttu-id="dd54f-107">Můžete také určit, jaké deklarace identity jsou určené jménem klienta pomocí iterace kolekce deklarací identity v <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="dd54f-107">You can also determine what claims are being made on behalf of the client by iterating through the collection of claims in the <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> property.</span></span>  
  
### <a name="to-get-the-current-security-context"></a><span data-ttu-id="dd54f-108">Chcete-li získat aktuální kontext zabezpečení</span><span class="sxs-lookup"><span data-stu-id="dd54f-108">To get the current security context</span></span>  
  
-   <span data-ttu-id="dd54f-109">Přístup k statickou vlastnost <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> získat aktuální kontext zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="dd54f-109">Access the static property <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> to get the current security context.</span></span> <span data-ttu-id="dd54f-110">Prozkoumejte v kterékoliv vlastnosti aktuální kontext z odkazu.</span><span class="sxs-lookup"><span data-stu-id="dd54f-110">Examine any of the properties of the current context from the reference.</span></span>  
  
### <a name="to-determine-the-identity-of-the-caller"></a><span data-ttu-id="dd54f-111">Chcete-li zjistit identitu volajícího</span><span class="sxs-lookup"><span data-stu-id="dd54f-111">To determine the identity of the caller</span></span>  
  
1.  <span data-ttu-id="dd54f-112">Tisk – hodnota <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> a <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="dd54f-112">Print the value of the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> and <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> properties.</span></span>  
  
### <a name="to-parse-the-claims-of-a-caller"></a><span data-ttu-id="dd54f-113">Analyzovat deklarace identity volající</span><span class="sxs-lookup"><span data-stu-id="dd54f-113">To parse the claims of a caller</span></span>  
  
1.  <span data-ttu-id="dd54f-114">Vrátí aktuální <xref:System.IdentityModel.Policy.AuthorizationContext> třídy.</span><span class="sxs-lookup"><span data-stu-id="dd54f-114">Return the current <xref:System.IdentityModel.Policy.AuthorizationContext> class.</span></span> <span data-ttu-id="dd54f-115">Použití <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> vlastnost, která má vrátit aktuální kontext zabezpečení služby a pak se vraťte `AuthorizationContext` pomocí <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="dd54f-115">Use the <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> property to return the current service security context, then return the `AuthorizationContext` using the <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> property.</span></span>  
  
2.  <span data-ttu-id="dd54f-116">Analyzovat kolekce <xref:System.IdentityModel.Claims.ClaimSet> objektů vrácený <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> vlastnost <xref:System.IdentityModel.Policy.AuthorizationContext> třídy.</span><span class="sxs-lookup"><span data-stu-id="dd54f-116">Parse the collection of <xref:System.IdentityModel.Claims.ClaimSet> objects returned by the <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> property of the <xref:System.IdentityModel.Policy.AuthorizationContext> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd54f-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="dd54f-117">Example</span></span>  
 <span data-ttu-id="dd54f-118">Následující příklad vypíše hodnoty <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> a <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> vlastnosti aktuální kontext zabezpečení a <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> vlastnost, prostředků hodnota deklarace identity a <xref:System.IdentityModel.Claims.Claim.Right%2A> vlastnost každých deklarace v aktuální zabezpečení kontext.</span><span class="sxs-lookup"><span data-stu-id="dd54f-118">The following example prints the values of the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> and <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> properties of the current security context and the <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> property, the resource value of the claim, and the <xref:System.IdentityModel.Claims.Claim.Right%2A> property of every claim in the current security context.</span></span>  
  
 [!code-csharp[c_PrincipalPermissionAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#4)]
 [!code-vb[c_PrincipalPermissionAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="dd54f-119">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="dd54f-119">Compiling the Code</span></span>  
 <span data-ttu-id="dd54f-120">Kód používá následujících oborů názvů:</span><span class="sxs-lookup"><span data-stu-id="dd54f-120">The code uses the following namespaces:</span></span>  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.IdentityModel.Policy>  
  
-   <xref:System.IdentityModel.Claims>  
  
## <a name="see-also"></a><span data-ttu-id="dd54f-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="dd54f-121">See Also</span></span>  
 [<span data-ttu-id="dd54f-122">Zabezpečení služeb</span><span class="sxs-lookup"><span data-stu-id="dd54f-122">Securing Services</span></span>](../../../docs/framework/wcf/securing-services.md)  
 [<span data-ttu-id="dd54f-123">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="dd54f-123">Service Identity and Authentication</span></span>](../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
