---
title: "Třída Operation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b19d1496-ef06-4d0c-b2ae-e728ec00cca0
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 739f8309e7a01eeecf921b50fcde24417fbbc515
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="operation-class"></a><span data-ttu-id="57cb4-102">Třída Operation</span><span class="sxs-lookup"><span data-stu-id="57cb4-102">Operation class</span></span>
<span data-ttu-id="57cb4-103">Operace</span><span class="sxs-lookup"><span data-stu-id="57cb4-103">Operation</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57cb4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="57cb4-104">Syntax</span></span>  
  
```  
class Operation  
{  
  string Action;  
  boolean AsyncPattern;  
  Behavior Behaviors[];  
  boolean IsCallback;  
  boolean IsInitiating;  
  boolean IsOneWay;  
  boolean IsTerminating;  
  string MethodSignature;  
  string Name;  
  string ParameterTypes[];  
  string ReplyAction;  
  string ReturnType;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="57cb4-105">Metody</span><span class="sxs-lookup"><span data-stu-id="57cb4-105">Methods</span></span>  
 <span data-ttu-id="57cb4-106">Třída Operation nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="57cb4-106">The Operation class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="57cb4-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="57cb4-107">Properties</span></span>  
 <span data-ttu-id="57cb4-108">Třída Operation má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="57cb4-108">The Operation class has the following properties:</span></span>  
  
### <a name="action"></a><span data-ttu-id="57cb4-109">Akce</span><span class="sxs-lookup"><span data-stu-id="57cb4-109">Action</span></span>  
 <span data-ttu-id="57cb4-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="57cb4-110">Data type: string</span></span>  
  
 <span data-ttu-id="57cb4-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="57cb4-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="57cb4-112">Akce WS-Addressing zprávy požadavku.</span><span class="sxs-lookup"><span data-stu-id="57cb4-112">The WS-Addressing action of the request message.</span></span>  
  
### <a name="asyncpattern"></a><span data-ttu-id="57cb4-113">Parametru AsyncPattern</span><span class="sxs-lookup"><span data-stu-id="57cb4-113">AsyncPattern</span></span>  
 <span data-ttu-id="57cb4-114">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="57cb4-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="57cb4-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="57cb4-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="57cb4-116">Označuje, že operace je implementovaná asynchronně pomocí `Begin`[otevření nebo uzavření lomené závorky] a `End`pár – metoda [otevření nebo uzavření lomené závorky] v kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="57cb4-116">Indicates that an operation is implemented asynchronously using a `Begin`[open/close angle brackets] and `End`[open/close angle brackets] method pair in a service contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="57cb4-117">Chování</span><span class="sxs-lookup"><span data-stu-id="57cb4-117">Behaviors</span></span>  
 <span data-ttu-id="57cb4-118">Datový typ: chování pole</span><span class="sxs-lookup"><span data-stu-id="57cb4-118">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="57cb4-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="57cb4-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="57cb4-120">Chování, které jsou spojené s touto operací.</span><span class="sxs-lookup"><span data-stu-id="57cb4-120">The behaviors associated with this operation.</span></span>  
  
### <a name="iscallback"></a><span data-ttu-id="57cb4-121">IsCallback</span><span class="sxs-lookup"><span data-stu-id="57cb4-121">IsCallback</span></span>  
 <span data-ttu-id="57cb4-122">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="57cb4-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="57cb4-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="57cb4-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="57cb4-124">Hodnota TRUE, po operaci zpětného volání operace.</span><span class="sxs-lookup"><span data-stu-id="57cb4-124">True when the operation is a callback operation.</span></span>  
  
### <a name="isinitiating"></a><span data-ttu-id="57cb4-125">IsInitiating</span><span class="sxs-lookup"><span data-stu-id="57cb4-125">IsInitiating</span></span>  
 <span data-ttu-id="57cb4-126">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="57cb4-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="57cb4-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="57cb4-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="57cb4-128">Určuje, zda metoda provádí operaci, která můžete zahájit relaci na serveru.</span><span class="sxs-lookup"><span data-stu-id="57cb4-128">Indicates whether the method implements an operation that can initiate a session on the server.</span></span>  
  
### <a name="isoneway"></a><span data-ttu-id="57cb4-129">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="57cb4-129">IsOneWay</span></span>  
 <span data-ttu-id="57cb4-130">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="57cb4-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="57cb4-131">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="57cb4-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="57cb4-132">Určuje, zda operace vrátí zprávu odpovědi.</span><span class="sxs-lookup"><span data-stu-id="57cb4-132">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="isterminating"></a><span data-ttu-id="57cb4-133">IsTerminating</span><span class="sxs-lookup"><span data-stu-id="57cb4-133">IsTerminating</span></span>  
 <span data-ttu-id="57cb4-134">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="57cb4-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="57cb4-135">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="57cb4-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="57cb4-136">Určuje, zda operace vrátí zprávu odpovědi.</span><span class="sxs-lookup"><span data-stu-id="57cb4-136">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="methodsignature"></a><span data-ttu-id="57cb4-137">MethodSignature</span><span class="sxs-lookup"><span data-stu-id="57cb4-137">MethodSignature</span></span>  
 <span data-ttu-id="57cb4-138">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="57cb4-138">Data type: string</span></span>  
  
 <span data-ttu-id="57cb4-139">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="57cb4-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="57cb4-140">Podpis metody operace.</span><span class="sxs-lookup"><span data-stu-id="57cb4-140">The method signature of the operation.</span></span>  
  
### <a name="name"></a><span data-ttu-id="57cb4-141">Název</span><span class="sxs-lookup"><span data-stu-id="57cb4-141">Name</span></span>  
 <span data-ttu-id="57cb4-142">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="57cb4-142">Data type: string</span></span>  
  
 <span data-ttu-id="57cb4-143">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="57cb4-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="57cb4-144">Název operace.</span><span class="sxs-lookup"><span data-stu-id="57cb4-144">The name of the operation.</span></span>  
  
### <a name="parametertypes"></a><span data-ttu-id="57cb4-145">ParameterTypes</span><span class="sxs-lookup"><span data-stu-id="57cb4-145">ParameterTypes</span></span>  
 <span data-ttu-id="57cb4-146">Datový typ: pole řetězců</span><span class="sxs-lookup"><span data-stu-id="57cb4-146">Data type: string array</span></span>  
  
 <span data-ttu-id="57cb4-147">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="57cb4-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="57cb4-148">Typy parametrů operace.</span><span class="sxs-lookup"><span data-stu-id="57cb4-148">The types of the parameters of the operation.</span></span>  
  
### <a name="replyaction"></a><span data-ttu-id="57cb4-149">ReplyAction</span><span class="sxs-lookup"><span data-stu-id="57cb4-149">ReplyAction</span></span>  
 <span data-ttu-id="57cb4-150">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="57cb4-150">Data type: string</span></span>  
  
 <span data-ttu-id="57cb4-151">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="57cb4-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="57cb4-152">Hodnota akce SOAP zprávy s odpovědí operace.</span><span class="sxs-lookup"><span data-stu-id="57cb4-152">The value of the SOAP action for the reply message of the operation.</span></span>  
  
### <a name="returntype"></a><span data-ttu-id="57cb4-153">Vlastnost ReturnType</span><span class="sxs-lookup"><span data-stu-id="57cb4-153">ReturnType</span></span>  
 <span data-ttu-id="57cb4-154">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="57cb4-154">Data type: string</span></span>  
  
 <span data-ttu-id="57cb4-155">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="57cb4-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="57cb4-156">Návratový typ operace.</span><span class="sxs-lookup"><span data-stu-id="57cb4-156">The return type of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57cb4-157">Požadavky</span><span class="sxs-lookup"><span data-stu-id="57cb4-157">Requirements</span></span>  
  
|<span data-ttu-id="57cb4-158">MOF</span><span class="sxs-lookup"><span data-stu-id="57cb4-158">MOF</span></span>|<span data-ttu-id="57cb4-159">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="57cb4-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="57cb4-160">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="57cb4-160">Namespace</span></span>|<span data-ttu-id="57cb4-161">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="57cb4-161">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="57cb4-162">Viz také</span><span class="sxs-lookup"><span data-stu-id="57cb4-162">See Also</span></span>  
 <xref:System.ServiceModel.Description.OperationDescription>
