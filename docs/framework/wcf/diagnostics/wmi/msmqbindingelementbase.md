---
title: MsmqBindingElementBase
ms.date: 03/30/2017
ms.assetid: 210d41ab-a2a4-4d7a-afd2-0916c08a4015
ms.openlocfilehash: a0e2ac250da3837b41134d3a04a21579a2fe923a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54569034"
---
# <a name="msmqbindingelementbase"></a><span data-ttu-id="f2dda-102">MsmqBindingElementBase</span><span class="sxs-lookup"><span data-stu-id="f2dda-102">MsmqBindingElementBase</span></span>
<span data-ttu-id="f2dda-103">MsmqBindingElementBase</span><span class="sxs-lookup"><span data-stu-id="f2dda-103">MsmqBindingElementBase</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2dda-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2dda-104">Syntax</span></span>  
  
```csharp  
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
  
## <a name="methods"></a><span data-ttu-id="f2dda-105">Metody</span><span class="sxs-lookup"><span data-stu-id="f2dda-105">Methods</span></span>  
 <span data-ttu-id="f2dda-106">Třída MsmqBindingElementBase nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="f2dda-106">The MsmqBindingElementBase class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f2dda-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="f2dda-107">Properties</span></span>  
 <span data-ttu-id="f2dda-108">Třída MsmqBindingElementBase má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="f2dda-108">The MsmqBindingElementBase class has the following properties:</span></span>  
  
### <a name="customdeadletterqueue"></a><span data-ttu-id="f2dda-109">CustomDeadLetterQueue</span><span class="sxs-lookup"><span data-stu-id="f2dda-109">CustomDeadLetterQueue</span></span>  
 <span data-ttu-id="f2dda-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="f2dda-110">Data type: string</span></span>  
  
 <span data-ttu-id="f2dda-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f2dda-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f2dda-112">Identifikátor URI, který obsahuje umístění fronty nedoručených zpráv pro každou aplikaci, kde jsou umístěny zprávy, jejichž platnost vypršela nebo které selhaly, přenos nebo doručení.</span><span class="sxs-lookup"><span data-stu-id="f2dda-112">A URI that contains the location of the dead letter queue for each application, where messages that have expired or that have failed transfer or delivery are placed.</span></span>  
  
### <a name="deadletterqueue"></a><span data-ttu-id="f2dda-113">DeadLetterQueue</span><span class="sxs-lookup"><span data-stu-id="f2dda-113">DeadLetterQueue</span></span>  
 <span data-ttu-id="f2dda-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="f2dda-114">Data type: string</span></span>  
  
 <span data-ttu-id="f2dda-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f2dda-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f2dda-116">Hodnota výčtu, která určuje typ fronty nepoužívaných dopisů používat.</span><span class="sxs-lookup"><span data-stu-id="f2dda-116">An enumeration value that indicates the type of dead letter queue to use.</span></span>  
  
### <a name="durable"></a><span data-ttu-id="f2dda-117">trvalý</span><span class="sxs-lookup"><span data-stu-id="f2dda-117">Durable</span></span>  
 <span data-ttu-id="f2dda-118">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="f2dda-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="f2dda-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f2dda-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f2dda-120">Hodnota, která určuje, zda zprávy zpracované touto vazbou jsou trvalé nebo přechodné.</span><span class="sxs-lookup"><span data-stu-id="f2dda-120">A value that indicates whether the messages processed by this binding are durable or volatile.</span></span>  
  
### <a name="exactlyonce"></a><span data-ttu-id="f2dda-121">exactlyOnce</span><span class="sxs-lookup"><span data-stu-id="f2dda-121">ExactlyOnce</span></span>  
 <span data-ttu-id="f2dda-122">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="f2dda-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="f2dda-123">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f2dda-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f2dda-124">Logická hodnota, která určuje, zda zprávy zpracované touto vazbou budou obdrženy pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="f2dda-124">A Boolean value that indicates whether messages processed by this binding are received exactly once.</span></span>  
  
### <a name="maxretrycycles"></a><span data-ttu-id="f2dda-125">MaxRetryCycles</span><span class="sxs-lookup"><span data-stu-id="f2dda-125">MaxRetryCycles</span></span>  
 <span data-ttu-id="f2dda-126">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="f2dda-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="f2dda-127">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f2dda-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f2dda-128">Maximální počet opakovaných cyklů pokusů o doručení zpráv do přijímající aplikace.</span><span class="sxs-lookup"><span data-stu-id="f2dda-128">The maximum number of retry cycles to attempt delivery of messages to the receiving application.</span></span>  
  
### <a name="receiveerrorhandling"></a><span data-ttu-id="f2dda-129">receiveErrorHandling</span><span class="sxs-lookup"><span data-stu-id="f2dda-129">ReceiveErrorHandling</span></span>  
 <span data-ttu-id="f2dda-130">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="f2dda-130">Data type: string</span></span>  
  
 <span data-ttu-id="f2dda-131">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f2dda-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f2dda-132">Nastavení pro manipulaci s nezpracovatelnými zprávami.</span><span class="sxs-lookup"><span data-stu-id="f2dda-132">The settings for poison message handling.</span></span>  
  
### <a name="receiveretrycount"></a><span data-ttu-id="f2dda-133">ReceiveRetryCount</span><span class="sxs-lookup"><span data-stu-id="f2dda-133">ReceiveRetryCount</span></span>  
 <span data-ttu-id="f2dda-134">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="f2dda-134">Data type: sint32</span></span>  
  
 <span data-ttu-id="f2dda-135">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f2dda-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f2dda-136">Maximální počet okamžitých opakovaných pokusů o zprávu, která je načtena z fronty aplikace.</span><span class="sxs-lookup"><span data-stu-id="f2dda-136">The maximum number of immediate retry attempts on a message that is read from the application queue.</span></span>  
  
### <a name="retrycycledelay"></a><span data-ttu-id="f2dda-137">RetryCycleDelay</span><span class="sxs-lookup"><span data-stu-id="f2dda-137">RetryCycleDelay</span></span>  
 <span data-ttu-id="f2dda-138">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="f2dda-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="f2dda-139">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f2dda-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f2dda-140">Hodnota, která určuje časovou prodlevu mezi opakovanými cykly při pokusu o doručení zprávy, která nemohla být doručena okamžitě.</span><span class="sxs-lookup"><span data-stu-id="f2dda-140">A value that indicates the time delay between retry cycles when attempting to deliver a message that could not be delivered immediately.</span></span>  
  
### <a name="timetolive"></a><span data-ttu-id="f2dda-141">TimeToLive</span><span class="sxs-lookup"><span data-stu-id="f2dda-141">TimeToLive</span></span>  
 <span data-ttu-id="f2dda-142">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="f2dda-142">Data type: datetime</span></span>  
  
 <span data-ttu-id="f2dda-143">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f2dda-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f2dda-144">Interval času, který označuje dobu zprávy zpracované touto vazbou může být ve frontě před vypršením jejich platnosti.</span><span class="sxs-lookup"><span data-stu-id="f2dda-144">The interval of time that indicates how long the messages processed by this binding can be in the queue before they expire.</span></span>  
  
### <a name="usemsmqtracing"></a><span data-ttu-id="f2dda-145">useMsmqTracing</span><span class="sxs-lookup"><span data-stu-id="f2dda-145">UseMsmqTracing</span></span>  
 <span data-ttu-id="f2dda-146">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="f2dda-146">Data type: boolean</span></span>  
  
 <span data-ttu-id="f2dda-147">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f2dda-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f2dda-148">Logická hodnota, která určuje, zda zprávy zpracované touto vazbou mají být vyvolány.</span><span class="sxs-lookup"><span data-stu-id="f2dda-148">A Boolean value that indicates whether messages processed by this binding should be traced.</span></span>  
  
### <a name="usesourcejournal"></a><span data-ttu-id="f2dda-149">UseSourceJournal</span><span class="sxs-lookup"><span data-stu-id="f2dda-149">UseSourceJournal</span></span>  
 <span data-ttu-id="f2dda-150">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="f2dda-150">Data type: boolean</span></span>  
  
 <span data-ttu-id="f2dda-151">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f2dda-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f2dda-152">Logická hodnota, která určuje, zda kopie zpráv zpracovaných touto vazbou uskladněny ve frontě deníku zdroje.</span><span class="sxs-lookup"><span data-stu-id="f2dda-152">A Boolean value that indicates whether copies of messages processed by this binding should be stored in the source journal queue.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2dda-153">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f2dda-153">Requirements</span></span>  
  
|<span data-ttu-id="f2dda-154">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="f2dda-154">MOF</span></span>|<span data-ttu-id="f2dda-155">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="f2dda-155">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="f2dda-156">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="f2dda-156">Namespace</span></span>|<span data-ttu-id="f2dda-157">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f2dda-157">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f2dda-158">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f2dda-158">See also</span></span>
- <xref:System.ServiceModel.NetMsmqBinding>
- <xref:System.ServiceModel.MsmqBindingBase>
