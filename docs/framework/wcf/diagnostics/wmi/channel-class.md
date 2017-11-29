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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1df634a61cce695fca74fdfe53beea6c0f83d082
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="channel-class"></a><span data-ttu-id="ab428-102">Třída Channel</span><span class="sxs-lookup"><span data-stu-id="ab428-102">Channel class</span></span>
<span data-ttu-id="ab428-103">Kanál</span><span class="sxs-lookup"><span data-stu-id="ab428-103">Channel</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab428-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ab428-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="ab428-105">Metody</span><span class="sxs-lookup"><span data-stu-id="ab428-105">Methods</span></span>  
 <span data-ttu-id="ab428-106">Třída Channel nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="ab428-106">The Channel class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ab428-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="ab428-107">Properties</span></span>  
 <span data-ttu-id="ab428-108">Třída Channel má následující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ab428-108">The Channel class has the following properties.</span></span>  
  
### <a name="localaddress"></a><span data-ttu-id="ab428-109">LocalAddress</span><span class="sxs-lookup"><span data-stu-id="ab428-109">LocalAddress</span></span>  
 <span data-ttu-id="ab428-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="ab428-110">Data type: string</span></span>  
  
 <span data-ttu-id="ab428-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ab428-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ab428-112">Místní koncový bod pro kanál.</span><span class="sxs-lookup"><span data-stu-id="ab428-112">The local endpoint for the channel.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="ab428-113">ref</span><span class="sxs-lookup"><span data-stu-id="ab428-113">ref</span></span>  
 <span data-ttu-id="ab428-114">Datový typ: koncový bod</span><span class="sxs-lookup"><span data-stu-id="ab428-114">Data type: Endpoint</span></span>  
  
 <span data-ttu-id="ab428-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ab428-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ab428-116">Odkaz na koncový bod kanálu se připojí k.</span><span class="sxs-lookup"><span data-stu-id="ab428-116">A reference to the endpoint the channel connects to.</span></span>  
  
### <a name="remoteaddress"></a><span data-ttu-id="ab428-117">RemoteAddress</span><span class="sxs-lookup"><span data-stu-id="ab428-117">RemoteAddress</span></span>  
 <span data-ttu-id="ab428-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="ab428-118">Data type: string</span></span>  
  
 <span data-ttu-id="ab428-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ab428-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ab428-120">Vzdálená adresa spojená s kanálem.</span><span class="sxs-lookup"><span data-stu-id="ab428-120">The remote address associated with the channel.</span></span>  
  
### <a name="sessionid"></a><span data-ttu-id="ab428-121">SessionId</span><span class="sxs-lookup"><span data-stu-id="ab428-121">SessionId</span></span>  
 <span data-ttu-id="ab428-122">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="ab428-122">Data type: string</span></span>  
  
 <span data-ttu-id="ab428-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ab428-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ab428-124">Aktuální relace Id, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="ab428-124">The current session Id, if any.</span></span>  
  
### <a name="type"></a><span data-ttu-id="ab428-125">Typ</span><span class="sxs-lookup"><span data-stu-id="ab428-125">Type</span></span>  
 <span data-ttu-id="ab428-126">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="ab428-126">Data type: string</span></span>  
  
 <span data-ttu-id="ab428-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ab428-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ab428-128">Typ kanálu.</span><span class="sxs-lookup"><span data-stu-id="ab428-128">The type of the channel.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab428-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ab428-129">Requirements</span></span>  
  
|<span data-ttu-id="ab428-130">MOF</span><span class="sxs-lookup"><span data-stu-id="ab428-130">MOF</span></span>|<span data-ttu-id="ab428-131">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="ab428-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ab428-132">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="ab428-132">Namespace</span></span>|<span data-ttu-id="ab428-133">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ab428-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ab428-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="ab428-134">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ChannelBase>
