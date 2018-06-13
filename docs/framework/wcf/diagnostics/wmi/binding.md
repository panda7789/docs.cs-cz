---
title: Binding2
ms.date: 03/30/2017
ms.assetid: 09511c6c-5749-4bb0-874e-0f0be36bfe04
ms.openlocfilehash: 0260b75a0f49e0f6f72d7d1eda642d0a494d2892
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33487004"
---
# <a name="binding"></a><span data-ttu-id="45d3f-102">Vazba</span><span class="sxs-lookup"><span data-stu-id="45d3f-102">Binding</span></span>
<span data-ttu-id="45d3f-103">rozhraní WMI vazby</span><span class="sxs-lookup"><span data-stu-id="45d3f-103">wmi Binding</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45d3f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="45d3f-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="45d3f-105">Metody</span><span class="sxs-lookup"><span data-stu-id="45d3f-105">Methods</span></span>  
 <span data-ttu-id="45d3f-106">Třídu vazby nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="45d3f-106">The Binding class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="45d3f-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="45d3f-107">Properties</span></span>  
 <span data-ttu-id="45d3f-108">Třídu vazby má následující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="45d3f-108">The Binding class has the following properties.</span></span>  
  
### <a name="bindingelements"></a><span data-ttu-id="45d3f-109">Třídy BindingElements</span><span class="sxs-lookup"><span data-stu-id="45d3f-109">BindingElements</span></span>  
 <span data-ttu-id="45d3f-110">Datový typ: pole BindingElement</span><span class="sxs-lookup"><span data-stu-id="45d3f-110">Data type: BindingElement array</span></span>  
  
 <span data-ttu-id="45d3f-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="45d3f-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="45d3f-112">Kolekce elementů vazby implementované vazby.</span><span class="sxs-lookup"><span data-stu-id="45d3f-112">The collection of binding elements implemented by the binding.</span></span>  
  
### <a name="closetimeout"></a><span data-ttu-id="45d3f-113">Intervalu</span><span class="sxs-lookup"><span data-stu-id="45d3f-113">CloseTimeout</span></span>  
 <span data-ttu-id="45d3f-114">Datový typ: data a času</span><span class="sxs-lookup"><span data-stu-id="45d3f-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="45d3f-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="45d3f-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="45d3f-116">Interval čas zadaný pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="45d3f-116">The interval of time provided for a close operation to complete.</span></span>  
  
### <a name="name"></a><span data-ttu-id="45d3f-117">Název</span><span class="sxs-lookup"><span data-stu-id="45d3f-117">Name</span></span>  
 <span data-ttu-id="45d3f-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="45d3f-118">Data type: string</span></span>  
  
 <span data-ttu-id="45d3f-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="45d3f-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="45d3f-120">Název vazby.</span><span class="sxs-lookup"><span data-stu-id="45d3f-120">The name of the binding.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="45d3f-121">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="45d3f-121">Namespace</span></span>  
 <span data-ttu-id="45d3f-122">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="45d3f-122">Data type: string</span></span>  
  
 <span data-ttu-id="45d3f-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="45d3f-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="45d3f-124">Obor názvů XML vazby.</span><span class="sxs-lookup"><span data-stu-id="45d3f-124">The XML namespace of the binding.</span></span>  
  
### <a name="opentimeout"></a><span data-ttu-id="45d3f-125">openTimeout</span><span class="sxs-lookup"><span data-stu-id="45d3f-125">OpenTimeout</span></span>  
 <span data-ttu-id="45d3f-126">Datový typ: data a času</span><span class="sxs-lookup"><span data-stu-id="45d3f-126">Data type: datetime</span></span>  
  
 <span data-ttu-id="45d3f-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="45d3f-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="45d3f-128">Interval čas zadaný pro otevřete na dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="45d3f-128">The interval of time provided for an open operation to complete.</span></span>  
  
### <a name="receivetimeout"></a><span data-ttu-id="45d3f-129">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="45d3f-129">ReceiveTimeout</span></span>  
 <span data-ttu-id="45d3f-130">Datový typ: data a času</span><span class="sxs-lookup"><span data-stu-id="45d3f-130">Data type: datetime</span></span>  
  
 <span data-ttu-id="45d3f-131">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="45d3f-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="45d3f-132">Interval čas zadaný pro na dokončení operace příjmu.</span><span class="sxs-lookup"><span data-stu-id="45d3f-132">The interval of time provided for a receive operation to complete.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="45d3f-133">Schéma</span><span class="sxs-lookup"><span data-stu-id="45d3f-133">Scheme</span></span>  
 <span data-ttu-id="45d3f-134">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="45d3f-134">Data type: string</span></span>  
  
 <span data-ttu-id="45d3f-135">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="45d3f-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="45d3f-136">Přenosové schéma identifikátoru URI používaný kanál a naslouchací proces objekty Factory, které jsou vytvořené pomocí vazby.</span><span class="sxs-lookup"><span data-stu-id="45d3f-136">The URI transport scheme that is used by the channel and listener factories that are built by the binding.</span></span>  
  
### <a name="sendtimeout"></a><span data-ttu-id="45d3f-137">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="45d3f-137">SendTimeout</span></span>  
 <span data-ttu-id="45d3f-138">Datový typ: data a času</span><span class="sxs-lookup"><span data-stu-id="45d3f-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="45d3f-139">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="45d3f-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="45d3f-140">Interval čas zadaný pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="45d3f-140">The interval of time provided for a send operation to complete.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45d3f-141">Požadavky</span><span class="sxs-lookup"><span data-stu-id="45d3f-141">Requirements</span></span>  
  
|<span data-ttu-id="45d3f-142">MOF</span><span class="sxs-lookup"><span data-stu-id="45d3f-142">MOF</span></span>|<span data-ttu-id="45d3f-143">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="45d3f-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="45d3f-144">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="45d3f-144">Namespace</span></span>|<span data-ttu-id="45d3f-145">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="45d3f-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="45d3f-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="45d3f-146">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>
