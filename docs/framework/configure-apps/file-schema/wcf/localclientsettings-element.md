---
title: <localClientSettings> – element
ms.date: 03/30/2017
ms.assetid: 4680ace5-f4e1-4fcb-b9d8-a4a4af5cd7ae
ms.openlocfilehash: e7331105582a4a48b7edd8cd4f6a691771b0b8ff
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930798"
---
# <a name="localclientsettings-element"></a><span data-ttu-id="1d855-102">\<localClientSettings – element ></span><span class="sxs-lookup"><span data-stu-id="1d855-102">\<localClientSettings> element</span></span>
<span data-ttu-id="1d855-103">Určuje nastavení zabezpečení místního klienta pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="1d855-103">Specifies the security settings of a local client for this binding.</span></span>  
  
 <span data-ttu-id="1d855-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="1d855-104">\<system.serviceModel></span></span>  
<span data-ttu-id="1d855-105">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="1d855-105">\<bindings></span></span>  
<span data-ttu-id="1d855-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="1d855-106">\<customBinding></span></span>  
<span data-ttu-id="1d855-107">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="1d855-107">\<binding></span></span>  
<span data-ttu-id="1d855-108">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="1d855-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d855-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1d855-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1d855-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1d855-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1d855-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1d855-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1d855-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="1d855-112">Attributes</span></span>  
  
