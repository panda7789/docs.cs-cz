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
ms.openlocfilehash: 0fd7915ef46899bdce8312bc6e8a466167e26382
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429207"
---
# <a name="imetadataimport2-interface"></a>IMetaDataImport2 – rozhraní
Rozšiřuje rozhraní [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) , aby poskytovala schopnost pracovat s obecnými typy.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[EnumGenericParamConstraints – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparamconstraints-method.md)|Získá enumerátor pro pole omezení obecného parametru přidruženého k obecnému parametru reprezentovanému zadaným tokenem.|  
|[EnumGenericParams – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md)|Získá enumerátor pro pole tokenů obecných parametrů přidružených k zadanému tokenu TypeDef nebo MethodDef.|  
|[EnumMethodSpecs – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enummethodspecs-method.md)|Získá enumerátor pro pole tokenů MethodSpec přidružených k zadanému tokenu MethodDef nebo MemberRef.|  
|[GetGenericParamConstraintProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamconstraintprops-method.md)|Získá metadata přidružená k omezení obecného parametru reprezentované zadaným tokenem omezení.|  
|[GetGenericParamProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamprops-method.md)|Získá metadata přidružená k obecnému parametru reprezentovanému zadaným tokenem.|  
|[GetMethodSpecProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getmethodspecprops-method.md)|Získá podpis metadat metody, na kterou odkazuje zadaný token MethodSpec.|  
|[GetPEKind – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)|Získá hodnotu identifikující povahu kódu v přenositelném spustitelném souboru (PE), obvykle soubor DLL nebo EXE, definovaný v aktuálním oboru metadat.|  
|[GetVersionString – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getversionstring-method.md)|Získá číslo verze modulu runtime, který byl použit k sestavení sestavení.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** Cor. h  
  
 **Knihovna:** Používá se jako prostředek v knihovně MsCorEE. dll.  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Reflection.PortableExecutableKinds>
- [Rozhraní pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
