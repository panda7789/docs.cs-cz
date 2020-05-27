---
title: IMetaDataEmit::SetFieldProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.SetFieldProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::SetFieldProps
helpviewer_keywords:
- IMetaDataEmit::SetFieldProps method [.NET Framework metadata]
- SetFieldProps method [.NET Framework metadata]
ms.assetid: 47132dda-fa92-4bd1-ae4b-24cd9a60665a
topic_type:
- apiref
ms.openlocfilehash: 220556ec130c7bff7c413405820c4fee0582b051
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84008011"
---
# <a name="imetadataemitsetfieldprops-method"></a><span data-ttu-id="81e3e-102">IMetaDataEmit::SetFieldProps – metoda</span><span class="sxs-lookup"><span data-stu-id="81e3e-102">IMetaDataEmit::SetFieldProps Method</span></span>
<span data-ttu-id="81e3e-103">Nastaví nebo aktualizuje výchozí hodnotu pro pole, na které se odkazuje pomocí zadaného tokenu pole.</span><span class="sxs-lookup"><span data-stu-id="81e3e-103">Sets or updates the default value for the field referenced by the specified field token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81e3e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="81e3e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetFieldProps (  
    [in]  mdFieldDef  fd,
    [in]  DWORD       dwFieldFlags,
    [in]  DWORD       dwCPlusTypeFlag,
    [in]  void const  *pValue,
    [in]  ULONG       cchValue
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81e3e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="81e3e-105">Parameters</span></span>  
 `fd`  
 <span data-ttu-id="81e3e-106">pro Token pro cílové pole</span><span class="sxs-lookup"><span data-stu-id="81e3e-106">[in] The token for the target field.</span></span>  
  
 `dwFieldFlags`  
 <span data-ttu-id="81e3e-107">pro Atributy pole</span><span class="sxs-lookup"><span data-stu-id="81e3e-107">[in] Field attributes.</span></span> <span data-ttu-id="81e3e-108">Toto je Bitová maska `CorFieldAttr` hodnot.</span><span class="sxs-lookup"><span data-stu-id="81e3e-108">This is a bitmask of `CorFieldAttr` values.</span></span>  
  
 `dwCPlusTypeFlag`  
 <span data-ttu-id="81e3e-109">pro `ELEMENT_TYPE_` *\** Pro hodnotu konstanty.</span><span class="sxs-lookup"><span data-stu-id="81e3e-109">[in] The `ELEMENT_TYPE_`*\** for the constant value.</span></span> <span data-ttu-id="81e3e-110">Toto je `CorElementType` hodnota.</span><span class="sxs-lookup"><span data-stu-id="81e3e-110">This is a `CorElementType` value.</span></span> <span data-ttu-id="81e3e-111">Pokud konstanta není definována, nastavte tuto hodnotu na `ELEMENT_TYPE_END` .</span><span class="sxs-lookup"><span data-stu-id="81e3e-111">If a constant is not being defined, set this value to `ELEMENT_TYPE_END`.</span></span>  
  
 `pValue`  
 <span data-ttu-id="81e3e-112">pro Hodnota konstanty pro pole</span><span class="sxs-lookup"><span data-stu-id="81e3e-112">[in] The constant value for the field.</span></span>  
  
 `cchValue`  
 <span data-ttu-id="81e3e-113">pro Velikost (v Unicode znacích) `pValue` .</span><span class="sxs-lookup"><span data-stu-id="81e3e-113">[in] The size, in Unicode characters, of `pValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81e3e-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="81e3e-114">Requirements</span></span>  
 <span data-ttu-id="81e3e-115">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81e3e-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81e3e-116">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="81e3e-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="81e3e-117">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="81e3e-117">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="81e3e-118">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81e3e-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81e3e-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="81e3e-119">See also</span></span>

- [<span data-ttu-id="81e3e-120">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="81e3e-120">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="81e3e-121">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="81e3e-121">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
