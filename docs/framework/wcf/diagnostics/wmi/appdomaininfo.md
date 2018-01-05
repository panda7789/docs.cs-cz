---
title: AppDomainInfo
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6610b7d8-81eb-4bec-a543-9b72ad7b6f73
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ed5053dd69628a9f5ff7318ce7fe772f42de6e24
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="appdomaininfo"></a><span data-ttu-id="150cd-102">AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="150cd-102">AppDomainInfo</span></span>
<span data-ttu-id="150cd-103">Informace o doméně aplikace</span><span class="sxs-lookup"><span data-stu-id="150cd-103">Application domain information</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="150cd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="150cd-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="150cd-105">Metody</span><span class="sxs-lookup"><span data-stu-id="150cd-105">Methods</span></span>  
 <span data-ttu-id="150cd-106">Třída AppDomainInfo nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="150cd-106">The AppDomainInfo class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="150cd-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="150cd-107">Properties</span></span>  
 <span data-ttu-id="150cd-108">Třída AppDomainInfo má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="150cd-108">The AppDomainInfo class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="150cd-109">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="150cd-109">AppDomainId</span></span>  
 <span data-ttu-id="150cd-110">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="150cd-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="150cd-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="150cd-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="150cd-112">Id domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="150cd-112">The Id of the appdomain.</span></span>  
  
### <a name="isdefault"></a><span data-ttu-id="150cd-113">IsDefault</span><span class="sxs-lookup"><span data-stu-id="150cd-113">IsDefault</span></span>  
 <span data-ttu-id="150cd-114">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="150cd-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="150cd-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="150cd-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="150cd-116">Určuje, zda domény aplikace je výchozí domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="150cd-116">Indicates whether the appdomain is the default appdomain.</span></span>  
  
### <a name="logmalformedmessages"></a><span data-ttu-id="150cd-117">LogMalformedMessages</span><span class="sxs-lookup"><span data-stu-id="150cd-117">LogMalformedMessages</span></span>  
 <span data-ttu-id="150cd-118">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="150cd-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="150cd-119">Přístup k typu: čtení/zápisu</span><span class="sxs-lookup"><span data-stu-id="150cd-119">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="150cd-120">Hodnota, která určuje, zda mají být protokolovány poškozených zpráv.</span><span class="sxs-lookup"><span data-stu-id="150cd-120">A value that specifies whether malformed messages are logged.</span></span>  
  
### <a name="logmessagesatservicelevel"></a><span data-ttu-id="150cd-121">LogMessagesAtServiceLevel</span><span class="sxs-lookup"><span data-stu-id="150cd-121">LogMessagesAtServiceLevel</span></span>  
 <span data-ttu-id="150cd-122">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="150cd-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="150cd-123">Přístup k typu: čtení/zápisu</span><span class="sxs-lookup"><span data-stu-id="150cd-123">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="150cd-124">Hodnota, která určuje, zda jsou zprávy nalezeny na úrovni služby (před šifrování a související přenosu transformací).</span><span class="sxs-lookup"><span data-stu-id="150cd-124">A value that specifies whether messages are traced at the service level (before encryption and transport-related transforms).</span></span>  
  
### <a name="logmessagesattransportlevel"></a><span data-ttu-id="150cd-125">LogMessagesAtTransportLevel</span><span class="sxs-lookup"><span data-stu-id="150cd-125">LogMessagesAtTransportLevel</span></span>  
 <span data-ttu-id="150cd-126">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="150cd-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="150cd-127">Přístup k typu: čtení/zápisu</span><span class="sxs-lookup"><span data-stu-id="150cd-127">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="150cd-128">Hodnota, která určuje, zda jsou zprávy nalezeny na úrovni přenosu.</span><span class="sxs-lookup"><span data-stu-id="150cd-128">A value that specifies whether messages are traced at the transport level.</span></span>  
  
