---
title: Třída Operation
ms.date: 03/30/2017
ms.assetid: b19d1496-ef06-4d0c-b2ae-e728ec00cca0
ms.openlocfilehash: d9256915afe9fdb8e4c91d186131fe41a7094c56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33487565"
---
# <a name="operation-class"></a><span data-ttu-id="98dad-102">Třída Operation</span><span class="sxs-lookup"><span data-stu-id="98dad-102">Operation class</span></span>
<span data-ttu-id="98dad-103">Operace</span><span class="sxs-lookup"><span data-stu-id="98dad-103">Operation</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98dad-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="98dad-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="98dad-105">Metody</span><span class="sxs-lookup"><span data-stu-id="98dad-105">Methods</span></span>  
 <span data-ttu-id="98dad-106">Třída Operation nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="98dad-106">The Operation class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="98dad-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="98dad-107">Properties</span></span>  
 <span data-ttu-id="98dad-108">Třída Operation má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="98dad-108">The Operation class has the following properties:</span></span>  
  
### <a name="action"></a><span data-ttu-id="98dad-109">Akce</span><span class="sxs-lookup"><span data-stu-id="98dad-109">Action</span></span>  
 <span data-ttu-id="98dad-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="98dad-110">Data type: string</span></span>  
  
 <span data-ttu-id="98dad-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="98dad-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="98dad-112">Akce WS-Addressing zprávy požadavku.</span><span class="sxs-lookup"><span data-stu-id="98dad-112">The WS-Addressing action of the request message.</span></span>  
  
### <a name="asyncpattern"></a><span data-ttu-id="98dad-113">Parametru AsyncPattern</span><span class="sxs-lookup"><span data-stu-id="98dad-113">AsyncPattern</span></span>  
 <span data-ttu-id="98dad-114">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="98dad-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="98dad-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="98dad-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="98dad-116">Označuje, že operace je implementovaná asynchronně pomocí `Begin`[otevření nebo uzavření lomené závorky] a `End`pár – metoda [otevření nebo uzavření lomené závorky] v kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="98dad-116">Indicates that an operation is implemented asynchronously using a `Begin`[open/close angle brackets] and `End`[open/close angle brackets] method pair in a service contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="98dad-117">Chování</span><span class="sxs-lookup"><span data-stu-id="98dad-117">Behaviors</span></span>  
 <span data-ttu-id="98dad-118">Datový typ: chování pole</span><span class="sxs-lookup"><span data-stu-id="98dad-118">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="98dad-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="98dad-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="98dad-120">Chování, které jsou spojené s touto operací.</span><span class="sxs-lookup"><span data-stu-id="98dad-120">The behaviors associated with this operation.</span></span>  
  
### <a name="iscallback"></a><span data-ttu-id="98dad-121">IsCallback</span><span class="sxs-lookup"><span data-stu-id="98dad-121">IsCallback</span></span>  
 <span data-ttu-id="98dad-122">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="98dad-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="98dad-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="98dad-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="98dad-124">Hodnota TRUE, po operaci zpětného volání operace.</span><span class="sxs-lookup"><span data-stu-id="98dad-124">True when the operation is a callback operation.</span></span>  
  
### <a name="isinitiating"></a><span data-ttu-id="98dad-125">IsInitiating</span><span class="sxs-lookup"><span data-stu-id="98dad-125">IsInitiating</span></span>  
 <span data-ttu-id="98dad-126">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="98dad-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="98dad-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="98dad-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="98dad-128">Určuje, zda metoda provádí operaci, která můžete zahájit relaci na serveru.</span><span class="sxs-lookup"><span data-stu-id="98dad-128">Indicates whether the method implements an operation that can initiate a session on the server.</span></span>  
  
