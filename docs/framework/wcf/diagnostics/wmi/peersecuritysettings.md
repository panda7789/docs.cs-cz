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
ms.openlocfilehash: 02cd483f2f7ec5e599b286b672d051a0e8d57940
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="peersecuritysettings"></a><span data-ttu-id="4d828-102">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="4d828-102">PeerSecuritySettings</span></span>
<span data-ttu-id="4d828-103">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="4d828-103">PeerSecuritySettings</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d828-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4d828-104">Syntax</span></span>  
  
```  
class PeerSecuritySettings  
{  
  string Mode;  
  PeerTransportSecuritySettings Transport;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="4d828-105">Metody</span><span class="sxs-lookup"><span data-stu-id="4d828-105">Methods</span></span>  
 <span data-ttu-id="4d828-106">Třída PeerSecuritySettings nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="4d828-106">The PeerSecuritySettings class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="4d828-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="4d828-107">Properties</span></span>  
 <span data-ttu-id="4d828-108">Třída PeerSecuritySettings má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="4d828-108">The PeerSecuritySettings class has the following properties:</span></span>  
  
### <a name="mode"></a><span data-ttu-id="4d828-109">Režim</span><span class="sxs-lookup"><span data-stu-id="4d828-109">Mode</span></span>  
 <span data-ttu-id="4d828-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="4d828-110">Data type: string</span></span>  
  
 <span data-ttu-id="4d828-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4d828-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4d828-112">Jestli úroveň zprávy a koncový bod nakonfigurovaná pomocí této vazby používá zabezpečení na úrovni přenosu.</span><span class="sxs-lookup"><span data-stu-id="4d828-112">Whether message-level and transport-level security are used by an endpoint configured with the binding.</span></span>  
  
### <a name="transport"></a><span data-ttu-id="4d828-113">Přenos</span><span class="sxs-lookup"><span data-stu-id="4d828-113">Transport</span></span>  
 <span data-ttu-id="4d828-114">Datový typ: třída PeerTransportSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="4d828-114">Data type: PeerTransportSecuritySettings</span></span>  
  
 <span data-ttu-id="4d828-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4d828-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4d828-116">Nastavení zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="4d828-116">Transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d828-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4d828-117">Requirements</span></span>  
  
|<span data-ttu-id="4d828-118">MOF</span><span class="sxs-lookup"><span data-stu-id="4d828-118">MOF</span></span>|<span data-ttu-id="4d828-119">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="4d828-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="4d828-120">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="4d828-120">Namespace</span></span>|<span data-ttu-id="4d828-121">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4d828-121">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4d828-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="4d828-122">See Also</span></span>  
 <xref:System.ServiceModel.PeerSecuritySettings>
