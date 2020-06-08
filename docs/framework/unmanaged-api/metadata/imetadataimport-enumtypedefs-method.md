---
title: IMetaDataImport::EnumTypeDefs – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.EnumTypeDefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::EnumTypeDefs
helpviewer_keywords:
- EnumTypeDefs method [.NET Framework metadata]
- IMetaDataImport::EnumTypeDefs method [.NET Framework metadata]
ms.assetid: 4e508711-da92-4381-aaf8-6803075cdaa2
topic_type:
- apiref
ms.openlocfilehash: cdfd4e10236d546af2555b125d44233172849a21
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503728"
---
# <a name="imetadataimportenumtypedefs-method"></a><span data-ttu-id="1379e-102">IMetaDataImport::EnumTypeDefs – metoda</span><span class="sxs-lookup"><span data-stu-id="1379e-102">IMetaDataImport::EnumTypeDefs Method</span></span>
<span data-ttu-id="1379e-103">Vytvoří výčet tokenů TypeDef reprezentujících všechny typy v rámci aktuálního oboru.</span><span class="sxs-lookup"><span data-stu-id="1379e-103">Enumerates TypeDef tokens representing all types within the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1379e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1379e-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumTypeDefs (  
   [out] HCORENUM   *phEnum,
   [in]  mdTypeDef  rTypeDefs[],  
   [in]  ULONG      cMax,
   [out] ULONG      *pcTypeDefs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1379e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1379e-105">Parameters</span></span>  
 `phEnum`  
 <span data-ttu-id="1379e-106">mimo Ukazatel na nový enumerátor.</span><span class="sxs-lookup"><span data-stu-id="1379e-106">[out] A pointer to the new enumerator.</span></span> <span data-ttu-id="1379e-107">Pro první volání této metody musí mít hodnotu NULL.</span><span class="sxs-lookup"><span data-stu-id="1379e-107">This must be NULL for the first call of this method.</span></span>  
  
 `rTypeDefs`  
 <span data-ttu-id="1379e-108">pro Pole použité pro ukládání tokenů TypeDef.</span><span class="sxs-lookup"><span data-stu-id="1379e-108">[in] The array used to store the TypeDef tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="1379e-109">pro Maximální velikost `rTypeDefs` pole.</span><span class="sxs-lookup"><span data-stu-id="1379e-109">[in] The maximum size of the `rTypeDefs` array.</span></span>  
  
 `pcTypeDefs`  
 <span data-ttu-id="1379e-110">mimo Počet vrácených tokenů TypeDef v `rTypeDefs` .</span><span class="sxs-lookup"><span data-stu-id="1379e-110">[out] The number of TypeDef tokens returned in `rTypeDefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1379e-111">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="1379e-111">Return Value</span></span>  
  
|<span data-ttu-id="1379e-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1379e-112">HRESULT</span></span>|<span data-ttu-id="1379e-113">Description</span><span class="sxs-lookup"><span data-stu-id="1379e-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="1379e-114">`EnumTypeDefs`úspěšně vráceno.</span><span class="sxs-lookup"><span data-stu-id="1379e-114">`EnumTypeDefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="1379e-115">Neexistují žádné tokeny k vytvoření výčtu.</span><span class="sxs-lookup"><span data-stu-id="1379e-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="1379e-116">V takovém případě `pcTypeDefs` je nula.</span><span class="sxs-lookup"><span data-stu-id="1379e-116">In that case, `pcTypeDefs` is zero.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1379e-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1379e-117">Remarks</span></span>  
 <span data-ttu-id="1379e-118">Token TypeDef představuje typ, jako je třída nebo rozhraní, a také libovolný typ přidaný prostřednictvím mechanismu rozšiřitelnosti.</span><span class="sxs-lookup"><span data-stu-id="1379e-118">The TypeDef token represents a type such as a class or an interface, as well as any type added via an extensibility mechanism.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1379e-119">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1379e-119">Requirements</span></span>  
 <span data-ttu-id="1379e-120">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1379e-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1379e-121">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="1379e-121">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1379e-122">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1379e-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1379e-123">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1379e-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1379e-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1379e-124">See also</span></span>

- [<span data-ttu-id="1379e-125">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1379e-125">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="1379e-126">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1379e-126">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
