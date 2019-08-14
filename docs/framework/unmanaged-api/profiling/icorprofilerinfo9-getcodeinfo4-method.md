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
ms.openlocfilehash: e0493ed3f8796019d5715ef468c88675b9970a39
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973699"
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
  
#### <a name="parameters"></a>Parametry  
 `pNativeCodeStartAddress`  
 pro Ukazatel na začátek nativní funkce.  

 `cCodeInfos`  
 pro Velikost `codeInfos` pole.  
  
 `pcCodeInfos`  
 mimo Ukazatel na celkový počet dostupných struktur [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md)  
  
 `codeInfos`  
 mimo Vyrovnávací paměť poskytnutá volajícím. Poté, co metoda vrátí, obsahuje pole `COR_PRF_CODE_INFO` struktury, z nichž každý popisuje blok nativního kódu.  
  
## <a name="remarks"></a>Poznámky  
 Metoda je podobná GetCodeInfo3 –, s tím rozdílem, že může vyhledat informace o kódu pro různé nativní verze metody. [](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getcodeinfo3-method.md) `GetCodeInfo4`  
  
> [!NOTE]
>  `GetCodeInfo4`může aktivovat uvolňování paměti.
  
 Rozsahy jsou seřazené v pořadí zvyšování Common Intermediate Language (CIL) posun.  
  
 Po `GetCodeInfo4` návratu je nutné ověřit `codeInfos` , zda byla vyrovnávací paměť dostatečně velká, aby obsahovala všechny struktury [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) . Chcete-li to provést, porovnejte `cCodeInfos` hodnotu s hodnotou `cchName` parametru. Je `cCodeInfos` -li děleno velikostí struktury [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) menší než `pcCodeInfos`, přidělte větší `codeInfos` vyrovnávací paměť, aktualizujte `cCodeInfos` novou, větší velikost a zavolejte `GetCodeInfo4` znovu.  
  
 Případně můžete pro získání správné velikosti `GetCodeInfo4` vyrovnávací paměti nejprve zavolat s `codeInfos` nulovou délkou vyrovnávací paměti. Pak můžete `codeInfos` nastavit velikost vyrovnávací paměti na hodnotu vrácenou `pcCodeInfos`v, vynásobenou velikostí [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) struktury a volat `GetCodeInfo4` znovu.   
  

## <a name="requirements"></a>Požadavky  
 **Platformu** Viz [podporované operační systémy .NET Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).  
  
 **Hlaviček** CorProf.idl, CorProf.h  
  
 **Knihovna** CorGuids.lib  
  
 **Verze rozhraní .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)] 
  
## <a name="see-also"></a>Viz také:
- [Rozhraní ICorProfilerInfo9](../../../../docs/framework/unmanaged-api/profiling/ICorProfilerInfo9-interface.md)

