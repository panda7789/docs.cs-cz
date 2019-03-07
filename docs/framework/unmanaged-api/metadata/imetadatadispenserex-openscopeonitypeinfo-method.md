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
ms.openlocfilehash: 122a31fab3bf7bf10eb2490a955fb8245ea0408b
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57471027"
---
# <a name="imetadatadispenserexopenscopeonitypeinfo-method"></a><span data-ttu-id="743fa-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="743fa-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo Method</span></span>
<span data-ttu-id="743fa-103">Tato metoda není implementována.</span><span class="sxs-lookup"><span data-stu-id="743fa-103">This method is not implemented.</span></span> <span data-ttu-id="743fa-104">Pokud je volána, vrátí E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="743fa-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="743fa-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="743fa-105">Syntax</span></span>  
  
```  
HRESULT OpenScopeOnITypeInfo (  
    [in]  ITypeInfo   *pITI,  
    [in]  DWORD       dwOpenFlags,  
    [in]  REFIID      riid,  
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="743fa-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="743fa-106">Parameters</span></span>  
 `pITI`  
 <span data-ttu-id="743fa-107">[in] Ukazatel [ITypeInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo) rozhraní, které poskytuje informace o typu, na kterém se má otevřít oboru.</span><span class="sxs-lookup"><span data-stu-id="743fa-107">[in] Pointer to an [ITypeInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo) interface that provides the type information on which to open the scope.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="743fa-108">[in] Režim otevření příznaky.</span><span class="sxs-lookup"><span data-stu-id="743fa-108">[in] The open mode flags.</span></span>  
  
 `riid`  
 <span data-ttu-id="743fa-109">[in] Požadované rozhraní.</span><span class="sxs-lookup"><span data-stu-id="743fa-109">[in] The desired interface.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="743fa-110">[out] Ukazatel na ukazatel na vrácené rozhraní.</span><span class="sxs-lookup"><span data-stu-id="743fa-110">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="743fa-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="743fa-111">Requirements</span></span>  
 <span data-ttu-id="743fa-112">**Platforma:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="743fa-112">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="743fa-113">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="743fa-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="743fa-114">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="743fa-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="743fa-115">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="743fa-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="743fa-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="743fa-116">See also</span></span>
- [<span data-ttu-id="743fa-117">IMetaDataDispenserEx – rozhraní</span><span class="sxs-lookup"><span data-stu-id="743fa-117">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="743fa-118">IMetaDataDispenser – rozhraní</span><span class="sxs-lookup"><span data-stu-id="743fa-118">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
