---
title: ICorProfilerCallback6::GetAssemblyReferences – metoda
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerCallback6.GetAssemblyReferences
api_location:
- mscorwks.dll
- corprof.idl
api_type:
- COM
ms.assetid: 8b391afb-d79f-41bd-94ce-43ce62c6b5fc
topic_type:
- apiref
ms.openlocfilehash: 5deacbff740ebb1dcc8cb8d1fb7e4eb0d4bdcc30
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84499217"
---
# <a name="icorprofilercallback6getassemblyreferences-method"></a><span data-ttu-id="6c187-102">ICorProfilerCallback6::GetAssemblyReferences – metoda</span><span class="sxs-lookup"><span data-stu-id="6c187-102">ICorProfilerCallback6::GetAssemblyReferences Method</span></span>
<span data-ttu-id="6c187-103">[Podporované v .NET Framework 4.5.2 a novějších verzích]</span><span class="sxs-lookup"><span data-stu-id="6c187-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="6c187-104">Upozorní profileru, že sestavení je ve fázi brzkého nasazování, pokud modul CLR provádí procházení zavřením odkazu na sestavení.</span><span class="sxs-lookup"><span data-stu-id="6c187-104">Notifies the profiler that an assembly is in a very early loading stage, when the common language runtime performs an assembly reference closure walk.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c187-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6c187-105">Syntax</span></span>  
  
