---
title: Binding2
ms.date: 03/30/2017
ms.assetid: 09511c6c-5749-4bb0-874e-0f0be36bfe04
ms.openlocfilehash: a040cc6e12833d2c737eb14c591300e5873ddce7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59979157"
---
# <a name="binding"></a><span data-ttu-id="a4a7c-102">Vazba</span><span class="sxs-lookup"><span data-stu-id="a4a7c-102">Binding</span></span>
<span data-ttu-id="a4a7c-103">rozhraní WMI vazby</span><span class="sxs-lookup"><span data-stu-id="a4a7c-103">wmi Binding</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4a7c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a4a7c-104">Syntax</span></span>  
  
```csharp
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
  
## <a name="methods"></a><span data-ttu-id="a4a7c-105">Metody</span><span class="sxs-lookup"><span data-stu-id="a4a7c-105">Methods</span></span>  
 <span data-ttu-id="a4a7c-106">Třídy vazby nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="a4a7c-106">The Binding class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a4a7c-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="a4a7c-107">Properties</span></span>  
 <span data-ttu-id="a4a7c-108">Třídy vazby má následující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="a4a7c-108">The Binding class has the following properties.</span></span>  
  
### <a name="bindingelements"></a><span data-ttu-id="a4a7c-109">Třídy BindingElements</span><span class="sxs-lookup"><span data-stu-id="a4a7c-109">BindingElements</span></span>  
 <span data-ttu-id="a4a7c-110">Datový typ: Pole BindingElement</span><span class="sxs-lookup"><span data-stu-id="a4a7c-110">Data type: BindingElement array</span></span>  
  
 <span data-ttu-id="a4a7c-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="a4a7c-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a4a7c-112">Kolekce elementů, které jsou implementovány vazbou vazby.</span><span class="sxs-lookup"><span data-stu-id="a4a7c-112">The collection of binding elements implemented by the binding.</span></span>  
  
### <a name="closetimeout"></a><span data-ttu-id="a4a7c-113">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="a4a7c-113">CloseTimeout</span></span>  
 <span data-ttu-id="a4a7c-114">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="a4a7c-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="a4a7c-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="a4a7c-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a4a7c-116">Časový interval poskytnutý pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="a4a7c-116">The interval of time provided for a close operation to complete.</span></span>  
  
### <a name="name"></a><span data-ttu-id="a4a7c-117">Název</span><span class="sxs-lookup"><span data-stu-id="a4a7c-117">Name</span></span>  
 <span data-ttu-id="a4a7c-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="a4a7c-118">Data type: string</span></span>  
  
 <span data-ttu-id="a4a7c-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="a4a7c-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a4a7c-120">Název vazby.</span><span class="sxs-lookup"><span data-stu-id="a4a7c-120">The name of the binding.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="a4a7c-121">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="a4a7c-121">Namespace</span></span>  
 <span data-ttu-id="a4a7c-122">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="a4a7c-122">Data type: string</span></span>  
  
 <span data-ttu-id="a4a7c-123">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="a4a7c-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a4a7c-124">XML obor názvů vazby.</span><span class="sxs-lookup"><span data-stu-id="a4a7c-124">The XML namespace of the binding.</span></span>  
  
### <a name="opentimeout"></a><span data-ttu-id="a4a7c-125">openTimeout</span><span class="sxs-lookup"><span data-stu-id="a4a7c-125">OpenTimeout</span></span>  
 <span data-ttu-id="a4a7c-126">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="a4a7c-126">Data type: datetime</span></span>  
  
 <span data-ttu-id="a4a7c-127">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="a4a7c-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a4a7c-128">Časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="a4a7c-128">The interval of time provided for an open operation to complete.</span></span>  
  
### <a name="receivetimeout"></a><span data-ttu-id="a4a7c-129">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="a4a7c-129">ReceiveTimeout</span></span>  
 <span data-ttu-id="a4a7c-130">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="a4a7c-130">Data type: datetime</span></span>  
  
 <span data-ttu-id="a4a7c-131">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="a4a7c-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a4a7c-132">Časový interval poskytnutý pro dokončení operace obdržení.</span><span class="sxs-lookup"><span data-stu-id="a4a7c-132">The interval of time provided for a receive operation to complete.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="a4a7c-133">Schéma</span><span class="sxs-lookup"><span data-stu-id="a4a7c-133">Scheme</span></span>  
 <span data-ttu-id="a4a7c-134">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="a4a7c-134">Data type: string</span></span>  
  
 <span data-ttu-id="a4a7c-135">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="a4a7c-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a4a7c-136">Schéma přepravy identifikátoru URI, který je používán továren kanálu a posluchače, které jsou vytvořeny vazbou.</span><span class="sxs-lookup"><span data-stu-id="a4a7c-136">The URI transport scheme that is used by the channel and listener factories that are built by the binding.</span></span>  
  
### <a name="sendtimeout"></a><span data-ttu-id="a4a7c-137">SendTimeout</span><span class="sxs-lookup"><span data-stu-id="a4a7c-137">SendTimeout</span></span>  
 <span data-ttu-id="a4a7c-138">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="a4a7c-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="a4a7c-139">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="a4a7c-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a4a7c-140">Časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="a4a7c-140">The interval of time provided for a send operation to complete.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4a7c-141">Požadavky</span><span class="sxs-lookup"><span data-stu-id="a4a7c-141">Requirements</span></span>  
  
|<span data-ttu-id="a4a7c-142">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="a4a7c-142">MOF</span></span>|<span data-ttu-id="a4a7c-143">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="a4a7c-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="a4a7c-144">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="a4a7c-144">Namespace</span></span>|<span data-ttu-id="a4a7c-145">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="a4a7c-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a4a7c-146">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a4a7c-146">See also</span></span>

- <xref:System.ServiceModel.Channels.Binding>
