---
title: <localClientSettings> – element
ms.date: 03/30/2017
ms.assetid: 4680ace5-f4e1-4fcb-b9d8-a4a4af5cd7ae
ms.openlocfilehash: 3ec0394943c030a8866087c98a912682a2a2112e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400323"
---
# <a name="localclientsettings-element"></a><span data-ttu-id="59e9f-102">\<localClientSettings> – element</span><span class="sxs-lookup"><span data-stu-id="59e9f-102">\<localClientSettings> element</span></span>
<span data-ttu-id="59e9f-103">Určuje nastavení zabezpečení místního klienta pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="59e9f-103">Specifies the security settings of a local client for this binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<localClientSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="59e9f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="59e9f-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="59e9f-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="59e9f-105">Attributes and Elements</span></span>  
 <span data-ttu-id="59e9f-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="59e9f-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="59e9f-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="59e9f-107">Attributes</span></span>  
  
|<span data-ttu-id="59e9f-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="59e9f-108">Attribute</span></span>|<span data-ttu-id="59e9f-109">Popis</span><span class="sxs-lookup"><span data-stu-id="59e9f-109">Description</span></span>|  
|---------------|-----------------|  
|`cacheCookies`|<span data-ttu-id="59e9f-110">Logická hodnota, která určuje, zda je povoleno ukládání souborů cookie do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="59e9f-110">A Boolean value that specifies whether cookie caching is enabled.</span></span> <span data-ttu-id="59e9f-111">Výchozí formát je `false`.</span><span class="sxs-lookup"><span data-stu-id="59e9f-111">The default is `false`.</span></span>|  
|`cookieRenewalThresholdPercentage`|<span data-ttu-id="59e9f-112">Celé číslo, které určuje maximální procento souborů cookie, které mohou být obnoveny.</span><span class="sxs-lookup"><span data-stu-id="59e9f-112">An integer that specifies the maximum percentage of cookies that can be renewed.</span></span> <span data-ttu-id="59e9f-113">Tato hodnota by měla být mezi 0 a 100 (včetně).</span><span class="sxs-lookup"><span data-stu-id="59e9f-113">This value should be between 0 and 100 inclusively.</span></span> <span data-ttu-id="59e9f-114">Výchozí hodnota je 90.</span><span class="sxs-lookup"><span data-stu-id="59e9f-114">The default is 90.</span></span>|  
|`detectReplays`|<span data-ttu-id="59e9f-115">Logická hodnota určující, zda jsou zjištěny opakované útoky proti kanálu a zda jsou řešeny automaticky.</span><span class="sxs-lookup"><span data-stu-id="59e9f-115">A Boolean value that specifies whether replay attacks against the channel are detected and dealt with automatically.</span></span> <span data-ttu-id="59e9f-116">Výchozí formát je `false`.</span><span class="sxs-lookup"><span data-stu-id="59e9f-116">The default is `false`.</span></span>|  
|`maxClockSkew`|<span data-ttu-id="59e9f-117">A <xref:System.TimeSpan> Určuje maximální časový rozdíl mezi systémovými hodinami dvou komunikujících stran.</span><span class="sxs-lookup"><span data-stu-id="59e9f-117">A <xref:System.TimeSpan> that specifies the maximum time difference between the system clocks of the two communicating parties.</span></span> <span data-ttu-id="59e9f-118">Výchozí hodnota je "00:05:00".</span><span class="sxs-lookup"><span data-stu-id="59e9f-118">The default value is "00:05:00".</span></span><br /><br /> <span data-ttu-id="59e9f-119">Pokud je tato hodnota nastavená na výchozí hodnotu, příjemce přijímá zprávy s časovými razítky pro odeslání až 5 minut později nebo dříve, než čas, kdy byla zpráva přijata.</span><span class="sxs-lookup"><span data-stu-id="59e9f-119">When this value is set to the default, the receiver accepts messages with send-time time stamps up to 5 minutes later or earlier than the time the message was received.</span></span> <span data-ttu-id="59e9f-120">Zprávy, které nevyhověly testu při odeslání, jsou odmítnuty.</span><span class="sxs-lookup"><span data-stu-id="59e9f-120">Messages that do not pass the send-time test are rejected.</span></span> <span data-ttu-id="59e9f-121">Toto nastavení se používá ve spojení s `replayWindow` atributem.</span><span class="sxs-lookup"><span data-stu-id="59e9f-121">This setting is used in conjunction with the `replayWindow` attribute.</span></span>|  
|`maxCookieCachingTime`|<span data-ttu-id="59e9f-122">A <xref:System.TimeSpan> Určuje maximální dobu života souborů cookie.</span><span class="sxs-lookup"><span data-stu-id="59e9f-122">A <xref:System.TimeSpan> that specifies the maximum lifetime of cookies.</span></span> <span data-ttu-id="59e9f-123">Výchozí hodnota je "10675199.02:48:05.4775807".</span><span class="sxs-lookup"><span data-stu-id="59e9f-123">The default value is "10675199.02:48:05.4775807".</span></span>|  
|`reconnectTransportOnFailure`|<span data-ttu-id="59e9f-124">Logická hodnota, která určuje, zda se připojení využívající zprávy WS-Reliable pokusí znovu připojit po selhání přenosu.</span><span class="sxs-lookup"><span data-stu-id="59e9f-124">A Boolean value that specifies whether connections using WS-Reliable messaging will attempt to reconnect after transport failures.</span></span> <span data-ttu-id="59e9f-125">Výchozí hodnota je `true` , což znamená, že došlo k pokusu o nekonečné pokusy o opětovné připojení.</span><span class="sxs-lookup"><span data-stu-id="59e9f-125">The default is `true`, which means that infinite attempts to reconnect are attempted.</span></span> <span data-ttu-id="59e9f-126">Cyklus je přerušen časovým limitem nečinnosti, což způsobí, že kanál vyvolá výjimku, když se nedá znovu připojit.</span><span class="sxs-lookup"><span data-stu-id="59e9f-126">The cycle is broken by the inactivity time-out, which causes the channel to throw an exception when it cannot be reconnected.</span></span>|  
|`replayCacheSize`|<span data-ttu-id="59e9f-127">Kladné celé číslo, které určuje počet hodnot náhodně generovaných identifikátorů v mezipaměti používaných pro detekci opakovaného přehrání.</span><span class="sxs-lookup"><span data-stu-id="59e9f-127">A positive integer that specifies the number of cached nonces used for replay detection.</span></span> <span data-ttu-id="59e9f-128">Pokud je tento limit překročen, je odebrána nejstarší hodnota nonce a pro novou zprávu je vytvořena nová hodnota nonce.</span><span class="sxs-lookup"><span data-stu-id="59e9f-128">If this limit is exceeded, the oldest nonce is removed and a new nonce is created for the new message.</span></span> <span data-ttu-id="59e9f-129">Výchozí hodnota je 500000.</span><span class="sxs-lookup"><span data-stu-id="59e9f-129">The default value is 500000.</span></span>|  
|`replayWindow`|<span data-ttu-id="59e9f-130">A <xref:System.TimeSpan> Určuje dobu, po kterou jsou jednotlivé náhodně generované identifikátory zprávy platné.</span><span class="sxs-lookup"><span data-stu-id="59e9f-130">A <xref:System.TimeSpan> that specifies the duration in which individual message nonces are valid.</span></span><br /><br /> <span data-ttu-id="59e9f-131">Po uplynutí této doby nebude přijata zpráva odeslaná se stejnou hodnota nonce jako ta, která byla odeslána před.</span><span class="sxs-lookup"><span data-stu-id="59e9f-131">After this duration, a message sent with the same nonce as the one sent before will not be accepted.</span></span> <span data-ttu-id="59e9f-132">Tento atribut se používá společně s `maxClockSkew` atributem, aby se zabránilo útokům přes opakované přehrání.</span><span class="sxs-lookup"><span data-stu-id="59e9f-132">This attribute is used in conjunction with the `maxClockSkew` attribute to prevent replay attacks.</span></span> <span data-ttu-id="59e9f-133">Útočník může znovu přehrát zprávu po vypršení platnosti jejího okna opětovného přehrání.</span><span class="sxs-lookup"><span data-stu-id="59e9f-133">An attacker could replay a message after its replay window has expired.</span></span> <span data-ttu-id="59e9f-134">Tato zpráva však selže při selhání testu, `maxClockSkew` který odmítne zprávy s časovými razítky času odeslání až do určeného času později nebo dříve, než čas, kdy byla zpráva přijata.</span><span class="sxs-lookup"><span data-stu-id="59e9f-134">This message, however, would fail the `maxClockSkew` test which rejects messages with send-time timestamps up to a specified time later or earlier than the time the message was received.</span></span>|  
|`sessionKeyRenewalInterval`|<span data-ttu-id="59e9f-135">A <xref:System.TimeSpan> Určuje dobu, po které iniciátor obnoví klíč pro relaci zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="59e9f-135">A <xref:System.TimeSpan> that specifies the duration after which the initiator will renew the key for the security session.</span></span> <span data-ttu-id="59e9f-136">Výchozí hodnota je "10:00:00".</span><span class="sxs-lookup"><span data-stu-id="59e9f-136">The default is "10:00:00".</span></span>|  
|`sessionKeyRolloverInterval`|<span data-ttu-id="59e9f-137">A <xref:System.TimeSpan> Určuje časový interval, po který je klíč předchozí relace platný pro příchozí zprávy během obnovování klíče.</span><span class="sxs-lookup"><span data-stu-id="59e9f-137">A <xref:System.TimeSpan> that specifies the time interval a previous session key is valid on incoming messages during a key renewal.</span></span> <span data-ttu-id="59e9f-138">Výchozí hodnota je "00:05:00".</span><span class="sxs-lookup"><span data-stu-id="59e9f-138">The default is "00:05:00".</span></span><br /><br /> <span data-ttu-id="59e9f-139">Během obnovování klíče musí klient a server vždy odesílat zprávy pomocí nejaktuálnějšího dostupného klíče.</span><span class="sxs-lookup"><span data-stu-id="59e9f-139">During key renewal, the client and server must always send messages using the most current available key.</span></span> <span data-ttu-id="59e9f-140">Obě strany budou přijímat příchozí zprávy zabezpečené s předchozí klíčovou relací, dokud nevyprší doba přeběhu.</span><span class="sxs-lookup"><span data-stu-id="59e9f-140">Both parties will accept incoming messages secured with the previous session key until the rollover time expires.</span></span>|  
|`timestampValidityDuration`|<span data-ttu-id="59e9f-141">Kladná <xref:System.TimeSpan> hodnota, která určuje dobu, po kterou je časové razítko platné.</span><span class="sxs-lookup"><span data-stu-id="59e9f-141">A positive <xref:System.TimeSpan> that specifies the duration in which a time stamp is valid.</span></span> <span data-ttu-id="59e9f-142">Výchozí hodnota je "00:15:00".</span><span class="sxs-lookup"><span data-stu-id="59e9f-142">The default is "00:15:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="59e9f-143">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="59e9f-143">Child Elements</span></span>  
 <span data-ttu-id="59e9f-144">Žádné</span><span class="sxs-lookup"><span data-stu-id="59e9f-144">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="59e9f-145">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="59e9f-145">Parent Elements</span></span>  
  