```cpp
HRESULT GetAssemblyReferences(        [in, string] const WCHAR* wszAssemblyPath,  
        [in] ICorProfilerAssemblyReferenceProvider* pAsmRefProvider  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c187-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="6c187-106">Parameters</span></span>  
 `wszAssemblyPath`  
 <span data-ttu-id="6c187-107">pro Cesta a název sestavení, jehož metadata budou změněna.</span><span class="sxs-lookup"><span data-stu-id="6c187-107">[in] The path and name of the assembly whose metadata will be modified.</span></span>  
  
 `pAsmRefProvider`  
 <span data-ttu-id="6c187-108">pro Ukazatel na adresu rozhraní [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) , které určuje odkazy na sestavení, které se mají přidat.</span><span class="sxs-lookup"><span data-stu-id="6c187-108">[in] A pointer to the address of an [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) interface that specifies the assembly references to add.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6c187-109">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6c187-109">Return Value</span></span>  
 <span data-ttu-id="6c187-110">Návratové hodnoty z tohoto zpětného volání jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="6c187-110">Return values from this callback are ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6c187-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6c187-111">Remarks</span></span>  
 <span data-ttu-id="6c187-112">Toto zpětné volání je řízeno nastavením příznaku masky události [COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES](cor-prf-high-monitor-enumeration.md) při volání metody [Icorprofilercallback5 –:: SetEventMask2 –](icorprofilerinfo5-seteventmask2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="6c187-112">This callback is controlled by setting the [COR_PRF_HIGH_ADD_ASSEMBLY_REFERENCES](cor-prf-high-monitor-enumeration.md) event mask flag when calling the [ICorProfilerCallback5::SetEventMask2](icorprofilerinfo5-seteventmask2-method.md) method.</span></span> <span data-ttu-id="6c187-113">Pokud profiler registruje pro metodu zpětného volání [ICorProfilerCallback6:: GetAssemblyReferences –](icorprofilercallback6-getassemblyreferences-method.md) , modul runtime předá cestu a název sestavení, které mají být načteny, spolu s ukazatelem na objekt rozhraní [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) k této metodě.</span><span class="sxs-lookup"><span data-stu-id="6c187-113">If the profiler registers for the [ICorProfilerCallback6::GetAssemblyReferences](icorprofilercallback6-getassemblyreferences-method.md) callback method, the runtime passes the path and name of the assembly to be loaded, along with a pointer to an [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) interface object to that method.</span></span> <span data-ttu-id="6c187-114">Profiler pak může zavolat metodu [ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference –](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) s `COR_PRF_ASSEMBLY_REFERENCE_INFO` objektem pro každé cílové sestavení, které plánuje odkaz na odkaz ze sestavení zadaného ve `GetAssemblyReferences` zpětném volání.</span><span class="sxs-lookup"><span data-stu-id="6c187-114">The profiler can then call the [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) method with a `COR_PRF_ASSEMBLY_REFERENCE_INFO` object for each target assembly it plans to reference from the assembly specified in the `GetAssemblyReferences` callback.</span></span>  
  
 <span data-ttu-id="6c187-115">`GetAssemblyReferences`Zpětné volání použijte pouze v případě, že Profiler musí upravit metadata sestavení pro přidání odkazů na sestavení.</span><span class="sxs-lookup"><span data-stu-id="6c187-115">Use the `GetAssemblyReferences` callback only if the profiler has to modify an assembly's metadata to add assembly references.</span></span> <span data-ttu-id="6c187-116">(Ale Všimněte si, že skutečná úprava metadat sestavení se provádí v metodě zpětného volání [ICorProfilerCallback:: ModuleLoadFinished –](icorprofilercallback-moduleloadfinished-method.md).) Profiler by měl implementovat `GetAssemblyReferences` metodu zpětného volání pro informování modulu CLR (Common Language Runtime), který bude přidán odkaz na sestavení, když byl modul načten.</span><span class="sxs-lookup"><span data-stu-id="6c187-116">(But note that the actual modification of an assembly's metadata is done in the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md)callback method.) The profiler should implement the `GetAssemblyReferences` callback method to inform the common language runtime (CLR) that assembly references will be added when the module has been loaded.</span></span>  <span data-ttu-id="6c187-117">To pomáhá zajistit, že rozhodnutí o sdílení sestavení, která provedla CLR v rámci této úvodní fáze, zůstávají platná, i když Profiler plánuje změnit odkazy na sestavení metadat později.</span><span class="sxs-lookup"><span data-stu-id="6c187-117">This helps ensure that assembly sharing decisions made by the CLR during this early stage remain valid although the profiler plans to modify the metadata assembly references later.</span></span>  <span data-ttu-id="6c187-118">To se může vyhnout některým instancím, ve kterých změny metadat profileru způsobují `SECURITY_E_INCOMPATIBLE_SHARE` chybu.</span><span class="sxs-lookup"><span data-stu-id="6c187-118">This can avoid some instances in which profiler metadata modifications cause an `SECURITY_E_INCOMPATIBLE_SHARE` error.</span></span>  
  
 <span data-ttu-id="6c187-119">Profiler používá objekt [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) poskytnutý touto metodou pro přidání odkazů na sestavení do prohlížeč ukončení odkazu sestavení CLR.</span><span class="sxs-lookup"><span data-stu-id="6c187-119">The profiler uses the [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) object provided by this method to add assembly references to the CLR assembly reference closure walker.</span></span>  <span data-ttu-id="6c187-120">Objekt [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) by měl být použit pouze v rámci tohoto zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="6c187-120">The [ICorProfilerAssemblyReferenceProvider](icorprofilerassemblyreferenceprovider-interface.md) object should be used only from within this callback.</span></span> <span data-ttu-id="6c187-121">Volání metody [ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference –](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) z tohoto zpětného volání nemají za následek změněná metadata, ale pouze v rámci upraveného procházení odkazu na sestavení.</span><span class="sxs-lookup"><span data-stu-id="6c187-121">Calls to the [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) method from this callback don't result in modified metadata, but only in a modified assembly reference closure walk.</span></span> <span data-ttu-id="6c187-122">Profiler bude stále muset použít objekt [IMetaDataAssemblyEmit](../metadata/imetadataassemblyemit-interface.md) k explicitnímu přidání odkazů na sestavení z zpětného volání [ICorProfilerCallback:: ModuleLoadFinished –](icorprofilercallback-moduleloadfinished-method.md) pro odkazující sestavení, i když implementuje `GetAssemblyReferences` zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="6c187-122">The profiler will still have to use an [IMetaDataAssemblyEmit](../metadata/imetadataassemblyemit-interface.md) object to explicitly add assembly references from within the [ICorProfilerCallback::ModuleLoadFinished](icorprofilercallback-moduleloadfinished-method.md) callback for the referencing assembly, even if it implements the `GetAssemblyReferences` callback.</span></span>  
  
 <span data-ttu-id="6c187-123">Profiler by měl být přizpůsobený tak, aby přijímal duplicitní volání tohoto zpětného volání pro stejné sestavení a měl by odpovědět identicky pro každé takové duplicitní volání (provedením stejné sady volání [ICorProfilerAssemblyReferenceProvider:: AddAssemblyReference –](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) ).</span><span class="sxs-lookup"><span data-stu-id="6c187-123">The profiler should be prepared to receive duplicate calls to this callback for the same assembly, and should respond identically for each such duplicate call (by making the same set of [ICorProfilerAssemblyReferenceProvider::AddAssemblyReference](icorprofilerassemblyreferenceprovider-addassemblyreference-method.md) calls).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c187-124">Požadavky</span><span class="sxs-lookup"><span data-stu-id="6c187-124">Requirements</span></span>  
 <span data-ttu-id="6c187-125">**Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6c187-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6c187-126">**Hlavička:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="6c187-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="6c187-127">**Knihovna:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6c187-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6c187-128">**Verze .NET Framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6c187-128">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c187-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6c187-129">See also</span></span>

- [<span data-ttu-id="6c187-130">ICorProfilerCallback6 – rozhraní</span><span class="sxs-lookup"><span data-stu-id="6c187-130">ICorProfilerCallback6 Interface</span></span>](icorprofilercallback6-interface.md)
- [<span data-ttu-id="6c187-131">ModuleLoadFinished – metoda</span><span class="sxs-lookup"><span data-stu-id="6c187-131">ModuleLoadFinished Method</span></span>](icorprofilercallback-moduleloadfinished-method.md)
- [<span data-ttu-id="6c187-132">COR_PRF_ASSEMBLY_REFERENCE_INFO – struktura</span><span class="sxs-lookup"><span data-stu-id="6c187-132">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>](cor-prf-assembly-reference-info-structure.md)
- [<span data-ttu-id="6c187-133">Rozhraní ICorProfilerAssemblyReferenceProvider</span><span class="sxs-lookup"><span data-stu-id="6c187-133">ICorProfilerAssemblyReferenceProvider Interface</span></span>](icorprofilerassemblyreferenceprovider-interface.md)
