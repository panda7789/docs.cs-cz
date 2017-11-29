---
title: "IMetaDataAssemblyImport::GetAssemblyFromScope – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataAssemblyImport.GetAssemblyFromScope
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataAssemblyImport::GetAssemblyFromScope
helpviewer_keywords:
- IMetaDataAssemblyImport::GetAssemblyFromScope method [.NET Framework metadata]
- GetAssemblyFromScope method [.NET Framework metadata]
ms.assetid: 0b437f70-561d-48c7-abe0-0cb9ace10c08
topic_type: apiref
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 99734207f3df4582d28c0b318fee80d6bf8926bb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="imetadataassemblyimportgetassemblyfromscope-method"></a><span data-ttu-id="d8730-102">IMetaDataAssemblyImport::GetAssemblyFromScope – metoda</span><span class="sxs-lookup"><span data-stu-id="d8730-102">IMetaDataAssemblyImport::GetAssemblyFromScope Method</span></span>
<span data-ttu-id="d8730-103">Získá ukazatel na sestavení v aktuálním oboru.</span><span class="sxs-lookup"><span data-stu-id="d8730-103">Gets a pointer to the assembly in the current scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8730-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d8730-104">Syntax</span></span>  
  
```  
HRESULT GetAssemblyFromScope (  
    [out] mdAssembly  *ptkAssembly  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="d8730-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d8730-105">Parameters</span></span>  
 `ptkAssembly`  
 <span data-ttu-id="d8730-106">[out] Ukazatel na načtený `mdAssembly` token, který identifikuje sestavení.</span><span class="sxs-lookup"><span data-stu-id="d8730-106">[out] A pointer to the retrieved `mdAssembly` token that identifies the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8730-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d8730-107">Requirements</span></span>  
 <span data-ttu-id="d8730-108">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8730-108">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8730-109">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="d8730-109">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d8730-110">**Knihovna:** používat jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="d8730-110">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="d8730-111">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8730-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8730-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="d8730-112">See Also</span></span>  
 [<span data-ttu-id="d8730-113">Imetadataassemblyimport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="d8730-113">IMetaDataAssemblyImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataassemblyimport-interface.md)
