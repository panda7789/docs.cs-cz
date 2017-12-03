---
title: "Postupy: Nastavení potvrzení podpisu"
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
- signature confirmation
- WCF, security
ms.assetid: 2424c137-c7c2-4aa9-8d5d-a066e12fefda
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fced2ddd16ae244e2ea3d945082f48ffd23302e6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-set-up-a-signature-confirmation"></a><span data-ttu-id="438df-102">Postupy: Nastavení potvrzení podpisu</span><span class="sxs-lookup"><span data-stu-id="438df-102">How to: Set Up a Signature Confirmation</span></span>
<span data-ttu-id="438df-103">*Potvrzení podpisu* mechanismus pro zprávu iniciátor zajistit, že byla přijata odpověď byla vygenerována v reakci na původní zprávu o odesílatele.</span><span class="sxs-lookup"><span data-stu-id="438df-103">*Signature confirmation* is a mechanism for a message initiator to ensure that a received reply was generated in response to the sender's original message.</span></span> <span data-ttu-id="438df-104">Potvrzení podpisu je definována ve specifikaci WS-zabezpečení 1.1.</span><span class="sxs-lookup"><span data-stu-id="438df-104">Signature confirmation is defined in the WS-Security 1.1 specification.</span></span> <span data-ttu-id="438df-105">Pokud koncový bod podporuje WS-Security 1.0, nemůžete použít potvrzení podpisu.</span><span class="sxs-lookup"><span data-stu-id="438df-105">If an endpoint supports WS-Security 1.0, you cannot use signature confirmation.</span></span>  
  
 <span data-ttu-id="438df-106">Následující postupy, určete, jak povolit pomocí potvrzení podpisu <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="438df-106">The following procedures specify how to enable signature confirmation using an <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="438df-107">Můžete použít stejný postup s <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="438df-107">You can use the same procedure with a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="438df-108">Postup staví na základní kroky, které jsou součástí [postupy: vytvoření vlastní vazby pomocí elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="438df-108">The procedure builds upon the basic steps found in [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>  
  
### <a name="to-enable-signature-confirmation-in-code"></a><span data-ttu-id="438df-109">Chcete-li povolit potvrzení podpisu v kódu</span><span class="sxs-lookup"><span data-stu-id="438df-109">To enable signature confirmation in code</span></span>  
  
1.  <span data-ttu-id="438df-110">Vytvořit instanci <xref:System.ServiceModel.Channels.BindingElementCollection> třídy.</span><span class="sxs-lookup"><span data-stu-id="438df-110">Create an instance of the <xref:System.ServiceModel.Channels.BindingElementCollection> class.</span></span>  
  
2.  <span data-ttu-id="438df-111">Vytvoření instance <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> třídy.</span><span class="sxs-lookup"><span data-stu-id="438df-111">Create an instance of the  <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> class.</span></span>  
  
3.  <span data-ttu-id="438df-112">Nastavte <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> k `true`.</span><span class="sxs-lookup"><span data-stu-id="438df-112">Set the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> to `true`.</span></span>  
  
4.  <span data-ttu-id="438df-113">Přidáte element zabezpečení do kolekce vazby.</span><span class="sxs-lookup"><span data-stu-id="438df-113">Add the security element to the binding collection.</span></span>  
  
5.  <span data-ttu-id="438df-114">Vytvoření vlastní vazby, jak je uvedeno v [postupy: vytvoření vlastní vazby pomocí elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="438df-114">Create a custom binding, as specified in [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>  
  
### <a name="to-enable-signature-confirmation-in-configuration"></a><span data-ttu-id="438df-115">Chcete-li povolit potvrzení podpisu v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="438df-115">To enable signature confirmation in configuration</span></span>  
  
1.  <span data-ttu-id="438df-116">Přidat `<customBinding>` elementu, který chcete `<bindings>` oddíl konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="438df-116">Add a `<customBinding>` element to the `<bindings>` section of the configuration file.</span></span>  
  
2.  <span data-ttu-id="438df-117">Přidat `<binding>` elementu a sadu název atributu na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="438df-117">Add a `<binding>` element and set the name attribute to an appropriate value.</span></span>  
  
3.  <span data-ttu-id="438df-118">Přidáte odpovídající element kódování.</span><span class="sxs-lookup"><span data-stu-id="438df-118">Add an appropriate encoding element.</span></span> <span data-ttu-id="438df-119">Následující příklad přidá `<TextMessageEncoding>` elementu.</span><span class="sxs-lookup"><span data-stu-id="438df-119">The following example adds a `<TextMessageEncoding>` element.</span></span>  
  
4.  <span data-ttu-id="438df-120">Přidat `<security>` podřízený element a sadu `requireSignatureConfirmation` atribut `true`.</span><span class="sxs-lookup"><span data-stu-id="438df-120">Add a `<security>` child element and set the `requireSignatureConfirmation` attribute to `true`.</span></span>  
  
5.  <span data-ttu-id="438df-121">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="438df-121">Optional.</span></span> <span data-ttu-id="438df-122">Chcete-li povolit potvrzení podpisu během službou bootstrap nástroje, přidejte [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) podřízený element a sadu `equireSignatureConfirmation` atribut `true`.</span><span class="sxs-lookup"><span data-stu-id="438df-122">To enable signature confirmation during the bootstrap, add a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) child element and set the `equireSignatureConfirmation` attribute to `true`.</span></span>  
  
6.  <span data-ttu-id="438df-123">Přidáte element odpovídající přenosu.</span><span class="sxs-lookup"><span data-stu-id="438df-123">Add an appropriate transport element.</span></span> <span data-ttu-id="438df-124">Následující příklad přidá [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md):</span><span class="sxs-lookup"><span data-stu-id="438df-124">The following example adds an [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md):</span></span>  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="SignatureConfirmationBinding">  
          <security requireSignatureConfirmation="true">  
            <secureConversationBootstrap requireSignatureConfirmation="true" />  
              </security>  
           <textMessageEncoding />  
             <httpTransport />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
## <a name="example"></a><span data-ttu-id="438df-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="438df-125">Example</span></span>  
 <span data-ttu-id="438df-126">Následující kód vytvoří instanci <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> a nastaví <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="438df-126">The following code creates an instance of the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and sets the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> property to `true`.</span></span> <span data-ttu-id="438df-127">Všimněte si, že v tomto příkladu se nepoužívá `<secureConversationBootstrap>` element v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="438df-127">Note that this example does not use the `<secureConversationBootstrap>` element shown in the preceding example.</span></span> <span data-ttu-id="438df-128">Tento příklad ukazuje potvrzení podpisu při použití tokenu systému Windows (protokol Kerberos).</span><span class="sxs-lookup"><span data-stu-id="438df-128">This example demonstrates signature confirmation when using a Windows (Kerberos protocol) token.</span></span> <span data-ttu-id="438df-129">V takovém případě podpis klienta je vrácený v všechny odpovědi ze služby a je potvrzen klientem.</span><span class="sxs-lookup"><span data-stu-id="438df-129">In this case, the signature of the client is returned in all responses from the service and is confirmed by the client.</span></span>  
  
 [!code-csharp[c_SignatureConfirmation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_signatureconfirmation/cs/source.cs#1)]
 [!code-vb[c_SignatureConfirmation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_signatureconfirmation/vb/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="438df-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="438df-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>  
 <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>  
 [<span data-ttu-id="438df-131">Postupy: vytvoření vlastní vazby pomocí elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="438df-131">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="438df-132">Postupy: vytvoření elementu SecurityBindingElement pro zadaný režim ověřování</span><span class="sxs-lookup"><span data-stu-id="438df-132">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
