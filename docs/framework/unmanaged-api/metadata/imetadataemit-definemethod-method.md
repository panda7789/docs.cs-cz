---
title: IMetaDataEmit::DefineMethod – metoda
ms.date: 03/30/2017
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
ms.openlocfilehash: d4f3c95428d6f0f8807e284c5b54582428176511
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177667"
---
# <a name="imetadataemitdefinemethod-method"></a><span data-ttu-id="659ee-102">IMetaDataEmit::DefineMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="659ee-102">IMetaDataEmit::DefineMethod Method</span></span>
<span data-ttu-id="659ee-103">Vytvoří definici metody nebo globální funkce se zadaným podpisem a vrátí token této definici metody.</span><span class="sxs-lookup"><span data-stu-id="659ee-103">Creates a definition for a method or global function with the specified signature, and returns a token to that method definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="659ee-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="659ee-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="parameters"></a><span data-ttu-id="659ee-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="659ee-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="659ee-106">[v] Token `mdTypedef` nadřazené třídy nebo nadřazeného rozhraní metody.</span><span class="sxs-lookup"><span data-stu-id="659ee-106">[in] The `mdTypedef` token of the parent class or parent interface of the method.</span></span> <span data-ttu-id="659ee-107">Pokud `td` `mdTokenNil`definujete globální funkci, nastavte na .</span><span class="sxs-lookup"><span data-stu-id="659ee-107">Set `td` to `mdTokenNil`, if you are defining a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="659ee-108">[v] Název člena v unicode.</span><span class="sxs-lookup"><span data-stu-id="659ee-108">[in] The member name in Unicode.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="659ee-109">[v] Hodnota [cormethodattr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) výčtu, který určuje atributy metody nebo globální funkce.</span><span class="sxs-lookup"><span data-stu-id="659ee-109">[in] A value of the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration that specifies the attributes of the method or global function.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="659ee-110">[v] Podpis metody.</span><span class="sxs-lookup"><span data-stu-id="659ee-110">[in] The method signature.</span></span> <span data-ttu-id="659ee-111">Podpis je trvalý podle dodaných.</span><span class="sxs-lookup"><span data-stu-id="659ee-111">The signature is persisted as supplied.</span></span> <span data-ttu-id="659ee-112">Pokud potřebujete zadat další informace pro všechny parametry, použijte metodu [IMetaDataEmit::SetParamProps.](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md)</span><span class="sxs-lookup"><span data-stu-id="659ee-112">If you need to specify additional information for any parameters, use the [IMetaDataEmit::SetParamProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md) method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="659ee-113">[v] Počet bajtů v `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="659ee-113">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="659ee-114">[v] Adresa kódu.</span><span class="sxs-lookup"><span data-stu-id="659ee-114">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="659ee-115">[v] Hodnota [cormethodimpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) výčtu, který určuje funkce implementace metody.</span><span class="sxs-lookup"><span data-stu-id="659ee-115">[in] A value of the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration that specifies the implementation features of the method.</span></span>  
  
 `pmd`  
 <span data-ttu-id="659ee-116">[out] Člen token.</span><span class="sxs-lookup"><span data-stu-id="659ee-116">[out] The member token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="659ee-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="659ee-117">Remarks</span></span>  
 <span data-ttu-id="659ee-118">Rozhraní API metadat zaručuje zachovat metody ve stejném pořadí jako volající vydává pro dané ohraničující `td` třídy nebo rozhraní, která je určena v parametru.</span><span class="sxs-lookup"><span data-stu-id="659ee-118">The metadata API guarantees to persist methods in the same order as the caller emits them for a given enclosing class or interface, which is specified in the `td` parameter.</span></span>  
  
 <span data-ttu-id="659ee-119">Další informace týkající `DefineMethod` se použití a konkrétní nastavení parametrů jsou uvedeny níže.</span><span class="sxs-lookup"><span data-stu-id="659ee-119">Additional information regarding the use of `DefineMethod` and particular parameter settings is given below.</span></span>  
  
## <a name="slots-in-the-v-table"></a><span data-ttu-id="659ee-120">Sloty ve V-tabulce</span><span class="sxs-lookup"><span data-stu-id="659ee-120">Slots in the V-table</span></span>  
 <span data-ttu-id="659ee-121">Runtime používá definice metod k nastavení slotů v-table.</span><span class="sxs-lookup"><span data-stu-id="659ee-121">The runtime uses method definitions to set up v-table slots.</span></span> <span data-ttu-id="659ee-122">V případě, že je třeba přeskočit jeden nebo více slotů, například zachovat paritu s rozvržením rozhraní COM, je definována fiktivní metoda, která zabere patici nebo patky ve v-tabulce; nastavte `dwMethodFlags` hodnotu `mdRTSpecialName` výčtu [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) a zadejte název jako:</span><span class="sxs-lookup"><span data-stu-id="659ee-122">In the case where one or more slots need to be skipped, such as to preserve parity with a COM interface layout, a dummy method is defined to take up the slot or slots in the v-table; set the `dwMethodFlags` to the `mdRTSpecialName` value of the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration and specify the name as:</span></span>  
  
 <span data-ttu-id="659ee-123">_VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*></span><span class="sxs-lookup"><span data-stu-id="659ee-123">_VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*></span></span>
  
 <span data-ttu-id="659ee-124">where *SequenceNumber* je pořadové číslo metody a *CountOfSlots* je počet slotů přeskočit v tabulce.</span><span class="sxs-lookup"><span data-stu-id="659ee-124">where *SequenceNumber* is the sequence number of the method and *CountOfSlots* is the number of slots to skip in the v-table.</span></span> <span data-ttu-id="659ee-125">Pokud *CountOfSlots* je vynechán, 1 se předpokládá.</span><span class="sxs-lookup"><span data-stu-id="659ee-125">If *CountOfSlots* is omitted, 1 is assumed.</span></span> <span data-ttu-id="659ee-126">Tyto fiktivní metody nelze volat ze spravovaného ani nespravovaného kódu a jakýkoli pokus o jejich volání ze spravovaného nebo nespravovaného kódu generuje výjimku.</span><span class="sxs-lookup"><span data-stu-id="659ee-126">These dummy methods are not callable from either managed or unmanaged code and any attempt to call them, from either managed or unmanaged code, generates an exception.</span></span> <span data-ttu-id="659ee-127">Jejich jediným účelem je zabírají místo v tabulce, která generuje za běhu pro integraci com.</span><span class="sxs-lookup"><span data-stu-id="659ee-127">Their only purpose is to take up space in the v-table that the runtime generates for COM integration.</span></span>  
  
## <a name="duplicate-methods"></a><span data-ttu-id="659ee-128">Duplicitní metody</span><span class="sxs-lookup"><span data-stu-id="659ee-128">Duplicate Methods</span></span>  
 <span data-ttu-id="659ee-129">Neměli byste definovat duplicitní metody.</span><span class="sxs-lookup"><span data-stu-id="659ee-129">You should not define duplicate methods.</span></span> <span data-ttu-id="659ee-130">To znamená, že `DefineMethod` byste neměli volat s `td` `wzName`duplicitní `pvSig` sadou hodnot v , a parametry.</span><span class="sxs-lookup"><span data-stu-id="659ee-130">That is, you should not call `DefineMethod` with a duplicate set of values in the `td`, `wzName`, and `pvSig` parameters.</span></span> <span data-ttu-id="659ee-131">(Tyto tři parametry společně jednoznačně definují metodu.).</span><span class="sxs-lookup"><span data-stu-id="659ee-131">(These three parameters together uniquely define the method.).</span></span> <span data-ttu-id="659ee-132">Můžete však použít duplicitní trojitý za předpokladu, že pro `mdPrivateScope` jednu `dwMethodFlags` z definic metody nastavíte bit v parametru.</span><span class="sxs-lookup"><span data-stu-id="659ee-132">However, you can use a duplicate triple provided that, for one of the method definitions, you set the `mdPrivateScope` bit in the `dwMethodFlags` parameter.</span></span> <span data-ttu-id="659ee-133">(Bit `mdPrivateScope` znamená, že kompilátor nebude vyzařovat odkaz na tuto definici metody.)</span><span class="sxs-lookup"><span data-stu-id="659ee-133">(The `mdPrivateScope` bit means that the compiler will not emit a reference to this method definition.)</span></span>  
  
## <a name="method-implementation-information"></a><span data-ttu-id="659ee-134">Informace o implementaci metody</span><span class="sxs-lookup"><span data-stu-id="659ee-134">Method Implementation Information</span></span>  
 <span data-ttu-id="659ee-135">Informace o implementaci metody často není známo v době, kdy je deklarována metoda.</span><span class="sxs-lookup"><span data-stu-id="659ee-135">Information about the method implementation is often not known at the time the method is declared.</span></span> <span data-ttu-id="659ee-136">Proto není nutné předat hodnoty v `ulCodeRVA` `dwImplFlags` parametry a `DefineMethod`při volání .</span><span class="sxs-lookup"><span data-stu-id="659ee-136">Therefore, you do not need to pass values in the `ulCodeRVA` and `dwImplFlags` parameters when calling `DefineMethod`.</span></span> <span data-ttu-id="659ee-137">Hodnoty mohou být dodány později prostřednictvím [IMetaDataEmit::SetMethodImplFlags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) nebo [IMetaDataEmit::SetRVA](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md), podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="659ee-137">The values can be supplied later through [IMetaDataEmit::SetMethodImplFlags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) or [IMetaDataEmit::SetRVA](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md), as appropriate.</span></span>  
  
 <span data-ttu-id="659ee-138">V některých situacích, jako je například vyvolání platformy (PInvoke) nebo `ulCodeRVA` com interop scénáře, tělo metody nebude zadána a by měla být nastavena na nulu.</span><span class="sxs-lookup"><span data-stu-id="659ee-138">In some situations, such as platform invocation (PInvoke) or COM interop scenarios, the method body will not be supplied, and `ulCodeRVA` should be set to zero.</span></span> <span data-ttu-id="659ee-139">V těchto situacích metoda by neměla být označena jako abstraktní, protože za běhu vyhledá implementaci.</span><span class="sxs-lookup"><span data-stu-id="659ee-139">In these situations, the method should not be tagged as abstract, because the runtime will locate the implementation.</span></span>  
  
## <a name="defining-a-method-for-pinvoke"></a><span data-ttu-id="659ee-140">Definování metody pro Vyvolání PInvoke</span><span class="sxs-lookup"><span data-stu-id="659ee-140">Defining a Method for PInvoke</span></span>  
 <span data-ttu-id="659ee-141">Pro každou nespravovanou funkci, která má být volána prostřednictvím PInvoke, musíte definovat spravovanou metodu, která představuje cílovou nespravovanou funkci.</span><span class="sxs-lookup"><span data-stu-id="659ee-141">For each unmanaged function to be called through PInvoke, you must define a managed method that represents the target unmanaged function.</span></span> <span data-ttu-id="659ee-142">Chcete-li definovat spravovanou metodu, použijte `DefineMethod` s některými parametry nastavenými na určité hodnoty v závislosti na způsobu, jakým se používá PInvoke:</span><span class="sxs-lookup"><span data-stu-id="659ee-142">To define the managed method, use `DefineMethod` with some of the parameters set to certain values, depending on the way in which PInvoke is used:</span></span>  
  
- <span data-ttu-id="659ee-143">True PInvoke - zahrnuje vyvolání externí nespravované metody, která je umístěna v nespravované dll.</span><span class="sxs-lookup"><span data-stu-id="659ee-143">True PInvoke - involves invocation of an external unmanaged method that resides in an unmanaged DLL.</span></span>  
  
- <span data-ttu-id="659ee-144">Místní PInvoke - zahrnuje vyvolání nativní nespravované metody, která je vložena do aktuálního spravovaného modulu.</span><span class="sxs-lookup"><span data-stu-id="659ee-144">Local PInvoke - involves invocation of a native unmanaged method that is embedded in the current managed module.</span></span>  
  
 <span data-ttu-id="659ee-145">Nastavení parametrů jsou uvedena v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="659ee-145">The parameter settings are given in the following table.</span></span>  
  
|<span data-ttu-id="659ee-146">Parametr</span><span class="sxs-lookup"><span data-stu-id="659ee-146">Parameter</span></span>|<span data-ttu-id="659ee-147">Hodnoty pro true PInvoke</span><span class="sxs-lookup"><span data-stu-id="659ee-147">Values for true PInvoke</span></span>|<span data-ttu-id="659ee-148">Hodnoty pro místní PInvoke</span><span class="sxs-lookup"><span data-stu-id="659ee-148">Values for local PInvoke</span></span>|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||<span data-ttu-id="659ee-149">Nastavit `mdStatic`; jasné `mdSynchronized` `mdAbstract`a .</span><span class="sxs-lookup"><span data-stu-id="659ee-149">Set `mdStatic`; clear `mdSynchronized` and `mdAbstract`.</span></span>|  
|`pvSigBlob`|<span data-ttu-id="659ee-150">Platný podpis metody CLR (COMMON Language runtime) s parametry, které jsou platnými spravovanými typy.</span><span class="sxs-lookup"><span data-stu-id="659ee-150">A valid common language runtime (CLR) method signature with parameters that are valid managed types.</span></span>|<span data-ttu-id="659ee-151">Platný podpis metody CLR s parametry, které jsou platné spravované typy.</span><span class="sxs-lookup"><span data-stu-id="659ee-151">A valid CLR method signature with parameters that are valid managed types.</span></span>|  
|`ulCodeRVA`||<span data-ttu-id="659ee-152">0</span><span class="sxs-lookup"><span data-stu-id="659ee-152">0</span></span>|  
|`dwImplFlags`|<span data-ttu-id="659ee-153">Nastavit `miCil` `miManaged`a .</span><span class="sxs-lookup"><span data-stu-id="659ee-153">Set `miCil` and `miManaged`.</span></span>|<span data-ttu-id="659ee-154">Nastavit `miNative` `miUnmanaged`a .</span><span class="sxs-lookup"><span data-stu-id="659ee-154">Set `miNative` and `miUnmanaged`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="659ee-155">Požadavky</span><span class="sxs-lookup"><span data-stu-id="659ee-155">Requirements</span></span>  
 <span data-ttu-id="659ee-156">**Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="659ee-156">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="659ee-157">**Záhlaví:** Kor.h.</span><span class="sxs-lookup"><span data-stu-id="659ee-157">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="659ee-158">**Knihovna:** Používá se jako prostředek v souboru MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="659ee-158">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="659ee-159">**Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="659ee-159">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="659ee-160">Viz také</span><span class="sxs-lookup"><span data-stu-id="659ee-160">See also</span></span>

- [<span data-ttu-id="659ee-161">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="659ee-161">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="659ee-162">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="659ee-162">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
