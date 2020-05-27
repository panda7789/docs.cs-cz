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
ms.openlocfilehash: 514f227e3c0c385f61090079d2f5214dac9b3924
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/27/2020
ms.locfileid: "84004527"
---
# <a name="imetadataemitdefinemethod-method"></a><span data-ttu-id="358cb-102">IMetaDataEmit::DefineMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="358cb-102">IMetaDataEmit::DefineMethod Method</span></span>
<span data-ttu-id="358cb-103">Vytvoří definici metody nebo globální funkce se zadaným podpisem a vrátí do této definice metody token.</span><span class="sxs-lookup"><span data-stu-id="358cb-103">Creates a definition for a method or global function with the specified signature, and returns a token to that method definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="358cb-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="358cb-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="358cb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="358cb-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="358cb-106">pro `mdTypedef`Token nadřazené třídy nebo nadřazeného rozhraní metody</span><span class="sxs-lookup"><span data-stu-id="358cb-106">[in] The `mdTypedef` token of the parent class or parent interface of the method.</span></span> <span data-ttu-id="358cb-107">Nastavte `td` na `mdTokenNil` , pokud definujete globální funkci.</span><span class="sxs-lookup"><span data-stu-id="358cb-107">Set `td` to `mdTokenNil`, if you are defining a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="358cb-108">pro Název člena v kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="358cb-108">[in] The member name in Unicode.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="358cb-109">pro Hodnota výčtu [CorMethodAttr –](cormethodattr-enumeration.md) , která určuje atributy metody nebo globální funkce.</span><span class="sxs-lookup"><span data-stu-id="358cb-109">[in] A value of the [CorMethodAttr](cormethodattr-enumeration.md) enumeration that specifies the attributes of the method or global function.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="358cb-110">pro Signatura metody.</span><span class="sxs-lookup"><span data-stu-id="358cb-110">[in] The method signature.</span></span> <span data-ttu-id="358cb-111">Signatura je trvalá jako dodaná.</span><span class="sxs-lookup"><span data-stu-id="358cb-111">The signature is persisted as supplied.</span></span> <span data-ttu-id="358cb-112">Pokud potřebujete zadat další informace pro všechny parametry, použijte metodu [IMetaDataEmit:: setparamprops –](imetadataemit-setparamprops-method.md) .</span><span class="sxs-lookup"><span data-stu-id="358cb-112">If you need to specify additional information for any parameters, use the [IMetaDataEmit::SetParamProps](imetadataemit-setparamprops-method.md) method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="358cb-113">pro Počet bajtů v `pvSigBlob` .</span><span class="sxs-lookup"><span data-stu-id="358cb-113">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="358cb-114">pro Adresa kódu.</span><span class="sxs-lookup"><span data-stu-id="358cb-114">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="358cb-115">pro Hodnota výčtu [CorMethodImpl –](cormethodimpl-enumeration.md) , která určuje implementační funkce metody.</span><span class="sxs-lookup"><span data-stu-id="358cb-115">[in] A value of the [CorMethodImpl](cormethodimpl-enumeration.md) enumeration that specifies the implementation features of the method.</span></span>  
  
 `pmd`  
 <span data-ttu-id="358cb-116">mimo Token členu.</span><span class="sxs-lookup"><span data-stu-id="358cb-116">[out] The member token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="358cb-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="358cb-117">Remarks</span></span>  
 <span data-ttu-id="358cb-118">Rozhraní API metadat zaručuje uchování metod ve stejném pořadí, ve kterém je volající vygeneruje pro danou ohraničující třídu nebo rozhraní, které jsou zadány v `td` parametru.</span><span class="sxs-lookup"><span data-stu-id="358cb-118">The metadata API guarantees to persist methods in the same order as the caller emits them for a given enclosing class or interface, which is specified in the `td` parameter.</span></span>  
  
 <span data-ttu-id="358cb-119">Další informace týkající se použití `DefineMethod` a konkrétního nastavení parametrů jsou uvedeny níže.</span><span class="sxs-lookup"><span data-stu-id="358cb-119">Additional information regarding the use of `DefineMethod` and particular parameter settings is given below.</span></span>  
  
