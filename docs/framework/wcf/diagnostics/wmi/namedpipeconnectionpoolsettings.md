---
title: NamedPipeConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 079bccb8-54b5-4436-a43d-5567763f72ce
ms.openlocfilehash: 8c2d4bfc08a503a8d6eb0e8abf6f1e798b90bc83
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59773698"
---
# <a name="namedpipeconnectionpoolsettings"></a><span data-ttu-id="8d090-102">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="8d090-102">NamedPipeConnectionPoolSettings</span></span>
<span data-ttu-id="8d090-103">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="8d090-103">NamedPipeConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d090-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d090-104">Syntax</span></span>  
  
```csharp
class NamedPipeConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="8d090-105">Metody</span><span class="sxs-lookup"><span data-stu-id="8d090-105">Methods</span></span>  
 <span data-ttu-id="8d090-106">Třída NamedPipeConnectionPoolSettings nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="8d090-106">The NamedPipeConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="8d090-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="8d090-107">Properties</span></span>  
 <span data-ttu-id="8d090-108">Třída NamedPipeConnectionPoolSettings má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="8d090-108">The NamedPipeConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="8d090-109">GroupName</span><span class="sxs-lookup"><span data-stu-id="8d090-109">GroupName</span></span>  
 <span data-ttu-id="8d090-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="8d090-110">Data type: string</span></span>  
  
 <span data-ttu-id="8d090-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="8d090-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8d090-112">Název skupiny fondu připojení používaný prvkem vazby.</span><span class="sxs-lookup"><span data-stu-id="8d090-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="8d090-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="8d090-113">IdleTimeout</span></span>  
 <span data-ttu-id="8d090-114">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="8d090-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="8d090-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="8d090-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8d090-116">Maximální doba, kterou může být připojení nečinné, než je odpojeno.</span><span class="sxs-lookup"><span data-stu-id="8d090-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="8d090-117">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="8d090-117">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="8d090-118">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="8d090-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="8d090-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="8d090-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8d090-120">Maximální počet odchozích připojení pro každý koncový bod na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="8d090-120">The maximum number of outbound connections for each endpoint on the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d090-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8d090-121">Requirements</span></span>  
  
|<span data-ttu-id="8d090-122">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="8d090-122">MOF</span></span>|<span data-ttu-id="8d090-123">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="8d090-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="8d090-124">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="8d090-124">Namespace</span></span>|<span data-ttu-id="8d090-125">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="8d090-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8d090-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8d090-126">See also</span></span>

- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
