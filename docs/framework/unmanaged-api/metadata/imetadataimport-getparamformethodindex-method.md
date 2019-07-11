---
title: IMetaDataImport::GetParamForMethodIndex – metoda
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fdb3def9574f4442a22b370323dfdf044170542b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778940"
---
# <a name="imetadataimportgetparamformethodindex-method"></a><span data-ttu-id="3d70f-102">IMetaDataImport::GetParamForMethodIndex – metoda</span><span class="sxs-lookup"><span data-stu-id="3d70f-102">IMetaDataImport::GetParamForMethodIndex Method</span></span>
<span data-ttu-id="3d70f-103">Získá token, který představuje zadaný parametr metodu reprezentovanou zadaný token MethodDef.</span><span class="sxs-lookup"><span data-stu-id="3d70f-103">Gets the token that represents a specified parameter of the method represented by the specified MethodDef token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d70f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3d70f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetParamForMethodIndex (  
   [in]  mdMethodDef      md,  
   [in]  ULONG            ulParamSeq,  
   [out] mdParamDef       *ppd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d70f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3d70f-105">Parameters</span></span>  
 `md`  
 <span data-ttu-id="3d70f-106">[in] Token, který představuje metody, která vrátí parametr token.</span><span class="sxs-lookup"><span data-stu-id="3d70f-106">[in] A token that represents the method to return the parameter token for.</span></span>  
  
 `ulParamSeq`  
 <span data-ttu-id="3d70f-107">[in] Pořadové číslo pozice v seznamu parametrů, kde dochází k požadovaný parametr.</span><span class="sxs-lookup"><span data-stu-id="3d70f-107">[in] The ordinal position in the parameter list where the requested parameter occurs.</span></span> <span data-ttu-id="3d70f-108">Parametry jsou číslovány od jednoho s návratovou hodnotu metody na pozici nula.</span><span class="sxs-lookup"><span data-stu-id="3d70f-108">Parameters are numbered starting from one, with the method's return value in position zero.</span></span>  
  
 `ppd`  
 <span data-ttu-id="3d70f-109">[out] Ukazatel na ParamDef token, který představuje požadovaný parametr.</span><span class="sxs-lookup"><span data-stu-id="3d70f-109">[out] A pointer to a ParamDef token that represents the requested parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d70f-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3d70f-110">Requirements</span></span>  
 <span data-ttu-id="3d70f-111">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d70f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d70f-112">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3d70f-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3d70f-113">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3d70f-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3d70f-114">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d70f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d70f-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3d70f-115">See also</span></span>

- [<span data-ttu-id="3d70f-116">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3d70f-116">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="3d70f-117">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="3d70f-117">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
