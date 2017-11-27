---
title: "IMetaDataImport::GetParamForMethodIndex – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IMetaDataImport.GetParamForMethodIndex
api_location: mscoree.dll
api_type: COM
f1_keywords: IMetaDataImport::GetParamForMethodIndex
helpviewer_keywords:
- IMetaDataImport::GetParamForMethodIndex method [.NET Framework metadata]
- GetParamForMethodIndex method [.NET Framework metadata]
ms.assetid: ec3bfa95-1920-4511-932e-3ff23d76fcb8
topic_type: apiref
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: cda4ffde7d38d74ddf7a81b6f0af4a556693094d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="imetadataimportgetparamformethodindex-method"></a><span data-ttu-id="00297-102">IMetaDataImport::GetParamForMethodIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="00297-102">IMetaDataImport::GetParamForMethodIndex Method</span></span>
<span data-ttu-id="00297-103">Získá token, který představuje zadaný parametr metodu reprezentovanou zadaný token MethodDef.</span><span class="sxs-lookup"><span data-stu-id="00297-103">Gets the token that represents a specified parameter of the method represented by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00297-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="00297-104">Syntax</span></span>  
  
```  
HRESULT GetParamForMethodIndex (  
   [in]  mdMethodDef      md,  
   [in]  ULONG            ulParamSeq,  
   [out] mdParamDef       *ppd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="00297-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="00297-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="00297-106">[v] Token, který představuje metodu pro návrat parametr token pro.</span><span class="sxs-lookup"><span data-stu-id="00297-106">[in] A token that represents the method to return the parameter token for.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="00297-107">[v] Pořadové číslo pozice v seznamu parametrů, kde dojde k požadovaný parametr.</span><span class="sxs-lookup"><span data-stu-id="00297-107">[in] The ordinal position in the parameter list where the requested parameter occurs.</span></span> <span data-ttu-id="00297-108">Parametry jsou číslována od jednoho s návratovou hodnotu metody v pozici nula.</span><span class="sxs-lookup"><span data-stu-id="00297-108">Parameters are numbered starting from one, with the method's return value in position zero.</span></span>  
  
 `ppd`  
 <span data-ttu-id="00297-109">[out] Ukazatel na ParamDef token, který je požadovaný parametr.</span><span class="sxs-lookup"><span data-stu-id="00297-109">[out] A pointer to a ParamDef token that represents the requested parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00297-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="00297-110">Requirements</span></span>  
 <span data-ttu-id="00297-111">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00297-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00297-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="00297-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="00297-113">**Knihovna:** zahrnuty jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="00297-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="00297-114">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00297-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00297-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="00297-115">See Also</span></span>  
 [<span data-ttu-id="00297-116">Imetadataimport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="00297-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)  
 [<span data-ttu-id="00297-117">Imetadataimport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="00297-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
