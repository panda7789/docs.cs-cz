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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ef4e27f6e7a45fe705aa09827702a64c960b6a16
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="endpoint"></a><span data-ttu-id="9ec94-102">Koncový bod</span><span class="sxs-lookup"><span data-stu-id="9ec94-102">Endpoint</span></span>
<span data-ttu-id="9ec94-103">Koncový bod</span><span class="sxs-lookup"><span data-stu-id="9ec94-103">Endpoint</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ec94-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9ec94-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="9ec94-105">Metody</span><span class="sxs-lookup"><span data-stu-id="9ec94-105">Methods</span></span>  
 <span data-ttu-id="9ec94-106">Třída koncový bod definuje následující metodu.</span><span class="sxs-lookup"><span data-stu-id="9ec94-106">The Endpoint class defines the following method.</span></span>  
  
|<span data-ttu-id="9ec94-107">Metoda</span><span class="sxs-lookup"><span data-stu-id="9ec94-107">Method</span></span>|<span data-ttu-id="9ec94-108">Popis</span><span class="sxs-lookup"><span data-stu-id="9ec94-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9ec94-109">GetOperationCounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="9ec94-109">GetOperationCounterInstanceName</span></span>](../../../../../docs/framework/wcf/diagnostics/wmi/getoperationcounterinstancename.md)|<span data-ttu-id="9ec94-110">Načte název instance čítače výkonu operace</span><span class="sxs-lookup"><span data-stu-id="9ec94-110">Retrieves the operation performance counter instance name</span></span>|  
  
## <a name="properties"></a><span data-ttu-id="9ec94-111">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="9ec94-111">Properties</span></span>  
 <span data-ttu-id="9ec94-112">Třída koncový bod má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="9ec94-112">The Endpoint class has the following properties:</span></span>  
  
### <a name="address"></a><span data-ttu-id="9ec94-113">Adresa</span><span class="sxs-lookup"><span data-stu-id="9ec94-113">Address</span></span>  
 <span data-ttu-id="9ec94-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="9ec94-114">Data type: string</span></span>  
  
 <span data-ttu-id="9ec94-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="9ec94-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9ec94-116">Identifikátor URI, který obsahuje adresu koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="9ec94-116">A URI that contains the address of the endpoint.</span></span>  
  
### <a name="addressheaders"></a><span data-ttu-id="9ec94-117">AddressHeaders</span><span class="sxs-lookup"><span data-stu-id="9ec94-117">AddressHeaders</span></span>  
 <span data-ttu-id="9ec94-118">Datový typ: pole řetězců</span><span class="sxs-lookup"><span data-stu-id="9ec94-118">Data type: string array</span></span>  
  
 <span data-ttu-id="9ec94-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="9ec94-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9ec94-120">Kolekce hlavičky adresy, které jsou připojené k tomuto koncovému bodu.</span><span class="sxs-lookup"><span data-stu-id="9ec94-120">The collection of address headers attached to this endpoint.</span></span>  
  
### <a name="addressidentity"></a><span data-ttu-id="9ec94-121">AddressIdentity</span><span class="sxs-lookup"><span data-stu-id="9ec94-121">AddressIdentity</span></span>  
 <span data-ttu-id="9ec94-122">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="9ec94-122">Data type: string</span></span>  
  
 <span data-ttu-id="9ec94-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="9ec94-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9ec94-124">Identitu koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="9ec94-124">The identity of the endpoint.</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="9ec94-125">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="9ec94-125">AppDomainId</span></span>  
 <span data-ttu-id="9ec94-126">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="9ec94-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="9ec94-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="9ec94-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9ec94-128">Identifikační číslo domény, který je hostitelem koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="9ec94-128">The appdomain id of the appdomain that hosts the endpoint.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="9ec94-129">Chování</span><span class="sxs-lookup"><span data-stu-id="9ec94-129">Behaviors</span></span>  
 <span data-ttu-id="9ec94-130">Datový typ: chování pole</span><span class="sxs-lookup"><span data-stu-id="9ec94-130">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="9ec94-131">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="9ec94-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9ec94-132">Kolekce vlastností implementovaná tento koncový bod.</span><span class="sxs-lookup"><span data-stu-id="9ec94-132">The collection of behaviors implemented by this endpoint.</span></span>  
  
