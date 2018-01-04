---
title: "InitDbgTransportManager – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: InitDbgTransportManager
api_location: mscordbi_macx86.dll
api_type: COM
f1_keywords: InitDbgTransportManager
helpviewer_keywords:
- remote debugging API [Silverlight]
- InitDbgTransportManager function
- Silverlight, remote debugging
ms.assetid: a30102ff-c52e-48c9-b3a9-aa14286a42b2
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 37b849ed482f76692a63c70cbb0a3b9e1bacc8ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="initdbgtransportmanager-function"></a><span data-ttu-id="099ab-102">InitDbgTransportManager – funkce</span><span class="sxs-lookup"><span data-stu-id="099ab-102">InitDbgTransportManager Function</span></span>
<span data-ttu-id="099ab-103">Inicializuje správce přenosu pro připojení k vzdálené cíle pro výčet proces a modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="099ab-103">Initializes the transport manager to connect to a remote target for process and runtime enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="099ab-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="099ab-104">Syntax</span></span>  
  
```  
HRESULT InitDbgTransportManager ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="099ab-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="099ab-105">Return Value</span></span>  
 <span data-ttu-id="099ab-106">S_OK</span><span class="sxs-lookup"><span data-stu-id="099ab-106">S_OK</span></span>  
 <span data-ttu-id="099ab-107">Úspěch.</span><span class="sxs-lookup"><span data-stu-id="099ab-107">Success.</span></span>  
  
 <span data-ttu-id="099ab-108">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="099ab-108">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="099ab-109">Funkce se nepodařilo přidělit paměť pro správce přenosu.</span><span class="sxs-lookup"><span data-stu-id="099ab-109">The function was unable to allocate memory for a transport manager.</span></span>  
  
 <span data-ttu-id="099ab-110">E_FAIL (nebo ostatní návratové kódy E_)</span><span class="sxs-lookup"><span data-stu-id="099ab-110">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="099ab-111">Jiné chyby.</span><span class="sxs-lookup"><span data-stu-id="099ab-111">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="099ab-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="099ab-112">Requirements</span></span>  
 <span data-ttu-id="099ab-113">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="099ab-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="099ab-114">**Záhlaví:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="099ab-114">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="099ab-115">**Knihovna:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="099ab-115">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="099ab-116">**Verze rozhraní .NET framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="099ab-116">**.NET Framework Versions:** 3.5 SP1</span></span>
