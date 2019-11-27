---
title: IMetaDataImport2 – rozhraní
ms.date: 03/30/2017
api_name:
- IMetaDataImport2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2
helpviewer_keywords:
- IMetaDataImport2 interface [.NET Framework metadata]
ms.assetid: d39b2b87-ba53-4771-ae53-952a68452511
topic_type:
- apiref
ms.openlocfilehash: 0fd7915ef46899bdce8312bc6e8a466167e26382
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429207"
---
# <a name="imetadataimport2-interface"></a><span data-ttu-id="2cf70-102">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2cf70-102">IMetaDataImport2 Interface</span></span>
<span data-ttu-id="2cf70-103">Rozšiřuje rozhraní [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) , aby poskytovala schopnost pracovat s obecnými typy.</span><span class="sxs-lookup"><span data-stu-id="2cf70-103">Extends the [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface to provide the capability of working with generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2cf70-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2cf70-104">Methods</span></span>  
  
|<span data-ttu-id="2cf70-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2cf70-105">Method</span></span>|<span data-ttu-id="2cf70-106">Popis</span><span class="sxs-lookup"><span data-stu-id="2cf70-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2cf70-107">EnumGenericParamConstraints – metoda</span><span class="sxs-lookup"><span data-stu-id="2cf70-107">EnumGenericParamConstraints Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparamconstraints-method.md)|<span data-ttu-id="2cf70-108">Získá enumerátor pro pole omezení obecného parametru přidruženého k obecnému parametru reprezentovanému zadaným tokenem.</span><span class="sxs-lookup"><span data-stu-id="2cf70-108">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>|  
|[<span data-ttu-id="2cf70-109">EnumGenericParams – metoda</span><span class="sxs-lookup"><span data-stu-id="2cf70-109">EnumGenericParams Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md)|<span data-ttu-id="2cf70-110">Získá enumerátor pro pole tokenů obecných parametrů přidružených k zadanému tokenu TypeDef nebo MethodDef.</span><span class="sxs-lookup"><span data-stu-id="2cf70-110">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>|  
|[<span data-ttu-id="2cf70-111">EnumMethodSpecs – metoda</span><span class="sxs-lookup"><span data-stu-id="2cf70-111">EnumMethodSpecs Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enummethodspecs-method.md)|<span data-ttu-id="2cf70-112">Získá enumerátor pro pole tokenů MethodSpec přidružených k zadanému tokenu MethodDef nebo MemberRef.</span><span class="sxs-lookup"><span data-stu-id="2cf70-112">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>|  
|[<span data-ttu-id="2cf70-113">GetGenericParamConstraintProps – metoda</span><span class="sxs-lookup"><span data-stu-id="2cf70-113">GetGenericParamConstraintProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamconstraintprops-method.md)|<span data-ttu-id="2cf70-114">Získá metadata přidružená k omezení obecného parametru reprezentované zadaným tokenem omezení.</span><span class="sxs-lookup"><span data-stu-id="2cf70-114">Gets the metadata associated with the generic parameter constraint represented by the specified constraint token.</span></span>|  
|[<span data-ttu-id="2cf70-115">GetGenericParamProps – metoda</span><span class="sxs-lookup"><span data-stu-id="2cf70-115">GetGenericParamProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamprops-method.md)|<span data-ttu-id="2cf70-116">Získá metadata přidružená k obecnému parametru reprezentovanému zadaným tokenem.</span><span class="sxs-lookup"><span data-stu-id="2cf70-116">Gets the metadata associated with the generic parameter represented by the specified token.</span></span>|  
|[<span data-ttu-id="2cf70-117">GetMethodSpecProps – metoda</span><span class="sxs-lookup"><span data-stu-id="2cf70-117">GetMethodSpecProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getmethodspecprops-method.md)|<span data-ttu-id="2cf70-118">Získá podpis metadat metody, na kterou odkazuje zadaný token MethodSpec.</span><span class="sxs-lookup"><span data-stu-id="2cf70-118">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>|  
|[<span data-ttu-id="2cf70-119">GetPEKind – metoda</span><span class="sxs-lookup"><span data-stu-id="2cf70-119">GetPEKind Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)|<span data-ttu-id="2cf70-120">Získá hodnotu identifikující povahu kódu v přenositelném spustitelném souboru (PE), obvykle soubor DLL nebo EXE, definovaný v aktuálním oboru metadat.</span><span class="sxs-lookup"><span data-stu-id="2cf70-120">Gets a value identifying the nature of the code in a portable executable (PE) file, typically a DLL or EXE file, defined in the current metadata scope</span></span>|  
|[<span data-ttu-id="2cf70-121">GetVersionString – metoda</span><span class="sxs-lookup"><span data-stu-id="2cf70-121">GetVersionString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getversionstring-method.md)|<span data-ttu-id="2cf70-122">Získá číslo verze modulu runtime, který byl použit k sestavení sestavení.</span><span class="sxs-lookup"><span data-stu-id="2cf70-122">Gets the version number of the runtime that was used to build the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2cf70-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2cf70-123">Requirements</span></span>  
 <span data-ttu-id="2cf70-124">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2cf70-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2cf70-125">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="2cf70-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2cf70-126">**Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="2cf70-126">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2cf70-127">**Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2cf70-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cf70-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2cf70-128">See also</span></span>

- <xref:System.Reflection.PortableExecutableKinds>
- [<span data-ttu-id="2cf70-129">Rozhraní pro metadata</span><span class="sxs-lookup"><span data-stu-id="2cf70-129">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="2cf70-130">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="2cf70-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
