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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a67e8ce19a2acf5b4ee1d114858e00d93cb183b2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59115580"
---
# <a name="imetadataemitdefinemethod-method"></a><span data-ttu-id="7f90c-102">IMetaDataEmit::DefineMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="7f90c-102">IMetaDataEmit::DefineMethod Method</span></span>
<span data-ttu-id="7f90c-103">Vytvoří definici pro metody nebo globální funkce se zadaným podpisem a vrátí token k definici této metody.</span><span class="sxs-lookup"><span data-stu-id="7f90c-103">Creates a definition for a method or global function with the specified signature, and returns a token to that method definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f90c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7f90c-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="7f90c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7f90c-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="7f90c-106">[in] `mdTypedef` Token nadřazené třídu nebo rozhraní nadřazené metody.</span><span class="sxs-lookup"><span data-stu-id="7f90c-106">[in] The `mdTypedef` token of the parent class or parent interface of the method.</span></span> <span data-ttu-id="7f90c-107">Nastavte `td` k `mdTokenNil`, pokud definujete globální funkce.</span><span class="sxs-lookup"><span data-stu-id="7f90c-107">Set `td` to `mdTokenNil`, if you are defining a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="7f90c-108">[in] Název člena v kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="7f90c-108">[in] The member name in Unicode.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="7f90c-109">[in] Hodnota [cormethodattr –](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) výčet, který určuje atributy metody nebo globální funkce.</span><span class="sxs-lookup"><span data-stu-id="7f90c-109">[in] A value of the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration that specifies the attributes of the method or global function.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="7f90c-110">[in] Podpis metody.</span><span class="sxs-lookup"><span data-stu-id="7f90c-110">[in] The method signature.</span></span> <span data-ttu-id="7f90c-111">Podpis se ukládají jako dodaného.</span><span class="sxs-lookup"><span data-stu-id="7f90c-111">The signature is persisted as supplied.</span></span> <span data-ttu-id="7f90c-112">Pokud je třeba zadat další informace o všech parametrů, použijte [imetadataemit::setparamprops –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="7f90c-112">If you need to specify additional information for any parameters, use the [IMetaDataEmit::SetParamProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md) method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="7f90c-113">[in] Počet bajtů v `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="7f90c-113">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="7f90c-114">[in] Adresa kód.</span><span class="sxs-lookup"><span data-stu-id="7f90c-114">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="7f90c-115">[in] Hodnota [cormethodimpl –](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) výčet, který určuje funkce implementace metody.</span><span class="sxs-lookup"><span data-stu-id="7f90c-115">[in] A value of the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration that specifies the implementation features of the method.</span></span>  
  
 `pmd`  
 <span data-ttu-id="7f90c-116">[out] Token členu.</span><span class="sxs-lookup"><span data-stu-id="7f90c-116">[out] The member token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f90c-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7f90c-117">Remarks</span></span>  
 <span data-ttu-id="7f90c-118">Zachování metody ve stejném pořadí jako volající vydává je pro danou ohraničující třídu nebo rozhraní, která je určena v zaručuje metadat rozhraní API `td` parametru.</span><span class="sxs-lookup"><span data-stu-id="7f90c-118">The metadata API guarantees to persist methods in the same order as the caller emits them for a given enclosing class or interface, which is specified in the `td` parameter.</span></span>  
  
 <span data-ttu-id="7f90c-119">Další informace týkající se použití `DefineMethod` a konkrétních parametrů nastavení je uvedena níže.</span><span class="sxs-lookup"><span data-stu-id="7f90c-119">Additional information regarding the use of `DefineMethod` and particular parameter settings is given below.</span></span>  
  