## <a name="slots-in-the-v-table"></a><span data-ttu-id="358cb-120">Sloty v tabulce v</span><span class="sxs-lookup"><span data-stu-id="358cb-120">Slots in the V-table</span></span>  
 <span data-ttu-id="358cb-121">Modul runtime používá k nastavení slotů v tabulce definice metod.</span><span class="sxs-lookup"><span data-stu-id="358cb-121">The runtime uses method definitions to set up v-table slots.</span></span> <span data-ttu-id="358cb-122">V případě, kdy je třeba jeden nebo více slotů přeskočit, například pro zachování parity pomocí rozložení rozhraní modelu COM, je definována fiktivní metoda, která zabere slot nebo sloty v tabulce v. Nastavte na `dwMethodFlags` `mdRTSpecialName` hodnotu výčtu [CorMethodAttr –](cormethodattr-enumeration.md) a zadejte název jako:</span><span class="sxs-lookup"><span data-stu-id="358cb-122">In the case where one or more slots need to be skipped, such as to preserve parity with a COM interface layout, a dummy method is defined to take up the slot or slots in the v-table; set the `dwMethodFlags` to the `mdRTSpecialName` value of the [CorMethodAttr](cormethodattr-enumeration.md) enumeration and specify the name as:</span></span>  
  
 <span data-ttu-id="358cb-123">_VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*></span><span class="sxs-lookup"><span data-stu-id="358cb-123">_VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*></span></span>
  
 <span data-ttu-id="358cb-124">kde *SequenceNumber* je pořadové číslo metody a *CountOfSlots* je počet slotů, které se mají přeskočit v tabulce v.</span><span class="sxs-lookup"><span data-stu-id="358cb-124">where *SequenceNumber* is the sequence number of the method and *CountOfSlots* is the number of slots to skip in the v-table.</span></span> <span data-ttu-id="358cb-125">Pokud je hodnota *CountOfSlots* vynechána, předpokládá se hodnota 1.</span><span class="sxs-lookup"><span data-stu-id="358cb-125">If *CountOfSlots* is omitted, 1 is assumed.</span></span> <span data-ttu-id="358cb-126">Tyto fiktivní metody nelze volat z spravovaného nebo nespravovaného kódu a jakékoli pokusy o jejich volání z spravovaného nebo nespravovaného kódu generují výjimku.</span><span class="sxs-lookup"><span data-stu-id="358cb-126">These dummy methods are not callable from either managed or unmanaged code and any attempt to call them, from either managed or unmanaged code, generates an exception.</span></span> <span data-ttu-id="358cb-127">Jediným účelem je zabírat místo v tabulce, kterou modul runtime generuje pro integraci modelu COM.</span><span class="sxs-lookup"><span data-stu-id="358cb-127">Their only purpose is to take up space in the v-table that the runtime generates for COM integration.</span></span>  
  
## <a name="duplicate-methods"></a><span data-ttu-id="358cb-128">Duplicitní metody</span><span class="sxs-lookup"><span data-stu-id="358cb-128">Duplicate Methods</span></span>  
 <span data-ttu-id="358cb-129">Neměli byste definovat duplicitní metody.</span><span class="sxs-lookup"><span data-stu-id="358cb-129">You should not define duplicate methods.</span></span> <span data-ttu-id="358cb-130">To znamená, že byste neměli volat `DefineMethod` s duplicitní sadou hodnot v `td` `wzName` `pvSig` parametrech, a.</span><span class="sxs-lookup"><span data-stu-id="358cb-130">That is, you should not call `DefineMethod` with a duplicate set of values in the `td`, `wzName`, and `pvSig` parameters.</span></span> <span data-ttu-id="358cb-131">(Tyto tři parametry společně definují jedinečnou metodu.).</span><span class="sxs-lookup"><span data-stu-id="358cb-131">(These three parameters together uniquely define the method.).</span></span> <span data-ttu-id="358cb-132">Můžete však použít duplicitní trojnásobný předpoklad, že pro jednu z definic metod nastavíte `mdPrivateScope` bit v `dwMethodFlags` parametru.</span><span class="sxs-lookup"><span data-stu-id="358cb-132">However, you can use a duplicate triple provided that, for one of the method definitions, you set the `mdPrivateScope` bit in the `dwMethodFlags` parameter.</span></span> <span data-ttu-id="358cb-133">( `mdPrivateScope` Bit znamená, že kompilátor negeneruje odkaz na tuto definici metody.)</span><span class="sxs-lookup"><span data-stu-id="358cb-133">(The `mdPrivateScope` bit means that the compiler will not emit a reference to this method definition.)</span></span>  
  
## <a name="method-implementation-information"></a><span data-ttu-id="358cb-134">Informace o implementaci metody</span><span class="sxs-lookup"><span data-stu-id="358cb-134">Method Implementation Information</span></span>  
 <span data-ttu-id="358cb-135">Informace o implementaci metody často nejsou známy v době, kdy je metoda deklarována.</span><span class="sxs-lookup"><span data-stu-id="358cb-135">Information about the method implementation is often not known at the time the method is declared.</span></span> <span data-ttu-id="358cb-136">Proto není nutné předávat hodnoty v `ulCodeRVA` `dwImplFlags` parametrech a při volání `DefineMethod` .</span><span class="sxs-lookup"><span data-stu-id="358cb-136">Therefore, you do not need to pass values in the `ulCodeRVA` and `dwImplFlags` parameters when calling `DefineMethod`.</span></span> <span data-ttu-id="358cb-137">Hodnoty lze zadat později prostřednictvím [IMetaDataEmit:: SetMethodImplFlags –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) nebo [IMetaDataEmit:: setrva –](imetadataemit-setrva-method.md), podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="358cb-137">The values can be supplied later through [IMetaDataEmit::SetMethodImplFlags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) or [IMetaDataEmit::SetRVA](imetadataemit-setrva-method.md), as appropriate.</span></span>  
  
 <span data-ttu-id="358cb-138">V některých situacích, například ve scénářích volání platformy (PInvoke) nebo v případě komunikace s objekty COM, nebude tělo metody dodáno a `ulCodeRVA` mělo by být nastaveno na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="358cb-138">In some situations, such as platform invocation (PInvoke) or COM interop scenarios, the method body will not be supplied, and `ulCodeRVA` should be set to zero.</span></span> <span data-ttu-id="358cb-139">V těchto situacích by neměla být metoda označena jako abstraktní, protože modul runtime vyhledá implementaci.</span><span class="sxs-lookup"><span data-stu-id="358cb-139">In these situations, the method should not be tagged as abstract, because the runtime will locate the implementation.</span></span>  
  
