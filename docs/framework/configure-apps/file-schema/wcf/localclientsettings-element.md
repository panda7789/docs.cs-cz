---
title: <localClientSettings> – element
ms.date: 03/30/2017
ms.assetid: 4680ace5-f4e1-4fcb-b9d8-a4a4af5cd7ae
ms.openlocfilehash: c5caf183e37edda6efc79ec81f1628180379fd46
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765775"
---
# <a name="localclientsettings-element"></a><span data-ttu-id="6164c-102">\<localClientSettings > – element</span><span class="sxs-lookup"><span data-stu-id="6164c-102">\<localClientSettings> element</span></span>
<span data-ttu-id="6164c-103">Určuje nastavení zabezpečení místního klienta pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="6164c-103">Specifies the security settings of a local client for this binding.</span></span>  
  
 <span data-ttu-id="6164c-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="6164c-104">\<system.serviceModel></span></span>  
<span data-ttu-id="6164c-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="6164c-105">\<bindings></span></span>  
<span data-ttu-id="6164c-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="6164c-106">\<customBinding></span></span>  
<span data-ttu-id="6164c-107">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="6164c-107">\<binding></span></span>  
<span data-ttu-id="6164c-108">\<security></span><span class="sxs-lookup"><span data-stu-id="6164c-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6164c-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6164c-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6164c-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6164c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6164c-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6164c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6164c-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="6164c-112">Attributes</span></span>  
  
