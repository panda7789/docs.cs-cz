---
title: IMetaDataEmit2::DefineMethodSpec – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataEmit2.DefineMethodSpec
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit2::DefineMethodSpec
helpviewer_keywords:
- DefineMethodSpec method [.NET Framework metadata]
- IMetaDataEmit2::DefineMethodSpec method [.NET Framework metadata]
ms.assetid: 3c24e552-fc69-4971-b65a-a3e4b5f7f1e8
topic_type:
- apiref
ms.openlocfilehash: 8e067dc4943e6847177c13a683703e3a649a49e4
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503814"
---
# <a name="imetadataemit2definemethodspec-method"></a><span data-ttu-id="b97ff-102">IMetaDataEmit2::DefineMethodSpec – metoda</span><span class="sxs-lookup"><span data-stu-id="b97ff-102">IMetaDataEmit2::DefineMethodSpec Method</span></span>
<span data-ttu-id="b97ff-103">Vytvoří obecnou instanci metody a získá do definice token.</span><span class="sxs-lookup"><span data-stu-id="b97ff-103">Creates a generic instance of a method, and gets a token to the definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b97ff-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b97ff-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineMethodSpec (  
    [in]  mdToken           tkParent,
    [in]  PCCOR_SIGNATURE   pvSigBlob,
    [in]  ULONG             cbSigBlob,
    [out] mdMethodSpec      *pmi  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b97ff-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b97ff-105">Parameters</span></span>  
 `tkParent`  
 <span data-ttu-id="b97ff-106">pro Token pro metodu, pro kterou chcete vytvořit obecnou instanci.</span><span class="sxs-lookup"><span data-stu-id="b97ff-106">[in] A token for the method of which to create the generic instance.</span></span> <span data-ttu-id="b97ff-107">Token musí být typu `mdMethodDef` nebo `mdMemberRef` .</span><span class="sxs-lookup"><span data-stu-id="b97ff-107">The token must be of type `mdMethodDef` or `mdMemberRef`.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="b97ff-108">pro Ukazatel na binární podpis modelu COM+ metody.</span><span class="sxs-lookup"><span data-stu-id="b97ff-108">[in] A pointer to the binary COM+ signature of the method.</span></span>  
  
 `cbSibBlob`  
 <span data-ttu-id="b97ff-109">pro Velikost v bajtech `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="b97ff-109">[in] The size, in bytes, of `pvSigBlob`.</span></span>  
  
 `pmi`  
 <span data-ttu-id="b97ff-110">mimo Token definice podpisu metadat metody.</span><span class="sxs-lookup"><span data-stu-id="b97ff-110">[out] A token to the metadata signature definition of the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b97ff-111">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b97ff-111">Requirements</span></span>  
 <span data-ttu-id="b97ff-112">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b97ff-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b97ff-113">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b97ff-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b97ff-114">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="b97ff-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b97ff-115">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b97ff-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b97ff-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b97ff-116">See also</span></span>

- [<span data-ttu-id="b97ff-117">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b97ff-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="b97ff-118">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b97ff-118">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
