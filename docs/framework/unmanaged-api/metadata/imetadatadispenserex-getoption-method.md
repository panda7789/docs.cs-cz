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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59136627"
---
# <a name="imetadatadispenserexgetoption-method"></a><span data-ttu-id="2c980-102">IMetaDataDispenserEx::GetOption – metoda</span><span class="sxs-lookup"><span data-stu-id="2c980-102">IMetaDataDispenserEx::GetOption Method</span></span>
<span data-ttu-id="2c980-103">Získá hodnotu zadané možnosti pro aktuální obor metadat.</span><span class="sxs-lookup"><span data-stu-id="2c980-103">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="2c980-104">Možnost řídí, jak se zpracovává volání na aktuální metadat.</span><span class="sxs-lookup"><span data-stu-id="2c980-104">The option controls how calls to the current metadata scope are handled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c980-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2c980-105">Syntax</span></span>  
  
```  
HRESULT GetOption (  
    [in]  REFGUID         optionId,   
    [out] const VARIANT   *pValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c980-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="2c980-106">Parameters</span></span>  
 `optionId`  
 <span data-ttu-id="2c980-107">[in] Ukazatel na identifikátor GUID, který určuje možnost, která se má načíst.</span><span class="sxs-lookup"><span data-stu-id="2c980-107">[in] A pointer to a GUID that specifies the option to be retrieved.</span></span> <span data-ttu-id="2c980-108">Naleznete v části poznámky pro seznam podporovaných identifikátory GUID.</span><span class="sxs-lookup"><span data-stu-id="2c980-108">See the Remarks section for a list of supported GUIDs.</span></span>  
  
 `pValue`  
 <span data-ttu-id="2c980-109">[out] Hodnota vrácená možnost.</span><span class="sxs-lookup"><span data-stu-id="2c980-109">[out] The value of the returned option.</span></span> <span data-ttu-id="2c980-110">Typ této hodnoty bude hodnotu typu variant Zadaná možnost typu.</span><span class="sxs-lookup"><span data-stu-id="2c980-110">The type of this value will be a variant of the specified option's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c980-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2c980-111">Remarks</span></span>  
 <span data-ttu-id="2c980-112">Následující seznam uvádí identifikátory GUID, které jsou podporovány pro tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="2c980-112">The following list shows the GUIDs that are supported for this method.</span></span> <span data-ttu-id="2c980-113">Popisy najdete v [imetadatadispenserex::SetOption –](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="2c980-113">For descriptions, see the [IMetaDataDispenserEx::SetOption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) method.</span></span> <span data-ttu-id="2c980-114">Pokud `optionId` nejsou v tomto seznamu, tato metoda vrátí hodnotu HRESULT `E_INVALIDARG`, která nesprávný parametr.</span><span class="sxs-lookup"><span data-stu-id="2c980-114">If `optionId` is not in this list, this method returns HRESULT `E_INVALIDARG`, indicating an incorrect parameter.</span></span>  
  
-   <span data-ttu-id="2c980-115">MetaDataCheckDuplicatesFor</span><span class="sxs-lookup"><span data-stu-id="2c980-115">MetaDataCheckDuplicatesFor</span></span>  
  
-   <span data-ttu-id="2c980-116">MetaDataRefToDefCheck</span><span class="sxs-lookup"><span data-stu-id="2c980-116">MetaDataRefToDefCheck</span></span>  
  
-   <span data-ttu-id="2c980-117">MetaDataNotificationForTokenMovement</span><span class="sxs-lookup"><span data-stu-id="2c980-117">MetaDataNotificationForTokenMovement</span></span>  
  
-   <span data-ttu-id="2c980-118">MetaDataSetENC</span><span class="sxs-lookup"><span data-stu-id="2c980-118">MetaDataSetENC</span></span>  
  
-   <span data-ttu-id="2c980-119">MetaDataErrorIfEmitOutOfOrder</span><span class="sxs-lookup"><span data-stu-id="2c980-119">MetaDataErrorIfEmitOutOfOrder</span></span>  
  
-   <span data-ttu-id="2c980-120">MetaDataGenerateTCEAdapters</span><span class="sxs-lookup"><span data-stu-id="2c980-120">MetaDataGenerateTCEAdapters</span></span>  
  
-   <span data-ttu-id="2c980-121">MetaDataLinkerOptions</span><span class="sxs-lookup"><span data-stu-id="2c980-121">MetaDataLinkerOptions</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c980-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2c980-122">Requirements</span></span>  
 <span data-ttu-id="2c980-123">**Platforma:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c980-123">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c980-124">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="2c980-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2c980-125">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2c980-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2c980-126">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c980-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c980-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2c980-127">See also</span></span>

- [<span data-ttu-id="2c980-128">IMetaDataDispenserEx – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2c980-128">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)
- [<span data-ttu-id="2c980-129">IMetaDataDispenser – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2c980-129">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