|<span data-ttu-id="6164c-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="6164c-113">Attribute</span></span>|<span data-ttu-id="6164c-114">Popis</span><span class="sxs-lookup"><span data-stu-id="6164c-114">Description</span></span>|  
|---------------|-----------------|  
|`cacheCookies`|<span data-ttu-id="6164c-115">Logická hodnota určující, zda je povoleno ukládání do mezipaměti souborů cookie.</span><span class="sxs-lookup"><span data-stu-id="6164c-115">A Boolean value that specifies whether cookie caching is enabled.</span></span> <span data-ttu-id="6164c-116">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="6164c-116">The default is `false`.</span></span>|  
|`cookieRenewalThresholdPercentage`|<span data-ttu-id="6164c-117">Celé číslo určující maximální procento souborů cookie, které jde ji obnovit.</span><span class="sxs-lookup"><span data-stu-id="6164c-117">An integer that specifies the maximum percentage of cookies that can be renewed.</span></span> <span data-ttu-id="6164c-118">Tato hodnota by měla být mezi 0 a 100 (včetně).</span><span class="sxs-lookup"><span data-stu-id="6164c-118">This value should be between 0 and 100 inclusively.</span></span> <span data-ttu-id="6164c-119">Výchozí hodnota je 90.</span><span class="sxs-lookup"><span data-stu-id="6164c-119">The default is 90.</span></span>|  
|`detectReplays`|<span data-ttu-id="6164c-120">Logická hodnota určující, zda jsou zjištěny a řešeny automaticky opakované útoky proti kanálu.</span><span class="sxs-lookup"><span data-stu-id="6164c-120">A Boolean value that specifies whether replay attacks against the channel are detected and dealt with automatically.</span></span> <span data-ttu-id="6164c-121">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="6164c-121">The default is `false`.</span></span>|  
|`maxClockSkew`|<span data-ttu-id="6164c-122">A <xref:System.TimeSpan> , která určuje maximální časový rozdíl mezi systémovými hodinami dvou komunikujících stran.</span><span class="sxs-lookup"><span data-stu-id="6164c-122">A <xref:System.TimeSpan> that specifies the maximum time difference between the system clocks of the two communicating parties.</span></span> <span data-ttu-id="6164c-123">Výchozí hodnota je "00: 05:00".</span><span class="sxs-lookup"><span data-stu-id="6164c-123">The default value is "00:05:00".</span></span><br /><br /> <span data-ttu-id="6164c-124">Pokud tato hodnota nastavena na výchozí hodnotu, příjemce přijímá zprávy s čas odeslání časová razítka na 5 minut později nebo dříve než čas přijetí zprávy.</span><span class="sxs-lookup"><span data-stu-id="6164c-124">When this value is set to the default, the receiver accepts messages with send-time time stamps up to 5 minutes later or earlier than the time the message was received.</span></span> <span data-ttu-id="6164c-125">Nepředávejte test čas odeslání zprávy jsou odmítnuta.</span><span class="sxs-lookup"><span data-stu-id="6164c-125">Messages that do not pass the send-time test are rejected.</span></span> <span data-ttu-id="6164c-126">Toto nastavení se používá ve spojení s `replayWindow` atribut.</span><span class="sxs-lookup"><span data-stu-id="6164c-126">This setting is used in conjunction with the `replayWindow` attribute.</span></span>|  
|`maxCookieCachingTime`|<span data-ttu-id="6164c-127">A <xref:System.TimeSpan> , která určuje maximální dobu života souboru cookie.</span><span class="sxs-lookup"><span data-stu-id="6164c-127">A <xref:System.TimeSpan> that specifies the maximum lifetime of cookies.</span></span> <span data-ttu-id="6164c-128">Výchozí hodnota je "10675199.02:48:05.4775807".</span><span class="sxs-lookup"><span data-stu-id="6164c-128">The default value is "10675199.02:48:05.4775807".</span></span>|  
|`reconnectTransportOnFailure`|<span data-ttu-id="6164c-129">Logická hodnota určující, zda připojení používající posílání WS-Reliable se pokusí znovu připojit po selhání přenosu.</span><span class="sxs-lookup"><span data-stu-id="6164c-129">A Boolean value that specifies whether connections using WS-Reliable messaging will attempt to reconnect after transport failures.</span></span> <span data-ttu-id="6164c-130">Výchozí hodnota je `true`, což znamená, že nedochází k pokusům o nekonečné pokusí znovu připojit.</span><span class="sxs-lookup"><span data-stu-id="6164c-130">The default is `true`, which means that infinite attempts to reconnect are attempted.</span></span> <span data-ttu-id="6164c-131">Cyklus je porušena časový limit nečinnosti, což způsobí, že kanálů pokusí vyvolat výjimku, pokud nelze je připojit.</span><span class="sxs-lookup"><span data-stu-id="6164c-131">The cycle is broken by the inactivity time-out, which causes the channel to throw an exception when it cannot be reconnected.</span></span>|  
|`replayCacheSize`|<span data-ttu-id="6164c-132">Celé kladné číslo určující počet náhodně generované identifikátory použitých pro zjištění opakování ukládat do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="6164c-132">A positive integer that specifies the number of cached nonces used for replay detection.</span></span> <span data-ttu-id="6164c-133">Pokud je tento limit překročen, nejstarší hodnota nonce je odebrán a nová hodnota nonce je vytvořen pro nové zprávy.</span><span class="sxs-lookup"><span data-stu-id="6164c-133">If this limit is exceeded, the oldest nonce is removed and a new nonce is created for the new message.</span></span> <span data-ttu-id="6164c-134">Výchozí hodnota je 500000.</span><span class="sxs-lookup"><span data-stu-id="6164c-134">The default value is 500000.</span></span>|  
|`replayWindow`|<span data-ttu-id="6164c-135">A <xref:System.TimeSpan> , který určuje dobu, po kterou jsou platné náhodně generované identifikátory jednotlivých zpráv.</span><span class="sxs-lookup"><span data-stu-id="6164c-135">A <xref:System.TimeSpan> that specifies the duration in which individual message nonces are valid.</span></span><br /><br /> <span data-ttu-id="6164c-136">Po této hodnotě duration zprávy se stejnou hodnotu nonce jako odeslaným před nepřijme.</span><span class="sxs-lookup"><span data-stu-id="6164c-136">After this duration, a message sent with the same nonce as the one sent before will not be accepted.</span></span> <span data-ttu-id="6164c-137">Tento atribut se používá ve spojení s `maxClockSkew` atribut, aby se zabránilo opakované útoky.</span><span class="sxs-lookup"><span data-stu-id="6164c-137">This attribute is used in conjunction with the `maxClockSkew` attribute to prevent replay attacks.</span></span> <span data-ttu-id="6164c-138">Útočník by mohl znovu přehrát zprávu po vypršení její okno opětovného přehrání.</span><span class="sxs-lookup"><span data-stu-id="6164c-138">An attacker could replay a message after its replay window has expired.</span></span> <span data-ttu-id="6164c-139">Tato zpráva, ale selže `maxClockSkew` testu, který odmítne zprávy s časovými razítky čas odeslání až po určitou dobu později nebo starší, než čas přijetí zprávy.</span><span class="sxs-lookup"><span data-stu-id="6164c-139">This message, however, would fail the `maxClockSkew` test which rejects messages with send-time timestamps up to a specified time later or earlier than the time the message was received.</span></span>|  
|`sessionKeyRenewalInterval`|<span data-ttu-id="6164c-140">A <xref:System.TimeSpan> , který určuje dobu, po které iniciátor obnoví klíč relace zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="6164c-140">A <xref:System.TimeSpan> that specifies the duration after which the initiator will renew the key for the security session.</span></span> <span data-ttu-id="6164c-141">Výchozí hodnota je "10: 00:00".</span><span class="sxs-lookup"><span data-stu-id="6164c-141">The default is "10:00:00".</span></span>|  
|`sessionKeyRolloverInterval`|<span data-ttu-id="6164c-142">A <xref:System.TimeSpan> , který určuje časový interval klíč předchozí relace je platný na příchozích zprávách během obnovení klíče.</span><span class="sxs-lookup"><span data-stu-id="6164c-142">A <xref:System.TimeSpan> that specifies the time interval a previous session key is valid on incoming messages during a key renewal.</span></span> <span data-ttu-id="6164c-143">Výchozí hodnota je "00: 05:00".</span><span class="sxs-lookup"><span data-stu-id="6164c-143">The default is "00:05:00".</span></span><br /><br /> <span data-ttu-id="6164c-144">Během obnovení klíče musí klient a server vždy odesílat zprávy pomocí nejnovější dostupné klíče.</span><span class="sxs-lookup"><span data-stu-id="6164c-144">During key renewal, the client and server must always send messages using the most current available key.</span></span> <span data-ttu-id="6164c-145">Obě strany bude přijímat příchozí zprávy, které jsou zabezpečené pomocí klíč předchozí relace, dokud nevyprší čas přechodu.</span><span class="sxs-lookup"><span data-stu-id="6164c-145">Both parties will accept incoming messages secured with the previous session key until the rollover time expires.</span></span>|  
|`timestampValidityDuration`|<span data-ttu-id="6164c-146">Pozitivní <xref:System.TimeSpan> , který určuje dobu, ve kterém je platné časové razítko.</span><span class="sxs-lookup"><span data-stu-id="6164c-146">A positive <xref:System.TimeSpan> that specifies the duration in which a time stamp is valid.</span></span> <span data-ttu-id="6164c-147">Výchozí hodnota je "00: 15:00".</span><span class="sxs-lookup"><span data-stu-id="6164c-147">The default is "00:15:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6164c-148">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6164c-148">Child Elements</span></span>  
 <span data-ttu-id="6164c-149">Žádné</span><span class="sxs-lookup"><span data-stu-id="6164c-149">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6164c-150">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6164c-150">Parent Elements</span></span>  
  
