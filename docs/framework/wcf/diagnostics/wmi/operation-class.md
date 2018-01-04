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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 54566bc452baa2e02cef7d8d13d29fcd5864c95c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="operation-class"></a><span data-ttu-id="5132f-102">Třída Operation</span><span class="sxs-lookup"><span data-stu-id="5132f-102">Operation class</span></span>
<span data-ttu-id="5132f-103">Operace</span><span class="sxs-lookup"><span data-stu-id="5132f-103">Operation</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5132f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5132f-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="5132f-105">Metody</span><span class="sxs-lookup"><span data-stu-id="5132f-105">Methods</span></span>  
 <span data-ttu-id="5132f-106">Třída Operation nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="5132f-106">The Operation class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="5132f-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="5132f-107">Properties</span></span>  
 <span data-ttu-id="5132f-108">Třída Operation má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="5132f-108">The Operation class has the following properties:</span></span>  
  
### <a name="action"></a><span data-ttu-id="5132f-109">Akce</span><span class="sxs-lookup"><span data-stu-id="5132f-109">Action</span></span>  
 <span data-ttu-id="5132f-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="5132f-110">Data type: string</span></span>  
  
 <span data-ttu-id="5132f-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="5132f-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5132f-112">Akce WS-Addressing zprávy požadavku.</span><span class="sxs-lookup"><span data-stu-id="5132f-112">The WS-Addressing action of the request message.</span></span>  
  
### <a name="asyncpattern"></a><span data-ttu-id="5132f-113">Parametru AsyncPattern</span><span class="sxs-lookup"><span data-stu-id="5132f-113">AsyncPattern</span></span>  
 <span data-ttu-id="5132f-114">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="5132f-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="5132f-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="5132f-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5132f-116">Označuje, že operace je implementovaná asynchronně pomocí `Begin`[otevření nebo uzavření lomené závorky] a `End`pár – metoda [otevření nebo uzavření lomené závorky] v kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="5132f-116">Indicates that an operation is implemented asynchronously using a `Begin`[open/close angle brackets] and `End`[open/close angle brackets] method pair in a service contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="5132f-117">Chování</span><span class="sxs-lookup"><span data-stu-id="5132f-117">Behaviors</span></span>  
 <span data-ttu-id="5132f-118">Datový typ: chování pole</span><span class="sxs-lookup"><span data-stu-id="5132f-118">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="5132f-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="5132f-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5132f-120">Chování, které jsou spojené s touto operací.</span><span class="sxs-lookup"><span data-stu-id="5132f-120">The behaviors associated with this operation.</span></span>  
  
### <a name="iscallback"></a><span data-ttu-id="5132f-121">IsCallback</span><span class="sxs-lookup"><span data-stu-id="5132f-121">IsCallback</span></span>  
 <span data-ttu-id="5132f-122">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="5132f-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="5132f-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="5132f-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5132f-124">Hodnota TRUE, po operaci zpětného volání operace.</span><span class="sxs-lookup"><span data-stu-id="5132f-124">True when the operation is a callback operation.</span></span>  
  
### <a name="isinitiating"></a><span data-ttu-id="5132f-125">IsInitiating</span><span class="sxs-lookup"><span data-stu-id="5132f-125">IsInitiating</span></span>  
 <span data-ttu-id="5132f-126">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="5132f-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="5132f-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="5132f-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5132f-128">Určuje, zda metoda provádí operaci, která můžete zahájit relaci na serveru.</span><span class="sxs-lookup"><span data-stu-id="5132f-128">Indicates whether the method implements an operation that can initiate a session on the server.</span></span>  
  
### <a name="isoneway"></a><span data-ttu-id="5132f-129">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="5132f-129">IsOneWay</span></span>  
 <span data-ttu-id="5132f-130">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="5132f-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="5132f-131">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="5132f-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5132f-132">Určuje, zda operace vrátí zprávu odpovědi.</span><span class="sxs-lookup"><span data-stu-id="5132f-132">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="isterminating"></a><span data-ttu-id="5132f-133">IsTerminating</span><span class="sxs-lookup"><span data-stu-id="5132f-133">IsTerminating</span></span>  
 <span data-ttu-id="5132f-134">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="5132f-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="5132f-135">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="5132f-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5132f-136">Určuje, zda operace vrátí zprávu odpovědi.</span><span class="sxs-lookup"><span data-stu-id="5132f-136">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="methodsignature"></a><span data-ttu-id="5132f-137">MethodSignature</span><span class="sxs-lookup"><span data-stu-id="5132f-137">MethodSignature</span></span>  
 <span data-ttu-id="5132f-138">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="5132f-138">Data type: string</span></span>  
  
 <span data-ttu-id="5132f-139">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="5132f-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5132f-140">Podpis metody operace.</span><span class="sxs-lookup"><span data-stu-id="5132f-140">The method signature of the operation.</span></span>  
  
### <a name="name"></a><span data-ttu-id="5132f-141">Název</span><span class="sxs-lookup"><span data-stu-id="5132f-141">Name</span></span>  
 <span data-ttu-id="5132f-142">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="5132f-142">Data type: string</span></span>  
  
 <span data-ttu-id="5132f-143">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="5132f-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5132f-144">Název operace.</span><span class="sxs-lookup"><span data-stu-id="5132f-144">The name of the operation.</span></span>  
  
### <a name="parametertypes"></a><span data-ttu-id="5132f-145">ParameterTypes</span><span class="sxs-lookup"><span data-stu-id="5132f-145">ParameterTypes</span></span>  
 <span data-ttu-id="5132f-146">Datový typ: pole řetězců</span><span class="sxs-lookup"><span data-stu-id="5132f-146">Data type: string array</span></span>  
  
 <span data-ttu-id="5132f-147">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="5132f-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5132f-148">Typy parametrů operace.</span><span class="sxs-lookup"><span data-stu-id="5132f-148">The types of the parameters of the operation.</span></span>  
  
### <a name="replyaction"></a><span data-ttu-id="5132f-149">ReplyAction</span><span class="sxs-lookup"><span data-stu-id="5132f-149">ReplyAction</span></span>  
 <span data-ttu-id="5132f-150">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="5132f-150">Data type: string</span></span>  
  
 <span data-ttu-id="5132f-151">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="5132f-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5132f-152">Hodnota akce SOAP zprávy s odpovědí operace.</span><span class="sxs-lookup"><span data-stu-id="5132f-152">The value of the SOAP action for the reply message of the operation.</span></span>  
  
### <a name="returntype"></a><span data-ttu-id="5132f-153">Vlastnost ReturnType</span><span class="sxs-lookup"><span data-stu-id="5132f-153">ReturnType</span></span>  
 <span data-ttu-id="5132f-154">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="5132f-154">Data type: string</span></span>  
  
 <span data-ttu-id="5132f-155">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="5132f-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5132f-156">Návratový typ operace.</span><span class="sxs-lookup"><span data-stu-id="5132f-156">The return type of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5132f-157">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5132f-157">Requirements</span></span>  
  
|<span data-ttu-id="5132f-158">MOF</span><span class="sxs-lookup"><span data-stu-id="5132f-158">MOF</span></span>|<span data-ttu-id="5132f-159">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="5132f-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="5132f-160">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="5132f-160">Namespace</span></span>|<span data-ttu-id="5132f-161">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="5132f-161">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5132f-162">Viz také</span><span class="sxs-lookup"><span data-stu-id="5132f-162">See Also</span></span>  
 <xref:System.ServiceModel.Description.OperationDescription>
