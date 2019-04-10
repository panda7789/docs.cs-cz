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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0aa9b84c9e16811f799a3cd2ad096508db3f7d34
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59220497"
---
# <a name="corgenericparamattr-enumeration"></a><span data-ttu-id="29313-102">CorGenericParamAttr – výčet</span><span class="sxs-lookup"><span data-stu-id="29313-102">CorGenericParamAttr Enumeration</span></span>
<span data-ttu-id="29313-103">Obsahuje hodnoty, které popisují <xref:System.Type> parametry pro obecné typy, jako používá ve volání [imetadataemit2::definegenericparam –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md).</span><span class="sxs-lookup"><span data-stu-id="29313-103">Contains values that describe the <xref:System.Type> parameters for generic types, as used in calls to [IMetaDataEmit2::DefineGenericParam](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-definegenericparam-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29313-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29313-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="29313-105">Členové</span><span class="sxs-lookup"><span data-stu-id="29313-105">Members</span></span>  
  
|<span data-ttu-id="29313-106">Člen</span><span class="sxs-lookup"><span data-stu-id="29313-106">Member</span></span>|<span data-ttu-id="29313-107">Popis</span><span class="sxs-lookup"><span data-stu-id="29313-107">Description</span></span>|  
|------------|-----------------|  
|`gpVarianceMask`|<span data-ttu-id="29313-108">Parametr variance platí pouze pro obecné parametry pro rozhraní a delegátů.</span><span class="sxs-lookup"><span data-stu-id="29313-108">Parameter variance applies only to generic parameters for interfaces and delegates.</span></span>|  
|`gpNonVariant`|<span data-ttu-id="29313-109">Ukazuje na nepřítomnost variance.</span><span class="sxs-lookup"><span data-stu-id="29313-109">Indicates the absence of variance.</span></span>|  
|`gpCovariant`|<span data-ttu-id="29313-110">Označuje kovariance.</span><span class="sxs-lookup"><span data-stu-id="29313-110">Indicates covariance.</span></span>|  
|`gpContravariant`|<span data-ttu-id="29313-111">Označuje kontravariance.</span><span class="sxs-lookup"><span data-stu-id="29313-111">Indicates contravariance.</span></span>|  
|`gpSpecialConstraintMask`|<span data-ttu-id="29313-112">Zvláštní omezení můžete použít pro libovolné <xref:System.Type> parametru.</span><span class="sxs-lookup"><span data-stu-id="29313-112">Special constraints can apply to any <xref:System.Type> parameter.</span></span>|  
|`gpNoSpecialConstraint`|<span data-ttu-id="29313-113">Označuje, že žádná omezení platí pro <xref:System.Type> parametru.</span><span class="sxs-lookup"><span data-stu-id="29313-113">Indicates that no constraint applies to the <xref:System.Type> parameter.</span></span>|  
|`gpReferenceTypeConstraint`|<span data-ttu-id="29313-114">Označuje, že <xref:System.Type> parametr musí být typ odkazu.</span><span class="sxs-lookup"><span data-stu-id="29313-114">Indicates that the <xref:System.Type> parameter must be a reference type.</span></span>|  
|`gpNotNullableValueTypeConstraint`|<span data-ttu-id="29313-115">Označuje, že <xref:System.Type> parametr musí být typ hodnoty, který nemůže mít hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="29313-115">Indicates that the <xref:System.Type> parameter must be a value type that cannot be a null value.</span></span>|  
|`gpDefaultConstructorConstraint`|<span data-ttu-id="29313-116">Označuje, že <xref:System.Type> parametr musí mít výchozí veřejný konstruktor, který nepřijímá žádné parametry.</span><span class="sxs-lookup"><span data-stu-id="29313-116">Indicates that the <xref:System.Type> parameter must have a default public constructor that takes no parameters.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="29313-117">Požadavky</span><span class="sxs-lookup"><span data-stu-id="29313-117">Requirements</span></span>  
 <span data-ttu-id="29313-118">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29313-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29313-119">**Záhlaví:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="29313-119">**Header:** CorHdr.h</span></span>  
  
 **<span data-ttu-id="29313-120">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="29313-120">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="29313-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="29313-121">See also</span></span>

- [<span data-ttu-id="29313-122">Výčty metadat</span><span class="sxs-lookup"><span data-stu-id="29313-122">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
