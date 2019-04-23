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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6717c48fca14f2200f783a984594388ef3b29c15
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59211923"
---
# <a name="imetadataimport2-interface"></a>IMetaDataImport2 – rozhraní
Rozšiřuje [imetadataimport –](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md) rozhraní poskytovat funkce pro práci s obecných typů.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[EnumGenericParamConstraints – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparamconstraints-method.md)|Získá enumerátor pro celou řadu omezeních obecných parametrů, které jsou přidružené k obecný parametr reprezentována zadaného tokenu.|  
|[EnumGenericParams – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enumgenericparams-method.md)|Získá enumerátor pro celou řadu obecný parametr tokeny přidružené k zadaným TypeDef nebo MethodDef token.|  
|[EnumMethodSpecs – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-enummethodspecs-method.md)|Získá enumerátor pro celou řadu MethodSpec tokeny přidružené k zadaným MethodDef nebo MemberRef token.|  
|[GetGenericParamConstraintProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamconstraintprops-method.md)|Získá metadata přidružená k omezení obecného parametru reprezentována token zadané omezení.|  
|[GetGenericParamProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getgenericparamprops-method.md)|Získá metadata přidružená k obecný parametr reprezentována zadaného tokenu.|  
|[GetMethodSpecProps – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getmethodspecprops-method.md)|Získá metadata podpis metody odkazuje zadaný token MethodSpec token.|  
|[GetPEKind – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getpekind-method.md)|Získá hodnotu určující druh kódu do přenosného spustitelného (PE) soubor, obvykle knihovny DLL nebo EXE souboru, definované v aktuálním oboru metadat|  
|[GetVersionString – metoda](../../../../docs/framework/unmanaged-api/metadata/imetadataimport2-getversionstring-method.md)|Získá číslo verze modulu runtime, která byla použita k vytvoření sestavení.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** Cor.h  
  
 **Knihovna:** Použít jako prostředek v MsCorEE.dll  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Reflection.PortableExecutableKinds>
- [Rozhraní pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
- [IMetaDataImport – rozhraní](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md)
