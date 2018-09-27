---
title: LocalServiceSecuritySettings
ms.date: 03/30/2017
ms.assetid: 490aa0e5-5242-4f8d-b505-5ec6287633b4
author: BrucePerlerMS
ms.openlocfilehash: c79eb11fcc1973a3ef25a78afb8b141443d865c3
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2018
ms.locfileid: "47398862"
---
# <a name="localservicesecuritysettings"></a><span data-ttu-id="8cbd8-102">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="8cbd8-102">LocalServiceSecuritySettings</span></span>
<span data-ttu-id="8cbd8-103">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="8cbd8-103">LocalServiceSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cbd8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8cbd8-104">Syntax</span></span>  
  
```  
class LocalServiceSecuritySettings  
{  
  boolean DetectReplays;  
  datetime InactivityTimeout;  
  datetime IssuedCookieLifetime;  
  sint32 MaxCachedCookies;  
  datetime MaxClockSkew;  
  sint32 MaxPendingSessions;  
  sint32 MaxStatefulNegotiations;  
  datetime NegotiationTimeout;  
  boolean ReconnectTransportOnFailure;  
  sint32 ReplayCacheSize;  
  datetime ReplayWindow;  
  datetime SessionKeyRenewalInterval;  
  datetime SessionKeyRolloverInterval;  
  datetime TimestampValidityDuration;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="8cbd8-105">Metody</span><span class="sxs-lookup"><span data-stu-id="8cbd8-105">Methods</span></span>  
 <span data-ttu-id="8cbd8-106">Třída LocalServiceSecuritySettings nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="8cbd8-106">The LocalServiceSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="8cbd8-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="8cbd8-107">Properties</span></span>  
 <span data-ttu-id="8cbd8-108">Třída LocalServiceSecuritySettings má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="8cbd8-108">The LocalServiceSecuritySettings class has the following properties:</span></span>  
  
### <a name="detectreplays"></a><span data-ttu-id="8cbd8-109">DetectReplays</span><span class="sxs-lookup"><span data-stu-id="8cbd8-109">DetectReplays</span></span>  
 <span data-ttu-id="8cbd8-110">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="8cbd8-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="8cbd8-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="8cbd8-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8cbd8-112">Logická hodnota určující, zda jsou zjištěny a řešeny automaticky opakované útoky proti kanálu.</span><span class="sxs-lookup"><span data-stu-id="8cbd8-112">A Boolean value that specifies whether replay attacks against the channel are detected and dealt with automatically.</span></span>  
  
### <a name="inactivitytimeout"></a><span data-ttu-id="8cbd8-113">InactivityTimeout</span><span class="sxs-lookup"><span data-stu-id="8cbd8-113">InactivityTimeout</span></span>  
 <span data-ttu-id="8cbd8-114">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="8cbd8-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="8cbd8-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="8cbd8-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8cbd8-116">Maximální počet nevyřešených bezpečnostních relací, které služba podporuje.</span><span class="sxs-lookup"><span data-stu-id="8cbd8-116">The maximum number of pending security sessions that the service supports.</span></span>  
  
### <a name="issuedcookielifetime"></a><span data-ttu-id="8cbd8-117">IssuedCookieLifetime</span><span class="sxs-lookup"><span data-stu-id="8cbd8-117">IssuedCookieLifetime</span></span>  
 <span data-ttu-id="8cbd8-118">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="8cbd8-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="8cbd8-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="8cbd8-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8cbd8-120">Interval TimeSpan, který určuje životnost vydanou pro všechny nové bezpečnostní soubory cookie.</span><span class="sxs-lookup"><span data-stu-id="8cbd8-120">A TimeSpan that specifies the lifetime issued to all new security cookies.</span></span>  
  
### <a name="maxcachedcookies"></a><span data-ttu-id="8cbd8-121">MaxCachedCookies</span><span class="sxs-lookup"><span data-stu-id="8cbd8-121">MaxCachedCookies</span></span>  
 <span data-ttu-id="8cbd8-122">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="8cbd8-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="8cbd8-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="8cbd8-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8cbd8-124">Maximální počet souborů cookie, které lze uložit do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="8cbd8-124">The maximum number of cookies that can be cached.</span></span>  
  
### <a name="maxclockskew"></a><span data-ttu-id="8cbd8-125">Maxclockskew –</span><span class="sxs-lookup"><span data-stu-id="8cbd8-125">MaxClockSkew</span></span>  
 <span data-ttu-id="8cbd8-126">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="8cbd8-126">Data type: datetime</span></span>  
  
 <span data-ttu-id="8cbd8-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="8cbd8-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8cbd8-128">Interval TimeSpan, který určuje maximální časový rozdíl mezi systémovými hodinami dvou komunikujících stran.</span><span class="sxs-lookup"><span data-stu-id="8cbd8-128">A TimeSpan that specifies the maximum time difference between the system clocks of the two communicating parties.</span></span>  
  
### <a name="maxpendingsessions"></a><span data-ttu-id="8cbd8-129">MaxPendingSessions</span><span class="sxs-lookup"><span data-stu-id="8cbd8-129">MaxPendingSessions</span></span>  
 <span data-ttu-id="8cbd8-130">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="8cbd8-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="8cbd8-131">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="8cbd8-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8cbd8-132">Maximální počet nevyřešených připojení služby.</span><span class="sxs-lookup"><span data-stu-id="8cbd8-132">The maximum number of pending connections on the service.</span></span>  
  
### <a name="maxstatefulnegotiations"></a><span data-ttu-id="8cbd8-133">MaxStatefulNegotiations</span><span class="sxs-lookup"><span data-stu-id="8cbd8-133">MaxStatefulNegotiations</span></span>  
 <span data-ttu-id="8cbd8-134">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="8cbd8-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="8cbd8-135">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="8cbd8-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8cbd8-136">Počet bezpečnostních vyjednávání, které mohou být souběžně aktivní.</span><span class="sxs-lookup"><span data-stu-id="8cbd8-136">The number of security negotiations that can be active concurrently.</span></span>  
  
### <a name="negotiationtimeout"></a><span data-ttu-id="8cbd8-137">NegotiationTimeout</span><span class="sxs-lookup"><span data-stu-id="8cbd8-137">NegotiationTimeout</span></span>  
 <span data-ttu-id="8cbd8-138">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="8cbd8-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="8cbd8-139">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="8cbd8-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8cbd8-140">Interval TimeSpan, který určuje maximální dobu trvání fáze bezpečnostního vyjednávání mezi serverem a klientem.</span><span class="sxs-lookup"><span data-stu-id="8cbd8-140">A TimeSpan that specifies the maximum duration for the security negotiation phase between server and client.</span></span>  
  
### <a name="reconnecttransportonfailure"></a><span data-ttu-id="8cbd8-141">ReconnectTransportOnFailure</span><span class="sxs-lookup"><span data-stu-id="8cbd8-141">ReconnectTransportOnFailure</span></span>  
 <span data-ttu-id="8cbd8-142">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="8cbd8-142">Data type: boolean</span></span>  
  
 <span data-ttu-id="8cbd8-143">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="8cbd8-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8cbd8-144">Logická hodnota určující, zda připojení používající posílání WS-Reliable se pokusí znovu připojit po selhání přenosu.</span><span class="sxs-lookup"><span data-stu-id="8cbd8-144">A Boolean value that specifies whether connections using WS-Reliable messaging attempt to reconnect after transport failures.</span></span>  
  
### <a name="replaycachesize"></a><span data-ttu-id="8cbd8-145">ReplayCacheSize</span><span class="sxs-lookup"><span data-stu-id="8cbd8-145">ReplayCacheSize</span></span>  
 <span data-ttu-id="8cbd8-146">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="8cbd8-146">Data type: sint32</span></span>  
  
 <span data-ttu-id="8cbd8-147">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="8cbd8-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8cbd8-148">Počet elementů v mezipaměti náhodně generované identifikátory použitých pro zjištění opakování.</span><span class="sxs-lookup"><span data-stu-id="8cbd8-148">The number of cached nonces used for replay detection.</span></span>  
  
### <a name="replaywindow"></a><span data-ttu-id="8cbd8-149">Třída ReplayWindow</span><span class="sxs-lookup"><span data-stu-id="8cbd8-149">ReplayWindow</span></span>  
 <span data-ttu-id="8cbd8-150">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="8cbd8-150">Data type: datetime</span></span>  
  
 <span data-ttu-id="8cbd8-151">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="8cbd8-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8cbd8-152">Interval TimeSpan, který určuje dobu, po kterou jsou platné náhodně generované identifikátory jednotlivých zpráv.</span><span class="sxs-lookup"><span data-stu-id="8cbd8-152">A TimeSpan that specifies the duration in which individual message nonces are valid.</span></span>  
  
### <a name="sessionkeyrenewalinterval"></a><span data-ttu-id="8cbd8-153">SessionKeyRenewalInterval</span><span class="sxs-lookup"><span data-stu-id="8cbd8-153">SessionKeyRenewalInterval</span></span>  
 <span data-ttu-id="8cbd8-154">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="8cbd8-154">Data type: datetime</span></span>  
  
 <span data-ttu-id="8cbd8-155">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="8cbd8-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8cbd8-156">Interval TimeSpan, který určuje dobu, po které iniciátor obnoví klíč relace zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="8cbd8-156">A TimeSpan that specifies the duration after which the initiator renews the key for the security session.</span></span>  
  
### <a name="sessionkeyrolloverinterval"></a><span data-ttu-id="8cbd8-157">SessionKeyRolloverInterval</span><span class="sxs-lookup"><span data-stu-id="8cbd8-157">SessionKeyRolloverInterval</span></span>  
 <span data-ttu-id="8cbd8-158">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="8cbd8-158">Data type: datetime</span></span>  
  
 <span data-ttu-id="8cbd8-159">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="8cbd8-159">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8cbd8-160">Časový interval, který určuje časový interval klíč předchozí relace platí na příchozích zprávách během obnovení klíče.</span><span class="sxs-lookup"><span data-stu-id="8cbd8-160">A TimeSpan that specifies the time interval a previous session key is valid on incoming messages during a key renewal.</span></span>  
  
### <a name="timestampvalidityduration"></a><span data-ttu-id="8cbd8-161">TimestampValidityDuration</span><span class="sxs-lookup"><span data-stu-id="8cbd8-161">TimestampValidityDuration</span></span>  
 <span data-ttu-id="8cbd8-162">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="8cbd8-162">Data type: datetime</span></span>  
  
 <span data-ttu-id="8cbd8-163">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="8cbd8-163">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8cbd8-164">Interval TimeSpan, který určuje dobu, ve kterém je platné časové razítko.</span><span class="sxs-lookup"><span data-stu-id="8cbd8-164">A TimeSpan that specifies the duration in which a time stamp is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8cbd8-165">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8cbd8-165">Requirements</span></span>  
  
|<span data-ttu-id="8cbd8-166">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="8cbd8-166">MOF</span></span>|<span data-ttu-id="8cbd8-167">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="8cbd8-167">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="8cbd8-168">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="8cbd8-168">Namespace</span></span>|<span data-ttu-id="8cbd8-169">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="8cbd8-169">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8cbd8-170">Viz také</span><span class="sxs-lookup"><span data-stu-id="8cbd8-170">See Also</span></span>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
