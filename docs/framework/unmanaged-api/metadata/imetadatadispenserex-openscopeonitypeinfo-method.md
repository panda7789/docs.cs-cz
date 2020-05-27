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
ms.openlocfilehash: 91ef9eaa855ed841bc75bfaeead462f045eb1d8b
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007452"
---
# <a name="imetadatadispenserexopenscopeonitypeinfo-method"></a><span data-ttu-id="6bb1e-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="6bb1e-102">IMetaDataDispenserEx::OpenScopeOnITypeInfo Method</span></span>
<span data-ttu-id="6bb1e-103">Tato metoda není implementována.</span><span class="sxs-lookup"><span data-stu-id="6bb1e-103">This method is not implemented.</span></span> <span data-ttu-id="6bb1e-104">Při volání Vrátí E_NOTIMPL.</span><span class="sxs-lookup"><span data-stu-id="6bb1e-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bb1e-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6bb1e-105">Syntax</span></span>  
  
```cpp  
HRESULT OpenScopeOnITypeInfo (  
    [in]  ITypeInfo   *pITI,  
    [in]  DWORD       dwOpenFlags,  
    [in]  REFIID      riid,  
    [out] IUnknown    **ppIUnk  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6bb1e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6bb1e-106">Parameters</span></span>  
 `pITI`  
 <span data-ttu-id="6bb1e-107">pro Ukazatel na rozhraní [volání ITypeInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo) , které poskytuje informace o typu, na které se má obor otevřít.</span><span class="sxs-lookup"><span data-stu-id="6bb1e-107">[in] Pointer to an [ITypeInfo](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-itypeinfo) interface that provides the type information on which to open the scope.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="6bb1e-108">pro Příznaky režimu otevření.</span><span class="sxs-lookup"><span data-stu-id="6bb1e-108">[in] The open mode flags.</span></span>  
  
 `riid`  
 <span data-ttu-id="6bb1e-109">pro Požadované rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6bb1e-109">[in] The desired interface.</span></span>  
  
 `ppIUnk`  
 <span data-ttu-id="6bb1e-110">mimo Ukazatel na ukazatel na vrácené rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6bb1e-110">[out] Pointer to a pointer to the returned interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6bb1e-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6bb1e-111">Requirements</span></span>  
 <span data-ttu-id="6bb1e-112">**Platforma:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6bb1e-112">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bb1e-113">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="6bb1e-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6bb1e-114">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="6bb1e-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6bb1e-115">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bb1e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bb1e-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="6bb1e-116">See also</span></span>

- [<span data-ttu-id="6bb1e-117">IMetaDataDispenserEx – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6bb1e-117">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="6bb1e-118">IMetaDataDispenser – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6bb1e-118">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
