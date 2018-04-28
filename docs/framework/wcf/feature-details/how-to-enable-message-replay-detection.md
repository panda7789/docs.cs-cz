---
title: 'Postupy: Povolení zjišťování opakování zpráv'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF security
- replay detection [WCF]
- WCF, custom bindings
- WCF, security
ms.assetid: 8b847e91-69a3-49e1-9e5f-0c455e50d804
caps.latest.revision: 10
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 55cd4b928c640f506e058f6a441189842bc9b8a3
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="how-to-enable-message-replay-detection"></a><span data-ttu-id="13fb4-102">Postupy: Povolení zjišťování opakování zpráv</span><span class="sxs-lookup"><span data-stu-id="13fb4-102">How to: Enable Message Replay Detection</span></span>
<span data-ttu-id="13fb4-103">Opakování útoku nastane, když útočník zkopíruje datového proudu zpráv mezi dvěma účastníky a replays datový proud na jeden nebo více stran.</span><span class="sxs-lookup"><span data-stu-id="13fb4-103">A replay attack occurs when an attacker copies a stream of messages between two parties and replays the stream to one or more of the parties.</span></span> <span data-ttu-id="13fb4-104">Pokud omezeny, budou počítače podřízené útoku zpracovat datového proudu jako legitimní zprávy, což vede k řadu chybný důsledky, jako je například redundantní objednávky položky.</span><span class="sxs-lookup"><span data-stu-id="13fb4-104">Unless mitigated, the computers subject to the attack will process the stream as legitimate messages, resulting in a range of bad consequences, such as redundant orders of an item.</span></span>  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="13fb4-105"> zpráva rozpoznání opětovného přehrání najdete v tématu [zjišťování opakování zpráv](http://go.microsoft.com/fwlink/?LinkId=88536).</span><span class="sxs-lookup"><span data-stu-id="13fb4-105"> message replay detection, see [Message Replay Detection](http://go.microsoft.com/fwlink/?LinkId=88536).</span></span>  
  
 <span data-ttu-id="13fb4-106">Následující postup ukazuje různé vlastnosti, které můžete použít k řízení opakování použitím zjišťování [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="13fb4-106">The following procedure demonstrates various properties that you can use to control replay detection using [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span>  
  
### <a name="to-control-replay-detection-on-the-client-using-code"></a><span data-ttu-id="13fb4-107">K řízení rozpoznání opětovného přehrání na straně klienta pomocí kódu</span><span class="sxs-lookup"><span data-stu-id="13fb4-107">To control replay detection on the client using code</span></span>  
  
1.  <span data-ttu-id="13fb4-108">Vytvoření <xref:System.ServiceModel.Channels.SecurityBindingElement> pro použití v <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="13fb4-108">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> to use in a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span> <span data-ttu-id="13fb4-109">Další informace najdete v tématu [postupy: vytvoření vlastní vazby pomocí elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="13fb4-109">For more information, see [How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span> <span data-ttu-id="13fb4-110">Následující příklad používá <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> vytvořené pomocí <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> z <xref:System.ServiceModel.Channels.SecurityBindingElement> třídy.</span><span class="sxs-lookup"><span data-stu-id="13fb4-110">The following example uses a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> created with the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> of the <xref:System.ServiceModel.Channels.SecurityBindingElement> class.</span></span>  
  
2.  <span data-ttu-id="13fb4-111">Použití <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> vlastnost vrací odkaz na <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> třídy a podle potřeby nastavte následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="13fb4-111">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> property to return a reference to the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> class and set any of the following properties, as appropriate:</span></span>  
  
    1.  <span data-ttu-id="13fb4-112">`DetectReplay`.</span><span class="sxs-lookup"><span data-stu-id="13fb4-112">`DetectReplay`.</span></span> <span data-ttu-id="13fb4-113">Logická hodnota.</span><span class="sxs-lookup"><span data-stu-id="13fb4-113">A Boolean value.</span></span> <span data-ttu-id="13fb4-114">To řídí, zda klient by měl zjistit opětovná přehrání ze serveru.</span><span class="sxs-lookup"><span data-stu-id="13fb4-114">This governs whether the client should detect replays from the server.</span></span> <span data-ttu-id="13fb4-115">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="13fb4-115">The default is `true`.</span></span>  
  
    2.  <span data-ttu-id="13fb4-116">`MaxClockSkew`.</span><span class="sxs-lookup"><span data-stu-id="13fb4-116">`MaxClockSkew`.</span></span> <span data-ttu-id="13fb4-117">A <xref:System.TimeSpan> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="13fb4-117">A <xref:System.TimeSpan> value.</span></span> <span data-ttu-id="13fb4-118">Řídí, kolik času zkosení mechanismus opakování tolerovat mezi klientem a serverem.</span><span class="sxs-lookup"><span data-stu-id="13fb4-118">Governs how much time skew the replay mechanism can tolerate between the client and the server.</span></span> <span data-ttu-id="13fb4-119">Tento mechanismus zabezpečení prověří časové razítko odesílají a určuje, zda byl odeslán příliš daleko zpět v minulosti.</span><span class="sxs-lookup"><span data-stu-id="13fb4-119">The security mechanism examines the time stamp sent and determines whether it was sent too far back in the past.</span></span> <span data-ttu-id="13fb4-120">Výchozí hodnota je 5 minut.</span><span class="sxs-lookup"><span data-stu-id="13fb4-120">The default is 5 minutes.</span></span>  
  
    3.  <span data-ttu-id="13fb4-121">`ReplayWindow`.</span><span class="sxs-lookup"><span data-stu-id="13fb4-121">`ReplayWindow`.</span></span> <span data-ttu-id="13fb4-122">A `TimeSpan` hodnotu.</span><span class="sxs-lookup"><span data-stu-id="13fb4-122">A `TimeSpan` value.</span></span> <span data-ttu-id="13fb4-123">To řídí, jak dlouho zprávu můžete za provozu v síti po server odešle (přes prostředníci) dříve, než dorazila klienta.</span><span class="sxs-lookup"><span data-stu-id="13fb4-123">This governs how long a message can live in the network after the server sends it (through intermediaries) before reaching the client.</span></span> <span data-ttu-id="13fb4-124">Klient sleduje podpis zprávy odeslané v rámci nejnovější `ReplayWindow` pro účely rozpoznání opětovného přehrání.</span><span class="sxs-lookup"><span data-stu-id="13fb4-124">The client tracks the signatures of the messages sent within the latest `ReplayWindow` for the purposes of replay detection.</span></span>  
  
    4.  <span data-ttu-id="13fb4-125">`ReplayCacheSize`.</span><span class="sxs-lookup"><span data-stu-id="13fb4-125">`ReplayCacheSize`.</span></span> <span data-ttu-id="13fb4-126">Celočíselná hodnota.</span><span class="sxs-lookup"><span data-stu-id="13fb4-126">An integer value.</span></span> <span data-ttu-id="13fb4-127">Klient ukládá do mezipaměti podpisů zprávy.</span><span class="sxs-lookup"><span data-stu-id="13fb4-127">The client stores the signatures of the message in a cache.</span></span> <span data-ttu-id="13fb4-128">Toto nastavení určuje, kolik podpisy může ukládat do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="13fb4-128">This setting specifies how many signatures the cache can store.</span></span> <span data-ttu-id="13fb4-129">Pokud počet zpráv odeslaných v rámci poslední období opakování dosáhne limitu mezipaměti, jsou odmítnuta nové zprávy, dokud nejstarší uložené v mezipaměti podpisy nezobrazí časový limit.</span><span class="sxs-lookup"><span data-stu-id="13fb4-129">If the number of messages sent within the last replay window reaches the cache limit, new messages are rejected until the oldest cached signatures reach the time limit.</span></span> <span data-ttu-id="13fb4-130">Výchozí hodnota je 500000.</span><span class="sxs-lookup"><span data-stu-id="13fb4-130">The default is 500000.</span></span>  
  
### <a name="to-control-replay-detection-on-the-service-using-code"></a><span data-ttu-id="13fb4-131">K řízení rozpoznání opětovného přehrání na úrovni služby pomocí kódu</span><span class="sxs-lookup"><span data-stu-id="13fb4-131">To control replay detection on the service using code</span></span>  
  
1.  <span data-ttu-id="13fb4-132">Vytvoření <xref:System.ServiceModel.Channels.SecurityBindingElement> pro použití v <xref:System.ServiceModel.Channels.CustomBinding>.</span><span class="sxs-lookup"><span data-stu-id="13fb4-132">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> to use in a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
2.  <span data-ttu-id="13fb4-133">Použití <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> vlastnost vrací odkaz na <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> třídy a nastavte vlastnosti, jak je popsáno výše.</span><span class="sxs-lookup"><span data-stu-id="13fb4-133">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> property to return a reference to the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class, and set the properties as described previously.</span></span>  
  
### <a name="to-control-replay-detection-in-configuration-for-the-client-or-service"></a><span data-ttu-id="13fb4-134">K řízení rozpoznání opětovného přehrání v konfiguraci pro klienta nebo služby</span><span class="sxs-lookup"><span data-stu-id="13fb4-134">To control replay detection in configuration for the client or service</span></span>  
  
1.  <span data-ttu-id="13fb4-135">Vytvoření [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span><span class="sxs-lookup"><span data-stu-id="13fb4-135">Create a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
2.  <span data-ttu-id="13fb4-136">Vytvoření `<security>` elementu.</span><span class="sxs-lookup"><span data-stu-id="13fb4-136">Create a `<security>` element.</span></span>  
  
3.  <span data-ttu-id="13fb4-137">Vytvoření [ \<localClientSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md) nebo [ \<localServiceSettings >](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md).</span><span class="sxs-lookup"><span data-stu-id="13fb4-137">Create a [\<localClientSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md) or [\<localServiceSettings>](../../../../docs/framework/configure-apps/file-schema/wcf/localservicesettings-element.md).</span></span>  
  
4.  <span data-ttu-id="13fb4-138">Podle potřeby nastavte následující hodnoty atributu: `detectReplays`, `maxClockSkew`, `replayWindow`, a `replayCacheSize`.</span><span class="sxs-lookup"><span data-stu-id="13fb4-138">Set the following attribute values, as appropriate: `detectReplays`, `maxClockSkew`, `replayWindow`, and `replayCacheSize`.</span></span> <span data-ttu-id="13fb4-139">Následující příklad nastaví atributy i `<localServiceSettings>` a `<localClientSettings>` element:</span><span class="sxs-lookup"><span data-stu-id="13fb4-139">The following example sets the attributes of both a `<localServiceSettings>` and a `<localClientSettings>` element:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="13fb4-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="13fb4-140">Example</span></span>  
 <span data-ttu-id="13fb4-141">Následující příklad vytvoří <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> pomocí <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> metoda a nastaví vlastnosti opakování vazby.</span><span class="sxs-lookup"><span data-stu-id="13fb4-141">The following example creates a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> using the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> method, and sets the replay properties of the binding.</span></span>  
  
 [!code-csharp[c_ReplayDetection#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_replaydetection/cs/source.cs#1)]
 [!code-vb[c_ReplayDetection#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_replaydetection/vb/source.vb#1)]  
  
## <a name="scope-of-replay-message-security-only"></a><span data-ttu-id="13fb4-142">Rozsah opětovného přehrání: pouze zabezpečení zpráv</span><span class="sxs-lookup"><span data-stu-id="13fb4-142">Scope of Replay: Message Security Only</span></span>  
 <span data-ttu-id="13fb4-143">Všimněte si, že následující postupy platí pouze pro režim zabezpečení zprávy.</span><span class="sxs-lookup"><span data-stu-id="13fb4-143">Note that the following procedures apply only to Message security mode.</span></span> <span data-ttu-id="13fb4-144">Mechanismy přenos pro přenos a přenos s pověřením zpráv režimy rozpoznat opětovná přehrání.</span><span class="sxs-lookup"><span data-stu-id="13fb4-144">For Transport and Transport with Message Credential modes, the transport mechanisms detect replays.</span></span>  
  
## <a name="secure-conversation-notes"></a><span data-ttu-id="13fb4-145">Zabezpečené konverzace poznámky</span><span class="sxs-lookup"><span data-stu-id="13fb4-145">Secure Conversation Notes</span></span>  
 <span data-ttu-id="13fb4-146">U vazeb, které umožňují zabezpečené konverzace můžete upravit tato nastavení pro aplikace kanál i pro vazbu bootstrap zabezpečené konverzaci.</span><span class="sxs-lookup"><span data-stu-id="13fb4-146">For bindings that enable secure conversations, you can adjust these settings both for the application channel as well as for the secure conversation bootstrap binding.</span></span> <span data-ttu-id="13fb4-147">Například můžete vypnout opětovná přehrání pro kanál aplikace ale mohly pro spouštěcí kanál, který stanoví k zabezpečené konverzaci.</span><span class="sxs-lookup"><span data-stu-id="13fb4-147">For example, you can turn off replays for the application channel but enable them for the bootstrap channel that establishes the secure conversation.</span></span>  
  
 <span data-ttu-id="13fb4-148">Pokud nepoužijete zabezpečené konverzaci relací, rozpoznání opětovného přehrání nezaručuje zjišťování opětovná přehrání v scénáře serveru farmy a když se proces recykluje.</span><span class="sxs-lookup"><span data-stu-id="13fb4-148">If you do not use secure conversation sessions, replay detection does not guarantee detecting replays in server farm scenarios and when the process is recycled.</span></span> <span data-ttu-id="13fb4-149">To platí pro následující vazby poskytované systémem:</span><span class="sxs-lookup"><span data-stu-id="13fb4-149">This applies to the following system-provided bindings:</span></span>  
  
-   <span data-ttu-id="13fb4-150"><xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="13fb4-150"><xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
-   <span data-ttu-id="13fb4-151"><xref:System.ServiceModel.WSHttpBinding> pomocí <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> vlastnost nastavena na hodnotu `false`.</span><span class="sxs-lookup"><span data-stu-id="13fb4-151"><xref:System.ServiceModel.WSHttpBinding> with the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property set to `false`.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="13fb4-152">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="13fb4-152">Compiling the Code</span></span>  
  
-   <span data-ttu-id="13fb4-153">Následující obory názvů jsou nezbytné pro kompilaci kódu:</span><span class="sxs-lookup"><span data-stu-id="13fb4-153">The following namespaces are required to compile the code:</span></span>  
  
-   <xref:System>  
  
-   <xref:System.ServiceModel>  
  
-   <xref:System.ServiceModel.Channels>  
  
## <a name="see-also"></a><span data-ttu-id="13fb4-154">Viz také</span><span class="sxs-lookup"><span data-stu-id="13fb4-154">See Also</span></span>  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 [<span data-ttu-id="13fb4-155">Zabezpečené konverzace a zabezpečené relace</span><span class="sxs-lookup"><span data-stu-id="13fb4-155">Secure Conversations and Secure Sessions</span></span>](../../../../docs/framework/wcf/feature-details/secure-conversations-and-secure-sessions.md)  
 [<span data-ttu-id="13fb4-156">\<localClientSettings ></span><span class="sxs-lookup"><span data-stu-id="13fb4-156">\<localClientSettings></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/localclientsettings-element.md)  
 [<span data-ttu-id="13fb4-157">Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="13fb4-157">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
