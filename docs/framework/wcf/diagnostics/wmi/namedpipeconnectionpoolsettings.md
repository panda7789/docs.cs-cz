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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: cf9c39334289cb30d1a01917c0be37da02fcdc5b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="namedpipeconnectionpoolsettings"></a><span data-ttu-id="12f56-102">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="12f56-102">NamedPipeConnectionPoolSettings</span></span>
<span data-ttu-id="12f56-103">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="12f56-103">NamedPipeConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12f56-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="12f56-104">Syntax</span></span>  
  
```  
class NamedPipeConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="12f56-105">Metody</span><span class="sxs-lookup"><span data-stu-id="12f56-105">Methods</span></span>  
 <span data-ttu-id="12f56-106">Třída NamedPipeConnectionPoolSettings nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="12f56-106">The NamedPipeConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="12f56-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="12f56-107">Properties</span></span>  
 <span data-ttu-id="12f56-108">Třída NamedPipeConnectionPoolSettings má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="12f56-108">The NamedPipeConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="12f56-109">Název skupiny</span><span class="sxs-lookup"><span data-stu-id="12f56-109">GroupName</span></span>  
 <span data-ttu-id="12f56-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="12f56-110">Data type: string</span></span>  
  
 <span data-ttu-id="12f56-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="12f56-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="12f56-112">Název skupiny fondu připojení používá prvku vazby.</span><span class="sxs-lookup"><span data-stu-id="12f56-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="12f56-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="12f56-113">IdleTimeout</span></span>  
 <span data-ttu-id="12f56-114">Datový typ: data a času</span><span class="sxs-lookup"><span data-stu-id="12f56-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="12f56-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="12f56-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="12f56-116">Maximální čas, kdy může být připojení nečinnosti, než dojde k odpojení.</span><span class="sxs-lookup"><span data-stu-id="12f56-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="12f56-117">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="12f56-117">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="12f56-118">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="12f56-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="12f56-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="12f56-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="12f56-120">Maximální počet odchozí připojení pro každý koncový bod na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="12f56-120">The maximum number of outbound connections for each endpoint on the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12f56-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="12f56-121">Requirements</span></span>  
  
|<span data-ttu-id="12f56-122">MOF</span><span class="sxs-lookup"><span data-stu-id="12f56-122">MOF</span></span>|<span data-ttu-id="12f56-123">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="12f56-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="12f56-124">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="12f56-124">Namespace</span></span>|<span data-ttu-id="12f56-125">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="12f56-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="12f56-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="12f56-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
