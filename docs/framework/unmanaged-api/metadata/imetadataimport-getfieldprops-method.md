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
ms.openlocfilehash: 2bd05b49c3d51ac13865997910c99cc0cd5ca2d9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84491241"
---
# <a name="imetadataimportgetfieldprops-method"></a><span data-ttu-id="19340-102">IMetaDataImport::GetFieldProps – metoda</span><span class="sxs-lookup"><span data-stu-id="19340-102">IMetaDataImport::GetFieldProps Method</span></span>
<span data-ttu-id="19340-103">Načte metadata přidružená k poli, na které odkazuje zadaný FieldDef token.</span><span class="sxs-lookup"><span data-stu-id="19340-103">Gets metadata associated with the field referenced by the specified FieldDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19340-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="19340-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="19340-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="19340-105">Parameters</span></span>  
 `mb`  
 <span data-ttu-id="19340-106">pro Token FieldDef, který představuje pole, pro které se mají získat přidružená metadata</span><span class="sxs-lookup"><span data-stu-id="19340-106">[in] A FieldDef token that represents the field to get associated metadata for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="19340-107">mimo Ukazatel na token TypeDef, který představuje typ třídy, do které pole patří.</span><span class="sxs-lookup"><span data-stu-id="19340-107">[out] A pointer to a TypeDef token that represents the type of the class that the field belongs to.</span></span>  
  
 `szField`  
 <span data-ttu-id="19340-108">mimo Název pole</span><span class="sxs-lookup"><span data-stu-id="19340-108">[out] The name of the field.</span></span>  
  
 `cchField`  
 <span data-ttu-id="19340-109">pro Velikost vyrovnávací paměti v různých znacích pro *szField*.</span><span class="sxs-lookup"><span data-stu-id="19340-109">[in] The size in wide characters of the buffer for *szField*.</span></span>  
  
 `pchField`  
 <span data-ttu-id="19340-110">mimo Skutečná velikost vrácené vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="19340-110">[out] The actual size of the returned buffer.</span></span>  
  
 `pdwAttr`  
 <span data-ttu-id="19340-111">mimo Příznaky přidružené k metadatům v poli</span><span class="sxs-lookup"><span data-stu-id="19340-111">[out] Flags associated with the field's metadata.</span></span>  
  
 `ppvSigBlob`  
 <span data-ttu-id="19340-112">pro Ukazatel na hodnotu binárních metadat, která popisuje pole.</span><span class="sxs-lookup"><span data-stu-id="19340-112">[in] A pointer to the binary metadata value that describes the field.</span></span>  
  
 `pcbSigBlob`  
 <span data-ttu-id="19340-113">mimo Velikost v bajtech `ppvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="19340-113">[out] The size in bytes of `ppvSigBlob`.</span></span>  
  
 `pdwCPlusTypeFlag`  
 <span data-ttu-id="19340-114">mimo Příznak, který určuje typ hodnoty pole.</span><span class="sxs-lookup"><span data-stu-id="19340-114">[out] A flag that specifies the value type of the field.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="19340-115">mimo Konstantní hodnota pro pole.</span><span class="sxs-lookup"><span data-stu-id="19340-115">[out] A constant value for the field.</span></span>  
  
 `pcchValue`  
 <span data-ttu-id="19340-116">mimo Velikost ve znakech `ppValue` nebo nula, pokud žádný řetězec neexistuje.</span><span class="sxs-lookup"><span data-stu-id="19340-116">[out] The size in chars of `ppValue`, or zero if no string exists.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19340-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="19340-117">Requirements</span></span>  
 <span data-ttu-id="19340-118">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19340-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19340-119">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="19340-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="19340-120">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="19340-120">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="19340-121">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19340-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19340-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="19340-122">See also</span></span>

- [<span data-ttu-id="19340-123">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="19340-123">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="19340-124">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="19340-124">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
