---
title: CallbackBehavior
ms.date: 03/30/2017
ms.assetid: 42acd302-2b62-4849-a2d1-a03084343ecd
ms.openlocfilehash: 2854671eaabb37066b57d87a7496183c9e5bba4d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54562844"
---
# <a name="callbackbehavior"></a><span data-ttu-id="520f5-102">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="520f5-102">CallbackBehavior</span></span>
<span data-ttu-id="520f5-103">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="520f5-103">CallbackBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="520f5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="520f5-104">Syntax</span></span>  
  
```csharp
class CallbackBehavior : Behavior  
{  
  boolean AutomaticSessionShutdown;  
  string ConcurrencyMode;  
  boolean IgnoreExtensionDataObject;  
  boolean IncludeExceptionDetailInFaults;  
  boolean MaxItemsInObjectGraph;  
  boolean UseSynchronizationContext;  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="520f5-105">Metody</span><span class="sxs-lookup"><span data-stu-id="520f5-105">Methods</span></span>  
 <span data-ttu-id="520f5-106">Třída CallbackBehavior nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="520f5-106">The CallbackBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="520f5-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="520f5-107">Properties</span></span>  
 <span data-ttu-id="520f5-108">Třída CallbackBehavior má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="520f5-108">The CallbackBehavior class has the following properties:</span></span>  
  
### <a name="automaticsessionshutdown"></a><span data-ttu-id="520f5-109">AutomaticSessionShutdown</span><span class="sxs-lookup"><span data-stu-id="520f5-109">AutomaticSessionShutdown</span></span>  
 <span data-ttu-id="520f5-110">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="520f5-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="520f5-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="520f5-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="520f5-112">V případě hodnoty true relace je automaticky uzavřena poté, co služba uzavře oboustrannou relaci.</span><span class="sxs-lookup"><span data-stu-id="520f5-112">When true, the session is automatically closed when a service closes a duplex session.</span></span>  
  
### <a name="concurrencymode"></a><span data-ttu-id="520f5-113">ConcurrencyMode</span><span class="sxs-lookup"><span data-stu-id="520f5-113">ConcurrencyMode</span></span>  
 <span data-ttu-id="520f5-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="520f5-114">Data type: string</span></span>  
<span data-ttu-id="520f5-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="520f5-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="520f5-116">Určuje, zda služba podporuje jedno vlákno, několik vláken nebo znovu zadaných volání.</span><span class="sxs-lookup"><span data-stu-id="520f5-116">Specifies whether the service supports one thread, multiple threads, or reentrant calls.</span></span>  
  
### <a name="ignoreextensiondataobject"></a><span data-ttu-id="520f5-117">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="520f5-117">IgnoreExtensionDataObject</span></span>  
 <span data-ttu-id="520f5-118">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="520f5-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="520f5-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="520f5-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="520f5-120">Hodnota, která určuje, zda mají data neznámé serializace přenosu.</span><span class="sxs-lookup"><span data-stu-id="520f5-120">A value that specifies whether to send unknown serialization data onto the wire.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="520f5-121">Třídu IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="520f5-121">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="520f5-122">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="520f5-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="520f5-123">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="520f5-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="520f5-124">Při povolené, podrobnosti o výjimkách odvolání připojeny k chybám vrácených službě.</span><span class="sxs-lookup"><span data-stu-id="520f5-124">When enabled, details about exceptions on the callback are attached to the faults returned to the service.</span></span>  
  
### <a name="maxitemsinobjectgraph"></a><span data-ttu-id="520f5-125">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="520f5-125">MaxItemsInObjectGraph</span></span>  
 <span data-ttu-id="520f5-126">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="520f5-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="520f5-127">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="520f5-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="520f5-128">Maximální počet položek povolených v serializovaném objektu.</span><span class="sxs-lookup"><span data-stu-id="520f5-128">The maximum number of items allowed in a serialized object.</span></span>  
  
### <a name="usesynchronizationcontext"></a><span data-ttu-id="520f5-129">UseSynchronizationContext</span><span class="sxs-lookup"><span data-stu-id="520f5-129">UseSynchronizationContext</span></span>  
 <span data-ttu-id="520f5-130">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="520f5-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="520f5-131">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="520f5-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="520f5-132">Určuje, jestli se má použít aktuální synchronizační kontext pro výběr vlákna exekuce.</span><span class="sxs-lookup"><span data-stu-id="520f5-132">Specifies whether to use the current synchronization context to choose the thread of execution.</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="520f5-133">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="520f5-133">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="520f5-134">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="520f5-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="520f5-135">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="520f5-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="520f5-136">Určuje, zda systém nebo aplikace uplatňuje zpracování záhlaví SOAP MustUnderstand.</span><span class="sxs-lookup"><span data-stu-id="520f5-136">Specifies whether the system or the application enforces SOAP MustUnderstand header processing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="520f5-137">Požadavky</span><span class="sxs-lookup"><span data-stu-id="520f5-137">Requirements</span></span>  
  
|<span data-ttu-id="520f5-138">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="520f5-138">MOF</span></span>|<span data-ttu-id="520f5-139">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="520f5-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="520f5-140">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="520f5-140">Namespace</span></span>|<span data-ttu-id="520f5-141">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="520f5-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="520f5-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="520f5-142">See also</span></span>
- <xref:System.ServiceModel.CallbackBehaviorAttribute>
