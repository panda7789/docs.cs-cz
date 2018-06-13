---
title: Služba
ms.date: 03/30/2017
ms.assetid: 999806e1-6376-409e-b998-b0af391adfe7
ms.openlocfilehash: 0cfeb178e26f6c93e29210accf5d7866cc1fca02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33487144"
---
# <a name="service"></a><span data-ttu-id="27251-102">Služba</span><span class="sxs-lookup"><span data-stu-id="27251-102">Service</span></span>
<span data-ttu-id="27251-103">Služba</span><span class="sxs-lookup"><span data-stu-id="27251-103">Service</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27251-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="27251-104">Syntax</span></span>  
  
```  
class Service  
{  
  string BaseAddresses[];  
  Behavior Behaviors[];  
  string ConfigurationName;  
  string CounterInstanceName;  
  string DistinguishedName;  
  string Extensions[];  
  string Metadata[];  
  string Name;  
  string Namespace;  
  datetime Opened;  
  Channel OutgoingChannels[];  
  sint32 ProcessId;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="27251-105">Metody</span><span class="sxs-lookup"><span data-stu-id="27251-105">Methods</span></span>  
 <span data-ttu-id="27251-106">Třída služby nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="27251-106">The Service class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="27251-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="27251-107">Properties</span></span>  
 <span data-ttu-id="27251-108">Třída služby má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="27251-108">The Service class has the following properties:</span></span>  
  
### <a name="baseaddresses"></a><span data-ttu-id="27251-109">BaseAddresses</span><span class="sxs-lookup"><span data-stu-id="27251-109">BaseAddresses</span></span>  
 <span data-ttu-id="27251-110">Datový typ: pole řetězců</span><span class="sxs-lookup"><span data-stu-id="27251-110">Data type: string array</span></span>  
  
 <span data-ttu-id="27251-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="27251-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="27251-112">Základní adresy používané službou.</span><span class="sxs-lookup"><span data-stu-id="27251-112">The base addresses used by the service.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="27251-113">Chování</span><span class="sxs-lookup"><span data-stu-id="27251-113">Behaviors</span></span>  
 <span data-ttu-id="27251-114">Datový typ: chování pole</span><span class="sxs-lookup"><span data-stu-id="27251-114">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="27251-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="27251-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="27251-116">Chování, které jsou spojené s touto službou.</span><span class="sxs-lookup"><span data-stu-id="27251-116">The behaviors associated with this service.</span></span>  
  
### <a name="configurationname"></a><span data-ttu-id="27251-117">ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="27251-117">ConfigurationName</span></span>  
 <span data-ttu-id="27251-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="27251-118">Data type: string</span></span>  
  
 <span data-ttu-id="27251-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="27251-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="27251-120">ServiceElement_BehaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="27251-120">ServiceElement_BehaviorConfiguration</span></span>  
  
### <a name="counterinstancename"></a><span data-ttu-id="27251-121">CounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="27251-121">CounterInstanceName</span></span>  
 <span data-ttu-id="27251-122">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="27251-122">Data type: string</span></span>  
  
 <span data-ttu-id="27251-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="27251-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="27251-124">Název instance instance čítače výkonu služby.</span><span class="sxs-lookup"><span data-stu-id="27251-124">Instance name of the instance of the performance counters of the service.</span></span>  
  
### <a name="distinguishedname"></a><span data-ttu-id="27251-125">DistinguishedName</span><span class="sxs-lookup"><span data-stu-id="27251-125">DistinguishedName</span></span>  
 <span data-ttu-id="27251-126">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="27251-126">Data type: string</span></span>  
  
 <span data-ttu-id="27251-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="27251-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="27251-128">Název služby na adrese.</span><span class="sxs-lookup"><span data-stu-id="27251-128">Service name at the address.</span></span>  
  
### <a name="extensions"></a><span data-ttu-id="27251-129">Rozšíření</span><span class="sxs-lookup"><span data-stu-id="27251-129">Extensions</span></span>  
 <span data-ttu-id="27251-130">Datový typ: pole řetězců</span><span class="sxs-lookup"><span data-stu-id="27251-130">Data type: string array</span></span>  
  
 <span data-ttu-id="27251-131">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="27251-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="27251-132">Kontexty instance pro rozšíření instance služby.</span><span class="sxs-lookup"><span data-stu-id="27251-132">The instance contexts for the extensions of the service instance.</span></span>  
  
### <a name="metadata"></a><span data-ttu-id="27251-133">Metadata</span><span class="sxs-lookup"><span data-stu-id="27251-133">Metadata</span></span>  
 <span data-ttu-id="27251-134">Datový typ: pole řetězců</span><span class="sxs-lookup"><span data-stu-id="27251-134">Data type: string array</span></span>  
  
 <span data-ttu-id="27251-135">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="27251-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="27251-136">Nastavení služby metadat.</span><span class="sxs-lookup"><span data-stu-id="27251-136">The service metadata settings.</span></span>  
  
### <a name="name"></a><span data-ttu-id="27251-137">Název</span><span class="sxs-lookup"><span data-stu-id="27251-137">Name</span></span>  
 <span data-ttu-id="27251-138">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="27251-138">Data type: string</span></span>  
  
 <span data-ttu-id="27251-139">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="27251-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="27251-140">Jedinečný název této služby.</span><span class="sxs-lookup"><span data-stu-id="27251-140">The unique name of this service.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="27251-141">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="27251-141">Namespace</span></span>  
 <span data-ttu-id="27251-142">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="27251-142">Data type: string</span></span>  
  
 <span data-ttu-id="27251-143">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="27251-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="27251-144">Obor názvů služby.</span><span class="sxs-lookup"><span data-stu-id="27251-144">The namespace of the service.</span></span>  
  
### <a name="opened"></a><span data-ttu-id="27251-145">Otevřít</span><span class="sxs-lookup"><span data-stu-id="27251-145">Opened</span></span>  
 <span data-ttu-id="27251-146">Datový typ: data a času</span><span class="sxs-lookup"><span data-stu-id="27251-146">Data type: datetime</span></span>  
  
 <span data-ttu-id="27251-147">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="27251-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="27251-148">Čas, kdy byla služba otevřena.</span><span class="sxs-lookup"><span data-stu-id="27251-148">The time the service was opened.</span></span>  
  
### <a name="outgoingchannels"></a><span data-ttu-id="27251-149">OutgoingChannels</span><span class="sxs-lookup"><span data-stu-id="27251-149">OutgoingChannels</span></span>  
 <span data-ttu-id="27251-150">Datový typ: pole Channel</span><span class="sxs-lookup"><span data-stu-id="27251-150">Data type: Channel array</span></span>  
  
 <span data-ttu-id="27251-151">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="27251-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="27251-152">Kanály, které vycházejí z instance služby.</span><span class="sxs-lookup"><span data-stu-id="27251-152">The channels that are outgoing from the service instance.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="27251-153">ID procesu</span><span class="sxs-lookup"><span data-stu-id="27251-153">ProcessId</span></span>  
 <span data-ttu-id="27251-154">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="27251-154">Data type: sint32</span></span>  
  
 <span data-ttu-id="27251-155">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="27251-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="27251-156">Id procesu procesu, který je hostitelem služby.</span><span class="sxs-lookup"><span data-stu-id="27251-156">The process id of the process that hosts the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27251-157">Požadavky</span><span class="sxs-lookup"><span data-stu-id="27251-157">Requirements</span></span>  
  
|<span data-ttu-id="27251-158">MOF</span><span class="sxs-lookup"><span data-stu-id="27251-158">MOF</span></span>|<span data-ttu-id="27251-159">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="27251-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="27251-160">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="27251-160">Namespace</span></span>|<span data-ttu-id="27251-161">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="27251-161">Defined in root\ServiceModel</span></span>|