|<span data-ttu-id="1d855-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="1d855-113">Attribute</span></span>|<span data-ttu-id="1d855-114">Popis</span><span class="sxs-lookup"><span data-stu-id="1d855-114">Description</span></span>|  
|---------------|-----------------|  
|`cacheCookies`|<span data-ttu-id="1d855-115">Logická hodnota, která určuje, zda je povoleno ukládání souborů cookie do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="1d855-115">A Boolean value that specifies whether cookie caching is enabled.</span></span> <span data-ttu-id="1d855-116">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="1d855-116">The default is `false`.</span></span>|  
|`cookieRenewalThresholdPercentage`|<span data-ttu-id="1d855-117">Celé číslo, které určuje maximální procento souborů cookie, které mohou být obnoveny.</span><span class="sxs-lookup"><span data-stu-id="1d855-117">An integer that specifies the maximum percentage of cookies that can be renewed.</span></span> <span data-ttu-id="1d855-118">Tato hodnota by měla být mezi 0 a 100 (včetně).</span><span class="sxs-lookup"><span data-stu-id="1d855-118">This value should be between 0 and 100 inclusively.</span></span> <span data-ttu-id="1d855-119">Výchozí hodnota je 90.</span><span class="sxs-lookup"><span data-stu-id="1d855-119">The default is 90.</span></span>|  
|`detectReplays`|<span data-ttu-id="1d855-120">Logická hodnota určující, zda jsou zjištěny opakované útoky proti kanálu a zda jsou řešeny automaticky.</span><span class="sxs-lookup"><span data-stu-id="1d855-120">A Boolean value that specifies whether replay attacks against the channel are detected and dealt with automatically.</span></span> <span data-ttu-id="1d855-121">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="1d855-121">The default is `false`.</span></span>|  
|`maxClockSkew`|<span data-ttu-id="1d855-122">A <xref:System.TimeSpan> určuje maximální časový rozdíl mezi systémovými hodinami dvou komunikujících stran.</span><span class="sxs-lookup"><span data-stu-id="1d855-122">A <xref:System.TimeSpan> that specifies the maximum time difference between the system clocks of the two communicating parties.</span></span> <span data-ttu-id="1d855-123">Výchozí hodnota je "00:05:00".</span><span class="sxs-lookup"><span data-stu-id="1d855-123">The default value is "00:05:00".</span></span><br /><br /> <span data-ttu-id="1d855-124">Pokud je tato hodnota nastavená na výchozí hodnotu, příjemce přijímá zprávy s časovými razítky pro odeslání až 5 minut později nebo dříve, než čas, kdy byla zpráva přijata.</span><span class="sxs-lookup"><span data-stu-id="1d855-124">When this value is set to the default, the receiver accepts messages with send-time time stamps up to 5 minutes later or earlier than the time the message was received.</span></span> <span data-ttu-id="1d855-125">Zprávy, které nevyhověly testu při odeslání, jsou odmítnuty.</span><span class="sxs-lookup"><span data-stu-id="1d855-125">Messages that do not pass the send-time test are rejected.</span></span> <span data-ttu-id="1d855-126">Toto nastavení se používá ve spojení s `replayWindow` atributem.</span><span class="sxs-lookup"><span data-stu-id="1d855-126">This setting is used in conjunction with the `replayWindow` attribute.</span></span>|  
|`maxCookieCachingTime`|<span data-ttu-id="1d855-127">A <xref:System.TimeSpan> určuje maximální dobu života souborů cookie.</span><span class="sxs-lookup"><span data-stu-id="1d855-127">A <xref:System.TimeSpan> that specifies the maximum lifetime of cookies.</span></span> <span data-ttu-id="1d855-128">Výchozí hodnota je "10675199.02:48:05.4775807".</span><span class="sxs-lookup"><span data-stu-id="1d855-128">The default value is "10675199.02:48:05.4775807".</span></span>|  
|`reconnectTransportOnFailure`|<span data-ttu-id="1d855-129">Logická hodnota, která určuje, zda se připojení využívající zprávy WS-Reliable pokusí znovu připojit po selhání přenosu.</span><span class="sxs-lookup"><span data-stu-id="1d855-129">A Boolean value that specifies whether connections using WS-Reliable messaging will attempt to reconnect after transport failures.</span></span> <span data-ttu-id="1d855-130">Výchozí hodnota je `true`, což znamená, že došlo k pokusu o nekonečné pokusy o opětovné připojení.</span><span class="sxs-lookup"><span data-stu-id="1d855-130">The default is `true`, which means that infinite attempts to reconnect are attempted.</span></span> <span data-ttu-id="1d855-131">Cyklus je přerušen časovým limitem nečinnosti, což způsobí, že kanál vyvolá výjimku, když se nedá znovu připojit.</span><span class="sxs-lookup"><span data-stu-id="1d855-131">The cycle is broken by the inactivity time-out, which causes the channel to throw an exception when it cannot be reconnected.</span></span>|  
|`replayCacheSize`|<span data-ttu-id="1d855-132">Kladné celé číslo, které určuje počet hodnot náhodně generovaných identifikátorů v mezipaměti používaných pro detekci opakovaného přehrání.</span><span class="sxs-lookup"><span data-stu-id="1d855-132">A positive integer that specifies the number of cached nonces used for replay detection.</span></span> <span data-ttu-id="1d855-133">Pokud je tento limit překročen, je odebrána nejstarší hodnota nonce a pro novou zprávu je vytvořena nová hodnota nonce.</span><span class="sxs-lookup"><span data-stu-id="1d855-133">If this limit is exceeded, the oldest nonce is removed and a new nonce is created for the new message.</span></span> <span data-ttu-id="1d855-134">Výchozí hodnota je 500000.</span><span class="sxs-lookup"><span data-stu-id="1d855-134">The default value is 500000.</span></span>|  
|`replayWindow`|<span data-ttu-id="1d855-135">A <xref:System.TimeSpan> určuje dobu, po kterou jsou jednotlivé náhodně generované identifikátory zprávy platné.</span><span class="sxs-lookup"><span data-stu-id="1d855-135">A <xref:System.TimeSpan> that specifies the duration in which individual message nonces are valid.</span></span><br /><br /> <span data-ttu-id="1d855-136">Po uplynutí této doby nebude přijata zpráva odeslaná se stejnou hodnota nonce jako ta, která byla odeslána před.</span><span class="sxs-lookup"><span data-stu-id="1d855-136">After this duration, a message sent with the same nonce as the one sent before will not be accepted.</span></span> <span data-ttu-id="1d855-137">Tento atribut se používá společně s `maxClockSkew` atributem, aby se zabránilo útokům přes opakované přehrání.</span><span class="sxs-lookup"><span data-stu-id="1d855-137">This attribute is used in conjunction with the `maxClockSkew` attribute to prevent replay attacks.</span></span> <span data-ttu-id="1d855-138">Útočník může znovu přehrát zprávu po vypršení platnosti jejího okna opětovného přehrání.</span><span class="sxs-lookup"><span data-stu-id="1d855-138">An attacker could replay a message after its replay window has expired.</span></span> <span data-ttu-id="1d855-139">Tato zpráva však selže při selhání `maxClockSkew` testu, který odmítne zprávy s časovými razítky času odeslání až do určeného času později nebo dříve, než čas, kdy byla zpráva přijata.</span><span class="sxs-lookup"><span data-stu-id="1d855-139">This message, however, would fail the `maxClockSkew` test which rejects messages with send-time timestamps up to a specified time later or earlier than the time the message was received.</span></span>|  
|`sessionKeyRenewalInterval`|<span data-ttu-id="1d855-140">A <xref:System.TimeSpan> určuje dobu, po které iniciátor obnoví klíč pro relaci zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="1d855-140">A <xref:System.TimeSpan> that specifies the duration after which the initiator will renew the key for the security session.</span></span> <span data-ttu-id="1d855-141">Výchozí hodnota je "10:00:00".</span><span class="sxs-lookup"><span data-stu-id="1d855-141">The default is "10:00:00".</span></span>|  
|`sessionKeyRolloverInterval`|<span data-ttu-id="1d855-142">A <xref:System.TimeSpan> určuje časový interval, po který je klíč předchozí relace platný pro příchozí zprávy během obnovování klíče.</span><span class="sxs-lookup"><span data-stu-id="1d855-142">A <xref:System.TimeSpan> that specifies the time interval a previous session key is valid on incoming messages during a key renewal.</span></span> <span data-ttu-id="1d855-143">Výchozí hodnota je "00:05:00".</span><span class="sxs-lookup"><span data-stu-id="1d855-143">The default is "00:05:00".</span></span><br /><br /> <span data-ttu-id="1d855-144">Během obnovování klíče musí klient a server vždy odesílat zprávy pomocí nejaktuálnějšího dostupného klíče.</span><span class="sxs-lookup"><span data-stu-id="1d855-144">During key renewal, the client and server must always send messages using the most current available key.</span></span> <span data-ttu-id="1d855-145">Obě strany budou přijímat příchozí zprávy zabezpečené s předchozí klíčovou relací, dokud nevyprší doba přeběhu.</span><span class="sxs-lookup"><span data-stu-id="1d855-145">Both parties will accept incoming messages secured with the previous session key until the rollover time expires.</span></span>|  
|`timestampValidityDuration`|<span data-ttu-id="1d855-146">Kladná <xref:System.TimeSpan> hodnota, která určuje dobu, po kterou je časové razítko platné.</span><span class="sxs-lookup"><span data-stu-id="1d855-146">A positive <xref:System.TimeSpan> that specifies the duration in which a time stamp is valid.</span></span> <span data-ttu-id="1d855-147">Výchozí hodnota je "00:15:00".</span><span class="sxs-lookup"><span data-stu-id="1d855-147">The default is "00:15:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1d855-148">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1d855-148">Child Elements</span></span>  
 <span data-ttu-id="1d855-149">Žádné</span><span class="sxs-lookup"><span data-stu-id="1d855-149">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1d855-150">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1d855-150">Parent Elements</span></span>  
  
