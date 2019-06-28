---
title: 'Postupy: Nastavení potvrzení podpisu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- signature confirmation
- WCF, security
ms.assetid: 2424c137-c7c2-4aa9-8d5d-a066e12fefda
ms.openlocfilehash: 6f44ae5e3615df7f529a25f4097ef042feba544d
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2019
ms.locfileid: "67425441"
---
# <a name="how-to-set-up-a-signature-confirmation"></a><span data-ttu-id="64fe9-102">Postupy: Nastavení potvrzení podpisu</span><span class="sxs-lookup"><span data-stu-id="64fe9-102">How to: Set Up a Signature Confirmation</span></span>

<span data-ttu-id="64fe9-103">*Potvrzení podpisu* sítí je mechanismus pro iniciátor zprávy k zajištění, že byla přijata odpověď byla vygenerována v reakci na původní zprávu o odesílatele.</span><span class="sxs-lookup"><span data-stu-id="64fe9-103">*Signature confirmation* is a mechanism for a message initiator to ensure that a received reply was generated in response to the sender's original message.</span></span> <span data-ttu-id="64fe9-104">Potvrzení podpisu je definováno ve specifikaci WS-Security 1.1.</span><span class="sxs-lookup"><span data-stu-id="64fe9-104">Signature confirmation is defined in the WS-Security 1.1 specification.</span></span> <span data-ttu-id="64fe9-105">Pokud koncový bod podporuje WS-Security 1.0, nemůžete použít potvrzení podpisu.</span><span class="sxs-lookup"><span data-stu-id="64fe9-105">If an endpoint supports WS-Security 1.0, you cannot use signature confirmation.</span></span>