## <a name="slots-in-the-v-table"></a><span data-ttu-id="7f90c-120">Sloty v tabulce</span><span class="sxs-lookup"><span data-stu-id="7f90c-120">Slots in the V-table</span></span>  
 <span data-ttu-id="7f90c-121">Modul runtime používá k vytvoření tabulky v sloty definice metod.</span><span class="sxs-lookup"><span data-stu-id="7f90c-121">The runtime uses method definitions to set up v-table slots.</span></span> <span data-ttu-id="7f90c-122">V případě, kdy jeden nebo více slotů musí být bylo přeskočeno, například tak, aby byly parita s rozložením rozhraní modelu COM, fiktivní metoda je definován tak, aby zabíraly slotu nebo sloty v tabulce. Nastavte `dwMethodFlags` k `mdRTSpecialName` hodnotu [cormethodattr –](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) výčet a zadejte název:</span><span class="sxs-lookup"><span data-stu-id="7f90c-122">In the case where one or more slots need to be skipped, such as to preserve parity with a COM interface layout, a dummy method is defined to take up the slot or slots in the v-table; set the `dwMethodFlags` to the `mdRTSpecialName` value of the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration and specify the name as:</span></span>  
  
 <span data-ttu-id="7f90c-123">_VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*></span><span class="sxs-lookup"><span data-stu-id="7f90c-123">_VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*></span></span>
  
 <span data-ttu-id="7f90c-124">kde *SequenceNumber* má pořadové číslo metody a *CountOfSlots* je počtu slotů pro přeskočení v tabulce.</span><span class="sxs-lookup"><span data-stu-id="7f90c-124">where *SequenceNumber* is the sequence number of the method and *CountOfSlots* is the number of slots to skip in the v-table.</span></span> <span data-ttu-id="7f90c-125">Pokud *CountOfSlots* je vynechána, předpokládá se 1.</span><span class="sxs-lookup"><span data-stu-id="7f90c-125">If *CountOfSlots* is omitted, 1 is assumed.</span></span> <span data-ttu-id="7f90c-126">Tyto metody fiktivní nejsou volány z spravovaného i nespravovaného kódu a jakýkoliv pokus o volání, od spravovaných nebo nespravovaných kódu, vygeneruje výjimku.</span><span class="sxs-lookup"><span data-stu-id="7f90c-126">These dummy methods are not callable from either managed or unmanaged code and any attempt to call them, from either managed or unmanaged code, generates an exception.</span></span> <span data-ttu-id="7f90c-127">Jejich jediným účelem je tak, aby zabíraly místo v tabulce, která generuje modul runtime integrace modelu COM.</span><span class="sxs-lookup"><span data-stu-id="7f90c-127">Their only purpose is to take up space in the v-table that the runtime generates for COM integration.</span></span>  
  
## <a name="duplicate-methods"></a><span data-ttu-id="7f90c-128">Duplicitní metody</span><span class="sxs-lookup"><span data-stu-id="7f90c-128">Duplicate Methods</span></span>  
 <span data-ttu-id="7f90c-129">Duplicitní metody by neměly definovat.</span><span class="sxs-lookup"><span data-stu-id="7f90c-129">You should not define duplicate methods.</span></span> <span data-ttu-id="7f90c-130">To znamená, že byste neměli volat `DefineMethod` duplicitní sadu hodnot v `td`, `wzName`, a `pvSig` parametry.</span><span class="sxs-lookup"><span data-stu-id="7f90c-130">That is, you should not call `DefineMethod` with a duplicate set of values in the `td`, `wzName`, and `pvSig` parameters.</span></span> <span data-ttu-id="7f90c-131">(Tyto tři parametry dohromady jedinečně definici této metody.).</span><span class="sxs-lookup"><span data-stu-id="7f90c-131">(These three parameters together uniquely define the method.).</span></span> <span data-ttu-id="7f90c-132">Ale můžete použít duplicitní triple za předpokladu, že pro jednu z definice metod, můžete nastavit `mdPrivateScope` bit ve `dwMethodFlags` parametru.</span><span class="sxs-lookup"><span data-stu-id="7f90c-132">However, you can use a duplicate triple provided that, for one of the method definitions, you set the `mdPrivateScope` bit in the `dwMethodFlags` parameter.</span></span> <span data-ttu-id="7f90c-133">( `mdPrivateScope` Bit znamená, že kompilátor nebude generovat odkaz na definici této metody.)</span><span class="sxs-lookup"><span data-stu-id="7f90c-133">(The `mdPrivateScope` bit means that the compiler will not emit a reference to this method definition.)</span></span>  
  
## <a name="method-implementation-information"></a><span data-ttu-id="7f90c-134">Informace o implementaci – metoda</span><span class="sxs-lookup"><span data-stu-id="7f90c-134">Method Implementation Information</span></span>  
 <span data-ttu-id="7f90c-135">Informace o implementaci metody se často není známý v době, kdy je deklarována jako metodu.</span><span class="sxs-lookup"><span data-stu-id="7f90c-135">Information about the method implementation is often not known at the time the method is declared.</span></span> <span data-ttu-id="7f90c-136">Proto není potřeba předat hodnoty `ulCodeRVA` a `dwImplFlags` parametrů při volání metody `DefineMethod`.</span><span class="sxs-lookup"><span data-stu-id="7f90c-136">Therefore, you do not need to pass values in the `ulCodeRVA` and `dwImplFlags` parameters when calling `DefineMethod`.</span></span> <span data-ttu-id="7f90c-137">Hodnoty mohou být poskytnuty později prostřednictvím [imetadataemit::setmethodimplflags –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) nebo [imetadataemit::setrva –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md)podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="7f90c-137">The values can be supplied later through [IMetaDataEmit::SetMethodImplFlags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) or [IMetaDataEmit::SetRVA](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md), as appropriate.</span></span>  
  
 <span data-ttu-id="7f90c-138">V některých situacích, jako je například vyvolání platformy (PInvoke) nebo COM interop scénáře, nebude zadán tělo metody, a `ulCodeRVA` musí být nastavena na nulu.</span><span class="sxs-lookup"><span data-stu-id="7f90c-138">In some situations, such as platform invocation (PInvoke) or COM interop scenarios, the method body will not be supplied, and `ulCodeRVA` should be set to zero.</span></span> <span data-ttu-id="7f90c-139">V těchto situacích by neměl být označené metodu jako abstraktní, vzhledem k tomu, že modul runtime vyhledá implementace.</span><span class="sxs-lookup"><span data-stu-id="7f90c-139">In these situations, the method should not be tagged as abstract, because the runtime will locate the implementation.</span></span>  
  
