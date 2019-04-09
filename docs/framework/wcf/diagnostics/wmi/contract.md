---
title: Contract1
ms.date: 03/30/2017
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
ms.openlocfilehash: 10789f9a2940c239ae20c8fd1e9d48bca0e820ed
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59201088"
---
# <a name="contract"></a><span data-ttu-id="8968f-102">Kontrakt</span><span class="sxs-lookup"><span data-stu-id="8968f-102">Contract</span></span>
<span data-ttu-id="8968f-103">Kontrakt</span><span class="sxs-lookup"><span data-stu-id="8968f-103">Contract</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8968f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8968f-104">Syntax</span></span>  
  
```csharp
class Contract  
{  
  sint32 AppDomainId;  
  Behavior Behaviors[];  
  string Name;  
  string Namespace;  
  Operation Operations[];  
  sint32 ProcessId;  
  Contract ref;  
  string SessionMode;  
  string Type;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="8968f-105">Metody</span><span class="sxs-lookup"><span data-stu-id="8968f-105">Methods</span></span>  
 <span data-ttu-id="8968f-106">Třída smlouvy nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="8968f-106">The Contract class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="8968f-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="8968f-107">Properties</span></span>  
 <span data-ttu-id="8968f-108">Třída smlouvy má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="8968f-108">The Contract class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="8968f-109">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="8968f-109">AppDomainId</span></span>  
 <span data-ttu-id="8968f-110">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="8968f-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="8968f-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="8968f-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8968f-112">Id domény, která hostuje kontrakt.</span><span class="sxs-lookup"><span data-stu-id="8968f-112">The appdomain id of the appdomain that hosts the contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="8968f-113">Chování</span><span class="sxs-lookup"><span data-stu-id="8968f-113">Behaviors</span></span>  
 <span data-ttu-id="8968f-114">Datový typ: Chování pole</span><span class="sxs-lookup"><span data-stu-id="8968f-114">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="8968f-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="8968f-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8968f-116">Vlastnosti přičleněné k tomuto kontraktu.</span><span class="sxs-lookup"><span data-stu-id="8968f-116">The behaviors associated with this contract.</span></span>  
  
### <a name="name"></a><span data-ttu-id="8968f-117">Name</span><span class="sxs-lookup"><span data-stu-id="8968f-117">Name</span></span>  
 <span data-ttu-id="8968f-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="8968f-118">Data type: string</span></span>  
  
 <span data-ttu-id="8968f-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="8968f-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8968f-120">Název kontraktu v jazyce WSDL.</span><span class="sxs-lookup"><span data-stu-id="8968f-120">The name of the contract in WSDL.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="8968f-121">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="8968f-121">Namespace</span></span>  
 <span data-ttu-id="8968f-122">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="8968f-122">Data type: string</span></span>  
  
 <span data-ttu-id="8968f-123">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="8968f-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8968f-124">Obor názvů `portType` elementu v jazyce WSDL.</span><span class="sxs-lookup"><span data-stu-id="8968f-124">The namespace of the `portType` element in WSDL.</span></span>  
  
### <a name="operations"></a><span data-ttu-id="8968f-125">Operace</span><span class="sxs-lookup"><span data-stu-id="8968f-125">Operations</span></span>  
 <span data-ttu-id="8968f-126">Datový typ: Operace pole</span><span class="sxs-lookup"><span data-stu-id="8968f-126">Data type: Operation array</span></span>  
  
 <span data-ttu-id="8968f-127">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="8968f-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8968f-128">Operace tohoto kontraktu.</span><span class="sxs-lookup"><span data-stu-id="8968f-128">The operations of this contract.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="8968f-129">ID procesu</span><span class="sxs-lookup"><span data-stu-id="8968f-129">ProcessId</span></span>  
 <span data-ttu-id="8968f-130">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="8968f-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="8968f-131">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="8968f-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8968f-132">Proces Id procesu, který hostuje kontrakt.</span><span class="sxs-lookup"><span data-stu-id="8968f-132">The process Id of the process that hosts the contract.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="8968f-133">ref</span><span class="sxs-lookup"><span data-stu-id="8968f-133">ref</span></span>  
 <span data-ttu-id="8968f-134">Datový typ: Kontrakt</span><span class="sxs-lookup"><span data-stu-id="8968f-134">Data type: Contract</span></span>  
  
 <span data-ttu-id="8968f-135">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="8968f-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8968f-136">Typ zpětného volání v případě, že kontrakt je oboustranný.</span><span class="sxs-lookup"><span data-stu-id="8968f-136">The type of callback when the contract is a duplex contract.</span></span>  
  
### <a name="sessionmode"></a><span data-ttu-id="8968f-137">SessionMode</span><span class="sxs-lookup"><span data-stu-id="8968f-137">SessionMode</span></span>  
 <span data-ttu-id="8968f-138">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="8968f-138">Data type: string</span></span>  
  
 <span data-ttu-id="8968f-139">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="8968f-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8968f-140">Určuje, zda kontrakt vyžaduje, aby připojení připojené k tomuto kontraktu použilo kanálové relace.</span><span class="sxs-lookup"><span data-stu-id="8968f-140">Indicates whether the contract requires the binding associated with this contract to use channel sessions.</span></span>  
  
### <a name="type"></a><span data-ttu-id="8968f-141">Type</span><span class="sxs-lookup"><span data-stu-id="8968f-141">Type</span></span>  
 <span data-ttu-id="8968f-142">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="8968f-142">Data type: string</span></span>  
  
 <span data-ttu-id="8968f-143">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="8968f-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8968f-144">Typ kontraktu.</span><span class="sxs-lookup"><span data-stu-id="8968f-144">The type of the contract.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8968f-145">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8968f-145">Requirements</span></span>  
  
|<span data-ttu-id="8968f-146">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="8968f-146">MOF</span></span>|<span data-ttu-id="8968f-147">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="8968f-147">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="8968f-148">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="8968f-148">Namespace</span></span>|<span data-ttu-id="8968f-149">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="8968f-149">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8968f-150">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8968f-150">See also</span></span>

- <xref:System.ServiceModel.Description.ContractDescription>
