---
title: Binding2
ms.date: 03/30/2017
ms.assetid: 09511c6c-5749-4bb0-874e-0f0be36bfe04
ms.openlocfilehash: 84e304f3dedcbd785d6238e6cb5eb142c288b995
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50033830"
---
# <a name="binding"></a><span data-ttu-id="ecbce-102">Vazba</span><span class="sxs-lookup"><span data-stu-id="ecbce-102">Binding</span></span>
<span data-ttu-id="ecbce-103">rozhraní WMI vazby</span><span class="sxs-lookup"><span data-stu-id="ecbce-103">wmi Binding</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecbce-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ecbce-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="ecbce-105">Metody</span><span class="sxs-lookup"><span data-stu-id="ecbce-105">Methods</span></span>  
 <span data-ttu-id="ecbce-106">Třídy vazby nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="ecbce-106">The Binding class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ecbce-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="ecbce-107">Properties</span></span>  
 <span data-ttu-id="ecbce-108">Třídy vazby má následující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ecbce-108">The Binding class has the following properties.</span></span>  
  
### <a name="bindingelements"></a><span data-ttu-id="ecbce-109">Třídy BindingElements</span><span class="sxs-lookup"><span data-stu-id="ecbce-109">BindingElements</span></span>  
 <span data-ttu-id="ecbce-110">Datový typ: pole BindingElement</span><span class="sxs-lookup"><span data-stu-id="ecbce-110">Data type: BindingElement array</span></span>  
  
 <span data-ttu-id="ecbce-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ecbce-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ecbce-112">Kolekce elementů, které jsou implementovány vazbou vazby.</span><span class="sxs-lookup"><span data-stu-id="ecbce-112">The collection of binding elements implemented by the binding.</span></span>  
  
### <a name="closetimeout"></a><span data-ttu-id="ecbce-113">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="ecbce-113">CloseTimeout</span></span>  
 <span data-ttu-id="ecbce-114">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="ecbce-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="ecbce-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ecbce-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ecbce-116">Časový interval poskytnutý pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="ecbce-116">The interval of time provided for a close operation to complete.</span></span>  
  
### <a name="name"></a><span data-ttu-id="ecbce-117">Název</span><span class="sxs-lookup"><span data-stu-id="ecbce-117">Name</span></span>  
 <span data-ttu-id="ecbce-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="ecbce-118">Data type: string</span></span>  
  
 <span data-ttu-id="ecbce-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ecbce-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ecbce-120">Název vazby.</span><span class="sxs-lookup"><span data-stu-id="ecbce-120">The name of the binding.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="ecbce-121">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="ecbce-121">Namespace</span></span>  
 <span data-ttu-id="ecbce-122">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="ecbce-122">Data type: string</span></span>  
  
 <span data-ttu-id="ecbce-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ecbce-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ecbce-124">XML obor názvů vazby.</span><span class="sxs-lookup"><span data-stu-id="ecbce-124">The XML namespace of the binding.</span></span>  
  
### <a name="opentimeout"></a><span data-ttu-id="ecbce-125">openTimeout</span><span class="sxs-lookup"><span data-stu-id="ecbce-125">OpenTimeout</span></span>  
 <span data-ttu-id="ecbce-126">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="ecbce-126">Data type: datetime</span></span>  
  
 <span data-ttu-id="ecbce-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ecbce-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ecbce-128">Časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="ecbce-128">The interval of time provided for an open operation to complete.</span></span>  
  
### <a name="receivetimeout"></a><span data-ttu-id="ecbce-129">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="ecbce-129">ReceiveTimeout</span></span>  
 <span data-ttu-id="ecbce-130">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="ecbce-130">Data type: datetime</span></span>  
  
 <span data-ttu-id="ecbce-131">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ecbce-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ecbce-132">Časový interval poskytnutý pro dokončení operace obdržení.</span><span class="sxs-lookup"><span data-stu-id="ecbce-132">The interval of time provided for a receive operation to complete.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="ecbce-133">Schéma</span><span class="sxs-lookup"><span data-stu-id="ecbce-133">Scheme</span></span>  
 <span data-ttu-id="ecbce-134">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="ecbce-134">Data type: string</span></span>  
  
 <span data-ttu-id="ecbce-135">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ecbce-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ecbce-136">Schéma přepravy identifikátoru URI, který je používán továren kanálu a posluchače, které jsou vytvořeny vazbou.</span><span class="sxs-lookup"><span data-stu-id="ecbce-136">The URI transport scheme that is used by the channel and listener factories that are built by the binding.</span></span>  
  
### <a name="sendtimeout"></a><span data-ttu-id="ecbce-137">SendTimeout</span><span class="sxs-lookup"><span data-stu-id="ecbce-137">SendTimeout</span></span>  
 <span data-ttu-id="ecbce-138">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="ecbce-138">Data type: datetime</span></span>  
  
 <span data-ttu-id="ecbce-139">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ecbce-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ecbce-140">Časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="ecbce-140">The interval of time provided for a send operation to complete.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecbce-141">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ecbce-141">Requirements</span></span>  
  
|<span data-ttu-id="ecbce-142">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="ecbce-142">MOF</span></span>|<span data-ttu-id="ecbce-143">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="ecbce-143">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ecbce-144">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="ecbce-144">Namespace</span></span>|<span data-ttu-id="ecbce-145">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ecbce-145">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ecbce-146">Viz také</span><span class="sxs-lookup"><span data-stu-id="ecbce-146">See Also</span></span>  
 <xref:System.ServiceModel.Channels.Binding>
