---
title: TcpConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 19acfba3-c057-4dbc-bac7-8674d7844d83
ms.openlocfilehash: 6fa68eed241edaea40b66c31240a4201e05779f4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2019
ms.locfileid: "59975339"
---
# <a name="tcpconnectionpoolsettings"></a><span data-ttu-id="b0bee-102">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="b0bee-102">TcpConnectionPoolSettings</span></span>
<span data-ttu-id="b0bee-103">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="b0bee-103">TcpConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0bee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b0bee-104">Syntax</span></span>  
  
```csharp
class TcpConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="b0bee-105">Metody</span><span class="sxs-lookup"><span data-stu-id="b0bee-105">Methods</span></span>  
 <span data-ttu-id="b0bee-106">Třída TcpConnectionPoolSettings nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="b0bee-106">The TcpConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b0bee-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="b0bee-107">Properties</span></span>  
 <span data-ttu-id="b0bee-108">Třída TcpConnectionPoolSettings má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="b0bee-108">The TcpConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="b0bee-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="b0bee-109">GroupName</span></span>  
 <span data-ttu-id="b0bee-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="b0bee-110">Data type: string</span></span>  
  
 <span data-ttu-id="b0bee-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="b0bee-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b0bee-112">Název skupiny fondu připojení používaný prvkem vazby.</span><span class="sxs-lookup"><span data-stu-id="b0bee-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="b0bee-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="b0bee-113">IdleTimeout</span></span>  
 <span data-ttu-id="b0bee-114">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="b0bee-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="b0bee-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="b0bee-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b0bee-116">Maximální doba, kterou může být připojení nečinné, než je odpojeno.</span><span class="sxs-lookup"><span data-stu-id="b0bee-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="leasetimeout"></a><span data-ttu-id="b0bee-117">LeaseTimeout</span><span class="sxs-lookup"><span data-stu-id="b0bee-117">LeaseTimeout</span></span>  
 <span data-ttu-id="b0bee-118">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="b0bee-118">Data type: datetime</span></span>  
  
 <span data-ttu-id="b0bee-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="b0bee-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b0bee-120">Maximální doba operace zapůjčení před vypršením časového limitu.</span><span class="sxs-lookup"><span data-stu-id="b0bee-120">The maximum time for the lease operation to complete before timing out.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="b0bee-121">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="b0bee-121">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="b0bee-122">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="b0bee-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="b0bee-123">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="b0bee-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b0bee-124">Maximální počet odchozích připojení pro každý koncový bod.</span><span class="sxs-lookup"><span data-stu-id="b0bee-124">The maximum outbound connections for each endpoint.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0bee-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b0bee-125">Requirements</span></span>  
  
|<span data-ttu-id="b0bee-126">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="b0bee-126">MOF</span></span>|<span data-ttu-id="b0bee-127">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="b0bee-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b0bee-128">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="b0bee-128">Namespace</span></span>|<span data-ttu-id="b0bee-129">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b0bee-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b0bee-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b0bee-130">See also</span></span>

- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings>
