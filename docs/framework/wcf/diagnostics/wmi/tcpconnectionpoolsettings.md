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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eaec1b7d179810faaba016cfa0c5eb7e6c950ab6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="tcpconnectionpoolsettings"></a><span data-ttu-id="abc44-102">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="abc44-102">TcpConnectionPoolSettings</span></span>
<span data-ttu-id="abc44-103">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="abc44-103">TcpConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="abc44-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="abc44-104">Syntax</span></span>  
  
```  
class TcpConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="abc44-105">Metody</span><span class="sxs-lookup"><span data-stu-id="abc44-105">Methods</span></span>  
 <span data-ttu-id="abc44-106">Třída TcpConnectionPoolSettings nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="abc44-106">The TcpConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="abc44-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="abc44-107">Properties</span></span>  
 <span data-ttu-id="abc44-108">Třída TcpConnectionPoolSettings má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="abc44-108">The TcpConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="abc44-109">Název skupiny</span><span class="sxs-lookup"><span data-stu-id="abc44-109">GroupName</span></span>  
 <span data-ttu-id="abc44-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="abc44-110">Data type: string</span></span>  
  
 <span data-ttu-id="abc44-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="abc44-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="abc44-112">Název skupiny fondu připojení používá prvku vazby.</span><span class="sxs-lookup"><span data-stu-id="abc44-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="abc44-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="abc44-113">IdleTimeout</span></span>  
 <span data-ttu-id="abc44-114">Datový typ: data a času</span><span class="sxs-lookup"><span data-stu-id="abc44-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="abc44-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="abc44-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="abc44-116">Maximální čas, kdy může být připojení nečinnosti, než dojde k odpojení.</span><span class="sxs-lookup"><span data-stu-id="abc44-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="abc44-117">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="abc44-117">LeaseTimeout</span></span>  
 <span data-ttu-id="abc44-118">Datový typ: data a času</span><span class="sxs-lookup"><span data-stu-id="abc44-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="abc44-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="abc44-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="abc44-120">Maximální dobu pro dokončení před vypršením časového limitu operace zapůjčení.</span><span class="sxs-lookup"><span data-stu-id="abc44-120">The maximum time for the lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="abc44-121">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="abc44-121">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="abc44-122">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="abc44-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="abc44-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="abc44-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="abc44-124">Maximální počet odchozí připojení pro každý koncový bod.</span><span class="sxs-lookup"><span data-stu-id="abc44-124">The maximum outbound connections for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="abc44-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="abc44-125">Requirements</span></span>  
  
|<span data-ttu-id="abc44-126">MOF</span><span class="sxs-lookup"><span data-stu-id="abc44-126">MOF</span></span>|<span data-ttu-id="abc44-127">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="abc44-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="abc44-128">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="abc44-128">Namespace</span></span>|<span data-ttu-id="abc44-129">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="abc44-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="abc44-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="abc44-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