### <a name="isoneway"></a><span data-ttu-id="98dad-129">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="98dad-129">IsOneWay</span></span>  
 <span data-ttu-id="98dad-130">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="98dad-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="98dad-131">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="98dad-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="98dad-132">Určuje, zda operace vrátí zprávu odpovědi.</span><span class="sxs-lookup"><span data-stu-id="98dad-132">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="isterminating"></a><span data-ttu-id="98dad-133">IsTerminating</span><span class="sxs-lookup"><span data-stu-id="98dad-133">IsTerminating</span></span>  
 <span data-ttu-id="98dad-134">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="98dad-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="98dad-135">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="98dad-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="98dad-136">Určuje, zda operace vrátí zprávu odpovědi.</span><span class="sxs-lookup"><span data-stu-id="98dad-136">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="methodsignature"></a><span data-ttu-id="98dad-137">MethodSignature</span><span class="sxs-lookup"><span data-stu-id="98dad-137">MethodSignature</span></span>  
 <span data-ttu-id="98dad-138">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="98dad-138">Data type: string</span></span>  
  
 <span data-ttu-id="98dad-139">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="98dad-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="98dad-140">Podpis metody operace.</span><span class="sxs-lookup"><span data-stu-id="98dad-140">The method signature of the operation.</span></span>  
  
### <a name="name"></a><span data-ttu-id="98dad-141">Název</span><span class="sxs-lookup"><span data-stu-id="98dad-141">Name</span></span>  
 <span data-ttu-id="98dad-142">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="98dad-142">Data type: string</span></span>  
  
 <span data-ttu-id="98dad-143">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="98dad-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="98dad-144">Název operace.</span><span class="sxs-lookup"><span data-stu-id="98dad-144">The name of the operation.</span></span>  
  
### <a name="parametertypes"></a><span data-ttu-id="98dad-145">ParameterTypes</span><span class="sxs-lookup"><span data-stu-id="98dad-145">ParameterTypes</span></span>  
 <span data-ttu-id="98dad-146">Datový typ: pole řetězců</span><span class="sxs-lookup"><span data-stu-id="98dad-146">Data type: string array</span></span>  
  
 <span data-ttu-id="98dad-147">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="98dad-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="98dad-148">Typy parametrů operace.</span><span class="sxs-lookup"><span data-stu-id="98dad-148">The types of the parameters of the operation.</span></span>  
  
### <a name="replyaction"></a><span data-ttu-id="98dad-149">ReplyAction</span><span class="sxs-lookup"><span data-stu-id="98dad-149">ReplyAction</span></span>  
 <span data-ttu-id="98dad-150">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="98dad-150">Data type: string</span></span>  
  
 <span data-ttu-id="98dad-151">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="98dad-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="98dad-152">Hodnota akce SOAP zprávy s odpovědí operace.</span><span class="sxs-lookup"><span data-stu-id="98dad-152">The value of the SOAP action for the reply message of the operation.</span></span>  
  
### <a name="returntype"></a><span data-ttu-id="98dad-153">Vlastnost ReturnType</span><span class="sxs-lookup"><span data-stu-id="98dad-153">ReturnType</span></span>  
 <span data-ttu-id="98dad-154">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="98dad-154">Data type: string</span></span>  
  
 <span data-ttu-id="98dad-155">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="98dad-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="98dad-156">Návratový typ operace.</span><span class="sxs-lookup"><span data-stu-id="98dad-156">The return type of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98dad-157">Požadavky</span><span class="sxs-lookup"><span data-stu-id="98dad-157">Requirements</span></span>  
  
|<span data-ttu-id="98dad-158">MOF</span><span class="sxs-lookup"><span data-stu-id="98dad-158">MOF</span></span>|<span data-ttu-id="98dad-159">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="98dad-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="98dad-160">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="98dad-160">Namespace</span></span>|<span data-ttu-id="98dad-161">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="98dad-161">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="98dad-162">Viz také</span><span class="sxs-lookup"><span data-stu-id="98dad-162">See Also</span></span>  
 <xref:System.ServiceModel.Description.OperationDescription>
