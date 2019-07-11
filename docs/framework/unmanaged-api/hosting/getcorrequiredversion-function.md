---
title: GetCORRequiredVersion – funkce
ms.date: 03/30/2017
api_name:
- GetCORRequiredVersion
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetCORRequiredVersion
helpviewer_keywords:
- GetCORRequiredVersion function [.NET Framework hosting]
ms.assetid: 1588fe7b-c378-4f4b-9c4b-48647f1119cc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8597b68b75d2b5f77f68fc13c3fb78bfdae46178
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67736288"
---
# <a name="getcorrequiredversion-function"></a><span data-ttu-id="195dd-102">GetCORRequiredVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="195dd-102">GetCORRequiredVersion Function</span></span>
<span data-ttu-id="195dd-103">Získá požadované common language runtime (CLR) číslo verze.</span><span class="sxs-lookup"><span data-stu-id="195dd-103">Gets the required common language runtime (CLR) version number.</span></span>  
  
 <span data-ttu-id="195dd-104">Tato funkce se již nepoužívá v rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="195dd-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="195dd-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="195dd-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCORRequiredVersion (  
    [out] LPWSTR   pbuffer,  
    [in]  DWORD    cchBuffer,  
    [out] DWORD   *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="195dd-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="195dd-106">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="195dd-107">[out] Vyrovnávací paměti, který obsahuje řetězec, který určuje číslo verze.</span><span class="sxs-lookup"><span data-stu-id="195dd-107">[out] A buffer containing a string that specifies the version number.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="195dd-108">[in] Velikost v bajtech, vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="195dd-108">[in] The size, in bytes, of the buffer.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="195dd-109">[out] Počet bajtů vrácených ve vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="195dd-109">[out] The number of bytes returned in the buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="195dd-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="195dd-110">Requirements</span></span>  
 <span data-ttu-id="195dd-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="195dd-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="195dd-112">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="195dd-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="195dd-113">**Knihovna:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="195dd-113">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="195dd-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="195dd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="195dd-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="195dd-115">See also</span></span>

- [<span data-ttu-id="195dd-116">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="195dd-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
