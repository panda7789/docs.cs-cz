---
title: "Třída Channel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 073f0a2a2731a08acd914a7dd85cb2b419d98128
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="channel-class"></a><span data-ttu-id="50f95-102">Třída Channel</span><span class="sxs-lookup"><span data-stu-id="50f95-102">Channel class</span></span>
<span data-ttu-id="50f95-103">Kanál</span><span class="sxs-lookup"><span data-stu-id="50f95-103">Channel</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50f95-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="50f95-104">Syntax</span></span>  
  
```  
class Channel  
{  
  string LocalAddress;  
  Endpoint ref;  
  string RemoteAddress;  
  string SessionId;  
  string Type;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="50f95-105">Metody</span><span class="sxs-lookup"><span data-stu-id="50f95-105">Methods</span></span>  
 <span data-ttu-id="50f95-106">Třída Channel nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="50f95-106">The Channel class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="50f95-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="50f95-107">Properties</span></span>  
 <span data-ttu-id="50f95-108">Třída Channel má následující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="50f95-108">The Channel class has the following properties.</span></span>  
  
### <a name="localaddress"></a><span data-ttu-id="50f95-109">LocalAddress</span><span class="sxs-lookup"><span data-stu-id="50f95-109">LocalAddress</span></span>  
 <span data-ttu-id="50f95-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="50f95-110">Data type: string</span></span>  
  
 <span data-ttu-id="50f95-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="50f95-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="50f95-112">Místní koncový bod pro kanál.</span><span class="sxs-lookup"><span data-stu-id="50f95-112">The local endpoint for the channel.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="50f95-113">ref</span><span class="sxs-lookup"><span data-stu-id="50f95-113">ref</span></span>  
 <span data-ttu-id="50f95-114">Datový typ: koncový bod</span><span class="sxs-lookup"><span data-stu-id="50f95-114">Data type: Endpoint</span></span>  
  
 <span data-ttu-id="50f95-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="50f95-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="50f95-116">Odkaz na koncový bod kanálu se připojí k.</span><span class="sxs-lookup"><span data-stu-id="50f95-116">A reference to the endpoint the channel connects to.</span></span>  
  
### <a name="remoteaddress"></a><span data-ttu-id="50f95-117">RemoteAddress</span><span class="sxs-lookup"><span data-stu-id="50f95-117">RemoteAddress</span></span>  
 <span data-ttu-id="50f95-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="50f95-118">Data type: string</span></span>  
  
 <span data-ttu-id="50f95-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="50f95-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="50f95-120">Vzdálená adresa spojená s kanálem.</span><span class="sxs-lookup"><span data-stu-id="50f95-120">The remote address associated with the channel.</span></span>  
  
### <a name="sessionid"></a><span data-ttu-id="50f95-121">SessionId</span><span class="sxs-lookup"><span data-stu-id="50f95-121">SessionId</span></span>  
 <span data-ttu-id="50f95-122">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="50f95-122">Data type: string</span></span>  
  
 <span data-ttu-id="50f95-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="50f95-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="50f95-124">Aktuální relace Id, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="50f95-124">The current session Id, if any.</span></span>  
  
### <a name="type"></a><span data-ttu-id="50f95-125">Typ</span><span class="sxs-lookup"><span data-stu-id="50f95-125">Type</span></span>  
 <span data-ttu-id="50f95-126">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="50f95-126">Data type: string</span></span>  
  
 <span data-ttu-id="50f95-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="50f95-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="50f95-128">Typ kanálu.</span><span class="sxs-lookup"><span data-stu-id="50f95-128">The type of the channel.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50f95-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="50f95-129">Requirements</span></span>  
  
|<span data-ttu-id="50f95-130">MOF</span><span class="sxs-lookup"><span data-stu-id="50f95-130">MOF</span></span>|<span data-ttu-id="50f95-131">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="50f95-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="50f95-132">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="50f95-132">Namespace</span></span>|<span data-ttu-id="50f95-133">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="50f95-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="50f95-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="50f95-134">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ChannelBase>
