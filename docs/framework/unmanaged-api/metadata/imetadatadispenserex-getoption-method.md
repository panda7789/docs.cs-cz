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
ms.openlocfilehash: 816e2f2dc7d4d00f74f67720ee45d7b3483e57fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177722"
---
# <a name="imetadatadispenserexgetoption-method"></a><span data-ttu-id="0de4c-102">IMetaDataDispenserEx::GetOption – metoda</span><span class="sxs-lookup"><span data-stu-id="0de4c-102">IMetaDataDispenserEx::GetOption Method</span></span>
<span data-ttu-id="0de4c-103">Získá hodnotu zadané možnosti pro aktuální obor metadat.</span><span class="sxs-lookup"><span data-stu-id="0de4c-103">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="0de4c-104">Tato možnost určuje, jak jsou zpracována volání aktuálního oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="0de4c-104">The option controls how calls to the current metadata scope are handled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0de4c-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0de4c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetOption (  
    [in]  REFGUID         optionId,
    [out] const VARIANT   *pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0de4c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="0de4c-106">Parameters</span></span>  
 `optionId`  
 <span data-ttu-id="0de4c-107">[v] Ukazatel na identifikátor GUID, který určuje možnost, která má být načtena.</span><span class="sxs-lookup"><span data-stu-id="0de4c-107">[in] A pointer to a GUID that specifies the option to be retrieved.</span></span> <span data-ttu-id="0de4c-108">Seznam podporovaných identifikátorů GUID naleznete v části Poznámky.</span><span class="sxs-lookup"><span data-stu-id="0de4c-108">See the Remarks section for a list of supported GUIDs.</span></span>  
  
 `pValue`  
 <span data-ttu-id="0de4c-109">[out] Hodnota vrácené možnosti.</span><span class="sxs-lookup"><span data-stu-id="0de4c-109">[out] The value of the returned option.</span></span> <span data-ttu-id="0de4c-110">Typ této hodnoty bude variantou typu zadané možnosti.</span><span class="sxs-lookup"><span data-stu-id="0de4c-110">The type of this value will be a variant of the specified option's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0de4c-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0de4c-111">Remarks</span></span>  
 <span data-ttu-id="0de4c-112">V následujícím seznamu jsou uvedeny identifikátory GUID, které jsou pro tuto metodu podporovány.</span><span class="sxs-lookup"><span data-stu-id="0de4c-112">The following list shows the GUIDs that are supported for this method.</span></span> <span data-ttu-id="0de4c-113">Popisy naleznete v metodě [IMetaDataDispenserEx::SetOption.](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md)</span><span class="sxs-lookup"><span data-stu-id="0de4c-113">For descriptions, see the [IMetaDataDispenserEx::SetOption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) method.</span></span> <span data-ttu-id="0de4c-114">Pokud `optionId` není v tomto seznamu, tato `E_INVALIDARG`metoda vrátí HRESULT , označující nesprávný parametr.</span><span class="sxs-lookup"><span data-stu-id="0de4c-114">If `optionId` is not in this list, this method returns HRESULT `E_INVALIDARG`, indicating an incorrect parameter.</span></span>  
  
- <span data-ttu-id="0de4c-115">MetaDataCheckDuplicatesFor</span><span class="sxs-lookup"><span data-stu-id="0de4c-115">MetaDataCheckDuplicatesFor</span></span>  
  
- <span data-ttu-id="0de4c-116">MetaDataRefToDefCheck</span><span class="sxs-lookup"><span data-stu-id="0de4c-116">MetaDataRefToDefCheck</span></span>  
  
- <span data-ttu-id="0de4c-117">MetaDataNotificationForTokenMovement</span><span class="sxs-lookup"><span data-stu-id="0de4c-117">MetaDataNotificationForTokenMovement</span></span>  
  
- <span data-ttu-id="0de4c-118">MetaDatasetENC</span><span class="sxs-lookup"><span data-stu-id="0de4c-118">MetaDataSetENC</span></span>  
  
- <span data-ttu-id="0de4c-119">MetaDataErrorIfEmitOutOfOrder</span><span class="sxs-lookup"><span data-stu-id="0de4c-119">MetaDataErrorIfEmitOutOfOrder</span></span>  
  
- <span data-ttu-id="0de4c-120">Adaptéry MetaDataGenerateTCE</span><span class="sxs-lookup"><span data-stu-id="0de4c-120">MetaDataGenerateTCEAdapters</span></span>  
  
- <span data-ttu-id="0de4c-121">Možnosti metadatalinkeru</span><span class="sxs-lookup"><span data-stu-id="0de4c-121">MetaDataLinkerOptions</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0de4c-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0de4c-122">Requirements</span></span>  
 <span data-ttu-id="0de4c-123">**Platforma:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0de4c-123">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0de4c-124">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="0de4c-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0de4c-125">**Knihovna:** Používá se jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0de4c-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0de4c-126">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0de4c-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0de4c-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="0de4c-127">See also</span></span>

- [<span data-ttu-id="0de4c-128">IMetaDataDispenserEx – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0de4c-128">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="0de4c-129">IMetaDataDispenser – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0de4c-129">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
