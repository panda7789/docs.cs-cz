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
ms.openlocfilehash: c46b075341742aac605537a08b762b3cf47ef35b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74431815"
---
# <a name="imetadataemitdefinemethod-method"></a><span data-ttu-id="89166-102">IMetaDataEmit::DefineMethod – metoda</span><span class="sxs-lookup"><span data-stu-id="89166-102">IMetaDataEmit::DefineMethod Method</span></span>
<span data-ttu-id="89166-103">Vytvoří definici metody nebo globální funkce se zadaným podpisem a vrátí do této definice metody token.</span><span class="sxs-lookup"><span data-stu-id="89166-103">Creates a definition for a method or global function with the specified signature, and returns a token to that method definition.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89166-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="89166-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="89166-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="89166-105">Parameters</span></span>  
 `td`  
 <span data-ttu-id="89166-106">pro Token `mdTypedef` nadřazené třídy nebo nadřazeného rozhraní metody</span><span class="sxs-lookup"><span data-stu-id="89166-106">[in] The `mdTypedef` token of the parent class or parent interface of the method.</span></span> <span data-ttu-id="89166-107">Pokud definujete globální funkci, nastavte `td` na `mdTokenNil`.</span><span class="sxs-lookup"><span data-stu-id="89166-107">Set `td` to `mdTokenNil`, if you are defining a global function.</span></span>  
  
 `szName`  
 <span data-ttu-id="89166-108">pro Název člena v kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="89166-108">[in] The member name in Unicode.</span></span>  
  
 `dwMethodFlags`  
 <span data-ttu-id="89166-109">pro Hodnota výčtu [CorMethodAttr –](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) , která určuje atributy metody nebo globální funkce.</span><span class="sxs-lookup"><span data-stu-id="89166-109">[in] A value of the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration that specifies the attributes of the method or global function.</span></span>  
  
 `pvSigBlob`  
 <span data-ttu-id="89166-110">pro Signatura metody.</span><span class="sxs-lookup"><span data-stu-id="89166-110">[in] The method signature.</span></span> <span data-ttu-id="89166-111">Signatura je trvalá jako dodaná.</span><span class="sxs-lookup"><span data-stu-id="89166-111">The signature is persisted as supplied.</span></span> <span data-ttu-id="89166-112">Pokud potřebujete zadat další informace pro všechny parametry, použijte metodu [IMetaDataEmit:: setparamprops –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md) .</span><span class="sxs-lookup"><span data-stu-id="89166-112">If you need to specify additional information for any parameters, use the [IMetaDataEmit::SetParamProps](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setparamprops-method.md) method.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="89166-113">pro Počet bajtů v `pvSigBlob`.</span><span class="sxs-lookup"><span data-stu-id="89166-113">[in] The count of bytes in `pvSigBlob`.</span></span>  
  
 `ulCodeRVA`  
 <span data-ttu-id="89166-114">pro Adresa kódu.</span><span class="sxs-lookup"><span data-stu-id="89166-114">[in] The address of the code.</span></span>  
  
 `dwImplFlags`  
 <span data-ttu-id="89166-115">pro Hodnota výčtu [CorMethodImpl –](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) , která určuje implementační funkce metody.</span><span class="sxs-lookup"><span data-stu-id="89166-115">[in] A value of the [CorMethodImpl](../../../../docs/framework/unmanaged-api/metadata/cormethodimpl-enumeration.md) enumeration that specifies the implementation features of the method.</span></span>  
  
 `pmd`  
 <span data-ttu-id="89166-116">mimo Token členu.</span><span class="sxs-lookup"><span data-stu-id="89166-116">[out] The member token.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="89166-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="89166-117">Remarks</span></span>  
 <span data-ttu-id="89166-118">Rozhraní API metadat zaručuje uchování metod ve stejném pořadí, ve kterém je volající vygeneruje pro danou ohraničující třídu nebo rozhraní, které jsou zadány v parametru `td`.</span><span class="sxs-lookup"><span data-stu-id="89166-118">The metadata API guarantees to persist methods in the same order as the caller emits them for a given enclosing class or interface, which is specified in the `td` parameter.</span></span>  
  
 <span data-ttu-id="89166-119">Další informace týkající se použití `DefineMethod` a konkrétního nastavení parametrů jsou uvedeny níže.</span><span class="sxs-lookup"><span data-stu-id="89166-119">Additional information regarding the use of `DefineMethod` and particular parameter settings is given below.</span></span>  
  
