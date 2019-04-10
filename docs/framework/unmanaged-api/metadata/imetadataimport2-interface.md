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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6717c48fca14f2200f783a984594388ef3b29c15
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59211923"
---
# <a name="imetadataimport2-interface"></a><span data-ttu-id="da7e7-102">IMetaDataImport2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="da7e7-102">IMetaDataImport2 Interface</span></span>
<span data-ttu-id="da7e7-103">Rozšiřuje [imetadataimport –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) rozhraní poskytovat funkce pro práci s obecných typů.</span><span class="sxs-lookup"><span data-stu-id="da7e7-103">Extends the [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) interface to provide the capability of working with generic types.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="da7e7-104">Metody</span><span class="sxs-lookup"><span data-stu-id="da7e7-104">Methods</span></span>  
  
|<span data-ttu-id="da7e7-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="da7e7-105">Method</span></span>|<span data-ttu-id="da7e7-106">Popis</span><span class="sxs-lookup"><span data-stu-id="da7e7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="da7e7-107">EnumGenericParamConstraints – metoda</span><span class="sxs-lookup"><span data-stu-id="da7e7-107">EnumGenericParamConstraints Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparamconstraints-method.md)|<span data-ttu-id="da7e7-108">Získá enumerátor pro celou řadu omezeních obecných parametrů, které jsou přidružené k obecný parametr reprezentována zadaného tokenu.</span><span class="sxs-lookup"><span data-stu-id="da7e7-108">Gets an enumerator for an array of generic parameter constraints associated with the generic parameter represented by the specified token.</span></span>|  
|[<span data-ttu-id="da7e7-109">EnumGenericParams – metoda</span><span class="sxs-lookup"><span data-stu-id="da7e7-109">EnumGenericParams Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md)|<span data-ttu-id="da7e7-110">Získá enumerátor pro celou řadu obecný parametr tokeny přidružené k zadaným TypeDef nebo MethodDef token.</span><span class="sxs-lookup"><span data-stu-id="da7e7-110">Gets an enumerator for an array of generic parameter tokens associated with the specified TypeDef or MethodDef token.</span></span>|  
|[<span data-ttu-id="da7e7-111">EnumMethodSpecs – metoda</span><span class="sxs-lookup"><span data-stu-id="da7e7-111">EnumMethodSpecs Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enummethodspecs-method.md)|<span data-ttu-id="da7e7-112">Získá enumerátor pro celou řadu MethodSpec tokeny přidružené k zadaným MethodDef nebo MemberRef token.</span><span class="sxs-lookup"><span data-stu-id="da7e7-112">Gets an enumerator for an array of MethodSpec tokens associated with the specified MethodDef or MemberRef token.</span></span>|  
|[<span data-ttu-id="da7e7-113">GetGenericParamConstraintProps – metoda</span><span class="sxs-lookup"><span data-stu-id="da7e7-113">GetGenericParamConstraintProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamconstraintprops-method.md)|<span data-ttu-id="da7e7-114">Získá metadata přidružená k omezení obecného parametru reprezentována token zadané omezení.</span><span class="sxs-lookup"><span data-stu-id="da7e7-114">Gets the metadata associated with the generic parameter constraint represented by the specified constraint token.</span></span>|  
|[<span data-ttu-id="da7e7-115">GetGenericParamProps – metoda</span><span class="sxs-lookup"><span data-stu-id="da7e7-115">GetGenericParamProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamprops-method.md)|<span data-ttu-id="da7e7-116">Získá metadata přidružená k obecný parametr reprezentována zadaného tokenu.</span><span class="sxs-lookup"><span data-stu-id="da7e7-116">Gets the metadata associated with the generic parameter represented by the specified token.</span></span>|  
|[<span data-ttu-id="da7e7-117">GetMethodSpecProps – metoda</span><span class="sxs-lookup"><span data-stu-id="da7e7-117">GetMethodSpecProps Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getmethodspecprops-method.md)|<span data-ttu-id="da7e7-118">Získá metadata podpis metody odkazuje zadaný token MethodSpec token.</span><span class="sxs-lookup"><span data-stu-id="da7e7-118">Gets the metadata signature of the method referenced by the specified MethodSpec token.</span></span>|  
|[<span data-ttu-id="da7e7-119">GetPEKind – metoda</span><span class="sxs-lookup"><span data-stu-id="da7e7-119">GetPEKind Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)|<span data-ttu-id="da7e7-120">Získá hodnotu určující druh kódu do přenosného spustitelného (PE) soubor, obvykle knihovny DLL nebo EXE souboru, definované v aktuálním oboru metadat</span><span class="sxs-lookup"><span data-stu-id="da7e7-120">Gets a value identifying the nature of the code in a portable executable (PE) file, typically a DLL or EXE file, defined in the current metadata scope</span></span>|  
|[<span data-ttu-id="da7e7-121">GetVersionString – metoda</span><span class="sxs-lookup"><span data-stu-id="da7e7-121">GetVersionString Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getversionstring-method.md)|<span data-ttu-id="da7e7-122">Získá číslo verze modulu runtime, která byla použita k vytvoření sestavení.</span><span class="sxs-lookup"><span data-stu-id="da7e7-122">Gets the version number of the runtime that was used to build the assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="da7e7-123">Požadavky</span><span class="sxs-lookup"><span data-stu-id="da7e7-123">Requirements</span></span>  
 <span data-ttu-id="da7e7-124">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da7e7-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da7e7-125">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="da7e7-125">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="da7e7-126">**Knihovna:** Použít jako prostředek v MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="da7e7-126">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 **<span data-ttu-id="da7e7-127">Verze rozhraní .NET framework:</span><span class="sxs-lookup"><span data-stu-id="da7e7-127">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="da7e7-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="da7e7-128">See also</span></span>

- <xref:System.Reflection.PortableExecutableKinds>
- [<span data-ttu-id="da7e7-129">Rozhraní metadat</span><span class="sxs-lookup"><span data-stu-id="da7e7-129">Metadata Interfaces</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [<span data-ttu-id="da7e7-130">IMetaDataImport – rozhraní</span><span class="sxs-lookup"><span data-stu-id="da7e7-130">IMetaDataImport Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
