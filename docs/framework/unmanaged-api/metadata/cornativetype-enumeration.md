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
ms.openlocfilehash: 09a351db65c7ed310d3eb68c71a5207ed6040dd4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79177973"
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
|`NATIVE_TYPE_BOOLEAN`|4bajtová logická hodnota, kde true je nenulová a NEPRAVDA je nula.|  
|`NATIVE_TYPE_I1`|Podepsaná osmibitová celočíselná hodnota.|  
|`NATIVE_TYPE_U1`|Nepodepsaná osmibitová celočíselná hodnota.|  
|`NATIVE_TYPE_I2`|Podepsaná 16bitová celočíselná hodnota.|  
|`NATIVE_TYPE_U2`|Nepodepsaná 16bitová celočíselná hodnota.|  
|`NATIVE_TYPE_I4`|Podepsaná 32bitová celočíselná hodnota.|  
|`NATIVE_TYPE_U4`|Nepodepsaná 32bitová celočíselná hodnota.|  
|`NATIVE_TYPE_I8`|Podepsaná 64bitová celočíselná hodnota.|  
|`NATIVE_TYPE_U8`|Nepodepsaná 64bitová celočíselná hodnota.|  
|`NATIVE_TYPE_R4`|Číselná hodnota s plovoucí desetinnou desetinnou hodnotou o hodnotě 4 bajtů.|  
|`NATIVE_TYPE_R8`|Osmibajtová číselná hodnota s plovoucí desetinnou desetinnou desetinnou hodnotou.|  
|`NATIVE_TYPE_SYSCHAR`|Zastaralé.|  
|`NATIVE_TYPE_VARIANT`|Zastaralé.|  
|`NATIVE_TYPE_CURRENCY`|Číselný typ COM, který <xref:System.Decimal> odpovídá spravovanému typu.|  
|`NATIVE_TYPE_PTR`|Zastaralé.|  
|`NATIVE_TYPE_DECIMAL`|Zastaralé.|  
|`NATIVE_TYPE_DATE`|Zastaralé.|  
|`NATIVE_TYPE_BSTR`|COM Interop.|  
|`NATIVE_TYPE_LPSTR`|Hodnota řetězce LPSTR.|  
|`NATIVE_TYPE_LPWSTR`|Hodnota řetězce LPWSTR.|  
|`NATIVE_TYPE_LPTSTR`|Hodnota řetězce LPTSTR.|  
|`NATIVE_TYPE_FIXEDSYSSTRING`|Pevná, systémem definovaná hodnota řetězce.|  
|`NATIVE_TYPE_OBJECTREF`|Zastaralé.|  
|`NATIVE_TYPE_IUNKNOWN`|COM Interop.|  
|`NATIVE_TYPE_IDISPATCH`|COM Interop.|  
|`NATIVE_TYPE_STRUCT`|Nativní hodnota struktury.|  
|`NATIVE_TYPE_INTF`|COM Interop.|  
|`NATIVE_TYPE_SAFEARRAY`|COM Interop.|  
|`NATIVE_TYPE_FIXEDARRAY`|Hodnota pole s pevnou délkou.|  
|`NATIVE_TYPE_INT`|Nativní 16bitová celočíselná hodnota.|  
|`NATIVE_TYPE_UINT`|Nativní 16bitová celočíselná hodnota bez podpisu.|  
|`NATIVE_TYPE_NESTEDSTRUCT`|Zastaralé.<br /><br /> Použijte NATIVE_TYPE_STRUCT.|  
|`NATIVE_TYPE_BYVALSTR`|COM Interop.|  
|`NATIVE_TYPE_ANSIBSTR`|COM Interop.|  
|`NATIVE_TYPE_TBSTR`|COM Interop.<br /><br /> Vyberte BSTR nebo ANSIBSTR v závislosti na platformě.|  
|`NATIVE_TYPE_VARIANTBOOL`|Dvoubajtová logická hodnota, kde TRUE je -1 a FALSE je nula.|  
|`NATIVE_TYPE_FUNC`|Ukazatel funkce.|  
|`NATIVE_TYPE_ASANY`|Odkaz na libovolný nativní typ.|  
|`NATIVE_TYPE_ARRAY`|Odkaz na pole s členy neurčeného typu.|  
|`NATIVE_TYPE_LPSTRUCT`|32bitový celočíselný ukazatel na strukturu.|  
|`NATIVE_TYPE_CUSTOMMARSHALER`|Nativní typ vlastního zařazovače.<br /><br /> Následuje řetězec následujícího formátu: "Nativní název typu/0Vlastní název zařazování/0Volitelný soubor cookie/0" nebo "{Nativní typ GUID}/0Vlastní název zařazování/0Volitelný soubor cookie/0"|  
|`NATIVE_TYPE_ERROR`|COM Interop.<br /><br /> S ELEMENT_TYPE_I4 tento typ mapuje na VT_HRESULT.|  
|`NATIVE_TYPE_IINSPECTABLE`|Nativní `IInspectable` typ.|  
|`NATIVE_TYPE_HSTRING`|Rodilý . `HString`|  
|`NATIVE_TYPE_MAX`|Neplatná hodnota.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Viz [Systémové požadavky](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorHdr.h  
  
 **Verze rozhraní .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.InteropServices.UnmanagedType>
- [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
