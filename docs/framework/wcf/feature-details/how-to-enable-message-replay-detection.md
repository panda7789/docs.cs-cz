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
ms.openlocfilehash: bf45b39f59e2fe38fec88d1fac23ab824c009546
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597082"
---
# <a name="how-to-enable-message-replay-detection"></a><span data-ttu-id="5e35b-102">Postupy: Povolení zjišťování opakování zpráv</span><span class="sxs-lookup"><span data-stu-id="5e35b-102">How to: Enable Message Replay Detection</span></span>
<span data-ttu-id="5e35b-103">K útoku opakovaného přehrání dojde, když útočník zkopíruje datový proud zpráv mezi dvěma stranami a přehraje datový proud na jednu nebo více stran.</span><span class="sxs-lookup"><span data-stu-id="5e35b-103">A replay attack occurs when an attacker copies a stream of messages between two parties and replays the stream to one or more of the parties.</span></span> <span data-ttu-id="5e35b-104">V případě, že počítače, které jsou předmětem útoku, zpracuje datový proud jako legitimní zprávy, což vede k celé řadě špatných důsledků, jako je například redundantní objednávka položky.</span><span class="sxs-lookup"><span data-stu-id="5e35b-104">Unless mitigated, the computers subject to the attack will process the stream as legitimate messages, resulting in a range of bad consequences, such as redundant orders of an item.</span></span>  
  
 <span data-ttu-id="5e35b-105">Další informace o detekci opětovného přehrání zpráv najdete v tématu zjištění opětovného [přehrání zprávy](https://docs.microsoft.com/previous-versions/msp-n-p/ff649371(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="5e35b-105">For more information about message replay detection, see [Message Replay Detection](https://docs.microsoft.com/previous-versions/msp-n-p/ff649371(v=pandp.10)).</span></span>  
  
 <span data-ttu-id="5e35b-106">Následující postup ukazuje různé vlastnosti, které lze použít k řízení detekce přehrání pomocí Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="5e35b-106">The following procedure demonstrates various properties that you can use to control replay detection using Windows Communication Foundation (WCF).</span></span>  
  
### <a name="to-control-replay-detection-on-the-client-using-code"></a><span data-ttu-id="5e35b-107">Řízení zjišťování opakování v klientovi pomocí kódu</span><span class="sxs-lookup"><span data-stu-id="5e35b-107">To control replay detection on the client using code</span></span>  
  
1. <span data-ttu-id="5e35b-108">Vytvořte <xref:System.ServiceModel.Channels.SecurityBindingElement> pro použití v <xref:System.ServiceModel.Channels.CustomBinding> .</span><span class="sxs-lookup"><span data-stu-id="5e35b-108">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> to use in a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span> <span data-ttu-id="5e35b-109">Další informace najdete v tématu [Postup: Vytvoření vlastní vazby pomocí SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span><span class="sxs-lookup"><span data-stu-id="5e35b-109">For more information, see [How to: Create a Custom Binding Using the SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md).</span></span> <span data-ttu-id="5e35b-110">V následujícím příkladu je použita <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> Třída vytvořená s <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> <xref:System.ServiceModel.Channels.SecurityBindingElement> třídou.</span><span class="sxs-lookup"><span data-stu-id="5e35b-110">The following example uses a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> created with the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> of the <xref:System.ServiceModel.Channels.SecurityBindingElement> class.</span></span>  
  
2. <span data-ttu-id="5e35b-111">Pomocí <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> vlastnosti vraťte odkaz na <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> třídu a podle potřeby nastavte libovolné z následujících vlastností:</span><span class="sxs-lookup"><span data-stu-id="5e35b-111">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A> property to return a reference to the <xref:System.ServiceModel.Channels.LocalClientSecuritySettings> class and set any of the following properties, as appropriate:</span></span>  
  
    1. <span data-ttu-id="5e35b-112">`DetectReplay`.</span><span class="sxs-lookup"><span data-stu-id="5e35b-112">`DetectReplay`.</span></span> <span data-ttu-id="5e35b-113">Logická hodnota</span><span class="sxs-lookup"><span data-stu-id="5e35b-113">A Boolean value.</span></span> <span data-ttu-id="5e35b-114">Tím se určuje, zda má klient detekovat hry ze serveru.</span><span class="sxs-lookup"><span data-stu-id="5e35b-114">This governs whether the client should detect replays from the server.</span></span> <span data-ttu-id="5e35b-115">Výchozí formát je `true`.</span><span class="sxs-lookup"><span data-stu-id="5e35b-115">The default is `true`.</span></span>  
  
    2. <span data-ttu-id="5e35b-116">`MaxClockSkew`.</span><span class="sxs-lookup"><span data-stu-id="5e35b-116">`MaxClockSkew`.</span></span> <span data-ttu-id="5e35b-117"><xref:System.TimeSpan>Hodnota.</span><span class="sxs-lookup"><span data-stu-id="5e35b-117">A <xref:System.TimeSpan> value.</span></span> <span data-ttu-id="5e35b-118">Určuje, kolik času se má v případě, že je možné mezi klientem a serverem tolerovat mechanismus opakovaného přehrávání.</span><span class="sxs-lookup"><span data-stu-id="5e35b-118">Governs how much time skew the replay mechanism can tolerate between the client and the server.</span></span> <span data-ttu-id="5e35b-119">Mechanismus zabezpečení prověřuje odeslané časové razítko a určí, zda byl v minulosti odeslán příliš daleko zpátky.</span><span class="sxs-lookup"><span data-stu-id="5e35b-119">The security mechanism examines the time stamp sent and determines whether it was sent too far back in the past.</span></span> <span data-ttu-id="5e35b-120">Výchozí hodnota je 5 minut.</span><span class="sxs-lookup"><span data-stu-id="5e35b-120">The default is 5 minutes.</span></span>  
  
    3. <span data-ttu-id="5e35b-121">`ReplayWindow`.</span><span class="sxs-lookup"><span data-stu-id="5e35b-121">`ReplayWindow`.</span></span> <span data-ttu-id="5e35b-122">`TimeSpan`Hodnota.</span><span class="sxs-lookup"><span data-stu-id="5e35b-122">A `TimeSpan` value.</span></span> <span data-ttu-id="5e35b-123">To určuje, jak dlouho může zpráva v síti fungovat poté, co ji server pošle (prostřednictvím zprostředkovatelů) před tím, než se dopustí klientovi.</span><span class="sxs-lookup"><span data-stu-id="5e35b-123">This governs how long a message can live in the network after the server sends it (through intermediaries) before reaching the client.</span></span> <span data-ttu-id="5e35b-124">Klient sleduje podpisy zpráv odeslaných v rámci nejnovějších `ReplayWindow` pro účely detekce opětovného přehrání.</span><span class="sxs-lookup"><span data-stu-id="5e35b-124">The client tracks the signatures of the messages sent within the latest `ReplayWindow` for the purposes of replay detection.</span></span>  
  
    4. <span data-ttu-id="5e35b-125">`ReplayCacheSize`.</span><span class="sxs-lookup"><span data-stu-id="5e35b-125">`ReplayCacheSize`.</span></span> <span data-ttu-id="5e35b-126">Celočíselná hodnota.</span><span class="sxs-lookup"><span data-stu-id="5e35b-126">An integer value.</span></span> <span data-ttu-id="5e35b-127">Klient ukládá podpisy zprávy do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="5e35b-127">The client stores the signatures of the message in a cache.</span></span> <span data-ttu-id="5e35b-128">Toto nastavení určuje, kolik podpisů může mezipaměť ukládat.</span><span class="sxs-lookup"><span data-stu-id="5e35b-128">This setting specifies how many signatures the cache can store.</span></span> <span data-ttu-id="5e35b-129">Pokud počet zpráv odeslaných v rámci posledního opětovného přehrávání dosáhne limitu mezipaměti, nové zprávy jsou odmítnuty, dokud nedosáhnou nejstarších podpisů v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="5e35b-129">If the number of messages sent within the last replay window reaches the cache limit, new messages are rejected until the oldest cached signatures reach the time limit.</span></span> <span data-ttu-id="5e35b-130">Výchozí hodnota je 500000.</span><span class="sxs-lookup"><span data-stu-id="5e35b-130">The default is 500000.</span></span>  
  
### <a name="to-control-replay-detection-on-the-service-using-code"></a><span data-ttu-id="5e35b-131">Řízení zjišťování opakování u služby pomocí kódu</span><span class="sxs-lookup"><span data-stu-id="5e35b-131">To control replay detection on the service using code</span></span>  
  
1. <span data-ttu-id="5e35b-132">Vytvořte <xref:System.ServiceModel.Channels.SecurityBindingElement> pro použití v <xref:System.ServiceModel.Channels.CustomBinding> .</span><span class="sxs-lookup"><span data-stu-id="5e35b-132">Create a <xref:System.ServiceModel.Channels.SecurityBindingElement> to use in a <xref:System.ServiceModel.Channels.CustomBinding>.</span></span>  
  
2. <span data-ttu-id="5e35b-133">Pomocí <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> vlastnosti vraťte odkaz na <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> třídu a nastavte vlastnosti tak, jak je popsáno výše.</span><span class="sxs-lookup"><span data-stu-id="5e35b-133">Use the <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A> property to return a reference to the <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings> class, and set the properties as described previously.</span></span>  
  
### <a name="to-control-replay-detection-in-configuration-for-the-client-or-service"></a><span data-ttu-id="5e35b-134">Řízení zjišťování opětovného přehrání v konfiguraci pro klienta nebo službu</span><span class="sxs-lookup"><span data-stu-id="5e35b-134">To control replay detection in configuration for the client or service</span></span>  
  
1. <span data-ttu-id="5e35b-135">Vytvořte [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md) .</span><span class="sxs-lookup"><span data-stu-id="5e35b-135">Create a [\<customBinding>](../../configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
2. <span data-ttu-id="5e35b-136">Vytvořte `<security>` element.</span><span class="sxs-lookup"><span data-stu-id="5e35b-136">Create a `<security>` element.</span></span>  
  
3. <span data-ttu-id="5e35b-137">Vytvořte [\<localClientSettings>](../../configure-apps/file-schema/wcf/localclientsettings-element.md) nebo [\<localServiceSettings>](../../configure-apps/file-schema/wcf/localservicesettings-element.md) .</span><span class="sxs-lookup"><span data-stu-id="5e35b-137">Create a [\<localClientSettings>](../../configure-apps/file-schema/wcf/localclientsettings-element.md) or [\<localServiceSettings>](../../configure-apps/file-schema/wcf/localservicesettings-element.md).</span></span>  
  
4. <span data-ttu-id="5e35b-138">Nastavte následující hodnoty atributu podle potřeby: `detectReplays` ,, a `maxClockSkew` `replayWindow` `replayCacheSize` .</span><span class="sxs-lookup"><span data-stu-id="5e35b-138">Set the following attribute values, as appropriate: `detectReplays`, `maxClockSkew`, `replayWindow`, and `replayCacheSize`.</span></span> <span data-ttu-id="5e35b-139">Následující příklad nastaví atributy prvku `<localServiceSettings>` a i `<localClientSettings>` elementu:</span><span class="sxs-lookup"><span data-stu-id="5e35b-139">The following example sets the attributes of both a `<localServiceSettings>` and a `<localClientSettings>` element:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="5e35b-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="5e35b-140">Example</span></span>  
 <span data-ttu-id="5e35b-141">Následující příklad vytvoří <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> pomocí <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> metody a nastaví vlastnosti opětovného přehrání vazby.</span><span class="sxs-lookup"><span data-stu-id="5e35b-141">The following example creates a <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> using the <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> method, and sets the replay properties of the binding.</span></span>  
  
 [!code-csharp[c_ReplayDetection#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_replaydetection/cs/source.cs#1)]
 [!code-vb[c_ReplayDetection#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_replaydetection/vb/source.vb#1)]  
  
## <a name="scope-of-replay-message-security-only"></a><span data-ttu-id="5e35b-142">Rozsah přehrání: pouze zabezpečení zprávy</span><span class="sxs-lookup"><span data-stu-id="5e35b-142">Scope of Replay: Message Security Only</span></span>  
 <span data-ttu-id="5e35b-143">Následující postupy platí pouze pro režim zabezpečení zpráv.</span><span class="sxs-lookup"><span data-stu-id="5e35b-143">Note that the following procedures apply only to Message security mode.</span></span> <span data-ttu-id="5e35b-144">Pro přenos a přenos s režimem přihlašovacích údajů zpráv zjišťují mechanismy přenosu.</span><span class="sxs-lookup"><span data-stu-id="5e35b-144">For Transport and Transport with Message Credential modes, the transport mechanisms detect replays.</span></span>  
  
## <a name="secure-conversation-notes"></a><span data-ttu-id="5e35b-145">Zabezpečené poznámky ke konverzaci</span><span class="sxs-lookup"><span data-stu-id="5e35b-145">Secure Conversation Notes</span></span>  
 <span data-ttu-id="5e35b-146">U vazeb, které umožňují zabezpečenou konverzaci, můžete tato nastavení upravit pro kanál aplikace i pro spouštěcí vazby zabezpečené konverzace.</span><span class="sxs-lookup"><span data-stu-id="5e35b-146">For bindings that enable secure conversations, you can adjust these settings both for the application channel as well as for the secure conversation bootstrap binding.</span></span> <span data-ttu-id="5e35b-147">Můžete například vypnout přehrávání pro kanál aplikace, ale povolit je pro spouštěcí kanál, který vytváří zabezpečenou konverzaci.</span><span class="sxs-lookup"><span data-stu-id="5e35b-147">For example, you can turn off replays for the application channel but enable them for the bootstrap channel that establishes the secure conversation.</span></span>  
  
 <span data-ttu-id="5e35b-148">Pokud nepoužíváte zabezpečené relace konverzace, detekce opětovného přehrání nezaručuje detekci přehrání ve scénářích serverové farmy a při recyklaci procesu.</span><span class="sxs-lookup"><span data-stu-id="5e35b-148">If you do not use secure conversation sessions, replay detection does not guarantee detecting replays in server farm scenarios and when the process is recycled.</span></span> <span data-ttu-id="5e35b-149">To platí pro následující vazby poskytované systémem:</span><span class="sxs-lookup"><span data-stu-id="5e35b-149">This applies to the following system-provided bindings:</span></span>  
  
- <span data-ttu-id="5e35b-150"><xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="5e35b-150"><xref:System.ServiceModel.BasicHttpBinding>.</span></span>  
  
- <span data-ttu-id="5e35b-151"><xref:System.ServiceModel.WSHttpBinding>s <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> vlastností nastavenou na `false` .</span><span class="sxs-lookup"><span data-stu-id="5e35b-151"><xref:System.ServiceModel.WSHttpBinding> with the <xref:System.ServiceModel.NonDualMessageSecurityOverHttp.EstablishSecurityContext%2A> property set to `false`.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5e35b-152">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="5e35b-152">Compiling the Code</span></span>  
  
- <span data-ttu-id="5e35b-153">Pro zkompilování kódu jsou vyžadovány následující obory názvů:</span><span class="sxs-lookup"><span data-stu-id="5e35b-153">The following namespaces are required to compile the code:</span></span>  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.ServiceModel.Channels>  
  
## <a name="see-also"></a><span data-ttu-id="5e35b-154">Viz také</span><span class="sxs-lookup"><span data-stu-id="5e35b-154">See also</span></span>

- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- [<span data-ttu-id="5e35b-155">Zabezpečené konverzace a zabezpečené relace</span><span class="sxs-lookup"><span data-stu-id="5e35b-155">Secure Conversations and Secure Sessions</span></span>](secure-conversations-and-secure-sessions.md)
- [\<localClientSettings>](../../configure-apps/file-schema/wcf/localclientsettings-element.md)
- [<span data-ttu-id="5e35b-156">Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="5e35b-156">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](how-to-create-a-custom-binding-using-the-securitybindingelement.md)
