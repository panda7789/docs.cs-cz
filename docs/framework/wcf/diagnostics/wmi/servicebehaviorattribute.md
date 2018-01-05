---
title: ServiceBehaviorAttribute
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5faa266f-587f-4e03-828d-1c7dd5acfe65
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7d6b0620e9cb2575bcfe9cd6f01b5d87669df69b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="servicebehaviorattribute"></a><span data-ttu-id="2e3c9-102">ServiceBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="2e3c9-102">ServiceBehaviorAttribute</span></span>
<span data-ttu-id="2e3c9-103">ServiceBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="2e3c9-103">ServiceBehaviorAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e3c9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2e3c9-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="2e3c9-105">Metody</span><span class="sxs-lookup"><span data-stu-id="2e3c9-105">Methods</span></span>  
 <span data-ttu-id="2e3c9-106">Třída ServiceBehaviorAttribute nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="2e3c9-106">The ServiceBehaviorAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="2e3c9-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="2e3c9-107">Properties</span></span>  
 <span data-ttu-id="2e3c9-108">Třída ServiceBehaviorAttribute má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="2e3c9-108">The ServiceBehaviorAttribute class has the following properties:</span></span>  
  
### <a name="automaticsessionshutdown"></a><span data-ttu-id="2e3c9-109">AutomaticSessionShutdown</span><span class="sxs-lookup"><span data-stu-id="2e3c9-109">AutomaticSessionShutdown</span></span>  
 <span data-ttu-id="2e3c9-110">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="2e3c9-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="2e3c9-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="2e3c9-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2e3c9-112">Označuje, zda automaticky zavřete relaci, když klient ukončí relaci výstupu.</span><span class="sxs-lookup"><span data-stu-id="2e3c9-112">Indicates whether to automatically close a session when a client closes an output session.</span></span>  
  
### <a name="concurrencymode"></a><span data-ttu-id="2e3c9-113">Režim ConcurrencyMode</span><span class="sxs-lookup"><span data-stu-id="2e3c9-113">ConcurrencyMode</span></span>  
 <span data-ttu-id="2e3c9-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="2e3c9-114">Data type: string</span></span>  
<span data-ttu-id="2e3c9-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="2e3c9-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2e3c9-116">Určuje, zda služba podporuje jedno vlákno, více vláken nebo znovu zadaná volání.</span><span class="sxs-lookup"><span data-stu-id="2e3c9-116">Indicates whether a service supports one thread, multiple threads, or reentrant calls.</span></span>  
  
### <a name="configurationname"></a><span data-ttu-id="2e3c9-117">ConfigurationName</span><span class="sxs-lookup"><span data-stu-id="2e3c9-117">ConfigurationName</span></span>  
 <span data-ttu-id="2e3c9-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="2e3c9-118">Data type: string</span></span>  
  
 <span data-ttu-id="2e3c9-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="2e3c9-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2e3c9-120">Název konfigurace služby.</span><span class="sxs-lookup"><span data-stu-id="2e3c9-120">The name of the service configuration.</span></span>  
  
### <a name="ignoreextensiondataobject"></a><span data-ttu-id="2e3c9-121">ignoreExtensionDataObject</span><span class="sxs-lookup"><span data-stu-id="2e3c9-121">IgnoreExtensionDataObject</span></span>  
 <span data-ttu-id="2e3c9-122">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="2e3c9-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="2e3c9-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="2e3c9-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2e3c9-124">Určuje, zda chcete odesílat data neznámé serializace drátové síti.</span><span class="sxs-lookup"><span data-stu-id="2e3c9-124">Specifies whether to send unknown serialization data onto the wire.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="2e3c9-125">Třídu IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="2e3c9-125">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="2e3c9-126">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="2e3c9-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="2e3c9-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="2e3c9-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2e3c9-128">Určuje, zda mají být zahrnuty informace o spravovaných výjimce podrobností chyb SOAP vrácených klientům pro účely ladění.</span><span class="sxs-lookup"><span data-stu-id="2e3c9-128">Specifies whether to include managed exception information in the detail of SOAP faults returned to the clients for debugging purposes.</span></span>  
  
### <a name="instancecontextmode"></a><span data-ttu-id="2e3c9-129">Režim InstanceContextMode</span><span class="sxs-lookup"><span data-stu-id="2e3c9-129">InstanceContextMode</span></span>  
 <span data-ttu-id="2e3c9-130">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="2e3c9-130">Data type: string</span></span>  
  
 <span data-ttu-id="2e3c9-131">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="2e3c9-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2e3c9-132">Určuje, kdy vytvořit nový objekt služby.</span><span class="sxs-lookup"><span data-stu-id="2e3c9-132">Specifies when a new service object is created.</span></span>  
  
### <a name="maxitemsinobjectgraph"></a><span data-ttu-id="2e3c9-133">maxItemsInObjectGraph</span><span class="sxs-lookup"><span data-stu-id="2e3c9-133">MaxItemsInObjectGraph</span></span>  
 <span data-ttu-id="2e3c9-134">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="2e3c9-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="2e3c9-135">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="2e3c9-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2e3c9-136">Maximální počet položek v serializovaný objekt povoleny.</span><span class="sxs-lookup"><span data-stu-id="2e3c9-136">The maximum number of items allowed in a serialized object.</span></span>  
  
