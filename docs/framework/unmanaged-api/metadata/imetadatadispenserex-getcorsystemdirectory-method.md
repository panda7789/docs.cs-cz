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
ms.openlocfilehash: 3dbfca942d61cd5667293d11f358f06bd000fa2e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59117998"
---
# <a name="imetadatadispenserexgetcorsystemdirectory-method"></a><span data-ttu-id="77dc2-102">IMetaDataDispenserEx::GetCORSystemDirectory – metoda</span><span class="sxs-lookup"><span data-stu-id="77dc2-102">IMetaDataDispenserEx::GetCORSystemDirectory Method</span></span>
<span data-ttu-id="77dc2-103">Získá adresář, který obsahuje aktuální modul (CLR).</span><span class="sxs-lookup"><span data-stu-id="77dc2-103">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="77dc2-104">Tato metoda je podporována pouze pro použití ladicími mimo proces.</span><span class="sxs-lookup"><span data-stu-id="77dc2-104">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="77dc2-105">Pokud je volána z jiné součásti, vrátí E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="77dc2-105">If called from another component, it will return E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77dc2-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="77dc2-106">Syntax</span></span>  
  
```  
HRESULT GetCORSystemDirectory (  
    [out] LPWSTR      szBuffer,   
    [in]  DWORD       cchBuffer,   
    [out] DWORD*      pchBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77dc2-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="77dc2-107">Parameters</span></span>  
 `szBuffer`  
 <span data-ttu-id="77dc2-108">[out] Vyrovnávací paměť pro příjem název adresáře.</span><span class="sxs-lookup"><span data-stu-id="77dc2-108">[out] The buffer to receive the directory name.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="77dc2-109">[in] Velikost v bajtech, z `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="77dc2-109">[in] The size, in bytes, of `szBuffer`.</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="77dc2-110">[out] Počet bajtů vrácených ve skutečnosti v `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="77dc2-110">[out] The number of bytes actually returned in `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77dc2-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="77dc2-111">Requirements</span></span>  
 <span data-ttu-id="77dc2-112">**Platforma:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="77dc2-112">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77dc2-113">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="77dc2-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="77dc2-114">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="77dc2-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="77dc2-115">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="77dc2-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="77dc2-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="77dc2-116">See also</span></span>

- [<span data-ttu-id="77dc2-117">IMetaDataDispenserEx – rozhraní</span><span class="sxs-lookup"><span data-stu-id="77dc2-117">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="77dc2-118">IMetaDataDispenser – rozhraní</span><span class="sxs-lookup"><span data-stu-id="77dc2-118">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
