---
title: Třída Channel
ms.date: 03/30/2017
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
ms.openlocfilehash: f60a3946617b0994db1ba9e9ddf43be863be81f9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61964078"
---
# <a name="channel-class"></a><span data-ttu-id="76a33-102">Třída Channel</span><span class="sxs-lookup"><span data-stu-id="76a33-102">Channel class</span></span>
<span data-ttu-id="76a33-103">Kanál</span><span class="sxs-lookup"><span data-stu-id="76a33-103">Channel</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76a33-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="76a33-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="76a33-105">Metody</span><span class="sxs-lookup"><span data-stu-id="76a33-105">Methods</span></span>  
 <span data-ttu-id="76a33-106">Třída kanálu nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="76a33-106">The Channel class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="76a33-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="76a33-107">Properties</span></span>  
 <span data-ttu-id="76a33-108">Třída kanálu má následující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="76a33-108">The Channel class has the following properties.</span></span>  
  
### <a name="localaddress"></a><span data-ttu-id="76a33-109">LocalAddress</span><span class="sxs-lookup"><span data-stu-id="76a33-109">LocalAddress</span></span>  
 <span data-ttu-id="76a33-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="76a33-110">Data type: string</span></span>  
  
 <span data-ttu-id="76a33-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="76a33-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="76a33-112">Místní koncový bod pro kanál.</span><span class="sxs-lookup"><span data-stu-id="76a33-112">The local endpoint for the channel.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="76a33-113">ref</span><span class="sxs-lookup"><span data-stu-id="76a33-113">ref</span></span>  
 <span data-ttu-id="76a33-114">Datový typ: Koncový bod</span><span class="sxs-lookup"><span data-stu-id="76a33-114">Data type: Endpoint</span></span>  
  
 <span data-ttu-id="76a33-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="76a33-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="76a33-116">Odkaz na koncový bod kanálu se připojí k.</span><span class="sxs-lookup"><span data-stu-id="76a33-116">A reference to the endpoint the channel connects to.</span></span>  
  
### <a name="remoteaddress"></a><span data-ttu-id="76a33-117">RemoteAddress</span><span class="sxs-lookup"><span data-stu-id="76a33-117">RemoteAddress</span></span>  
 <span data-ttu-id="76a33-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="76a33-118">Data type: string</span></span>  
  
 <span data-ttu-id="76a33-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="76a33-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="76a33-120">Vzdálená adresa připojená ke kanálu.</span><span class="sxs-lookup"><span data-stu-id="76a33-120">The remote address associated with the channel.</span></span>  
  
### <a name="sessionid"></a><span data-ttu-id="76a33-121">SessionId</span><span class="sxs-lookup"><span data-stu-id="76a33-121">SessionId</span></span>  
 <span data-ttu-id="76a33-122">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="76a33-122">Data type: string</span></span>  
  
 <span data-ttu-id="76a33-123">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="76a33-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="76a33-124">Id aktuálního procesu, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="76a33-124">The current session Id, if any.</span></span>  
  
### <a name="type"></a><span data-ttu-id="76a33-125">Type</span><span class="sxs-lookup"><span data-stu-id="76a33-125">Type</span></span>  
 <span data-ttu-id="76a33-126">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="76a33-126">Data type: string</span></span>  
  
 <span data-ttu-id="76a33-127">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="76a33-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="76a33-128">Typ kanálu.</span><span class="sxs-lookup"><span data-stu-id="76a33-128">The type of the channel.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76a33-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="76a33-129">Requirements</span></span>  
  
|<span data-ttu-id="76a33-130">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="76a33-130">MOF</span></span>|<span data-ttu-id="76a33-131">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="76a33-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="76a33-132">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="76a33-132">Namespace</span></span>|<span data-ttu-id="76a33-133">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="76a33-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="76a33-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="76a33-134">See also</span></span>

- <xref:System.ServiceModel.Channels.ChannelBase>
