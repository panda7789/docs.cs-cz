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
ms.openlocfilehash: e4abf876681d5b04555c9f030a94b722874e326e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450279"
---
# <a name="corgenericparamattr-enumeration"></a><span data-ttu-id="40963-102">CorGenericParamAttr – výčet</span><span class="sxs-lookup"><span data-stu-id="40963-102">CorGenericParamAttr Enumeration</span></span>
<span data-ttu-id="40963-103">Obsahuje hodnoty, které popisují parametry <xref:System.Type> pro obecné typy, jak se používají v voláních [IMetaDataEmit2::D efinegenericparam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md).</span><span class="sxs-lookup"><span data-stu-id="40963-103">Contains values that describe the <xref:System.Type> parameters for generic types, as used in calls to [IMetaDataEmit2::DefineGenericParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40963-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="40963-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="40963-105">Členové</span><span class="sxs-lookup"><span data-stu-id="40963-105">Members</span></span>  
  
|<span data-ttu-id="40963-106">Člen</span><span class="sxs-lookup"><span data-stu-id="40963-106">Member</span></span>|<span data-ttu-id="40963-107">Popis</span><span class="sxs-lookup"><span data-stu-id="40963-107">Description</span></span>|  
|------------|-----------------|  
|`gpVarianceMask`|<span data-ttu-id="40963-108">Variance parametru se vztahuje pouze na Obecné parametry pro rozhraní a delegáty.</span><span class="sxs-lookup"><span data-stu-id="40963-108">Parameter variance applies only to generic parameters for interfaces and delegates.</span></span>|  
|`gpNonVariant`|<span data-ttu-id="40963-109">Označuje absenci odchylky.</span><span class="sxs-lookup"><span data-stu-id="40963-109">Indicates the absence of variance.</span></span>|  
|`gpCovariant`|<span data-ttu-id="40963-110">Označuje kovarianci.</span><span class="sxs-lookup"><span data-stu-id="40963-110">Indicates covariance.</span></span>|  
|`gpContravariant`|<span data-ttu-id="40963-111">Označuje kontravariance.</span><span class="sxs-lookup"><span data-stu-id="40963-111">Indicates contravariance.</span></span>|  
|`gpSpecialConstraintMask`|<span data-ttu-id="40963-112">Speciální omezení se můžou vztahovat na libovolný <xref:System.Type> parametr.</span><span class="sxs-lookup"><span data-stu-id="40963-112">Special constraints can apply to any <xref:System.Type> parameter.</span></span>|  
|`gpNoSpecialConstraint`|<span data-ttu-id="40963-113">Indikuje, že se pro parametr <xref:System.Type> neplatí žádné omezení.</span><span class="sxs-lookup"><span data-stu-id="40963-113">Indicates that no constraint applies to the <xref:System.Type> parameter.</span></span>|  
|`gpReferenceTypeConstraint`|<span data-ttu-id="40963-114">Označuje, že parametr <xref:System.Type> musí být typ odkazu.</span><span class="sxs-lookup"><span data-stu-id="40963-114">Indicates that the <xref:System.Type> parameter must be a reference type.</span></span>|  
|`gpNotNullableValueTypeConstraint`|<span data-ttu-id="40963-115">Určuje, že parametr <xref:System.Type> musí být hodnotový typ, který nemůže být hodnota null.</span><span class="sxs-lookup"><span data-stu-id="40963-115">Indicates that the <xref:System.Type> parameter must be a value type that cannot be a null value.</span></span>|  
|`gpDefaultConstructorConstraint`|<span data-ttu-id="40963-116">Určuje, že parametr <xref:System.Type> musí mít výchozí veřejný konstruktor, který nepřijímá žádné parametry.</span><span class="sxs-lookup"><span data-stu-id="40963-116">Indicates that the <xref:System.Type> parameter must have a default public constructor that takes no parameters.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="40963-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="40963-117">Requirements</span></span>  
 <span data-ttu-id="40963-118">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40963-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40963-119">**Hlavička:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="40963-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="40963-120">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40963-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40963-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="40963-121">See also</span></span>

- [<span data-ttu-id="40963-122">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="40963-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
