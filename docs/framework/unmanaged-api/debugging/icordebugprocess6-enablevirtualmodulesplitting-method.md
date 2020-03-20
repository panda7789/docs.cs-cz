---
title: ICorDebugProcess6::EnableVirtualModuleSplitting – metoda
ms.date: 03/30/2017
ms.assetid: e7733bd3-68da-47f9-82ef-477db5f2e32d
ms.openlocfilehash: 8ad15d11ce81323b30434b3db98259a74a198f29
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178561"
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
 `true`pro umožnění rozdělení virtuálních modulů; `false` a vypněte jej.  
  
## <a name="remarks"></a>Poznámky  
 Rozdělení virtuálních modulů způsobí, že [ICorDebug](icordebug-interface.md) rozpozná moduly, které byly sloučeny během procesu sestavení a prezentovat je jako skupinu samostatných modulů, nikoli jeden velký modul. Tím se změní chování různých metod [ICorDebug](icordebug-interface.md) popsaných níže.  
  
> [!NOTE]
> Tato metoda je k dispozici pouze s nativní .NET.  
  
 Tuto metodu lze volat `enableSplitting` a hodnotu lze kdykoli změnit. Nezpůsobí žádné stavové funkční změny v objektu [ICorDebug,](icordebug-interface.md) kromě změny chování metod uvedených v [rozdělení virtuálnímodul a nespravované ladění rozhraní API](#APIs) části v době, kdy jsou volány. Použití virtuálních modulů nezpůsobuje snížení výkonu při volání těchto metod. Kromě toho může být nutné významné ukládání do mezipaměti virtualizovaných metadat správně implementovat rozhraní API [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) a tyto mezipaměti mohou být zachovány i po vypnutí rozdělení virtuálního modulu.  
  
## <a name="terminology"></a>Terminologie  
 Následující termíny se používají při popisu rozdělení virtuálnímodul:  
  
 kontejnerové moduly nebo kontejnery  
 Agregační moduly.  
  
 podmoduly nebo virtuální moduly  
 Moduly nalezené v kontejneru.  
  
 pravidelné moduly  
 Moduly, které nebyly sloučeny v době sestavení. Nejsou to ani kontejnerové moduly, ani dílčí moduly.  
  
 Moduly kontejneru i podmoduly jsou reprezentovány objekty rozhraní ICorDebugModule. Chování rozhraní se však mírně liší v každém \<případě, jako x ref do části> části popisuje.  
  
## <a name="modules-and-assemblies"></a>Moduly a sestavy  
 Sestavení s více moduly nejsou podporovány pro scénáře slučování sestavení, takže existuje vztah 1:1 mezi modulem a sestavením. Každý objekt ICorDebugModule, bez ohledu na to, zda představuje modul kontejneru nebo podmodul, má odpovídající objekt ICorDebugAssembly. Metoda [ICorDebugModule::GetAssembly](icordebugmodule-getassembly-method.md) se převede z modulu na sestavení. Chcete-li mapovat v opačném směru, [Metoda ICorDebugAssembly::EnumerateModules](icordebugassembly-enumeratemodules-method.md) vyjmenovává pouze 1 modul. Vzhledem k tomu, že sestavení a modul tvoří v tomto případě pevně spřažený pár, podmínky sestavení a modul se stanou do značné míry zaměnitelné.  
  
## <a name="behavioral-differences"></a>Rozdíly v chování  
 Moduly kontejneru mají následující chování a charakteristiky:  
  
- Jejich metadata pro všechny dílčí moduly složek jsou sloučena.  
  
- Jejich názvy typů mohou být pošalené.  
  
- Metoda [ICorDebugModule::GetName](icordebugmodule-getname-method.md) vrátí cestu k modulu na disku.  
  
- [Metoda ICorDebugModule::GetSize](icordebugmodule-getsize-method.md) vrátí velikost této bitové kopie.  
  
- Metoda ICorDebugAssembly3.EnumerateContainedAssemblies uvádí podmoduly.  
  
- Metoda ICorDebugAssembly3.GetContainerAssembly `S_FALSE`vrátí .  
  
 Dílčí moduly mají následující chování a charakteristiky:  
  
- Mají sníženou sadu metadat, která odpovídá pouze původní sestavení, které bylo sloučeno.  
  
- Názvy metadat nejsou pošacené.  
  
- Tokeny metadat pravděpodobně neodpovídají tokenům v původním sestavení před sloučením v procesu sestavení.  
  
- Metoda [ICorDebugModule::GetName](icordebugmodule-getname-method.md) vrátí název sestavení, nikoli cestu k souboru.  
  
- [Metoda ICorDebugModule::GetSize](icordebugmodule-getsize-method.md) vrátí původní velikost nesloučeného obrázku.  
  
- Metoda ICorDebugModule3.EnumerateContainedAssemblvrátí `S_FALSE`.  
  
- Metoda ICorDebugAssembly3.GetContainerAssembly vrátí obsahující modul.  
  
## <a name="interfaces-retrieved-from-modules"></a>Rozhraní načtená z modulů  
 Z modulů lze vytvářet nebo načítat různá rozhraní. Zde jsou některá z vylepšení:  
  
- Objekt ICorDebugClass, který je vrácen metodou [ICorDebugModule::GetClassFromToken.](icordebugmodule-getclassfromtoken-method.md)  
  
- Objekt ICorDebugAssembly, který je vrácen metodou [ICorDebugModule::GetAssembly.](icordebugmodule-getassembly-method.md)  
  
 Tyto objekty jsou vždy uloženy do mezipaměti [ICorDebug](icordebug-interface.md)a budou mít stejnou identitu ukazatele bez ohledu na to, zda byly vytvořeny nebo dotazovány z modulu kontejneru nebo dílčího modulu. Podmodul poskytuje filtrované zobrazení těchto objektů uložených v mezipaměti, nikoli samostatnou mezipaměť s vlastními kopiemi.  
  
<a name="APIs"></a>
## <a name="virtual-module-splitting-and-the-unmanaged-debugging-apis"></a>Rozdělení virtuálního modulu a nespravovaná rozhraní API ladění  
 Následující tabulka ukazuje, jak rozdělení virtuálního modulu ovlivňuje chování jiných metod v nespravovaném rozhraní API ladění.  
  
|Metoda|`enableSplitting` = `true`|`enableSplitting` = `false`|  
|------------|---------------------------------|----------------------------------|  
|[ICorDebugFunction::GetModule](icordebugfunction-getmodule-method.md)|Vrátí dílčí modul, ve které byla tato funkce původně definována v|Vrátí modul kontejneru, do kterého byla tato funkce sloučena.|  
|[Třída ICorDebugClass::GetModule](icordebugclass-getmodule-method.md)|Vrátí dílčí modul, ve které byla tato třída původně definována.|Vrátí modul kontejneru, do kterého byla tato třída sloučena.|  
|ICorDebugModuleDebugEvent::GetModule|Vrátí modul kontejneru, který byl načten. Dílčí moduly nejsou uvedeny události zatížení bez ohledu na toto nastavení.|Vrátí modul kontejneru, který byl načten.|  
|[ICorDebugAppDomain::EnumerateAssemblies](icordebugappdomain-enumerateassemblies-method.md)|Vrátí seznam podsestav a pravidelných sestav. nejsou zahrnuty žádné sestavy kontejnerů. **Poznámka:**  Pokud žádné sestavení kontejneru chybí symboly, žádný z jeho podsestav budou uvedeny výčtu. Pokud některé pravidelné sestavení chybí symboly, může nebo nemusí být výčtu.|Vrátí seznam sestavení kontejnerů a pravidelných sestavení. nejsou zahrnuty žádné podsestavy. **Poznámka:**  Pokud některé pravidelné sestavení chybí symboly, může nebo nemusí být výčtu.|  
|[ICorDebugCode::GetCode](icordebugcode-getcode-method.md) (pouze při odkazování na kód IL)|Vrátí hodnotu IL, která by byla platná v bitové kopii sestavení před sloučením. Konkrétně všechny tokeny vložených metadat budou správně TypeRef nebo MemberRef tokeny, pokud typy uvedené nejsou definovány ve virtuálním modulu obsahujícím IL. Tyto Tokeny TypeRef nebo MemberRef lze vyhledat v objektu [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) pro odpovídající virtuální objekt ICorDebugModule.|Vrátí IL v image sestavení po sloučení.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorDebug.idl, CorDebug.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Viz také

- [Rozhraní ICorDebugProcess6](icordebugprocess6-interface.md)
- [Debugging – rozhraní](debugging-interfaces.md)
