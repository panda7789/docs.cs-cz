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
ms.openlocfilehash: 9423922753efee7aac32e430f97307c715e43464
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84586909"
---
# <a name="how-to-set-up-a-signature-confirmation"></a><span data-ttu-id="7ca73-102">Postupy: Nastavení potvrzení podpisu</span><span class="sxs-lookup"><span data-stu-id="7ca73-102">How to: Set Up a Signature Confirmation</span></span>

<span data-ttu-id="7ca73-103">*Potvrzení podpisu* je mechanismus pro iniciátora zprávy, který zajistí, že přijatá odpověď byla vygenerována v reakci na původní zprávu odesílatele.</span><span class="sxs-lookup"><span data-stu-id="7ca73-103">*Signature confirmation* is a mechanism for a message initiator to ensure that a received reply was generated in response to the sender's original message.</span></span> <span data-ttu-id="7ca73-104">Potvrzení podpisu je definováno ve specifikaci WS-Security 1,1.</span><span class="sxs-lookup"><span data-stu-id="7ca73-104">Signature confirmation is defined in the WS-Security 1.1 specification.</span></span> <span data-ttu-id="7ca73-105">Pokud koncový bod podporuje WS-Security 1,0, nemůžete použít potvrzení podpisu.</span><span class="sxs-lookup"><span data-stu-id="7ca73-105">If an endpoint supports WS-Security 1.0, you cannot use signature confirmation.</span></span>

