---
title: IMetaDataImport::GetCustomAttributeByName – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetCustomAttributeByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetCustomAttributeByName
helpviewer_keywords:
- IMetaDataImport::GetCustomAttributeByName method [.NET Framework metadata]
- GetCustomAttributeByName method [.NET Framework metadata]
ms.assetid: 909aa530-2e3b-4d0a-a38a-a2750e535d7d
topic_type:
- apiref
ms.openlocfilehash: bd7ba7ff10918e5953ea8ae89a60af3115af48a3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74437683"
---
# <a name="imetadataimportgetcustomattributebyname-method"></a><span data-ttu-id="b6e87-102">IMetaDataImport::GetCustomAttributeByName – metoda</span><span class="sxs-lookup"><span data-stu-id="b6e87-102">IMetaDataImport::GetCustomAttributeByName Method</span></span>
<span data-ttu-id="b6e87-103">Získá vlastní atribut, který je dán jménem a vlastníkem.</span><span class="sxs-lookup"><span data-stu-id="b6e87-103">Gets the custom attribute, given its name and owner.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6e87-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b6e87-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCustomAttributeByName (  
   [in]  mdToken          tkObj,  
   [in]  LPCWSTR          szName,  
   [out] const void       **ppData,  
   [out] ULONG            *pcbData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b6e87-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b6e87-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="b6e87-106">pro Token metadat představující objekt vlastnící vlastní atribut.</span><span class="sxs-lookup"><span data-stu-id="b6e87-106">[in] A metadata token representing the object that owns the custom attribute.</span></span>  
  
 `szName`  
 <span data-ttu-id="b6e87-107">pro Název vlastního atributu</span><span class="sxs-lookup"><span data-stu-id="b6e87-107">[in] The name of the custom attribute.</span></span>  
  
 `ppData`  
 <span data-ttu-id="b6e87-108">mimo Ukazatel na pole dat, které je hodnotou vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="b6e87-108">[out] A pointer to an array of data that is the value of the custom attribute.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="b6e87-109">mimo Velikost v bajtech dat vrácených ve formátu \*`ppData`.</span><span class="sxs-lookup"><span data-stu-id="b6e87-109">[out] The size in bytes of the data returned in \*`ppData`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b6e87-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b6e87-110">Remarks</span></span>  
 <span data-ttu-id="b6e87-111">Je právní pro stejného vlastníka definovat více vlastních atributů; můžou mít i stejný název.</span><span class="sxs-lookup"><span data-stu-id="b6e87-111">It is legal to define multiple custom attributes for the same owner; they may even have the same name.</span></span> <span data-ttu-id="b6e87-112">`GetCustomAttributeByName` ale vrátí jenom jednu instanci.</span><span class="sxs-lookup"><span data-stu-id="b6e87-112">However, `GetCustomAttributeByName` returns only one instance.</span></span> <span data-ttu-id="b6e87-113">(`GetCustomAttributeByName` vrací první instanci, kterou nalezne.) Chcete-li najít všechny instance vlastního atributu, zavolejte metodu [IMetaDataImport:: EnumCustomAttributes –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumcustomattributes-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b6e87-113">(`GetCustomAttributeByName` returns the first instance that it encounters.) To find all instances of a custom attribute, call the [IMetaDataImport::EnumCustomAttributes](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumcustomattributes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b6e87-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b6e87-114">Requirements</span></span>  
 <span data-ttu-id="b6e87-115">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b6e87-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b6e87-116">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="b6e87-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="b6e87-117">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="b6e87-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="b6e87-118">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b6e87-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b6e87-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b6e87-119">See also</span></span>

- [<span data-ttu-id="b6e87-120">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b6e87-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="b6e87-121">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="b6e87-121">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
