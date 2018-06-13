---
title: AppDomainInfo
ms.date: 03/30/2017
ms.assetid: 6610b7d8-81eb-4bec-a543-9b72ad7b6f73
ms.openlocfilehash: 7189448a930298837089cf3ac2743cb7e073ae02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486978"
---
# <a name="appdomaininfo"></a><span data-ttu-id="6fd7f-102">AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="6fd7f-102">AppDomainInfo</span></span>
<span data-ttu-id="6fd7f-103">Informace o doméně aplikace</span><span class="sxs-lookup"><span data-stu-id="6fd7f-103">Application domain information</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fd7f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6fd7f-104">Syntax</span></span>  
  
```  
class AppDomainInfo  
{  
  sint32 AppDomainId;  
  boolean IsDefault;  
  boolean LogMalformedMessages;  
  boolean LogMessagesAtServiceLevel;  
  boolean LogMessagesAtTransportLevel;  
  TraceListener MessageLoggingTraceListeners[];  
  string Name;  
  string PerformanceCounters;  
  sint32 ProcessId;  
  string ServiceConfigPath;  
  string TraceLevel;  
  TraceListener wmiTraceListeners[];  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="6fd7f-105">Metody</span><span class="sxs-lookup"><span data-stu-id="6fd7f-105">Methods</span></span>  
 <span data-ttu-id="6fd7f-106">Třída AppDomainInfo nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="6fd7f-106">The AppDomainInfo class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="6fd7f-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="6fd7f-107">Properties</span></span>  
 <span data-ttu-id="6fd7f-108">Třída AppDomainInfo má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="6fd7f-108">The AppDomainInfo class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="6fd7f-109">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="6fd7f-109">AppDomainId</span></span>  
 <span data-ttu-id="6fd7f-110">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="6fd7f-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="6fd7f-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="6fd7f-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6fd7f-112">Id domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="6fd7f-112">The Id of the appdomain.</span></span>  
  
### <a name="isdefault"></a><span data-ttu-id="6fd7f-113">IsDefault</span><span class="sxs-lookup"><span data-stu-id="6fd7f-113">IsDefault</span></span>  
 <span data-ttu-id="6fd7f-114">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="6fd7f-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="6fd7f-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="6fd7f-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6fd7f-116">Určuje, zda domény aplikace je výchozí domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="6fd7f-116">Indicates whether the appdomain is the default appdomain.</span></span>  
  
### <a name="logmalformedmessages"></a><span data-ttu-id="6fd7f-117">LogMalformedMessages</span><span class="sxs-lookup"><span data-stu-id="6fd7f-117">LogMalformedMessages</span></span>  
 <span data-ttu-id="6fd7f-118">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="6fd7f-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="6fd7f-119">Přístup k typu: čtení/zápisu</span><span class="sxs-lookup"><span data-stu-id="6fd7f-119">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="6fd7f-120">Hodnota, která určuje, zda mají být protokolovány poškozených zpráv.</span><span class="sxs-lookup"><span data-stu-id="6fd7f-120">A value that specifies whether malformed messages are logged.</span></span>  
  
### <a name="logmessagesatservicelevel"></a><span data-ttu-id="6fd7f-121">LogMessagesAtServiceLevel</span><span class="sxs-lookup"><span data-stu-id="6fd7f-121">LogMessagesAtServiceLevel</span></span>  
 <span data-ttu-id="6fd7f-122">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="6fd7f-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="6fd7f-123">Přístup k typu: čtení/zápisu</span><span class="sxs-lookup"><span data-stu-id="6fd7f-123">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="6fd7f-124">Hodnota, která určuje, zda jsou zprávy nalezeny na úrovni služby (před šifrování a související přenosu transformací).</span><span class="sxs-lookup"><span data-stu-id="6fd7f-124">A value that specifies whether messages are traced at the service level (before encryption and transport-related transforms).</span></span>  
  
### <a name="logmessagesattransportlevel"></a><span data-ttu-id="6fd7f-125">LogMessagesAtTransportLevel</span><span class="sxs-lookup"><span data-stu-id="6fd7f-125">LogMessagesAtTransportLevel</span></span>  
 <span data-ttu-id="6fd7f-126">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="6fd7f-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="6fd7f-127">Přístup k typu: čtení/zápisu</span><span class="sxs-lookup"><span data-stu-id="6fd7f-127">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="6fd7f-128">Hodnota, která určuje, zda jsou zprávy nalezeny na úrovni přenosu.</span><span class="sxs-lookup"><span data-stu-id="6fd7f-128">A value that specifies whether messages are traced at the transport level.</span></span>  
  
### <a name="messageloggingtracelisteners"></a><span data-ttu-id="6fd7f-129">MessageLoggingTraceListeners</span><span class="sxs-lookup"><span data-stu-id="6fd7f-129">MessageLoggingTraceListeners</span></span>  
 <span data-ttu-id="6fd7f-130">Datový typ: TraceListener pole</span><span class="sxs-lookup"><span data-stu-id="6fd7f-130">Data type: TraceListener array</span></span>  
  
 <span data-ttu-id="6fd7f-131">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="6fd7f-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6fd7f-132">Kolekce naslouchací procesy trasování které naslouchání zdroje System.Wmi.MessageLogging trasování.</span><span class="sxs-lookup"><span data-stu-id="6fd7f-132">The collection trace listeners that listen to the System.Wmi.MessageLogging trace source.</span></span>  
  
### <a name="name"></a><span data-ttu-id="6fd7f-133">Název</span><span class="sxs-lookup"><span data-stu-id="6fd7f-133">Name</span></span>  
 <span data-ttu-id="6fd7f-134">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="6fd7f-134">Data type: string</span></span>  
  
 <span data-ttu-id="6fd7f-135">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="6fd7f-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6fd7f-136">Název domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="6fd7f-136">The name of the appdomain.</span></span>  
  
### <a name="performancecounters"></a><span data-ttu-id="6fd7f-137">čítače výkonu</span><span class="sxs-lookup"><span data-stu-id="6fd7f-137">PerformanceCounters</span></span>  
 <span data-ttu-id="6fd7f-138">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="6fd7f-138">Data type: string</span></span>  
  
 <span data-ttu-id="6fd7f-139">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="6fd7f-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6fd7f-140">Rozsah čítače výkonu active do domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="6fd7f-140">The scope of active performance counters in the appdomain.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="6fd7f-141">ID procesu</span><span class="sxs-lookup"><span data-stu-id="6fd7f-141">ProcessId</span></span>  
 <span data-ttu-id="6fd7f-142">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="6fd7f-142">Data type: sint32</span></span>  
  
 <span data-ttu-id="6fd7f-143">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="6fd7f-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6fd7f-144">ID procesu</span><span class="sxs-lookup"><span data-stu-id="6fd7f-144">The process Id.</span></span>  
  
### <a name="serviceconfigpath"></a><span data-ttu-id="6fd7f-145">ServiceConfigPath</span><span class="sxs-lookup"><span data-stu-id="6fd7f-145">ServiceConfigPath</span></span>  
 <span data-ttu-id="6fd7f-146">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="6fd7f-146">Data type: string</span></span>  
  
 <span data-ttu-id="6fd7f-147">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="6fd7f-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6fd7f-148">Cesta ke konfiguraci služby.</span><span class="sxs-lookup"><span data-stu-id="6fd7f-148">The path to the configuration of the service.</span></span>  
  
### <a name="tracelevel"></a><span data-ttu-id="6fd7f-149">TraceLevel</span><span class="sxs-lookup"><span data-stu-id="6fd7f-149">TraceLevel</span></span>  
 <span data-ttu-id="6fd7f-150">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="6fd7f-150">Data type: string</span></span>  
  
 <span data-ttu-id="6fd7f-151">Přístup k typu: čtení/zápisu</span><span class="sxs-lookup"><span data-stu-id="6fd7f-151">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="6fd7f-152">Úroveň trasování System.Wmi zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="6fd7f-152">The trace level of the System.Wmi trace source.</span></span>  
  
### <a name="servicemodeltracelisteners"></a><span data-ttu-id="6fd7f-153">ServiceModelTraceListeners</span><span class="sxs-lookup"><span data-stu-id="6fd7f-153">ServiceModelTraceListeners</span></span>  
 <span data-ttu-id="6fd7f-154">Datový typ: TraceListener pole</span><span class="sxs-lookup"><span data-stu-id="6fd7f-154">Data type: TraceListener array</span></span>  
  
 <span data-ttu-id="6fd7f-155">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="6fd7f-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="6fd7f-156">Kolekce ve zdroji System.ServiceModel trasování – moduly naslouchání.</span><span class="sxs-lookup"><span data-stu-id="6fd7f-156">A collection of listeners from the System.ServiceModel trace source.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6fd7f-157">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6fd7f-157">Requirements</span></span>  
  
|<span data-ttu-id="6fd7f-158">MOF</span><span class="sxs-lookup"><span data-stu-id="6fd7f-158">MOF</span></span>|<span data-ttu-id="6fd7f-159">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="6fd7f-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="6fd7f-160">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="6fd7f-160">Namespace</span></span>|<span data-ttu-id="6fd7f-161">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="6fd7f-161">Defined in root\ServiceModel</span></span>|