<span data-ttu-id="7ca73-106">Následující postupy určují, jak povolit potvrzení podpisu pomocí <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="7ca73-106">The following procedures specify how to enable signature confirmation using an <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="7ca73-107">Stejný postup můžete použít s <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="7ca73-107">You can use the same procedure with a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>.</span></span> <span data-ttu-id="7ca73-108">Procedura je založena na základních krocích, které byly nalezeny v tématu [Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="7ca73-108">The procedure builds upon the basic steps found in [How to: Create a Custom Binding Using the SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>

### <a name="to-enable-signature-confirmation-in-code"></a><span data-ttu-id="7ca73-109">Povolení potvrzení podpisu v kódu</span><span class="sxs-lookup"><span data-stu-id="7ca73-109">To enable signature confirmation in code</span></span>

1. <span data-ttu-id="7ca73-110">Vytvořit instanci <xref:System.ServiceModel.Channels.BindingElementCollection> třídy.</span><span class="sxs-lookup"><span data-stu-id="7ca73-110">Create an instance of the <xref:System.ServiceModel.Channels.BindingElementCollection> class.</span></span>

2. <span data-ttu-id="7ca73-111">Vytvořte instanci <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> třídy.</span><span class="sxs-lookup"><span data-stu-id="7ca73-111">Create an instance of the  <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> class.</span></span>

3. <span data-ttu-id="7ca73-112">Nastavte na <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> `true` .</span><span class="sxs-lookup"><span data-stu-id="7ca73-112">Set the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> to `true`.</span></span>

4. <span data-ttu-id="7ca73-113">Přidejte prvek zabezpečení do kolekce vazeb.</span><span class="sxs-lookup"><span data-stu-id="7ca73-113">Add the security element to the binding collection.</span></span>

5. <span data-ttu-id="7ca73-114">Vytvořte vlastní vazbu, jak je uvedeno v tématu [Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="7ca73-114">Create a custom binding, as specified in [How to: Create a Custom Binding Using the SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span>

### <a name="to-enable-signature-confirmation-in-configuration"></a><span data-ttu-id="7ca73-115">Povolení potvrzení podpisu v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="7ca73-115">To enable signature confirmation in configuration</span></span>

1. <span data-ttu-id="7ca73-116">Přidejte `<customBinding>` element do `<bindings>` oddílu konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="7ca73-116">Add a `<customBinding>` element to the `<bindings>` section of the configuration file.</span></span>

2. <span data-ttu-id="7ca73-117">Přidejte `<binding>` element a nastavte atribut Name na odpovídající hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7ca73-117">Add a `<binding>` element and set the name attribute to an appropriate value.</span></span>

3. <span data-ttu-id="7ca73-118">Přidejte příslušný element kódování.</span><span class="sxs-lookup"><span data-stu-id="7ca73-118">Add an appropriate encoding element.</span></span> <span data-ttu-id="7ca73-119">Následující příklad přidá `<TextMessageEncoding>` prvek.</span><span class="sxs-lookup"><span data-stu-id="7ca73-119">The following example adds a `<TextMessageEncoding>` element.</span></span>

4. <span data-ttu-id="7ca73-120">Přidejte `<security>` podřízený element a nastavte `requireSignatureConfirmation` atribut na `true` .</span><span class="sxs-lookup"><span data-stu-id="7ca73-120">Add a `<security>` child element and set the `requireSignatureConfirmation` attribute to `true`.</span></span>

5. <span data-ttu-id="7ca73-121">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="7ca73-121">Optional.</span></span> <span data-ttu-id="7ca73-122">Chcete-li povolit potvrzení podpisu při spuštění, přidejte [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) podřízený element a nastavte `requireSignatureConfirmation` atribut na `true` .</span><span class="sxs-lookup"><span data-stu-id="7ca73-122">To enable signature confirmation during the bootstrap, add a [\<secureConversationBootstrap>](../../configure-apps/file-schema/wcf/secureconversationbootstrap.md) child element and set the `requireSignatureConfirmation` attribute to `true`.</span></span>

6. <span data-ttu-id="7ca73-123">Přidejte příslušný transportní element.</span><span class="sxs-lookup"><span data-stu-id="7ca73-123">Add an appropriate transport element.</span></span> <span data-ttu-id="7ca73-124">Následující příklad přidá [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md) :</span><span class="sxs-lookup"><span data-stu-id="7ca73-124">The following example adds an [\<httpTransport>](../../configure-apps/file-schema/wcf/httptransport.md):</span></span>

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

## <a name="example"></a><span data-ttu-id="7ca73-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="7ca73-125">Example</span></span>

<span data-ttu-id="7ca73-126">Následující kód vytvoří instanci třídy <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> a nastaví <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> vlastnost na hodnotu `true` .</span><span class="sxs-lookup"><span data-stu-id="7ca73-126">The following code creates an instance of the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> and sets the <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement.RequireSignatureConfirmation%2A> property to `true`.</span></span> <span data-ttu-id="7ca73-127">Všimněte si, že tento příklad nepoužívá `<secureConversationBootstrap>` prvek zobrazený v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="7ca73-127">Note that this example does not use the `<secureConversationBootstrap>` element shown in the preceding example.</span></span> <span data-ttu-id="7ca73-128">Tento příklad ukazuje potvrzení podpisu při použití tokenu Windows (protokolu Kerberos).</span><span class="sxs-lookup"><span data-stu-id="7ca73-128">This example demonstrates signature confirmation when using a Windows (Kerberos protocol) token.</span></span> <span data-ttu-id="7ca73-129">V takovém případě se podpis klienta vrátí ve všech odpovědích služby a klient ho potvrdí.</span><span class="sxs-lookup"><span data-stu-id="7ca73-129">In this case, the signature of the client is returned in all responses from the service and is confirmed by the client.</span></span>

[!code-csharp[c_SignatureConfirmation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_signatureconfirmation/cs/source.cs#1)]
[!code-vb[c_SignatureConfirmation#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_signatureconfirmation/vb/source.vb#1)]

## <a name="see-also"></a><span data-ttu-id="7ca73-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="7ca73-130">See also</span></span>

- <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>
- <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>
- [<span data-ttu-id="7ca73-131">Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="7ca73-131">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="7ca73-132">Postupy: Vytvoření elementu SecurityBindingElement pro zadaný režim ověřování</span><span class="sxs-lookup"><span data-stu-id="7ca73-132">How to: Create a SecurityBindingElement for a Specified Authentication Mode</span></span>](how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
