---
title: CallbackBehavior
ms.date: 03/30/2017
ms.assetid: 42acd302-2b62-4849-a2d1-a03084343ecd
ms.openlocfilehash: 2755ac4f365536366b41e743110ce494063a5ecc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486935"
---
# <a name="callbackbehavior"></a><span data-ttu-id="56f59-102">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="56f59-102">CallbackBehavior</span></span>
<span data-ttu-id="56f59-103">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="56f59-103">CallbackBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56f59-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="56f59-104">Syntax</span></span>  
  
```  
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
  
## <a name="methods"></a><span data-ttu-id="56f59-105">Metody</span><span class="sxs-lookup"><span data-stu-id="56f59-105">Methods</span></span>  
 <span data-ttu-id="56f59-106">Třída CallbackBehavior nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="56f59-106">The CallbackBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="56f59-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="56f59-107">Properties</span></span>  
 <span data-ttu-id="56f59-108">Třída CallbackBehavior má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="56f59-108">The CallbackBehavior class has the following properties:</span></span>  
  
### <a name="automaticsessionshutdown"></a><span data-ttu-id="56f59-109">AutomaticSessionShutdown</span><span class="sxs-lookup"><span data-stu-id="56f59-109">AutomaticSessionShutdown</span></span>  
 <span data-ttu-id="56f59-110">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="56f59-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="56f59-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="56f59-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="56f59-112">V případě hodnoty true relace se automaticky zavře po ukončení služby duplexní relace.</span><span class="sxs-lookup"><span data-stu-id="56f59-112">When true, the session is automatically closed when a service closes a duplex session.</span></span>  
  
### <a name="concurrencymode"></a><span data-ttu-id="56f59-113">Režim ConcurrencyMode</span><span class="sxs-lookup"><span data-stu-id="56f59-113">ConcurrencyMode</span></span>  
 <span data-ttu-id="56f59-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="56f59-114">Data type: string</span></span>  
<span data-ttu-id="56f59-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="56f59-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="56f59-116">Určuje, jestli služba podporuje jedno vlákno, více vláken nebo znovu zadaná volání.</span><span class="sxs-lookup"><span data-stu-id="56f59-116">Specifies whether the service supports one thread, multiple threads, or reentrant calls.</span></span>  
  
### <a name="ignoreextensiondataobject"></a><span data-ttu-id="56f59-117">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="56f59-117">IgnoreExtensionDataObject</span></span>  
 <span data-ttu-id="56f59-118">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="56f59-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="56f59-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="56f59-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="56f59-120">Hodnota, která určuje, zda chcete odesílat data neznámé serializace drátové síti.</span><span class="sxs-lookup"><span data-stu-id="56f59-120">A value that specifies whether to send unknown serialization data onto the wire.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="56f59-121">Třídu IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="56f59-121">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="56f59-122">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="56f59-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="56f59-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="56f59-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="56f59-124">Když je povolené, podrobnosti o výjimkách odvolání jsou připojené k chybám vrácených ke službě.</span><span class="sxs-lookup"><span data-stu-id="56f59-124">When enabled, details about exceptions on the callback are attached to the faults returned to the service.</span></span>  
  
### <a name="maxitemsinobjectgraph"></a><span data-ttu-id="56f59-125">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="56f59-125">MaxItemsInObjectGraph</span></span>  
 <span data-ttu-id="56f59-126">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="56f59-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="56f59-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="56f59-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="56f59-128">Maximální počet položek v serializovaný objekt povoleny.</span><span class="sxs-lookup"><span data-stu-id="56f59-128">The maximum number of items allowed in a serialized object.</span></span>  
  
### <a name="usesynchronizationcontext"></a><span data-ttu-id="56f59-129">UseSynchronizationContext</span><span class="sxs-lookup"><span data-stu-id="56f59-129">UseSynchronizationContext</span></span>  
 <span data-ttu-id="56f59-130">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="56f59-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="56f59-131">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="56f59-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="56f59-132">Určuje, zda chcete použít aktuální kontext synchronizace pro vybrání procesu spuštění.</span><span class="sxs-lookup"><span data-stu-id="56f59-132">Specifies whether to use the current synchronization context to choose the thread of execution.</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="56f59-133">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="56f59-133">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="56f59-134">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="56f59-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="56f59-135">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="56f59-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="56f59-136">Určuje, zda je systém nebo aplikace vynucuje zpracování záhlaví SOAP MustUnderstand.</span><span class="sxs-lookup"><span data-stu-id="56f59-136">Specifies whether the system or the application enforces SOAP MustUnderstand header processing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56f59-137">Požadavky</span><span class="sxs-lookup"><span data-stu-id="56f59-137">Requirements</span></span>  
  
|<span data-ttu-id="56f59-138">MOF</span><span class="sxs-lookup"><span data-stu-id="56f59-138">MOF</span></span>|<span data-ttu-id="56f59-139">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="56f59-139">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="56f59-140">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="56f59-140">Namespace</span></span>|<span data-ttu-id="56f59-141">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="56f59-141">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="56f59-142">Viz také</span><span class="sxs-lookup"><span data-stu-id="56f59-142">See Also</span></span>  
 <xref:System.ServiceModel.CallbackBehaviorAttribute>
