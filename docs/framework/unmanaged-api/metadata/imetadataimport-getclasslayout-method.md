---
title: IMetaDataImport::GetClassLayout – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetClassLayout
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetClassLayout
helpviewer_keywords:
- IMetaDataImport::GetClassLayout method [.NET Framework metadata]
- GetClassLayout method, IMetaDataImport interface [.NET Framework metadata]
ms.assetid: 8f35414d-f40b-4b99-8768-9adb675c622a
topic_type:
- apiref
ms.openlocfilehash: 36c0ffef2d984604be4ae19899e8f3f912cee123
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491469"
---
# <a name="imetadataimportgetclasslayout-method"></a><span data-ttu-id="3aedb-102">IMetaDataImport::GetClassLayout – metoda</span><span class="sxs-lookup"><span data-stu-id="3aedb-102">IMetaDataImport::GetClassLayout Method</span></span>
<span data-ttu-id="3aedb-103">Získá informace o rozložení pro třídu, na kterou odkazuje zadaný token TypeDef.</span><span class="sxs-lookup"><span data-stu-id="3aedb-103">Gets layout information for the class referenced by the specified TypeDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3aedb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3aedb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClassLayout  (
   [in]  mdTypeDef          td,
   [out] DWORD              *pdwPackSize,  
   [out] COR_FIELD_OFFSET   rFieldOffset[],  
   [in]  ULONG              cMax,  
   [out] ULONG              *pcFieldOffset,  
   [out] ULONG              *pulClassSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3aedb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3aedb-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="3aedb-106">pro Token TypeDef pro třídu s rozložením, které má být vráceno.</span><span class="sxs-lookup"><span data-stu-id="3aedb-106">[in] The TypeDef token for the class with the layout to return.</span></span>  
  
 `pdwPackSize`  
 <span data-ttu-id="3aedb-107">mimo Jedna z hodnot 1, 2, 4, 8 nebo 16 představující velikost balíčku třídy.</span><span class="sxs-lookup"><span data-stu-id="3aedb-107">[out] One of the values 1, 2, 4, 8, or 16, representing the pack size of the class.</span></span>  
  
 `rFieldOffset`  
 <span data-ttu-id="3aedb-108">mimo Pole hodnot [COR_FIELD_OFFSET](cor-field-offset-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="3aedb-108">[out] An array of [COR_FIELD_OFFSET](cor-field-offset-structure.md) values.</span></span>  
  
 `cMax`  
 <span data-ttu-id="3aedb-109">pro Maximální velikost `rFieldOffset` pole.</span><span class="sxs-lookup"><span data-stu-id="3aedb-109">[in] The maximum size of the `rFieldOffset` array.</span></span>  
  
 `pcFieldOffset`  
 <span data-ttu-id="3aedb-110">mimo Počet elementů vrácených v `rFieldOffset` .</span><span class="sxs-lookup"><span data-stu-id="3aedb-110">[out] The number of elements returned in `rFieldOffset`.</span></span>  
  
 `pulClassSize`  
 <span data-ttu-id="3aedb-111">mimo Velikost v bajtech třídy reprezentované `td` .</span><span class="sxs-lookup"><span data-stu-id="3aedb-111">[out] The size in bytes of the class represented by `td`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3aedb-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3aedb-112">Requirements</span></span>  
 <span data-ttu-id="3aedb-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3aedb-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3aedb-114">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="3aedb-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3aedb-115">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3aedb-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3aedb-116">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3aedb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3aedb-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3aedb-117">See also</span></span>

- [<span data-ttu-id="3aedb-118">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3aedb-118">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="3aedb-119">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3aedb-119">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
