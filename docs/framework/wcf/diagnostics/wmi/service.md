---
title: Služba
ms.date: 03/30/2017
ms.assetid: 999806e1-6376-409e-b998-b0af391adfe7
ms.openlocfilehash: c59672b3b7617d9c28d99f7d534b6e7f2f2e9fbb
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2018
ms.locfileid: "49633940"
---
# <a name="service"></a><span data-ttu-id="793b1-102">Služba</span><span class="sxs-lookup"><span data-stu-id="793b1-102">Service</span></span>
<span data-ttu-id="793b1-103">Služba</span><span class="sxs-lookup"><span data-stu-id="793b1-103">Service</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="793b1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="793b1-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="793b1-105">Metody</span><span class="sxs-lookup"><span data-stu-id="793b1-105">Methods</span></span>  
 <span data-ttu-id="793b1-106">Třídu služby nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="793b1-106">The Service class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="793b1-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="793b1-107">Properties</span></span>  
 <span data-ttu-id="793b1-108">Třídu služby má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="793b1-108">The Service class has the following properties:</span></span>  
  
### <a name="baseaddresses"></a><span data-ttu-id="793b1-109">BaseAddresses</span><span class="sxs-lookup"><span data-stu-id="793b1-109">BaseAddresses</span></span>  
 <span data-ttu-id="793b1-110">Datový typ: pole řetězců</span><span class="sxs-lookup"><span data-stu-id="793b1-110">Data type: string array</span></span>  
  
 <span data-ttu-id="793b1-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="793b1-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="793b1-112">Základní adresy používané službou.</span><span class="sxs-lookup"><span data-stu-id="793b1-112">The base addresses used by the service.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="793b1-113">Chování</span><span class="sxs-lookup"><span data-stu-id="793b1-113">Behaviors</span></span>  
 <span data-ttu-id="793b1-114">Datový typ: chování pole</span><span class="sxs-lookup"><span data-stu-id="793b1-114">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="793b1-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="793b1-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="793b1-116">Chování, které jsou spojené s touto službou.</span><span class="sxs-lookup"><span data-stu-id="793b1-116">The behaviors associated with this service.</span></span>  
  
### <a name="configurationname"></a><span data-ttu-id="793b1-117">ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="793b1-117">ConfigurationName</span></span>  
 <span data-ttu-id="793b1-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="793b1-118">Data type: string</span></span>  
  
 <span data-ttu-id="793b1-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="793b1-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="793b1-120">ServiceElement_BehaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="793b1-120">ServiceElement_BehaviorConfiguration</span></span>  
  
### <a name="counterinstancename"></a><span data-ttu-id="793b1-121">CounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="793b1-121">CounterInstanceName</span></span>  
 <span data-ttu-id="793b1-122">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="793b1-122">Data type: string</span></span>  
  
 <span data-ttu-id="793b1-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="793b1-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="793b1-124">Instanci název instance čítače výkonu služby.</span><span class="sxs-lookup"><span data-stu-id="793b1-124">Instance name of the instance of the performance counters of the service.</span></span>  
  
### <a name="distinguishedname"></a><span data-ttu-id="793b1-125">DistinguishedName</span><span class="sxs-lookup"><span data-stu-id="793b1-125">DistinguishedName</span></span>  
 <span data-ttu-id="793b1-126">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="793b1-126">Data type: string</span></span>  
  
 <span data-ttu-id="793b1-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="793b1-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="793b1-128">Název služby na adrese.</span><span class="sxs-lookup"><span data-stu-id="793b1-128">Service name at the address.</span></span>  
  
### <a name="extensions"></a><span data-ttu-id="793b1-129">Rozšíření</span><span class="sxs-lookup"><span data-stu-id="793b1-129">Extensions</span></span>  
 <span data-ttu-id="793b1-130">Datový typ: pole řetězců</span><span class="sxs-lookup"><span data-stu-id="793b1-130">Data type: string array</span></span>  
  
 <span data-ttu-id="793b1-131">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="793b1-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="793b1-132">Kontexty instance pro rozšíření instance služby.</span><span class="sxs-lookup"><span data-stu-id="793b1-132">The instance contexts for the extensions of the service instance.</span></span>  
  
### <a name="metadata"></a><span data-ttu-id="793b1-133">Metadata</span><span class="sxs-lookup"><span data-stu-id="793b1-133">Metadata</span></span>  
 <span data-ttu-id="793b1-134">Datový typ: pole řetězců</span><span class="sxs-lookup"><span data-stu-id="793b1-134">Data type: string array</span></span>  
  
 <span data-ttu-id="793b1-135">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="793b1-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="793b1-136">Nastavení metadat služby.</span><span class="sxs-lookup"><span data-stu-id="793b1-136">The service metadata settings.</span></span>  
  
### <a name="name"></a><span data-ttu-id="793b1-137">Název</span><span class="sxs-lookup"><span data-stu-id="793b1-137">Name</span></span>  
 <span data-ttu-id="793b1-138">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="793b1-138">Data type: string</span></span>  
  
 <span data-ttu-id="793b1-139">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="793b1-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="793b1-140">Jedinečný název této služby.</span><span class="sxs-lookup"><span data-stu-id="793b1-140">The unique name of this service.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="793b1-141">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="793b1-141">Namespace</span></span>  
 <span data-ttu-id="793b1-142">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="793b1-142">Data type: string</span></span>  
  
 <span data-ttu-id="793b1-143">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="793b1-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="793b1-144">Obor názvů služby.</span><span class="sxs-lookup"><span data-stu-id="793b1-144">The namespace of the service.</span></span>  
  
### <a name="opened"></a><span data-ttu-id="793b1-145">Otevřít</span><span class="sxs-lookup"><span data-stu-id="793b1-145">Opened</span></span>  
 <span data-ttu-id="793b1-146">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="793b1-146">Data type: datetime</span></span>  
  
 <span data-ttu-id="793b1-147">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="793b1-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="793b1-148">Čas, kdy byla služba otevřena.</span><span class="sxs-lookup"><span data-stu-id="793b1-148">The time the service was opened.</span></span>  
  
### <a name="outgoingchannels"></a><span data-ttu-id="793b1-149">OutgoingChannels</span><span class="sxs-lookup"><span data-stu-id="793b1-149">OutgoingChannels</span></span>  
 <span data-ttu-id="793b1-150">Datový typ: pole Channel</span><span class="sxs-lookup"><span data-stu-id="793b1-150">Data type: Channel array</span></span>  
  
 <span data-ttu-id="793b1-151">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="793b1-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="793b1-152">Kanály, které vycházejí z instance služby.</span><span class="sxs-lookup"><span data-stu-id="793b1-152">The channels that are outgoing from the service instance.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="793b1-153">ID procesu</span><span class="sxs-lookup"><span data-stu-id="793b1-153">ProcessId</span></span>  
 <span data-ttu-id="793b1-154">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="793b1-154">Data type: sint32</span></span>  
  
 <span data-ttu-id="793b1-155">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="793b1-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="793b1-156">Proces id procesu, který je hostitelem služby.</span><span class="sxs-lookup"><span data-stu-id="793b1-156">The process id of the process that hosts the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="793b1-157">Požadavky</span><span class="sxs-lookup"><span data-stu-id="793b1-157">Requirements</span></span>  
  
|<span data-ttu-id="793b1-158">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="793b1-158">MOF</span></span>|<span data-ttu-id="793b1-159">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="793b1-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="793b1-160">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="793b1-160">Namespace</span></span>|<span data-ttu-id="793b1-161">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="793b1-161">Defined in root\ServiceModel</span></span>|
