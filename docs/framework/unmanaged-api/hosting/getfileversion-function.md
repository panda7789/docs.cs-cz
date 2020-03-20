---
title: GetFileVersion – funkce
ms.date: 03/30/2017
api_name:
- GetFileVersion
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- GetFileVersion
helpviewer_keywords:
- GetFileVersion function [.NET Framework hosting]
ms.assetid: b3222c85-da88-4485-97d7-3a6ee3e8d358
topic_type:
- apiref
ms.openlocfilehash: f3b51c1b376fa9c664de53aa76ec724ca305ae6a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178183"
---
# <a name="getfileversion-function"></a><span data-ttu-id="b1189-102">GetFileVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="b1189-102">GetFileVersion Function</span></span>
<span data-ttu-id="b1189-103">Získá informace o verzi clr (COMMON Language runtime) zadaného souboru pomocí zadané vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="b1189-103">Gets the common language runtime (CLR) version information of the specified file, using the specified buffer.</span></span>  
  
 <span data-ttu-id="b1189-104">Tato funkce byla v rozhraní .NET Framework 4 zastaralá.</span><span class="sxs-lookup"><span data-stu-id="b1189-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1189-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1189-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFileVersion (  
    [in]  LPCWSTR      szFilename,
    [in, out] LPWSTR   szBuffer,
    [in]  DWORD        cchBuffer,
    [out] DWORD        *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1189-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b1189-106">Parameters</span></span>  
 `szFilename`  
 <span data-ttu-id="b1189-107">[v] Cesta souboru, který má být zkontrolován.</span><span class="sxs-lookup"><span data-stu-id="b1189-107">[in] The path of the file to be examined.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="b1189-108">[dovnitř, ven] Vyrovnávací paměť přidělená pro informace o verzi, která je vrácena.</span><span class="sxs-lookup"><span data-stu-id="b1189-108">[in, out] The buffer allocated for the version information that is returned.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="b1189-109">[v] Velikost . `szBuffer`</span><span class="sxs-lookup"><span data-stu-id="b1189-109">[in] The size, in wide characters, of `szBuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="b1189-110">[out] Velikost vráceného bajtu v bajtech `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="b1189-110">[out] The size, in bytes, of the returned `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1189-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b1189-111">Requirements</span></span>  
 <span data-ttu-id="b1189-112">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1189-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1189-113">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b1189-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b1189-114">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1189-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1189-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="b1189-115">See also</span></span>

- [<span data-ttu-id="b1189-116">Zastaralé funkce hostování CLR</span><span class="sxs-lookup"><span data-stu-id="b1189-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
