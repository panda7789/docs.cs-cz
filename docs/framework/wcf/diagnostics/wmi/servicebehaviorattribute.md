---
title: ServiceBehaviorAttribute
ms.date: 03/30/2017
ms.assetid: 5faa266f-587f-4e03-828d-1c7dd5acfe65
ms.openlocfilehash: b6221e93f10b87a368bd594932a8c36ae14df8f3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59206873"
---
# <a name="servicebehaviorattribute"></a><span data-ttu-id="30035-102">ServiceBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="30035-102">ServiceBehaviorAttribute</span></span>
<span data-ttu-id="30035-103">ServiceBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="30035-103">ServiceBehaviorAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30035-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="30035-104">Syntax</span></span>  
  
```csharp
class ServiceBehaviorAttribute : Behavior  
{  
  boolean AutomaticSessionShutdown;  
  string ConcurrencyMode;  
  string ConfigurationName;  
  boolean IgnoreExtensionDataObject;  
  boolean IncludeExceptionDetailInFaults;  
  string InstanceContextMode;  
  sint32 MaxItemsInObjectGraph;  
  string Name;  
  string Namespace;  
  boolean ReleaseServiceInstanceOnTransactionComplete;  
  boolean TransactionAutoCompleteOnSessionClose;  
  string TransactionIsolationLevel;  
  datetime TransactionTimeout;  
  boolean UseSynchronizationContext;  
  boolean ValidateMustUnderstand;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="30035-105">Metody</span><span class="sxs-lookup"><span data-stu-id="30035-105">Methods</span></span>  
 <span data-ttu-id="30035-106">Třídy ServiceBehaviorAttribute nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="30035-106">The ServiceBehaviorAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="30035-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="30035-107">Properties</span></span>  
 <span data-ttu-id="30035-108">Třídy ServiceBehaviorAttribute má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="30035-108">The ServiceBehaviorAttribute class has the following properties:</span></span>  
  
### <a name="automaticsessionshutdown"></a><span data-ttu-id="30035-109">AutomaticSessionShutdown</span><span class="sxs-lookup"><span data-stu-id="30035-109">AutomaticSessionShutdown</span></span>  
 <span data-ttu-id="30035-110">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="30035-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="30035-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="30035-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="30035-112">Označuje, zda automaticky ukončit relaci, když klient ukončí relaci výstupu.</span><span class="sxs-lookup"><span data-stu-id="30035-112">Indicates whether to automatically close a session when a client closes an output session.</span></span>  
  
### <a name="concurrencymode"></a><span data-ttu-id="30035-113">ConcurrencyMode</span><span class="sxs-lookup"><span data-stu-id="30035-113">ConcurrencyMode</span></span>  
 <span data-ttu-id="30035-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="30035-114">Data type: string</span></span>  
<span data-ttu-id="30035-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="30035-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="30035-116">Určuje, zda služba podporuje jedno vlákno, několik vláken nebo znovu zadaných volání.</span><span class="sxs-lookup"><span data-stu-id="30035-116">Indicates whether a service supports one thread, multiple threads, or reentrant calls.</span></span>  
  
### <a name="configurationname"></a><span data-ttu-id="30035-117">ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="30035-117">ConfigurationName</span></span>  
 <span data-ttu-id="30035-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="30035-118">Data type: string</span></span>  
  
 <span data-ttu-id="30035-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="30035-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="30035-120">Název konfigurace služby.</span><span class="sxs-lookup"><span data-stu-id="30035-120">The name of the service configuration.</span></span>  
  
### <a name="ignoreextensiondataobject"></a><span data-ttu-id="30035-121">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="30035-121">IgnoreExtensionDataObject</span></span>  
 <span data-ttu-id="30035-122">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="30035-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="30035-123">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="30035-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="30035-124">Určuje, zda mají data neznámé serializace přenosu.</span><span class="sxs-lookup"><span data-stu-id="30035-124">Specifies whether to send unknown serialization data onto the wire.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="30035-125">Třídu IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="30035-125">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="30035-126">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="30035-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="30035-127">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="30035-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="30035-128">Určuje, jestli se má být řízená informace výjimky zařazená do podrobností chyb SOAP vrácena klientům pro účely ladění.</span><span class="sxs-lookup"><span data-stu-id="30035-128">Specifies whether to include managed exception information in the detail of SOAP faults returned to the clients for debugging purposes.</span></span>  
  
### <a name="instancecontextmode"></a><span data-ttu-id="30035-129">InstanceContextMode</span><span class="sxs-lookup"><span data-stu-id="30035-129">InstanceContextMode</span></span>  
 <span data-ttu-id="30035-130">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="30035-130">Data type: string</span></span>  
  
 <span data-ttu-id="30035-131">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="30035-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="30035-132">Určuje, kdy je vytvořen nový objekt služby.</span><span class="sxs-lookup"><span data-stu-id="30035-132">Specifies when a new service object is created.</span></span>  
  
### <a name="maxitemsinobjectgraph"></a><span data-ttu-id="30035-133">MaxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="30035-133">MaxItemsInObjectGraph</span></span>  
 <span data-ttu-id="30035-134">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="30035-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="30035-135">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="30035-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="30035-136">Maximální počet položek povolených v serializovaném objektu.</span><span class="sxs-lookup"><span data-stu-id="30035-136">The maximum number of items allowed in a serialized object.</span></span>  
  
### <a name="name"></a><span data-ttu-id="30035-137">Name</span><span class="sxs-lookup"><span data-stu-id="30035-137">Name</span></span>  
 <span data-ttu-id="30035-138">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="30035-138">Data type: string</span></span>  
  
 <span data-ttu-id="30035-139">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="30035-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="30035-140">Atribut názvu služby ve WSDL.</span><span class="sxs-lookup"><span data-stu-id="30035-140">The name attribute of the service in WSDL.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="30035-141">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="30035-141">Namespace</span></span>  
 <span data-ttu-id="30035-142">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="30035-142">Data type: string</span></span>  
  
 <span data-ttu-id="30035-143">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="30035-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="30035-144">Cílový obor názvů služby ve WSDL.</span><span class="sxs-lookup"><span data-stu-id="30035-144">The target namespace of the service in WSDL.</span></span>  
  
### <a name="releaseserviceinstanceontransactioncomplete"></a><span data-ttu-id="30035-145">ReleaseServiceInstanceOnTransactionComplete</span><span class="sxs-lookup"><span data-stu-id="30035-145">ReleaseServiceInstanceOnTransactionComplete</span></span>  
 <span data-ttu-id="30035-146">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="30035-146">Data type: boolean</span></span>  
  
 <span data-ttu-id="30035-147">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="30035-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="30035-148">Určuje, zda je objekt služby vrácen, pokud je aktuální transakce dokončena.</span><span class="sxs-lookup"><span data-stu-id="30035-148">Specifies whether the service object is recycled when the current transaction completes.</span></span>  
  
### <a name="transactionautocompleteonsessionclose"></a><span data-ttu-id="30035-149">TransactionAutoCompleteOnSessionClose</span><span class="sxs-lookup"><span data-stu-id="30035-149">TransactionAutoCompleteOnSessionClose</span></span>  
 <span data-ttu-id="30035-150">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="30035-150">Data type: boolean</span></span>  
  
 <span data-ttu-id="30035-151">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="30035-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="30035-152">Určuje, zda jsou nevyřízené transakce dokončeny zavře aktuální relaci.</span><span class="sxs-lookup"><span data-stu-id="30035-152">Specifies whether pending transactions are completed when the current session closes.</span></span>  
  
### <a name="transactionisolationlevel"></a><span data-ttu-id="30035-153">Úroveň TransactionIsolationLevel</span><span class="sxs-lookup"><span data-stu-id="30035-153">TransactionIsolationLevel</span></span>  
 <span data-ttu-id="30035-154">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="30035-154">Data type: string</span></span>  
  
 <span data-ttu-id="30035-155">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="30035-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="30035-156">Určuje úroveň izolace transakce.</span><span class="sxs-lookup"><span data-stu-id="30035-156">Specifies the transaction isolation level.</span></span>  
  
### <a name="transactiontimeout"></a><span data-ttu-id="30035-157">Vlastnost TransactionTimeout</span><span class="sxs-lookup"><span data-stu-id="30035-157">TransactionTimeout</span></span>  
 <span data-ttu-id="30035-158">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="30035-158">Data type: datetime</span></span>  
  
 <span data-ttu-id="30035-159">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="30035-159">Access type: Read-only</span></span>  
  
 <span data-ttu-id="30035-160">Období, ve kterém musí být transakce dokončena.</span><span class="sxs-lookup"><span data-stu-id="30035-160">The period within which a transaction must complete.</span></span>  
  
### <a name="usesynchronizationcontext"></a><span data-ttu-id="30035-161">UseSynchronizationContext</span><span class="sxs-lookup"><span data-stu-id="30035-161">UseSynchronizationContext</span></span>  
 <span data-ttu-id="30035-162">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="30035-162">Data type: boolean</span></span>  
  
 <span data-ttu-id="30035-163">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="30035-163">Access type: Read-only</span></span>  
  
 <span data-ttu-id="30035-164">Určuje, jestli se má použít aktuální synchronizační kontext pro výběr provedení vlákna.</span><span class="sxs-lookup"><span data-stu-id="30035-164">Specifies whether to use the current synchronization context to choose the thread execution.</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="30035-165">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="30035-165">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="30035-166">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="30035-166">Data type: boolean</span></span>  
  
 <span data-ttu-id="30035-167">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="30035-167">Access type: Read-only</span></span>  
  
 <span data-ttu-id="30035-168">Určuje, zda systém nebo aplikace uplatňuje zpracování záhlaví SOAP MustUnderstand.</span><span class="sxs-lookup"><span data-stu-id="30035-168">Specifies whether the system or the application enforces SOAP MustUnderstand header processing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30035-169">Požadavky</span><span class="sxs-lookup"><span data-stu-id="30035-169">Requirements</span></span>  
  
|<span data-ttu-id="30035-170">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="30035-170">MOF</span></span>|<span data-ttu-id="30035-171">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="30035-171">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="30035-172">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="30035-172">Namespace</span></span>|<span data-ttu-id="30035-173">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="30035-173">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="30035-174">Viz také:</span><span class="sxs-lookup"><span data-stu-id="30035-174">See also</span></span>

- <xref:System.ServiceModel.ServiceBehaviorAttribute>
