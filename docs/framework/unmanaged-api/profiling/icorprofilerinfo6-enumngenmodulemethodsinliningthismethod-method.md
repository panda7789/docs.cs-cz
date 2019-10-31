---
title: ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod – metoda
ms.date: 03/30/2017
ms.assetid: b933dfe6-7833-40cb-aad8-40842dc3034f
ms.openlocfilehash: 103fe1b6845edfe0a364db979557db63511f6ee3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130376"
---
# <a name="icorprofilerinfo6enumngenmodulemethodsinliningthismethod-method"></a>ICorProfilerInfo6::EnumNgenModuleMethodsInliningThisMethod – metoda

Vrátí enumerátor pro všechny metody, které jsou definovány v daném modulu NGen a vloží danou metodu.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT EnumNgenModuleMethodsInliningThisMethod(
        [in] ModuleID inlinersModuleId,
        [in] ModuleID inlineeModuleId,
        [in] mdMethodDef inlineeMethodId,
        [out] BOOL *incompleteData,
        [out] ICorProfilerMethodEnum** ppEnum
);
```

## <a name="parameters"></a>Parametry

`inlinersModuleId`\
pro Identifikátor modulu NGen.

`inlineeModuleId`\
pro Identifikátor modulu, který definuje `inlineeMethodId`. Další informace naleznete v části Poznámky.

`inlineeMethodId`\
pro Identifikátor vložené metody. Další informace naleznete v části Poznámky.

`incompleteData`\
mimo Příznak, který označuje, zda `ppEnum` obsahuje všechny metody pro vkládání dané metody.  Další informace naleznete v části Poznámky.

`ppEnum`\
mimo Ukazatel na adresu čítače výčtu

## <a name="remarks"></a>Poznámky

`inlineeModuleId` a `inlineeMethodId` dohromady tvoří úplný identifikátor pro metodu, která může být vložena. Předpokládejme například, že modul `A` definuje metodu `Simple.Add`:

```csharp
Simple.Add(int a, int b)
{ return a + b; }
```

a modul B definuje `Fancy.AddTwice`:

```csharp
Fancy.AddTwice(int a, int b)
{ return Simple.Add(a,b) + Simple.Add(a,b); }
```

Umožňuje také předpokládat, že `Fancy.AddTwice` zadává volání `SimpleAdd`. Profiler může tento enumerátor použít k vyhledání všech metod definovaných v modulu B, které obsahují vložené `Simple.Add`a výsledek by měl vytvořit výčet `AddTwice`.  `inlineeModuleId` je identifikátor `A`modulu a `inlineeMethodId` je identifikátor `Simple.Add(int a, int b)`.

Pokud `incompleteData` má hodnotu true poté, co funkce vrátí, enumerátor neobsahuje všechny metody pro vkládání dané metody. K tomu může dojít v případě, že není ještě načtena jedna nebo více přímých nebo nepřímých závislostí modulu inlinie. Pokud profiler potřebuje přesná data, zkuste to znovu později, až se načtou další moduly, nejlépe při každém načtení modulu.

Metodu `EnumNgenModuleMethodsInliningThisMethod` lze použít k obejít omezení pro vkládání pro ReJIT. ReJIT umožňuje profileru změnit implementaci metody a pak za běhu vytvořit nový kód. Například můžeme změnit `Simple.Add` následujícím způsobem:

```csharp
Simple.Add(int a, int b)
{ return 42; }
```

Vzhledem k tomu, že `Fancy.AddTwice` již byl vložen `Simple.Add`, bude nadále mít stejné chování jako předtím. Chcete-li toto omezení obejít, volající musí vyhledat všechny metody ve všech modulech, které jsou vloženy `Simple.Add` a použít `ICorProfilerInfo5::RequestRejit` na každou z těchto metod. Když jsou metody znovu zkompilovány, budou mít nové chování `Simple.Add` místo starého chování.

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).

**Hlavička:** CorProf. idl, CorProf. h

**Knihovna:** CorGuids. lib

**Verze .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]

## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo6 – rozhraní](icorprofilerinfo6-interface.md)
