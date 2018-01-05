---
title: Binding2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 09511c6c-5749-4bb0-874e-0f0be36bfe04
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f6553d1e1c030a30eed74ff81d3e07e28a9f25b7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="binding"></a><span data-ttu-id="b02d9-102">Vazba</span><span class="sxs-lookup"><span data-stu-id="b02d9-102">Binding</span></span>
<span data-ttu-id="b02d9-103">rozhraní WMI vazby</span><span class="sxs-lookup"><span data-stu-id="b02d9-103">wmi Binding</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b02d9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b02d9-104">Syntax</span></span>  
  
```  
class Binding  
{  
  BindingElement BindingElements[];  
  datetime CloseTimeout;  
  string Name;  
  string Namespace;  
  datetime OpenTimeout;  
  datetime ReceiveTimeout;  
  string Scheme;  
  datetime SendTimeout;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="b02d9-105">Metody</span><span class="sxs-lookup"><span data-stu-id="b02d9-105">Methods</span></span>  
 <span data-ttu-id="b02d9-106">Třídu vazby nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="b02d9-106">The Binding class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b02d9-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="b02d9-107">Properties</span></span>  
 <span data-ttu-id="b02d9-108">Třídu vazby má následující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b02d9-108">The Binding class has the following properties.</span></span>  
  
### <a name="bindingelements"></a><span data-ttu-id="b02d9-109">Třídy BindingElements</span><span class="sxs-lookup"><span data-stu-id="b02d9-109">BindingElements</span></span>  
 <span data-ttu-id="b02d9-110">Datový typ: pole BindingElement</span><span class="sxs-lookup"><span data-stu-id="b02d9-110">Data type: BindingElement array</span></span>  
  
 <span data-ttu-id="b02d9-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="b02d9-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b02d9-112">Kolekce elementů vazby implementované vazby.</span><span class="sxs-lookup"><span data-stu-id="b02d9-112">The collection of binding elements implemented by the binding.</span></span>  
  
### <a name="closetimeout"></a><span data-ttu-id="b02d9-113">Intervalu</span><span class="sxs-lookup"><span data-stu-id="b02d9-113">CloseTimeout</span></span>  
 <span data-ttu-id="b02d9-114">Datový typ: data a času</span><span class="sxs-lookup"><span data-stu-id="b02d9-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="b02d9-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="b02d9-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b02d9-116">Interval čas zadaný pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="b02d9-116">The interval of time provided for a close operation to complete.</span></span>  
  
### <a name="name"></a><span data-ttu-id="b02d9-117">Název</span><span class="sxs-lookup"><span data-stu-id="b02d9-117">Name</span></span>  
 <span data-ttu-id="b02d9-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="b02d9-118">Data type: string</span></span>  
  
 <span data-ttu-id="b02d9-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="b02d9-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b02d9-120">Název vazby.</span><span class="sxs-lookup"><span data-stu-id="b02d9-120">The name of the binding.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="b02d9-121">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="b02d9-121">Namespace</span></span>  
 <span data-ttu-id="b02d9-122">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="b02d9-122">Data type: string</span></span>  
  
 <span data-ttu-id="b02d9-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="b02d9-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b02d9-124">Obor názvů XML vazby.</span><span class="sxs-lookup"><span data-stu-id="b02d9-124">The XML namespace of the binding.</span></span>  
  
### <a name="opentimeout"></a><span data-ttu-id="b02d9-125">openTimeout</span><span class="sxs-lookup"><span data-stu-id="b02d9-125">OpenTimeout</span></span>  
 <span data-ttu-id="b02d9-126">Datový typ: data a času</span><span class="sxs-lookup"><span data-stu-id="b02d9-126">Data type: datetime</span></span>  
  
 <span data-ttu-id="b02d9-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="b02d9-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b02d9-128">Interval čas zadaný pro otevřete na dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="b02d9-128">The interval of time provided for an open operation to complete.</span></span>  
  
### <a name="receivetimeout"></a><span data-ttu-id="b02d9-129">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="b02d9-129">ReceiveTimeout</span></span>  
 <span data-ttu-id="b02d9-130">Datový typ: data a času</span><span class="sxs-lookup"><span data-stu-id="b02d9-130">Data type: datetime</span></span>  
  
 <span data-ttu-id="b02d9-131">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="b02d9-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b02d9-132">Interval čas zadaný pro na dokončení operace příjmu.</span><span class="sxs-lookup"><span data-stu-id="b02d9-132">The interval of time provided for a receive operation to complete.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="b02d9-133">Schéma</span><span class="sxs-lookup"><span data-stu-id="b02d9-133">Scheme</span></span>  
 <span data-ttu-id="b02d9-134">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="b02d9-134">Data type: string</span></span>  
  
 <span data-ttu-id="b02d9-135">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="b02d9-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b02d9-136">Přenosové schéma identifikátoru URI používaný kanál a naslouchací proces objekty Factory, které jsou vytvořené pomocí vazby.</span><span class="sxs-lookup"><span data-stu-id="b02d9-136">The URI transport scheme that is used by the channel and listener factories that are built by the binding.</span></span>  
  
### <a name="sendtimeout"></a><span data-ttu-id="b02d9-137">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="b02d9-137">SendTimeout</span></span>  
 <span data-ttu-id="b02d9-138">Datový typ: data a času</span><span class="sxs-lookup"><span data-stu-id="b02d9-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="b02d9-139">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="b02d9-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b02d9-140">Interval čas zadaný pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="b02d9-140">The interval of time provided for a send operation to complete.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b02d9-141">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b02d9-141">Requirements</span></span>  
  
|<span data-ttu-id="b02d9-142">MOF</span><span class="sxs-lookup"><span data-stu-id="b02d9-142">MOF</span></span>|<span data-ttu-id="b02d9-143">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="b02d9-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b02d9-144">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="b02d9-144">Namespace</span></span>|<span data-ttu-id="b02d9-145">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b02d9-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b02d9-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="b02d9-146">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>
