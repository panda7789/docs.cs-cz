---
title: IMetaDataImport::GetMethodProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetMethodProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetMethodProps
helpviewer_keywords:
- GetMethodProps method [.NET Framework metadata]
- IMetaDataImport::GetMethodProps method [.NET Framework metadata]
ms.assetid: e0667ef7-1d31-4c89-a2d3-d426f023f8d2
topic_type:
- apiref
ms.openlocfilehash: 3c7c3525f2f8753241c9a206e4cf5e552bf06efe
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503621"
---
# <a name="imetadataimportgetmethodprops-method"></a><span data-ttu-id="7893d-102">IMetaDataImport::GetMethodProps – metoda</span><span class="sxs-lookup"><span data-stu-id="7893d-102">IMetaDataImport::GetMethodProps Method</span></span>
<span data-ttu-id="7893d-103">Získá metadata přidružená k metodě, na kterou odkazuje zadaný token MethodDef.</span><span class="sxs-lookup"><span data-stu-id="7893d-103">Gets the metadata associated with the method referenced by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7893d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7893d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodProps (  
    [in]  mdMethodDef         mb,  
    [out] mdTypeDef           *pClass,  
    [out] LPWSTR              szMethod,  
    [in]  ULONG               cchMethod,  
    [out] ULONG               *pchMethod,  
    [out] DWORD               *pdwAttr,  
    [out] PCCOR_SIGNATURE     *ppvSigBlob,  
    [out] ULONG               *pcbSigBlob,  
    [out] ULONG               *pulCodeRVA,  
    [out] DWORD               *pdwImplFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7893d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7893d-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="7893d-106">pro Token MethodDef, který představuje metodu pro vrácení metadat.</span><span class="sxs-lookup"><span data-stu-id="7893d-106">[in] The MethodDef token that represents the method to return metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="7893d-107">mimo Ukazatel na token TypeDef, který představuje typ, který implementuje metodu.</span><span class="sxs-lookup"><span data-stu-id="7893d-107">[out] A Pointer to a TypeDef token that represents the type that implements the method.</span></span>  
  
 `szMethod`  
 <span data-ttu-id="7893d-108">mimo Ukazatel na vyrovnávací paměť, která má název metody.</span><span class="sxs-lookup"><span data-stu-id="7893d-108">[out] A Pointer to a buffer that has the method's name.</span></span>  
  
 `cchMethod`  
 <span data-ttu-id="7893d-109">pro Požadovaná velikost `szMethod` .</span><span class="sxs-lookup"><span data-stu-id="7893d-109">[in] The requested size of `szMethod`.</span></span>  
  
 `pchMethod`  
 <span data-ttu-id="7893d-110">mimo Ukazatel na velikost v rámci velkých písmen `szMethod` nebo v případě zkrácení, skutečný počet znaků v názvu metody.</span><span class="sxs-lookup"><span data-stu-id="7893d-110">[out] A Pointer to the size in wide characters of `szMethod`, or in the case of truncation, the actual number of wide characters in the method name.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="7893d-111">mimo Ukazatel na libovolný příznak spojený s metodou.</span><span class="sxs-lookup"><span data-stu-id="7893d-111">[out] A pointer to any flags associated with the method.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="7893d-112">mimo Ukazatel na binární podpis metadat metody.</span><span class="sxs-lookup"><span data-stu-id="7893d-112">[out] A pointer to the binary metadata signature of the method.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="7893d-113">mimo Ukazatel na velikost v bajtech `ppvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="7893d-113">[out] A Pointer to the size in bytes of `ppvSigBlob`.</span></span>  
  
 `pulCodeRVA`  
 <span data-ttu-id="7893d-114">mimo Ukazatel na relativní virtuální adresu metody.</span><span class="sxs-lookup"><span data-stu-id="7893d-114">[out] A pointer to the relative virtual address of the method.</span></span>  
  
 `pdwImplFlags`  
 <span data-ttu-id="7893d-115">mimo Ukazatel na libovolný příznak implementace pro metodu.</span><span class="sxs-lookup"><span data-stu-id="7893d-115">[out] A pointer to any implementation flags for the method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7893d-116">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7893d-116">Requirements</span></span>  
 <span data-ttu-id="7893d-117">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7893d-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7893d-118">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="7893d-118">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7893d-119">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="7893d-119">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7893d-120">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7893d-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7893d-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7893d-121">See also</span></span>

- [<span data-ttu-id="7893d-122">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7893d-122">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="7893d-123">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7893d-123">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
