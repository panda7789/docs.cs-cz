---
title: IMetaDataImport::GetPinvokeMap – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetPinvokeMap
helpviewer_keywords:
- IMetaDataImport::GetPinvokeMap method [.NET Framework metadata]
- GetPinvokeMap method [.NET Framework metadata]
ms.assetid: b8685c1e-b80c-4198-8eb3-748d6f48a99e
topic_type:
- apiref
ms.openlocfilehash: 8409e56b5ec4dbe47035a0555b6b7ce175b517ee
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490975"
---
# <a name="imetadataimportgetpinvokemap-method"></a><span data-ttu-id="56fd2-102">IMetaDataImport::GetPinvokeMap – metoda</span><span class="sxs-lookup"><span data-stu-id="56fd2-102">IMetaDataImport::GetPinvokeMap Method</span></span>
<span data-ttu-id="56fd2-103">Získá token Odkaz ModuleRef představující cílové sestavení volání PInvoke.</span><span class="sxs-lookup"><span data-stu-id="56fd2-103">Gets a ModuleRef token to represent the target assembly of a PInvoke call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56fd2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="56fd2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPinvokeMap (  
   [in]  mdToken       tk,  
   [out] DWORD         *pdwMappingFlags,  
   [out] LPWSTR        szImportName,  
   [in]  ULONG         cchImportName,  
   [out] ULONG         *pchImportName,  
   [out] mdModuleRef   *pmrImportDLL  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="56fd2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="56fd2-105">Parameters</span></span>  
 `tk`  
 <span data-ttu-id="56fd2-106">pro FieldDef nebo MethodDef token pro získání metadat mapování PInvoke pro.</span><span class="sxs-lookup"><span data-stu-id="56fd2-106">[in] A FieldDef or MethodDef token to get the PInvoke mapping metadata for.</span></span>  
  
 `pdwMappingFlags`  
 <span data-ttu-id="56fd2-107">mimo Ukazatel na příznaky použité pro mapování.</span><span class="sxs-lookup"><span data-stu-id="56fd2-107">[out] A pointer to flags used for mapping.</span></span> <span data-ttu-id="56fd2-108">Tato hodnota je Bitová maska z výčtu [CorPinvokeMap –](corpinvokemap-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="56fd2-108">This value is a bitmask from the [CorPinvokeMap](corpinvokemap-enumeration.md) enumeration.</span></span>  
  
 `szImportName`  
 <span data-ttu-id="56fd2-109">mimo Název nespravované cílové knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="56fd2-109">[out] The name of the unmanaged target DLL.</span></span>  
  
 `cchImportName`  
 <span data-ttu-id="56fd2-110">pro Velikost v různých znacích `szImportName` .</span><span class="sxs-lookup"><span data-stu-id="56fd2-110">[in] The size in wide characters of `szImportName`.</span></span>  
  
 `pchImportName`  
 <span data-ttu-id="56fd2-111">mimo Počet znaků vrácených v rámci `szImportName` .</span><span class="sxs-lookup"><span data-stu-id="56fd2-111">[out] The number of wide characters returned in `szImportName`.</span></span>  
  
 `pmrImportDLL`  
 <span data-ttu-id="56fd2-112">mimo Ukazatel na token Odkaz ModuleRef, který představuje knihovnu nespravovaného cílového objektu.</span><span class="sxs-lookup"><span data-stu-id="56fd2-112">[out] A pointer to a ModuleRef token that represents the unmanaged target object library.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56fd2-113">Požadavky</span><span class="sxs-lookup"><span data-stu-id="56fd2-113">Requirements</span></span>  
 <span data-ttu-id="56fd2-114">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="56fd2-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="56fd2-115">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="56fd2-115">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="56fd2-116">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="56fd2-116">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="56fd2-117">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="56fd2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56fd2-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="56fd2-118">See also</span></span>

- [<span data-ttu-id="56fd2-119">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="56fd2-119">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="56fd2-120">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="56fd2-120">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
