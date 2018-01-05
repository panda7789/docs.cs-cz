---
title: PeerSecuritySettings
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24ae0d35-f3a3-419b-afd6-686e22aae27b
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 48a9cc5a7a05b47a5589d1bf9a730184fb7f0543
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="peersecuritysettings"></a><span data-ttu-id="fd9ec-102">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="fd9ec-102">PeerSecuritySettings</span></span>
<span data-ttu-id="fd9ec-103">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="fd9ec-103">PeerSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd9ec-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fd9ec-104">Syntax</span></span>  
  
```  
class PeerSecuritySettings  
{  
  string Mode;  
  PeerTransportSecuritySettings Transport;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="fd9ec-105">Metody</span><span class="sxs-lookup"><span data-stu-id="fd9ec-105">Methods</span></span>  
 <span data-ttu-id="fd9ec-106">Třída PeerSecuritySettings nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="fd9ec-106">The PeerSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="fd9ec-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="fd9ec-107">Properties</span></span>  
 <span data-ttu-id="fd9ec-108">Třída PeerSecuritySettings má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="fd9ec-108">The PeerSecuritySettings class has the following properties:</span></span>  
  
### <a name="mode"></a><span data-ttu-id="fd9ec-109">Režim</span><span class="sxs-lookup"><span data-stu-id="fd9ec-109">Mode</span></span>  
 <span data-ttu-id="fd9ec-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="fd9ec-110">Data type: string</span></span>  
  
 <span data-ttu-id="fd9ec-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="fd9ec-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fd9ec-112">Jestli úroveň zprávy a koncový bod nakonfigurovaná pomocí této vazby používá zabezpečení na úrovni přenosu.</span><span class="sxs-lookup"><span data-stu-id="fd9ec-112">Whether message-level and transport-level security are used by an endpoint configured with the binding.</span></span>  
  
### <a name="transport"></a><span data-ttu-id="fd9ec-113">Přenos</span><span class="sxs-lookup"><span data-stu-id="fd9ec-113">Transport</span></span>  
 <span data-ttu-id="fd9ec-114">Datový typ: třída PeerTransportSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="fd9ec-114">Data type: PeerTransportSecuritySettings</span></span>  
  
 <span data-ttu-id="fd9ec-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="fd9ec-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="fd9ec-116">Nastavení zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="fd9ec-116">Transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fd9ec-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="fd9ec-117">Requirements</span></span>  
  
|<span data-ttu-id="fd9ec-118">MOF</span><span class="sxs-lookup"><span data-stu-id="fd9ec-118">MOF</span></span>|<span data-ttu-id="fd9ec-119">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="fd9ec-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="fd9ec-120">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="fd9ec-120">Namespace</span></span>|<span data-ttu-id="fd9ec-121">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="fd9ec-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fd9ec-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="fd9ec-122">See Also</span></span>  
 <xref:System.ServiceModel.PeerSecuritySettings>
