---
title: IMetaDataImport::GetInterfaceImplProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetInterfaceImplProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetInterfaceImplProps
helpviewer_keywords:
- IMetaDataImport::GetInterfaceImplProps method [.NET Framework metadata]
- GetInterfaceImpProps method [.NET Framework metadata]
ms.assetid: be3f5985-b1e4-4036-8602-c16e8508d4af
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 91cb42a5bf1115de82b5fe28693cb77b66915c9d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54600554"
---
# <a name="imetadataimportgetinterfaceimplprops-method"></a><span data-ttu-id="c3e06-102">IMetaDataImport::GetInterfaceImplProps – metoda</span><span class="sxs-lookup"><span data-stu-id="c3e06-102">IMetaDataImport::GetInterfaceImplProps Method</span></span>
<span data-ttu-id="c3e06-103">Získá ukazatel na tokeny metadat pro <xref:System.Type> zadanou metodu, která implementuje a rozhraní, která deklaruje dané metody.</span><span class="sxs-lookup"><span data-stu-id="c3e06-103">Gets a pointer to the metadata tokens for the <xref:System.Type> that implements the specified method, and for the interface that declares that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3e06-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c3e06-104">Syntax</span></span>  
  
```  
HRESULT GetInterfaceImplProps (  
   [in]  mdInterfaceImpl        iiImpl,  
   [out] mdTypeDef              *pClass,  
   [out] mdToken                *ptkIface  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c3e06-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c3e06-105">Parameters</span></span>  
 `iiImpl`  
 <span data-ttu-id="c3e06-106">[in] Představující metodu vrátit třídu a interface tokeny pro token metadat.</span><span class="sxs-lookup"><span data-stu-id="c3e06-106">[in] The metadata token representing the method to return the class and interface tokens for.</span></span>  
  
 `pClass`  
 <span data-ttu-id="c3e06-107">[out] Token metadat představující třídu, která implementuje metodu.</span><span class="sxs-lookup"><span data-stu-id="c3e06-107">[out] The metadata token representing the class that implements the method.</span></span>  
  
 `ptkIface`  
 <span data-ttu-id="c3e06-108">[out] Představuje rozhraní, které definuje implementované metody token metadat.</span><span class="sxs-lookup"><span data-stu-id="c3e06-108">[out] The metadata token representing the interface that defines the implemented method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3e06-109">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c3e06-109">Requirements</span></span>  
 <span data-ttu-id="c3e06-110">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3e06-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3e06-111">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="c3e06-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c3e06-112">**Knihovna:** Zahrnuté jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c3e06-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c3e06-113">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3e06-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3e06-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c3e06-114">See also</span></span>
- [<span data-ttu-id="c3e06-115">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c3e06-115">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
- [<span data-ttu-id="c3e06-116">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="c3e06-116">IMetaDataImport2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-interface.md)
