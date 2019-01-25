---
title: 'Postupy: Povolit zjišťování opakování zpráv'
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
ms.openlocfilehash: 8a5f693b98d1437ccf0c8a373fcb11aa96ee6191
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54653577"
---
# <a name="how-to-enable-message-replay-detection"></a><span data-ttu-id="a2d09-102">Postupy: Povolit zjišťování opakování zpráv</span><span class="sxs-lookup"><span data-stu-id="a2d09-102">How to: Enable Message Replay Detection</span></span>
<span data-ttu-id="a2d09-103">Opakování útoku nastane, pokud útočník zkopíruje datový proud zpráv mezi dvěma stranami a přehrává datový proud na jeden nebo více stran.</span><span class="sxs-lookup"><span data-stu-id="a2d09-103">A replay attack occurs when an attacker copies a stream of messages between two parties and replays the stream to one or more of the parties.</span></span> <span data-ttu-id="a2d09-104">Pokud zmírnit, počítače v souladu s útok bude zpracovávat datového proudu jako legitimní zprávy, což vede k celou řadu chybný důsledky, jako je například redundantní objednávky položku.</span><span class="sxs-lookup"><span data-stu-id="a2d09-104">Unless mitigated, the computers subject to the attack will process the stream as legitimate messages, resulting in a range of bad consequences, such as redundant orders of an item.</span></span>  
  
 <span data-ttu-id="a2d09-105">Další informace o zjišťování opakování zpráv najdete v tématu [zjišťování opakování zpráv](https://go.microsoft.com/fwlink/?LinkId=88536).</span><span class="sxs-lookup"><span data-stu-id="a2d09-105">For more information about message replay detection, see [Message Replay Detection](https://go.microsoft.com/fwlink/?LinkId=88536).</span></span>  
  
 <span data-ttu-id="a2d09-106">Následující postup ukazuje různé vlastnosti, které můžete použít k řízení rozpoznání opětovného přehrání pomocí Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="a2d09-106">The following procedure demonstrates various properties that you can use to control replay detection using Windows Communication Foundation (WCF).</span></span>  
  
### <a name="to-control-replay-detection-on-the-client-using-code"></a><span data-ttu-id="a2d09-107">K řízení rozpoznání opětovného přehrání na straně klienta pomocí kódu</span><span class="sxs-lookup"><span data-stu-id="a2d09-107">To control replay detection on the client using code</span></span>  
  
1.  <span data-ttu-id="a2d09-108">Vytvoření <xref:System.ServiceModel.Channels.SecurityBindingElement> používané <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="a2d09-108">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> to use in a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span> <span data-ttu-id="a2d09-109">Další informace najdete v tématu [jak: Vytvoření vlastní vazby pomocí elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="a2d09-109">For more information, see [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span> <span data-ttu-id="a2d09-110">Následující příklad používá <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> vytvořené pomocí <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> z <xref:System.ServiceModel.Channels.SecurityBindingElement> třídy.</span><span class="sxs-lookup"><span data-stu-id="a2d09-110">The following example uses a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> created with the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> of the <xref:System.ServiceModel.Channels.SecurityBindingElement> class.</span></span>  
  
2.  <span data-ttu-id="a2d09-111">Použití <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> vlastnost vrací odkaz <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> třídy a nastavte libovolné z následujících vlastností, podle potřeby:</span><span class="sxs-lookup"><span data-stu-id="a2d09-111">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> property to return a reference to the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> class and set any of the following properties, as appropriate:</span></span>  
  
    1.  <span data-ttu-id="a2d09-112">`DetectReplay`.</span><span class="sxs-lookup"><span data-stu-id="a2d09-112">`DetectReplay`.</span></span> <span data-ttu-id="a2d09-113">Logická hodnota.</span><span class="sxs-lookup"><span data-stu-id="a2d09-113">A Boolean value.</span></span> <span data-ttu-id="a2d09-114">To se řídí, zda klient by měl zjistit riziko ze serveru.</span><span class="sxs-lookup"><span data-stu-id="a2d09-114">This governs whether the client should detect replays from the server.</span></span> <span data-ttu-id="a2d09-115">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="a2d09-115">The default is `true`.</span></span>  
  
    2.  <span data-ttu-id="a2d09-116">`MaxClockSkew`.</span><span class="sxs-lookup"><span data-stu-id="a2d09-116">`MaxClockSkew`.</span></span> <span data-ttu-id="a2d09-117">A <xref:System.TimeSpan> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a2d09-117">A <xref:System.TimeSpan> value.</span></span> <span data-ttu-id="a2d09-118">Řídí, kolik času Nerovnoměrná distribuce mechanismus opakování může tolerovat možnost, mezi klientem a serverem.</span><span class="sxs-lookup"><span data-stu-id="a2d09-118">Governs how much time skew the replay mechanism can tolerate between the client and the server.</span></span> <span data-ttu-id="a2d09-119">Mechanismus zabezpečení, který prověří časové razítko odeslání a určuje, zda byl odeslán příliš daleko v minulosti.</span><span class="sxs-lookup"><span data-stu-id="a2d09-119">The security mechanism examines the time stamp sent and determines whether it was sent too far back in the past.</span></span> <span data-ttu-id="a2d09-120">Výchozí hodnota je 5 minut.</span><span class="sxs-lookup"><span data-stu-id="a2d09-120">The default is 5 minutes.</span></span>  
  
    3.  <span data-ttu-id="a2d09-121">`ReplayWindow`.</span><span class="sxs-lookup"><span data-stu-id="a2d09-121">`ReplayWindow`.</span></span> <span data-ttu-id="a2d09-122">A `TimeSpan` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a2d09-122">A `TimeSpan` value.</span></span> <span data-ttu-id="a2d09-123">To se řídí jak dlouho zpráva může existovat v síti, jakmile server odešle ho (prostřednictvím zprostředkovatelů) před dosažením klienta.</span><span class="sxs-lookup"><span data-stu-id="a2d09-123">This governs how long a message can live in the network after the server sends it (through intermediaries) before reaching the client.</span></span> <span data-ttu-id="a2d09-124">Klient sleduje podpisy některé zprávy odeslané v rámci nejnovější `ReplayWindow` za účelem rozpoznání opětovného přehrání.</span><span class="sxs-lookup"><span data-stu-id="a2d09-124">The client tracks the signatures of the messages sent within the latest `ReplayWindow` for the purposes of replay detection.</span></span>  
  
    4.  <span data-ttu-id="a2d09-125">`ReplayCacheSize`.</span><span class="sxs-lookup"><span data-stu-id="a2d09-125">`ReplayCacheSize`.</span></span> <span data-ttu-id="a2d09-126">Celočíselná hodnota.</span><span class="sxs-lookup"><span data-stu-id="a2d09-126">An integer value.</span></span> <span data-ttu-id="a2d09-127">Klient ukládá do mezipaměti podpisy zprávy.</span><span class="sxs-lookup"><span data-stu-id="a2d09-127">The client stores the signatures of the message in a cache.</span></span> <span data-ttu-id="a2d09-128">Toto nastavení určuje, kolik podpisy, které můžete ukládat do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="a2d09-128">This setting specifies how many signatures the cache can store.</span></span> <span data-ttu-id="a2d09-129">Pokud počet zpráv odeslaných v rámci poslední období opakování dosáhne limitu mezipaměti, nové zprávy jsou odmítnuta, až do nejstaršího uložené v mezipaměti podpisy dosažení časový limit.</span><span class="sxs-lookup"><span data-stu-id="a2d09-129">If the number of messages sent within the last replay window reaches the cache limit, new messages are rejected until the oldest cached signatures reach the time limit.</span></span> <span data-ttu-id="a2d09-130">Výchozí hodnota je 500000.</span><span class="sxs-lookup"><span data-stu-id="a2d09-130">The default is 500000.</span></span>  
  
### <a name="to-control-replay-detection-on-the-service-using-code"></a><span data-ttu-id="a2d09-131">K řízení rozpoznání opětovného přehrání na služby promocí kódu</span><span class="sxs-lookup"><span data-stu-id="a2d09-131">To control replay detection on the service using code</span></span>  
  
1.  <span data-ttu-id="a2d09-132">Vytvoření <xref:System.ServiceModel.Channels.SecurityBindingElement> používané <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="a2d09-132">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> to use in a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
2.  <span data-ttu-id="a2d09-133">Použití <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> vlastnost vrací odkaz <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> třídy a nastavit vlastnosti, jak je popsáno výše.</span><span class="sxs-lookup"><span data-stu-id="a2d09-133">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> property to return a reference to the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class, and set the properties as described previously.</span></span>  
  
### <a name="to-control-replay-detection-in-configuration-for-the-client-or-service"></a><span data-ttu-id="a2d09-134">K řízení rozpoznání opětovného přehrání v konfiguraci klienta nebo služby</span><span class="sxs-lookup"><span data-stu-id="a2d09-134">To control replay detection in configuration for the client or service</span></span>  
  
1.  <span data-ttu-id="a2d09-135">Vytvoření [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="a2d09-135">Create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
2.  <span data-ttu-id="a2d09-136">Vytvoření `<security>` elementu.</span><span class="sxs-lookup"><span data-stu-id="a2d09-136">Create a `<security>` element.</span></span>  
  
3.  <span data-ttu-id="a2d09-137">Vytvoření [ \<localClientSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md) nebo [ \<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md).</span><span class="sxs-lookup"><span data-stu-id="a2d09-137">Create a [\<localClientSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md) or [\<localServiceSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md).</span></span>  
  
4.  <span data-ttu-id="a2d09-138">Nastavte následující hodnoty atributu, podle potřeby: `detectReplays`, `maxClockSkew`, `replayWindow`, a `replayCacheSize`.</span><span class="sxs-lookup"><span data-stu-id="a2d09-138">Set the following attribute values, as appropriate: `detectReplays`, `maxClockSkew`, `replayWindow`, and `replayCacheSize`.</span></span> <span data-ttu-id="a2d09-139">Následující příklad nastaví atributy obou `<localServiceSettings>` a `<localClientSettings>` element:</span><span class="sxs-lookup"><span data-stu-id="a2d09-139">The following example sets the attributes of both a `<localServiceSettings>` and a `<localClientSettings>` element:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="a2d09-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="a2d09-140">Example</span></span>  
 <span data-ttu-id="a2d09-141">Následující příklad vytvoří <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> pomocí <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> metoda a nastaví vlastnosti opakování vazby.</span><span class="sxs-lookup"><span data-stu-id="a2d09-141">The following example creates a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> using the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> method, and sets the replay properties of the binding.</span></span>  
  
 [!code-csharp[c_ReplayDetection#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_replaydetection/cs/source.cs#1)]
 [!code-vb[c_ReplayDetection#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_replaydetection/vb/source.vb#1)]  
  
## <a name="scope-of-replay-message-security-only"></a><span data-ttu-id="a2d09-142">Rozsah opakování: Pouze zabezpečení zpráv</span><span class="sxs-lookup"><span data-stu-id="a2d09-142">Scope of Replay: Message Security Only</span></span>  
 <span data-ttu-id="a2d09-143">Všimněte si, že následující postupy platí pouze pro režim zabezpečených zpráv.</span><span class="sxs-lookup"><span data-stu-id="a2d09-143">Note that the following procedures apply only to Message security mode.</span></span> <span data-ttu-id="a2d09-144">Pro přenos a dopravu s přihlašovacími údaji zprávy režimy rozpoznat mechanismy přenosu riziko.</span><span class="sxs-lookup"><span data-stu-id="a2d09-144">For Transport and Transport with Message Credential modes, the transport mechanisms detect replays.</span></span>  
  
## <a name="secure-conversation-notes"></a><span data-ttu-id="a2d09-145">Zabezpečené konverzace poznámky</span><span class="sxs-lookup"><span data-stu-id="a2d09-145">Secure Conversation Notes</span></span>  
 <span data-ttu-id="a2d09-146">U vazeb, které umožňují zabezpečené konverzace můžete upravit tato nastavení pro kanál aplikace i pro zaváděcí vazbu zabezpečené konverzace.</span><span class="sxs-lookup"><span data-stu-id="a2d09-146">For bindings that enable secure conversations, you can adjust these settings both for the application channel as well as for the secure conversation bootstrap binding.</span></span> <span data-ttu-id="a2d09-147">Můžete například vypnout riziko pro kanál aplikace ale povolit jejich spuštění kanálu, který vytvoří zabezpečené konverzace.</span><span class="sxs-lookup"><span data-stu-id="a2d09-147">For example, you can turn off replays for the application channel but enable them for the bootstrap channel that establishes the secure conversation.</span></span>  
  
 <span data-ttu-id="a2d09-148">Pokud nepoužijete relací zabezpečené konverzace, rozpoznání opětovného přehrání nezaručuje zjišťování riziko v scénáře serveru farmy a když se proces recykluje.</span><span class="sxs-lookup"><span data-stu-id="a2d09-148">If you do not use secure conversation sessions, replay detection does not guarantee detecting replays in server farm scenarios and when the process is recycled.</span></span> <span data-ttu-id="a2d09-149">To platí pro následující vazeb poskytovaných systémem:</span><span class="sxs-lookup"><span data-stu-id="a2d09-149">This applies to the following system-provided bindings:</span></span>  
  
-   <span data-ttu-id="a2d09-150"><xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="a2d09-150"><xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
-   <span data-ttu-id="a2d09-151"><xref:System.ServiceModel.WSHttpBinding> s <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> nastavenou na `false`.</span><span class="sxs-lookup"><span data-stu-id="a2d09-151"><xref:System.ServiceModel.WSHttpBinding> with the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property set to `false`.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a2d09-152">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="a2d09-152">Compiling the Code</span></span>  
  
-   <span data-ttu-id="a2d09-153">Pro zkompilování kódu se vyžaduje následující obory názvů:</span><span class="sxs-lookup"><span data-stu-id="a2d09-153">The following namespaces are required to compile the code:</span></span>  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
## <a name="see-also"></a><span data-ttu-id="a2d09-154">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a2d09-154">See also</span></span>
- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [<span data-ttu-id="a2d09-155">Zabezpečené konverzace a zabezpečené relace</span><span class="sxs-lookup"><span data-stu-id="a2d09-155">Secure Conversations and Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)
- [<span data-ttu-id="a2d09-156">\<localClientSettings></span><span class="sxs-lookup"><span data-stu-id="a2d09-156">\<localClientSettings></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)
- [<span data-ttu-id="a2d09-157">Postupy: Vytvoření vlastní vazby pomocí elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="a2d09-157">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
