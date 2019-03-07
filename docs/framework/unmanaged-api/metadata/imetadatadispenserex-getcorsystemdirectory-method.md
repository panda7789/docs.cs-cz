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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bb61dbcee1851ebe70c1dc0138e14aaa7a08d901
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468686"
---
# <a name="imetadatadispenserexgetcorsystemdirectory-method"></a><span data-ttu-id="2e891-102">IMetaDataDispenserEx::GetCORSystemDirectory – metoda</span><span class="sxs-lookup"><span data-stu-id="2e891-102">IMetaDataDispenserEx::GetCORSystemDirectory Method</span></span>
<span data-ttu-id="2e891-103">Získá adresář, který obsahuje aktuální modul (CLR).</span><span class="sxs-lookup"><span data-stu-id="2e891-103">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="2e891-104">Tato metoda je podporována pouze pro použití ladicími mimo proces.</span><span class="sxs-lookup"><span data-stu-id="2e891-104">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="2e891-105">Pokud je volána z jiné součásti, vrátí E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="2e891-105">If called from another component, it will return E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e891-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2e891-106">Syntax</span></span>  
  
```  
HRESULT GetCORSystemDirectory (  
    [out] LPWSTR      szBuffer,   
    [in]  DWORD       cchBuffer,   
    [out] DWORD*      pchBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2e891-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="2e891-107">Parameters</span></span>  
 `szBuffer`  
 <span data-ttu-id="2e891-108">[out] Vyrovnávací paměť pro příjem název adresáře.</span><span class="sxs-lookup"><span data-stu-id="2e891-108">[out] The buffer to receive the directory name.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="2e891-109">[in] Velikost v bajtech, z `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="2e891-109">[in] The size, in bytes, of `szBuffer`.</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="2e891-110">[out] Počet bajtů vrácených ve skutečnosti v `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="2e891-110">[out] The number of bytes actually returned in `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2e891-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2e891-111">Requirements</span></span>  
 <span data-ttu-id="2e891-112">**Platforma:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e891-112">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e891-113">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2e891-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2e891-114">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2e891-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2e891-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e891-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e891-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2e891-116">See also</span></span>
- [<span data-ttu-id="2e891-117">IMetaDataDispenserEx – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e891-117">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="2e891-118">IMetaDataDispenser – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2e891-118">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
