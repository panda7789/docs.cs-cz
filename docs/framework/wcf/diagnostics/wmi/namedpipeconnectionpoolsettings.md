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
ms.workload: dotnet
ms.openlocfilehash: 601ccd5589da759606365570538e0df902e4fbe2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="namedpipeconnectionpoolsettings"></a><span data-ttu-id="e7791-102">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="e7791-102">NamedPipeConnectionPoolSettings</span></span>
<span data-ttu-id="e7791-103">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="e7791-103">NamedPipeConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7791-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e7791-104">Syntax</span></span>  
  
```  
class NamedPipeConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e7791-105">Metody</span><span class="sxs-lookup"><span data-stu-id="e7791-105">Methods</span></span>  
 <span data-ttu-id="e7791-106">Třída NamedPipeConnectionPoolSettings nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="e7791-106">The NamedPipeConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e7791-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e7791-107">Properties</span></span>  
 <span data-ttu-id="e7791-108">Třída NamedPipeConnectionPoolSettings má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="e7791-108">The NamedPipeConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="e7791-109">Název skupiny</span><span class="sxs-lookup"><span data-stu-id="e7791-109">GroupName</span></span>  
 <span data-ttu-id="e7791-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="e7791-110">Data type: string</span></span>  
  
 <span data-ttu-id="e7791-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e7791-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e7791-112">Název skupiny fondu připojení používá prvku vazby.</span><span class="sxs-lookup"><span data-stu-id="e7791-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="e7791-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="e7791-113">IdleTimeout</span></span>  
 <span data-ttu-id="e7791-114">Datový typ: data a času</span><span class="sxs-lookup"><span data-stu-id="e7791-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="e7791-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e7791-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e7791-116">Maximální čas, kdy může být připojení nečinnosti, než dojde k odpojení.</span><span class="sxs-lookup"><span data-stu-id="e7791-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="e7791-117">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="e7791-117">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="e7791-118">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="e7791-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="e7791-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e7791-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e7791-120">Maximální počet odchozí připojení pro každý koncový bod na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="e7791-120">The maximum number of outbound connections for each endpoint on the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e7791-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e7791-121">Requirements</span></span>  
  
|<span data-ttu-id="e7791-122">MOF</span><span class="sxs-lookup"><span data-stu-id="e7791-122">MOF</span></span>|<span data-ttu-id="e7791-123">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="e7791-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e7791-124">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="e7791-124">Namespace</span></span>|<span data-ttu-id="e7791-125">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e7791-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e7791-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="e7791-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
