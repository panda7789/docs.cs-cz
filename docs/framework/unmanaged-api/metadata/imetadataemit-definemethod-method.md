---
title: "IMetaDataEmit::DefineMethod – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IMetaDataEmit.DefineMethod
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineMethod
helpviewer_keywords:
- DefineMethod method [.NET Framework metadata]
- IMetaDataEmit::DefineMethod method [.NET Framework metadata]
ms.assetid: 3e2102c5-48b7-4c0e-b805-7e2b5e156e3d
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4fa136f5e6669e58ef709db5b53f538804cfcac2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="imetadataemitdefinemethod-method"></a><span data-ttu-id="ad170-102">IMetaDataEmit::DefineMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="ad170-102">IMetaDataEmit::DefineMethod Method</span></span>
<span data-ttu-id="ad170-103">Vytvoří definici metody nebo globální funkce zadaný podpisem a vrátí token tuto definici metody.</span><span class="sxs-lookup"><span data-stu-id="ad170-103">Creates a definition for a method or global function with the specified signature, and returns a token to that method definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad170-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ad170-104">Syntax</span></span>  
  
```  
HRESULT DefineMethod (      
    [in]  mdTypeDef         td,   
    [in]  LPCWSTR           szName,   
    [in]  DWORD             dwMethodFlags,   
    [in]  PCCOR_SIGNATURE   pvSigBlob,   
    [in]  ULONG             cbSigBlob,   
    [in]  ULONG             ulCodeRVA,   
    [in]  DWORD             dwImplFlags,   
    [out] mdMethodDef      *pmd  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ad170-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ad170-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="ad170-106">[v] `mdTypedef` Tokenu nadřazené třídy nebo rozhraní nadřazené metody.</span><span class="sxs-lookup"><span data-stu-id="ad170-106">[in] The `mdTypedef` token of the parent class or parent interface of the method.</span></span> <span data-ttu-id="ad170-107">Nastavit `td` k `mdTokenNil`v případě, že definujete globální funkce.</span><span class="sxs-lookup"><span data-stu-id="ad170-107">Set `td` to `mdTokenNil`, if you are defining a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="ad170-108">[v] Název členu v kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="ad170-108">[in] The member name in Unicode.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="ad170-109">[v] Hodnota [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) výčet, který určuje atributy, metoda nebo globální funkce.</span><span class="sxs-lookup"><span data-stu-id="ad170-109">[in] A value of the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration that specifies the attributes of the method or global function.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="ad170-110">[v] Podpis metody.</span><span class="sxs-lookup"><span data-stu-id="ad170-110">[in] The method signature.</span></span> <span data-ttu-id="ad170-111">Podpis je jako trvalý, protože zadaná.</span><span class="sxs-lookup"><span data-stu-id="ad170-111">The signature is persisted as supplied.</span></span> <span data-ttu-id="ad170-112">Pokud je třeba zadat další informace o všech parametrů, použijte [imetadataemit::setparamprops –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md) metoda.</span><span class="sxs-lookup"><span data-stu-id="ad170-112">If you need to specify additional information for any parameters, use the [IMetaDataEmit::SetParamProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md) method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="ad170-113">[v] Počet bajtů v `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="ad170-113">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="ad170-114">[v] Adresa kód.</span><span class="sxs-lookup"><span data-stu-id="ad170-114">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="ad170-115">[v] Hodnota [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) výčet, který určuje funkce implementace metody.</span><span class="sxs-lookup"><span data-stu-id="ad170-115">[in] A value of the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration that specifies the implementation features of the method.</span></span>  
  
 `pmd`  
 <span data-ttu-id="ad170-116">[out] Člen token.</span><span class="sxs-lookup"><span data-stu-id="ad170-116">[out] The member token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad170-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ad170-117">Remarks</span></span>  
 <span data-ttu-id="ad170-118">Metadat rozhraní API zaručuje udržení metody ve stejném pořadí jako volající vysílá je pro danou nadřazených třídy nebo rozhraní, které se určuje v `td` parametr.</span><span class="sxs-lookup"><span data-stu-id="ad170-118">The metadata API guarantees to persist methods in the same order as the caller emits them for a given enclosing class or interface, which is specified in the `td` parameter.</span></span>  
  
 <span data-ttu-id="ad170-119">Další informace týkající se použití `DefineMethod` a nastavení konkrétní parametrů je uveden níže.</span><span class="sxs-lookup"><span data-stu-id="ad170-119">Additional information regarding the use of `DefineMethod` and particular parameter settings is given below.</span></span>  
  
