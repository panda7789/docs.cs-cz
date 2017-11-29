---
title: "IMetaDataDispenserEx::GetOption – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataDispenserEx.GetOption
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataDispenserEx::GetOption
helpviewer_keywords:
- GetOption method [.NET Framework metadata]
- IMetaDataDispenserEx::GetOption method [.NET Framework metadata]
ms.assetid: d7f794e5-8e25-4d65-850a-7c34fbfce87d
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: fa9db222c81c2d6536b782c3e047e24c773bd018
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadatadispenserexgetoption-method"></a><span data-ttu-id="43ac9-102">IMetaDataDispenserEx::GetOption – metoda</span><span class="sxs-lookup"><span data-stu-id="43ac9-102">IMetaDataDispenserEx::GetOption Method</span></span>
<span data-ttu-id="43ac9-103">Získá hodnotu Zadaná možnost pro aktuální obor metadat.</span><span class="sxs-lookup"><span data-stu-id="43ac9-103">Gets the value of the specified option for the current metadata scope.</span></span> <span data-ttu-id="43ac9-104">Možnost určuje způsob zpracování volání do aktuálního oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="43ac9-104">The option controls how calls to the current metadata scope are handled.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43ac9-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="43ac9-105">Syntax</span></span>  
  
```  
HRESULT GetOption (  
    [in]  REFGUID         optionId,   
    [out] const VARIANT   *pValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="43ac9-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="43ac9-106">Parameters</span></span>  
 `optionId`  
 <span data-ttu-id="43ac9-107">[v] Ukazatel na identifikátor GUID, který určuje možnosti, které mají být načteny.</span><span class="sxs-lookup"><span data-stu-id="43ac9-107">[in] A pointer to a GUID that specifies the option to be retrieved.</span></span> <span data-ttu-id="43ac9-108">Najdete v části poznámky seznam podporovaných identifikátory GUID.</span><span class="sxs-lookup"><span data-stu-id="43ac9-108">See the Remarks section for a list of supported GUIDs.</span></span>  
  
 `pValue`  
 <span data-ttu-id="43ac9-109">[out] Hodnota vrácená možnost.</span><span class="sxs-lookup"><span data-stu-id="43ac9-109">[out] The value of the returned option.</span></span> <span data-ttu-id="43ac9-110">Typ této hodnoty bude hodnotu typu variant Zadaná možnost typu.</span><span class="sxs-lookup"><span data-stu-id="43ac9-110">The type of this value will be a variant of the specified option's type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="43ac9-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="43ac9-111">Remarks</span></span>  
 <span data-ttu-id="43ac9-112">V následujícím seznamu jsou identifikátory GUID, které jsou podporovány pro tuto metodu.</span><span class="sxs-lookup"><span data-stu-id="43ac9-112">The following list shows the GUIDs that are supported for this method.</span></span> <span data-ttu-id="43ac9-113">Popis najdete v tématu [imetadatadispenserex::SetOption –](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="43ac9-113">For descriptions, see the [IMetaDataDispenserEx::SetOption](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-setoption-method.md) method.</span></span> <span data-ttu-id="43ac9-114">Pokud `optionId` nejsou v tomto seznamu, tato metoda vrátí hodnotu HRESULT `E_INVALIDARG`, která určuje nesprávný parametr.</span><span class="sxs-lookup"><span data-stu-id="43ac9-114">If `optionId` is not in this list, this method returns HRESULT `E_INVALIDARG`, indicating an incorrect parameter.</span></span>  
  
-   <span data-ttu-id="43ac9-115">MetaDataCheckDuplicatesFor</span><span class="sxs-lookup"><span data-stu-id="43ac9-115">MetaDataCheckDuplicatesFor</span></span>  
  
-   <span data-ttu-id="43ac9-116">MetaDataRefToDefCheck</span><span class="sxs-lookup"><span data-stu-id="43ac9-116">MetaDataRefToDefCheck</span></span>  
  
-   <span data-ttu-id="43ac9-117">MetaDataNotificationForTokenMovement</span><span class="sxs-lookup"><span data-stu-id="43ac9-117">MetaDataNotificationForTokenMovement</span></span>  
  
-   <span data-ttu-id="43ac9-118">MetaDataSetENC</span><span class="sxs-lookup"><span data-stu-id="43ac9-118">MetaDataSetENC</span></span>  
  
-   <span data-ttu-id="43ac9-119">MetaDataErrorIfEmitOutOfOrder</span><span class="sxs-lookup"><span data-stu-id="43ac9-119">MetaDataErrorIfEmitOutOfOrder</span></span>  
  
-   <span data-ttu-id="43ac9-120">MetaDataGenerateTCEAdapters</span><span class="sxs-lookup"><span data-stu-id="43ac9-120">MetaDataGenerateTCEAdapters</span></span>  
  
-   <span data-ttu-id="43ac9-121">MetaDataLinkerOptions</span><span class="sxs-lookup"><span data-stu-id="43ac9-121">MetaDataLinkerOptions</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43ac9-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="43ac9-122">Requirements</span></span>  
 <span data-ttu-id="43ac9-123">**Platforma:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43ac9-123">**Platform:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43ac9-124">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="43ac9-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="43ac9-125">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="43ac9-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="43ac9-126">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43ac9-126">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43ac9-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="43ac9-127">See Also</span></span>  
 [<span data-ttu-id="43ac9-128">Imetadatadispenserex – rozhraní</span><span class="sxs-lookup"><span data-stu-id="43ac9-128">IMetaDataDispenserEx Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenserex-interface.md)  
 [<span data-ttu-id="43ac9-129">Imetadatadispenser – rozhraní</span><span class="sxs-lookup"><span data-stu-id="43ac9-129">IMetaDataDispenser Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatadispenser-interface.md)
