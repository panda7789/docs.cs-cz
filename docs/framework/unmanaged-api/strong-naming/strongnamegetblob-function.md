---
title: StrongNameGetBlob – funkce
ms.date: 03/30/2017
api_name:
- StrongNameGetBlob
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- StrongNameGetBlob
helpviewer_keywords:
- StrongNameGetBlob function [.NET Framework strong naming]
ms.assetid: 15d09166-be00-4696-913f-2c1fbc7ac2e1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: af2fa38bab8b22f86429dbcd95c842cec9ae73c3
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484823"
---
# <a name="strongnamegetblob-function"></a><span data-ttu-id="adf5a-102">StrongNameGetBlob – funkce</span><span class="sxs-lookup"><span data-stu-id="adf5a-102">StrongNameGetBlob Function</span></span>
<span data-ttu-id="adf5a-103">Vyplní zadané vyrovnávací paměti binární reprezentace spustitelný soubor na zadané adrese.</span><span class="sxs-lookup"><span data-stu-id="adf5a-103">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>  
  
 <span data-ttu-id="adf5a-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="adf5a-104">This function has been deprecated.</span></span> <span data-ttu-id="adf5a-105">Použití [iclrstrongname::strongnamegetblob –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="adf5a-105">Use the [ICLRStrongName::StrongNameGetBLob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="adf5a-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="adf5a-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="adf5a-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="adf5a-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="adf5a-108">[in] Platnou cestu ke spustitelnému souboru, který se má načíst.</span><span class="sxs-lookup"><span data-stu-id="adf5a-108">[in] A valid path to the executable file to be loaded.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="adf5a-109">[in] Vyrovnávací paměť, do kterého chcete načíst spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="adf5a-109">[in] The buffer into which to load the executable file.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="adf5a-110">[out v] Požadovanou maximální velikost v bajtech, `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="adf5a-110">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="adf5a-111">Po návratu, skutečná velikost v bajtech, z `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="adf5a-111">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="adf5a-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="adf5a-112">Return Value</span></span>  
 <span data-ttu-id="adf5a-113">`true` Při úspěšném dokončení; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="adf5a-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="adf5a-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="adf5a-114">Remarks</span></span>  
 <span data-ttu-id="adf5a-115">Pokud `StrongNameGetBlob` není úspěšně dokončit, volání funkce [strongnameerrorinfo –](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkce k načtení poslední chyby generované.</span><span class="sxs-lookup"><span data-stu-id="adf5a-115">If the `StrongNameGetBlob` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="adf5a-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="adf5a-116">Requirements</span></span>  
 <span data-ttu-id="adf5a-117">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="adf5a-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="adf5a-118">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="adf5a-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="adf5a-119">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="adf5a-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="adf5a-120">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="adf5a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adf5a-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="adf5a-121">See also</span></span>
- [<span data-ttu-id="adf5a-122">StrongNameGetBlob – metoda</span><span class="sxs-lookup"><span data-stu-id="adf5a-122">StrongNameGetBlob Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)
- [<span data-ttu-id="adf5a-123">StrongNameGetBlobFromImage – metoda</span><span class="sxs-lookup"><span data-stu-id="adf5a-123">StrongNameGetBlobFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [<span data-ttu-id="adf5a-124">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="adf5a-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
