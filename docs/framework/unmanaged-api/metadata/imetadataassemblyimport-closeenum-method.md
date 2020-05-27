---
title: IMetaDataAssemblyImport::CloseEnum – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.CloseEnum
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::CloseEnum
helpviewer_keywords:
- CloseEnum method, IMetaDataAssemblyImport interface [.NET Framework metadata]
- IMetaDataAssemblyImport::CloseEnum method [.NET Framework metadata]
ms.assetid: c9df4087-12b3-46d9-b075-9067dd7805df
topic_type:
- apiref
ms.openlocfilehash: 63e81e822eb55b4090aeee6d6be3c72adbd94451
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84009129"
---
# <a name="imetadataassemblyimportcloseenum-method"></a><span data-ttu-id="bc784-102">IMetaDataAssemblyImport::CloseEnum – metoda</span><span class="sxs-lookup"><span data-stu-id="bc784-102">IMetaDataAssemblyImport::CloseEnum Method</span></span>
<span data-ttu-id="bc784-103">Uvolní odkaz na zadanou instanci výčtu.</span><span class="sxs-lookup"><span data-stu-id="bc784-103">Releases a reference to the specified enumeration instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc784-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bc784-104">Syntax</span></span>  
  
```cpp  
void CloseEnum (  
    [in] HCORENUM     hEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bc784-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bc784-105">Parameters</span></span>  
 `hEnum`  
 <span data-ttu-id="bc784-106">pro Instance výčtu, která má být zavřena.</span><span class="sxs-lookup"><span data-stu-id="bc784-106">[in] The enumeration instance to be closed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc784-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="bc784-107">Requirements</span></span>  
 <span data-ttu-id="bc784-108">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc784-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc784-109">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="bc784-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bc784-110">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="bc784-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bc784-111">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc784-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc784-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="bc784-112">See also</span></span>

- [<span data-ttu-id="bc784-113">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="bc784-113">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
