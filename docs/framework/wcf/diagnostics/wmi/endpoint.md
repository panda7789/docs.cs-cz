---
title: "Koncový bod"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fe63370d-81a1-40f3-97c2-59cb357c78d2
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ed3c01f6943ec2958da56777ac0d6223fff66ab0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="endpoint"></a><span data-ttu-id="d7400-102">Koncový bod</span><span class="sxs-lookup"><span data-stu-id="d7400-102">Endpoint</span></span>
<span data-ttu-id="d7400-103">Koncový bod</span><span class="sxs-lookup"><span data-stu-id="d7400-103">Endpoint</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7400-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d7400-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="d7400-105">Metody</span><span class="sxs-lookup"><span data-stu-id="d7400-105">Methods</span></span>  
 <span data-ttu-id="d7400-106">Třída koncový bod definuje následující metodu.</span><span class="sxs-lookup"><span data-stu-id="d7400-106">The Endpoint class defines the following method.</span></span>  
  
|<span data-ttu-id="d7400-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="d7400-107">Method</span></span>|<span data-ttu-id="d7400-108">Popis</span><span class="sxs-lookup"><span data-stu-id="d7400-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d7400-109">GetOperationCounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="d7400-109">GetOperationCounterInstanceName</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/getoperationcounterinstancename.md)|<span data-ttu-id="d7400-110">Načte název instance čítače výkonu operace</span><span class="sxs-lookup"><span data-stu-id="d7400-110">Retrieves the operation performance counter instance name</span></span>|  
  
## <a name="properties"></a><span data-ttu-id="d7400-111">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="d7400-111">Properties</span></span>  
 <span data-ttu-id="d7400-112">Třída koncový bod má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="d7400-112">The Endpoint class has the following properties:</span></span>  
  
### <a name="address"></a><span data-ttu-id="d7400-113">Adresa</span><span class="sxs-lookup"><span data-stu-id="d7400-113">Address</span></span>  
 <span data-ttu-id="d7400-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="d7400-114">Data type: string</span></span>  
  
 <span data-ttu-id="d7400-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d7400-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d7400-116">Identifikátor URI, který obsahuje adresu koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="d7400-116">A URI that contains the address of the endpoint.</span></span>  
  
### <a name="addressheaders"></a><span data-ttu-id="d7400-117">AddressHeaders</span><span class="sxs-lookup"><span data-stu-id="d7400-117">AddressHeaders</span></span>  
 <span data-ttu-id="d7400-118">Datový typ: pole řetězců</span><span class="sxs-lookup"><span data-stu-id="d7400-118">Data type: string array</span></span>  
  
 <span data-ttu-id="d7400-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d7400-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d7400-120">Kolekce hlavičky adresy, které jsou připojené k tomuto koncovému bodu.</span><span class="sxs-lookup"><span data-stu-id="d7400-120">The collection of address headers attached to this endpoint.</span></span>  
  
### <a name="addressidentity"></a><span data-ttu-id="d7400-121">AddressIdentity</span><span class="sxs-lookup"><span data-stu-id="d7400-121">AddressIdentity</span></span>  
 <span data-ttu-id="d7400-122">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="d7400-122">Data type: string</span></span>  
  
 <span data-ttu-id="d7400-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d7400-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d7400-124">Identitu koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="d7400-124">The identity of the endpoint.</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="d7400-125">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="d7400-125">AppDomainId</span></span>  
 <span data-ttu-id="d7400-126">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="d7400-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="d7400-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d7400-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d7400-128">Identifikační číslo domény, který je hostitelem koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="d7400-128">The appdomain id of the appdomain that hosts the endpoint.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="d7400-129">Chování</span><span class="sxs-lookup"><span data-stu-id="d7400-129">Behaviors</span></span>  
 <span data-ttu-id="d7400-130">Datový typ: chování pole</span><span class="sxs-lookup"><span data-stu-id="d7400-130">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="d7400-131">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d7400-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d7400-132">Kolekce vlastností implementovaná tento koncový bod.</span><span class="sxs-lookup"><span data-stu-id="d7400-132">The collection of behaviors implemented by this endpoint.</span></span>  
  
