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
ms.openlocfilehash: f197c8802bd9e55391b3e3e20c64398736070a16
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136339"
---
# <a name="getfileversion-function"></a><span data-ttu-id="afb7f-102">GetFileVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="afb7f-102">GetFileVersion Function</span></span>
<span data-ttu-id="afb7f-103">Získá informace o verzi modulu CLR (Common Language Runtime) zadaného souboru pomocí zadané vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="afb7f-103">Gets the common language runtime (CLR) version information of the specified file, using the specified buffer.</span></span>  
  
 <span data-ttu-id="afb7f-104">Tato funkce se už nepoužívá v .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="afb7f-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afb7f-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="afb7f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFileVersion (  
    [in]  LPCWSTR      szFilename,   
    [in, out] LPWSTR   szBuffer,   
    [in]  DWORD        cchBuffer,   
    [out] DWORD        *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="afb7f-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="afb7f-106">Parameters</span></span>  
 `szFilename`  
 <span data-ttu-id="afb7f-107">pro Cesta k souboru, který se má prozkoumat</span><span class="sxs-lookup"><span data-stu-id="afb7f-107">[in] The path of the file to be examined.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="afb7f-108">[in, out] Vyrovnávací paměť přidělená pro vrácené informace o verzi.</span><span class="sxs-lookup"><span data-stu-id="afb7f-108">[in, out] The buffer allocated for the version information that is returned.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="afb7f-109">pro Velikost `szBuffer`v různých znacích.</span><span class="sxs-lookup"><span data-stu-id="afb7f-109">[in] The size, in wide characters, of `szBuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="afb7f-110">mimo Velikost vrácených `szBuffer`v bajtech.</span><span class="sxs-lookup"><span data-stu-id="afb7f-110">[out] The size, in bytes, of the returned `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afb7f-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="afb7f-111">Requirements</span></span>  
 <span data-ttu-id="afb7f-112">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="afb7f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="afb7f-113">**Hlavička:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="afb7f-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="afb7f-114">**Verze .NET Framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="afb7f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afb7f-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="afb7f-115">See also</span></span>

- [<span data-ttu-id="afb7f-116">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="afb7f-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
