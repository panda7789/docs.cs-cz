---
title: ICorProfilerInfo9 – rozhraní
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 431a546fb4a3b92b379e273553f0caf540ba1473
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449727"
---
# <a name="icorprofilerinfo9-interface"></a>ICorProfilerInfo9 – rozhraní

Podtřída [ICorProfilerInfo8](icorprofilerinfo8-interface.md) , která poskytuje metody pro dotazování na informace o funkcích s více nativními verzemi kódu.  

## <a name="methods"></a>Metody  

| Metoda|Popis|  
| ------------|-----------------|  
|[Metoda GetNativeCodeStartAddresses](icorprofilerinfo9-getnativecodestartaddresses-method.md)| S ohledem na functionId a rejitId vytvoří výčet počáteční adresy kódu pro všechny zpracovaných kompilátorem JIT verze tohoto kódu, který aktuálně existuje. |
|[Metoda GetILToNativeMapping3](icorprofilerinfo9-getiltonativemapping3-method.md)| Vzhledem k počáteční adrese nativního kódu vrací nativní informace mapování IL pro tuto verzi zpracovaných kompilátorem JIT kódu. |
|[Metoda GetCodeInfo4](icorprofilerinfo9-getcodeinfo4-method.md)| Vzhledem k počáteční adrese nativního kódu vrátí bloky virtuální paměti, která ukládá tento kód. |

## <a name="requirements"></a>Požadavky  
**Platformy:** Viz [podporované operační systémy .NET Core](../../../core/install/dependencies.md?pivots=os-windows).  
**Hlavička:** CorProf. idl, CorProf. h  
**Verze rozhraní .NET:** [!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]  

## <a name="see-also"></a>Viz také

- [Rozhraní pro profilaci](profiling-interfaces.md)
