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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bf62000fd4ec5c8f3dea3fa7d560b3f9ead33fa7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59113916"
---
# <a name="cornativetype-enumeration"></a>CorNativeType – výčet
Obsahuje hodnoty, které popisují nativní nespravovaných typů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
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
|`NATIVE_TYPE_BOOLEAN`|4 bajty. logická hodnota, kde hodnota TRUE je nenulová a FALSE je nula.|  
|`NATIVE_TYPE_I1`|Podepsané 8bitovou celočíselnou hodnotu.|  
|`NATIVE_TYPE_U1`|Hodnota typu celé číslo bez znaménka 8 bitů.|  
|`NATIVE_TYPE_I2`|Hodnota, celé číslo se znaménkem 16 bitů.|  
|`NATIVE_TYPE_U2`|Hodnota typu celé číslo bez znaménka 16 bitů.|  
|`NATIVE_TYPE_I4`|Hodnota, celé číslo se znaménkem 32-bit.|  
|`NATIVE_TYPE_U4`|Hodnota typu celé číslo bez znaménka 32-bit.|  
|`NATIVE_TYPE_I8`|Hodnota, celé číslo se znaménkem 64-bit.|  
|`NATIVE_TYPE_U8`|Hodnota typu celé číslo bez znaménka 64-bit.|  
|`NATIVE_TYPE_R4`|4bajtový s plovoucí desetinnou čárkou číselnou hodnotu.|  
|`NATIVE_TYPE_R8`|8bajtový s plovoucí desetinnou čárkou číselnou hodnotu.|  
|`NATIVE_TYPE_SYSCHAR`|Zastaralé.|  
|`NATIVE_TYPE_VARIANT`|Zastaralé.|  
|`NATIVE_TYPE_CURRENCY`|Číselný typ modelu COM, která odpovídá spravovanou <xref:System.Decimal> typu.|  
|`NATIVE_TYPE_PTR`|Zastaralé.|  
|`NATIVE_TYPE_DECIMAL`|Zastaralé.|  
|`NATIVE_TYPE_DATE`|Zastaralé.|  
|`NATIVE_TYPE_BSTR`|Komunikace s objekty COM|  
|`NATIVE_TYPE_LPSTR`|Hodnota řetězce typem LPSTR.|  
|`NATIVE_TYPE_LPWSTR`|LPWSTR řetězcovou hodnotu.|  
|`NATIVE_TYPE_LPTSTR`|LPTSTR řetězcovou hodnotu.|  
|`NATIVE_TYPE_FIXEDSYSSTRING`|Hodnotu řetězce pevné, definované v systému.|  
|`NATIVE_TYPE_OBJECTREF`|Zastaralé.|  
|`NATIVE_TYPE_IUNKNOWN`|Komunikace s objekty COM|  
|`NATIVE_TYPE_IDISPATCH`|Komunikace s objekty COM|  
|`NATIVE_TYPE_STRUCT`|Hodnota nativní struktury.|  
|`NATIVE_TYPE_INTF`|Komunikace s objekty COM|  
|`NATIVE_TYPE_SAFEARRAY`|Komunikace s objekty COM|  
|`NATIVE_TYPE_FIXEDARRAY`|Hodnota pole s pevnou délkou.|  
|`NATIVE_TYPE_INT`|Hodnota nativní 16bitové celé číslo se znaménkem.|  
|`NATIVE_TYPE_UINT`|Hodnota nativní 16bitové celé číslo bez znaménka.|  
|`NATIVE_TYPE_NESTEDSTRUCT`|Zastaralé.<br /><br /> Použijte NATIVE_TYPE_STRUCT.|  
|`NATIVE_TYPE_BYVALSTR`|Komunikace s objekty COM|  
|`NATIVE_TYPE_ANSIBSTR`|Komunikace s objekty COM|  
|`NATIVE_TYPE_TBSTR`|Komunikace s objekty COM<br /><br /> Vyberte, BSTR nebo ANSIBSTR podle platformy.|  
|`NATIVE_TYPE_VARIANTBOOL`|2bajtový logická hodnota, kde nastavena hodnota TRUE je -1 a hodnota FALSE je nula.|  
|`NATIVE_TYPE_FUNC`|Ukazatel na funkci.|  
|`NATIVE_TYPE_ASANY`|Odkaz na jakékoli nativního typu.|  
|`NATIVE_TYPE_ARRAY`|Odkaz na pole s členy neurčeného typu.|  
|`NATIVE_TYPE_LPSTRUCT`|32bitové celé číslo ukazatel na strukturu.|  
|`NATIVE_TYPE_CUSTOMMARSHALER`|Vlastní zařazování nativního typu.<br /><br /> Toto musí následovat řetězec následující formát: "Název/0Custom nativní typ zařazovacího modulu typu název/0Optional souboru cookie/0" nebo "{nativní typ GUID} / 0Custom zařazování zadejte název/0Optional souboru cookie/0"|  
|`NATIVE_TYPE_ERROR`|Komunikace s objekty COM<br /><br /> Tento typ s ELEMENT_TYPE_I4 mapuje VT_HRESULT.|  
|`NATIVE_TYPE_IINSPECTABLE`|Nativní `IInspectable` typu.|  
|`NATIVE_TYPE_HSTRING`|Nativní `HString`.|  
|`NATIVE_TYPE_MAX`|Neplatná hodnota.|  
  
## <a name="requirements"></a>Požadavky  
 **Platformy:** Zobrazit [požadavky na systém](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Záhlaví:** CorHdr.h  
  
 **Verze rozhraní .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.InteropServices.UnmanagedType>
- [Výčty pro metadata](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
