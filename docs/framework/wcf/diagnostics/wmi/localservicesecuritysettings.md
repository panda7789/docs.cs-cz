---
title: LocalServiceSecuritySettings
ms.date: 03/30/2017
ms.assetid: 490aa0e5-5242-4f8d-b505-5ec6287633b4
ms.openlocfilehash: 5c68706c5dcec3a5b0ec62bb9cfbea4e1496b4f6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574596"
---
# <a name="localservicesecuritysettings"></a><span data-ttu-id="4bfb1-102">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="4bfb1-102">LocalServiceSecuritySettings</span></span>
<span data-ttu-id="4bfb1-103">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="4bfb1-103">LocalServiceSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bfb1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4bfb1-104">Syntax</span></span>  
  
```csharp
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
  
## <a name="methods"></a><span data-ttu-id="4bfb1-105">Metody</span><span class="sxs-lookup"><span data-stu-id="4bfb1-105">Methods</span></span>  
 <span data-ttu-id="4bfb1-106">Třída LocalServiceSecuritySettings nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="4bfb1-106">The LocalServiceSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="4bfb1-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="4bfb1-107">Properties</span></span>  
 <span data-ttu-id="4bfb1-108">Třída LocalServiceSecuritySettings má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="4bfb1-108">The LocalServiceSecuritySettings class has the following properties:</span></span>  
  
### <a name="detectreplays"></a><span data-ttu-id="4bfb1-109">DetectReplays</span><span class="sxs-lookup"><span data-stu-id="4bfb1-109">DetectReplays</span></span>  
 <span data-ttu-id="4bfb1-110">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="4bfb1-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="4bfb1-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4bfb1-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4bfb1-112">Logická hodnota určující, zda jsou zjištěny a řešeny automaticky opakované útoky proti kanálu.</span><span class="sxs-lookup"><span data-stu-id="4bfb1-112">A Boolean value that specifies whether replay attacks against the channel are detected and dealt with automatically.</span></span>  
  
### <a name="inactivitytimeout"></a><span data-ttu-id="4bfb1-113">InactivityTimeout</span><span class="sxs-lookup"><span data-stu-id="4bfb1-113">InactivityTimeout</span></span>  
 <span data-ttu-id="4bfb1-114">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="4bfb1-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="4bfb1-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4bfb1-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4bfb1-116">Maximální počet nevyřešených bezpečnostních relací, které služba podporuje.</span><span class="sxs-lookup"><span data-stu-id="4bfb1-116">The maximum number of pending security sessions that the service supports.</span></span>  
  
### <a name="issuedcookielifetime"></a><span data-ttu-id="4bfb1-117">IssuedCookieLifetime</span><span class="sxs-lookup"><span data-stu-id="4bfb1-117">IssuedCookieLifetime</span></span>  
 <span data-ttu-id="4bfb1-118">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="4bfb1-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="4bfb1-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4bfb1-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4bfb1-120">Interval TimeSpan, který určuje životnost vydanou pro všechny nové bezpečnostní soubory cookie.</span><span class="sxs-lookup"><span data-stu-id="4bfb1-120">A TimeSpan that specifies the lifetime issued to all new security cookies.</span></span>  
  
### <a name="maxcachedcookies"></a><span data-ttu-id="4bfb1-121">MaxCachedCookies</span><span class="sxs-lookup"><span data-stu-id="4bfb1-121">MaxCachedCookies</span></span>  
 <span data-ttu-id="4bfb1-122">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="4bfb1-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="4bfb1-123">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4bfb1-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4bfb1-124">Maximální počet souborů cookie, které lze uložit do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="4bfb1-124">The maximum number of cookies that can be cached.</span></span>  
  
### <a name="maxclockskew"></a><span data-ttu-id="4bfb1-125">MaxClockSkew</span><span class="sxs-lookup"><span data-stu-id="4bfb1-125">MaxClockSkew</span></span>  
 <span data-ttu-id="4bfb1-126">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="4bfb1-126">Data type: datetime</span></span>  
  
 <span data-ttu-id="4bfb1-127">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4bfb1-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4bfb1-128">Interval TimeSpan, který určuje maximální časový rozdíl mezi systémovými hodinami dvou komunikujících stran.</span><span class="sxs-lookup"><span data-stu-id="4bfb1-128">A TimeSpan that specifies the maximum time difference between the system clocks of the two communicating parties.</span></span>  
  
### <a name="maxpendingsessions"></a><span data-ttu-id="4bfb1-129">MaxPendingSessions</span><span class="sxs-lookup"><span data-stu-id="4bfb1-129">MaxPendingSessions</span></span>  
 <span data-ttu-id="4bfb1-130">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="4bfb1-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="4bfb1-131">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4bfb1-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4bfb1-132">Maximální počet nevyřešených připojení služby.</span><span class="sxs-lookup"><span data-stu-id="4bfb1-132">The maximum number of pending connections on the service.</span></span>  
  
### <a name="maxstatefulnegotiations"></a><span data-ttu-id="4bfb1-133">MaxStatefulNegotiations</span><span class="sxs-lookup"><span data-stu-id="4bfb1-133">MaxStatefulNegotiations</span></span>  
 <span data-ttu-id="4bfb1-134">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="4bfb1-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="4bfb1-135">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4bfb1-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4bfb1-136">Počet bezpečnostních vyjednávání, které mohou být souběžně aktivní.</span><span class="sxs-lookup"><span data-stu-id="4bfb1-136">The number of security negotiations that can be active concurrently.</span></span>  
  
### <a name="negotiationtimeout"></a><span data-ttu-id="4bfb1-137">NegotiationTimeout</span><span class="sxs-lookup"><span data-stu-id="4bfb1-137">NegotiationTimeout</span></span>  
 <span data-ttu-id="4bfb1-138">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="4bfb1-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="4bfb1-139">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4bfb1-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4bfb1-140">Interval TimeSpan, který určuje maximální dobu trvání fáze bezpečnostního vyjednávání mezi serverem a klientem.</span><span class="sxs-lookup"><span data-stu-id="4bfb1-140">A TimeSpan that specifies the maximum duration for the security negotiation phase between server and client.</span></span>  
  
### <a name="reconnecttransportonfailure"></a><span data-ttu-id="4bfb1-141">ReconnectTransportOnFailure</span><span class="sxs-lookup"><span data-stu-id="4bfb1-141">ReconnectTransportOnFailure</span></span>  
 <span data-ttu-id="4bfb1-142">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="4bfb1-142">Data type: boolean</span></span>  
  
 <span data-ttu-id="4bfb1-143">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4bfb1-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4bfb1-144">Logická hodnota určující, zda připojení používající posílání WS-Reliable se pokusí znovu připojit po selhání přenosu.</span><span class="sxs-lookup"><span data-stu-id="4bfb1-144">A Boolean value that specifies whether connections using WS-Reliable messaging attempt to reconnect after transport failures.</span></span>  
  
### <a name="replaycachesize"></a><span data-ttu-id="4bfb1-145">ReplayCacheSize</span><span class="sxs-lookup"><span data-stu-id="4bfb1-145">ReplayCacheSize</span></span>  
 <span data-ttu-id="4bfb1-146">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="4bfb1-146">Data type: sint32</span></span>  
  
 <span data-ttu-id="4bfb1-147">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4bfb1-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4bfb1-148">Počet elementů v mezipaměti náhodně generované identifikátory použitých pro zjištění opakování.</span><span class="sxs-lookup"><span data-stu-id="4bfb1-148">The number of cached nonces used for replay detection.</span></span>  
  
### <a name="replaywindow"></a><span data-ttu-id="4bfb1-149">Třída ReplayWindow</span><span class="sxs-lookup"><span data-stu-id="4bfb1-149">ReplayWindow</span></span>  
 <span data-ttu-id="4bfb1-150">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="4bfb1-150">Data type: datetime</span></span>  
  
 <span data-ttu-id="4bfb1-151">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4bfb1-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4bfb1-152">Interval TimeSpan, který určuje dobu, po kterou jsou platné náhodně generované identifikátory jednotlivých zpráv.</span><span class="sxs-lookup"><span data-stu-id="4bfb1-152">A TimeSpan that specifies the duration in which individual message nonces are valid.</span></span>  
  
### <a name="sessionkeyrenewalinterval"></a><span data-ttu-id="4bfb1-153">SessionKeyRenewalInterval</span><span class="sxs-lookup"><span data-stu-id="4bfb1-153">SessionKeyRenewalInterval</span></span>  
 <span data-ttu-id="4bfb1-154">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="4bfb1-154">Data type: datetime</span></span>  
  
 <span data-ttu-id="4bfb1-155">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4bfb1-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4bfb1-156">Interval TimeSpan, který určuje dobu, po které iniciátor obnoví klíč relace zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="4bfb1-156">A TimeSpan that specifies the duration after which the initiator renews the key for the security session.</span></span>  
  
### <a name="sessionkeyrolloverinterval"></a><span data-ttu-id="4bfb1-157">SessionKeyRolloverInterval</span><span class="sxs-lookup"><span data-stu-id="4bfb1-157">SessionKeyRolloverInterval</span></span>  
 <span data-ttu-id="4bfb1-158">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="4bfb1-158">Data type: datetime</span></span>  
  
 <span data-ttu-id="4bfb1-159">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4bfb1-159">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4bfb1-160">Časový interval, který určuje časový interval klíč předchozí relace platí na příchozích zprávách během obnovení klíče.</span><span class="sxs-lookup"><span data-stu-id="4bfb1-160">A TimeSpan that specifies the time interval a previous session key is valid on incoming messages during a key renewal.</span></span>  
  
### <a name="timestampvalidityduration"></a><span data-ttu-id="4bfb1-161">TimestampValidityDuration</span><span class="sxs-lookup"><span data-stu-id="4bfb1-161">TimestampValidityDuration</span></span>  
 <span data-ttu-id="4bfb1-162">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="4bfb1-162">Data type: datetime</span></span>  
  
 <span data-ttu-id="4bfb1-163">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4bfb1-163">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4bfb1-164">Interval TimeSpan, který určuje dobu, ve kterém je platné časové razítko.</span><span class="sxs-lookup"><span data-stu-id="4bfb1-164">A TimeSpan that specifies the duration in which a time stamp is valid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4bfb1-165">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4bfb1-165">Requirements</span></span>  
  
|<span data-ttu-id="4bfb1-166">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="4bfb1-166">MOF</span></span>|<span data-ttu-id="4bfb1-167">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="4bfb1-167">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="4bfb1-168">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="4bfb1-168">Namespace</span></span>|<span data-ttu-id="4bfb1-169">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4bfb1-169">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4bfb1-170">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4bfb1-170">See also</span></span>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
