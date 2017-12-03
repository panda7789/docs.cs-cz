---
title: Element &lt;localClientSettings&gt;
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4680ace5-f4e1-4fcb-b9d8-a4a4af5cd7ae
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cabde7eb9dd122c2f7060b2f2e2c16f5949dc1f3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltlocalclientsettingsgt-element"></a><span data-ttu-id="b1827-102">Element &lt;localClientSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="b1827-102">&lt;localClientSettings&gt; element</span></span>
<span data-ttu-id="b1827-103">Určuje nastavení zabezpečení místního klienta pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="b1827-103">Specifies the security settings of a local client for this binding.</span></span>  
  
 <span data-ttu-id="b1827-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="b1827-104">\<system.serviceModel></span></span>  
<span data-ttu-id="b1827-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="b1827-105">\<bindings></span></span>  
<span data-ttu-id="b1827-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="b1827-106">\<customBinding></span></span>  
<span data-ttu-id="b1827-107">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="b1827-107">\<binding></span></span>  
<span data-ttu-id="b1827-108">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="b1827-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1827-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1827-109">Syntax</span></span>  
  
```xml  
<security>  
   <localClientSettings cacheCookies="Boolean"  
      cookieRenewalThresholdPercentage="Integer"  
      detectReplays="Boolean"  
      maxClockSkew="TimeSpan"  
      maxCookieCachingTime="TimeSpan"  
      reconnectTransportOnFailure="Boolean"  
      replayCacheSize="Integer"  
      replayWindow="TimeSpan"  
      sessionKeyRenewalInterval="TimeSpan"  
      sessionKeyRolloverInterval="TimeSpan"  
      timestampValidityDuration="TimeSpan" />  
</security>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b1827-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b1827-110">Attributes and Elements</span></span>  
 <span data-ttu-id="b1827-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b1827-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b1827-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="b1827-112">Attributes</span></span>  
  
|<span data-ttu-id="b1827-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="b1827-113">Attribute</span></span>|<span data-ttu-id="b1827-114">Popis</span><span class="sxs-lookup"><span data-stu-id="b1827-114">Description</span></span>|  
|---------------|-----------------|  
|`cacheCookies`|<span data-ttu-id="b1827-115">Logická hodnota, která určuje, zda je povoleno ukládání do mezipaměti souborů cookie.</span><span class="sxs-lookup"><span data-stu-id="b1827-115">A Boolean value that specifies whether cookie caching is enabled.</span></span> <span data-ttu-id="b1827-116">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="b1827-116">The default is `false`.</span></span>|  
|`cookieRenewalThresholdPercentage`|<span data-ttu-id="b1827-117">Celé číslo, které určuje maximální procento soubory cookie, které může být obnovena.</span><span class="sxs-lookup"><span data-stu-id="b1827-117">An integer that specifies the maximum percentage of cookies that can be renewed.</span></span> <span data-ttu-id="b1827-118">Tato hodnota by měla být mezi 0 a 100 (včetně).</span><span class="sxs-lookup"><span data-stu-id="b1827-118">This value should be between 0 and 100 inclusively.</span></span> <span data-ttu-id="b1827-119">Výchozí hodnota je 90.</span><span class="sxs-lookup"><span data-stu-id="b1827-119">The default is 90.</span></span>|  
|`detectReplays`|<span data-ttu-id="b1827-120">Logická hodnota, která určuje, jestli jsou před zneužitím útoky na kanál zjistil a řešeny automaticky.</span><span class="sxs-lookup"><span data-stu-id="b1827-120">A Boolean value that specifies whether replay attacks against the channel are detected and dealt with automatically.</span></span> <span data-ttu-id="b1827-121">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="b1827-121">The default is `false`.</span></span>|  
|`maxClockSkew`|<span data-ttu-id="b1827-122">A <xref:System.TimeSpan> , který určuje maximální časový rozdíl mezi systémovými hodinami dvou komunikujících stran.</span><span class="sxs-lookup"><span data-stu-id="b1827-122">A <xref:System.TimeSpan> that specifies the maximum time difference between the system clocks of the two communicating parties.</span></span> <span data-ttu-id="b1827-123">Výchozí hodnota je "00: 05:00".</span><span class="sxs-lookup"><span data-stu-id="b1827-123">The default value is "00:05:00".</span></span><br /><br /> <span data-ttu-id="b1827-124">Pokud je tato hodnota nastavená na výchozí hodnoty, příjemce přijímá zprávy s okamžiku odeslání časová razítka na 5 minut později nebo starší než čas zpráva byla přijata.</span><span class="sxs-lookup"><span data-stu-id="b1827-124">When this value is set to the default, the receiver accepts messages with send-time time stamps up to 5 minutes later or earlier than the time the message was received.</span></span> <span data-ttu-id="b1827-125">Zprávy, které nepředávejte testovací odeslání čas odmítají.</span><span class="sxs-lookup"><span data-stu-id="b1827-125">Messages that do not pass the send-time test are rejected.</span></span> <span data-ttu-id="b1827-126">Toto nastavení se používá ve spojení s `replayWindow` atribut.</span><span class="sxs-lookup"><span data-stu-id="b1827-126">This setting is used in conjunction with the `replayWindow` attribute.</span></span>|  
|`maxCookieCachingTime`|<span data-ttu-id="b1827-127">A <xref:System.TimeSpan> určující maximální doba života souborů cookie.</span><span class="sxs-lookup"><span data-stu-id="b1827-127">A <xref:System.TimeSpan> that specifies the maximum lifetime of cookies.</span></span> <span data-ttu-id="b1827-128">Výchozí hodnota je "10675199.02:48:05.4775807".</span><span class="sxs-lookup"><span data-stu-id="b1827-128">The default value is "10675199.02:48:05.4775807".</span></span>|  
|`reconnectTransportOnFailure`|<span data-ttu-id="b1827-129">Logická hodnota, která určuje, zda připojení pomocí protokolu WS-spolehlivé zasílání zpráv se pokusí znovu připojit po selhání přenosu.</span><span class="sxs-lookup"><span data-stu-id="b1827-129">A Boolean value that specifies whether connections using WS-Reliable messaging will attempt to reconnect after transport failures.</span></span> <span data-ttu-id="b1827-130">Výchozí hodnota je `true`, což znamená, že se pokusil nekonečné pokusí znovu připojit.</span><span class="sxs-lookup"><span data-stu-id="b1827-130">The default is `true`, which means that infinite attempts to reconnect are attempted.</span></span> <span data-ttu-id="b1827-131">Cyklus je rozděleno podle časový limit nečinnosti, což způsobí, že kanál, ke způsobí výjimku, pokud ji nelze znovu připojit.</span><span class="sxs-lookup"><span data-stu-id="b1827-131">The cycle is broken by the inactivity time-out, which causes the channel to throw an exception when it cannot be reconnected.</span></span>|  
|`replayCacheSize`|<span data-ttu-id="b1827-132">Kladné celé číslo určující počet do mezipaměti náhodně generované identifikátory používá pro rozpoznání opětovného přehrání.</span><span class="sxs-lookup"><span data-stu-id="b1827-132">A positive integer that specifies the number of cached nonces used for replay detection.</span></span> <span data-ttu-id="b1827-133">Pokud je tento limit překročen, nejstarší hodnotu nonce se odebere a novou hodnotu nonce se vytvoří pro novou zprávu.</span><span class="sxs-lookup"><span data-stu-id="b1827-133">If this limit is exceeded, the oldest nonce is removed and a new nonce is created for the new message.</span></span> <span data-ttu-id="b1827-134">Výchozí hodnota je 500000.</span><span class="sxs-lookup"><span data-stu-id="b1827-134">The default value is 500000.</span></span>|  
|`replayWindow`|<span data-ttu-id="b1827-135">A <xref:System.TimeSpan> který určuje dobu, ve kterém jsou platné náhodně generované identifikátory jednotlivé zprávy.</span><span class="sxs-lookup"><span data-stu-id="b1827-135">A <xref:System.TimeSpan> that specifies the duration in which individual message nonces are valid.</span></span><br /><br /> <span data-ttu-id="b1827-136">Po této hodnotě duration nebudou přijaté zprávy odeslané s stejnou hodnotu nonce jako odesílat před.</span><span class="sxs-lookup"><span data-stu-id="b1827-136">After this duration, a message sent with the same nonce as the one sent before will not be accepted.</span></span> <span data-ttu-id="b1827-137">Tento atribut se používá ve spojení s `maxClockSkew` atribut, aby se zabránilo provedení útoku formou opakovaného.</span><span class="sxs-lookup"><span data-stu-id="b1827-137">This attribute is used in conjunction with the `maxClockSkew` attribute to prevent replay attacks.</span></span> <span data-ttu-id="b1827-138">Útočník by mohl přehráním zprávu po vypršení platnosti jeho opětovného přehrání okno.</span><span class="sxs-lookup"><span data-stu-id="b1827-138">An attacker could replay a message after its replay window has expired.</span></span> <span data-ttu-id="b1827-139">Tato zpráva, ale dojde k selhání `maxClockSkew` test, který odmítne zprávy Časová razítka okamžiku odeslání až určitou dobu novější nebo starší, než čas zpráva byla přijata.</span><span class="sxs-lookup"><span data-stu-id="b1827-139">This message, however, would fail the `maxClockSkew` test which rejects messages with send-time timestamps up to a specified time later or earlier than the time the message was received.</span></span>|  
|`sessionKeyRenewalInterval`|<span data-ttu-id="b1827-140">A <xref:System.TimeSpan> který určuje dobu, po které bude iniciátoru obnovíte klíč relace zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="b1827-140">A <xref:System.TimeSpan> that specifies the duration after which the initiator will renew the key for the security session.</span></span> <span data-ttu-id="b1827-141">Výchozí hodnota je "10: 00:00".</span><span class="sxs-lookup"><span data-stu-id="b1827-141">The default is "10:00:00".</span></span>|  
|`sessionKeyRolloverInterval`|<span data-ttu-id="b1827-142">A <xref:System.TimeSpan> který určuje časový interval klíče předchozí relace je platná pro příchozí zprávy během obnovení klíče.</span><span class="sxs-lookup"><span data-stu-id="b1827-142">A <xref:System.TimeSpan> that specifies the time interval a previous session key is valid on incoming messages during a key renewal.</span></span> <span data-ttu-id="b1827-143">Výchozí hodnota je "00: 05:00".</span><span class="sxs-lookup"><span data-stu-id="b1827-143">The default is "00:05:00".</span></span><br /><br /> <span data-ttu-id="b1827-144">Během obnovení klíče musí klient a server vždy odesílat zprávy pomocí nejnovější dostupné klíče.</span><span class="sxs-lookup"><span data-stu-id="b1827-144">During key renewal, the client and server must always send messages using the most current available key.</span></span> <span data-ttu-id="b1827-145">Obě strany bude přijímat příchozí zprávy zabezpečené klíčem předchozí relace, dokud nevyprší časový výměny.</span><span class="sxs-lookup"><span data-stu-id="b1827-145">Both parties will accept incoming messages secured with the previous session key until the rollover time expires.</span></span>|  
|`timestampValidityDuration`|<span data-ttu-id="b1827-146">U kladné <xref:System.TimeSpan> který určuje dobu, ve kterém je platný časové razítko.</span><span class="sxs-lookup"><span data-stu-id="b1827-146">A positive <xref:System.TimeSpan> that specifies the duration in which a time stamp is valid.</span></span> <span data-ttu-id="b1827-147">Výchozí hodnota je "00: 15:00".</span><span class="sxs-lookup"><span data-stu-id="b1827-147">The default is "00:15:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b1827-148">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b1827-148">Child Elements</span></span>  
 <span data-ttu-id="b1827-149">Žádné</span><span class="sxs-lookup"><span data-stu-id="b1827-149">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b1827-150">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b1827-150">Parent Elements</span></span>  
  
|<span data-ttu-id="b1827-151">Prvek</span><span class="sxs-lookup"><span data-stu-id="b1827-151">Element</span></span>|<span data-ttu-id="b1827-152">Popis</span><span class="sxs-lookup"><span data-stu-id="b1827-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b1827-153">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="b1827-153">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|<span data-ttu-id="b1827-154">Určuje možnosti zabezpečení u vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="b1827-154">Specifies the security options for a custom binding.</span></span>|  
|[<span data-ttu-id="b1827-155">\<secureConversationBootstrap ></span><span class="sxs-lookup"><span data-stu-id="b1827-155">\<secureConversationBootstrap></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|<span data-ttu-id="b1827-156">Určuje výchozí hodnoty používané pro inicializaci služby Zabezpečené konverzaci.</span><span class="sxs-lookup"><span data-stu-id="b1827-156">Specifies the default values used for initiating a secure conversation service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1827-157">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b1827-157">Remarks</span></span>  
 <span data-ttu-id="b1827-158">Nastavení jsou místní v tom smyslu, že se nejedná o nastavení odvozené ze zásad zabezpečení služby.</span><span class="sxs-lookup"><span data-stu-id="b1827-158">The settings are local in the sense that they are not settings derived from the security policy of the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1827-159">Viz také</span><span class="sxs-lookup"><span data-stu-id="b1827-159">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>  
 <xref:System.ServiceModel.Configuration.SecurityElementBase.LocalClientSettings%2A>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A>  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="b1827-160">Vazby</span><span class="sxs-lookup"><span data-stu-id="b1827-160">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="b1827-161">Rozšiřování vazeb</span><span class="sxs-lookup"><span data-stu-id="b1827-161">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="b1827-162">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="b1827-162">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="b1827-163">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="b1827-163">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="b1827-164">Postupy: vytvoření vlastní vazby pomocí elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="b1827-164">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [<span data-ttu-id="b1827-165">Zabezpečení vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="b1827-165">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
