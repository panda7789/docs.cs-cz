---
title: IMetaDataImport2::GetPEKind – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport2.GetPEKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2::GetPEKind
helpviewer_keywords:
- GetPEKind method [.NET Framework metadata]
- IMetaDataImport2::GetPEKind method [.NET Framework metadata]
ms.assetid: d91c3d89-8022-4a4c-a2a2-a8af2c387507
topic_type:
- apiref
ms.openlocfilehash: 0464c61e4ff01483e10fb5708d5ed4b5f5ed63d0
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445235"
---
# <a name="imetadataimport2getpekind-method"></a><span data-ttu-id="301e9-102">IMetaDataImport2::GetPEKind – metoda</span><span class="sxs-lookup"><span data-stu-id="301e9-102">IMetaDataImport2::GetPEKind Method</span></span>
<span data-ttu-id="301e9-103">Gets a value identifying the nature of the code in the portable executable (PE) file, typically a DLL or EXE file, that is defined in the current metadata scope.</span><span class="sxs-lookup"><span data-stu-id="301e9-103">Gets a value identifying the nature of the code in the portable executable (PE) file, typically a DLL or EXE file, that is defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="301e9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="301e9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPEKind (  
   [out] DWORD *pdwPEKind,  
   [out] DWORD *pdwMachine  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="301e9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="301e9-105">Parameters</span></span>  
 `pdwPEKind`  
 <span data-ttu-id="301e9-106">[out] A pointer to a value of the [CorPEKind](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md) enumeration that describes the PE file.</span><span class="sxs-lookup"><span data-stu-id="301e9-106">[out] A pointer to a value of the [CorPEKind](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md) enumeration that describes the PE file.</span></span>  
  
 `pdwMachine`  
 <span data-ttu-id="301e9-107">[out] A pointer to a value that identifies the architecture of the machine.</span><span class="sxs-lookup"><span data-stu-id="301e9-107">[out] A pointer to a value that identifies the architecture of the machine.</span></span> <span data-ttu-id="301e9-108">See the next section for possible values.</span><span class="sxs-lookup"><span data-stu-id="301e9-108">See the next section for possible values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="301e9-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="301e9-109">Remarks</span></span>  
 <span data-ttu-id="301e9-110">The value referenced by the `pdwMachine` parameter can be one of the following.</span><span class="sxs-lookup"><span data-stu-id="301e9-110">The value referenced by the `pdwMachine` parameter can be one of the following.</span></span>  
  
|<span data-ttu-id="301e9-111">Hodnota</span><span class="sxs-lookup"><span data-stu-id="301e9-111">Value</span></span>|<span data-ttu-id="301e9-112">Machine architecture</span><span class="sxs-lookup"><span data-stu-id="301e9-112">Machine architecture</span></span>|  
|-----------|--------------------------|  
|<span data-ttu-id="301e9-113">IMAGE_FILE_MACHINE_I386</span><span class="sxs-lookup"><span data-stu-id="301e9-113">IMAGE_FILE_MACHINE_I386</span></span><br /><br /> <span data-ttu-id="301e9-114">0x014C</span><span class="sxs-lookup"><span data-stu-id="301e9-114">0x014C</span></span>|<span data-ttu-id="301e9-115">x86</span><span class="sxs-lookup"><span data-stu-id="301e9-115">x86</span></span>|  
|<span data-ttu-id="301e9-116">IMAGE_FILE_MACHINE_IA64</span><span class="sxs-lookup"><span data-stu-id="301e9-116">IMAGE_FILE_MACHINE_IA64</span></span><br /><br /> <span data-ttu-id="301e9-117">0x0200</span><span class="sxs-lookup"><span data-stu-id="301e9-117">0x0200</span></span>|<span data-ttu-id="301e9-118">Intel IPF</span><span class="sxs-lookup"><span data-stu-id="301e9-118">Intel IPF</span></span>|  
|<span data-ttu-id="301e9-119">IMAGE_FILE_MACHINE_AMD64</span><span class="sxs-lookup"><span data-stu-id="301e9-119">IMAGE_FILE_MACHINE_AMD64</span></span><br /><br /> <span data-ttu-id="301e9-120">0x8664</span><span class="sxs-lookup"><span data-stu-id="301e9-120">0x8664</span></span>|<span data-ttu-id="301e9-121">x64</span><span class="sxs-lookup"><span data-stu-id="301e9-121">x64</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="301e9-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="301e9-122">Requirements</span></span>  
 <span data-ttu-id="301e9-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="301e9-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="301e9-124">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="301e9-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="301e9-125">**Library:** Used as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="301e9-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="301e9-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="301e9-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="301e9-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="301e9-127">See also</span></span>

- [<span data-ttu-id="301e9-128">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="301e9-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="301e9-129">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="301e9-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="301e9-130">CorPEKind – výčet</span><span class="sxs-lookup"><span data-stu-id="301e9-130">CorPEKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md)
