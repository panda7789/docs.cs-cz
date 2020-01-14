---
title: IMetaDataTables::GetNextUserString – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetNextUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetNextUserString
helpviewer_keywords:
- GetNextUserString method [.NET Framework metadata]
- IMetaDataTables::GetNextUserString method [.NET Framework metadata]
ms.assetid: b7cb40ee-67b7-4f4e-8dcc-ee7ac8bc986b
topic_type:
- apiref
ms.openlocfilehash: 6522dbc8e49d612fc4c0d9597a9b5f12edb2cfe1
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937777"
---
# <a name="imetadatatablesgetnextuserstring-method"></a><span data-ttu-id="f3b0c-102">IMetaDataTables::GetNextUserString – metoda</span><span class="sxs-lookup"><span data-stu-id="f3b0c-102">IMetaDataTables::GetNextUserString Method</span></span>
<span data-ttu-id="f3b0c-103">Získá index řádku, který obsahuje další pevně zakódovaný řetězec ve sloupci aktuální tabulky.</span><span class="sxs-lookup"><span data-stu-id="f3b0c-103">Gets the index of the row that contains the next hard-coded string in the current table column.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3b0c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3b0c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNextUserString (  
    [in]  ULONG   ixUserString,  
    [out] ULONG   *pNext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f3b0c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f3b0c-105">Parameters</span></span>  
 `ixUserString`  
 <span data-ttu-id="f3b0c-106">pro Hodnota indexu z aktuálního sloupce řetězce.</span><span class="sxs-lookup"><span data-stu-id="f3b0c-106">[in] An index value from the current string column.</span></span>  
  
 `pNext`  
 <span data-ttu-id="f3b0c-107">mimo Ukazatel na index řádku dalšího řetězce ve sloupci</span><span class="sxs-lookup"><span data-stu-id="f3b0c-107">[out] A pointer to the row index of the next string in the column.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f3b0c-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f3b0c-108">Remarks</span></span>  
 <span data-ttu-id="f3b0c-109">Nedoporučujeme používat tuto metodu, protože nevrací konzistentní výsledky.</span><span class="sxs-lookup"><span data-stu-id="f3b0c-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="f3b0c-110">Informace o tabulce identifikátorů GUID najdete v dokumentaci k Common Language Infrastructure (CLI), zejména v oddílu oddíl II: definice metadat a sémantika.</span><span class="sxs-lookup"><span data-stu-id="f3b0c-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="f3b0c-111">Dokumentace je k dispozici online; viz [ECMA C# a Common Language Infrastructure standardy](../../../standard/components.md#applicable-standards) a [standardní ECMA-335-Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span><span class="sxs-lookup"><span data-stu-id="f3b0c-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](../../../standard/components.md#applicable-standards) and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3b0c-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f3b0c-112">Requirements</span></span>  
 <span data-ttu-id="f3b0c-113">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f3b0c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f3b0c-114">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="f3b0c-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="f3b0c-115">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="f3b0c-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="f3b0c-116">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f3b0c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3b0c-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f3b0c-117">See also</span></span>

- [<span data-ttu-id="f3b0c-118">IMetaDataTables – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f3b0c-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)
- [<span data-ttu-id="f3b0c-119">IMetaDataTables2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="f3b0c-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
