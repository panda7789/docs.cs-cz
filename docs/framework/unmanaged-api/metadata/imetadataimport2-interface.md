---
title: IMetaDataImport2 – rozhraní
ms.date: 03/30/2017
api_name:
- IMetaDataImport2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport2
helpviewer_keywords:
- IMetaDataImport2 interface [.NET Framework metadata]
ms.assetid: d39b2b87-ba53-4771-ae53-952a68452511
topic_type:
- apiref
ms.openlocfilehash: fe9e87618291218a41e52f80198ce9068c9c56e2
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84490391"
---
# <a name="imetadataimport2-interface"></a>IMetaDataImport2 – rozhraní
Rozšiřuje rozhraní [IMetaDataImport](imetadataimport-interface.md) , aby poskytovala schopnost pracovat s obecnými typy.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Description|  
|------------|-----------------|  
|[EnumGenericParamConstraints – metoda](imetadataimport2-enumgenericparamconstraints-method.md)|Získá enumerátor pro pole omezení obecného parametru přidruženého k obecnému parametru reprezentovanému zadaným tokenem.|  
|[EnumGenericParams – metoda](imetadataimport2-enumgenericparams-method.md)|Získá enumerátor pro pole tokenů obecných parametrů přidružených k zadanému tokenu TypeDef nebo MethodDef.|  
|[EnumMethodSpecs – metoda](imetadataimport2-enummethodspecs-method.md)|Získá enumerátor pro pole tokenů MethodSpec přidružených k zadanému tokenu MethodDef nebo MemberRef.|  
|[GetGenericParamConstraintProps – metoda](imetadataimport2-getgenericparamconstraintprops-method.md)|Získá metadata přidružená k omezení obecného parametru reprezentované zadaným tokenem omezení.|  
|[GetGenericParamProps – metoda](imetadataimport2-getgenericparamprops-method.md)|Získá metadata přidružená k obecnému parametru reprezentovanému zadaným tokenem.|  
|[GetMethodSpecProps – metoda](imetadataimport2-getmethodspecprops-method.md)|Získá podpis metadat metody, na kterou odkazuje zadaný token MethodSpec.|  
|[GetPEKind – metoda](imetadataimport2-getpekind-method.md)|Získá hodnotu identifikující povahu kódu v přenositelném spustitelném souboru (PE), obvykle soubor DLL nebo EXE, definovaný v aktuálním oboru metadat.|  
|[GetVersionString – metoda](imetadataimport2-getversionstring-method.md)|Získá číslo verze modulu runtime, který byl použit k sestavení sestavení.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Reflection.PortableExecutableKinds>
- [Rozhraní pro metadata](metadata-interfaces.md)
- [IMetaDataImport – rozhraní](imetadataimport-interface.md)
