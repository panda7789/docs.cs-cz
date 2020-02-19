---
title: ICorProfilerInfo9::GetCodeInfo4
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetCodeInfo4
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: f65cebff912adeb7afc34434467cf7be72f9be32
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449761"
---
# <a name="icorprofilerinfo9getcodeinfo4-method"></a>ICorProfilerInfo9:: GetCodeInfo4 – metoda

Vzhledem k počáteční adrese nativního kódu vrátí bloky virtuální paměti, která ukládá tento kód.

## <a name="syntax"></a>Syntaxe

```cpp
HRESULT GetCodeInfo4( [in]  UINT_PTR pNativeCodeStartAddress,
                      [in]  ULONG32 cCodeInfos,
                      [out] ULONG32* pcCodeInfos,
                      [out] COR_PRF_CODE_INFO codeInfos[]);
```

## <a name="parameters"></a>Parametry

- `pNativeCodeStartAddress`

  \[in] ukazatel na začátek nativní funkce.

- `cCodeInfos`

  \[] velikost pole `codeInfos`.

- `pcCodeInfos`

  \[] ukazatel na celkový počet dostupných [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) struktur.

- `codeInfos`

  \[] vyrovnávací paměť poskytnutou volajícím. Poté, co metoda vrátí, obsahuje pole `COR_PRF_CODE_INFO` struktury, z nichž každý popisuje blok nativního kódu.

## <a name="remarks"></a>Poznámky

Metoda `GetCodeInfo4` je podobná [GetCodeInfo3 –](icorprofilerinfo4-getcodeinfo3-method.md), s tím rozdílem, že může vyhledat informace o kódu pro různé nativní verze metody.

> [!NOTE]
> `GetCodeInfo4` může aktivovat uvolňování paměti.

Rozsahy jsou seřazené v pořadí zvyšování Common Intermediate Language (CIL) posun.

Po `GetCodeInfo4` vrátí, je nutné ověřit, zda byla vyrovnávací paměť `codeInfos` dostatečně velká, aby obsahovala všechny [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) struktury. To provedete tak, že porovnáte hodnotu `cCodeInfos` s hodnotou parametru `cchName`. Pokud je `cCodeInfos` dělené velikostí [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) struktury menší než `pcCodeInfos`, přidělte větší vyrovnávací paměť `codeInfos`, aktualizujte `cCodeInfos` o novou, větší velikost a zavolejte `GetCodeInfo4` znovu.

Alternativně můžete pro získání správné velikosti vyrovnávací paměti nejprve volat `GetCodeInfo4` s nulovou délkou `codeInfos` vyrovnávací paměti. Pak můžete nastavit velikost vyrovnávací paměti `codeInfos` na hodnotu vrácenou v `pcCodeInfos`vynásobenou velikostí [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) struktury a znovu volat `GetCodeInfo4`.

## <a name="requirements"></a>Požadavky

**Platformy:** Viz [podporované operační systémy .NET Core](../../../core/install/dependencies.md?pivots=os-windows).

**Hlavička:** CorProf. idl, CorProf. h

**Knihovna:** CorGuids. lib

**Verze rozhraní .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]

## <a name="see-also"></a>Viz také

- [Rozhraní ICorProfilerInfo9](ICorProfilerInfo9-interface.md)