|<span data-ttu-id="1d855-151">Prvek</span><span class="sxs-lookup"><span data-stu-id="1d855-151">Element</span></span>|<span data-ttu-id="1d855-152">Popis</span><span class="sxs-lookup"><span data-stu-id="1d855-152">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1d855-153">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="1d855-153">\<security></span></span>](security-of-custombinding.md)|<span data-ttu-id="1d855-154">Určuje možnosti zabezpečení pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="1d855-154">Specifies the security options for a custom binding.</span></span>|  
|[<span data-ttu-id="1d855-155">\<secureConversationBootstrap></span><span class="sxs-lookup"><span data-stu-id="1d855-155">\<secureConversationBootstrap></span></span>](secureconversationbootstrap.md)|<span data-ttu-id="1d855-156">Určuje výchozí hodnoty, které se použijí při inicializaci služby zabezpečené konverzace.</span><span class="sxs-lookup"><span data-stu-id="1d855-156">Specifies the default values used for initiating a secure conversation service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d855-157">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1d855-157">Remarks</span></span>  
 <span data-ttu-id="1d855-158">Nastavení jsou místní v tom smyslu, že nejsou nastavení odvozená ze zásad zabezpečení služby.</span><span class="sxs-lookup"><span data-stu-id="1d855-158">The settings are local in the sense that they are not settings derived from the security policy of the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d855-159">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1d855-159">See also</span></span>

- <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.LocalClientSettings%2A>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A>
- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="1d855-160">Vazby</span><span class="sxs-lookup"><span data-stu-id="1d855-160">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="1d855-161">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="1d855-161">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="1d855-162">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="1d855-162">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="1d855-163">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="1d855-163">\<customBinding></span></span>](custombinding.md)
- [<span data-ttu-id="1d855-164">Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="1d855-164">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="1d855-165">Zabezpečení vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="1d855-165">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