## <a name="slots-in-the-v-table"></a><span data-ttu-id="ad170-120">Sloty v tabulce V</span><span class="sxs-lookup"><span data-stu-id="ad170-120">Slots in the V-table</span></span>  
 <span data-ttu-id="ad170-121">Modul runtime používá metoda definice nastavit sloty tabulky v.</span><span class="sxs-lookup"><span data-stu-id="ad170-121">The runtime uses method definitions to set up v-table slots.</span></span> <span data-ttu-id="ad170-122">V případě, kdy je potřeba jeden nebo více sloty být bylo vynecháno, například tak, aby byly parita s rozložení rozhraní modelu COM, fiktivní je definována metoda tak, aby zaplnily slotu nebo sloty v v tabulce. Nastavte `dwMethodFlags` k `mdRTSpecialName` hodnotu [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) – výčet a zadejte název:</span><span class="sxs-lookup"><span data-stu-id="ad170-122">In the case where one or more slots need to be skipped, such as to preserve parity with a COM interface layout, a dummy method is defined to take up the slot or slots in the v-table; set the `dwMethodFlags` to the `mdRTSpecialName` value of the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration and specify the name as:</span></span>  
  
 <span data-ttu-id="ad170-123">_VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*></span><span class="sxs-lookup"><span data-stu-id="ad170-123">_VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*></span></span>  
  
 <span data-ttu-id="ad170-124">kde *SequenceNumber* má pořadové číslo metody a *CountOfSlots* je počet patic tak, aby přeskočil v tabulce v.</span><span class="sxs-lookup"><span data-stu-id="ad170-124">where *SequenceNumber* is the sequence number of the method and *CountOfSlots* is the number of slots to skip in the v-table.</span></span> <span data-ttu-id="ad170-125">Pokud *CountOfSlots* je tento parametr vynechán, předpokládá se 1.</span><span class="sxs-lookup"><span data-stu-id="ad170-125">If *CountOfSlots* is omitted, 1 is assumed.</span></span> <span data-ttu-id="ad170-126">Tyto metody fiktivní nejsou možné volat z kódu spravované nebo nespravované a pokusy o jejich volat z kódu spravované nebo nespravované, vygeneruje výjimku.</span><span class="sxs-lookup"><span data-stu-id="ad170-126">These dummy methods are not callable from either managed or unmanaged code and any attempt to call them, from either managed or unmanaged code, generates an exception.</span></span> <span data-ttu-id="ad170-127">Jejich jediným účelem je tak, aby zaplnily místo v – tabulka, která generuje modulu runtime pro integrace COM.</span><span class="sxs-lookup"><span data-stu-id="ad170-127">Their only purpose is to take up space in the v-table that the runtime generates for COM integration.</span></span>  
  
