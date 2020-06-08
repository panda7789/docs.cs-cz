---
title: IMetaDataImport::GetScopeProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetScopeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetScopeProps
helpviewer_keywords:
- IMetaDataImport::GetScopeProps method [.NET Framework metadata]
- GetScopeProps method [.NET Framework metadata]
ms.assetid: c8ba42d2-d9fa-43cb-bbc0-f33e1e592cb6
topic_type:
- apiref
ms.openlocfilehash: 0916b6382bb9352616d85e21f423301dc6aa9fa9
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490845"
---
# <a name="imetadataimportgetscopeprops-method"></a><span data-ttu-id="0b6da-102">IMetaDataImport::GetScopeProps – metoda</span><span class="sxs-lookup"><span data-stu-id="0b6da-102">IMetaDataImport::GetScopeProps Method</span></span>
<span data-ttu-id="0b6da-103">Získá název a volitelně identifikátor verze sestavení nebo modulu v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="0b6da-103">Gets the name and optionally the version identifier of the assembly or module in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b6da-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0b6da-104">Syntax</span></span>  
  
```cpp  
HRESULT GetScopeProps (  
   [out] LPWSTR           szName,  
   [in]  ULONG            cchName,  
   [out] ULONG            *pchName,  
   [out, optional] GUID   *pmvid  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b6da-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0b6da-105">Parameters</span></span>  
 `szName`  
 <span data-ttu-id="0b6da-106">mimo Vyrovnávací paměť pro název sestavení nebo modulu.</span><span class="sxs-lookup"><span data-stu-id="0b6da-106">[out] A buffer for the assembly or module name.</span></span>  
  
 `cchName`  
 <span data-ttu-id="0b6da-107">pro Velikost v různých znacích `szName` .</span><span class="sxs-lookup"><span data-stu-id="0b6da-107">[in] The size in wide characters of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="0b6da-108">mimo Počet znaků vrácených v rámci `szName` .</span><span class="sxs-lookup"><span data-stu-id="0b6da-108">[out] The number of wide characters returned in `szName`.</span></span>  
  
 `pmvid`  
 <span data-ttu-id="0b6da-109">[out, volitelné] Ukazatel na identifikátor GUID, který jedinečně identifikuje verzi sestavení nebo modulu.</span><span class="sxs-lookup"><span data-stu-id="0b6da-109">[out, optional] A pointer to a GUID that uniquely identifies the version of the assembly or module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b6da-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0b6da-110">Remarks</span></span>  
 <span data-ttu-id="0b6da-111">Metoda [IMetaDataEmit:: SetModuleProps –](imetadataemit-setmoduleprops-method.md) slouží k nastavení těchto vlastností.</span><span class="sxs-lookup"><span data-stu-id="0b6da-111">The [IMetaDataEmit::SetModuleProps](imetadataemit-setmoduleprops-method.md) method is used to set these properties.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b6da-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0b6da-112">Requirements</span></span>  
 <span data-ttu-id="0b6da-113">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b6da-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b6da-114">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="0b6da-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0b6da-115">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="0b6da-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0b6da-116">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b6da-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b6da-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0b6da-117">See also</span></span>

- [<span data-ttu-id="0b6da-118">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0b6da-118">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="0b6da-119">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0b6da-119">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
