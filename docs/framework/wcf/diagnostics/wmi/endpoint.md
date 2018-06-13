---
title: Koncový bod
ms.date: 03/30/2017
ms.assetid: fe63370d-81a1-40f3-97c2-59cb357c78d2
ms.openlocfilehash: 5d597e9e029cec3552c94b47a64dfbf36d933e67
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33487643"
---
# <a name="endpoint"></a><span data-ttu-id="65b0e-102">Koncový bod</span><span class="sxs-lookup"><span data-stu-id="65b0e-102">Endpoint</span></span>
<span data-ttu-id="65b0e-103">Koncový bod</span><span class="sxs-lookup"><span data-stu-id="65b0e-103">Endpoint</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65b0e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="65b0e-104">Syntax</span></span>  
  
```  
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
  
## <a name="methods"></a><span data-ttu-id="65b0e-105">Metody</span><span class="sxs-lookup"><span data-stu-id="65b0e-105">Methods</span></span>  
 <span data-ttu-id="65b0e-106">Třída koncový bod definuje následující metodu.</span><span class="sxs-lookup"><span data-stu-id="65b0e-106">The Endpoint class defines the following method.</span></span>  
  
|<span data-ttu-id="65b0e-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="65b0e-107">Method</span></span>|<span data-ttu-id="65b0e-108">Popis</span><span class="sxs-lookup"><span data-stu-id="65b0e-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="65b0e-109">GetOperationCounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="65b0e-109">GetOperationCounterInstanceName</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/getoperationcounterinstancename.md)|<span data-ttu-id="65b0e-110">Načte název instance čítače výkonu operace</span><span class="sxs-lookup"><span data-stu-id="65b0e-110">Retrieves the operation performance counter instance name</span></span>|  
  
## <a name="properties"></a><span data-ttu-id="65b0e-111">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="65b0e-111">Properties</span></span>  
 <span data-ttu-id="65b0e-112">Třída koncový bod má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="65b0e-112">The Endpoint class has the following properties:</span></span>  
  
### <a name="address"></a><span data-ttu-id="65b0e-113">Adresa</span><span class="sxs-lookup"><span data-stu-id="65b0e-113">Address</span></span>  
 <span data-ttu-id="65b0e-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="65b0e-114">Data type: string</span></span>  
  
 <span data-ttu-id="65b0e-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="65b0e-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="65b0e-116">Identifikátor URI, který obsahuje adresu koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="65b0e-116">A URI that contains the address of the endpoint.</span></span>  
  
### <a name="addressheaders"></a><span data-ttu-id="65b0e-117">AddressHeaders</span><span class="sxs-lookup"><span data-stu-id="65b0e-117">AddressHeaders</span></span>  
 <span data-ttu-id="65b0e-118">Datový typ: pole řetězců</span><span class="sxs-lookup"><span data-stu-id="65b0e-118">Data type: string array</span></span>  
  
 <span data-ttu-id="65b0e-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="65b0e-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="65b0e-120">Kolekce hlavičky adresy, které jsou připojené k tomuto koncovému bodu.</span><span class="sxs-lookup"><span data-stu-id="65b0e-120">The collection of address headers attached to this endpoint.</span></span>  
  
### <a name="addressidentity"></a><span data-ttu-id="65b0e-121">AddressIdentity</span><span class="sxs-lookup"><span data-stu-id="65b0e-121">AddressIdentity</span></span>  
 <span data-ttu-id="65b0e-122">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="65b0e-122">Data type: string</span></span>  
  
 <span data-ttu-id="65b0e-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="65b0e-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="65b0e-124">Identitu koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="65b0e-124">The identity of the endpoint.</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="65b0e-125">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="65b0e-125">AppDomainId</span></span>  
 <span data-ttu-id="65b0e-126">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="65b0e-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="65b0e-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="65b0e-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="65b0e-128">Identifikační číslo domény, který je hostitelem koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="65b0e-128">The appdomain id of the appdomain that hosts the endpoint.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="65b0e-129">Chování</span><span class="sxs-lookup"><span data-stu-id="65b0e-129">Behaviors</span></span>  
 <span data-ttu-id="65b0e-130">Datový typ: chování pole</span><span class="sxs-lookup"><span data-stu-id="65b0e-130">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="65b0e-131">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="65b0e-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="65b0e-132">Kolekce vlastností implementovaná tento koncový bod.</span><span class="sxs-lookup"><span data-stu-id="65b0e-132">The collection of behaviors implemented by this endpoint.</span></span>  
  
### <a name="binding"></a><span data-ttu-id="65b0e-133">Vazba</span><span class="sxs-lookup"><span data-stu-id="65b0e-133">Binding</span></span>  
 <span data-ttu-id="65b0e-134">Datový typ: vytvoření vazby</span><span class="sxs-lookup"><span data-stu-id="65b0e-134">Data type: Binding</span></span>  
  
 <span data-ttu-id="65b0e-135">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="65b0e-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="65b0e-136">Vazba používaný tímto koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="65b0e-136">The binding used by this endpoint.</span></span>  
  
### <a name="contractname"></a><span data-ttu-id="65b0e-137">ContractName</span><span class="sxs-lookup"><span data-stu-id="65b0e-137">ContractName</span></span>  
 <span data-ttu-id="65b0e-138">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="65b0e-138">Data type: string</span></span>  
  
 <span data-ttu-id="65b0e-139">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="65b0e-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="65b0e-140">Řetězec, který určuje, jaký kontrakt tento koncový bod je vystavení.</span><span class="sxs-lookup"><span data-stu-id="65b0e-140">A string that specifies which contract this endpoint is exposing.</span></span>  
  
### <a name="counterinstancename"></a><span data-ttu-id="65b0e-141">CounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="65b0e-141">CounterInstanceName</span></span>  
 <span data-ttu-id="65b0e-142">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="65b0e-142">Data type: string</span></span>  
  
 <span data-ttu-id="65b0e-143">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="65b0e-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="65b0e-144">Název instance čítače výkonu koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="65b0e-144">The name of the instance of performance counters of the endpoint.</span></span>  
  
### <a name="listenuri"></a><span data-ttu-id="65b0e-145">Adrese ListenUri</span><span class="sxs-lookup"><span data-stu-id="65b0e-145">ListenUri</span></span>  
 <span data-ttu-id="65b0e-146">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="65b0e-146">Data type: string</span></span>  
  
 <span data-ttu-id="65b0e-147">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="65b0e-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="65b0e-148">Identifikátor Uri koncového bodu naslouchá na.</span><span class="sxs-lookup"><span data-stu-id="65b0e-148">The Uri the endpoint listens on.</span></span>  
  
### <a name="name"></a><span data-ttu-id="65b0e-149">Název</span><span class="sxs-lookup"><span data-stu-id="65b0e-149">Name</span></span>  
 <span data-ttu-id="65b0e-150">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="65b0e-150">Data type: string</span></span>  
  
 <span data-ttu-id="65b0e-151">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="65b0e-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="65b0e-152">Jedinečný název tohoto koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="65b0e-152">The unique name of this endpoint.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="65b0e-153">ID procesu</span><span class="sxs-lookup"><span data-stu-id="65b0e-153">ProcessId</span></span>  
 <span data-ttu-id="65b0e-154">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="65b0e-154">Data type: sint32</span></span>  
  
 <span data-ttu-id="65b0e-155">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="65b0e-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="65b0e-156">Id procesu, který je hostitelem koncového bodu procesu.</span><span class="sxs-lookup"><span data-stu-id="65b0e-156">The process Id of the process that hosts the endpoint.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="65b0e-157">ref</span><span class="sxs-lookup"><span data-stu-id="65b0e-157">ref</span></span>  
 <span data-ttu-id="65b0e-158">Datový typ: kontraktu</span><span class="sxs-lookup"><span data-stu-id="65b0e-158">Data type: Contract</span></span>  
  
 <span data-ttu-id="65b0e-159">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="65b0e-159">Access type: Read-only</span></span>  
  
 <span data-ttu-id="65b0e-160">Kontrakt tento koncový bod je vystavení.</span><span class="sxs-lookup"><span data-stu-id="65b0e-160">The contract this endpoint is exposing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65b0e-161">Požadavky</span><span class="sxs-lookup"><span data-stu-id="65b0e-161">Requirements</span></span>  
  
|<span data-ttu-id="65b0e-162">MOF</span><span class="sxs-lookup"><span data-stu-id="65b0e-162">MOF</span></span>|<span data-ttu-id="65b0e-163">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="65b0e-163">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="65b0e-164">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="65b0e-164">Namespace</span></span>|<span data-ttu-id="65b0e-165">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="65b0e-165">Defined in root\ServiceModel</span></span>|
