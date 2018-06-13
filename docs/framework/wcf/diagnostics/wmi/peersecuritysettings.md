---
title: PeerSecuritySettings
ms.date: 03/30/2017
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 58b372f26fee7dc180d75731fd4855db569c87c7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33484517"
---
# <a name="peersecuritysettings"></a><span data-ttu-id="1fdbc-102">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="1fdbc-102">PeerSecuritySettings</span></span>
<span data-ttu-id="1fdbc-103">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="1fdbc-103">PeerSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fdbc-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1fdbc-104">Syntax</span></span>  
  
```  
class PeerSecuritySettings  
{  
  string Mode;  
  PeerTransportSecuritySettings Transport;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="1fdbc-105">Metody</span><span class="sxs-lookup"><span data-stu-id="1fdbc-105">Methods</span></span>  
 <span data-ttu-id="1fdbc-106">Třída PeerSecuritySettings nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="1fdbc-106">The PeerSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="1fdbc-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="1fdbc-107">Properties</span></span>  
 <span data-ttu-id="1fdbc-108">Třída PeerSecuritySettings má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="1fdbc-108">The PeerSecuritySettings class has the following properties:</span></span>  
  
### <a name="mode"></a><span data-ttu-id="1fdbc-109">Režim</span><span class="sxs-lookup"><span data-stu-id="1fdbc-109">Mode</span></span>  
 <span data-ttu-id="1fdbc-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="1fdbc-110">Data type: string</span></span>  
  
 <span data-ttu-id="1fdbc-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="1fdbc-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1fdbc-112">Jestli úroveň zprávy a koncový bod nakonfigurovaná pomocí této vazby používá zabezpečení na úrovni přenosu.</span><span class="sxs-lookup"><span data-stu-id="1fdbc-112">Whether message-level and transport-level security are used by an endpoint configured with the binding.</span></span>  
  
### <a name="transport"></a><span data-ttu-id="1fdbc-113">Přenos</span><span class="sxs-lookup"><span data-stu-id="1fdbc-113">Transport</span></span>  
 <span data-ttu-id="1fdbc-114">Datový typ: třída PeerTransportSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="1fdbc-114">Data type: PeerTransportSecuritySettings</span></span>  
  
 <span data-ttu-id="1fdbc-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="1fdbc-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1fdbc-116">Nastavení zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="1fdbc-116">Transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1fdbc-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1fdbc-117">Requirements</span></span>  
  
|<span data-ttu-id="1fdbc-118">MOF</span><span class="sxs-lookup"><span data-stu-id="1fdbc-118">MOF</span></span>|<span data-ttu-id="1fdbc-119">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="1fdbc-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="1fdbc-120">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="1fdbc-120">Namespace</span></span>|<span data-ttu-id="1fdbc-121">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="1fdbc-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1fdbc-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="1fdbc-122">See Also</span></span>  
 <xref:System.ServiceModel.PeerSecuritySettings>
