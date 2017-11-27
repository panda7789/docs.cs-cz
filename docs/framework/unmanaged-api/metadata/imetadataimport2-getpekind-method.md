---
title: "IMetaDataImport2::GetPEKind – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport2.GetPEKind
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport2::GetPEKind
helpviewer_keywords:
- GetPEKind method [.NET Framework metadata]
- IMetaDataImport2::GetPEKind method [.NET Framework metadata]
ms.assetid: d91c3d89-8022-4a4c-a2a2-a8af2c387507
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9fc963f38a845db67bb5b5d377ecabf9a40c359f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimport2getpekind-method"></a><span data-ttu-id="0b0ba-102">IMetaDataImport2::GetPEKind – metoda</span><span class="sxs-lookup"><span data-stu-id="0b0ba-102">IMetaDataImport2::GetPEKind Method</span></span>
<span data-ttu-id="0b0ba-103">Získá hodnotu identifikace povaha kód na přenosné spustitelný soubor (PE) souboru, obvykle DLL nebo EXE soubor, který je definován v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="0b0ba-103">Gets a value identifying the nature of the code in the portable executable (PE) file, typically a DLL or EXE file, that is defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b0ba-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0b0ba-104">Syntax</span></span>  
  
```  
HRESULT GetPEKind (  
   [out] DWORD *pdwPEKind,  
   [out] DWORD *pdwMachine  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0b0ba-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0b0ba-105">Parameters</span></span>  
 `pdwPEKind`  
 <span data-ttu-id="0b0ba-106">[out] Ukazatel na hodnotu [CorPEKind](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md) výčet, který popisuje PE souborů.</span><span class="sxs-lookup"><span data-stu-id="0b0ba-106">[out] A pointer to a value of the [CorPEKind](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md) enumeration that describes the PE file.</span></span>  
  
 `pdwMachine`  
 <span data-ttu-id="0b0ba-107">[out] Ukazatel na hodnotu, která identifikuje architektuře počítače.</span><span class="sxs-lookup"><span data-stu-id="0b0ba-107">[out] A pointer to a value that identifies the architecture of the machine.</span></span> <span data-ttu-id="0b0ba-108">Naleznete v části Další možné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="0b0ba-108">See the next section for possible values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b0ba-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0b0ba-109">Remarks</span></span>  
 <span data-ttu-id="0b0ba-110">Hodnota odkazovaná `pdwMachine` parametr může být jedna z následujících akcí.</span><span class="sxs-lookup"><span data-stu-id="0b0ba-110">The value referenced by the `pdwMachine` parameter can be one of the following.</span></span>  
  
|<span data-ttu-id="0b0ba-111">Hodnota</span><span class="sxs-lookup"><span data-stu-id="0b0ba-111">Value</span></span>|<span data-ttu-id="0b0ba-112">Architektura počítače</span><span class="sxs-lookup"><span data-stu-id="0b0ba-112">Machine architecture</span></span>|  
|-----------|--------------------------|  
|<span data-ttu-id="0b0ba-113">IMAGE_FILE_MACHINE_I386</span><span class="sxs-lookup"><span data-stu-id="0b0ba-113">IMAGE_FILE_MACHINE_I386</span></span><br /><br /> <span data-ttu-id="0b0ba-114">0x014C</span><span class="sxs-lookup"><span data-stu-id="0b0ba-114">0x014C</span></span>|<span data-ttu-id="0b0ba-115">x86</span><span class="sxs-lookup"><span data-stu-id="0b0ba-115">x86</span></span>|  
|<span data-ttu-id="0b0ba-116">IMAGE_FILE_MACHINE_IA64</span><span class="sxs-lookup"><span data-stu-id="0b0ba-116">IMAGE_FILE_MACHINE_IA64</span></span><br /><br /> <span data-ttu-id="0b0ba-117">hodnotu 0x0200</span><span class="sxs-lookup"><span data-stu-id="0b0ba-117">0x0200</span></span>|<span data-ttu-id="0b0ba-118">Intel IPF</span><span class="sxs-lookup"><span data-stu-id="0b0ba-118">Intel IPF</span></span>|  
|<span data-ttu-id="0b0ba-119">IMAGE_FILE_MACHINE_AMD64</span><span class="sxs-lookup"><span data-stu-id="0b0ba-119">IMAGE_FILE_MACHINE_AMD64</span></span><br /><br /> <span data-ttu-id="0b0ba-120">0x8664</span><span class="sxs-lookup"><span data-stu-id="0b0ba-120">0x8664</span></span>|<span data-ttu-id="0b0ba-121">x64</span><span class="sxs-lookup"><span data-stu-id="0b0ba-121">x64</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0b0ba-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="0b0ba-122">Requirements</span></span>  
 <span data-ttu-id="0b0ba-123">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b0ba-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b0ba-124">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="0b0ba-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0b0ba-125">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0b0ba-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0b0ba-126">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b0ba-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b0ba-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="0b0ba-127">See Also</span></span>  
 [<span data-ttu-id="0b0ba-128">Imetadataimport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0b0ba-128">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)  
 [<span data-ttu-id="0b0ba-129">Imetadataimport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="0b0ba-129">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="0b0ba-130">CorPEKind – výčet</span><span class="sxs-lookup"><span data-stu-id="0b0ba-130">CorPEKind Enumeration</span></span>](../../../../docs/framework/unmanaged-api/metadata/corpekind-enumeration.md)
