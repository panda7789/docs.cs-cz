---
title: Třída Channel
ms.date: 03/30/2017
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
ms.openlocfilehash: 3fbf398cca7ae9adbbecb9439bf3cbd32eb03969
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54668389"
---
# <a name="channel-class"></a><span data-ttu-id="955d8-102">Třída Channel</span><span class="sxs-lookup"><span data-stu-id="955d8-102">Channel class</span></span>
<span data-ttu-id="955d8-103">Kanál</span><span class="sxs-lookup"><span data-stu-id="955d8-103">Channel</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="955d8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="955d8-104">Syntax</span></span>  
  
```csharp
class Channel  
{  
  string LocalAddress;  
  Endpoint ref;  
  string RemoteAddress;  
  string SessionId;  
  string Type;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="955d8-105">Metody</span><span class="sxs-lookup"><span data-stu-id="955d8-105">Methods</span></span>  
 <span data-ttu-id="955d8-106">Třída kanálu nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="955d8-106">The Channel class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="955d8-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="955d8-107">Properties</span></span>  
 <span data-ttu-id="955d8-108">Třída kanálu má následující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="955d8-108">The Channel class has the following properties.</span></span>  
  
### <a name="localaddress"></a><span data-ttu-id="955d8-109">LocalAddress</span><span class="sxs-lookup"><span data-stu-id="955d8-109">LocalAddress</span></span>  
 <span data-ttu-id="955d8-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="955d8-110">Data type: string</span></span>  
  
 <span data-ttu-id="955d8-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="955d8-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="955d8-112">Místní koncový bod pro kanál.</span><span class="sxs-lookup"><span data-stu-id="955d8-112">The local endpoint for the channel.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="955d8-113">ref</span><span class="sxs-lookup"><span data-stu-id="955d8-113">ref</span></span>  
 <span data-ttu-id="955d8-114">Datový typ: Koncový bod</span><span class="sxs-lookup"><span data-stu-id="955d8-114">Data type: Endpoint</span></span>  
  
 <span data-ttu-id="955d8-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="955d8-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="955d8-116">Odkaz na koncový bod kanálu se připojí k.</span><span class="sxs-lookup"><span data-stu-id="955d8-116">A reference to the endpoint the channel connects to.</span></span>  
  
### <a name="remoteaddress"></a><span data-ttu-id="955d8-117">RemoteAddress</span><span class="sxs-lookup"><span data-stu-id="955d8-117">RemoteAddress</span></span>  
 <span data-ttu-id="955d8-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="955d8-118">Data type: string</span></span>  
  
 <span data-ttu-id="955d8-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="955d8-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="955d8-120">Vzdálená adresa připojená ke kanálu.</span><span class="sxs-lookup"><span data-stu-id="955d8-120">The remote address associated with the channel.</span></span>  
  
### <a name="sessionid"></a><span data-ttu-id="955d8-121">SessionId</span><span class="sxs-lookup"><span data-stu-id="955d8-121">SessionId</span></span>  
 <span data-ttu-id="955d8-122">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="955d8-122">Data type: string</span></span>  
  
 <span data-ttu-id="955d8-123">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="955d8-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="955d8-124">Id aktuálního procesu, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="955d8-124">The current session Id, if any.</span></span>  
  
### <a name="type"></a><span data-ttu-id="955d8-125">Typ</span><span class="sxs-lookup"><span data-stu-id="955d8-125">Type</span></span>  
 <span data-ttu-id="955d8-126">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="955d8-126">Data type: string</span></span>  
  
 <span data-ttu-id="955d8-127">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="955d8-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="955d8-128">Typ kanálu.</span><span class="sxs-lookup"><span data-stu-id="955d8-128">The type of the channel.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="955d8-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="955d8-129">Requirements</span></span>  
  
|<span data-ttu-id="955d8-130">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="955d8-130">MOF</span></span>|<span data-ttu-id="955d8-131">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="955d8-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="955d8-132">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="955d8-132">Namespace</span></span>|<span data-ttu-id="955d8-133">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="955d8-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="955d8-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="955d8-134">See also</span></span>
- <xref:System.ServiceModel.Channels.ChannelBase>