## <a name="slots-in-the-v-table"></a><span data-ttu-id="89166-120">Sloty v tabulce v</span><span class="sxs-lookup"><span data-stu-id="89166-120">Slots in the V-table</span></span>  
 <span data-ttu-id="89166-121">Modul runtime používá k nastavení slotů v tabulce definice metod.</span><span class="sxs-lookup"><span data-stu-id="89166-121">The runtime uses method definitions to set up v-table slots.</span></span> <span data-ttu-id="89166-122">V případě, kdy je třeba jeden nebo více slotů přeskočit, například pro zachování parity pomocí rozložení rozhraní modelu COM, je definována fiktivní metoda, která zabere slot nebo sloty v tabulce v. Nastavte `dwMethodFlags` na `mdRTSpecialName` hodnotu výčtu [CorMethodAttr –](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) a zadejte název jako:</span><span class="sxs-lookup"><span data-stu-id="89166-122">In the case where one or more slots need to be skipped, such as to preserve parity with a COM interface layout, a dummy method is defined to take up the slot or slots in the v-table; set the `dwMethodFlags` to the `mdRTSpecialName` value of the [CorMethodAttr](../../../../docs/framework/unmanaged-api/metadata/cormethodattr-enumeration.md) enumeration and specify the name as:</span></span>  
  
 <span data-ttu-id="89166-123">_VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*></span><span class="sxs-lookup"><span data-stu-id="89166-123">_VtblGap\<*SequenceNumber*>\<\_*CountOfSlots*></span></span>
  
 <span data-ttu-id="89166-124">kde *SequenceNumber* je pořadové číslo metody a *CountOfSlots* je počet slotů, které se mají přeskočit v tabulce v.</span><span class="sxs-lookup"><span data-stu-id="89166-124">where *SequenceNumber* is the sequence number of the method and *CountOfSlots* is the number of slots to skip in the v-table.</span></span> <span data-ttu-id="89166-125">Pokud je hodnota *CountOfSlots* vynechána, předpokládá se hodnota 1.</span><span class="sxs-lookup"><span data-stu-id="89166-125">If *CountOfSlots* is omitted, 1 is assumed.</span></span> <span data-ttu-id="89166-126">Tyto fiktivní metody nelze volat z spravovaného nebo nespravovaného kódu a jakékoli pokusy o jejich volání z spravovaného nebo nespravovaného kódu generují výjimku.</span><span class="sxs-lookup"><span data-stu-id="89166-126">These dummy methods are not callable from either managed or unmanaged code and any attempt to call them, from either managed or unmanaged code, generates an exception.</span></span> <span data-ttu-id="89166-127">Jediným účelem je zabírat místo v tabulce, kterou modul runtime generuje pro integraci modelu COM.</span><span class="sxs-lookup"><span data-stu-id="89166-127">Their only purpose is to take up space in the v-table that the runtime generates for COM integration.</span></span>  
  
