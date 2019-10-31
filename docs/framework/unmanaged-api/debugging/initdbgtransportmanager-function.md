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
ms.openlocfilehash: 2d67bee3ea0e57080179b3fbb7e0b4193860c44d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73103290"
---
# <a name="initdbgtransportmanager-function"></a><span data-ttu-id="50843-102">InitDbgTransportManager – funkce</span><span class="sxs-lookup"><span data-stu-id="50843-102">InitDbgTransportManager Function</span></span>
<span data-ttu-id="50843-103">Inicializuje správce přenosu pro připojení ke vzdálenému cíli pro proces a výčet za běhu.</span><span class="sxs-lookup"><span data-stu-id="50843-103">Initializes the transport manager to connect to a remote target for process and runtime enumeration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50843-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="50843-104">Syntax</span></span>  
  
```cpp  
HRESULT InitDbgTransportManager ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="50843-105">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="50843-105">Return Value</span></span>  
 <span data-ttu-id="50843-106">S_OK</span><span class="sxs-lookup"><span data-stu-id="50843-106">S_OK</span></span>  
 <span data-ttu-id="50843-107">Nástup.</span><span class="sxs-lookup"><span data-stu-id="50843-107">Success.</span></span>  
  
 <span data-ttu-id="50843-108">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="50843-108">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="50843-109">Funkce nemohla přidělit paměť pro správce přenosu.</span><span class="sxs-lookup"><span data-stu-id="50843-109">The function was unable to allocate memory for a transport manager.</span></span>  
  
 <span data-ttu-id="50843-110">E_FAIL (nebo jiné návratové kódy E_)</span><span class="sxs-lookup"><span data-stu-id="50843-110">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="50843-111">Další chyby.</span><span class="sxs-lookup"><span data-stu-id="50843-111">Other failures.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50843-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="50843-112">Requirements</span></span>  
 <span data-ttu-id="50843-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50843-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50843-114">**Hlavička:** CoreClrRemoteDebuggingInterfaces. h</span><span class="sxs-lookup"><span data-stu-id="50843-114">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="50843-115">**Knihovna:** mscordbi_macx86. dll</span><span class="sxs-lookup"><span data-stu-id="50843-115">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="50843-116">**Verze .NET Framework:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="50843-116">**.NET Framework Versions:** 3.5 SP1</span></span>