<span data-ttu-id="64fe9-106">Následující postupy, určete, jak povolit potvrzení podpisu pomocí <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="64fe9-106">The following procedures specify how to enable signature confirmation using an <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="64fe9-107">Můžete použít stejný postup se <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="64fe9-107">You can use the same procedure with a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="64fe9-108">Postup staví na základních kroků v [jak: Vytvoření vlastní vazby pomocí elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="64fe9-108">The procedure builds upon the basic steps found in [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>

### <a name="to-enable-signature-confirmation-in-code"></a><span data-ttu-id="64fe9-109">Chcete-li povolit potvrzení podpisu v kódu</span><span class="sxs-lookup"><span data-stu-id="64fe9-109">To enable signature confirmation in code</span></span>

1. <span data-ttu-id="64fe9-110">Vytvořit instanci <xref:System.ServiceModel.Channels.BindingElementCollection> třídy.</span><span class="sxs-lookup"><span data-stu-id="64fe9-110">Create an instance of the <xref:System.ServiceModel.Channels.BindingElementCollection> class.</span></span>

2. <span data-ttu-id="64fe9-111">Vytvoření instance <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> třídy.</span><span class="sxs-lookup"><span data-stu-id="64fe9-111">Create an instance of the  <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> class.</span></span>

3. <span data-ttu-id="64fe9-112">Nastavte <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> k `true`.</span><span class="sxs-lookup"><span data-stu-id="64fe9-112">Set the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> to `true`.</span></span>

4. <span data-ttu-id="64fe9-113">Přidáte element zabezpečení do kolekce vazby.</span><span class="sxs-lookup"><span data-stu-id="64fe9-113">Add the security element to the binding collection.</span></span>

5. <span data-ttu-id="64fe9-114">Vytvoření vlastní vazby, jak je uvedeno v [jak: Vytvoření vlastní vazby pomocí elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="64fe9-114">Create a custom binding, as specified in [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>

### <a name="to-enable-signature-confirmation-in-configuration"></a><span data-ttu-id="64fe9-115">Chcete-li povolit potvrzení podpisu v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="64fe9-115">To enable signature confirmation in configuration</span></span>

1. <span data-ttu-id="64fe9-116">Přidat `<customBinding>` elementu `<bindings>` oddílu konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="64fe9-116">Add a `<customBinding>` element to the `<bindings>` section of the configuration file.</span></span>

2. <span data-ttu-id="64fe9-117">Přidat `<binding>` elementu a nastavte název atributu na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="64fe9-117">Add a `<binding>` element and set the name attribute to an appropriate value.</span></span>

3. <span data-ttu-id="64fe9-118">Přidáte odpovídající element kódování.</span><span class="sxs-lookup"><span data-stu-id="64fe9-118">Add an appropriate encoding element.</span></span> <span data-ttu-id="64fe9-119">Následující příklad přidá `<TextMessageEncoding>` elementu.</span><span class="sxs-lookup"><span data-stu-id="64fe9-119">The following example adds a `<TextMessageEncoding>` element.</span></span>

4. <span data-ttu-id="64fe9-120">Přidat `<security>` podřízený element a nastavte `requireSignatureConfirmation` atribut `true`.</span><span class="sxs-lookup"><span data-stu-id="64fe9-120">Add a `<security>` child element and set the `requireSignatureConfirmation` attribute to `true`.</span></span>

5. <span data-ttu-id="64fe9-121">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="64fe9-121">Optional.</span></span> <span data-ttu-id="64fe9-122">Chcete-li povolit potvrzení podpisu během spuštění, přidejte [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) podřízený element a nastavte `requireSignatureConfirmation` atribut `true`.</span><span class="sxs-lookup"><span data-stu-id="64fe9-122">To enable signature confirmation during the bootstrap, add a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) child element and set the `requireSignatureConfirmation` attribute to `true`.</span></span>

6. <span data-ttu-id="64fe9-123">Přidáte element přenosu odpovídající.</span><span class="sxs-lookup"><span data-stu-id="64fe9-123">Add an appropriate transport element.</span></span> <span data-ttu-id="64fe9-124">Následující příklad přidá [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md):</span><span class="sxs-lookup"><span data-stu-id="64fe9-124">The following example adds an [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md):</span></span>

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

## <a name="example"></a><span data-ttu-id="64fe9-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="64fe9-125">Example</span></span>

<span data-ttu-id="64fe9-126">Následující kód vytvoří instanci <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> a nastaví <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="64fe9-126">The following code creates an instance of the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and sets the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> property to `true`.</span></span> <span data-ttu-id="64fe9-127">Všimněte si, že v tomto příkladu nepoužívá `<secureConversationBootstrap>` element je znázorněno v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="64fe9-127">Note that this example does not use the `<secureConversationBootstrap>` element shown in the preceding example.</span></span> <span data-ttu-id="64fe9-128">Tento příklad ukazuje potvrzení podpisu při použití token Windows (protokol Kerberos).</span><span class="sxs-lookup"><span data-stu-id="64fe9-128">This example demonstrates signature confirmation when using a Windows (Kerberos protocol) token.</span></span> <span data-ttu-id="64fe9-129">V tomto případě podpis klienta se vrátí ve všech odpovědí od služby a potvrdí klientem.</span><span class="sxs-lookup"><span data-stu-id="64fe9-129">In this case, the signature of the client is returned in all responses from the service and is confirmed by the client.</span></span>

[!code-csharp[c_SignatureConfirmation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_signatureconfirmation/cs/source.cs#1)]
[!code-vb[c_SignatureConfirmation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_signatureconfirmation/vb/source.vb#1)]

## <a name="see-also"></a><span data-ttu-id="64fe9-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="64fe9-130">See also</span></span>

- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>
- [<span data-ttu-id="64fe9-131">Postupy: Vytvoření vlastní vazby pomocí elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="64fe9-131">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="64fe9-132">Postupy: Vytvoření elementu SecurityBindingElement pro zadaný režim ověřování</span><span class="sxs-lookup"><span data-stu-id="64fe9-132">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
