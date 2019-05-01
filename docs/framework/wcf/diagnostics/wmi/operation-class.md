---
title: Třída Operation
ms.date: 03/30/2017
ms.assetid: b19d1496-ef06-4d0c-b2ae-e728ec00cca0
ms.openlocfilehash: 9696a7f026e54afacb5ccbfa8703a2ba617a9f3d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61963108"
---
# <a name="operation-class"></a><span data-ttu-id="94844-102">Třída Operation</span><span class="sxs-lookup"><span data-stu-id="94844-102">Operation class</span></span>
<span data-ttu-id="94844-103">Operace</span><span class="sxs-lookup"><span data-stu-id="94844-103">Operation</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94844-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="94844-104">Syntax</span></span>  
  
```csharp
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
  
## <a name="methods"></a><span data-ttu-id="94844-105">Metody</span><span class="sxs-lookup"><span data-stu-id="94844-105">Methods</span></span>  
 <span data-ttu-id="94844-106">Třída Operation nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="94844-106">The Operation class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="94844-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="94844-107">Properties</span></span>  
 <span data-ttu-id="94844-108">Třída Operation má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="94844-108">The Operation class has the following properties:</span></span>  
  
### <a name="action"></a><span data-ttu-id="94844-109">Akce</span><span class="sxs-lookup"><span data-stu-id="94844-109">Action</span></span>  
 <span data-ttu-id="94844-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="94844-110">Data type: string</span></span>  
  
 <span data-ttu-id="94844-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="94844-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="94844-112">Akce WS-Adressing zprávy s požadavkem.</span><span class="sxs-lookup"><span data-stu-id="94844-112">The WS-Addressing action of the request message.</span></span>  
  
### <a name="asyncpattern"></a><span data-ttu-id="94844-113">AsyncPattern</span><span class="sxs-lookup"><span data-stu-id="94844-113">AsyncPattern</span></span>  
 <span data-ttu-id="94844-114">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="94844-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="94844-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="94844-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="94844-116">Označuje, že operace je provedena asynchronně pomocí `Begin`[otevřít nebo zavřít ostrých závorek] a `End`dvojice metody [otevřít nebo zavřít ostrých závorek] v kontraktu služby.</span><span class="sxs-lookup"><span data-stu-id="94844-116">Indicates that an operation is implemented asynchronously using a `Begin`[open/close angle brackets] and `End`[open/close angle brackets] method pair in a service contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="94844-117">Chování</span><span class="sxs-lookup"><span data-stu-id="94844-117">Behaviors</span></span>  
 <span data-ttu-id="94844-118">Datový typ: Chování pole</span><span class="sxs-lookup"><span data-stu-id="94844-118">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="94844-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="94844-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="94844-120">Chování, které jsou spojené s touto operací.</span><span class="sxs-lookup"><span data-stu-id="94844-120">The behaviors associated with this operation.</span></span>  
  
### <a name="iscallback"></a><span data-ttu-id="94844-121">IsCallback</span><span class="sxs-lookup"><span data-stu-id="94844-121">IsCallback</span></span>  
 <span data-ttu-id="94844-122">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="94844-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="94844-123">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="94844-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="94844-124">Hodnota TRUE, pokud je operace operací zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="94844-124">True when the operation is a callback operation.</span></span>  
  
### <a name="isinitiating"></a><span data-ttu-id="94844-125">IsInitiating</span><span class="sxs-lookup"><span data-stu-id="94844-125">IsInitiating</span></span>  
 <span data-ttu-id="94844-126">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="94844-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="94844-127">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="94844-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="94844-128">Určuje, zda metoda provádí operaci, která může iniciovat relaci na serveru.</span><span class="sxs-lookup"><span data-stu-id="94844-128">Indicates whether the method implements an operation that can initiate a session on the server.</span></span>  
  
### <a name="isoneway"></a><span data-ttu-id="94844-129">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="94844-129">IsOneWay</span></span>  
 <span data-ttu-id="94844-130">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="94844-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="94844-131">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="94844-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="94844-132">Určuje, zda operace vrátí zprávy s odpovědí.</span><span class="sxs-lookup"><span data-stu-id="94844-132">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="isterminating"></a><span data-ttu-id="94844-133">IsTerminating</span><span class="sxs-lookup"><span data-stu-id="94844-133">IsTerminating</span></span>  
 <span data-ttu-id="94844-134">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="94844-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="94844-135">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="94844-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="94844-136">Určuje, zda operace vrátí zprávy s odpovědí.</span><span class="sxs-lookup"><span data-stu-id="94844-136">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="methodsignature"></a><span data-ttu-id="94844-137">MethodSignature</span><span class="sxs-lookup"><span data-stu-id="94844-137">MethodSignature</span></span>  
 <span data-ttu-id="94844-138">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="94844-138">Data type: string</span></span>  
  
 <span data-ttu-id="94844-139">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="94844-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="94844-140">Označení metody operace.</span><span class="sxs-lookup"><span data-stu-id="94844-140">The method signature of the operation.</span></span>  
  
### <a name="name"></a><span data-ttu-id="94844-141">Název</span><span class="sxs-lookup"><span data-stu-id="94844-141">Name</span></span>  
 <span data-ttu-id="94844-142">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="94844-142">Data type: string</span></span>  
  
 <span data-ttu-id="94844-143">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="94844-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="94844-144">Název operace.</span><span class="sxs-lookup"><span data-stu-id="94844-144">The name of the operation.</span></span>  
  
### <a name="parametertypes"></a><span data-ttu-id="94844-145">ParameterTypes</span><span class="sxs-lookup"><span data-stu-id="94844-145">ParameterTypes</span></span>  
 <span data-ttu-id="94844-146">Datový typ: pole řetězců</span><span class="sxs-lookup"><span data-stu-id="94844-146">Data type: string array</span></span>  
  
 <span data-ttu-id="94844-147">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="94844-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="94844-148">Typy parametrů operace.</span><span class="sxs-lookup"><span data-stu-id="94844-148">The types of the parameters of the operation.</span></span>  
  
### <a name="replyaction"></a><span data-ttu-id="94844-149">Třídu ReplyAction</span><span class="sxs-lookup"><span data-stu-id="94844-149">ReplyAction</span></span>  
 <span data-ttu-id="94844-150">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="94844-150">Data type: string</span></span>  
  
 <span data-ttu-id="94844-151">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="94844-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="94844-152">Hodnota akce SOAP pro odpověď operace.</span><span class="sxs-lookup"><span data-stu-id="94844-152">The value of the SOAP action for the reply message of the operation.</span></span>  
  
### <a name="returntype"></a><span data-ttu-id="94844-153">Vlastnost ReturnType</span><span class="sxs-lookup"><span data-stu-id="94844-153">ReturnType</span></span>  
 <span data-ttu-id="94844-154">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="94844-154">Data type: string</span></span>  
  
 <span data-ttu-id="94844-155">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="94844-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="94844-156">Návratový typ operace.</span><span class="sxs-lookup"><span data-stu-id="94844-156">The return type of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94844-157">Požadavky</span><span class="sxs-lookup"><span data-stu-id="94844-157">Requirements</span></span>  
  
|<span data-ttu-id="94844-158">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="94844-158">MOF</span></span>|<span data-ttu-id="94844-159">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="94844-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="94844-160">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="94844-160">Namespace</span></span>|<span data-ttu-id="94844-161">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="94844-161">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="94844-162">Viz také:</span><span class="sxs-lookup"><span data-stu-id="94844-162">See also</span></span>

- <xref:System.ServiceModel.Description.OperationDescription>
