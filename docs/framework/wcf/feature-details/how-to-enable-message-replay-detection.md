---
title: 'Postupy: Povolení zjišťování opakování zpráv'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF security
- replay detection [WCF]
- WCF, custom bindings
- WCF, security
ms.assetid: 8b847e91-69a3-49e1-9e5f-0c455e50d804
ms.openlocfilehash: 450a99fc6604ccb3fa796e8a73e1ddc3e3adff9e
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964658"
---
# <a name="how-to-enable-message-replay-detection"></a><span data-ttu-id="89db4-102">Postupy: Povolení zjišťování opakování zpráv</span><span class="sxs-lookup"><span data-stu-id="89db4-102">How to: Enable Message Replay Detection</span></span>
<span data-ttu-id="89db4-103">K útoku opakovaného přehrání dojde, když útočník zkopíruje datový proud zpráv mezi dvěma stranami a přehraje datový proud na jednu nebo více stran.</span><span class="sxs-lookup"><span data-stu-id="89db4-103">A replay attack occurs when an attacker copies a stream of messages between two parties and replays the stream to one or more of the parties.</span></span> <span data-ttu-id="89db4-104">V případě, že počítače, které jsou předmětem útoku, zpracuje datový proud jako legitimní zprávy, což vede k celé řadě špatných důsledků, jako je například redundantní objednávka položky.</span><span class="sxs-lookup"><span data-stu-id="89db4-104">Unless mitigated, the computers subject to the attack will process the stream as legitimate messages, resulting in a range of bad consequences, such as redundant orders of an item.</span></span>  
  
 <span data-ttu-id="89db4-105">Další informace o detekci opětovného přehrání zpráv najdete v tématu zjištění opětovného [přehrání zprávy](https://docs.microsoft.com/previous-versions/msp-n-p/ff649371(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="89db4-105">For more information about message replay detection, see [Message Replay Detection](https://docs.microsoft.com/previous-versions/msp-n-p/ff649371(v=pandp.10)).</span></span>  
  
 <span data-ttu-id="89db4-106">Následující postup ukazuje různé vlastnosti, které lze použít k řízení detekce přehrání pomocí Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="89db4-106">The following procedure demonstrates various properties that you can use to control replay detection using Windows Communication Foundation (WCF).</span></span>  
  
### <a name="to-control-replay-detection-on-the-client-using-code"></a><span data-ttu-id="89db4-107">Řízení zjišťování opakování v klientovi pomocí kódu</span><span class="sxs-lookup"><span data-stu-id="89db4-107">To control replay detection on the client using code</span></span>  
  
1. <span data-ttu-id="89db4-108">Vytvořte <xref:System.ServiceModel.Channels.SecurityBindingElement> pro použití v <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="89db4-108">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> to use in a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span> <span data-ttu-id="89db4-109">Další informace najdete v tématu [Postup: Vytvoření vlastní vazby pomocí SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="89db4-109">For more information, see [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span> <span data-ttu-id="89db4-110">Následující příklad používá <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> vytvořené pomocí <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> třídy <xref:System.ServiceModel.Channels.SecurityBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="89db4-110">The following example uses a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> created with the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> of the <xref:System.ServiceModel.Channels.SecurityBindingElement> class.</span></span>  
  
2. <span data-ttu-id="89db4-111">Pomocí vlastnosti <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> vraťte odkaz na třídu <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> a podle potřeby nastavte některou z následujících vlastností:</span><span class="sxs-lookup"><span data-stu-id="89db4-111">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> property to return a reference to the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> class and set any of the following properties, as appropriate:</span></span>  
  
    1. <span data-ttu-id="89db4-112">`DetectReplay`.</span><span class="sxs-lookup"><span data-stu-id="89db4-112">`DetectReplay`.</span></span> <span data-ttu-id="89db4-113">Logická hodnota</span><span class="sxs-lookup"><span data-stu-id="89db4-113">A Boolean value.</span></span> <span data-ttu-id="89db4-114">Tím se určuje, zda má klient detekovat hry ze serveru.</span><span class="sxs-lookup"><span data-stu-id="89db4-114">This governs whether the client should detect replays from the server.</span></span> <span data-ttu-id="89db4-115">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="89db4-115">The default is `true`.</span></span>  
  
    2. <span data-ttu-id="89db4-116">`MaxClockSkew`.</span><span class="sxs-lookup"><span data-stu-id="89db4-116">`MaxClockSkew`.</span></span> <span data-ttu-id="89db4-117">Hodnota <xref:System.TimeSpan>.</span><span class="sxs-lookup"><span data-stu-id="89db4-117">A <xref:System.TimeSpan> value.</span></span> <span data-ttu-id="89db4-118">Určuje, kolik času se má v případě, že je možné mezi klientem a serverem tolerovat mechanismus opakovaného přehrávání.</span><span class="sxs-lookup"><span data-stu-id="89db4-118">Governs how much time skew the replay mechanism can tolerate between the client and the server.</span></span> <span data-ttu-id="89db4-119">Mechanismus zabezpečení prověřuje odeslané časové razítko a určí, zda byl v minulosti odeslán příliš daleko zpátky.</span><span class="sxs-lookup"><span data-stu-id="89db4-119">The security mechanism examines the time stamp sent and determines whether it was sent too far back in the past.</span></span> <span data-ttu-id="89db4-120">Výchozí hodnota je 5 minut.</span><span class="sxs-lookup"><span data-stu-id="89db4-120">The default is 5 minutes.</span></span>  
  
    3. <span data-ttu-id="89db4-121">`ReplayWindow`.</span><span class="sxs-lookup"><span data-stu-id="89db4-121">`ReplayWindow`.</span></span> <span data-ttu-id="89db4-122">Hodnota `TimeSpan`.</span><span class="sxs-lookup"><span data-stu-id="89db4-122">A `TimeSpan` value.</span></span> <span data-ttu-id="89db4-123">To určuje, jak dlouho může zpráva v síti fungovat poté, co ji server pošle (prostřednictvím zprostředkovatelů) před tím, než se dopustí klientovi.</span><span class="sxs-lookup"><span data-stu-id="89db4-123">This governs how long a message can live in the network after the server sends it (through intermediaries) before reaching the client.</span></span> <span data-ttu-id="89db4-124">Klient sleduje podpisy zpráv odeslaných v rámci nejnovější `ReplayWindow` pro účely detekce opětovného přehrání.</span><span class="sxs-lookup"><span data-stu-id="89db4-124">The client tracks the signatures of the messages sent within the latest `ReplayWindow` for the purposes of replay detection.</span></span>  
  
    4. <span data-ttu-id="89db4-125">`ReplayCacheSize`.</span><span class="sxs-lookup"><span data-stu-id="89db4-125">`ReplayCacheSize`.</span></span> <span data-ttu-id="89db4-126">Celočíselná hodnota.</span><span class="sxs-lookup"><span data-stu-id="89db4-126">An integer value.</span></span> <span data-ttu-id="89db4-127">Klient ukládá podpisy zprávy do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="89db4-127">The client stores the signatures of the message in a cache.</span></span> <span data-ttu-id="89db4-128">Toto nastavení určuje, kolik podpisů může mezipaměť ukládat.</span><span class="sxs-lookup"><span data-stu-id="89db4-128">This setting specifies how many signatures the cache can store.</span></span> <span data-ttu-id="89db4-129">Pokud počet zpráv odeslaných v rámci posledního opětovného přehrávání dosáhne limitu mezipaměti, nové zprávy jsou odmítnuty, dokud nedosáhnou nejstarších podpisů v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="89db4-129">If the number of messages sent within the last replay window reaches the cache limit, new messages are rejected until the oldest cached signatures reach the time limit.</span></span> <span data-ttu-id="89db4-130">Výchozí hodnota je 500000.</span><span class="sxs-lookup"><span data-stu-id="89db4-130">The default is 500000.</span></span>  
  
### <a name="to-control-replay-detection-on-the-service-using-code"></a><span data-ttu-id="89db4-131">Řízení zjišťování opakování u služby pomocí kódu</span><span class="sxs-lookup"><span data-stu-id="89db4-131">To control replay detection on the service using code</span></span>  
  
1. <span data-ttu-id="89db4-132">Vytvořte <xref:System.ServiceModel.Channels.SecurityBindingElement> pro použití v <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="89db4-132">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> to use in a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
2. <span data-ttu-id="89db4-133">Pomocí vlastnosti <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> vraťte odkaz na třídu <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> a nastavte vlastnosti tak, jak je popsáno výše.</span><span class="sxs-lookup"><span data-stu-id="89db4-133">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> property to return a reference to the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class, and set the properties as described previously.</span></span>  
  
### <a name="to-control-replay-detection-in-configuration-for-the-client-or-service"></a><span data-ttu-id="89db4-134">Řízení zjišťování opětovného přehrání v konfiguraci pro klienta nebo službu</span><span class="sxs-lookup"><span data-stu-id="89db4-134">To control replay detection in configuration for the client or service</span></span>  
  
1. <span data-ttu-id="89db4-135">Vytvořte [\<CustomBinding](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="89db4-135">Create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
2. <span data-ttu-id="89db4-136">Vytvořte `<security>` element.</span><span class="sxs-lookup"><span data-stu-id="89db4-136">Create a `<security>` element.</span></span>  
  
3. <span data-ttu-id="89db4-137">Vytvořte [\<localClientSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md) nebo [\<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md).</span><span class="sxs-lookup"><span data-stu-id="89db4-137">Create a [\<localClientSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md) or [\<localServiceSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md).</span></span>  
  
4. <span data-ttu-id="89db4-138">Nastavte následující hodnoty atributu podle potřeby: `detectReplays`, `maxClockSkew`, `replayWindow`a `replayCacheSize`.</span><span class="sxs-lookup"><span data-stu-id="89db4-138">Set the following attribute values, as appropriate: `detectReplays`, `maxClockSkew`, `replayWindow`, and `replayCacheSize`.</span></span> <span data-ttu-id="89db4-139">Následující příklad nastaví atributy `<localServiceSettings>` a `<localClientSettings>` elementu:</span><span class="sxs-lookup"><span data-stu-id="89db4-139">The following example sets the attributes of both a `<localServiceSettings>` and a `<localClientSettings>` element:</span></span>  
  
    ```xml  
    <customBinding>  
      <binding name="NewBinding0">  
       <textMessageEncoding />  
        <security>  
         <localClientSettings   
          replayCacheSize="800000"   
          maxClockSkew="00:03:00"  
          replayWindow="00:03:00" />  
         <localServiceSettings   
          replayCacheSize="800000"   
          maxClockSkew="00:03:00"  
          replayWindow="00:03:00" />  
        <secureConversationBootstrap />  
       </security>  
      <httpTransport />  
     </binding>  
    </customBinding>  
    ```  
  
## <a name="example"></a><span data-ttu-id="89db4-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="89db4-140">Example</span></span>  
 <span data-ttu-id="89db4-141">Následující příklad vytvoří <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> pomocí metody <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> a nastaví vlastnosti opětovného přehrání vazby.</span><span class="sxs-lookup"><span data-stu-id="89db4-141">The following example creates a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> using the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> method, and sets the replay properties of the binding.</span></span>  
  
 [!code-csharp[c_ReplayDetection#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_replaydetection/cs/source.cs#1)]
 [!code-vb[c_ReplayDetection#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_replaydetection/vb/source.vb#1)]  
  
## <a name="scope-of-replay-message-security-only"></a><span data-ttu-id="89db4-142">Rozsah přehrání: pouze zabezpečení zprávy</span><span class="sxs-lookup"><span data-stu-id="89db4-142">Scope of Replay: Message Security Only</span></span>  
 <span data-ttu-id="89db4-143">Následující postupy platí pouze pro režim zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="89db4-143">Note that the following procedures apply only to Message security mode.</span></span> <span data-ttu-id="89db4-144">Pro přenos a přenos s režimem přihlašovacích údajů zpráv zjišťují mechanismy přenosu.</span><span class="sxs-lookup"><span data-stu-id="89db4-144">For Transport and Transport with Message Credential modes, the transport mechanisms detect replays.</span></span>  
  
## <a name="secure-conversation-notes"></a><span data-ttu-id="89db4-145">Zabezpečené poznámky ke konverzaci</span><span class="sxs-lookup"><span data-stu-id="89db4-145">Secure Conversation Notes</span></span>  
 <span data-ttu-id="89db4-146">U vazeb, které umožňují zabezpečenou konverzaci, můžete tato nastavení upravit pro kanál aplikace i pro spouštěcí vazby zabezpečené konverzace.</span><span class="sxs-lookup"><span data-stu-id="89db4-146">For bindings that enable secure conversations, you can adjust these settings both for the application channel as well as for the secure conversation bootstrap binding.</span></span> <span data-ttu-id="89db4-147">Můžete například vypnout přehrávání pro kanál aplikace, ale povolit je pro spouštěcí kanál, který vytváří zabezpečenou konverzaci.</span><span class="sxs-lookup"><span data-stu-id="89db4-147">For example, you can turn off replays for the application channel but enable them for the bootstrap channel that establishes the secure conversation.</span></span>  
  
 <span data-ttu-id="89db4-148">Pokud nepoužíváte zabezpečené relace konverzace, detekce opětovného přehrání nezaručuje detekci přehrání ve scénářích serverové farmy a při recyklaci procesu.</span><span class="sxs-lookup"><span data-stu-id="89db4-148">If you do not use secure conversation sessions, replay detection does not guarantee detecting replays in server farm scenarios and when the process is recycled.</span></span> <span data-ttu-id="89db4-149">To platí pro následující vazby poskytované systémem:</span><span class="sxs-lookup"><span data-stu-id="89db4-149">This applies to the following system-provided bindings:</span></span>  
  
- <span data-ttu-id="89db4-150"><xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="89db4-150"><xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
- <span data-ttu-id="89db4-151"><xref:System.ServiceModel.WSHttpBinding> s vlastností <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> nastavenou na `false`.</span><span class="sxs-lookup"><span data-stu-id="89db4-151"><xref:System.ServiceModel.WSHttpBinding> with the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property set to `false`.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="89db4-152">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="89db4-152">Compiling the Code</span></span>  
  
- <span data-ttu-id="89db4-153">Pro zkompilování kódu jsou vyžadovány následující obory názvů:</span><span class="sxs-lookup"><span data-stu-id="89db4-153">The following namespaces are required to compile the code:</span></span>  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.ServiceModel.Channels>  
  
## <a name="see-also"></a><span data-ttu-id="89db4-154">Viz také:</span><span class="sxs-lookup"><span data-stu-id="89db4-154">See also</span></span>

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [<span data-ttu-id="89db4-155">Zabezpečené konverzace a zabezpečené relace</span><span class="sxs-lookup"><span data-stu-id="89db4-155">Secure Conversations and Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)
- [<span data-ttu-id="89db4-156">\<localClientSettings></span><span class="sxs-lookup"><span data-stu-id="89db4-156">\<localClientSettings></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)
- [<span data-ttu-id="89db4-157">Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="89db4-157">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
