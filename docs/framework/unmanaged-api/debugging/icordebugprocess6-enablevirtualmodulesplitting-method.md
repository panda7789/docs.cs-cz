---
title: "ICorDebugProcess6::EnableVirtualModuleSplitting – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: e7733bd3-68da-47f9-82ef-477db5f2e32d
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 34a2c2571ba7f3560d861d0a5271cc3a955253a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugprocess6enablevirtualmodulesplitting-method"></a>ICorDebugProcess6::EnableVirtualModuleSplitting – metoda
Povolí nebo zakáže virtuální modulu rozdělení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnableVirtualModuleSplitting(  
   BOOL enableSplitting  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `enableSplitting`  
 `true`Chcete-li povolit modul virtuální rozdělení; `false` ji zakázat.  
  
## <a name="remarks"></a>Poznámky  
 Virtuální modulu rozdělení příčiny [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) moduly, které byly během sestavení společně sloučit zpracovat a prezentovat jako skupina samostatné moduly spíše než jeden modul velké rozpoznat. Tato funkce změní chování různých [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) metod popsaných níže.  
  
> [!NOTE]
>  Tato metoda je k dispozici s .NET Native jenom.  
  
 Tuto metodu lze volat a hodnotu `enableSplitting` lze kdykoli změnit. Nezpůsobí žádné stavové funkčních změn v [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) objekt, než změny chování metody uvedené v [virtuální modulu rozdělení a nespravované rozhraní API pro ladění](#APIs) oddíl v době, kdy jsou volány. Pomocí virtuální moduly způsobit snížení výkonu při volání těchto metod. Kromě toho významné do mezipaměti v paměti virtualizované metadat může být nutné správně implementovat [imetadataimport –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) rozhraní API a tyto mezipaměti může být zachována i po rozdělení virtuální modul byl vypnut.  
  
## <a name="terminology"></a>Terminologie  
 Při popisu rozdělení virtuální modul, se používají následující termíny:  
  
 kontejner moduly nebo kontejnerů  
 Agregační moduly.  
  
 dílčí, nebo moduly virtuální  
 Moduly najít v kontejneru.  
  
 regulární moduly  
 Moduly, které nebyly sloučit v čase vytvoření buildu. Jsou moduly kontejner ani dílčí moduly.  
  
 Kontejner moduly a dílčí moduly jsou reprezentované pomocí objektů ICorDebugModule rozhraní. Chování rozhraní se však mírně liší v každém případě jako \<x-ref sekci > část popisuje.  
  
## <a name="modules-and-assemblies"></a>Moduly a sestavení  
 Více modul sestavení nejsou podporovány pro sestavení slučování scénářů, takže není relace mezi modul a sestavení. Každý objekt ICorDebugModule, bez ohledu na to, jestli představuje modul kontejneru nebo dílčí modul, má odpovídající ICorDebugAssembly objektu. [Icordebugmodule::getassembly –](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md) metoda převede z modulu sestavení. Pro mapování v jiných směru, [icordebugassembly::enumeratemodules –](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-enumeratemodules-method.md) metoda zobrazí pouze 1 modulu. Protože sestavení a modul formuláři pár úzce párované v tomto případě podmínky sestavení a modul budou z velké části zaměnitelné.  
  
## <a name="behavioral-differences"></a>Rozdíly v chování  
 Kontejner modulů se na následující chování a vlastnosti:  
  
-   Jejich metadata pro všechny základní dílčí moduly je sloučen společně.  
  
-   Může být pozměněny jejich názvy typů.  
  
-   [Icordebugmodule::getName –](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md) metoda vrací cestu na modul na disku.  
  
-   [Icordebugmodule::getsize –](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md) metoda vrátí velikost této bitové kopie.  
  
-   Metoda ICorDebugAssembly3.EnumerateContainedAssemblies seznam dílčí modulů.  
  
-   Vrátí metodu ICorDebugAssembly3.GetContainerAssembly `S_FALSE`.  
  
 Dílčí modulů se na následující chování a vlastnosti:  
  
-   Mají omezenou sadu metadata, která odpovídá pouze původní sestavení, které se sloučit.  
  
-   Názvy metadat nejsou pozměněny.  
  
-   Tokeny metadat je nepravděpodobné, že aby byla sloučit v procesu sestavení tokenů v původní sestavení.  
  
-   [Icordebugmodule::getName –](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md) metoda vrátí název sestavení, ne cestu k souboru.  
  
-   [Icordebugmodule::getsize –](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md) metoda vrátí původní velikost obrázku nejsou sloučeny.  
  
-   Vrátí metodu ICorDebugModule3.EnumerateContainedAssemblies `S_FALSE`.  
  
-   Metoda ICorDebugAssembly3.GetContainerAssembly vrátí obsahující modulu.  
  
## <a name="interfaces-retrieved-from-modules"></a>Rozhraní načíst z modulů  
 Celou řadu rozhraní můžou vytvořit nebo načíst z modulů. Mezi ty patří:  
  
-   ICorDebugClass objekt, který je vrácen rutinou [icordebugmodule::getclassfromtoken –](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md) metoda.  
  
-   ICorDebugAssembly objekt, který je vrácen rutinou [icordebugmodule::getassembly –](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md) metoda.  
  
 Tyto objekty jsou vždy mezipaměti [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md), a budou mít stejnou identitu ukazatel bez ohledu na to, zda byly vytvořeny nebo získaných z dílčí modul nebo modul kontejneru. Dílčí modul poskytuje filtrované zobrazení tyto objekty uložené v mezipaměti není samostatné mezipaměti s vlastní kopie.  
  
<a name="APIs"></a>   
## <a name="virtual-module-splitting-and-the-unmanaged-debugging-apis"></a>Rozdělení virtuální modulu a nespravované rozhraní API pro ladění  
 Následující tabulka uvádí virtuálních modulu rozdělení ovlivňuje chování jiné metody v nespravované rozhraní API pro ladění.  
  
|Metoda|`enableSplitting` = `true`|`enableSplitting` = `false`|  
|------------|---------------------------------|----------------------------------|  
|[Icordebugfunction::getmodule –](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|Vrátí dílčí modul, který tato funkce byla původně definována v|Vrátí modul kontejneru, který tato funkce se sloučí.|  
|[Icordebugclass::getmodule –](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getmodule-method.md)|Vrátí dílčí modul, který tato třída byla původně definována v.|Vrátí kontejner modul, který tato třída se sloučí.|  
|ICorDebugModuleDebugEvent::GetModule|Vrátí kontejner modul, který byl načten. Dílčí moduly nejsou zadané události zatížení bez ohledu na toto nastavení.|Vrátí kontejner modul, který byl načten.|  
|[Icordebugappdomain::enumerateassemblies –](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|Vrátí seznam sestavení dílčí a regulární sestavení; žádné kontejneru sestavení jsou zahrnuty. **Poznámka:** Pokud žádné kontejneru sestavení chybí symboly, žádný z jeho dílčí sestavení bude možné provést výčet. Pokud žádné regulární sestavení chybí symboly, může nebo nemusí být ve výčtu.|Vrátí seznam sestavení kontejneru a regulární sestavení; žádné dílčí sestavení jsou zahrnuty. **Poznámka:** Pokud žádné regulární sestavení chybí symboly, může nebo nemusí být ve výčtu.|  
|[Icordebugcode::getcode –](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md) (k odkazování na kód IL pouze)|Vrátí IL, která by byla platná v bitové kopii před sloučení sestavení. Konkrétně tokenů metadat vložené správně bude odkaz TypeRef nebo MemberRef tokeny při typy odkazovaného nejsou definované v virtuální modul, který obsahuje IL. Tyto tokeny Odkaz TypeRef nebo MemberRef lze vyhledávat [imetadataimport –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) objektu pro objekt odpovídající ICorDebugModule virtuální.|Vrátí IL v bitové kopii po sloučení sestavení.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorDebugProcess6 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
