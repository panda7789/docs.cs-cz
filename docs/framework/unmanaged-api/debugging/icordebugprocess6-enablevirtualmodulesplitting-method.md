---
title: ICorDebugProcess6::EnableVirtualModuleSplitting – metoda
ms.date: 03/30/2017
ms.assetid: e7733bd3-68da-47f9-82ef-477db5f2e32d
ms.openlocfilehash: 32648f40046959ffd8676fe67a1e0a123b0e801f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73123514"
---
# <a name="icordebugprocess6enablevirtualmodulesplitting-method"></a>ICorDebugProcess6::EnableVirtualModuleSplitting – metoda
Povolí nebo zakáže rozdělení virtuálního modulu.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT EnableVirtualModuleSplitting(  
   BOOL enableSplitting  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `enableSplitting`  
 `true` Povolit rozdělení virtuálního modulu; `false` ji zakážete.  
  
## <a name="remarks"></a>Poznámky  
 Rozdělení virtuálního modulu způsobí, že [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) rozpoznává moduly, které byly sloučeny společně během procesu sestavení, a prezentuje je jako skupinu samostatných modulů, nikoli jenom jeden velký modul. Tím se změní chování různých [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) metod popsaných níže.  
  
> [!NOTE]
> Tato metoda je k dispozici pouze s .NET Native.  
  
 Tuto metodu lze volat a hodnotu `enableSplitting` lze kdykoli změnit. Nezpůsobí změny stavového funkce v objektu [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) , jiné než změna chování metod uvedených v tématu [rozdělení virtuálního modulu a rozhraní API nespravovaného ladění](#APIs) v době volání. Při volání těchto metod při použití virtuálních modulů dojde ke snížení výkonu. Kromě toho může být pro správnou implementaci rozhraní [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) API nutná významná mezipaměť virtualizovaného ukládání do paměti a tyto mezipaměti mohou být zachovány i po vypnutí funkce rozdělení virtuálního modulu.  
  
## <a name="terminology"></a>Terminologie  
 Následující výrazy se použijí při popisu rozdělení virtuálního modulu:  
  
 moduly kontejneru nebo kontejnery  
 Agregované moduly.  
  
 dílčí moduly nebo virtuální moduly  
 Moduly nalezené v kontejneru.  
  
 běžné moduly  
 Moduly, které nebyly sloučeny v době sestavení. Nejsou to žádné moduly kontejneru ani podmoduly.  
  
 Moduly a dílčí moduly kontejneru jsou reprezentovány objekty rozhraní ICorDebugModule. Chování rozhraní se ale v každém případě mírně liší, protože popisuje \<x-ref na oddíl > oddíl.  
  
## <a name="modules-and-assemblies"></a>Moduly a sestavení  
 Sestavení s více moduly nejsou u scénářů sloučení sestavení podporována, takže existuje vztah 1:1 mezi modulem a sestavením. Každý objekt ICorDebugModule, bez ohledu na to, zda představuje modul kontejneru nebo dílčí modul, má odpovídající objekt ICorDebugAssembly. Metoda [ICorDebugModule:: GetAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md) se převede z modulu na sestavení. Aby bylo možné namapovat druhý směr, metoda [ICorDebugAssembly:: EnumerateModules –](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-enumeratemodules-method.md) vytvoří pouze jeden modul. Vzhledem k tomu, že sestavení a modul tvoří v tomto případě pevně spojenou dvojici, podmínky sestavení a modulu se stanou v podstatě zaměnitelné.  
  
## <a name="behavioral-differences"></a>Rozdíly v chování  
 Moduly kontejneru mají následující chování a vlastnosti:  
  
- Jejich metadata pro všechny dílčí moduly prvku se sloučí dohromady.  
  
- Jejich názvy typů se můžou považovat za pozměněné.  
  
- Metoda [ICorDebugModule:: GetName](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md) vrátí cestu k modulu na disku.  
  
- Metoda [ICorDebugModule:: GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md) vrátí velikost tohoto obrázku.  
  
- Metoda ICorDebugAssembly3. EnumerateContainedAssemblies – zobrazí dílčí moduly.  
  
- Metoda ICorDebugAssembly3. GetContainerAssembly – vrací `S_FALSE`.  
  
 Dílčí moduly mají následující chování a vlastnosti:  
  
- Mají omezenou sadu metadat, která odpovídá pouze původnímu sestavení, které bylo sloučeno.  
  
- Názvy metadat nejsou pozměněny.  
  
- Tokeny metadat pravděpodobně neodpovídají tokenům v původním sestavení před jejich sloučením v procesu sestavení.  
  
- Metoda [ICorDebugModule:: GetName](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getname-method.md) vrátí název sestavení, ne cestu k souboru.  
  
- Metoda [ICorDebugModule:: GetSize](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getsize-method.md) vrátí původní nesloučenou velikost obrázku.  
  
- Metoda ICorDebugModule3. EnumerateContainedAssemblies – vrací `S_FALSE`.  
  
- Metoda ICorDebugAssembly3. GetContainerAssembly – vrátí obsahující modul.  
  
## <a name="interfaces-retrieved-from-modules"></a>Rozhraní načtená z modulů  
 V modulech lze vytvořit nebo načíst celou řadu rozhraní. Zde jsou některá z vylepšení:  
  
- Objekt ICorDebugClass, který je vrácen metodou [ICorDebugModule:: getclassfromtoken –](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getclassfromtoken-method.md) .  
  
- Objekt ICorDebugAssembly, který je vrácen metodou [ICorDebugModule:: GetAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-getassembly-method.md) .  
  
 Tyto objekty jsou vždy ukládány do mezipaměti podle [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)a budou mít stejnou identitu ukazatele bez ohledu na to, zda byly vytvořeny nebo dotazovány z modulu kontejneru nebo dílčího modulu. Dílčí modul poskytuje filtrované zobrazení těchto objektů v mezipaměti, nikoli samostatnou mezipaměť s vlastními kopiemi.  
  
<a name="APIs"></a>   
## <a name="virtual-module-splitting-and-the-unmanaged-debugging-apis"></a>Rozdělení virtuálního modulu a nespravované rozhraní API pro ladění  
 Následující tabulka ukazuje, jak rozdělení virtuálního modulu ovlivňuje chování jiných metod v nespravovaném rozhraní API pro ladění.  
  
|Metoda|`enableSplitting` = `true`|`enableSplitting` = `false`|  
|------------|---------------------------------|----------------------------------|  
|[ICorDebugFunction:: GetModule](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-getmodule-method.md)|Vrátí dílčí modul, ve kterém byla tato funkce původně definovaná.|Vrátí modul kontejneru, do kterého byla funkce sloučena.|  
|[ICorDebugClass:: GetModule](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-getmodule-method.md)|Vrátí dílčí modul, ve kterém je tato třída původně definovaná.|Vrátí modul kontejneru, do kterého byla tato třída sloučena.|  
|ICorDebugModuleDebugEvent:: GetModule|Vrátí modul kontejneru, který byl načten. Dílčím modulům nejsou předány události načtení bez ohledu na toto nastavení.|Vrátí modul kontejneru, který byl načten.|  
|[ICorDebugAppDomain:: Enumerateassemblies –](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-enumerateassemblies-method.md)|Vrátí seznam podsestav a běžných sestavení. nejsou součástí žádného sestavení kontejneru. **Poznámka:**  Pokud v žádném sestavení kontejneru chybí symboly, nebude vytvořena výčet žádného z jeho dílčích sestavení. Pokud některé běžné sestavení chybějící symboly, může nebo nemusí být výčtu.|Vrátí seznam sestavení kontejneru a běžná sestavení; žádná dílčí sestavení nejsou součástí. **Poznámka:**  Pokud některé běžné sestavení chybějící symboly, může nebo nemusí být výčtu.|  
|[ICorDebugCode:: GetCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getcode-method.md) (při odkazování pouze na kód Il)|Vrátí IL, který by byl platný v imagi sestavení před sloučením. Konkrétně všechny vložené tokeny metadat budou mít správné tokeny TypeRef nebo MemberRef, pokud typy, na které se odkazuje, nejsou definovány ve virtuálním modulu obsahujícím IL. Tyto tokeny TypeRef a MemberRef lze vyhledat v objektu [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) pro odpovídající objekt Virtual ICorDebugModule.|Vrátí IL v imagi sestavení po sloučení.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorDebug. idl, CorDebug. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorDebugProcess6 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
