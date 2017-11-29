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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 97818cf1fc6fa1c59b8b0eeaab69a73b21360151
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="appdomaininfo"></a><span data-ttu-id="74bfc-102">AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="74bfc-102">AppDomainInfo</span></span>
<span data-ttu-id="74bfc-103">Informace o doméně aplikace</span><span class="sxs-lookup"><span data-stu-id="74bfc-103">Application domain information</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74bfc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="74bfc-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="74bfc-105">Metody</span><span class="sxs-lookup"><span data-stu-id="74bfc-105">Methods</span></span>  
 <span data-ttu-id="74bfc-106">Třída AppDomainInfo nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="74bfc-106">The AppDomainInfo class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="74bfc-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="74bfc-107">Properties</span></span>  
 <span data-ttu-id="74bfc-108">Třída AppDomainInfo má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="74bfc-108">The AppDomainInfo class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="74bfc-109">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="74bfc-109">AppDomainId</span></span>  
 <span data-ttu-id="74bfc-110">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="74bfc-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="74bfc-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="74bfc-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="74bfc-112">Id domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="74bfc-112">The Id of the appdomain.</span></span>  
  
### <a name="isdefault"></a><span data-ttu-id="74bfc-113">IsDefault</span><span class="sxs-lookup"><span data-stu-id="74bfc-113">IsDefault</span></span>  
 <span data-ttu-id="74bfc-114">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="74bfc-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="74bfc-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="74bfc-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="74bfc-116">Určuje, zda domény aplikace je výchozí domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="74bfc-116">Indicates whether the appdomain is the default appdomain.</span></span>  
  
### <a name="logmalformedmessages"></a><span data-ttu-id="74bfc-117">LogMalformedMessages</span><span class="sxs-lookup"><span data-stu-id="74bfc-117">LogMalformedMessages</span></span>  
 <span data-ttu-id="74bfc-118">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="74bfc-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="74bfc-119">Přístup k typu: čtení/zápisu</span><span class="sxs-lookup"><span data-stu-id="74bfc-119">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="74bfc-120">Hodnota, která určuje, zda mají být protokolovány poškozených zpráv.</span><span class="sxs-lookup"><span data-stu-id="74bfc-120">A value that specifies whether malformed messages are logged.</span></span>  
  
### <a name="logmessagesatservicelevel"></a><span data-ttu-id="74bfc-121">LogMessagesAtServiceLevel</span><span class="sxs-lookup"><span data-stu-id="74bfc-121">LogMessagesAtServiceLevel</span></span>  
 <span data-ttu-id="74bfc-122">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="74bfc-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="74bfc-123">Přístup k typu: čtení/zápisu</span><span class="sxs-lookup"><span data-stu-id="74bfc-123">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="74bfc-124">Hodnota, která určuje, zda jsou zprávy nalezeny na úrovni služby (před šifrování a související přenosu transformací).</span><span class="sxs-lookup"><span data-stu-id="74bfc-124">A value that specifies whether messages are traced at the service level (before encryption and transport-related transforms).</span></span>  
  
### <a name="logmessagesattransportlevel"></a><span data-ttu-id="74bfc-125">LogMessagesAtTransportLevel</span><span class="sxs-lookup"><span data-stu-id="74bfc-125">LogMessagesAtTransportLevel</span></span>  
 <span data-ttu-id="74bfc-126">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="74bfc-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="74bfc-127">Přístup k typu: čtení/zápisu</span><span class="sxs-lookup"><span data-stu-id="74bfc-127">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="74bfc-128">Hodnota, která určuje, zda jsou zprávy nalezeny na úrovni přenosu.</span><span class="sxs-lookup"><span data-stu-id="74bfc-128">A value that specifies whether messages are traced at the transport level.</span></span>  
  
### <a name="messageloggingtracelisteners"></a><span data-ttu-id="74bfc-129">MessageLoggingTraceListeners</span><span class="sxs-lookup"><span data-stu-id="74bfc-129">MessageLoggingTraceListeners</span></span>  
 <span data-ttu-id="74bfc-130">Datový typ: TraceListener pole</span><span class="sxs-lookup"><span data-stu-id="74bfc-130">Data type: TraceListener array</span></span>  
  
 <span data-ttu-id="74bfc-131">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="74bfc-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="74bfc-132">Kolekce naslouchací procesy trasování které naslouchání zdroje System.Wmi.MessageLogging trasování.</span><span class="sxs-lookup"><span data-stu-id="74bfc-132">The collection trace listeners that listen to the System.Wmi.MessageLogging trace source.</span></span>  
  
