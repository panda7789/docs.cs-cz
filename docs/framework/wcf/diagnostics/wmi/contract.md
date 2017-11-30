---
title: Contract1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2e92c5d804fca3c04506e951a5c341c89eed1c54
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="contract"></a><span data-ttu-id="f2825-102">Kontrakt</span><span class="sxs-lookup"><span data-stu-id="f2825-102">Contract</span></span>
<span data-ttu-id="f2825-103">Kontrakt</span><span class="sxs-lookup"><span data-stu-id="f2825-103">Contract</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2825-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2825-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="f2825-105">Metody</span><span class="sxs-lookup"><span data-stu-id="f2825-105">Methods</span></span>  
 <span data-ttu-id="f2825-106">Třídou kontraktu nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="f2825-106">The Contract class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f2825-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="f2825-107">Properties</span></span>  
 <span data-ttu-id="f2825-108">Třída smlouvy má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="f2825-108">The Contract class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="f2825-109">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="f2825-109">AppDomainId</span></span>  
 <span data-ttu-id="f2825-110">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="f2825-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="f2825-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f2825-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f2825-112">Identifikační číslo domény, která hostuje kontrakt.</span><span class="sxs-lookup"><span data-stu-id="f2825-112">The appdomain id of the appdomain that hosts the contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="f2825-113">Chování</span><span class="sxs-lookup"><span data-stu-id="f2825-113">Behaviors</span></span>  
 <span data-ttu-id="f2825-114">Datový typ: chování pole</span><span class="sxs-lookup"><span data-stu-id="f2825-114">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="f2825-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f2825-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f2825-116">Chování přidružené k této smlouvy.</span><span class="sxs-lookup"><span data-stu-id="f2825-116">The behaviors associated with this contract.</span></span>  
  
### <a name="name"></a><span data-ttu-id="f2825-117">Název</span><span class="sxs-lookup"><span data-stu-id="f2825-117">Name</span></span>  
 <span data-ttu-id="f2825-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="f2825-118">Data type: string</span></span>  
  
 <span data-ttu-id="f2825-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f2825-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f2825-120">Název smlouvy, které ve schématu WSDL.</span><span class="sxs-lookup"><span data-stu-id="f2825-120">The name of the contract in WSDL.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="f2825-121">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="f2825-121">Namespace</span></span>  
 <span data-ttu-id="f2825-122">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="f2825-122">Data type: string</span></span>  
  
 <span data-ttu-id="f2825-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f2825-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f2825-124">Obor názvů `portType` element v jazyce WSDL.</span><span class="sxs-lookup"><span data-stu-id="f2825-124">The namespace of the `portType` element in WSDL.</span></span>  
  
### <a name="operations"></a><span data-ttu-id="f2825-125">Operace</span><span class="sxs-lookup"><span data-stu-id="f2825-125">Operations</span></span>  
 <span data-ttu-id="f2825-126">Datový typ: operace pole</span><span class="sxs-lookup"><span data-stu-id="f2825-126">Data type: Operation array</span></span>  
  
 <span data-ttu-id="f2825-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f2825-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f2825-128">Operace tohoto kontraktu.</span><span class="sxs-lookup"><span data-stu-id="f2825-128">The operations of this contract.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="f2825-129">ID procesu</span><span class="sxs-lookup"><span data-stu-id="f2825-129">ProcessId</span></span>  
 <span data-ttu-id="f2825-130">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="f2825-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="f2825-131">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f2825-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f2825-132">Id procesu, který je hostitelem kontrakt procesu.</span><span class="sxs-lookup"><span data-stu-id="f2825-132">The process Id of the process that hosts the contract.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="f2825-133">ref</span><span class="sxs-lookup"><span data-stu-id="f2825-133">ref</span></span>  
 <span data-ttu-id="f2825-134">Datový typ: kontraktu</span><span class="sxs-lookup"><span data-stu-id="f2825-134">Data type: Contract</span></span>  
  
 <span data-ttu-id="f2825-135">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f2825-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f2825-136">Typ zpětné volání, když je kontrakt duplexního kontraktu.</span><span class="sxs-lookup"><span data-stu-id="f2825-136">The type of callback when the contract is a duplex contract.</span></span>  
  
### <a name="sessionmode"></a><span data-ttu-id="f2825-137">SessionMode</span><span class="sxs-lookup"><span data-stu-id="f2825-137">SessionMode</span></span>  
 <span data-ttu-id="f2825-138">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="f2825-138">Data type: string</span></span>  
  
 <span data-ttu-id="f2825-139">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f2825-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f2825-140">Určuje, jestli kontrakt vyžaduje vazby přidružené k této smlouvy pro použití kanálu relací.</span><span class="sxs-lookup"><span data-stu-id="f2825-140">Indicates whether the contract requires the binding associated with this contract to use channel sessions.</span></span>  
  
### <a name="type"></a><span data-ttu-id="f2825-141">Typ</span><span class="sxs-lookup"><span data-stu-id="f2825-141">Type</span></span>  
 <span data-ttu-id="f2825-142">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="f2825-142">Data type: string</span></span>  
  
 <span data-ttu-id="f2825-143">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f2825-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f2825-144">Typ smlouvy.</span><span class="sxs-lookup"><span data-stu-id="f2825-144">The type of the contract.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2825-145">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f2825-145">Requirements</span></span>  
  
|<span data-ttu-id="f2825-146">MOF</span><span class="sxs-lookup"><span data-stu-id="f2825-146">MOF</span></span>|<span data-ttu-id="f2825-147">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="f2825-147">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="f2825-148">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="f2825-148">Namespace</span></span>|<span data-ttu-id="f2825-149">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f2825-149">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f2825-150">Viz také</span><span class="sxs-lookup"><span data-stu-id="f2825-150">See Also</span></span>  
 <xref:System.ServiceModel.Description.ContractDescription>
