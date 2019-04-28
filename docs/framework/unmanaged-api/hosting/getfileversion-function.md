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
ms.openlocfilehash: d25a3ccdd66ff7acb70f1f5e6c60157b53cc97c5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61628454"
---
# <a name="getfileversion-function"></a><span data-ttu-id="275d6-102">GetFileVersion – funkce</span><span class="sxs-lookup"><span data-stu-id="275d6-102">GetFileVersion Function</span></span>
<span data-ttu-id="275d6-103">Získá common language runtime (CLR) informace o verzi zadaného souboru pomocí zadané vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="275d6-103">Gets the common language runtime (CLR) version information of the specified file, using the specified buffer.</span></span>  
  
 <span data-ttu-id="275d6-104">Tato funkce se již nepoužívá v [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="275d6-104">This function has been deprecated in the [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)].</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="275d6-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="275d6-105">Syntax</span></span>  
  
```  
HRESULT GetFileVersion (  
    [in]  LPCWSTR      szFilename,   
    [in, out] LPWSTR   szBuffer,   
    [in]  DWORD        cchBuffer,   
    [out] DWORD        *dwLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="275d6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="275d6-106">Parameters</span></span>  
 `szFilename`  
 <span data-ttu-id="275d6-107">[in] Cesta souboru, který má být zkontrolován.</span><span class="sxs-lookup"><span data-stu-id="275d6-107">[in] The path of the file to be examined.</span></span>  
  
 `szBuffer`  
 <span data-ttu-id="275d6-108">[out v] Vyrovnávací paměť přidělená pro informace o verzi, která je vrácena.</span><span class="sxs-lookup"><span data-stu-id="275d6-108">[in, out] The buffer allocated for the version information that is returned.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="275d6-109">[in] Velikost v širokých znaků, z `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="275d6-109">[in] The size, in wide characters, of `szBuffer`.</span></span>  
  
 `dwLength`  
 <span data-ttu-id="275d6-110">[out] Velikost v bajtech, vráceného `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="275d6-110">[out] The size, in bytes, of the returned `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="275d6-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="275d6-111">Requirements</span></span>  
 <span data-ttu-id="275d6-112">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="275d6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="275d6-113">**Záhlaví:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="275d6-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="275d6-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="275d6-114">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="275d6-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="275d6-115">See also</span></span>

- [<span data-ttu-id="275d6-116">Zastaralé funkce pro hostování CLR</span><span class="sxs-lookup"><span data-stu-id="275d6-116">Deprecated CLR Hosting Functions</span></span>](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