### <a name="messageloggingtracelisteners"></a><span data-ttu-id="150cd-129">MessageLoggingTraceListeners</span><span class="sxs-lookup"><span data-stu-id="150cd-129">MessageLoggingTraceListeners</span></span>  
 <span data-ttu-id="150cd-130">Datový typ: TraceListener pole</span><span class="sxs-lookup"><span data-stu-id="150cd-130">Data type: TraceListener array</span></span>  
  
 <span data-ttu-id="150cd-131">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="150cd-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="150cd-132">Kolekce naslouchací procesy trasování které naslouchání zdroje System.Wmi.MessageLogging trasování.</span><span class="sxs-lookup"><span data-stu-id="150cd-132">The collection trace listeners that listen to the System.Wmi.MessageLogging trace source.</span></span>  
  
### <a name="name"></a><span data-ttu-id="150cd-133">Název</span><span class="sxs-lookup"><span data-stu-id="150cd-133">Name</span></span>  
 <span data-ttu-id="150cd-134">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="150cd-134">Data type: string</span></span>  
  
 <span data-ttu-id="150cd-135">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="150cd-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="150cd-136">Název domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="150cd-136">The name of the appdomain.</span></span>  
  
### <a name="performancecounters"></a><span data-ttu-id="150cd-137">čítače výkonu</span><span class="sxs-lookup"><span data-stu-id="150cd-137">PerformanceCounters</span></span>  
 <span data-ttu-id="150cd-138">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="150cd-138">Data type: string</span></span>  
  
 <span data-ttu-id="150cd-139">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="150cd-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="150cd-140">Rozsah čítače výkonu active do domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="150cd-140">The scope of active performance counters in the appdomain.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="150cd-141">ID procesu</span><span class="sxs-lookup"><span data-stu-id="150cd-141">ProcessId</span></span>  
 <span data-ttu-id="150cd-142">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="150cd-142">Data type: sint32</span></span>  
  
 <span data-ttu-id="150cd-143">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="150cd-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="150cd-144">ID procesu</span><span class="sxs-lookup"><span data-stu-id="150cd-144">The process Id.</span></span>  
  
### <a name="serviceconfigpath"></a><span data-ttu-id="150cd-145">ServiceConfigPath</span><span class="sxs-lookup"><span data-stu-id="150cd-145">ServiceConfigPath</span></span>  
 <span data-ttu-id="150cd-146">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="150cd-146">Data type: string</span></span>  
  
 <span data-ttu-id="150cd-147">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="150cd-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="150cd-148">Cesta ke konfiguraci služby.</span><span class="sxs-lookup"><span data-stu-id="150cd-148">The path to the configuration of the service.</span></span>  
  
### <a name="tracelevel"></a><span data-ttu-id="150cd-149">TraceLevel</span><span class="sxs-lookup"><span data-stu-id="150cd-149">TraceLevel</span></span>  
 <span data-ttu-id="150cd-150">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="150cd-150">Data type: string</span></span>  
  
 <span data-ttu-id="150cd-151">Přístup k typu: čtení/zápisu</span><span class="sxs-lookup"><span data-stu-id="150cd-151">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="150cd-152">Úroveň trasování System.Wmi zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="150cd-152">The trace level of the System.Wmi trace source.</span></span>  
  
### <a name="servicemodeltracelisteners"></a><span data-ttu-id="150cd-153">ServiceModelTraceListeners</span><span class="sxs-lookup"><span data-stu-id="150cd-153">ServiceModelTraceListeners</span></span>  
 <span data-ttu-id="150cd-154">Datový typ: TraceListener pole</span><span class="sxs-lookup"><span data-stu-id="150cd-154">Data type: TraceListener array</span></span>  
  
 <span data-ttu-id="150cd-155">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="150cd-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="150cd-156">Kolekce ve zdroji System.ServiceModel trasování – moduly naslouchání.</span><span class="sxs-lookup"><span data-stu-id="150cd-156">A collection of listeners from the System.ServiceModel trace source.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="150cd-157">Požadavky</span><span class="sxs-lookup"><span data-stu-id="150cd-157">Requirements</span></span>  
  
|<span data-ttu-id="150cd-158">MOF</span><span class="sxs-lookup"><span data-stu-id="150cd-158">MOF</span></span>|<span data-ttu-id="150cd-159">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="150cd-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="150cd-160">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="150cd-160">Namespace</span></span>|<span data-ttu-id="150cd-161">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="150cd-161">Defined in root\ServiceModel</span></span>|
