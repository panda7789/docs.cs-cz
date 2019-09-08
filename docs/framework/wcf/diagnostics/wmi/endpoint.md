---
title: Koncový bod
ms.date: 03/30/2017
ms.assetid: fe63370d-81a1-40f3-97c2-59cb357c78d2
ms.openlocfilehash: 03c401358839671d750985b95b1aada599931aad
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795905"
---
# <a name="endpoint"></a><span data-ttu-id="975dd-102">Koncový bod</span><span class="sxs-lookup"><span data-stu-id="975dd-102">Endpoint</span></span>
<span data-ttu-id="975dd-103">Koncový bod</span><span class="sxs-lookup"><span data-stu-id="975dd-103">Endpoint</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="975dd-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="975dd-104">Syntax</span></span>  
  
```csharp
class Endpoint  
{  
  string Address;  
  string AddressHeaders[];  
  string AddressIdentity;  
  sint32 AppDomainId;  
  Behavior Behaviors[];  
  Binding Binding;  
  string ContractName;  
  string CounterInstanceName;  
  string ListenUri;  
  string Name;  
  sint32 ProcessId;  
  Contract ref;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="975dd-105">Metody</span><span class="sxs-lookup"><span data-stu-id="975dd-105">Methods</span></span>  
 <span data-ttu-id="975dd-106">Třída Endpoint definuje následující metodu.</span><span class="sxs-lookup"><span data-stu-id="975dd-106">The Endpoint class defines the following method.</span></span>  
  
|<span data-ttu-id="975dd-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="975dd-107">Method</span></span>|<span data-ttu-id="975dd-108">Popis</span><span class="sxs-lookup"><span data-stu-id="975dd-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="975dd-109">GetOperationCounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="975dd-109">GetOperationCounterInstanceName</span></span>](getoperationcounterinstancename.md)|<span data-ttu-id="975dd-110">Načte název instance čítače výkonu operace.</span><span class="sxs-lookup"><span data-stu-id="975dd-110">Retrieves the operation performance counter instance name</span></span>|  
  
## <a name="properties"></a><span data-ttu-id="975dd-111">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="975dd-111">Properties</span></span>  
 <span data-ttu-id="975dd-112">Třída Endpoint má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="975dd-112">The Endpoint class has the following properties:</span></span>  
  
### <a name="address"></a><span data-ttu-id="975dd-113">Adresa</span><span class="sxs-lookup"><span data-stu-id="975dd-113">Address</span></span>  
 <span data-ttu-id="975dd-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="975dd-114">Data type: string</span></span>  
  
 <span data-ttu-id="975dd-115">Typ přístupu: Jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="975dd-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="975dd-116">Identifikátor URI, který obsahuje adresu koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="975dd-116">A URI that contains the address of the endpoint.</span></span>  
  
### <a name="addressheaders"></a><span data-ttu-id="975dd-117">AddressHeaders</span><span class="sxs-lookup"><span data-stu-id="975dd-117">AddressHeaders</span></span>  
 <span data-ttu-id="975dd-118">Datový typ: pole řetězců</span><span class="sxs-lookup"><span data-stu-id="975dd-118">Data type: string array</span></span>  
  
 <span data-ttu-id="975dd-119">Typ přístupu: Jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="975dd-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="975dd-120">Kolekce hlaviček adres připojených k tomuto koncovému bodu.</span><span class="sxs-lookup"><span data-stu-id="975dd-120">The collection of address headers attached to this endpoint.</span></span>  
  
### <a name="addressidentity"></a><span data-ttu-id="975dd-121">AddressIdentity</span><span class="sxs-lookup"><span data-stu-id="975dd-121">AddressIdentity</span></span>  
 <span data-ttu-id="975dd-122">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="975dd-122">Data type: string</span></span>  
  
 <span data-ttu-id="975dd-123">Typ přístupu: Jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="975dd-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="975dd-124">Identita koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="975dd-124">The identity of the endpoint.</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="975dd-125">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="975dd-125">AppDomainId</span></span>  
 <span data-ttu-id="975dd-126">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="975dd-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="975dd-127">Typ přístupu: Jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="975dd-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="975dd-128">ID domény AppDomain, která hostuje koncový bod.</span><span class="sxs-lookup"><span data-stu-id="975dd-128">The appdomain id of the appdomain that hosts the endpoint.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="975dd-129">Chování</span><span class="sxs-lookup"><span data-stu-id="975dd-129">Behaviors</span></span>  
 <span data-ttu-id="975dd-130">Datový typ: Pole chování</span><span class="sxs-lookup"><span data-stu-id="975dd-130">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="975dd-131">Typ přístupu: Jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="975dd-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="975dd-132">Kolekce chování implementovaná tímto koncovým bodem</span><span class="sxs-lookup"><span data-stu-id="975dd-132">The collection of behaviors implemented by this endpoint.</span></span>  
  
### <a name="binding"></a><span data-ttu-id="975dd-133">Vazba</span><span class="sxs-lookup"><span data-stu-id="975dd-133">Binding</span></span>  
 <span data-ttu-id="975dd-134">Datový typ: Vazba</span><span class="sxs-lookup"><span data-stu-id="975dd-134">Data type: Binding</span></span>  
  
 <span data-ttu-id="975dd-135">Typ přístupu: Jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="975dd-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="975dd-136">Vazba, kterou tento koncový bod používá.</span><span class="sxs-lookup"><span data-stu-id="975dd-136">The binding used by this endpoint.</span></span>  
  
### <a name="contractname"></a><span data-ttu-id="975dd-137">Kontrakt</span><span class="sxs-lookup"><span data-stu-id="975dd-137">ContractName</span></span>  
 <span data-ttu-id="975dd-138">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="975dd-138">Data type: string</span></span>  
  
 <span data-ttu-id="975dd-139">Typ přístupu: Jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="975dd-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="975dd-140">Řetězec, který určuje, který kontrakt tento koncový bod vystavuje.</span><span class="sxs-lookup"><span data-stu-id="975dd-140">A string that specifies which contract this endpoint is exposing.</span></span>  
  
### <a name="counterinstancename"></a><span data-ttu-id="975dd-141">CounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="975dd-141">CounterInstanceName</span></span>  
 <span data-ttu-id="975dd-142">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="975dd-142">Data type: string</span></span>  
  
 <span data-ttu-id="975dd-143">Typ přístupu: Jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="975dd-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="975dd-144">Název instance čítačů výkonu koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="975dd-144">The name of the instance of performance counters of the endpoint.</span></span>  
  
### <a name="listenuri"></a><span data-ttu-id="975dd-145">ListenUri</span><span class="sxs-lookup"><span data-stu-id="975dd-145">ListenUri</span></span>  
 <span data-ttu-id="975dd-146">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="975dd-146">Data type: string</span></span>  
  
 <span data-ttu-id="975dd-147">Typ přístupu: Jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="975dd-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="975dd-148">Identifikátor URI, na kterém je koncový bod naslouchá.</span><span class="sxs-lookup"><span data-stu-id="975dd-148">The Uri the endpoint listens on.</span></span>  
  
### <a name="name"></a><span data-ttu-id="975dd-149">Name</span><span class="sxs-lookup"><span data-stu-id="975dd-149">Name</span></span>  
 <span data-ttu-id="975dd-150">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="975dd-150">Data type: string</span></span>  
  
 <span data-ttu-id="975dd-151">Typ přístupu: Jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="975dd-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="975dd-152">Jedinečný název tohoto koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="975dd-152">The unique name of this endpoint.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="975dd-153">ID procesu</span><span class="sxs-lookup"><span data-stu-id="975dd-153">ProcessId</span></span>  
 <span data-ttu-id="975dd-154">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="975dd-154">Data type: sint32</span></span>  
  
 <span data-ttu-id="975dd-155">Typ přístupu: Jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="975dd-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="975dd-156">ID procesu, který hostuje koncový bod.</span><span class="sxs-lookup"><span data-stu-id="975dd-156">The process Id of the process that hosts the endpoint.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="975dd-157">ref</span><span class="sxs-lookup"><span data-stu-id="975dd-157">ref</span></span>  
 <span data-ttu-id="975dd-158">Datový typ: Kontrakt</span><span class="sxs-lookup"><span data-stu-id="975dd-158">Data type: Contract</span></span>  
  
 <span data-ttu-id="975dd-159">Typ přístupu: Jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="975dd-159">Access type: Read-only</span></span>  
  
 <span data-ttu-id="975dd-160">Kontrakt, který tento koncový bod zveřejňuje.</span><span class="sxs-lookup"><span data-stu-id="975dd-160">The contract this endpoint is exposing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="975dd-161">Požadavky</span><span class="sxs-lookup"><span data-stu-id="975dd-161">Requirements</span></span>  
  
|<span data-ttu-id="975dd-162">TVOŘÍCÍ</span><span class="sxs-lookup"><span data-stu-id="975dd-162">MOF</span></span>|<span data-ttu-id="975dd-163">Deklarováno v souboru ServiceModel. mof.</span><span class="sxs-lookup"><span data-stu-id="975dd-163">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="975dd-164">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="975dd-164">Namespace</span></span>|<span data-ttu-id="975dd-165">Definováno v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="975dd-165">Defined in root\ServiceModel</span></span>|
