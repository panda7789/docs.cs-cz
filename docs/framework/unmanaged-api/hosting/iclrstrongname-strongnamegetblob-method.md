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
ms.openlocfilehash: c7f04364cc52bd38d7d2659d1d188c5fd783ad01
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2020
ms.locfileid: "75899767"
---
# <a name="iclrstrongnamestrongnamegetblob-method"></a><span data-ttu-id="737ef-102">ICLRStrongName::StrongNameGetBlob – metoda</span><span class="sxs-lookup"><span data-stu-id="737ef-102">ICLRStrongName::StrongNameGetBlob Method</span></span>
<span data-ttu-id="737ef-103">Vyplní zadanou vyrovnávací paměť binární reprezentací spustitelného souboru na zadané adrese.</span><span class="sxs-lookup"><span data-stu-id="737ef-103">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="737ef-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="737ef-104">Syntax</span></span>  
  
```cpp  
HRESULT StrongNameGetBlob (  
    [in]  LPCWSTR    wszFilePath,  
    [in]  BYTE       *pbBlob,  
    [in, out] DWORD  *pcbBlob  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="737ef-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="737ef-105">Parameters</span></span>  
 `wszFilePath`  
 <span data-ttu-id="737ef-106">pro Platná cesta ke spustitelnému souboru, který se má načíst.</span><span class="sxs-lookup"><span data-stu-id="737ef-106">[in] A valid path to the executable file to be loaded.</span></span>  
  
 `pbBlob`  
 <span data-ttu-id="737ef-107">pro Vyrovnávací paměť, do které se má načíst spustitelný soubor.</span><span class="sxs-lookup"><span data-stu-id="737ef-107">[in] The buffer into which to load the executable file.</span></span>  
  
 `pcbBlob`  
 <span data-ttu-id="737ef-108">[in, out] Požadovaná maximální velikost v bajtech `pbBlob`.</span><span class="sxs-lookup"><span data-stu-id="737ef-108">[in, out] The requested maximum size, in bytes, of `pbBlob`.</span></span> <span data-ttu-id="737ef-109">Po návratu se skutečná velikost `pbBlob`v bajtech.</span><span class="sxs-lookup"><span data-stu-id="737ef-109">Upon return, the actual size, in bytes, of `pbBlob`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="737ef-110">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="737ef-110">Return Value</span></span>  
 <span data-ttu-id="737ef-111">`S_OK`, zda byla metoda úspěšně dokončena; v opačném případě hodnota HRESULT, která označuje selhání (viz [společné hodnoty HRESULT](/windows/win32/seccrypto/common-hresult-values) pro seznam).</span><span class="sxs-lookup"><span data-stu-id="737ef-111">`S_OK` if the method completed successfully; otherwise, an HRESULT value that indicates failure (see [Common HRESULT Values](/windows/win32/seccrypto/common-hresult-values) for a list).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="737ef-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="737ef-112">Requirements</span></span>  
 <span data-ttu-id="737ef-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="737ef-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="737ef-114">**Hlavička:** MetaHost. h</span><span class="sxs-lookup"><span data-stu-id="737ef-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="737ef-115">**Knihovna:** Zahrnuto jako prostředek v knihovně MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="737ef-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="737ef-116">**Verze .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="737ef-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="737ef-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="737ef-117">See also</span></span>

- [<span data-ttu-id="737ef-118">StrongNameGetBlobFromImage – metoda</span><span class="sxs-lookup"><span data-stu-id="737ef-118">StrongNameGetBlobFromImage Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-strongnamegetblobfromimage-method.md)
- [<span data-ttu-id="737ef-119">ICLRStrongName – rozhraní</span><span class="sxs-lookup"><span data-stu-id="737ef-119">ICLRStrongName Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrstrongname-interface.md)
