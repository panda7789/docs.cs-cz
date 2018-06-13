---
title: Třída Channel
ms.date: 03/30/2017
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
ms.openlocfilehash: 4b7c66560c0c136a258c527d8a681d491eb50aae
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485780"
---
# <a name="channel-class"></a><span data-ttu-id="0ee18-102">Třída Channel</span><span class="sxs-lookup"><span data-stu-id="0ee18-102">Channel class</span></span>
<span data-ttu-id="0ee18-103">Kanál</span><span class="sxs-lookup"><span data-stu-id="0ee18-103">Channel</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ee18-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0ee18-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="0ee18-105">Metody</span><span class="sxs-lookup"><span data-stu-id="0ee18-105">Methods</span></span>  
 <span data-ttu-id="0ee18-106">Třída Channel nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="0ee18-106">The Channel class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="0ee18-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="0ee18-107">Properties</span></span>  
 <span data-ttu-id="0ee18-108">Třída Channel má následující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="0ee18-108">The Channel class has the following properties.</span></span>  
  
### <a name="localaddress"></a><span data-ttu-id="0ee18-109">LocalAddress</span><span class="sxs-lookup"><span data-stu-id="0ee18-109">LocalAddress</span></span>  
 <span data-ttu-id="0ee18-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="0ee18-110">Data type: string</span></span>  
  
 <span data-ttu-id="0ee18-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="0ee18-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0ee18-112">Místní koncový bod pro kanál.</span><span class="sxs-lookup"><span data-stu-id="0ee18-112">The local endpoint for the channel.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="0ee18-113">ref</span><span class="sxs-lookup"><span data-stu-id="0ee18-113">ref</span></span>  
 <span data-ttu-id="0ee18-114">Datový typ: koncový bod</span><span class="sxs-lookup"><span data-stu-id="0ee18-114">Data type: Endpoint</span></span>  
  
 <span data-ttu-id="0ee18-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="0ee18-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0ee18-116">Odkaz na koncový bod kanálu se připojí k.</span><span class="sxs-lookup"><span data-stu-id="0ee18-116">A reference to the endpoint the channel connects to.</span></span>  
  
### <a name="remoteaddress"></a><span data-ttu-id="0ee18-117">RemoteAddress</span><span class="sxs-lookup"><span data-stu-id="0ee18-117">RemoteAddress</span></span>  
 <span data-ttu-id="0ee18-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="0ee18-118">Data type: string</span></span>  
  
 <span data-ttu-id="0ee18-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="0ee18-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0ee18-120">Vzdálená adresa spojená s kanálem.</span><span class="sxs-lookup"><span data-stu-id="0ee18-120">The remote address associated with the channel.</span></span>  
  
### <a name="sessionid"></a><span data-ttu-id="0ee18-121">SessionId</span><span class="sxs-lookup"><span data-stu-id="0ee18-121">SessionId</span></span>  
 <span data-ttu-id="0ee18-122">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="0ee18-122">Data type: string</span></span>  
  
 <span data-ttu-id="0ee18-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="0ee18-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0ee18-124">Aktuální relace Id, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="0ee18-124">The current session Id, if any.</span></span>  
  
### <a name="type"></a><span data-ttu-id="0ee18-125">Typ</span><span class="sxs-lookup"><span data-stu-id="0ee18-125">Type</span></span>  
 <span data-ttu-id="0ee18-126">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="0ee18-126">Data type: string</span></span>  
  
 <span data-ttu-id="0ee18-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="0ee18-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="0ee18-128">Typ kanálu.</span><span class="sxs-lookup"><span data-stu-id="0ee18-128">The type of the channel.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ee18-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0ee18-129">Requirements</span></span>  
  
|<span data-ttu-id="0ee18-130">MOF</span><span class="sxs-lookup"><span data-stu-id="0ee18-130">MOF</span></span>|<span data-ttu-id="0ee18-131">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="0ee18-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="0ee18-132">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="0ee18-132">Namespace</span></span>|<span data-ttu-id="0ee18-133">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="0ee18-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0ee18-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="0ee18-134">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ChannelBase>
