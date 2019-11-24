---
title: IMetaDataImport2::GetVersionString – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetVersionString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetVersionString
helpviewer_keywords:
- GetVersionString method, IMetaDataImport2 interface [.NET Framework metadata]
- IMetaDataImport2::GetVersionString method [.NET Framework metadata]
ms.assetid: 308183ee-fd44-4432-9d86-ef00d181b49b
topic_type:
- apiref
ms.openlocfilehash: 0c9f667edf30feb23e1cdaa28950503283fce42e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445222"
---
# <a name="imetadataimport2getversionstring-method"></a><span data-ttu-id="65ff5-102">IMetaDataImport2::GetVersionString – metoda</span><span class="sxs-lookup"><span data-stu-id="65ff5-102">IMetaDataImport2::GetVersionString Method</span></span>
<span data-ttu-id="65ff5-103">Gets the version number of the runtime that was used to build the assembly.</span><span class="sxs-lookup"><span data-stu-id="65ff5-103">Gets the version number of the runtime that was used to build the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="65ff5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="65ff5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetVersionString (  
   [out] LPWSTR      pwzBuf,  
   [in]  DWORD       ccBufSize,  
   [out] DWORD       *pccBufSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="65ff5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="65ff5-105">Parameters</span></span>  
 `pwzBuf`  
 <span data-ttu-id="65ff5-106">[out] An array to store the string that specifies the version.</span><span class="sxs-lookup"><span data-stu-id="65ff5-106">[out] An array to store the string that specifies the version.</span></span>  
  
 `ccBufSize`  
 <span data-ttu-id="65ff5-107">[in] The size, in wide characters, of the `pwzBuf` array.</span><span class="sxs-lookup"><span data-stu-id="65ff5-107">[in] The size, in wide characters, of the `pwzBuf` array.</span></span>  
  
 `pccBufSize`  
 <span data-ttu-id="65ff5-108">[out] The number of wide characters, including a null terminator, returned in the `pwzBuf` array.</span><span class="sxs-lookup"><span data-stu-id="65ff5-108">[out] The number of wide characters, including a null terminator, returned in the `pwzBuf` array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65ff5-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="65ff5-109">Remarks</span></span>  
 <span data-ttu-id="65ff5-110">The `GetVersionString` method gets the built-for version of the current metadata scope.</span><span class="sxs-lookup"><span data-stu-id="65ff5-110">The `GetVersionString` method gets the built-for version of the current metadata scope.</span></span> <span data-ttu-id="65ff5-111">If the scope has never been saved, it will not have a built-for version, and an empty string will be returned.</span><span class="sxs-lookup"><span data-stu-id="65ff5-111">If the scope has never been saved, it will not have a built-for version, and an empty string will be returned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="65ff5-112">Požadavky</span><span class="sxs-lookup"><span data-stu-id="65ff5-112">Requirements</span></span>  
 <span data-ttu-id="65ff5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="65ff5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="65ff5-114">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="65ff5-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="65ff5-115">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="65ff5-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="65ff5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65ff5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65ff5-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="65ff5-117">See also</span></span>

- [<span data-ttu-id="65ff5-118">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="65ff5-118">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="65ff5-119">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="65ff5-119">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
