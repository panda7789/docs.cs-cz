---
title: IMetaDataImport::GetNestedClassProps – metoda
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetNestedClassProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetNestedClassProps
helpviewer_keywords:
- GetNestedClassProps method [.NET Framework metadata]
- IMetaDataImport::GetNestedClassProps method [.NET Framework metadata]
ms.assetid: 704d19f1-bdef-4745-af8c-6476eb246fb3
topic_type:
- apiref
ms.openlocfilehash: 82cf5e14520f0e677c2d274cf013d8a0020e8fa2
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503533"
---
# <a name="imetadataimportgetnestedclassprops-method"></a><span data-ttu-id="5f760-102">IMetaDataImport::GetNestedClassProps – metoda</span><span class="sxs-lookup"><span data-stu-id="5f760-102">IMetaDataImport::GetNestedClassProps Method</span></span>
<span data-ttu-id="5f760-103">Získá token TypeDef pro nadřazenou položku <xref:System.Type> zadaného vnořeného typu.</span><span class="sxs-lookup"><span data-stu-id="5f760-103">Gets the TypeDef token for the parent <xref:System.Type> of the specified nested type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f760-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5f760-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNestedClassProps (  
   [in]   mdTypeDef      tdNestedClass,  
   [out]  mdTypeDef      *ptdEnclosingClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f760-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5f760-105">Parameters</span></span>  
 `tdNestedClass`  
 <span data-ttu-id="5f760-106">pro Token TypeDef reprezentující, <xref:System.Type> který vrátí token nadřazené třídy pro.</span><span class="sxs-lookup"><span data-stu-id="5f760-106">[in] A TypeDef token representing the <xref:System.Type> to return the parent class token for.</span></span>  
  
 `ptdEnclosingClass`  
 <span data-ttu-id="5f760-107">mimo Ukazatel na token TypeDef pro <xref:System.Type> , který `tdNestedClass` je vnořen v.</span><span class="sxs-lookup"><span data-stu-id="5f760-107">[out] A pointer to the TypeDef token for the <xref:System.Type> that `tdNestedClass` is nested in.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f760-108">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5f760-108">Requirements</span></span>  
 <span data-ttu-id="5f760-109">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f760-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f760-110">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="5f760-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5f760-111">**Knihovna:** Zahrnuto jako prostředek v knihovně MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="5f760-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5f760-112">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f760-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f760-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5f760-113">See also</span></span>

- [<span data-ttu-id="5f760-114">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5f760-114">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="5f760-115">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="5f760-115">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
