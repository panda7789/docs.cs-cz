---
title: IMetaDataDispenserEx::GetOption – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.GetOption
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::GetOption
helpviewer_keywords:
- GetOption method [.NET Framework metadata]
- IMetaDataDispenserEx::GetOption method [.NET Framework metadata]
ms.assetid: d7f794e5-8e25-4d65-850a-7c34fbfce87d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fe9bc9aea4ceb0f5b5c03416f43894b482c3294e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59136627"
---
# <a name="imetadatadispenserexgetoption-method"></a><span data-ttu-id="c2d43-102">IMetaDataDispenserEx::GetOption – metoda</span><span class="sxs-lookup"><span data-stu-id="c2d43-102">IMetaDataDispenserEx::GetOption Method</span></span>
<span data-ttu-id="c2d43-103">Získá hodnotu zadané možnosti pro aktuální obor metadat.</span><span class="sxs-lookup"><span data-stu-id="c2d43-103">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="c2d43-104">Možnost řídí, jak se zpracovává volání na aktuální metadat.</span><span class="sxs-lookup"><span data-stu-id="c2d43-104">The option controls how calls to the current metadata scope are handled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c2d43-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c2d43-105">Syntax</span></span>  
  
```  
HRESULT GetOption (  
    [in]  REFGUID         optionId,   
    [out] const VARIANT   *pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c2d43-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c2d43-106">Parameters</span></span>  
 `optionId`  
 <span data-ttu-id="c2d43-107">[in] Ukazatel na identifikátor GUID, který určuje možnost, která se má načíst.</span><span class="sxs-lookup"><span data-stu-id="c2d43-107">[in] A pointer to a GUID that specifies the option to be retrieved.</span></span> <span data-ttu-id="c2d43-108">Naleznete v části poznámky pro seznam podporovaných identifikátory GUID.</span><span class="sxs-lookup"><span data-stu-id="c2d43-108">See the Remarks section for a list of supported GUIDs.</span></span>  
  
 `pValue`  
 <span data-ttu-id="c2d43-109">[out] Hodnota vrácená možnost.</span><span class="sxs-lookup"><span data-stu-id="c2d43-109">[out] The value of the returned option.</span></span> <span data-ttu-id="c2d43-110">Typ této hodnoty bude hodnotu typu variant Zadaná možnost typu.</span><span class="sxs-lookup"><span data-stu-id="c2d43-110">The type of this value will be a variant of the specified option's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c2d43-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c2d43-111">Remarks</span></span>  
 <span data-ttu-id="c2d43-112">Následující seznam uvádí identifikátory GUID, které jsou podporovány pro tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="c2d43-112">The following list shows the GUIDs that are supported for this method.</span></span> <span data-ttu-id="c2d43-113">Popisy najdete v [imetadatadispenserex::SetOption –](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="c2d43-113">For descriptions, see the [IMetaDataDispenserEx::SetOption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) method.</span></span> <span data-ttu-id="c2d43-114">Pokud `optionId` nejsou v tomto seznamu, tato metoda vrátí hodnotu HRESULT `E_INVALIDARG`, která nesprávný parametr.</span><span class="sxs-lookup"><span data-stu-id="c2d43-114">If `optionId` is not in this list, this method returns HRESULT `E_INVALIDARG`, indicating an incorrect parameter.</span></span>  
  
-   <span data-ttu-id="c2d43-115">MetaDataCheckDuplicatesFor</span><span class="sxs-lookup"><span data-stu-id="c2d43-115">MetaDataCheckDuplicatesFor</span></span>  
  
-   <span data-ttu-id="c2d43-116">MetaDataRefToDefCheck</span><span class="sxs-lookup"><span data-stu-id="c2d43-116">MetaDataRefToDefCheck</span></span>  
  
-   <span data-ttu-id="c2d43-117">MetaDataNotificationForTokenMovement</span><span class="sxs-lookup"><span data-stu-id="c2d43-117">MetaDataNotificationForTokenMovement</span></span>  
  
-   <span data-ttu-id="c2d43-118">MetaDataSetENC</span><span class="sxs-lookup"><span data-stu-id="c2d43-118">MetaDataSetENC</span></span>  
  
-   <span data-ttu-id="c2d43-119">MetaDataErrorIfEmitOutOfOrder</span><span class="sxs-lookup"><span data-stu-id="c2d43-119">MetaDataErrorIfEmitOutOfOrder</span></span>  
  
-   <span data-ttu-id="c2d43-120">MetaDataGenerateTCEAdapters</span><span class="sxs-lookup"><span data-stu-id="c2d43-120">MetaDataGenerateTCEAdapters</span></span>  
  
-   <span data-ttu-id="c2d43-121">MetaDataLinkerOptions</span><span class="sxs-lookup"><span data-stu-id="c2d43-121">MetaDataLinkerOptions</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c2d43-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c2d43-122">Requirements</span></span>  
 <span data-ttu-id="c2d43-123">**Platforma:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c2d43-123">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c2d43-124">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c2d43-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c2d43-125">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c2d43-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="c2d43-126">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="c2d43-126">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c2d43-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c2d43-127">See also</span></span>

- [<span data-ttu-id="c2d43-128">IMetaDataDispenserEx – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c2d43-128">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="c2d43-129">IMetaDataDispenser – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c2d43-129">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
