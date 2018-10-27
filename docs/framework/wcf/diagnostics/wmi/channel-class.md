---
title: Třída Channel
ms.date: 03/30/2017
ms.assetid: d9fae2ca-209c-4341-a0f5-6b79d1a67776
ms.openlocfilehash: 108d5f8e3cd092863dbd48e2bb9d180798b091a4
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50047368"
---
# <a name="channel-class"></a><span data-ttu-id="30091-102">Třída Channel</span><span class="sxs-lookup"><span data-stu-id="30091-102">Channel class</span></span>
<span data-ttu-id="30091-103">Kanál</span><span class="sxs-lookup"><span data-stu-id="30091-103">Channel</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30091-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="30091-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="30091-105">Metody</span><span class="sxs-lookup"><span data-stu-id="30091-105">Methods</span></span>  
 <span data-ttu-id="30091-106">Třída kanálu nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="30091-106">The Channel class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="30091-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="30091-107">Properties</span></span>  
 <span data-ttu-id="30091-108">Třída kanálu má následující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="30091-108">The Channel class has the following properties.</span></span>  
  
### <a name="localaddress"></a><span data-ttu-id="30091-109">LocalAddress</span><span class="sxs-lookup"><span data-stu-id="30091-109">LocalAddress</span></span>  
 <span data-ttu-id="30091-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="30091-110">Data type: string</span></span>  
  
 <span data-ttu-id="30091-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="30091-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="30091-112">Místní koncový bod pro kanál.</span><span class="sxs-lookup"><span data-stu-id="30091-112">The local endpoint for the channel.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="30091-113">ref</span><span class="sxs-lookup"><span data-stu-id="30091-113">ref</span></span>  
 <span data-ttu-id="30091-114">Datový typ: koncového bodu</span><span class="sxs-lookup"><span data-stu-id="30091-114">Data type: Endpoint</span></span>  
  
 <span data-ttu-id="30091-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="30091-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="30091-116">Odkaz na koncový bod kanálu se připojí k.</span><span class="sxs-lookup"><span data-stu-id="30091-116">A reference to the endpoint the channel connects to.</span></span>  
  
### <a name="remoteaddress"></a><span data-ttu-id="30091-117">RemoteAddress</span><span class="sxs-lookup"><span data-stu-id="30091-117">RemoteAddress</span></span>  
 <span data-ttu-id="30091-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="30091-118">Data type: string</span></span>  
  
 <span data-ttu-id="30091-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="30091-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="30091-120">Vzdálená adresa připojená ke kanálu.</span><span class="sxs-lookup"><span data-stu-id="30091-120">The remote address associated with the channel.</span></span>  
  
### <a name="sessionid"></a><span data-ttu-id="30091-121">SessionId</span><span class="sxs-lookup"><span data-stu-id="30091-121">SessionId</span></span>  
 <span data-ttu-id="30091-122">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="30091-122">Data type: string</span></span>  
  
 <span data-ttu-id="30091-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="30091-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="30091-124">Id aktuálního procesu, pokud existuje.</span><span class="sxs-lookup"><span data-stu-id="30091-124">The current session Id, if any.</span></span>  
  
### <a name="type"></a><span data-ttu-id="30091-125">Typ</span><span class="sxs-lookup"><span data-stu-id="30091-125">Type</span></span>  
 <span data-ttu-id="30091-126">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="30091-126">Data type: string</span></span>  
  
 <span data-ttu-id="30091-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="30091-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="30091-128">Typ kanálu.</span><span class="sxs-lookup"><span data-stu-id="30091-128">The type of the channel.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30091-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="30091-129">Requirements</span></span>  
  
|<span data-ttu-id="30091-130">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="30091-130">MOF</span></span>|<span data-ttu-id="30091-131">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="30091-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="30091-132">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="30091-132">Namespace</span></span>|<span data-ttu-id="30091-133">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="30091-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="30091-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="30091-134">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ChannelBase>
