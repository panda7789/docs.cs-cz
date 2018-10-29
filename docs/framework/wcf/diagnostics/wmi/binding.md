---
title: Binding2
ms.date: 03/30/2017
ms.assetid: 09511c6c-5749-4bb0-874e-0f0be36bfe04
ms.openlocfilehash: 84e304f3dedcbd785d6238e6cb5eb142c288b995
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2018
ms.locfileid: "50198886"
---
# <a name="binding"></a><span data-ttu-id="f4801-102">Vazba</span><span class="sxs-lookup"><span data-stu-id="f4801-102">Binding</span></span>
<span data-ttu-id="f4801-103">rozhraní WMI vazby</span><span class="sxs-lookup"><span data-stu-id="f4801-103">wmi Binding</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4801-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f4801-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="f4801-105">Metody</span><span class="sxs-lookup"><span data-stu-id="f4801-105">Methods</span></span>  
 <span data-ttu-id="f4801-106">Třídy vazby nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="f4801-106">The Binding class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f4801-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="f4801-107">Properties</span></span>  
 <span data-ttu-id="f4801-108">Třídy vazby má následující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="f4801-108">The Binding class has the following properties.</span></span>  
  
### <a name="bindingelements"></a><span data-ttu-id="f4801-109">Třídy BindingElements</span><span class="sxs-lookup"><span data-stu-id="f4801-109">BindingElements</span></span>  
 <span data-ttu-id="f4801-110">Datový typ: pole BindingElement</span><span class="sxs-lookup"><span data-stu-id="f4801-110">Data type: BindingElement array</span></span>  
  
 <span data-ttu-id="f4801-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f4801-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f4801-112">Kolekce elementů, které jsou implementovány vazbou vazby.</span><span class="sxs-lookup"><span data-stu-id="f4801-112">The collection of binding elements implemented by the binding.</span></span>  
  
### <a name="closetimeout"></a><span data-ttu-id="f4801-113">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="f4801-113">CloseTimeout</span></span>  
 <span data-ttu-id="f4801-114">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="f4801-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="f4801-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f4801-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f4801-116">Časový interval poskytnutý pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="f4801-116">The interval of time provided for a close operation to complete.</span></span>  
  
### <a name="name"></a><span data-ttu-id="f4801-117">Název</span><span class="sxs-lookup"><span data-stu-id="f4801-117">Name</span></span>  
 <span data-ttu-id="f4801-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="f4801-118">Data type: string</span></span>  
  
 <span data-ttu-id="f4801-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f4801-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f4801-120">Název vazby.</span><span class="sxs-lookup"><span data-stu-id="f4801-120">The name of the binding.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="f4801-121">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="f4801-121">Namespace</span></span>  
 <span data-ttu-id="f4801-122">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="f4801-122">Data type: string</span></span>  
  
 <span data-ttu-id="f4801-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f4801-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f4801-124">XML obor názvů vazby.</span><span class="sxs-lookup"><span data-stu-id="f4801-124">The XML namespace of the binding.</span></span>  
  
### <a name="opentimeout"></a><span data-ttu-id="f4801-125">openTimeout</span><span class="sxs-lookup"><span data-stu-id="f4801-125">OpenTimeout</span></span>  
 <span data-ttu-id="f4801-126">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="f4801-126">Data type: datetime</span></span>  
  
 <span data-ttu-id="f4801-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f4801-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f4801-128">Časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="f4801-128">The interval of time provided for an open operation to complete.</span></span>  
  
### <a name="receivetimeout"></a><span data-ttu-id="f4801-129">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="f4801-129">ReceiveTimeout</span></span>  
 <span data-ttu-id="f4801-130">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="f4801-130">Data type: datetime</span></span>  
  
 <span data-ttu-id="f4801-131">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f4801-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f4801-132">Časový interval poskytnutý pro dokončení operace obdržení.</span><span class="sxs-lookup"><span data-stu-id="f4801-132">The interval of time provided for a receive operation to complete.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="f4801-133">Schéma</span><span class="sxs-lookup"><span data-stu-id="f4801-133">Scheme</span></span>  
 <span data-ttu-id="f4801-134">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="f4801-134">Data type: string</span></span>  
  
 <span data-ttu-id="f4801-135">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f4801-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f4801-136">Schéma přepravy identifikátoru URI, který je používán továren kanálu a posluchače, které jsou vytvořeny vazbou.</span><span class="sxs-lookup"><span data-stu-id="f4801-136">The URI transport scheme that is used by the channel and listener factories that are built by the binding.</span></span>  
  
### <a name="sendtimeout"></a><span data-ttu-id="f4801-137">SendTimeout</span><span class="sxs-lookup"><span data-stu-id="f4801-137">SendTimeout</span></span>  
 <span data-ttu-id="f4801-138">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="f4801-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="f4801-139">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f4801-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f4801-140">Časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="f4801-140">The interval of time provided for a send operation to complete.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4801-141">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f4801-141">Requirements</span></span>  
  
|<span data-ttu-id="f4801-142">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="f4801-142">MOF</span></span>|<span data-ttu-id="f4801-143">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="f4801-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="f4801-144">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="f4801-144">Namespace</span></span>|<span data-ttu-id="f4801-145">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f4801-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f4801-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="f4801-146">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>
