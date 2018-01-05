---
title: "IMetaDataDispenserEx::GetCORSystemDirectory – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenserEx.GetCORSystemDirectory
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenserEx::GetCORSystemDirectory
helpviewer_keywords:
- IMetaDataDispenserEx::GetCORSystemDirectory method [.NET Framework metadata]
- GetCORSystemDirectory method [.NET Framework metadata]
ms.assetid: d9e0f3b6-e106-4820-bada-5bfba34ce360
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e93f544e504949b496881369c15905ef43a0d2f6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadatadispenserexgetcorsystemdirectory-method"></a><span data-ttu-id="eb600-102">IMetaDataDispenserEx::GetCORSystemDirectory – metoda</span><span class="sxs-lookup"><span data-stu-id="eb600-102">IMetaDataDispenserEx::GetCORSystemDirectory Method</span></span>
<span data-ttu-id="eb600-103">Získá adresář, který obsahuje modul aktuální CLR (CLR).</span><span class="sxs-lookup"><span data-stu-id="eb600-103">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="eb600-104">Tato metoda podporuje jenom pro použití ladicí programy mimo proces.</span><span class="sxs-lookup"><span data-stu-id="eb600-104">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="eb600-105">Pokud volání z jiné komponenty, vrátí E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="eb600-105">If called from another component, it will return E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eb600-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eb600-106">Syntax</span></span>  
  
```  
HRESULT GetCORSystemDirectory (  
    [out] LPWSTR      szBuffer,   
    [in]  DWORD       cchBuffer,   
    [out] DWORD*      pchBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="eb600-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="eb600-107">Parameters</span></span>  
 `szBuffer`  
 <span data-ttu-id="eb600-108">[out] Vyrovnávací paměť pro příjem název adresáře.</span><span class="sxs-lookup"><span data-stu-id="eb600-108">[out] The buffer to receive the directory name.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="eb600-109">[v] Velikost v bajtech z `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="eb600-109">[in] The size, in bytes, of `szBuffer`.</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="eb600-110">[out] Počet bajtů ve skutečnosti, vrátí se v `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="eb600-110">[out] The number of bytes actually returned in `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eb600-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="eb600-111">Requirements</span></span>  
 <span data-ttu-id="eb600-112">**Platforma:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb600-112">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eb600-113">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="eb600-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="eb600-114">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="eb600-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="eb600-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eb600-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb600-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="eb600-116">See Also</span></span>  
 [<span data-ttu-id="eb600-117">IMetaDataDispenserEx – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eb600-117">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="eb600-118">IMetaDataDispenser – rozhraní</span><span class="sxs-lookup"><span data-stu-id="eb600-118">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
