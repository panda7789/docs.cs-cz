---
title: PeerSecuritySettings
ms.date: 03/30/2017
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
author: BrucePerlerMS
ms.openlocfilehash: c74ee82d7aa3a23f0ee6a69185ad45857c31bb0b
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47087876"
---
# <a name="peersecuritysettings"></a><span data-ttu-id="27e7a-102">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="27e7a-102">PeerSecuritySettings</span></span>
<span data-ttu-id="27e7a-103">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="27e7a-103">PeerSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27e7a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="27e7a-104">Syntax</span></span>  
  
```  
class PeerSecuritySettings  
{  
  string Mode;  
  PeerTransportSecuritySettings Transport;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="27e7a-105">Metody</span><span class="sxs-lookup"><span data-stu-id="27e7a-105">Methods</span></span>  
 <span data-ttu-id="27e7a-106">Třída PeerSecuritySettings nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="27e7a-106">The PeerSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="27e7a-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="27e7a-107">Properties</span></span>  
 <span data-ttu-id="27e7a-108">Třída PeerSecuritySettings má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="27e7a-108">The PeerSecuritySettings class has the following properties:</span></span>  
  
### <a name="mode"></a><span data-ttu-id="27e7a-109">Režim</span><span class="sxs-lookup"><span data-stu-id="27e7a-109">Mode</span></span>  
 <span data-ttu-id="27e7a-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="27e7a-110">Data type: string</span></span>  
  
 <span data-ttu-id="27e7a-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="27e7a-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="27e7a-112">Určuje, zda zpráva úrovni a koncovým bodem nakonfigurovaným s vazbou používají zabezpečení na úrovni přenosu.</span><span class="sxs-lookup"><span data-stu-id="27e7a-112">Whether message-level and transport-level security are used by an endpoint configured with the binding.</span></span>  
  
### <a name="transport"></a><span data-ttu-id="27e7a-113">Přenos</span><span class="sxs-lookup"><span data-stu-id="27e7a-113">Transport</span></span>  
 <span data-ttu-id="27e7a-114">Datový typ: třída PeerTransportSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="27e7a-114">Data type: PeerTransportSecuritySettings</span></span>  
  
 <span data-ttu-id="27e7a-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="27e7a-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="27e7a-116">Nastavení zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="27e7a-116">Transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27e7a-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="27e7a-117">Requirements</span></span>  
  
|<span data-ttu-id="27e7a-118">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="27e7a-118">MOF</span></span>|<span data-ttu-id="27e7a-119">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="27e7a-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="27e7a-120">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="27e7a-120">Namespace</span></span>|<span data-ttu-id="27e7a-121">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="27e7a-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="27e7a-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="27e7a-122">See Also</span></span>  
 <xref:System.ServiceModel.PeerSecuritySettings>
