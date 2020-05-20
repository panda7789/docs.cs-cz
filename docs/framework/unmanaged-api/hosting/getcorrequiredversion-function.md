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
ms.openlocfilehash: 6b9fd62102056a8d5f859ac913f4786f04c1df7e
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83617240"
---
# <a name="getcorrequiredversion-function"></a><span data-ttu-id="95dc5-102">GetCORRequiredVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="95dc5-102">GetCORRequiredVersion Function</span></span>
<span data-ttu-id="95dc5-103">Získá požadované číslo verze modulu CLR (Common Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="95dc5-103">Gets the required common language runtime (CLR) version number.</span></span>  
  
 <span data-ttu-id="95dc5-104">Tato funkce se už nepoužívá v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="95dc5-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95dc5-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="95dc5-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCORRequiredVersion (  
    [out] LPWSTR   pbuffer,  
    [in]  DWORD    cchBuffer,  
    [out] DWORD   *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95dc5-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="95dc5-106">Parameters</span></span>  
 `pbuffer`  
 <span data-ttu-id="95dc5-107">mimo Vyrovnávací paměť obsahující řetězec, který určuje číslo verze.</span><span class="sxs-lookup"><span data-stu-id="95dc5-107">[out] A buffer containing a string that specifies the version number.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="95dc5-108">pro Velikost vyrovnávací paměti v bajtech.</span><span class="sxs-lookup"><span data-stu-id="95dc5-108">[in] The size, in bytes, of the buffer.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="95dc5-109">mimo Počet bajtů vrácených ve vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="95dc5-109">[out] The number of bytes returned in the buffer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95dc5-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="95dc5-110">Requirements</span></span>  
 <span data-ttu-id="95dc5-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95dc5-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95dc5-112">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="95dc5-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="95dc5-113">**Knihovna:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="95dc5-113">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="95dc5-114">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95dc5-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95dc5-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="95dc5-115">See also</span></span>

- [<span data-ttu-id="95dc5-116">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="95dc5-116">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
