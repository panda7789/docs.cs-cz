---
title: GetAssemblyIdentityFromFile – funkce
ms.date: 03/30/2017
api_name:
- GetAssemblyIdentityFromFile
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- COM
f1_keywords:
- GetAssemblyIdentityFromFile
helpviewer_keywords:
- GetAssemblyIdentityFromFile function [.NET Framework fusion]
ms.assetid: 2c32da53-76c7-4048-84d0-d05207333004
topic_type:
- apiref
ms.openlocfilehash: 50ec5a23db4d2460480bcc3e463ecd88e7470bde
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134522"
---
# <a name="getassemblyidentityfromfile-function"></a><span data-ttu-id="f27b9-102">GetAssemblyIdentityFromFile – funkce</span><span class="sxs-lookup"><span data-stu-id="f27b9-102">GetAssemblyIdentityFromFile Function</span></span>
<span data-ttu-id="f27b9-103">Získá ukazatel na objekt `IUnknown` se zadaným `IID` v sestavení v zadané cestě k souboru.</span><span class="sxs-lookup"><span data-stu-id="f27b9-103">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f27b9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f27b9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyIdentityFromFile (  
    [in]  LPCWSTR   pwzFilePath,  
    [in]  REFIID    riid,  
    [out] IUnknown  **ppIdentity  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="f27b9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f27b9-105">Parameters</span></span>  
 `pwzFilePath`  
 <span data-ttu-id="f27b9-106">pro Platná cesta k požadovanému sestavení.</span><span class="sxs-lookup"><span data-stu-id="f27b9-106">[in] A valid path to the requested assembly.</span></span>  
  
 `riid`  
 <span data-ttu-id="f27b9-107">pro `IID` rozhraní, které se má vrátit.</span><span class="sxs-lookup"><span data-stu-id="f27b9-107">[in] The `IID` of the interface to return.</span></span>  
  
 `ppIdentity`  
 <span data-ttu-id="f27b9-108">mimo Vrácený ukazatel rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f27b9-108">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f27b9-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f27b9-109">Requirements</span></span>  
 <span data-ttu-id="f27b9-110">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f27b9-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f27b9-111">**Hlavička:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="f27b9-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="f27b9-112">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f27b9-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f27b9-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f27b9-113">See also</span></span>

- [<span data-ttu-id="f27b9-114">IUnknown</span><span class="sxs-lookup"><span data-stu-id="f27b9-114">IUnknown</span></span>](/cpp/atl/iunknown)
- [<span data-ttu-id="f27b9-115">Globální statické funkce pro fúze</span><span class="sxs-lookup"><span data-stu-id="f27b9-115">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
