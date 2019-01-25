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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5ad18aaca1caef242832bbdae9a1094b2ef2d7be
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54572458"
---
# <a name="imetadataimport2getpekind-method"></a><span data-ttu-id="25237-102">IMetaDataImport2::GetPEKind – metoda</span><span class="sxs-lookup"><span data-stu-id="25237-102">IMetaDataImport2::GetPEKind Method</span></span>
<span data-ttu-id="25237-103">Získá hodnotu určující druh kódu do přenosného spustitelného (PE) soubor, obvykle knihovny DLL nebo EXE souboru, která je definována v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="25237-103">Gets a value identifying the nature of the code in the portable executable (PE) file, typically a DLL or EXE file, that is defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25237-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25237-104">Syntax</span></span>  
  
```  
HRESULT GetPEKind (  
   [out] DWORD *pdwPEKind,  
   [out] DWORD *pdwMachine  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="25237-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="25237-105">Parameters</span></span>  
 `pdwPEKind`  
 <span data-ttu-id="25237-106">[out] Ukazatel na hodnotu [corpekind –](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md) výčet, který popisuje soubor PE.</span><span class="sxs-lookup"><span data-stu-id="25237-106">[out] A pointer to a value of the [CorPEKind](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md) enumeration that describes the PE file.</span></span>  
  
 `pdwMachine`  
 <span data-ttu-id="25237-107">[out] Ukazatel na hodnotu, která identifikuje architektura počítače.</span><span class="sxs-lookup"><span data-stu-id="25237-107">[out] A pointer to a value that identifies the architecture of the machine.</span></span> <span data-ttu-id="25237-108">Naleznete v části Další možné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="25237-108">See the next section for possible values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25237-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="25237-109">Remarks</span></span>  
 <span data-ttu-id="25237-110">Hodnota odkazuje `pdwMachine` parametr může být jedna z následujících akcí.</span><span class="sxs-lookup"><span data-stu-id="25237-110">The value referenced by the `pdwMachine` parameter can be one of the following.</span></span>  
  
|<span data-ttu-id="25237-111">Hodnota</span><span class="sxs-lookup"><span data-stu-id="25237-111">Value</span></span>|<span data-ttu-id="25237-112">Architektura počítače</span><span class="sxs-lookup"><span data-stu-id="25237-112">Machine architecture</span></span>|  
|-----------|--------------------------|  
|<span data-ttu-id="25237-113">IMAGE_FILE_MACHINE_I386</span><span class="sxs-lookup"><span data-stu-id="25237-113">IMAGE_FILE_MACHINE_I386</span></span><br /><br /> <span data-ttu-id="25237-114">0x014C</span><span class="sxs-lookup"><span data-stu-id="25237-114">0x014C</span></span>|<span data-ttu-id="25237-115">x86</span><span class="sxs-lookup"><span data-stu-id="25237-115">x86</span></span>|  
|<span data-ttu-id="25237-116">IMAGE_FILE_MACHINE_IA64</span><span class="sxs-lookup"><span data-stu-id="25237-116">IMAGE_FILE_MACHINE_IA64</span></span><br /><br /> <span data-ttu-id="25237-117">0x0200</span><span class="sxs-lookup"><span data-stu-id="25237-117">0x0200</span></span>|<span data-ttu-id="25237-118">Intel IPF</span><span class="sxs-lookup"><span data-stu-id="25237-118">Intel IPF</span></span>|  
|<span data-ttu-id="25237-119">IMAGE_FILE_MACHINE_AMD64</span><span class="sxs-lookup"><span data-stu-id="25237-119">IMAGE_FILE_MACHINE_AMD64</span></span><br /><br /> <span data-ttu-id="25237-120">0x8664</span><span class="sxs-lookup"><span data-stu-id="25237-120">0x8664</span></span>|<span data-ttu-id="25237-121">x64</span><span class="sxs-lookup"><span data-stu-id="25237-121">x64</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="25237-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="25237-122">Requirements</span></span>  
 <span data-ttu-id="25237-123">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25237-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25237-124">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="25237-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="25237-125">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="25237-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="25237-126">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25237-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25237-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="25237-127">See also</span></span>
- [<span data-ttu-id="25237-128">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="25237-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
- [<span data-ttu-id="25237-129">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="25237-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="25237-130">CorPEKind – výčet</span><span class="sxs-lookup"><span data-stu-id="25237-130">CorPEKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md)
