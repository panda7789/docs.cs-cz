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
ms.openlocfilehash: ea84b742c901ba58a3bb730f1f5033a0d90610ce
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84007374"
---
# <a name="corgenericparamattr-enumeration"></a><span data-ttu-id="05236-102">CorGenericParamAttr – výčet</span><span class="sxs-lookup"><span data-stu-id="05236-102">CorGenericParamAttr Enumeration</span></span>
<span data-ttu-id="05236-103">Obsahuje hodnoty, které popisují <xref:System.Type> parametry pro obecné typy, jak se používají v voláních [IMetaDataEmit2::D efinegenericparam](imetadataemit2-definegenericparam-method.md).</span><span class="sxs-lookup"><span data-stu-id="05236-103">Contains values that describe the <xref:System.Type> parameters for generic types, as used in calls to [IMetaDataEmit2::DefineGenericParam](imetadataemit2-definegenericparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05236-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05236-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="05236-105">Členové</span><span class="sxs-lookup"><span data-stu-id="05236-105">Members</span></span>  
  
|<span data-ttu-id="05236-106">Člen</span><span class="sxs-lookup"><span data-stu-id="05236-106">Member</span></span>|<span data-ttu-id="05236-107">Description</span><span class="sxs-lookup"><span data-stu-id="05236-107">Description</span></span>|  
|------------|-----------------|  
|`gpVarianceMask`|<span data-ttu-id="05236-108">Variance parametru se vztahuje pouze na Obecné parametry pro rozhraní a delegáty.</span><span class="sxs-lookup"><span data-stu-id="05236-108">Parameter variance applies only to generic parameters for interfaces and delegates.</span></span>|  
|`gpNonVariant`|<span data-ttu-id="05236-109">Označuje absenci odchylky.</span><span class="sxs-lookup"><span data-stu-id="05236-109">Indicates the absence of variance.</span></span>|  
|`gpCovariant`|<span data-ttu-id="05236-110">Označuje kovarianci.</span><span class="sxs-lookup"><span data-stu-id="05236-110">Indicates covariance.</span></span>|  
|`gpContravariant`|<span data-ttu-id="05236-111">Označuje kontravariance.</span><span class="sxs-lookup"><span data-stu-id="05236-111">Indicates contravariance.</span></span>|  
|`gpSpecialConstraintMask`|<span data-ttu-id="05236-112">Speciální omezení se můžou vztahovat na libovolný <xref:System.Type> parametr.</span><span class="sxs-lookup"><span data-stu-id="05236-112">Special constraints can apply to any <xref:System.Type> parameter.</span></span>|  
|`gpNoSpecialConstraint`|<span data-ttu-id="05236-113">Označuje, že se pro parametr neplatí žádné omezení <xref:System.Type> .</span><span class="sxs-lookup"><span data-stu-id="05236-113">Indicates that no constraint applies to the <xref:System.Type> parameter.</span></span>|  
|`gpReferenceTypeConstraint`|<span data-ttu-id="05236-114">Označuje, že <xref:System.Type> parametr musí být typ odkazu.</span><span class="sxs-lookup"><span data-stu-id="05236-114">Indicates that the <xref:System.Type> parameter must be a reference type.</span></span>|  
|`gpNotNullableValueTypeConstraint`|<span data-ttu-id="05236-115">Označuje, že <xref:System.Type> parametr musí být typ hodnoty, který nemůže být hodnota null.</span><span class="sxs-lookup"><span data-stu-id="05236-115">Indicates that the <xref:System.Type> parameter must be a value type that cannot be a null value.</span></span>|  
|`gpDefaultConstructorConstraint`|<span data-ttu-id="05236-116">Označuje, že <xref:System.Type> parametr musí mít výchozí veřejný konstruktor, který nepřijímá žádné parametry.</span><span class="sxs-lookup"><span data-stu-id="05236-116">Indicates that the <xref:System.Type> parameter must have a default public constructor that takes no parameters.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="05236-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="05236-117">Requirements</span></span>  
 <span data-ttu-id="05236-118">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="05236-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05236-119">**Hlavička:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="05236-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="05236-120">**Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05236-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05236-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="05236-121">See also</span></span>

- [<span data-ttu-id="05236-122">Výčty pro metadata</span><span class="sxs-lookup"><span data-stu-id="05236-122">Metadata Enumerations</span></span>](metadata-enumerations.md)
