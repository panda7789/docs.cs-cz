---
title: ICorDebugProcess6::EnableVirtualModuleSplitting – metoda
ms.date: 03/30/2017
ms.assetid: e7733bd3-68da-47f9-82ef-477db5f2e32d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f0f4a1de47670c59f2794feecd0be301a68b8724
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64613799"
---
# <a name="icordebugprocess6enablevirtualmodulesplitting-method"></a>ICorDebugProcess6::EnableVirtualModuleSplitting – metoda
Povolí nebo zakáže virtuální modulu rozdělení.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnableVirtualModuleSplitting(  
   BOOL enableSplitting  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `enableSplitting`  
 `true` Povolit virtuální modulu rozdělení; `false` ho zakážete.  
  
## <a name="remarks"></a>Poznámky  
 Rozdělení způsobí, že virtuální modulu [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) rozpoznat moduly, které byly sloučeny během sestavení zpracovávat a prezentovat jako skupina samostatných modulů spíše než jeden modul velké. Tím se změní chování různých [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) metod popsaných níže.  
  
> [!NOTE]
>  Tato metoda je pouze k dispozici s .NET Native.  
  
 Tuto metodu lze volat a hodnota `enableSplitting` můžete kdykoli změnit. Nezpůsobí žádné stavové funkční změny v [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) objektu, než se změna chování metody uvedené v [virtuální modulu rozdělení a nespravované ladění rozhraní API](#APIs) část v době, kdy jsou volány. Používání virtuální modulů mít za následek snížení výkonu při volání těchto metod. Kromě toho, ukládání v mezipaměti významné virtualizované metadat může být vyžadováno pro správnou implementaci [imetadataimport –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) rozhraní API a mezipamětí nemusí být zachovány i po rozdělení virtuální modul byl vypnut.  
  
## <a name="terminology"></a>Terminologie  
 Při popisu rozdělení virtuální modulu se používají následující termíny:  
  
 kontejner moduly nebo kontejnery  
 Agregační moduly.  
  
 dílčí moduly nebo virtuální moduly  
 Moduly v kontejneru.  
  
 pravidelné moduly  
 Moduly, které nebyly sloučeny v okamžiku sestavení. Jsou moduly kontejneru ani dílčích modulů.  
  
 Kontejner moduly a dílčích modulů jsou reprezentované pomocí objektů icordebugmodule – rozhraní. Chování rozhraní je ale mírně liší v každém případě jako \<x odkaz na oddíl > část popisuje.  
  
## <a name="modules-and-assemblies"></a>Moduly a sestavení  
 Vícemodulová sestavení nejsou podporována pro sestavení sloučení scénářů, takže vztah 1: 1 mezi modulu a sestavení. Každý objekt ICorDebugModule, bez ohledu na to, zda představuje kontejner modulu nebo dílčí modul, má odpovídající objekt ICorDebugAssembly. [Icordebugmodule::getassembly –](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md) metoda převede z modulu na sestavení. K mapování v opačném směru, [icordebugassembly::enumeratemodules –](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-enumeratemodules-method.md) metoda výčet pouze 1 modulu. Protože sestavení a modul formuláře v tomto případě dvojici těsně vázaných, podmínky sestavení a modul stát zaměnitelná.  
  
## <a name="behavioral-differences"></a>Behaviorální rozdíly  
 Kontejner moduly mají následující charakteristiky a chování:  
  
- Jejich metadata pro všechny základní dílčí moduly sloučení dohromady.  
  
- Jejich názvy typů mohou pozměněny.  
  
- [Icordebugmodule::getName –](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md) metoda vrátí cestu k modulu na disku.  
  
- [Icordebugmodule::getsize –](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md) metoda vrátí velikost tohoto obrázku.  
  
- Metoda ICorDebugAssembly3.EnumerateContainedAssemblies seznam dílčích modulů.  
  
- Vrátí metodu ICorDebugAssembly3.GetContainerAssembly `S_FALSE`.  
  
 Dílčí moduly mají následující charakteristiky a chování:  
  
- Mají omezenou sadu metadata, která pouze odpovídá původní sestavení, která se slučuje.  
  
- Metadata názvy nejsou pozměněny.  
  
- Tokeny metadat by problém nahlásili shodovat s tokeny v původní sestavení předtím, než se nesloučila v procesu sestavení.  
  
- [Icordebugmodule::getName –](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md) metoda vrátí název sestavení, ne cestu k souboru.  
  
- [Icordebugmodule::getsize –](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md) metoda vrátí původní velikost nesloučené bitové kopie.  
  
- Vrátí metodu ICorDebugModule3.EnumerateContainedAssemblies `S_FALSE`.  
  
- Metoda ICorDebugAssembly3.GetContainerAssembly vrátí obsahující modul.  
  
## <a name="interfaces-retrieved-from-modules"></a>Rozhraní načíst z modulů  
 Širokou škálu rozhraní můžou vytvořit nebo načíst z modulů. Zde jsou některá z vylepšení:  
  
- Icordebugclass – objekt, který je vrácený [icordebugmodule::getclassfromtoken –](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md) metody.  
  
- Icordebugassembly – objekt, který je vrácený [icordebugmodule::getassembly –](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md) metody.  
  
 Tyto objekty jsou vždy v mezipaměti [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md), a budou mít stejnou identitu ukazatele bez ohledu na to, zda byly vytvořeny nebo posílat dotaz z kontejnerů modulu nebo dílčí modul. Dílčí modul obsahuje filtrované zobrazení těchto objektů uložených v mezipaměti, samostatné mezipaměti s vlastní kopie.  
  
<a name="APIs"></a>   
## <a name="virtual-module-splitting-and-the-unmanaged-debugging-apis"></a>Nespravované ladění rozhraní API a rozdělení virtuální modulu  
 Následující tabulka uvádí virtuálních modulu rozdělení ovlivní chování jiné metody v rozhraní API pro nespravované ladění.  
  
|Metoda|`enableSplitting` = `true`|`enableSplitting` = `false`|  
|------------|---------------------------------|----------------------------------|  
|[Icordebugfunction::getmodule –](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|Vrátí dílčí modul, který tato funkce byla původně definována v|Vrátí kontejner modul, který tato funkce se nesloučila do|  
|[ICorDebugClass::GetModule](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getmodule-method.md)|Vrátí dílčí modul, který tato třída byla původně definována v.|Vrátí kontejner modul, který tato třída se nesloučila do.|  
|ICorDebugModuleDebugEvent::GetModule|Vrátí kontejner modulu, který byl načten. Dílčí moduly nejsou uvedeny zatížení událostí bez ohledu na toto nastavení.|Vrátí kontejner modulu, který byl načten.|  
|[ICorDebugAppDomain::EnumerateAssemblies](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|Vrátí seznam hodnot dílčí sestavení a regulárního sestavení; žádná kontejneru sestavení nejsou zahrnuty. **Poznámka:**  Pokud žádné sestavení kontejneru chybí symboly, žádný z jeho dílčích sestavení se vytvořil výčet. Pokud žádné regulárního sestavení chybí symboly, může nebo nemusí být ve výčtu.|Vrátí seznam sestavení kontejneru a regulárního sestavení; žádná dílčí sestavení nejsou zahrnuty. **Poznámka:**  Pokud žádné regulárního sestavení chybí symboly, může nebo nemusí být ve výčtu.|  
|[Icordebugcode::getcode –](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md) (k odkazování na pouze kód IL)|Vrátí IL, která by byla platná v bitové kopii předběžného sloučení sestavení. Konkrétně všechny vložené tokeny metadat správně bude odkaz TypeRef nebo MemberRef tokeny při typů, který se odkazuje nejsou definované v modulu virtuální obsahující IL. Tyto tokeny TypeRef nebo MemberRef lze vyhledávat [imetadataimport –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) objekt pro odpovídající virtuální ICorDebugModule objekt.|Vrátí image po sloučení sestavení IL.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugProcess6 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
