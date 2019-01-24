---
title: NamedPipeConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 079bccb8-54b5-4436-a43d-5567763f72ce
ms.openlocfilehash: 3dddfa878e3cb5bd89fb76009d0dba530debb297
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54725074"
---
# <a name="namedpipeconnectionpoolsettings"></a><span data-ttu-id="32bb5-102">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="32bb5-102">NamedPipeConnectionPoolSettings</span></span>
<span data-ttu-id="32bb5-103">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="32bb5-103">NamedPipeConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32bb5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="32bb5-104">Syntax</span></span>  
  
```csharp
class NamedPipeConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="32bb5-105">Metody</span><span class="sxs-lookup"><span data-stu-id="32bb5-105">Methods</span></span>  
 <span data-ttu-id="32bb5-106">Třída NamedPipeConnectionPoolSettings nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="32bb5-106">The NamedPipeConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="32bb5-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="32bb5-107">Properties</span></span>  
 <span data-ttu-id="32bb5-108">Třída NamedPipeConnectionPoolSettings má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="32bb5-108">The NamedPipeConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="32bb5-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="32bb5-109">GroupName</span></span>  
 <span data-ttu-id="32bb5-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="32bb5-110">Data type: string</span></span>  
  
 <span data-ttu-id="32bb5-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="32bb5-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="32bb5-112">Název skupiny fondu připojení používaný prvkem vazby.</span><span class="sxs-lookup"><span data-stu-id="32bb5-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="32bb5-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="32bb5-113">IdleTimeout</span></span>  
 <span data-ttu-id="32bb5-114">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="32bb5-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="32bb5-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="32bb5-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="32bb5-116">Maximální doba, kterou může být připojení nečinné, než je odpojeno.</span><span class="sxs-lookup"><span data-stu-id="32bb5-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="32bb5-117">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="32bb5-117">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="32bb5-118">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="32bb5-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="32bb5-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="32bb5-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="32bb5-120">Maximální počet odchozích připojení pro každý koncový bod na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="32bb5-120">The maximum number of outbound connections for each endpoint on the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32bb5-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="32bb5-121">Requirements</span></span>  
  
|<span data-ttu-id="32bb5-122">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="32bb5-122">MOF</span></span>|<span data-ttu-id="32bb5-123">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="32bb5-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="32bb5-124">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="32bb5-124">Namespace</span></span>|<span data-ttu-id="32bb5-125">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="32bb5-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="32bb5-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="32bb5-126">See also</span></span>
- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
