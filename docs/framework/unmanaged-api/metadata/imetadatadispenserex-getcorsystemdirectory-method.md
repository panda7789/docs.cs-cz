---
title: IMetaDataDispenserEx::GetCORSystemDirectory – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.GetCORSystemDirectory
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::GetCORSystemDirectory
helpviewer_keywords:
- IMetaDataDispenserEx::GetCORSystemDirectory method [.NET Framework metadata]
- GetCORSystemDirectory method [.NET Framework metadata]
ms.assetid: d9e0f3b6-e106-4820-bada-5bfba34ce360
topic_type:
- apiref
ms.openlocfilehash: fb673666543bea3df44005ee3b20d311524f51d0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79175912"
---
# <a name="imetadatadispenserexgetcorsystemdirectory-method"></a><span data-ttu-id="253bd-102">IMetaDataDispenserEx::GetCORSystemDirectory – metoda</span><span class="sxs-lookup"><span data-stu-id="253bd-102">IMetaDataDispenserEx::GetCORSystemDirectory Method</span></span>
<span data-ttu-id="253bd-103">Získá adresář, který obsahuje aktuální clr (COMMON Language Runtime).</span><span class="sxs-lookup"><span data-stu-id="253bd-103">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="253bd-104">Tato metoda je podporována pouze pro použití mimoprocesladivé.</span><span class="sxs-lookup"><span data-stu-id="253bd-104">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="253bd-105">Pokud je volána z jiné součásti, vrátí E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="253bd-105">If called from another component, it will return E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="253bd-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="253bd-106">Syntax</span></span>  
  
```cpp  
HRESULT GetCORSystemDirectory (  
    [out] LPWSTR      szBuffer,
    [in]  DWORD       cchBuffer,
    [out] DWORD*      pchBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="253bd-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="253bd-107">Parameters</span></span>  
 `szBuffer`  
 <span data-ttu-id="253bd-108">[out] Vyrovnávací paměť pro příjem názvu adresáře.</span><span class="sxs-lookup"><span data-stu-id="253bd-108">[out] The buffer to receive the directory name.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="253bd-109">[v] Velikost v bajtů `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="253bd-109">[in] The size, in bytes, of `szBuffer`.</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="253bd-110">[out] Počet bajtů skutečně vrácených v `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="253bd-110">[out] The number of bytes actually returned in `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="253bd-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="253bd-111">Requirements</span></span>  
 <span data-ttu-id="253bd-112">**Platforma:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="253bd-112">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="253bd-113">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="253bd-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="253bd-114">**Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="253bd-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="253bd-115">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="253bd-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="253bd-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="253bd-116">See also</span></span>

- [<span data-ttu-id="253bd-117">IMetaDataDispenserEx – rozhraní</span><span class="sxs-lookup"><span data-stu-id="253bd-117">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="253bd-118">IMetaDataDispenser – rozhraní</span><span class="sxs-lookup"><span data-stu-id="253bd-118">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
