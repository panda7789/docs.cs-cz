---
title: LocalServiceSecuritySettings
ms.date: 03/30/2017
ms.assetid: 490aa0e5-5242-4f8d-b505-5ec6287633b4
author: BrucePerlerMS
ms.openlocfilehash: c79eb11fcc1973a3ef25a78afb8b141443d865c3
ms.sourcegitcommit: d88024e6d6d8b242feae5f4007a709379355aa24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2018
ms.locfileid: "49316217"
---
# <a name="localservicesecuritysettings"></a><span data-ttu-id="4e22e-102">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="4e22e-102">LocalServiceSecuritySettings</span></span>
<span data-ttu-id="4e22e-103">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="4e22e-103">LocalServiceSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e22e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4e22e-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="4e22e-105">Metody</span><span class="sxs-lookup"><span data-stu-id="4e22e-105">Methods</span></span>  
 <span data-ttu-id="4e22e-106">Třída LocalServiceSecuritySettings nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="4e22e-106">The LocalServiceSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="4e22e-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="4e22e-107">Properties</span></span>  
 <span data-ttu-id="4e22e-108">Třída LocalServiceSecuritySettings má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="4e22e-108">The LocalServiceSecuritySettings class has the following properties:</span></span>  
  
### <a name="detectreplays"></a><span data-ttu-id="4e22e-109">DetectReplays</span><span class="sxs-lookup"><span data-stu-id="4e22e-109">DetectReplays</span></span>  
 <span data-ttu-id="4e22e-110">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="4e22e-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="4e22e-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4e22e-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4e22e-112">Logická hodnota určující, zda jsou zjištěny a řešeny automaticky opakované útoky proti kanálu.</span><span class="sxs-lookup"><span data-stu-id="4e22e-112">A Boolean value that specifies whether replay attacks against the channel are detected and dealt with automatically.</span></span>  
  
### <a name="inactivitytimeout"></a><span data-ttu-id="4e22e-113">InactivityTimeout</span><span class="sxs-lookup"><span data-stu-id="4e22e-113">InactivityTimeout</span></span>  
 <span data-ttu-id="4e22e-114">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="4e22e-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="4e22e-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4e22e-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4e22e-116">Maximální počet nevyřešených bezpečnostních relací, které služba podporuje.</span><span class="sxs-lookup"><span data-stu-id="4e22e-116">The maximum number of pending security sessions that the service supports.</span></span>  
  
### <a name="issuedcookielifetime"></a><span data-ttu-id="4e22e-117">IssuedCookieLifetime</span><span class="sxs-lookup"><span data-stu-id="4e22e-117">IssuedCookieLifetime</span></span>  
 <span data-ttu-id="4e22e-118">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="4e22e-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="4e22e-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4e22e-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4e22e-120">Interval TimeSpan, který určuje životnost vydanou pro všechny nové bezpečnostní soubory cookie.</span><span class="sxs-lookup"><span data-stu-id="4e22e-120">A TimeSpan that specifies the lifetime issued to all new security cookies.</span></span>  
  
### <a name="maxcachedcookies"></a><span data-ttu-id="4e22e-121">MaxCachedCookies</span><span class="sxs-lookup"><span data-stu-id="4e22e-121">MaxCachedCookies</span></span>  
 <span data-ttu-id="4e22e-122">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="4e22e-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="4e22e-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4e22e-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4e22e-124">Maximální počet souborů cookie, které lze uložit do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="4e22e-124">The maximum number of cookies that can be cached.</span></span>  
  
### <a name="maxclockskew"></a><span data-ttu-id="4e22e-125">Maxclockskew –</span><span class="sxs-lookup"><span data-stu-id="4e22e-125">MaxClockSkew</span></span>  
 <span data-ttu-id="4e22e-126">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="4e22e-126">Data type: datetime</span></span>  
  
 <span data-ttu-id="4e22e-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4e22e-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4e22e-128">Interval TimeSpan, který určuje maximální časový rozdíl mezi systémovými hodinami dvou komunikujících stran.</span><span class="sxs-lookup"><span data-stu-id="4e22e-128">A TimeSpan that specifies the maximum time difference between the system clocks of the two communicating parties.</span></span>  
  
### <a name="maxpendingsessions"></a><span data-ttu-id="4e22e-129">MaxPendingSessions</span><span class="sxs-lookup"><span data-stu-id="4e22e-129">MaxPendingSessions</span></span>  
 <span data-ttu-id="4e22e-130">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="4e22e-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="4e22e-131">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4e22e-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4e22e-132">Maximální počet nevyřešených připojení služby.</span><span class="sxs-lookup"><span data-stu-id="4e22e-132">The maximum number of pending connections on the service.</span></span>  
  
### <a name="maxstatefulnegotiations"></a><span data-ttu-id="4e22e-133">MaxStatefulNegotiations</span><span class="sxs-lookup"><span data-stu-id="4e22e-133">MaxStatefulNegotiations</span></span>  
 <span data-ttu-id="4e22e-134">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="4e22e-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="4e22e-135">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4e22e-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4e22e-136">Počet bezpečnostních vyjednávání, které mohou být souběžně aktivní.</span><span class="sxs-lookup"><span data-stu-id="4e22e-136">The number of security negotiations that can be active concurrently.</span></span>  
  
