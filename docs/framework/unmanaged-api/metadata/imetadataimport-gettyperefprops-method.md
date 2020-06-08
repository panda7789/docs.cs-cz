---
title: IMetaDataImport::GetTypeRefProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetTypeRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetTypeRefProps
helpviewer_keywords:
- IMetaDataImport::GetTypeRefProps method [.NET Framework metadata]
- GetTypeRefProps method [.NET Framework metadata]
ms.assetid: 01837955-ce1e-4068-b338-fd473bd77d1d
topic_type:
- apiref
ms.openlocfilehash: 273922e00c3e5319d5a03652cc77b69f4479ea67
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503520"
---
# <a name="imetadataimportgettyperefprops-method"></a><span data-ttu-id="cb1ae-102">IMetaDataImport::GetTypeRefProps – metoda</span><span class="sxs-lookup"><span data-stu-id="cb1ae-102">IMetaDataImport::GetTypeRefProps Method</span></span>
<span data-ttu-id="cb1ae-103">Načte metadata přidružená k <xref:System.Type> odkazovanému pomocí zadaného tokenu TypeRef.</span><span class="sxs-lookup"><span data-stu-id="cb1ae-103">Gets the metadata associated with the <xref:System.Type> referenced by the specified TypeRef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb1ae-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cb1ae-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeRefProps (  
   [in]  mdTypeRef   tr,  
   [out] mdToken     *ptkResolutionScope,  
   [out] LPWSTR      szName,  
   [in]  ULONG       cchName,  
   [out] ULONG       *pchName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb1ae-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cb1ae-105">Parameters</span></span>  
 `tr`  
 <span data-ttu-id="cb1ae-106">pro Token TypeRef, který představuje typ, pro který se mají vracet metadata</span><span class="sxs-lookup"><span data-stu-id="cb1ae-106">[in] The TypeRef token that represents the type to return metadata for.</span></span>  
  
 `ptkResolutionScope`  
 <span data-ttu-id="cb1ae-107">mimo Ukazatel na obor, ve kterém je odkaz proveden.</span><span class="sxs-lookup"><span data-stu-id="cb1ae-107">[out] A pointer to the scope in which the reference is made.</span></span> <span data-ttu-id="cb1ae-108">Tato hodnota je AssemblyRef nebo odkaz ModuleRef token.</span><span class="sxs-lookup"><span data-stu-id="cb1ae-108">This value is an AssemblyRef or ModuleRef token.</span></span>  
  
 `szName`  
 <span data-ttu-id="cb1ae-109">mimo Vyrovnávací paměť obsahující název typu.</span><span class="sxs-lookup"><span data-stu-id="cb1ae-109">[out] A buffer containing the type name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="cb1ae-110">pro Požadovaná velikost v různých znacích `szName` .</span><span class="sxs-lookup"><span data-stu-id="cb1ae-110">[in] The requested size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="cb1ae-111">mimo Vrácená velikost v různých znacích `szName` .</span><span class="sxs-lookup"><span data-stu-id="cb1ae-111">[out] The returned size in wide characters of `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cb1ae-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cb1ae-112">Requirements</span></span>  
 <span data-ttu-id="cb1ae-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cb1ae-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cb1ae-114">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="cb1ae-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cb1ae-115">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="cb1ae-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cb1ae-116">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cb1ae-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb1ae-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cb1ae-117">See also</span></span>

- [<span data-ttu-id="cb1ae-118">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cb1ae-118">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="cb1ae-119">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="cb1ae-119">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
