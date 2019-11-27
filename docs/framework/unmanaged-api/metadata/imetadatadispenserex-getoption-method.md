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
ms.openlocfilehash: ab74b02df959fe6e6457273e67ba3b82ae6a015c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435993"
---
# <a name="imetadatadispenserexgetoption-method"></a><span data-ttu-id="bba77-102">IMetaDataDispenserEx::GetOption – metoda</span><span class="sxs-lookup"><span data-stu-id="bba77-102">IMetaDataDispenserEx::GetOption Method</span></span>
<span data-ttu-id="bba77-103">Získá hodnotu zadané možnosti pro aktuální obor metadat.</span><span class="sxs-lookup"><span data-stu-id="bba77-103">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="bba77-104">Možnost určuje, jak jsou zpracovávány volání do aktuálního oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="bba77-104">The option controls how calls to the current metadata scope are handled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bba77-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bba77-105">Syntax</span></span>  
  
```cpp  
HRESULT GetOption (  
    [in]  REFGUID         optionId,   
    [out] const VARIANT   *pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bba77-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="bba77-106">Parameters</span></span>  
 `optionId`  
 <span data-ttu-id="bba77-107">pro Ukazatel na identifikátor GUID, který určuje možnost, která má být načtena.</span><span class="sxs-lookup"><span data-stu-id="bba77-107">[in] A pointer to a GUID that specifies the option to be retrieved.</span></span> <span data-ttu-id="bba77-108">Seznam podporovaných identifikátorů GUID najdete v části s poznámkami.</span><span class="sxs-lookup"><span data-stu-id="bba77-108">See the Remarks section for a list of supported GUIDs.</span></span>  
  
 `pValue`  
 <span data-ttu-id="bba77-109">mimo Hodnota vrácené možnosti.</span><span class="sxs-lookup"><span data-stu-id="bba77-109">[out] The value of the returned option.</span></span> <span data-ttu-id="bba77-110">Typ této hodnoty bude varianta zadaného typu možnosti.</span><span class="sxs-lookup"><span data-stu-id="bba77-110">The type of this value will be a variant of the specified option's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bba77-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bba77-111">Remarks</span></span>  
 <span data-ttu-id="bba77-112">V následujícím seznamu jsou uvedeny identifikátory GUID, které jsou pro tuto metodu podporovány.</span><span class="sxs-lookup"><span data-stu-id="bba77-112">The following list shows the GUIDs that are supported for this method.</span></span> <span data-ttu-id="bba77-113">Popisy naleznete v tématu [IMetaDataDispenserEx:: SetOption –](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="bba77-113">For descriptions, see the [IMetaDataDispenserEx::SetOption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) method.</span></span> <span data-ttu-id="bba77-114">Pokud `optionId` není v tomto seznamu, vrátí tato metoda hodnotu HRESULT `E_INVALIDARG`, která označuje nesprávný parametr.</span><span class="sxs-lookup"><span data-stu-id="bba77-114">If `optionId` is not in this list, this method returns HRESULT `E_INVALIDARG`, indicating an incorrect parameter.</span></span>  
  
- <span data-ttu-id="bba77-115">MetaDataCheckDuplicatesFor</span><span class="sxs-lookup"><span data-stu-id="bba77-115">MetaDataCheckDuplicatesFor</span></span>  
  
- <span data-ttu-id="bba77-116">MetaDataRefToDefCheck</span><span class="sxs-lookup"><span data-stu-id="bba77-116">MetaDataRefToDefCheck</span></span>  
  
- <span data-ttu-id="bba77-117">MetaDataNotificationForTokenMovement</span><span class="sxs-lookup"><span data-stu-id="bba77-117">MetaDataNotificationForTokenMovement</span></span>  
  
- <span data-ttu-id="bba77-118">MetaDataSetENC</span><span class="sxs-lookup"><span data-stu-id="bba77-118">MetaDataSetENC</span></span>  
  
- <span data-ttu-id="bba77-119">MetaDataErrorIfEmitOutOfOrder</span><span class="sxs-lookup"><span data-stu-id="bba77-119">MetaDataErrorIfEmitOutOfOrder</span></span>  
  
- <span data-ttu-id="bba77-120">MetaDataGenerateTCEAdapters</span><span class="sxs-lookup"><span data-stu-id="bba77-120">MetaDataGenerateTCEAdapters</span></span>  
  
- <span data-ttu-id="bba77-121">MetaDataLinkerOptions</span><span class="sxs-lookup"><span data-stu-id="bba77-121">MetaDataLinkerOptions</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bba77-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bba77-122">Requirements</span></span>  
 <span data-ttu-id="bba77-123">**Platforma:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bba77-123">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bba77-124">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="bba77-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bba77-125">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="bba77-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bba77-126">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bba77-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bba77-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bba77-127">See also</span></span>

- [<span data-ttu-id="bba77-128">IMetaDataDispenserEx – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bba77-128">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="bba77-129">IMetaDataDispenser – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bba77-129">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
