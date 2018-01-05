---
title: MsmqBindingElementBase
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 210d41ab-a2a4-4d7a-afd2-0916c08a4015
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 10e476931ef07ec694dff200e64ce2ded74c8dfb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="msmqbindingelementbase"></a><span data-ttu-id="37113-102">MsmqBindingElementBase</span><span class="sxs-lookup"><span data-stu-id="37113-102">MsmqBindingElementBase</span></span>
<span data-ttu-id="37113-103">MsmqBindingElementBase</span><span class="sxs-lookup"><span data-stu-id="37113-103">MsmqBindingElementBase</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37113-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="37113-104">Syntax</span></span>  
  
```  
class MsmqBindingElementBase : TransportBindingElement  
{  
  string CustomDeadLetterQueue;  
  string DeadLetterQueue;  
  boolean Durable;  
  boolean ExactlyOnce;  
  sint32 MaxRetryCycles;  
  string ReceiveErrorHandling;  
  sint32 ReceiveRetryCount;  
  datetime RetryCycleDelay;  
  datetime TimeToLive;  
  boolean UseMsmqTracing;  
  boolean UseSourceJournal;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="37113-105">Metody</span><span class="sxs-lookup"><span data-stu-id="37113-105">Methods</span></span>  
 <span data-ttu-id="37113-106">Třída MsmqBindingElementBase nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="37113-106">The MsmqBindingElementBase class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="37113-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="37113-107">Properties</span></span>  
 <span data-ttu-id="37113-108">Třída MsmqBindingElementBase má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="37113-108">The MsmqBindingElementBase class has the following properties:</span></span>  
  
### <a name="customdeadletterqueue"></a><span data-ttu-id="37113-109">customDeadLetterQueue</span><span class="sxs-lookup"><span data-stu-id="37113-109">CustomDeadLetterQueue</span></span>  
 <span data-ttu-id="37113-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="37113-110">Data type: string</span></span>  
  
 <span data-ttu-id="37113-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="37113-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="37113-112">Identifikátor URI, který obsahuje umístění fronty nedoručených zpráv pro každou aplikaci, kde jsou umístěny zprávy, jejichž platnost vypršela nebo které selhaly přenos nebo doručení.</span><span class="sxs-lookup"><span data-stu-id="37113-112">A URI that contains the location of the dead letter queue for each application, where messages that have expired or that have failed transfer or delivery are placed.</span></span>  
  
### <a name="deadletterqueue"></a><span data-ttu-id="37113-113">deadLetterQueue</span><span class="sxs-lookup"><span data-stu-id="37113-113">DeadLetterQueue</span></span>  
 <span data-ttu-id="37113-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="37113-114">Data type: string</span></span>  
  
 <span data-ttu-id="37113-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="37113-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="37113-116">Hodnota výčtu, která určuje typ fronty nedoručených zpráv používat.</span><span class="sxs-lookup"><span data-stu-id="37113-116">An enumeration value that indicates the type of dead letter queue to use.</span></span>  
  
### <a name="durable"></a><span data-ttu-id="37113-117">trvanlivý</span><span class="sxs-lookup"><span data-stu-id="37113-117">Durable</span></span>  
 <span data-ttu-id="37113-118">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="37113-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="37113-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="37113-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="37113-120">Hodnota, která určuje, zda jsou zprávy zpracovávané touto vazbou trvalé nebo přechodné.</span><span class="sxs-lookup"><span data-stu-id="37113-120">A value that indicates whether the messages processed by this binding are durable or volatile.</span></span>  
  
### <a name="exactlyonce"></a><span data-ttu-id="37113-121">exactlyOnce</span><span class="sxs-lookup"><span data-stu-id="37113-121">ExactlyOnce</span></span>  
 <span data-ttu-id="37113-122">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="37113-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="37113-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="37113-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="37113-124">Logická hodnota, která určuje, zda jsou zprávy zpracovávané touto vazbou obdrženy pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="37113-124">A Boolean value that indicates whether messages processed by this binding are received exactly once.</span></span>  
  
### <a name="maxretrycycles"></a><span data-ttu-id="37113-125">maxRetryCycles</span><span class="sxs-lookup"><span data-stu-id="37113-125">MaxRetryCycles</span></span>  
 <span data-ttu-id="37113-126">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="37113-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="37113-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="37113-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="37113-128">Maximální počet cyklů opakování pokusu o doručení zprávy do přijímající aplikace.</span><span class="sxs-lookup"><span data-stu-id="37113-128">The maximum number of retry cycles to attempt delivery of messages to the receiving application.</span></span>  
  
### <a name="receiveerrorhandling"></a><span data-ttu-id="37113-129">receiveErrorHandling</span><span class="sxs-lookup"><span data-stu-id="37113-129">ReceiveErrorHandling</span></span>  
 <span data-ttu-id="37113-130">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="37113-130">Data type: string</span></span>  
  
 <span data-ttu-id="37113-131">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="37113-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="37113-132">Nastavení pro zpracování poškozených zpráv.</span><span class="sxs-lookup"><span data-stu-id="37113-132">The settings for poison message handling.</span></span>  
  
### <a name="receiveretrycount"></a><span data-ttu-id="37113-133">receiveRetryCount</span><span class="sxs-lookup"><span data-stu-id="37113-133">ReceiveRetryCount</span></span>  
 <span data-ttu-id="37113-134">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="37113-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="37113-135">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="37113-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="37113-136">Maximální počet okamžitou opakování pokusů na zprávu, která je pro čtení z fronty aplikace.</span><span class="sxs-lookup"><span data-stu-id="37113-136">The maximum number of immediate retry attempts on a message that is read from the application queue.</span></span>  
  
### <a name="retrycycledelay"></a><span data-ttu-id="37113-137">retryCycleDelay</span><span class="sxs-lookup"><span data-stu-id="37113-137">RetryCycleDelay</span></span>  
 <span data-ttu-id="37113-138">Datový typ: data a času</span><span class="sxs-lookup"><span data-stu-id="37113-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="37113-139">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="37113-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="37113-140">Hodnotu, která určuje prodlevu mezi opakování cyklů při pokusu o doručení zprávy, která nelze doručit okamžitě.</span><span class="sxs-lookup"><span data-stu-id="37113-140">A value that indicates the time delay between retry cycles when attempting to deliver a message that could not be delivered immediately.</span></span>  
  
### <a name="timetolive"></a><span data-ttu-id="37113-141">TimeToLive</span><span class="sxs-lookup"><span data-stu-id="37113-141">TimeToLive</span></span>  
 <span data-ttu-id="37113-142">Datový typ: data a času</span><span class="sxs-lookup"><span data-stu-id="37113-142">Data type: datetime</span></span>  
  
 <span data-ttu-id="37113-143">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="37113-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="37113-144">Interval času, která určuje, jak dlouho zprávy zpracovávané touto vazbou může být ve frontě před vypršením jejich platnosti.</span><span class="sxs-lookup"><span data-stu-id="37113-144">The interval of time that indicates how long the messages processed by this binding can be in the queue before they expire.</span></span>  
  
### <a name="usemsmqtracing"></a><span data-ttu-id="37113-145">useMsmqTracing</span><span class="sxs-lookup"><span data-stu-id="37113-145">UseMsmqTracing</span></span>  
 <span data-ttu-id="37113-146">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="37113-146">Data type: boolean</span></span>  
  
 <span data-ttu-id="37113-147">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="37113-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="37113-148">Logická hodnota, která označuje, zda zprávy zpracovávané touto vazbou má trasovat.</span><span class="sxs-lookup"><span data-stu-id="37113-148">A Boolean value that indicates whether messages processed by this binding should be traced.</span></span>  
  
### <a name="usesourcejournal"></a><span data-ttu-id="37113-149">useSourceJournal</span><span class="sxs-lookup"><span data-stu-id="37113-149">UseSourceJournal</span></span>  
 <span data-ttu-id="37113-150">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="37113-150">Data type: boolean</span></span>  
  
 <span data-ttu-id="37113-151">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="37113-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="37113-152">Logická hodnota, která určuje, zda by měly být uložené kopie zprávy zpracovávané touto vazbou ve frontě deníku zdroje.</span><span class="sxs-lookup"><span data-stu-id="37113-152">A Boolean value that indicates whether copies of messages processed by this binding should be stored in the source journal queue.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37113-153">Požadavky</span><span class="sxs-lookup"><span data-stu-id="37113-153">Requirements</span></span>  
  
|<span data-ttu-id="37113-154">MOF</span><span class="sxs-lookup"><span data-stu-id="37113-154">MOF</span></span>|<span data-ttu-id="37113-155">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="37113-155">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="37113-156">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="37113-156">Namespace</span></span>|<span data-ttu-id="37113-157">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="37113-157">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="37113-158">Viz také</span><span class="sxs-lookup"><span data-stu-id="37113-158">See Also</span></span>  
 <xref:System.ServiceModel.NetMsmqBinding>  
 <xref:System.ServiceModel.MsmqBindingBase>
