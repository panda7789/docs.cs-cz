---
title: "CorGenericParamAttr – výčet"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorGenericParamAttr
api_location: mscoree.dll
api_type: COM
f1_keywords: CorGenericParamAttr
helpviewer_keywords: CorGenericParamAttr enumeration [.NET Framework metadata]
ms.assetid: 36c76266-71d8-48dc-bd89-54943fa659c1
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 95d7a6097766c8e2389e9828f54e81e37ffea454
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="corgenericparamattr-enumeration"></a><span data-ttu-id="c351e-102">CorGenericParamAttr – výčet</span><span class="sxs-lookup"><span data-stu-id="c351e-102">CorGenericParamAttr Enumeration</span></span>
<span data-ttu-id="c351e-103">Obsahuje hodnoty, které popisují <xref:System.Type> parametry pro obecné typy, jako používá volání [imetadataemit2::definegenericparam –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md).</span><span class="sxs-lookup"><span data-stu-id="c351e-103">Contains values that describe the <xref:System.Type> parameters for generic types, as used in calls to [IMetaDataEmit2::DefineGenericParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c351e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c351e-104">Syntax</span></span>  
  
```  
typedef enum CorGenericParamAttr {  
  
    gpVarianceMask                     =   0x0003,  
    gpNonVariant                       =   0x0000,   
    gpCovariant                        =   0x0001,  
    gpContravariant                    =   0x0002,  
  
    gpSpecialConstraintMask            =   0x001C,  
    gpNoSpecialConstraint              =   0x0000,  
    gpReferenceTypeConstraint          =   0x0004,   
    gpNotNullableValueTypeConstraint   =   0x0008,  
    gpDefaultConstructorConstraint     =   0x0010  
  
} CorGenericParamAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="c351e-105">Členové</span><span class="sxs-lookup"><span data-stu-id="c351e-105">Members</span></span>  
  
|<span data-ttu-id="c351e-106">Člen</span><span class="sxs-lookup"><span data-stu-id="c351e-106">Member</span></span>|<span data-ttu-id="c351e-107">Popis</span><span class="sxs-lookup"><span data-stu-id="c351e-107">Description</span></span>|  
|------------|-----------------|  
|`gpVarianceMask`|<span data-ttu-id="c351e-108">Parametr odchylky platí pouze pro obecné parametry pro rozhraní a delegáti.</span><span class="sxs-lookup"><span data-stu-id="c351e-108">Parameter variance applies only to generic parameters for interfaces and delegates.</span></span>|  
|`gpNonVariant`|<span data-ttu-id="c351e-109">Ukazuje na nepřítomnost odchylky.</span><span class="sxs-lookup"><span data-stu-id="c351e-109">Indicates the absence of variance.</span></span>|  
|`gpCovariant`|<span data-ttu-id="c351e-110">Označuje kovariance.</span><span class="sxs-lookup"><span data-stu-id="c351e-110">Indicates covariance.</span></span>|  
|`gpContravariant`|<span data-ttu-id="c351e-111">Označuje kontravariance.</span><span class="sxs-lookup"><span data-stu-id="c351e-111">Indicates contravariance.</span></span>|  
|`gpSpecialConstraintMask`|<span data-ttu-id="c351e-112">Můžete použít zvláštní omezení pro libovolné <xref:System.Type> parametr.</span><span class="sxs-lookup"><span data-stu-id="c351e-112">Special constraints can apply to any <xref:System.Type> parameter.</span></span>|  
|`gpNoSpecialConstraint`|<span data-ttu-id="c351e-113">Označuje, že žádné omezení platí pro <xref:System.Type> parametr.</span><span class="sxs-lookup"><span data-stu-id="c351e-113">Indicates that no constraint applies to the <xref:System.Type> parameter.</span></span>|  
|`gpReferenceTypeConstraint`|<span data-ttu-id="c351e-114">Určuje, že <xref:System.Type> parametr musí být odkazového typu.</span><span class="sxs-lookup"><span data-stu-id="c351e-114">Indicates that the <xref:System.Type> parameter must be a reference type.</span></span>|  
|`gpNotNullableValueTypeConstraint`|<span data-ttu-id="c351e-115">Určuje, že <xref:System.Type> parametr musí být typ hodnoty, který nemůže mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="c351e-115">Indicates that the <xref:System.Type> parameter must be a value type that cannot be a null value.</span></span>|  
|`gpDefaultConstructorConstraint`|<span data-ttu-id="c351e-116">Určuje, že <xref:System.Type> parametr musí mít výchozí veřejný konstruktor, které nepřijímá žádné parametry.</span><span class="sxs-lookup"><span data-stu-id="c351e-116">Indicates that the <xref:System.Type> parameter must have a default public constructor that takes no parameters.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c351e-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c351e-117">Requirements</span></span>  
 <span data-ttu-id="c351e-118">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c351e-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c351e-119">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="c351e-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="c351e-120">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c351e-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c351e-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="c351e-121">See Also</span></span>  
 [<span data-ttu-id="c351e-122">Výčty metadat</span><span class="sxs-lookup"><span data-stu-id="c351e-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
