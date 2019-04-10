---
title: IMetaDataDispenserEx::OpenScopeOnITypeInfo – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.OpenScopeOnITypeInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::OpenScopeOnITypeInfo
helpviewer_keywords:
- OpenScopeOnITypeInfo method [.NET Framework metadata]
- IMetaDataDispenserEx::OpenScopeOnITypeInfo method [.NET Framework metadata]
ms.assetid: 3480bbdb-c442-44a0-b7c6-333354503c52
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: deecd9ed4161bbd72e97a6320188961ae76d1e7c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59218781"
---
# <a name="imetadatadispenserexopenscopeonitypeinfo-method"></a><span data-ttu-id="bee01-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="bee01-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo Method</span></span>
<span data-ttu-id="bee01-103">Tato metoda není implementována.</span><span class="sxs-lookup"><span data-stu-id="bee01-103">This method is not implemented.</span></span> <span data-ttu-id="bee01-104">Pokud je volána, vrátí E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="bee01-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bee01-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bee01-105">Syntax</span></span>  
  
```  
HRESULT OpenScopeOnITypeInfo (  
    [in]  ITypeInfo   *pITI,  
    [in]  DWORD       dwOpenFlags,  
    [in]  REFIID      riid,  
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bee01-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="bee01-106">Parameters</span></span>  
 `pITI`  
 <span data-ttu-id="bee01-107">[in] Ukazatel [ITypeInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo) rozhraní, které poskytuje informace o typu, na kterém se má otevřít oboru.</span><span class="sxs-lookup"><span data-stu-id="bee01-107">[in] Pointer to an [ITypeInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo) interface that provides the type information on which to open the scope.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="bee01-108">[in] Režim otevření příznaky.</span><span class="sxs-lookup"><span data-stu-id="bee01-108">[in] The open mode flags.</span></span>  
  
 `riid`  
 <span data-ttu-id="bee01-109">[in] Požadované rozhraní.</span><span class="sxs-lookup"><span data-stu-id="bee01-109">[in] The desired interface.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="bee01-110">[out] Ukazatel na ukazatel na vrácené rozhraní.</span><span class="sxs-lookup"><span data-stu-id="bee01-110">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bee01-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bee01-111">Requirements</span></span>  
 <span data-ttu-id="bee01-112">**Platforma:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bee01-112">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bee01-113">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="bee01-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bee01-114">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bee01-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="bee01-115">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="bee01-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bee01-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bee01-116">See also</span></span>

- [<span data-ttu-id="bee01-117">IMetaDataDispenserEx – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bee01-117">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="bee01-118">IMetaDataDispenser – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bee01-118">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
