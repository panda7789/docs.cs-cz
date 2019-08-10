---
title: Kontrakt
ms.date: 03/30/2017
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
ms.openlocfilehash: e4a21e95a6f1f1860ed36c968d17bb8ac8465dce
ms.sourcegitcommit: 9ee6cd851b6e176a5811ea28ed0d5935c71950f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2019
ms.locfileid: "68868436"
---
# <a name="contract"></a><span data-ttu-id="7ce04-102">Kontrakt</span><span class="sxs-lookup"><span data-stu-id="7ce04-102">Contract</span></span>
<span data-ttu-id="7ce04-103">Kontrakt</span><span class="sxs-lookup"><span data-stu-id="7ce04-103">Contract</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ce04-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7ce04-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="7ce04-105">Metody</span><span class="sxs-lookup"><span data-stu-id="7ce04-105">Methods</span></span>  
 <span data-ttu-id="7ce04-106">Třída kontraktu nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="7ce04-106">The Contract class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="7ce04-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="7ce04-107">Properties</span></span>  
 <span data-ttu-id="7ce04-108">Třída kontraktu má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="7ce04-108">The Contract class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="7ce04-109">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="7ce04-109">AppDomainId</span></span>  
 <span data-ttu-id="7ce04-110">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="7ce04-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="7ce04-111">Typ přístupu: Jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="7ce04-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7ce04-112">ID domény AppDomain, která hostuje kontrakt.</span><span class="sxs-lookup"><span data-stu-id="7ce04-112">The appdomain id of the appdomain that hosts the contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="7ce04-113">Chování</span><span class="sxs-lookup"><span data-stu-id="7ce04-113">Behaviors</span></span>  
 <span data-ttu-id="7ce04-114">Datový typ: Pole chování</span><span class="sxs-lookup"><span data-stu-id="7ce04-114">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="7ce04-115">Typ přístupu: Jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="7ce04-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7ce04-116">Chování spojené s touto smlouvou.</span><span class="sxs-lookup"><span data-stu-id="7ce04-116">The behaviors associated with this contract.</span></span>  
  
### <a name="name"></a><span data-ttu-id="7ce04-117">Name</span><span class="sxs-lookup"><span data-stu-id="7ce04-117">Name</span></span>  
 <span data-ttu-id="7ce04-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="7ce04-118">Data type: string</span></span>  
  
 <span data-ttu-id="7ce04-119">Typ přístupu: Jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="7ce04-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7ce04-120">Název kontraktu v jazyce WSDL.</span><span class="sxs-lookup"><span data-stu-id="7ce04-120">The name of the contract in WSDL.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="7ce04-121">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="7ce04-121">Namespace</span></span>  
 <span data-ttu-id="7ce04-122">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="7ce04-122">Data type: string</span></span>  
  
 <span data-ttu-id="7ce04-123">Typ přístupu: Jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="7ce04-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7ce04-124">Obor názvů `portType` prvku v jazyce WSDL.</span><span class="sxs-lookup"><span data-stu-id="7ce04-124">The namespace of the `portType` element in WSDL.</span></span>  
  
### <a name="operations"></a><span data-ttu-id="7ce04-125">Operace</span><span class="sxs-lookup"><span data-stu-id="7ce04-125">Operations</span></span>  
 <span data-ttu-id="7ce04-126">Datový typ: Pole operace</span><span class="sxs-lookup"><span data-stu-id="7ce04-126">Data type: Operation array</span></span>  
  
 <span data-ttu-id="7ce04-127">Typ přístupu: Jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="7ce04-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7ce04-128">Operace tohoto kontraktu.</span><span class="sxs-lookup"><span data-stu-id="7ce04-128">The operations of this contract.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="7ce04-129">ID procesu</span><span class="sxs-lookup"><span data-stu-id="7ce04-129">ProcessId</span></span>  
 <span data-ttu-id="7ce04-130">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="7ce04-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="7ce04-131">Typ přístupu: Jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="7ce04-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7ce04-132">ID procesu, který hostuje kontrakt.</span><span class="sxs-lookup"><span data-stu-id="7ce04-132">The process Id of the process that hosts the contract.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="7ce04-133">ref</span><span class="sxs-lookup"><span data-stu-id="7ce04-133">ref</span></span>  
 <span data-ttu-id="7ce04-134">Datový typ: Kontrakt</span><span class="sxs-lookup"><span data-stu-id="7ce04-134">Data type: Contract</span></span>  
  
 <span data-ttu-id="7ce04-135">Typ přístupu: Jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="7ce04-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7ce04-136">Typ zpětného volání v případě, že kontrakt je oboustranný.</span><span class="sxs-lookup"><span data-stu-id="7ce04-136">The type of callback when the contract is a duplex contract.</span></span>  
  
### <a name="sessionmode"></a><span data-ttu-id="7ce04-137">SessionMode</span><span class="sxs-lookup"><span data-stu-id="7ce04-137">SessionMode</span></span>  
 <span data-ttu-id="7ce04-138">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="7ce04-138">Data type: string</span></span>  
  
 <span data-ttu-id="7ce04-139">Typ přístupu: Jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="7ce04-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7ce04-140">Určuje, zda kontrakt vyžaduje, aby vazba přidružená k tomuto kontraktu použila relace kanálu.</span><span class="sxs-lookup"><span data-stu-id="7ce04-140">Indicates whether the contract requires the binding associated with this contract to use channel sessions.</span></span>  
  
### <a name="type"></a><span data-ttu-id="7ce04-141">type</span><span class="sxs-lookup"><span data-stu-id="7ce04-141">Type</span></span>  
 <span data-ttu-id="7ce04-142">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="7ce04-142">Data type: string</span></span>  
  
 <span data-ttu-id="7ce04-143">Typ přístupu: Jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="7ce04-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7ce04-144">Typ kontraktu.</span><span class="sxs-lookup"><span data-stu-id="7ce04-144">The type of the contract.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ce04-145">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7ce04-145">Requirements</span></span>  
  
|<span data-ttu-id="7ce04-146">TVOŘÍCÍ</span><span class="sxs-lookup"><span data-stu-id="7ce04-146">MOF</span></span>|<span data-ttu-id="7ce04-147">Deklarováno v souboru ServiceModel. mof.</span><span class="sxs-lookup"><span data-stu-id="7ce04-147">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="7ce04-148">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="7ce04-148">Namespace</span></span>|<span data-ttu-id="7ce04-149">Definováno v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="7ce04-149">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7ce04-150">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7ce04-150">See also</span></span>

- <xref:System.ServiceModel.Description.ContractDescription>