## <a name="duplicate-methods"></a><span data-ttu-id="ad170-128">Duplicitní metody</span><span class="sxs-lookup"><span data-stu-id="ad170-128">Duplicate Methods</span></span>  
 <span data-ttu-id="ad170-129">Duplicitní metody by nemělo definovat.</span><span class="sxs-lookup"><span data-stu-id="ad170-129">You should not define duplicate methods.</span></span> <span data-ttu-id="ad170-130">To znamená, by neměl volání `DefineMethod` duplicitní sadu hodnot v `td`, `wzName`, a `pvSig` parametry.</span><span class="sxs-lookup"><span data-stu-id="ad170-130">That is, you should not call `DefineMethod` with a duplicate set of values in the `td`, `wzName`, and `pvSig` parameters.</span></span> <span data-ttu-id="ad170-131">(Tyto tři parametry společně jednoznačně definovat metodu.).</span><span class="sxs-lookup"><span data-stu-id="ad170-131">(These three parameters together uniquely define the method.).</span></span> <span data-ttu-id="ad170-132">Ale můžete použít duplicitní triple za předpokladu, že pro jeden z definice metoda nastavíte `mdPrivateScope` bit ve `dwMethodFlags` parametr.</span><span class="sxs-lookup"><span data-stu-id="ad170-132">However, you can use a duplicate triple provided that, for one of the method definitions, you set the `mdPrivateScope` bit in the `dwMethodFlags` parameter.</span></span> <span data-ttu-id="ad170-133">( `mdPrivateScope` Bit znamená, že nebude kompilátor emitování odkaz na definici této metody.)</span><span class="sxs-lookup"><span data-stu-id="ad170-133">(The `mdPrivateScope` bit means that the compiler will not emit a reference to this method definition.)</span></span>  
  
## <a name="method-implementation-information"></a><span data-ttu-id="ad170-134">Informace o implementaci – metoda</span><span class="sxs-lookup"><span data-stu-id="ad170-134">Method Implementation Information</span></span>  
 <span data-ttu-id="ad170-135">Informace o implementaci metoda je často není známý v době, kdy je deklarovaná metodu.</span><span class="sxs-lookup"><span data-stu-id="ad170-135">Information about the method implementation is often not known at the time the method is declared.</span></span> <span data-ttu-id="ad170-136">Proto není potřeba předejte hodnoty `ulCodeRVA` a `dwImplFlags` parametry při volání metody `DefineMethod`.</span><span class="sxs-lookup"><span data-stu-id="ad170-136">Therefore, you do not need to pass values in the `ulCodeRVA` and `dwImplFlags` parameters when calling `DefineMethod`.</span></span> <span data-ttu-id="ad170-137">Hodnoty můžete zadat později prostřednictvím [imetadataemit::setmethodimplflags –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) nebo [imetadataemit::setrva –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md)podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="ad170-137">The values can be supplied later through [IMetaDataEmit::SetMethodImplFlags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) or [IMetaDataEmit::SetRVA](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md), as appropriate.</span></span>  
  
 <span data-ttu-id="ad170-138">V některých situacích, jako je například vyvolání platformy (PInvoke) nebo scénářů, zprostředkovatele komunikace s objekty COM, nebude zadaný text metoda, a `ulCodeRVA` musí být nastavena na nulu.</span><span class="sxs-lookup"><span data-stu-id="ad170-138">In some situations, such as platform invocation (PInvoke) or COM interop scenarios, the method body will not be supplied, and `ulCodeRVA` should be set to zero.</span></span> <span data-ttu-id="ad170-139">V těchto situacích by neměl být metodu označené jako abstraktní, protože modul runtime vyhledá implementace.</span><span class="sxs-lookup"><span data-stu-id="ad170-139">In these situations, the method should not be tagged as abstract, because the runtime will locate the implementation.</span></span>  
  
## <a name="defining-a-method-for-pinvoke"></a><span data-ttu-id="ad170-140">Definování metodu pro služby PInvoke</span><span class="sxs-lookup"><span data-stu-id="ad170-140">Defining a Method for PInvoke</span></span>  
 <span data-ttu-id="ad170-141">Pro každou nespravované funkci, která se má volat pomocí služby PInvoke je nutné definovat spravované metodu, která představuje funkci cíl nespravované.</span><span class="sxs-lookup"><span data-stu-id="ad170-141">For each unmanaged function to be called through PInvoke, you must define a managed method that represents the target unmanaged function.</span></span> <span data-ttu-id="ad170-142">Definujte metodu spravované pomocí `DefineMethod` pomocí některé z parametrů nastavit určité hodnoty v závislosti na způsobu, ve kterém je používána PInvoke:</span><span class="sxs-lookup"><span data-stu-id="ad170-142">To define the managed method, use `DefineMethod` with some of the parameters set to certain values, depending on the way in which PInvoke is used:</span></span>  
  