### <a name="binding"></a><span data-ttu-id="d7400-133">Vazba</span><span class="sxs-lookup"><span data-stu-id="d7400-133">Binding</span></span>  
 <span data-ttu-id="d7400-134">Datový typ: vytvoření vazby</span><span class="sxs-lookup"><span data-stu-id="d7400-134">Data type: Binding</span></span>  
  
 <span data-ttu-id="d7400-135">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d7400-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d7400-136">Vazba používaný tímto koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="d7400-136">The binding used by this endpoint.</span></span>  
  
### <a name="contractname"></a><span data-ttu-id="d7400-137">ContractName</span><span class="sxs-lookup"><span data-stu-id="d7400-137">ContractName</span></span>  
 <span data-ttu-id="d7400-138">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="d7400-138">Data type: string</span></span>  
  
 <span data-ttu-id="d7400-139">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d7400-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d7400-140">Řetězec, který určuje, jaký kontrakt tento koncový bod je vystavení.</span><span class="sxs-lookup"><span data-stu-id="d7400-140">A string that specifies which contract this endpoint is exposing.</span></span>  
  
### <a name="counterinstancename"></a><span data-ttu-id="d7400-141">CounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="d7400-141">CounterInstanceName</span></span>  
 <span data-ttu-id="d7400-142">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="d7400-142">Data type: string</span></span>  
  
 <span data-ttu-id="d7400-143">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d7400-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d7400-144">Název instance čítače výkonu koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="d7400-144">The name of the instance of performance counters of the endpoint.</span></span>  
  
### <a name="listenuri"></a><span data-ttu-id="d7400-145">Adrese ListenUri</span><span class="sxs-lookup"><span data-stu-id="d7400-145">ListenUri</span></span>  
 <span data-ttu-id="d7400-146">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="d7400-146">Data type: string</span></span>  
  
 <span data-ttu-id="d7400-147">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d7400-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d7400-148">Identifikátor Uri koncového bodu naslouchá na.</span><span class="sxs-lookup"><span data-stu-id="d7400-148">The Uri the endpoint listens on.</span></span>  
  
### <a name="name"></a><span data-ttu-id="d7400-149">Název</span><span class="sxs-lookup"><span data-stu-id="d7400-149">Name</span></span>  
 <span data-ttu-id="d7400-150">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="d7400-150">Data type: string</span></span>  
  
 <span data-ttu-id="d7400-151">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d7400-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d7400-152">Jedinečný název tohoto koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="d7400-152">The unique name of this endpoint.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="d7400-153">ID procesu</span><span class="sxs-lookup"><span data-stu-id="d7400-153">ProcessId</span></span>  
 <span data-ttu-id="d7400-154">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="d7400-154">Data type: sint32</span></span>  
  
 <span data-ttu-id="d7400-155">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d7400-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d7400-156">Id procesu, který je hostitelem koncového bodu procesu.</span><span class="sxs-lookup"><span data-stu-id="d7400-156">The process Id of the process that hosts the endpoint.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="d7400-157">ref</span><span class="sxs-lookup"><span data-stu-id="d7400-157">ref</span></span>  
 <span data-ttu-id="d7400-158">Datový typ: kontraktu</span><span class="sxs-lookup"><span data-stu-id="d7400-158">Data type: Contract</span></span>  
  
 <span data-ttu-id="d7400-159">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d7400-159">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d7400-160">Kontrakt tento koncový bod je vystavení.</span><span class="sxs-lookup"><span data-stu-id="d7400-160">The contract this endpoint is exposing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7400-161">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d7400-161">Requirements</span></span>  
  
|<span data-ttu-id="d7400-162">MOF</span><span class="sxs-lookup"><span data-stu-id="d7400-162">MOF</span></span>|<span data-ttu-id="d7400-163">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="d7400-163">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="d7400-164">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="d7400-164">Namespace</span></span>|<span data-ttu-id="d7400-165">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d7400-165">Defined in root\ServiceModel</span></span>|
