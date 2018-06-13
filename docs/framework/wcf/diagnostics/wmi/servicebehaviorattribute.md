---
title: ServiceBehaviorAttribute
ms.date: 03/30/2017
ms.assetid: 5faa266f-587f-4e03-828d-1c7dd5acfe65
ms.openlocfilehash: 514af4c6d9eaaf8929ca831e4e786c895d14c67d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33487196"
---
# <a name="servicebehaviorattribute"></a><span data-ttu-id="ba872-102">ServiceBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="ba872-102">ServiceBehaviorAttribute</span></span>
<span data-ttu-id="ba872-103">ServiceBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="ba872-103">ServiceBehaviorAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba872-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ba872-104">Syntax</span></span>  
  
```  
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
  
## <a name="methods"></a><span data-ttu-id="ba872-105">Metody</span><span class="sxs-lookup"><span data-stu-id="ba872-105">Methods</span></span>  
 <span data-ttu-id="ba872-106">Třída ServiceBehaviorAttribute nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="ba872-106">The ServiceBehaviorAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ba872-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="ba872-107">Properties</span></span>  
 <span data-ttu-id="ba872-108">Třída ServiceBehaviorAttribute má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="ba872-108">The ServiceBehaviorAttribute class has the following properties:</span></span>  
  
### <a name="automaticsessionshutdown"></a><span data-ttu-id="ba872-109">AutomaticSessionShutdown</span><span class="sxs-lookup"><span data-stu-id="ba872-109">AutomaticSessionShutdown</span></span>  
 <span data-ttu-id="ba872-110">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="ba872-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="ba872-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ba872-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ba872-112">Označuje, zda automaticky zavřete relaci, když klient ukončí relaci výstupu.</span><span class="sxs-lookup"><span data-stu-id="ba872-112">Indicates whether to automatically close a session when a client closes an output session.</span></span>  
  
### <a name="concurrencymode"></a><span data-ttu-id="ba872-113">Režim ConcurrencyMode</span><span class="sxs-lookup"><span data-stu-id="ba872-113">ConcurrencyMode</span></span>  
 <span data-ttu-id="ba872-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="ba872-114">Data type: string</span></span>  
<span data-ttu-id="ba872-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ba872-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ba872-116">Určuje, zda služba podporuje jedno vlákno, více vláken nebo znovu zadaná volání.</span><span class="sxs-lookup"><span data-stu-id="ba872-116">Indicates whether a service supports one thread, multiple threads, or reentrant calls.</span></span>  
  
### <a name="configurationname"></a><span data-ttu-id="ba872-117">ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="ba872-117">ConfigurationName</span></span>  
 <span data-ttu-id="ba872-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="ba872-118">Data type: string</span></span>  
  
 <span data-ttu-id="ba872-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ba872-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ba872-120">Název konfigurace služby.</span><span class="sxs-lookup"><span data-stu-id="ba872-120">The name of the service configuration.</span></span>  
  
### <a name="ignoreextensiondataobject"></a><span data-ttu-id="ba872-121">IgnoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="ba872-121">IgnoreExtensionDataObject</span></span>  
 <span data-ttu-id="ba872-122">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="ba872-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="ba872-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ba872-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ba872-124">Určuje, zda chcete odesílat data neznámé serializace drátové síti.</span><span class="sxs-lookup"><span data-stu-id="ba872-124">Specifies whether to send unknown serialization data onto the wire.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="ba872-125">Třídu IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="ba872-125">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="ba872-126">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="ba872-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="ba872-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ba872-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ba872-128">Určuje, zda mají být zahrnuty informace o spravovaných výjimce podrobností chyb SOAP vrácených klientům pro účely ladění.</span><span class="sxs-lookup"><span data-stu-id="ba872-128">Specifies whether to include managed exception information in the detail of SOAP faults returned to the clients for debugging purposes.</span></span>  
  
### <a name="instancecontextmode"></a><span data-ttu-id="ba872-129">Režim InstanceContextMode</span><span class="sxs-lookup"><span data-stu-id="ba872-129">InstanceContextMode</span></span>  
 <span data-ttu-id="ba872-130">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="ba872-130">Data type: string</span></span>  
  
 <span data-ttu-id="ba872-131">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ba872-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ba872-132">Určuje, kdy vytvořit nový objekt služby.</span><span class="sxs-lookup"><span data-stu-id="ba872-132">Specifies when a new service object is created.</span></span>  
  
### <a name="maxitemsinobjectgraph"></a><span data-ttu-id="ba872-133">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="ba872-133">MaxItemsInObjectGraph</span></span>  
 <span data-ttu-id="ba872-134">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="ba872-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="ba872-135">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ba872-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ba872-136">Maximální počet položek v serializovaný objekt povoleny.</span><span class="sxs-lookup"><span data-stu-id="ba872-136">The maximum number of items allowed in a serialized object.</span></span>  
  
### <a name="name"></a><span data-ttu-id="ba872-137">Název</span><span class="sxs-lookup"><span data-stu-id="ba872-137">Name</span></span>  
 <span data-ttu-id="ba872-138">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="ba872-138">Data type: string</span></span>  
  
 <span data-ttu-id="ba872-139">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ba872-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ba872-140">Atribut názvu služby v jazyce WSDL.</span><span class="sxs-lookup"><span data-stu-id="ba872-140">The name attribute of the service in WSDL.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="ba872-141">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="ba872-141">Namespace</span></span>  
 <span data-ttu-id="ba872-142">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="ba872-142">Data type: string</span></span>  
  
 <span data-ttu-id="ba872-143">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ba872-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ba872-144">Cílový obor názvů služby v jazyce WSDL.</span><span class="sxs-lookup"><span data-stu-id="ba872-144">The target namespace of the service in WSDL.</span></span>  
  
### <a name="releaseserviceinstanceontransactioncomplete"></a><span data-ttu-id="ba872-145">ReleaseServiceInstanceOnTransactionComplete</span><span class="sxs-lookup"><span data-stu-id="ba872-145">ReleaseServiceInstanceOnTransactionComplete</span></span>  
 <span data-ttu-id="ba872-146">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="ba872-146">Data type: boolean</span></span>  
  
 <span data-ttu-id="ba872-147">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ba872-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ba872-148">Určuje, jestli je objekt služby recykluje po dokončení aktuální transakci.</span><span class="sxs-lookup"><span data-stu-id="ba872-148">Specifies whether the service object is recycled when the current transaction completes.</span></span>  
  
### <a name="transactionautocompleteonsessionclose"></a><span data-ttu-id="ba872-149">TransactionAutoCompleteOnSessionClose</span><span class="sxs-lookup"><span data-stu-id="ba872-149">TransactionAutoCompleteOnSessionClose</span></span>  
 <span data-ttu-id="ba872-150">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="ba872-150">Data type: boolean</span></span>  
  
 <span data-ttu-id="ba872-151">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ba872-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ba872-152">Určuje, zda jsou nevyřízené transakce dokončeny zavře aktuální relaci.</span><span class="sxs-lookup"><span data-stu-id="ba872-152">Specifies whether pending transactions are completed when the current session closes.</span></span>  
  
### <a name="transactionisolationlevel"></a><span data-ttu-id="ba872-153">TransactionIsolationLevel</span><span class="sxs-lookup"><span data-stu-id="ba872-153">TransactionIsolationLevel</span></span>  
 <span data-ttu-id="ba872-154">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="ba872-154">Data type: string</span></span>  
  
 <span data-ttu-id="ba872-155">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ba872-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ba872-156">Určuje úroveň izolace transakce.</span><span class="sxs-lookup"><span data-stu-id="ba872-156">Specifies the transaction isolation level.</span></span>  
  
### <a name="transactiontimeout"></a><span data-ttu-id="ba872-157">Vlastnost TransactionTimeout</span><span class="sxs-lookup"><span data-stu-id="ba872-157">TransactionTimeout</span></span>  
 <span data-ttu-id="ba872-158">Datový typ: data a času</span><span class="sxs-lookup"><span data-stu-id="ba872-158">Data type: datetime</span></span>  
  
 <span data-ttu-id="ba872-159">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ba872-159">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ba872-160">Období, ve kterém musíte dokončit transakci.</span><span class="sxs-lookup"><span data-stu-id="ba872-160">The period within which a transaction must complete.</span></span>  
  
### <a name="usesynchronizationcontext"></a><span data-ttu-id="ba872-161">UseSynchronizationContext</span><span class="sxs-lookup"><span data-stu-id="ba872-161">UseSynchronizationContext</span></span>  
 <span data-ttu-id="ba872-162">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="ba872-162">Data type: boolean</span></span>  
  
 <span data-ttu-id="ba872-163">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ba872-163">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ba872-164">Určuje, zda chcete použít aktuální kontext synchronizace zvolit provádění vlákna.</span><span class="sxs-lookup"><span data-stu-id="ba872-164">Specifies whether to use the current synchronization context to choose the thread execution.</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="ba872-165">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="ba872-165">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="ba872-166">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="ba872-166">Data type: boolean</span></span>  
  
 <span data-ttu-id="ba872-167">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ba872-167">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ba872-168">Určuje, zda je systém nebo aplikace vynucuje zpracování záhlaví SOAP MustUnderstand.</span><span class="sxs-lookup"><span data-stu-id="ba872-168">Specifies whether the system or the application enforces SOAP MustUnderstand header processing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba872-169">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ba872-169">Requirements</span></span>  
  
|<span data-ttu-id="ba872-170">MOF</span><span class="sxs-lookup"><span data-stu-id="ba872-170">MOF</span></span>|<span data-ttu-id="ba872-171">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="ba872-171">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ba872-172">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="ba872-172">Namespace</span></span>|<span data-ttu-id="ba872-173">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ba872-173">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ba872-174">Viz také</span><span class="sxs-lookup"><span data-stu-id="ba872-174">See Also</span></span>  
 <xref:System.ServiceModel.ServiceBehaviorAttribute>