-   <span data-ttu-id="ad170-143">True PInvoke – zahrnuje volání metody externí nespravované, který se nachází v nespravované knihovny DLL.</span><span class="sxs-lookup"><span data-stu-id="ad170-143">True PInvoke - involves invocation of an external unmanaged method that resides in an unmanaged DLL.</span></span>  
  
-   <span data-ttu-id="ad170-144">Místní PInvoke - zahrnuje vyvolání nativní nespravované metodu, která je součástí aktuální spravovaného modulu.</span><span class="sxs-lookup"><span data-stu-id="ad170-144">Local PInvoke - involves invocation of a native unmanaged method that is embedded in the current managed module.</span></span>  
  
 <span data-ttu-id="ad170-145">Nastavení parametrů jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="ad170-145">The parameter settings are given in the following table.</span></span>  
  
|<span data-ttu-id="ad170-146">Parametr</span><span class="sxs-lookup"><span data-stu-id="ad170-146">Parameter</span></span>|<span data-ttu-id="ad170-147">Hodnoty true PInvoke</span><span class="sxs-lookup"><span data-stu-id="ad170-147">Values for true PInvoke</span></span>|<span data-ttu-id="ad170-148">Hodnoty pro místní služby PInvoke</span><span class="sxs-lookup"><span data-stu-id="ad170-148">Values for local PInvoke</span></span>|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||<span data-ttu-id="ad170-149">Nastavit `mdStatic`; vymazat `mdSynchronized` a `mdAbstract`.</span><span class="sxs-lookup"><span data-stu-id="ad170-149">Set `mdStatic`; clear `mdSynchronized` and `mdAbstract`.</span></span>|  
|`pvSigBlob`|<span data-ttu-id="ad170-150">Platný common language runtime (CLR) metoda podpis s parametry, které jsou platné spravované typy.</span><span class="sxs-lookup"><span data-stu-id="ad170-150">A valid common language runtime (CLR) method signature with parameters that are valid managed types.</span></span>|<span data-ttu-id="ad170-151">Neplatný podpis metody CLR s parametry, které jsou platné spravované typy.</span><span class="sxs-lookup"><span data-stu-id="ad170-151">A valid CLR method signature with parameters that are valid managed types.</span></span>|  
|`ulCodeRVA`||<span data-ttu-id="ad170-152">0</span><span class="sxs-lookup"><span data-stu-id="ad170-152">0</span></span>|  
|`dwImplFlags`|<span data-ttu-id="ad170-153">Nastavit `miCil` a `miManaged`.</span><span class="sxs-lookup"><span data-stu-id="ad170-153">Set `miCil` and `miManaged`.</span></span>|<span data-ttu-id="ad170-154">Nastavit `miNative` a `miUnmanaged`.</span><span class="sxs-lookup"><span data-stu-id="ad170-154">Set `miNative` and `miUnmanaged`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ad170-155">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ad170-155">Requirements</span></span>  
 <span data-ttu-id="ad170-156">**Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad170-156">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad170-157">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="ad170-157">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ad170-158">**Knihovna:** používat jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ad170-158">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ad170-159">**Verze rozhraní .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad170-159">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad170-160">Viz také</span><span class="sxs-lookup"><span data-stu-id="ad170-160">See Also</span></span>  
 [<span data-ttu-id="ad170-161">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ad170-161">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)  
 [<span data-ttu-id="ad170-162">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="ad170-162">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