## <a name="duplicate-methods"></a><span data-ttu-id="89166-128">Duplicitní metody</span><span class="sxs-lookup"><span data-stu-id="89166-128">Duplicate Methods</span></span>  
 <span data-ttu-id="89166-129">Neměli byste definovat duplicitní metody.</span><span class="sxs-lookup"><span data-stu-id="89166-129">You should not define duplicate methods.</span></span> <span data-ttu-id="89166-130">To znamená, že byste neměli volat `DefineMethod` s duplicitní sadou hodnot v parametrech `td`, `wzName`a `pvSig`.</span><span class="sxs-lookup"><span data-stu-id="89166-130">That is, you should not call `DefineMethod` with a duplicate set of values in the `td`, `wzName`, and `pvSig` parameters.</span></span> <span data-ttu-id="89166-131">(Tyto tři parametry společně definují jedinečnou metodu.).</span><span class="sxs-lookup"><span data-stu-id="89166-131">(These three parameters together uniquely define the method.).</span></span> <span data-ttu-id="89166-132">Můžete však použít duplicitní trojnásobný předpoklad, že pro jednu z definic metod nastavíte bit `mdPrivateScope` v parametru `dwMethodFlags`.</span><span class="sxs-lookup"><span data-stu-id="89166-132">However, you can use a duplicate triple provided that, for one of the method definitions, you set the `mdPrivateScope` bit in the `dwMethodFlags` parameter.</span></span> <span data-ttu-id="89166-133">(`mdPrivateScope` bit znamená, že kompilátor negeneruje odkaz na tuto definici metody.)</span><span class="sxs-lookup"><span data-stu-id="89166-133">(The `mdPrivateScope` bit means that the compiler will not emit a reference to this method definition.)</span></span>  
  
## <a name="method-implementation-information"></a><span data-ttu-id="89166-134">Informace o implementaci metody</span><span class="sxs-lookup"><span data-stu-id="89166-134">Method Implementation Information</span></span>  
 <span data-ttu-id="89166-135">Informace o implementaci metody často nejsou známy v době, kdy je metoda deklarována.</span><span class="sxs-lookup"><span data-stu-id="89166-135">Information about the method implementation is often not known at the time the method is declared.</span></span> <span data-ttu-id="89166-136">Proto není nutné předávat hodnoty do `ulCodeRVA` a `dwImplFlags` parametrů při volání `DefineMethod`.</span><span class="sxs-lookup"><span data-stu-id="89166-136">Therefore, you do not need to pass values in the `ulCodeRVA` and `dwImplFlags` parameters when calling `DefineMethod`.</span></span> <span data-ttu-id="89166-137">Hodnoty lze zadat později prostřednictvím [IMetaDataEmit:: SetMethodImplFlags –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) nebo [IMetaDataEmit:: setrva –](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md), podle potřeby.</span><span class="sxs-lookup"><span data-stu-id="89166-137">The values can be supplied later through [IMetaDataEmit::SetMethodImplFlags](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setmethodimplflags-method.md) or [IMetaDataEmit::SetRVA](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-setrva-method.md), as appropriate.</span></span>  
  
 <span data-ttu-id="89166-138">V některých situacích, například ve scénářích volání platformy (PInvoke) nebo zprostředkovateli komunikace s objekty COM, nebude tělo metody dodáno a `ulCodeRVA` by měl být nastaven na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="89166-138">In some situations, such as platform invocation (PInvoke) or COM interop scenarios, the method body will not be supplied, and `ulCodeRVA` should be set to zero.</span></span> <span data-ttu-id="89166-139">V těchto situacích by neměla být metoda označena jako abstraktní, protože modul runtime vyhledá implementaci.</span><span class="sxs-lookup"><span data-stu-id="89166-139">In these situations, the method should not be tagged as abstract, because the runtime will locate the implementation.</span></span>  
  
## <a name="defining-a-method-for-pinvoke"></a><span data-ttu-id="89166-140">Definování metody pro PInvoke</span><span class="sxs-lookup"><span data-stu-id="89166-140">Defining a Method for PInvoke</span></span>  
 <span data-ttu-id="89166-141">Pro každou nespravovanou funkci, která má být volána prostřednictvím PInvoke, je nutné definovat spravovanou metodu, která představuje cílovou nespravovanou funkci.</span><span class="sxs-lookup"><span data-stu-id="89166-141">For each unmanaged function to be called through PInvoke, you must define a managed method that represents the target unmanaged function.</span></span> <span data-ttu-id="89166-142">Pro definování spravované metody použijte `DefineMethod` s některými parametry nastavenými na určité hodnoty, v závislosti na způsobu použití PInvoke:</span><span class="sxs-lookup"><span data-stu-id="89166-142">To define the managed method, use `DefineMethod` with some of the parameters set to certain values, depending on the way in which PInvoke is used:</span></span>  
  
