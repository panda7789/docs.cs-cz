---
title: CorNativeType – výčet
ms.date: 03/30/2017
api_name:
- CorNativeType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNativeType
helpviewer_keywords:
- CorNativeType enumeration [.NET Framework metadata]
ms.assetid: e47a72f1-9609-48ed-bb34-97170d7f6890
topic_type:
- apiref
ms.openlocfilehash: ef4788891e91608a394482319a89b8b0d258449f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436513"
---
# <a name="cornativetype-enumeration"></a>CorNativeType – výčet
Obsahuje hodnoty, které popisují nativní nespravované typy.  
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
typedef enum CorNativeType {  
  
    NATIVE_TYPE_END                  = 0x0,  
    NATIVE_TYPE_VOID                 = 0x1,  
    NATIVE_TYPE_BOOLEAN              = 0x2,  
    NATIVE_TYPE_I1                   = 0x3,  
    NATIVE_TYPE_U1                   = 0x4,  
    NATIVE_TYPE_I2                   = 0x5,  
    NATIVE_TYPE_U2                   = 0x6,  
    NATIVE_TYPE_I4                   = 0x7,  
    NATIVE_TYPE_U4                   = 0x8,  
    NATIVE_TYPE_I8                   = 0x9,  
    NATIVE_TYPE_U8                   = 0xa,  
    NATIVE_TYPE_R4                   = 0xb,  
    NATIVE_TYPE_R8                   = 0xc,  
    NATIVE_TYPE_SYSCHAR              = 0xd,  
    NATIVE_TYPE_VARIANT              = 0xe,  
    NATIVE_TYPE_CURRENCY             = 0xf,  
    NATIVE_TYPE_PTR                  = 0x10,  
  
    NATIVE_TYPE_DECIMAL              = 0x11,  
    NATIVE_TYPE_DATE                 = 0x12,  
    NATIVE_TYPE_BSTR                 = 0x13,  
    NATIVE_TYPE_LPSTR                = 0x14,  
    NATIVE_TYPE_LPWSTR               = 0x15,  
    NATIVE_TYPE_LPTSTR               = 0x16,  
    NATIVE_TYPE_FIXEDSYSSTRING       = 0x17,  
    NATIVE_TYPE_OBJECTREF            = 0x18,  
    NATIVE_TYPE_IUNKNOWN             = 0x19,  
    NATIVE_TYPE_IDISPATCH            = 0x1a,  
    NATIVE_TYPE_STRUCT               = 0x1b,  
    NATIVE_TYPE_INTF                 = 0x1c,  
    NATIVE_TYPE_SAFEARRAY            = 0x1d,  
    NATIVE_TYPE_FIXEDARRAY           = 0x1e,  
    NATIVE_TYPE_INT                  = 0x1f,  
    NATIVE_TYPE_UINT                 = 0x20,  
  
    NATIVE_TYPE_NESTEDSTRUCT         = 0x21,  
    NATIVE_TYPE_BYVALSTR             = 0x22,  
    NATIVE_TYPE_ANSIBSTR             = 0x23,  
    NATIVE_TYPE_TBSTR                = 0x24,  
    NATIVE_TYPE_VARIANTBOOL          = 0x25,  
    NATIVE_TYPE_FUNC                 = 0x26,  
  
    NATIVE_TYPE_ASANY                = 0x28,  
    NATIVE_TYPE_ARRAY                = 0x2a,  
    NATIVE_TYPE_LPSTRUCT             = 0x2b,  
    NATIVE_TYPE_CUSTOMMARSHALER      = 0x2c,  
    NATIVE_TYPE_IINSPECTABLE         = 0x2e,  
    NATIVE_TYPE_HSTRING              = 0x2f,  
  
    NATIVE_TYPE_ERROR                = 0x2d,   
  
    NATIVE_TYPE_MAX                  = 0x50  
  
} CorNativeType;  
```  
  
## <a name="members"></a>Členové  
  
|Člen|Popis|  
|------------|-----------------|  
|`NATIVE_TYPE_END`|Zastaralé.|  
|`NATIVE_TYPE_VOID`|Zastaralé.|  
|`NATIVE_TYPE_BOOLEAN`|Kladná logická hodnota o velikosti 4 bajty, kde TRUE je nenulová a hodnota FALSE je nula.|  
|`NATIVE_TYPE_I1`|8bitové celé číslo se znaménkem.|  
|`NATIVE_TYPE_U1`|16bitová celočíselná hodnota bez znaménka.|  
|`NATIVE_TYPE_I2`|16bitová celočíselná hodnota se znaménkem.|  
|`NATIVE_TYPE_U2`|16bitová celočíselná hodnota bez znaménka.|  
|`NATIVE_TYPE_I4`|Podepsaná hodnota se znaménkem 32.|  
|`NATIVE_TYPE_U4`|Celočíselná hodnota bez znaménka 32-bit.|  
|`NATIVE_TYPE_I8`|Podepsaná hodnota se znaménkem 64.|  
|`NATIVE_TYPE_U8`|Celočíselná hodnota bez znaménka 64-bit.|  
|`NATIVE_TYPE_R4`|Číselná hodnota s plovoucí desetinnou čárkou a 4 bajty.|  
|`NATIVE_TYPE_R8`|Číselná hodnota s plovoucí desetinnou čárkou o velikosti 8 bajtů.|  
|`NATIVE_TYPE_SYSCHAR`|Zastaralé.|  
|`NATIVE_TYPE_VARIANT`|Zastaralé.|  
|`NATIVE_TYPE_CURRENCY`|Číselný typ COM, který odpovídá spravovanému typu <xref:System.Decimal>.|  
|`NATIVE_TYPE_PTR`|Zastaralé.|  
|`NATIVE_TYPE_DECIMAL`|Zastaralé.|  
|`NATIVE_TYPE_DATE`|Zastaralé.|  
|`NATIVE_TYPE_BSTR`|Zprostředkovatel komunikace s objekty COM.|  
|`NATIVE_TYPE_LPSTR`|Hodnota řetězce typem LPStr.|  
|`NATIVE_TYPE_LPWSTR`|Hodnota řetězce LPWSTR.|  
|`NATIVE_TYPE_LPTSTR`|Hodnota řetězce LPTSTR.|  
|`NATIVE_TYPE_FIXEDSYSSTRING`|Pevná, systémem definovaná řetězcová hodnota.|  
|`NATIVE_TYPE_OBJECTREF`|Zastaralé.|  
|`NATIVE_TYPE_IUNKNOWN`|Zprostředkovatel komunikace s objekty COM.|  
|`NATIVE_TYPE_IDISPATCH`|Zprostředkovatel komunikace s objekty COM.|  
|`NATIVE_TYPE_STRUCT`|Hodnota nativní struktury.|  
|`NATIVE_TYPE_INTF`|Zprostředkovatel komunikace s objekty COM.|  
|`NATIVE_TYPE_SAFEARRAY`|Zprostředkovatel komunikace s objekty COM.|  
|`NATIVE_TYPE_FIXEDARRAY`|Hodnota pole s pevnou délkou.|  
|`NATIVE_TYPE_INT`|Nativní 16bitové celočíselné hodnoty se znaménkem.|  
|`NATIVE_TYPE_UINT`|Nativní 16bitová hodnota unsigned integer.|  
|`NATIVE_TYPE_NESTEDSTRUCT`|Zastaralé.<br /><br /> Použijte NATIVE_TYPE_STRUCT.|  
|`NATIVE_TYPE_BYVALSTR`|Zprostředkovatel komunikace s objekty COM.|  
|`NATIVE_TYPE_ANSIBSTR`|Zprostředkovatel komunikace s objekty COM.|  
|`NATIVE_TYPE_TBSTR`|Zprostředkovatel komunikace s objekty COM.<br /><br /> V závislosti na platformě vyberte BSTR nebo ANSIBSTR.|  
|`NATIVE_TYPE_VARIANTBOOL`|Logická hodnota 2 bajtů, kde TRUE je-1 a FALSE je nula.|  
|`NATIVE_TYPE_FUNC`|Ukazatel na funkci.|  
|`NATIVE_TYPE_ASANY`|Odkaz na jakýkoliv nativní typ.|  
|`NATIVE_TYPE_ARRAY`|Odkaz na pole se členy nespecifikovaného typu.|  
|`NATIVE_TYPE_LPSTRUCT`|Ne32ý celočíselný ukazatel na strukturu.|  
|`NATIVE_TYPE_CUSTOMMARSHALER`|Vlastní nativní typ zařazovacího modulu.<br /><br /> Musí následovat řetězec v následujícím formátu: "název nativního typu/0Custom zařazovacího typu/0Optional soubor cookie/0" nebo "{Native GUID} název typu/0Optional soubor cookie/0"|  
|`NATIVE_TYPE_ERROR`|Zprostředkovatel komunikace s objekty COM.<br /><br /> ELEMENT_TYPE_I4 tento typ mapuje na VT_HRESULT.|  
|`NATIVE_TYPE_IINSPECTABLE`|Nativní typ `IInspectable`.|  
|`NATIVE_TYPE_HSTRING`|Nativní `HString`.|  
|`NATIVE_TYPE_MAX`|Neplatná hodnota.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Hlavička:** CorHdr. h  
  
 **Verze .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.UnmanagedType>
- [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
