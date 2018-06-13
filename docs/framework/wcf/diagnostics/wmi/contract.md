---
title: Contract1
ms.date: 03/30/2017
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
ms.openlocfilehash: 12b45c08a3d8dc69e740ce77d0d2abd097907ac2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485704"
---
# <a name="contract"></a><span data-ttu-id="74467-102">Kontrakt</span><span class="sxs-lookup"><span data-stu-id="74467-102">Contract</span></span>
<span data-ttu-id="74467-103">Kontrakt</span><span class="sxs-lookup"><span data-stu-id="74467-103">Contract</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74467-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="74467-104">Syntax</span></span>  
  
```  
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
  
## <a name="methods"></a><span data-ttu-id="74467-105">Metody</span><span class="sxs-lookup"><span data-stu-id="74467-105">Methods</span></span>  
 <span data-ttu-id="74467-106">Třídou kontraktu nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="74467-106">The Contract class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="74467-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="74467-107">Properties</span></span>  
 <span data-ttu-id="74467-108">Třída smlouvy má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="74467-108">The Contract class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="74467-109">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="74467-109">AppDomainId</span></span>  
 <span data-ttu-id="74467-110">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="74467-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="74467-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="74467-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="74467-112">Identifikační číslo domény, která hostuje kontrakt.</span><span class="sxs-lookup"><span data-stu-id="74467-112">The appdomain id of the appdomain that hosts the contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="74467-113">Chování</span><span class="sxs-lookup"><span data-stu-id="74467-113">Behaviors</span></span>  
 <span data-ttu-id="74467-114">Datový typ: chování pole</span><span class="sxs-lookup"><span data-stu-id="74467-114">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="74467-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="74467-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="74467-116">Chování přidružené k této smlouvy.</span><span class="sxs-lookup"><span data-stu-id="74467-116">The behaviors associated with this contract.</span></span>  
  
### <a name="name"></a><span data-ttu-id="74467-117">Název</span><span class="sxs-lookup"><span data-stu-id="74467-117">Name</span></span>  
 <span data-ttu-id="74467-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="74467-118">Data type: string</span></span>  
  
 <span data-ttu-id="74467-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="74467-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="74467-120">Název smlouvy, které ve schématu WSDL.</span><span class="sxs-lookup"><span data-stu-id="74467-120">The name of the contract in WSDL.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="74467-121">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="74467-121">Namespace</span></span>  
 <span data-ttu-id="74467-122">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="74467-122">Data type: string</span></span>  
  
 <span data-ttu-id="74467-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="74467-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="74467-124">Obor názvů `portType` element v jazyce WSDL.</span><span class="sxs-lookup"><span data-stu-id="74467-124">The namespace of the `portType` element in WSDL.</span></span>  
  
### <a name="operations"></a><span data-ttu-id="74467-125">Operace</span><span class="sxs-lookup"><span data-stu-id="74467-125">Operations</span></span>  
 <span data-ttu-id="74467-126">Datový typ: operace pole</span><span class="sxs-lookup"><span data-stu-id="74467-126">Data type: Operation array</span></span>  
  
 <span data-ttu-id="74467-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="74467-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="74467-128">Operace tohoto kontraktu.</span><span class="sxs-lookup"><span data-stu-id="74467-128">The operations of this contract.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="74467-129">ID procesu</span><span class="sxs-lookup"><span data-stu-id="74467-129">ProcessId</span></span>  
 <span data-ttu-id="74467-130">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="74467-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="74467-131">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="74467-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="74467-132">Id procesu, který je hostitelem kontrakt procesu.</span><span class="sxs-lookup"><span data-stu-id="74467-132">The process Id of the process that hosts the contract.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="74467-133">ref</span><span class="sxs-lookup"><span data-stu-id="74467-133">ref</span></span>  
 <span data-ttu-id="74467-134">Datový typ: kontraktu</span><span class="sxs-lookup"><span data-stu-id="74467-134">Data type: Contract</span></span>  
  
 <span data-ttu-id="74467-135">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="74467-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="74467-136">Typ zpětné volání, když je kontrakt duplexního kontraktu.</span><span class="sxs-lookup"><span data-stu-id="74467-136">The type of callback when the contract is a duplex contract.</span></span>  
  
### <a name="sessionmode"></a><span data-ttu-id="74467-137">SessionMode</span><span class="sxs-lookup"><span data-stu-id="74467-137">SessionMode</span></span>  
 <span data-ttu-id="74467-138">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="74467-138">Data type: string</span></span>  
  
 <span data-ttu-id="74467-139">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="74467-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="74467-140">Určuje, jestli kontrakt vyžaduje vazby přidružené k této smlouvy pro použití kanálu relací.</span><span class="sxs-lookup"><span data-stu-id="74467-140">Indicates whether the contract requires the binding associated with this contract to use channel sessions.</span></span>  
  
### <a name="type"></a><span data-ttu-id="74467-141">Typ</span><span class="sxs-lookup"><span data-stu-id="74467-141">Type</span></span>  
 <span data-ttu-id="74467-142">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="74467-142">Data type: string</span></span>  
  
 <span data-ttu-id="74467-143">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="74467-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="74467-144">Typ smlouvy.</span><span class="sxs-lookup"><span data-stu-id="74467-144">The type of the contract.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74467-145">Požadavky</span><span class="sxs-lookup"><span data-stu-id="74467-145">Requirements</span></span>  
  
|<span data-ttu-id="74467-146">MOF</span><span class="sxs-lookup"><span data-stu-id="74467-146">MOF</span></span>|<span data-ttu-id="74467-147">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="74467-147">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="74467-148">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="74467-148">Namespace</span></span>|<span data-ttu-id="74467-149">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="74467-149">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="74467-150">Viz také</span><span class="sxs-lookup"><span data-stu-id="74467-150">See Also</span></span>  
 <xref:System.ServiceModel.Description.ContractDescription>