- <span data-ttu-id="89166-143">True PInvoke – zahrnuje vyvolání externí nespravované metody, která se nachází v nespravované knihovně DLL.</span><span class="sxs-lookup"><span data-stu-id="89166-143">True PInvoke - involves invocation of an external unmanaged method that resides in an unmanaged DLL.</span></span>  
  
- <span data-ttu-id="89166-144">Místní PInvoke – zahrnuje vyvolání nativní nespravované metody, která je vložena do aktuálního spravovaného modulu.</span><span class="sxs-lookup"><span data-stu-id="89166-144">Local PInvoke - involves invocation of a native unmanaged method that is embedded in the current managed module.</span></span>  
  
 <span data-ttu-id="89166-145">Nastavení parametru jsou uvedena v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="89166-145">The parameter settings are given in the following table.</span></span>  
  
|<span data-ttu-id="89166-146">Parametr</span><span class="sxs-lookup"><span data-stu-id="89166-146">Parameter</span></span>|<span data-ttu-id="89166-147">Hodnoty pro True PInvoke</span><span class="sxs-lookup"><span data-stu-id="89166-147">Values for true PInvoke</span></span>|<span data-ttu-id="89166-148">Hodnoty pro místní PInvoke</span><span class="sxs-lookup"><span data-stu-id="89166-148">Values for local PInvoke</span></span>|  
|---------------|-----------------------------|------------------------------|  
|`dwMethodFlags`||<span data-ttu-id="89166-149">Nastavit `mdStatic`; zrušte zaškrtnutí `mdSynchronized` a `mdAbstract`.</span><span class="sxs-lookup"><span data-stu-id="89166-149">Set `mdStatic`; clear `mdSynchronized` and `mdAbstract`.</span></span>|  
|`pvSigBlob`|<span data-ttu-id="89166-150">Platný podpis metody modulu CLR (Common Language Runtime) s parametry, které jsou platnými spravovanými typy.</span><span class="sxs-lookup"><span data-stu-id="89166-150">A valid common language runtime (CLR) method signature with parameters that are valid managed types.</span></span>|<span data-ttu-id="89166-151">Platná signatura metody CLR s parametry, které jsou platnými spravovanými typy.</span><span class="sxs-lookup"><span data-stu-id="89166-151">A valid CLR method signature with parameters that are valid managed types.</span></span>|  
|`ulCodeRVA`||<span data-ttu-id="89166-152">0</span><span class="sxs-lookup"><span data-stu-id="89166-152">0</span></span>|  
|`dwImplFlags`|<span data-ttu-id="89166-153">Nastavte `miCil` a `miManaged`.</span><span class="sxs-lookup"><span data-stu-id="89166-153">Set `miCil` and `miManaged`.</span></span>|<span data-ttu-id="89166-154">Nastavte `miNative` a `miUnmanaged`.</span><span class="sxs-lookup"><span data-stu-id="89166-154">Set `miNative` and `miUnmanaged`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="89166-155">Požadavky</span><span class="sxs-lookup"><span data-stu-id="89166-155">Requirements</span></span>  
 <span data-ttu-id="89166-156">**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89166-156">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89166-157">**Hlavička:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="89166-157">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="89166-158">**Knihovna:** Používá se jako prostředek v knihovně MSCorEE. dll.</span><span class="sxs-lookup"><span data-stu-id="89166-158">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="89166-159">**Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89166-159">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89166-160">Viz také:</span><span class="sxs-lookup"><span data-stu-id="89166-160">See also</span></span>

- [<span data-ttu-id="89166-161">IMetaDataEmit – rozhraní</span><span class="sxs-lookup"><span data-stu-id="89166-161">IMetaDataEmit Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md)
- [<span data-ttu-id="89166-162">IMetaDataEmit2 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="89166-162">IMetaDataEmit2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-interface.md)
