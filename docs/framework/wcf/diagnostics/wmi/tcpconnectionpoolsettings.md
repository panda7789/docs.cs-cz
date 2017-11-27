---
title: TcpConnectionPoolSettings
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 19acfba3-c057-4dbc-bac7-8674d7844d83
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5038d093333eca9ca191c3ecae4cfa889d723276
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="tcpconnectionpoolsettings"></a><span data-ttu-id="74478-102">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="74478-102">TcpConnectionPoolSettings</span></span>
<span data-ttu-id="74478-103">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="74478-103">TcpConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74478-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="74478-104">Syntax</span></span>  
  
```  
class TcpConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="74478-105">Metody</span><span class="sxs-lookup"><span data-stu-id="74478-105">Methods</span></span>  
 <span data-ttu-id="74478-106">Třída TcpConnectionPoolSettings nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="74478-106">The TcpConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="74478-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="74478-107">Properties</span></span>  
 <span data-ttu-id="74478-108">Třída TcpConnectionPoolSettings má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="74478-108">The TcpConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="74478-109">Název skupiny</span><span class="sxs-lookup"><span data-stu-id="74478-109">GroupName</span></span>  
 <span data-ttu-id="74478-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="74478-110">Data type: string</span></span>  
  
 <span data-ttu-id="74478-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="74478-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="74478-112">Název skupiny fondu připojení používá prvku vazby.</span><span class="sxs-lookup"><span data-stu-id="74478-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="74478-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="74478-113">IdleTimeout</span></span>  
 <span data-ttu-id="74478-114">Datový typ: data a času</span><span class="sxs-lookup"><span data-stu-id="74478-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="74478-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="74478-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="74478-116">Maximální čas, kdy může být připojení nečinnosti, než dojde k odpojení.</span><span class="sxs-lookup"><span data-stu-id="74478-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="74478-117">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="74478-117">LeaseTimeout</span></span>  
 <span data-ttu-id="74478-118">Datový typ: data a času</span><span class="sxs-lookup"><span data-stu-id="74478-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="74478-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="74478-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="74478-120">Maximální dobu pro dokončení před vypršením časového limitu operace zapůjčení.</span><span class="sxs-lookup"><span data-stu-id="74478-120">The maximum time for the lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="74478-121">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="74478-121">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="74478-122">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="74478-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="74478-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="74478-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="74478-124">Maximální počet odchozí připojení pro každý koncový bod.</span><span class="sxs-lookup"><span data-stu-id="74478-124">The maximum outbound connections for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74478-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="74478-125">Requirements</span></span>  
  
|<span data-ttu-id="74478-126">MOF</span><span class="sxs-lookup"><span data-stu-id="74478-126">MOF</span></span>|<span data-ttu-id="74478-127">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="74478-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="74478-128">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="74478-128">Namespace</span></span>|<span data-ttu-id="74478-129">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="74478-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="74478-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="74478-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
