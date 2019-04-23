---
title: IMetaDataAssemblyImport::GetAssemblyFromScope – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyFromScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyFromScope
helpviewer_keywords:
- IMetaDataAssemblyImport::GetAssemblyFromScope method [.NET Framework metadata]
- GetAssemblyFromScope method [.NET Framework metadata]
ms.assetid: 0b437f70-561d-48c7-abe0-0cb9ace10c08
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7d4797c952bfec4e0863e7a12b97e038c7ff8d95
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59191520"
---
# <a name="imetadataassemblyimportgetassemblyfromscope-method"></a><span data-ttu-id="be594-102">IMetaDataAssemblyImport::GetAssemblyFromScope – metoda</span><span class="sxs-lookup"><span data-stu-id="be594-102">IMetaDataAssemblyImport::GetAssemblyFromScope Method</span></span>
<span data-ttu-id="be594-103">Získá ukazatel na sestavení v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="be594-103">Gets a pointer to the assembly in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be594-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="be594-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyFromScope (  
    [out] mdAssembly  *ptkAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be594-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="be594-105">Parameters</span></span>  
 `ptkAssembly`  
 <span data-ttu-id="be594-106">[out] Ukazatel na načtené `mdAssembly` token, který identifikuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="be594-106">[out] A pointer to the retrieved `mdAssembly` token that identifies the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be594-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="be594-107">Requirements</span></span>  
 <span data-ttu-id="be594-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be594-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be594-109">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="be594-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="be594-110">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="be594-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="be594-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be594-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be594-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="be594-112">See also</span></span>

- [<span data-ttu-id="be594-113">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="be594-113">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
