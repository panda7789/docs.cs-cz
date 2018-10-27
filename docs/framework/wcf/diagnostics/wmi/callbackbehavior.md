---
title: CallbackBehavior
ms.date: 03/30/2017
ms.assetid: 42acd302-2b62-4849-a2d1-a03084343ecd
ms.openlocfilehash: 38a38a71db2927d187ccdd93e5e364b0d4955373
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2018
ms.locfileid: "49452609"
---
# <a name="callbackbehavior"></a><span data-ttu-id="81e79-102">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="81e79-102">CallbackBehavior</span></span>
<span data-ttu-id="81e79-103">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="81e79-103">CallbackBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81e79-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="81e79-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="81e79-105">Metody</span><span class="sxs-lookup"><span data-stu-id="81e79-105">Methods</span></span>  
 <span data-ttu-id="81e79-106">Třída CallbackBehavior nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="81e79-106">The CallbackBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="81e79-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="81e79-107">Properties</span></span>  
 <span data-ttu-id="81e79-108">Třída CallbackBehavior má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="81e79-108">The CallbackBehavior class has the following properties:</span></span>  
  
### <a name="automaticsessionshutdown"></a><span data-ttu-id="81e79-109">AutomaticSessionShutdown</span><span class="sxs-lookup"><span data-stu-id="81e79-109">AutomaticSessionShutdown</span></span>  
 <span data-ttu-id="81e79-110">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="81e79-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="81e79-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="81e79-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="81e79-112">V případě hodnoty true relace je automaticky uzavřena poté, co služba uzavře oboustrannou relaci.</span><span class="sxs-lookup"><span data-stu-id="81e79-112">When true, the session is automatically closed when a service closes a duplex session.</span></span>  
  
### <a name="concurrencymode"></a><span data-ttu-id="81e79-113">Režim ConcurrencyMode</span><span class="sxs-lookup"><span data-stu-id="81e79-113">ConcurrencyMode</span></span>  
 <span data-ttu-id="81e79-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="81e79-114">Data type: string</span></span>  
<span data-ttu-id="81e79-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="81e79-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="81e79-116">Určuje, zda služba podporuje jedno vlákno, několik vláken nebo znovu zadaných volání.</span><span class="sxs-lookup"><span data-stu-id="81e79-116">Specifies whether the service supports one thread, multiple threads, or reentrant calls.</span></span>  
  
### <a name="ignoreextensiondataobject"></a><span data-ttu-id="81e79-117">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="81e79-117">IgnoreExtensionDataObject</span></span>  
 <span data-ttu-id="81e79-118">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="81e79-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="81e79-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="81e79-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="81e79-120">Hodnota, která určuje, zda mají data neznámé serializace přenosu.</span><span class="sxs-lookup"><span data-stu-id="81e79-120">A value that specifies whether to send unknown serialization data onto the wire.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="81e79-121">Třídu IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="81e79-121">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="81e79-122">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="81e79-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="81e79-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="81e79-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="81e79-124">Při povolené, podrobnosti o výjimkách odvolání připojeny k chybám vrácených službě.</span><span class="sxs-lookup"><span data-stu-id="81e79-124">When enabled, details about exceptions on the callback are attached to the faults returned to the service.</span></span>  
  
### <a name="maxitemsinobjectgraph"></a><span data-ttu-id="81e79-125">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="81e79-125">MaxItemsInObjectGraph</span></span>  
 <span data-ttu-id="81e79-126">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="81e79-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="81e79-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="81e79-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="81e79-128">Maximální počet položek povolených v serializovaném objektu.</span><span class="sxs-lookup"><span data-stu-id="81e79-128">The maximum number of items allowed in a serialized object.</span></span>  
  
### <a name="usesynchronizationcontext"></a><span data-ttu-id="81e79-129">UseSynchronizationContext</span><span class="sxs-lookup"><span data-stu-id="81e79-129">UseSynchronizationContext</span></span>  
 <span data-ttu-id="81e79-130">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="81e79-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="81e79-131">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="81e79-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="81e79-132">Určuje, jestli se má použít aktuální synchronizační kontext pro výběr vlákna exekuce.</span><span class="sxs-lookup"><span data-stu-id="81e79-132">Specifies whether to use the current synchronization context to choose the thread of execution.</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="81e79-133">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="81e79-133">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="81e79-134">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="81e79-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="81e79-135">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="81e79-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="81e79-136">Určuje, zda systém nebo aplikace uplatňuje zpracování záhlaví SOAP MustUnderstand.</span><span class="sxs-lookup"><span data-stu-id="81e79-136">Specifies whether the system or the application enforces SOAP MustUnderstand header processing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81e79-137">Požadavky</span><span class="sxs-lookup"><span data-stu-id="81e79-137">Requirements</span></span>  
  
|<span data-ttu-id="81e79-138">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="81e79-138">MOF</span></span>|<span data-ttu-id="81e79-139">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="81e79-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="81e79-140">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="81e79-140">Namespace</span></span>|<span data-ttu-id="81e79-141">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="81e79-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="81e79-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="81e79-142">See Also</span></span>  
 <xref:System.ServiceModel.CallbackBehaviorAttribute>
