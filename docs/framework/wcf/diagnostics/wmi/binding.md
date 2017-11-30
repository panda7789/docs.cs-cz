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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6505fa08ca43e64df224b75500aacbc903783398
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="binding"></a><span data-ttu-id="f2cd6-102">Vazba</span><span class="sxs-lookup"><span data-stu-id="f2cd6-102">Binding</span></span>
<span data-ttu-id="f2cd6-103">rozhraní WMI vazby</span><span class="sxs-lookup"><span data-stu-id="f2cd6-103">wmi Binding</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2cd6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f2cd6-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="f2cd6-105">Metody</span><span class="sxs-lookup"><span data-stu-id="f2cd6-105">Methods</span></span>  
 <span data-ttu-id="f2cd6-106">Třídu vazby nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="f2cd6-106">The Binding class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f2cd6-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="f2cd6-107">Properties</span></span>  
 <span data-ttu-id="f2cd6-108">Třídu vazby má následující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="f2cd6-108">The Binding class has the following properties.</span></span>  
  
### <a name="bindingelements"></a><span data-ttu-id="f2cd6-109">Třídy BindingElements</span><span class="sxs-lookup"><span data-stu-id="f2cd6-109">BindingElements</span></span>  
 <span data-ttu-id="f2cd6-110">Datový typ: pole BindingElement</span><span class="sxs-lookup"><span data-stu-id="f2cd6-110">Data type: BindingElement array</span></span>  
  
 <span data-ttu-id="f2cd6-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f2cd6-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f2cd6-112">Kolekce elementů vazby implementované vazby.</span><span class="sxs-lookup"><span data-stu-id="f2cd6-112">The collection of binding elements implemented by the binding.</span></span>  
  
### <a name="closetimeout"></a><span data-ttu-id="f2cd6-113">Intervalu</span><span class="sxs-lookup"><span data-stu-id="f2cd6-113">CloseTimeout</span></span>  
 <span data-ttu-id="f2cd6-114">Datový typ: data a času</span><span class="sxs-lookup"><span data-stu-id="f2cd6-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="f2cd6-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f2cd6-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f2cd6-116">Interval čas zadaný pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="f2cd6-116">The interval of time provided for a close operation to complete.</span></span>  
  
### <a name="name"></a><span data-ttu-id="f2cd6-117">Název</span><span class="sxs-lookup"><span data-stu-id="f2cd6-117">Name</span></span>  
 <span data-ttu-id="f2cd6-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="f2cd6-118">Data type: string</span></span>  
  
 <span data-ttu-id="f2cd6-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f2cd6-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f2cd6-120">Název vazby.</span><span class="sxs-lookup"><span data-stu-id="f2cd6-120">The name of the binding.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="f2cd6-121">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="f2cd6-121">Namespace</span></span>  
 <span data-ttu-id="f2cd6-122">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="f2cd6-122">Data type: string</span></span>  
  
 <span data-ttu-id="f2cd6-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f2cd6-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f2cd6-124">Obor názvů XML vazby.</span><span class="sxs-lookup"><span data-stu-id="f2cd6-124">The XML namespace of the binding.</span></span>  
  
### <a name="opentimeout"></a><span data-ttu-id="f2cd6-125">openTimeout</span><span class="sxs-lookup"><span data-stu-id="f2cd6-125">OpenTimeout</span></span>  
 <span data-ttu-id="f2cd6-126">Datový typ: data a času</span><span class="sxs-lookup"><span data-stu-id="f2cd6-126">Data type: datetime</span></span>  
  
 <span data-ttu-id="f2cd6-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f2cd6-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f2cd6-128">Interval čas zadaný pro otevřete na dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="f2cd6-128">The interval of time provided for an open operation to complete.</span></span>  
  
### <a name="receivetimeout"></a><span data-ttu-id="f2cd6-129">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="f2cd6-129">ReceiveTimeout</span></span>  
 <span data-ttu-id="f2cd6-130">Datový typ: data a času</span><span class="sxs-lookup"><span data-stu-id="f2cd6-130">Data type: datetime</span></span>  
  
 <span data-ttu-id="f2cd6-131">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f2cd6-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f2cd6-132">Interval čas zadaný pro na dokončení operace příjmu.</span><span class="sxs-lookup"><span data-stu-id="f2cd6-132">The interval of time provided for a receive operation to complete.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="f2cd6-133">Schéma</span><span class="sxs-lookup"><span data-stu-id="f2cd6-133">Scheme</span></span>  
 <span data-ttu-id="f2cd6-134">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="f2cd6-134">Data type: string</span></span>  
  
 <span data-ttu-id="f2cd6-135">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f2cd6-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f2cd6-136">Přenosové schéma identifikátoru URI používaný kanál a naslouchací proces objekty Factory, které jsou vytvořené pomocí vazby.</span><span class="sxs-lookup"><span data-stu-id="f2cd6-136">The URI transport scheme that is used by the channel and listener factories that are built by the binding.</span></span>  
  
### <a name="sendtimeout"></a><span data-ttu-id="f2cd6-137">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="f2cd6-137">SendTimeout</span></span>  
 <span data-ttu-id="f2cd6-138">Datový typ: data a času</span><span class="sxs-lookup"><span data-stu-id="f2cd6-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="f2cd6-139">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f2cd6-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f2cd6-140">Interval čas zadaný pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="f2cd6-140">The interval of time provided for a send operation to complete.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2cd6-141">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f2cd6-141">Requirements</span></span>  
  
|<span data-ttu-id="f2cd6-142">MOF</span><span class="sxs-lookup"><span data-stu-id="f2cd6-142">MOF</span></span>|<span data-ttu-id="f2cd6-143">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="f2cd6-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="f2cd6-144">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="f2cd6-144">Namespace</span></span>|<span data-ttu-id="f2cd6-145">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f2cd6-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f2cd6-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="f2cd6-146">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>
