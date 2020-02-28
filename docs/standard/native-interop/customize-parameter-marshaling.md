---
title: Přizpůsobení zařazování parametrů – .NET
description: Naučte se, jak přizpůsobit, jak .NET zařazování parametrů do nativní reprezentace.
ms.date: 01/18/2019
ms.openlocfilehash: ff646ad942cf051ce90cd75b24c8562e536182d9
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159608"
---
# <a name="customizing-parameter-marshaling"></a>Přizpůsobení zařazování parametrů

Pokud chování při zařazování výchozích parametrů modulu .NET runtime nezpůsobí, můžete použít atribut <xref:System.Runtime.InteropServices.MarshalAsAttribute?displayProperty=nameWithType> k přizpůsobení způsobu zařazení parametrů.

## <a name="customizing-string-parameters"></a>Přizpůsobení parametrů řetězce

Rozhraní .NET má různé formáty pro zařazování řetězců. Tyto metody jsou rozděleny do samostatných oddílů v řetězcích stylu C a ve formátech řetězců orientovaných na systém Windows.

### <a name="c-style-strings"></a>Řetězce ve stylu jazyka C

Každý z těchto formátů předá řetězec zakončený hodnotou null do nativního kódu. Liší se v kódování nativního řetězce.

| hodnota `System.Runtime.InteropServices.UnmanagedType` | Kódování |
|------------------------------------------------------|----------|
| LPStr | ANSI |
| LPUTF8Str | UTF-8 |
| LPWStr | UTF-16 |
| LPTStr | UTF-16 |

Formát <xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr?displayProperty=nameWithType> se mírně liší. Podobně jako `LPWStr`, zařazování řetězce do nativního řetězce ve stylu jazyka C kódovaného v kódování UTF-16. Spravovaný podpis však předáte do řetězce odkazem a na základě odpovídajícího nativního podpisu převezme řetězec podle hodnoty. Tento rozdíl umožňuje použít nativní rozhraní API, které přebírá řetězec podle hodnoty a upravuje ho místně bez nutnosti použít `StringBuilder`. Doporučujeme, abyste ručně používali tento formát, protože je náchylný k záměně s neshodou nativních a spravovaných podpisů.

### <a name="windows-centric-string-formats"></a>Formáty řetězců orientované na systém Windows

Při interakci s rozhraními COM nebo OLE pravděpodobně zjistíte, že nativní funkce přebírají řetězce jako argumenty `BSTR`. K zařazení řetězce jako `BSTR`můžete použít <xref:System.Runtime.InteropServices.UnmanagedType.BStr?displayProperty=nameWithType> nespravovaný typ.

Pokud pracujete s rozhraními API WinRT, můžete použít formát <xref:System.Runtime.InteropServices.UnmanagedType.HString?displayProperty=nameWithType> k zařazení řetězce jako `HSTRING`.

## <a name="customizing-array-parameters"></a>Přizpůsobení parametrů pole

Rozhraní .NET také poskytuje více způsobů zařazování parametrů pole. Pokud voláte rozhraní API, které přijímá pole ve stylu jazyka C, použijte <xref:System.Runtime.InteropServices.UnmanagedType.LPArray?displayProperty=nameWithType> nespravovaný typ. Pokud hodnoty v poli vyžadují přizpůsobené zařazování, můžete použít pole <xref:System.Runtime.InteropServices.MarshalAsAttribute.ArraySubType> v atributu `[MarshalAs]` pro.

Pokud používáte rozhraní API modelu COM, budete pravděpodobně muset zařazovat parametry pole jako `SAFEARRAY*`s. K tomu můžete použít <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType> nespravovaný typ. Výchozí typ prvků `SAFEARRAY` lze zobrazit v tabulce [přizpůsobení `object` polí](./customize-struct-marshaling.md#marshaling-systemobjects). Pole <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArraySubType?displayProperty=nameWithType> a <xref:System.Runtime.InteropServices.MarshalAsAttribute.SafeArrayUserDefinedSubType?displayProperty=nameWithType> lze použít k přizpůsobení přesného typu prvku `SAFEARRAY`.

## <a name="customizing-boolean-or-decimal-parameters"></a>Přizpůsobení logických nebo desetinných parametrů

Informace o zařazování logických nebo desetinných parametrů najdete v tématu [přizpůsobení zařazování struktury](customize-struct-marshaling.md).

## <a name="customizing-object-parameters-windows-only"></a>Přizpůsobení parametrů objektu (pouze systém Windows)

V systému Windows modul runtime .NET poskytuje řadu různých způsobů zařazování parametrů objektů do nativního kódu.

### <a name="marshaling-as-specific-com-interfaces"></a>Zařazování jako specifických rozhraní COM

Pokud rozhraní API převezme ukazatel na objekt modelu COM, můžete použít libovolný z následujících formátů `UnmanagedType` v parametru `object`typu a sdělit tak technologii .NET možnost zařazování jako těchto specifických rozhraní:

- `IUnknown`
- `IDispatch`
- `IInspectable`

Kromě toho, pokud je typ označený `[ComVisible(true)]` nebo zařadíte `object` typ, můžete použít formát <xref:System.Runtime.InteropServices.UnmanagedType.Interface?displayProperty=nameWithType> k zařazení objektu jako vydanou obálku modelu COM pro zobrazení vašeho typu.

### <a name="marshaling-to-a-variant"></a>Zařazování do `VARIANT`

Pokud vaše nativní rozhraní API přebírá `VARIANT`Win32, můžete použít formát <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> na parametru `object` k zařazení objektů jako `VARIANT`s. V dokumentaci k [přizpůsobení `object` polí](customize-struct-marshaling.md#marshaling-systemobjects) pro mapování mezi typy rozhraní .net a `VARIANT` typy.

### <a name="custom-marshalers"></a>Vlastní zařazovací modul

Pokud chcete promítnout nativní rozhraní COM do jiného spravovaného typu, můžete použít formát `UnmanagedType.CustomMarshaler` a implementaci <xref:System.Runtime.InteropServices.ICustomMarshaler> k poskytnutí vlastního kódu zařazování.