### <a name="negotiationtimeout"></a><span data-ttu-id="4e22e-137">NegotiationTimeout</span><span class="sxs-lookup"><span data-stu-id="4e22e-137">NegotiationTimeout</span></span>  
 <span data-ttu-id="4e22e-138">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="4e22e-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="4e22e-139">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4e22e-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4e22e-140">Interval TimeSpan, který určuje maximální dobu trvání fáze bezpečnostního vyjednávání mezi serverem a klientem.</span><span class="sxs-lookup"><span data-stu-id="4e22e-140">A TimeSpan that specifies the maximum duration for the security negotiation phase between server and client.</span></span>  
  
### <a name="reconnecttransportonfailure"></a><span data-ttu-id="4e22e-141">ReconnectTransportOnFailure</span><span class="sxs-lookup"><span data-stu-id="4e22e-141">ReconnectTransportOnFailure</span></span>  
 <span data-ttu-id="4e22e-142">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="4e22e-142">Data type: boolean</span></span>  
  
 <span data-ttu-id="4e22e-143">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4e22e-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4e22e-144">Logická hodnota určující, zda připojení používající posílání WS-Reliable se pokusí znovu připojit po selhání přenosu.</span><span class="sxs-lookup"><span data-stu-id="4e22e-144">A Boolean value that specifies whether connections using WS-Reliable messaging attempt to reconnect after transport failures.</span></span>  
  
### <a name="replaycachesize"></a><span data-ttu-id="4e22e-145">ReplayCacheSize</span><span class="sxs-lookup"><span data-stu-id="4e22e-145">ReplayCacheSize</span></span>  
 <span data-ttu-id="4e22e-146">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="4e22e-146">Data type: sint32</span></span>  
  
 <span data-ttu-id="4e22e-147">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4e22e-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4e22e-148">Počet elementů v mezipaměti náhodně generované identifikátory použitých pro zjištění opakování.</span><span class="sxs-lookup"><span data-stu-id="4e22e-148">The number of cached nonces used for replay detection.</span></span>  
  
### <a name="replaywindow"></a><span data-ttu-id="4e22e-149">Třída ReplayWindow</span><span class="sxs-lookup"><span data-stu-id="4e22e-149">ReplayWindow</span></span>  
 <span data-ttu-id="4e22e-150">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="4e22e-150">Data type: datetime</span></span>  
  
 <span data-ttu-id="4e22e-151">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4e22e-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4e22e-152">Interval TimeSpan, který určuje dobu, po kterou jsou platné náhodně generované identifikátory jednotlivých zpráv.</span><span class="sxs-lookup"><span data-stu-id="4e22e-152">A TimeSpan that specifies the duration in which individual message nonces are valid.</span></span>  
  
### <a name="sessionkeyrenewalinterval"></a><span data-ttu-id="4e22e-153">SessionKeyRenewalInterval</span><span class="sxs-lookup"><span data-stu-id="4e22e-153">SessionKeyRenewalInterval</span></span>  
 <span data-ttu-id="4e22e-154">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="4e22e-154">Data type: datetime</span></span>  
  
 <span data-ttu-id="4e22e-155">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4e22e-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4e22e-156">Interval TimeSpan, který určuje dobu, po které iniciátor obnoví klíč relace zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="4e22e-156">A TimeSpan that specifies the duration after which the initiator renews the key for the security session.</span></span>  
  
### <a name="sessionkeyrolloverinterval"></a><span data-ttu-id="4e22e-157">SessionKeyRolloverInterval</span><span class="sxs-lookup"><span data-stu-id="4e22e-157">SessionKeyRolloverInterval</span></span>  
 <span data-ttu-id="4e22e-158">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="4e22e-158">Data type: datetime</span></span>  
  
 <span data-ttu-id="4e22e-159">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4e22e-159">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4e22e-160">Časový interval, který určuje časový interval klíč předchozí relace platí na příchozích zprávách během obnovení klíče.</span><span class="sxs-lookup"><span data-stu-id="4e22e-160">A TimeSpan that specifies the time interval a previous session key is valid on incoming messages during a key renewal.</span></span>  
  
### <a name="timestampvalidityduration"></a><span data-ttu-id="4e22e-161">TimestampValidityDuration</span><span class="sxs-lookup"><span data-stu-id="4e22e-161">TimestampValidityDuration</span></span>  
 <span data-ttu-id="4e22e-162">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="4e22e-162">Data type: datetime</span></span>  
  
 <span data-ttu-id="4e22e-163">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4e22e-163">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4e22e-164">Interval TimeSpan, který určuje dobu, ve kterém je platné časové razítko.</span><span class="sxs-lookup"><span data-stu-id="4e22e-164">A TimeSpan that specifies the duration in which a time stamp is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e22e-165">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4e22e-165">Requirements</span></span>  
  
|<span data-ttu-id="4e22e-166">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="4e22e-166">MOF</span></span>|<span data-ttu-id="4e22e-167">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="4e22e-167">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="4e22e-168">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="4e22e-168">Namespace</span></span>|<span data-ttu-id="4e22e-169">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4e22e-169">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4e22e-170">Viz také</span><span class="sxs-lookup"><span data-stu-id="4e22e-170">See Also</span></span>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
