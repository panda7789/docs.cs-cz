---
title: Služba
ms.date: 03/30/2017
ms.assetid: 999806e1-6376-409e-b998-b0af391adfe7
ms.openlocfilehash: c59672b3b7617d9c28d99f7d534b6e7f2f2e9fbb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991442"
---
# <a name="service"></a><span data-ttu-id="fc759-102">Služba</span><span class="sxs-lookup"><span data-stu-id="fc759-102">Service</span></span>
<span data-ttu-id="fc759-103">Služba</span><span class="sxs-lookup"><span data-stu-id="fc759-103">Service</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc759-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fc759-104">Syntax</span></span>  
  
```csharp
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
  
## <a name="methods"></a><span data-ttu-id="fc759-105">Metody</span><span class="sxs-lookup"><span data-stu-id="fc759-105">Methods</span></span>  
 <span data-ttu-id="fc759-106">Třídu služby nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="fc759-106">The Service class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="fc759-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="fc759-107">Properties</span></span>  
 <span data-ttu-id="fc759-108">Třídu služby má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="fc759-108">The Service class has the following properties:</span></span>  
  
### <a name="baseaddresses"></a><span data-ttu-id="fc759-109">BaseAddresses</span><span class="sxs-lookup"><span data-stu-id="fc759-109">BaseAddresses</span></span>  
 <span data-ttu-id="fc759-110">Datový typ: pole řetězců</span><span class="sxs-lookup"><span data-stu-id="fc759-110">Data type: string array</span></span>  
  
 <span data-ttu-id="fc759-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="fc759-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fc759-112">Základní adresy používané službou.</span><span class="sxs-lookup"><span data-stu-id="fc759-112">The base addresses used by the service.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="fc759-113">Chování</span><span class="sxs-lookup"><span data-stu-id="fc759-113">Behaviors</span></span>  
 <span data-ttu-id="fc759-114">Datový typ: Chování pole</span><span class="sxs-lookup"><span data-stu-id="fc759-114">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="fc759-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="fc759-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fc759-116">Chování, které jsou spojené s touto službou.</span><span class="sxs-lookup"><span data-stu-id="fc759-116">The behaviors associated with this service.</span></span>  
  
### <a name="configurationname"></a><span data-ttu-id="fc759-117">ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="fc759-117">ConfigurationName</span></span>  
 <span data-ttu-id="fc759-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="fc759-118">Data type: string</span></span>  
  
 <span data-ttu-id="fc759-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="fc759-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fc759-120">ServiceElement_BehaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="fc759-120">ServiceElement_BehaviorConfiguration</span></span>  
  
### <a name="counterinstancename"></a><span data-ttu-id="fc759-121">CounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="fc759-121">CounterInstanceName</span></span>  
 <span data-ttu-id="fc759-122">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="fc759-122">Data type: string</span></span>  
  
 <span data-ttu-id="fc759-123">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="fc759-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fc759-124">Instanci název instance čítače výkonu služby.</span><span class="sxs-lookup"><span data-stu-id="fc759-124">Instance name of the instance of the performance counters of the service.</span></span>  
  
### <a name="distinguishedname"></a><span data-ttu-id="fc759-125">DistinguishedName</span><span class="sxs-lookup"><span data-stu-id="fc759-125">DistinguishedName</span></span>  
 <span data-ttu-id="fc759-126">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="fc759-126">Data type: string</span></span>  
  
 <span data-ttu-id="fc759-127">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="fc759-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fc759-128">Název služby na adrese.</span><span class="sxs-lookup"><span data-stu-id="fc759-128">Service name at the address.</span></span>  
  
### <a name="extensions"></a><span data-ttu-id="fc759-129">Rozšíření</span><span class="sxs-lookup"><span data-stu-id="fc759-129">Extensions</span></span>  
 <span data-ttu-id="fc759-130">Datový typ: pole řetězců</span><span class="sxs-lookup"><span data-stu-id="fc759-130">Data type: string array</span></span>  
  
 <span data-ttu-id="fc759-131">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="fc759-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fc759-132">Kontexty instance pro rozšíření instance služby.</span><span class="sxs-lookup"><span data-stu-id="fc759-132">The instance contexts for the extensions of the service instance.</span></span>  
  
### <a name="metadata"></a><span data-ttu-id="fc759-133">Metadata</span><span class="sxs-lookup"><span data-stu-id="fc759-133">Metadata</span></span>  
 <span data-ttu-id="fc759-134">Datový typ: pole řetězců</span><span class="sxs-lookup"><span data-stu-id="fc759-134">Data type: string array</span></span>  
  
 <span data-ttu-id="fc759-135">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="fc759-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fc759-136">Nastavení metadat služby.</span><span class="sxs-lookup"><span data-stu-id="fc759-136">The service metadata settings.</span></span>  
  
### <a name="name"></a><span data-ttu-id="fc759-137">Název</span><span class="sxs-lookup"><span data-stu-id="fc759-137">Name</span></span>  
 <span data-ttu-id="fc759-138">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="fc759-138">Data type: string</span></span>  
  
 <span data-ttu-id="fc759-139">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="fc759-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fc759-140">Jedinečný název této služby.</span><span class="sxs-lookup"><span data-stu-id="fc759-140">The unique name of this service.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="fc759-141">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="fc759-141">Namespace</span></span>  
 <span data-ttu-id="fc759-142">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="fc759-142">Data type: string</span></span>  
  
 <span data-ttu-id="fc759-143">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="fc759-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fc759-144">Obor názvů služby.</span><span class="sxs-lookup"><span data-stu-id="fc759-144">The namespace of the service.</span></span>  
  
### <a name="opened"></a><span data-ttu-id="fc759-145">Otevřít</span><span class="sxs-lookup"><span data-stu-id="fc759-145">Opened</span></span>  
 <span data-ttu-id="fc759-146">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="fc759-146">Data type: datetime</span></span>  
  
 <span data-ttu-id="fc759-147">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="fc759-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fc759-148">Čas, kdy byla služba otevřena.</span><span class="sxs-lookup"><span data-stu-id="fc759-148">The time the service was opened.</span></span>  
  
### <a name="outgoingchannels"></a><span data-ttu-id="fc759-149">OutgoingChannels</span><span class="sxs-lookup"><span data-stu-id="fc759-149">OutgoingChannels</span></span>  
 <span data-ttu-id="fc759-150">Datový typ: Pole Channel</span><span class="sxs-lookup"><span data-stu-id="fc759-150">Data type: Channel array</span></span>  
  
 <span data-ttu-id="fc759-151">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="fc759-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fc759-152">Kanály, které vycházejí z instance služby.</span><span class="sxs-lookup"><span data-stu-id="fc759-152">The channels that are outgoing from the service instance.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="fc759-153">ID procesu</span><span class="sxs-lookup"><span data-stu-id="fc759-153">ProcessId</span></span>  
 <span data-ttu-id="fc759-154">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="fc759-154">Data type: sint32</span></span>  
  
 <span data-ttu-id="fc759-155">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="fc759-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fc759-156">Proces id procesu, který je hostitelem služby.</span><span class="sxs-lookup"><span data-stu-id="fc759-156">The process id of the process that hosts the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc759-157">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fc759-157">Requirements</span></span>  
  
|<span data-ttu-id="fc759-158">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="fc759-158">MOF</span></span>|<span data-ttu-id="fc759-159">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="fc759-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="fc759-160">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="fc759-160">Namespace</span></span>|<span data-ttu-id="fc759-161">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="fc759-161">Defined in root\ServiceModel</span></span>|
