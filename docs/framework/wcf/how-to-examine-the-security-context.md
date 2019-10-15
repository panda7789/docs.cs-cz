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
# <a name="how-to-examine-the-security-context"></a><span data-ttu-id="e7fca-102">Postupy: Prozkoumání kontextu zabezpečení</span><span class="sxs-lookup"><span data-stu-id="e7fca-102">How to: Examine the Security Context</span></span>
<span data-ttu-id="e7fca-103">Při programování Windows Communication Foundation (WCF) se v kontextu zabezpečení služby dá určit podrobnosti o přihlašovacích údajích klienta a deklaracích identity používaných k ověřování pomocí služby.</span><span class="sxs-lookup"><span data-stu-id="e7fca-103">When programming Windows Communication Foundation (WCF) services, the service security context enables you to determine details about the client credentials and claims used to authenticate with the service.</span></span> <span data-ttu-id="e7fca-104">To se provádí pomocí vlastností třídy <xref:System.ServiceModel.ServiceSecurityContext>.</span><span class="sxs-lookup"><span data-stu-id="e7fca-104">This is done by using the properties of the <xref:System.ServiceModel.ServiceSecurityContext> class.</span></span>  
  
 <span data-ttu-id="e7fca-105">Identitu aktuálního klienta můžete například načíst pomocí vlastnosti <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> nebo <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A>.</span><span class="sxs-lookup"><span data-stu-id="e7fca-105">For example, you can retrieve the identity of the current client by using the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> or the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property.</span></span> <span data-ttu-id="e7fca-106">Pokud chcete zjistit, jestli je klient anonymní, použijte vlastnost <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A>.</span><span class="sxs-lookup"><span data-stu-id="e7fca-106">To determine whether the client is anonymous, use the <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A> property.</span></span>  
  
 <span data-ttu-id="e7fca-107">Pomocí iterace kolekce deklarací ve vlastnosti <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> můžete také určit, které deklarace identity se přidávají jménem klienta.</span><span class="sxs-lookup"><span data-stu-id="e7fca-107">You can also determine what claims are being made on behalf of the client by iterating through the collection of claims in the <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> property.</span></span>  
  
### <a name="to-get-the-current-security-context"></a><span data-ttu-id="e7fca-108">Získání aktuálního kontextu zabezpečení</span><span class="sxs-lookup"><span data-stu-id="e7fca-108">To get the current security context</span></span>  
  
- <span data-ttu-id="e7fca-109">Přístup ke statické vlastnosti <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> pro získání aktuálního kontextu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e7fca-109">Access the static property <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> to get the current security context.</span></span> <span data-ttu-id="e7fca-110">Prověřte všechny vlastnosti aktuálního kontextu z reference.</span><span class="sxs-lookup"><span data-stu-id="e7fca-110">Examine any of the properties of the current context from the reference.</span></span>  
  
### <a name="to-determine-the-identity-of-the-caller"></a><span data-ttu-id="e7fca-111">Určení identity volajícího</span><span class="sxs-lookup"><span data-stu-id="e7fca-111">To determine the identity of the caller</span></span>  
  
1. <span data-ttu-id="e7fca-112">Vytiskněte hodnotu vlastností <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> a <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A>.</span><span class="sxs-lookup"><span data-stu-id="e7fca-112">Print the value of the <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> and <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> properties.</span></span>  
  
### <a name="to-parse-the-claims-of-a-caller"></a><span data-ttu-id="e7fca-113">Postup analýzy deklarací volajícího</span><span class="sxs-lookup"><span data-stu-id="e7fca-113">To parse the claims of a caller</span></span>  
  
1. <span data-ttu-id="e7fca-114">Vrátí aktuální třídu <xref:System.IdentityModel.Policy.AuthorizationContext>.</span><span class="sxs-lookup"><span data-stu-id="e7fca-114">Return the current <xref:System.IdentityModel.Policy.AuthorizationContext> class.</span></span> <span data-ttu-id="e7fca-115">Pomocí vlastnosti <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> vraťte aktuální kontext zabezpečení služby a pak pomocí vlastnosti <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> vraťte `AuthorizationContext`.</span><span class="sxs-lookup"><span data-stu-id="e7fca-115">Use the <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> property to return the current service security context, then return the `AuthorizationContext` using the <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A> property.</span></span>  
  
2. <span data-ttu-id="e7fca-116">Analyzuje kolekci objektů <xref:System.IdentityModel.Claims.ClaimSet> vrácených vlastností <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> třídy <xref:System.IdentityModel.Policy.AuthorizationContext>.</span><span class="sxs-lookup"><span data-stu-id="e7fca-116">Parse the collection of <xref:System.IdentityModel.Claims.ClaimSet> objects returned by the <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> property of the <xref:System.IdentityModel.Policy.AuthorizationContext> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7fca-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="e7fca-117">Example</span></span>  
 <span data-ttu-id="e7fca-118">Následující příklad vytiskne hodnoty vlastností <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> a <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> aktuálního kontextu zabezpečení a vlastnost <xref:System.IdentityModel.Claims.Claim.ClaimType%2A>, hodnotu prostředku deklarace identity a vlastnost <xref:System.IdentityModel.Claims.Claim.Right%2A> každé deklarace identity v aktuálním kontextu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e7fca-118">The following example prints the values of the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> and <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> properties of the current security context and the <xref:System.IdentityModel.Claims.Claim.ClaimType%2A> property, the resource value of the claim, and the <xref:System.IdentityModel.Claims.Claim.Right%2A> property of every claim in the current security context.</span></span>  
  
 [!code-csharp[c_PrincipalPermissionAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#4)]
 [!code-vb[c_PrincipalPermissionAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#4)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e7fca-119">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="e7fca-119">Compiling the Code</span></span>  
 <span data-ttu-id="e7fca-120">Kód používá následující obory názvů:</span><span class="sxs-lookup"><span data-stu-id="e7fca-120">The code uses the following namespaces:</span></span>  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.IdentityModel.Policy>  
  
- <xref:System.IdentityModel.Claims>  
  
## <a name="see-also"></a><span data-ttu-id="e7fca-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e7fca-121">See also</span></span>

- [<span data-ttu-id="e7fca-122">Zabezpečení služeb</span><span class="sxs-lookup"><span data-stu-id="e7fca-122">Securing Services</span></span>](securing-services.md)
- [<span data-ttu-id="e7fca-123">Identita a ověřování služby</span><span class="sxs-lookup"><span data-stu-id="e7fca-123">Service Identity and Authentication</span></span>](./feature-details/service-identity-and-authentication.md)