### <a name="name"></a><span data-ttu-id="74bfc-133">Název</span><span class="sxs-lookup"><span data-stu-id="74bfc-133">Name</span></span>  
 <span data-ttu-id="74bfc-134">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="74bfc-134">Data type: string</span></span>  
  
 <span data-ttu-id="74bfc-135">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="74bfc-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="74bfc-136">Název domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="74bfc-136">The name of the appdomain.</span></span>  
  
### <a name="performancecounters"></a><span data-ttu-id="74bfc-137">čítače výkonu</span><span class="sxs-lookup"><span data-stu-id="74bfc-137">PerformanceCounters</span></span>  
 <span data-ttu-id="74bfc-138">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="74bfc-138">Data type: string</span></span>  
  
 <span data-ttu-id="74bfc-139">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="74bfc-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="74bfc-140">Rozsah čítače výkonu active do domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="74bfc-140">The scope of active performance counters in the appdomain.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="74bfc-141">ID procesu</span><span class="sxs-lookup"><span data-stu-id="74bfc-141">ProcessId</span></span>  
 <span data-ttu-id="74bfc-142">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="74bfc-142">Data type: sint32</span></span>  
  
 <span data-ttu-id="74bfc-143">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="74bfc-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="74bfc-144">ID procesu</span><span class="sxs-lookup"><span data-stu-id="74bfc-144">The process Id.</span></span>  
  
### <a name="serviceconfigpath"></a><span data-ttu-id="74bfc-145">ServiceConfigPath</span><span class="sxs-lookup"><span data-stu-id="74bfc-145">ServiceConfigPath</span></span>  
 <span data-ttu-id="74bfc-146">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="74bfc-146">Data type: string</span></span>  
  
 <span data-ttu-id="74bfc-147">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="74bfc-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="74bfc-148">Cesta ke konfiguraci služby.</span><span class="sxs-lookup"><span data-stu-id="74bfc-148">The path to the configuration of the service.</span></span>  
  
### <a name="tracelevel"></a><span data-ttu-id="74bfc-149">TraceLevel</span><span class="sxs-lookup"><span data-stu-id="74bfc-149">TraceLevel</span></span>  
 <span data-ttu-id="74bfc-150">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="74bfc-150">Data type: string</span></span>  
  
 <span data-ttu-id="74bfc-151">Přístup k typu: čtení/zápisu</span><span class="sxs-lookup"><span data-stu-id="74bfc-151">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="74bfc-152">Úroveň trasování System.Wmi zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="74bfc-152">The trace level of the System.Wmi trace source.</span></span>  
  
### <a name="servicemodeltracelisteners"></a><span data-ttu-id="74bfc-153">ServiceModelTraceListeners</span><span class="sxs-lookup"><span data-stu-id="74bfc-153">ServiceModelTraceListeners</span></span>  
 <span data-ttu-id="74bfc-154">Datový typ: TraceListener pole</span><span class="sxs-lookup"><span data-stu-id="74bfc-154">Data type: TraceListener array</span></span>  
  
 <span data-ttu-id="74bfc-155">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="74bfc-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="74bfc-156">Kolekce ve zdroji System.ServiceModel trasování – moduly naslouchání.</span><span class="sxs-lookup"><span data-stu-id="74bfc-156">A collection of listeners from the System.ServiceModel trace source.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74bfc-157">Požadavky</span><span class="sxs-lookup"><span data-stu-id="74bfc-157">Requirements</span></span>  
  
|<span data-ttu-id="74bfc-158">MOF</span><span class="sxs-lookup"><span data-stu-id="74bfc-158">MOF</span></span>|<span data-ttu-id="74bfc-159">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="74bfc-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="74bfc-160">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="74bfc-160">Namespace</span></span>|<span data-ttu-id="74bfc-161">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="74bfc-161">Defined in root\ServiceModel</span></span>|
