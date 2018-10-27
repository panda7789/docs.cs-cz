---
title: TcpConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 19acfba3-c057-4dbc-bac7-8674d7844d83
ms.openlocfilehash: f9e1c043579f632f16a7cf36bf34c2467a743e47
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50189560"
---
# <a name="tcpconnectionpoolsettings"></a><span data-ttu-id="b8cdb-102">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="b8cdb-102">TcpConnectionPoolSettings</span></span>
<span data-ttu-id="b8cdb-103">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="b8cdb-103">TcpConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8cdb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8cdb-104">Syntax</span></span>  
  
```csharp
class TcpConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="b8cdb-105">Metody</span><span class="sxs-lookup"><span data-stu-id="b8cdb-105">Methods</span></span>  
 <span data-ttu-id="b8cdb-106">Třída TcpConnectionPoolSettings nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="b8cdb-106">The TcpConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b8cdb-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="b8cdb-107">Properties</span></span>  
 <span data-ttu-id="b8cdb-108">Třída TcpConnectionPoolSettings má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="b8cdb-108">The TcpConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="b8cdb-109">Název skupiny</span><span class="sxs-lookup"><span data-stu-id="b8cdb-109">GroupName</span></span>  
 <span data-ttu-id="b8cdb-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="b8cdb-110">Data type: string</span></span>  
  
 <span data-ttu-id="b8cdb-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="b8cdb-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b8cdb-112">Název skupiny fondu připojení používaný prvkem vazby.</span><span class="sxs-lookup"><span data-stu-id="b8cdb-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="b8cdb-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="b8cdb-113">IdleTimeout</span></span>  
 <span data-ttu-id="b8cdb-114">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="b8cdb-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="b8cdb-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="b8cdb-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b8cdb-116">Maximální doba, kterou může být připojení nečinné, než je odpojeno.</span><span class="sxs-lookup"><span data-stu-id="b8cdb-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="b8cdb-117">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="b8cdb-117">LeaseTimeout</span></span>  
 <span data-ttu-id="b8cdb-118">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="b8cdb-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="b8cdb-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="b8cdb-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b8cdb-120">Maximální doba operace zapůjčení před vypršením časového limitu.</span><span class="sxs-lookup"><span data-stu-id="b8cdb-120">The maximum time for the lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="b8cdb-121">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="b8cdb-121">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="b8cdb-122">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="b8cdb-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="b8cdb-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="b8cdb-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b8cdb-124">Maximální počet odchozích připojení pro každý koncový bod.</span><span class="sxs-lookup"><span data-stu-id="b8cdb-124">The maximum outbound connections for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8cdb-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b8cdb-125">Requirements</span></span>  
  
|<span data-ttu-id="b8cdb-126">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="b8cdb-126">MOF</span></span>|<span data-ttu-id="b8cdb-127">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="b8cdb-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b8cdb-128">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="b8cdb-128">Namespace</span></span>|<span data-ttu-id="b8cdb-129">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b8cdb-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b8cdb-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="b8cdb-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
