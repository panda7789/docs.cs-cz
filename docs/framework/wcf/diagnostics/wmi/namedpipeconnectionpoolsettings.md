---
title: NamedPipeConnectionPoolSettings
ms.date: 03/30/2017
ms.assetid: 079bccb8-54b5-4436-a43d-5567763f72ce
ms.openlocfilehash: 77d8403947d341ea2efcef98bbf166f94f75f31f
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188726"
---
# <a name="namedpipeconnectionpoolsettings"></a><span data-ttu-id="d8051-102">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="d8051-102">NamedPipeConnectionPoolSettings</span></span>
<span data-ttu-id="d8051-103">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="d8051-103">NamedPipeConnectionPoolSettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8051-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d8051-104">Syntax</span></span>  
  
```csharp
class NamedPipeConnectionPoolSettings  
{  
  string GroupName;  
  datetime IdleTimeout;  
  sint32 MaxOutboundConnectionsPerEndpoint;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="d8051-105">Metody</span><span class="sxs-lookup"><span data-stu-id="d8051-105">Methods</span></span>  
 <span data-ttu-id="d8051-106">Třída NamedPipeConnectionPoolSettings nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="d8051-106">The NamedPipeConnectionPoolSettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d8051-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="d8051-107">Properties</span></span>  
 <span data-ttu-id="d8051-108">Třída NamedPipeConnectionPoolSettings má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="d8051-108">The NamedPipeConnectionPoolSettings class has the following properties:</span></span>  
  
### <a name="groupname"></a><span data-ttu-id="d8051-109">Název skupiny</span><span class="sxs-lookup"><span data-stu-id="d8051-109">GroupName</span></span>  
 <span data-ttu-id="d8051-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="d8051-110">Data type: string</span></span>  
  
 <span data-ttu-id="d8051-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d8051-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d8051-112">Název skupiny fondu připojení používaný prvkem vazby.</span><span class="sxs-lookup"><span data-stu-id="d8051-112">The group name of the connection pool used by the binding element.</span></span>  
  
### <a name="idletimeout"></a><span data-ttu-id="d8051-113">IdleTimeout</span><span class="sxs-lookup"><span data-stu-id="d8051-113">IdleTimeout</span></span>  
 <span data-ttu-id="d8051-114">Datový typ: datum a čas</span><span class="sxs-lookup"><span data-stu-id="d8051-114">Data type: datetime</span></span>  
  
 <span data-ttu-id="d8051-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d8051-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d8051-116">Maximální doba, kterou může být připojení nečinné, než je odpojeno.</span><span class="sxs-lookup"><span data-stu-id="d8051-116">The maximum time the connection can be idle before being disconnected.</span></span>  
  
### <a name="maxoutboundconnectionsperendpoint"></a><span data-ttu-id="d8051-117">MaxOutboundConnectionsPerEndpoint</span><span class="sxs-lookup"><span data-stu-id="d8051-117">MaxOutboundConnectionsPerEndpoint</span></span>  
 <span data-ttu-id="d8051-118">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="d8051-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="d8051-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d8051-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d8051-120">Maximální počet odchozích připojení pro každý koncový bod na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="d8051-120">The maximum number of outbound connections for each endpoint on the client.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8051-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d8051-121">Requirements</span></span>  
  
|<span data-ttu-id="d8051-122">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="d8051-122">MOF</span></span>|<span data-ttu-id="d8051-123">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="d8051-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="d8051-124">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="d8051-124">Namespace</span></span>|<span data-ttu-id="d8051-125">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d8051-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d8051-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="d8051-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
