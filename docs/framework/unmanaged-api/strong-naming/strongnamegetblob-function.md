---
title: "StrongNameGetBlob – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b1948a0d8a8536ebe9b0531eecaf3df446252b0a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="strongnamegetblob-function"></a><span data-ttu-id="821a1-102">StrongNameGetBlob – funkce</span><span class="sxs-lookup"><span data-stu-id="821a1-102">StrongNameGetBlob Function</span></span>
<span data-ttu-id="821a1-103">Vyplní zadanou vyrovnávací paměť binární reprezentace spustitelný soubor na zadané adrese.</span><span class="sxs-lookup"><span data-stu-id="821a1-103">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>  
  
 <span data-ttu-id="821a1-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="821a1-104">This function has been deprecated.</span></span> <span data-ttu-id="821a1-105">Použití [iclrstrongname::strongnamegetblob –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="821a1-105">Use the [ICLRStrongName::StrongNameGetBLob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="821a1-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="821a1-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="821a1-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="821a1-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="821a1-108">[v] Platná cesta ke spustitelnému souboru, který má být načten.</span><span class="sxs-lookup"><span data-stu-id="821a1-108">[in] A valid path to the executable file to be loaded.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="821a1-109">[v] Vyrovnávací paměť, do kterého se načíst spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="821a1-109">[in] The buffer into which to load the executable file.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="821a1-110">[ve out] Požadovanou maximální velikost v bajtech `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="821a1-110">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="821a1-111">Po návratu, skutečná velikost v bajtech z `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="821a1-111">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="821a1-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="821a1-112">Return Value</span></span>  
 <span data-ttu-id="821a1-113">`true`Při úspěšném dokončení; v opačném `false`.</span><span class="sxs-lookup"><span data-stu-id="821a1-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="821a1-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="821a1-114">Remarks</span></span>  
 <span data-ttu-id="821a1-115">Pokud `StrongNameGetBlob` není úspěšně dokončit, volání funkce [strongnameerrorinfo –](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkce načíst poslední generované chyba.</span><span class="sxs-lookup"><span data-stu-id="821a1-115">If the `StrongNameGetBlob` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="821a1-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="821a1-116">Requirements</span></span>  
 <span data-ttu-id="821a1-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="821a1-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="821a1-118">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="821a1-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="821a1-119">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="821a1-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="821a1-120">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="821a1-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="821a1-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="821a1-121">See Also</span></span>  
 [<span data-ttu-id="821a1-122">StrongNameGetBlob – metoda</span><span class="sxs-lookup"><span data-stu-id="821a1-122">StrongNameGetBlob Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)  
 [<span data-ttu-id="821a1-123">StrongNameGetBlobFromImage – metoda</span><span class="sxs-lookup"><span data-stu-id="821a1-123">StrongNameGetBlobFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)  
 [<span data-ttu-id="821a1-124">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="821a1-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
