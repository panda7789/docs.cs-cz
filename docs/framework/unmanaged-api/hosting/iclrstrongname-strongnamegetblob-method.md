---
title: ICLRStrongName::StrongNameGetBlob – metoda
ms.date: 03/30/2017
api_name:
- ICLRStrongName.StrongNameGetBlob
- ICLRStrongName.StrongNameGetBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName::StrongNameGetBlob
helpviewer_keywords:
- ICLRStrongName::StrongNameGetBlob method [.NET Framework hosting]
- StrongNameGetBlob method, ICLRStrongName interface [.NET Framework hosting]
ms.assetid: a24218f8-7196-44be-b7a2-ee9cdd7a85c4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f4621a7d143d401d4cb620ac17c31e4ee5f13837
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47086772"
---
# <a name="iclrstrongnamestrongnamegetblob-method"></a><span data-ttu-id="6053b-102">ICLRStrongName::StrongNameGetBlob – metoda</span><span class="sxs-lookup"><span data-stu-id="6053b-102">ICLRStrongName::StrongNameGetBlob Method</span></span>
<span data-ttu-id="6053b-103">Vyplní zadané vyrovnávací paměti binární reprezentace spustitelný soubor na zadané adrese.</span><span class="sxs-lookup"><span data-stu-id="6053b-103">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6053b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6053b-104">Syntax</span></span>  
  
```  
HRESULT StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6053b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6053b-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="6053b-106">[in] Platnou cestu ke spustitelnému souboru, který se má načíst.</span><span class="sxs-lookup"><span data-stu-id="6053b-106">[in] A valid path to the executable file to be loaded.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="6053b-107">[in] Vyrovnávací paměť, do kterého chcete načíst spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="6053b-107">[in] The buffer into which to load the executable file.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="6053b-108">[out v] Požadovanou maximální velikost v bajtech, `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="6053b-108">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="6053b-109">Po návratu, skutečná velikost v bajtech, z `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="6053b-109">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6053b-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6053b-110">Return Value</span></span>  
 <span data-ttu-id="6053b-111">`S_OK` Pokud metoda dokončena úspěšně; v opačném případě hodnotu HRESULT označující selhání (viz [běžné hodnoty HRESULT](https://go.microsoft.com/fwlink/?LinkId=213878) seznam).</span><span class="sxs-lookup"><span data-stu-id="6053b-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](https://go.microsoft.com/fwlink/?LinkId=213878) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6053b-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6053b-112">Requirements</span></span>  
 <span data-ttu-id="6053b-113">**Platformy:** naleznete v tématu [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6053b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6053b-114">**Záhlaví:** MetaHost.h</span><span class="sxs-lookup"><span data-stu-id="6053b-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="6053b-115">**Knihovna:** zahrnuty jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6053b-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6053b-116">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6053b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6053b-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="6053b-117">See Also</span></span>  
 [<span data-ttu-id="6053b-118">StrongNameGetBlobFromImage – metoda</span><span class="sxs-lookup"><span data-stu-id="6053b-118">StrongNameGetBlobFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)  
 [<span data-ttu-id="6053b-119">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6053b-119">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
