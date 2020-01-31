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
ms.openlocfilehash: 64d2cd76dafb1a51814b916b5ce73fb08cdcaef9
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868857"
---
# <a name="icorprofilerinfo2getclassidinfo2-method"></a>ICorProfilerInfo2::GetClassIDInfo2 – metoda
Získá nadřazený modul a token metadat pro otevřenou obecnou definici zadané třídy, `ClassID` své nadřazené třídy a `ClassID` pro každý argument typu, pokud je k dispozici pro třídu.  
  
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
 pro Velikost pole `typeArgs`.  
  
 `pcNumTypeArgs`  
 mimo Ukazatel na celkový počet dostupných prvků.  
  
 `typeArgs`  
 mimo Pole hodnot `ClassID`, z nichž každá představuje ID argumentu typu třídy. Když se metoda vrátí, `typeArgs` bude obsahovat některé nebo všechny dostupné `ClassID` hodnoty.  
  
## <a name="remarks"></a>Poznámky  
 Metoda `GetClassIDInfo2` je podobná metodě [ICorProfilerInfo:: GetClassIDInfo –](icorprofilerinfo-getclassidinfo-method.md) , ale `GetClassIDInfo2` získá další informace o obecném typu.  
  
 Kód profileru může zavolat [ICorProfilerInfo:: GetModuleMetaData –](icorprofilerinfo-getmodulemetadata-method.md) a získat rozhraní [metadat](../../../../docs/framework/unmanaged-api/metadata/index.md) pro daný modul. Token metadat, který je vrácen do umístění odkazovaného `pTypeDefToken` lze následně použít pro přístup k metadatům třídy.  
  
 Jakmile `GetClassIDInfo2` vrátí, je nutné ověřit, zda byla vyrovnávací paměť `typeArgs` dostatečně velká, aby obsahovala všechny `ClassID` hodnoty. To provedete tak, že porovnáte hodnotu, na kterou `pcNumTypeArgs` odkazuje, hodnotou `cNumTypeArgs` parametru. Pokud `pcNumTypeArgs` odkazuje na hodnotu, která je větší než `cNumTypeArgs`, přidělte větší vyrovnávací paměť `typeArgs`, aktualizujte `cNumTypeArgs` novou, větší velikostí a zavolejte `GetClassIDInfo2` znovu.  
  
 Alternativně můžete pro získání správné velikosti vyrovnávací paměti nejprve volat `GetClassIDInfo2` s nulovou délkou `typeArgs` vyrovnávací paměti. Pak můžete nastavit velikost vyrovnávací paměti `typeArgs` na hodnotu vrácenou v `pcNumTypeArgs` a volat `GetClassIDInfo2` znovu.  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorProf. idl, CorProf. h  
  
 **Knihovna:** CorGuids. lib  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [ICorProfilerInfo – rozhraní](icorprofilerinfo-interface.md)
- [ICorProfilerInfo2 – rozhraní](icorprofilerinfo2-interface.md)
- [Rozhraní pro profilaci](profiling-interfaces.md)
- [Profilace](index.md)