|<span data-ttu-id="6164c-151">Prvek</span><span class="sxs-lookup"><span data-stu-id="6164c-151">Element</span></span>|<span data-ttu-id="6164c-152">Popis</span><span class="sxs-lookup"><span data-stu-id="6164c-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6164c-153">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="6164c-153">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|<span data-ttu-id="6164c-154">Určuje možnosti zabezpečení pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="6164c-154">Specifies the security options for a custom binding.</span></span>|  
|[<span data-ttu-id="6164c-155">\<secureConversationBootstrap></span><span class="sxs-lookup"><span data-stu-id="6164c-155">\<secureConversationBootstrap></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|<span data-ttu-id="6164c-156">Určuje výchozí hodnoty pro inicializaci služby zabezpečené konverzace.</span><span class="sxs-lookup"><span data-stu-id="6164c-156">Specifies the default values used for initiating a secure conversation service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6164c-157">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6164c-157">Remarks</span></span>  
 <span data-ttu-id="6164c-158">Nastavení, musí být místní v tom smyslu, že se nejedná o nastavení odvozený od zásady zabezpečení služby.</span><span class="sxs-lookup"><span data-stu-id="6164c-158">The settings are local in the sense that they are not settings derived from the security policy of the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6164c-159">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6164c-159">See also</span></span>

- <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.LocalClientSettings%2A>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A>
- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="6164c-160">Vazby</span><span class="sxs-lookup"><span data-stu-id="6164c-160">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="6164c-161">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="6164c-161">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="6164c-162">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="6164c-162">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="6164c-163">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="6164c-163">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [<span data-ttu-id="6164c-164">Postupy: Vytvoření vlastní vazby pomocí elementu SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="6164c-164">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="6164c-165">Zabezpečení vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="6164c-165">Custom Binding Security</span></span>](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
