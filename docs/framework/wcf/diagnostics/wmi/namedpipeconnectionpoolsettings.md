---
title: NamedPipeConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 079bccb8-54b5-4436-a43d-5567763f72ce
ms.openlocfilehash: 3548a1f19672a98ad0fc81eec15d5be29e5170bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486279"
---
# <a name="namedpipeconnectionpoolsettings"></a><span data-ttu-id="929ec-102">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="929ec-102">NamedPipeConnectionPoolSettings</span></span>
<span data-ttu-id="929ec-103">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="929ec-103">NamedPipeConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="929ec-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="929ec-104">Syntax</span></span>  
  
```  
class NamedPipeConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="929ec-105">Metody</span><span class="sxs-lookup"><span data-stu-id="929ec-105">Methods</span></span>  
 <span data-ttu-id="929ec-106">Třída NamedPipeConnectionPoolSettings nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="929ec-106">The NamedPipeConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="929ec-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="929ec-107">Properties</span></span>  
 <span data-ttu-id="929ec-108">Třída NamedPipeConnectionPoolSettings má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="929ec-108">The NamedPipeConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="929ec-109">Název skupiny</span><span class="sxs-lookup"><span data-stu-id="929ec-109">GroupName</span></span>  
 <span data-ttu-id="929ec-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="929ec-110">Data type: string</span></span>  
  
 <span data-ttu-id="929ec-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="929ec-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="929ec-112">Název skupiny fondu připojení používá prvku vazby.</span><span class="sxs-lookup"><span data-stu-id="929ec-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="929ec-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="929ec-113">IdleTimeout</span></span>  
 <span data-ttu-id="929ec-114">Datový typ: data a času</span><span class="sxs-lookup"><span data-stu-id="929ec-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="929ec-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="929ec-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="929ec-116">Maximální čas, kdy může být připojení nečinnosti, než dojde k odpojení.</span><span class="sxs-lookup"><span data-stu-id="929ec-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="929ec-117">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="929ec-117">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="929ec-118">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="929ec-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="929ec-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="929ec-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="929ec-120">Maximální počet odchozí připojení pro každý koncový bod na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="929ec-120">The maximum number of outbound connections for each endpoint on the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="929ec-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="929ec-121">Requirements</span></span>  
  
|<span data-ttu-id="929ec-122">MOF</span><span class="sxs-lookup"><span data-stu-id="929ec-122">MOF</span></span>|<span data-ttu-id="929ec-123">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="929ec-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="929ec-124">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="929ec-124">Namespace</span></span>|<span data-ttu-id="929ec-125">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="929ec-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="929ec-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="929ec-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
