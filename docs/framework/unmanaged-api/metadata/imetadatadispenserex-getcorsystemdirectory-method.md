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
ms.openlocfilehash: a876d6ffb8331ee52789d5c146db7615d352dc1b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatadispenserexgetcorsystemdirectory-method"></a><span data-ttu-id="3667d-102">IMetaDataDispenserEx::GetCORSystemDirectory – metoda</span><span class="sxs-lookup"><span data-stu-id="3667d-102">IMetaDataDispenserEx::GetCORSystemDirectory Method</span></span>
<span data-ttu-id="3667d-103">Získá adresář, který obsahuje modul aktuální CLR (CLR).</span><span class="sxs-lookup"><span data-stu-id="3667d-103">Gets the directory that holds the current common language runtime (CLR).</span></span> <span data-ttu-id="3667d-104">Tato metoda podporuje jenom pro použití ladicí programy mimo proces.</span><span class="sxs-lookup"><span data-stu-id="3667d-104">This method is supported only for use by out-of-process debuggers.</span></span> <span data-ttu-id="3667d-105">Pokud volání z jiné komponenty, vrátí E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="3667d-105">If called from another component, it will return E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3667d-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3667d-106">Syntax</span></span>  
  
```  
HRESULT GetCORSystemDirectory (  
    [out] LPWSTR      szBuffer,   
    [in]  DWORD       cchBuffer,   
    [out] DWORD*      pchBuffer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3667d-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="3667d-107">Parameters</span></span>  
 `szBuffer`  
 <span data-ttu-id="3667d-108">[out] Vyrovnávací paměť pro příjem název adresáře.</span><span class="sxs-lookup"><span data-stu-id="3667d-108">[out] The buffer to receive the directory name.</span></span>  
  
 `cchBuffer`  
 <span data-ttu-id="3667d-109">[v] Velikost v bajtech z `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="3667d-109">[in] The size, in bytes, of `szBuffer`.</span></span>  
  
 `pchBuffer`  
 <span data-ttu-id="3667d-110">[out] Počet bajtů ve skutečnosti, vrátí se v `szBuffer`.</span><span class="sxs-lookup"><span data-stu-id="3667d-110">[out] The number of bytes actually returned in `szBuffer`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3667d-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3667d-111">Requirements</span></span>  
 <span data-ttu-id="3667d-112">**Platforma:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3667d-112">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3667d-113">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3667d-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3667d-114">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3667d-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3667d-115">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3667d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3667d-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="3667d-116">See Also</span></span>  
 [<span data-ttu-id="3667d-117">Imetadatadispenserex – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3667d-117">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="3667d-118">Imetadatadispenser – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3667d-118">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
