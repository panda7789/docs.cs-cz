---
title: "ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod – metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b933dfe6-7833-40cb-aad8-40842dc3034f
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6cf0bccebbfe5620ef329cc8c6f72582a7afe85a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfo6enumngenmodulemethodsinliningthismethod-method"></a>ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod – metoda
[Podporované v rozhraní .NET Framework 4.6 a novějších verzích]  
  
 Vrátí enumerátor pro všechny metody, které jsou definovány v daném modulu NGen a vložené dané metody.  
  
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
 [v] Identifikátor modul NGen.  
  
 `inlineeModuleId`  
 [v] Identifikátor modul, který definuje `inlineeMethodId`. Další informace naleznete v části Poznámky.  
  
 `inlineeMethodId`  
 [v] Identifikátor vložená metoda. Další informace naleznete v části Poznámky.  
  
 `incompleteData`  
 [out] Příznak, který určuje, zda `ppEnum` obsahuje všechny metody vložené dané metody.  Další informace naleznete v části Poznámky.  
  
 `ppEnum`  
 [out] Ukazatel na adresu enumerátor  
  
## <a name="remarks"></a>Poznámky  
 `inlineeModuleId`a `inlineeMethodId` společně tvoří úplný identifikátor metodu, která může být vložená. Předpokládejme například, modul `A` definuje metodu `Simple.Add`:  
  
```csharp  
Simple.Add(int a, int b)   
{ return a + b; }  
```  
  
 modul Bdefines a `Fancy.AddTwice`:  
  
```csharp  
Fancy.AddTwice(int a, int b)   
{ return Simple.Add(a,b) + Simple.Add(a,b); }  
```  
  
 Umožňuje také předpokládají, že `Fancy.AddTwice` inlines volání do `SimpleAdd`. Profileru použít tento enumerátor najít všechny metody definované v modulu B, který vložené `Simple.Add`, a výsledkem by výčet `AddTwice`.  `inlineeModuleId`je identifikátor modulu `A`, a `inlineeeMethodId` je identifikátor `Simple.Add(int a, int b)`.  
  
 Pokud `incompleteData` platí po funkce vrátí enumerátor neobsahuje všechny metody vložené dané metody. K tomu může dojít, pokud jeden nebo dosud nebyla načtena přímý nebo nepřímý závislosti inliners modulu. Pokud profileru potřebuje přesná data, jeho pokus opakovat později. Pokud další moduly jsou načteny, pokud možno na každém načtení modulu.  
  
 `EnumNgenModuleMethodsInliningThisMethod` Metoda lze obejít omezení na vložené pro ReJIT. ReJIT umožňuje profileru změňte implementaci metody a pak vytvořte nový kód pro něj za chodu. Například nám změnit `Simple.Add` následujícím způsobem:  
  
```csharp  
Simple.Add(int a, int b)   
{ return 42; }  
```  
  
 Ale protože `Fancy.AddTwice` má již vložená `Simple.Add`, pokračuje tak, aby měl stejné chování jako předtím. Toto omezení obejít, má vyhledat všechny metody ve všech modulech přímo tady volající `Simple.Add` a používat `ICorProfilerInfo5::RequestRejit` na každé z těchto metod. Pokud se metody znovu kompilované, budou mít nové chování `Simple.Add` místo staré chování.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** najdete v části [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorProf.idl, CorProf.h  
  
 **Knihovna:** CorGuids.lib  
  
 **Verze rozhraní .NET framework:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Viz také  
 [ICorProfilerInfo6 rozhraní](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo6-interface.md)
