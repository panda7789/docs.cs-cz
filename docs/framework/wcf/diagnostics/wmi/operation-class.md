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
ms.openlocfilehash: 492a3cb4b11706bfabc42976fb1adfad24a2279a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="operation-class"></a><span data-ttu-id="e91d7-102">Třída Operation</span><span class="sxs-lookup"><span data-stu-id="e91d7-102">Operation class</span></span>
<span data-ttu-id="e91d7-103">Operace</span><span class="sxs-lookup"><span data-stu-id="e91d7-103">Operation</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e91d7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e91d7-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="e91d7-105">Metody</span><span class="sxs-lookup"><span data-stu-id="e91d7-105">Methods</span></span>  
 <span data-ttu-id="e91d7-106">Třída Operation nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="e91d7-106">The Operation class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e91d7-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e91d7-107">Properties</span></span>  
 <span data-ttu-id="e91d7-108">Třída Operation má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="e91d7-108">The Operation class has the following properties:</span></span>  
  
### <a name="action"></a><span data-ttu-id="e91d7-109">Akce</span><span class="sxs-lookup"><span data-stu-id="e91d7-109">Action</span></span>  
 <span data-ttu-id="e91d7-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="e91d7-110">Data type: string</span></span>  
  
 <span data-ttu-id="e91d7-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e91d7-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e91d7-112">Akce WS-Addressing zprávy požadavku.</span><span class="sxs-lookup"><span data-stu-id="e91d7-112">The WS-Addressing action of the request message.</span></span>  
  
### <a name="asyncpattern"></a><span data-ttu-id="e91d7-113">Parametru AsyncPattern</span><span class="sxs-lookup"><span data-stu-id="e91d7-113">AsyncPattern</span></span>  
 <span data-ttu-id="e91d7-114">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="e91d7-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="e91d7-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e91d7-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e91d7-116">Označuje, že operace je implementovaná asynchronně pomocí `Begin`[otevření nebo uzavření lomené závorky] a `End`pár – metoda [otevření nebo uzavření lomené závorky] v kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="e91d7-116">Indicates that an operation is implemented asynchronously using a `Begin`[open/close angle brackets] and `End`[open/close angle brackets] method pair in a service contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="e91d7-117">Chování</span><span class="sxs-lookup"><span data-stu-id="e91d7-117">Behaviors</span></span>  
 <span data-ttu-id="e91d7-118">Datový typ: chování pole</span><span class="sxs-lookup"><span data-stu-id="e91d7-118">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="e91d7-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e91d7-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e91d7-120">Chování, které jsou spojené s touto operací.</span><span class="sxs-lookup"><span data-stu-id="e91d7-120">The behaviors associated with this operation.</span></span>  
  
### <a name="iscallback"></a><span data-ttu-id="e91d7-121">IsCallback</span><span class="sxs-lookup"><span data-stu-id="e91d7-121">IsCallback</span></span>  
 <span data-ttu-id="e91d7-122">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="e91d7-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="e91d7-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e91d7-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e91d7-124">Hodnota TRUE, po operaci zpětného volání operace.</span><span class="sxs-lookup"><span data-stu-id="e91d7-124">True when the operation is a callback operation.</span></span>  
  
### <a name="isinitiating"></a><span data-ttu-id="e91d7-125">IsInitiating</span><span class="sxs-lookup"><span data-stu-id="e91d7-125">IsInitiating</span></span>  
 <span data-ttu-id="e91d7-126">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="e91d7-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="e91d7-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e91d7-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e91d7-128">Určuje, zda metoda provádí operaci, která můžete zahájit relaci na serveru.</span><span class="sxs-lookup"><span data-stu-id="e91d7-128">Indicates whether the method implements an operation that can initiate a session on the server.</span></span>  
  