### <a name="binding"></a><span data-ttu-id="9ec94-133">Vazba</span><span class="sxs-lookup"><span data-stu-id="9ec94-133">Binding</span></span>  
 <span data-ttu-id="9ec94-134">Datový typ: vytvoření vazby</span><span class="sxs-lookup"><span data-stu-id="9ec94-134">Data type: Binding</span></span>  
  
 <span data-ttu-id="9ec94-135">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="9ec94-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9ec94-136">Vazba používaný tímto koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="9ec94-136">The binding used by this endpoint.</span></span>  
  
### <a name="contractname"></a><span data-ttu-id="9ec94-137">ContractName</span><span class="sxs-lookup"><span data-stu-id="9ec94-137">ContractName</span></span>  
 <span data-ttu-id="9ec94-138">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="9ec94-138">Data type: string</span></span>  
  
 <span data-ttu-id="9ec94-139">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="9ec94-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9ec94-140">Řetězec, který určuje, jaký kontrakt tento koncový bod je vystavení.</span><span class="sxs-lookup"><span data-stu-id="9ec94-140">A string that specifies which contract this endpoint is exposing.</span></span>  
  
### <a name="counterinstancename"></a><span data-ttu-id="9ec94-141">CounterInstanceName</span><span class="sxs-lookup"><span data-stu-id="9ec94-141">CounterInstanceName</span></span>  
 <span data-ttu-id="9ec94-142">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="9ec94-142">Data type: string</span></span>  
  
 <span data-ttu-id="9ec94-143">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="9ec94-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9ec94-144">Název instance čítače výkonu koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="9ec94-144">The name of the instance of performance counters of the endpoint.</span></span>  
  
### <a name="listenuri"></a><span data-ttu-id="9ec94-145">Adrese ListenUri</span><span class="sxs-lookup"><span data-stu-id="9ec94-145">ListenUri</span></span>  
 <span data-ttu-id="9ec94-146">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="9ec94-146">Data type: string</span></span>  
  
 <span data-ttu-id="9ec94-147">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="9ec94-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9ec94-148">Identifikátor Uri koncového bodu naslouchá na.</span><span class="sxs-lookup"><span data-stu-id="9ec94-148">The Uri the endpoint listens on.</span></span>  
  
### <a name="name"></a><span data-ttu-id="9ec94-149">Název</span><span class="sxs-lookup"><span data-stu-id="9ec94-149">Name</span></span>  
 <span data-ttu-id="9ec94-150">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="9ec94-150">Data type: string</span></span>  
  
 <span data-ttu-id="9ec94-151">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="9ec94-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9ec94-152">Jedinečný název tohoto koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="9ec94-152">The unique name of this endpoint.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="9ec94-153">ID procesu</span><span class="sxs-lookup"><span data-stu-id="9ec94-153">ProcessId</span></span>  
 <span data-ttu-id="9ec94-154">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="9ec94-154">Data type: sint32</span></span>  
  
 <span data-ttu-id="9ec94-155">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="9ec94-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9ec94-156">Id procesu, který je hostitelem koncového bodu procesu.</span><span class="sxs-lookup"><span data-stu-id="9ec94-156">The process Id of the process that hosts the endpoint.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="9ec94-157">ref</span><span class="sxs-lookup"><span data-stu-id="9ec94-157">ref</span></span>  
 <span data-ttu-id="9ec94-158">Datový typ: kontraktu</span><span class="sxs-lookup"><span data-stu-id="9ec94-158">Data type: Contract</span></span>  
  
 <span data-ttu-id="9ec94-159">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="9ec94-159">Access type: Read-only</span></span>  
  
 <span data-ttu-id="9ec94-160">Kontrakt tento koncový bod je vystavení.</span><span class="sxs-lookup"><span data-stu-id="9ec94-160">The contract this endpoint is exposing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ec94-161">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9ec94-161">Requirements</span></span>  
  
|<span data-ttu-id="9ec94-162">MOF</span><span class="sxs-lookup"><span data-stu-id="9ec94-162">MOF</span></span>|<span data-ttu-id="9ec94-163">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="9ec94-163">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="9ec94-164">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="9ec94-164">Namespace</span></span>|<span data-ttu-id="9ec94-165">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="9ec94-165">Defined in root\ServiceModel</span></span>|
