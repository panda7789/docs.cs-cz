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
ms.openlocfilehash: 0fc82ad87721c31337002dcfc5bbfdb9300afb31
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57479737"
---
# <a name="imetadataassemblyimportgetassemblyfromscope-method"></a><span data-ttu-id="c21e1-102">IMetaDataAssemblyImport::GetAssemblyFromScope – metoda</span><span class="sxs-lookup"><span data-stu-id="c21e1-102">IMetaDataAssemblyImport::GetAssemblyFromScope Method</span></span>
<span data-ttu-id="c21e1-103">Získá ukazatel na sestavení v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="c21e1-103">Gets a pointer to the assembly in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c21e1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c21e1-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyFromScope (  
    [out] mdAssembly  *ptkAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c21e1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c21e1-105">Parameters</span></span>  
 `ptkAssembly`  
 <span data-ttu-id="c21e1-106">[out] Ukazatel na načtené `mdAssembly` token, který identifikuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="c21e1-106">[out] A pointer to the retrieved `mdAssembly` token that identifies the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c21e1-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c21e1-107">Requirements</span></span>  
 <span data-ttu-id="c21e1-108">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c21e1-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c21e1-109">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c21e1-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c21e1-110">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c21e1-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c21e1-111">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c21e1-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c21e1-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c21e1-112">See also</span></span>
- [<span data-ttu-id="c21e1-113">IMetaDataAssemblyImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c21e1-113">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
