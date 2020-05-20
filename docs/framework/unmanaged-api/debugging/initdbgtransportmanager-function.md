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
ms.openlocfilehash: e18ceb25b9c58a9710ef967cb071e3ef55beea8c
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83421043"
---
# <a name="initdbgtransportmanager-function"></a><span data-ttu-id="21e3b-102">InitDbgTransportManager – funkce</span><span class="sxs-lookup"><span data-stu-id="21e3b-102">InitDbgTransportManager Function</span></span>
<span data-ttu-id="21e3b-103">Inicializuje správce přenosu pro připojení ke vzdálenému cíli pro proces a výčet za běhu.</span><span class="sxs-lookup"><span data-stu-id="21e3b-103">Initializes the transport manager to connect to a remote target for process and runtime enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21e3b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21e3b-104">Syntax</span></span>  
  
```cpp  
HRESULT InitDbgTransportManager ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="21e3b-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="21e3b-105">Return Value</span></span>  
 <span data-ttu-id="21e3b-106">S_OK</span><span class="sxs-lookup"><span data-stu-id="21e3b-106">S_OK</span></span>  
 <span data-ttu-id="21e3b-107">Úspěch.</span><span class="sxs-lookup"><span data-stu-id="21e3b-107">Success.</span></span>  
  
 <span data-ttu-id="21e3b-108">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="21e3b-108">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="21e3b-109">Funkce nemohla přidělit paměť pro správce přenosu.</span><span class="sxs-lookup"><span data-stu-id="21e3b-109">The function was unable to allocate memory for a transport manager.</span></span>  
  
 <span data-ttu-id="21e3b-110">E_FAIL (nebo jiné návratové kódy E_)</span><span class="sxs-lookup"><span data-stu-id="21e3b-110">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="21e3b-111">Další chyby.</span><span class="sxs-lookup"><span data-stu-id="21e3b-111">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21e3b-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="21e3b-112">Requirements</span></span>  
 <span data-ttu-id="21e3b-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21e3b-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21e3b-114">**Hlavička:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="21e3b-114">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="21e3b-115">**Knihovna:** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="21e3b-115">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="21e3b-116">**Verze .NET Framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="21e3b-116">**.NET Framework Versions:** 3.5 SP1</span></span>
