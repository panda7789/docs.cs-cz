---
title: ServiceToEndpointAssociation
ms.date: 03/30/2017
ms.assetid: 03c3cd15-e1b2-4dc2-bdc2-59fdccdae110
ms.openlocfilehash: 3d23a3ee10c47e04ea7bdba202ea5063c0d84fac
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2018
ms.locfileid: "49452706"
---
# <a name="servicetoendpointassociation"></a><span data-ttu-id="109d2-102">ServiceToEndpointAssociation</span><span class="sxs-lookup"><span data-stu-id="109d2-102">ServiceToEndpointAssociation</span></span>
<span data-ttu-id="109d2-103">Služba se mapuje na koncový bod.</span><span class="sxs-lookup"><span data-stu-id="109d2-103">Maps a service to an endpoint.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="109d2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="109d2-104">Syntax</span></span>  
  
```csharp
class ServiceToEndpointAssociation  
{  
  Service ref;  
  Endpoint ref;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="109d2-105">Metody</span><span class="sxs-lookup"><span data-stu-id="109d2-105">Methods</span></span>  
 <span data-ttu-id="109d2-106">Třída ServiceToEndpointAssociation nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="109d2-106">The ServiceToEndpointAssociation class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="109d2-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="109d2-107">Properties</span></span>  
 <span data-ttu-id="109d2-108">Třída ServiceToEndpointAssociation má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="109d2-108">The ServiceToEndpointAssociation class has the following properties:</span></span>  
  
### <a name="ref"></a><span data-ttu-id="109d2-109">ref</span><span class="sxs-lookup"><span data-stu-id="109d2-109">ref</span></span>  
 <span data-ttu-id="109d2-110">Datový typ: Služba</span><span class="sxs-lookup"><span data-stu-id="109d2-110">Data type: Service</span></span>  
  
 <span data-ttu-id="109d2-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="109d2-111">Access type: Read-only</span></span>  
<span data-ttu-id="109d2-112">Kvalifikátory: klíč</span><span class="sxs-lookup"><span data-stu-id="109d2-112">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="109d2-113">Služba spojená s koncovým bodem.</span><span class="sxs-lookup"><span data-stu-id="109d2-113">The service associated with the endpoint.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="109d2-114">ref</span><span class="sxs-lookup"><span data-stu-id="109d2-114">ref</span></span>  
 <span data-ttu-id="109d2-115">Datový typ: koncového bodu</span><span class="sxs-lookup"><span data-stu-id="109d2-115">Data type: Endpoint</span></span>  
  
 <span data-ttu-id="109d2-116">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="109d2-116">Access type: Read-only</span></span>  
<span data-ttu-id="109d2-117">Kvalifikátory: klíč</span><span class="sxs-lookup"><span data-stu-id="109d2-117">Qualifiers: Key</span></span>  
  
 <span data-ttu-id="109d2-118">Koncový bod, související se službou.</span><span class="sxs-lookup"><span data-stu-id="109d2-118">The endpoint associated with the service.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="109d2-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="109d2-119">Requirements</span></span>  
  
|<span data-ttu-id="109d2-120">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="109d2-120">MOF</span></span>|<span data-ttu-id="109d2-121">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="109d2-121">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="109d2-122">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="109d2-122">Namespace</span></span>|<span data-ttu-id="109d2-123">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="109d2-123">Defined in root\ServiceModel</span></span>|
