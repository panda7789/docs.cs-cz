---
title: IMetaDataTables2::GetMetaDataStreamInfo – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables2.GetMetaDataStreamInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables2::GetMetaDataStreamInfo
helpviewer_keywords:
- GetMetaDataStreamInfo method [.NET Framework metadata]
- IMetaDataTables2::GetMetaDataStreamInfo method [.NET Framework metadata]
ms.assetid: 8b280627-cc74-4789-95da-1fefc966de05
topic_type:
- apiref
ms.openlocfilehash: 7d39d089c348b7320651ed21ea14ba07d7877fd4
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501092"
---
# <a name="imetadatatables2getmetadatastreaminfo-method"></a><span data-ttu-id="57318-102">IMetaDataTables2::GetMetaDataStreamInfo – metoda</span><span class="sxs-lookup"><span data-stu-id="57318-102">IMetaDataTables2::GetMetaDataStreamInfo Method</span></span>
<span data-ttu-id="57318-103">Získá název, velikost a obsah datového proudu metadat v zadaném indexu.</span><span class="sxs-lookup"><span data-stu-id="57318-103">Gets the name, size, and contents of the metadata stream at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57318-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="57318-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMetaDataStreamInfo (  
   [in]  ULONG        ix,  
   [out] const char   **ppchName,  
   [out] const void   **ppv,  
   [out] ULONG        *pcb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57318-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="57318-105">Parameters</span></span>  
 `ix`  
 <span data-ttu-id="57318-106">pro Index požadovaného streamu metadat.</span><span class="sxs-lookup"><span data-stu-id="57318-106">[in] The index of the requested metadata stream.</span></span>  
  
 `ppchName`  
 <span data-ttu-id="57318-107">mimo Ukazatel na název datového proudu.</span><span class="sxs-lookup"><span data-stu-id="57318-107">[out] A pointer to the name of the stream.</span></span>  
  
 `ppv`  
 <span data-ttu-id="57318-108">mimo Ukazatel na datový proud metadat.</span><span class="sxs-lookup"><span data-stu-id="57318-108">[out] A pointer to the metadata stream.</span></span>  
  
 `pcb`  
 <span data-ttu-id="57318-109">mimo Velikost v bajtech `ppv` .</span><span class="sxs-lookup"><span data-stu-id="57318-109">[out] The size, in bytes, of `ppv`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57318-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="57318-110">Requirements</span></span>  
 <span data-ttu-id="57318-111">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57318-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57318-112">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="57318-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="57318-113">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="57318-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="57318-114">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57318-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57318-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="57318-115">See also</span></span>

- [<span data-ttu-id="57318-116">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="57318-116">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
- [<span data-ttu-id="57318-117">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="57318-117">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
