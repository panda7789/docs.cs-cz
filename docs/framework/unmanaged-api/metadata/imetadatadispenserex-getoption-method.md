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
ms.openlocfilehash: 832adacac4a6df9ccf21578538a1c557150f3ba1
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008778"
---
# <a name="imetadatadispenserexgetoption-method"></a><span data-ttu-id="85e6b-102">IMetaDataDispenserEx::GetOption – metoda</span><span class="sxs-lookup"><span data-stu-id="85e6b-102">IMetaDataDispenserEx::GetOption Method</span></span>
<span data-ttu-id="85e6b-103">Získá hodnotu zadané možnosti pro aktuální obor metadat.</span><span class="sxs-lookup"><span data-stu-id="85e6b-103">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="85e6b-104">Možnost určuje, jak jsou zpracovávány volání do aktuálního oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="85e6b-104">The option controls how calls to the current metadata scope are handled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85e6b-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="85e6b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetOption (  
    [in]  REFGUID         optionId,
    [out] const VARIANT   *pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="85e6b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="85e6b-106">Parameters</span></span>  
 `optionId`  
 <span data-ttu-id="85e6b-107">pro Ukazatel na identifikátor GUID, který určuje možnost, která má být načtena.</span><span class="sxs-lookup"><span data-stu-id="85e6b-107">[in] A pointer to a GUID that specifies the option to be retrieved.</span></span> <span data-ttu-id="85e6b-108">Seznam podporovaných identifikátorů GUID najdete v části s poznámkami.</span><span class="sxs-lookup"><span data-stu-id="85e6b-108">See the Remarks section for a list of supported GUIDs.</span></span>  
  
 `pValue`  
 <span data-ttu-id="85e6b-109">mimo Hodnota vrácené možnosti.</span><span class="sxs-lookup"><span data-stu-id="85e6b-109">[out] The value of the returned option.</span></span> <span data-ttu-id="85e6b-110">Typ této hodnoty bude varianta zadaného typu možnosti.</span><span class="sxs-lookup"><span data-stu-id="85e6b-110">The type of this value will be a variant of the specified option's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="85e6b-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="85e6b-111">Remarks</span></span>  
 <span data-ttu-id="85e6b-112">V následujícím seznamu jsou uvedeny identifikátory GUID, které jsou pro tuto metodu podporovány.</span><span class="sxs-lookup"><span data-stu-id="85e6b-112">The following list shows the GUIDs that are supported for this method.</span></span> <span data-ttu-id="85e6b-113">Popisy naleznete v tématu [IMetaDataDispenserEx:: SetOption –](imetadatadispenserex-setoption-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="85e6b-113">For descriptions, see the [IMetaDataDispenserEx::SetOption](imetadatadispenserex-setoption-method.md) method.</span></span> <span data-ttu-id="85e6b-114">Pokud není `optionId` v tomto seznamu, tato metoda vrátí hodnotu HRESULT `E_INVALIDARG` , což značí nesprávný parametr.</span><span class="sxs-lookup"><span data-stu-id="85e6b-114">If `optionId` is not in this list, this method returns HRESULT `E_INVALIDARG`, indicating an incorrect parameter.</span></span>  
  
- <span data-ttu-id="85e6b-115">MetaDataCheckDuplicatesFor</span><span class="sxs-lookup"><span data-stu-id="85e6b-115">MetaDataCheckDuplicatesFor</span></span>  
  
- <span data-ttu-id="85e6b-116">MetaDataRefToDefCheck</span><span class="sxs-lookup"><span data-stu-id="85e6b-116">MetaDataRefToDefCheck</span></span>  
  
- <span data-ttu-id="85e6b-117">MetaDataNotificationForTokenMovement</span><span class="sxs-lookup"><span data-stu-id="85e6b-117">MetaDataNotificationForTokenMovement</span></span>  
  
- <span data-ttu-id="85e6b-118">MetaDataSetENC</span><span class="sxs-lookup"><span data-stu-id="85e6b-118">MetaDataSetENC</span></span>  
  
- <span data-ttu-id="85e6b-119">MetaDataErrorIfEmitOutOfOrder</span><span class="sxs-lookup"><span data-stu-id="85e6b-119">MetaDataErrorIfEmitOutOfOrder</span></span>  
  
- <span data-ttu-id="85e6b-120">MetaDataGenerateTCEAdapters</span><span class="sxs-lookup"><span data-stu-id="85e6b-120">MetaDataGenerateTCEAdapters</span></span>  
  
- <span data-ttu-id="85e6b-121">MetaDataLinkerOptions</span><span class="sxs-lookup"><span data-stu-id="85e6b-121">MetaDataLinkerOptions</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85e6b-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="85e6b-122">Requirements</span></span>  
 <span data-ttu-id="85e6b-123">**Platforma:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85e6b-123">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85e6b-124">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="85e6b-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="85e6b-125">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="85e6b-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="85e6b-126">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85e6b-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85e6b-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="85e6b-127">See also</span></span>

- [<span data-ttu-id="85e6b-128">IMetaDataDispenserEx – rozhraní</span><span class="sxs-lookup"><span data-stu-id="85e6b-128">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="85e6b-129">IMetaDataDispenser – rozhraní</span><span class="sxs-lookup"><span data-stu-id="85e6b-129">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
