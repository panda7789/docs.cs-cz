---
title: ICorProfilerInfo2::GetClassIDInfo2 – metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetClassIDInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassIDInfo2
helpviewer_keywords:
- GetClassIDInfo2 method [.NET Framework profiling]
- ICorProfilerInfo2::GetClassIDInfo2 method [.NET Framework profiling]
ms.assetid: 0141d582-d066-4d49-8d1f-ae82129a1960
topic_type:
- apiref
ms.openlocfilehash: a33e51969dc0579d976f08470ebc6e2bcca04dd7
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497163"
---
# <a name="icorprofilerinfo2getclassidinfo2-method"></a>ICorProfilerInfo2::GetClassIDInfo2 – metoda
Získá nadřazený modul a token metadat pro otevřenou obecnou definici zadané třídy, `ClassID` její nadřazené třídy a `ClassID` pro každý argument typu (Pokud je k dispozici) třídy.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
HRESULT GetClassIDInfo2(  
    [in]  ClassID classId,  
    [out] ModuleID *pModuleId,  
    [out] mdTypeDef *pTypeDefToken,  
    [out] ClassID *pParentClassId,  
    [in]  ULONG32 cNumTypeArgs,  
    [out] ULONG32 *pcNumTypeArgs,  
    [out] ClassID typeArgs[]);  
```  
  
## <a name="parameters"></a>Parametry  
 `classId`  
 pro ID třídy, pro kterou budou načteny informace.  
  
 `pModuleId`  
 mimo Ukazatel na ID nadřazeného modulu pro otevřenou obecnou definici zadané třídy.  
  
 `pTypeDefToken`  
 mimo Ukazatel na token metadat pro otevřenou obecnou definici zadané třídy.  
  
 `pParentClassId`  
 mimo Ukazatel na ID nadřazené třídy.  
  
 `cNumTypeArgs`  
 pro Velikost `typeArgs` pole.  
  
 `pcNumTypeArgs`  
 mimo Ukazatel na celkový počet dostupných prvků.  
  
 `typeArgs`  
 mimo Pole `ClassID` hodnot, z nichž každá představuje ID argumentu typu třídy. Když se metoda vrátí, `typeArgs` bude obsahovat některé nebo všechny dostupné `ClassID` hodnoty.  
  
## <a name="remarks"></a>Poznámky  
 `GetClassIDInfo2`Metoda je podobná metodě [ICorProfilerInfo:: GetClassIDInfo –](icorprofilerinfo-getclassidinfo-method.md) , ale `GetClassIDInfo2` získá další informace o obecném typu.  
  
 Kód profileru může zavolat [ICorProfilerInfo:: GetModuleMetaData –](icorprofilerinfo-getmodulemetadata-method.md) a získat rozhraní [metadat](../metadata/index.md) pro daný modul. Token metadat, který je vrácen do umístění odkazovaného pomocí, `pTypeDefToken` lze následně použít pro přístup k metadatům třídy.  
  
 Po `GetClassIDInfo2` návratu je nutné ověřit, zda `typeArgs` byla vyrovnávací paměť dostatečně velká, aby obsahovala všechny `ClassID` hodnoty. Provedete to tak, že porovnáte hodnotu, `pcNumTypeArgs` na kterou odkazuje, s hodnotou `cNumTypeArgs` parametru. Pokud `pcNumTypeArgs` odkazuje na hodnotu, která je větší než `cNumTypeArgs` , přidělte větší `typeArgs` vyrovnávací paměť, aktualizujte `cNumTypeArgs` novou, větší velikost a zavolejte `GetClassIDInfo2` znovu.  
  
 Případně můžete `GetClassIDInfo2` pro získání správné velikosti vyrovnávací paměti nejprve zavolat s nulovou délkou `typeArgs` vyrovnávací paměti. Pak můžete nastavit `typeArgs` Velikost vyrovnávací paměti na hodnotu vrácenou v `pcNumTypeArgs` a volat `GetClassIDInfo2` znovu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 – rozhraní](icorprofilerinfo2-interface.md)
- [Rozhraní pro profilaci](profiling-interfaces.md)
- [Profilace](index.md)
