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
ms.openlocfilehash: 3626998c456e23fb922ae45a68bedb0e45a7ccba
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490429"
---
# <a name="imetadataimport2getpekind-method"></a><span data-ttu-id="2c375-102">IMetaDataImport2::GetPEKind – metoda</span><span class="sxs-lookup"><span data-stu-id="2c375-102">IMetaDataImport2::GetPEKind Method</span></span>
<span data-ttu-id="2c375-103">Získává hodnotu identifikující povahu kódu v přenositelném spustitelném souboru (PE), obvykle v souboru DLL nebo EXE, který je definován v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="2c375-103">Gets a value identifying the nature of the code in the portable executable (PE) file, typically a DLL or EXE file, that is defined in the current metadata scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c375-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2c375-104">Syntax</span></span>  
  
```cpp  
HRESULT GetPEKind (  
   [out] DWORD *pdwPEKind,  
   [out] DWORD *pdwMachine  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c375-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2c375-105">Parameters</span></span>  
 `pdwPEKind`  
 <span data-ttu-id="2c375-106">mimo Ukazatel na hodnotu výčtu [CorPEKind –](corpekind-enumeration.md) , která popisuje soubor PE.</span><span class="sxs-lookup"><span data-stu-id="2c375-106">[out] A pointer to a value of the [CorPEKind](corpekind-enumeration.md) enumeration that describes the PE file.</span></span>  
  
 `pdwMachine`  
 <span data-ttu-id="2c375-107">mimo Ukazatel na hodnotu, která identifikuje architekturu počítače.</span><span class="sxs-lookup"><span data-stu-id="2c375-107">[out] A pointer to a value that identifies the architecture of the machine.</span></span> <span data-ttu-id="2c375-108">Možné hodnoty najdete v další části.</span><span class="sxs-lookup"><span data-stu-id="2c375-108">See the next section for possible values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c375-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2c375-109">Remarks</span></span>  
 <span data-ttu-id="2c375-110">Hodnota, na kterou parametr odkazuje, `pdwMachine` může být jedna z následujících.</span><span class="sxs-lookup"><span data-stu-id="2c375-110">The value referenced by the `pdwMachine` parameter can be one of the following.</span></span>  
  
|<span data-ttu-id="2c375-111">Hodnota</span><span class="sxs-lookup"><span data-stu-id="2c375-111">Value</span></span>|<span data-ttu-id="2c375-112">Architektura počítače</span><span class="sxs-lookup"><span data-stu-id="2c375-112">Machine architecture</span></span>|  
|-----------|--------------------------|  
|<span data-ttu-id="2c375-113">IMAGE_FILE_MACHINE_I386</span><span class="sxs-lookup"><span data-stu-id="2c375-113">IMAGE_FILE_MACHINE_I386</span></span><br /><br /> <span data-ttu-id="2c375-114">0x014C</span><span class="sxs-lookup"><span data-stu-id="2c375-114">0x014C</span></span>|<span data-ttu-id="2c375-115">x86</span><span class="sxs-lookup"><span data-stu-id="2c375-115">x86</span></span>|  
|<span data-ttu-id="2c375-116">IMAGE_FILE_MACHINE_IA64</span><span class="sxs-lookup"><span data-stu-id="2c375-116">IMAGE_FILE_MACHINE_IA64</span></span><br /><br /> <span data-ttu-id="2c375-117">0x0200</span><span class="sxs-lookup"><span data-stu-id="2c375-117">0x0200</span></span>|<span data-ttu-id="2c375-118">Intel IPF</span><span class="sxs-lookup"><span data-stu-id="2c375-118">Intel IPF</span></span>|  
|<span data-ttu-id="2c375-119">IMAGE_FILE_MACHINE_AMD64</span><span class="sxs-lookup"><span data-stu-id="2c375-119">IMAGE_FILE_MACHINE_AMD64</span></span><br /><br /> <span data-ttu-id="2c375-120">0x8664</span><span class="sxs-lookup"><span data-stu-id="2c375-120">0x8664</span></span>|<span data-ttu-id="2c375-121">x64</span><span class="sxs-lookup"><span data-stu-id="2c375-121">x64</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2c375-122">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2c375-122">Requirements</span></span>  
 <span data-ttu-id="2c375-123">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c375-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c375-124">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="2c375-124">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2c375-125">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="2c375-125">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2c375-126">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c375-126">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c375-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2c375-127">See also</span></span>

- [<span data-ttu-id="2c375-128">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2c375-128">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
- [<span data-ttu-id="2c375-129">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2c375-129">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="2c375-130">CorPEKind – výčet</span><span class="sxs-lookup"><span data-stu-id="2c375-130">CorPEKind Enumeration</span></span>](corpekind-enumeration.md)
