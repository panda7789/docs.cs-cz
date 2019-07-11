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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b1f5508e9ee41d8670b43d5b219846237e11fc8f
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778144"
---
# <a name="getfileversion-function"></a><span data-ttu-id="796c4-102">GetFileVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="796c4-102">GetFileVersion Function</span></span>
<span data-ttu-id="796c4-103">Získá common language runtime (CLR) informace o verzi zadaného souboru pomocí zadané vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="796c4-103">Gets the common language runtime (CLR) version information of the specified file, using the specified buffer.</span></span>  
  
 <span data-ttu-id="796c4-104">Tato funkce se již nepoužívá v rozhraní .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="796c4-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="796c4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="796c4-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFileVersion (  
    [in]  LPCWSTR      szFilename,   
    [in, out] LPWSTR   szBuffer,   
    [in]  DWORD        cchBuffer,   
    [out] DWORD        *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="796c4-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="796c4-106">Parameters</span></span>  
 `szFilename`  
 <span data-ttu-id="796c4-107">[in] Cesta souboru, který má být zkontrolován.</span><span class="sxs-lookup"><span data-stu-id="796c4-107">[in] The path of the file to be examined.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="796c4-108">[out v] Vyrovnávací paměť přidělená pro informace o verzi, která je vrácena.</span><span class="sxs-lookup"><span data-stu-id="796c4-108">[in, out] The buffer allocated for the version information that is returned.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="796c4-109">[in] Velikost v širokých znaků, z `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="796c4-109">[in] The size, in wide characters, of `szBuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="796c4-110">[out] Velikost v bajtech, vráceného `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="796c4-110">[out] The size, in bytes, of the returned `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="796c4-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="796c4-111">Requirements</span></span>  
 <span data-ttu-id="796c4-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="796c4-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="796c4-113">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="796c4-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="796c4-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="796c4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="796c4-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="796c4-115">See also</span></span>

- [<span data-ttu-id="796c4-116">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="796c4-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
