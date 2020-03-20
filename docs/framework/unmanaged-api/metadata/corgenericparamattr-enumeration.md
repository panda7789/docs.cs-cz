---
title: CorGenericParamAttr – výčet
ms.date: 03/30/2017
api_name:
- CorGenericParamAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorGenericParamAttr
helpviewer_keywords:
- CorGenericParamAttr enumeration [.NET Framework metadata]
ms.assetid: 36c76266-71d8-48dc-bd89-54943fa659c1
topic_type:
- apiref
ms.openlocfilehash: bf0008ce9429671f0c156df4256bed0b2aaee184
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176172"
---
# <a name="corgenericparamattr-enumeration"></a><span data-ttu-id="b84b7-102">CorGenericParamAttr – výčet</span><span class="sxs-lookup"><span data-stu-id="b84b7-102">CorGenericParamAttr Enumeration</span></span>
<span data-ttu-id="b84b7-103">Obsahuje hodnoty, <xref:System.Type> které popisují parametry pro obecné typy, jak je použito v volání [IMetaDataEmit2::DefineGenericParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md).</span><span class="sxs-lookup"><span data-stu-id="b84b7-103">Contains values that describe the <xref:System.Type> parameters for generic types, as used in calls to [IMetaDataEmit2::DefineGenericParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b84b7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b84b7-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="b84b7-105">Členové</span><span class="sxs-lookup"><span data-stu-id="b84b7-105">Members</span></span>  
  
|<span data-ttu-id="b84b7-106">Člen</span><span class="sxs-lookup"><span data-stu-id="b84b7-106">Member</span></span>|<span data-ttu-id="b84b7-107">Popis</span><span class="sxs-lookup"><span data-stu-id="b84b7-107">Description</span></span>|  
|------------|-----------------|  
|`gpVarianceMask`|<span data-ttu-id="b84b7-108">Odchylka parametrů platí pouze pro obecné parametry pro rozhraní a delegáty.</span><span class="sxs-lookup"><span data-stu-id="b84b7-108">Parameter variance applies only to generic parameters for interfaces and delegates.</span></span>|  
|`gpNonVariant`|<span data-ttu-id="b84b7-109">Označuje nepřítomnost odchylky.</span><span class="sxs-lookup"><span data-stu-id="b84b7-109">Indicates the absence of variance.</span></span>|  
|`gpCovariant`|<span data-ttu-id="b84b7-110">Označuje kovariance.</span><span class="sxs-lookup"><span data-stu-id="b84b7-110">Indicates covariance.</span></span>|  
|`gpContravariant`|<span data-ttu-id="b84b7-111">Označuje kontravariance.</span><span class="sxs-lookup"><span data-stu-id="b84b7-111">Indicates contravariance.</span></span>|  
|`gpSpecialConstraintMask`|<span data-ttu-id="b84b7-112">Zvláštní omezení lze použít <xref:System.Type> na libovolný parametr.</span><span class="sxs-lookup"><span data-stu-id="b84b7-112">Special constraints can apply to any <xref:System.Type> parameter.</span></span>|  
|`gpNoSpecialConstraint`|<span data-ttu-id="b84b7-113">Označuje, že na <xref:System.Type> parametr se nevztahuje žádné omezení.</span><span class="sxs-lookup"><span data-stu-id="b84b7-113">Indicates that no constraint applies to the <xref:System.Type> parameter.</span></span>|  
|`gpReferenceTypeConstraint`|<span data-ttu-id="b84b7-114">Označuje, <xref:System.Type> že parametr musí být typ odkazu.</span><span class="sxs-lookup"><span data-stu-id="b84b7-114">Indicates that the <xref:System.Type> parameter must be a reference type.</span></span>|  
|`gpNotNullableValueTypeConstraint`|<span data-ttu-id="b84b7-115">Označuje, <xref:System.Type> že parametr musí být typ hodnoty, který nemůže být nulovou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="b84b7-115">Indicates that the <xref:System.Type> parameter must be a value type that cannot be a null value.</span></span>|  
|`gpDefaultConstructorConstraint`|<span data-ttu-id="b84b7-116">Označuje, <xref:System.Type> že parametr musí mít výchozí veřejný konstruktor, který nepřebírá žádné parametry.</span><span class="sxs-lookup"><span data-stu-id="b84b7-116">Indicates that the <xref:System.Type> parameter must have a default public constructor that takes no parameters.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b84b7-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b84b7-117">Requirements</span></span>  
 <span data-ttu-id="b84b7-118">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b84b7-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b84b7-119">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="b84b7-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="b84b7-120">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b84b7-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b84b7-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="b84b7-121">See also</span></span>

- [<span data-ttu-id="b84b7-122">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="b84b7-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