### <a name="name"></a><span data-ttu-id="2e3c9-137">Název</span><span class="sxs-lookup"><span data-stu-id="2e3c9-137">Name</span></span>  
 <span data-ttu-id="2e3c9-138">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="2e3c9-138">Data type: string</span></span>  
  
 <span data-ttu-id="2e3c9-139">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="2e3c9-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2e3c9-140">Atribut názvu služby v jazyce WSDL.</span><span class="sxs-lookup"><span data-stu-id="2e3c9-140">The name attribute of the service in WSDL.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="2e3c9-141">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="2e3c9-141">Namespace</span></span>  
 <span data-ttu-id="2e3c9-142">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="2e3c9-142">Data type: string</span></span>  
  
 <span data-ttu-id="2e3c9-143">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="2e3c9-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2e3c9-144">Cílový obor názvů služby v jazyce WSDL.</span><span class="sxs-lookup"><span data-stu-id="2e3c9-144">The target namespace of the service in WSDL.</span></span>  
  
### <a name="releaseserviceinstanceontransactioncomplete"></a><span data-ttu-id="2e3c9-145">ReleaseServiceInstanceOnTransactionComplete</span><span class="sxs-lookup"><span data-stu-id="2e3c9-145">ReleaseServiceInstanceOnTransactionComplete</span></span>  
 <span data-ttu-id="2e3c9-146">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="2e3c9-146">Data type: boolean</span></span>  
  
 <span data-ttu-id="2e3c9-147">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="2e3c9-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2e3c9-148">Určuje, jestli je objekt služby recykluje po dokončení aktuální transakci.</span><span class="sxs-lookup"><span data-stu-id="2e3c9-148">Specifies whether the service object is recycled when the current transaction completes.</span></span>  
  
### <a name="transactionautocompleteonsessionclose"></a><span data-ttu-id="2e3c9-149">TransactionAutoCompleteOnSessionClose</span><span class="sxs-lookup"><span data-stu-id="2e3c9-149">TransactionAutoCompleteOnSessionClose</span></span>  
 <span data-ttu-id="2e3c9-150">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="2e3c9-150">Data type: boolean</span></span>  
  
 <span data-ttu-id="2e3c9-151">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="2e3c9-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2e3c9-152">Určuje, zda jsou nevyřízené transakce dokončeny zavře aktuální relaci.</span><span class="sxs-lookup"><span data-stu-id="2e3c9-152">Specifies whether pending transactions are completed when the current session closes.</span></span>  
  
### <a name="transactionisolationlevel"></a><span data-ttu-id="2e3c9-153">TransactionIsolationLevel</span><span class="sxs-lookup"><span data-stu-id="2e3c9-153">TransactionIsolationLevel</span></span>  
 <span data-ttu-id="2e3c9-154">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="2e3c9-154">Data type: string</span></span>  
  
 <span data-ttu-id="2e3c9-155">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="2e3c9-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2e3c9-156">Určuje úroveň izolace transakce.</span><span class="sxs-lookup"><span data-stu-id="2e3c9-156">Specifies the transaction isolation level.</span></span>  
  
### <a name="transactiontimeout"></a><span data-ttu-id="2e3c9-157">Vlastnost TransactionTimeout</span><span class="sxs-lookup"><span data-stu-id="2e3c9-157">TransactionTimeout</span></span>  
 <span data-ttu-id="2e3c9-158">Datový typ: data a času</span><span class="sxs-lookup"><span data-stu-id="2e3c9-158">Data type: datetime</span></span>  
  
 <span data-ttu-id="2e3c9-159">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="2e3c9-159">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2e3c9-160">Období, ve kterém musíte dokončit transakci.</span><span class="sxs-lookup"><span data-stu-id="2e3c9-160">The period within which a transaction must complete.</span></span>  
  
### <a name="usesynchronizationcontext"></a><span data-ttu-id="2e3c9-161">UseSynchronizationContext</span><span class="sxs-lookup"><span data-stu-id="2e3c9-161">UseSynchronizationContext</span></span>  
 <span data-ttu-id="2e3c9-162">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="2e3c9-162">Data type: boolean</span></span>  
  
 <span data-ttu-id="2e3c9-163">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="2e3c9-163">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2e3c9-164">Určuje, zda chcete použít aktuální kontext synchronizace zvolit provádění vlákna.</span><span class="sxs-lookup"><span data-stu-id="2e3c9-164">Specifies whether to use the current synchronization context to choose the thread execution.</span></span>  
  
### <a name="validatemustunderstand"></a><span data-ttu-id="2e3c9-165">ValidateMustUnderstand</span><span class="sxs-lookup"><span data-stu-id="2e3c9-165">ValidateMustUnderstand</span></span>  
 <span data-ttu-id="2e3c9-166">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="2e3c9-166">Data type: boolean</span></span>  
  
 <span data-ttu-id="2e3c9-167">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="2e3c9-167">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2e3c9-168">Určuje, zda je systém nebo aplikace vynucuje zpracování záhlaví SOAP MustUnderstand.</span><span class="sxs-lookup"><span data-stu-id="2e3c9-168">Specifies whether the system or the application enforces SOAP MustUnderstand header processing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e3c9-169">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2e3c9-169">Requirements</span></span>  
  
|<span data-ttu-id="2e3c9-170">MOF</span><span class="sxs-lookup"><span data-stu-id="2e3c9-170">MOF</span></span>|<span data-ttu-id="2e3c9-171">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="2e3c9-171">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="2e3c9-172">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="2e3c9-172">Namespace</span></span>|<span data-ttu-id="2e3c9-173">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="2e3c9-173">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2e3c9-174">Viz také</span><span class="sxs-lookup"><span data-stu-id="2e3c9-174">See Also</span></span>  
 <xref:System.ServiceModel.ServiceBehaviorAttribute>