## <a name="defining-a-method-for-pinvoke"></a><span data-ttu-id="7f90c-140">Definování metody pro volání PInvoke</span><span class="sxs-lookup"><span data-stu-id="7f90c-140">Defining a Method for PInvoke</span></span>  
 <span data-ttu-id="7f90c-141">Pro každou nespravovanou funkci volané prostřednictvím PInvoke je nutné definovat spravované metody, která představuje cíl nespravované funkci.</span><span class="sxs-lookup"><span data-stu-id="7f90c-141">For each unmanaged function to be called through PInvoke, you must define a managed method that represents the target unmanaged function.</span></span> <span data-ttu-id="7f90c-142">Chcete-li definovat spravované metody, použijte `DefineMethod` pomocí některé z parametrů nastavit určité hodnoty v závislosti na způsobu, ve kterém se používá PInvoke:</span><span class="sxs-lookup"><span data-stu-id="7f90c-142">To define the managed method, use `DefineMethod` with some of the parameters set to certain values, depending on the way in which PInvoke is used:</span></span>  
  
-   <span data-ttu-id="7f90c-143">True PInvoke – zahrnuje volání externí nespravované metody, které se nacházejí v nespravovaná knihovna DLL.</span><span class="sxs-lookup"><span data-stu-id="7f90c-143">True PInvoke - involves invocation of an external unmanaged method that resides in an unmanaged DLL.</span></span>  
  
-   <span data-ttu-id="7f90c-144">Místní PInvoke – zahrnuje volání nativního nespravované metody, které jsou součástí aktuální spravovaný modul.</span><span class="sxs-lookup"><span data-stu-id="7f90c-144">Local PInvoke - involves invocation of a native unmanaged method that is embedded in the current managed module.</span></span>  
  
 <span data-ttu-id="7f90c-145">Nastavení parametrů jsou uvedeny v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="7f90c-145">The parameter settings are given in the following table.</span></span>  
  
|<span data-ttu-id="7f90c-146">Parametr</span><span class="sxs-lookup"><span data-stu-id="7f90c-146">Parameter</span></span>|<span data-ttu-id="7f90c-147">Hodnoty true PInvoke</span><span class="sxs-lookup"><span data-stu-id="7f90c-147">Values for true PInvoke</span></span>|<span data-ttu-id="7f90c-148">Hodnoty pro místní PInvoke</span><span class="sxs-lookup"><span data-stu-id="7f90c-148">Values for local PInvoke</span></span>|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||<span data-ttu-id="7f90c-149">Nastavte `mdStatic`; vymazat `mdSynchronized` a `mdAbstract`.</span><span class="sxs-lookup"><span data-stu-id="7f90c-149">Set `mdStatic`; clear `mdSynchronized` and `mdAbstract`.</span></span>|  
|`pvSigBlob`|<span data-ttu-id="7f90c-150">Platný common language runtime (CLR) podpis metody s parametry, které jsou platné spravovaných typů.</span><span class="sxs-lookup"><span data-stu-id="7f90c-150">A valid common language runtime (CLR) method signature with parameters that are valid managed types.</span></span>|<span data-ttu-id="7f90c-151">Neplatný podpis metody CLR s parametry, které jsou platné spravovaných typů.</span><span class="sxs-lookup"><span data-stu-id="7f90c-151">A valid CLR method signature with parameters that are valid managed types.</span></span>|  
|`ulCodeRVA`||<span data-ttu-id="7f90c-152">0</span><span class="sxs-lookup"><span data-stu-id="7f90c-152">0</span></span>|  
|`dwImplFlags`|<span data-ttu-id="7f90c-153">Nastavte `miCil` a `miManaged`.</span><span class="sxs-lookup"><span data-stu-id="7f90c-153">Set `miCil` and `miManaged`.</span></span>|<span data-ttu-id="7f90c-154">Nastavte `miNative` a `miUnmanaged`.</span><span class="sxs-lookup"><span data-stu-id="7f90c-154">Set `miNative` and `miUnmanaged`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7f90c-155">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7f90c-155">Requirements</span></span>  
 <span data-ttu-id="7f90c-156">**Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f90c-156">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f90c-157">**Záhlaví:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="7f90c-157">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7f90c-158">**Knihovna:** Použít jako prostředek v MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7f90c-158">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7f90c-159">**Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f90c-159">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f90c-160">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7f90c-160">See also</span></span>

- [<span data-ttu-id="7f90c-161">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7f90c-161">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="7f90c-162">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="7f90c-162">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
