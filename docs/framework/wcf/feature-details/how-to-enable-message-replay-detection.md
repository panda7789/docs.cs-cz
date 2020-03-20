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
ms.openlocfilehash: 05bcddabf625e478616cce39f08b0ff8af282716
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184956"
---
# <a name="how-to-enable-message-replay-detection"></a><span data-ttu-id="bb493-102">Postupy: Povolení zjišťování opakování zpráv</span><span class="sxs-lookup"><span data-stu-id="bb493-102">How to: Enable Message Replay Detection</span></span>
<span data-ttu-id="bb493-103">K útoku při přehrání dojde, když útočník zkopíruje datový proud zpráv mezi dvěma stranami a přehraje datový proud na jednu nebo více stran.</span><span class="sxs-lookup"><span data-stu-id="bb493-103">A replay attack occurs when an attacker copies a stream of messages between two parties and replays the stream to one or more of the parties.</span></span> <span data-ttu-id="bb493-104">Pokud to nebude zmírněno, počítače, které jsou předmětem útoku, zpracují datový proud jako legitimní zprávy, což má za následek řadu chybných důsledků, jako jsou například nadbytečné objednávky položky.</span><span class="sxs-lookup"><span data-stu-id="bb493-104">Unless mitigated, the computers subject to the attack will process the stream as legitimate messages, resulting in a range of bad consequences, such as redundant orders of an item.</span></span>  
  
 <span data-ttu-id="bb493-105">Další informace o detekci opětovného přehrání zpráv naleznete v [tématu Detekce opětovného přehrání zpráv](https://docs.microsoft.com/previous-versions/msp-n-p/ff649371(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="bb493-105">For more information about message replay detection, see [Message Replay Detection](https://docs.microsoft.com/previous-versions/msp-n-p/ff649371(v=pandp.10)).</span></span>  
  
 <span data-ttu-id="bb493-106">Následující postup ukazuje různé vlastnosti, které můžete použít k řízení detekce přehrání pomocí Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="bb493-106">The following procedure demonstrates various properties that you can use to control replay detection using Windows Communication Foundation (WCF).</span></span>  
  
### <a name="to-control-replay-detection-on-the-client-using-code"></a><span data-ttu-id="bb493-107">Řízení detekce přehrání na straně klienta pomocí kódu</span><span class="sxs-lookup"><span data-stu-id="bb493-107">To control replay detection on the client using code</span></span>  
  
1. <span data-ttu-id="bb493-108">Vytvořte <xref:System.ServiceModel.Channels.SecurityBindingElement> a pro <xref:System.ServiceModel.Channels.CustomBinding>použití v .</span><span class="sxs-lookup"><span data-stu-id="bb493-108">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> to use in a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span> <span data-ttu-id="bb493-109">Další informace naleznete v [tématu How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="bb493-109">For more information, see [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span> <span data-ttu-id="bb493-110">Následující příklad používá <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> vytvořené <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> s <xref:System.ServiceModel.Channels.SecurityBindingElement> třídy.</span><span class="sxs-lookup"><span data-stu-id="bb493-110">The following example uses a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> created with the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> of the <xref:System.ServiceModel.Channels.SecurityBindingElement> class.</span></span>  
  
2. <span data-ttu-id="bb493-111">Pomocí <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> vlastnosti vrátíte odkaz <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> na třídu a podle potřeby nastavte některou z následujících vlastností:</span><span class="sxs-lookup"><span data-stu-id="bb493-111">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> property to return a reference to the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> class and set any of the following properties, as appropriate:</span></span>  
  
    1. <span data-ttu-id="bb493-112">`DetectReplay`.</span><span class="sxs-lookup"><span data-stu-id="bb493-112">`DetectReplay`.</span></span> <span data-ttu-id="bb493-113">Logická hodnota</span><span class="sxs-lookup"><span data-stu-id="bb493-113">A Boolean value.</span></span> <span data-ttu-id="bb493-114">To určuje, zda by měl klient zjistit záznamy ze serveru.</span><span class="sxs-lookup"><span data-stu-id="bb493-114">This governs whether the client should detect replays from the server.</span></span> <span data-ttu-id="bb493-115">Výchozí formát je `true`.</span><span class="sxs-lookup"><span data-stu-id="bb493-115">The default is `true`.</span></span>  
  
    2. <span data-ttu-id="bb493-116">`MaxClockSkew`.</span><span class="sxs-lookup"><span data-stu-id="bb493-116">`MaxClockSkew`.</span></span> <span data-ttu-id="bb493-117">Hodnota. <xref:System.TimeSpan></span><span class="sxs-lookup"><span data-stu-id="bb493-117">A <xref:System.TimeSpan> value.</span></span> <span data-ttu-id="bb493-118">Určuje, kolik času zkosení mechanismus přehrání může tolerovat mezi klientem a serverem.</span><span class="sxs-lookup"><span data-stu-id="bb493-118">Governs how much time skew the replay mechanism can tolerate between the client and the server.</span></span> <span data-ttu-id="bb493-119">Bezpečnostní mechanismus zkontroluje odeslané časové razítko a určí, zda bylo odesláno příliš daleko v minulosti.</span><span class="sxs-lookup"><span data-stu-id="bb493-119">The security mechanism examines the time stamp sent and determines whether it was sent too far back in the past.</span></span> <span data-ttu-id="bb493-120">Výchozí hodnota je 5 minut.</span><span class="sxs-lookup"><span data-stu-id="bb493-120">The default is 5 minutes.</span></span>  
  
    3. <span data-ttu-id="bb493-121">`ReplayWindow`.</span><span class="sxs-lookup"><span data-stu-id="bb493-121">`ReplayWindow`.</span></span> <span data-ttu-id="bb493-122">Hodnota. `TimeSpan`</span><span class="sxs-lookup"><span data-stu-id="bb493-122">A `TimeSpan` value.</span></span> <span data-ttu-id="bb493-123">To určuje, jak dlouho může zpráva žít v síti poté, co ji server odešle (prostřednictvím zprostředkovatelů) před dosažením klienta.</span><span class="sxs-lookup"><span data-stu-id="bb493-123">This governs how long a message can live in the network after the server sends it (through intermediaries) before reaching the client.</span></span> <span data-ttu-id="bb493-124">Klient sleduje podpisy zpráv odeslaných nejpozději `ReplayWindow` pro účely detekce přehrání.</span><span class="sxs-lookup"><span data-stu-id="bb493-124">The client tracks the signatures of the messages sent within the latest `ReplayWindow` for the purposes of replay detection.</span></span>  
  
    4. <span data-ttu-id="bb493-125">`ReplayCacheSize`.</span><span class="sxs-lookup"><span data-stu-id="bb493-125">`ReplayCacheSize`.</span></span> <span data-ttu-id="bb493-126">Hodnota celého čísla.</span><span class="sxs-lookup"><span data-stu-id="bb493-126">An integer value.</span></span> <span data-ttu-id="bb493-127">Klient ukládá podpisy zprávy do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="bb493-127">The client stores the signatures of the message in a cache.</span></span> <span data-ttu-id="bb493-128">Toto nastavení určuje, kolik podpisů může mezipaměť uložit.</span><span class="sxs-lookup"><span data-stu-id="bb493-128">This setting specifies how many signatures the cache can store.</span></span> <span data-ttu-id="bb493-129">Pokud počet zpráv odeslaných v posledním okně přehrávání dosáhne limitu mezipaměti, budou nové zprávy odmítnuty, dokud nejstarší podpisy uložené v mezipaměti nedosáhnou časového limitu.</span><span class="sxs-lookup"><span data-stu-id="bb493-129">If the number of messages sent within the last replay window reaches the cache limit, new messages are rejected until the oldest cached signatures reach the time limit.</span></span> <span data-ttu-id="bb493-130">Výchozí hodnota je 500000.</span><span class="sxs-lookup"><span data-stu-id="bb493-130">The default is 500000.</span></span>  
  
### <a name="to-control-replay-detection-on-the-service-using-code"></a><span data-ttu-id="bb493-131">Řízení detekce přehrání ve službě pomocí kódu</span><span class="sxs-lookup"><span data-stu-id="bb493-131">To control replay detection on the service using code</span></span>  
  
1. <span data-ttu-id="bb493-132">Vytvořte <xref:System.ServiceModel.Channels.SecurityBindingElement> a pro <xref:System.ServiceModel.Channels.CustomBinding>použití v .</span><span class="sxs-lookup"><span data-stu-id="bb493-132">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> to use in a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
2. <span data-ttu-id="bb493-133">Pomocí <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> vlastnosti vrátit odkaz <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> na třídu a nastavit vlastnosti, jak je popsáno výše.</span><span class="sxs-lookup"><span data-stu-id="bb493-133">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> property to return a reference to the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class, and set the properties as described previously.</span></span>  
  
### <a name="to-control-replay-detection-in-configuration-for-the-client-or-service"></a><span data-ttu-id="bb493-134">Řízení detekce přehrání v konfiguraci pro klienta nebo službu</span><span class="sxs-lookup"><span data-stu-id="bb493-134">To control replay detection in configuration for the client or service</span></span>  
  
1. <span data-ttu-id="bb493-135">Vytvořte [ \<vlastní vazbu>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="bb493-135">Create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
2. <span data-ttu-id="bb493-136">Vytvořte `<security>` prvek.</span><span class="sxs-lookup"><span data-stu-id="bb493-136">Create a `<security>` element.</span></span>  
  
3. <span data-ttu-id="bb493-137">Vytvořte [ \<>nastavení localClientSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md) nebo [ \<localServiceSettings ](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md).</span><span class="sxs-lookup"><span data-stu-id="bb493-137">Create a [\<localClientSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md) or [\<localServiceSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md).</span></span>  
  
4. <span data-ttu-id="bb493-138">Podle potřeby nastavte následující hodnoty `detectReplays` `maxClockSkew`atributů: , , `replayWindow`a `replayCacheSize`.</span><span class="sxs-lookup"><span data-stu-id="bb493-138">Set the following attribute values, as appropriate: `detectReplays`, `maxClockSkew`, `replayWindow`, and `replayCacheSize`.</span></span> <span data-ttu-id="bb493-139">Následující příklad nastaví atributy `<localServiceSettings>` prvku `<localClientSettings>` a prvku a prvku:</span><span class="sxs-lookup"><span data-stu-id="bb493-139">The following example sets the attributes of both a `<localServiceSettings>` and a `<localClientSettings>` element:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="bb493-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="bb493-140">Example</span></span>  
 <span data-ttu-id="bb493-141">Následující příklad vytvoří <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> pomocí <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> metody a nastaví vlastnosti přehrání vazby.</span><span class="sxs-lookup"><span data-stu-id="bb493-141">The following example creates a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> using the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> method, and sets the replay properties of the binding.</span></span>  
  
 [!code-csharp[c_ReplayDetection#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_replaydetection/cs/source.cs#1)]
 [!code-vb[c_ReplayDetection#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_replaydetection/vb/source.vb#1)]  
  
## <a name="scope-of-replay-message-security-only"></a><span data-ttu-id="bb493-142">Rozsah přehrání: Pouze zabezpečení zpráv</span><span class="sxs-lookup"><span data-stu-id="bb493-142">Scope of Replay: Message Security Only</span></span>  
 <span data-ttu-id="bb493-143">Všimněte si, že následující postupy platí pouze pro režim zabezpečení zprávy.</span><span class="sxs-lookup"><span data-stu-id="bb493-143">Note that the following procedures apply only to Message security mode.</span></span> <span data-ttu-id="bb493-144">Pro přenos a přenos s režimy pověření zprávy, mechanismy přenosu rozpoznat záznamy.</span><span class="sxs-lookup"><span data-stu-id="bb493-144">For Transport and Transport with Message Credential modes, the transport mechanisms detect replays.</span></span>  
  
## <a name="secure-conversation-notes"></a><span data-ttu-id="bb493-145">Zabezpečené poznámky k konverzaci</span><span class="sxs-lookup"><span data-stu-id="bb493-145">Secure Conversation Notes</span></span>  
 <span data-ttu-id="bb493-146">Pro vazby, které umožňují zabezpečené konverzace, můžete upravit tato nastavení jak pro kanál aplikace, tak pro zabezpečené konverzace bootstrap vazby.</span><span class="sxs-lookup"><span data-stu-id="bb493-146">For bindings that enable secure conversations, you can adjust these settings both for the application channel as well as for the secure conversation bootstrap binding.</span></span> <span data-ttu-id="bb493-147">Můžete například vypnout záznamy pro aplikační kanál, ale povolit je pro zaváděcí kanál, který vytváří zabezpečenou konverzaci.</span><span class="sxs-lookup"><span data-stu-id="bb493-147">For example, you can turn off replays for the application channel but enable them for the bootstrap channel that establishes the secure conversation.</span></span>  
  
 <span data-ttu-id="bb493-148">Pokud nepoužíváte zabezpečené relace konverzace, zjišťování přehrání nezaručuje zjišťování záznamů ve scénářích serverové farmy a při recyklaci procesu.</span><span class="sxs-lookup"><span data-stu-id="bb493-148">If you do not use secure conversation sessions, replay detection does not guarantee detecting replays in server farm scenarios and when the process is recycled.</span></span> <span data-ttu-id="bb493-149">To platí pro následující systémově poskytované vazby:</span><span class="sxs-lookup"><span data-stu-id="bb493-149">This applies to the following system-provided bindings:</span></span>  
  
- <span data-ttu-id="bb493-150"><xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="bb493-150"><xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
- <span data-ttu-id="bb493-151"><xref:System.ServiceModel.WSHttpBinding>s <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> vlastností `false`nastavenou na .</span><span class="sxs-lookup"><span data-stu-id="bb493-151"><xref:System.ServiceModel.WSHttpBinding> with the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property set to `false`.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bb493-152">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="bb493-152">Compiling the Code</span></span>  
  
- <span data-ttu-id="bb493-153">Ke kompilaci kódu jsou vyžadovány následující obory názvů:</span><span class="sxs-lookup"><span data-stu-id="bb493-153">The following namespaces are required to compile the code:</span></span>  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.ServiceModel.Channels>  
  
## <a name="see-also"></a><span data-ttu-id="bb493-154">Viz také</span><span class="sxs-lookup"><span data-stu-id="bb493-154">See also</span></span>

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [<span data-ttu-id="bb493-155">Zabezpečené konverzace a zabezpečené relace</span><span class="sxs-lookup"><span data-stu-id="bb493-155">Secure Conversations and Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)
- [<span data-ttu-id="bb493-156">\<localClientSettings></span><span class="sxs-lookup"><span data-stu-id="bb493-156">\<localClientSettings></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)
- [<span data-ttu-id="bb493-157">Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="bb493-157">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