## <a name="defining-a-method-for-pinvoke"></a><span data-ttu-id="358cb-140">Definování metody pro PInvoke</span><span class="sxs-lookup"><span data-stu-id="358cb-140">Defining a Method for PInvoke</span></span>  
 <span data-ttu-id="358cb-141">Pro každou nespravovanou funkci, která má být volána prostřednictvím PInvoke, je nutné definovat spravovanou metodu, která představuje cílovou nespravovanou funkci.</span><span class="sxs-lookup"><span data-stu-id="358cb-141">For each unmanaged function to be called through PInvoke, you must define a managed method that represents the target unmanaged function.</span></span> <span data-ttu-id="358cb-142">Pro definování spravované metody použijte `DefineMethod` s některými parametry nastavenými na určité hodnoty, v závislosti na způsobu použití PInvoke:</span><span class="sxs-lookup"><span data-stu-id="358cb-142">To define the managed method, use `DefineMethod` with some of the parameters set to certain values, depending on the way in which PInvoke is used:</span></span>  
  
- <span data-ttu-id="358cb-143">True PInvoke – zahrnuje vyvolání externí nespravované metody, která se nachází v nespravované knihovně DLL.</span><span class="sxs-lookup"><span data-stu-id="358cb-143">True PInvoke - involves invocation of an external unmanaged method that resides in an unmanaged DLL.</span></span>  
  
- <span data-ttu-id="358cb-144">Místní PInvoke – zahrnuje vyvolání nativní nespravované metody, která je vložena do aktuálního spravovaného modulu.</span><span class="sxs-lookup"><span data-stu-id="358cb-144">Local PInvoke - involves invocation of a native unmanaged method that is embedded in the current managed module.</span></span>  
  
 <span data-ttu-id="358cb-145">Nastavení parametru jsou uvedena v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="358cb-145">The parameter settings are given in the following table.</span></span>  
  
|<span data-ttu-id="358cb-146">Parametr</span><span class="sxs-lookup"><span data-stu-id="358cb-146">Parameter</span></span>|<span data-ttu-id="358cb-147">Hodnoty pro True PInvoke</span><span class="sxs-lookup"><span data-stu-id="358cb-147">Values for true PInvoke</span></span>|<span data-ttu-id="358cb-148">Hodnoty pro místní PInvoke</span><span class="sxs-lookup"><span data-stu-id="358cb-148">Values for local PInvoke</span></span>|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||<span data-ttu-id="358cb-149">Set `mdStatic` ; clear `mdSynchronized` a `mdAbstract` .</span><span class="sxs-lookup"><span data-stu-id="358cb-149">Set `mdStatic`; clear `mdSynchronized` and `mdAbstract`.</span></span>|  
|`pvSigBlob`|<span data-ttu-id="358cb-150">Platný podpis metody modulu CLR (Common Language Runtime) s parametry, které jsou platnými spravovanými typy.</span><span class="sxs-lookup"><span data-stu-id="358cb-150">A valid common language runtime (CLR) method signature with parameters that are valid managed types.</span></span>|<span data-ttu-id="358cb-151">Platná signatura metody CLR s parametry, které jsou platnými spravovanými typy.</span><span class="sxs-lookup"><span data-stu-id="358cb-151">A valid CLR method signature with parameters that are valid managed types.</span></span>|  
|`ulCodeRVA`||<span data-ttu-id="358cb-152">0</span><span class="sxs-lookup"><span data-stu-id="358cb-152">0</span></span>|  
|`dwImplFlags`|<span data-ttu-id="358cb-153">Nastavte `miCil` a `miManaged` .</span><span class="sxs-lookup"><span data-stu-id="358cb-153">Set `miCil` and `miManaged`.</span></span>|<span data-ttu-id="358cb-154">Nastavte `miNative` a `miUnmanaged` .</span><span class="sxs-lookup"><span data-stu-id="358cb-154">Set `miNative` and `miUnmanaged`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="358cb-155">Požadavky</span><span class="sxs-lookup"><span data-stu-id="358cb-155">Requirements</span></span>  
 <span data-ttu-id="358cb-156">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="358cb-156">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="358cb-157">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="358cb-157">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="358cb-158">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="358cb-158">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="358cb-159">**Verze .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="358cb-159">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="358cb-160">Viz také</span><span class="sxs-lookup"><span data-stu-id="358cb-160">See also</span></span>

- [<span data-ttu-id="358cb-161">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="358cb-161">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="358cb-162">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="358cb-162">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
