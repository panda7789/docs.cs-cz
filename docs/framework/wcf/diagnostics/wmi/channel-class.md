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
ms.openlocfilehash: 93632d6a178c0f58143fc148a0e1eb51be94ed17
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="channel-class"></a><span data-ttu-id="3a99e-102">Třída Channel</span><span class="sxs-lookup"><span data-stu-id="3a99e-102">Channel class</span></span>
<span data-ttu-id="3a99e-103">Kanál</span><span class="sxs-lookup"><span data-stu-id="3a99e-103">Channel</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a99e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3a99e-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="3a99e-105">Metody</span><span class="sxs-lookup"><span data-stu-id="3a99e-105">Methods</span></span>  
 <span data-ttu-id="3a99e-106">Třída Channel nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="3a99e-106">The Channel class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="3a99e-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="3a99e-107">Properties</span></span>  
 <span data-ttu-id="3a99e-108">Třída Channel má následující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3a99e-108">The Channel class has the following properties.</span></span>  
  
### <a name="localaddress"></a><span data-ttu-id="3a99e-109">LocalAddress</span><span class="sxs-lookup"><span data-stu-id="3a99e-109">LocalAddress</span></span>  
 <span data-ttu-id="3a99e-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="3a99e-110">Data type: string</span></span>  
  
 <span data-ttu-id="3a99e-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="3a99e-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3a99e-112">Místní koncový bod pro kanál.</span><span class="sxs-lookup"><span data-stu-id="3a99e-112">The local endpoint for the channel.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="3a99e-113">ref</span><span class="sxs-lookup"><span data-stu-id="3a99e-113">ref</span></span>  
 <span data-ttu-id="3a99e-114">Datový typ: koncový bod</span><span class="sxs-lookup"><span data-stu-id="3a99e-114">Data type: Endpoint</span></span>  
  
 <span data-ttu-id="3a99e-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="3a99e-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3a99e-116">Odkaz na koncový bod kanálu se připojí k.</span><span class="sxs-lookup"><span data-stu-id="3a99e-116">A reference to the endpoint the channel connects to.</span></span>  
  
### <a name="remoteaddress"></a><span data-ttu-id="3a99e-117">RemoteAddress</span><span class="sxs-lookup"><span data-stu-id="3a99e-117">RemoteAddress</span></span>  
 <span data-ttu-id="3a99e-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="3a99e-118">Data type: string</span></span>  
  
 <span data-ttu-id="3a99e-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="3a99e-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3a99e-120">Vzdálená adresa spojená s kanálem.</span><span class="sxs-lookup"><span data-stu-id="3a99e-120">The remote address associated with the channel.</span></span>  
  
### <a name="sessionid"></a><span data-ttu-id="3a99e-121">SessionId</span><span class="sxs-lookup"><span data-stu-id="3a99e-121">SessionId</span></span>  
 <span data-ttu-id="3a99e-122">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="3a99e-122">Data type: string</span></span>  
  
 <span data-ttu-id="3a99e-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="3a99e-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3a99e-124">Aktuální relace Id, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="3a99e-124">The current session Id, if any.</span></span>  
  
### <a name="type"></a><span data-ttu-id="3a99e-125">Typ</span><span class="sxs-lookup"><span data-stu-id="3a99e-125">Type</span></span>  
 <span data-ttu-id="3a99e-126">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="3a99e-126">Data type: string</span></span>  
  
 <span data-ttu-id="3a99e-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="3a99e-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3a99e-128">Typ kanálu.</span><span class="sxs-lookup"><span data-stu-id="3a99e-128">The type of the channel.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a99e-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3a99e-129">Requirements</span></span>  
  
|<span data-ttu-id="3a99e-130">MOF</span><span class="sxs-lookup"><span data-stu-id="3a99e-130">MOF</span></span>|<span data-ttu-id="3a99e-131">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="3a99e-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="3a99e-132">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="3a99e-132">Namespace</span></span>|<span data-ttu-id="3a99e-133">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="3a99e-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3a99e-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="3a99e-134">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ChannelBase>
