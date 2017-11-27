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
ms.openlocfilehash: 72bc3dfcc91cb0fe5b393c9735c83b6331d5e0dd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-examine-the-security-context"></a><span data-ttu-id="7a008-102">Postupy: Prozkoumání kontextu zabezpečení</span><span class="sxs-lookup"><span data-stu-id="7a008-102">How to: Examine the Security Context</span></span>
<span data-ttu-id="7a008-103">Při programování [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] služby, kontext zabezpečení služby vám umožní určit podrobnosti o pověření klienta a deklarace identity, které slouží k ověření u služby.</span><span class="sxs-lookup"><span data-stu-id="7a008-103">When programming [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] services, the service security context enables you to determine details about the client credentials and claims used to authenticate with the service.</span></span> <span data-ttu-id="7a008-104">To se provádí pomocí vlastnosti <xref:System.ServiceModel.ServiceSecurityContext> třídy.</span><span class="sxs-lookup"><span data-stu-id="7a008-104">This is done by using the properties of the <xref:System.ServiceModel.ServiceSecurityContext> class.</span></span>  
  
 <span data-ttu-id="7a008-105">Například můžete načíst identitu aktuálního klienta pomocí <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> nebo <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7a008-105">For example, you can retrieve the identity of the current client by using the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> or the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property.</span></span> <span data-ttu-id="7a008-106">Chcete-li zjistit, zda klient je anonymní, použijte <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7a008-106">To determine whether the client is anonymous, use the <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> property.</span></span>  
  
 <span data-ttu-id="7a008-107">Můžete také určit, jaké deklarace identity jsou určené jménem klienta pomocí iterace kolekce deklarací identity v <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7a008-107">You can also determine what claims are being made on behalf of the client by iterating through the collection of claims in the <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> property.</span></span>  
  
### <a name="to-get-the-current-security-context"></a><span data-ttu-id="7a008-108">Chcete-li získat aktuální kontext zabezpečení</span><span class="sxs-lookup"><span data-stu-id="7a008-108">To get the current security context</span></span>  
  
-   <span data-ttu-id="7a008-109">Přístup k statickou vlastnost <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> získat aktuální kontext zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7a008-109">Access the static property <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> to get the current security context.</span></span> <span data-ttu-id="7a008-110">Prozkoumejte v kterékoliv vlastnosti aktuální kontext z odkazu.</span><span class="sxs-lookup"><span data-stu-id="7a008-110">Examine any of the properties of the current context from the reference.</span></span>  
  
### <a name="to-determine-the-identity-of-the-caller"></a><span data-ttu-id="7a008-111">Chcete-li zjistit identitu volajícího</span><span class="sxs-lookup"><span data-stu-id="7a008-111">To determine the identity of the caller</span></span>  
  
1.  <span data-ttu-id="7a008-112">Tisk – hodnota <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> a <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="7a008-112">Print the value of the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> and <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> properties.</span></span>  
  
### <a name="to-parse-the-claims-of-a-caller"></a><span data-ttu-id="7a008-113">Analyzovat deklarace identity volající</span><span class="sxs-lookup"><span data-stu-id="7a008-113">To parse the claims of a caller</span></span>  
  
1.  <span data-ttu-id="7a008-114">Vrátí aktuální <xref:System.IdentityModel.Policy.AuthorizationContext> třídy.</span><span class="sxs-lookup"><span data-stu-id="7a008-114">Return the current <xref:System.IdentityModel.Policy.AuthorizationContext> class.</span></span> <span data-ttu-id="7a008-115">Použití <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> vlastnost, která má vrátit aktuální kontext zabezpečení služby a pak se vraťte `AuthorizationContext` pomocí <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7a008-115">Use the <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> property to return the current service security context, then return the `AuthorizationContext` using the <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> property.</span></span>  
  
2.  <span data-ttu-id="7a008-116">Analyzovat kolekce <xref:System.IdentityModel.Claims.ClaimSet> objektů vrácený <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> vlastnost <xref:System.IdentityModel.Policy.AuthorizationContext> třídy.</span><span class="sxs-lookup"><span data-stu-id="7a008-116">Parse the collection of <xref:System.IdentityModel.Claims.ClaimSet> objects returned by the <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> property of the <xref:System.IdentityModel.Policy.AuthorizationContext> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a008-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="7a008-117">Example</span></span>  
 <span data-ttu-id="7a008-118">Následující příklad vypíše hodnoty <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> a <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> vlastnosti aktuální kontext zabezpečení a <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> vlastnost, prostředků hodnota deklarace identity a <xref:System.IdentityModel.Claims.Claim.Right%2A> vlastnost každých deklarace v aktuální zabezpečení kontext.</span><span class="sxs-lookup"><span data-stu-id="7a008-118">The following example prints the values of the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> and <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> properties of the current security context and the <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> property, the resource value of the claim, and the <xref:System.IdentityModel.Claims.Claim.Right%2A> property of every claim in the current security context.</span></span>  
  
 [!code-csharp[c_PrincipalPermissionAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#4)]
 [!code-vb[c_PrincipalPermissionAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7a008-119">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="7a008-119">Compiling the Code</span></span>  
 <span data-ttu-id="7a008-120">Kód používá následujících oborů názvů:</span><span class="sxs-lookup"><span data-stu-id="7a008-120">The code uses the following namespaces:</span></span>  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.IdentityModel.Policy>  
  
-   <xref:System.IdentityModel.Claims>  
  
## <a name="see-also"></a><span data-ttu-id="7a008-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="7a008-121">See Also</span></span>  
 [<span data-ttu-id="7a008-122">Zabezpečení služeb</span><span class="sxs-lookup"><span data-stu-id="7a008-122">Securing Services</span></span>](../../../docs/framework/wcf/securing-services.md)  
 [<span data-ttu-id="7a008-123">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="7a008-123">Service Identity and Authentication</span></span>](../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
