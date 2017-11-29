---
title: "StrongNameGetBlob – funkce"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: StrongNameGetBlob
api_location: mscoree.dll
api_type: DLLExport
f1_keywords: StrongNameGetBlob
helpviewer_keywords: StrongNameGetBlob function [.NET Framework strong naming]
ms.assetid: 15d09166-be00-4696-913f-2c1fbc7ac2e1
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0a88131e4a764c963d24a698935ebb12e0daa96c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="strongnamegetblob-function"></a><span data-ttu-id="f6677-102">StrongNameGetBlob – funkce</span><span class="sxs-lookup"><span data-stu-id="f6677-102">StrongNameGetBlob Function</span></span>
<span data-ttu-id="f6677-103">Vyplní zadanou vyrovnávací paměť binární reprezentace spustitelný soubor na zadané adrese.</span><span class="sxs-lookup"><span data-stu-id="f6677-103">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>  
  
 <span data-ttu-id="f6677-104">Tato funkce je zastaralá.</span><span class="sxs-lookup"><span data-stu-id="f6677-104">This function has been deprecated.</span></span> <span data-ttu-id="f6677-105">Použití [iclrstrongname::strongnamegetblob –](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md) metoda místo.</span><span class="sxs-lookup"><span data-stu-id="f6677-105">Use the [ICLRStrongName::StrongNameGetBLob](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6677-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f6677-106">Syntax</span></span>  
  
```  
BOOLEAN StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f6677-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6677-107">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="f6677-108">[v] Platná cesta ke spustitelnému souboru, který má být načten.</span><span class="sxs-lookup"><span data-stu-id="f6677-108">[in] A valid path to the executable file to be loaded.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="f6677-109">[v] Vyrovnávací paměť, do kterého se načíst spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="f6677-109">[in] The buffer into which to load the executable file.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="f6677-110">[ve out] Požadovanou maximální velikost v bajtech `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="f6677-110">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="f6677-111">Po návratu, skutečná velikost v bajtech z `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="f6677-111">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f6677-112">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="f6677-112">Return Value</span></span>  
 <span data-ttu-id="f6677-113">`true`Při úspěšném dokončení; v opačném `false`.</span><span class="sxs-lookup"><span data-stu-id="f6677-113">`true` on successful completion; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f6677-114">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f6677-114">Remarks</span></span>  
 <span data-ttu-id="f6677-115">Pokud `StrongNameGetBlob` není úspěšně dokončit, volání funkce [strongnameerrorinfo –](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) funkce načíst poslední generované chyba.</span><span class="sxs-lookup"><span data-stu-id="f6677-115">If the `StrongNameGetBlob` function does not complete successfully, call the [StrongNameErrorInfo](../../../../docs/framework/unmanaged-api/strong-naming/strongnameerrorinfo-function.md) function to retrieve the last generated error.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6677-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f6677-116">Requirements</span></span>  
 <span data-ttu-id="f6677-117">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6677-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6677-118">**Záhlaví:** StrongName.h</span><span class="sxs-lookup"><span data-stu-id="f6677-118">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="f6677-119">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f6677-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f6677-120">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6677-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6677-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="f6677-121">See Also</span></span>  
 [<span data-ttu-id="f6677-122">Strongnamegetblob – metoda</span><span class="sxs-lookup"><span data-stu-id="f6677-122">StrongNameGetBlob Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblob-method.md)  
 [<span data-ttu-id="f6677-123">Strongnamegetblobfromimage – metoda</span><span class="sxs-lookup"><span data-stu-id="f6677-123">StrongNameGetBlobFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)  
 [<span data-ttu-id="f6677-124">Iclrstrongname – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f6677-124">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
