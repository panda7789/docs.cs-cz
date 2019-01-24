---
title: ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method
ms.date: 03/30/2017
ms.assetid: b933dfe6-7833-40cb-aad8-40842dc3034f
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 07b1c905e587708336ce690bbf3d187b2d21e5b9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54568150"
---
# <a name="icorprofilerinfo6enumngenmodulemethodsinliningthismethod-method"></a>ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod Method
[Podporované v rozhraní .NET Framework 4.6 a novějších verzích]  
  
 Vrátí enumerátor pro všechny metody, které jsou definovány v zadaném modulu NGen a vložené dané metody.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
HRESULT EnumNgenModuleMethodsInliningThisMethod(  
        [in] ModuleID inlinersModuleId,  
        [in] ModuleID inlineeModuleId,  
        [in] mdMethodDef inlineeMethodId,  
        [out] BOOL *incompleteData,  
        [out] ICorProfilerMethodEnum** ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `inlinersModuleId`  
 [in] Identifikátor modulu technologie NGen.  
  
 `inlineeModuleId`  
 [in] Identifikátor modulu, který definuje `inlineeMethodId`. Další informace naleznete v části Poznámky.  
  
 `inlineeMethodId`  
 [in] Identifikátor je vložená metoda. Další informace naleznete v části Poznámky.  
  
 `incompleteData`  
 [out] Příznak označující, zda `ppEnum` obsahuje všechny metody vkládání dané metody.  Další informace naleznete v části Poznámky.  
  
 `ppEnum`  
 [out] Ukazatel na adresu enumerátor  
  
## <a name="remarks"></a>Poznámky  
 `inlineeModuleId` a `inlineeMethodId` společně tvoří úplný identifikátor pro metodu, která mohou být vložená. Předpokládejme například, modul `A` definuje metodu `Simple.Add`:  
  
```csharp  
Simple.Add(int a, int b)   
{ return a + b; }  
```  
  
 modul Bdefines a `Fancy.AddTwice`:  
  
```csharp  
Fancy.AddTwice(int a, int b)   
{ return Simple.Add(a,b) + Simple.Add(a,b); }  
```  
  
 Umožňuje taky se předpokládá, že `Fancy.AddTwice` inlines volání do `SimpleAdd`. Profiler může použít výčet najít všechny metody definované v modulu B které vložené `Simple.Add`, a výsledek by výčet `AddTwice`.  `inlineeModuleId` identifikátor modulu `A`, a `inlineeeMethodId` je identifikátor `Simple.Add(int a, int b)`.  
  
 Pokud `incompleteData` platí za funkci vrací enumerátor neobsahuje všechny metody vkládání dané metody. K tomu může dojít v případě, že jedna nebo přímou nebo nepřímou závislostmi inliners modulu nebyly dosud načteny. Pokud profiler přesná data, je při další moduly se načítají, pokud možno na každého modulu zatížení opakovat později.  
  
 `EnumNgenModuleMethodsInliningThisMethod` Metodu je možné obejít omezení na vkládání pro ReJIT. ReJIT umožňuje profileru, změňte implementaci metody a pak vytvořte nový kód pro něj v reálném čase. Můžeme například změnit `Simple.Add` následujícím způsobem:  
  
```csharp  
Simple.Add(int a, int b)   
{ return 42; }  
```  
  
 Ale protože `Fancy.AddTwice` má již vložených `Simple.Add`, nadále mají stejné chování jako předtím. Toto omezení obejít, volající musí vyhledat všechny metody ve všech modulech přímo tady `Simple.Add` a použít `ICorProfilerInfo5::RequestRejit` na každé z těchto metod. Pokud metody jsou znovu zkompilovány, mají nové chování `Simple.Add` místo staré chování.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Viz také:
- [ICorProfilerInfo6 – rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)
