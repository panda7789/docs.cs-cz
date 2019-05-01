---
title: AppDomainInfo
ms.date: 03/30/2017
ms.assetid: 6610b7d8-81eb-4bec-a543-9b72ad7b6f73
ms.openlocfilehash: 0b7f8aadbd9a9dfcdd33fc65be3a5a41ea95f5be
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61964252"
---
# <a name="appdomaininfo"></a><span data-ttu-id="d203e-102">AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="d203e-102">AppDomainInfo</span></span>
<span data-ttu-id="d203e-103">Informace o domény aplikace</span><span class="sxs-lookup"><span data-stu-id="d203e-103">Application domain information</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d203e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d203e-104">Syntax</span></span>  
  
```csharp
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
  
## <a name="methods"></a><span data-ttu-id="d203e-105">Metody</span><span class="sxs-lookup"><span data-stu-id="d203e-105">Methods</span></span>  
 <span data-ttu-id="d203e-106">Třída AppDomainInfo nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="d203e-106">The AppDomainInfo class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d203e-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="d203e-107">Properties</span></span>  
 <span data-ttu-id="d203e-108">Třída AppDomainInfo má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="d203e-108">The AppDomainInfo class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="d203e-109">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="d203e-109">AppDomainId</span></span>  
 <span data-ttu-id="d203e-110">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="d203e-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="d203e-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d203e-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d203e-112">Id domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="d203e-112">The Id of the appdomain.</span></span>  
  
### <a name="isdefault"></a><span data-ttu-id="d203e-113">IsDefault</span><span class="sxs-lookup"><span data-stu-id="d203e-113">IsDefault</span></span>  
 <span data-ttu-id="d203e-114">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="d203e-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="d203e-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d203e-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d203e-116">Označuje, zda je doména appdomain výchozí.</span><span class="sxs-lookup"><span data-stu-id="d203e-116">Indicates whether the appdomain is the default appdomain.</span></span>  
  
### <a name="logmalformedmessages"></a><span data-ttu-id="d203e-117">LogMalformedMessages</span><span class="sxs-lookup"><span data-stu-id="d203e-117">LogMalformedMessages</span></span>  
 <span data-ttu-id="d203e-118">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="d203e-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="d203e-119">Typ přístupu: Čtení/zápisu</span><span class="sxs-lookup"><span data-stu-id="d203e-119">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="d203e-120">Hodnota, která určuje, zda jsou špatně vytvořené zprávy zaznamenány.</span><span class="sxs-lookup"><span data-stu-id="d203e-120">A value that specifies whether malformed messages are logged.</span></span>  
  
### <a name="logmessagesatservicelevel"></a><span data-ttu-id="d203e-121">LogMessagesAtServiceLevel</span><span class="sxs-lookup"><span data-stu-id="d203e-121">LogMessagesAtServiceLevel</span></span>  
 <span data-ttu-id="d203e-122">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="d203e-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="d203e-123">Typ přístupu: Čtení/zápisu</span><span class="sxs-lookup"><span data-stu-id="d203e-123">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="d203e-124">Hodnota, která určuje, zda jsou zprávy trasovány na úrovni služby (před šifrování a týkají).</span><span class="sxs-lookup"><span data-stu-id="d203e-124">A value that specifies whether messages are traced at the service level (before encryption and transport-related transforms).</span></span>  
  
### <a name="logmessagesattransportlevel"></a><span data-ttu-id="d203e-125">LogMessagesAtTransportLevel</span><span class="sxs-lookup"><span data-stu-id="d203e-125">LogMessagesAtTransportLevel</span></span>  
 <span data-ttu-id="d203e-126">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="d203e-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="d203e-127">Typ přístupu: Čtení/zápisu</span><span class="sxs-lookup"><span data-stu-id="d203e-127">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="d203e-128">Hodnota, která určuje, zda jsou zprávy trasovány na úrovni přenosu.</span><span class="sxs-lookup"><span data-stu-id="d203e-128">A value that specifies whether messages are traced at the transport level.</span></span>  
  
### <a name="messageloggingtracelisteners"></a><span data-ttu-id="d203e-129">MessageLoggingTraceListeners</span><span class="sxs-lookup"><span data-stu-id="d203e-129">MessageLoggingTraceListeners</span></span>  
 <span data-ttu-id="d203e-130">Datový typ: TraceListener pole</span><span class="sxs-lookup"><span data-stu-id="d203e-130">Data type: TraceListener array</span></span>  
  
 <span data-ttu-id="d203e-131">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d203e-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d203e-132">Kolekce naslouchací procesy trasování, kteří poslouchají zdroj trasování System.Wmi.MessageLogging.</span><span class="sxs-lookup"><span data-stu-id="d203e-132">The collection trace listeners that listen to the System.Wmi.MessageLogging trace source.</span></span>  
  
### <a name="name"></a><span data-ttu-id="d203e-133">Název</span><span class="sxs-lookup"><span data-stu-id="d203e-133">Name</span></span>  
 <span data-ttu-id="d203e-134">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="d203e-134">Data type: string</span></span>  
  
 <span data-ttu-id="d203e-135">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d203e-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d203e-136">Název domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="d203e-136">The name of the appdomain.</span></span>  
  
### <a name="performancecounters"></a><span data-ttu-id="d203e-137">PerformanceCounters</span><span class="sxs-lookup"><span data-stu-id="d203e-137">PerformanceCounters</span></span>  
 <span data-ttu-id="d203e-138">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="d203e-138">Data type: string</span></span>  
  
 <span data-ttu-id="d203e-139">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d203e-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d203e-140">Rozsah počítačů aktivního výkonu v doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="d203e-140">The scope of active performance counters in the appdomain.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="d203e-141">ID procesu</span><span class="sxs-lookup"><span data-stu-id="d203e-141">ProcessId</span></span>  
 <span data-ttu-id="d203e-142">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="d203e-142">Data type: sint32</span></span>  
  
 <span data-ttu-id="d203e-143">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d203e-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d203e-144">ID procesu.</span><span class="sxs-lookup"><span data-stu-id="d203e-144">The process Id.</span></span>  
  
### <a name="serviceconfigpath"></a><span data-ttu-id="d203e-145">ServiceConfigPath</span><span class="sxs-lookup"><span data-stu-id="d203e-145">ServiceConfigPath</span></span>  
 <span data-ttu-id="d203e-146">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="d203e-146">Data type: string</span></span>  
  
 <span data-ttu-id="d203e-147">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d203e-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d203e-148">Cesta ke konfiguraci této služby.</span><span class="sxs-lookup"><span data-stu-id="d203e-148">The path to the configuration of the service.</span></span>  
  
### <a name="tracelevel"></a><span data-ttu-id="d203e-149">TraceLevel</span><span class="sxs-lookup"><span data-stu-id="d203e-149">TraceLevel</span></span>  
 <span data-ttu-id="d203e-150">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="d203e-150">Data type: string</span></span>  
  
 <span data-ttu-id="d203e-151">Typ přístupu: Čtení/zápisu</span><span class="sxs-lookup"><span data-stu-id="d203e-151">Access type: Read/Write</span></span>  
  
 <span data-ttu-id="d203e-152">Úroveň trasování System.Wmi zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="d203e-152">The trace level of the System.Wmi trace source.</span></span>  
  
### <a name="servicemodeltracelisteners"></a><span data-ttu-id="d203e-153">ServiceModelTraceListeners</span><span class="sxs-lookup"><span data-stu-id="d203e-153">ServiceModelTraceListeners</span></span>  
 <span data-ttu-id="d203e-154">Datový typ: TraceListener pole</span><span class="sxs-lookup"><span data-stu-id="d203e-154">Data type: TraceListener array</span></span>  
  
 <span data-ttu-id="d203e-155">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d203e-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d203e-156">Kolekce naslouchacích procesů trasování zdrojem System.ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="d203e-156">A collection of listeners from the System.ServiceModel trace source.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d203e-157">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d203e-157">Requirements</span></span>  
  
|<span data-ttu-id="d203e-158">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="d203e-158">MOF</span></span>|<span data-ttu-id="d203e-159">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="d203e-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="d203e-160">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="d203e-160">Namespace</span></span>|<span data-ttu-id="d203e-161">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d203e-161">Defined in root\ServiceModel</span></span>|
