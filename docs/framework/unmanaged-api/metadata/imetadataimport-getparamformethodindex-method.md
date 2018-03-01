---
title: "IMetaDataImport::GetParamForMethodIndex – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataImport.GetParamForMethodIndex
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetParamForMethodIndex
helpviewer_keywords:
- IMetaDataImport::GetParamForMethodIndex method [.NET Framework metadata]
- GetParamForMethodIndex method [.NET Framework metadata]
ms.assetid: ec3bfa95-1920-4511-932e-3ff23d76fcb8
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0cedc993e6b8794a15ff9927b06ff650ed76b79e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataimportgetparamformethodindex-method"></a><span data-ttu-id="9d3e0-102">IMetaDataImport::GetParamForMethodIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="9d3e0-102">IMetaDataImport::GetParamForMethodIndex Method</span></span>
<span data-ttu-id="9d3e0-103">Získá token, který představuje zadaný parametr metodu reprezentovanou zadaný token MethodDef.</span><span class="sxs-lookup"><span data-stu-id="9d3e0-103">Gets the token that represents a specified parameter of the method represented by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d3e0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d3e0-104">Syntax</span></span>  
  
```  
HRESULT GetParamForMethodIndex (  
   [in]  mdMethodDef      md,  
   [in]  ULONG            ulParamSeq,  
   [out] mdParamDef       *ppd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9d3e0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9d3e0-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="9d3e0-106">[v] Token, který představuje metodu pro návrat parametr token pro.</span><span class="sxs-lookup"><span data-stu-id="9d3e0-106">[in] A token that represents the method to return the parameter token for.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="9d3e0-107">[v] Pořadové číslo pozice v seznamu parametrů, kde dojde k požadovaný parametr.</span><span class="sxs-lookup"><span data-stu-id="9d3e0-107">[in] The ordinal position in the parameter list where the requested parameter occurs.</span></span> <span data-ttu-id="9d3e0-108">Parametry jsou číslována od jednoho s návratovou hodnotu metody v pozici nula.</span><span class="sxs-lookup"><span data-stu-id="9d3e0-108">Parameters are numbered starting from one, with the method's return value in position zero.</span></span>  
  
 `ppd`  
 <span data-ttu-id="9d3e0-109">[out] Ukazatel na ParamDef token, který je požadovaný parametr.</span><span class="sxs-lookup"><span data-stu-id="9d3e0-109">[out] A pointer to a ParamDef token that represents the requested parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d3e0-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="9d3e0-110">Requirements</span></span>  
 <span data-ttu-id="9d3e0-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d3e0-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d3e0-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="9d3e0-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9d3e0-113">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9d3e0-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9d3e0-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d3e0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d3e0-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="9d3e0-115">See Also</span></span>  
 [<span data-ttu-id="9d3e0-116">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9d3e0-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="9d3e0-117">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="9d3e0-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
