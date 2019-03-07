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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 26a4ed5bc406645e662ded54374f0594d1e97524
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485418"
---
# <a name="imetadataimportgetcustomattributebyname-method"></a><span data-ttu-id="bc6ce-102">IMetaDataImport::GetCustomAttributeByName – metoda</span><span class="sxs-lookup"><span data-stu-id="bc6ce-102">IMetaDataImport::GetCustomAttributeByName Method</span></span>
<span data-ttu-id="bc6ce-103">Získá vlastní atribut zadaný název a vlastníka.</span><span class="sxs-lookup"><span data-stu-id="bc6ce-103">Gets the custom attribute, given its name and owner.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc6ce-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bc6ce-104">Syntax</span></span>  
  
```  
HRESULT GetCustomAttributeByName (  
   [in]  mdToken          tkObj,  
   [in]  LPCWSTR          szName,  
   [out] const void       **ppData,  
   [out] ULONG            *pcbData  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc6ce-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bc6ce-105">Parameters</span></span>  
 `tkObj`  
 <span data-ttu-id="bc6ce-106">[in] Token metadat představující objekt, který je vlastníkem vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="bc6ce-106">[in] A metadata token representing the object that owns the custom attribute.</span></span>  
  
 `szName`  
 <span data-ttu-id="bc6ce-107">[in] Název vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="bc6ce-107">[in] The name of the custom attribute.</span></span>  
  
 `ppData`  
 <span data-ttu-id="bc6ce-108">[out] Ukazatel na pole dat, která je hodnota vlastního atributu.</span><span class="sxs-lookup"><span data-stu-id="bc6ce-108">[out] A pointer to an array of data that is the value of the custom attribute.</span></span>  
  
 `pcbData`  
 <span data-ttu-id="bc6ce-109">[out] Velikost v bajtech dat vrácených v \*`ppData`.</span><span class="sxs-lookup"><span data-stu-id="bc6ce-109">[out] The size in bytes of the data returned in \*`ppData`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bc6ce-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bc6ce-110">Remarks</span></span>  
 <span data-ttu-id="bc6ce-111">Je možné definovat více vlastních atributů pro téhož vlastníka; může probíhat dokonce se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="bc6ce-111">It is legal to define multiple custom attributes for the same owner; they may even have the same name.</span></span> <span data-ttu-id="bc6ce-112">Ale `GetCustomAttributeByName` vrátí pouze jednu instanci.</span><span class="sxs-lookup"><span data-stu-id="bc6ce-112">However, `GetCustomAttributeByName` returns only one instance.</span></span> <span data-ttu-id="bc6ce-113">(`GetCustomAttributeByName` vrátí první instance, který nalezne.) Chcete-li vyhledat všechny instance vlastního atributu, zavolejte [imetadataimport::enumcustomattributes –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumcustomattributes-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="bc6ce-113">(`GetCustomAttributeByName` returns the first instance that it encounters.) To find all instances of a custom attribute, call the [IMetaDataImport::EnumCustomAttributes](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-enumcustomattributes-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc6ce-114">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bc6ce-114">Requirements</span></span>  
 <span data-ttu-id="bc6ce-115">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc6ce-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc6ce-116">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="bc6ce-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bc6ce-117">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bc6ce-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bc6ce-118">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc6ce-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc6ce-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bc6ce-119">See also</span></span>
- [<span data-ttu-id="bc6ce-120">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bc6ce-120">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="bc6ce-121">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bc6ce-121">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
