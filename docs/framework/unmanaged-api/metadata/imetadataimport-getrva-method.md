---
title: IMetaDataImport::GetRVA – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetRVA
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetRVA
helpviewer_keywords:
- GetRVA method [.NET Framework metadata]
- IMetaDataImport::GetRVA method [.NET Framework metadata]
ms.assetid: ea422217-988b-4acd-b2db-c55357938275
topic_type:
- apiref
ms.openlocfilehash: 58ab9ee9381fce4d7af1910df6c8d3bb813bcf13
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490888"
---
# <a name="imetadataimportgetrva-method"></a><span data-ttu-id="1488d-102">IMetaDataImport::GetRVA – metoda</span><span class="sxs-lookup"><span data-stu-id="1488d-102">IMetaDataImport::GetRVA Method</span></span>
<span data-ttu-id="1488d-103">Získá relativní virtuální adresu (RVA) a příznaky implementace metody nebo pole reprezentované zadaným tokenem.</span><span class="sxs-lookup"><span data-stu-id="1488d-103">Gets the relative virtual address (RVA) and the implementation flags of the method or field represented by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1488d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1488d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRVA (  
   [in]  mdToken     tk,
   [out] ULONG       *pulCodeRVA,
   [out]  DWORD      *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1488d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1488d-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="1488d-106">pro Token metadat MethodDef nebo FieldDef, který představuje objekt kódu, pro který má být vrácena adresa RVA.</span><span class="sxs-lookup"><span data-stu-id="1488d-106">[in] A MethodDef or FieldDef metadata token that represents the code object to return the RVA for.</span></span> <span data-ttu-id="1488d-107">Pokud je tokenem FieldDef, musí být pole globální proměnná.</span><span class="sxs-lookup"><span data-stu-id="1488d-107">If the token is a FieldDef, the field must be a global variable.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="1488d-108">mimo Ukazatel na relativní virtuální adresu objektu kódu reprezentovaného tokenem.</span><span class="sxs-lookup"><span data-stu-id="1488d-108">[out] A pointer to the relative virtual address of the code object represented by the token.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="1488d-109">mimo Ukazatel na příznaky implementace pro metodu.</span><span class="sxs-lookup"><span data-stu-id="1488d-109">[out] A pointer to the implementation flags for the method.</span></span> <span data-ttu-id="1488d-110">Tato hodnota je Bitová maska z výčtu [CorMethodImpl –](cormethodimpl-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="1488d-110">This value is a bitmask from the [CorMethodImpl](cormethodimpl-enumeration.md) enumeration.</span></span> <span data-ttu-id="1488d-111">Hodnota `pdwImplFlags` je platná pouze v případě `tk` , že je to token MethodDef.</span><span class="sxs-lookup"><span data-stu-id="1488d-111">The value of `pdwImplFlags` is valid only if `tk` is a MethodDef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1488d-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1488d-112">Requirements</span></span>  
 <span data-ttu-id="1488d-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1488d-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1488d-114">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="1488d-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1488d-115">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1488d-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1488d-116">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1488d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1488d-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1488d-117">See also</span></span>

- [<span data-ttu-id="1488d-118">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1488d-118">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="1488d-119">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="1488d-119">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