### <a name="isoneway"></a><span data-ttu-id="e91d7-129">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="e91d7-129">IsOneWay</span></span>  
 <span data-ttu-id="e91d7-130">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="e91d7-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="e91d7-131">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e91d7-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e91d7-132">Určuje, zda operace vrátí zprávu odpovědi.</span><span class="sxs-lookup"><span data-stu-id="e91d7-132">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="isterminating"></a><span data-ttu-id="e91d7-133">IsTerminating</span><span class="sxs-lookup"><span data-stu-id="e91d7-133">IsTerminating</span></span>  
 <span data-ttu-id="e91d7-134">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="e91d7-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="e91d7-135">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e91d7-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e91d7-136">Určuje, zda operace vrátí zprávu odpovědi.</span><span class="sxs-lookup"><span data-stu-id="e91d7-136">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="methodsignature"></a><span data-ttu-id="e91d7-137">MethodSignature</span><span class="sxs-lookup"><span data-stu-id="e91d7-137">MethodSignature</span></span>  
 <span data-ttu-id="e91d7-138">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="e91d7-138">Data type: string</span></span>  
  
 <span data-ttu-id="e91d7-139">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e91d7-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e91d7-140">Podpis metody operace.</span><span class="sxs-lookup"><span data-stu-id="e91d7-140">The method signature of the operation.</span></span>  
  
### <a name="name"></a><span data-ttu-id="e91d7-141">Název</span><span class="sxs-lookup"><span data-stu-id="e91d7-141">Name</span></span>  
 <span data-ttu-id="e91d7-142">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="e91d7-142">Data type: string</span></span>  
  
 <span data-ttu-id="e91d7-143">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e91d7-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e91d7-144">Název operace.</span><span class="sxs-lookup"><span data-stu-id="e91d7-144">The name of the operation.</span></span>  
  
### <a name="parametertypes"></a><span data-ttu-id="e91d7-145">ParameterTypes</span><span class="sxs-lookup"><span data-stu-id="e91d7-145">ParameterTypes</span></span>  
 <span data-ttu-id="e91d7-146">Datový typ: pole řetězců</span><span class="sxs-lookup"><span data-stu-id="e91d7-146">Data type: string array</span></span>  
  
 <span data-ttu-id="e91d7-147">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e91d7-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e91d7-148">Typy parametrů operace.</span><span class="sxs-lookup"><span data-stu-id="e91d7-148">The types of the parameters of the operation.</span></span>  
  
### <a name="replyaction"></a><span data-ttu-id="e91d7-149">ReplyAction</span><span class="sxs-lookup"><span data-stu-id="e91d7-149">ReplyAction</span></span>  
 <span data-ttu-id="e91d7-150">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="e91d7-150">Data type: string</span></span>  
  
 <span data-ttu-id="e91d7-151">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e91d7-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e91d7-152">Hodnota akce SOAP zprávy s odpovědí operace.</span><span class="sxs-lookup"><span data-stu-id="e91d7-152">The value of the SOAP action for the reply message of the operation.</span></span>  
  
### <a name="returntype"></a><span data-ttu-id="e91d7-153">Vlastnost ReturnType</span><span class="sxs-lookup"><span data-stu-id="e91d7-153">ReturnType</span></span>  
 <span data-ttu-id="e91d7-154">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="e91d7-154">Data type: string</span></span>  
  
 <span data-ttu-id="e91d7-155">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e91d7-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e91d7-156">Návratový typ operace.</span><span class="sxs-lookup"><span data-stu-id="e91d7-156">The return type of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e91d7-157">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e91d7-157">Requirements</span></span>  
  
|<span data-ttu-id="e91d7-158">MOF</span><span class="sxs-lookup"><span data-stu-id="e91d7-158">MOF</span></span>|<span data-ttu-id="e91d7-159">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="e91d7-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e91d7-160">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="e91d7-160">Namespace</span></span>|<span data-ttu-id="e91d7-161">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e91d7-161">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e91d7-162">Viz také</span><span class="sxs-lookup"><span data-stu-id="e91d7-162">See Also</span></span>  
 <xref:System.ServiceModel.Description.OperationDescription>
