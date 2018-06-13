---
title: TcpConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 19acfba3-c057-4dbc-bac7-8674d7844d83
ms.openlocfilehash: 4a30ad3ddfef5d39942345b0e0d5274eeff8e596
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485918"
---
# <a name="tcpconnectionpoolsettings"></a><span data-ttu-id="d2eca-102">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="d2eca-102">TcpConnectionPoolSettings</span></span>
<span data-ttu-id="d2eca-103">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="d2eca-103">TcpConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2eca-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d2eca-104">Syntax</span></span>  
  
```  
class TcpConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="d2eca-105">Metody</span><span class="sxs-lookup"><span data-stu-id="d2eca-105">Methods</span></span>  
 <span data-ttu-id="d2eca-106">Třída TcpConnectionPoolSettings nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="d2eca-106">The TcpConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d2eca-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="d2eca-107">Properties</span></span>  
 <span data-ttu-id="d2eca-108">Třída TcpConnectionPoolSettings má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="d2eca-108">The TcpConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="d2eca-109">Název skupiny</span><span class="sxs-lookup"><span data-stu-id="d2eca-109">GroupName</span></span>  
 <span data-ttu-id="d2eca-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="d2eca-110">Data type: string</span></span>  
  
 <span data-ttu-id="d2eca-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d2eca-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d2eca-112">Název skupiny fondu připojení používá prvku vazby.</span><span class="sxs-lookup"><span data-stu-id="d2eca-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="d2eca-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="d2eca-113">IdleTimeout</span></span>  
 <span data-ttu-id="d2eca-114">Datový typ: data a času</span><span class="sxs-lookup"><span data-stu-id="d2eca-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="d2eca-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d2eca-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d2eca-116">Maximální čas, kdy může být připojení nečinnosti, než dojde k odpojení.</span><span class="sxs-lookup"><span data-stu-id="d2eca-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="d2eca-117">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="d2eca-117">LeaseTimeout</span></span>  
 <span data-ttu-id="d2eca-118">Datový typ: data a času</span><span class="sxs-lookup"><span data-stu-id="d2eca-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="d2eca-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d2eca-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d2eca-120">Maximální dobu pro dokončení před vypršením časového limitu operace zapůjčení.</span><span class="sxs-lookup"><span data-stu-id="d2eca-120">The maximum time for the lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="d2eca-121">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="d2eca-121">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="d2eca-122">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="d2eca-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="d2eca-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d2eca-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d2eca-124">Maximální počet odchozí připojení pro každý koncový bod.</span><span class="sxs-lookup"><span data-stu-id="d2eca-124">The maximum outbound connections for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2eca-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d2eca-125">Requirements</span></span>  
  
|<span data-ttu-id="d2eca-126">MOF</span><span class="sxs-lookup"><span data-stu-id="d2eca-126">MOF</span></span>|<span data-ttu-id="d2eca-127">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="d2eca-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="d2eca-128">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="d2eca-128">Namespace</span></span>|<span data-ttu-id="d2eca-129">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d2eca-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d2eca-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="d2eca-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
