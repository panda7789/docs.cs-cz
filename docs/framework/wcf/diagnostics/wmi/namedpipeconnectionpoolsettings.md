---
title: NamedPipeConnectionPoolSettings
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 079bccb8-54b5-4436-a43d-5567763f72ce
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 18740c4c87aaeafcd0a28991376e0c45fe688223
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="namedpipeconnectionpoolsettings"></a><span data-ttu-id="d6d2d-102">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="d6d2d-102">NamedPipeConnectionPoolSettings</span></span>
<span data-ttu-id="d6d2d-103">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="d6d2d-103">NamedPipeConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6d2d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6d2d-104">Syntax</span></span>  
  
```  
class NamedPipeConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="d6d2d-105">Metody</span><span class="sxs-lookup"><span data-stu-id="d6d2d-105">Methods</span></span>  
 <span data-ttu-id="d6d2d-106">Třída NamedPipeConnectionPoolSettings nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="d6d2d-106">The NamedPipeConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d6d2d-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="d6d2d-107">Properties</span></span>  
 <span data-ttu-id="d6d2d-108">Třída NamedPipeConnectionPoolSettings má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="d6d2d-108">The NamedPipeConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="d6d2d-109">Název skupiny</span><span class="sxs-lookup"><span data-stu-id="d6d2d-109">GroupName</span></span>  
 <span data-ttu-id="d6d2d-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="d6d2d-110">Data type: string</span></span>  
  
 <span data-ttu-id="d6d2d-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d6d2d-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d6d2d-112">Název skupiny fondu připojení používá prvku vazby.</span><span class="sxs-lookup"><span data-stu-id="d6d2d-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="d6d2d-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="d6d2d-113">IdleTimeout</span></span>  
 <span data-ttu-id="d6d2d-114">Datový typ: data a času</span><span class="sxs-lookup"><span data-stu-id="d6d2d-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="d6d2d-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d6d2d-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d6d2d-116">Maximální čas, kdy může být připojení nečinnosti, než dojde k odpojení.</span><span class="sxs-lookup"><span data-stu-id="d6d2d-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="d6d2d-117">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="d6d2d-117">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="d6d2d-118">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="d6d2d-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="d6d2d-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d6d2d-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d6d2d-120">Maximální počet odchozí připojení pro každý koncový bod na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="d6d2d-120">The maximum number of outbound connections for each endpoint on the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6d2d-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d6d2d-121">Requirements</span></span>  
  
|<span data-ttu-id="d6d2d-122">MOF</span><span class="sxs-lookup"><span data-stu-id="d6d2d-122">MOF</span></span>|<span data-ttu-id="d6d2d-123">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="d6d2d-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="d6d2d-124">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="d6d2d-124">Namespace</span></span>|<span data-ttu-id="d6d2d-125">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d6d2d-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d6d2d-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="d6d2d-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