|<span data-ttu-id="59e9f-146">Prvek</span><span class="sxs-lookup"><span data-stu-id="59e9f-146">Element</span></span>|<span data-ttu-id="59e9f-147">Description</span><span class="sxs-lookup"><span data-stu-id="59e9f-147">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-custombinding.md)|<span data-ttu-id="59e9f-148">Určuje možnosti zabezpečení pro vlastní vazbu.</span><span class="sxs-lookup"><span data-stu-id="59e9f-148">Specifies the security options for a custom binding.</span></span>|  
|[\<secureConversationBootstrap>](secureconversationbootstrap.md)|<span data-ttu-id="59e9f-149">Určuje výchozí hodnoty, které se použijí při inicializaci služby zabezpečené konverzace.</span><span class="sxs-lookup"><span data-stu-id="59e9f-149">Specifies the default values used for initiating a secure conversation service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="59e9f-150">Poznámky</span><span class="sxs-lookup"><span data-stu-id="59e9f-150">Remarks</span></span>  
 <span data-ttu-id="59e9f-151">Nastavení jsou místní v tom smyslu, že nejsou nastavení odvozená ze zásad zabezpečení služby.</span><span class="sxs-lookup"><span data-stu-id="59e9f-151">The settings are local in the sense that they are not settings derived from the security policy of the service.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59e9f-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="59e9f-152">See also</span></span>

- <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.LocalClientSettings%2A>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A>
- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="59e9f-153">Vazby</span><span class="sxs-lookup"><span data-stu-id="59e9f-153">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="59e9f-154">Rozšíření vazeb</span><span class="sxs-lookup"><span data-stu-id="59e9f-154">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="59e9f-155">Vlastní vazby</span><span class="sxs-lookup"><span data-stu-id="59e9f-155">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [<span data-ttu-id="59e9f-156">Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="59e9f-156">How to: Create a Custom Binding Using the SecurityBindingElement</span></span>](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [<span data-ttu-id="59e9f-157">Zabezpečení vlastních vazeb</span><span class="sxs-lookup"><span data-stu-id="59e9f-157">Custom Binding Security</span></span>](../../../wcf/samples/custom-binding-security.md)
