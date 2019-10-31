---
title: 'ICorDebugSymbolProvider2:: GetGenericDictionaryInfo – metoda'
ms.date: 03/30/2017
ms.assetid: ba28fe4e-5491-4670-bff7-7fde572d7593
ms.openlocfilehash: c9f7206cac54d64c28eb50d81fea00a6f3c494d4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133636"
---
# <a name="icordebugsymbolprovider2getgenericdictionaryinfo-method"></a>ICorDebugSymbolProvider2:: GetGenericDictionaryInfo – metoda

Načte mapu obecného slovníku.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetGenericDictionaryInfo(
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer
);
```

## <a name="parameters"></a>Parametry

`ppMemoryBuffer`\
mimo Ukazatel na adresu objektu [ICorDebugMemoryBuffer](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md) obsahující mapu obecného slovníku. Další informace naleznete v části Poznámky.

## <a name="remarks"></a>Poznámky

> [!NOTE]
> Tato metoda je k dispozici pouze s .NET Native.

Mapa se skládá ze dvou sekcí nejvyšší úrovně:

- [Adresář](#Directory) obsahující relativní virtuální adresy (RVA) všech slovníků obsažených v této mapě.

- [Halda](#Heap) zarovnaná na bajt, která obsahuje informace o vytváření instancí objektů. Spustí se hned za poslední položkou adresáře.

<a name="Directory"></a>

## <a name="the-directory"></a>Adresář

Každá položka v adresáři odkazuje na posun uvnitř haldy. To znamená, že se jedná o posun, který je relativní ke spuštění haldy. Hodnota jednotlivých položek není nutně jedinečná; je možné, aby více položek adresáře odkazovalo na stejný posun v haldě.

Část adresáře mapy obecného slovníku má následující strukturu:

- Prvních 4 bajtů obsahuje počet položek slovníku (tj. počet relativních virtuálních adres ve slovníku). Na tuto hodnotu odkazujeme jako na *N*. Pokud je nastavený vysoký bit, položky se seřadí podle relativní virtuální adresy ve vzestupném pořadí.

- Následují položky adresáře *N* . Každá položka se skládá z 8 bajtů, ve dvou segmentech se 4 bajty:

  - Bajty 0-3: RVA; relativní virtuální adresa slovníku

  - Bajty 4-7: offset; posun vzhledem k začátku haldy.

<a name="Heap"></a>

## <a name="the-heap"></a>Halda

Velikost haldy lze vypočítat pomocí čtečky datového proudu odečtením délky datového proudu od velikosti adresáře + 4. Jinými slovy:

```csharp
Heap Size = Stream.Length – (Directory Size + 4)
```

kde je velikost adresáře `N * 8`.

Formát pro každou položku informací o instanciaci haldy je:

- Délka položky informací o instanciování v bajtech v komprimovaném formátu metadat ECMA Tato hodnota vylučuje tyto informace o délce.

- Počet generických typů vytváření instancí, nebo *T*, v komprimovaném formátu metadat ECMA.

- Typy *T* , z nichž každá představuje formát podpisu typu ECMA.

Zahrnutí délky pro každý prvek haldy umožňuje jednoduché řazení oddílu adresáře bez ovlivnění haldy.

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).

**Hlavička:** CorDebug. idl, CorDebug. h

**Knihovna:** CorGuids. lib

**Verze .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]

## <a name="see-also"></a>Viz také:

- [ICorDebugSymbolProvider2 – rozhraní](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)
- [Rozhraní pro ladění](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
