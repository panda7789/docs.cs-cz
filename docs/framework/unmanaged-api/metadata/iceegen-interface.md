---
title: ICeeGen – rozhraní
ms.date: 03/30/2017
api_name:
- ICeeGen
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen
helpviewer_keywords:
- ICeeGen interface [.NET Framework metadata]
ms.assetid: 383d20b0-efe9-4e71-8fb8-1186b2e7d0c0
topic_type:
- apiref
ms.openlocfilehash: ae3c372951de00b097d0a8437039a3a85bf3aabf
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74426150"
---
# <a name="iceegen-interface"></a>ICeeGen – rozhraní
Provides methods for dynamic code compilation.  
  
 This interface is obsolete and should not be used.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Popis|  
|------------|-----------------|  
|[AddSectionReloc – metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)|Zastaralé. Adds a .reloc instruction to the code base.|  
|[AllocateMethodBuffer – metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-allocatemethodbuffer-method.md)|Zastaralé. Creates a buffer of the specified size for a method, and gets the relative virtual address of the method.|  
|[ComputePointer – metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-computepointer-method.md)|Zastaralé. Determines the buffer for the specified code section.|  
|[EmitString – metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-emitstring-method.md)|Zastaralé. Emits the specified string into the code base.|  
|[GenerateCeeFile – metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-generateceefile-method.md)|Zastaralé. Generates a code-base file that contains the code base currently loaded into this `ICeeGen`.|  
|[GenerateCeeMemoryImage – metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-generateceememoryimage-method.md)|Zastaralé. Generates an image in memory for the code base.|  
|[GetIlSection – metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-getilsection-method.md)|Zastaralé. Gets the section of the intermediate language code base referenced by the specified handle.|  
|[GetIMapTokenIface – metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-getimaptokeniface-method.md)|Zastaralé. Gets the interface referenced by the specified token.|  
|[GetMethodBuffer – metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-getmethodbuffer-method.md)|Zastaralé. Gets a buffer of the appropriate size for the method at the specified relative virtual address.|  
|[GetSectionBlock – metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectionblock-method.md)|Zastaralé. Gets a section block of the code base.|  
|[GetSectionCreate – metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectioncreate-method.md)|Zastaralé. Generates and gets a code section using the specified name and flag values.|  
|[GetSectionDataLen – metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-getsectiondatalen-method.md)|Zastaralé. Gets the length of the specified section.|  
|[GetString – metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-getstring-method.md)|Zastaralé. Gets the string stored at the specified relative virtual address.|  
|[GetStringSection – metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-getstringsection-method.md)|Zastaralé. Gets a string representation of the code section referenced by the specified handle.|  
|[TruncateSection – metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-truncatesection-method.md)|Zastaralé. Truncates the specified code section by the specified length.|  
  
## <a name="requirements"></a>Požadavky  
 **Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Header:** Cor.h  
  
 **Library:** Used as a resource in MsCorEE.dll  
  
 **.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- [Rozhraní pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-interfaces.md)
