---
title: IMetaDataImport::GetFieldProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetFieldProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetFieldProps
helpviewer_keywords:
- IMetaDataImport::GetFieldProps method [.NET Framework metadata]
- GetFieldProps method [.NET Framework metadata]
ms.assetid: 7b0e9b10-8cef-4ba6-8432-40bf63e65ab1
topic_type:
- apiref
ms.openlocfilehash: 8c3f98a124dbbcae3b0500932a2357ed1757951f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177235"
---
# <a name="imetadataimportgetfieldprops-method"></a><span data-ttu-id="258e6-102">IMetaDataImport::GetFieldProps – metoda</span><span class="sxs-lookup"><span data-stu-id="258e6-102">IMetaDataImport::GetFieldProps Method</span></span>
<span data-ttu-id="258e6-103">Získá metadata přidružená k poli, na které odkazuje zadaný token FieldDef.</span><span class="sxs-lookup"><span data-stu-id="258e6-103">Gets metadata associated with the field referenced by the specified FieldDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="258e6-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="258e6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFieldProps (  
   [in]  mdFieldDef        mb,
   [out] mdTypeDef         *pClass,  
   [out] LPWSTR            szField,  
   [in]  ULONG             cchField,
   [out] ULONG             *pchField,  
   [out] DWORD             *pdwAttr,  
   [in]  PCCOR_SIGNATURE   *ppvSigBlob,
   [out] ULONG             *pcbSigBlob,
   [out] DWORD             *pdwCPlusTypeFlag,
   [out] UVCP_CONSTANT     *ppValue,  
   [out] ULONG             *pcchValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="258e6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="258e6-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="258e6-106">[v] Token FieldDef, který představuje pole získat přidružená metadata.</span><span class="sxs-lookup"><span data-stu-id="258e6-106">[in] A FieldDef token that represents the field to get associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="258e6-107">[out] Ukazatel na token TypeDef, který představuje typ třídy, ke které pole patří.</span><span class="sxs-lookup"><span data-stu-id="258e6-107">[out] A pointer to a TypeDef token that represents the type of the class that the field belongs to.</span></span>  
  
 `szField`  
 <span data-ttu-id="258e6-108">[out] Název pole.</span><span class="sxs-lookup"><span data-stu-id="258e6-108">[out] The name of the field.</span></span>  
  
 `cchField`  
 <span data-ttu-id="258e6-109">[v] Velikost v široké znaky vyrovnávací paměti pro *szField*.</span><span class="sxs-lookup"><span data-stu-id="258e6-109">[in] The size in wide characters of the buffer for *szField*.</span></span>  
  
 `pchField`  
 <span data-ttu-id="258e6-110">[out] Skutečná velikost vrácené vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="258e6-110">[out] The actual size of the returned buffer.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="258e6-111">[out] Příznaky přidružené k metadatům pole.</span><span class="sxs-lookup"><span data-stu-id="258e6-111">[out] Flags associated with the field's metadata.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="258e6-112">[v] Ukazatel na binární hodnotu metadat, která popisuje pole.</span><span class="sxs-lookup"><span data-stu-id="258e6-112">[in] A pointer to the binary metadata value that describes the field.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="258e6-113">[out] Velikost v bajtů `ppvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="258e6-113">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="258e6-114">[out] Příznak, který určuje typ hodnoty pole.</span><span class="sxs-lookup"><span data-stu-id="258e6-114">[out] A flag that specifies the value type of the field.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="258e6-115">[out] Konstantní hodnota pole.</span><span class="sxs-lookup"><span data-stu-id="258e6-115">[out] A constant value for the field.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="258e6-116">[out] Velikost v znaku `ppValue`, nebo nula, pokud neexistuje žádný řetězec.</span><span class="sxs-lookup"><span data-stu-id="258e6-116">[out] The size in chars of `ppValue`, or zero if no string exists.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="258e6-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="258e6-117">Requirements</span></span>  
 <span data-ttu-id="258e6-118">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="258e6-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="258e6-119">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="258e6-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="258e6-120">**Knihovna:** Zahrnuto jako prostředek v souboru MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="258e6-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="258e6-121">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="258e6-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="258e6-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="258e6-122">See also</span></span>

- [<span data-ttu-id="258e6-123">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="258e6-123">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="258e6-124">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="258e6-124">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
