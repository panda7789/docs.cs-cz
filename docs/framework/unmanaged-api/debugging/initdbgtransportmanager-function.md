---
title: InitDbgTransportManager – funkce
ms.date: 03/30/2017
api_name:
- InitDbgTransportManager
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- InitDbgTransportManager
helpviewer_keywords:
- remote debugging API [Silverlight]
- InitDbgTransportManager function
- Silverlight, remote debugging
ms.assetid: a30102ff-c52e-48c9-b3a9-aa14286a42b2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 948e97064d12dc5b2044faf35aa374e5ba5f2592
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67764780"
---
# <a name="initdbgtransportmanager-function"></a><span data-ttu-id="b3452-102">InitDbgTransportManager – funkce</span><span class="sxs-lookup"><span data-stu-id="b3452-102">InitDbgTransportManager Function</span></span>
<span data-ttu-id="b3452-103">Inicializuje správce přenosu pro připojení k vzdálené cílové pro výčet procesu a modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="b3452-103">Initializes the transport manager to connect to a remote target for process and runtime enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3452-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b3452-104">Syntax</span></span>  
  
```cpp  
HRESULT InitDbgTransportManager ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="b3452-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="b3452-105">Return Value</span></span>  
 <span data-ttu-id="b3452-106">S_OK</span><span class="sxs-lookup"><span data-stu-id="b3452-106">S_OK</span></span>  
 <span data-ttu-id="b3452-107">Úspěch.</span><span class="sxs-lookup"><span data-stu-id="b3452-107">Success.</span></span>  
  
 <span data-ttu-id="b3452-108">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="b3452-108">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="b3452-109">Funkce se nepodařilo přidělit paměť pro správce přenosu.</span><span class="sxs-lookup"><span data-stu-id="b3452-109">The function was unable to allocate memory for a transport manager.</span></span>  
  
 <span data-ttu-id="b3452-110">E_FAIL (nebo jiné E_ návratové kódy)</span><span class="sxs-lookup"><span data-stu-id="b3452-110">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="b3452-111">Jiné chyby.</span><span class="sxs-lookup"><span data-stu-id="b3452-111">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3452-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b3452-112">Requirements</span></span>  
 <span data-ttu-id="b3452-113">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3452-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3452-114">**Záhlaví:** CoreClrRemoteDebuggingInterfaces.h</span><span class="sxs-lookup"><span data-stu-id="b3452-114">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="b3452-115">**Library:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="b3452-115">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="b3452-116">**Verze rozhraní .NET framework:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="b3452-116">**.NET Framework Versions:** 3.5 SP1</span></span>
